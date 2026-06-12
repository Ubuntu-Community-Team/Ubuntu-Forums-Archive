---
title: "Dual Boot with 2 hard drives - Where to put GRUB"
date: 2008-11-08
forum: New to Ubuntu
---

### Post by Go_Big_Blue on 2008-11-08
Well - I'm another "newbie", so pardon this post.  But I have searched the forums and can't seem to find the answer to my particular question.  So here goes.

Desktop computer (generic) with Intel Quad Core Processor, 2 GB of RAM, and two SATA hard drives, one 320GB and one 160GB.

I have Windows XP Pro installed on a 320GB hard drive, /dev/sda1.

I am wanting to install Ubuntu 8.04.1 Hardy Heron on the second drive, currently /dev/sdb1.  

NOTE: before starting, I did NOT change any of the jumper settings or anything like that, so Windows is still the MASTER.

As I go through the install wizard, and I get to step five (the partitioner), I chose to install Ubuntu on /dev/sdb.  No problems so far.  But when I got to the end, step 7, I clicked on Advanced because I wanted to see what the settings were and what other options I had.

In the Advanced tab, it has "Install GRUB Loader" (or something similar to that) with a check box checked off.  Then the location for GRUB to be installed is (hd0).  In the drop down list, it also lists the following:
[LIST]
[*]/dev/sda ATA WDC WD3200AAJS-0 (298.1 GB)
[*]/dev/sda1 Microsoft Windows XP Professional
[*]/dev/sda-1
[*]/dev/sdb ATA WDC WD1600AAJS-6 (149.1 GB)
[*]/dev/sdb1
[/LIST]

I would prefer to not have to enter the BIOS every time I want to boot into Ubuntu, and I would also prefer to not have to take my machine apart to change the jumpers. So, here is my question.

Can I select to have GRUB load to /dev/sda1 where my Windows Installation is, and still install Hardy to /dev/sdb1?  If so, will it screw up my ability to boot into Windows?

Sorry it's so long, but I just like to know what it is that I am doing before I do it.  Thanks for the help.

---

### Post by kansasnoob on 2008-11-08
I can really only refer you to Herman's Grub Page:

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by Go_Big_Blue on 2008-11-08
Wow! Thanks for such a quick response! :)  But I can't find where on his website to go to find the answer to my question.  Any particular area you think I should look (he's got alot of stuff and links on there)?

---

### Post by cdtech on 2008-11-08
With your situation you would want to install to the primary drive sda1 which XP is installed on. This will overwrite the MBR of that drive. You would have no problems repairing the MBR if you ever had to with Windows.

You may need to alter the /boot/grub/menu.lst once you can boot into Ubuntu in order to boot Windows properly, no big deal though.

Good luck.......

---

### Post by Go_Big_Blue on 2008-11-08
Man - this is awesome! I never received this kind of quick response on Windows forums! Totally cool! 

So, if I understand you correctly ... partition /dev/sda1 and load Ubuntu onto the same HDD as the Windows XP Professional installation?

What would I used /dev/sdb1 for? Just use it as storage?

---

### Post by WWSmith36 on 2008-11-08
I prefer not to overwrite windows boot loader.  Here is my configuration.

sda - Ubuntu with grub on MBR
sdb - Windows with windows bootloader on MBR

Then I created Windows entry with map command in /boot/menu.lst

```
### END DEBIAN AUTOMAGIC KERNELS LIST

title	Other Operating Systems  
root

title		Window XP Professional
		rootnoverify (hd1)
		map (hd0) (hd1)
		map (hd1) (hd0)
		chainloader +1
```

If you install grub on windows mbr, and something happens to the ubuntu disk, you will not be able to boot windows either.  You will have to reinstall windows bootloader to mbr to get your system working again.  I prefer to keep the disks and OS´s as independent as possible.

There is not right or wrong way to do this - its just personal preference.

---

### Post by cdtech on 2008-11-08
> **Go_Big_Blue said:**
> I am wanting to install Ubuntu 8.04.1 Hardy Heron on the second drive, currently /dev/sdb1.  


You said you wanted it on the second hard drive.......
Just direct your installation to the sdb drive and install grub on the sda drive, If you don't want to use your BIOS to select the drive order.

---

### Post by cdtech on 2008-11-08
I run a dual boot dual drive like you want. I have my original Vista drive and a separete Ubuntu drive. I just swapped my primary (Vista) with the secondary (Ubuntu) within the computer. I did the Ubuntu install to the sda (my new Ubuntu drive) and installed the GRUB bootloader to that drive. It found Vista and added it to the menu list for me. Now when I boot into the primary drive (Ubuntu) I can select the unchanged Vista drive as well.

---

### Post by bumanie on 2008-11-08
If using a live cd, the installer should do you want by default.

---

