---
title: "Newest Ubuntu disk ?"
date: 2008-09-10
forum: New to Ubuntu
---

### Post by tomsubt on 2008-09-10
Hello  I have received the ubuntu disk and want to know if I can use it without making a Dual boot. Just want to run it for awhile before I try that, I am using xp home edition,  If so how? Thanks

---

### Post by kpkeerthi on 2008-09-10
Change the boot order in your BIOS such that your CD-ROM is listed as the first boot device.

Pop in the Ubuntu CD and reboot. Ubuntu should start loading.

---

### Post by Archmage on 2008-09-10
You can also install it from Windows and have it like a sperate program that you can use and remove if you don't want it.

But kindly note that it would run faster directly. But for the first look this might work.

---

### Post by clive littlewood on 2008-09-10
Hi

Run as a "Live CD" and then you can see if Ubuntu recognises your hardware and internet connection before taking the plunge.

Hope this helps


cl

---

### Post by billgoldberg on 2008-09-10
Or you can download "Virtualbox" and run Ubuntu from within Windows.

This will allow you to modify Ubuntu (add codecs, ...) but I don't think the 3d effects will work in it.

---

### Post by tomsubt on 2008-09-10
Thanks Guys, need to ask further questions to some of you, first>>
Clive littlewood said>> Run as a "Live CD" and then you can see if Ubuntu recognises your hardware and internet connection before taking the plunge.
Do you mean just put it in the pc and start auto play?

---

### Post by mlentink on 2008-09-10
No. You will need to actually boot from the cd, so in the bios, change boot order so that it lists CD first. On some computers (like mine) you can press F9 (or F11 on others) to select the device to boot from.

Boot from the cd and you will be able to explore Ubuntu without any damage to your current setup.


@Archmage: I sincerely doubt whether you would be able to notice any perfromance effects by installing Ubuntu with Wubi (the Windows Installer.

---

### Post by tomsubt on 2008-09-10
I see, thats what kpkeerthi 
mentioned too, Thank You all for your help, thats what I will do!!!!

---

### Post by elmer_42 on 2008-09-10
Well, since you said you didn't want to set up a dual boot, you can use Wubi. The description on [their site]("http://wubi-installer.org/") pretty much sums it up in a better way than I ever could.
[QUOTE=wubi-installer.org]Wubi is an officially supported Ubuntu installer for Windows users that can bring you to the Linux world with a single click. Wubi allows you to install and uninstall Ubuntu as any other Windows application, in a simple and safe way. Are you curious about Linux and Ubuntu? Trying them out has never been easier![/QUOTE]

Also, as has been mentioned before, you could try out the LiveCD. For this, make sure you have the regular install disk (not the Alternate or Minimal disks), and boot from this CD. On all the computers I have used (and the one I have built) the first thing I do in the BIOS is set to boot from the CD. I would test that out, because I have seen a few computers that will boot from CD before booting from a hard drive.

If this doesn't work, go into the BIOS (on my PC you enter the BIOS with the [FONT="Courier New"]Delete[/FONT] key) and select the option that is something like "Boot Order" or "Boot Devices." On some PCs there is an option to chose just a boot device and stay out of the BIOS completely. If this is the case with your PC it will be showing at the bottom of the screen when you first boot up, in the same line that the  key for the BIOS will display.

**e:**Dangit, he left before he could read this. Oh well. Hopefully it will be useful to some other person.

---

### Post by billgoldberg on 2008-09-10
> **tomsubt said:**
> Thanks Guys, need to ask further questions to some of you, first>>
Clive littlewood said>> Run as a "Live CD" and then you can see if Ubuntu recognises your hardware and internet connection before taking the plunge.
Do you mean just put it in the pc and start auto play?

Yes.

But your graphics card will not work on the live cd and your internet connection (wireless) might also not work if your wireless card or usb isn't supported OOTB.

You can use Ndiswrapper if this is the case after you installed it.

--

PS: check my guide on codecs (link in signature). It will save you some questions/problems.

Also my customization guide can be useful if you want to tweak Ubuntu interface/eyecandy.

---

### Post by gregphil on 2008-09-10
Setting your bios boot order so the CD or DVD is tried before the disk drives, and rebooting with the ubuntu Live CD in the drive will run ubuntu without touching your hard drive (but run slower).

There was susposed to be a Windows program on the ubuntu Live DVD that Windows autorun would invoke and would then offer to "reboot your PC for you".  However the developer screwed up the self-check version number and as a result the Windows autorun method does not work for the ubuntu 8.04.1 Live! DVD.  (this does not inspire a load of confidence in the pre-release testing)

Hard disks (especially SATA) are soooo cheap these days the easyiest way might just be to add a new hard disk to your machine and then use the Live! disk to install to the new disk.

---

