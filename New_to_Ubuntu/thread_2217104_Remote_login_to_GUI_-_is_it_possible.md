---
title: "Remote login to GUI - is it possible?"
date: 2014-04-15
forum: New to Ubuntu
---

### Post by Priest Apostate on 2014-04-15
I just recently installed KDE to my server, and I am able to login to it locally, to a GUI, if I wish (I'm doing this to study for my LPIC). 

I am curious as how to obtain the ability to remotely log in my server's GUI, if I so wished. I am using Ubuntu 12.04LTS, with PuTTY, with SSH enabled and configured. Can I do it with Putty, or do I need another program to log into the server?

---

### Post by Derek Karpinski on 2014-04-15
[http://www.teamviewer.com/en/index.aspx](http://www.teamviewer.com/en/index.aspx)

Seems to me to be the best, fastest option.

---

### Post by Priest Apostate on 2014-04-16
Coolness -- but is there a setting that I would need to configure manually that would allow the same access, without the need for an additional program? While I'm getting a pretty good workout with bash, I'd figure that that may come in handy sometime...

---

### Post by mastablasta on 2014-04-16
you want to run a graphical application via SSH?:
[http://www.cyberciti.biz/tips/running-x-window-graphical-application-over-ssh-session.html](http://www.cyberciti.biz/tips/running-x-window-graphical-application-over-ssh-session.html)

[https://help.ubuntu.com/community/SSH](https://help.ubuntu.com/community/SSH)

[http://askubuntu.com/questions/47642/how-to-start-a-a-gui-software-on-a-remote-linux-pc-via-ssh](http://askubuntu.com/questions/47642/how-to-start-a-a-gui-software-on-a-remote-linux-pc-via-ssh)

also in ubutnu you do not need putty. default terminal can handle ssh just fine.

---

### Post by Canterwood on 2014-04-16
There's a few resources (like [this one]("http://ubuntuforums.org/showthread.php?t=505541")) that tell you how to run the entire desktop environment (i.e. Gnome, KDE, XFCE, etc.) over SSH, but if you want to use a single application it's really easy to do over SSH. Ubuntu comes with OpenSSH, so you don't need to install anything. Just open up a terminal and issue the command:

```
ssh -X user@server
firefox
```

This example starts an SSH session with X tunneling enabled. This means that any application you start afterwards will tunnel it's graphical output over SSH to your local machine. If you start firefox like in the example above, the window will open at your local machine.

Hope that helps!

---

### Post by Priest Apostate on 2014-04-16
Thanks everyone - I will cut my teeth on these options!

---