### Post by ad_267 on 2008-11-08
Yeah I have to say, just let the installer stick GRUB where it wants and you won't have any problems. It will install it on /dev/sda1 automatically. I don't even bother to check those advanced settings.

---

### Post by ugm6hr on 2008-11-08
> **Go_Big_Blue said:**
> I would prefer to not have to enter the BIOS every time I want to boot into Ubuntu, and I would also prefer to not have to take my machine apart to change the jumpers. So, here is my question.

Can I select to have GRUB load to /dev/sda1 where my Windows Installation is, and still install Hardy to /dev/sdb1?  If so, will it screw up my ability to boot into Windows?

GRUB can be installed on either HD, and it will work just fine, provided both HDs are OK and installed.  However, for future protection, I would suggest writing GRUB to hd1 (what GRUB identifies your 2nd HD as - i.e. sdb).  If you do this, you will have to change the BIOS boot order **once** only (to boot the Ubuntu HD - sdb - as 1st boot priority, ahead of Windows HD).

Let me explain the options, which will hopefully illustrate why:

If you use the default setting, with GRUB on hd0 MBR, GRUB will boot from the WIndows HD, then locate its settings from the Ubuntu HD, giving you the option screen to select which OS you want.  Works great.  Except, if you develop a hardware problem with either HD, or you remove one of the HDs, **neither** OS will boot at all, since GRUB is dependent on both, and GRUB has overwritten the original Windows boot loader.

If you install GRUB to hd1 MBR, you have to change boot priority (but only once - not every time you boot).  But, GRUB resides on the Ubuntu HD MBR, accesses its settings on the Ubuntu HD, and then offers you the OS selection screen.  If your Windows HD fails, Ubuntu will continue to function independently.  If your Ubuntu HD fails, you can simply return to BIOS, reset the boot priority to Windows HD first, and then Windows will boot (using its own, untouched boot loader).

Does that make sense?

Even if you have already installed GRUB to hd0, it is possible to reinstall the Windows bootloader ([http://www.users.bigpond.net.au/hermanzone/p18.htm#MbrFix.exe](http://www.users.bigpond.net.au/hermanzone/p18.htm#MbrFix.exe)) which will prevent you booting Ubuntu, and then reinstall GRUB to hd1 (or reinstall Ubuntu again from scratch with GRUB) to allow access to Ubuntu.  Have to say - I can't remember how to reinstall GRUB alone from the Ubuntu LiveCD - but it must be possible (else the Super GRUB disk will do it for you).

Hope that helps.

---

### Post by Go_Big_Blue on 2008-11-08
I cancelled the install on Step 7 so I still have the option of installing GRUB where I want.  And I understand what you're saying with respect to placing GRUB on hd1.  But ...

The BIOS currently does not see both HDD's.  I don't know why, but it doesn't.  It sees both DVD/CD drives, but only one HDD.  I presume it only sees 1 because they are set up in a MASTER/SLAVE arrangement, but I am unsure of that.

Because the BIOS only sees 1 HDD, would you still recommend installing GRUB on hd1?  If yes, would I select /dev/sdb1 under the Advanced tab during step 7 of the installation process?  Or, would you recommend going ahead and jumpering out the HDD's the way everyone seems to be recommending?

---

### Post by ugm6hr on 2008-11-08
> **Go_Big_Blue said:**
> Because the BIOS only sees 1 HDD, would you still recommend installing GRUB on hd1?  If yes, would I select /dev/sdb1 under the Advanced tab during step 7 of the installation process?  Or, would you recommend going ahead and jumpering out the HDD's the way everyone seems to be recommending?

That is unusual, and the MASTER / SLAVE issue shouldn't matter. This is obviously an idiosyncrasy of your BIOS.

If you can't get BIOS to boot the Ubuntu drive (hd1), then your options are to:

1. Swap the Ubuntu and Windows HDs using the jumper settings (so that Ubuntu=hd0 and Windows=hd1) and install Ubuntu using default hd0 GRUB.

2. Just install it as it is, with GRUB on the Windows HD.

Obviously, option 2 has the potential downside as discussed above. If the Windows HD had the problem in the future, you could still install GRUB to the Ubuntu HD in the future, in order to boot into Ubuntu (or you could do that now - install GRUB to both hd0 and hd1). But Windows would be harder to recover, except with a original Windows CD (not OEM).  Not that it's impossible - just a significant nuisance.

Your choice...

---

### Post by Go_Big_Blue on 2008-11-08
I'll have to check the BIOS again.  Shouldn't take me too long, but as I recall, it only showed the two DVD/CD drives and one HDD.

---

### Post by Go_Big_Blue on 2008-11-08
The BIOS seems to be "fancy pants".  It is written by American Megatrends, Inc., and I am running AMIBIOS Version 0401, Build date 07/19/07.  Regardless, it has 2 different configuration settings:
1) I can change the boot order between either of the 2 IDE devices and the selected HDD, or
2) I can change the HDD boot priority.  

