---
title: "HOWTO: Install Ubuntu on a MacBook and use GRUB to boot."
date: 2006-08-09
forum: Outdated Tutorials &amp; Tips
---

### Post by Entity on 2006-08-09
We will delete Mac OS X as we don't use it often enough and install Ubuntu its partitions in order to take advantage of the entire disk's space. This is not a multi boot setup.

You will be able to boot Mac OS X and/or Windows XP from an external hard drive (with a GUID Partition Table) in order to update your hardware firmwares, etc. (Not covered here for the moment)

You will need :

- MacBook Mac OS X Install Disc 1 (Might not be necessary after all, see hereunder for more details)
- Ubuntu 6.06 LTS (aka Dapper Drake)
- The MacBook itself (duh!)
- A patched version of the GRUB boot loader (provided here)

***

1) First you will boot using the MacBook Mac OS X Install Disc 1. Press C on system startup.

You will then launch the Disk Utility and select you hard drive. You will click on the Options button and change GPT (GUID Partition Table) to the MS-DOS partition table. We save the change (We don't care about the partition setup for now, the default is OK).

**Update:** This first step might not be mandatory as you can convert the partition table to MD-DOS type from gparted using the Ubuntu Dapper Drake LiveCD. It would need to be tested. If it doesn't work restart from step #1.

2)  Restart the computer and now you will boot using the Ubuntu LiveCD. Press C on system startup.

In Ubuntu, simply launch the Installer as you would do in a normal installation. Partition your drive as you wish and there is no need to keep your HFS volume.

Since we change the partition table to an ms-dos type we won't get any error and the installation process will complete normaly (GREAT!)

3) When finished, set the active partition. You can use parted :

```
sudo parted

print (no flag?)
set (enter the partition number)
boot
on
print (check the boot flag!)
quit
```

4) Now you need to install the [patched version of GRUB]("http://www.ubuntuforums.org/attachment.php?attachmentid=14070&stc=1&d=1155169902") or else the boot process will hang on stage2. Let's chroot our root partition.

```
sudo mkdir /mnt/ubuntu
sudo mount /dev/sda1 /mnt/ubuntu/
sudo mount -t proc none /mnt/ubuntu/proc
sudo mount -o bind /dev /mnt/ubuntu/dev
sudo chroot /mnt/ubuntu
```

Now install the package after unzipping it.

```
unzip grub_0.97-1ubuntu10_i386.zip
dpkg -i grub_0.97-1ubuntu10_i386.deb
```

Just to be sure...

```
grub-install /dev/sda
```

Voilà! You can now restart the computer and wait for GRUB to do its job. The only difference you will note, is that you will not see the apple logo on startup anymore but a folder with a question mark instead. I would love to replace it by the Ubuntu logo! :D

FYI, I guess it would be possible to install Mac OS X on an external drive that has a GPT partition table but I can't test it tonight!

Also note, the patch was taken from [there]("http://www.scl.ameslab.gov/Projects/mini-xen/grub-a20.patch").  And I applied this patch to the package myself using the Ubuntu source package and this simple but great [howto]("https://wiki.ubuntu.com/CreatePackageFromSourcePackage?highlight=%28source%29%7C%28package%29"). It was my first time doing so! Use at your own risk. :D

---

### Post by Jukey on 2006-08-10
Sounds really cool but its destructive to OSX. That's fine if you only want ubutnu but the OSX environment is also really cool.

---

### Post by incubii on 2006-08-11
For some reason i cant download that file at all. Keeps saying im not logged in. :/

---

### Post by incubii on 2006-08-14
> **incubii said:**
> For some reason i cant download that file at all. Keeps saying im not logged in. :/

Never mind i got the file.

Also i followed your guide and it work perfectly! Hopefulyl they will add official support to ubuntu for intel macs.

I have it running on an Intel MacMini 1.666ghz

---

### Post by Entity on 2006-08-15
> **Jukey said:**
> Sounds really cool but its destructive to OSX. That's fine if you only want ubutnu but the OSX environment is also really cool.

Yes, OS X is cool. But I don't use it on a daily basis, actually after playing with it a few hours, I never booted it again.

You would still be able to boot Mac OS X and/or Windows XP from an external hard drive that has GUID Partition Table (Partionned with the OS X Disk Utility) in order to update your hardware firmwares, etc.

That is what I will do because I need those GB! ;-)

---

### Post by jedsen on 2006-08-24
Edit: nevermind, you have to click on the "partition" tab, and then change the options before you partition it.

I don't know what you mean when you say in step 1 to click on the "options button" on the Apple Disk Utility. I have no option button.

Thanks, and good riddance to OS X!

---

### Post by blot0 on 2006-08-27
i manged to get through the whole walk thru, everything happened as it should (after hunting for the right places).
reboot.. (sorry dont have it infront of me right now.. so not 100% sure)

