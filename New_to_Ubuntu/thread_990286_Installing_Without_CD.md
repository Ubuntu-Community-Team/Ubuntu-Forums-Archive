---
title: "Installing Without CD?"
date: 2008-11-22
forum: New to Ubuntu
---

### Post by Azhtabak on 2008-11-22
Hello all. I've just started down the path converting from windows (evil!) to linux (yay!) and have a few questions.

1.) I've downloaded the distrobution from this site, but my CD drive doesn't really work, and I have a distinct lack of blank CDs - is it possible to install Ubuntu without having to burn the CD? If so, how do I do this? I'm guessing just run it like a normal installer, but I'm afraid to try in case I mess up and delete everything.

2.) I would like to keep windows installed as well, (Yes, evil, I know :P ) mostly because I have lots of important data and various games on it. I know its possible to run both of them, but how do I set that up?

---

### Post by shifty_powers on 2008-11-22
have you looked at wubi?

[http://wubi-installer.org/](http://wubi-installer.org/)

---

### Post by taurus on 2008-11-22
Maybe one of these methods works for you.

[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

---

### Post by Azhtabak on 2008-11-22
I am awed by your fast responses.

So, after quickly glancing at Wubi, that seems to do what I want - so I install Wubi, run Wubi (Which contains Ubuntu? judging by the file size, I guess?) and then when I next load windows (evil!) it asks me if I want to run ubuntu on top of that, and I can exit from ubuntu to windows at any time?

Sorry for all the probably obvious questions, I'm very new to all this :)

---

### Post by shifty_powers on 2008-11-22
not quite. yes, you download the wubi software. this will then download a cd image of ubuntu which it will install ubuntu from. this will appear as a file on your windows partition.

when you reboot you will have a boot menu where you can choose which os to go into. once booted though, you cannot switch without rebooting.

to uninstall it is as simple as going into add/remove programs of windows control panel...

---

### Post by Azhtabak on 2008-11-22
Thanks :)

If I then install it onto a partition, do I still need the virtual hard drive thing and the spare memory, or will that be taken care of by Wubi? I think so, based off what the FAQs on the Wubi site are saying, but I'd prefer to confirm :)

Also, will I be able to run programs currently installed on windows within Ubuntu this way, or will I have to reinstall them seperately within Ubuntu? Or is there some kind of handy file-transfer system between them?

Again, sorry for all the obvious questions, and thanks again in advance :)

---

### Post by shifty_powers on 2008-11-22
you need spare hard drive space yes.

but you are only running one os at a time.

so if you run ubuntu, it will have all of the system ram available to it, as windows is not running.

windows programs generally do not run in ubuntu. they are two different os. just as mac osx programs won't run in windows and vice versa.

ubuntu will come with many programs pre installed, and there are thousands that can be downloaded from the repositories.

have a look at

[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

---

### Post by Azhtabak on 2008-11-22
Ooh, clever, so I effectively double my space?

I know most programs won't run on Ubuntu, but what about transferring over various files? I have several useful word documents, videos, etc that would be a pain to have to rewrite/download - is there an easy file transfer between the two, or will I have to go to a third party file host or something?

---

### Post by shifty_powers on 2008-11-22
heh no, it is not some tardis, dr who like thing....

when you install wubi and create the ubuntu drive, it creates a file that takes space up on the windows partition.

so as you use space in ubuntu, the available space in windows goes down...

but it is a good way of trying ubuntu whilst keeping windows...

---

### Post by Azhtabak on 2008-11-22
Ah, I see, thanks :)

Well, I'm off to try installing it then :) I'm guessing this is one of those programs that I should listen to when it says to close everything else first?

---

### Post by shifty_powers on 2008-11-22
well i suppose so, but windows installers always say that.

but better safe than sorry.

good luck and any questions give us all a shout :D

---

### Post by ranch hand on 2008-11-22
I live on dial up so I can't download the CD.  If your CDrom will read you could go this way <http://linuxcd.org/>.

Fast service and then you will be running the real thing without Win concerns.

---

### Post by Azhtabak on 2008-11-22
It is now installed and working (yay!) but I am experiencing a minor problem - I have no internet, and can't seem to get to my windows files. I'm guessing the two are related, as it won't let me on my windows network, and tells me that there is no network connection.

My windows has this problem as well, saying sometimes that 'a local area network cable is unplugged', but can still connect to my wireless network - how do I make ubuntu do the same?

