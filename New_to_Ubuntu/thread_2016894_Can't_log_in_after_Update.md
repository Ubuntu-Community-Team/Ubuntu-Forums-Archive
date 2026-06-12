---
title: "Can't log in after Update"
date: 2012-07-04
forum: New to Ubuntu
---

### Post by DeanM1134 on 2012-07-04
I'm somewhat new to ubuntu and recently started using 12.04, installed with Wubi and dual booting along Windows 7. After a recent update (about a week ago) I can no longer log into Ubuntu. Before the update I got a login screen [like this]("http://1.bp.blogspot.com/-WE3KdvhtQCY/T5ZmI4TyDpI/AAAAAAAAIqc/BuD1Ehsk9XE/s1600/ubuntu12.04-login-screen.png")
But after the update all I got is a black screen that says "Ubuntu 12.04 login ttyl" (something like that) that asks for my log in and then my password. That's the ONLY information on the screen and it on't accept ANY of my login information.  I'm sorry for the long post, but I really need the help with it. If any system information is needed i'll happily oblige.
Ubuntu 12.04 on a 64bit AMD processor

---

### Post by anewguy on 2012-07-04
It sounds like a video driver problem.  When you get the terminal window for a text loging, you should be able to type in your userid and press enter, then type your password (it won't show on the screen) and press enter, and it should log you in.  Please post back whether that works or not (couldn't tell from your initial post if you perhaps stopped when your password didn't show on the screen).

---

### Post by DeanM1134 on 2012-07-04
I did try that, I realized that the password just didn't show up. It won't accept my login information, including the original username and password I used before the update. I've tried Owner, my name, Admin, and Administrator. If it is a video crad problem how would I fix that? It worked before, but only after I downloaded the correct driver for it from the update manager.

---

### Post by DeanM1134 on 2012-07-04
Bump out of desperation. Not sure if it's necessary but whatever

---

### Post by bcbc on 2012-07-04
Boot in recovery mode:
1. Select Ubuntu
2. Immediately hold down the Shift key
3. Select second entry on grub menu that appears
4. Drop to a administrator command prompt
5. Find your username
```
ls /home
```
Wubi has a weird setup that uses the Windows account name as the display name, and so it's possible that you are not aware of your actual username, especially if you've never done a non-graphical login before. That should allow you to login using the other method.
Also, check the space - often the graphical logon will fail if you're short on space.
```
df -h
```
Look for the first line of output (for /dev/loop0) - that's your Wubi virtual disk. You'll need upwards of 500MB free space for a functional system.
6. Hit exit to return to the recovery menu

I don't now what else you can try... it really depends on what the problem is. I suppose you could check the logs to see if there is some other issue.
7. Resume normal boot
8. ??

Feedback with what you find.

PS you can also recover data from the virtual disk (\ubuntu\disks\root.disk) from Windows  using [http://ext2read.blogspot.ca/](http://ext2read.blogspot.ca/) and then do a normal dual boot. But it's probably a good idea to figure out what went wrong because it doesn't sound like a wubi-specific issue.

---

