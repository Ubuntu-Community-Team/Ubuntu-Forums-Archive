---
title: "Newbie installing Ubuntu 13.04 on replacement hard drive"
date: 2013-06-15
forum: New to Ubuntu
---

### Post by FlyingV1812 on 2013-06-15
Hi guys,

I recently ran Ubuntu 13.04 from disk to give it a try and was very impressed.

What I want to do now is install the full product on my PC however I want to install in onto a replacement hard drive.

The hard drive in my PC is running Windows XP which I want to keep (for the moment!) so I want to remove that hard drive leaving XP on it (so it is not affected by the Ubuntu install) and replace it with another hard drive onto which I will install 13.04.

The idea is that if I do wish to use XP I can 'pop the hood' take out the Ubuntu drive and replace it with the XP one, without one affecting the other!

Fortunately my hard drive is easy to remove so it would not be a problem physically swapping the drives around.

Is this possible or will it create issues?

Many thanks.

---

### Post by flanagan on 2013-06-15
Yes, that sounds plausible. I do not see any problems with that other than the fact the XP drive will just gather dust!

---

### Post by ajgreeny on 2013-06-15
If you have two hard disk bays in the machine you do not have to remove the XP disk, though it will, I accept, remove the possibility of mistakenly overwriting the XP installation.

You can use the "Something Else" option at partitioning stage and there choose to install Ubuntu to the second disk.  Do not do anything with the disk that has your ntfs partitions on it, and if the new drive is not already partitioned you can do that either from the live ubuntu system with gparted, or you can, I think, partition at installation time, the choice is yours.

With two separate physical disks you can also put grub, the linux bootloader, on to the new disk and leave windows MBR on the old one, giving you a failsafe option if grub should ever fail you.  Doing things that way you can set the second disk (Ubuntu) as the boot device and thus use grub, which will boot either XP or ubuntu, but should grub fail, you can change boot priority of your boot device and boot to XP.

If you need more help come back again for information and perhaps more details.

---

### Post by newb85 on 2013-06-15
> **ajgreeny said:**
> With two separate physical disks you can also put grub, the linux bootloader, on to the new disk and leave windows MBR on the old one, giving you a failsafe option if grub should ever fail you.  Doing things that way you can set the second disk (Ubuntu) as the boot device and thus use grub, which will boot either XP or ubuntu, but should grub fail, you can change boot priority of your boot device and boot to XP.

If you have two bays, this is what I would recommend.  It makes zero changes to your Windows HD.  It allows you to choose which OS you want to use at boot-up, without making any physical changes to the machine to switch systems.

Of course, if your Gruib fails, my first suggestion would be to run Boot-Repair from the Live DVD or USB.

---

### Post by Maverick Meerkat on 2013-06-15
Hi,

Using two hard drives is the way I have it set up on my main computer.
I think it is best to have both drives installed at the same time for these reasons:
- Boot to either operating system without swapping hardware.
- While running Ubuntu, I can see my Windows drive in my Files folder and can go in there and get stuff, photo's, files, etc.
- I don't have to worry about splitting up my main drive, and if I want a clean install of a new Ubuntu release, I just reformat my Ubuntu drive.

My drives are different sizes, so making sure which one I'm installing to is easy enough, but if in doubt, pull the plug on your Windows drive during install.

When I power up my computer, I get a purple screen with the Operating Systems listed ( GRUB menu ), in my case, Ubuntu is at the top of the list and will boot to that unless I scroll down the list with my keyboard arrows and select Windows.

I actually had a two drive setup at work and loved it there as well.
The only reason my other two computers at home have one drive is because they are Ubuntu only <3

Rick

---

### Post by cincinnatus13 on 2013-06-15
Honestly though, if the OP has two hard drives, they could theoretically just install GRUB to the Ubuntu drive and if it ever did fail for any reason, just pop that drive out. BIOS would then look for the other drive (naturally) and just boot to XP with no problem.
Am I missing something or is that another failsafe that we just overlooked?

---

### Post by wc711 on 2013-06-15
I started out with a bootable CD, but It wouldn't always boot.  Before going into the BIOS, Just decided to go ahead and do a side by side installation.  It worked better but it would still freeze and stall along with the screen "dimming".  I remembered I had a 60 gig external hard drive so I did an uninstall and got rid of the Ubuntu I had installed then I formatted the external hard drive and installed Ubuntu again.  This time it worked great.  No stalling or freezing and no dimming of the screen.  I had a little problem with the Nvidia graphics driver as I mentioned in another thread, but I was able to find Nvidia even with the really difficult screen with out the graphics driver.  After I got the driver installed it was good.  Everything was going fine. I installed a bunch of software for music, pictures and video, and even installed all my picture collection from a memory stick.  At this point, things started going wrong.  With all the new installations, I decided to set up the Backup, but I was having problems with it, and then I got a screen pop that said I had almost 300 updates ready for installation, so I dropped the backup and started the update.  After a short time I got a screen pop that said the updates could not be completed because of a lack of disk space. I've only used less than 8 gigs so far, but it suggested I empty the waste basket and delete the tmp packages lefter over from previous installations.  I only had 1 .exe file in the trash, and the only tmp folder I could find was in the system folder.  It had several folders and a few doc files.  The folders couldn't be deleted, but even so they didn't seem to be  that much space.  

