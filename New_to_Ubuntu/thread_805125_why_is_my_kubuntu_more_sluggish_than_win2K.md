---
title: "why is my kubuntu more sluggish than win2K?"
date: 2008-05-23
forum: New to Ubuntu
---

### Post by evencoil on 2008-05-23
I'm a new user coming from Win2K. I was a pretty determined win2K user and tried to de-bloat that OS as much as possible. It would be great after a fresh install (and up until say a year after), but it was time for a new install, so I figured I would try something new.

I have been finding performance in Kubuntu/Ubuntu/Xubuntu (tried them all) to be quite slow and unresponsive, particularly with FireFox and also navigating my file structure. I tried using amaroK and it was sluggish to the point of being unusable. And this is all after I've turned down all of the GUI eyecandy in kubuntu.

I'm thinking that perhaps something is wrong, because this is the exact opposite of what everyone says about Linux. Linux is supposed to be fast and smooth and made for hyperactive multitaskers like myself. Right?

The only thing I can think of is that I have 2 IDE HDs and I left my win2K install on the master and have used the slave for my kubuntu partition. Would this make a difference? Anything else? I'd really like to make the switch, but the slowness is frustrating me. 

Also, my specs should be fine...Celeron 2.7 Ghz, 1 GB RAM, etc, a very run-of-the-mill box for office work, internet browsing and music playing.

Any ideas? Thanks!

---

### Post by Paqman on 2008-05-23
Ubuntu is not a light-and-fast distro. KDE is a fully-featured desktop designed for relatively modern machines. Win2K is old, and therefore very light and fast.

What are your system specs? If you're finding KDE too much for your machine you'll almost certainly se a huge improvement by switching to a lighter desktop. Try the XFCE desktop that Xubuntu uses:

[Click here to install XFCE](apt:xubuntu-desktop)

After it's downloaded, log out > Options > Select Session > XFCE and you'll be running as you'd installed Xubuntu.

If you don't like XFCE there are even lighter options that you can try like Fluxbox.

---

### Post by evencoil on 2008-05-23
celeron 2.7 Ghz
1GB RAM
some onboard video...
can't really remember the mobo specs but it was a medium line motherboard about 4 years ago when I bought it.

I tried Xfce and didn't find it to be noticeably faster than either Kubuntu or Ubuntu. This is rather disappointing...

---

### Post by starcannon on 2008-05-23
Am guessing your onboard video isn't set up correctly, would need to know what onboard video it is to assist any further though.

---

### Post by shifty_powers on 2008-05-23
have you treid fluxbuntu?

> What is Fluxbuntu?

Fluxbuntu is a modern operating system based upon the extremely successful and powerful Linux and GNU technology base.

Why Fluxbuntu?

Although there are a plethora of options available to an individual who wishes to harness a Linux / GNU environment, we believe Fluxbuntu fills an extremely important niche. Fluxbuntu was created for the user who wishes to utilize the massively popular and versatile Ubuntu distribution base while minimizing the impact on their system's resources. To this end, we firmly believe that Fluxbuntu is the wisest choice for anyone seeking a low profile operating system -- from performance enthusiasts to people who need a lightweight operating system to breathe new life into an old computer.

We know you have exceptionally high standards for your computing environment. So does Fluxbuntu.


[http://fluxbuntu.org/](http://fluxbuntu.org/)

---

### Post by Paqman on 2008-05-23
> **evencoil said:**
> 
I tried Xfce and didn't find it to be noticeably faster than either Kubuntu or Ubuntu. This is rather disappointing...

Those specs should swallow any flavour of Ubuntu with ease. I agree with starcannon, something isn't working right at all. Have you checked the Hardware Manager to see if you can install a better driver?

---

### Post by evencoil on 2008-05-23
> **starcannon said:**
> Am guessing your onboard video isn't set up correctly, would need to know what onboard video it is to assist any further though.

This is my motherboard: [http://eu.shuttle.com/archive/en/fb51.htm](http://eu.shuttle.com/archive/en/fb51.htm)

And I'm using the onboard video on it. In Kubuntu it does seem to have correctly found my video card. Although things are noticeably blurrier than in win2k...

---

### Post by shifty_powers on 2008-05-23
could you post the output of

```
lspci
```

in a terminal?

---

### Post by evencoil on 2008-05-23
lspci:

00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 02)
01:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
01:07.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 46)
01:08.0 Multimedia audio controller: Creative Labs SB Audigy (rev 03)
01:08.1 Input device controller: Creative Labs SB Audigy Game Port (rev 03)
01:08.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port

---

### Post by starcannon on 2008-05-23
[i]Mainboard: Shuttle FB51
Description: Intel Model, Intel 845GE Chipset , 1 x AGP Slot, 1 x PCI, onboard 6 channel sound, USB2.0, Firewire, onboard LAN, onboard Intel 845GE graphics, Supports Hyper-Threading, 400/533MHz FSB, Glowing Panel, Colour Shell. (Basically the same as the SB51G and SB51GB apart from the glowing panel and coloured shell)[/i]

Found that on google

---

### Post by shifty_powers on 2008-05-23
if you go system>administration>hardware drivcers, does it say restricted drivers in use?

