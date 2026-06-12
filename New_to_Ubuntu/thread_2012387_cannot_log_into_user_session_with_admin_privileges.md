---
title: "cannot log into user session with admin privileges"
date: 2012-06-29
forum: New to Ubuntu
---

### Post by emekadavid on 2012-06-29
After I started using this command from my terminal, ```
sudo shutdown –h now
```, hours later I cannot log into the only user session with administrative privileges. At the login screen after booting, after I have inserted my username and password, the screen gives me this message :```
 “Plymouth command failed”
``` and also ```
“disconnected from Plymouth.”
``` 
  I tried logging into my Ubuntu 12.04 desktop through another user session which is standard privileges and then switch to the admin user but Plymouth refuses to allow me access to the system. 
  How do I resolve this problem. I cannot use root without admin privileges. Btw, my the Ubuntu desktop is so annoying that I might have to download the server edition of precise. It keeps giving crash reports, especially after I mounted an ntfs partition where I keep most of the files I use for reference purposes. 
  Help please. And thanks.

---

### Post by Gone fishing on 2012-06-29
I'm sure the shutdown command didn't cause the problem. Did you install a video driver run an update or similar.

Can you login to the admin account using a tty Alt Control F1?

---

### Post by emekadavid on 2012-06-29
> **Gone fishing said:**
> I'm sure the shutdown command didn't cause the problem. Did you install a video driver run an update or similar.

Can you login to the admin account using a tty Alt Control F1?
no driver installation of recent at all. 
opened tty and it worked. does it mean i will be limited to using only tty? 
am a noob and am reading up linux and ubuntu pdf files on the desktop while working with the bash shell. wondering how i will survive with just the tty?
please do help me on that
tanx

---

### Post by emekadavid on 2012-06-30
I created a script that referenced the shell as ```
#!/bin/bash
``` from an old linux textbook while ubuntu precise's documentation, which i am reading from a tty, references it from ```
#!/bin/sh
```. 
I have a peculiar problem of not being able to log onto the graphical mode of ubuntu precise with an admin/system user; normal user can log onto graphical mode. 
see the problem description here:
[http://ubuntuforums.org/showthread.php?t=2012387](http://ubuntuforums.org/showthread.php?t=2012387)
could referencing the wrong shell function be the cause of my system's problem?
solutions needed

---

### Post by MG&amp;TL on 2012-06-30
Nope, running a different shell should have no effect. Particularly as bash is compatible with sh.

On a side note, /bin/bash is preferred to /bin/sh as it has more features.

---

### Post by wildmanne39 on 2012-06-30
Hi, please do not create duplicate threads it dilutes the communities efforts.
Thanks

---

### Post by dodo3773 on 2012-06-30
> **MG&TL said:**
> Nope, running a different shell should have no effect. Particularly as bash is compatible with sh.

On a side note, /bin/bash is preferred to /bin/sh as it has more features.

Not sure about how Ubuntu is doing things nowadays but:

ls -l /bin/sh
```

lrwxrwxrwx 1 root root 4 May 31 04:50 /bin/sh -> bash*

```

I would say compatible is a little bit of an understatement haha.

---

### Post by MG&amp;TL on 2012-06-30
> **dodo3773 said:**
> Not sure about how Ubuntu is doing things nowadays but:

ls -l /bin/sh
```

lrwxrwxrwx 1 root root 4 May 31 04:50 /bin/sh -> bash*

