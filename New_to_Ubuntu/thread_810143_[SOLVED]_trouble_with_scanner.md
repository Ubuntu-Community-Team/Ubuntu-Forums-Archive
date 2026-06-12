---
title: "[SOLVED] trouble with scanner"
date: 2008-05-28
forum: New to Ubuntu
---

### Post by fr.theo on 2008-05-28
I have a HP Scanjet 4p, and Ubuntu 8.04 recognizes the device, however, Sane cannot find the scanner. 

I have checked the with "cat scsi" and the scanner is listed 

theodore@theodore-desktop:/proc/scsi$ cat scsi
Attached devices:
Host: scsi0 Channel: 00 Id: 01 Lun: 00
  Vendor: HP       Model: C1130A           Rev: 3540
  Type:   Processor                        ANSI  SCSI revision: 02

also I have used the command lsscsi and it finds the device however their is no assigned "dev/" to it.   

[0:0:1:0]    process HP       C1130A           3540  -       
[1:0:0:0]    cd/dvd  LITE-ON  DVD SHD-16P1S    GS02  /dev/scd1

any help would be appreciated.

---

### Post by Mark_in_Hollywood on 2008-05-29
Reading at the SANE webpages, I see that the 4p is supported:

[http://www.sane-project.org/man/sane-hp.5.html](http://www.sane-project.org/man/sane-hp.5.html)

try:

sudo aptitude install sane

and post the results. Let's begin there and see if that's enough.

IF that gets your scanner working, please find the Thread Tools link at the top of this thread, open it and mark the thread as SOLVED.

---

### Post by fr.theo on 2008-05-30
Mark I would firstly like to thank you for taking time to assist me, I had a look at the site which you mentioned and followed your instructions. however, I ran sane once again, after I executed the command you advised 

"sudo aptitude install sane" (it completed successfully)  

and once again the scanner was not found. 

I also ran the "lsscsi" and the same result apeared 

"[0:0:1:0]    process HP       C1130A           3540  - " 

I noticed on the site which you mentioned that the scanner should have a "dev/scanner" port assigned or linux will presume that your scanner is a usb and not scsi. I also had a look at the "hp.conf" under sane.d directory on my computer and found no listing of my scanner and that "dev/scanner" was the default assignment. 

I tried to follow the instructions on the site but found it a bit daunting as I am still new to linux. I thought may be if you knew my configuration of my computer or at least the scsi card I am using this may help.

Scsi card model :Adaptec, ava-2904 (99) 1814000a (as it appears on the card) 

Scsi Card Chip lable: AIC- 7856T (as it appears on the chip that is mounted on the card)

if you want my computers configuration let me know.

once again thank you.

Theo.

---

### Post by fr.theo on 2008-05-30
Mark, I have fixed the problem using the following, I am not sure if what you suggested triggered it or the steps I tried after that caused it to work.

but thank you very much for your help, it certainly pushed me in the right direction.

I went to the "sane" site, from there I searched for the problem I had [http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=5076094](http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=5076094) and the following helped:

#   My Linux kernel recognizes my SCSI scanner but SANE does not
Usually the hp-backend is configured to find the SCSI scanner automatically or at least at /dev/scanner. This requires that /dev/scanner is a link to the device where the scanner is really located. Run the tool sane-find-scanner from SANEs tools-directory (in old versions of SANE it is called find-scanner). This will print a list of device names where the scanner is found. If for example /dev/sg0 is in that list, become root, create a link and set permissions with the commands


ln -s /dev/sg0 /dev/scanner
chmod 666 /dev/sg0

You also can try to force scanimage to use the correct device:

scanimage -d hp:/dev/sg0 > scan.ppm

(MY SCANNER WAS LOCATED ON SG6) so I simply changed the "/dev/sg0" to "sg6)

Ps. I tried scanimage -L first and it found my scanner then I proceeded with the online help from Sane (the above commands). I also rebooted after I sent my last message to you, this might be usefully information to any one with similar problems (I know that sounds stupid and amateurish but it could of contributed). 

once again thank you.

Theodore.

---

### Post by Mark_in_Hollywood on 2008-05-30
Please find the Thread Tools link near the beginning of your thread and pull down the menu, select "Mark as Solved"

Thanks.

---

