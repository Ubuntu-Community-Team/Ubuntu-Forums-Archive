---
title: "readonly ext3 filesystem"
date: 2008-08-03
forum: New to Ubuntu
---

### Post by augustm on 2008-08-03
hello there,

i hope you can help me out at that issue:
iam trying to install ubuntu 8.04 as a dualboot system next to winxp at a ibm thinkpad R60.
after any installation from that live-cd-mode, login and ubuntu work just fine, except there are no write permissions at / ,ext3, the only partition with swap.
fstab looks fine (.. error=remount-ro 0 1 ..)

an installation without live-cd, "just-installation-mode" cant finish due to a missing "retry" button when I/O-problems occur.
(didnt work with 3 different cds)
any suggestions or hints? 
thanks in advance

---

### Post by linfidel on 2008-08-03
> **augustm said:**
> hello there,

i hope you can help me out at that issue:
iam trying to install ubuntu 8.04 as a dualboot system next to winxp at a ibm thinkpad R60.
after any installation from that live-cd-mode, login and ubuntu work just fine, except there are no write permissions at / ,ext3, the only partition with swap.
fstab looks fine (.. error=remount-ro 0 1 ..)

an installation without live-cd, "just-installation-mode" cant finish due to a missing "retry" button when I/O-problems occur.
(didnt work with 3 different cds)
any suggestions or hints? 
thanks in advance
Why do you think you should have write permission for the root?  Normally, you will only have write permission to your home directory and its subdirectories.  If you need to write to anything else, you need to be root (like windows administrator), either by using "sudo" or "gksudo" from the command line (or "su").

Perhaps I'm not understanding your problem correctly?

Sorry, I don't really understand your 2nd question.  If you're having I/O problems, perhaps the lack of a retry button is not really the source of your problems.

---

### Post by augustm on 2008-08-03
sorry for not being exactly.
with no "write-permissions" i ment the whole tree of /, so that even at my desktop i havent any permissions do create documents.

well, thats the main problem, i have no idea why my harddisk is mounted read-only (mount point is / )..with my fstab-option this should only be the case, when there are errors while mounting..
but i dont know where to find logs or which tools to use to check my system.

the second thing - the installation from cd
there are 2 modes: 
1) start live-session and press the installation button at desktop
2) install directly

when read-problems occur at 1) there is a retry-button and by pressing it mostly fixes the i/o-error

read-problems at 2) lead to an abortion of the installation (missing retry-button :) )

so my installation is from mode1) - so maybe the error occurs because it was installed from live-cd? i have no idea - and thanks for responding.

---

### Post by kahlil88 on 2008-08-03
That's very strange, but the following commands (in a terminal) should set you straight:
```
sudo chown **username** -Rv ~
sudo chmod 644 -Rv ~
```

---

### Post by linfidel on 2008-08-04
> **kahlil88 said:**
> That's very strange, but the following commands (in a terminal) should set you straight:
```
sudo chown **username** -Rv ~
sudo chmod 644 -Rv ~
```
That might not be a good idea.  That makes all files unable to execute.  And he will not be able to access any subdirectories, since they need executable mode.

---

### Post by perlluver on 2008-08-04
Sounds like you have a bad CD.  Run a check on that disk.

---

### Post by linfidel on 2008-08-04
> **augustm said:**
> sorry for not being exactly.
with no "write-permissions" i ment the whole tree of /, so that even at my desktop i havent any permissions do create documents.

well, thats the main problem, i have no idea why my harddisk is mounted read-only (mount point is / )..with my fstab-option this should only be the case, when there are errors while mounting..
but i dont know where to find logs or which tools to use to check my system.

the second thing - the installation from cd
there are 2 modes: 
1) start live-session and press the installation button at desktop
2) install directly

when read-problems occur at 1) there is a retry-button and by pressing it mostly fixes the i/o-error

read-problems at 2) lead to an abortion of the installation (missing retry-button :) )

so my installation is from mode1) - so maybe the error occurs because it was installed from live-cd? i have no idea - and thanks for responding.I see, although I don't understand how the system could run if it can't write to your home directory.  At the risk of offending, are you sure you removed the CD when you booted?  Obviously, when booting from CD, everything would be Read/only.  

Installing from CD is no problem - I've done it that way, and it works fine.

It may be that the errors you mentioned have something to do with this.  If there are errors, it remounts as readonly.

Sorry, I don't have any better ideas right now.

---

### Post by augustm on 2008-08-04
the chown-thing seems not to be a good way for fixing or working around my problem, but thanks.
i tried 3 different cds (one worked fine on a different R60) and as well removed the cd after installation ;)

maybe its just badluck, but 4 times the same problem?

you say 
> If there are errors, it remounts as readonly.
what kind of errors are these? those to the filesystem(ext3) or harddisk-errors?

---

### Post by linfidel on 2008-08-04
> **augustm said:**
> the chown-thing seems not to be a good way for fixing or working around my problem, but thanks.
i tried 3 different cds (one worked fine on a different R60) and as well removed the cd after installation ;)

maybe its just badluck, but 4 times the same problem?

you say 

what kind of errors are these? those to the filesystem(ext3) or harddisk-errors?
I agree with the chown/chmod accessment - it's never a good idea to globally change things like that.

The remount ro feature happens when the disk reports errors.  I don't know the details, though.  It could be some problem with the Thinkpad compatibility, or possibly even a bad drive.  Perhaps something here might be useful:  [http://www.thinkwiki.org/wiki/Problems_with_SATA_and_Linux](http://www.thinkwiki.org/wiki/Problems_with_SATA_and_Linux)

You might get some information from the startup log, which I think you can get to from the menu, in the Administrative tools section (I'm not at my system now).

Another idea is to try the gutsy version.  I know someone with a Thinkpad that has problems with Hardy but not Gutsy for some reason.

Sorry I can't think of any better solutions.

---

### Post by augustm on 2008-08-06
well, after running a lot of tests and installations i can say, hardy has been installed successfully and the problem detected. 

after the installation there are 95 updates to be installed and if i do so, the read-problem occurs immediately, because linux-restricted-modules.deb cant delete a temporary file after the installation in /lib/linux-restriced-??-generic?/

If i install every other update except these two, everything works just fine.

any suggestions?
and thanks again.

---