So, I presume that based on your suggestion, I select to boot from hd1, and then just let GRUB install on there.  Then, when I reboot, it should provide me with the selection menu of which OS I wish to start.  Is that correct?

---

### Post by bumanie on 2008-11-08
I have come across the issue of idiosyncratic Bios's before. I once had a dual boot that would only boot into linux with super grub disc; /boot/grub/menu.lst, /etc/fstab were set up correctly but it wouldn't boot correctly. Unfortunately if your BIOS is like this, there might not be much you can do other than try super grub disk - I had to use it on every boot into ubuntu - quite annoying, but better than being unable to use ubuntu at all. Sorry, this doesn't help solve the issue.

---

### Post by ugm6hr on 2008-11-08
> **Go_Big_Blue said:**
> So, I presume that based on your suggestion, I select to boot from hd1, and then just let GRUB install on there.  Then, when I reboot, it should provide me with the selection menu of which OS I wish to start.  Is that correct?

Yes.  But just one point...

If you change the BIOS selection prior to installing (rather than after), it is likely that will actually change the HD labelling too.  I have never fully understood how this works, but, in general...

hd0 = 1st boot device

Do a little experimenting to see.  If you get it wrong - no harm done - you can just use mbrfix to reinstate the Windows bootloader, and then install GRUB to the Ubuntu HD.

---

### Post by caljohnsmith on 2008-11-08
> **ugm6hr said:**
> Yes.  But just one point...

If you change the BIOS selection prior to installing (rather than after), it is likely that will actually change the HD labelling too.  I have never fully understood how this works, but, in general...

hd0 = 1st boot device

Do a little experimenting to see.  If you get it wrong - no harm done - you can just use mbrfix to reinstate the Windows bootloader, and then install GRUB to the Ubuntu HD.
Actually, changing the BIOS boot order should not change the order of drives as Ubuntu sees them, in other words how Ubuntu orders them in the /dev directory, because the drives are always ordered by IDE, SATA, USB, etc and not as the BIOS boot order (which Ubuntu has no way of knowing). The confusing point I think is that Grub sees the order of drives differently on start up then when you are running Grub commands in Ubuntu; on start up, Grub sees the order of drives simply as the BIOS boot order, so that:
```
(hd0) = 1st boot drive
(hd1) = 2nd boot drive
(hd2) = 3rd boot drive
...etc.
```
But when you run Grub commands in Ubuntu, then Grub sees the order of drives as the same order as they are in the /dev directory:
```
(hd0) = sda
(hd1) = sdb
(hd2) = sdc
...etc.
```
So on start up, (hd0) can change if you change your first boot drive, but when you work with Grub in Ubuntu, (hd0) will always be sda unless you specifically tell Grub otherwise. :)

---

### Post by Go_Big_Blue on 2008-11-08
> **ugm6hr said:**
> Yes.  But just one point...

If you change the BIOS selection prior to installing (rather than after), it is likely that will actually change the HD labelling too.  I have never fully understood how this works, but, in general...

hd0 = 1st boot device


Okay - so just to make sure that I am going to do this correctly:
1. Install Hardy on /dev/sdb1
2. Reboot and go into BIOS and change boot order

Then everything should work just fine. ???

---

### Post by SamSlater on 2008-11-08
Not sure if this would work but if you unplugged the HD with XP on it, then maybe your bios will see the other HD and you can do the Ubuntu install, then, after installation, plug the other HD back in and see if grub automatically detects the other OS, or if not, there's a way of editing /boot/grub/menu.lst to add it?

I have a duel boot with both XP and Ubuntu on the same drive, and use the second drive as backup (ntfs). That way, if one drive gets corrupted, I always have a copy of all my photos, music, vids, etc....inserting the XP disk, hitting 'r' for repair, and typing 'fixmbr' at the command always wrote the windows boot record over grub anyway.

One final thing.....what's all this master/slave thingy? You said you had 2 SATA drives? They don't have jumper settings like IDE drives do (unless they're hybrids).  :confused:

---

### Post by caljohnsmith on 2008-11-08
> **Go_Big_Blue said:**
> Okay - so just to make sure that I am going to do this correctly:
1. Install Hardy on /dev/sdb1
2. Reboot and go into BIOS and change boot order

Then everything should work just fine. ???
Sure, install Hardy to sdb1, but near the end of the installation process, click the "advanced" button, and make sure you specify Grub to be installed to /dev/sdb (not /dev/sdb1 or anything else). When it's all done, reboot, set your BIOS to boot your sdb drive, and then you should be able to boot Ubuntu no problem. If Ubuntu doesn't automatically add an entry to boot Windows, I can help you with that if you want. Let us know how it goes. :)

