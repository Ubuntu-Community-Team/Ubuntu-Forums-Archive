---
title: "Ubuntu server video problem"
date: 2014-12-26
forum: New to Ubuntu
---

### Post by Ricky_Riccardi on 2014-12-26
I just got done installing Ubuntu server on a dell power edge 400SC.  the install was not as easy as i thought, but upon reboot, i am unable to read the screen!!!!! anyone have any suggestions? I am very new to Ubuntu and i am trying to learn it, but it makes it impossible when the text on the screen is jumpy and unreadable.

---

### Post by TheFu on 2014-12-27
Install openssh-server on the 400SC, then use ssh from any other machine to manage the box.  That is how 99.99999999999% of the UNIX/Linux servers are managed around the world - through ssh from other machines.  Only people at home sit behind the server and type on that screen post install.

If you need ssh to be available over the internet, install fail2ban or denyhosts to block brute force attacks and disable remote password logins - only allow ssh-keys to be used.

---

### Post by Ricky_Riccardi on 2014-12-27
Thanks for the information, but how do i install SSH?
In addition, can i configure the server with ssh after its installed?

---

### Post by sandyd on 2014-12-27
> **Ricky_Riccardi said:**
> Thanks for the information, but how do i install SSH?
In addition, can i configure the server with ssh after its installed?
You can either install it during the installation by selecting "SSH Server" when asked about what software you want on the system, or by running the following command after logging in (im sure you can still log in with the "jumpy text".
```

sudo apt-get install openssh-server
```

You can then use putty on Windows, and the ssh command on mac/linux to access the machine.

Regards,

---

### Post by TheFu on 2014-12-27
> **Ricky_Riccardi said:**
> Thanks for the information, but how do i install SSH?
In addition, can i configure the server with ssh after its installed?

Ah ... you are a true complete beginner.  We all were new at some point. The learning curve is steep, like a new language, but rewarding.

Save yourself many days, weeks, months of frustration by reading a few primers ... like these:
* [http://www.dedoimedo.com/computers/ultimate-linux-guide-for-windows-users.html](http://www.dedoimedo.com/computers/ultimate-linux-guide-for-windows-users.html) - ignore the GUI stuff, you are running a server
* [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php) - free PDF book on Linux - READ the first 100pgs, skim the rest over 2-3 hrs to get a taste of possibilities. The early pgs provide background, set expectations, and help to get-your-mind-right for Linux.
* [http://blog.jdpfu.com/linsysmaint](http://blog.jdpfu.com/linsysmaint) - minimal Ubuntu System maintenance how-to - patch and backup with just a few other minimal things. Ubuntu mostly runs itself, but ... 
* [http://blog.jdpfu.com/2012/02/15/beginning-linux-thought-shift-needed](http://blog.jdpfu.com/2012/02/15/beginning-linux-thought-shift-needed) - learn to think the linux way.

Oh ... and if you want to work on a true console, connect up a terminal with a serial port. However, this is usually beyond someone so new to UNIX systems.  Best to stay with ssh.

There are many other guides to teach Linux. Google searching doesn't work well without some background first. Be cautious copy/pasting commands. That's a good way to trash a system.  Understand what each command does first. Learn the options by reading the manual pages for each command on YOUR system, not the web.  There are different versions of most commands and only the manpages installed on your system will truly reflect the options for the commands installed there.  Most of the major options haven't changed too often, but sometimes ... just sometimes, do change and can screw the uninformed.  Better to just get into the habit now.

Of course, if you have more questions, you can ask on these forums, but it is best to google a tad first and to describe what the end goal is. When I was new, I didn't know the easiest way to a solution and more experienced users helped with ideas, usually 1-3 commands when I thought a new, huge, program was needed.

---

### Post by Ricky_Riccardi on 2014-12-27
Thanks to all for replying. Yes, i am a TOTAL beginner!!!  i wanted a system that i can store my files on and access them from my macbook without having to deal with the issues and problems in windows servers.  I am also dealing with older hardware, so any new version of windows would just bog the system down.

I figured out how to get ssh going on the server side.  when i login from my mac (os x mavericks) i am asked for my password which keeps getting rejected as being incorrect. I seem to have no problem on the console with my password. any thoughts?

---

### Post by sandyd on 2014-12-27
> **Ricky_Riccardi said:**
> Thanks to all for replying. Yes, i am a TOTAL beginner!!!  i wanted a system that i can store my files on and access them from my macbook without having to deal with the issues and problems in windows servers.  I am also dealing with older hardware, so any new version of windows would just bog the system down.

I figured out how to get ssh going on the server side.  when i login from my mac (os x mavericks) i am asked for my password which keeps getting rejected as being incorrect. I seem to have no problem on the console with my password. any thoughts?

Are you logging in using the command
```

ssh user@serveriphere
```

If you do not place user@ in front of serveriphere, ssh will attempt to login to the server with your mac username.

---

