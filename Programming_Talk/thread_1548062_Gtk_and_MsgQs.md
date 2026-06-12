---
title: "Gtk and MsgQs"
date: 2010-08-07
forum: Programming Talk
---

### Post by bcz on 2010-08-07
I have a multiUser database.  Basically a record locking filehandler which allows multiple programs to read and write to ISAM files

The programs communicate using SYSV message Qs, shared memory segments and semaphores.

Using standard C programs all works fine

If I use Gtk2 in the application, then at the first "msgrcv" call which normally blocks waiting for a response from the database, I get a "permission denied" failure from the perror() call below

My question is "Do Gtk2 and MsgQs work together".  Also with semaphores and shared memory

Code snippet follows

while (active) {
    //printf("getwork %d\n",msgid); 
    if (msgrcv(msgid,&buff,7,(long)msgid+1,0)>=0) {
      //printf("msgrcv id %d rtyp %d\n",msgid,(int)buff.rtype);
      if (buff.rtype==1) {
        wrkptr[0]=0;        /* set no work present */
        dowork(wrkptr);
        if (wrkptr[0]!=0) active=0;
        }
      else printf("Invalid msg type %c\n",buff.rtype);
      }else{perror("getWork failure"); exit(20);}

Any thoughts appreciated

Rgds to all

BillC

---

### Post by bcz on 2010-08-13
They work together fine.

However it seems that code which functions fine in Xenix 286 and SCO 386 openserver, originally written about 1985, and still in use today at multiple sites requires source code changes to work properly in 2010 Linux systems.  Possibly the API has changed in the last 25 years.  Somehow it functioned without apparent problems until I used it with GTK.

Rgds Bill

---

### Post by dwhitney67 on 2010-08-13
I haven't a clue from the little (and incomplete) code you posted why you are getting a failure.

Nevertheless, I took a little time to write a small little program to demonstrate the usage of the sizeof() operator.

You should compile this program and run it, and then ask yourself why you chose to hard-code the number 7 as the size of the data you expect to receive from the message queue.

```

#include <sys/types.h>
#include <sys/ipc.h>
#include <sys/msg.h>
#include <stdio.h>

int main(void)
{
   printf("%u\n", sizeof(struct msgbuf));
   return 0;
}

```

P.S.  In the future, post code within CODE tags.

---

### Post by bcz on 2010-08-15
Thanks, DWhitney67, for your reply.  Yes sizeof() could be used here.

However as I understand it, the last field of the "msgbuf" is char[] to allow for varying length messages...  so in most cases it is necessary to code an application specific length

The API has changed as "shorts" have become "ints".  Possibly there have been other API changes.  Code as per current documentation, and it works.  What originally worked fine with SCO Unix appears to randomly fail with Linux, so the problems I saw when I used GTK application code were not related to GTK.  Likely the old code should never have worked, but SCO handled it in such a manner that it worked 100%.


How do I use "code blocks".  I notice others using this feature, but the intuitiveness of it escapes me.  Am using Firefox 3.6.8 under Ubunto 9.04 on this system

Rgds Bill

---

