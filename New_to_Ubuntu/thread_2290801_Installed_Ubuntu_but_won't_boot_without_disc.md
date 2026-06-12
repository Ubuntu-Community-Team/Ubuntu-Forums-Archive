---
title: "Installed Ubuntu but won't boot without disc"
date: 2015-08-15
forum: New to Ubuntu
---

### Post by Ian_Kirkman on 2015-08-15
Hi, I've installed Ubuntu 14.04.03 from a usb stick on my Acer Aspire laptop. Absolutely love it compared to Windows. However it won't boot without the stick and therefore I'm constantly in test or install mode. I understand I may have to do something with the bios settings but as I'm a beginner I'm totally stuck.
Could one of you knowledgeable guys please help?

---

### Post by dino99 on 2015-08-15
looks like your bios/uefi is still pointing to boot on the usb device; change the bios/uefi setting to boot on the internal hdd/sdd; and remove the usb stick before booting
hopes your have not forgotten to install grub (the boot loader) onto /dev/sda while doing the whole installation

---

### Post by Ian_Kirkman on 2015-08-15
Hi Dino99, thanks for your quick reply.

Ok, yes, I've changed the boot to HDD but without the stick I get the message 'No Bootable Device'

Your second bit about forgetting to install grub onto /dev/sda.  Errrrrrm, as a beginner I wasn't prompted to do that so I'm thinking that I haven't.  Is this something that can be corrected or am I totally stuffed?

Regards.  Ian

---

### Post by Ian_Kirkman on 2015-08-15
This is the procedure I followed.
My laptop is a fairly new Acer Aspire with Windows 8.1 It was getting slower and slower with all the bloatware and constantly updating and restarting and I got sick of the message 'Internet Explorer not responding' etc. So I found a guy on Youtube explaining how to install Linux.

I downloaded Ubuntu 14.04.03 LTS and used a program to burn to usb stick.
I installed to my laptop following the instructions and allowed Ubuntu to make the necessary partitions, however on the prompt to restart, it kept booting straight to Windows and even after checking for solutions on the web I couldn't change it.
Thinking I hadn't installed properly, I re-installed using the entire hard drive thinking 'well it can't keep finding Windows now'
Unfortunately it Can't find anything now.

---

### Post by Bucky Ball on 2015-08-15
You may have installed in legacy mode and Windows 8.1 is installed in UEFI mode. That won't work. If you didn't switch off secureboot in the BIOS, then that's probably what's happened. 

