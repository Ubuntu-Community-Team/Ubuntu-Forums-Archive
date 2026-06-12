---
title: "Drive 2 is under media and is treated as a removable drive"
date: 2021-10-15
forum: New to Ubuntu
---

### Post by imthetrashmammal on 2021-10-15
Hi! I just installed Ubuntu today and immediately replaced windows, and did no additional prep work for this (I went in blind).
It was going great until i realized my 2nd drive could not be found in the files when trying to create a new file download path for steam. The main drive is a 1tb Nvme SSD also mounted straight on the board. 
How can i make the drive a system drive? Its a 500 gb NVME SSD mounted right on the board that i re-partitioned to the linux file system, which i thought would make it a system drive.

---

### Post by psychohermit on 2021-10-16
You need to make an /etc/fstab entry for it. Make a directory to mount it to and specify that directory in fstab.

--glenn

---

### Post by Impavidus on 2021-10-16
Your filemanager can mount whatever filesystem it finds and will do so in /media. It treats removable filesystems and internal ones in the same way. The solution is to make an entry for this second drive (or rather, the filesystems on it) in your /etc/fstab configuration file. When you have done so, the file manager will no longer list it as a removable drive, but it will be automatically mounted at boot time at a directory of your choice.

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

