---
title: "Windows 10 can't see the SSD drive | from Ubuntu I can't access Windows files"
date: 2022-02-07
forum: New to Ubuntu
---

### Post by fizitinu on 2022-02-07
Hello. Can you tell me how to solve a problem?
Windows 10 can't see the SSD drive on which Ubuntu 20.04 is installed. 
And from Ubuntu sometimes I can't access Windows files. How can I fix it?

Windows 10 on HDD and Ubuntu on SSD.

---

### Post by Impavidus on 2022-02-08
Ubuntu must be installed on a Linux filesystem, usually ext4. Windows doesn't know about Linux filesystems. It only knows NTFS, fat and exFAT. That's why Windows cannot access the Ubuntu filesystem.

Ubuntu can access Windows filesystems, however, Windows has a feature known as Fast Startup. This is designed to hide that fact that Windows boots very slowly, by not really booting at all. Instead, Windows uses some hybrid of booting and hibernating. But when Windows does that, it doesn't cleanly unmount its filesystems and therefore Ubuntu cannot access the Windows filesystem (or only in read-only mode). So make sure Fast Startup is disabled. It may get enabled automatically during Windows updates.

BTW, when you access the Windows filesystem from Ubuntu, none of the safeguards to prevent damage to Windows work, so be careful. It's recommended to access only a data partition on Windows (something like "D drive" in Windows parlance, although not actually a drive), not the system partition (known as the "C drive").

---

### Post by Autodave on 2022-02-08
I don't know aht the size of your HDs are, but you could take the largest one and partition it to hold files that you wish to have available on either operating system.  Format that partition to a Windows system.  Then turn off Fast Boot or Fats Startup in windows.  That way, when Windows actually shuts down, the newly made partition will be available to Linux and Windows.  

Alternately, like I have here, add a third HD and use that for storage.

---

