---
title: "Install Server or Desktop"
date: 2019-11-03
forum: New to Ubuntu
---

### Post by peter847 on 2019-11-03
I am about to install Ubuntu on an old dual core 1.5MHz Celeron machine as a file server for music and pictures.  I know I could just install the server version but for ease of setup and maintenance I would like to install the desktop version.  I know the desktop will be slow but is there any performance hit from having the desktop sitting around in the background?  In other words if I log out of the desktop and leave it inactive, will the machine's performance as a file server be the same as if I just ran the Ubuntu server version?

---

### Post by CatKiller on 2019-11-03
For a home server it will make essentially no difference.

If you were trying to squeeze every clock cycle on your supercomputer, or were incredibly RAM-constrained, you might notice the difference.

You'll probably want to remove the snaps, though.

---

### Post by uRock on 2019-11-03
Hello and welcome to the forums.

I have an old Netbook running as a server. I installed it as a desktop with Debian LXDE(like Lubuntu) as the Desktop Environment. When I just boot it up and let it run without logging into the desktop, it is using 247MB of RAM and about 80% use of one core of the CPU. 70% of that one core is for the service I am running, which is an app called Motion. It streams a webcam and reords when motion is detected. When motion is not running, the server is using about 2% of a CPU core and 140MB RAM.

I hope that helps with making a decision. Lubuntu is very lightwiehgt and should offer all of the tools needed for setting up a file server.

---

### Post by TheFu on 2019-11-03
If you are "new to Linux", then there really isn't any choice.  Desktop.  The learning curve is steep enough already.

You can choose a lighter GUI variant which will help with CPU and RAM utilization.  xubuntu, lubuntu, ubuntu-mate.
Any GUI will always have *some* impact.  GUIs also impact security and stability, on some levels. Stability with a GUI running has always been a little less than non-GUI servers. Still, a Linux GUI should stay up and working for months without issue. Security is really a LAN issue, provided a real router with all inbound ports closed is used.

18.04 Ubuntu-mate is my suggestion, but as long as you are 18.04 with one of the lite DEs, it should be fine. Only you can pick the right answer for your needs.

Just be aware that for server stuff, there aren't any GUIs that setup the most efficient ways of doing server stuff.  No point-n-click.  There are some point-n-click methods, but they have big network and disk performance hits. Just be aware.

---