---

### Post by Go_Big_Blue on 2008-11-08
Thank you for the help.  I'll do it like you suggested, and let you know how it goes.

---

### Post by Go_Big_Blue on 2008-11-08
Well, it didn't work.

I installed Ubuntu on /dev/sdb.  Then when I rebooted, I went into the BIOS and selected /dev/sdb as the 1st boot drive.  Unfortunately, GRUB loaded correctly but when I selected the Ubuntu installation, it gave me an Error 17: Volume not mounted.

So, then I went to try and load the Windows XP Pro installation it gave me an Error 13: ...

So, any suggestions?

BTW - today's my boy's birthday so I will be out of pocket for the next few hours.  But we're still gonna have fun (just not on the computer). :)

---

### Post by caljohnsmith on 2008-11-08
Yes, your problem is most likely really easy to fix; go ahead and reboot again, and when you get the Grub menu, select the first Ubuntu entry, press "e" to edit it, select the line that says "root (hdX,Y)" where X and Y are numbers, press "e" to edit it, change it to "root (hd0,Y)", press return to save the change, then press "b" to boot. Based on the info you gave, I think that should be all it takes to boot Ubuntu. Note that the above change is not permanent, so you'll need to modify your menu.lst to make it permanent.

So if it works, when you get into Ubuntu, just open a terminal (Applications > Accessories > Terminal) and do:
```
gksudo gedit /boot/grub/menu.lst
```
And change the line that says "#groot=(hdX,Y)" to use the (hd0,Y) that worked to boot Ubuntu. Also, to boot Windows, at the end of your menu.lst add the following:
```
title	   Windows XP
root       (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1
```
Save, quit gedit, then run:
```
sudo update-grub
```
And hopefully you should be all set. Let me know how it goes or if you run into problems.

---

### Post by SamSlater on 2008-11-08
Maybe a little late now, but my recommending of unplugging the HD with XP installed seems to be the way this guy does what you're looking for >> [http://ubuntuforums.org/showthread.php?t=179902]("http://ubuntuforums.org/showthread.php?t=179902")

---

### Post by ugm6hr on 2008-11-08
> **caljohnsmith said:**
> Yes, your problem is most likely really easy to fix; go ahead and reboot again, and when you get the Grub menu, select the first Ubuntu entry, press "e" to edit it, select the line that says "root (hdX,Y)" where X and Y are numbers, press "e" to edit it, change it to "root (hd0,Y)", press return to save the change, then press "b" to boot. Based on the info you gave, I think that should be all it takes to boot Ubuntu. Note that the above change is not permanent, so you'll need to modify your menu.lst to make it permanent.

That sounds right - the difference between GRUB HD identities (hd0, hd1 etc) and Linux/Ubuntu HD identities (sda, sdb etc) following the change in BIOS boot order are the likely problem.

Hence the above solution.

---

### Post by Go_Big_Blue on 2008-11-09
Thank you for the advice.  I did what you said and was able to boot into Ubuntu, but I still cannot seem to boot into Windows from GRUB.  I think this stems from the issues that others have posted - Windows MBR must have Windows on (hd0).  Any thoughts?

---

### Post by Go_Big_Blue on 2008-11-09
Thank you.  I have been through that post a bit, but I would prefer to not have to crack the case open and unplug my XP drive.  That seems a bit laborious to have to do everyday that I need to get into XP.  I can live without XP, but my wife cannot and needs the computer (and specifically XP) to do her data entry job. Unfortunate really.

---

### Post by caljohnsmith on 2008-11-09
Did you add the Windows entry to your menu.lst that I gave in my previous post? And if so, what exactly happens when you choose it from the Grub menu? How about posting the full output of:
```
sudo fdisk -lu
sudo dd if=/dev/sda count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
```
And we can work from there.

---

### Post by carml on 2008-11-09
I hope,I can help submitting my experience.
I have a notebook with MS Vista as primary OS.
When I installed Vista,I created two logical drive,dividing my hard disk of 160GB.Two weeks ago I downloaded the Ubuntu distro,and I created an other logical drive reserving a part of the second one for Ubuntu;when the installation procedure asked me where to install Grub,I left it install Grub on the MBR.
Doing so,everytime I turn on my PC I can choose which OS start with,and if I don't choose nothing,it starts with Ubuntu(the option I rather),else I have onlyto select Vista from the list of the OS installed.

---

### Post by Go_Big_Blue on 2008-11-09
Because I am "analytical" by nature, I have a need to understand what it is that I am doing.  So, let me see if I can put this in "newbie" terms if I can.

