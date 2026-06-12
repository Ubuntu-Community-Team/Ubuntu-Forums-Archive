---
title: "Wd external now read only"
date: 2012-05-10
forum: New to Ubuntu
---

### Post by Filthy Stockings on 2012-05-10
Posted this on HARDWARE forum but clearly I still lack the knowledge base to understand the technical specifics so could someone explain and advise re those matters that still confuse, please?

Been  using a WD ELEMENTS 1 TB EXTERNAL HD for over 10 months and a WD  ELEMENTS 2 TB EXTERNAL HD for 4 months; only plugging in weekly to  backup data.

ALL whilst using U 11.04 OS.

BUT one week ago, as backing up items to 2TB unit, the COPY TO process  suddenly stopped and noticed the EXTERNAL HD icon on the DASH had  vanished and then seemed to intermittently re-appear...then not  re-appear so had to disconnect without SAFELY REMOVE option.

Then tried same USB CABLE/POWER UNIT for the 1TB to try and back up to  that; since needed some space on the PC....but same problem occurred as  copying data and had to remove without SAFELY REMOVE option.

When tried to start the 1TB up again got the following alert on screen;

                                  [SIZE=3]Error mounting: mount exited with exit code 13: $MFTMirr does not match $MFT (record 0).[/SIZE]
 [SIZE=3]Failed to mount '/dev/sdb1': Input/output error[/SIZE]
 [SIZE=3]NTFS is either inconsistent, or there is a hardware fault, or it's a[/SIZE]
 [SIZE=3]SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows[/SIZE]
 [SIZE=3]then reboot into Windows twice. The usage of the /f parameter is very[/SIZE]
 [SIZE=3]important! If the device is a SoftRAID/FakeRAID then first activate[/SIZE]
 [SIZE=3]it and mount a different device under the /dev/mapper/ directory, (e.g.[/SIZE]
 [SIZE=3]/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation[/SIZE]
 [SIZE=3]for more details.[/SIZE]
  
As a technical novice am ignorant as to what the above means but as  installing the 2TB also produced the same alert, and after swapping the  USB and POWER UNITS; am now stuck with 2 apparently unusable EXTERNALS  with over 2TB data between them; which I now fear might have been lost.

Have connected the 1 TB unit to a W2K PC and followed above procedure re [SIZE=3]run chkdsk /f on Window [/SIZE][SIZE=3]then reboot into Windows twice....

[/SIZE]but didn't do the x2 reboot as was wary of causing further harm now the UNIT allowed me to read it and copy files to it and safely removed.

But when then connected to UBUNTU 11.04 PC whilst chuffed did not get the previous ERROR message, now found the unit READ ONLY.

1 Could this be because I did not REBOOT TWICE?

2 Could following this procedure return the unit to READ/WRITE functions?;
                                  

Code:
 $ sudo apt-get install ntfsprogs 



Code:
 $ sudo ntfsfix /dev/sda2 "This should fix the disk. Reboot after this."


[*HAVE ALREADY DONE THE ABOVE BUT DID NOT HAVE THE UNIT CONNECTED WHEN TYPING THE 2ND CODE...DUE TO IGNORANCE/FEAR DATA WOULD BE LOST...]*
  


 *DO I REBOOT WITH THE EXTERNAL HDD STILL CONNECTED AND POWERED FROM THE MAINS?*

  
3 How can I determine which USB port is identified as[SIZE=3]
'/dev/sdb1'
[SIZE=2]in the original error report? As this seems critical in the advice directly above which I found on an old thread.[/SIZE][/SIZE][SIZE=3][SIZE=2] I have 2 to choose from....[/SIZE][/SIZE]
[SIZE=3][SIZE=2]
4 Any other suggestions that do not involve removing the drive from its casing etc....software solutions preferred.

Thanks in advance.

SA 
[/SIZE][/SIZE]

---

### Post by Filthy Stockings on 2012-05-10
Can anyone offer any help please? However small greatly appreciated as still do not know if should have external HDD connected to its power supply and to connect to UBUNTU 11.04 PC and then run

 sudo ntfsfix /dev/sda2

and/or how to accurately identify which PORT is the one the HDD will be connected to, as imperative when running above command.

OR do I have to go back to WINDOWS machine to REBOOT TWICE to restore WRITE TO facility to this currently READ ONLY unit.

Still have 2TB WD ELEMENTS which suffered same USB/POWER failure and subsequent error report.

Could I connect this to UBUNTU PC and try the above command WITHOUT going through the WINDOWS chkdsk, as did with 1TB HDD and resulted in the switch to READ ONLY.

Hope someone might find some time to guide me through these problems; thank you.

---

### Post by Filthy Stockings on 2012-05-11
Have not been able to persuade anyone to help me on this matter. 

Am I misunderstanding some forum etiquette here?

Am open to any advice that might get me some help as whilst not new to LINUX since have had my UBUNTU PC for nearly a year; I am not very technically confident and greatly appreciate guidance from those much more proficient.

Can see others with more general questions get lots of replies so am confused as to why my problems; posted as precise and clear as I can manage; seem to be gaining no useful advice.

Regards

SA

---

### Post by Mark Phelps on 2012-05-11
> **Shia Asininity said:**
> Have not been able to persuade anyone to help me on this matter. 

Am I misunderstanding some forum etiquette here?



NO ... you're encountering the "standard" problem you will get with any volunteer-supported forum: You may not get advice as quickly as you need it.

For the most part, since NTFS is NOT a Linux filesystem, anything but the most trivial of filesystem errors really requires MS Windows to do the repairs.

If the NTFS filesystem is merely marked as "dirty" (which is what happens if the drive is suddenly disconnected), you should be able to fix that by plugging the drive into an actual MS Windows PC and doing CHKDSK on the drive.

If that doesn't restore access, or if the CHKDSK fails on the MS Windows PC, then you will have to resort to using MS Windows utilities to try to recover the data.

---

### Post by Filthy Stockings on 2012-05-12
Thanks for the advice and explanation as to how some posts become ignored.

Can you help me a little bit more?

As stated in my first posts, I have managed to use a WINDOWS PC and do the CHKDSK but this seems to have rendered the WD EXTERNAL HDD as being READ ONLY when reconnected to my UBUNTU 11.10 PC.

Do you know if the quoted suggested cures which I have found by search and posted here, would likely SOLVE the READ ONLY aspect?

Also some basics such as SHOULD I HAVE REBOOTED TWICE as ERROR REPORT suggested?

Would that have prevented the READ ONLY result of the CHKDSK?

Also is there any risk of a DIRTY occasion again arising if I keep the EXTERNAL HDD in ANY pc and powered from mains and do REBOOTS?

I still have a 2nd WD ELEMENTS HDD which suffered the same DIRTY removal but have not tried the WINDOWS CHKDSK on it yet as fear the same READ ONLY result may occur.

Do you think that AVOIDING the WINDOWS CHKDSK route and just connecting the 2TB WD to my UBUNTU 11.10 PC and doing 

sudo ntfsfix /dev/sda2

would present any greater risks re losing data?

Thanks to you and anyone who might find the time to share their knowledge on this matter.

---

### Post by Filthy Stockings on 2012-05-14
FINALLY found a cure to restore my WD EXTERNAL HDD to READ/WRITE by constant searching these forums, so thanks to the more recent poster who sought out the result in the thread below...he attracted the advice I never received.

  	 	 	 	 	 	    [COLOR=#000000][SIZE=3][http://ubuntuforums.org/showthread.php?t=1979516](http://ubuntuforums.org/showthread.php?t=1979516)[/SIZE][/COLOR]


and below is his posted link to the SOLUTION which is NOT from these forums...til now
 

  [COLOR=#000000][SIZE=3][http://www.noobslab.com/2011/12/inst...-tool-and.html](http://www.noobslab.com/2011/12/inst...-tool-and.html)[/SIZE][/COLOR]
  

  WESTERN DIGITAL SUPPORT were HOPELESS!

---

### Post by JKyleOKC on 2012-05-14
That link should be ```
http://www.noobslab.com/2011/12/install-ntfs-configuration-tool-and.html
```
Apparently the message editor chopped out the middle of it, turning it into an invalid address! Here's the full version again: [http://www.noobslab.com/2011/12/install-ntfs-configuration-tool-and.html](http://www.noobslab.com/2011/12/install-ntfs-configuration-tool-and.html) (which looks the same, but works properly this time).

---

