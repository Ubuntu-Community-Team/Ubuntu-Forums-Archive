---
title: "Broken Grub menu after Windows update"
date: 2016-10-02
forum: New to Ubuntu
---

### Post by dshinks on 2016-10-02
Hi all,

I'm pretty new to this so any help would be appreciated.

I've been running Ubuntu 16.04 lts on a second partition of my Windows 10 laptop for a few months now. I've just had an automatic Windows update that seems to have killed off my Grub menu; instead of prompting me to select Linux or windows, I'm being booted direct into Windows again.

If I boot from a USB key, I can still see my Linux partition and all my files.

I've disabled secure boot and run boot-repair, but no joy.

Boot repair logs are at [http://paste2.org/dFktcAX9](http://paste2.org/dFktcAX9)

Any suggestions on what I should look for next?

Thanks

---

### Post by oldfred on 2016-10-02
First make a windows repair/recovery flash drive.
       Windows 10 repair disk
[http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html](http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html)
[http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html](http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html)
Repair/backup/restore
[https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive](https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive)
[http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options](http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options)

Turn off Windows fast start up or always on hibernation. Windows on updates may turn this back on, and to dual boot it must be off.

 Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html) 
    
You have an HP. And HP has not been dual boot friendly. 
What changes did you do to boot Ubuntu before?   
 Many HP users copy shimx64.efi to /EFI/Boot and rename shimx64.efi to bootx64.efi. That is a fallback or hard drive boot entry. HP normally has an entry to boot hard drive which then works.
Boot-Repair and some older instructions had users copy shim over the Windows .efi boot file, but then Windows updates overwrite the shim/grub entry and you cannot boot. Better to use fallback entry. Some HP have a custom setting buried somewhere that will let you set ubuntu as a valid entry.

       HP Check if Customized UEFI settings available like this  HP ProBook 4340
