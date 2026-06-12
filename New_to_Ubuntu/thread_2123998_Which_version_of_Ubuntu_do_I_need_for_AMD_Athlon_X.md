---
title: "Which version of Ubuntu do I need for AMD Athlon XP 3200+ CPU?"
date: 2013-03-09
forum: New to Ubuntu
---

### Post by Cheesenacho on 2013-03-09
Hello everyone, I am completely new to the Linux/Ubuntu and have been curious to try the OS. I have an older computer with a wiped hard drive and downloaded Ubuntu 12 (AMD) version from the website, but when I try to install, it states that I need an i686 version. Where can I find that version to install? Are there alternatives??Thanks in advance,  CN

---

### Post by arpanaut on 2013-03-09
From this page: [http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)

Download the 32bit iso. Best bet the 12.04 LTS release supported through 2017.
There is instruction on that page to get the iso on cd/dvd/usb. in order to try and/or install.

---

### Post by stinkeye on 2013-03-09
> **Cheesenacho said:**
> Hello everyone, I am completely new to the Linux/Ubuntu and have been curious to try the OS. I have an older computer with a wiped hard drive and downloaded Ubuntu 12 (AMD) version from the website, but when I try to install, it states that I need an i686 version. Where can I find that version to install? Are there alternatives??Thanks in advance,  CN
You may be confused by the use of AMD in the  download name.
The original  64bit specification was created by AMD and is just a naming convention.
Linux distributions use AMD64 to signify 64bit OS installable on intel or amd 64bit processors.

amd64 ...64bit (intel or amd)
i386  ...32bit (intel or amd)

---

### Post by fiodev on 2013-03-09
If you have 4 gigs of ram use the 64 bit. 64 bit OS uses more ram and processor power inherently.
Use the 32 bit i386 for better performance and stability.

---

