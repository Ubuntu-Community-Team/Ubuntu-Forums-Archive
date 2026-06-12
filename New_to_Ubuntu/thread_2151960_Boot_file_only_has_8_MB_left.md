---
title: "Boot file only has 8 MB left"
date: 2013-06-06
forum: New to Ubuntu
---

### Post by Ed in CT on 2013-06-06
Everytime I turn on the computer, I get a message that there is only 8 MB left in my boot file and that I should move some files elsewhere.  I don't know what to move or what is safe.  Can someone help me with advice on what to move and where so I don't mess up the operating system?

Thanks

Ed

---

### Post by newb85 on 2013-06-06
What release of Ubuntu are you running, and how many kernels do you have installed?

---

### Post by MoebusNet on 2013-06-06
The first thing I would recommend to you is to back up your data before you do anything else. That way if it all comes unglued you at least haven't lost your valuable data.

EDIT: BTW, I notice that you appear to be running Ubuntu 9.10. Since 9.10 is no longer supported and updates may be difficult to come by if you must reinstall, perhaps this is an opportunity to evaluate whether or not a newer version of Ubuntucan fulfill you requirements. I would try out Ubuntu 12.04LTS which has 5 year support. You can evaluate it on a Live-CD/USB to confirm hardware compatibility before you commit to changing anything.

If you are gonig to attempt to stay with 9.10, maybe this will help:

[http://www.upubuntu.com/2011/11/how-to-remove-unused-old-kernels-on.html](http://www.upubuntu.com/2011/11/how-to-remove-unused-old-kernels-on.html)

---

### Post by Impavidus on 2013-06-06
This probably means you have a separate /boot partition and that it's full.

Have a look at the /boot directory and look at the version numbers present. You can probably uninstall a bunch of old kernels.

Edit: It may be best not to uninstall all old kernels. Keep one, just as a backup in case your current one breaks.

---

### Post by Ed in CT on 2013-06-07
I am running Ubuntu 13.04.  It is the only operating system on a 156 GB hard drive.  Using Dolphin,  I looked at /boot directory as Impavidus suggested and I see a folder labeled grub, another labeled lost+found and then a bunch of files "abi-3.5.0-XX-generic"  another set config "3.5.0-XX generic", still another "initrd.img-3.5.0-XX-generic" then "System.map-3.5.0-XX generic" and "vmlinuz-3.5.0-XX generic".  Then there are a couple of more files: memtest86+.bin and memtest86+_multiboot.bin.  The XX numbers are the same and I assume determine the version I'm looking at.

Which of these should I delete?  Can I use Dolphin to delete them.

I'm a beginner.  Sorry if this stuff is obvious to you guys.
I appreciate any help.

Ed

---

### Post by VMC on 2013-06-07
What's the output of this command, from a terminal:

```
df -h
```

---

### Post by monkeybrain2012 on 2013-06-07
Did you install Ubuntu inside WIndows with WUBI?

---

### Post by Impavidus on 2013-06-08
Use your favorite package manager (software centre, synaptics, apt-get) and uninstall some packages named **linux-image-<some version number>**. Leave the two most recent versions installed. Don't start manually deleting files from /boot.

---

### Post by siddharth007 on 2013-06-12
I would recommend that you use the Ubuntu Tweak tool.It has the 'janitor' feature which can remove all junk from your system and also the older kernel versions safely. For more info on this tool see this [link]("http://bluesteel007india.blogspot.com/2013/03/tweak-your-ubuntu-with-this-smart-tool.html")

---