[https://ubuntuforums.org/showthread.php?t=2332681&p=13527216#post13527216](https://ubuntuforums.org/showthread.php?t=2332681&p=13527216#post13527216)
[http://askubuntu.com/questions/244261/how-do-i-get-my-hp-laptop-to-boot-into-grub-from-my-new-efi-file](http://askubuntu.com/questions/244261/how-do-i-get-my-hp-laptop-to-boot-into-grub-from-my-new-efi-file)

Running Boot-Repair can copy shim to bootx64.efi, if you use advanced options. Older threads have users manually copy shim.
       
Boot-Repair now creates  bkpbootx64.efi and copies shimx64.efi as bootx64.efi. This is a hard drive default or fallback boot entry in UEFI.
'Use the standard EFI file' in advanced options.
[https://bugs.launchpad.net/boot-repair/+bug/1531178](https://bugs.launchpad.net/boot-repair/+bug/1531178) 
      
You show a hard drive entry, but I am not sure if UEFI or BIOS. Or if HP will auto find the new bootx64.efi and add an UEFI boot entry. If not we can add one.

 HP Probook 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)
HP Manually renamed files to make it work.
[http://ubuntuforums.org/showthread.php?t=2131886](http://ubuntuforums.org/showthread.php?t=2131886) 


You may also want to houseclean old kernels. With 16.04 it now only keeps 2, but all older versions require users to houseclean.
      
 Better to use Synaptic to select the ones you no longer want. Also you get notified about dependencies to be removed and can reconsider, if need be.
[http://lifehacker.com/5817282/what-kind-of-maintenance-do-i-need-to-do-on-my-linux-pc](http://lifehacker.com/5817282/what-kind-of-maintenance-do-i-need-to-do-on-my-linux-pc) 
           
 Determine your current kernel:
uname -a 

 sudo apt-get install synaptic
In synaptic search for linux-image to choose to delete old ones
Using synaptic
[http://ubuntuforums.org/showthread.php?t=1283521](http://ubuntuforums.org/showthread.php?t=1283521)

---

### Post by dshinks on 2016-10-03
Thanks very much for responding @oldfred,

I've worked through a few of those now (I think) but still not much luck sadly.

Managed to turn off fast-startup so Windows actually stops instead of hibernating.

Re changes before when I first installed; I don't recall doing anything special tbh; I just ran the installer from a live usb and followed the steps for installing a new ubuntu instance alongside Windows.

I've had a poke around inside /dev/sda2/efi/boot and it looks like there's a backup of bootx64.efi in there (bkpbootx64.efi); I guess boot-repair has done this and then updated bootx64.efi. I've also tried copying shimx64.efi over this (taking another backup of it first). So, the contents of this folder are now:
- bkp2bootx64.efi (my backup)
- bkpbootx64.efi (existing backup)
- bootx64.efi (the copy of shimx64.efi that I've added)
Still booting into windows though!

Interstingly, I've come across a temporary workaround whereby I can use my live usb key to sort of jump-start a boot into my installed linux environment: If I start my machine with the key plugged in, instead of selecting an option from the key's boot menu, if I press [esc] I get taken to a grub command prompt. If I then exit that shell, I get taken to another boot manager where I can select from Windows and two ubuntu instances. Selecting the first one takes me into my installed instance.

I'm going to keep working through your instructions, but could you clarify what you meant on this line?:
[INDENT]"You show a hard drive entry, but I am not sure if UEFI or BIOS. Or if HP  will auto find the new bootx64.efi and add an UEFI boot entry. If not  we can add one."
[/INDENT]

Thanks again

---

### Post by oldfred on 2016-10-03
Check entry is there.
sudo efibootmgr -v  

If not you can create one:
      
 This should create a new entry, if ESP is sda1, uses defaults:
sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\Microsoft\Boot\bootmgfw.efi"
if ESP sda2 or sda3, you have to specify drive & partition, example for sda2
sudo efibootmgr -c -d /dev/sda -p 2 -L "Windows Boot Manager" -l "\EFI\Microsoft\Boot\bootmgfw.efi" 

see this for more explanation. 
man efibootmgr 
      
 Then check again if entry is there and first in boot order. Even HP usually allows that entry.
sudo efibootmgr -v

---

### Post by dshinks on 2016-10-04
Thanks again @oldfred;

Looks like I'm almost sorted but not quite.

I've run
sudo efibootmgr -v 

and got this:

BootCurrent: 0000
Timeout: 2 seconds
BootOrder: 2001,0001,3001,0000,0002,2002,2003
Boot0000* ubuntu    HD(2,GPT,dc64baca-df1b-4e45-af37-721c4c0642f7,0xc8800,0x82000)/File(\EFI\ubuntu\shimx64.efi)
Boot0001* Windows Boot Manager    HD(2,GPT,dc64baca-df1b-4e45-af37-721c4c0642f7,0xc8800,0x82000)/File(\EFI\Microsoft\Boot\bootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}.../................
Boot0002* Ubuntu    HD(2,GPT,dc64baca-df1b-4e45-af37-721c4c0642f7,0xc8800,0x82000)/File(\EFI\ubuntu\grubx64.efi)RC
Boot0003* USB Hard Drive (UEFI) - SanDisk    PciRoot(0x0)/Pci(0x14,0x0)/USB(4,0)/HD(1,MBR,0x4294967268,0x800,0x1ca3592)RC
Boot2001* USB Drive (UEFI)    RC
Boot2002* Internal CD/DVD ROM Drive (UEFI)    RC
Boot3001* Internal Hard Disk or Solid State Disk    RC

FYI, this record was taken while I was logged into my installed instance (via that method I found of jump-starting from a live-usb copy of grub).

I managed to get it to boot direct into Ubuntu by setting Boot0000 as the next boot:
sudo efibootmgr -n 0

That worked fine, so I tried changing the boot order permanently using:
sudo efibootmgr -o 0,1,2001,3001,0002,2002

It looked that that was going to work (terminal responded with the revised boot order), but when I restarted my computer, it booted back into Windows! (after an initial error message from Windows to say that it failed to boot!)

Thanks for sticking with this one so far! :)

---

### Post by oldfred on 2016-10-04
Windows sometimes on updates will reset system to make Windows first. It assumes users only want Windows and of course it must correct system.
So just be prepared with live installer to occasionally have to update it.

---

### Post by dshinks on 2016-10-05
Thanks Oldfred, I'll definitely remember how to use boot-repair repair and efibootmgr for next time Windows decides to mess with me :)

Is there anything I can do to set my boot order properly now though? As I say efibootmgr works fine when using -n (next boot only) but doesn't work on -o (change boot order) it looks like the boot order gets set right, but it boots into Windows anyway.

In fact, the next time I log into Ubuntu, it shows that the boot order gets set back to the original (windows first).

Feel like we're close to cracking it but not quite yet.

Thanks

---

### Post by oldfred on 2016-10-05
You can just use UEFI one time boot key. Some just do that.

There are work arounds, most systems boot a fallback or hard drive entry even for internal drives.
See post #2.

I have a list of many work arounds, but if dual booting, most use the fallback entry. See link below in my signature. Boot-Repair's "use standard file" copies shimx64.efi to bootx64.efi as fallback. But you may have to cold boot, full power down, remove battery, and hold power switch to drain last bit of power. It should find entry.
But you can add entry with efibootmgr. Also in link in my signature.

 HP Check if Customized UEFI settings available like this  HP ProBook 4340
[https://ubuntuforums.org/showthread.php?t=2332681&p=13527216#post13527216](https://ubuntuforums.org/showthread.php?t=2332681&p=13527216#post13527216)
[http://askubuntu.com/questions/244261/how-do-i-get-my-hp-laptop-to-boot-into-grub-from-my-new-efi-file](http://askubuntu.com/questions/244261/how-do-i-get-my-hp-laptop-to-boot-into-grub-from-my-new-efi-file)

---

### Post by dshinks on 2016-10-06
Thanks again for your help on this @OldFred.

I've now managed to get myself back up and running, and managed to learn a little about UEFI and boot managers along the way! :) (oh, and how fussy Windows can truly be!)

My machine continues to insist I use the Windows Boot Manager, but as boot-repair (and probably you too) suggested, I changed the default boot entry of the Windows bootloader.

As it states in the dialog from boot-repair, I did this by:
* booting into Windows
* opening an administrator command prompt
* entering the following command string

bcedit /set {bootmgr} path \EFI\ubuntu\shimx64.efi

thanks again for your help on this!

---

