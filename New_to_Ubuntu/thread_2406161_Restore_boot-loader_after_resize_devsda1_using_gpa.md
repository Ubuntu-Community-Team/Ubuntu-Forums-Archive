---
title: "Restore boot-loader after resize dev/sda1 using gparted"
date: 2018-11-16
forum: New to Ubuntu
---

### Post by zshan63 on 2018-11-16
Applogies i've been searching on google my solution and stackoverflow but could not found.
 
 
 Explanation:
 
 
 I was need to install windows alongside ubuntu16.04.
 I free up some space from my dev/sda1 (my ubunut was installed on this) using gparted from live usb.
 It was taking too much time around 40min plus. I intentially cancled operation and then restarted my laptop at this time the actual ubuntu was not loading in boot options of laptop.
 I then again run live usb ubuntu and tried to repair boot using Boot-Repair tool but that is giving me this message.
 
 
 **Please enable a repository containing the [grub-efi-amd64-signed] packages in the software sources of unknown Linux (sda1). Then try again.**
 
 
 unknown Linux (sda1)  is my ubuntu. I am not able to access it how can i enable grub*** on it?
 
 
 please help me
 
 
 
 
 [https://paste.ubuntu.com/p/ZVDjbcghY6/](https://paste.ubuntu.com/p/ZVDjbcghY6/)  Thanks

---

### Post by oldfred on 2018-11-16
Depending on what exactly gparted was doing, you may have totally corrupted install. You may have to reinstall and restore from your backups.
Generally you cannot interrupt partition changes.
But a simple shrink should not take a long time unless drive had other issues or shrink was too large, not leaving enough working room.

       May be best to see details, use ppa version with your live installer or any working install,  not older Boot-Repair ISO:
Please attach link to the summary report, the auto fix sometimes can create more issues.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

