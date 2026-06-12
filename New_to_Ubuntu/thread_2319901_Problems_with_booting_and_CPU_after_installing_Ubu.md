---
title: "Problems with booting and CPU after installing Ubuntu Desktop"
date: 2016-04-08
forum: New to Ubuntu
---

### Post by 1two3 on 2016-04-08
I installed Ubuntu Desktop with LVM so that I can take snapshots and so that the the HDD is encrypted. Sounds good since I do care about privacy which is one of the reasons I switched from Windows to Ubuntu. 

First thing that I did after installing it is update it completely through the Software Updater. When I restarted the computer and came to the grub 2 menu where I can select to boot Ubuntu or go to Ubuntu Advanced settings etc, I clicked Ubuntu and then the screen just goes black forever so I took out my phone as googled for what could be wrong and found out I had to press the 'e' button on the grub 2 menu and then change the letters 'ro' to 'rw' and then hit F10 to boot and it worked. I would have to do this every time I restart though -_-

Then I installed some privacy addons for firefox, enabled UFW to default setting. I'm not sure what went wrong but when I used youtube on firefox ubuntu suddenly became super slow and the firefox window would occasionaly transition opacity to dark and then back to normal. It was unbearably slow, takes forever to do one thing even just opening Terminal. 

I installed gnome-system-monitor and saw no burden on the memory but the CPU was peaking even after I closed down Firefox. 
I wrote in the Terminal "ps aux|sort -k 3|tail -n 10" and saw that kidle_inject had 3 instances running, each taking 50% CPU. 

I then "sudo rmmod intel_powerclamp" which stops the kidle_inject processes but didn't help. 

I then restart the computer but this time I couldn't get it to launch the same way as last time by editing the letters 'ro' to 'rw' but if I hit shift key directly after selecting to boot Ubuntu then it worked. 

However, I've also tried restarting another time after this and then neither the shift key or changing 'ro' to 'rw' helped so I left the computer shut off for a few hours then I came back and got it to work either through shift or changing letters method, don't remember which one I did that time. 

But the computer isn't slow anymore after restarting but I'm worried that if I watch youtube videos again it will become unbearably slow again and then I'll need to restart the computer and then I might not be able to get back in, I would just have to pray that after a few hours it will let me back in again. 

It's about 24 degrees inside my home so it's not too hot for the laptop.

---

### Post by grahammechanical on 2016-04-08
It would be useful to know the version of Ubuntu & the hardware specifications of the machine. Do include details of the video adapter, especially the amount of video memory. This makes me wonder

> I installed gnome-system-monitor

I think the system monitor is installed by default. I have it on my system & I have never installed it. I do not have LVM or even an encrypted /home let alone full disk encryption. This

> found out I had to press the 'e' button on the grub 2 menu and then change the letters 'ro' to 'rw'

means that the file system is not being put into read/write mode. It is still being left in read only mode. But with disk encryption it would take a password from you to make that change. Do, you still get a request to decrypt the hard disk? Or have you revealed a very simple method of bypassing disk encryption? I wonder.

I do suggest that once you get to a working desktop environment you go to system settings>Software & Updates>Additional Drivers tab and change video drivers. That could be the cause of the problem in the first place. A video driver conflict of some sort.

When we have a video driver conflict Ubuntu will often load with a fallback open source video driver and that works but gives a much slower response even on very capable video adapters. And that is because 3D video rendering is being done in software not in the hardware of the video adapter. If the original problem was a video driver conflict made complicated by encryption then all those CPU & video issues could be caused by running on the fallback video driver. Then what you are getting is follow-on problems because the original problem has not been dealt with.

The more layers of encryption we set up the greater the load on the CPU as it works to encrypt & decrypt in real time. If you really want to see what is happening then run top

```
top
```

or install htop

```
sudo apt-get install htop
```

load it and watch what is happening.

Regards.

---

### Post by 1two3 on 2016-04-08
> **grahammechanical said:**
> It would be useful to know the version of Ubuntu & the hardware specifications of the machine. Do include details of the video adapter, especially the amount of video memory. 


[LIST]
[*]Ubuntu 14.04 LTS 64bit
[*]Intel Core i5 3230M 2.6GHz (3.2GHz)
[*]Nvidia GeForce GT 630M with 1GB Dedicated VRAM
[*]8GB DDR3 Memory
[/LIST]



> **grahammechanical said:**
> I think the system monitor is installed by default. I have it on my system & I have never installed it. 

It's possible I didn't remember this part correctly, it's possible I didn't install it, I'm not sure any more, maybe I reinstalled it and in that case I used apt-get to do it.

> **grahammechanical said:**
> I do not have LVM or even an encrypted /home let alone full disk encryption. This means that the file system is not being put into read/write mode. It is still being left in read only mode. But with disk encryption it would take a password from you to make that change. Do, you still get a request to decrypt the hard disk? Or have you revealed a very simple method of bypassing disk encryption? I wonder.

I still need to type in a password to decrypt the disk (not the same as my user password). 

> **grahammechanical said:**
> I do suggest that once you get to a working desktop environment you go to system settings>Software & Updates>Additional Drivers tab and change video drivers. That could be the cause of the problem in the first place. A video driver conflict of some sort.

I have a list of 7 different additional video drivers to choose between.. 4 of them are nvidia binary drivers and 2 are legacy nvidia legacy drivers.. last driver is using X.Org.X server - Nouveau display driver and that's also the default selected one.

---

### Post by 1two3 on 2016-04-10
I did another reboot and nothing worked to reboot even waiting hours didn't work so I just kept trying over and over again the 2 different methods of getting it to boot successfully and then suddenly one of those times it worked. 

I decided that I can't continue like this and want to try reinstalling Ubuntu desktop but this time without LVM and encryption. 

But with the Ubuntu DVD inserted I can't even reach the grub2 menu. I'm stuck on the first screen which is the acer logo and a small text saying "Press F2 for settings" but if I press it or don't it doesn't matter, I'm stuck at that acer screen. 

Please help!

---

