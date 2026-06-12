---
title: "Ubuntu on &quot;probably&quot; broken HD"
date: 2015-02-22
forum: New to Ubuntu
---

### Post by pawe6 on 2015-02-22
Hello!

I'm new a user. I frankly hope I post this thread in the proper section.

Recently my windows 7 laptop has stopped booting. I  checked the hard drive through a tool from DOS and it appeared, that  "Short DST" test of my hard drive has "FAILED". I though that my HD got problably broken, so I realised I needed to back-up all the things I had there. I  decided to use Ubuntu from CD for that puropouse. But I liked the  system so much that I wanted to have it on my laptop.
I was thinking  if I should install it on USB, but then again after having no troubles  with backing-up all the files I decided to try and install it on  one of the partitions of my HD. Well I choose option with formating the  HD and Ubuntu installed with no problem.

I launched so installed  Ubuntu and I'm running it right now. Everyting seems to work properly, though when I do the test in DOS it still shows that Short DST has failed.
So my question is - is it possible it will continue to work and won't crash with the HD in this condition? And is it possible to check it, or repair? Ubuntu has left my HD in the whole with no partitions.

Thanks in advance :)

---

### Post by Bashing-om on 2015-02-22
pawe6; Hi ! Welcome to the forum .

Did you install (u)buntu ? If so there is the tool "disks" installed by default. in the dash type "disks" to activate the tool.
In disks select "run SMART test" .. See what the test results are.
One can do a more in depth check from terminal with terminal command:
```

sudo smartctl -a -d ata /dev/sda

```
where 'sda' is the 1st hard drive - assuming that is the drive you want to check in this instance.

[INDENT][INDENT]maybe yes
[INDENT][INDENT][INDENT]maybe not so yes
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by grahammechanical on 2015-02-22
Ubuntu has a utility called Disks and if the hard disk has SMART the disk utility will run the SMART test for you. Look for an icon of three horizontal lines one on top of the other. Have you searched the internet for what "Short DST" means? I have. Short Drive Self Test.

From various web sites the opinion is that the drive is failing, or the file system is corrupt or even that a Windows anti-virus utility is causing the failure.

