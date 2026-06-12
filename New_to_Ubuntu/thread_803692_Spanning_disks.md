---
title: "Spanning disks?"
date: 2008-05-22
forum: New to Ubuntu
---

### Post by rickferd on 2008-05-22
I have installed ubuntu on to an 80 gig hard drive. I also have 4 more drives in the system. 2 250G and 2 200G I want to combine the 2 250's to make a 500G and combine the 2 200's to make a 400G. I found an article that walked me thought combining them using software RAID 5 and now I have a 250G and a 200G that are mirrored I'm quessing. How do I make a 500G and a 400G drive? I know this can be done in windows, by doing spanning, is there a way to do this in ubuntu? Thanks Rich

---

### Post by aikiwolfie on 2008-05-22
Have you looked up dmraid?

---

### Post by cenwesi on 2008-05-22
I think what he really wants is LVM. I did this about 2 weeks ago. In my case i have 4x500gig hd.

[http://www.linuxdevcenter.com/pub/a/linux/2006/04/27/managing-disk-space-with-lvm.html](http://www.linuxdevcenter.com/pub/a/linux/2006/04/27/managing-disk-space-with-lvm.html)
[http://wiki.randompage.org/index.php/DistOS:Linux:LVM](http://wiki.randompage.org/index.php/DistOS:Linux:LVM)

for managing LVM using gui-->  [http://ubuntuforums.org/showthread.php?t=216117](http://ubuntuforums.org/showthread.php?t=216117)


read up on lvm before you even venture into it. Make sure you understand fully the basic concert. Now if you really don't care about the data on the drives, then you can go straight into it... But if you don't want to loose any data before issue the commands, then i will suggest you move dir/files to one of the bigger drives and then start converting the smaller drives to LVM... kinda of like swapping... i hope it makes sense :)

---

### Post by rickferd on 2008-05-25
Thanks I will start there and see how it goes, and let you know. Thanks

---

