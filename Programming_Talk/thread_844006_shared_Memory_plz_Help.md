---
title: "shared Memory plz Help"
date: 2008-06-29
forum: Programming Talk
---

### Post by tornado89 on 2008-06-29
I have a class named Peers containing 2 variables
bool* status, char* name

and a global variable 
[PHP] Peers p [/PHP]



now i'm creating a shared memory and attaching both of them 
to it
[PHP]
p.status = (bool*)shmat( id, NULL, 0 );
p.name   = (char*)shmat( id, NULL, 0 );
[/PHP]

Now I'm Creating A Child Using fork() That Modify The Value of p.status & p.name
And Only The Forked Child Is Accessing These Variables.. There's No Single Operation Done From The Parent Process.... but to shmat() them

Now After Changing The Value of p.status [PHP] *p.status = true [/PHP]
the first letter from p.name is deleted
for example if p.name contains "semaphore", it will be "emaphore"...

Any IDEA ???!!!!!

---

### Post by dwhitney67 on 2008-06-29
I see you attaching the shared memory, but I don't see where you created it.  Hint:  shmget().

Also, you need to define an allocated space for the name field of Peers.  Say an array of 80 characters?

Also, why are you attaching the individual components of the Peer class... just attach the class itself.  It will work unless your class has virtual functions.

For instance,
[PHP]
class Peers
{
  public:
    bool status;
    char name[80];
};
[/PHP]
Shared-Memory creator:
[PHP]
#include "Peers.h"

#include <fcntl.h>       // for O_RDWR | IPC_CREAT
#include <sys/types.h>   // for key_t
#include <sys/shm.h>     // for shmat()

#include <cstring>
#include <iostream>


int main(int argc, char** argv)
{
  key_t key = 1234;

  int shmid = shmget(key, sizeof(Peers), IPC_CREAT | 0666);

  if (shmid < 0)
  {
    perror("shmget");
    return -1;
  }

  void *shm = shmat(shmid, NULL, 0);

  if (shm == (char*) -1)
  {
    perror("shmat");
    return -1;
  }

  Peers *peers = reinterpret_cast<Peers*>(shm);

  peers->status = true;
  strncpy(peers->name, "semaphore", 9);  

  while (peers->status == true)
  {
    sleep(1);
  }

  if (shmdt(peers) < 0)
  {
    perror("shmdt");
    return -1;
  }

  if (shmctl(shmid, IPC_RMID, NULL) < 0)
  {
    perror("shmctl");
    return -1;
  }

  return 0;
}
[/PHP]
Shared-Memory client:
[PHP]
#include "Peers.h"

#include <sys/types.h>    // for key_t
#include <sys/shm.h>      // for shmget(), shmat()
#include <iostream>


int main(int argc, char** argv)
{
  key_t key = 1234;

  int shmid = shmget( key, sizeof(Peers), 0666 );

  if (shmid < 0)
  {
    perror("shmget");
    return -1;
  }

  void *shm = shmat(shmid, NULL, 0);

  if (shm == (char *) -1)
  {
    perror("shmat");
    return -1;
  }

  Peers *peers = reinterpret_cast<Peers*>(shm);

  std::cout << "Peers status: " << (peers->status ? "true" : "false") << std::endl;
  std::cout << "Peers name:   " << peers->name << std::endl;

  peers->status = false;

  return 0;
}
[/PHP]

---

### Post by tornado89 on 2008-06-29
Thanks dwhitney67...
I Am Using The shmget To Create The Shared Memory For Sure... :)
But Ur Code Helped Much...
I Don't Know Why Didn't I Attach The Class All At Once...
It Was Like 4:00AM When I Had This Issue At First...Perhaps I Was Sleepy
:lolflag:

Thanks...

---

### Post by dwhitney67 on 2008-06-29
You are welcome!  However, just bear in mind for future reference, that the reason you initially had trouble with your code is because you had failed to define space for the 'name' element of Peers.

Originally Peers was (presumably):
[PHP]class Peers
{
  public:
    bool status;
    char *name;
};[/PHP]
The size of Peers in this case is a mere 8 bytes (1 for the boolean, 4 for the pointer, 3 of padding to make the class structure word-aligned).  In any case, 8 bytes was too small to store the boolean status value _and_ the word "semaphore".  I think this would have been immediately apparent had your code crashed (seg-faulted) rather than spit out erroneous output.

Anyhow, I hope this makes sense to you.

---

