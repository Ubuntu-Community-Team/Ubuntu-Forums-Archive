---
title: "Need help with partitioning and install of 12.04 server"
date: 2012-07-15
forum: New to Ubuntu
---

### Post by OleKingCoale on 2012-07-15
This is the second time I've used Linux for a file server installation, the first being Ubuntu v9 when it was the latest, so it's been a while. Basically, I know just barely enough to be dangerous. :P

Last time I just used Ubuntu Desktop, since I didn't need any robust server features--just a centralized location for my company's files--and as a complete noob I wanted the comfort of a GUI for installation. (Speaking of GUI...I read somewhere in these forums that once you install a GUI on server it basically is no different from desktop...is that true?)

This time I'm expanding my horizons and using Ubuntu Server (12.04, AMD 64). Hardware is a refurb HP ProLiant DL385 G2 rack server with hardware raid, 4GB RAM, dual core AMD 2.2 GHz. Hard drives are 1 pair of 72 GB and 1 pair of 750 GB. In addition to the main purpose as a file server, I also want to use it as a LAMP server for website testing (local only).

I've actually almost finished the install, but am concerned about a few details and want to find out if I should have done something differently now rather than later.

I followed the Advanced Installation instructions for LVM, but am concerned about the partitions. Specifically, the size of the partitions and whether I missed any that I needed.

Currently I have the 72 GB drive partitioned as follows:

#1  Primary     999.3 MB     ext3     /boot     (flagged as bootable)
#2  Primary         1.0 GB     swap    swap
#3  Primary         6.0 GB     ext3     /
#5  Logical         65.4 GB     lvm

Initially I included a /home partition of 20 GB, but when I did that it said the rest of the drive was "unusable".  (???)

Also, when I installed v9 before, I had a whole list of partitions I was instructed to create that were not mentioned in the LVM instructions, nor in the instructions I found posted in this forum:
/usr
/usr/local
/tmp
/var
/var/spool
/home

Are these not necessary?

Assuming I'm ok without them, are the sizes of my partitions within recommended ranges? Especially the swap partition...I thought it should be twice the RAM, but one post I found said twice the RAM _but _max of 1GB (I followed that advice, since I wasn't able to find anything that contradicted it).

Answers, suggestions, and even heckling are welcome.

---

### Post by oldfred on 2012-07-16
I do not know servers. 

Swap generally now is one times RAM in GiB if you want to hibernate. The old rule of 2X was when RAM was 256K or 512K. Not sure if some server processes like a database server may use more RAM and if too many programs are running need swap.

Only server installs may need the separate root folders as separate partitions. Some use it because they want to isolate certain processes or know they want some things separate. One desktops the default install is just / (root) and swap and some use a swap file.

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

Lightweight Desktop environment
Ubuntu Server + lxde
works smooth in under 256mb ram on a p2
sudo apt-get install lxde
Or Xfce GUI without any of the associated Xubuntu applications
sudo apt-get install xfce
Comparison of desktop environments 
[https://wiki.archlinux.org/index.php/Desktop_Environment](https://wiki.archlinux.org/index.php/Desktop_Environment)
[http://en.wikipedia.org/wiki/Comparison_of_X_Window_System_desktop_environments](http://en.wikipedia.org/wiki/Comparison_of_X_Window_System_desktop_environments)

Difference between Windows manager & desktop environments
[http://forums.linuxmint.com/viewtopic.php?f=90&t=54945&start=0#p314893](http://forums.linuxmint.com/viewtopic.php?f=90&t=54945&start=0#p314893)
window managers like Icewm, Openbox, Fluxbox, and Xfwm
desktop environments are KDE, Gnome, Xfce, Enlightenment, and LXDE

---

### Post by OleKingCoale on 2012-07-17
Thank you for the reply and info.  From your post and the links you provided, it seems my system should have a 4GB swap partition (and considerably less would be OK, since it's primarily just a file server, I don't foresee it using anywhere near all its RAM at the same time very often--if ever).

I'm still not sure what to think about the other partitions (/var/spool, /tmp, etc.). I'm assuming it became unnecessary to have them separately partitioned during one of the upgrades, 9 to 10 or 10 to 11...but I haven't found any documentation about it yet, and I'd feel better if I knew for sure. If anyone can tell me or point me in the right direction, feel free to message/email me through the forum.

I did find answers to some of my other questions, though, so I'm posting them here so I can mark the thread as solved and maybe help someone else looking for the same info.
...
[INDENT]*"Initially I included a /home partition of 20 GB, but when I did that it said the rest of the drive was "unusable".  (???)"*
[/INDENT]That happened because I made the mistake of setting /home to be a primary partition, making it my 4th primary partition on the drive. I didn't realize you're limited to 4 primary partitions or 3 primary + 1 extended.

[RIGHT](source and quick info on partitioning schemes: [https://help.ubuntu.com/community/PartitioningSchemes](https://help.ubuntu.com/community/PartitioningSchemes))
[LEFT]...
[/LEFT]
[/RIGHT]
[INDENT]*"I read somewhere in these forums that once you install a GUI on server it basically is no different from desktop...is that true?"*
[/INDENT]I found confirmation that--as of the 12.04 release--the only real difference between desktop and server versions is the presence or absence of the GUI/desktop environment: 
[INDENT]*"The amd64 -generic and -server kernel flavors have been merged  into a single -generic kernel flavor for Ubuntu 12.04.  Given the few  differences that existed between the two flavors, it only made sense to  merge the two and reduce the overall maintenance burden over the life of  this LTS release."*
[/INDENT][RIGHT](source: [https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop))
[/RIGHT]

---

### Post by oldfred on 2012-07-17
Similar to your source on kernel from the desktop wiki page, there is a server wiki page. Some of the same info:

[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuServer](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuServer)

And a server guide.
[https://help.ubuntu.com/12.04/index.html](https://help.ubuntu.com/12.04/index.html)

---

