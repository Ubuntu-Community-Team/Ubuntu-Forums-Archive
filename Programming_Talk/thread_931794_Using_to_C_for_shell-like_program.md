---
title: "Using to C for shell-like program"
date: 2008-09-27
forum: Programming Talk
---

### Post by carrie.peary on 2008-09-27
Basically I'm trying to use C to execute commands like a shell would, such as "ls" "rm" "mkdir blah" etc. And I seem to be more and more stuck.

Basically this is what I have:

```

#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>
#include <sys/types.h>
  
int main(void)
{
	char str[64];
	pid_t  pid;
		
		while (str != "exit") {
					        
		    printf("mshell2-> ");
			scanf("%s",str); 
			
		    pid = fork();
		    
		    if (pid < 0) {
		    	fprintf(stderr, "Fork Failed");
		    	exit(-1);
		    }
		    else if (pid == 0) {
		         execl("/bin/sh", str, (char *) 0);
		    }
		    else {
		    	wait(NULL);
		        printf("*** Child is done ***\n");
		    }
		}   
	return 0;
}

```

But it doesn't like to do anything at all. I'm stuck really. 

Any help for just maybe how to get it to execute just any command would be great. I've scoured the internet but really haven't found much.

---

### Post by dribeas on 2008-09-27
> **carrie.peary said:**
> 
```

		         execl("/bin/sh", str, (char *) 0);

```


[man execl]("http://www.manpagez.com/man/3/execl/")

> 
int
execl(const char *path, const char *arg0, ... /*, (char *)0 */);


You are passing str as arg0 to /bin/sh, which is probably not what you want. I don't even know if that is what you want to do...

To exec, as an example, the equivalent of 'echo "Hello my friend"' you would need to:

```

execl( "/bin/echo", "echo", "Hello my friend", 0 );

```

---

### Post by stroyan on 2008-09-27
The "system()" function can give you a little help with starting shell commands.
Your fork/execl/wait can be replaced by ```
int result=system(str);
```

Your comparison to "exit" is only comparing addresses of the str
variable and the "exit" string constant.
It won't match when the string read in has the value "exit".
The strcmp function will make the comparison that you want.

You should get away from the habit of using scanf with %s.
Buffer overruns are a serious security problem.
You can use %as to ask scanf to allocate enough space for a string.
```

#include <unistd.h>
#include <malloc.h>
#include <stdio.h>

int main(int argc, char *argv[])
{
    char *str;

    printf("mshell2-> ");
    while (1 == scanf("%as", &str)) {
	if (strcmp("exit",str)==0) break;
	system(str);
	free(str);
	printf("*** Child is done ***\n");
	printf("mshell2-> ");
    }
    return 0;
}

```

---

### Post by dwhitney67 on 2008-09-28
If your goal is to learn C programming, then stick to using the C library rather than using the shell equivalents.

To list the contents of a directory:  opendir() and readdir()
Try using these in a manner that employs recursion, so that you can delve into sub-directories.

To remove a file:  unlink()

To make a directory:  mkdir()

The man-pages will be able to assist you with documentation on each of these library functions.

---

### Post by ankursethi on 2008-09-28
@dwhitney
I think carrie.peary is trying to write a whole new shell (like bash or ksh).

---

### Post by dwhitney67 on 2008-09-28
> **ankursethi said:**
> @dwhitney
I think carrie.peary is trying to write a whole new shell (like bash or ksh).
I have no idea what carrie.peary is trying to do.  However it does seem that he/she is depending on the shell (/bin/sh) to execute commands.  Thus I don't get the impression the application will yield anything substantial equaling an existing shell.

---

### Post by ankursethi on 2008-09-28
Oh, I noticed that just now.

(How *do* you write a shell anyway?)

---

### Post by dwhitney67 on 2008-09-28
Sorry, but my expertise falls quite short of being able to write a shell.  But it has been done and the source code is open source if you care to find out.