> **caljohnsmith said:**
> Yes, your problem is most likely really easy to fix; go ahead and reboot again, and when you get the Grub menu, select the first Ubuntu entry, press "e" to edit it, select the line that says "root (hdX,Y)" where X and Y are numbers, press "e" to edit it, change it to "root (hd0,Y)", press return to save the change, then press "b" to boot. Based on the info you gave, I think that should be all it takes to boot Ubuntu. Note that the above change is not permanent, so you'll need to modify your menu.lst to make it permanent.

What this is doing is pointing GRUB to where the boot file is so that it will boot UBUNTU from the second HDD.  When it was first installed, GRUB was loaded on the second HDD (/dev/sdb) so it is looking for UBUNTU to be on (hd1) (i.e. /dev/sdb).  However, by changing the BIOS boot order (so that it would boot from the second HDD where GRUB and UBUNTU were installed), the BIOS re-mapped ((hd0)=/dev/sda) as (hd1) and ((hd1)=/dev/sdb) as (hd0).  By editing the GRUB UBUNTU entry, it temporarily tells GRUB where UBUNTU is located.

> **caljohnsmith said:**
> So if it works, when you get into Ubuntu, just open a terminal (Applications > Accessories > Terminal) and do:
```
gksudo gedit /boot/grub/menu.lst
```
And change the line that says "#groot=(hdX,Y)" to use the (hd0,Y) that worked to boot Ubuntu. Also, to boot Windows, at the end of your menu.lst add the following:
```
title	   Windows XP
root       (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1
```
Save, quit gedit, then run:
```
sudo update-grub
```
And hopefully you should be all set. Let me know how it goes or if you run into problems.

These steps are necessary for two reasons:
1) to permanently tell GRUB where UBUNTU is located relative to the new BIOS boot order, and 
2) the last step is to "trick" Windows into believing that it is loaded onto the (hd0) partition.  When GRUB starts and 'Windows XP Professional' is selected, GRUB then temporarily maps (hd0) to (hd1) and vice versa.  This way Windows thinks it is on (hd0) so it will boot.  But, because this is temporary, the next time you boot up and select UBUNTU, everything is back to "normal"?  

Did I get it correct?

---

### Post by carml on 2008-11-09
I hope everyone who read my previous post can understand what I wrote,because english isn't my home language,and it's a long time I don't write something in english

---

### Post by Go_Big_Blue on 2008-11-09
What you did is exactly what I did with my laptop.  In the laptop scenario, one doesn't have the option of selecting different HDD's because the BIOS of the computer knows that these are really "partitions" of the same HDD.  

The difference here being that I have two completely seperate HDD's on my desktop unit.  The MBR is located on (hd0).  When I installed UBUNTU, I told it to install GRUB on (hd1).  Without the changes above, when I reboot my computer (without changing the BIOS boot order) my computer will boot straight into Windows XP (Vista in your case) without the option to select which OS to load.

However, by changing the BIOS boot order, it loads GRUB and then gives me the option to select which OS to boot.  

The reason that I chose to do it this way was because as ugm6hr mentioned, if either HDD were happen to fail or become corrupt, I can still boot my computer into the other OS on the HDD that didn't fail.  It is a little safer approach than what we have done on our laptops.

---

### Post by caljohnsmith on 2008-11-09
> **Go_Big_Blue said:**
> 
[QUOTE=caljohnsmith]Yes, your problem is most likely really easy to fix; go ahead and reboot again, and when you get the Grub menu, select the first Ubuntu entry, press "e" to edit it, select the line that says "root (hdX,Y)" where X and Y are numbers, press "e" to edit it, change it to "root (hd0,Y)", press return to save the change, then press "b" to boot. Based on the info you gave, I think that should be all it takes to boot Ubuntu. Note that the above change is not permanent, so you'll need to modify your menu.lst to make it permanent.
What this is doing is pointing GRUB to where the boot file is so that it will boot UBUNTU from the second HDD.  When it was first installed, GRUB was loaded on the second HDD (/dev/sdb) so it is looking for UBUNTU to be on (hd1) (i.e. /dev/sdb).  However, by changing the BIOS boot order (so that it would boot from the second HDD where GRUB and UBUNTU were installed), the BIOS re-mapped ((hd0)=/dev/sda) as (hd1) and ((hd1)=/dev/sdb) as (hd0).  By editing the GRUB UBUNTU entry, it temporarily tells GRUB where UBUNTU is located.
[/quote]
You have the concept basically right, but the procedure I described in that quote just temporarily modifies your Grub's menu.lst so you can boot Ubuntu, since Ubuntu is on the first boot drive (hd0); but that procedure doesn't tell Grub where to find its boot files. When you originally installed Ubuntu and told it to install Grub to your external drive, that's when Grub was installed to the MBR (Master Boot Record) of your external drive and was configured to look on the external drive for its boot files. :)
> **Go_Big_Blue said:**
> 
These steps are necessary for two reasons:
1) to permanently tell GRUB where UBUNTU is located relative to the new BIOS boot order, and 
2) the last step is to "trick" Windows into believing that it is loaded onto the (hd0) partition.  When GRUB starts and 'Windows XP Professional' is selected, GRUB then temporarily maps (hd0) to (hd1) and vice versa.  This way Windows thinks it is on (hd0) so it will boot.  But, because this is temporary, the next time you boot up and select UBUNTU, everything is back to "normal"?  

