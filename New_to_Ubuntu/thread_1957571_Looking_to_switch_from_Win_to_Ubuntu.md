---
title: "Looking to switch from Win to Ubuntu"
date: 2012-04-12
forum: New to Ubuntu
---

### Post by TheMTtakeover on 2012-04-12
So I Installed Ubuntu through wubi and I have to say that I really like it. I plan on make the complete transition seeing as how everything works as needed with Ubuntu. I had two questions:

1. To switch I planned to burn an ISO to a CD from windows and then use CCleaner to completely wipe out my harddrive. and then to turn on my computer with the Ubuntu Disc in the drive. Is this a bad idea? Or a better way to go about it? I pretty much just want to make sure that I am starting completely fresh in my Ubuntu set-up.

2. Now I know 12.04 is coming in a few weeks. when I update I'll want it to a fresh install. What is the best way of going about this?

Thanks for anyone willing to take the time to help.

---

### Post by NikTh on 2012-04-12
hello TheMTtakeover ,
to completely switch from windows to Ubuntu i think its a very wise decision .(as i keep in my mind that you already tried Ubuntu with wubi)
The easy way is to burn an iso of 12.04 ( its already very stable) ,grab it from here --> [http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/) (Daily build) and boot from CD. The just hit "install Ubuntu" and at the process of installer hit "replace windows with Ubuntu". Thats all. 
Keep in mind that you will lose everything. All of your data. All of your Windows ... everything. 
Good Luck.

---

### Post by TheMTtakeover on 2012-04-12
Thanks for the fast reply and for the info.

---

### Post by oldfred on 2012-04-12
While I am a huge fan of Ubuntu, we regularly get users who come back and say they cannot live without that one application that is Windows only. Best to make a full backup, just in case.

Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

If you have configured Ubuntu in wubi or installed a lot of applications you can migrate that to a new install.

HOWTO: migrate wubi install to partition - bcbc 
[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

---

### Post by papibe on 2012-04-12
Hi TheMTtakeover.

I few thoughts:

I wouldn't worry about wiping the drive with CCleaner since the installation process can delete all current partitions, create new ones, and format them.

Backing up your personal date is always a good idea when installing a new OS.

Although updating to an intimidate higher version has became pretty safe, I've always run with little troubles that made me do a clean install in the end.

Regards.

---

### Post by TheMTtakeover on 2012-04-12
@oldfred I do have that one windows program I can't go without and luckly after testing it, it runs very well in Crossover.
 
@papibe Thanks I won't bother with wiping the drive then.

---

