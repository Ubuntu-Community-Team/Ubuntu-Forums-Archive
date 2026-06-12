---
title: "Makefile g++ gcc error"
date: 2010-10-02
forum: Programming Talk
---

### Post by Geek10 on 2010-10-02
Hi all,

I have been using a makefile to try to compile some code I would like to test. The makefile is this:
```

CC=gcc
CFLAGS=-c -Wall
LDFLAGS=
SOURCES=src/MutexTrial.cpp
OBJECTS=$(SOURCES:.cpp=.o)
EXECUTABLE=hello

all: $(SOURCES) $(EXECUTABLE)
    
$(EXECUTABLE): $(OBJECTS) 
    $(CC) $(LDFLAGS) $(OBJECTS) pthread -o thread $@

.cpp.o:
    $(CC) $(CFLAGS) $< pthread -o thread $@

```The file I am trying to compile is an example of mutexes used (I know it is not PHP code, but PHP in square brackets makes it MUCH clearer because of the commenting).
[PHP]
/* You can compile this program with:
 * gcc -Wall -D_REENTRANT -o thread thread.c<\n>
 * -lpthread */
/* We always need to include this header file for<\n>
 * the threads */
#include <pthread.h>
#include <stdio.h>
#include <stdlib.h>

/* This is the prototype for our thread function */
void *mythread(void *data);

/* We must initialize our mutex */
pthread_mutex_t count_mutex = PTHREAD_MUTEX_INITIALIZER;

/* This will be a shared variable between all of<\n>
 * the threads */
int x = 0;

int main(void) {
   /* This will be an array holding the thread ids<\n>
    * for each thread */
   /* We keep track of all the tids so that we can<\n>
    * call pthread_join()later to retrieve
    * the return value from the thread */
   pthread_t tids[10];

   int i;

   /* We will now create the 10 threads. Each<\n>
    * thread will increment x until x is 4000.
    * On our last argument ot pthread_create
    * we could have passed an argument to the
    * thread function */
   for(i=0; i<10; i++) {
      pthread_create(&tids[i], NULL, mythread, NULL);
   }

   /* We will now wait for each thread to<\n>
    * terminate */
   for(i=0; i<10; i++) {
   /* This will block until the specified
    * thread finishes execution. Our second
    * argument to pthread_join can be a pointer
    * that will have the return value of the
    * thread stored in it */
      pthread_join(tids[i], NULL);
      printf("Thread id %ld returned\n", tids[i]);
   }
   return(1);
}
   /* This is our actual thread function */
void *mythread(void *data) {
   while(x < 4000) {
      /* We will now try to lock the mutex. If
       * another thread already has it locked, we
       * block until it is available again. After
       * you first run this program, you should
       * comment out the lock/unlock lines in this
       * function so that you can see why you need
       * mutexes. */
      pthread_mutex_lock(&count_mutex);

      x++;

      /* We will have it print out the thread ID
       * and the value of X */
      printf("Thread ID%ld: X is now %d.\n",
         pthread_self(), x);

      /* We will now release the mutex so that
       * another thread gets the chance to run. */
      pthread_mutex_unlock(&count_mutex);
   }
   /* We can return a pointer. Whatever pointer
    * we return can later be retrieved using the
    * pthread_join function */
   pthread_exit(NULL);
}
[/PHP]I get the following error when I try and make it:

[COLOR=DarkGreen]gcc -c -Wall src/MutexTrial.cpp pthread -o thread src/MutexTrial.o
gcc: pthread: No such file or directory
gcc: src/MutexTrial.o: No such file or directory
gcc: error trying to exec 'cc1plus': execvp: No such file or directory
make: *** [src/MutexTrial.o] Error 1[/COLOR]

The error [COLOR=DarkGreen]gcc: error trying to exec 'cc1plus': execvp: No  such file or directory [COLOR=Black]is quite a common one. Like a good boy, I looked it up on these forums and people suggested:

1. Update the gcc and g++ using the command: [COLOR=DarkRed]sudo apt-get install build-essential g++ [COLOR=black]and[/COLOR] [/COLOR][/COLOR][/COLOR][COLOR=DarkGreen][COLOR=Black][COLOR=DarkRed]sudo  apt-get install build-essential gcc[/COLOR][/COLOR][/COLOR][COLOR=DarkGreen][COLOR=Black] but get similar responses for both.
[COLOR=DarkGreen]I get the following
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package build-essential is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package build-essential has no installation candidate
[COLOR=Black]
2. Make sure you have the cc1 files!
I did this by typing:[COLOR=DarkRed] find /usr/lib/gcc -name cc1 -o -name cc1plus[/COLOR]
And got: 
[COLOR=DarkGreen]/usr/lib/gcc/i486-linux-gnu/4.4/cc1

[COLOR=Black]So I'm at a loose end as to know what to do!

Thanks for any help.
[/COLOR] [/COLOR]
[/COLOR][/COLOR]


[/COLOR][/COLOR]

---

### Post by spjackson on 2010-10-02
You have several mistakes in your makefile. The following works for me. (If you copy and paste, note that the action lines need to begin with a TAB.)

```

CC=g++
CFLAGS=-c -Wall
LDFLAGS=
SOURCES=src/MutexTrial.cpp
OBJECTS=$(SOURCES:.cpp=.o)
EXECUTABLE=hello

all: $(SOURCES) $(EXECUTABLE)

$(EXECUTABLE): $(OBJECTS)
    $(CC) $(LDFLAGS) $(OBJECTS) -lpthread -o $@

.cpp.o:
    $(CC) $(CFLAGS) $< -o $@

```

---

### Post by Geek10 on 2010-10-02
Thanks spjackson, I reckon you fixed some of my errors I would have hit once I fix this gcc and g++ problem. Your help is very much appreciated - my experience with makefiles is negligible - I have found a great site to understand them though.

