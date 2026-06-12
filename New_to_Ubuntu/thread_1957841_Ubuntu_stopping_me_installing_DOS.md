---
title: "Ubuntu stopping me installing DOS"
date: 2012-04-13
forum: New to Ubuntu
---

### Post by Homeground on 2012-04-13
I've got a spare drive, which I wanted to use for DOS and a few other things. It had Ubuntu 10.04 on it, which I didn't want to keep. I installed DOS 6.2 from floppy disks, which seemed to go okay. But when I booted up I got

error: no such partition.
grub rescue>

Help?

---

### Post by roelforg on 2012-04-13
I don't think old dos disks and moders ext* filesystems get along

---

### Post by Homeground on 2012-04-13
Obviously they don't. But since DOS formats the disc before installing, I didn't think it mattered. My question was, what can I do about it?

---

### Post by roelforg on 2012-04-13
> **Homeground said:**
> Obviously they don't. But since DOS formats the disc before installing, I didn't think it mattered. My question was, what can I do about it?
 
Formatting a disk, in dos, means erasing it... No wonder grub can't find it's files.

---

### Post by westie457 on 2012-04-13
> **Homeground said:**
> I've got a spare drive, which I wanted to use for DOS and a few other things. It had Ubuntu 10.04 on it, which I didn't want to keep. I installed DOS 6.2 from floppy disks, which seemed to go okay. But when I booted up I got

error: no such partition.
grub rescue>

Help?

Hi just re-formatting the drive is not enough because Grub files are written to the MBR - master boot record.

The drive has to be re-partitioned to remove the Grub files from the drive and Dos will have to installed from scratch.

Here is a guide to using the Dos FDISK command.

