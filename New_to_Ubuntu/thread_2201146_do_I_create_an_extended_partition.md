---
title: "do I create an extended partition?"
date: 2014-01-22
forum: New to Ubuntu
---

### Post by Ralph_Lam on 2014-01-22
I have 2 NTFS partitions; one big, one small - windows
I have 1 ext4 partition - SolydXK (Linux)
I have 1 linux swap partition.

I want to install Ubuntu as well and have grub option to boot as Windows, or SolydK or Ubunutu

gparted, and other patition software tell me that I can no create more than 4 "primary" partitions.

gparted at least gave me a window with a suggestion that I create an extended partition.

real simple - how?

Thanks

---

### Post by Dave_L on 2014-01-22
You didn't mention the sizes of the partitions.

You could get rid of the swap partition, then create an extended partition. Within it you could create as many logical volumes as you want, including one for swap. You could also move your existing SolydXK Linux primary partition into a logical volume of the extended partition.

Of course working with partitions is always risky, so ensure that everything is backed up first.

---

### Post by deadflowr on 2014-01-22
You would have to resize one or more of your existing partitions first.
I would recommend, and it is usually the recommendation, of running Windows Disk Management tools.
Disk Management is much safer and better at resizing NTFS partitions.
(Some might say run windows dragmentation once or twice first, as well)

But getting beyond that, then boot a live cd, assuming that you should now have a section of drive spaced duly named unallocated.
Open gparted and right click on the newly minted unallocated and select new.
You should have choices, somewhere in there should be a choice of making the partition Extended.
choose that and select OK.
Once you made that selection, and it resets, click on the new partition underneath what is now the extended partition and make that space a logical drive.(Best bet, is to set the file system type to ext4)
then when all is set, click apply.

---

### Post by Ralph_Lam on 2014-01-22
"...You would have to resize one or more of your existing partitions first.
I would recommend, and it is usually the recommendation, of running Windows Disk Management tools..."

Yes, this is the tool I used.  At the very beginning, I re-sized my original windows drive to allow for installation of SolydXK.  Then loaded the SolydXK live disc, and it all was down hill form there...created swap, created ext4 etc, etc, then ran installation.  All works perfectly.

"...You should have choices, somewhere in there should be a choice of making the partition Extended.
choose that and select OK...."   

NO, at precisely this juncture, it simply stops and says that I can't create more than 4 primary drives.  I was hoping that it would give me the choise to create primary of logical after clicking but it just presumes that i am trying to create a primary drive.  I don't know how to tell it otherwise...

??

---

### Post by Ralph_Lam on 2014-01-22
while in gparted, I select the unallocated drive, then click on "new" in the partition menu, and I do not get a choice to create logical or primary, I get the following message

"It is not possible to create more than 4 primary partitions

If you want more partitions you should first create an extended partition. Such a partition can contain other partitions. Because an extended partition is also a primary partition it might be necessary to remove a primary partition first."

Maybe I have to skuttle the ext4 drive that my first distro is on, but I still don't see howto create "extended" or "logical" drive even if this were the case

---

### Post by deadflowr on 2014-01-22
Delete the swap partition.
At least that's what I would do.
Then proceed from there.

after you make the extended, remake the swap.
in the solydk fstab, you'll have to change the UUID for the swap later to match the new swap.

Post the output of the 
```
sudo parted -l
```
which should give a better understanding of how the drive is laid out.

Sometimes when mucking about with partition, it can become a nice game of musical chairs.

My guess is that swap is the last partition. 
So after deleting it, I would merge it into the next partition, presumably the ext4.
after that you should have 3 primaries.
When you make the extended partition, now, leave a little space for the swap again.

---

### Post by Ralph_Lam on 2014-01-23
Deadflowr and Dave L;

I originally had a 350 gig that my first linux distro was on.  I had already shrunk is to half and had a 150 gig unallocated space. 

I deleted the swap, made an extended drive out of the unallocated space, made a 1 gig logica drive and a 149 gig logical drive, then made the 1 gig drive a swap drive so I have a ext2 logical drive and a swap drive in addition to the original windows drive and roginal linux drive.

