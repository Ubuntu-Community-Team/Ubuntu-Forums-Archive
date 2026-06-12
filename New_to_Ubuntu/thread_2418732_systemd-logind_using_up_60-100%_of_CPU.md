---
title: "systemd-logind using up 60-100% of CPU"
date: 2019-05-10
forum: New to Ubuntu
---

### Post by diegoatravesar on 2019-05-10
Hello everyone,

I recently set up a Linux set up on a netbook to run [Home-Assistant.io]("https://www.home-assistant.io/") for some home automation tasks. During the install, I set up Docker using [THIS]("https://stackoverflow.com/questions/37989534/how-to-install-docker-on-32bit-machine-having-ubuntu-12-04") tutorial as I needed it set up on a 32 bit machine. 

I am able to access Home-Assistant fine, and have no idea if / what docker is doing, but the system appears to be functioning as intended.

What I've noticed is that when I use htop to view the CPU / RAM usage, systemd-logind is using between 60-100% of my CPU at all times, followed closely by /sbin/init splash at 20-25% and systemd-journald at 15-20%. This means that at almost all times the server is maxed out on processing power.

I am wondering if there is any reason this is occuring, and whether or not disabling systemd-logind would cause any long term issues. Based on the research I've dug up, it looks like it can be masked to not automatically restart with no issues, but I want to ask people better informed than myself.

I am also planning on disabling the Desktop as I don't intend on using the screen, I will be remoting into it if needed. Is there anything I should be aware of when attempting to do so?

PC Specs:
OS : Lubuntu 18.10
CPU : Intel Atom N270 @ 1.6GHz
RAM : 2GB DDR2 @ 533MHz
Storage : 16GB Flash Storage(Honestly not entirely sure the specifics on this)

---

