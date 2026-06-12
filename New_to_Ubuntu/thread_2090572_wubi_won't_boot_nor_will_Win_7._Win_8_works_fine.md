---
title: "wubi won't boot nor will Win 7. Win 8 works fine"
date: 2012-12-02
forum: New to Ubuntu
---

### Post by RJayB on 2012-12-02
I have an HPE h8-1360t with dual boot windows 8 and windows 7. I just now downloaded and installed wubi. Now when I try to boot ubuntu for the first time I get "Windows failed to start. A recent hardware or software change might be the cause. To fix the problem:
1. Insert your windows installation disc and restart your computer.
2. Choose your language settings and click next.
3. Click "Repair your computer."

If you do not have this disc, contact your system administrator or computer manufacturer for assistance.

File: \ubuntu\winboot\wubildr.mbr

Status: 0xc000007b

Info: The applicationor operating system couldn't be loaded because a required file is missing or contains errors.
----------------------------------------------------------------

Then the computer shuts down.
Windows 7 won't start either, it just sits on the "Windows Starting" screen but does nothing.
Windows 8 boots and runs perfectly. I do not have a Windows 7 installation disc, it came preloaded so I only have the recovery partition (D drive). I have repair and recovery discs for both windows operating systems and both are fully backed up by Seagate GoFlex
I have tried to restart several times. Is there any other way besides getting a windows installation disc from MS or HP.
Help!

---

### Post by Jmackxxx on 2012-12-02
You need to reinstall Grub in the MBR.  Here is a link to do this .. [http://howtoubuntu.org/how-to-repairrestorereinstall-grub-2-with-a-ubuntu-live-cd/...  ]("http://howtoubuntu.org/how-to-repairrestorereinstall-grub-2-with-a-ubuntu-live-cd/")

Hope that works


I also recommend Testing on a VM.

---

### Post by mansonfan78 on 2012-12-02
If you have a recovery disk for Win7 you should be able to load it and at the prompt type "fixboot" without the quotes.  You will most likely lose your boot menu that lets you select ubuntu and will have to reinstall with wubi (although I recommend doing a normal install of ubuntu to a different partition).

---

### Post by oldfred on 2012-12-02
If not UEFI, Windows only directly boots from one partition or the "active" partition in Windows or the boot flag that we see in Linux.
      

Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
    
If both Windows are in primary partitions you can use grub to boot both if you repair the second install to also have its boot files. Only the first install in the boot partition has boot files and an updated BCD to boot both systems.

But wubi may be in the other install. If you do not have a full install of Ubuntu you cannot use grub as wubi only boots thru the Windows boot loader. 

I know wubi does not work on Windows 8 installs in gpt partitions, but am not sure about MBR partitions.

---

### Post by lisati on 2012-12-02
*cough*

It *could* be a problem with grub, but I recall seeing wubi mentioned....

(Sorry, beyond that observation, nothing useful to add at present.)

---