[http://www.cs.colby.edu/maxwell/courses/tutorials/maketutor/](http://www.cs.colby.edu/maxwell/courses/tutorials/maketutor/)

I am using the update manager to ensure that I have the latest versions of everything because [COLOR=DarkRed]sudo apt-get build essentials[/COLOR] didn't work for me.

I'll let people know if that fixes the errors I get with gcc and g++.

---

### Post by Geek10 on 2010-10-02
So synaptics package manager found a whole lot more g++ files when I followed the instructions on this page. They installed and I rebooted the computer.

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

So now when I type in: "sudo make" it gives me a different error.

[COLOR=DarkRed]g++ -Wall -D_GNULINUX -c src/MutexTrial.cpp -o src/MutexTrial.o 
Unable to exec g++.real: No such file or directory
make: *** [src/MutexTrial.o] Error 2[/COLOR]

I looked up "Unable to exec g++.real: No such file or directory" and there is an archived Ubuntu forum thread on that topic here:

[http://ubuntuforums.org/archive/index.php/t-520703.html](http://ubuntuforums.org/archive/index.php/t-520703.html)

This made me change one thing in the makefile - the line with CC to do g++ not gcc, so I am compiling C++.
[COLOR=DarkRed]CC = g++[/COLOR]

I don't really mind if your suggestions might lead me on the wrong track for a while - I'm just stumped and I need to find another way of getting around this! Please suggest something to help - I'll post ANY information you need if you are generous enough to assist me!

Thanks,

---

### Post by Geek10 on 2010-10-02
SUCCESS!!!!

I found I kept getting the error "Unable to exec g++.real: No such file or directory".

I tried "sudo apt-get update" in the command console, but this wouldn't find the necessary libraries. I found I needed to edit /etc/apt/sources.list with the following:

These are the repositories that are used to see if your computer packages are up to date. I modified all of the library lines from [https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine)

To edit sources.list, first make a backup by typing:
```

cp /etc/apt/sources.list /etc/apt/sources.list.backup

```Then type the following commands

```

cd /etc/apt
gksudo gedit sources.list

```Now delete everything in there, and paste the following in (all the blue section) - If you have the latest Ubuntu version (in my time it's Maverick Meerkat, then replace all of the "Lucid Lynx" with "Maverick Meerkat", and all "lucid" with "maverick")

[COLOR=Navy]# sources.list
# deb cdrom:[Ubuntu 8.04.1 _Lucid Lynx_ - Release amd64 (20080701)]/ lucid main restricted

#deb cdrom:[Ubuntu 8.04.1 _Lucid Lynx_ - Release amd64 (20080701)]/ lucid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates main restricted

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates universe

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates multiverse

[COLOR=Black]Now do
```

sudo apt-get update
sudo apt-get install build-essential g++

```The update will take much longer than originally - for me it downloaded 11.2MB of lists of software. Then the g++ you have to confirm you want the packages you don't have, and it downloaded the actual missing packages.

And that's it! After only 3 hours or so of searching, my problem was finally resolved.

To test my g++ worked, I made a little file test.cpp
[PHP]
#include <iostream>
#include <ostream>

using namespace std;

int main()
{
cout << "Hello World!" << endl;
return 0;
}
[/PHP]And then changed directory ("cd" command) to that folder and typed:
[CODE]
g++ test.cpp -o MyOutputProgram
./MyOutputProgram
[CODE]
If the ./[/COLOR][/COLOR][COLOR=Navy][COLOR=Black]MyOutputProgram does not allow you to run the shell, then use "sudo [/COLOR][/COLOR][COLOR=Navy][COLOR=Black]./MyOutputProgram"

:KS:KS:KS[/COLOR][/COLOR][COLOR=Navy][COLOR=Black]:grin:[/COLOR][/COLOR][COLOR=Navy][COLOR=Black]:grin:[/COLOR][/COLOR][COLOR=Navy][COLOR=Black]:grin:[/COLOR][/COLOR]

---

### Post by donbis88 on 2010-10-05
Hi...
I have the same problem, but I can't resolve it...I just reinstall g++ and build-essential....
How can I resolve??


this is my code:

[B][I][COLOR=black]root@gauge:/home/simone/fisica/Rimoldi/geant4/examples/novice/N02# g4make
Running " /usr/bin/make "
Making dependency for file exampleN02.cc ...
g++: error trying to exec 'cc1plus': execvp: No such file or directory
Making dependency for file src/ExN02TrackerSD.cc ...
g++: error trying to exec 'cc1plus': execvp: No such file or directory
Making dependency for file src/ExN02TrackerHit.cc ...
g++: error trying to exec 'cc1plus': execvp: No such file or directory
Making dependency for file src/ExN02SteppingVerbose.cc ...
g++: error trying to exec 'cc1plus': execvp: No such file or directory
Making dependency for file src/ExN02SteppingAction.cc ...
g++: error trying to exec 'cc1plus': execvp: No such file or directory
Making dependency for file src/ExN02RunAction.cc ...
g++: error trying to exec 'cc1plus': execvp: No such file or directory
Making dependency for file src/ExN02PrimaryGeneratorAction.cc ...
g++: error trying to exec 'cc1plus': execvp: No such file or directory
Making dependency for file src/ExN02PhysicsList.cc ...
g++: error trying to exec 'cc1plus': execvp: No such file or directory
Making dependency for file src/ExN02MagneticField.cc ...
g++: error trying to exec 'cc1plus': execvp: No such file or directory
Making dependency for file src/ExN02EventAction.cc ...
g++: error trying to exec 'cc1plus': execvp: No such file or directory
Making dependency for file src/ExN02DetectorMessenger.cc ...
g++: error trying to exec 'cc1plus': execvp: No such file or directory
Making dependency for file src/ExN02DetectorConstruction.cc ...
g++: error trying to exec 'cc1plus': execvp: No such file or directory
Making dependency for file src/ExN02ChamberParameterisation.cc ...
g++: error trying to exec 'cc1plus': execvp: No such file or directory
Compiling ExN02ChamberParameterisation.cc ...
g++: error trying to exec 'cc1plus': execvp: No such file or directory
make: *** [/home/simone/fisica/Rimoldi/geant4/examples/novice/N02/tmp/Linux-g++/exampleN02/ExN02ChamberParameterisation.o] Error 1
[/COLOR][/I][/B]

---

### Post by Geek10 on 2010-10-14
donbis88, did you follow my instructions carefully and completely. I got similar errors, and I posted above exactly how to fix them!

---

