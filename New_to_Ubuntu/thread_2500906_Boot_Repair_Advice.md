---
title: "Boot Repair Advice"
date: 2024-09-15
forum: New to Ubuntu
---

### Post by jeraldweinstein on 2024-09-15
Hello,

I am not a noob however this issue I have seems like the best place to get assistance with.

[U]My system

[/U]Dell Inspiron 7506, 1TB hard drive. Dual boot Ubuntu Linux 22.04 / Windows 11. Still can access
Windows but only through BIOS.

Source of not being able to boot into Ubuntu because there is no grub boot menu appearing.

I clicked on "partial upgrade" and ran out of filesystem memory and aborted the upgrade leaving
unfinished and maxed out memory and unable to continue.

Now, If I can start a recovery boot but it hangs.

[COLOR=#333333][FONT=helvetica][COLOR=#333333][FONT=helvetica]The Boot-Repair Summary pastebin link is:
[URL="https://paste.ubuntu.com/p/yF4cW3zd8c/"]https://paste.ubuntu.com/p/yF4cW3zd8c/

[/URL][/FONT][/COLOR][/FONT][/COLOR]The report is long ( 11 partitions ) and  the recommended fix at the end seems pretty safe.

I just would really like to hear it's ok from someone who knows more about this than I do.

Thank you for your reply.

---

### Post by yancek on 2024-09-15
I expect it would work if the install of Ubuntu 22.04 on partition5 of the device is what you want.  What is the purpose of having 3 separate installations of the same release of Ubuntu on one drive and another install on the next drive?  Beginning at line 142 in boot repair.  Line 147 shows another install of 22.04 on the same partition (5) of another drive.  Do you know which you want?  Line 2 of boot repair shows syslinux installed in the MBR of that drive, was that intentional?  Line 199 shows it is not a gpt drive.

---

### Post by jeraldweinstein on 2024-09-15
Indeed partition 5 is the only partition I want to have 22.04 on.

/dev/nvme0n1p5  ext4    UUID: e19f5036-fe9a-4bec-abe7-d0eef5994ee6

In my trying to boot some I  used Ubuntu Live to install two times 22.04 in

efforts to get one or more installation would "catch" the boot loader.

I only want one 22.04.

I should delete the other ones .

I can do that using fdisk I believe. 




RE: "Line 2 of boot repair shows syslinux installed in the MBR of that  drive, was that intentional? "

Line 199 shows it is not a gpt drive."  

Should it be GPT drive in order to boot correctly?


I could use some clarification on this ( line 199 ).  I'm unclear how syslinux plays into this.  
I believe in the past I had needed to boot using a boot usb stick that had syslinux on it
and this explains why it is installed in the MBR.
Sounds reasonable.

It is not doing anything by being in the MBR I hear you saying.


For more background I do remember that the root directory contained Ubuntu 21.04 and is the 
installation that I erroneously tried to do a partial upgrade on.
It is OS #4
I was (still is?) on partition 5. ( same as the ext4 22.04 I am keeping )

It is identified as /dev/nvme1n1p5  ext4    UUID: be64308a-5955-43c3-98c0-5110fe399d26 4188b4fa-05   
OS#4 (linux):   Ubuntu 22.04.5 LTS on nvme1n1p5

It was the source of this whole mess . It now has zero percent free space
and is basically worthless at this. point.


So The default repair of the Boot-Repair utility would purge (in order to fix packages) and reinstall the grub-efi of
nvme1n1p5, 

using the following options:  nvme0n1p1/boot/efi

sounds like the ok thing to do at this point.  

What do you think?

One final question : purging packages would delete the partial upgrade packages and free up space
so it would be ok to reinstall the grub-efi on the device that was messed up in the beginning.

---

### Post by oldfred on 2024-09-16
Microsoft required gpt partitioning for UEFI boot of Windows since 2012.
Linux does not require gpt, but probably should. 
If not really using the second NVMe drive, I would convert to gpt, but that will totally erase it.

You should only have on ESP - efi system partition per drive. Am I not seeing 4 ESP on your first NVMe drive?
Remove boot,esp flags on all but first one. Easier to use gparted on live installer.
Boot-Repair defaults to first install  on reinstall. Make sure it uses correct partitions as default repair or use its advanced mode to choose install & drive you want to repair.

---

### Post by jeraldweinstein on 2024-09-16
If not really using the second NVMe drive, I would convert to gpt, but that will totally erase it.

**I actually want it to be erased.**

Line 199:

**nvme1n1    : notGPT,**    no-BIOSboot,    has-noESP,     not-usb,    not-mmc, has-os,    no-wind,    2048 sectors * 512 bytes
************************************************************************************************************

Am I not seeing 4 ESP on your first NVMe drive? Yes I found what you were referring to.

Line 302:

**nvme0n1 **                                                                                                    
&#9500;&#9472;**nvme0n1p1**  vfat     CCC9-2FE5    28fcbc4b-214b-49d0-bed4-97b963b783b6** ESP**   EFI system partition

Line 279:

**nvme01n11**:807GB:902GB:95.0GB:ext4::boot, **esp;**

Line 281:

**nvme01n**5:906GB:1007GB:101GB:ext4::boot, **esp**;

Line 286:

**nvme01n**10:1024GB:1024GB:13.6MB:ntfs::boot, **esp**;

*******************************************************************************************

Remove boot,esp flags on all but first one. Easier to use gparted on live installer.

Yes I do know how to do that.


*********************************************************************************************

Boot-Repair defaults to first install  on reinstall. 

Which install would be the first install?  

I think it is the  one I wanted to delete - the second one at:

**nvme1n1p5  **ext4     be64308a-5955-43c3-98c0-5110fe399d26 4188b4fa-05 


In which case if I delete it then would it cause problems in the recommended repair?


[B]The default repair of the Boot-Repair utility would purge (in order to fix packages) and reinstall the grub-efi of
nvme1n1p5,
using the following options:  nvme0n1p1/boot/efi[/B]

I'm unclear about this.  Isn't it a conflict if ultimately I want it deleted.  Or should I just leave it to install 
grub-efi then purge packages so I can reboot.
Then later remove it?  Or then would the boot loader become a problem a second time!


Make sure it uses  correct partitions as default repair or use its advanced mode to choose  install & drive you want to repair.         

 

Thank you Fred.

---

### Post by oldfred on 2024-09-16
If Boot-Repair is defaulting to use the second small NVMe drive's Ubuntu, can just use Advanced mode and choose the correct install.

If you convert second NVMe drive from MBR to gpt, then Boot-Repair will not find anything on that drive.

Converting to or from GPT - must have good backups.
[http://www.rodsbooks.com/gdisk/mbr2gpt.html](http://www.rodsbooks.com/gdisk/mbr2gpt.html)

Or use gparted Top menu, device, be sure you have selected correct drive.
You can also use gparted but must change device label to gpt for default partitioning first.
With gparted select gpt under device, advanced over msdos(MBR) default partitioning before starting.

---

### Post by jeraldweinstein on 2024-09-16
Boot-repair is listing only the default 100% full serving drive.
 It doesn&#8217;t list the nvme01n1p5 device.

I clicked advanced and it would ask me to delete
 files first so I could boot into the default drive

I thought I deleted about 5gb however it didn&#8217;t make a difference
 in fixing it.

Currently the grub screen contains 5 choices
 The first one is &#8220;Ubuntu&#8221;
 it will begin booting but stops booting
with message

/dev/nvme0n1p5 clean

you are in emergency mode


After that choices are maintenance or ctrl d 
to continue

 I pressed ctrl d 
and was returned to

 you are in emergency mode again

 I then pressed maintenance

 with return message in red

&#8221; Failed to start default target. Transaction got graphical. target/start
 is destructive. (emergency. target has &#8216;start&#8217; job queued, but &#8216;stop&#8217;
 is included in transaction &#8220;

The boot process hangs.

 From root in recovery mode tried to run &#8220;start x&#8221;
 and it started to load and the half of the screen
 was same color as the screen for a normal boot
 the other half was dos emergency message



 It seems like it&#8217;s going the right direction
 but the x server erring start

What does the summary show?

 thank you






 report summary
[https://pastebin](https://pastebin). ubuntu.com/p/2gQj9jvjTG/

---

### Post by oldfred on 2024-09-17
Your preferred install on p5 has some issue(s).
Does recovery mode boot to terminal?
You show. 
> TigerLake-LP GT2 [Iris Xe Graphics] DG1

But seem to be booting 22.04. I think you need 24.04 for that new of a video system.
You could try this. Have seen several users add this in place of quiet splash on LInux line in grub.
i915.enable_dc=0 intel_idle.max_cstate=1

Did you change the ESP settings, p5 was ESP, but needs to be Linux.

---

### Post by jeraldweinstein on 2024-09-17
The boot menu lists 4 kernels - each with a recovery mode from which I have drilled through each one
As noted, the Ubuntu default recovery mode is bootable to a terminal from where I can select and
 enter as root.

 Let me ask you would a viable option be to start all over with a fresh installation?

Could that just remove this default drive problem altogether?

I have backed up my home folder .

I have a live usb 22.04 stick to do this.

 Should do 24.4.

---

### Post by jeraldweinstein on 2024-09-17
I&#8217;ll try first replacing the quiet splash in grub.
 And checking the esp settings on p5.

---

### Post by ajgreeny on 2024-09-17
No, not in grub.cfg but in **/etc/default/grub**

---

### Post by jeraldweinstein on 2024-09-18
Decided to install 24.04. 

Then deleted the problem partition altogether.


All back to normal now.

Thanks oldfred and ajgreeny.

---

