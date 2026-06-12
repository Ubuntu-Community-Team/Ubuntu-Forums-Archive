---
title: "[SOLVED] BIOS Shutdown Problem"
date: 2008-07-30
forum: New to Ubuntu
---

### Post by colintivy on 2008-07-30
Hi folks,

I have started a new thread having plodded through similar ones around the Ubuntu fora because they do not cover my situation sufficiently closely. I hope that I will be forgiven.

I have 8.04 more or less well installed on a clean 30GB HD in an elderly laptop (Pent III 866Mhz 256 KB RAM). Although it used to shutdown on its original OS (Windows 98 SE) quite normally, now it always stops short of complete shutdown to "System halted". I have tried most of the cures which seem to have satisfied others without any effect. What I have discovered is that a very quick error message during boot-up tells me that "acpi=force is required because my Bios is pre-2000". What I do not know is precisely how this can be updated since it is in cmos of the machine. The software originator is SystemSoft Corp and is their MoblePRO BIOS 1.01. This was suggested in an earlier post reply which merely said get an update and flash it, the writer has never replied again. I do not know how to do this being none too technical. Perhaps someone can elucidate?

colintivy :confused:

Tags Ububtu 8.04,Out of date BIOS, Update installation

---

### Post by JoneYee on 2008-07-30
> **colintivy said:**
> Hi folks,

I have started a new thread having plodded through similar ones around the Ubuntu fora because they do not cover my situation sufficiently closely. I hope that I will be forgiven.

I have 8.04 more or less well installed on a clean 30GB HD in an elderly laptop (Pent III 866Mhz 256 KB RAM). Although it used to shutdown on its original OS (Windows 98 SE) quite normally, now it always stops short of complete shutdown to "System halted". I have tried most of the cures which seem to have satisfied others without any effect. What I have discovered is that a very quick error message during boot-up tells me that "acpi=force is required because my Bios is pre-2000". What I do not know is precisely how this can be updated since it is in cmos of the machine. The software originator is SystemSoft Corp and is their MoblePRO BIOS 1.01. This was suggested in an earlier post reply which merely said get an update and flash it, the writer has never replied again. I do not know how to do this being none too technical. Perhaps someone can elucidate?

colintivy :confused:

Tags Ububtu 8.04,Out of date BIOS, Update installation

256KB of RAM?  HOpefully you mean MB.  

That said, you may want to consider Xubuntu, I thing the min Ram is 384 (or something like that) for Ubuntu.  

I'll look and see if I can locate a BIOS flash for you, give me as many details as possible about the systemboard and what you see inside the system BIOS.


EDIT:  Actually knowing the system type and vendor would be beneficial as well.

---

### Post by prshah on 2008-07-30
> **colintivy said:**
> 
 What I have discovered is that a very quick error message during boot-up tells me that "acpi=force is required because my Bios is pre-2000". What I do not know is precisely how this can be updated since it is in cmos of the machine. 

You don't need to update the CMOS. the message about "ACPI=FORCE" means that you must add that command during your system startup.

To do it temporarily (recommended): Press esc to enter the GRUB menu; scroll to the usual booting option, but press "e" instead of enter. Scroll down to the second (?) line (the one that starts with "kernel") then press "e" again to edit it. At the end of the line, add a space and the phrase
```

acpi=force
```

then press enter; then "b" to boot.

If you find that it makes your computer work better, post back on how to make it permanent.

---

### Post by colintivy on 2008-07-31
Hi! prshah!!

You have hit the bullseye. Fix worked 100% Thanks a lot.

Looking forward to making it permanent please.

A very grateful,
Colintivy  :):)

---

### Post by JoneYee on 2008-07-31
Good Call prshah

---

### Post by Potatoj316 on 2008-07-31
to make it permanent edit your menu.lst
```
gksudo gedit /boot/grub/menu.lst
```and add acpi=force to the same entry you did before (its at the bottom of the file)

---

### Post by prshah on 2008-07-31
> **Potatoj316 said:**
> to make it permanent edit your menu.lst
```
gksudo gedit /boot/grub/menu.lst
```and add acpi=force to the same entry you did before (its at the bottom of the file)

What he said.

