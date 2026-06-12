---
title: "Ubuntu 11.10 requiring external drive present on startup"
date: 2011-11-17
forum: New to Ubuntu
---

### Post by Psyrus on 2011-11-17
Hi,

I am running Ubuntu 11.10 on a Dell Latitude E5510. I use an external drive on a daily basis. A few days ago Ubuntu began searching for this external drive on startup. Bootup is paused with a message saying it is waiting for the drive, giving me the option to skip the mount or try to mount it manually. Booting continues normally once I've plugged the drive in. If I skip the mount request, I receive an error when I try to plug the drive in later.

Does anyone have any idea what would cause this? The only change I have made is to install the NTFS Config Tool because I was suddenly unable to write to the drive (maybe due to an Ubuntu update?).

---

### Post by wolfen69 on 2011-11-17
[https://help.ubuntu.com/community/Grub2#Reinstalling_GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling_GRUB2)

---

### Post by Mark Phelps on 2011-11-17
Don't use the NTFS Config tool, so I don't know for sure, but my guess would be that the drive got added to your fstab file.

Open a terminal and enter "gksudo gedit /etc/fstab".  That will open your fstab in read-write mode.  If the external drive is listed in there, remove that line, save the file.

Then, in the same terminal, enter "mount -a".  That will remount your drives. You should not get an error message anymore.

---

### Post by coffeecat on 2011-11-17
> **Psyrus said:**
> Does anyone have any idea what would cause this? The only change I have made is to install the NTFS Config Tool because I was suddenly unable to write to the drive (maybe due to an Ubuntu update?).

I agree with Mark Phelps not to use ntfs-config. It's been unmaintained for years and can do strange things. 

About not being able to write to a NTFS drive - this is almost certainly because you have lost the package ntfs-3g, which is the ntfs read-write driver. You mention an update and some people report losing ntfs-3g after an update, but it's more likely to have happened if you installed the package ntfsprogs or installed all the suggested dependencies for Gparted.

Re-install ntfs-3g. This will remove ntfsprogs if you have installed this, but this does not matter since the version of ntfs-3g in 11.10 includes the functionality previously supplied by ntfsprogs.

---

### Post by Psyrus on 2011-11-18
Thanks for the replies! I had started looking down the fstab route(the drive is definitely listed), but I wasn't too sure if it should be there, if the parameters were correct, or if it shouldn't be there at all. I think the NTFS config tool probably made that entry. I will remove the config tool, ensure that ntfs-3g is present/re-install ntfs-3g. Will report my progress a little later.

---

### Post by Psyrus on 2011-11-18
That seems to have sorted it out. I un-installed the NTFS config tool, re-installed the ntfs-3g package, removed the external drive from fstab. Booting now no longer requires the presence of the external drive, and I can write to the external normally again.

Thanks for all the help. Use Linux if you want to learn something new everyday! :p

---