comes up with something about starting stage 1.5

then it comes up with GRUB installing please wait (i think thats it)
and does not move any further, was like that for a good 10min, had to leave so not sure if its still like that now. but it shouldnt take that long should it?

only thing i could think of is i ran the .deb file (because i couldnt find where it was in command line) but that came up ok, nice little installer program, and seemed to install it ok.

---

### Post by Entity on 2006-08-27
> **blot0 said:**
> i manged to get through the whole walk thru, everything happened as it should (after hunting for the right places).
reboot.. (sorry dont have it infront of me right now.. so not 100% sure)

comes up with something about starting stage 1.5

then it comes up with GRUB installing please wait (i think thats it)
and does not move any further, was like that for a good 10min, had to leave so not sure if its still like that now. but it shouldnt take that long should it?

only thing i could think of is i ran the .deb file (because i couldnt find where it was in command line) but that came up ok, nice little installer program, and seemed to install it ok.

You have to upgrade grub or else you get this problem. What you need to do now is to boot from Live CD, then chroot your installed system and upgrade grub.

---

### Post by blot0 on 2006-08-27
yeah.. i figured out what i did wrong.
i wasnt chrooted into the hdd system when i did it.
did it over again when i got home and all works good now...
except when i reboot.. if i reboot. when it starts up again it just has a black screen rather then coming up with the grub stuff and loading linux.
i have to shutdown and then boot up for it to work.

bit strange, but not to much of a hassle, boots rather quickly.
just need to figure out how to get wifi working now.
i run a wpa network so its a little trickyer i'm reading.
and people having issues with wifi in the latest 686 kernel with SMP

---

### Post by mdmunoz on 2006-08-28
I apologize for my ignorance, but could someone explain how exactly I would "convert the partition table to MD-DOS type from gparted using the Ubuntu Dapper Drake LiveCD"?

I would really appreciate it, as I am now surviving solely on the Live CD.

On an unrelated note, it seems the installation error only occurs if I've updated GRUB. Of course not updating it makes the installation a moot point...

---

### Post by blot0 on 2006-08-28
i did it with the macOSX cd1.
boot with it in, goto tools up the top.
load up disk utility. select the internal hdd (not one of the partitions) then there is a tab you can select (i think its the third one from the left by memory)
and there will be an options button down the bottom.
you can select MS-DOS there, then hit partition.

---

### Post by mdmunoz on 2006-08-28
But assuming I don't have expedient access to my os x install disk, how can I use the live cd to do this?

---

### Post by mdmunoz on 2006-08-29
Okay, I have gotten through the installation without error, mounted, chrooted, etc., but when I type ```
unzip grub_0.97-1ubuntu10_i386.zip
``` I get ```
unzip:  cannot find or open grub_0.97-1ubuntu10_i386.zip, grub_0.97-1ubuntu10_i386.zip.zip or grub_0.97-1ubuntu10_i386.zip.ZIP.
```
Which is very odd, sice I just saved it to the desktop.

If I simply open the zip file and click the Install button in the UI, I am informed that it has been installed, but ```
grub-install /dev/sda
``` returns ```
Probing devices to guess BIOS drives. This may take a long time.
Could not find device for /boot: Not found or not a block device.
``` And when I restart the computer, grub fails to work in the usual manner.

What do I do?

---

### Post by blot0 on 2006-08-30
from your above post.. you didnt install the patched GRUB.
grub will be on there for you to be able to "grub-install /dev/sda"
but.. not the patched version.

because you are chrooted into you HDD and not the live CD's file system. it wont show up.
the way i managed to do it is i had the .zip file on a usb drive, i mounted that after chrooting.
cd'ed to where i mounted it and all worked fine :)

after you have mounted /dev/sda to /mnt/ubuntu (i think thats right yeah?)
sudo cp ~/Desktop/<grub file> /mnt/ubuntu
that should copy it onto your hdd.. so when you chroot over.. you should be able to unzip it and dkpg it.

but someone more experenced might want to check that.. i'm only new

---

### Post by mdmunoz on 2006-08-31
On the contrary, you said exactly what I needed to hear (10 posts and already saving people from Live CD hell?). It now works fine. Thanks to you and Entity for the guide.

I have one thing to add: I did this successfully without changing the partition table, or using the OS X cd. I did not need to use parted, since the flag was already there.

One last question: will this howto work for xubuntu?

---

### Post by jedsen on 2006-09-09
I guess those of us who ditched OS X are missing out on the SMC firmware update, which seems to make the fan more sensitive, at least until someone creates a cutter/loader.

---

### Post by goneskiing on 2006-09-24
In the install I deleted all partitions and created a "/" "swap" and "/home" set of partitions - then install went fine except bootloader (tried to install elilo).  So I used LiveCD and I copied and installed the patched grub but when I run "grub-install /dev/sda" it gives error "/boot/grub/stage1 not read correctly"

