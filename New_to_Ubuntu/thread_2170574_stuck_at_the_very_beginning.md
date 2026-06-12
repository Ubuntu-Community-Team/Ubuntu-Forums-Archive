---
title: "stuck at the very beginning"
date: 2013-08-26
forum: New to Ubuntu
---

### Post by kendo_nut on 2013-08-26
I have no real idea what I'm doing (hence this post), so please forgive me if the answer is blindingly obvious to everyone except me. 

I decided to get back into linux after years (more than a decade) away. 

On my windows xp service pack 3 desktop I downloaded ubuntu-12.04.3-desktop-i386.iso I also downloaded and installed a programme called 'Free Easy Burner'. Using this programme I created a DVD which I thought would act as a boot disk to allow me the choice of installing ubuntu or running it as a live distro to try it out. After burning, the DVD has the following directories [.disk boot casper dists install isolinux pics pool pressed ] and the follwing files autorun md5sum README.diskdefines wubi].

I rebooted my machine with the disk in the dvd drive and, rather than booting into windows the machine just hung, with a black screen and a flashing cursor in the top left hand corner. I waited for about 20 mins but nothing changed. I bashed a few buttons which had no effect (except a few of the function keys which beeped). I pressed ctrl-alt-del and the machine rebooted to the same spot. I pressed the same key combination and interuped the boot sequence by pressing the esc key to get to the list of locations that the machine can boot from and forced it to boot from the hard disk to get back into windows.

What am I doing wrong? I tried an old dvd with the Knoppix live distro on it and that booted (albeit slowly). Any help or advice appreciated.

---

### Post by eternal243 on 2013-08-26
Well, I have never ever used the program "Free easy burner", but the ISO is just a normal image file and should be possible to burn with most dvd burning software. Usually there is an option named "burn image" or something similar. And yes, the normal ISO should if all works out with the burning process, function both as a Live CD and Install CD, but it also contains Wubi which is the Windows Ubuntu Installer. That one should better be left alone though, since Wubi has been discontinued and won't be supported in the long run.

To me it seems the data on the CD/DVD is probably corrupt if you can't boot from it, maybe you can try another dvd burning software?

---

### Post by alphacrucis2 on 2013-08-26
If it turns out that disk burning is not the problem, another issue could be the PAE kernel that Ubuntu 12.04 32bit version uses by default. The fact you are running XP suggests your PC is fairly old. Maybe it doesn't support PAE.

---

### Post by Bashing-om on 2013-08-26
eternal243; Hi ! My welocme to the forum.

