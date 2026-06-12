---
title: "Boot problem - switching from Ubuntu 11.10 to XP"
date: 2012-06-23
forum: New to Ubuntu
---

### Post by GxEnomics on 2012-06-23
I've tried and tried to resolve this problem but everything I've attempted only temporarily resolves the issue. I can restart Ubuntu over and over but if I run XP and close it down my machine gets stuck in a loop at the first start up menu (ie where the F2 & F12 options are displayed)
 
I've repeatedly tried Disk-Repair off a USB and through the terminal, but the boot problem happens once again when I run XP. I just gave Grub Customizer a go, and while it shifted the XP listing from the bottom to the top of the start up screen, it too failed to resolve the boot problem. 
 
What should I do next?

---

### Post by U202E on 2012-06-23
a reboot loop is a typical windows xp problem, you could do this:

[LIST]
[*]use a** live cd**/**ubuntu partition** to make a **backup.**
[LIST]
[*]then** reinstall xp** with a cd (and recover GRUB2)
[/LIST]
[*]run in** safe mode** with command prompt, open **cmd** and type **sfc /scannow**
[*]run a file system check, maybe your hdd is damaged. (live cd  is handy)
[/LIST]

---

### Post by GxEnomics on 2012-06-23
> **U202E said:**
> a reboot loop is a typical windows xp problem, you could do this:

[LIST]
[*]use a** live cd**/**ubuntu partition** to make a **backup.**
[LIST]
[*]then** reinstall xp** with a cd (and recover GRUB2)
[/LIST]
[*]run in** safe mode** with command prompt, open **cmd** and type **sfc /scannow**
[*]run a file system check, maybe your hdd is damaged. (live cd is handy)
[/LIST]
 
Thanks U202E. I'll have to try and track down a CD copy of XP.
 
If my current problem is linked to XP, and assuming the HDD isn't damaged, which alternative option should I try: Virtual Box or WUBI?

---

### Post by anewguy on 2012-06-23
You could also just boot Ubuntu and try the following in a terminal window:

sudo update-grub

No guarantee it will fix your problem, but it may just be a problem in the way grub got configured.

This would be a lot faster to try than trying to reinstall Windows - I would use that as the fall back plan - which you may need to use anyway - but try the update-grub first.

---

### Post by GxEnomics on 2012-06-23
> **anewguy said:**
> You could also just boot Ubuntu and try the following in a terminal window:
 
sudo update-grub
 
No guarantee it will fix your problem, but it may just be a problem in the way grub got configured.
 
This would be a lot faster to try than trying to reinstall Windows - I would use that as the fall back plan - which you may need to use anyway - but try the update-grub first.
 
Yep already tried it but I'm happy to give it another go.

---

### Post by oldfred on 2012-06-23
Are you running any DRM Digital Rights Management Software in XP or some game with DRM.

There was an old issue with grub2 being large than grub legacy. Grub also uses the space after the MBR for more code and some Windows software also hid serial numbers in that same space creating grub issues. This was more an issue with Windows 7.

Grub2 created a work around for this one.
Flexnet in Boot area (DRM "rights"/security)

Some vendor apps also write into the same area.
HP ProtectTools, Dell Recovery, flexnet and a few others write into MBR area.

---

### Post by GxEnomics on 2012-06-24
Installing Ubuntu 11.10 with wubi has fixed the boot problem. The issue isn't totally resolved though as I now get the following error message: 
 
                    windows_root\System32\Hal.dll missing or corrupt:

                   Please re-install a copy of the above file. 
 
Oh well, the current dual boot set up is definitely more workable than before.

---

### Post by oldfred on 2012-06-24
The missing hal.dll is almost never a missing file but issues with other files. First check boot.ini to see if it matches the partition it is in.

Fix WinXP hal.dll 
[http://ubuntuforums.org/showthread.php?t=1410696](http://ubuntuforums.org/showthread.php?t=1410696)
Missing hal.dll not always missing, but other errors or boot.ini wrong partition
[http://members.iinet.net.au/~herman546/p15.html#hal.dll_is_missing_or_corrupt](http://members.iinet.net.au/~herman546/p15.html#hal.dll_is_missing_or_corrupt)
[http://pcsupport.about.com/od/findbyerrormessage/a/missinghaldll.htm](http://pcsupport.about.com/od/findbyerrormessage/a/missinghaldll.htm)

---

### Post by GxEnomics on 2012-06-24
> **oldfred said:**
> The missing hal.dll is almost never a missing file but issues with other files. First check boot.ini to see if it matches the partition it is in.

Fix WinXP hal.dll 
[http://ubuntuforums.org/showthread.php?t=1410696](http://ubuntuforums.org/showthread.php?t=1410696)
Missing hal.dll not always missing, but other errors or boot.ini wrong partition
[http://members.iinet.net.au/~herman546/p15.html#hal.dll_is_missing_or_corrupt]("http://members.iinet.net.au/%7Eherman546/p15.html#hal.dll_is_missing_or_corrupt")
[http://pcsupport.about.com/od/findbyerrormessage/a/missinghaldll.htm](http://pcsupport.about.com/od/findbyerrormessage/a/missinghaldll.htm)

Thanks oldfred! 

I'll check out those links and keep chipping away at the problem.

---

