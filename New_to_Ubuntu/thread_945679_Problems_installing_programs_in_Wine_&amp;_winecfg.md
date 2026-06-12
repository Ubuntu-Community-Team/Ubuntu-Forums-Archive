---
title: "Problems installing programs in Wine &amp; winecfg Locked"
date: 2008-10-12
forum: New to Ubuntu
---

### Post by NoJobyDesert on 2008-10-12
I installed Wine, and confirmed that it is working.
I now have 2 problems.
First, when I try to run winecfg I get this:
> pja1992@Ubuntu-Desktop:~$ sudo winecfg
Password:
wine: /home/pja1992/.wine is not owned by you

Second, When trying to install a program in wine...
> pja1992@Ubuntu-Desktop:~$ wine /cdrom/setup.exe
Nothing happens. I then run the same command except beginning with "sudo", and it tells me that folder ".wine" is not owned by me.

How do I make the ".wine" folder un-restricted?

I am using Dapper.

---

### Post by jamesrl on 2008-10-12
can you try just normal winecfg (no sudo)?

---

### Post by jamesrl on 2008-10-12
and your cdrom drive is more likely /media/cdrom so try ```
wine /media/cdrom/setup.exe
```

---

### Post by jamesrl on 2008-10-12
The heart of the issue seems to be that wine is installed in a sub-directory of your home directory, so you do not need root privileges to configure wine settings (whereas you would if it was located in say /usr/local or something).  Wine pays enough attention to things, to say hey you are trying to modify wine settings of another user so prevents you from doing so (though with sudo -u username you can pretend to be that other username if you really wanted to).

---

