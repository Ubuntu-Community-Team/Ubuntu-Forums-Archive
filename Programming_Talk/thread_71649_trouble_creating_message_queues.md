---
title: "trouble creating message queues"
date: 2005-10-04
forum: Programming Talk
---

### Post by blipmode on 2005-10-04
Hi,
I'm trying to execute someone else's code (multithreaded) in Ubuntu 5.04.  (I'm a brand-newbie, so it's been a journey to this point).
Code compiles ok with gcc
The makefile has some unfamiliar (to me) stuff:
chown root testcode
chgrp root testcode
chmod 4755 testcode
(I included this because not sure if it indicates a privilege problem or what?)
The Problem:
Program fails early in execution because call to msgget fails, error = No space left on disk.
I am running in gnome terminal as root.  Not sure how to proceed, any suggestions?

---

### Post by blipmode on 2005-10-04
This test program works:
int main()
{
key_t key;
int msgq_id;
int idx;
for(idx=1; idx<100; idx++)
{
key = ftok(".",idx);
if((msgq_id == msgget(key, IPC_CREAT | 0600)) == -1)
printf("Can't create message queue %d\n", idx);      // never gets here
}
printf("Complete\n");
return 0;
}


But this snippet from the "testcode" program fails:
key = ftok(".", token);    // token is 33
if((msgq_id = msgget(key, IPC_CREAT | 0600)) == -1)
{
perror("Can't create message queue");      // always gets here
exit();
}
The error is "No space left on device".

I'm not out of HD space or RAM, so it's a mystery to me what space I'm running out of.  Any ideas?

---

### Post by blipmode on 2005-10-05
Not to worry, finally figured it out.

msgget fails if the key value is greater than 0x7fffffff, something like that.

---

### Post by beatle1637 on 2008-11-09
hello why is it so hard ?
I am very new to all this, where do you get to create a thread ? 
i have a problem with ubuntu its the error 15 when trying to boot from hdd after reading for an hour i think i need to reinstall grub  
Why ? its a fresh install ? why is this such an issue ? why doesnt the ubuntu 8.1 do this ?? i thought this was getting easier, the more i read the more confusing it gets ? I am beginning to think windows isnt that bad. I am just getting sick of spending hours trying to find a solution when it should work right from the start (grub boot loader sudo this mkdir that what a crock very confusing)

---

