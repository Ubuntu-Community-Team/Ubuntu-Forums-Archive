---
title: "Dual-boot, ubuntu works, win7 disk read error"
date: 2012-11-27
forum: New to Ubuntu
---

### Post by dyeabog on 2012-11-27
Hello everbody!

TL;DR, skip to the 5th paragraph

So i've been going through a VERY long process to something i thought was very easy (and, actually, I have done before successfully without headaches)... Anyway.

I had Win 7 installed on my laptop (HP) and i made more than 4 partitions with caused all of the partitions to be turned from basic to dynamic (at the time, I didnt know this). So then with the allocated space I installed ubuntu from a LiveUSB. Ubuntu didn't work (gave up waiting for root device, error) and Win7 didnt work (disk read error). Bummer! So i booted up the liveCD and removed linux.

Boom! Win7 works again like a charm. So I go back in, delete two partitions (HP tools and HP recovery) leaving me with system and C: and unallocated space. Reinstalled with LiveUSB. Same two errors.

Then I looked on the forum and they said it was a problem with the partitions being dynamic and not basic. So! I deleted the ubuntu partition AGAIN, and loaded up windows. Yup, they were dynamic. So I used a probably (wizard partition) to change them from dynamic to basic. 

Windows said that the partitions (system and C:) where now basic and that there were 40gb of unallocated space. I reinstalled Ubuntu for the third time and finally ubuntu worked! I am on it currently. Win 7 still gives me the disk read error though.

