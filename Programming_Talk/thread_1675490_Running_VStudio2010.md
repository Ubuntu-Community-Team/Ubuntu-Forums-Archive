---
title: "Running VStudio2010"
date: 2011-01-25
forum: Programming Talk
---

### Post by doctorzeus on 2011-01-25
Hi,

Ok I switched to Ubuntu Linux on my laptop a while ago now and it seems I may now need to use VS2010 and the .Net framework on my laptop..

My Question is what are my options? Obviously .NET fw is not suppported on Linux and it only works up to V2.0 on wine...I considered partioning with a windows section but I thought that may be a bit extreme for just one programs needs..my other thought was using virtualbox although I'd obviouslly rather have a Linux option or even better (but highly unlikely) get Visual Studio 2010 working on Linux...

Any Suggestions would be fantastic :)

---

### Post by slavik on 2011-01-25
if vstudio is a hard requirement then run windows. otherwise, will mono work?

don't complain that xcode is only available for OSX ;)

---

### Post by Milliways on 2011-01-25
> **doctorzeus said:**
> Hi,

Ok I switched to Ubuntu Linux on my laptop a while ago now and it seems I may now need to use VS2010 and the .Net framework on my laptop..


If you can afford the full version of VS2010 you could buy a dedicated laptop.
This would not cost much more than buying a Windows licence.

If the Express version don't.

Either way, you really need Windows, either as a dedicated boot or VirtualBox installation.

---

### Post by muteXe on 2011-01-26
I've gone down the vs2010 express in virtualbox route, works ok for me.

---

### Post by fct on 2011-01-26
I guess you have also considered Monodevelop? If so, I guess your only option is a VM like Virtualbox. I'm afraid wine can't run VS2010 at all.

---

### Post by directhex on 2011-01-26
> **doctorzeus said:**
> Obviously .NET fw is not suppported on Linux

Ubuntu has shipped with .NET apps by default since 2005.

You likely want to install apt:monodevelop

---

### Post by scott_tiger on 2011-01-26
Install virtual box or QEMU..

try moonlight in place of microsoft silverlight?

---

### Post by doctorzeus on 2011-01-26
> **Milliways said:**
> If you can afford the full version of VS2010 you could buy a dedicated laptop.
This would not cost much more than buying a Windows licence.

If the Express version don't.

Either way, you really need Windows, either as a dedicated boot or VirtualBox installation.

Thanks for the Reply,

I have a buisness lisense, so my work payed for it not me :)

---

### Post by doctorzeus on 2011-01-26
> **slavik said:**
> if vstudio is a hard requirement then run windows. otherwise, will mono work?

don't complain that xcode is only available for OSX ;)

Thanks for the reply,

Haha ;) Am I to assume your a mac person? :p :)

considering partioning more now...

---

### Post by doctorzeus on 2011-01-26
> **muteXe said:**
> I've gone down the vs2010 express in virtualbox route, works ok for me.

Thanks for the Reply,

Yeah I considered that, but I hate the complex sharing process between you and the virtual OS...

---

### Post by doctorzeus on 2011-01-26
> **fct said:**
> I guess you have also considered Monodevelop? If so, I guess your only option is a VM like Virtualbox. I'm afraid wine can't run VS2010 at all.

Thanks for the reply,

Yeah I know,

you know if we will ever support .NET 4.0?

---

### Post by doctorzeus on 2011-01-26
> **directhex said:**
> Ubuntu has shipped with .NET apps by default since 2005.

You likely want to install apt:monodevelop

Thanks for the reply,

