---
title: "Ubuntu 12.04 Start up errors"
date: 2012-12-01
forum: New to Ubuntu
---

### Post by Gonda on 2012-12-01
Hi, 

I keep receiving error messages when i start up. 
When i start in recovery mode and try fix errors I receive the following:

1. The one at the moment is: mountall: Filesystem has errors:/

2. The other problem is a package issue:

Please could someone advise what I should do?

My pc info: nvidia ge force 7300gt
32 bit res
intel (R) core (TM) 2 cpu
6300@1.86 GHz
1.86 ghz, 2gb ram
xp/ubuntu partitioned

---

### Post by Bashing-om on 2012-12-01
Gonda; Hi !

Let's see how serious of a problem the file system has. Force a file system check on the next boot:
execute the following terminal commands (copy and paste into terminal): one command line at a time:
```
sudo touch /forcefsck
sudo shutdown -r now

```Be advised the use of "sudo"grants admin privileges requiring your password, will get no response to the screen (security reasons).

Will have to repair the file system before repairing the package manager (separate issue?, nother thread).
[INDENT][INDENT]just try'n to help

[/INDENT][/INDENT]

---

### Post by monkeybrain2012 on 2012-12-01
Before you try to fix anything, do you actually experience any problem or just an error message? It could be a false alarm from Apport. 

[http://askubuntu.com/questions/142016/sorry-ubuntu-12-04-has-experienced-an-internal-error](http://askubuntu.com/questions/142016/sorry-ubuntu-12-04-has-experienced-an-internal-error)

I used to be hit by these "internal error" messages every hour, I have turned off Apport and never had any problem since, it seems that the only thing that is constantly experiencing internal error is Apport itself.Last week someone reported on this forum that he actually got an Apport internal error message  about Apport itself.:)

---

### Post by Gonda on 2012-12-01
Hi,

thanks - will do so and post back here.  Will now need to open another post as another even more serious issue has developed. Not having a good pc day. I hope I'm doing the right thing by starting another thread as it is a totally different problem. Apologies in advance if i'm wrong.

---

### Post by Bucky Ball on 2012-12-01
> **Gonda said:**
> I hope I'm doing the right thing by starting another thread as it is a totally different problem. 

Starting a new thread is ***exactly*** what you should do as it is a totally different and unrelated (possibly) problem. Please use a descriptive thread title and post in the appropriate sub-forum. This will increase your chances of getting help. Good luck. ;)

---

### Post by Gonda on 2012-12-02
Thanks for that Bucky.

I have also managed to get a screen shot of the package that i think (may be wrong of course) that is causing my start up error.

So before I try and do the other instructions you all sent, can you advise me what to do with this error?

---

### Post by Bucky Ball on 2012-12-02
That looks like it might be having a problem with a USB printer connection. Have you a printer plugged in USB? If so, unplug and reboot and see if that takes the error away. If it does, there are possibly drivers missing for the device and that is what it is squealing about; doesn't recognise the device at boot.

---

