---
title: "Error: no such partition. Entering resuce mode"
date: 2014-05-15
forum: New to Ubuntu
---

### Post by joshua_gremo on 2014-05-15
Hello everyone,

   Last night for last time I tried dual booting linux with windows 8. I follow this guide that said to switch from UEFI to CSM and see if that works. It didn't, so I just wiped the linux partition and decided to stay with windows. Forgot to change the CSM back and now I'm completely stuck in "error: no such partition. Entering rescue mode....grub rescue>".

I have searched the net for a fix but nothing works. I can't boot from the livecd to try and install or atleast repair it. I can't boot windows recovery disks. USB doesn't work. Not sure what to do at this point. I have a laptop that is useless right now. If I turn the comp off then on hitting F2 i get the bios, but its all greyed out and can't hit return to default. 

Thanks for any help, its greatly appreciated.

---

### Post by oldfred on 2014-05-15
Sometimes a full cold boot works, so you can get into UEFI/BIOS.

Turn off computer, remove battery and hold power switch for a few seconds to drain capacitors.

Then see if you can get into UEFI/BIOS?

---

### Post by joshua_gremo on 2014-05-15
Got it into GNU Grub. Should I restart and set my boot order to my dvd drive and reinstall ubuntu? Then uninstall it the proper way? I'd love to use it for a while since im on summer break, only during the semester do I need to use windows. I have a full backup of my windows. If I attempt another install should I just have Ubuntu wipe the windows OS?

---

### Post by oldfred on 2014-05-15
Currently there seems to be a bug in the description of the reinstall screen. And since just description they do not really consider it a bug they will fix.
Reinstalling Ubuntu with any auto option may show over write Ubuntu not mentioning Windows. And then just erase entire drive.
Best to use Something Else and choose the Ubuntu / for the install of a new / partition.

If Windows is UEFI, best to install Ubuntu in UEFI mode. 
See link in my signature for some of the issues. :)

---

### Post by joshua_gremo on 2014-05-15
Thank you for the help! : )   Im doing a windows MBR repair now, gunna back it up once more then uninstall windows and install ubuntu to see how i like it. Do i click "best answer or solved ?"

---

