---
title: "TRYING to install on a new ASUS UX31A (bought in Japan)"
date: 2012-09-29
forum: New to Ubuntu
---

### Post by salmonberger on 2012-09-29
Having tried to boot from a Live USB and failed, I tried the Windows Installer (which worked great on my Toshiba Satellite) and am having the following problem.

OK, so I can get as far as the boot screen, where Windows 7 and Ubuntu are both offered as boot options. 

However, when I choose to boot with Ubuntu, I get blocked and told that to resolve the problem, I must:

1.) Insert a Windows Install Disk and then restart the computer.
2.) Go to Language Settings, click "NEXT"
3.) Click system restore.

Problem: No disk drive on the ASUS UX31A.
Second problem: I am trying to do this in Japanese, which I am only moderately competent in. Reading these menus takes me ages. I have Windows 7 installed in English, so once I'm operating Windows, I have no issues, but boot options are a nightmare.

I tried to install after having selected Japanese as the Ubuntu language, thinking it was just a formatting issue which I could reassign after installation, but the problem persists.

Knowing next to nothing about Linux, my theory is: I need to perform a partition, since all of this is being done at the best of the WINDOWS Boot Manager, a tyrant I may not have to deal with if it were resigned to its own insulated hive. Unfortunately, I have no idea how.

Maybe there is a general fix somebody knows of regarding installing Ubuntu on computers with stubborn language settings or region-coding issues?

Errors encountered while trying to install from a Live USB entail a separate set of error messages, which I would be happy to try and translate here if you think it is a better option.

Cheerio and muchas gracias,
s

---

### Post by evilishan on 2012-09-29
No.1 thing I would do would be to try and find an option for the English language under bios during bootup. Sorry if it seems kinda obvious just double checking..

If that doesn't fix the startup of Ubuntu from GRUB4DOS, I believe the best option would be to try and reinstall using the Windows Installer (WUBI) and perhaps use English as the primary language (additional language options can be installed later anyways).

If niether of these options are of any help It would be awesome if you could get a screen of the error message that comes up when you try to load Ubuntu. I maybe be able to provide further assistance.

---

### Post by newb85 on 2012-09-29
Try installing from a Live USB, selecting English.

---

### Post by mips on 2012-09-29
You could always try flashing the bios to a english version if you can't manually change the language.

---

### Post by salmonberger on 2012-09-29
> **evilishan said:**
> No.1 thing I would do would be to try and find an option for the English language under bios during bootup. Sorry if it seems kinda obvious just double checking..

If that doesn't fix the startup of Ubuntu from GRUB4DOS, I believe the best option would be to try and reinstall using the Windows Installer (WUBI) and perhaps use English as the primary language (additional language options can be installed later anyways).

If niether of these options are of any help It would be awesome if you could get a screen of the error message that comes up when you try to load Ubuntu. I maybe be able to provide further assistance.

Well, the bios screens are in English, so thats not a problem - the Japanese is from the Windows Boot Manager that solicits my selection of which OS to boot from:

1: Windows 7
2: Ubuntu

If 1, everything boots normally. If 2, I get the aforementioned instructions, plus:

File: \ubuntu\winboot\wubildr.mbr
State(condition): 0xc0000098

Can't get screen captures from prior to OS boot up, but will take a digital photo if you think it might help (its in Japanese, though).

Cheers!
s

---

### Post by salmonberger on 2012-09-29
Based on the steps the Boot manager asks me to take in my first post, it seems it is taking issue with the language interface of the Ubuntu installer, but this strikes me as odd since Japanese is available as a language from the installer itself (which I have tried selecting prior to initial restart).

I mean, the PC was bought in Japan with a pre-installed Windows 7, and I'm attempting to install a version of Ubuntu which claims to be perfectly compatible with Japanese language settings. Not sure why the hiccup...

---

### Post by newb85 on 2012-09-29
If you install from a Live USB, selecting English, it should replace Windows' boot manager with GRUB.

---

### Post by salmonberger on 2012-09-29
> **newb85 said:**
> If you install from a Live USB, selecting English, it should replace Windows' boot manager with GRUB.

With my Live USB inserted, the boot menu gives me three options:

1. Windows Boot Manager
2. UEFI: TDK MediaTF 250 Drive
3. TDKMediaTF 250 Drive

If I assign UEFI: TDKMedia or TDK Media (my USB) to #1, then try to save and exit, I am told the following:

"Reboot and select proper boot device or insert boot media in selected boot device and press a key."

From here, any key I press gives me the same message, so I'm forced to do a manual shutdown.

How else can I get far enough into the installation to choose English?

Thanks in advance,
s

---

### Post by critin on 2012-09-29
It's possibly something to do with UEFI. hopefully you can find some answers here.

[http://ubuntuforums.org/showthread.php?t=2003442](http://ubuntuforums.org/showthread.php?t=2003442)

---

### Post by salmonberger on 2012-09-29
Solved. Thanks all.

---

### Post by mips on 2012-09-29
> **salmonberger said:**
> Solved. Thanks all.

Might help others if you shared the solution ;)

---

### Post by critin on 2012-09-29
Yes, please tell how you solved it to help others with the same problem!   That's how the forums become helpful!!

---

### Post by gmaninvan on 2012-10-27
Yes, please. I would really like to know how to solve this. I heard it is because the UX31A uses UEFI instead of an MBR. I decided to give Windows 8 a try in the meantime but it is pretty much polishing a terd. I am going back to linux with Gnome 3 so please tell me how to get this going!! I want my dual boot that I had on my old laptop.

---

