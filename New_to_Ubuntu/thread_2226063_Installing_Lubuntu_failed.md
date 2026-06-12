---
title: "Installing Lubuntu failed"
date: 2014-05-25
forum: New to Ubuntu
---

### Post by elrufero24792 on 2014-05-25
Hello, this is my first time trying linux and my first post, I was hoping to install Lubuntu 12.04 in my old pc (i was trying with v 14.0 but it seems my pc doesn't support PAE so i must install an older version according to the ubuntu official site). I created a LiveUSB using Unetbooting, turned on my pc, changed the boot order to run usb first, restart and wait for the installer to run, i chose to install ubuntu and erase all the partitions and files on the hard disk, chose my preferences and the installation stopped at about 75% and a warning showed me this message:

"The installer found a problem when copying the files to the hard disk:
```
[Errno 30] Read only file system. ‘/target/usr/lib/i386-linux-gnu/gtk-2.0/2.10.0/engines/libclearlooks.so’
```
Usually this happens because of a faulty hdd, it is either too old and has to be replaced or you should move your computer to a colder place. "

Even though my computer is old i belive Lubuntu should work because Before fresh installing Lubuntu I tried it with the "try without installing" option, and it ran smoothly, though my old files were still there the Lubuntu OS worked fine. I also checked the disk for errors and it reported clean. My pc uses Windows 7 basic but it was to much for it as it came shipped with WindowsXP SP1.

my pc is a 2006 IBM think pad T40:
1.5 GHz Intel Pentium M 32 bit
1GB RAM
35 GB Hard disk + 5GB in the partition that contained the original WindowsXP OS recovery

THANK YOU FOR YOUR HELP! :)

---

### Post by sudodus on 2014-05-25
I think Lubuntu 14.04 LTS will work in your IBM thinkpad T40 computer, if you use the boot option ***forcepae***. I have a similar IBM thinkpad T42 which works well with a similar CPU.

See this link for more details 