very cool.

Thanks much to all

---

### Post by deadflowr on 2014-01-23
Good to see you got it working.

Now then, did you change the swap entry for the original distro?
If not, it's an easy fix
step one:
enter this in a terminal
```
sudo blkid
```
find the UUID for the swap partition.

step two:
either run 
```
sudo nano /etc/fstab
```
or
```
gksu gedit /etc/fstab
```
(if kde then change that to
```
kdesudo kate /etc/fstab
```
(the last one is one I've little used so, change if needed. Been awhile:-\")
Then simply replace the UUID for the swap.
save it. (in nano press ctrl+x, the y for yes and then enter; this will save over the file)

All this is an assumption on my part and if you've already done it, disregard the above.

---

### Post by Ralph_Lam on 2014-01-24
"Then simply replace the UUID for the swap."

How?

Also, everything looks like it installed but when I start the computer, I only see my first linux distro (SolydK) and Windows in the grub menu.

How do I get UBUNTU into the grub menu as a choice to boot from?

Why do I need to mess with the swap?

Thanks

---

### Post by deadflowr on 2014-01-24
> **Ralph_Lam said:**
> "Then simply replace the UUID for the swap."

How?

Also, everything looks like it installed but when I start the computer, I only see my first linux distro (SolydK) and Windows in the grub menu.

How do I get UBUNTU into the grub menu as a choice to boot from?

Why do I need to mess with the swap?

Thanks

copy and paste the entry from the blkid command.

Try running 
```
sudo update-grub
```
see if the ubuntu install shows up in the entries.
Try running it from the soldyk distro.

You need to redo swap in the fstab file because the UUID listed would be different than the one you have now, IF you moved it,reformatted it, made a new one , et al.
Otherwise the file will tell the OS to look for the swap in a probably non-existent partition/disk.

---

### Post by Ralph_Lam on 2014-01-24
Ok, I think that I have the full picure.

So, first things first.

I think perhaps I will open the treminal and enter this "sudo update-grub"

Then if it looks like I can boot into Ubuntu, I will go back and try to make sense of the list of stuff you gave me on the swap drive issue.

Will this fix it so that Ubuntu and Solyd will both look at the swap drive location properly, or do I need to take those steps while running SolydK too?

Thanks

---

### Post by Ralph_Lam on 2014-01-24
Ok, just re-read your question on this.  You are asking if I did this for SolydK.  I get it.  Sense I told the Ubuntu install where the swap drive was during that process, it should already be good.

Thanks so much.

---

### Post by Ralph_Lam on 2014-01-24
Ok, looks like grub has ubuntu in it's list

Now, about the swap,  I see that my swap uuid is 3bfa3fcb-911f-47d5-aa00-872f903cfa5c.

Running the 
sudo nano /etc/fstab

gives me some stuff, but not sure what to do with it.

You said simply replace the uuid withthe new one....how?

Thanks

---

### Post by deadflowr on 2014-01-24
> **Ralph_Lam said:**
> Ok, just re-read your question on this.  You are asking if I did this for SolydK.  I get it.  Sense I told the Ubuntu install where the swap drive was during that process, it should already be good.

Thanks so much.

Exactly.

In the file /etc/fstab do you have a line (section) that looks like this
```
# swap was on /dev/sda5 during installation
UUID=**e863140f-977c-4c84-b785-c3c3b439ffad** none            swap    sw              0       0

```
Simply erase the number and enter in the new one.

Of course it's also possible that solydK uses the device path instead.
That would show as the partition number It would look something like this
```
/dev/sda5 none            swap    sw              0       0
```
in which case, you would simply change the partition number to whatever the newly remade swap's partition number is.

This might give some better understanding
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

Hope it helps better than I can explain it.

---

### Post by Ralph_Lam on 2014-01-24
Was able to update the grub, computer now give sme three choices at start up
1.)SolydK
2.)Ubuntu
3.)Windows

