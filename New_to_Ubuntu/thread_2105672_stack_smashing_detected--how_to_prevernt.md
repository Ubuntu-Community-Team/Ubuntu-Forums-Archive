---
title: "stack smashing detected--how to prevernt"
date: 2013-01-16
forum: New to Ubuntu
---

### Post by allynm on 2013-01-16
Hello everyone,

I am playing around with system V message queues and have run into a curious situation.  I have a simple c program that makes the appropriate calls to sys v apis and successfully sends a message to a receiver in another terminal.  The code for the sender is:
> 
#include <sys/types.h>
#include <sys/msg.h>
#include <sys/ipc.h>
#include <string.h>

int main (void) {

        key_t ipckey;
        int mq_id;
        struct { long type; char text[100]; } mymsg;

        /* Generate the ipc key */
ipckey = ftok("/tmp/foo", 1);
        printf("My key is %d\n", ipckey);

        /* Set up the message queue */
        mq_id = msgget(ipckey, IPC_CREAT | 0666);
        printf("Message identifier is %d\n", mq_id);
        /* Send a message */
        memset(mymsg.text, 0, 100); /* Clear out the space */[
strcpy(mymsg.text, "Hello, world!");
        mymsg.type = 1;
        msgsnd(mq_id, &mymsg, sizeof(mymsg), 0);
return 0;
}
The receiver code is quite simple. 
> 
#include <sys/types.h>
#include <sys/msg.h>
#include <sys/ipc.h>
#include <string.h>
#include <stdio.h>

int main (void) {

        key_t ipckey;
        int mq_id;
        struct { long type; char text[100]; } mymsg;
        int received;
    mymsg.type=1;
    mymsg.text[0]=0;
        /* Generate the ipc key */
        ipckey = ftok("/tmp/foo", 1);
        printf("My key is %d\n", ipckey);

        /* Set up the message queue */
        mq_id = msgget(ipckey, 0);
        printf("Message identifier is %d\n", mq_id);

        received = msgrcv(mq_id, &mymsg, sizeof(mymsg), 0, 0);
    
        printf("%s (%d)\n", mymsg.text, received);
    msgctl(mq_id, IPC_RMID, 0);
return 0;
}
If I compile the receiver code using GCC -c sysvrcvr.c and then link with GCC -o sysrcvr sysrcvr.o the program receives messages sent by the sender and then emits a "smashing stack detected" message and aborts.

I can get around this behavior if I compile with the  -fno-stack-protector switch enabled.  OK, fine.

But, what is it about the 104 byte msg buffer that I'm sending which is triggering the stack protector.  The receiver code is fully aware of the size of the 104 byte buffer that is sent.

Thanks,
Mark Allyn aka allynm

---

### Post by squakie on 2013-01-16
Try using an IDE like CodeBlocks - it has a built in debugger.  You can put your code in there, set breakpoints, etc., and step into the code to see where this is happening.

My experience has been that stack smashing has occured  when I walked past the end of a variable.  I only took a brief look at your code, but perhaps you need to initialize mymsg.txt after the memset to nulls so the data you place in there is null terminated.  Also, how are you getting a 104 byte msg on a text that is allocated as 100 bytes?

---

### Post by allynm on 2013-01-16
Hi squakie (Hope this is right; don't have my glasses on....)
 
I'll try the debugger idea.  I use ddd...
 
As for the 104 bytes.  The message struct has two fields;  one is a long int and the other is the message itself with 100 entries.  This is where the 104 comes from.
 
Thanks for helping...
 
Mark aka allynm

---

