---
title: "Understanding tty"
date: 2012-07-12
forum: New to Ubuntu
---

### Post by andrewcole50 on 2012-07-12
Hello,

Still new to Ubuntu and I was pointed to bumblebee's github to report a bug. I'm supposed to access the logs through tty for those guys but I'm kind of lost. I can access the ttys and get back to the GUI but I don't know what they are or how to save the logs. I've tried looking on google and through here but I haven't found an explanation that makes sense to me or is complete. So what are they and how do I save logs?

---

### Post by drmrgd on 2012-07-12
Maybe way more information than you need, but here is a nice little write up describing and demystifying the TTY:

[http://www.linusakesson.net/programming/tty/index.php](http://www.linusakesson.net/programming/tty/index.php)

However, for your sake, I think you can just open a Terminal window and copy / paste the portions of the log files you need.  Alternatively, you could probably get those logs by navigating to them with Nautilus.

I might be assuming too much, here, though as I don't know what software you're trying to file a bug report on, and I don't know what log files you're looking for.

---

### Post by richpri on 2012-07-12
In the old days [the old timer said] all text terminals were referred to as TTY terminals. In 1968 [at Bell Labs] my terminal actually was a physical TTY terminal.  Talk about slow!

---

### Post by andrewcole50 on 2012-07-12
Wow that's an interesting article! I don't have time to read it all at the moment but i skimmed for what I think I need. I didn't see or understand what I needed for my particular issue. I'm trying to report a bug for bumblebee and here is a link to the report:
 [https://github.com/Bumblebee-Project/Bumblebee/issues/198](https://github.com/Bumblebee-Project/Bumblebee/issues/198)


I figured this forum would be a more appropriate place to ask how to access the logs than in the bug report.

---

### Post by bab1 on 2012-07-12
> **andrewcole50 said:**
> Wow that's an interesting article! I don't have time to read it all at the moment but i skimmed for what I think I need. I didn't see or understand what I needed for my particular issue. I'm trying to report a bug for bumblebee and here is a link to the report:
 [https://github.com/Bumblebee-Project/Bumblebee/issues/198](https://github.com/Bumblebee-Project/Bumblebee/issues/198)


I figured this forum would be a more appropriate place to ask how to access the logs than in the bug report.
The TTY is now represented by a pseudo TTY (the terminal) in a GUI environment (your desktop).  Just open a terminal session and do this ```
tail /var/log/Xorg.0.log 

or 

tail /var/log/kern.log 

or 

tail /var/log/syslog 
```

All the logs are at /var/log in a Debian/Ubuntu system.

To copy the log you can do this```
cat /var/log/Xorg.0.log > xorg.0.log
```
...this will put a file in your home directory called xorg.0.log

You might want to learn how to work from the command line (CLI aka the terminal) if you are going to use Linux more than just casually.

---

### Post by andrewcole50 on 2012-07-12
Ah thank you very much! Hopefully this is what the guys at Bumblebee are looking for. 

I am currently learning as much as I can about Ubuntu and Linux in general (including the terminal) because a handful of my coworkers and I are seriously considering implementing Ubuntu as the primary OS for the pc's at work. So I need to learn as much as I can about it!

Thank you!

---

### Post by Lekensteyn on 2012-07-13
> **bab1 said:**
> To copy the log you can do this```
cat /var/log/Xorg.0.log > xorg.0.log
```...this will put a file in your home directory called xorg.0.log.

Copying without using redirection can also be done with:
```
cp /var/log/Xorg.0.log xorg.0.log
```

Unless you change the current working directory (which can be shown by executing the "pwd" command, "Print Working Directory") using "cd" ("Change Directory"), the file will then be put in your home directory.

---

