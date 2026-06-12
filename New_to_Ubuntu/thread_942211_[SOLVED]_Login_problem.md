---
title: "[SOLVED] Login problem"
date: 2008-10-08
forum: New to Ubuntu
---

### Post by cnoc on 2008-10-08
Cannot get beyond login screen. It will accecept user name but will not accept cursor or script in password box. Username and password are correct - (have checked and reset password in recovery mode). System was working ok prior 2 days - new to linux and first install- on seperate partition with windows. No dought I have changed something I should have left alone re login choices.

---

### Post by Ubuntiac on 2008-10-09
Just boot your computer and go into GRUB (the text menu with a list of operating systems you can boot - you may need to push Esc at the right moment to get to it).

Choose the first option down the list that ends in (Recovery Mode), to boot as the root user. When booting (into the console) has finished, enter:

```
passwd username
```

replacing "username" with, well, your username! You should be asked for a new username which you then enter. Once this is done, type:
```
shutdown -r now
```
to restart. Boot normally, and use the password you entered above to log in.

Hope this helps!

---

### Post by cnoc on 2008-10-09
Thanks for the info which I tried but the problem still persists. Accepts username but I still cant type in password in box - it wont accept curser or any input.

I have retraced my session before the problem started using the live CD. I am almost sure that I checked the "Allow Auto Login " box but did not insert "User Name" associated with that action.
I need to know if I can rectify this from recovery/root user mode?.

---

### Post by Ubuntiac on 2008-10-09
This is a rather ugly method, and I'm sure there are people here who can offer you a much better way, however.... until they do, you could try this:

1. Boot into recovery mode.
2. at recovery mode type startx
3. Your system will boot as root without asking for any password. From here you can most likely go in and switch off autologin.

BEWARE: Running your system as root is generally a *very bad idea*. I would avoid doing anything you don't have to to get your system working, and log out back into a normal user as soon as possible. There is a chance that some programs (such as Nautilus / Dolphin) may even have permission problems later if you open them while still running as root. You're essentially overriding your systems basic security which let's you accidentally screw things up much more easily.

Like I said, get in, fix the problem, get out asap.


If anyone is reading this with a better idea, now's the time to share it!

---

### Post by Big_Kahunaca on 2008-10-09
> **Ubuntiac said:**
> BEWARE: Running your system as root is generally a *very bad idea*.

Apparently you haven't read this article...

[http://www.garyshood.com/root/]("http://www.garyshood.com/root/")

:)

---

### Post by Ubuntiac on 2008-10-09
Cool!

Now I'm *always* going to run as root! It's awesome! Besides, rm -rf / isn't really *that* dangerous. See!:

> ~?rm-rf /
~>Deleting /
~>ls

command not found.
... aw cr*p! Why is my syste..fiysdiu nsdud diid dii
command not found.
command not found.
comman.. sfgsdg

error.

post terminated.

---

### Post by Ubuntiac on 2008-10-09
...

---

### Post by bodhi.zazen on 2008-10-09
> **cnoc said:**
> Cannot get beyond login screen. It will accecept user name but will not accept cursor or script in password box. Username and password are correct - (have checked and reset password in recovery mode). System was working ok prior 2 days - new to linux and first install- on seperate partition with windows. No dought I have changed something I should have left alone re login choices.

When entering your password, the terminal will not appear to be responding, ie nothing will reflect on the screen as you type your password. This is normal behavior, just type in your password and hit the enter key.

---

### Post by cnoc on 2008-10-10
Thankyou for the info bodhi.zazen (and ubuntiac). Solved the problem that I thought I had. Just crawling my way into the world of ubuntu/linux.

---

### Post by Ubuntiac on 2008-10-10
Would be great to post what fixed it for you for anyone else reading this thread with a similar problem.

Glad you got it worked out! :KS

---

### Post by cnoc on 2008-10-10
Sorry! Advice from bodhi.zazen did the job ie: 

"When entering your password, the terminal will not appear to be responding, ie nothing will reflect on the screen as you type your password. This is normal behavior, just type in your password and hit the enter key." 

After it booted up I added the missing user name and now boots up with no user name or password required. Good for home use and for my wife.

---

