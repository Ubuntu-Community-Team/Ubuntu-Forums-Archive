---
title: "[SOLVED] Start VNC automatically in Kubuntu"
date: 2008-06-12
forum: New to Ubuntu
---

### Post by mwjones on 2008-06-12
I am trying to get VNC (server) to start automatically on my desktop running Kubuntu 8.04.  I need to be able to graphically login without any local intervention.  Our power company is rather inconsistent here, and we lose power fairly frequently.  Another requirement is that I also need to be able to connect from both GNU/Linux and Windows XP.  

[LIST]
[*]The [Hardy - Kubuntuguide]("http://kubuntuguide.org/Hardy#VNC") section is close, but requires that the desktop be logged in locally. 
 
[*][This LifeHacker article]("http://lifehacker.com/software/how-to/set-up-vnc-on-ubuntu-in-four-steps-317125.php") runs VNC successfully, but it must be manually executed first.
[/LIST]
I have read numerous other pages and spent the better part of today searching these forums and Google :(  How do I get this working without local intervention?

---

### Post by gr4nf on 2008-06-12
Do you know the command that starts the server? If so, just append it to ~/.bashrc, the shell script.

---

### Post by mwjones on 2008-06-12
> **gr4nf said:**
> Do you know the command that starts the server? If so, just append it to ~/.bashrc, the shell script.

Then it would run every time a bash shell was spawned.  I want it to kick off once when the computer boots, not with me having to login.  

The correct way, I thought, to do automatic loading was with a script in **/etc/init.d/** and to use **update-rc.d**; however the *x11vnc* process does not continue running via that method (or at least with the script I had).

---

### Post by gr4nf on 2008-06-12
check your /etc/rc3.d

it is possible that it is already there, created by the installer, but is not set to run.

---

### Post by mwjones on 2008-06-12
> **gr4nf said:**
> check your /etc/rc3.d

it is possible that it is already there, created by the installer, but is not set to run.

It wasn't.  There was no init.d script created or run-level symlinks.  I had to make those myself.  I saw the script kick off in the framebuffer when Kubuntu was booting, but when the OS was loaded, the *x11vnc* process was not in memory (**ps -ef | grep -i x11**).

---

### Post by gr4nf on 2008-06-12
You could try this tiny one:
```

#!/bin/sh
#
# Startup/Stop script for vncservers for some users.
#

case "$1" in

'start')
   /bin/su - bob -c "/usr/local/bin/vncserver :1"
   /bin/su - sally -c "/usr/local/bin/vncserver :2"
   /bin/su - jim -c "/usr/local/bin/vncserver :3"
   ;;

'stop')
   /bin/su - bob -c "/usr/local/bin/vncserver -kill :1"
   /bin/su - sally -c "/usr/local/bin/vncserver -kill :2"
   /bin/su - jim -c "/usr/local/bin/vncserver -kill :3"
   ;;

*)
   echo "Usage: /etc/init.d/rc.vnc { start | stop }"
   ;;

esac

```

---

### Post by mwjones on 2008-06-12
Which package is that for?  **aptitude install ________**

---

### Post by krunge on 2008-06-12
> **mwjones said:**
> 
The correct way, I thought, to do automatic loading was with a script in **/etc/init.d/** and to use **update-rc.d**; however the *x11vnc* process does not continue running via that method (or at least with the script I had).

I think the best way is to start x11vnc in an "Xsetup" script.  Then whenever the X server is started x11vnc is also started & attached to it.  It shows the GDM/KDM/etc login screen.

[http://www.karlrunge.com/x11vnc/faq.html#faq-display-manager]("http://www.karlrunge.com/x11vnc/faq.html#faq-display-manager")

Another option is inetd, but like any init.d scheme it needs to guess the DISPLAY (nearly always ":0") and XAUTHORITY (often has a random basename).

[http://www.karlrunge.com/x11vnc/faq.html#faq-inetd]("http://www.karlrunge.com/x11vnc/faq.html#faq-inetd")

---

### Post by cariboo on 2008-06-12
Have you tried the remote desktop software that comes with Ubuntu? You can enable it in System-->Preferences-->Remote Desktop.

Just tried it from windows using vncviewer and it works quite well.

I see you're on Kubuntu, but if you don't mind using a few gnome tools the programs you need are **vinagre** and **vino**

Jim

---

### Post by mwjones on 2008-06-13
**krunge:** Thanks so much, your doc had the piece I needed.  Here is the line:

**/etc/kde3/kdm/Xsetup**```
x11vnc -forever -rfbauth /home/xyz/.vnc/passwd -bg -o /var/log/x11vnc.log
```

From another doc, I already had a couple commands in that file as well as Xsession.  But commenting out the previous commands, and just adding the one above has made it work correctly.  Thanks!


**cariboo907:**  Thank you for your suggestion and testing as well.  Those apps would have been my next move in the process.

Cheers,
mwjones

---

### Post by WangWeiLin on 2009-12-01
Hello

I hope mwjones is still active. I have the exact same Problem as you and not a lot of people seem to understand the problem when I describe it to them.

Would you be so kind to explain to me the steps you took. So that I can follow them and get this sucker running on my system.

Or maybe anybody here has news regarding this topic.

thanks wangweilin

p.s.: running Kubuntu 9.10
- I thought of using tightvnc (which shouldn't be much different)
- I would rather not use one of the gnome tools.

---