Did I get it correct?
That's exactly right, except that changing your menu.lst will make it so you can always boot Ubuntu when booting your external drive, so you won't need to do that temporary Grub menu-editing trick I gave before. 

So the question still remains though, what happens when you boot Windows using that Grub menu entry I gave? :)

---

### Post by Go_Big_Blue on 2008-11-09
> **caljohnsmith said:**
> Did you add the Windows entry to your menu.lst that I gave in my previous post? And if so, what exactly happens when you choose it from the Grub menu? How about posting the full output of:
```
sudo fdisk -lu
sudo dd if=/dev/sda count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
```
And we can work from there.

Well, I will, but ... (you don't know me well enough yet, but I am a little, well alot ADHD) ... I forgot my username to get into UBUNTU. :biggrin:

Right now, I am rolling on the floor LMAO.

But I just re-loaded it and will let you know shortly. :biggrin:

---

### Post by Go_Big_Blue on 2008-11-09
> **caljohnsmith said:**
> Yes, your problem is most likely really easy to fix; go ahead and reboot again, and when you get the Grub menu, select the first Ubuntu entry, press "e" to edit it, select the line that says "root (hdX,Y)" where X and Y are numbers, press "e" to edit it, change it to "root (hd0,Y)", press return to save the change, then press "b" to boot. Based on the info you gave, I think that should be all it takes to boot Ubuntu. Note that the above change is not permanent, so you'll need to modify your menu.lst to make it permanent.

So if it works, when you get into Ubuntu, just open a terminal (Applications > Accessories > Terminal) and do:
```
gksudo gedit /boot/grub/menu.lst
```
And change the line that says "#groot=(hdX,Y)" to use the (hd0,Y) that worked to boot Ubuntu. Also, to boot Windows, at the end of your menu.lst add the following:
```
title	   Windows XP
root       (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1
```
Save, quit gedit, then run:
```
sudo update-grub
```
And hopefully you should be all set. Let me know how it goes or if you run into problems.

Okay - I have changed the #groot entry in menu.lst, but I found something curious at the end of the file.  So before I change it to what you suggest, this is what it currently is:

```

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
chainloader	+1
```

Should I just add the additional lines so that the last entry would then read:

```

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root       (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
savedefault
chainloader	+1
```

Your thoughts are greatly appreciated.:-|

---

### Post by caljohnsmith on 2008-11-09
Yes, that's fine if you want to use the savedefault line, just use that second Windows entry you posted to replace the first one. Then let me know what happens when you try and boot Windows from Grub.

---

### Post by Go_Big_Blue on 2008-11-09
Well, I was able to boot into Windows XP Pro with the above changes.  The only difference was the following:
```

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root       (hd1,0)
savedefault
chainloader	+1
map        (hd0) (hd1)
map        (hd1) (hd0)
```

However, I still receive the "Error 17: Unable to Mount Volume" error when I reboot and go to boot into UBUNTU.  So, what I am now proposing is the following changes to the MENU.lst file:
Old ```

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=ec537853-3fa8-404b-a222-60b8a9ba7d6a ro quiet splash
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=ec537853-3fa8-404b-a222-60b8a9ba7d6a ro single
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
```

New ```

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=ec537853-3fa8-404b-a222-60b8a9ba7d6a ro quiet splash
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=ec537853-3fa8-404b-a222-60b8a9ba7d6a ro single
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
```

In doing so, I believe this should fix the "Error 17" error.  What I have done is changed all of the roots from (hd1,0) => (hd0,0) because I am now booting from what was the 2nd HDD (/dev/sdb) but is now seen as the 1st HDD in the BIOS.

NOTE TO ALL:  All of this has been done without removing the Windows XP HDD, changing any jumpers, and only going into the BIOS one (1) time to change the boot priority.

---

### Post by Go_Big_Blue on 2008-11-09
Well, I was able to boot into Windows XP Pro with the above changes.  The only difference was the following:
```

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root       (hd1,0)
savedefault
chainloader	+1
map        (hd0) (hd1)
map        (hd1) (hd0)
```

However, I still receive the "Error 17: Unable to Mount Volume" error when I reboot and go to boot into UBUNTU.  So, what I am now proposing is the following changes to the MENU.lst file:
Old ```

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=ec537853-3fa8-404b-a222-60b8a9ba7d6a ro quiet splash
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=ec537853-3fa8-404b-a222-60b8a9ba7d6a ro single
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
```

New ```

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=ec537853-3fa8-404b-a222-60b8a9ba7d6a ro quiet splash
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=ec537853-3fa8-404b-a222-60b8a9ba7d6a ro single
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
```

In doing so, I believe this should fix the "Error 17" error.  What I have done is changed all of the roots from (hd1,0) => (hd0,0) because I am now booting from what was the 2nd HDD (/dev/sdb) but is now seen as the 1st HDD in the BIOS.

NOTE TO ALL:  All of this has been done without removing the Windows XP HDD, changing any jumpers, and only going into the BIOS one (1) time to change the boot priority.

---

### Post by caljohnsmith on 2008-11-09
Go_Big_Blue, if you change the "groot" line in your menu.lst to use the new (hd0,0) like I mentioned before, you don't need to change all your Ubuntu menu entries by hand; it's also important to change the groot line so that when you get a new kernel upgrade, it will use the correct (hd0,0). So I would recommend to just change the groot line to be:
```
# groot=(hd0,0)
```
Save, exit your menu.lst, and then run:
```
sudo update-grub
```
And then all your Ubuntu entries should be using (hd0,0) instead of (hd1,0). :)

