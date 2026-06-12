---
title: "ubuntu 16.04 is slow &amp; has poor performance , Why?"
date: 2016-04-29
forum: New to Ubuntu
---

### Post by 2sourcez on 2016-04-29
1-1.5 years age i installed the previous version of ubuntu (i think it was 15.*) in my VM , i was so happy because it had  excellent performance with my Limited power of my computer so i think about if ubuntu has all power of my computer it can be awesome so i decided to install it alongside of windows 8 & it turns to be my only Os but with my problems i missed it .
 3-4 days ago i download ubuntu 16.04 & install it alongside my windows 10 & with very happy face i boot ubuntu but i see poor performance& it is slow , i download a deb but i can't install it because i wait for 30 minutes  but it wasn't install .

---

### Post by oldos2er on 2016-04-29
Please post your hardware specs.

> i download a deb but i can't install it because i wait for 30 minutes  but it wasn't install. This is a known bug: [https://bugs.launchpad.net/ubuntu/+source/gnome-software/+bug/1573408](https://bugs.launchpad.net/ubuntu/+source/gnome-software/+bug/1573408)

---

### Post by 2sourcez on 2016-04-29
[RIGHT][LEFT]Intel Core i5 4200M 2.50GHz up to 3.10 GHz[/LEFT]
[/RIGHT]
8GB Ram

[RIGHT][LEFT]NVIDIA GeForce GT 740M 2GB




[/LEFT]
[/RIGHT]

---

### Post by oldos2er on 2016-04-29
Laptop or desktop? Have you tried installing Nvidia proprietary drivers?

---

### Post by wildmanne39 on 2016-04-29
Please> Use color and font properties for highlighting portions of your text, and not for all of the text in your post. Please use the default font color and properties unless you need to highlight or draw attention to a part of your post. ALL CAPS is interpreted as screaming. Funky non-uniform font size/color is difficult for those who are visually impaired. If you are having problems with reading the font, please adjust your browser.
[http://ubuntuforums.org/showthread.php?t=2158945](http://ubuntuforums.org/showthread.php?t=2158945)

---

### Post by groenem on 2016-06-25
I also have the same problem. Everything was working fine with 15.10, but after upgrading to 16.04 my PC is very slow. I have a Intel® Core&#8482;2 Duo CPU E7500 @ 2.93GHz × 2, with 1GB RAM. Graphics card is a Gallium 0.4 on AMD RV730 (DRM 2.43.0, LLVM 3.8.0).
My Kodi also played seamlessly with previous 15.10, now playback is very slow with big mkv files. I have installed the ubuntu-extra-codes, but it does not help either. I am very disappointed with 16.04. It is even worse than Windows currently.

---

### Post by Mark Phelps on 2016-06-25
[groenem]("groenem")

The problem is most likely to be that fglrx is no longer supported with Ubuntu 16.04, as AMD is working on a new open-source driver to replace it.

That means you probably do NOT have hardware accelerated video anymore, and while this would not be noticeable in routine desktop graphics, it would be noticeable with anything the plays video.

As far as I know, there is no "fix" for this -- other than to wait for AMD to release their new drivers.

---

### Post by banceu_sergiu_ione on 2016-06-25
> **groenem said:**
> I also have the same problem. Everything was working fine with 15.10, but after upgrading to 16.04 my PC is very slow. I have a Intel® Core™2 Duo CPU E7500 @ 2.93GHz × 2, with 1GB RAM. Graphics card is a Gallium 0.4 on AMD RV730 (DRM 2.43.0, LLVM 3.8.0).
My Kodi also played seamlessly with previous 15.10, now playback is very slow with big mkv files. I have installed the ubuntu-extra-codes, but it does not help either. I am very disappointed with 16.04. It is even worse than Windows currently.

With only 1gb Ram you wont going to ran 16.04. Here are the[ requirements]("https://wiki.ubuntu.com/XenialXerus/ReleaseNotes/UbuntuGNOME"), and people have to read it first and not after wondering what is going wrong.

You may want to try Ubuntu Mate or Lubuntu or same other [flavours]("https://wiki.ubuntu.com/XenialXerus/ReleaseNotes") that your pc. spec. support.

---

### Post by Geoffrey_Arndt on 2016-06-25
Really, your best option is to do a fresh install of 14.04, install the proprietary driver, and hopefully later this year or early next, the AMD people will release their open source driver for your gpu.    Remember, 14.04 is supported through April 2019.

(and maybe an upgrade to 2 GiB of RAM would also work wonders while waiting for new drivers to become available).

---

### Post by andmey on 2016-08-16
I know  I am late, but this fixed everything for me: [http://askubuntu.com/questions/761429/kubuntu-16-04-driver-manager-broken](http://askubuntu.com/questions/761429/kubuntu-16-04-driver-manager-broken) 

Summary: update your drivers. In the linked thread its perfectly explained how it works.

---

### Post by Luke M on 2016-09-01
I had the same symptom of extremely bad performance, as if something was taking 95% of the CPU, after upgrading to 16.04. It seems to be caused by the nouveau driver in Linux 4.4. Installing the nvidia closed source driver fixed the problem.

---

### Post by Fernando_Rosas on 2016-11-15
I am having a lot of problems with my system as well. I read everything and went through every link shared in this thread to no avail. The main issue is that everytime I open youtube, amazon or pages with large amount of flash content, my computer starts to slow down and it takes a long time to render the page or video. Video on youtube is choppy as well as streaming media. When using Darktable and Blender, the programs also slow down a lot and is hard to have a proper workflow at those speeds. When playing video or running Kodi, I have no issues and video runs smoothly whith it's known hiccups related to Linux. I was even thinking about getting new equipment but as I keep reviewing my specs, I realize I don't need new gear but some solution.
The specs are:
Ubuntu 16.04.1 Xenial
Asus Laptop N53Jq
Core  i7 Q 740 @ 1.73GHz (8 threads)
16 GB RAM (4GB x 4) DDR3
HDD SSD Corsair 120GB
HDD Seagate 500 GB
GeForce GT 425M 1024MB @560MH DDR3 Videocard

As you can see, I should be able to run everything smoothly but quite the contrary. I used to be able to use Blender (3d software) without any problems and also Darktable (Post Processing Photo software) and now my workflow is struggling. If someone has any hints that could be thrown at me I will really appreciate it. I've been a linux user for a long time and although I'm not a guru, I know my way around it. Thank you very much in advance for your help.

Fernando Rosas

---

### Post by mörgæs on 2016-11-16
Yes, the hardware looks fine (and much stronger than anything in my household). 
Which drivers for the graphics processor are you using?

---

### Post by Fernando_Rosas on 2016-11-20
I'm sorry for not replying answer, somehow I turned off my notifications and I kept waiting an email notification.
Anyway, I get this:

```
lspci -nnk | grep -i vga -A3
```
```
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GF108M [GeForce GT 425M] [10de:0df0] (rev a1)
    Subsystem: ASUSTeK Computer Inc. GF108M [GeForce GT 425M] [1043:1522]
    Kernel driver in use: nvidia
    Kernel modules: nvidiafb, nouveau, nvidia_367, nvidia_367_drm
```

I'm not sure if there's a better video driver to use or if this is the only one/better to use.
Thank you.

---

### Post by Fernando_Rosas on 2016-11-20
I should mention that I just finished updating/upgrading ubuntu after a painful process of "Not enough space in boot partition" but finally updated everything. Everything seems a bit faster but as soon as I get some flash content, somehow everything gets dreadfully slow. Not sure what's going on...

---

### Post by luz3448 on 2017-01-05
To add my two cents:

16.04 is slower than 14.04 on my Lenovo G570 laptop with Intel Pentium B940 @ 2GHz,
with Graphics: Intel Sandybridge Mobile.  3.8GB RAM. OS type: 64-bit

It also freezes when I switch to a user who does not enter a password on login.
(Yes I know - that's a different issue but nevertheless .....)

---

### Post by schmitta on 2017-03-21
It is because vm.swapiness=60. It should be 15. You have a tremendous swap file problem the thing is totally using VM instead of the RAM. This is the fix for your problem: [http://askubuntu.com/questions/779042/ubuntu-16-04-is-slow-and-lags](http://askubuntu.com/questions/779042/ubuntu-16-04-is-slow-and-lags)

---

### Post by norafaithrainbow on 2017-03-21
> **groenem said:**
> I also have the same problem. Everything was working fine with 15.10, but after upgrading to 16.04 my PC is very slow. I have a Intel® Core™2 Duo CPU E7500 @ 2.93GHz × 2, with 1GB RAM. Graphics card is a Gallium 0.4 on AMD RV730 (DRM 2.43.0, LLVM 3.8.0).
My Kodi also played seamlessly with previous 15.10, now playback is very slow with big mkv files. I have installed the ubuntu-extra-codes, but it does not help either. I am very disappointed with 16.04. It is even worse than Windows currently.

You don't meet the minimum system requirements for ubuntu 16. It requires at least 2gbs of ram, four if you want it to run well.

---

### Post by oldos2er on 2017-03-22
Thread closed.

Rather than "hijacking" an old thread, we encourage users to create their own thread for their problems or questions.  Thanks.

---