---

### Post by sportscrazed2 on 2008-11-22
your wireless card might have a restricted driver for it go to system>adminiistratin>hardware drivers and check

---

### Post by Azhtabak on 2008-11-22
Ok - in windows or ubuntu? And where do I find that?

---

### Post by sportscrazed2 on 2008-11-22
its in ubuntu under system

---

### Post by billgoldberg on 2008-11-22
> **Azhtabak said:**
> Hello all. I've just started down the path converting from windows (evil!) to linux (yay!) and have a few questions.

1.) I've downloaded the distrobution from this site, but my CD drive doesn't really work, and I have a distinct lack of blank CDs - is it possible to install Ubuntu without having to burn the CD? If so, how do I do this? I'm guessing just run it like a normal installer, but I'm afraid to try in case I mess up and delete everything.

2.) I would like to keep windows installed as well, (Yes, evil, I know :P ) mostly because I have lots of important data and various games on it. I know its possible to run both of them, but how do I set that up?

I haven't read the reactions yet, but sure it's perfectly possible to do this.

First you'll need an usb stick or and external usb drive.

Format it (if it has partitions, make sure you use the first one) to fat32 and give it a boot flag.

You can use a multitude of windows programs for this, google it.

Download and instal "unetbootin" and use it to install the ubuntu .iso to the usb stick or external usb drive.

Now you can boot from the usb. Make sure your usb drive is set as the first boot device in your bios.

--

I also see you want to dual boot, simply create a new partition on you hard drive. The bare minimum would be 4gb or something, but the more the better.

While installing Ubuntu, tell it to install on that newly create partition.

When it's done and you restart the pc, you will be able to either start Ubuntu or Windows.

[I](note, if you are new to this, it may seem a bit hard, but it really isn't that hard once you have done it once.

note2, see the codecs in ubuntu link in my signature. Once you installed Ubuntu, you'll find it useful)[/I]

---

### Post by Azhtabak on 2008-11-22
> **sportscrazed2 said:**
> your wireless card might have a restricted driver for it go to system>adminiistratin>hardware drivers and check


'No proprietry drivers could be found'.

That sounds bad :(

---

### Post by billgoldberg on 2008-11-22
Ok, I see you went with an Wubi install.

I wouldn't use that, as it might create some problems, or so I heard.

--

In Ubuntu, open up a terminal (applications -> accessories) and give use the output of this command:

```
lspci
```

---

### Post by Azhtabak on 2008-11-22
Ok, it gives me:

```

00:00.0 Host bridge: VIA Technologies, Inc. VT8385 [K8T800 AGP] Host Bridge (rev 01) 
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South] 
00:0b.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03) 
00:0d.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04) 
00:0d.1 Input device controller: Creative Labs SB Audigy Game Port (rev 04) 
00:0d.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port (rev 04) 
00:0e.0 RAID bus controller: Integrated Technology Express, Inc. IT/ITE8212 Dual channel ATA RAID controller (rev 11) 
00:0f.0 RAID bus controller: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80) 
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06) 
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81) 
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81) 
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81) 
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81) 
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86) 
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South] 
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60) 
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78) 
00:13.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10) 
00:14.0 FireWire (IEEE 1394): Texas Instruments TSB82AA2 IEEE-1394b Link Layer Controller (rev 01) 
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration 
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map 
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller 
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control 
01:00.0 VGA compatible controller: nVidia Corporation NV25 [GeForce4 Ti 4200] (rev a3) 
azhtabak@ubuntu:~$ 

```

That took far too long to do :( :P

---

### Post by Azhtabak on 2008-11-23
Bump? I'm still having this problem...

(Sorry if that's not allowed here, I'm not sure, and I could really use some help :( )

---

### Post by shifty_powers on 2008-11-23
sorry, i do have to sleep you know ;)

what is the output of 

```
sudo iwlist scan
```

---

### Post by Azhtabak on 2008-11-24
It asks me for my password, then gives me:

```

lo        Interface doesn't support scanning. 
 
eth0      Interface doesn't support scanning. 
 
eth1      Interface doesn't support scanning. 
 
wmaster0  Interface doesn't support scanning. 
 
wlan0     Interface doesn't support scanning : Network is down 
 
pan0      Interface doesn't support scanning.

```

Is there a way I can learn to do all this sort of stuff myself, btw? I don't suppose there's any 'how to program Ubuntu' guide lying around? :P

---

