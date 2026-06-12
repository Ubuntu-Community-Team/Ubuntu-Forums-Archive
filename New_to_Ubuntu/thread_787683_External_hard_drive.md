---
title: "External hard drive"
date: 2008-05-09
forum: New to Ubuntu
---

### Post by philipluna66 on 2008-05-09
I have an external U>S<B hard drive 200gb On it I have 15gb of things I would like to keep But they are for my Windows xp ie NFTS files. My Ubuntu 8.04 is on my old computer by 10 years so is very slow but is handling Ubuntu VERY well . But my hard drive is only 8 gb. What I am wanting to do is connect my External hard drive to my Ubuntu but when I do it says cant connects NFTS files. So do I have to format my hard drive but I dont want to loose 15gb of files. Should I burn the files to DVD???. I dont want to bye a new usb hard drive as I am saving for a new monitor I am getting sick of swopping the cable over. If you have any ideas please let me know. ps, I am new to ubuntu so keep it simple Thanks

---

### Post by tribaal on 2008-05-09
What you can do is use "gparted" (sudo aptitude install gparted - it then shows up in your system administration menu) to resize your ntfs partition on your external drive to something smaller (like 20 Gb for example), then create a new partition formatted as ext3 which you can use as an additional HDD for your Ubuntu installation?

I don't know if this answers your question, but it's how I would use a spare HDD :)

Cheers

- Trib'

---

### Post by linuxisfree on 2008-05-09
are NTFS 3G and NTFS config installed? If not, then you can install them via the repositories. Hope that'll help:)

EDIT: Those programs i mentioned should allow you access to your NTFS Drive.

---

### Post by subzero316 on 2008-05-09
> **philipluna66 said:**
> I have an external U>S<B hard drive 200gb On it I have 15gb of things I would like to keep But they are for my Windows xp ie NFTS files. My Ubuntu 8.04 is on my old computer by 10 years so is very slow but is handling Ubuntu VERY well . But my hard drive is only 8 gb. What I am wanting to do is connect my External hard drive to my Ubuntu but when I do it says cant connects NFTS files. So do I have to format my hard drive but I dont want to loose 15gb of files. Should I burn the files to DVD???. I dont want to bye a new usb hard drive as I am saving for a new monitor I am getting sick of swopping the cable over. If you have any ideas please let me know. ps, I am new to ubuntu so keep it simple Thanks



Partion the free space using GTPARTED . as for swooping the cables buy an usb extender cable.

---

### Post by Crossroads on 2008-05-09
> **linuxisfree said:**
> are NTFS 3G and NTFS config installed? If not, then you can install them via the repositories. Hope that'll help:)

EDIT: Those programs i mentioned should allow you access to your NTFS Drive.
The OP has Ubuntu 8.04 .
Doesn't 8.04 come with these already installed?

---

### Post by linuxisfree on 2008-05-10
> **Crossroads said:**
> The OP has Ubuntu 8.04 .
Doesn't 8.04 come with these already installed?

You're right! It's supposed to... which makes me wonder why he can't access the NTFS Harddrive.

---

### Post by 2hot6ft2 on 2008-05-10
> **philipluna66 said:**
> I have an external U>S<B hard drive 200gb On it I have 15gb of things I would like to keep But they are for my Windows xp ie NFTS files. My Ubuntu 8.04 is on my old computer by 10 years so is very slow but is handling Ubuntu VERY well . But my hard drive is only 8 gb. What I am wanting to do is connect my External hard drive to my Ubuntu but when I do it says cant connects NFTS files. So do I have to format my hard drive but I dont want to loose 15gb of files. Should I burn the files to DVD???. I dont want to bye a new usb hard drive as I am saving for a new monitor I am getting sick of swopping the cable over. If you have any ideas please let me know. ps, I am new to ubuntu so keep it simple Thanks

Sounds a bit like XP still has a grip on the drive. Did you use "safely disconnect hardware" or shut down the pc while it was still connected in XP?

If not try it. Fire up XP then once it's all running and the USB Drive is connected. Use the "safely disconnect hardware" it's a icon in the lower right by the clock. Either that or shut XP down normally with it still connected and "ON".

It's like unmounting a usb drive in linux. If you just unplug it without unmounting it first it can cause problems.

Just my 2 cents on how it sounds. Hope it helps

---

