---
title: "Troubbleshouter for EFI invalid path"
date: 2012-11-06
forum: New to Ubuntu
---

### Post by Poutrathor on 2012-11-06
Hi 

I tried and successfully  installed an Ubuntu LTS alongside a W7 on my new Asus N76VZ. BUT the grub bootloader does not work for W7 (both options normal one and recovery one) Invalid EFI path (or smthg) 

So I ended up here with my Boot repair unsuccessful and I paste you all my boot repair info (after reparations). The ubunut is running great (i am currently writing from it by WiFi).

[http://paste.ubuntu.com/1337420/]("http://paste.ubuntu.com/1337156/")

Someone can help me/pinpoints the issue ? 

Thanks a lot!



Bonjour,

J'ai essayé de me renseigner et de pas rater mon installation d'Ubuntu LTS en parallèle d'un W7 sur mon nouvel Asus N76VZ (comme sur mon ancien laptop), particulièrement quand il s'agissait du device sur le quel mettre le bootloader. Raté -_-

Linux roule parfaitement, avec Wifi et tout.
W7 n'est pas perdu, seulement: Invalid EFI path.

Donc Boot repair. J'espérais que cela résoudrait mon problème puisqu'il avait l'air similaire à celui de premiers posters mais non. 

Voici mon boot-repair info: [http://paste.ubuntu.com/1337420/](http://paste.ubuntu.com/1337420/)

Est-ce que quelqu'un peut m'indiquer mon erreur/la marche à suivre?

Un grand merci.

Notez l'ironie du 1337 dans l'adresse du rapport du noob :) [URL="http://paste.ubuntu.com/1337156/"]
[/URL]
old report: [URL="http://paste.ubuntu.com/1337156/"]http://paste.ubuntu.com/1337156/
[/URL]

---

### Post by Poutrathor on 2012-11-06
Hi all,

I am stuck with an error to boot W7 from grub after Ubuntu LTS successfully installed and running (usb live wubi) 

I am trying to understand something about all that firmware layers but it is DIFFICULT :(

Currently i am with boot repair failing and a boot-repair report: [http://paste.ubuntu.com/1337420/]("http://paste.ubuntu.com/1337156/")

Please tell me there is somewhere someone who had done a troubleshooting to this issue. Up to now i have only find threads of individual problems and experienced people helping (thx to them all) but I have not enough experience to understand the initial problem and the proposed solutions.

A step-by-step troubleshooter for EFI issues?

Thanks & i ll keep udpate if I find something

++

---

### Post by oldfred on 2012-11-06
Your sdb drive is MBR, so you installed Ubuntu as BIOS/MBR on sdb. But grub2's os-prober added the standard BIOS chain boot entries. But with efi the boot entries are different. 
Boot repair has a function to convert a BIOS install to efi and add correct chain entries, but it will not convert sdb to gpt partitioning which is really required for efi. (Ubuntu may work but it is not correct). And you do not have the efi partition as the first partition with the gpt efi code.

Best to repartion with gpt partitioning and reinstall on sdb.
You have to use 64 bit version, and boot flash drive or CD in UEFI mode from UEFI menu. Then it will install correctly to efi mode. You still need to use manual install and choose sdb for partitions, but install grub to sdb and sda's efi partition. I think you will still need Boot-Repair to add correct chain boot entries.

---

### Post by Poutrathor on 2012-11-06
Hi, thanks a lot to give more time on this subject.

I was reading just now another thread where you appeared :) [http://ubuntuforums.org/showthread.php?t=2055176](http://ubuntuforums.org/showthread.php?t=2055176)

I will try to understand your first paragraph and reinstall:

*Your sdb drive is MBR, *My second hard-drive is the Master Boot Register. Who decide that? Me, when I did the action below?
*so you installed Ubuntu as BIOS/MBR on sdb*. Actually, I selected "device to install boot loader on" as the one partition of this hd that I had created for Linux.
*But  grub2's os-prober added the standard BIOS chain boot entries.* :confused: 
*But with  efi the boot entries are different. *I understand EFI as the new name for the BIOS (wikipedia)? GRub 2 is brand new (june 2012): it is not adjusted to EFI yet or I failed smth?
*Boot repair has a function to convert a BIOS install to efi and add  correct chain entries, but it will not convert sdb to gpt partitioning  which is really required for efi. (Ubuntu may work but it is not  correct). *OK. So now my Ubuntu is bypassing the EFI ? 
*And you do not have the efi partition as the first partition  with the gpt efi code.* c'est du chinois.


About what I should do:
*Best to repartion with gpt partitioning and reinstall on sdb.* I ll find a way by Google.
*You have to use 64 bit version, and boot flash drive or CD in UEFI mode  from UEFI menu. *UEFI menu is what I call BIOS menu I suppose.
*Then it will install correctly to efi mode. You still  need to use manual install and choose sdb for partitions, but install  grub to sdb and sda's efi partition.* 
This is the only point I don t get at all (all the others i should understand after some searching). HOW can I install grub on both sda and sdb? and what s the point? What is a Hard-drive's efi partition?

*I think you will still need  Boot-Repair to add correct chain boot entries.* If you say so, I believe :)

Thanks a lot for trying to help me. I am gonna try to find my way and i ll update as soon as I got something.

PS: If I succeed it would be interested in (someone &/or me) writing a short introduction to this issue that seems to have be common the last months and that beginners meet. 

PPS: It seems related a lot to asus laptop or just because I was searching for mine?

Sry for bad English, not a native speaker.

---

### Post by oldfred on 2012-11-06
Your English is fine. A whole lot better than my High School French from 50 years ago that I have not really used since. But Yann may be better to help.

Yes UEFI is the new "upgraded" BIOS. But most will work in the old BIOS mode or in the new UEFI mode. BIOS boots from the MBR or first sector on a hard drive. UEFI has more boot code and can read the efi partition to find boot files. 

MBR partitioning goes back to the first hard drives on PC's in the 1980's and cannot be used for drives over 2TB. The new gpt is for large drives, recommended for SSDs and required for UEFI booting. Windows only boots from gpt partitioned drives if UEFI booting.

If you chose to boot the Ubuntu installer in BIOS/AHCI/legacy mode or used 32 bit version you will automatically get MBR partitioning and a BIOS boot type install. If booted with UEFI/efi mode (only with 64 bit version) then you get gpt partitioning, the extra efi boot partition and a UEFI type install. 

Examples that worked.

UEFI dual boot two drives
[http://ubuntuforums.org/showthread.php?t=2072950](http://ubuntuforums.org/showthread.php?t=2072950)
[http://ubuntuforums.org/showthread.php?t=2031836](http://ubuntuforums.org/showthread.php?t=2031836)

Lots of detail:
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)

I have not installed UEFI but often the grub install offers the use of spacebar to choose and if you click/spacebar on more than one place it will install to several. If not available just install to the sdb or Ubuntu drive, set UEFI to boot from that.

---

### Post by oldfred on 2012-11-06
@Poutrathor

Moved your posts form Yann's mega thread on Boot-Repair, so you do have have duplicate answers in different threads.

---

### Post by Poutrathor on 2012-11-06
Hi,

Sorry for the delay, had to buy groceries. 

1)  I have "clean" my second hd (called sdb) under windows (i was not sure about converting it with gdisk under ubuntu since the same ubuntu was on the drive)

2) I have reinstalled ubuntu LTS (12.04.1) on sdb. I installed with a pendrive (same as before) running Wubi, I don't know if it matters. 

3) Boot W7 same error