---

### Post by Paqman on 2008-05-23
From a quick scan of the forums it seems like other people have had problems with screen resolution from that graphics card. What are running at currently? There's also a suggestion that Compiz doesn't like it. Have you tried completely disabling Compiz?

You might also want to check your BIOS, as recommended by the [Hardware  support](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsIntel) section of the wiki.

---

### Post by evencoil on 2008-05-23
no restricted drivers

running at 1280 x 1024 x 60 Hz

and I haven't tried disabling compiz...is that a good place to start?

---

### Post by shifty_powers on 2008-05-23
i would certainly say so, yes. just go system>preferences>appearance>visual effects and select none...

---

### Post by starcannon on 2008-05-23
Yeah go to System-->Preferences-->Appearance: *Doh Shifty beat me to it* :)

Click the Visual Effects Tab
Select None
Click Close

See if that makes things a bit faster for you.

I note that your board has an AGP 4x slot, it may be a good idea to get a nice Nvidia card to stab in there, with a decent little AGP card you'd likely be able to enjoy the Visual Effects if you so choose.

GL

---

### Post by shifty_powers on 2008-05-23
beat ya to it ;)

---

### Post by evencoil on 2008-05-23
Ah yeah, no I guess they aren't installed afterall. I went to System > Desktop Effects and it is greyed out and says that I need the Compiz effects engine to get Compiz Desktop Effects. So I guess its not installed. When I was installing Kubuntu I chose almost the highest performance setting as far as desktop bells and whistles.

---

### Post by starcannon on 2008-05-23
@Shifty: Yeah well my mom can beat up your mom :-P

Ha, these boards rule, can't tell you how many boards I've been to where you get no answer, here you get 10 answers and in short order hehe

---

### Post by starcannon on 2008-05-23
@evencoil:

I have no grudge against KDE, but I do have to admit when using Ubuntu I find the Gnome desktop much easier to configure; that said if you prefer KDE its well supported here at the forums as well, and is a great desktop. But I'm out of my element with it as I switched to Gnome 5 years ago and haven't messed with KDE at all since then.

With that gpu I'd turn stuff down a bit, go into bios and max out its shared memory, make sure the xserver-xorg-video-intel package is installed *System-->Administration-->Synaptic Package Manager: Search: xserver-xorg-video-intel--> if it has a green box next to it, its installed. Search the forums as well, its not a rare gpu so somebody must have it optimized and have a guide or something.

GL and consider getting a nice nvidia agp card, should be cheap or next to nothin if you hunt around ebay awhile.

---

### Post by evencoil on 2008-05-23
Ok I verified that xserver-xorg-video-intel is installed.

I initially started with Ubuntu, and changed to Kubuntu to see if things would speed up. I found a bit of improvement especially in the file browser, but still not as smooth as Win2K was.

---

### Post by evertsfnic on 2008-05-23
I thinks you are right....
I like the idea of ubuntu, but it's true.
Xp Run faster than ubuntu
but
Ubuntu runs faster than vista. and they have more function than xp
or trying to say that they have more tecnology....... than xp

---

### Post by PrimoTurbo on 2008-06-11
In my experience Windows is **a lot faster** and responsive then Linux. I have never had a distro preform faster for me, no matter what optimizations I used.

---

### Post by ad_267 on 2008-06-11
> **PrimoTurbo said:**
> In my experience Windows is **a lot faster** and responsive then Linux. I have never had a distro preform faster for me, no matter what optimizations I used.

I have to disagree. In my experience, Ubuntu has been a lot faster than Windows. I just read that the worlds new [fastest supercomputer]("http://www.networkworld.com/news/2008/060908-ibm-roadrunner-supercomputer.html?page=2") is running Linux. Wouldn't IBM be using Windows if they thought it was faster? I think there is something about your machine that just doesn't like Ubuntu, or something about Ubuntu that doesn't like your machine. Maybe you could try another distribution like Fedora and see if that helps.

---

### Post by stalkier on 2008-06-11
> **ad_267 said:**
> I have to disagree. In my experience, Ubuntu has been a lot faster than Windows. I just read that the worlds new [fastest supercomputer]("http://www.networkworld.com/news/2008/060908-ibm-roadrunner-supercomputer.html?page=2") is running Linux. Wouldn't IBM be using Windows if they thought it was faster? I think there is something about your machine that just doesn't like Ubuntu, or something about Ubuntu that doesn't like your machine. Maybe you could try another distribution like Fedora and see if that helps.

I have to agree with you. I have found new life in my old AMD Athlon XP system using Ubuntu over XP. I added a GB of DDR and now is screams compaired to how it performed with XP. It is almost as fast as my Dual-Core system.

---

### Post by flyingtiger on 2008-06-12
> **evencoil said:**
> This is my motherboard: [http://eu.shuttle.com/archive/en/fb51.htm](http://eu.shuttle.com/archive/en/fb51.htm)

And I'm using the onboard video on it. In Kubuntu it does seem to have correctly found my video card. Although things are noticeably blurrier than in win2k...

If you have an onboard video, it's a chip not a video card. Onboard video chips steal some of your system RAM, while video cards have their own video RAM, aka VRAM.

---

