---
title: "Transfer Files From Ubuntu to Windows While In Ubuntu"
date: 2008-11-24
forum: New to Ubuntu
---

### Post by dmalpack89 on 2008-11-24
Hi I'm currently running Ubuntu 8.10 and everything is working great. 

I just had a quick question:

While I am in Ubuntu, is there a way I can send files to my windows desktop?

My friend can see his hard drive easily in the "Places" bar, but mine is not there. Just my HP recovery, my cd drive and my Linux partition. He said something about mounting the internal hard drive. Any ideas on what I need to do?
Thanks

---

### Post by grazed on 2008-11-24
just so i know before i go on, you're dual booting windows and ubuntu correct?

or are you talking about two seperate systems?

---

### Post by nhasian on 2008-11-24
first we're going to need the output of 

```
sudo fdisk -l
```

---

### Post by dmalpack89 on 2008-11-24
> **grazed said:**
> just so i know before i go on, you're dual booting windows and ubuntu correct?

or are you talking about two seperate systems?

Sorry about that. Yea I'm dual booting Windows Vista Home Premium and Ubuntu 8.10

---

### Post by vwvr9 on 2008-11-24
Are you able to boot into Windows normally now?

---

### Post by dmalpack89 on 2008-11-24
Yea I can boot both systems fine, I was just wondering if i was downloading stuff or edited a document in ubuntu if there was a way to put them in windows like my friend can

---

### Post by grazed on 2008-11-24
type the following into the terminal, and copy paste it here.

sudo fdisk -l

also, try going to the places window again, and press ctl-H

this will unhide any hidden folders/drives/etc.

---

### Post by dmalpack89 on 2008-11-24
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xac72ee30

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       13727   110261140    7  HPFS/NTFS
/dev/sda2           13728       14593     6956145    7  HPFS/NTFS

---

### Post by vwvr9 on 2008-11-24
Have you looked at NTFS 3G? [https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G)

---

### Post by dmalpack89 on 2008-11-24
and I tried the ctrl H thing and it's basically a maze to find my windows hardrive, but it's there. the problem is is that i would prefer to have the shortcut available under the places menu if at all possible

---

### Post by grazed on 2008-11-24
> **dmalpack89 said:**
> Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xac72ee30

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       13727   110261140    7  HPFS/NTFS
/dev/sda2           13728       14593     6956145    7  HPFS/NTFS

you're using wubi? (installed ubuntu from within windows)

---

### Post by prshah on 2008-11-24
> **dmalpack89 said:**
> 
My friend can see his hard drive easily in the "Places" bar, but mine is not there. 

Are you using Ubuntu through a "wubi" (Installed within Windows) installation?

In that case, you cannot open that drive (the one which contains the wubi installation) in Ubuntu.

So, if you have wubi-installed to the C:\Ubuntu (for example), you cannot access that drive in Wubi-Ubuntu.

---

### Post by dmalpack89 on 2008-11-24
nfts config only detects my hp recovery drive

---

### Post by grazed on 2008-11-24
> **prshah said:**
> Are you using Ubuntu through a "wubi" (Installed within Windows) installation?

In that case, you cannot open that drive (the one which contains the wubi installation) in Ubuntu.

So, if you have wubi-installed to the C:\Ubuntu (for example), you cannot access that drive in Wubi-Ubuntu.

actually, you can.

the entire windows file system is under /host

---

### Post by dmalpack89 on 2008-11-24
thanks a lot for the help

i did use wubi to install, but the /host is exactly where i found my windows directory 

is there a way however that i can link this under places?

---

### Post by vwvr9 on 2008-11-24
from the Applications->System Tools --> NTFS menu is "write internal drive" enabled?

---

### Post by grazed on 2008-11-24
> **dmalpack89 said:**
> nfts config only detects my hp recovery drive

go to /host

it should be the first available directory in your filesystem. from there you should be able to see your windows directory as well.

you can bookmark any spot in the drive from the bookmark option on the top of the file browser. from there, open bookmarks, and drag and drop it onto your desktop, or point to it from the gnome menu editor. (right click the ubuntu logo)

---

### Post by grazed on 2008-11-24
> **dmalpack89 said:**
> thanks a lot for the help

i did use wubi to install, but the /host is exactly where i found my windows directory 

is there a way however that i can link this under places?

yup, just drag the windows directory folder into the left pane in the file browser.

it will then appear in your places menu under bookmarks.

---

### Post by dmalpack89 on 2008-11-24
THANK YOU SO MUCH. i realized how much of a noob I was. I see the bookmark function and i successully bookmarked the folder I needed. (My first day using ubuntu) I really appreciate your help!!

---

### Post by nhasian on 2008-11-24
also if you use the middle mouse button to drag a folder from one window to another (or to the desktop) you will have the options to link, copy, or move.  Link is like a shortcut in windows.

---

### Post by grazed on 2008-11-24
no problem!

just remember to defrag in windows every once in a while since you used wubi. it will keep your ubuntu system speedy. 

and if you so choose, an actual ubuntu partition always performs better. =P

---