Do you have any idea whether you have installed in UEFI mode or legacy? Try Boot Repair and use it to make the bootinfoscript (don't do any of the repairs at this point) then post the link to it here so we can have a look at how your system is set up. 

Glad you like Ubuntu, we'll get there. ;)

Get Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Yannbuntu's thread:
[http://ubuntuforums.org/showthread.php?t=1769482](http://ubuntuforums.org/showthread.php?t=1769482)

PS: When you say "I installed to my laptop following the instructions ...": which instructions? Also, allowing Ubuntu to install 'alongside' automatically can sometimes be problematic. Better to use 'Something Else' and create the partitions manually. Goes without saying, but I'm sure you made a backup of any valuable data prior to commencing the install ... :)

---

### Post by Ian_Kirkman on 2015-08-15
Hi Bucky, yes I love Ubuntu.

In answer to your question I don't know if I installed in Legacy or UEFI. I didn't disable secure boot as at that time I knew nothing about it.
 Basically I put the stick in, changed boot to E and it loaded up. I then followed the instructions to install that came up on the screen. At the first attempt, I went with the default option of letting Ubuntu load alongside Windows creating it's own partition but when it wouldn't boot without the stick I re-installed allowing Ubuntu to format and occupy the whole disc. (I was sick of Windows constantly freezing and I had no work of note to save, so I happy to see the back of it anyway)

After foraging about for info I've tried disabling secure boot, changed boot to legacy etc. and generally tinkered about with the settings, all to no avail I'm afraid.
I guess this is something I should have done prior to installing but as I say, I'm a relative beginner.

I'll follow the link for the boot repair and see if I'm able to post the link as you suggest.

Many thanks for your time.

---

### Post by Geoffrey_Arndt on 2015-08-15
Ian, 

Here's a bit more background info that may help with your potential install/repair:

>   Generally it's not recommended or needed to disable secure boot (in most cases, best to leave it on)
>   Best to install in same environment as laptop uses to boot (if starts up by default as an UEFI device, then do the install leaving or selecting UEFI vs legacy (bios simulation)
>   Very important to disable "fast boot"  - - sometimes called "quick boot" . . . to prevent laptop from going into hibernation mode while install is in progress
>   Often best not to remove Windows, as it may mess with the hdd partitions (especially the small 100mb win partition)

Anyway,we still don't know what your PC is - or what your hard drive(s) look like.   Need PC specs especially cpu, ram, gpu (graphics system), wireless type (intel, broadcom, realtek, atheros, etc.) AND see if you can run from a LIVE linux disk or flash-stick - the gparted program so we can get a snapshot of your partitions table.

Thanks.

---

### Post by Ian_Kirkman on 2015-08-16
Hi Bucky
I've downloaded boot-repair by using the terminal, (learning all the time :-) and this is the URL it tells me to post for boot info

[http://paste.ubuntu.com/12098197/](http://paste.ubuntu.com/12098197/)

Hope this is what you require. Many thanks in anticipation.

Ian

---

### Post by yancek on 2015-08-16
Your boot repair output shows that you have Ubuntu installed on sda2 (first hard drive, second partition) using UEFI.  On sda1 is your EFI partition with the proper Ubuntu boot files and your windows is gone so that worked.  I don't use UEFI myself but you should have an option in the BIOS to enable UEFI boot rather than Legacy boot.  If you can't find that, you can continue searching or wait for someone with more experience with UEFI to suggest something.

---

### Post by Ian_Kirkman on 2015-08-16
Thanks for the reply yancek.
My machine was originally set to boot from UEFI (I think), before I tried legacy and didn't work. I noticed in the log files a message saying 'no boot loader is installed' so I'm kind of hoping that means something to Bucky or another expert. Not going to go touching things anymore till I get the nod :-)

Thanks also for Geoffrey taking the time to reply.

---

### Post by Bucky Ball on 2015-08-16
You do have secureboot off in the BIOS? Looks like it in the output.

I'm no expert but I've checked the bootinfo a few times and found this:

```
Partition 1 does not start on physical sector boundary.
```

Doubt that it has anything to do with not being able to boot, but ...

At the end of the output:

```
=================== Suggested repair
The default repair of the Boot-Repair utility would reinstall the grub-efi-amd64-signed of sda2, using the following options:        sda1/boot/efi,
Additional repair would be performed: unhide-bootmenu-10s    use-standard-efi-file rename-ms-efi
```

I suggest you launch Boot Repair and try the recommended (default) repair. There seems to be a problem with the sda2 boot files is my guess:

```
Boot files:        /boot/grub/grub.cfg /etc/fstab
```

That seems to be for regular legacy boot and it looks like you've installed in EFI. If so, unsure what's happened there. You just let Ubuntu install automagically or went for 'Something Else'?

---

### Post by Ian_Kirkman on 2015-08-16
Hi Bucky
Just checked..secure boot is disabled. No go I'm afraid.

Will try the repair as you say. Fingers crossed.

---

### Post by Bucky Ball on 2015-08-16
Only go the recommended for now. Don't try any tweaks as it may confuse the issue. :)

---

### Post by Ian_Kirkman on 2015-08-16
Ok, I think we're starting to get somewhere.

I've done the default repair and on startup I now get a blue screen with the following message
 'Default Boot Device missing or boot failed insert recovery media
Then select 'boot manager' to chose a new boot device or to boot recovery media'

I didn't put the stick in but hit 'enter'

This took me to a choice of:-
1. unknown device <WDC5000LPUX-22VOTTO>
2.windows boot manager<WDC5000LPUX-22VOTTO>

I set to the first option and hey presto, it loaded up fine. Brilliant, only problem is, I have to go through this procedure every time I start up

Any thoughts?
ps. I originally let Ubuntu install to the entire disc, (the 2nd option I think),  rather than 'something else'

---

### Post by Bucky Ball on 2015-08-16
Ok, great. So at least you can get there. I'm a bit confused with the Windows bootloader bit, seeing as you don't have Win installed, but as I say, I'm no expert. Hopefully someone can chime in who knows how to fix this:

> Default Boot Device missing or boot failed insert recovery media
Then select 'boot manager' to chose a new boot device or to boot recovery media

It might have something to do with the Win bootmanager. What happens when you choose the second option? I wonder if it tries to boot a Windows that isn't there. This may be connected to the other issue I mentioned. :-k

Can you pop out a bootinfo now, please? You can run the bootinfoscript:

BootInfoScript download:
[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

Instructions:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

PS: Yep, the partitioning looks fine: sda1 is the EFI partition, sda2 your Ubuntu install and sda3 /swap, like a Win pagefile. All pretty much as it should be. :)

---

### Post by Ian_Kirkman on 2015-08-16
Cheers Bucky

I've downloaded bootinfo and copied the code into the terminal but it's asking me for a password which I'm unable to enter.
I'll try and get my thick head around it and will post back.

Thanks

---

### Post by Bucky Ball on 2015-08-16
Just your regular password you use when logging in. It will be invisible. When you type, you will see nothing. Security. ;)

Type in your login password and hit enter.

---

### Post by Ian_Kirkman on 2015-08-16
Hi Bucky
entered my password and I'm getting message in terminal

ian1001@ian1001-Aspire-ES1-512:~$  sudo ~/Downloads/bootinfoscript
[sudo] password for ian1001: 
sudo: /home/ian1001/Downloads/bootinfoscript: command not found
ian1001@ian1001-Aspire-ES1-512:~$ 

Blimey, I might actually know something when this is all over :-)

---

### Post by Ian_Kirkman on 2015-08-16
Just thinking aloud

I had to setup a password in order to access an F12 boot menu, wonder if that's now block the way somehow?

---

### Post by Bucky Ball on 2015-08-17
I haven't used it for awhile, but should that be:

```
sudo ~/Downloads/bootinfoscript.sh
```

? Also, you have downloaded the bootinfoscript to the /Downloads folder? If bootinfoscript has another folder inside that, you should be in there prior to entering the command. 

You can also install Boot Repair directly in Ubuntu and generate the bootinfo from that.

---

### Post by monkeybrain20122 on 2015-08-17
It looks like you have installed the bootloader in the USB drive instead of the hd. Normally the fix is very easy (but see *). I would just boot from the usb drive, start the terminal and run
```
sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

Then turn off the computer, remove the usb and restart and you should be fine.

Here /dev/sda is your internal hd, /dev/sda1 is the Ubuntu partition (or the Ubuntu / partition if you have a separate one) Change these according to your configuration.

*But I don't know if it works with uefi secure boot and what not, just makes everything more complicated.

---

### Post by Ian_Kirkman on 2015-08-17
Thanks Monkeybrain

Bucky asked me to post up the bootinfo link so here it is for you both to check. (bit paranoid about doing too much without checking first :-) )

[http://paste.ubuntu.com/12109330/](http://paste.ubuntu.com/12109330/)

Thanks

---

### Post by Ian_Kirkman on 2015-08-18
Hi Monkeybrain

I've done as you say but the following message in the terminal doesn't look too promising?
Any thoughts?

ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt /dev/sda
Installing for i386-pc platform.
grub-install: warning: this GPT partition label contains no BIOS Boot Partition; embedding won't be possible.
grub-install: warning: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and their use is discouraged..
grub-install: error: will not proceed with blocklists.
ubuntu@ubuntu:~$

---

### Post by Bucky Ball on 2015-08-18
You have an EFI install. No need for grub in sda as far as I know. That might confuse things.

---

### Post by oldfred on 2015-08-18
There are two versions of grub. Grub-pc is for BIOS and grub-efi-amd64 is for UEFI. Also other versions for 32 bit or other systems.

You still install grub to drive sda, but with UEFI it knows to reinstall to ESP - efi system partition.

Since you mentioned Acer have you set the supervisory password and enabled "trust" on the Ubuntu boot files? Several threads where other Acer users set password and explain process a bit more.
 Acer Aspire ES1-512-C39M Details on supervisor password and settings to enable trust on ubuntu entries Also R14 model same fix
[http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044](http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044)
[http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot](http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot)
[http://acer.custhelp.com/app/answers/detail/a_id/29349/](http://acer.custhelp.com/app/answers/detail/a_id/29349/)
[http://acer.custhelp.com/app/answers/detail/a_id/29349/](http://acer.custhelp.com/app/answers/detail/a_id/29349/)
[http://ubuntuforums.org/showthread.php?t=2290594](http://ubuntuforums.org/showthread.php?t=2290594)
Details on password & trust setting:
[http://askubuntu.com/questions/597213/bootable-device-not-found-after-clean-install-of-ubuntu-14-04-uefi](http://askubuntu.com/questions/597213/bootable-device-not-found-after-clean-install-of-ubuntu-14-04-uefi)
How to install Ubuntu for dual-boot with Windows 8 on Acer Aspire V5-551G. Post #3 Supervisory password required
[http://ubuntuforums.org/showthread.php?t=2176273](http://ubuntuforums.org/showthread.php?t=2176273)

---