### Post by fiodev on 2013-03-09
You may also want to consider adjusting the swapiness to something less aggresive. I have a machine with 2 gigs of ram and the swap rarely gets used, so using resources to prepare for swap is somewhat pointless and does not help me. 
Here is a short video for educating:
[http://www.youtube.com/watch?v=vwBoHZuauL8](http://www.youtube.com/watch?v=vwBoHZuauL8)

---

### Post by Paqman on 2013-03-09
> **fiodev said:**
> If you have 4 gigs of ram use the 64 bit. 64 bit OS uses more ram and processor power inherently.
Use the 32 bit i386 for better performance and stability.

64-bit uses marginally more RAM, but is faster. Choice of 32-bit or 64-bit will not affect stability. 

You should only use the 32-bit if you have <1GB of RAM or you have a 32-bit only CPU. For every other machine 64-bit is the way to to.

---

### Post by Cheesenacho on 2013-03-09
> **fiodev said:**
> You may also want to consider adjusting the swapiness to something less aggresive. I have a machine with 2 gigs of ram and the swap rarely gets used, so using resources to prepare for swap is somewhat pointless and does not help me. 
Here is a short video for educating:
[http://www.youtube.com/watch?v=vwBoHZuauL8](http://www.youtube.com/watch?v=vwBoHZuauL8)

I will certainly check out the video...thanks for the advice.  I have downloaded the 32 bit version mentioned above and it is installing now. I resurrected this computer this morning with a new power supply and my thought was to put it in a guest bedroom to give people access to a computer, and I hope that it will work with XBMC. Since this computer only has 2 gigs of ram and an older processor, I'm not sure it will have enough horse power. On a positive note, at least I get to see how this OS works... I am curious about the swapiness mentioned and would like to investigate that once I have the OS loaded and I'm able to use it. I appreciate all the help...you guys are great!   CN

---

### Post by fiodev on 2013-03-09
Also go into gedit go to preferences plugins and turn off the file browser plugin. It has a bug that can effect the performance of your machine. I do this and it is the single greatest performance boost for my AMD turion 64. Ubuntu goes from laggy to snappy for me with that one option.

---

### Post by fiodev on 2013-03-09
Welcome to Linux!

---

### Post by Paqman on 2013-03-09
> **Cheesenacho said:**
> I hope that it will work with XBMC. Since this computer only has 2 gigs of ram and an older processor, I'm not sure it will have enough horse power.

The main thing that will affect performance of video playback in XBMC will be the graphics card. If the card in the machine isn't up to scratch try and find out what kind of graphics port it has on the motherboard. If it has an old AGP slot you're in trouble as those cards are pretty rare, but if it's PCI-Express then you can pick up a card good enough for HD video playback very cheaply. I would just get a second hand one off Ebay. Something like an Nvidia 8XXX card would be plenty good enough.

---

### Post by Cheesenacho on 2013-03-09
> **Paqman said:**
> The main thing that will affect performance of video playback in XBMC will be the graphics card. If the card in the machine isn't up to scratch try and find out what kind of graphics port it has on the motherboard. If it has an old AGP slot you're in trouble as those cards are pretty rare, but if it's PCI-Express then you can pick up a card good enough for HD video playback very cheaply. I would just get a second hand one off Ebay. Something like an Nvidia 8XXX card would be plenty good enough.    -----------> So, the OS is loaded and it's doing updates. I have downloaded XBMCBuntu, and it's an ISO file...how do you install the ISO files? Seems it wants to burn it to a disk versus install...is there a program that I need to install before I can do this? And what's the deal with not being able to get a carriage return when you post a reply????

---

### Post by Cheesenacho on 2013-03-09
So, the OS is loaded and it's doing updates. I have downloaded XBMCBuntu, and it's an ISO file...how do you install the ISO files? Seems it wants to burn it to a disk versus install...is there a program that I need to install before I can do this?

---

### Post by sanderj on 2013-03-09
> **Cheesenacho said:**
> So, the OS is loaded and it's doing updates. I have downloaded XBMCBuntu, and it's an ISO file...how do you install the ISO files? Seems it wants to burn it to a disk versus install...is there a program that I need to install before I can do this?

If XBMCBuntu is an ISO, it's probably an OS installation disk by itself. So ... burn it to CD/DVD, boot it, and see if it offers to install to your disk. It will overwrite the Ubuntu you just installed ...

---

### Post by Cheesenacho on 2013-03-09
> **sanderj said:**
> If XBMCBuntu is an ISO, it's probably an OS installation disk by itself. So ... burn it to CD/DVD, boot it, and see if it offers to install to your disk. It will overwrite the Ubuntu you just installed ... That concerns me as I needed to download a 32 bit AMD version...I guess I can try, and it doesn't work, then it shouldn't install...let me try that...thanks!

---

### Post by stinkeye on 2013-03-09
> **Cheesenacho said:**
> That concerns me as I needed to download a 32 bit AMD version...I guess I can try, and it doesn't work, then it shouldn't install...let me try that...thanks!
xbmc is available in the software centre. Just install from there.

---

### Post by Paqman on 2013-03-09
> **stinkeye said:**
> xbmc is available in the software centre. Just install from there.

+1

Or just to make things even easier, just click this: [xbmc]("apt:xbmc"), and it'll open software centre for you :)

---

### Post by sanderj on 2013-03-10
> **stinkeye said:**
> xbmc is available in the software centre. Just install from there.

Really? I expect a lot of configuration that way.

With the XMBCubuntu.iso I expect everything to be pre-configured and/or a smart wizard. So ... easier.

---

### Post by stinkeye on 2013-03-10
> **sanderj said:**
> Really? I expect a lot of configuration that way.

With the XMBCubuntu.iso I expect everything to be pre-configured and/or a smart wizard. So ... easier.
He's already installed ubuntu.
So for quick a test, installing through software centre seems easier to me.

I think Cheesenacho needs a bit more understanding of different install methods
and maybe explain if he wants to use the computer solely for xbmc.

---

### Post by Paqman on 2013-03-11
> **sanderj said:**
> Really? I expect a lot of configuration that way.


Not really. The only thing I had to do after installing it on my HTPC was point it at the location of my files and switch on VDPAU in the video settings.

---