---

### Post by Go_Big_Blue on 2008-11-09
I did make those changes, but it still gave me the error.  Did the sudo update-grub thing too.  But, the good news is that when I made the changes above to all the root lines, all OS's started up like a champ with no problemo's. :biggrin:

Here is the output from 
```

sudo fdisk -lu
sudo dd if=/dev/sda count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
```

```

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe933e933

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   625121279   312560608+   7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x10f1804c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   300415499   150207718+  83  Linux
/dev/sdb2       300415500   312576704     6080602+   5  Extended
/dev/sdb5       300415563   312576704     6080571   82  Linux swap / Solaris
```

---

### Post by Go_Big_Blue on 2008-11-09
This reply is a summary of everything that I have learned regarding how to install Ubuntu to a 2nd hard drive, and have a dual boot WITHOUT having to change the slave/master settings on your HDD's, WITHOUT having to disconnect the drive that Windows XP (or Vista) is installed on during installation, OR WITHOUT having to enter into the BIOS during every boot to select which drive to boot from.

1) Place the CD that has your Ubuntu distro on it, in your CD-ROM drive of your computer.
2) Restart your computer.  When the BIOS message pops up during start-up, enter the BIOS (by selecting F2, DEL or some other button depending on your BIOS.)
  (a) Make sure you are set to boot from the CD-ROM as your fist boot location.
  (b) Make sure you are set to boot from the HDD that has your Windows XP/Vista installation on it.  This hard drive is known as /dev/sda (hd0).
  (c) Press F10 to save any changes and exit.  It will ask you to confirm, so just hit enter for 'OK', and then your computer will restart and boot to the Ubuntu CD.  
3) Once the CD has loaded the Linux kernel and loaded the temporary installation, right click on the "Install" icon on the desktop and select "Open".  This will begin the installation wizard.
4) I believe it is in Step 4 of 7, once the partition manager has loaded, select "Guided Installation" and select the radio button for the HDD to which you want to install Ubuntu.
5) Allow the system to progress, until you get to Step 7 of 7.  Then you should have the following ready to be installed:
[LIST]
[*]Windows XP/Vista on the 1st HDD.  This is (hd0).  It is also /dev/sda.  This is where the MBR (Master Boot Record) for Windows XP/Vista is located.
[*]Ubuntu to be installed on the 2nd HDD.  This is (hd1).  It is also /dev/sdb.  This is where the GRUB loader and MBR for Ubuntu will be located.
[/LIST]
6) In Step 7 of 7, you will notice a button in the lower right hand corner of the wizard window that says "Advanced".  Click on this button.  
7) When the "Advanced" window opens up, it is telling you where it is going to install the GRUB loader.  It should say (hd0), and be part of a drop-down list.  From the drop-down list, select /dev/sdb.  This will load the GRUB loader on the same drive that your Ubuntu installation is about to be loaded onto.  (You may need to select /dev/sdX, where X may be a,b,c,d,e,f ... depending on how many HDD's you have installed on to your system.  Most individuals will only have 2 - the original and the one they just installed for Ubuntu.)
8) Select, "OK" and/or "Next" to finish the installation.  After Step 7 finishes, it will prompt you to restart your computer.  During the shutdown, it will ask you to romove the CD from the CD-ROM drive.  Do so.
9) During the reboot, press F2, DEL or whatever button will allow you to go into your BIOS (discovered in Step 2 above).  When in your BIOS, now select your computer to:
  (a) boot from your 2nd Hard Drive (the one with Ubuntu loaded on it); and 
  (b) to boot from your HDD's first, and then your CD-ROM drive.
