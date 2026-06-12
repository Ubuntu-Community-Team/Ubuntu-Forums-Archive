---
title: "Ubuntu 23.04 - Sudo Update Lunar issue"
date: 2023-07-17
forum: New to Ubuntu
---

### Post by profeandresfajardo on 2023-07-17
When I try to update always apperas this message, but I try to remove on Sotware && Updates but always reapers, I have installed Ubuntu 23.04

sudo apt update
Get:1 file:/cdrom lunar InRelease
Ign:1 file:/cdrom lunar InRelease
Get:2 file:/cdrom lunar Release
Err:2 file:/cdrom lunar Release
  File not found - /cdrom/dists/lunar/Release (2: No such file or directory)
Hit:3 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lunar InRelease
Hit:4 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lunar-proposed InRelease
Reading package lists... Done
E: The repository 'file:/cdrom lunar Release' no longer has a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: [http://archive.ubuntu.com/ubuntu/dists/lunar/InRelease:](http://archive.ubuntu.com/ubuntu/dists/lunar/InRelease:) Key is stored in legacy trusted.gpg keyring (/etc/apt/trusted.gpg), see the DEPRECATION section in apt-key(8) for details.
W: [http://archive.ubuntu.com/ubuntu/dists/lunar-proposed/InRelease:](http://archive.ubuntu.com/ubuntu/dists/lunar-proposed/InRelease:) Key is stored in legacy trusted.gpg keyring (/etc/apt/trusted.gpg), see the DEPRECATION section in apt-key(8) for details.

---

### Post by Bashing-om on 2023-07-17
hello profeandresfajardo - Welcome to the Forums :D

Check in the GUI software sources app that the CD is not enabled.
Looks as if the system is looking for that install CD, that of course is not available.

[INDENT]could be Yes
[/INDENT]

---

### Post by guiverc on 2023-07-17
The CDROM refers to your installation media.

If using a GUI or Desktop system, you can enter *Software and Updates* and uncheck the box for your installation media and it'll stop being used as a resource (*until re-enabled if you'd ever want to do that*).

If using a text or server system, you can just edit your sources to exclude that; adding a "#" at the start of the line will *disable* it (what the GUI checkbox does).

The main sources file is /etc/apt/sources.list , but there is also a directory /etc/apt/sources.list.d that is scanned, but that directory is empty on a new install, so anything in it was added post-install by users with `sudo` privileges.

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

*You didn't mention if using 23.04 Desktop or 23.04 Server; so I've tried to speak generically.*

---

### Post by ActionParsnip on 2023-07-18
or, comment out the top few lines in the file
```

/etc/apt/sources.list

```

---

