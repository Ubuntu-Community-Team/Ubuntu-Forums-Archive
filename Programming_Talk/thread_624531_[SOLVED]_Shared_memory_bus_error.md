---
title: "[SOLVED] Shared memory bus error"
date: 2007-11-27
forum: Programming Talk
---

### Post by derrick81787 on 2007-11-27
Hi.  I've been trying to get shared memory working in one of my projects for a week or so, and I just cannot seem to get it working.  I would like to use POSIX shared memory, but I'm desperate enough that any type would do.  For my project, I just want to share a char* between two processes.  However, I've written two small test programs in order to try to get shared memory to work with them, but I get a bus error every time I try to run it, and I don't know why.  If anyone could just show me how to get shared memory working at all, I'd greatly appreciate it.

I've attached my test programs so you can see what I've been doing.  I've tried using shm_open and mmap as well as using shmget and shmat.  The file extensions should be .c, but I had to change them to .txt in order to upload them.

The commands I'm using to compile the programs are "gcc -lrt -g parent-mem.c -o parent-mem" and "gcc -lrt -g child-mem.c -o child-mem".

If anyone can help out, I'd really appreciate it.  Thanks a lot in advance.

- Derrick

---

### Post by dwhitney67 on 2007-11-27
Here's a reference I found on the web by merely doing a Google search:
[IPC: Shared Memory]("http://www.cs.cf.ac.uk/Dave/C/node27.html#SECTION002730000000000000000").

or you can look at my slightly modified example:

For the "creator", shm_creator.c:
```
#include <fcntl.h>       // for IPC_CREAT
#include <sys/types.h>   // for key_t
#include <sys/shm.h>     // for shmat()

#include <stdio.h>       // for perror() and snprintf()
#include <stdlib.h>      // for exit()
#include <errno.h>       // for errno
#include <unistd.h>      // for sleep()


int main( int argc, char** argv )
{
  key_t key = 1234;
  int shmid = -1;

  if ((shmid = shmget( key, 1024, IPC_CREAT | 0666 )) < 0 )
  {
    perror( "shmget" );
    exit( errno );
  }

  char* data = 0;
  if ((data = shmat( shmid, NULL, 0 )) == (char*) -1)
  {
    perror( "shmat" );
    exit( errno );
  }

  snprintf( (char*) data, 12, "hello world" );

  while ( *data != '\0' )
  {
    sleep( 1 );
  }

  if ( shmdt( data ) < 0 )
  {
    perror( "shmdt" );
    exit( errno );
  }

  if ( shmctl( shmid, IPC_RMID, NULL ) < 0 )
  {
    perror( "shmctl" );
    exit( errno );
  }

  return 0;
}
```

For the "client", shm_client.c:
```
#include <sys/types.h>    // for key_t
#include <sys/shm.h>      // for shmget(), shmat()
#include <stdio.h>        // for perror() and printf()
#include <stdlib.h>       // for exit()


int main( int argc, char** argv )
{
  key_t key = 1234;
  int shmid = -1;

  if ((shmid = shmget( key, 1024, 0666 )) < 0)
  {
    perror("shmget");
    exit(1);
  }

  char* shm = (char*) -1;
  if ((shm = shmat( shmid, NULL, 0 )) == (char *) -1)
  {
    perror("shmat");
    exit(1);
  }

  printf( "received message is '%s'\n", shm );

  *shm = '\0';    // notify the server to exit

  return 0;
}
```

To compile:
```
$ gcc --std=gnu99 shm_client.c -lrt -o client
$ gcc --std=gnu99 shm_creator.c -lrt -o creator
```

---

### Post by derrick81787 on 2007-11-27
Thanks a lot.  That worked perfectly.  I changed the code some to fit my needs a little better, so I'll post my code here in case anyone else has the same problem.  Again, thanks a lot.

For my parent process:
```

#include <fcntl.h>       // for IPC_CREAT
#include <sys/types.h>   // for key_t
#include <sys/shm.h>     // for shmat()

#include <stdio.h>       // for perror() and snprintf()
#include <stdlib.h>      // for exit()
#include <errno.h>       // for errno
#include <unistd.h>      // for sleep()


int main( int argc, char** argv )
{
  key_t key = getpid(); // will be random and unique
  int shmid = -1;

  if ((shmid = shmget( key, 1024, IPC_CREAT | 0666 )) < 0 )
  {
    perror( "shmget" );
    exit( errno );
  }

  char* data = 0;
  if ((data = shmat( shmid, NULL, 0 )) == (char*) -1)
  {
    perror( "shmat" );
    exit( errno );
  }

  snprintf( (char*) data, 12, "hello world" );

  if (fork() == 0)
     execl("./child-mem2", "./child-mem2", 0);

/* You would really want a semaphore, but this
 * works just for the example */
 sleep( 5 );

   printf("Parent received message is '%s'\n", data);

  if ( shmdt( data ) < 0 )
  {
    perror( "shmdt" );
    exit( errno );
  }

  if ( shmctl( shmid, IPC_RMID, NULL ) < 0 )
  {
    perror( "shmctl" );
    exit( errno );
  }

  return 0;
}

```

And for my child process
```

#include <sys/types.h>    // for key_t
#include <sys/shm.h>      // for shmget(), shmat()
#include <stdio.h>        // for perror() and printf()
#include <stdlib.h>       // for exit()
#include <unistd.h>


int main( int argc, char** argv )
{
  key_t key = getppid(); // will be random and always equal to the parent key
  int shmid = -1;

  if ((shmid = shmget( key, 1024, 0666 )) < 0)
  {
    perror("shmget");
    exit(1);
  }

  char* shm = (char*) -1;
  if ((shm = shmat( shmid, NULL, 0 )) == (char *) -1)
  {
    perror("shmat");
    exit(1);
  }

  printf( "Child received message is '%s'\n", shm );

  sprintf( (char*) shm, "goodbye world" );

  return 0;
}

```

---