After editing your menu.lst file, don't forget the command ```
sudo update-grub
``` Give it from the terminal (Applications-Accessories-Terminal)

Be careful when editing your menu.lst file.

---

### Post by colintivy on 2008-07-31
> **prshah said:**
> What he said.

After editing your menu.lst file, don't forget the command ```
sudo update-grub
``` Give it from the terminal (Applications-Accessories-Terminal)

Be careful when editing your menu.lst file.

Hi prshah,

Tried all that, found two kernal lines withe same ending  i.e. af233 ro quiet splash. Added acpi=force as instructed. Then went to Terminal and inserted sudo update-grub. Listing ran down to all updated but shutdown unaffected. I must have missed something out, was it following the edit?

Colintivy :confused:

---

### Post by prshah on 2008-07-31
> **colintivy said:**
> 
Tried all that, found two kernal lines withe same ending  i.e. af233 ro quiet splash. Added acpi=force as instructed. Then went to Terminal and inserted sudo update-grub. 

I hope you saved and quit the editor before giving the update-grub command. I don't understand what you want to say; did you get any error with the update-grub command? Can you post the output?

---

### Post by plucky on 2008-07-31
> **prshah said:**
> I hope you saved and quit the editor before giving the update-grub command. I don't understand what you want to say; did you get any error with the update-grub command? Can you post the output?

Doesn't the "update-grub" command create a new menu.lst file?

So unless you have put "acpi=force" into the default options part of menu.lst,then update-grub will change the kernel line and remove the "acpi=force" the OP put into the file.

So in menu.lst search for
> ## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash acpi=force

and put acpi=force here,so that every time menu.lst is updated,the correct options are put onto the kernel line.

Good Luck

---

### Post by colintivy on 2008-08-01
Hi folks!

Thanks to you all for thorough sorting of my problem. In my haste to make my last post I forgot that the change to the line required would not be seen until the system had to be rebooted!!! Cosequently I was quite wrong to say that the editing had not worked and it has done so on all my next use. I will look at the additional advice from plucky since he (she) thinks it will be a good insurance. When I know a bit more I will feel more comfortable in delving so deeply into the works.

colintivy :D :D

---

### Post by colintivy on 2008-08-01
Hi! Jone Yee,

Thanks for concern. Yes I did mean MB and now can report it is 512MB as a new memory has just arrived ans seems to work. This should give me more elbow room. Since the problem seems to have gone away I tink I will leave sleeping BIOS's alone for now. Should I change my mind I may well come back to you for advice.  Thanks.

colintivy :D :D

---

### Post by prshah on 2008-08-01
> **plucky said:**
> Doesn't the "update-grub" command create a new menu.lst file?


No, it doesn't.

---

### Post by louieb on 2008-08-01
from the command
```
 man update-grub
```> 
       update-grub is a program used to generate the menu.lst file used by the
       grub bootloader.  It works by looking in  /boot  for  all  files  which
       start  with  "vmlinuz-". They will be treated as kernels, and grub menu
       entries will be created for each.  It  will  also  create  the  initial
       menu.lst  if  none  exists, after prompting the user.  It will also add
       initrd lines for ramdisk images found with the same version as  kernels
       found.  e.g.  /boot/vmlinuz-2.4.5  and  /boot/initrd-2.4.5 will cause a
       line of "initrd=/boot/initrd-2.4.5 or similar to be added for the  ker&#8208;
       nel entry in the menu.lst.



If you have questions about any command in Linux (what it does, how to use it) try ** man <command name>** or **info <command name>**

---

### Post by prshah on 2008-08-01
> **louieb said:**
> from the command
```
 man update-grub
```



The key here is "..if none exists..". If there is _no_ menu.lst file, it will generate one. In real life usage, every change to the menu.lst file will need a corresponding update-grub before the changes will take effect.

A little odd that you missed the paragraph immediately following the paragraph that you've quoted: from the man(ual) > 

After update-grub has been run for the first time, the user is required
       to edit the generated menu.lst. The  user  must  set  the  two  options
       update-grub  uses.  Then  re-run  the  update-grub script to update the
       menu.lst file using the default’s that have been set.


---

### Post by louieb on 2008-08-01
> **prshah said:**
> In real life usage, every change to the menu.lst file will need a corresponding update-grub before the changes will take effect.
That is not correct. After using a text editor to change menu.lst the changes will go into effect the next time the PC is booted. update-grub does not have to be run. 

Sounds like you are getting GRUB and LILO mixed up. (LILO does required the lilo command to be run before changes to its configuration file take effect).  

> **prshah said:**
> A little odd that you missed the paragraph immediately following the paragraph that you've quoted: from the man(ual)

No I did not miss it. As you pointed out in post 3 adding the statement** acpi=force** from the grub menu  is just a temporary one boot change.

In post #6  Potato316  #6 told how to add the statement to end of the kernel line.  There is one problem with doing it that way. The next time there is a kernel update the acpi=force would have been removed by update-grub.

In post #10  plucky showed how to get update-grub to  add "acpi=force", whenever it is run,to the kernel line by modifying the defoptions line **# defoptions=quiet splash acpi=force**  

Hope this helped.

---

