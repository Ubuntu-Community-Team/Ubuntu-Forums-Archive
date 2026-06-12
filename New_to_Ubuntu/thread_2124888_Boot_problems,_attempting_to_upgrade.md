---
title: "Boot problems, attempting to upgrade"
date: 2013-03-12
forum: New to Ubuntu
---

### Post by hermintrude on 2013-03-12
I have been running an old version of Ubuntu on a couple of PCs, each double-booted with XP. I have now downloaded 12.10 LTS, burned it to a CD, and tried to upgrade the two PCs. In both cases it reported that it had 'uninstalled' the old Ubuntu, but it seems to have left the HAD.DLL 'missing or corrupt', so that the boot process now ignores the CD, and only offers a choice between XP (which still boots OK) and 'Windows default' (which seems to be a replacement for the old Ubuntu option) but it fails, reporting the HAD.DLL problem.

The CD looks to have been burned OK, from the download, and it starts to run OK, but when I take the 3rd option, (Help me to boot from CD) and after it reports the uninstall, it then offers to make a 'new boot menu entry'. When I take this 'Install' option, the Ubuntu CD Boot Helper then reports an error, referring to some log-entry, which I cannot find.

The CD precedes the hard-drive in the boot-sequence on both PCs, but the HAD.DLL problem seems to trump that. It looks as if I need to clean up the debris of the (incomplete?) uninstall, by sorting out the HAD.DLL, before it will allow the CD to boot-up the new 12.10 LTS, presumably onto a PC which by then would look as if it had never had Unbuntu installed before?

So questions....
.... if that right, how do I do it?
.... if not, then what to do next?

Any advice, please.

---

### Post by Impavidus on 2013-03-12
The old dual booted ubuntu, was that a normal install or a wubi install? And have you properly burned the .iso to the cd as an image, not as a file?

There isn't really such a thing as uninstalling Ubuntu, except for uninstalling wubi. Uninstalling Ubuntu means nothing more than deleting the Ubuntu partition and installing a new (windows) boot loader, and to install a new ubuntu you can just overwrite the old one without first uninstalling it. So I'm puzzled where the uninstall step comes from.

HAD.DLL is a windows file (as are all .dll files) and is not used when booting Ubuntu. When booting Ubuntu from the Live cd no file from your hard disk is read, so it appears to me that the HAD.DLL problem only occurs after your computer has already given up on booting from the Live cd. Whatever operating systems, properly or improperly installed or uninstalled, are on your hard disk doesn't matter for your Live cd. And when you can boot from your Live cd you can install Ubuntu, whatever is on your disk (but be careful not to delete your win XP, unless you want to get rid of that anyway).

---

