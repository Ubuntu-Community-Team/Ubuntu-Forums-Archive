---
title: "Using remote desktop"
date: 2008-05-07
forum: New to Ubuntu
---

### Post by drrwhistle3 on 2008-05-07
Can I use remote desktop to access my home computer from work?  If so, how?  Also, can I use my work pc with XP to do it, so I can get my Ubuntu fix for the day?

---

### Post by Monicker on 2008-05-07
This covers it pretty well:

[http://howtoforge.com/configure-remote-access-to-your-ubuntu-desktop]("http://howtoforge.com/configure-remote-access-to-your-ubuntu-desktop")

---

### Post by quelx on 2008-05-07
Try following what these people did...  vnc over the internet (or any network) is **NOT** secure so you are much better off creating a tunnel to your home machine, howtoforge leaves that bit out, plus tunnels are good for all kinds of secure nonsense with your home box

Basically you need to :

[LIST]
[*]forward port 22 on your home router to the IP address of your ubuntu box.
[*]install ssh-server on you home machine
[*]activate vino (vino-preferences] on you home machine
[*]at work install putty and tightvnc
[*]create a tunnel in putty 5900:localhost:5900 ([http://www.maths.utas.edu.au/People/Hill/vnc/vnc.html](http://www.maths.utas.edu.au/People/Hill/vnc/vnc.html))
[*]ssh into you home box (you got the IP address before you left correct? ([http://whatismyip.org/](http://whatismyip.org/))
[*]look into dynamic dns services like dyndns or no-ip to help with this
[*]run tight vnc to localhost:5900
[/LIST]

[http://ubuntuforums.org/showthread.php?t=783623](http://ubuntuforums.org/showthread.php?t=783623)

---