As for carrie.peary, here's a solution that you might find helpful:
[php]
#include <stdio.h>
#include <unistd.h>
#include <stdlib.h>
#include <string.h>
#include <sys/wait.h>


int main()
{
  // echo prompt
  while ( printf( "mysh > " ) )
  {
    char cmd[512] = {0};

    // await input of command; if none given, re-issue the prompt;
    // otherwise, remove ending newline character
    if ( fgets( cmd, sizeof(cmd), stdin ) == NULL )
    {
      printf( "\n" );
      continue;
    }
    cmd[ strlen(cmd) - 1 ] = '\0';

    if ( !strcmp( cmd, "quit" ) || !strcmp( cmd, "exit" ) )
    {
      break;
    }

    // fork process
    pid_t pid = fork();

    if ( pid < 0 )
    {
      perror( "Fork failed" );
      break;
    }
    else if ( pid == 0 )
    {
      // child process
      char ** argv = malloc( 10 * sizeof(char*) );
      int     argc = 0;
      char *  arg  = strtok( cmd, " " );

      // collect argv's; allow at most 9
      do
      {
        argv[ argc++ ] = strdup( arg );
      }
      while ( (arg = strtok( NULL, " " )) != 0  && argc < 9 );

      // terminate argv's with a null
      argv[ argc ] = 0;

      // execute shell command
      execvp( argv[0], argv );

      // free memory from strdup()
      for ( int i = 0; i < argc; ++i )
      {
        free( argv[i] );
      }
      free( argv );

      // exit child process
      exit(0);
    }
    else
    {
      // parent process... nothing to do
      wait( NULL );
    }
  }
  return 0;
}
[/php]

---

### Post by carrie.peary on 2008-09-28
> **dwhitney67 said:**
> Sorry, but my expertise falls quite short of being able to write a shell.  But it has been done and the source code is open source if you care to find out.

As for carrie.peary, here's a solution that you might find helpful:
[php]
#include <stdio.h>
#include <unistd.h>
#include <stdlib.h>
#include <string.h>
#include <sys/wait.h>


int main()
{
  // echo prompt
  while ( printf( "mysh > " ) )
  {
    char cmd[512] = {0};

    // await input of command; if none given, re-issue the prompt;
    // otherwise, remove ending newline character
    if ( fgets( cmd, sizeof(cmd), stdin ) == NULL )
    {
      printf( "\n" );
      continue;
    }
    cmd[ strlen(cmd) - 1 ] = '\0';

    if ( !strcmp( cmd, "quit" ) || !strcmp( cmd, "exit" ) )
    {
      break;
    }

    // fork process
    pid_t pid = fork();

    if ( pid < 0 )
    {
      perror( "Fork failed" );
      break;
    }
    else if ( pid == 0 )
    {
      // child process
      char ** argv = malloc( 10 * sizeof(char*) );
      int     argc = 0;
      char *  arg  = strtok( cmd, " " );

      // collect argv's; allow at most 9
      do
      {
        argv[ argc++ ] = strdup( arg );
      }
      while ( (arg = strtok( NULL, " " )) != 0  && argc < 9 );

      // terminate argv's with a null
      argv[ argc ] = 0;

      // execute shell command
      execvp( argv[0], argv );

      // free memory from strdup()
      for ( int i = 0; i < argc; ++i )
      {
        free( argv[i] );
      }
      free( argv );

      // exit child process
      exit(0);
    }
    else
    {
      // parent process... nothing to do
      wait( NULL );
    }
  }
  return 0;
}
[/php]

Thanks, the above is helping to get through this alot.

And to all who replied above, the reason I need to do this like I am is because it's for a school homework assignment. I do know/found others ways to get this done but this was the starting point for part of my HW assignment. I didn't want to post it all on here because I do want to figure it out myself, but just got really, really stuck.

So thanks everyone!

---