I decided to reboot and when I did, I had no pointer so I plugged in a usb mouse and tried to log on, but my wireless keyboard didn't work either so I used the on screen keyboard and was able to get in.  Everything seemed normal so I went to the context menu and saw that there were no updates, but I clicked on it anyway and got a screen pop that said there was not enough disk space to complete the updates and asked if I wanted to do a partial update to which I clicked OK.  The terminal popped up and I watch it work.  There was a bunch of stuff installed, like office software and so forth, but towards the end it again said not enough disk space.  It completed whatever it was doing and shut down.
At that point I decided to check a few things and  found I had no sound even though all indicators showed I should.  I decided to reboot, and it got really bad after that.  I can't log on because I apparently have a graphic problem and it suggests I use a low graphics setup to which I click OK and all I get is the terminal.  I don't know anything about DOS except to type DIR:  What I got is desktop and the other folders.  I opened desk top and it showed two packages that had not been installed so I installed them.  Of course, I couldn't remember how to exit so I did an Alt Ctrl Delete to restart which got me back to my Windows dual boot screen.  By the way, I have noticed that even though I installed on an external hard drive, Unbuntu is back in my Programs and Features on the Control Panel.  Anyway, I've rebooted several times and always get the graphics problem screen with the low graphics suggestions.  This, of course, brings me back to the terminal.  I have reached the limit of my skill.  I did check the grub folder in my Ubuntu folder, and it was empty so I copied the contents of the grub folder on the installation disk, but I  don't know what that would do.  My next thought, since Ubuntu is in Programs and Features, is to uninstall and start all over for the 4th time.  Each time I do it, I learn more and accomplish more.  I sure would like to fix this now if I can because I have spent a lot of time with software and pics.  Any help will be much appreciated.

---

### Post by newb85 on 2013-06-16
> **cincinnatus13 said:**
> Honestly though, if the OP has two hard drives, they could theoretically just install GRUB to the Ubuntu drive and if it ever did fail for any reason, just pop that drive out. BIOS would then look for the other drive (naturally) and just boot to XP with no problem.
Am I missing something or is that another failsafe that we just overlooked?

Nope.  That's exactly what ajgreeny, Maverick Meerkat, and I were describing.

---

### Post by newb85 on 2013-06-16
@wc711 - It sounds like there's something wrong with your external HDD.  I would use live DVD/USB to check the SMART status of the drive.

Also, it sounds like you did the initial install with the Windows Ubuntu Installer (Wubi).  I make a habit of recommending people steer clear of Wubi.

---

### Post by user_of_gnomes on 2013-06-16
> After a short time I got a screen pop that said the updates could not be completed because of a lack of disk space. I've only used less than 8 gigs so far, but it suggested I empty the waste basket and delete the tmp packages lefter over from previous installations. I only had 1 .exe file in the trash, and the only tmp folder I could find was in the system folder. It had several folders and a few doc files. The folders couldn't be deleted, but even so they didn't seem to be that much space. 

Sometimes you need to do a sudo apt-get clean after having installed a lot of updates if you did not allocate a lot of disk space to the file system partition otherwise it won't load the graphical interface any more because the partition will be full with cached files. Restarting the computer afterwards should cause the graphical interface to start again. (sudo shutdown -r now)

---

### Post by cincinnatus13 on 2013-06-16
> **newb85 said:**
> Nope.  That's exactly what ajgreeny, Maverick Meerkat, and I were describing.

Ahhh, excuse me. Low sleep the last few days. I think I glanced right over it, haha.

---

### Post by FlyingV1812 on 2013-06-21
Thanks for the comments/advice. I opted to remove the XP drive in the end, put in the new drive and install Ubuntu to that! I am way too cautious sometimes but better safe than sorry!

The install went well however it has taken awhile to get used to its features.

The boot up and general operation of my PC is much quicker than with XP and I have been able to do all the things I could using XP although some things now run much better, Youtube for example.

I like the vast array of free software available and will try as many of the best ones as I can.

As a quick test I did swap the Ubuntu drive for the XP one and found that  XP booted up fine.I then switching back to the Ubuntu drive which again  booted fine.

To be honest I am not 100% sold on Ubuntu just yet (I had a few issues that took me awhile to work out mainly due to still being on the learning curve) but I certainly haven't found any reason to switch back to XP!

---

### Post by newb85 on 2013-06-21
Glad to hear it installed without a hitch.  Yes, there's a bit of a learning curve to it.  I hope no one misled you on that point.

In the end you should use what works best for you.  That might mean switching back and forth for a while, which was a great way for me to get more comfortable with Ubuntu.  When I just needed to do something quickly and didn't know how in Ubuntu, I switched to Windows.  Of course, it didn't take long for my XP install to start gathering dust, but it might be different for you.

It's only prudent to point out that it's generally not a good idea to use an End-of-Life operating system (one that is no longer supported or receiving security updates), be it Windows, Linux, or Mac.  XP will hit EoL in April of 2014.  According to Microsoft's help page,

> An unsupported version of Windows will no longer receive software updates from Windows Update. These include security updates that can help protect your PC from harmful viruses, spyware, and other malicious software, which can steal your personal information. Windows Update also installs the latest software updates to improve the reliability of Windows—new drivers for your hardware and more.

All of that applies to Ubuntu, as well.  (Although viruses and spyware are unheard of in the Linux world, updates close security vulnerabilities.)

Edit: To be fair, I should also point out that 13.04 will hit EoL in January 2014.  Upgrading Ubuntu will be cheaper and easier than upgrading Windows, though.

Ubuntu releases have a 9-month support cycle, except for Long Term Support Releases (LTS), which have a 5-hear support cycle.  12.04 was LTS, and 14.04 will be.

---

