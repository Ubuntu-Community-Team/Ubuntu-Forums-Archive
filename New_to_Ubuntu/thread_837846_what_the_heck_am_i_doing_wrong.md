---
title: "what the heck am i doing wrong??"
date: 2008-06-22
forum: New to Ubuntu
---

### Post by Andrew79 on 2008-06-22
Okay, so i am trying to upgrade from 6.10 to 8.04
i downloaded the iso image from the website. then i drag and drop to the disk and burn it. it asks how i want to do it, i choose the burn image option. cool. i turn the computer off, then back on, i press esc, i don't get the normal install, run live, several options menu. i get one that gives me the choice between run the cd/boot or boot from the hard drive. so i choose the disk, but it dosn't install my upgrade. it does nothing. it just goes to the normal desktop 6.10, like i did nothing. 
what the heck am i doing wrong?

---

### Post by PmDematagoda on 2008-06-22
Did you set the BIOS to boot from the CD?

---

### Post by RomeReactor on 2008-06-22
Hi. Make sure the disc is burned as an image; once you boot to your Dapper desktop, browse the CD and see if there are files and folders there. If you only have the same ISO image you downloaded, you need to burn another disc. I think this feature was available in Dapper: Just right-click the ISO image and choose 'Write to Disc...'.

EDIT: Note that if you don't have a separate /home partition, installing Hardy this way will not upgrade your system, but overwrite it instead. Though you can't upgrade directly from 6.10 to 8.04, [this page]("https://help.ubuntu.com/community/UpgradeNotes") has instructions on how to upgrade either through the package manager or using an Alternate CD.

---

### Post by Oldsoldier2003 on 2008-06-22
> **Andrew79 said:**
> Okay, so i am trying to upgrade from 6.10 to 8.04
i downloaded the iso image from the website. then i drag and drop to the disk and burn it. it asks how i want to do it, i choose the burn image option. cool. i turn the computer off, then back on, i press esc, i don't get the normal install, run live, several options menu. i get one that gives me the choice between run the cd/boot or boot from the hard drive. so i choose the disk, but it dosn't install my upgrade. it does nothing. it just goes to the normal desktop 6.10, like i did nothing. 
what the heck am i doing wrong?

6.10 will not direct upgrade to 8.04.(well you can do it if you are brave and want to take a chance using unsupported methods)...

The correct way to go from 6.10>8.04  is to do the upgrades in this order: 6.10>7.04>7.10>8.04

TBH I would just backup and do a clean install.

---

### Post by Andrew79 on 2008-06-22
> **PmDematagoda said:**
> Did you set the BIOS to boot from the CD?

okay, i think i am missing something here. when you say set the bios to boot from the cd, what does that mean exactly. i thought when i was pressing esc to get to the menu that was bios, i did choose to boot from the cd from that menu

---

### Post by fenian on 2008-06-22
After you chose to boot from cd in the bios did you save the settings before rebooting?

---

### Post by Andrew79 on 2008-06-22
> **RomeReactor said:**
> Hi. Make sure the disc is burned as an image; once you boot to your Dapper desktop, browse the CD and see if there are files and folders there. If you only have the same ISO image you downloaded, you need to burn another disc. I think this feature was available in Dapper: Just right-click the ISO image and choose 'Write to Disc...'.

EDIT: Note that if you don't have a separate /home partition, installing Hardy this way will not upgrade your system, but overwrite it instead. Though you can't upgrade directly from 6.10 to 8.04, [this page]("https://help.ubuntu.com/community/UpgradeNotes") has instructions on how to upgrade either through the package manager or using an Alternate CD.

I checked out this page, nice clear instructions i went through the steps, and it would not let me do what we need to do. so i did the check in the syn.pak. mangr and went through the steps, i got a can not do anything message with errors, and failed what evers. i ordered a new disk to be mailed, is this going to be my only option?

---

### Post by Andrew79 on 2008-06-22
> **fenian said:**
> After you chose to boot from cd in the bios did you save the settings before rebooting?

okay. what setting? i need someone to explain please step by step what it is that your saying here, cause i am just getting confused with the differnet ways to do this. sorry, i don't mean to be ingrateful, please dont take it that way, it is just a question to my question is just making my head spin, i have been sitting here for three day now, and always end up with error messages, or no change. ughhhhhhhhhh

---

### Post by RomeReactor on 2008-06-22
He's referring to the changes you made in BIOS so that it would boot from the CD drive. There should be an option there to save that change so that it will always try to boot from the CD first.

What error messages are you getting in Synaptic when trying to upgrade? Did you make sure the disc was burned correctly?

---

### Post by cariboo on 2008-06-22
I'll add some pictures to show you what you need to do. This is Brasero it is installed by default you can access it in Applcations-->Sound&Video-->Brasero.

Check the attached sceenshots.

Jim

---

### Post by RomeReactor on 2008-06-22
I don't think Brasero is not installed by default in Edgy.

---

### Post by cariboo on 2008-06-23
You might be right, its been quite a while since I used Edgy.

Jim

---

### Post by Andrew79 on 2008-06-23
allright, so I downloaded 8.04, it goes to my desktop, i put in a cd, drag and drop the image to the disk, it asks what i want to do, i tell it to copy the file image to the disk. when i turn the computer off, then back on, i hit escape, i tell it to boot from the cd-rom, then it goes through to my regular screen, and here i am again :confused:
when you say bios, where do i need to go to get the dang thing to go to the regular screen from the live disk where i can choose to install? what am i missing?

---

### Post by Bradtek on 2008-06-23
Look on your burnt CD (using file manager)
What do you see ?
If you see an .iso file
you did not burn it correctly
and it will not boot

If you see a bunch of directories and files
it should work.

What kind of PC are you doing this on ?

---

### Post by RomeReactor on 2008-06-23
> **Andrew79 said:**
> allright, so I downloaded 8.04, it goes to my desktop, i put in a cd, drag and drop the image to the disk, it asks what i want to do, i tell it to copy the file image to the disk.

Don't drag it; just right click on the ISO and select 'Write to Disc...'.

---

### Post by Andrew79 on 2008-06-23
Okay, just wanted to say that I am writing this from my freshly installed 8.04!!! Thank you to everyone for your guidance. I have been working at this now for 3 days, and it was a simple unknowing on my part, but, we are good now. Thank you

---

### Post by RomeReactor on 2008-06-23
Glad you got it installed! That's what we're here for: to learn from one another. Enjoy Hardy! :popcorn:

---

