---
title: "Daemon input"
date: 2009-08-15
forum: Programming Talk
---

### Post by Hexorg on 2009-08-15
Good daytime to all of you!
I'm writting a little program in C++ that'll work in the background like daemon. Program writes some data to my device located at /dev/ttyUSB0

From time to time i'll have to send different commands to the program (like "--DisplayOff"); I'm trying to think what are the ways (and implementation of them) to send some commands to my program? i know how to build in a little upd server that would listen for commands, but that's just using up too much resources. 

Then i tried to open an ifstream, and try reading from it, program compiled well, but bash's echo "--DisplayOff" >> "d.commands" flew back with permission denied (even with sudo)

Then i found something about pipes, but couldn't quite get the code to work.

Any ideas what can i use? and how do linux's main daemons work like ./gdm stop and ./gdm start?

---

### Post by soltanis on 2009-08-15
I think the ./gdm behaviors you described are implemented by listening for signals. This works pretty well if your daemon only needs to do simple things (i.e. start up, shut down, reset state, reload configuration), but anything more advanced will require that you step it up.

You could have the program listen on a named pipe. Use mknod/mkfifo to create a special pipe on the filesystem, then listen for reads to it and interpret them as commands.

This usually works pretty well for me and is a common, easy arrangement that doesn't have to muck around with the difficulties of sockets. However, you might find that sockets give you the kind of versatility you need -- and their resource cost is not that great (it's about the same as if you were just reading from a file, really). You might still consider using UDP sockets.

---

### Post by Hexorg on 2009-08-15
ok, I was thinking about the problem more and i got into a dead end... both named pipes and sockets would freeze the program until something is written into them, while my program does something every second, so I'd have to make a separate thread for the sockets with fork(); but then how will i be able to send the command from the sockets thread to the every_second_loop of my main program?

---

### Post by Wim Sturkenboom on 2009-08-16
There are blocking sockets and non-blocking sockets. In your case you would use the latter; a read from them will not block but return something indicating that there is or is not data available. It's a while ago that I did socket programming. A possible disavantage is that you might put it in an endless loop and wasting all your processing power.

You can look into *select* and *poll*. They will block till something has happened on a file descriptor (socket, stdin, serial port etc).

And forking is not the same as threading.

---

### Post by Wim Sturkenboom on 2009-08-16
duplicate of above; sorry

---

### Post by Hexorg on 2009-08-16
ok, thank you. I'm currently reading a tutorial I found about threads, seems like one more thread with mutex should do the trick :)

Thank you.

For everyone else who tries to get in such topic - i'm posting my little program, that writes current time in a file every second in one thread, and gets commands in the other:

```

#include <stdio.h>
#include <stdlib.h>
#include <pthread.h>
#include <iostream>
#include <string>
#include <fstream>
#include <ctime>

using namespace std;

pthread_mutex_t mutex1 = PTHREAD_MUTEX_INITIALIZER;
string command;
time_t rawtime;
void *functionC(void *ptr);

int main() {
    int rc1;
    pthread_t thread1;
    ofstream data("data.txt");
    string CurTime;

    if ((rc1=pthread_create(&thread1, NULL, &functionC, NULL))) {  //Create a thread
        cerr << "Thread creation failed\n";
    }

    while (command != "--exit") {  //Unless the second thread will write "--exit", it'll loop in
        time ( &rawtime );
        CurTime = ctime(&rawtime);
        data << CurTime << "\t current command = " << command << '\n';
        data.flush();
        sleep(1);
    }
    return 0;

}

void *functionC(void *ptr) {      // Second thread function
    while (command != "--exit") { //ask for all the commands untill user asks to exit
        /* 
           FROM http://www.yolinux.com/TUTORIALS/LinuxTutorialPosixThreads.html -->
           Mutexes are used to prevent data inconsistencies due to race conditions.
        */
        pthread_mutex_lock(&mutex1); 
        cout << "Please, give a command: "; //be a polite thread :)
        cin >> command;
        pthread_mutex_unlock(&mutex1);
    }
}

```

---

