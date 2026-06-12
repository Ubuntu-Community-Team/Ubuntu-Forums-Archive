---
title: "REMOVE OPtion from WIndows Boot Manager (nothing works)"
date: 2012-09-27
forum: New to Ubuntu
---

### Post by Rblatss on 2012-09-27
Hi everyone,

I'm having a tough time figuring out what my issue is and there are forum posts that are perhaps related to my issue but i'm having trouble figuring out what is going on.

I use to have an Ubuntu 11.10 partition that I was running side by side with Windows 7 (which i upgraded from XP off a flashdrive). I used Wubi to put 11.04 on my computer off of a CD and then upgraded to 11.10. I decided i wanted to upgrade to a 64 bit version and so subsequently deleted Ubuntu using Windows disk management (right clicked and hit delete volume). 

But windows boot manager is still giving me the option of starting up Ubuntu. I have  tried a few things to rid of this option but nothing recognizes Ubuntu ... I have tried

- BCDEdit.
- EasyBCD
- MSConfig
- drop down menu to set default OSUnder settings in startup and recovery of system properties.

What can i do to rid of that option aat startup and anything else of Ubuntu that may lingering of Ubuntu that i am unaware of?

---

### Post by newb85 on 2012-09-27
You should use Add/Remove Programs in the Control Panel to uninstall Wubi.

By the way, if you're planning to use the install long-term, you're better off installing from a Live CD or USB.  Wubi was only designed for testing purposes (a fact Ubuntu inexplicably and irresponsibly omitted from their website).

---

### Post by critin on 2012-09-27
> **Rblatss said:**
> Hi everyone,

What can i do to rid of that option aat startup and anything else of Ubuntu that may lingering of Ubuntu that i am unaware of?

As newb85 says, go into Windows Add/Remove and remove ubuntu or wubi from the installed list.

To get rid of the other stuff find the ubuntu folder in 'windows'.  Usually in hidden.    I'd also do a search for all things Wubi/ubuntu and delete all.  

This is all done in Windows.

---

### Post by Rblatss on 2012-09-27
Wubi is not there.

---

### Post by critin on 2012-09-27
> **newb85 said:**
> 

By the way, if you're planning to use the install long-term, you're better off installing from a Live CD or USB.  Wubi was only designed for testing purposes (a fact Ubuntu inexplicably and irresponsibly omitted from their website).

I keep hearing this and know it was true originally, but I used Wubi for two years and never had a bit of trouble with it.  I upgraded once and all went as well as it does on separate partitions now.   In fact, upgrading now causes many issues, so we're advised to do fresh  installs instead.   I think wubi is easier/safer for the mbr of newbies who've never partitioned.  JMO

---

### Post by critin on 2012-09-27
> **Rblatss said:**
> Wubi is not there.

Okay, if it's still showing in the menu, something is still there.   Double click on My Computer, then double click on the hdd.  The page will open and show lists of folders.  Find Windows and search there for ubuntu folder.  Delete the folder.  Also do a general search.

I'm looking at XP but Win7 should be the same.

Look for ubuntu and also look for wubi.

---

### Post by critin on 2012-09-27
It may have something to do with grub being installed in mbr, but I can't help with that.   Too risky for me.

---

### Post by Wim Sturkenboom on 2012-09-28
Lets go one step back.

1)
You had a dual boot of 11.10 and WinXP.
2)
Next you installed Win7 over WinXP.
3)
Next you installed 11.04 inside Win7.
4)
You removed Ubuntu using disk management.

If so, step 2 removed grub from the MBR and you could only boot windows. That's good.
Next step 4 removed your old 11.10 partition(s); it did NOT remove your wubi installation.

What's left is Win7 with a functional wubi installation. I'm not a wubi man. What happens when you try to boot Ubuntu? still working?

---

### Post by Mark Phelps on 2012-09-28
Although it's unlikely, it's possible that you have the Windows boot loader files in two partitions -- XP and Win7.

You already had a boot loader installed when you had XP.  When you installed Win7, it should have added its information to the XP partition, but if it put it into the Win7 partition, then you would be left with two: NTLDR in XP, and BCD in Win7.

Go into Win7 and run EasyBCD.  

When it opens, point it to the /boot directory in Win7 -- and see what is there.

Then, reopen it, this time, pointing it to the /boot directory in XP -- and see what is there.

If you have BCDs in BOTH, then you have the boot loader installed twice.

---

### Post by Rblatss on 2012-09-28
**Wim** : No I had Windows Xp. Then installed an 11.04 partition alongside it.
I then upgraded XP to Win7 and  11.04 to 11.10, respectively.
 
**Critin **: I found that folder in my hdd and removed it. Windows Boot Manager still prompts me with Ubuntu. I hit Ubuntu and received this message:
 
"GNU Grub 1.99~rcl 13Ubuntu3
 
Minimal Bash - like line editing is supported. For the first word, TAB lists possible cmd completions. Anywhere else TAB lists possible device or file completions. "

---

### Post by Rblatss on 2012-09-28
**Mark**: I'll check it out soon. But last time I checked in Win7 Easy BCD i found nothing. Perhaps in XP tho ? For a while windows boot manager prompted me with the "Old Version of Windows" and I had to use BCD edit to remove that.

---

### Post by Mark Phelps on 2012-09-28
> **Rblatss said:**
> **Mark**: I'll check it out soon. But last time I checked in Win7 Easy BCD i found nothing. Perhaps in XP tho ? For a while windows boot manager prompted me with the "Old Version of Windows" and I had to use BCD edit to remove that.

"Old version of Windows" is what the Win7 boot manager calls "XP".  If you remove that from the boot loader selection, you can't then boot XP anymore.

---

### Post by Rblatss on 2012-09-29
Right. I had upgraded to windows 7 and there was never a separate partition of xp because I had upgraded it to win7 and then deleted the Bootloader option for xp.

---

### Post by Rblatss on 2012-09-30
Can anyone help?

---

### Post by UniversalCyborg on 2012-10-02
I think you might be having the same issue that I had.

Go to my thread. [http://ubuntuforums.org/showthread.php?t=2065372](http://ubuntuforums.org/showthread.php?t=2065372)

Then go to the thread that bcbc suggested on my thread.

It worked for me.

---

### Post by Mark Phelps on 2012-10-02
Sometimes, EasyBCD has problems finding the BCD files, especially if they're not where EasyBCD expects to find them.

You should open EasyBCD. If it does not automatically show the boot menu, you will need to browse through your partitions, looking for it.  If you have more than one /boot folder, you could have more than one BCD file.

---