4) Boot-repair without advanced option

5) Boot W7 same error: invalid efi paths etc etc.

So I am gonna start reading your links I just saw them. 

I start to understand little more than the beginning but still I don't get why it is so hard to get dual boot working (I mean: it seems to be just saying the UEFI where to search first and to have written at this the index of the booting register for both (or more) system, right?). 

Anyway thank you for the help and I keep updating! 

++

EDIT: W7 is working perfectly if I press the Ecape key at power up and I select the right booting option. It's just so frustrating

---

### Post by Poutrathor on 2012-11-06
Hello, back to update some

I add the boot-repair info: [http://paste.ubuntu.com/1338006/](http://paste.ubuntu.com/1338006/)

For as long as I understand I have failed the partitioning of an (U)EFI sdb1 because even if I said it was EFI boot in the installer, it does not have the FAT32 as the sda1 has. Correct?

But did I have install Ubuntu over the EFI mode when I select "EFI SanDIsk" over simply-named"SanDisk" (where SanDIsk is the name of my USB drive containing Wubi installer)?

I keep reading, I will surely have to rest soon :mad:

++

---

### Post by oldfred on 2012-11-06
Install looks a lot better. It looks like Ubuntu installed grub2 efi loader to sda1's efi partition not sdb1's efi. But that should be ok. 

From UEFI/BIOS does it offer two choices to boot, one Windows & the other ubuntu? It should.

But from Ubuntu's menu you still have the old BIOS type chain entries to boot. Boot-Repair should fix it.

Also see dual drive UEFI links in previous threads for for detail.

---

### Post by Poutrathor on 2012-11-06
These are the possibility offered by the BIOS/UEFI menu:

Window Boot Manager (P0: Hitachi HTSXXXX)    (1)
Ubuntu (P1: Hitachi HTS XXXXXXXX)                       (2)
idem except P1 replace by P0                                   (3)
idem except P0 replace by P1                                   (4)
P2 MATSHITABD-CMD UJ160                                    (5)  probably my second disk 
Enter Setup

(2) = (3) and the three ubuntu have the same HD. Doubt for the Windows one, it should be different will edit next time I go back there.

The order of priority for booting is the same as above except that window come in second position.

Boot-repair does not repair with normal options. I want to try it following the second example of dual boot, the one where the OP wrote a step-by-step process after he succeed.

For the EFI install in the sda1, I am wondering: I am sure to have selected sdb as the device for the bootloader but as mentionned in my previous post I feel like my partition sdb1 which I had planned to be a EFI booting one has failed since it is not similar as the one for Windows; the ubuntu booting files might be the ones installed by my first installation of ubuntu. 

I keep reading/trying, Thank you for your support, I feel less alone -_- 

BTW I love Chicago (went twice) 
have you vote yet?

EDIT: Ok so all bootloader on one disk and all working, that confirms your analysis (not a surprise). back tomorrow

---

### Post by Poutrathor on 2012-11-06
These are the possibility offered by the BIOS/UEFI menu:

Window Boot Manager (P0: Hitachi HTSXXXX)    (1)
Ubuntu (P1: Hitachi HTS XXXXXXXX)                       (2)
idem except P1 replace by P0                                   (3)
idem except P0 replace by P1                                   (4)
P2 MATSHITABD-CMD UJ160                                    (5)  my second drive I believe
Enter Setup

(2) = (3) and the three ubuntu have the same HD. Doubt for the Windows one, it should be different will edit next time I go back there.

The order of priority for booting is the same as above except that window come in second position.

Boot-repair does not repair with normal options. I want to try it following the second example of dual boot, the one where the OP wrote a step-by-step process after he succeed.

For the EFI install in the sda1, I am wondering: I am sure to have selected sdb as the device for the bootloader but as mentionned in my previous post I feel like my partition sdb1 which I had planned to be a EFI booting one has failed since it is not similar as the one for Windows; the ubuntu booting files might be the ones installed by my first installation of ubuntu. 

I keep reading/trying, Thank you for your support, I feel less alone -_- 

BTW I love Chicago (went twice) 
have you vote yet?

---

### Post by oldfred on 2012-11-06
Have you tried booting with each of the entries?

My wife & went to vote this morning, no lines except if wanting to use the video mode. Then out for breakfast which do only do occasionally.  

Standard process is paper with fill-in circles and scanner to read. One advantage of paper is the paper trail & when scanned it will tell you some basic errors like two entries or missing entry and let you fix or accept as is (vote for that candidate will not count).
I go back to the days of arguing over whether the X on a paper ballot was inside the box as required. If outside some argued intention, but rules were inside only. But then they argued over X on the lines of the box. Someone is always unhappy with the results and wants to make waves.

---

### Post by Poutrathor on 2012-11-07
YES!

After a nice sleep, I did it! As far as I see, it is working fine. 

Thank you Oldfred for your kind support and advice, I would have not succeed alone!

The all powerful thread, solution for dual boot on double disk:
[http://ubuntuforums.org/showthread.php?t=2031836](http://ubuntuforums.org/showthread.php?t=2031836)

It is indeed the indexation of the W7 bootloader that is not correct and need to be added as described above. All that I still could do is to remove the wrong entries in the grub2 menu for aesthetics.

still don't believe it! I learn a lot again, thx! 

Voting is kinda complex in the USA ^^ and very often waves about cheating. In France we are still paper election so we do not really know if there are frauds :D 

See you!

---

### Post by YannBuntu on 2012-11-07
Good job :)

Logs indicate you have only used the "Create BootInfo" button of Boot-Repair. Did you try the "Recommended Repair" button? if yes, please could you indicate the URL that appeared?

EDIT: i think this was a bug introduced in the boot-repair3.194~ppa50 package. I fixed it today.

---

### Post by oldfred on 2012-11-07
Glad it worked. 

Yann's Boot-Repair fixes two standard issues with UEFI installs. 

One is where users install in BIOS mode. Boot-Repair will un-install grub-pc and install grub-efi and update fstab so it is correct UEFI install. 

The other is the bug in grub2's os-prober that puts in a BIOS/MBR chain load entry to Windows. Boot-Repair will automatically add the correct chain entries back to the efi Windows boot loader.

If you do not want the os-prober you can turn it off so you do not get the old wrong entries, or back on later if you add more systems and want another update. 

In /etc/default/grub I added this, change back to false if you want to run it again:

gksudo gedit /etc/default/grub

GRUB_DISABLE_OS_PROBER=true

or turn off executeable bit
sudo chmod a-x /etc/grub.d/30_os-prober

Then run
sudo update-grub

---

