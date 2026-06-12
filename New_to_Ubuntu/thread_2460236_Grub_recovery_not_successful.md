---
title: "Grub recovery not successful"
date: 2021-04-05
forum: New to Ubuntu
---

### Post by madhu on 2021-04-05
Hello!

I was running a Windows 10 + Ubuntu 20.04 dual boot. 

I updated by Windows to latest and enlarged the size of my C drive. I found that that I couldn't go into Ubuntu anymore.

I followed the instructions in [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) and tried to repair but I couldn't. 

Can you please help me to fix this? Below is the paste bin details

[https://paste.ubuntu.com/p/YStWXpMN2d/](https://paste.ubuntu.com/p/YStWXpMN2d/)

Thank you!

---

### Post by tea for one on 2021-04-05
[COLOR="#0000FF"]Line 396[/COLOR] - The current session is in BIOS-compatibility mode. Please disable BIOS-compatibility/CSM/Legacy mode in your UEFI firmware, and use this software from a live-CD (or live-USB) that is compatible with UEFI booting mode. For example, use a live-USB of Boot-Repair-Disk-64bit ([www.sourceforge.net/p/boot-repair-cd](www.sourceforge.net/p/boot-repair-cd)), after making sure your BIOS is set up to boot USB in EFI mode. 

Please boot your live session in UEFI mode, run the boot-repair again and post the new report.

---

### Post by oldfred on 2021-04-05
Since Windows is UEFI, you should have Ubuntu in UEFI boot mode.
Follow tea for one's advice.

But it looks like you have mount of ESP in fstab for UEFI boot, but no UEFI boot entry nor folder in ESP.
And you have grub in gpt's protective MBR for BIOS boot, and bios_grub partition sda8. Grub seems to think it is sda11, but has correct sector.

Or better to do an UEFI repair, not a BIOS type repair, since Windows is UEFI. And how you boot repair tool like Boot-Repair is then how it defaults to repair. 

You also show NTFS BS - boot sector issues. Lines 52, 62, & 72. You may just need to run chkdsk on each of those partition from Windows.
NTFS wants BS sector info to match partition table info. May not be critical if not a bootable partition, but best to repair.

Be sure to have good backups for both Ubuntu & Windows, before any changes.

---

### Post by madhu on 2021-04-05
Thanks for the detailed explanations!

I had boot Ubuntu live USB in UEFI mode this time and managed to successfully run the 'boot-repair's 'Recommended Repair' option. Now my laptop boots directly into Ubuntu and I am unable to go into Windows. Please help me fix this.

**Additional information:**

After selecting 'Recommended Repair', it prompted to run the following commands which I did

sudo chroot "/mnt/boot-sav/sda10" dpkg --configure -a
sudo chroot "/mnt/boot-sav/sda10" apt-get install -fy
sudo chroot "/mnt/boot-sav/sda10" apt-get purge -y grub*-common shim-signed

I had confirmation box with following question:

> Do you want to have all GRUB 2 files removed from /boot/grub?
This will make the system unbootable unless another boot loader is installed.
Remove GRUB 2 from /boot/grub?

I confirmed by choosing 'Yes'

Finally I ran this command

sudo chroot "/mnt/boot-sav/sda10" apt-get install -y grub-efi-amd64-signed shim-signed linux-headers-generic

I have also created a paste bin as soon as the process got finished
 [https://paste.ubuntu.com/p/mcfnFFtnVf/](https://paste.ubuntu.com/p/mcfnFFtnVf/)

---

### Post by tea for one on 2021-04-05
[COLOR="#0000FF"]Line 21 - 23[/COLOR] - Falling back to read-only mount because the NTFS partition is in an
unsafe state. Please resume and shutdown Windows fully (no hibernation
or fast restarting.)

Boot-repair will **not** recognise a Windows OS in **hibernation** state.
You will need a Windows repair disk to boot into Windows 10 and then fully shut it down i.e. not hibernating nor fast start up.

Then run boot-repair again in UEFI mode via an Ubuntu live session.
This subsequent repair should then recognise the Windows 10 OS and add it to grub.

Windows updates and manipulating disks within Windows tend to be unfriendly to dual boot systems.

---

### Post by oldfred on 2021-04-05
Since UEFI, you should be able to directly boot Windows from UEFI one time boot menu. You may need f8 then to get into Windows repair console.
But best to have Windows repair disk.
If BIOS install, you have to have a way to repair Windows when it turns fast start up back on, which it does with updates.

Fast Start up off (always on hibernation), note that Windows turns this back on with updates, SHIFT + Shut down button
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

---

### Post by madhu on 2021-04-05
Earlier I did not hibernate the Windows. Probably I exited Windows using 'Restart' instead of 'Shutdown'.

I ran the boot repair ('Recommended Repair' option - [https://paste.ubuntu.com/p/w4FQhxvBQN/](https://paste.ubuntu.com/p/w4FQhxvBQN/) ). But still I couldn't see Windows while booting. 

So in Boor Repair I went to 'Advanced Options' > 'GRUB location' tab and choose 'OS to boot by default' drop down from Ubuntu to Windows ([https://paste.ubuntu.com/p/779PpTWJG7/](https://paste.ubuntu.com/p/779PpTWJG7/)). This didn't help either.  So I repeated this step one more time ([https://paste.ubuntu.com/p/HhrPTVftR6/](https://paste.ubuntu.com/p/HhrPTVftR6/)). I did not notice any difference while booting.

---

### Post by madhu on 2021-04-05
I am sorry, I missed to read the details in one of your link. 

I tried another time after turning off the fast startup option, but still I don't see Windows as an option

I have created a paste bin from this run
[https://paste.ubuntu.com/p/T425ynZvzQ/](https://paste.ubuntu.com/p/T425ynZvzQ/)

---

### Post by tea for one on 2021-04-05
You are currently using Ubuntu (line 252)
Boot successfully repaired (line 136)

I would try```
sudo update-grub
```

Then power off and cold boot - see what happens.

The concern seems to be with your partition **sda8** (lines 20 - 21), although your Windows OS is on **sda4**.

---

### Post by oldfred on 2021-04-05
Both sda8 as bios_grub (which with UEFI you do not need) and sda3 as Windows system reserved are unformatted partitions.
As unformatted they show as errors, but those can be ignored.

Grub only boots working Windows. And that also means it cannot be hibernated. Nor fast start up which sets hibernation flag.
And Windows turns hibernation/fast start up back on with updates.  If grub does not boot Windows, you then have to directly boot Windows from UEFI and turn it off again. Then grub should boot it.

---

### Post by madhu on 2021-04-05
I have a screenshot of how each partition looks like in my hard disk. 

I have marked the sda number corresponding to each partition and uploaded it to the page below
[https://madhusundar.com/ubuntu-grub-load-error/](https://madhusundar.com/ubuntu-grub-load-error/)

Hoping this might help to understand why there are errors related to sda3 and sda8. 

Separately, earlier when I had Grub load problems, I had reinstalled Ubuntu on an already existing ext4 partition on which Ubuntu was running. Each time I did this, the Ubuntu (20.04) installation process added a new 500 MB partition to Windows (probably this 500 MB was removed from ext4 and added to Windows). I find this wired, I have Ubuntu installation several times in past 15 years. Never encountered this before. Recently I merged these two 500 MB partitions into one partition which is what seen as sda9 in the screenshot. I am not quiet sure whether these details are relevant to the current issue, anyways sharing just in case.  

Thank you!

---

### Post by tea for one on 2021-04-06
I am not clear where you are now?

Can you boot into Ubuntu 20.04?
Can you boot into Windows 10?

---

### Post by madhu on 2021-04-06
I am able to boot into Ubuntu 20.04 and Windows 10. 

By default it boots into Ubuntu 20.04. If need to go into Windows 10, I need to go into boot setup every time. 

I would like to be able to choose between two when it boots.

---

### Post by oldfred on 2021-04-06
Did you turn off fast start up as per post #6.
And then run grub's update per post #9.

And is Ubuntu now in UEFI boot mode as grub can only boot other installs in same boot mode.

---

### Post by madhu on 2021-04-08
> Did you turn off fast start up as per post #6.
And then run grub's update per post #9.

Yes, I did! Still I am unable to see Windows during the booting process.

---

### Post by tea for one on 2021-04-08
When you ran **sudo update-grub**, did the terminal response indicate:-

Found [COLOR="#0000FF"]Windows Boot Manager[/COLOR] (or similar phrase)?

---

### Post by madhu on 2021-04-09
Yes, Windows Boot Manager is displayed when I run **sudo update-grub**

It shows the following 

> superadmin@superadmin-Inspiron-7537:~$ sudo update-grub
[sudo] password for superadmin: 
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-5.8.0-48-generic
Found initrd image: /boot/initrd.img-5.8.0-48-generic
Found linux image: /boot/vmlinuz-5.8.0-45-generic
Found initrd image: /boot/initrd.img-5.8.0-45-generic
Found Windows Boot Manager on /dev/sda2@/EFI/Microsoft/Boot/bootmgfw.efi
Adding boot menu entry for UEFI Firmware Settings
done

---

### Post by tea for one on 2021-04-09
That output looks fine.

When you power on the PC, do you see the Grub menu?

---

### Post by madhu on 2021-04-09
No, I still don't see. It directly goes into Ubuntu without giving the choice to choose.

---

### Post by oldfred on 2021-04-09
I did not see this in your Boot-Repair summary report.
Post this in code tags.

cat /etc/default/grub

---

### Post by tea for one on 2021-04-09
As indicated by **oldfred**, it looks like grub may need a tweak.
If it is any help, here is a copy of [COLOR="#0000FF"]/etc/default/grub[/COLOR], where grub appears after power on and provides a 10 second delay for OS selection.
```
GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=menu
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
#GRUB_DISTRIBUTOR="Ubuntu 20.04"
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
```

---

### Post by madhu on 2021-04-09
> **oldfred said:**
> I did not see this in your Boot-Repair summary report.
Post this in code tags.

cat /etc/default/grub

cat /etc/default/grub displays the following:

```
superadmin@superadmin-Inspiron-7537:~$ cat /etc/default/grub
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT="menuentry 'Windows Boot Manager (on /dev/sda2)' --class windows --class os  'osprober-efi-5E75-94AD' {"
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
superadmin@superadmin-Inspiron-7537:~$ 


```

Thank you!

---

### Post by oldfred on 2021-04-09
Change this as also shown in tea for one's version:
GRUB_TIMEOUT_STYLE=hidden
to this:
GRUB_TIMEOUT_STYLE=menu

sudo nano -B /etc/default/grub
Control x and save when exiting.

---

### Post by tea for one on 2021-04-09
After editing the grub file, do not forget to run:-
```
sudo update-grub
```

---

### Post by madhu on 2021-04-09
I have changed and saved
```
GRUB_TIMEOUT_STYLE=menu
```

and then ran 
```
sudo update-grub
```

unfortunately, still the menu is not displayed.

---

### Post by oldfred on 2021-04-09
I do not know if it is going to show anything or not, but run a new copy of the report from Boot-Repair and post link.
Do not run any suggested autofixes.

---

### Post by madhu on 2021-04-09
The new Boot-Repair report summary is in the following link

[https://paste.ubuntu.com/p/J7RWc3Cyg2/](https://paste.ubuntu.com/p/J7RWc3Cyg2/)

---

### Post by tea for one on 2021-04-09
```
GRUB_DEFAULT="menuentry 'Windows Boot Manager (on /dev/sda2)' --class windows --class os  'osprober-efi-5E75-94AD' {"
```
 As an experiment, I would also change this line as follows:-
```
GRUB_DEFAULT=0
```
Followed by 
```
sudo-update-grub
```
Worth a shot..............?

Posted before your new boot-repair report

---

### Post by oldfred on 2021-04-09
[https://help.ubuntu.com/community/Grub2/Setup#Specific_Entries](https://help.ubuntu.com/community/Grub2/Setup#Specific_Entries)

I think your description entry has too much. It should be just what os-prober would have grub menu show.
Probably just 
'Windows Boot Manager (on /dev/sda2)'

---

### Post by madhu on 2021-04-10
Thank you so much for taking quiet a lot of effort in helping me! I really appreciate it!! 

When I tried
```
GRUB_DEFAULT=0
```
it was still going into Ubuntu directly

When I tried
```
GRUB_DEFAULT="Windows Boot Manager (on /dev/sda2)"
```
it was booting Windows directly without giving any option. 

Interestingly, I found that irrespective of GRUB_DEFAULT, the grub menu is displayed when I press F12 and then select 'Ubuntu' while booting.

I have a made a video recording of this to help understand it better. You can find it here
[https://youtu.be/5OS7qdgxdHI]("https://youtu.be/5OS7qdgxdHI")

PS: 
[LIST=1]
[*]I never saw the Grub menu from the time I installed Ubuntu as dual boot. The machine always used to boot into Windows by default (until I tried Boot Repair). If I wanted to go into Ubuntu, I used to press F12 while booting and then choose 'Hard Drive' under the *Legacy Boot* section (as if my Windows were present outside of my hard drive). 
[*]
[*]My system time in Windows always resets (probably to GMT/UT) every time I go into Ubuntu and then I go back into Windows.
[/LIST]
 
*Probably* the Grub menu getting displayed after selecting Ubuntu, having to select 'Hard Drive' in boot options menu to go into Ubuntu, the time getting resetting in Windows every time I boot into Ubuntu are all connected.

---

### Post by CelticWarrior on 2021-04-10
F12 is not the Grub menu, it's the one-time UEFI boot menu. That you CAN boot Ubuntu (Grub) from it means that everything is fine except you still have Windows as the boot default in UEFI Settings > Boot. Please check and change accordingly. It shouldn't take 3 forum pages for something so trivial.

---

### Post by oldfred on 2021-04-10
If you look at boot repair report it has a Windows BCD setting.
Some systems sync BCD with UEFI, so whatever is in BCD will be UEFI. That may be why booting Windows resets boot order.

There are many threads on the time issue and how to resolve it. I do not have that issue and do not know details.

---

### Post by madhu on 2021-04-11
Thank you so much **oldfred** and **tea for one** for all the guidance!!

---

