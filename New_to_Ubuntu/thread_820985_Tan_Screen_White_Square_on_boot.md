---
title: "Tan Screen White Square on boot"
date: 2008-06-06
forum: New to Ubuntu
---

### Post by Grahamca on 2008-06-06
Hello,
I am a Ubuntu Newbie using Hardy, and have run into some problems with the desktop similar to others.  This question has been asked before however the solutions that were offered did not solve my problem.  sudo apt-get ubuntu desktop did not get me a functioning desktop

I have a Toshiba Laptop A210,
Was installing the wireless driver using ndswrapper, when i did the reboot i got the white screen in the upper left hand corner of the desktop.

I followed the "gconftool-2 -s -t bool /apps/nautilus/preferences/show_desktop true" command in the terminal. However it will only seem to allow basic functions. I can not seem to connect to the internet with a wire. Eventually I get to a point where the desktop is visible and looks normal, however there is no functionality. I can not even shut down from the desktop using the shut down button on the desktop. I end up powering down with the power switch on the laptop.

I have tried GRUB manager and tried all the restore options and they did not have any effect.

Question: Is this fixable, and if not I can easily reinstall, however i would like to recover a few photos fiiles I have loaded onto the computer. Is there a way to access the photos from terminal and copy them to an external ram drive?

Thanks very much for your help.

Graham

---

### Post by cariboo on 2008-06-06
It looks like somehow your Ubuntu desktop is gone. You could try Ctrl-f1 to get to a console and then login and type:

```
sudo apt-get update && apt-get upgrade
```

This might restore whats missing

JIm

---

### Post by NilsE on 2008-06-06
> **Grahamca said:**
> Hello,

Question: Is there a way to access the photos from terminal and copy them to an external ram drive?
Before you reinstall, if that is necessary, boot from the live cd and access the drive to copy the data somewhere.

---

### Post by Grahamca on 2008-06-07
> **NilsE said:**
> Before you reinstall, if that is necessary, boot from the live cd and access the drive to copy the data somewhere.

I will do that, however I find when i go to the files that are on the hard drive, they are password protected I would suspect from the log in and I can not move them.  Do you know how to get passed this?

Thanks for your help
Graham

---

### Post by Kronie on 2008-06-07
hey guys, i think i got same problem... i just installed ati x600 drivers and after restart, after i login to my account i see plain white screen with the mouse... also, it tries to open some windows on a background because i can see the compiz effect.. right now i am on livecd.. so is there any way to fix it?  dont really want to reinstall ubuntu since it took me couple days to configure it just the way i want it to be T_T

---

### Post by cariboo on 2008-06-07
Just login with your username and password, you'll have to do everything from the command line.

Jim

---

### Post by Kronie on 2008-06-07
and by everything u mean...?

---

### Post by socngill on 2008-06-08
Same problem.  Done a clean reinstall twice now and really don't want to do it a 3rd time! Seems to be graphics card (possibly Compiz?) related as that was the last thing I installed.  On restart get the white screen after log in.  I can hear all the stuff loading up, but no picture except the cursor on a white screen.

I can log in as failsafe and get the terminal but I have no idea what to do from that point.  Any help would be very much appreciated :)

---

### Post by PmDematagoda on 2008-06-08
For those who have the Compiz white screen problem, try this:-
1) Switch to a tty by pressing Ctrl+Alt+F1. Enter your normal user credentials and login.

2) Execute:-
```
metacity --replace
```

3) Switch back by pressing Ctrl+Alt+F7 and see if you can see the desktop now.

Edit:- If that doesn't work, switch back to the tty and execute:-
```
killall compiz.real
```
and see if that fixes it.

---

### Post by socngill on 2008-06-08
> **PmDematagoda said:**
> For those who have the Compiz white screen problem, try this:-
1) Switch to a tty by pressing Ctrl+Alt+F1. Enter your normal user credentials and login.

2) Execute:-
```
metacity --replace
```

3) Switch back by pressing Ctrl+Alt+F7 and see if you can see the desktop now.

Edit:- If that doesn't work, switch back to the tty and execute:-
```
killall compiz.real
```
and see if that fixes it.

Interestingly the matacity part told me I didn't have it installed - so I installed it but made no difference.  However, running the kill command did work and I have my desktop back :) So thanks very much for that.

Does this meantherefore that I can't use Compiz and all the lovely eyecandy?  Probably down to having a ATI graphics card grrr!

---

### Post by sigve on 2008-06-08
you can also choose to login using a gnome safemode session from the login screen and then you can uninstall compiz.

---

