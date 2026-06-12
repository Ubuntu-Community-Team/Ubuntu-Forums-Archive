---
title: "Need help finding wireless connection."
date: 2008-09-18
forum: New to Ubuntu
---

### Post by misterhan on 2008-09-18
[http://ubuntuforums.org/showthread.php?t=190177](http://ubuntuforums.org/showthread.php?t=190177)

I've tried that guide but it still didn't find the connection.


These commands were denied to me. Please help me. My notebook is acting up very very badly and looks like I'm stuck with the OS.

modprobe ndiswrapper

echo ndiswrapper >> /etc/modules

The first was given for the first command and the second to the other.

FATAL: Error inserting ndiswrapper (/lib/modules/2.6.24-19-generic/ubuntu/misc/ndiswrapper/ndiswrapper.ko): Operation not permitted

bash: /etc/modules: Permission denied

Thanks.

---

### Post by jbrown96 on 2008-09-18
You do not have permission to edit your /etc/modules file. Use sudo before the command. Cool trick: if you execute a command and it complains about permission being denied, you can use ```
sudo !!
``` to re-run the previous command as root.

---

### Post by misterhan on 2008-09-18
Thanks for the quick reply and the extra tip. I'll give it another try and hopefully my router will be found.

This command
echo ndiswrapper >> /etc/modules
is still being denied. I tried putting sudo in front but that still was denied. Any advice?

---

### Post by jbrown96 on 2008-09-18
Not sure why. I've tried playing aroudn with echo before and have never had much luck. You could try ```
sudo gedit /etc/modules
``` and then just add ndiswrapper to a new line at the end. Echo just appends something to the end of a file, so there won't be any difference.

---

### Post by misterhan on 2008-09-18
This is troublesome since the internet still continues to not work.
Does anyone have any advice for me?

---

### Post by jbrown96 on 2008-09-18
Edit: that guide is from 2006. Unless you are running an old version of ubuntu, don't use it. It's not necessary. Look at this [one]("http://www.foogazi.com/2008/04/28/how-to-enable-bcm43xx-in-ubuntu-804/")

I set up a 43xx card for my dad, and it was super easy. Ubuntu was able to automatically set it up (I believe it used ndiswrapper too). See if there is anything listed for your card in System-->Administration-->Hardware Drivers. I know this worked in 7.10 and 8.04. However, messing with ndiswrapper can do some strange things, so it might not even appear normally now. If you have a liveCd, you may have better luck trying to see if the drivers exist on that. 
As far as ndiswrapper goes, are you sure that ndiswrapper is being loaded (check lsmod), the driver is loaded (ndiswrapper -l), the interface is up (ifconfig), network-manager doesn't fail to report results (try manually scannning with iwlist scan), does your system see any wireless devices (iwconfig)? you can post back all the output of those

---

### Post by misterhan on 2008-09-19
You are such a help. Thanks so much I'll get right on it.

---

### Post by Borusa on 2008-09-19
One way to do the echo thing with sudo is

```
echo *Foo goes here* | sudo tee -a *Place it's going*
```

---

### Post by misterhan on 2008-09-19
jbrown so I tried the guide, but the box will not check. Do I need some firmware to run it?

I also tried this guide:
1 #install fwcutter with command:
sudo apt-get install bcm43xx-fwcutter

2 #download firmware of here [http://www.ulaopstudio.it/firmware/wl_apsta.o](http://www.ulaopstudio.it/firmware/wl_apsta.o)

3 bcm43xx-fwcutter -w /lib/firmware /insert path of wl_apsta.o

4 #insert word bcm43xx on modules with command
vim /etc/modules //insert bcm43xx

5 reboot

But the command /insert says it doesn't work.

---

### Post by jbrown96 on 2008-09-20
> **misterhan said:**
> jbrown so I tried the guide, but the box will not check. Do I need some firmware to run it?

I also tried this guide:
1 #install fwcutter with command:
sudo apt-get install bcm43xx-fwcutter

2 #download firmware of here [http://www.ulaopstudio.it/firmware/wl_apsta.o](http://www.ulaopstudio.it/firmware/wl_apsta.o)

3 bcm43xx-fwcutter -w /lib/firmware /insert path of wl_apsta.o

4 #insert word bcm43xx on modules with command
vim /etc/modules //insert bcm43xx

5 reboot

But the command /insert says it doesn't work.

From what I can remember, it automatically installed fwcuttter. Then it had another bit about downloading firmware from some German website (.de) I believe. Sorry I can't help you more, but it did it automatically for me. There might have been some trouble with distributing the firmware without the manufacturers consent that caused it to be taken down - not sure though.

---