[http://www.computerhope.com/fdiskhlp.htm](http://www.computerhope.com/fdiskhlp.htm)

---

### Post by Homeground on 2012-04-13
> **westie457 said:**
> Hi just re-formatting the drive is not enough because Grub files are written to the MBR - master boot record.

The drive has to be re-partitioned to remove the Grub files from the drive and Dos will have to installed from scratch.

Here is a guide to using the Dos FDISK command.

[http://www.computerhope.com/fdiskhlp.htm](http://www.computerhope.com/fdiskhlp.htm)

The kind of useful reply I was hoping for. Thanks.

---

### Post by mastablasta on 2012-04-13
also disk needs to be format as system disk. this should overwrite the MBR i think.
 
format /s /u is the switch if memorry serves me correct
 
why don't you want Ubuntu? if you would want to run DOS programmes you could just use DOS box. if you need a lighter OS because mashcine is old there is plenty out there... i mean why install 25 year old os instead of modern one?

---

### Post by Homeground on 2012-04-13
> **mastablasta said:**
> also disk needs to be format as system disk. this should overwrite the MBR i think.
 
format /s /u is the switch if memorry serves me correct
 
why don't you want Ubuntu? if you would want to run DOS programmes you could just use DOS box. if you need a lighter OS because mashcine is old there is plenty out there... i mean why install 25 year old os instead of modern one?

I already have Ubuntu on my main disk. This is a spare. There are several reasons I want a clean DOS install. I've tried the Ubuntu DOSbox and don't like it much. Programs run too slow, and it screws up the key-mapping. A DOS box in Windows is better, provided it's Win95 or 98. Later versions have tried to squeeze DOS out altogether by providing a DOS box that is so small it's unusable. But even Win95/98 run all programs in VM, and there are some programs that have to be run in real mode. Hence, a need for one small partition with barebones DOS.

---

### Post by s1baker on 2012-04-13
I use dosemu to emulate DOS.

---

### Post by s1baker on 2012-04-13
forgot to add though, dosemu also has a small size screen.

---

### Post by emendelson on 2012-04-15
> **s1baker said:**
> forgot to add though, dosemu also has a small size screen.

Methods for changing the screen size, etc., in DOSEMU may be found here:

[http://www.columbia.edu/~em36/wpdos/linux.html#screensize]("http://www.columbia.edu/~em36/wpdos/linux.html#screensize")

---

### Post by spillin_dylan on 2012-04-15
Not to dissuade you against MS-DOS 6.2, but have you tried [FreeDOS?]("http://www.freedos.org/")  It looks like it is a modern-day replacement for MS-DOS, and is still being developed.  Never tried it myself, but it sure sounds good.

Also, what about [GlaDOS]("http://en.wikipedia.org/wiki/Glados")?  :lolflag:

---

### Post by mastablasta on 2012-04-15
> **Homeground said:**
> I already have Ubuntu on my main disk. This is a spare. There are several reasons I want a clean DOS install. I've tried the Ubuntu DOSbox and don't like it much. Programs run too slow, and it screws up the key-mapping. A DOS box in Windows is better, provided it's Win95 or 98. Later versions have tried to squeeze DOS out altogether by providing a DOS box that is so small it's unusable. But even Win95/98 run all programs in VM, and there are some programs that have to be run in real mode. Hence, a need for one small partition with barebones DOS.


you are talking about this DOSbox, right? : [http://www.dosbox.com/](http://www.dosbox.com/)
It can be found in repositories. 

they are the same windows or linux as i know. and i am using it on widnowsXP as well as on linux. here is a good Linux GUI to help you set it up propperly: [http://members.quicknet.nl/blankendaalr/dbgl/](http://members.quicknet.nl/blankendaalr/dbgl/)
EDIT: this linux GUI requires Sun java not open java to work propperly.

it's an emulator, so yes you need to have 7 or 8 year old computer to run it smooth. you can also speed it up or slow it down by adjusting the cycles. you can also record movies with it, take screenshots...
what programme is giving you the toruble? and what do you mean screws keymapping? it stays the same whenever i used it and besides there are also config files where i am sure you can remap the keys if needed. 

ofcourse not everythind can do well via emulator.

indeed if that is the case then perhaps freedos could be an alternative. again i am not sure how good their compatibility is with MS dos since i never tried it but i think it is like MS-DOS 7.x and it does work on new maschines. they do aim to make it 100% MS Dos compatible.

---

### Post by Homeground on 2012-04-16
> **mastablasta said:**
> you are talking about this DOSbox, right? : [http://www.dosbox.com/](http://www.dosbox.com/)
It can be found in repositories. 

they are the same windows or linux as i know. and i am using it on widnowsXP as well as on linux. here is a good Linux GUI to help you set it up propperly: [http://members.quicknet.nl/blankendaalr/dbgl/](http://members.quicknet.nl/blankendaalr/dbgl/)
EDIT: this linux GUI requires Sun java not open java to work propperly.

it's an emulator, so yes you need to have 7 or 8 year old computer to run it smooth. you can also speed it up or slow it down by adjusting the cycles. you can also record movies with it, take screenshots...
what programme is giving you the toruble? and what do you mean screws keymapping? it stays the same whenever i used it and besides there are also config files where i am sure you can remap the keys if needed. 

ofcourse not everythind can do well via emulator.

indeed if that is the case then perhaps freedos could be an alternative. again i am not sure how good their compatibility is with MS dos since i never tried it but i think it is like MS-DOS 7.x and it does work on new maschines. they do aim to make it 100% MS Dos compatible.

The Dos boxes I was talking about, mostly, were those provided by Windows, by which you can run Dos programs with click-and-run. The early 9x versions provided the best ones. The app called Dosbox is a different thing. I used it in Ubuntu for a week or so. It screws key-mapping if your program needs to use the Function keys F1-F9. Yes, you can re-map them and use different keys, but all in all, I didn't find the experience satisfactory.

I already have FreeDos on my main disk. It's fine, except for the fact that it doesn't seem to run in real mode, but in some kind of virtual mode. It's probably something to do with the Dos extender that comes with part of the package. I've only just discovered that, so I haven't been able to look into it.

---

### Post by jwbrase on 2012-04-16
> **Homeground said:**
> The Dos boxes I was talking about, mostly, were those provided by Windows, by which you can run Dos programs with click-and-run. The early 9x versions provided the best ones.

That's because Win9x was, in fact, a DOS-based system. Unlike Dos up to version 6 and Windows up to version 3, however, Microsoft no longer sold DOS and Windows separately.

EDIT: The fact that it was DOS-based is also why Win9x was so crashy. 

> The app called Dosbox is a different thing. I used it in Ubuntu for a week or so. It screws key-mapping if your program needs to use the Function keys F1-F9. Yes, you can re-map them and use different keys, but all in all, I didn't find the experience satisfactory.

I think you also mentioned you found it slow. Did you try adjusting the speed? DOSBox by default runs slow because there are a lot of DOS programs that don't work correctly on fast processors. You can, however, adjust the running speed (I think the default keymapping is Ctrl+F11 and Ctrl+F12, or something, but I'm not entirely sure).

The biggest issue I have with DOSbox is that the sound is skippy.

> 
I already have FreeDos on my main disk. It's fine, except for the fact that it doesn't seem to run in real mode, but in some kind of virtual mode. It's probably something to do with the Dos extender that comes with part of the package. I've only just discovered that, so I haven't been able to look into it.

Yes, memory managers meant for use with 386's (or more recent machines) cause DOS to run in V86 mode, since that allows said memory managers to access memory beyond 1MB without special hardware.

Apps that do their own memory management but don't check to see if there's a memory manager already there to do it for them, or for whatever reason *have* to do their own memory management, will either be killed by the memory manager or refuse to run when started in V86 mode.

This applies to MS-DOS and FreeDOS alike. You can edit your config.sys to give you a menu that will allow you to choose between booting with the memory manager enabled or disabled according to what software you want to run.

---

### Post by Homeground on 2012-04-18
What are the memory managers that cause a program to run in V86 mode? QEMM, I guess is one. What are the others? There are times I might have to disable them in order to run in real mode. 

It's so long since I've used Dos I've forgotten how to exclude things in the Config.sys file. Is it "rem"?

---

### Post by jwbrase on 2012-04-18
> **Homeground said:**
> What are the memory managers that cause a program to run in V86 mode? QEMM, I guess is one. What are the others? There are times I might have to disable them in order to run in real mode. 

Well, first off, anything with "EMM" in the name:

There's EMM386 (which is actually several memory managers, as MS-DOS, DR-DOS, and FreeDos each had their own memory managers with that name), more recent versions of FreeDos have JEMM / JEMMEX, and then there were some other memory managers like CEMM and 386MAX.

I'm not sure, but HIMEM / HIMEMX *may* use V86 mode.

> 
It's so long since I've used Dos I've forgotten how to exclude things in the Config.sys file. Is it "rem"?

Yes, but I actually don't think you need to for FreeDOS (and even for MS-DOS you shouldn't need to, but you'll need to do a bit of setup). When it boots you should get a menu with options like "Load FreeDOS with EMM386, no EMS", "Load FreeDOS with EMM386+EMS and SHARE", etc.

If you pick an option that doesn't include EMM386 / JEMM / JEMMEX, that *should* have you in real mode, unless there's something that menu item loads that puts things into V86 mode that I've missed.

(BTW, for FreeDOS, you should edit fdconfig.sys, not config.sys, unless fdconfig.sys does not exist. FreeDOS checks fdconfig.sys first and ignores config.sys unless fdconfig.sys does not exist.)

Anyways, both FreeDOS and MS-DOS allow for menus in config.sys / fdconfig.sys, allowing you to choose which (fd)config.sys items to run at boot time, rather than by rem-ing things out and rebooting.

There's information on MS-DOS menus here:

[http://dos.rsvs.net/DOSPAGE/CONFMENU.HTM](http://dos.rsvs.net/DOSPAGE/CONFMENU.HTM)

And for FreeDOS menus here:

[http://help.fdos.org/en/hhstndrd/cnfigsys/menu.htm](http://help.fdos.org/en/hhstndrd/cnfigsys/menu.htm)

---