Still not quite the same though :(

---

### Post by lukeiamyourfather on 2011-01-26
> **doctorzeus said:**
> Thanks for the Reply,

Yeah I considered that, but I hate the complex sharing process between you and the virtual OS...

If you can figure out programming with .NET and Visual Studio then you can figure out how to install the virtual guest add-ons and mount a drive.

[https://help.ubuntu.com/community/VirtualBox/SharedFolders](https://help.ubuntu.com/community/VirtualBox/SharedFolders)

---

### Post by doctorzeus on 2011-01-26
> **lukeiamyourfather said:**
> If you can figure out programming with .NET and Visual Studio then you can figure out how to install the virtual guest add-ons and mount a drive.

[https://help.ubuntu.com/community/VirtualBox/SharedFolders](https://help.ubuntu.com/community/VirtualBox/SharedFolders)

Thanks for the reply,

Hmm, that seems straight forward enough..funny my friend told me otherwise, will need to give him an earful at work tommorow :)

Doctorzeus

---

### Post by slooksterpsv on 2011-01-26
> **doctorzeus said:**
> Thanks for the reply,

Hmm, that seems straight forward enough..funny my friend told me otherwise, will need to give him an earful at work tommorow :)

Doctorzeus

Well, it varies, sometimes it can get messy, but usually it's pretty straight-forward, especially if you have Ubuntu as Host, and Windows as guest, cause you install the addons, setup the share under Devices -> Shared Folders... -> set your shared folder; then on the Windows vm navigate to: 
\\VBOXSVR - locate your share, and you're there.

Also you can do seamless mode so if you don't want the VM in a window, but want it to look like so via seamless mode:

---

### Post by doctorzeus on 2011-01-26
> **slooksterpsv said:**
> Well, it varies, sometimes it can get messy, but usually it's pretty straight-forward, especially if you have Ubuntu as Host, and Windows as guest, cause you install the addons, setup the share under Devices -> Shared Folders... -> set your shared folder; then on the Windows vm navigate to: 
\\VBOXSVR - locate your share, and you're there.

Also you can do seamless mode so if you don't want the VM in a window, but want it to look like so via seamless mode:

Thanks for the reply,

I may try that but to be honest I am leaning towards creating a small windows boot partion inside Ubuntu...

Can you/anyone suggest a good tutorial for this?

I will read up further on the virtual sharing and see which ones probubly the best option..It may also be usefull in case I for some reason decide to game on my laptop, performance wise I mean...

---

### Post by Milliways on 2011-01-27
> **doctorzeus said:**
> Thanks for the reply,

I may try that but to be honest I am leaning towards creating a small windows boot partion inside Ubuntu...

Can you/anyone suggest a good tutorial for this?

I will read up further on the virtual sharing and see which ones probubly the best option..It may also be usefull in case I for some reason decide to game on my laptop, performance wise I mean...

I don't know that is feasible to install Windows after GNU/Linux (I have never tried this) but look at the following tutorials. It is a while since I read these (pre Windows 7) but I found them very good.
[http://apcmag.com/tags.htm?tids=2324,812,2013,1766](http://apcmag.com/tags.htm?tids=2324,812,2013,1766)

VirtualBox works quite well, and sharing partitions is quite easy (once you master the tricks). I still don't entirely trust GNU/Linux write on NTFS, but SAMBA works well for sharing.

VirtualBox lets you mount host partitions for sharing, and this is probably the best and most reliable way to share data.

I mostly use VirtualBox on a Windows host with different clients, but it works well on GNU/Linux. This would be easier than trying to install Windows on a Linux machine, particularly with the new boot sector in Vista/Win7.

If you try VirtualBox, you will find experienced users on these Forums.

---

### Post by lukeiamyourfather on 2011-01-27
> **Milliways said:**
> I don't know that is feasible to install Windows after GNU/Linux

Usually Windows will install a different boot loader over GRUB (the boot loader that Ubuntu uses). All you have to do is reinstall GRUB from a live session of Ubuntu booted from an install disc. When reinstalling GRUB it should automatically discover the Windows partition and make it an option on the boot menu. If all you need is Visual Studio I still think a virtual machine is a better option.

---

### Post by doctorzeus on 2011-01-27
> I still don't entirely trust GNU/Linux write on NTFS, but SAMBA works well for sharing.

I know what you mean, I have a backup NTFS external drive. Wierd and random problems pop up ocasionally like I/O errors when on LINUX..

Doctorzeus

---

### Post by doctorzeus on 2011-01-27
Ok I backed everything up and put windows 7 along with leaving 32GB of unalocated space for LINUX.

Probulby was the best way of going about that from the sounds of it :)

Thanks for all the help everyone :) :guitar:

---