able to boot into UBUNTU - way cool (using that now)

still don't know exactly what to do on the swap partition thing though.

I entered the fstab stuff and got a screen full of stuff that looks like a miniature interface with commands listed at the bottom.

Now what?  How do I tell it that my swap partition is at such-and-such UUID?

Thanks

---

### Post by deadflowr on 2014-01-24
> [COLOR=#000000] How do I tell it that my swap partition is at such-and-such UUID?[/COLOR]
Run the sudo blkid command and look for a line that would look something like this
```
/dev/sda5: UUID="e863140f-977c-4c84-b785-c3c3b439ffad" TYPE="swap" 
```
The partition number is probably different but the key is looking for the Type = "swap" at the end.

---

### Post by Ralph_Lam on 2014-01-24
After "sudo update-grub", I am able to boot into UBUNTU from grub which is now showing 3 OS's o choose from at start up.

entering "    [COLOR=#000000][FONT=Arial]gksu gedit /etc/fstab[/FONT][/COLOR] "

gives me a screen of what looks like a miniature interface with a list of commands.

How to I "tell" SolydK the UID of the new swap location?

---

### Post by Ralph_Lam on 2014-01-24
ralph@rgl-isa-laptop ~ $ sudo blkid
[sudo] password for ralph: 
/dev/sda1: LABEL="System Reserved" UUID="389427C29427818C" TYPE="ntfs" 
/dev/sda2: UUID="52462A044629EA05" TYPE="ntfs" 
/dev/sda4: UUID="3cfaea19-2636-488d-9174-74b907d5d224" TYPE="ext4" 
/dev/sda5: UUID="48481bc1-9777-4968-8539-1d12bf03216e" TYPE="ext4" 
/dev/sda6: UUID="3bfa3fcb-911f-47d5-aa00-872f903cfa5c" TYPE="swap" 
ralph@rgl-isa-laptop ~ $ 

ok, so "3bfa3fcb-911f-47d5-aa00-872f903cfa5c" is obvious;y the UID of "swap"

then I entered this
 
 [COLOR=#000000]sudo nano /etc/fstab[/COLOR]

and this is what followed...



# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc    /proc   proc    defaults        0       0
# /dev/sda3
UUID=ef137d4b-3f20-4c4b-aa62-92581a3c5816       swap    swap    sw      0       0
# /dev/sda4
UUID=3cfaea19-2636-488d-9174-74b907d5d224       /       ext4    rw,errors=remount-ro    0       1

It seems like it SudoK thinks that the UID of "swap" is ef137d4b-3f20-4c4b-aa62-92581a3c5816, so how do it tell it otherwise?

---

### Post by Ralph_Lam on 2014-01-24
There is all of this stuff down at the bottom of the screen after  "sudo nano /etc/fstab


                            [ line 1/9 (11%), col 1/46 (2%), char 0/305 (0%) ]
^G Get Help      ^O WriteOut      ^R Read File     ^Y Prev Page     ^K Cut Text      ^C Cur Pos
^X Exit          ^J Justify       ^W Where Is      ^V Next Page     ^U UnCut Text    ^T To Spell

---

### Post by deadflowr on 2014-01-24
> **Ralph_Lam said:**
> ralph@rgl-isa-laptop ~ $ sudo blkid
[sudo] password for ralph: 
```
/dev/sda1: LABEL="System Reserved" UUID="389427C29427818C" TYPE="ntfs" 
/dev/sda2: UUID="52462A044629EA05" TYPE="ntfs" 
/dev/sda4: UUID="3cfaea19-2636-488d-9174-74b907d5d224" TYPE="ext4" 
/dev/sda5: UUID="48481bc1-9777-4968-8539-1d12bf03216e" TYPE="ext4" 
/dev/sda6: UUID="**3bfa3fcb-911f-47d5-aa00-872f903cfa5c**" TYPE="swap" 
```


ok, so "3bfa3fcb-911f-47d5-aa00-872f903cfa5c" is obvious;y the UID of "swap"

then I entered this
 
 [COLOR=#000000]sudo nano /etc/fstab[/COLOR]

and this is what followed...



```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc    /proc   proc    defaults        0       0
# /dev/sda3
UUID=**ef137d4b-3f20-4c4b-aa62-92581a3c5816**       swap    swap    sw      0       0
# /dev/sda4
UUID=3cfaea19-2636-488d-9174-74b907d5d224       /       ext4    rw,errors=remount-ro    0       1
```

It seems like it SudoK thinks that the UID of "swap" is ef137d4b-3f20-4c4b-aa62-92581a3c5816, so how do it tell it otherwise?
Copy the swap UUID from the blkid
open the fstab file, go to the swap line delete the old line and replace it with the new one.
I would simply go to the line and use backspace to delete.
Then right click and paste in the new line.
Then save and exit.
(I use ctrl+x to save and exit.)
It'll ask if you want to overwrite the file, answer y(yes) then make sure the name it says is the right name(should be, unless you hit a key by accident) then hit enter.

---

### Post by Ralph_Lam on 2014-01-24
just replace it, do I hit enter?

---

### Post by Ralph_Lam on 2014-01-24
apparently, I don't know how to open the fstab file

---

### Post by jeremy1138 on 2014-01-24
You should probably just use gedit to edit the fstab file.  Nano can be a little daunting if you've never used it.  I think that will fix most of your problems.

```

gksu gedit /etc/fstab

```

---

### Post by Ralph_Lam on 2014-01-24
Ok, starting to understadn now.  "fstab" is a text document in the folder named "etc" in "root".  I need to use a text editor to paste the UUID given when I ran  [COLOR=#000000][FONT=Arial]sudo blkid, into the fstab text document

Ok, so [COLOR=#000000][FONT=Arial]" sudo blkid "[/FONT][/COLOR] returned this

/dev/sda1: LABEL="System Reserved" UUID="389427C29427818C" TYPE="ntfs" 
/dev/sda2: UUID="52462A044629EA05" TYPE="ntfs" 
/dev/sda4: UUID="3cfaea19-2636-488d-9174-74b907d5d224" TYPE="ext4" 
/dev/sda5: UUID="48481bc1-9777-4968-8539-1d12bf03216e" TYPE="ext4" 
/dev/sda6: UUID="3bfa3fcb-911f-47d5-aa00-872f903cfa5c" TYPE="swap" 

so to me, this looks like somewhere in it's world it can see that /dev/sda6 is "swap"

the fstab text document looks like this

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc    /proc    proc    defaults    0    0
# /dev/sda3
UUID=ef137d4b-3f20-4c4b-aa62-92581a3c5816    swap    swap    sw    0    0
# /dev/sda4
UUID=3cfaea19-2636-488d-9174-74b907d5d224    /    ext4    rw,errors=remount-ro    0    1

I don't see anywhere that it says sda6 in the current fstab text document.

will simply changing [/FONT][/COLOR][COLOR=#000000][FONT=Arial][COLOR=#000000][FONT=Arial]" ef137d4b-3f20-4c4b-aa62-92581a3c5816 " to [COLOR=#000000][FONT=Arial]" 3bfa3fcb-911f-47d5-aa00-872f903cfa5c " in the above text and saving it do the trick?

It looks like [COLOR=#000000][FONT=Arial][COLOR=#000000][FONT=Arial]" ef137d4b-3f20-4c4b-aa62-92581a3c5816 " is sandwiched between sda3 and sda4, a tad confusing for a newbie.

Thanks so much for your help.
[/FONT][/COLOR][/FONT][/COLOR][/FONT][/COLOR][/FONT][/COLOR]
PS.

This is what fstab says on the UBUNTU etc folder

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=48481bc1-9777-4968-8539-1d12bf03216e /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=3bfa3fcb-911f-47d5-aa00-872f903cfa5c none            swap    sw              0       0

[/FONT][/COLOR]

---

### Post by deadflowr on 2014-01-24
The # symbol in the fstab file means(as it does for all files) that line will be ignored.

The old partitioning you had, had swap on /dev/sda4, but now it is on /dev/sda6.

You can change that too, if you like.
But it's not as important.

Think of it as a helpful hint.
The important lines are the ones without a # symbol in the front.

So yes, simply changing the UUID is all you need to do.

---

### Post by Ralph_Lam on 2014-01-24
I might be guessing, but itt loks like I would hav to change more than just replacing the number on the line whee the word "swap" appears.

I lloks like SolydK thinks that sda3 is swap, when sda3 no longer exists.  There is only sda1, sda2, sda4, sda5 and sda6.

Might I have to replace all of the following

[COLOR=#000000][FONT=Arial]# /dev/sda3
UUID=ef137d4b-3f20-4c4b-aa62-92581a3c5816    swap    swap    sw    0    0[/FONT][/COLOR]

with the following

[COLOR=#000000][FONT=Arial]# /dev/sda6: 
UUID=3bfa3fcb-911f-47d5-aa00-872f903cfa5c swap swap sw 0 0

???

[/FONT][/COLOR]Thank you, thank you, thank you

---

### Post by Ralph_Lam on 2014-01-24
ok, all I did is replace the number and save.

Good thing I remembered that I had to open it as "root" to make changes.

I think that is all I need for this episode.

Conclusion:

I can not boot in Windows, SoldydK, or UBUNTU and the swap is understood by both linux distros.

Problem sovled!!

Thanks ever so much to all.

Now, watching Netflix....

---

### Post by deadflowr on 2014-01-24
> [COLOR=#000000]I can ***not*** boot in Windows, SoldydK, or UBUNTU [/COLOR]

I hope you mean "now"

Anyway, how is booting into each working.

---

### Post by Ralph_Lam on 2014-01-24
On start up, I am presented with a screen (blue background) that has

SolydK
SolydK (recovery)
Windows 7
Ubuntu
Ubuntu (recovery)

choosing Windows 7 takes me to a screen which looks exactly like the first one, but the font is somewhat smaller, and it has an orange background.

Choosing Windows 7 on this screen just keeps putting up the same screen with the orange background.

It seems to like threre is a grub on 2 drives...

now what?

I cna not boot in Windows 7 but I CAN see all my files on it's partition (thankfully)

hmmmmm

---

### Post by oldfred on 2014-01-24
Grub only boots a working Windows. Windows always needs a chkdsk after a resize, but may need other repairs. Boot-Repair is only for Linux and can only do minor fixes to Windows. If chkdsk or other repairs to Windows are required, you need your Windows repairCD or flash drive.

But to see if system is configured correctly this will show most eveything in detail. It does not parse Windows BCD and some other Windows things.
       Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by Ralph_Lam on 2014-01-24
I did not resize the windows partition.

Nothing on the windows partition was changed by me.

Is there a grub on the windows partition that I can delete?

---

### Post by oldfred on 2014-01-24
Post Bootinfo so we can tell if that is an issue.

---

### Post by Ralph_Lam on 2014-01-24
this is the second time this has happened.  It looks like it is all going very well after entering the sudo commands as described, it shows a gray screen that has the word "ok" as the end, but there does not seem to be any way to click ok or mover forward in any way....

this is the text in the ray box preceding the word "ok"

 Configuring ttf-mscorefonts-installer  

TrueType core fonts for the Web EULA                                         
 &#9474;                                                                              
 &#9474; END-USER LICENSE AGREEMENT FOR MICROSOFT SOFTWARE                            
 &#9474;                                                                              
 &#9474; IMPORTANT-READ CAREFULLY: This Microsoft End-User License Agreement          
 &#9474; ("EULA") is a legal agreement between you (either an individual or a         
 &#9474; single entity) and Microsoft Corporation for the Microsoft software          
 &#9474; accompanying this EULA, which includes computer software and may include     
 &#9474; associated media, printed materials, and "on-line" or electronic             
 &#9474; documentation ("SOFTWARE PRODUCT" or "SOFTWARE"). By exercising your         
 &#9474; rights to make and use copies of the SOFTWARE PRODUCT, you agree to be       
 &#9474; bound by the terms of this EULA. If you do not agree to the terms of         
 &#9474; this EULA, you may not use the SOFTWARE PRODUCT. 
SOFTWARE PRODUCT LICENSE The SOFTWARE PRODUCT is protected by copyright      
 &#9474; laws and international copyright treaties, as well as other intellectual     
 &#9474; property laws and treaties. The SOFTWARE PRODUCT is licensed, not sold.      
 &#9474;                                                                              
 &#9474; 1. GRANT OF LICENSE. This EULA grants you the following rights:              
 &#9474;                                                                              
 &#9474;  &#8226; Installation and Use. You may install and use an unlimited number         
 &#9474;    of copies of the SOFTWARE PRODUCT.                                        
 &#9474;  &#8226; Reproduction and Distribution. You may reproduce and distribute           
 &#9474;    an unlimited number of copies of the SOFTWARE PRODUCT; provided           
 &#9474;    that each copy shall be a true and complete copy, including all           
 &#9474;    copyright and trademark notices, and shall be accompanied by a   
 copy of this EULA. Copies of the SOFTWARE PRODUCT may not be              
 &#9474;    distributed for profit either on a standalone basis or included           
 &#9474;    as part of your own product.                                              
 &#9474;                                                                              
 &#9474;                                                                              
 &#9474; 2. DESCRIPTION OF OTHER RIGHTS AND LIMITATIONS.                              
 &#9474;                                                                              
 &#9474;  &#8226; Limitations on Reverse Engineering, Decompilation, and                    
 &#9474;    Disassembly. You may not reverse engineer, decompile, or                  
 &#9474;    disassemble the SOFTWARE PRODUCT, except and only to the extent           
 &#9474;    that such activity is expressly permitted by applicable law               &#8226; Restrictions on Alteration. You may not rename, edit or create            
 &#9474;    any derivative works from the SOFTWARE PRODUCT, other than                
 &#9474;    subsetting when embedding them in documents.                              
 &#9474;  &#8226; Software Transfer. You may permanently transfer all of your               
 &#9474;    rights under this EULA, provided the recipient agrees to the              
 &#9474;    terms of this EULA.                                                       
 &#9474;  &#8226; Termination. Without prejudice to any other rights, Microsoft may         
 &#9474;    terminate this EULA if you fail to comply with the terms and              
 &#9474;    conditions of this EULA. In such event, you must destroy all              
 &#9474;    copies of the SOFTWARE PRODUCT and all of its component parts.     
3. COPYRIGHT. All title and copyrights in and to the SOFTWARE PRODUCT        
 &#9474; (including but not limited to any images, text, and "applets"                
 &#9474; incorporated into the SOFTWARE PRODUCT), the accompanying printed            
 &#9474; materials, and any copies of the SOFTWARE PRODUCT are owned by Microsoft     
 &#9474; or its suppliers. The SOFTWARE PRODUCT is protected by copyright laws        
 &#9474; and international treaty provisions. Therefore, you must treat the           
 &#9474; SOFTWARE PRODUCT like any other copyrighted material.                        
 &#9474;                                                                              
 &#9474; 4. U.S. GOVERNMENT RESTRICTED RIGHTS. The SOFTWARE PRODUCT and               
 &#9474; documentation are provided with RESTRICTED RIGHTS. Use, duplication, or      
 &#9474; disclosure by the Government is subject to restrictions as set forth in      
 &#9474; subparagraph (c)(1)(ii) of the Rights in Technical Data and Computer     
Software clause at DFARS 252.227-7013 or subparagraphs (c) (1) and (2)       
 &#9474; of the Commercial Computer Software - Restricted Rights at 48 CFR            
 &#9474; 52.227-19, as applicable. Manufacturer is Microsoft Corporation/One          
 &#9474; Microsoft Way/Redmond, WA 98052-6399.                                        
 &#9474;                                                                              
 &#9474; LIMITED WARRANTY                                                             
 &#9474;                                                                              
 &#9474; NO WARRANTIES. Microsoft expressly disclaims any warranty for the            
 &#9474; SOFTWARE PRODUCT. The SOFTWARE PRODUCT and any related documentation is      
 &#9474; provided "as is" without warranty of any kind, either express or             
 &#9474; implied, including, without limitation, the implied warranties or            
 &#9474; merchantability, fitness for a particular purpose, or noninfringement. 
The entire risk arising out of use or performance of the SOFTWARE            
 &#9474; PRODUCT remains with you.                                                    
 &#9474;                                                                              
 &#9474; NO LIABILITY FOR CONSEQUENTIAL DAMAGES. In no event shall Microsoft or       
 &#9474; its suppliers be liable for any damages whatsoever (including, without       
 &#9474; limitation, damages for loss of business profits, business interruption,     
 &#9474; loss of business information, or any other pecuniary loss) arising out       
 &#9474; of the use of or inability to use this Microsoft product, even if            
 &#9474; Microsoft has been advised of the possibility of such damages. Because       
 &#9474; some states/jurisdictions do not allow the exclusion or limitation of        
 &#9474; liability for consequential or incidental damages, the above limitation      
 &#9474; may not apply to you.                           
MISCELLANEOUS                                                                
 &#9474;                                                                              
 &#9474; If you acquired this product in the United States, this EULA is governed     
 &#9474; by the laws of the State of Washington.                                      
 &#9474;                                                                              
 &#9474; If this product was acquired outside the United States, then local laws      
 &#9474; may apply.                                                                   
 &#9474;                                                                              
 &#9474; Should you have any questions concerning this EULA, or if you desire to      
 &#9474; contact Microsoft for any reason, please contact the Microsoft               
 &#9474; subsidiary serving your country, or write: Microsoft Sales Information       
 &#9474; Center/One Microsoft Way/Redmond, WA 98052-6399.                             
 &#9474;                                                                              
 &#9474; Reference: [http://www.microsoft.com/typography/fontpack/eula.htm](http://www.microsoft.com/typography/fontpack/eula.htm)    
 &#9474;    notwithstanding this limitation. 

                                <Ok>

---

### Post by deadflowr on 2014-01-24
[COLOR=#000000]Did you get the font installer from running the command to install [boot-repair/bootinfo]("https://help.ubuntu.com/community/Boot-Info")?

I've never seen that before.

[/COLOR]

---

### Post by Ralph_Lam on 2014-01-24
yes, and it did it before when I tried to get pipelight installed in order to watch netflix.  How do you accept, or click on the "ok"?

---

### Post by deadflowr on 2014-01-24
> **Ralph_Lam said:**
> yes, and it did it before when I tried to get pipelight installed in order to watch netflix.  How do you accept, or click on the "ok"?

It's been a while, but I think the tab button should move you to the ok button.
Maybe the left/right buttons.

But still, I wouldn't think that's normal.

Did you by chance try installing the package "ubuntu-restricted-extras"
that ttf-blahblah package is normally part of that.

---

### Post by Ralph_Lam on 2014-01-24
no, just followed the instructions.

So, my mistake was trying it form the Ubuntu that is on my hard drive.  I re-read the instructions and it clearly said to try it from a live DVD.  I did it from the live DVD, and I did not get that screen, and it worked perfectly.  I am now able to boot from all three.

Pretty cool...

Thanks to oldfred, moderator.  This worked like a charm.

I will also try the tab button next time I see this gray screen.

awesome.  feeling powerful, even though I did this with advise from others.  I find Ubuntu to be pretty good.

---

### Post by oldfred on 2014-01-25
Glad you got it working.

When you ran Boot-Repair from your install it runs a an update to be sure you have everything current and in sync. 
And if you have just installed and not updated after install or checked to update as part of install, then Boot-Repair will trigger the update which then may include a lot of other updates.

---

