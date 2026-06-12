---
title: "Ubuntu Starts up in Terminal"
date: 2013-11-01
forum: New to Ubuntu
---

### Post by ziig_starD on 2013-11-01
Hi guys, absolute newb, got Ubuntu because I read I could use the graphical interface for everything and would never have to bother with the terminal and memorizing commands. All went good for about a month, I used the computer to watch movies, surf the web, anything I did with my previous Windows computer but without the virusses and bloatware. 

Today however I booted up my computer and I got the black screen with the white letters, asking for my username and password. I gave it, tried alt F7 to go to the visual desktop I'm used to and it just gave me a black screen without anything on it, not even my cursor. I used alt F2 to get back to that MSDos looking interface. I have no idea what I can do and how I can get my familiar desktop back. Any help?

I'm Running Ubuntu 12.04.03 LTS, I'm pretty sure it was shut down correctly every time, I made backups but I have no idea how to access or load them.

---

### Post by protoss96 on 2013-11-01
Try this.

If you prompt is asking for your user and password give it then.

When you are logged in type:
```
startx
```

According to your description may the boot configure file is corrupted.

---

### Post by fantab on 2013-11-01
Try Recovery Mode. 
Use 'dpkg', 'fsck' and 'xfix'  and the other options
[http://unixlab.blogspot.in/2009/08/exploring-ubuntu-recovery-mode.html](http://unixlab.blogspot.in/2009/08/exploring-ubuntu-recovery-mode.html)
[https://wiki.ubuntu.com/RecoveryMode](https://wiki.ubuntu.com/RecoveryMode)

---

### Post by MG&amp;TL on 2013-11-01
Did you run any updates or install any software before this happened? The graphical interface usually fails to start because of software misconfiguration or driver problems.

Something to try is restarting the graphical server. Log in using your username and password (for security reasons, your password won't show up in the terminal), then type this command and enter your password:

```
sudo service lightdm restart
```*

See what happens, then post back any results or errors. Thanks. :-)

*An explanation, word for word:
[LIST]
[*]*sudo* - run any following commands as if you were the root user; the user 'root' (disabled by default in Ubuntu) is a 'superuser'- it can do anything the operating system can, unrestricted by lack of privileges. 
[*]*service* - manipulate 'services' - system programs which run continuously. 
[*]*lightdm* - Light Display Manager. This is the program which handles the display and graphical login. 
[*]*restart* - Restart the lightdm service if it has crashed or stopped. 
[/LIST]

---

### Post by ziig_starD on 2013-11-11
Hi guys, sorry for the late reply.

I did ```
sudo restart now
``` last time before the first answer was posted here and the problem was solved, I started in the usual graphical interface on the next boot. Weird, but problem solved I guessed.

Today upon booting I had the terminal again and the same problem. Tried 
```
sudo service lightdm restart
```
worked great, thanks.

As for what causes the problem, this time my screen wasn't turned on upon booting (it usually is). Could this be the reason? It's just a standard PC monitor, connected with a DVI cable.
[COLOR=#000000][FONT=Ubuntu Mono]
[/FONT][/COLOR]

---

