---
title: "&quot;no processes killed&quot; got when sudo pkill invoked"
date: 2008-06-11
forum: New to Ubuntu
---

### Post by jambalaya on 2008-06-11
Hi.
One of the users turned on amarok, and I wanted to kill it, so I sshd to it as my user, and invoked:
sudo pkill -9 amarok
and got this as a response:
amarok: no process killed

So, I su to the user that runs it:
sudo su amarok_user
and now pkill -9 amarok worked fine

The question is: how is that possible that sudo wasn't able to turn it off? This happens only when amarok is actually playing something, and it doesnt happen when I su to root, and then try to kill it, soe there is something wrong with the sudo command. I thought sudo switches me temporarily to root, but it is somewhat diffrent than root, apparently.
Could someone explain this to me, please?
Thanks.

EDIT: (Of course, I have the root password as I actually am the "admin" ;-) of that machine)

---

### Post by compiledkernel on 2008-06-11
Hmmmm, can you kill via the PID of the offending application with sudo? 

Id do 

ps aux | grep amarok 

find the PID of the application 

sudo kill -9 <PID> 

does that produce the same result?

---

### Post by NilsE on 2008-06-11
I could be wrong but I thought pkill only works at the user level so you would have to be su'd to the user.  kill should work so give it a try.

I also didn't think that pkill accepted the -9 signal but I guess it does based on your experience.

So, you could try

sudo kill -9 PID# where PID# is the PID of the process

or

sudo killall name where name is the name (or wildcard) of the process

Just a side note, sudo gives you root privileges but does not log you into  root.

---

### Post by jambalaya on 2008-06-14
Hi.
Today I wanted to reproduce this error and it worked fine, all of the options. Weird.

---

