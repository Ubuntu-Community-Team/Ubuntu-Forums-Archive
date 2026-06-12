---
title: "Windows says linux drive needs to be formatted?"
date: 2008-04-23
forum: New to Ubuntu
---

### Post by TheNemeses on 2008-04-23
I just reinstalled my linux drive and i installed that thingy for windows to read extfs2 and 3 and now its showing up in my computer but when i double click it it says the disk needs to be formatted, what do i do?

---

### Post by ace007 on 2008-04-23
Dont format it!

Windows will tell you you need to reformat anything that windows cannot read i.e. Ubuntu's ext3 partition

---

### Post by quinnten83 on 2008-04-23
reinstall it again,it shoudl be able to read the ext2/3 partitions,but it won't read your swap.
I used the fsdrive software, ithink you did too.

---

### Post by TheNemeses on 2008-04-23
k, i just uninstalled and about to reinstall, i didnt format it, but why does it do that? is my data and stuff lost?

EDIT: Still doing the same thing. :-\

---

### Post by ace007 on 2008-04-23
I doubt it is lost.  Windows just sees that the drive is there now, but it cant read it so it assumes it is just raw space waiting to be formatted.  I've never used the fsdrive program so I cant tell you much about it.

---

### Post by Paqman on 2008-04-23
> **TheNemeses said:**
> i installed that thingy for windows to read extfs2 and 3

Which one? I've used [ext2ifs](http://www.fs-driver.org/download.html) in the past and it worked fine.

---

### Post by Wazoot on 2008-04-23
nemeses, Just ignore the windows format thing. Windows will tell you to format something it wont read, cause it doesnt like other OS's lol. So for now just ignore it if u can :mad:

---

### Post by SOULRiDER on 2008-04-23
Yes, ignore it, windows goes completely nazi when it finds non-Microsoft stuff.

---

### Post by Scheater5 on 2008-04-23
Whoa there, there may be a simpler solution - particularly if you're using ex2ifs.  If a drive was removed without being unmounted, sometimes Windows refuses to recognize it.  I have a Western Digital drive the constantly tries to mount itself under Windows, so I have to make sure all the writing is done and then "unsafely remove" it every time - sure enough, Windows won't see it next time.  I have to mount it and then unmount it under Linux or OSX before Windows will see it.

---

### Post by TheNemeses on 2008-04-23
yup and now x.org is ****** up in linux and i cant get in, i forgot my password, now what do i do?

---

### Post by Scheater5 on 2008-04-23
If you accidentally formatted it under Windows, you might be in trouble.  And if you can't remember your password, you might have difficulty fixing this.  I would suggest first checking to see if the data is still safe by booting into a livecd and mounting that partition.  Then we can see about recovery options - maybe copy an old backup of /etc/X11/xorg.

---

### Post by SigmaHog on 2008-04-24
I am having this same problem if anyone can figure this out it would be nice, i reinstalled the program and it's telling me to reformat the drive but I didn't...

---

### Post by yaknowwat on 2008-04-24
its a bad choice to try to view you linux partition with windows even if it is possible it is highly unstable and screws up your partition logs and making it near impossible to boot.

I suggest making a NTFS or FAT32 sub partition for sharing linux files to windows.

---

### Post by Whiffle on 2008-04-24
In windows go to control panel and click on the icon for the ext2ifs driver, make sure everything looks okay there.  I have this installed on my dads computer back home and its been working flawlessly for a couple of years now.

---

### Post by ubuntu27 on 2008-04-24
I can't help you in how to fix your recent problem (forgot password, or the drive could be formated).

For future reference, I recommend you to use [explore2fs]("http://www.chrysocome.net/explore2fs") to READ partitions with ext2 and ext3 filesystem. 

I been using explore2fs for four years and I have never experienced problems. What I like about it is that unlike the other one mentioned in this thread, it does not have the ability to write to ext2/ext3 partitions (it only reads). Furthermore, it does not mount the partition when you start Windows. It only starts when you execute the program yourself.

Here is the link:

[http://www.chrysocome.net/explore2fs](http://www.chrysocome.net/explore2fs)

---

### Post by TheNemeses on 2008-04-25
K i fixed it, i got into ubuntu thanks to my 1337 hacking skills, finally after doing a dpkg-reconfigure xorg.xserver i got in, reinstalled ntfs reading and writability, booted back into windows and walah! thanks boys.

---

