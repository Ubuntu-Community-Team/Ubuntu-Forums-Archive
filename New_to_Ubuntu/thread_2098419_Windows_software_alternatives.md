---
title: "Windows software alternatives"
date: 2012-12-26
forum: New to Ubuntu
---

### Post by microdroid on 2012-12-26
Hey guys,

I tried dual-booting Windows 8 and Ubuntu 12.10 - which didn't work, Windows isn't booting anymore. I know why it didn't work by now and I actually know how to fix it, but when I try reinstalling Windows from DVD, the setup doesn't recognize any partitions...
But maybe I don't even need to solve that problem, because I really like Ubuntu, I just need to find some software alternatives. I'm looking for apps like

- Sony Vegas Pro
- MorphVox Pro
- HyperCam 3
- Avery DesignPro

Espacially Vegas, MorphVox and HyperCam are very important to me because I used them a lot in Windows. If there are no Linux alternatives to those apps, I really need a solution for my dual-boot problem (I need Linux for some work stuff...)

---

### Post by N00b-un-2 on 2012-12-26
Depending on your video editing needs, there are quite a few good programs available in the repos. In my opinion the best application on Linux for video editing is Kino, especially if you work with a DV camera over firewire.  Openshot is good for basic editing too.  Pitivi looks promising and is easy to use, but lacks some features.  I also like Avidemux for post processing/transcoding.  You may also want to look into Blender and Cinelerra for more advanced features.

Audacity and Ardour are two very good audio editing tools, although they don't do quite the same things as MorphVox.  

gtk-recordmydesktop is a very easy to use screencasting tool like hypercam.  If needed, you can even use VLC to record your X server although the process is nowhere near as straightforward as purpose-built software like recordmydesktop.

pretty much anything you can do on Avery Design Pro can be accomplished using LibreOffice Draw or Writer.  As far as I recall, you should be able to import any Avery templates directly into LibreOffice.

Then if all else fails, there is always the option of using Windows software on WINE or Virtualbox.

** Almost forgot!
Kdenlive has an avid fan community, if you're willing to venture outside the Gnome ecosystem.

---

### Post by microdroid on 2012-12-26
> **N00b-un-2 said:**
> Depending on your video editing needs, there are quite a few good programs available in the repos. In my opinion the best application on Linux for video editing is Kino, especially if you work with a DV camera over firewire.  Openshot is good for basic editing too.  Pitivi looks promising and is easy to use, but lacks some features.  I also like Avidemux for post processing/transcoding.  You may also want to look into Blender and Cinelerra for more advanced features.

Audacity and Ardour are two very good audio editing tools, although they don't do quite the same things as MorphVox.  

gtk-recordmydesktop is a very easy to use screencasting tool like hypercam.  If needed, you can even use VLC to record your X server although the process is nowhere near as straightforward as purpose-built software like recordmydesktop.

pretty much anything you can do on Avery Design Pro can be accomplished using LibreOffice Draw or Writer.  As far as I recall, you should be able to import any Avery templates directly into LibreOffice.

Then if all else fails, there is always the option of using Windows software on WINE or Virtualbox.

** Almost forgot!
Kdenlive has an avid fan community, if you're willing to venture outside the Gnome ecosystem.

OK i tried to run MorphVox with Wine, it didn't work, and i know Audacity but that's not what I'm looking for. But all the other stuff sounds pretty promising, and I heard that Vegas Pro 10 is Wine compatible (I don't need the latest version of Vegas anyway). But I really need something like MorphVox, so I think I'm gonna have to try to get Windows again. Anyway, thank you for your answer :)

So has anyone got an idea how to make the Windows installer recognize partitions again?

---

### Post by N00b-un-2 on 2012-12-26
what do you mean 'make the windows installer recognize partitions again'?

If there is an NTFS partition available on an MBR formatted hard drive, it will detect it.

If you are on a GPT disk, you can accomplish the same thing, provided your NTFS partition is between partitions 1-4 (the first always being the 200 MB EFI hidden drive) and using gptsync to create a hybrid MBR.

---

### Post by microdroid on 2012-12-26
well there is an nfts partition availaible - the one windows was installed on before (and still is, but just not booting). but when i install windows from dvd, it shows me no partitions to install it on.

---

### Post by arpanaut on 2012-12-26
Have you tried Boot Repair?
[http://ubuntuforums.org/showthread.php?t=1769482](http://ubuntuforums.org/showthread.php?t=1769482)

---

### Post by microdroid on 2012-12-26
> **arpanaut said:**
> Have you tried Boot Repair?
[http://ubuntuforums.org/showthread.php?t=1769482](http://ubuntuforums.org/showthread.php?t=1769482)

not yet but that sounds good, i'll try it. thanks :)

---

### Post by acimi66 on 2012-12-26
Have you thought about running those windows programs inside a Virtual Box?

---

### Post by MishaX2 on 2012-12-26
Running these apps in a virtual box really won't help him. Especially sony vegas takes a lot of computing power...

---

### Post by qyot27 on 2012-12-26
> **MishaX2 said:**
> Running these apps in a virtual box really won't help him. Especially sony vegas takes a lot of computing power...
It all depends on the underlying hardware, really.  I don't use Vegas for my video editing (Premiere user), but if you've got a Core i-series or equivalent processor, then running NLE software in a Windows VM shouldn't be that painful, if at all.

Although if it can run without problems under Wine, that's preferable to using a VM.

---

### Post by mredding on 2012-12-26
Although there's no reason you can't dual boot, OpenShot is a personal favorite for video editing. It works with Blender for 3D titles and such. A good place to look for alternatives to all kinds of software is osalt.com.

Anyway, you should definitely be able to fix your boot issue, but there's not really enough information to help. Does Windows show up in Grub at all?

---

### Post by microdroid on 2012-12-27
> **qyot27 said:**
> It all depends on the underlying hardware, really.  I don't use Vegas for my video editing (Premiere user), but if you've got a Core i-series or equivalent processor, then running NLE software in a Windows VM shouldn't be that painful, if at all.

Although if it can run without problems under Wine, that's preferable to using a VM.

I'm on an AMD A6 Quad-Core processor... 

You think uninstalling Win8 with OS-Uninstaller might solve the problem? I got no idea what to do, the Win7 installer also doesn't recognize any partitions (except for my external HDD, which doesn't really help me ^_^ )

---

### Post by microdroid on 2012-12-27
> **mredding said:**
> Anyway, you should definitely be able to fix your boot issue, but there's not really enough information to help. Does Windows show up in Grub at all?

Yes, Windows shows up in Grub, but when i choose it, it says:

error: device format "ldm/bfa0ee70-37cd-11e2-be81-101f74172b72/Volume1" invalid: must be (f|h)dN, with 0 <= N < 128. 
Press any key to continue...

and then

A disk read error occured 
Press Ctrl+Alt+Del to restart

> **mredding said:**
> A good place to look for alternatives to all kinds of software is osalt.com.

Thanks, that's a really good website 8-)

---

### Post by mredding on 2013-01-14
Although I've never seen that specific problem (hopefully someone else can give better advice) you may be successful booting with the Windows CD and doing a startup repair. If that works to restore Windows, you can then use the Ubuntu Live CD to reinstall grub.

---

