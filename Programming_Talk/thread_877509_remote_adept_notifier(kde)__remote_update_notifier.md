---
title: "remote adept notifier(kde) / remote update notifier(gnome)"
date: 2008-08-01
forum: Programming Talk
---

### Post by survient on 2008-08-01
I'm looking to compile two programs, one for kde and one for gnome, possibly porting to xfce if this works out. For the longest time I've wanted a system tray notifier to bug me about updates on some of my running systems(I have a server that I only connect to through webmin or vnc when I really need to, and that's the only time I check for updates because I keep forgetting). Basically an adept updater(kde)/update manager(gnome) or some other GUI that will let me run updates on a remote system. For now I'm only planning this for a LAN environment, but will possibly later move on to allowing it to work over the internet. It may work for both at the same time. My basic idea would be to take the existing programs adept updater(kde)/update manager(gnome) to use an ssh session to check on a remote system's synaptic status. I'm sure this is a crude approach but it's the only way I can think of off-hand. My trouble is this is my first time coding in ubuntu, other than some java work I have done that works on any system. I'm familiar with coding and some scripting, but I'm not sure what the updater/notifier programs are built on(language-wise). From their dependencies I can only guess a combination of python and perl for update manager and a bit of qt, c, and gcc for adept updater? The adept/update notifier daemons also caught my eye, but I'm not sure if using them would be superfluous to what I want to do. I just need some help in getting pointed in the right direction with this.

---