[http://h30434.www3.hp.com/t5/Notebook-Lockups-Freezes-Hangs/Short-DST-Failed/td-p/997555](http://h30434.www3.hp.com/t5/Notebook-Lockups-Freezes-Hangs/Short-DST-Failed/td-p/997555)

[http://answers.microsoft.com/en-us/windows/forum/windows_xp-system/how-to-fix-dst-short-test-on-a-laptop/61165d2c-775d-41aa-8d94-1f2a1f3a13fd](http://answers.microsoft.com/en-us/windows/forum/windows_xp-system/how-to-fix-dst-short-test-on-a-laptop/61165d2c-775d-41aa-8d94-1f2a1f3a13fd)

[http://www.ehow.com/info_12133492_laptop-dst-short-test.html](http://www.ehow.com/info_12133492_laptop-dst-short-test.html)

When we install Ubuntu using the Erase disk and install Ubuntu option the installer creates 2 partitions. One for Ubuntu and one for Swap.

Regards.

---

### Post by pawe6 on 2015-02-22
Thank you for the quick answer ! :)

I run the SMART test from the "disks" tool and... it said with red colour that the "SELF-TEST FAILED".

Self-test Result: smart-self-test-resultLast self-test failed (read)
Overall Assessment: SELF-TEST FAILED
I can paste screenshot if it's needed.

Anyway, can I do anything about it?
I can't use Windows Recover Console, because I have no Windows installed - or maybe I do something wrong? I tried with win7 ultimate cd. Maybe I should try install Windows only to run Repair Console (though that sound ridiculous to me... Maybe the error was cause by a windows program, but shouldn't the problem gone with the wipe that Ubuntu did?). Or is there a way to try and repair the disc without this Windows tool? (if it's possible)?

[SIZE=1](And yes, indeed, I realised Ubuntu has actually created the partitions. Sorry for the mislead :( )[/SIZE]

---

### Post by Bashing-om on 2015-02-22
pawe6; Does not bode well for the home team !

However;
Post back the results:
```

sudo smartctl -a -d ata /dev/sda

```
to see where the fault is.

[INDENT][INDENT]nothing lasts forever
[INDENT][INDENT][INDENT]I do hate it when this happens ( backs ups !) 
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by pawe6 on 2015-02-22
That is a bit unexpected...


[IMG]https://lh3.googleusercontent.com/5tIut5blrUQf8ZcMhlTpYck-BaBt8k_EYo62Bi0Ow-3SqlD-IiLMo1ZG21A7nt8X_UL4gW__cJM=w1275-h518[/IMG]


What do I do now? The password is correct, and the destination is the same as it said in the "disks" tool (/dev/sda).

---

### Post by Bashing-om on 2015-02-22
pawe6; Hey !

Your 'image' gives a 403 "forbidden" ..
Maybe try a simpler command to see the SMART data ?
```

sudo smartctl -a /dev/sda

```
where 'sda' is to be that hard drive in question, adjust otherwise:
```

sudo fdisk -lu

```
to see what the disk identifier is .

[INDENT][INDENT]try'n to help
[/INDENT][/INDENT]

---

### Post by deadflowr on 2015-02-22
> I can paste screenshot if it's needed.
Probably not needed, but just in case, post them as attachments.
(In reply to thread, or adv reply or go advanced, click on the paperclip in the reply box toolbar and upload the image as an attachment)

---

### Post by pawe6 on 2015-02-23
[ATTACH=CONFIG]260173[/ATTACH][ATTACH=CONFIG]260172[/ATTACH][ATTACH=CONFIG]260171[/ATTACH]

1 - During the test
Self-test Result: Self-test in progress — 90% remaining
Self-assessment: Threshold not exceeded
Overall Assessment: Disk is OK, but it has 265 wrong sectors

2 - After the test
Self-test Result: Last self-test failed (read)
Self-assessment:Threshold not exceeded
Overall Assessment: SELF-TEST FAILED

3 - Terminal
shian@Leina-Ubuntu:~$ sudo fdisk -lu
[sudo] password for shian: 

NOTE: '/dev/sda' found GPT patition table (GUID Partition Table)! fdisk does not support GPT. You must use GNU Parted.


Disk /dev/sda: 250.1 GB, 250059350016 bytes
heads: 255, sectors/track: 63, cylinders: 30401, total sectors: 488397168
Units = sectors, or 1 * 512 = 512 bytes
Sector size (logical/physical) in bytes: 512 / 4096
Size/O (minimum/optimal) in bytes: 4096 / 4096
Disk identifier: 0x00000000

Device Boot   Start      End   Blocks   ID  System
/dev/sda1               1   488397167   244198583+  ee  GPT
Partition 1 does not start at the border of the physical block.
shian@Leina-Ubuntu:~$ sudo smartctl -a /dev/sda
sudo: smartctl: command not found
shian@Leina-Ubuntu:~$ 



I have the system in Polish, so I had to translate it according to original texts, which I found in the internet.

---

### Post by stalkingwolf on 2015-02-23
you can try using the hard drive regenerator on the hirens repair disk.  I have used it many times.[http://www.hiren.info/pages/bootcd]("http://www.hiren.info/pages/bootcd")

It just depends on how bad the drive is.  some ive used it on work for years others there was no joy.

---

### Post by pawe6 on 2015-02-23
Stalkingwolf how to run this tool? I've downloaded an ".exe" expresioned file and I don't know what I can do with it.

EDIT: Nevermind, I think I'm about to manage. I'm gonna post the results :) Thanks.

---

### Post by stalkingwolf on 2015-02-24
i always download the iso and either burn it to a disc or use unetbootin and put it on a flash drive.  then you are running from a live disc or flash drive and the hdd is not mounted.

---

### Post by pawe6 on 2015-02-24
I managed to burn the CD.

I launched HDAT2 and run "Device Tests Menu". The program detected no problems.
Then I did the tests from "File System Menu" and it found some bad sectors. What do I do now?
I tried to go back to the previous menu (Device Tests Menu) and try to "Check and Repair bad sectors" but again it found no problems...
I can post some picturers made with my phone... but I'm not quite sure what's going on... 



[ATTACH=CONFIG]260192[/ATTACH][ATTACH=CONFIG]260193[/ATTACH][ATTACH=CONFIG]260194[/ATTACH][ATTACH=CONFIG]260195[/ATTACH][ATTACH=CONFIG]260196[/ATTACH]

---