Any ideas would be appreciated! Here is the pastebin of the boot info script  because it seems like a common theme to post in these kind of problems:
[http://pastebin.com/FasLjM7f](http://pastebin.com/FasLjM7f)

Thank you in advanced!

---

### Post by oldfred on 2012-11-27
Does Ubuntu boot?

It looks like you have grub2 1.99 in the MBR looking to partition 72 which says it is not configured correctly. And 12.10 should have grub2 2.00 as its install. Not sure if boot script not seeing or configuration issue.

Windows looks ok from what the script shows. But after any partition changes Windows wants to do chkdsk. I would try that from a Windows repairCD or USB first.

       [http://www.sevenforums.com/tutorials/681-startup-repair.html](http://www.sevenforums.com/tutorials/681-startup-repair.html)
[http://www.w7forums.com/startup-repair-t441.html](http://www.w7forums.com/startup-repair-t441.html)
[http://www.bleepingcomputer.com/tutorials/tutorial148.html](http://www.bleepingcomputer.com/tutorials/tutorial148.html)

Some have been able to get into the internal repair console in sda1 by hitting f8 very quickly after or at same time as tying to boot from grub menu item for Windows in sda1. Others just use repairCD.

---

### Post by dyeabog on 2012-11-27
Hey!

Thanks for your response. I am able to get on Ubuntu and I just did "grub-update" to make sure I had the most update to date version. I am creating a LiveUSB win7 repair disc now to see how that works and will get back to you with how that goes!

Thanks

---

### Post by squakie on 2012-11-27
> **oldfred said:**
> Does Ubuntu boot?

It looks like you have grub2 1.99 in the MBR looking to partition 72 which says it is not configured correctly. And 12.10 should have grub2 2.00 as its install. Not sure if boot script not seeing or configuration issue.

Windows looks ok from what the script shows. But after any partition changes Windows wants to do chkdsk. I would try that from a Windows repairCD or USB first.

       [http://www.sevenforums.com/tutorials/681-startup-repair.html](http://www.sevenforums.com/tutorials/681-startup-repair.html)
[http://www.w7forums.com/startup-repair-t441.html](http://www.w7forums.com/startup-repair-t441.html)
[http://www.bleepingcomputer.com/tutorials/tutorial148.html](http://www.bleepingcomputer.com/tutorials/tutorial148.html)

Some have been able to get into the internal repair console in sda1 by hitting f8 very quickly after or at same time as tying to boot from grub menu item for Windows in sda1. Others just use repairCD.

I remember you gave me some good advice when I was going to dual boot with Win 7.  in particular you said to do the repartitioning with a Windows tool BEFORE installing ubuntu - something about the ubuntu partition could mess up the partitions in Win 7.  I don't remember the exact details, but I'm wondering if it might have something to do with whatever that was?

---

### Post by oldfred on 2012-11-27
@squakie
A possibility and why I suggest chkdsk first. Even if you use Windows to resize itself the first thing it does is a chkdsk. But when other tools are used it may work, but still best to use Windows tools for Windows & Linux tools for Linux. 

A sudo update grub really just updates the grub menu.

May be better to reinstall grub2. Either just a reinstall or a full uninstall and reinstall.

This reinstalls it:
       sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions

    
If you can boot into your system, you skip the chroot steps.
       chroot & grub uninstall & reinstall -drs305
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

    
       apt-get update #resync package index
apt-get upgrade #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade
apt-get -f install
dpkg --configure -a

            # uninstall both grub legacy & grub2 reinstall grub2 and to sda
apt-get purge grub grub-pc grub-common
mv /boot/grub /boot/grub_backup
mkdir /boot/grub
apt-get install grub-pc grub-common
grub-install /dev/sda
grub-install --recheck /dev/sda

---

### Post by dyeabog on 2012-11-27
Okay!

So, I'll tell you where im at now. With a LOT of fighting, I completely removed Ubuntu and went back to just Win7. I ran a chkdsk /f and the partitions are System (active, basic) and C:\ (basic) and unallocated (40gb).

Is there anyway to do this safely while maintaining the integrity of both operating systems?

Thanks!

---

### Post by oldfred on 2012-11-27
If you want to use 40GB, I would just use the auto side by side install into the unallocated.  
I always prefer manual partitioning as then I have total control over partitions, but I have lots of partitions. 
Just as a test with 12.04 when it came out, I did an auto install to see what it would do. I had two unallocated spaces on sdc and it took the largest and used that and installed grub to sda, but it worked without any issue.

Unless you have something very unusual with your Windows install, you should end up with a dual boot. And did you have issues on Video or other drivers?

---

### Post by dyeabog on 2012-11-27
Something must be VERY unusual with my windows install... I was on Win7, I had basic partitions AND it was chkdsk'd! I installed using LiLi LiveUSB w/ Ubuntu 12.10 and it installed it over the allocated space... Restarted... Ubuntu works fine (video drivers, everything, etc). Windows -> "A disk read error... Crtl+Alt+Del to restart"

Was I just not meant to have both?...

EDIT:

I have actually "accidentally" found a work around. I plugged in my Live Win7 Recovery USB and loaded it up. It said it had to "Repair boot problems", so I hit okay and restarted. Then in the GRUB menu I selected Win7 and it didn't work. Bummer. So i restarted and selected my Live Win7 Recovery USB and it booted DIRECTLY to my Win7 login! Now every time I boot to the Recovery USB, it goes to Windows (and windows works fine). Its a pretty awful workaround and im not even sure how it works... but it does :\

---

### Post by oldfred on 2012-11-28
Vista used to do that.

Grub2's os-prober always reverses the menu entries for the recovery partition and the  Windows Vista install. Have not seen it with Windows 7. 
Actually dangerous as if you start recovery it restores system to as purchased. And the first thing it usually does is overwrite partition table so it makes it difficult to repair if only partially done.

Best to see what is where with BootInfo. May be best to use grub customizer to rename & hide entries or manually change entries.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

    
       New Grub Customizer works with 12.10
[http://www.webupd8.org/2012/09/grub-customizer-30-released.html](http://www.webupd8.org/2012/09/grub-customizer-30-released.html)
HOWTO: Grub Customizer Updated for grub 1.99
[http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134)

---

### Post by dyeabog on 2012-11-28
Okay, I ran the script and here is the output:
[http://paste.ubuntu.com/1393712/](http://paste.ubuntu.com/1393712/)

After recommended repair:
[http://paste.ubuntu.com/1393757/](http://paste.ubuntu.com/1393757/)

Thanks

---

### Post by YannBuntu on 2012-11-28
Hello

> **dyeabog said:**
> After recommended repair:
[http://paste.ubuntu.com/1393757/](http://paste.ubuntu.com/1393757/)

You are affected by this bug of GRUB2.00: [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1061255](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1061255)

There is a workaround, but i haven't automatized it yet into Boot-Repair (because i want to be sure it is reliable), so you'll have to do it manually. Please tell us if you succeed, and exactly how (which commands you used).

---

### Post by oldfred on 2012-11-28
@Yann,
I had not seen this bug on LDM.
But would another workaround just be to add our own Windows chain entry with msdos mod not ldm mod? Or like we used to have to do with grub legcy as legacy almost never found Windows 7 to add chain entries.

LIke this with correct Windows UUID.

```
menuentry "Windows 7 (loader) (on /dev/sda1)" {

 insmod ntfs
set root=(hd0,1)
search --no-floppy --fs-uuid --set [COLOR=Red]2ae000d2e000a663[/COLOR]
chainloader +1

 }
    
```Or even this which someone once suggested. This assumes Windows on sdb1?
       menuentry "Windows 7"
{

 drivemap -s (hd0) (hd1)
set root='(hd1,msdos1)'
ntldr /bootmgr

 }
    
@dyeabog
IF willing to experiment a bit, copy the entry below which I edited with your sda1 UUID to 40_custom and see it that will boot.

       #Add menu entry to 40_custom,
gksudo gedit /etc/grub.d/40_custom

#update grub menu
sudo update-grub
    

```
menuentry "Windows 7 (loader) (on /dev/sda1) test" {
insmod ntfs
set root=(hd0,1)
search --no-floppy --fs-uuid --set 908A5B7D8A5B5F32
chainloader +1
}

```If that works you can turn off os-prober to hide the incorrect entries. If you reconfigure or add another system, you can just turn it back on with false.

#Turn off prober
gksudo gedit /etc/default/grub
#Add this line
GRUB_DISABLE_OS_PROBER=true

---

### Post by dyeabog on 2012-11-28
@oldfred:

It worked perfectly! I can start Windows 7 and login and see my files and I can start Ubuntu and everything works too!

If it isn't too much trouble, why did this menu entry work and not the other ones? 

Thanks again!

---

### Post by oldfred on 2012-11-28
Glad to know that works and it is a lot safer to suggest to users than the dd option in the bug report.

---

### Post by YannBuntu on 2012-11-28
Good job Fred :)

---