Any ideas ?  can I edit grub ?  should I just load regular grub ?

---

### Post by Entity on 2006-09-24
jedsen, for the updates, the best would be to install Mac OS X on an external drive.

goneskiing, this might be because you didn't convert the partition table to MD-DOS type?

---

### Post by louistan3 on 2006-09-25
will your your howto work with OS X still in a partition? and i just create a new partition for ubuntu?

---

### Post by mikkas on 2006-10-02
Hey Mikkas here from the UbuntuOS podcast ;)
I've been looking around the 'net and still can't really find a Working guide for installing Ubuntu on my macbook.

I'm really new to the os in general, so the whole "chroot to your install" is a little confusing to me. Anyway, I was wondering if anyone has got a dual boot working with OSX and Eft beta1? (So far I can only boot 6.06, 6.06.1crashes (Live), 6.10b1 alt kinda works, and 6.10b1 live gets stuck on the brown screen).

Would anyone also know, if a "Macbook" iso could be made / or is in the works? I think this would be SO handy for noobies like myself. Even if old versions of bootloaders were included on the iso, I wouldn't mind, I just really want to get Ubuntu installed as the main OS, with minimal hassles. So far, I've been unsuccessful for about 12 hours all up now.

Any replies would be great :) Thanks in advance.

Michael.

---

### Post by bodhi.zazen on 2006-10-12
This How-to was archived to the Ubuntu wiki.

[Ubuntu MacBook](http://doc.gwos.org/index.php/InstallUbuntuMacBook)

---

### Post by mikkas on 2006-10-12
Although I really really appreciate this, I was wondering if a dual boot wiki will ever be added (I'm quite addicted to osx now -- while waiting for Eft (of course :)).

Thanks for the guide =)
I look forward to more ;)

Mikkas

---

### Post by bodhi.zazen on 2006-10-12
> **mikkas said:**
> Although I really really appreciate this, I was wondering if a dual boot wiki will ever be added (I'm quite addicted to osx now -- while waiting for Eft (of course :)).

Thanks for the guide =)
I look forward to more ;)

Mikkas

I am aware of two guides:

[Illustrated Dual Boot Site](http://users.bigpond.net.au/hermanzone/)

[Graphical Ubuntu Install guide](http://www.psychocats.net/ubuntu/installing) [color=red]Thanks aysiu[/color]

---

### Post by mikkas on 2006-10-12
Ya, But I'm talking about Macbook specific guides to installing Ubuntu (dual boot). I've found a few, but can't get them to work.. eg.

[http://bin-false.org/?p=17](http://bin-false.org/?p=17)

*Waits for eft and grub2.0 (EFI baby!)*

---

### Post by Terry Jones on 2007-01-06
Can this process be used to tri boot  Windows, Linux and Mac OS X. I have done a quad boot on a dell gx 280 using Windows 2000, Windows XP ,Fedora Core 6, and Ubuntu Dapper Drake.  Iused the grub bootloader. I am an application developer who is trying to devlope software for people who ave physical disablities. I myself has had double cornea transplants. I am only 24 years old. The first was done in the summer 0f 2003. The second was done the fall of 2004.

---

### Post by wenfeng.su on 2007-03-13
is it possible to install Ubuntu 6.10 Edgy Eft into my Black Macbook using this HowTo?

---

### Post by coernel on 2008-03-14
i was wondering if i am able to install the patched grub loader on my 64 bit system.... becaus the file name says i386. didnt try it because i'm new on ubuntu (linux in general).

my problem is: after falling on my macbook and crashing the display ( ._. ) i am - for what reasons i dont know - not able to install the original tiger/leopard os. linux works. 
ideas?
hope any1 can help me

greetz from ger


ps. perhaps there is an patched version of the patched grub available for 64 bit?

edith says: i went through this howto with gutsy, seems i did not need to install the patched grub.

and for the poster above: there should be no problem,just try it out ;)

---

### Post by Greg K on 2008-11-02
Sorry to revive an old thread but does this still work for Intrepid? The patched version of grub was done for 6.06 with grub 0.97, I think 8.10 comes with grub 1.96?

---

### Post by Tsuki on 2008-11-05
I'd also like to know if this is still valid.  If we don't get any replies, I'll give it a go tonight!

---

### Post by regebro on 2008-11-16
I did this with a MacBook 4,1 and Intrepid, and I get the annoying 20 second wait on boot. Other that that it works. Hints on how to get rid of that is appreciated.

---

### Post by nTia89 on 2009-08-05
> **regebro said:**
> I did this with a MacBook 4,1 and Intrepid, and I get the annoying 20 second wait on boot. Other that that it works. Hints on how to get rid of that is appreciated.

quote

same problem !!!

---

