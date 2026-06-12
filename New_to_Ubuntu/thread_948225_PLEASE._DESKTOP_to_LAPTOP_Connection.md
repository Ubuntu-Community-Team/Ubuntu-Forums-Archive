---
title: "PLEASE. DESKTOP to LAPTOP Connection?"
date: 2008-10-15
forum: New to Ubuntu
---

### Post by Parasitesss on 2008-10-15
I have a desktop computer which is currently running Ubuntu. My desktop also has a windows partition that contains some really valuable family videos. I want to transfer the **videos** from the Windows Partitions to my MacBook. How would I go about doing so?

---

### Post by eentonig on 2008-10-15
Do you have a network/Local LAN?

---

### Post by mdecler2 on 2008-10-15
Do you have access to the Windows partition? Is the Windows partition mounted when you run Ubuntu? I see two options:

1. Boot Windows, load your videos on to a flash drive and copy them over
2. Boot Ubuntu, mount the windows partition, insert your flash drive and mount it, then copy things over and unmount it.

---

### Post by namegame on 2008-10-15
There are Windows applications that allow you to access Ext2/Ext3 partitions from within Windows. 

[http://www.chrysocome.net/explore2fs](http://www.chrysocome.net/explore2fs)
[http://www.fs-driver.org/index.html](http://www.fs-driver.org/index.html)
[http://www.diskinternals.com/linux-reader/](http://www.diskinternals.com/linux-reader/)

---

### Post by mdecler2 on 2008-10-15
> **namegame said:**
> There are Windows applications that allow you to access Ext2/Ext3 partitions from within Windows. 

[http://www.chrysocome.net/explore2fs](http://www.chrysocome.net/explore2fs)
[http://www.fs-driver.org/index.html](http://www.fs-driver.org/index.html)
[http://www.diskinternals.com/linux-reader/](http://www.diskinternals.com/linux-reader/)
I think the question is about accessing videos on a Windows partition from an Ubuntu partition, not the other way around. Accessing a windows partition is as easy as mounting that partition, or simply going into that directory if it is already mounted.

---

### Post by namegame on 2008-10-15
> **mdecler2 said:**
> I think the question is about accessing videos on a Windows partition from an Ubuntu partition, not the other way around. Accessing a windows partition is as easy as mounting that partition, or simply going into that directory if it is already mounted.

I think we all misunderstood.

I think the OP wants to move files from his Windows partition on his Desktop to his Mac laptop.

For that I would suggest using a CD or Flashdrive. I don't think you could "link" them together, unless you had a home-network set up.

---

### Post by Parasitesss on 2008-10-15
Yes, That's what I want to do namegame!
Just so you know, I have around 80Gs of video I need transfered.

I can't use the CD option cause I my burner broke. But is the Flashdrive the ONLY option?

What about this network thing you guys are talking about?

---

### Post by JeeZiTsDave on 2008-10-15
Well, you can go and buy an external harddrive.  I mean you might only use it once, but you might find it for other uses.  Especially on a MacBook for Time Machine.  Any size will go.  Of course, if there is enough space to hold all of the data that you want to keep.

---

### Post by eentonig on 2008-10-16
Several directions you can take.

- Buy an USB Flashdrive or External HD and copy over the needed files to this device. Then copy them from the USB drive to the other computer.

- Spent a few bucks on a little switch/Wireless AP/Router and connect the two pc's via a network. This way, you can access (with some additional configuration) information from one computer on the other one.


Option 2 is the most technical, but also the most flexible. You could use this for internet sharing i.e.

Option 1 is the cheapest and fastest.

---

### Post by woodenbrick on 2008-10-16
I have been able to do this just by connecting an ethernet cable between the two computers.

---

### Post by Sarmacid on 2008-10-16
Yes, you can just plug the 2 computers with an ethernet cable, just make sure it is crossover cable. And if your macbook can access files through samba, you should try this [https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

---

### Post by PcTestCard.com on 2008-10-16
Why not use a cross over cable to link 2 PCs together and transfer the files?

Maybe a USB to USB cable can do the job as well.

---

### Post by Parasitesss on 2008-10-16
Thank you all for your replies, I know its a bit cliche but I APPRECIATE IT SOO MUCH!

I will try the ethernet connect between my ubuntu and macbook!

ps. once pluged in, does ubuntu immediately recognize it? or do I have to configure it?

---

### Post by bobheaps on 2008-10-17
Is it just as easy as that?
Have you any more details - I have the same situation

---

### Post by namegame on 2008-10-17
> **bobheaps said:**
> Is it just as easy as that?
Have you any more details - I have the same situation

I would make a new thread. Since this one has been resolved.

---

### Post by Sarmacid on 2008-10-17
Parasitesss sent me a private message and this is what I told him, should be helpful to you.

> I'm not sure how to configure your network in the macbook, but on ubuntu, just pick an ip like 172.16.100.1 and run in a console

```
sudo ifconfig eth0 172.16.100.1 netmask 255.255.255.0
```

The macbook should have an ip in the 172.16.100.* range, so 172.16.100.2 should do. After configuring your macbook, run

```
ping <macbook ip>
```

If it works, then that means ubuntu can see the macbook.

---