[https://wiki.ubuntu.com/Lubuntu/AdvancedMethods#Pentium_M_and_Celeron_M](https://wiki.ubuntu.com/Lubuntu/AdvancedMethods#Pentium_M_and_Celeron_M)

---

### Post by jjaakkol on 2014-06-30
[FONT=arial]I had T40 with Lubuntu 12.04 in first place because of PAE not supported. But yesterday I made upgrades with software updater 12.04-> 12.10-> 13.10-> 14.04 or something like that. 

I was using this prochedure to enable PAE (and this I had to do after each upgrade of course!): [/FONT]

[https://help.ubuntu.com/community/EnablingPAE](https://help.ubuntu.com/community/EnablingPAE)

**Add "pae" flag to /proc/cpuinfo** 

 ```
cat /proc/cpuinfo | sed 's/flags\t*:/& pae/' > /tmp/cpuinfo_pae
 sudo mount -o bind /tmp/cpuinfo_pae /proc/cpuinfo
 sudo mount -o remount,ro,bind /proc/cpuinfo
 grep flags /proc/cpuinfo
 # should output "flags : ... pae ..."
```

[FONT=arial]I still have one issue left but there seems to be solution for that. 
My account desktop is empty, no "start menu" and no icons on desktop. Other accounts are OK. [/FONT] 

[http://askubuntu.com/questions/451858/blank-desktop-after-upgrading-lubuntu-to-the-next-version](http://askubuntu.com/questions/451858/blank-desktop-after-upgrading-lubuntu-to-the-next-version)

[FONT=arial]Install of 14.04 from USB directly did not work even with forcepae option. Thats why I made it "hard way". [/FONT] :)

[URL="https://help.ubuntu.com/community/EnablingPAE"]


[/URL]

---

### Post by sudodus on 2014-06-30
> **jjaakkol said:**
> [FONT=arial]I had T40 with Lubuntu 12.04 in first place because of PAE not supported. But yesterday I made upgrades with software updater 12.04-> 12.10-> 13.10-> 14.04 or something like that. 

I was using this prochedure to enable PAE (and this I had to do after each upgrade of course!): [/FONT]

[https://help.ubuntu.com/community/EnablingPAE](https://help.ubuntu.com/community/EnablingPAE)

**Add "pae" flag to /proc/cpuinfo** 

 ```
cat /proc/cpuinfo | sed 's/flags\t*:/& pae/' > /tmp/cpuinfo_pae
 sudo mount -o bind /tmp/cpuinfo_pae /proc/cpuinfo
 sudo mount -o remount,ro,bind /proc/cpuinfo
 grep flags /proc/cpuinfo
 # should output "flags : ... pae ..."
```

[FONT=arial]I still have one issue left but there seems to be solution for that. 
My account desktop is empty, no "start menu" and no icons on desktop. Other accounts are OK. [/FONT] 

[http://askubuntu.com/questions/451858/blank-desktop-after-upgrading-lubuntu-to-the-next-version](http://askubuntu.com/questions/451858/blank-desktop-after-upgrading-lubuntu-to-the-next-version)

[FONT=arial]Install of 14.04 from USB directly did not work even with forcepae option. Thats why I made it "hard way". [/FONT] :)


Your problem might be caused by the long upgrading path.

An alternative is to use a non-pae kernel with 14.04 LTS according to these links

[https://help.ubuntu.com/community/9w](https://help.ubuntu.com/community/9w)

[http://ubuntuforums.org/showthread.php?t=2216356&page=4&p=13016786#post13016786](http://ubuntuforums.org/showthread.php?t=2216356&page=4&p=13016786#post13016786)

(and also other posts in the same thread)

---

### Post by gordintoronto on 2014-06-30
I'm not sure if Lubuntu includes a program called Disks or Disk Utility. If not, you can install it on the LiveUSB. Run it, highlight the hard drive, see what it says about the health of the hard drive, under SMART Status.

---

### Post by kalehrl on 2014-07-01
Disks (gnome-disks) is already installed in Lubuntu.

---

### Post by mörgæs on 2014-07-01
We have no indication that jjaakkol has hard disk problems. 

> **jjaakkol said:**
> 
[FONT=arial]Install of 14.04 from USB directly did not work even with forcepae option. [/FONT][URL="https://help.ubuntu.com/community/EnablingPAE"]
[/URL]

Exactly what happened when you tried?

---

### Post by jjaakkol on 2014-07-10
I tried to install Lubuntu 14.04 from LiveUSB with forcepae option as explained here: [https://help.ubuntu.com/community/EnablingPAE](https://help.ubuntu.com/community/EnablingPAE) but it failed.

My 14.04 Lubuntu is working quite ok now. Only when there is kernel update coming I have to put pae flag on  to cpuinfo otherwise update will fail.. ;)

I could give a try 14.04 non-pae some day.

---

### Post by sudodus on 2014-07-10
You can add forcepae alongside quiet splash in the file **/etc/default/grub**

change
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```
to
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash forcepae"
```

save and run

```
sudo update-grub
```

Then you will always have forcepae and need not worry about it for the kernel upgrades

---

### Post by jjaakkol on 2014-07-10
Great! I will give a try. :)

---

### Post by jjaakkol on 2014-09-02
> **sudodus said:**
> You can add forcepae alongside quiet splash in the file **/etc/default/grub**

change
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```
to
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash forcepae"
```

save and run

```
sudo update-grub
```

Then you will always have forcepae and need not worry about it for the kernel upgrades

Yes, this did the job.

---

### Post by sudodus on 2014-09-03
I'm glad it works for you with forcepae :-)

---

### Post by jjaakkol on 2014-09-05
I tried yesterday also install directly 14.04 by adding forcepae option. This time it worked to IBM T40. I do not know what went wrong in first time.

There was an other issue, relating to USB not found after "Install Lubuntu" command. Live USB was made with [http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)

Solution was here in answer #55.

[https://bugs.launchpad.net/ubuntu/+source/casper/+bug/1241589](https://bugs.launchpad.net/ubuntu/+source/casper/+bug/1241589) 

And in really first place noticed that I have to put USB stick to upper USB slot in my laptop that it would appear to booting device list. ;)

---