### Post by grahammechanical on 2013-03-12
It is my guess that you are using what was called Ubuntu Secure Remix and is now called Linix Secure Remix. [https://help.ubuntu.com/community/LinuxSecureRemix?action=show&redirect=UbuntuSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix?action=show&redirect=UbuntuSecureRemix) and you are using OS-Uninstaller, which did what you told it to do. It uninstalled that old version of Ubuntu. But the question is: Have you installed Ubuntu 12.10? Oh, by the way, 12.10 is not an LTS. It is Ubuntu 12.04 that is the present LTS version. So, there is some confusion.

---

### Post by bcbc on 2013-03-12
> **hermintrude said:**
> I have been running an old version of Ubuntu on a couple of PCs, each double-booted with XP. I have now downloaded 12.10 LTS, burned it to a CD, and tried to upgrade the two PCs. In both cases it reported that it had 'uninstalled' the old Ubuntu, but it seems to have left the HAD.DLL 'missing or corrupt', so that the boot process now ignores the CD, and only offers a choice between XP (which still boots OK) and 'Windows default' (which seems to be a replacement for the old Ubuntu option) but it fails, reporting the HAD.DLL problem.

The CD looks to have been burned OK, from the download, and it starts to run OK, but when I take the 3rd option, (Help me to boot from CD) and after it reports the uninstall, it then offers to make a 'new boot menu entry'. When I take this 'Install' option, the Ubuntu CD Boot Helper then reports an error, referring to some log-entry, which I cannot find.

The CD precedes the hard-drive in the boot-sequence on both PCs, but the HAD.DLL problem seems to trump that. It looks as if I need to clean up the debris of the (incomplete?) uninstall, by sorting out the HAD.DLL, before it will allow the CD to boot-up the new 12.10 LTS, presumably onto a PC which by then would look as if it had never had Unbuntu installed before?

So questions....
.... if that right, how do I do it?
.... if not, then what to do next?

Any advice, please.
When you have a Wubi install, rerunning Wubi will first remove the old install (everything, data, setup etc.). This is what happened. The third option, help me boot from CD, just does what it says, helps you boot from the CD for people that cannot get the BIOS to boot the CD. This is usually unnecessary - pressing F12 or whatever BIOS override key you have will let you boot from the CD. 
Installing in this way (by booting the CD), creates a normal dual boot, not a Wubi install which it appears you had previously (gone if you ran Wubi in Windows).

So, if you want to install a normal dual boot, just boot from the CD and install. If you want to upgrade, then you cannot do it from the CD. You have to do it from the booted Ubuntu install. (This may be too late for you).
If you had backups of the \ubuntu directory from Windows, you may be able to recover the old installs.


Also those HAL.DLL errors, usually just mean the boot entry is bad. Not sure what is going on, but post the contents of C:\boot.ini and I can see what's up.

---

### Post by hermintrude on 2013-03-13
Thanks for the feedback - several points....

1 ... yes, my mistake on the version number - it was (of course) the non-LTS which was 12.10, what I downloaded was 12.04 LTS.

2 ... I suspect (recall? - it was some time ago) that what I had (on both XP PCs) was a Wubi installation. I think it was visible in the Control Panel list of apps, but it also did offer Ubuntu v XP at boot time (which confused me).

3 ... Based on your advice, I'm now suspecting that I may have two different problems .... not copying/burning the boot-disk correctly, plus a bit of detritus in my boot info.

When making the CD, it offered me two different ways of copying, and I've now tried both. They both now seem to start the boot process OK (with the purple display, and four dots progressively changing colour) but after a couple of minutes they both start reporting various errors. In each case I used a blank CD-R, and their contents 'look' OK. I recently tried a different method, but it demanded a CD-RW, which I did not have to-hand.

Unfortunately, my two XP PCs are both so old that they won't boot from a USB - so I guess that I need to get the CD copy working properly. I do have another (Vista) PC, and I was thinking of also trying to make that double-booted (Vista and Ubuntu-12.04-LTS). If I can solve the CD-writing problem (for the older XP PCs), then presumably it would also work for the Vista PC, but (to get started) would it be easier to go for a USB installation on the Vista PC..?

bcbc .... I could only find a boot.ini.backup, but it was recently updated, so I suspect its contents may reflect the real thing - they are as follows....

[FONT=arial][COLOR=#0000CD][boot loader][/COLOR][/FONT]
[FONT=arial][COLOR=#0000CD]timeout=10[/COLOR][/FONT]
[FONT=arial][COLOR=#0000CD]default=C:\wubildr.mbr[/COLOR][/FONT]
[FONT=arial][COLOR=#0000CD][operating systems][/COLOR][/FONT]
[FONT=arial][COLOR=#0000CD]multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn[/COLOR]


[/FONT]
The 3rd line looks like the detritus (??), but how to get rid of it?

Thanks again for all the help.

---

### Post by bcbc on 2013-03-13
Change the boot.ini to: (notice that the "default=xxx" matches the last line up to the first "=", so you can copy it rather than try to type it)

```
[COLOR=#000000][FONT=arial][COLOR=#0000CD][boot loader][/COLOR][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][COLOR=#0000CD]timeout=10[/COLOR][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][COLOR=#0000CD]default=[/COLOR][/FONT][/COLOR][COLOR=#0000CD][FONT=arial]multi(0)disk(0)rdisk(0)partition(2)\WINDOWS[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][COLOR=#0000CD][operating systems][/COLOR][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][COLOR=#0000CD]multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Micro soft Windows XP Home Edition" /fastdetect /NoExecute=OptIn[/COLOR][/FONT][/COLOR]
```

NOTE: backup the one you have before making changes. If you make a mistake it could prevent Windows from booting. See [How to edit the Boot.ini]("http://support.microsoft.com/kb/289022") for more info.

In order to create an Ubuntu CD, you need to download the ISO and then [check the md5sum]("https://help.ubuntu.com/community/HowToMD5SUM#MD5SUM_on_Windows"). If you don't check it, then you could waste a CD by burning a corrupted ISO. If you used a torrent to download it, it's probably okay, but a web browser download can be unreliable so you need to check. 

You can also check your existing CDs by booting from them, pressing a key when you first see the keyboard and person icon (bottom centre), then select your language, and from the extended menu select "Check disk for errors". Because it's also possible that the CD is okay but maybe there are some hardware issues with an older PC.

Also, the 12.10 ISO is too big for a CD, you'd need a DVD. If you have the 10.04.2 ISO it looks like it should fit at 693MB.  So likely you did download the 12.04.2 but check anyway.

Finally, your confusing about Wubi is understandable... it installs inside Windows (hence the control panel, add/remove programs entry), but it dual boots 'natively'. So it does appear to be a normal dual boot. Under the covers there is a virtual disk/partition, so it's not the same as a normal dual boot. 
And at any time you can completely remove it by uninstalling from the Windows control panel (which it appears you have done).

---

### Post by hermintrude on 2013-03-14
Bcbc …. Thanks for the advice. As it happens I had already worked out how to burn a proper disk-image, and also that the size forced me to go to a DVD. So I had not confirmed any checksum, but now the DVD does seem to boot OK, and it offers me the run (try out) or install options, and I have tried the install, several times. On the first time I selected to install side-by-side with XP, and it then went through the partitioning process.

In due course the Ubuntu desktop came up, but it reported a ‘system problem detected’ but carried on. Then it reported that ‘Sorry Ubuntu 12.04 has experienced an internal error – if you note further problems, try restarting’. Voluminous details followed, but it included the following….
·         executable path …. /usr/bin/Xorg
·         title …. Xorg crashed with SIGABORT in miPointerUpdateSprite()
·         ‘unreportable reason’ …. ‘you have some obsolete package versions installed – please upgrade the following packages and check if the problem still occurs …. libciaccess0, xserver-common’.

I am puzzled by the concept of having obsolete packages ‘installed’, when I assumed that all the s/w was coming from the DVD..?? The desktop still seemed to ‘work’, but very slowly, and the CD-drive was in overdrive, so it did not seem to be working from the hard-drive. When I went to shut-down, it only offered ‘suspend’, and I had to power-down to restart.

Rebooting then did not offer an Ubuntu option, but when I repeated the whole installation process (several times) it always offered to re-install Ubuntu 12.04.LTS, which it seemed to recognise as already installed. Each installation attempt then consistently fails on the same ‘obsolete packages’ problem.

I guess that I could go back to the checksum point, but the problem (at least as reported) seems to be more contextual.

Any further advice would be much appreciated.

---

### Post by bcbc on 2013-03-14
What is the full hardware specs of the machine? (include brand, model, graphics card, wifi card etc.). The problem could be a hardware incompatibility coupled with a 'grasping at straws' message text.

If you can boot from the DVD, then do it, as soon as you see the keyboard/person icon (bottom centre) press any key, then select your language and it should load an extended menu - one of the options is to check the disk for errors... try this and it should verify it correctly and rule out any chance that the packages are invalid.

---

### Post by hermintrude on 2013-03-15
bcbc .... thanks for the tip on checking the disk, and it passed OK - so it's now it looks more like an install problem than a 'boot problem'.

The PC is a Dell DIMENSION 8250, Intel(R), Pentium(R)...
.... running Windows XP Home Edition Version 2002, Service Pack 3, but I suppose that is not relevant here.

It is unchanged since it came direct from Dell many years ago.

I am not aware of any wifi facility or card, and I cannot find any reference to the/a graphics card....
.... but the web suggests that the 8250 (normally) came with a AGP Geforce 4 mx420 … ??

BTW, the message sequence, during the LTS install process is consistent....
.... a one-liner, towards the end of the initial (4 dots) phase, saying:  I/O space for GPIO uninitialised
.... a message-window, after the Ubuntu desktop shows, saying:  system error detected .... but providing a 'continue' button
.... the later message-window, saying:  sorry Ubuntu 12.04 has experienced an internal error, etc, including reference to the two 'packages'

....after which no further DVD disk activity

The desktop continued 'working', but painfully slowly, and the installation appears to be incomplete, because it then is not available on re-boot.

Does that help at all ..??

---

### Post by bcbc on 2013-03-15
You should make sure you're [booting with nomodeset]("http://ubuntuforums.org/showthread.php?t=1613132") - see if that helps since the failure looks related to graphics (the one mentioning obsolete packages). But you might also want to consider running a lighter distro like Lubuntu or Xubuntu on that hardware since Ubuntu 12.04 is (near as I can tell) not really designed to work on older hardware. 

I've got an old desktop at home and it's still running 10.04 because I'm sure that it's not going to work with 12.04. But try first with nomodeset - run the updates - see how far it gets you.

---

### Post by hermintrude on 2013-03-16
bcbc .... thanks for the further advice.

I repeated the boot on the XP machine with nomodeset, and it seemed to work OK - it still reported the 'GPIO ininitialised', but not the two later messages.

It then ran Ubuntu like a dog, which brings me onto the main lesson you have taught me - don't waste time shoe-horning modern software into obsolete hardware.

In that spirit, this 'success' with XP encouraged me to try out the same boot disk on a Vista PC (Dell Inspiron 530), about half the age of the XP machine.
.... it worked fine, with none of the three messages - I'll try (dual) installing it later.

But I may also have a go at dualling Lubuntu or Xubuntu on the XP machine, as you suggested.

Thanks again for all your help.

---

### Post by hermintrude on 2013-03-16
bcbc …. sorry for the delay in replying – I thought I’d replied earlier, but I must have missed the final click..??
 
Anyway, thanks for the further advice.
 
I tried the nomodeset option, (on try out, rather than install) on the XP-PC, and that seemed to work OK….
…. it still gave the ‘space for GPIO uninitiated’ message, but not the later two messages
…. and eventually it just left me with a ‘working’ Ubuntu desktop, but it ran very slowly
 
Which comes back to the main lesson you have taught me….
…. to avoid shoe-horn-ing too much modern s/w into effectively obsolete h/w.
 
So I then ran the boot disk on a (Vista) Dell Inspiron 530 PC, which is about half the age of the XP-PC, and much bigger....
.... it ran (the try out) OK, and without the need for the nomodeset option - I’ll try the dual-boot install later.
 
I’m also following your other advice …. I’ve now made an iso disk image for Xubuntu, and I’ll have a go with that on the XP-PC.
 
Many thanks again, for all your help.

---

### Post by hermintrude on 2013-03-16
ah, now I'm starting to get the hang of it - page 1 is followed by page 2..!!

---

### Post by bcbc on 2013-03-16
Great! It sounds like you've got it all figured out. If you install on the Vista machine you might want to shrink C: from Windows' disk management console. It's generally recommended. Here's a guide via a quick google search: [http://www.liberiangeek.net/2010/02/how-to-shrink-the-primary-c-partition-in-windows-vista-windows-7/](http://www.liberiangeek.net/2010/02/how-to-shrink-the-primary-c-partition-in-windows-vista-windows-7/)

Burning a Vista repair CD (from Windows beforehand) is also a good idea.
Good luck!

---

### Post by hermintrude on 2013-03-17
OK, thanks, but one more question....
.... should I do the shrink C: before or after I do the LTS install...??
.... as I thought that the LTS install in effect did the same thing, by splitting one into two...??

---

### Post by bcbc on 2013-03-17
If you run the installer it will split C: as well. As I said, some people (including myself) tend to recommend manual partitioning for more control. It's definitely simpler to let the installer do it automatically. So if you already did it - then no prob.

---

### Post by hermintrude on 2013-03-17
bcbc .... sorry, it's me again - some progress, but I've hit another snag.

As part of my learning-curve, I'm trying (first) to complete the Xubuntu installation on the XP-PC.

I've made several attempts, but they have all failed (after showing the desktop) with a 'crash' message - I've taken the 'report' option, but ..??

Then I realised that I was not using the nomodeset option (I had been assuming that was only for Ubuntu..??)....
.... so I started again, with that option, but realised when it came to the partitioning step that the size figures were going down, and the count of other partitions was going up - now to 5.

So I quit, and now the 'Disk Management' (under 'Computer Management') is showing the following....

Healthy (EISA)                    39MB  87% free (FAT)
Healthy (Unknown Partition)  7.74GB 100% free
Healthy (Unknown Partition)  8.89GB 100% free
Healthy (Unknown Partition)  6.97GB 100% free
Healthy (Unknown Partition)  509MB 100% free
Healthy (System)                31.64GB 16% free (NTFS)

Maybe my abortive attempts are adding in more partitions, before crashing..??
.... perhaps the top 3 Unknowns (6~9 GB each) came about that way..??
.... and maybe the smaller one (509MB) is a relic of the earlier Wubi installation..??

And maybe the existence of all this detritus is what is now preventing the installation finishing correctly..??

BTW, in the meantime....
... I've corrected the BAT.INI, as you suggested, and that now boots OK - ie straight into XP
... and I've removed the remnants of (Wubi?) Unbuntu from the Apps List in Control Panel - I recall that removal of that didn't end cleanly

Would you advise me now to....
.... delete the four Unknown Partitions, using Disk Management (all 100% free)
.... try the Xubuntu installation again - setting nomodeset

---

### Post by bcbc on 2013-03-17
Yes it's been splitting your XP partition and adding a swap and root partition each time. Or maybe it split the XP partition once and now it's splitting the Ubuntu root each time... either way not good.

From Windows they appear as unknown / free but they are not. The 509MB partition is almost certainly a swap partition. Not left over from Wubi because Wubi doesn't create any partitions.

So... I would advise deleting the partitions and reinstalling. Make sure your C: drive is big enough if it's been shrunk too much (you could resize it if not). You can do all this from the installer - choose "Something else" and then delete those partitions and create two new ones in their place. One for root (/) as EXT4 and one for swap. Swap can be 500MB-1GB but if you intend to hibernate it should be larger than the RAM.

Just be careful that you don't accidentally delete the XP partition now. There is always a small risk when partitioning, and that risk gets bigger if you're not experienced with it. So maybe it will be easier to delete the partitions from Windows. Then when you run the installer, make sure it's installing into that free space.

And use nomodeset.

If you have questions just ask.

---

### Post by hermintrude on 2013-03-17
bcbc .... thanks again - progress report....

I deleted all 4 partitions OK, using Windows....
.... it created 24Gb of 'free space'

I ran the reinstall, from the Xubuntu disk - which BTW I had checked OK from the F6 menu....
.... with nomodeset option on
.... it ran without saying/showing anything about partitioning
.... the desktop came up OK
.... it finally crashed as usual, message top-right, and notification icon
.... the listed details showed the same old 'packages' fault

I went back into XP and checked the partitions config....
.... it had grabbed the whole 24Gb, 510Mb (for the swap?) and 23.?Gb (for the root?)
.... I deleted them both - back to 24Gb of free space

I repeated the installation, but this time omitting the 3rd party s/w option - just in case that was a problem....
.... exactly the same procedure and result
.... I went back into XP and deleted the same two new partitions, so back to 24Gb of free space, again

I suppose the good news is twofold....
.... at least it is consistent
.... I now seem to be able to inspect and delete partitions

Any ideas on next move, please..??

---

### Post by bcbc on 2013-03-17
Yes... you're becoming a partitioning expert now ;) So there's the silver lining. 

Okay. So in summary, you got Ubuntu installed okay (using nomodeset), but it was sluggish. Or maybe that was just running off a live CD?. Either way...
And now you're trying to install Xubuntu but it's giving the same error as before (graphics failure)?  And the install doesn't complete. 

Doesn't sound very promising. Xubuntu and Lubuntu run lighter desktop environments but I guess it depends on what sort of graphics failure it is. If not related to the desktop environment i.e. greater demands of Unity (used by Ubuntu) then it may not be any help to use Lubuntu/Xubuntu (I might be wrong but I guess they use the same underlying graphics stack).

So I'm not sure what to suggest. There was something I read about 12.04.2 having an updated graphics stack for newer computers. But I'm not sure where to find the older 12.04 or 12.04.1 ISOs. 
The other thing you can try is to use the alternate installer.

---

### Post by hermintrude on 2013-03-17
Sorry, what is 'the alternate installer'...??

---

### Post by bcbc on 2013-03-17
This is a guide to the alternate CD installer. Note that the alternate cd was dropped for 12.10. So it's only available for 12.04.2 right now. [http://members.iinet.net.au/~herman546/p2.html](http://members.iinet.net.au/~herman546/p2.html)

It installs in low graphics mode. Xubuntu has an alternate CD.

---

### Post by bcbc on 2013-03-17
PS I found the old 12.04 ISOs (12.04 and 12.04.1) here: [http://old-releases.ubuntu.com/releases/12.04.1/](http://old-releases.ubuntu.com/releases/12.04.1/)

---

### Post by hermintrude on 2013-03-18
bcbc .... great minds think alike....!!!
.... so did I - mainly triggered by your reference to 'stack' - .... mumbo-jumbo to me
.... but what caught my eye was something about Precise stack, rather than hardware enablement stack..!!

That was only after I had repeated with Lubuntu the same procedure that I had followed with Xubuntu....
.... but, as you predicted, with the same result - crash
.... different displays, but all still failing, including the initial message - GPIO space uninitiated

And I have now downloaded 12.10.1 LTS, burned the DVD, checked it, run it (with nomodeset option), and installed it, on the Dell Dimension 8250.

So we have success - thanks for all your help, and I've learned some stuff along the way.

One snag though - when I boot it up now, it just goes straight into Ubuntu, and does not offer me XP....
.... is there something I need to do to get into Windows..??

---

### Post by bcbc on 2013-03-18
Cool! That's great news. Because now you have an OS that will be supported for another couple of years.

To get Windows added, first try this from the terminal: 

```
sudo update-grub
```

Otherwise, I'll need the [booinfoscript]("http://bootinfoscript.sourceforge.net/") results to see what's up.

---

### Post by hermintrude on 2013-03-18
First, an update on behaviour....

On the LTS install, I'm sure that I opted for 'side-by-side' with XP.

When I look at the system details it shows Ubuntu in a 25Gb partition....
.... which is roughly half the hard-drive, and corresponds to what I had in 'free-space'.

When I boot....
.... it show the initial (bios?) screen OK
.... then it says it cannot show the display mode (I've tried a couple of different screens) for about 40secs
.... then it goes into the Ubuntu boot, and show that OK

So it looks to me as if it might well have installed the dual-boot, but now the boot-menu won't show, but times-out to Ubuntu....
.... just my theory..!!??

Anyway, I don't follow how or where I' supposed to type sudo, etc into the 'terminal'....
.... this sounds like the Ubuntu equivalent of the command-line
.... but I cannot get into XP to get access to its command-line
.... and I've tried looking at Ubuntu help, but got no joy there..??

If you can please give me a steer on that, then I'll type it in.

Thanks.

---

### Post by bcbc on 2013-03-18
To get to a terminal in Ubuntu enter Ctrl+Alt+T. If you're in [Xubuntu it's Super+T]("http://askubuntu.com/questions/217079/how-to-open-terminal-on-xubuntu") and Lubuntu should be the same as Ubuntu. See here for more details: [https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal](https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal)

I think your problem is that grub just isn't displaying itself. To make it show I'd suggest using the 'text' mode.

1. Get to that terminal
2. Edit the grub defaults file (you can use the command line editor 'nano' from Xubuntu and Ubuntu, or Gedit (gui) for Ubuntu or mousepad (gui) for Xubuntu. I think 'nano' is common to all, and 'vi' exists if you know it otherwise avoid it):
```
sudo nano /etc/default/grub

or

gksudo mousepad /etc/default/grub

or

gksudo gedit /etc/default/grub
```

3. Then edit the file, deleting the # from the following line:
```
#GRUB_TERMINAL=console

to

GRUB_TERMINAL=console

```

Then save and exit the editor, and regenerate grub:
```
sudo update-grub
```

---

### Post by hermintrude on 2013-03-18
Wow, that was scary .... but it worked - thanks.
.... I did used to use DOS, years ago, but I've lost the habit on that sort of stuff.

So now, after the bios bit, a boot menu comes up....
.... and sandwiched in between Ubuntu and XP there are three other options, Ubuntu (recovery) and a couple of memory-tests
.... after about 10secs it defaults through to Ubuntu - perfect..!!

I've tried it through to both Ubuntu and to XP, and they both seem to work OK.

Well, that seems to put the Dell Dimension 8250 to bed - thanks for all your help on that.

At the risk of out-staying my welcome, may I ask a couple more (hopefully final) questions....

1 .... when I try the same boot disk in an old Dell Dimension 2400, it ignores it and boots from the hard drive - but I have the setup boot-sequence to read the CD-ROM first - any thoughts..??

2 .... I'm inclined to use the same (12,04.1) version in my Vista Inspiron - even though the full 12.04.2 does seem to work OK, because I'd rather not mix versions - see any problem with that..??

Thanks again.

---

### Post by bcbc on 2013-03-18
1. Assuming it's a DVD/CD drive, and not a CD drive... I wouldn't know why it would ignore it. But there are always reports of people unable to boot from a CD/DVD. I had the same problem on one of my computers (a new one) that for some reason wouldn't boot from the Windows repair CD I had created. I tried it over and over, and finally it worked. So all I can speculate is that there is some "BIOS"/"DVD drive" disconnect over timing, or some firmware bugs - and that it's good to keep trying a few times, sometimes cold boots, sometimes warm reboots. And if it can't be done at all... then there's not much you can do about it.

2. I have 12.04 on my main computer. It's been updated with all the package releases so effectively it's on 12.04.2 but it's running the old stack (which doesn't get upgraded using the normal update manager). I think it's a good idea to just stick with 12.04.1 on both. The only reason to go with the newer is if you are aware of some fix for your hardware.

I'd recommend to setup file sharing on Ubuntu One. You get some free GB (5 or 10) and can use it to synch folders between your computers. I use that to keep copies of things I change (like /etc/default/grub). Then you don't have to try to remember something you changed on one computer but isn't yet on the second.
Or just keep notes somewhere in the cloud like Gmail or Google Drive - if you ever have to reinstall you won't remember everything.

So e.g. create a folder ~/Documents/SavedSystemChanges  (the "~/" is automatically expanded to your /home directory  i.e. /home/hermintrude/Documents/SavedSystemChanges directory) and then you can synch that to ubuntu One and copy files you change into it. e.g. from terminal:
```
cp /etc/default/grub ~/Documents/SavedSystemChanges/etc_default_grub
```

---