```I would say compatible is a little bit of an understatement haha.

Lol! Oh well, not really a problem then. :)

---

### Post by emekadavid on 2012-07-01
Then why can i not log into my system with the graphical mode. init 5 does not work. when i try to call a gui program i get: ```
X11 initialization failed
``` message. 
i am presently using the tty until i get a hold on this problem. 
tanx

---

### Post by dodo3773 on 2012-07-01
> **emekadavid said:**
> Then why can i not log into my system with the graphical mode. init 5 does not work. when i try to call a gui program i get: ```
X11 initialization failed
``` message. 
i am presently using the tty until i get a hold on this problem. 
tanx

Well first of all trying to load an X11 app or any graphical application without X running is obviously not going to work. How did you get to init 3 in the first place? Through the kernel command line or something? Since earlier you said plymouth was giving you errors why don't you just try disabling plymouth. I am sure there are probably various ways to do this. Or maybe after you log in as your normal user from the command line you can just type "startx" and then look at your Xorg log if it fails from there.

Edit: You know what just post your Xorg log for us. Or look for errors there. It should be somewhere like -> "/var/log/Xorg.0.log"

---

### Post by emekadavid on 2012-07-02
> **dodo3773 said:**
> Well first of all trying to load an X11 app or any graphical application without X running is obviously not going to work. How did you get to init 3 in the first place? Through the kernel command line or something? Since earlier you said plymouth was giving you errors why don't you just try disabling plymouth. I am sure there are probably various ways to do this. Or maybe after you log in as your normal user from the command line you can just type "startx" and then look at your Xorg log if it fails from there.

Edit: You know what just post your Xorg log for us. Or look for errors there. It should be somewhere like -> "/var/log/Xorg.0.log"
1. i disabled plymouth and updated grub, but the problem persists. 
2. ran "startx" command from the cli as root but i received "X server failure error".
3. so i decided to send the Xorg.0.log file. find it attached.

---

### Post by dodo3773 on 2012-07-02
> **emekadavid said:**
> 1. i disabled plymouth and updated grub, but the problem persists. 
2. ran "startx" command from the cli as root but i received "X server failure error".
3. so i decided to send the Xorg.0.log file. find it attached.

I said "log in as your normal user" and startx. Not as root. Unless your normal user is root I guess. But, I kind of doubt it. Also, did you create an xorg.conf file? Do you have one on your system? Probably somewhere like "/etc/X11/xorg.conf". Also, are you sure that is your entire Xorg log? Seems like some of it is missing. Please just post it in code tags next time too or at least on a text pasting website. Not sure how many people would want to download and view a pdf you created. I did. But I may not have your answer either.

---

### Post by emekadavid on 2012-07-03
> **dodo3773 said:**
> I said "log in as your normal user" and startx. Not as root. Unless your normal user is root I guess. But, I kind of doubt it. Also, did you create an xorg.conf file? Do you have one on your system? Probably somewhere like "/etc/X11/xorg.conf". Also, are you sure that is your entire Xorg log? Seems like some of it is missing. Please just post it in code tags next time too or at least on a text pasting website. Not sure how many people would want to download and view a pdf you created. I did. But I may not have your answer either.
normal user, admin, startx failed. 
xorg.conf does not exist. searched with locate, searched on xorg.conf.d directory, does not exist on the system. 
viewing the downloaded pdf is better than pasting the code tags. imagine how many pages it would take. i read through it myself. 
hope this problem can be resolved so i can use my system again. 
thanks

---

### Post by steeldriver on 2012-07-03
if you can log in to a regular desktop session as another (non privileged) user then I don´t think there´s anything wrong with your xserver setup or graphics driver

more likely there is something specific in your user config that is crashing your xsession (or preventing it from starting) - you could look in ~/.xsession-errors to see if you can figure out what but frankly it´s going to be hard to troubleshoot something like this - you may be better off creating a new user account from your tty login (with sudo group membership) and copying over your personal files - don´t copy any ´dot´ files which may propagate the error

---

### Post by emekadavid on 2012-07-04
> **steeldriver said:**
> if you can log in to a regular desktop session as another (non privileged) user then I don´t think there´s anything wrong with your xserver setup or graphics driver

more likely there is something specific in your user config that is crashing your xsession (or preventing it from starting) - you could look in ~/.xsession-errors to see if you can figure out what but frankly it´s going to be hard to troubleshoot something like this - you may be better off creating a new user account from your tty login (with sudo group membership) and copying over your personal files - don´t copy any ´dot´ files which may propagate the error
that is the most natural thing to do in solving that problem, which i have but a new user account with sudo group does not pass through plymouth. that is, i am constrained to use only tty. :popcorn:. am not enjoying it any longer.

---

### Post by steeldriver on 2012-07-04
I don't understand what you mean by "does not pass through plymouth"?? can you post the EXACT error you get please?

are you trying to do this in a virtual terminal (Ctrl-Alt-F1... F6) or at the recovery console?

---

