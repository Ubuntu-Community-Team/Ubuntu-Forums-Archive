---
title: "Problems installing ubuntu 13 among win8"
date: 2013-06-27
forum: New to Ubuntu
---

### Post by annlee on 2013-06-27
hi, I have done several times this procedure installing ubuntu in already existing windows, however, now seems impossible to get it done, I've read many tutorials, applied some changes in grub.cfg and others tutorials, including supergrub2 and its brother, but still wrong.

Historic:

- Brand-new Lenovo Y500 with win8, then installed correctly using this tutorial: [http://askubuntu.com/questions/272570/unable-to-install-ubuntu-on-lenovo-y500](http://askubuntu.com/questions/272570/unable-to-install-ubuntu-on-lenovo-y500)

- when restart, in grub splash screen only works ubuntu and runs correctly, others give error

- installed and executed "boot-repair", now gives different errors and only works ubuntu

- executed "boot-repair" again and in advanced settings restored, then **currently **only load windows (no grub splash)


I asked people and suggested me to use syslinux/chroot instead of grub but dont want more complication, using live cd is not a solution


Can anyone tell me what _pastebins_ do I have to place here so we can fix it and have grub with multi-os?

---

### Post by VMC on 2013-06-27
If you could tell us where "boot-repair" put pastbin, that would be great. It will hep us determine where the error lies.

Also, members jump all over any boot issues. So just be patient.

---

### Post by Kopkins on 2013-06-27
I did some digging on the Y500 and it seems that people have problems with grub. An easy fix is to use syslinux instead of grub. That will probably be the most straightforward solution. You will probably have to go in through a live CD or USB and chroot into your ubuntu system. Then remove grub and install syslinux. 

Kopkins

---

### Post by annlee on 2013-06-27
ok guys, I am going to run in live-cd then install/run boot-repair and paste here the results

I am afraid I wont be able to start win8 again like happened before, brb

---

### Post by annlee on 2013-06-27
there it is the result of boot/repair [http://paste.ubuntu.com/5804981/](http://paste.ubuntu.com/5804981/)

---

### Post by CaseyC on 2013-06-27
> **annlee said:**
> ok guys, I am going to run in live-cd then install/run boot-repair and paste here the results

I am afraid I wont be able to start win8 again like happened before, brb

When you boot to your live cd, take your files you want to preserve from Win8 just in case something goes wrong (hopefully not) and slap them on a cd/usb/network share. Just a friendly reminder :)

---

### Post by annlee on 2013-06-27
ok, after applying boot-repair now I messed it all, cant run ubuntu nor win8

I dont have any files to save from win8 (luckyly)

in startup gives an error, so I am in your hands if you help me

do you need screenshots from BIOS and startup errors?

---

### Post by VMC on 2013-06-27
@annlee,

Just looking at the "pastebin" file, it looks like you have several hard drives. First off, *sda* has no boot loader, and has no known file system. *sdb* and *sdc*. What are they external drives?
Since you have Windows 8, you must be using UEFI, as sdb2 and sdb3 are referring to.

---

### Post by annlee on 2013-06-27
> **VMC said:**
> @annlee,

Just looking at the "pastebin" file, it looks like you have several hard drives. First off, *sda* has no boot loader, and has no known file system. *sdb* and *sdc*. What are they external drives?
Since you have Windows 8, you must be using UEFI, as sdb2 and sdb3 are referring to.

Lenovo Y500 has 2 hard drives:
- 1TB (win8, linux, swap...)
- 16GB SSD
each one has repair sections,

"sda has no boot loader": how do I add one? seems boot-repair removed it

the only external drive is the USB live ubuntu I am using

"Since you have Windows 8, you must be using UEFI, as sdb2 and sdb3 are referring to" it is set in BIOS to use UEFI also secure mode off

Can you please give me some steps or do you have any other question?

Perhaps, if I restore EFI from advanced section in boot-repair, can at least go back to win8 like (I think) I did before?

---

### Post by dino99 on 2013-06-27
there are some "ubuntu grub2 win8" threads around when googling about, like that one:
[http://askubuntu.com/questions/300467/wheres-my-win8-go](http://askubuntu.com/questions/300467/wheres-my-win8-go)

[http://www.google.fr/#q=ubuntu+grub2+wn8&source=lnt&tbs=qdr:y&sa=X&ei=1mHMUd-DNs7UPO7vgdgO&ved=0CB0QpwUoBQ&bav=on.2,or.r_qf.&bvm=bv.48340889,d.d2k&fp=b5edd32b96520ea9&biw=1672&bih=924](http://www.google.fr/#q=ubuntu+grub2+wn8&source=lnt&tbs=qdr:y&sa=X&ei=1mHMUd-DNs7UPO7vgdgO&ved=0CB0QpwUoBQ&bav=on.2,or.r_qf.&bvm=bv.48340889,d.d2k&fp=b5edd32b96520ea9&biw=1672&bih=924)

---

### Post by annlee on 2013-06-27
thanks, but that link dont help much, hope to get at least win8

last pastebin [http://paste.ubuntu.com/5805166/](http://paste.ubuntu.com/5805166/)

---

### Post by annlee on 2013-06-27
for the love of god, at least recovered win8 ;)

---

### Post by xannaxprozaxx on 2013-06-27
I ended up being able to get Ubuntu to run using syslinux, but I wiped out the win8 partition;
It is not exactly the same case, but maybe it can help if I document what I did:

I tried to make GRUB work for a long time to no avail (roughly one week).
I boot-repaired countless times, got in touch with dozens of people in forums and on IRC, to no avail.
Ubuntu was installing fine, but would not boot.

I got in touch with the Grub maintainers on their mailing list, and although they were great in providing support and explanations, we didn't manage to fix my problem.
I will not transcript the whole convo, but here are the last relevant bits:

> So you're having nouveau problems when booting in EFI mode? Welcome to the club. I've found kernel 3.6.10 and 3.6.11 to work very well, and all 3.7 kernels are OK, some boot time corruption but GNOME/KDE are fine once they load. 3.8 intermittently, maybe 1/10 times, implodes with nouveau. And 3.9 there's been a regression such that I have a black screen and need to use nomodeset. Anyway, point is, it's worth trying other kernels.
[...]
> do you know what could be causing the freezing of "grub loading."?
No. Could be a firmware bug. Could be a GRUB bug. That this is in CSM-BIOS mode with GRUB2 sounds more to me like hardware related [...] but it needs more data points to be sure. You could try a Fedora 18 x86_64 LiveCD ISO, which when burned to actual media or dd'd to a USB stick, can boot either EFI or BIOS computers. When booting EFI, it uses GRUB2 EFI, and when booting BIOS it uses isolinux. So if it turns out to be a bug in GRUB, and you can't or don't want to compile your own from current source (although Arch is usually pretty up to date I think), then maybe you need to try a different boot loader. In that case, my choice for BIOS would be extlinux, or for EFI rEFInd or gummiboot.


Note that at that time I had switched to Arch as it gave me more flexibility. A cool person on the Arch IRC guided poor stupid me for litteraly hours, relentlessly, until we got Arch installed, but then I could not use my graphic card.

It was getting too complex for me, so I left it at that and tried other bootloaders.

Since I had no access to Ubuntu at all, even if it installed correctly (I only ever got a black frozen screen), I could not install syslinux.
The USB boot worked fine though, so I booted off the USB key, and chrooted into my installed system.

In order to be able to install the software correctly, I needed to symlink several directories from the usb system;
However, as I am not very knowledgeable, I forgot which.
I got them right in the end by a mixture of trial and error, and checking Arch's chroot script.
Maybe someone can say which are the dirs that need to be symlinked, and in what way?

After chrooting, I sudoAptGot syslinux, and set it up according to the arch's wiki.

After a few trials, I was good to go, and I was able to boot into buntu flawlessly. Everything worked but the brightness keys, but I don't really care for that, so after a few (unsuccessful) trials, I left it at that.

Here are a few threads that might help:
[http://askubuntu.com/questions/272570/unable-to-install-ubuntu-on-lenovo-y500](http://askubuntu.com/questions/272570/unable-to-install-ubuntu-on-lenovo-y500)
[http://ubuntuforums.org/showthread.php?t=2095063](http://ubuntuforums.org/showthread.php?t=2095063)
[http://ubuntuforums.org/showthread.php?t=2145694](http://ubuntuforums.org/showthread.php?t=2145694)
[http://ubuntuforums.org/showthread.php?t=2130516](http://ubuntuforums.org/showthread.php?t=2130516)
[http://ubuntuforums.org/showthread.php?t=2127341](http://ubuntuforums.org/showthread.php?t=2127341)
[http://forums.lenovo.com/t5/Linux-Discussion/Lenovo-Y500-SLI-Linux-Ubuntu-support/td-p/1082277](http://forums.lenovo.com/t5/Linux-Discussion/Lenovo-Y500-SLI-Linux-Ubuntu-support/td-p/1082277)

Hope this sheds some light

---

### Post by annlee on 2013-06-27
thanks a lot, I also liked your tutorial I mention above that worked to create a working usb drive live

finally, I am suffering more or less what you mean, in the end, 

mostly, I think I will format that partition for games one and will use linux via usb live for delicated stuff like paying online or using personal certificates

I really liked ubuntu13, in win8 permanently uses minimum of 33% ram, in linux I checked 13%, but this Lenovo is fast enougth to stay just with win8

---

### Post by Mark Phelps on 2013-06-27
I don't know what you read, but I'm surprised you charged ahead with Wubi, Ubuntu 13.04, and Win8, considering:
1) Wubi has been dropped from 13.04 -- documented clearly in the Release Notes:  [https://wiki.ubuntu.com/RaringRingtail/ReleaseNotes]("https://wiki.ubuntu.com/RaringRingtail/ReleaseNotes")
2) The Ubuntu website advises against using Wubi with Windows 8 -- again, clearly documented:  [http://www.ubuntu.com/download/desktop/windows-installer]("http://www.ubuntu.com/download/desktop/windows-installer")
3) Wubi does NOT use GRUB; instead, it uses a derivative of GRUB known as GRUB4DOS.  Installing GRUB  in a Wubi installation will not only NOT repair it, it will actually make things worse by corrupting the Windows boot -- as you have discovered.

---

### Post by annlee on 2013-06-27
who mentioned Wubi?

To ubuntu developers:

installing ubuntu right after windows should not be an issue or something to "break" to be "repaired" in grub, since this should a pretty common procedure, and not a headache as it is right now

grub should be smart enought to manage it without repair tools, experts giving advices of very complex stuff and so on

---

### Post by VMC on 2013-06-27
The mentioned of Wubi  threw me off. I thought I missed something. Re-tracing the "pastbins" I didn't see any mention of Wubi.

Your right, grub should be able to handle the booting process, but Windows 8 brings in a whole new ball game.

As I don't have UEFI, and/or Windows 8, I can't be of much help. As suggested, try searching for Ubuntu and windows 8 installs for a clue.

---

### Post by annlee on 2013-06-27
lol "pastbins" congrats, you created a new meme/viral/lolcatz

for mods, this thread is done, I will format that partition for games

---

### Post by Kopkins on 2013-06-28
> **annlee said:**
> who mentioned Wubi?

To ubuntu developers:

installing ubuntu right after windows should not be an issue or something to "break" to be "repaired" in grub, since this should a pretty common procedure, and not a headache as it is right now

grub should be smart enought to manage it without repair tools, experts giving advices of very complex stuff and so on

Microsoft did a pretty good job making sure that it is very difficult to use any operating system but Windows with Windows 8. Lots of things got added that make it much more troublesome to try to get linux and windows to share. Win 7 was not as much of a problem. So to be fair, it's not Ubuntu developers fault. It's Microsoft, and it seems like it was on purpose.

Kopkins

---

