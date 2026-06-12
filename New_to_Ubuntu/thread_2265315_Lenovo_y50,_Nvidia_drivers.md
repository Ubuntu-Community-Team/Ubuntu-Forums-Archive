---
title: "Lenovo y50, Nvidia drivers"
date: 2015-02-14
forum: New to Ubuntu
---

### Post by jerephi on 2015-02-14
Hi, I completely messed over my comp trying to do this on my own (black screen), have tried googling this and not getting anywhere, and posted to reddit but it got burried with no replies.  I have ubuntu on my laptop, it recognizes the integrated graphics but I assume not the graphics because games look bad.  I downloaded the linux driver from intel, but I click it and it goes to text pad or whatever, I tried doing many many things and I'm super dumb and frustrated right now. If anyone could help that would be awesome.

---

### Post by nerdtron on 2015-02-14
What is the model of the laptop? What version of Ubuntu?

Have you tried Step 8 only from this link: [http://howtoubuntu.org/things-to-do-after-installing-ubuntu-14-04-trusty-tahr](http://howtoubuntu.org/things-to-do-after-installing-ubuntu-14-04-trusty-tahr)

---

### Post by jerephi on 2015-02-14
lenovo y50 12.04.1, yeah, it says no additional drivers found.  Actually just black screened myself for the second time and am torn between installing ubuntu again or just reinstalling windows.  :(

---

### Post by nerdtron on 2015-02-14
12.04 is abit old. Latest kernels on latest Ubuntu 14.04 may (or may not) added support to new hardware drivers. It might be worth a try. Also 14.04 feels faster than 12.04.

And don't give up on linux. You can even try Xubuntu or Kubuntu, or Linux Mint (see link on my signature). They are all the same Ubuntu just different Desktop GUI.

---

### Post by jerephi on 2015-02-14
ok sorry 14.04 i just downloaded it

I really want to get it to work, mostly cause I don't like the idea of an operating system beating me, but I dunno, man, I thought the biggest negative to linux would be its lack of support for various programs.  I figured hey, np, I can go without some games and whatever.  But man, after following instructions on the internet twice and blackscreening my computer, and then spending hours and hours trying to things that to me seem simple to me, like getting netflix to work or updating or installing a graphics driver, I just don't know if I can make it. 

I do like linux from what I've used, I think it has a nice feel to it, but I've litterally spent hours and hours on just trying to get my graphics card to work.  It's frustrating.

And then I'm like, is this what it's going to be like every time there's a driver update? I'm going to have to go through this madness? Now it's just a waste of time, but if this happens when there's something on my comp I really don't want to lose...

---

### Post by gregor-skrt on 2015-02-16
Did you manage to install nvidia drivers on the end ? I'm still struggling with installation..after switching to nvidia-340 driver my kernel dies which didn't happen in whole 14 years as a Linux user.

Ok: 15 min later for anyone looking for same information about installing nvidia gtx 860m on a Y50 4k laptop **story goes like this**: 

install edgers repository and nvidia-346 driver: 

> sudo add-apt-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install nvidia-346

It works ...

I'm not sure what was problem with my previous installs. I suspect I had wrong resolution when installing. 

More info here: [http://forum.notebookreview.com/threads/y50-linux-thread.756405/page-5](http://forum.notebookreview.com/threads/y50-linux-thread.756405/page-5)

---

### Post by gregor-skrt on 2015-02-16
Ahm ahm :) well ...again same problem after few successful boots black screen of death ! So sad....

Hopefully final destination :( [URL="http://ubuntuforums.org/showthread.php?t=2262882&page=12"]

http://ubuntuforums.org/showthread.php?t=2262882&page=12[/URL]

---

### Post by JDAIII on 2015-03-04
So I have the Lenovo y-50 4k with the NVIDIA GeForce GTX 860M vidjo card. It is not being recognized by the OS, only the onboard intel gpu is being recognized. I tried many of the xorg-edgers and they gave me the black screen of death. I noticed people saying that they re-installed ubuntu at this point, which I did 2 or 3 or 30 times. But it seemed to resolve the issue when I reverted to the older driver.  I was able to recover by going to runlevel 3 and removing nvidia-346 and nvidia-opencl-icd-346 and installing nvidia-opencl-icd-331. Now someone mentioned in another thread that using a different repo works instead of xorgedgers. I'm wondering if the two guys in here have been able to do anything to get their y50s to take the Nvidia drivers properly as I would like to take advantage of the 2GB video ram just sitting there unused.

@gregor-skrt - I'm the same JDAIII from the notebookreview post so I'm there with you. You can see my list of attempts over the last few months. Let me know if you found anything that works.

I saw the other post at [http://ubuntuforums.org/showthread.php?t=2262882&page=12](http://ubuntuforums.org/showthread.php?t=2262882&page=12) and I'm slowly sorting through it for more details. Let me know if this non-xorgedgers repo worked for you.


Edit: Let me clarify that Ubuntu still does not recognize my nvidia card. Everything I have done has not allowed me to boot into gnome using the nvidia card, it always reverts to the black screen of death.


BTW, i did a lshw -C display and then I did an lspci. This is what I see.
```

 &#10140; sudo lshw -C display                                                      ~ 
  *-display UNCLAIMED     
       description: 3D controller
       product: GM107M [GeForce GTX 860M]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
       resources: memory:d0000000-d0ffffff memory:a0000000-afffffff memory:b0000000-b1ffffff ioport:4000(size=128) memory:b2000000-b207ffff
  *-display
       description: VGA compatible controller
       product: 4th Gen Core Processor Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 06
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:47 memory:d1000000-d13fffff memory:c0000000-cfffffff ioport:5000(size=64)



 &#10140; lspci -nnk | grep -iA3 vga                                                ~ 
00:02.0 VGA compatible controller [0300]: Intel Corporation 4th Gen Core Processor Integrated Graphics Controller [8086:0416] (rev 06)
        Subsystem: Lenovo Device [17aa:3978]
        Kernel driver in use: i915
00:03.0 Audio device [0403]: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller [8086:0c0c] (rev 06)




```

And when I run dpkg -l | grep nvidia, I can see that I have some drivers installed, but not everything. As mentioned above, I did remove two applications and reinstall nvidia-opencl-icd-331. Looks like a mess to me from my repeated attempts to install other version. I'm afraid to remove these as I'm not quite sure how my machine will react and it's my primary work computer and is required daily.

```

 &#10140; sudo dpkg -l | grep nvidia                                                ~ 
rc  nvidia-340                                  340.65-0ubuntu1~xedgers14.10.1                         amd64        NVIDIA binary driver - version 340.65
rc  nvidia-346                                  346.35-0ubuntu1~xedgers14.10.1                         amd64        NVIDIA binary driver - version 346.35
ii  nvidia-opencl-icd-331                       331.113-0ubuntu1~xedgers14.10.1                        amd64        NVIDIA OpenCL ICD
rc  nvidia-opencl-icd-346                       346.35-0ubuntu1~xedgers14.10.1                         amd64        NVIDIA OpenCL ICD
rc  nvidia-prime                                0.6.7                                                  amd64        Tools to enable NVIDIA's Prime
rc  nvidia-settings                             346.35-0ubuntu1~xedgers14.10.1                         amd64        Tool for configuring the NVIDIA graphics driver

```

---