10) Press F10 to exit and save your changes, and allow the computer to reboot.
11) The next thing that happens is that you see the GRUB loader window where you can select which operating system (OS) you want to start.
***HERE LIES THE PROBLEM (which has been reported to the Ubuntu gurus)***
12) Highlight the first UBUNTU OS line and press 'e' to edit it.
13) This will open another window that shows the root at (hd1,0).  Highlight that line and press 'e' to edit it.  This will bring you to a GRUB editor line.  Press backspace to remove the portion of the line that shows "(hd1,0)", and replace it with "(hd0,0)". Then press enter.
14) That will return you to the window that shows the root, but now it should show that the root is at (hd0,0).  If it does, great.  Now press 'b' to boot into Ubuntu.
15) Once Ubuntu loads, open a terminal window (Applications -> Terminal Window) and type the following:
```

gksudo gedit /boot/grub/menu.lst
```
It will prompt you for the administrator password, which should be the password with which you log in to Ubunt.  Scroll down through the Menu.lst file until you find a line that shows:
```

# groot (hd1,0) 
```
and change it so that it shows:
```

# groot (hd0,0) 
```
16) NOTE: you may have to use the (hdX,Y) that worked to boot Ubuntu if you have more than one hard drive installed.
17) We are almost done, so hang in there. If you saved the file, exited and rebooted and tried to go into your Windows OS, it won't work.  So we need to fix that next.  
18) To boot your Windows XP/Vista installation, scroll down to the at the end of your menu.lst until you see the follwing:
```

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
chainloader	+1 
```
We need to change these entries so that they show the following:

```

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title	        Microsoft Windows XP Professional
root            (hd1,0)
savedefault
chainloader     +1
map             (hd0) (hd1)
map             (hd1) (hd0) 
```

19) Now save the file and exit out of the text editor.
20) You should still have a terminal window open.  If so, type the following line:
```

sudo update-grub 
```
This may open a window that states there is another GRUB file on your system, but you have locally changed yours, and asks you which you want to keep.  Choose the option that says the locally changed file.
21) Now you can reboot your system and select either your Ubuntu installation or your Windows XP/Vista installation.

NOTE: one other thing that I did while I was in the Menu.lst file is to udjust the amount of time I had to select the OS that I wanted to boot.  I did this by udjusting the following line of code:
```

## timeout sec
# Set a timout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        60 
```
This changed the timeout from 10 seconds to 60 seconds before it boots into the first OS line.

The next post is an explaination of what we just did.

---

### Post by Go_Big_Blue on 2008-11-09
Why I did what I did from above.

1st, I had two hard drives on my computer (custom built, so it came that way), but I was only using one of the hard drives. So, I decided to install Ubuntu on to the 2nd hard drive that wasn't being used. (No, it didn't have a backup of XP on it.)

But, I wanted to keep both drives completely separate, that way if one drive failed, I could still use the other with no problems. (Note, I also have a 500GB external hard drive for storing just my data files.)  But, the issue is that both Windows XP and GRUB both need to be loaded on the "first" hard drive, (hd0).

So, what I did was the following:
1) Installed Ubuntu on to the 2nd hard drive, and told it to load GRUB on to that same drive (hd1,0) by selecting it from the Advanced Window at installation. (Note, it was labeled as /dev/sdb.)

2) On restart after the installation, I went into the BIOS and told the computer to start from the hard drive before the CD-ROM and also told it to start from the 2nd hard drive (hd1).  When I did this, the BIOS re-identifies the 2nd hard drive NOW as (hd0) and the 1st hard drive (the one with Windows XP on it) as (hd1).  

3) But here is the problem.  When GRUB was loaded, it was loaded and told that it was going to be installed on (hd1) not on (hd0). So, when the computer restarts, GRUB loads it program.  Then you go to select Ubuntu, but it says that the "Volume Is Not Mounted".  Correct, Ubuntu is now on (hd0), but GRUB thinks that it is on (hd1) which is where Windows XP is now.

4) So, to counter this effect, we edit the GRUB line for Ubuntu and change it temporarily to (hd0,0).  Then when Ubuntu restarts, we change the menu.lst file so that it becomes a permanent change.  Additionally, in the menu.lst program, we changed the Windows XP options so that GRUB knows that XP is now on (hd1,0).   But we also added to "map" commands.  These are necessary because Windows XP loader HAS to be on (hd0).  The map commands added at the end, "trick" windows into thinking that it is loaded on (hd0) by remapping the drives (hd1) -> (hd0) and (hd0) -> (hd1).

All of this is done so that I didn't have to open the case of my computer, set the XP drive from Master to Slave, install Ubuntu and go through a whole lot of manual labor that could potentially destroy a computer.  The pins on the backs of HDD's are easily bent and/or broken.  If that happens, you can pretty much say good-bye to that HDD.  

Hope this helps.

---

