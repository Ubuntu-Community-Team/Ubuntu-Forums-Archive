---
title: "My Laptop running 11.04, should I upgrade to 12.04 or 12.10 ??"
date: 2012-10-18
forum: New to Ubuntu
---

### Post by cwmoser on 2012-10-18
My laptop is running 11.04.
Should I upgrade to 12.04 or 12.10???

When I do upgrade, I want to partition the drive
so the OS is in its own partition - think that
10GB is large enough?

I definitely want Gnome Desktop.

11.04 runs pretty good.
My laptop is a Lenovo T500, 2GB RAM, 1680x1050

Comments????

Thanks

Carl

---

### Post by Wim Sturkenboom on 2012-10-18
How much software do you install? I don't install much and currently have 4.2GB used (after clean the apt cache). So 10-15GB is enough for me; there are however people who will run out in no time (downloading 2GB games from the software center seems to be possible).

If disk space is not really a constraint, 20-25GB would be my preferred option. It makes that you don't have to worry (or to a far lesser extent) about cleaning the apt-cache, old kernels, installation fo additional software etc.

---

### Post by valroadie on 2012-10-18
I would say if your comp runs great now, why not? I went from 11.10 to 12.04 on my macbook 2,1 and it worked out great. Nothing really changed except for the new looks :) About the space, I concur with sturkenboom, if you dont play a lot of games or download a lot of videos I would say 10G's is plenty. :) Have fun! Keep us updated.

---

### Post by Mark Phelps on 2012-10-19
NOT a good idea to Force an upgrade -- until you have a chance to see how well it works with your PC.  Create an Ubuntu LiveCD or LiveUSB first, boot from that, and see how well it works.

Note that there is no easy way to "roll back" to a previous Ubuntu release.  So, if the upgrade produces problems, you will be faced with having to fix them to get a working system back.

Also, the Gnome desktop is not automatically available in 12.10.  See the link below for instructions on how to install it:

[http://alinuxblog.com/ubuntu/change-desktop-environment-ubuntu.htm]("http://alinuxblog.com/ubuntu/change-desktop-environment-ubuntu.htm")

---

### Post by pqwoerituytrueiwoq on 2012-10-19
[LIST=1]
[*]Always use a live cd/usb to see if the new version will run on your system
[LIST=1]
[*]If you get a blank screen at boot, use nomodeset in the kernels boot line this is commonly needed for nvidia GPUs
[/LIST]
 
[*]11.04 goes EOL this month ( [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases) )
[/LIST]
you said you like the gnome desktop...
[Ubuntu 12.10 Gnome edition](https://wiki.ubuntu.com/UbuntuGNOME/ReleaseNotes/12.10)

---

### Post by cwmoser on 2012-10-19
Reconfigured my single HD partition into separate partitions
for /home, one for Ubuntu 11.04, and one for Ubuntu 12.10

Playing with 12.04 Gnome Classic.
I note that Workspaces feature not working properly - namely when
I switch workspaces I get a window with no menu and cannot
get back to Workspace #1

Carl

---

