---
title: "root access in .profile"
date: 2011-09-26
forum: New to Ubuntu
---

### Post by Chiel92 on 2011-09-26
Hey,

I want to obtain root access in my .profile. Just typing sudo in front of a command doesn't seem to work. Not in a gnome-session. In a terminal I am asked for the root password. I tried with 'shutdown' command. I just want to get root access within .profile without having to type a password. And I need it in gnome-sessions.

Thanks for any help!

---

### Post by Lisiano on 2011-09-26
Why do you wish to do this?
Maybe using ```
gksudo
``` instead will work better since then it will prompt you.

---

### Post by Chiel92 on 2011-09-26
> **Lisiano said:**
> Why do you wish to do this?
Maybe using ```
gksudo
``` instead will work better since then it will prompt you.

It doesnt seem to work when I re-login. Nothing happens. No prompt and no shutdown.

---

### Post by Lisiano on 2011-09-26
Maybe instead of directly appending it to gnome-sessions try appending it to Startup Applications? Also to use shutdown, you need to specify what to do, else it will just bring it down to single-user mode (Runlevel 1) AKA, recovery mode.
```
sudo shutdown -h now
```
This will turn off your PC the second you type your password correctly.

---

### Post by ajgreeny on 2011-09-26
I can not understand what you are trying to do, but if you want to instantly shutdown your computer with a click, or double click, make a desktop launcher to an "Application in terminal" and in the command box type ```
dbus-send --system --print-reply --dest=org.freedesktop.Hal /org/freedesktop/Hal/devices/computer org.freedesktop.Hal.Device.SystemPowerManagement.Shutdown
```  When you click or double click on that the computer will shutdown with no questions asked, no password needed.

If I have misunderstood you, just ignore all this.

---

### Post by e79 on 2011-09-26
or you could use

```
sudo shutdown -h -P now
```

---

### Post by ajgreeny on 2011-09-26
> **Chiel92 said:**
> Hey,

I want to obtain root access in my .profile. Just typing sudo in front of a command doesn't seem to work. Not in a gnome-session. In a terminal I am asked for the root password. I tried with 'shutdown' command. I just want to get root access within .profile without having to type a password. And I need it in gnome-sessions.

Thanks for any help!
I have read and re-read your post, and I now begin to think that what you are asking about is to have root permissions to be able to do anything and not have to use your password, ever.  Am I correct about that?

**If so I would very strongly advise against it.**

I expect that you may now reply that the computer is yours, and you are the only one who uses it, and thereis no problem with needing no password, but nevertheless, without the password requirement it is very easy to inadvertently do something with a click of the mouse, or an errant terminal command, that completely kills your system.  Why do you feel you need this, if I am correct about your original question?

If you insist on doing so, it is easy to do, but I will not add a link to how it is done here, but will await your reply.

---

### Post by Chiel92 on 2011-09-26
> **ajgreeny said:**
> I have read and re-read your post, and I now begin to think that what you are asking about is to have root permissions to be able to do anything and not have to use your password, ever.  Am I correct about that?

**If so I would very strongly advise against it.**

I expect that you may now reply that the computer is yours, and you are the only one who uses it, and thereis no problem with needing no password, but nevertheless, without the password requirement it is very easy to inadvertently do something with a click of the mouse, or an errant terminal command, that completely kills your system.  Why do you feel you need this, if I am correct about your original question?

If you insist on doing so, it is easy to do, but I will not add a link to how it is done here, but will await your reply.

Indeed, the point is that I want to do stuff as root in files like .profile. The shutdown command is an example that passed by in a different thread, in which I came upon this problem.
(It concerns [http://ubuntuforums.org/showthread.php?t=1849002](http://ubuntuforums.org/showthread.php?t=1849002) by the way, if you're interested)

---

### Post by ajgreeny on 2011-09-27
> **Chiel92 said:**
> Indeed, the point is that I want to do stuff as root in files like .profile. The shutdown command is an example that passed by in a different thread, in which I came upon this problem.
(It concerns [http://ubuntuforums.org/showthread.php?t=1849002](http://ubuntuforums.org/showthread.php?t=1849002) by the way, if you're interested)
OK, so use ```
sudo nano /etc/skel/.profile
``` or ```
gksudo gedit /etc/skel/.profile 
``` if you want to use the GI text editor, enter your password, and you will be able to edit that file and save it with your temporarily raised privileges, if that is the one you mean.

There is no need to remove password requirements completely just to edit a root owned system file such as that.

See Root-sudo in my signature for all the details.

---

### Post by Chiel92 on 2011-09-27
> **ajgreeny said:**
> OK, so use ```
sudo nano /etc/skel/.profile
``` or ```
gksudo gedit /etc/skel/.profile 
``` if you want to use the GI text editor, enter your password, and you will be able to edit that file and save it with your temporarily raised privileges, if that is the one you mean.

There is no need to remove password requirements completely just to edit a root owned system file such as that.

See Root-sudo in my signature for all the details.

I mean that I want things to be done as root in the execution of .profile. Not editing them as root. Sorry if I was not clear enough.

The problem is that appending e.g. "sudo shutdown -h +30" to the end of .profile doesnt seem to work.

---

### Post by Lisiano on 2011-09-27
I think I get it now. You can't do that though. You could set it so that certain commands can be run by anyone without a password or set it that only you can run that command but passwordless. Use this```
export EDITOR=nano
sudo visudo
```You can omit the export command if you want to use Vi.

More on how to do it here
 [https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)

---

### Post by Chiel92 on 2011-09-27
> **Lisiano said:**
> I think I get it now. You can't do that though. You could set it so that certain commands can be run by anyone without a password or set it that only you can run that command but passwordless. Use this```
export EDITOR=nano
sudo visudo
```You can omit the export command if you want to use Vi.

More on how to do it here
 [https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)
Thanks for pointing that out! 
So it is not possible to run any sudoer from within .profile, without modding the sudoers file? I didn't expect that.
Thanks again.

---