I expect that you are doing nothing wrong .. what I anticipate is a situation with the graphics card.
Try this:
Boot the liveCD;
At the purple splash screen (stick figure keyboard emblems at bottom of screen) -> hit any key ->
Language screen -> escape key to accept the default ->
Booting options screen -> f6 key (other options) -> arrow down to the preset option(s)- choose "nomodeset" space or enter to accept and then the escape key to exit; for other additions the boot options kernel boot line is also available, though not of interest at this time.
Enter key to continue the boot process to the GUI desk top; Perhaps to a degraded graphics state which is ok for now .. 
Once to the desktop on the left of the screen is the launcher -> click system settings -> additional drivers; install the recommended driver. (connected to the 'net via a wired connection)

Advise if you can get this far .. and additional advise is to follow to get the proper graphics driver loaded in the actual install.

[INDENT][INDENT]just try'n to help
[/INDENT][/INDENT]

---

### Post by eternal243 on 2013-08-26
> **Bashing-om said:**
> eternal243; Hi ! My welocme to the forum.

Thanks for the welcome, I did join the forum in 2008 though, but haven't used it much since I dropped Ubuntu quite quickly and tried some other distributions instead, I picked up Ubuntu again a few days ago to just see how it have developed over the years. =)

> **Bashing-om said:**
> 
I expect that you are doing nothing wrong .. what I anticipate is a situation with the graphics card.
Try this:
Boot the liveCD;
At the purple splash screen (stick figure keyboard emblems at bottom of screen) -> hit any key ->
Language screen -> escape key to accept the default ->
Booting options screen -> f6 key (other options) -> arrow down to the preset option(s)- choose "nomodeset" space or enter to accept and then the escape key to exit; for other additions the boot options kernel boot line is also available, though not of interest at this time.
Enter key to continue the boot process to the GUI desk top; Perhaps to a degraded graphics state which is ok for now .. 
Once to the desktop on the left of the screen is the launcher -> click system settings -> additional drivers; install the recommended driver. (connected to the 'net via a wired connection)

Advise if you can get this far .. and additional advise is to follow to get the proper graphics driver loaded in the actual install.

[INDENT][INDENT]just try'n to help
[/INDENT][/INDENT]

As I understood it he can't boot at all from the live cd, and got stuck with a blank screen as soon as he tried to reboot with the new cd in the drive. :)

---

### Post by ibjsb4 on 2013-08-26
You have downloaded the [wubi installer]("https://wiki.ubuntu.com/WubiGuide") which is used to install ubuntu inside your windows system.  If you want to just try ubuntu without installing it, you need the [live CD]("http://releases.ubuntu.com/precise/").

---

### Post by eternal243 on 2013-08-26
> **ibjsb4 said:**
> You have downloaded the [wubi installer]("https://wiki.ubuntu.com/WubiGuide") which is used to install ubuntu inside your windows system.  If you want to just try ubuntu without installing it, you need the [live CD]("http://releases.ubuntu.com/precise/").

Nope, he downloaded the **ubuntu-12.04.3-desktop-i386.iso**, which is the live cd, it does however contain the Wubi installer.

---

### Post by cmh79 on 2013-08-26
Make sure you do not have a Microsoft web cam or any other unnecessary usb devices. start with just the very basics you need for the computer to operate. Its worked for me in the past.

---

### Post by Impavidus on 2013-08-26
> **alphacrucis2 said:**
> If it turns out that disk burning is not the problem, another issue could be the PAE kernel that Ubuntu 12.04 32bit version uses by default. The fact you are running XP suggests your PC is fairly old. Maybe it doesn't support PAE.
In which case I think you can try Xubuntu, which doesn't use the pae kernel by default and is in general a better performer on older hardware. But first try Bashing-om's suggestion.

---

### Post by gil2 on 2013-08-26
I agree with Impavidus. Xubuntu would be better to you.

---

### Post by r_avital on 2013-08-26
Kendo, welcome,

This might sound silly, but I've seen this happen so many times:
An ISO file is an archive, similar in concept to a zip file.  When you burn a CD or DVD, you can do one of two things:  Make a straight copy of the ISO on the CD/DVD, or "unpack" the archive onto a CD/DVD.

So forgive a silly question, if you compare the ISO you downloaded on your Windows hard-drive, does it look exactly like the contents of your DVD?

If so, that would explain the behavior that you're seeing, this will never boot.  What you need, is to burn it in such a way that **the contents** of the ISO are burned onto your DVD, not the ISO itself.

For Windows XP (which is what you're using), here's an excellent free (voluntary contribution) tool you can download, install on Windows, and use to expand the ISO as you're burning it onto your DVD:

[http://alexfeinman.com/v2.htm](http://alexfeinman.com/v2.htm)

There are links to both 32-bit and 64-bit versions.  It's been ages since I've used it, but once installed (it's a Windows .msi file), when you right-click on your Ubuntu ISO file in Windows, the popup menu should show an option of "Burn ISO to CD/DVD" or similar language.

The DVD created from that, will be bootable.

Sorry if I was completely off-base.  Let us know.

Good luck!

---

### Post by oldrocker99 on 2013-08-26
Also, bear in mind that WinXP is nearing the end of its support, and it will surely be attacked after that...

---

### Post by mastablasta on 2013-08-27
it's attacked already anyway....

here is the instruciton on how to burnthe iso to DVD: [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by red_starfox2 on 2013-08-27
I forgot that only Linux can handle to burn a Linux iso file, with success...ruined 3 DL layer disks on windows before I tried out Brasero under Ubuntu.
Also it seams like you need a DVD-drive with DVD-RAM ability, to run a newer GUI based Linux live image. Under Win 7 Ultimate x64 I had no success with Nero or MagicISOmaker...even with a DVD-RAM compatible DVD-RW-drive...don't know if some of my experience may help you, but hope so.

Had problems booting a Linux live CD or DVD without the drive supporting the DVD-RAM feature...

---

### Post by eternal243 on 2013-08-27
> **red_starfox2 said:**
> I forgot that only Linux can handle to burn a Linux iso file, with success.

Actually there should be no problem to burn a linux ISO file from windows, I have done it several times and it has never failed. Usually I use Nero, and I have burnt images of both Ubuntu, Kubuntu, Debian, Gentoo and Sabayon, and they have always worked for me, you must either have some problem within your windows installation or you might be doing something wrong.

---

### Post by verymadpip on 2013-08-27
> **eternal243 said:**
> Actually there should be no problem to burn a linux ISO file from windows, I have done it several times and it has never failed.

This +1.

How about putting the image onto a USB drive with unetbootin?  That's available for Windows.
Of course you'll need a spare USB drive...

---

### Post by oldrocker99 on 2013-08-27
I burned a Linux .iso from within Windows 7 just using the built-in burner that opened when I right-clicked the .iso file. And it worked fine.

---

### Post by verymadpip on 2013-08-27
I don't think XP has a built-in burner.
I use something called CDBurnerXP on the XP machine I have access to.  Never had a problem.
As an aside, have you checked the MD5 sum of the iso?  The download could be frazzed.  I use an app called hashcalc to do this in Windows.

---

### Post by Pako Pako on 2013-08-27
Love Xubuntu as it makes my 1 GHz machine fly so I can attest to that.
Though that machine also runs the Knoppix recoveryCD rather well. How old must Kendo_Nut's machine be if Knoppix's liveCD runs slowly?

---

### Post by squakie on 2013-08-27
Forgive me here, but I think there is something going on besides whether it is an iso image or not.  Why?  Every PC I have ever had that had the ability to boot from CD has always had just a boot order parameter in the BIOS.  That just says what order to try to find a bootable media in - if the CD/DVD is not bootable it should just move on to the next device, in which case for the OP it should have just booted Windows XP.

So, I have to ask first - did you change the boot order in your BIOS for the CD/DVD drive to be the topmost in the list, or did you do something similar to pressing a function key for a boot menu and selecting the CD/DVD drive?

---

