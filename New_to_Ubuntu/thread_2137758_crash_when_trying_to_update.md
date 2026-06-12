---
title: "crash when trying to update"
date: 2013-04-21
forum: New to Ubuntu
---

### Post by zmike1 on 2013-04-21
Running a Dell Inspiron 6400,  Ubuntu 12.04 LTS generally favorable except when things change...

My "update manager" (using LXDE) shows I have 20 updates to apply... when I apply them via GUI, it crashes with the message:

Dpkg was interrupted, you must manually run
'Sudo dpkg - -configure -a ' to correct the problem

Sometimes it just crashes with a screen of "[ 101.684059]  [,c1577214.] syscall_call+0x7/oxb   " gibberish

Fine.  
I run "Sudo dpkg - -configure -a" in terminal which runs for a while and finally gives: 

"Segmentation fault"

the computer otherwise seems to run fine but I can't upgrade/update to address my wifi problem...

Any advice on how to troubleshoot this?

---

### Post by pqwoerituytrueiwoq on 2013-04-21
the data you see at a crash looks like dmesg output
i assume since the command worked, as in tried to run means you typed sudo with a lower case s, you posted it as a capital s

i am guessing it crashed while updating the one program that is required to run that command, you may be able to fix it from a live usb and running the command after chroot-ing into the system, i am not exactly sure how that works, but worth googling, it also may help someone who knows more about this type or issue get a idea

---

### Post by zmike1 on 2013-04-21
thanks for the info.  (Yes, I did use a lowercase s for sudo - - my word processor automatically capitalized & I didn't change)

I'll look into chroot ' ing  whatever that might bring.  I am just a novice.  thanks.  Still open to more advice, options, google search ideas, etc.
Thanks.

---

