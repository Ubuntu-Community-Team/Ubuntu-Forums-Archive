---
title: "[SOLVED] Unable to mount my SD card"
date: 2008-10-23
forum: New to Ubuntu
---

### Post by Aedes on 2008-10-23
Hello folks.  I just installed Ubuntu-eee as an opportunity to learn my way through a full blown Linux operating system.  I've got a little experience with Linux based systems but this is my first dedicated machine.  
While using the live disk I had no problem opening my SD card, but after installing when I try to open it I get a "Cannot mount volume: Must be superuser to mount." error message.  Through the GUI I found the Authorizations section and set the implicit authorizations for the "Mount file systems from removable drives" to yes thinking that would do the trick without any luck. How would I get the system to automatically mount removable media?  Terminal commands would be preferable ("sudo apt-get install" is such a wonderful gateway drug into the terminal).

---

### Post by Yoke &amp; Chung on 2008-10-23
Are you using it on an eee PC?

---

### Post by Hexagoon on 2008-10-23
Discovered the same problem yesterday, feels like a bug only in ubuntu eee. The solution however, is to create a folder like /media/sd and then mount the memory as root in the terminal.

```
sudo mkdir /media/sd
sudo mount /dev/sdb1 /media/sd
```

Then you can browse to /media/sd in nautilus and use the files... Seems like the only way right now :/

---

### Post by panhandle on 2008-10-23
This is a known problem.

Start here:

[http://ubuntuforums.org/showthread.php?t=931755](http://ubuntuforums.org/showthread.php?t=931755)

Also try the eee boards, though I have seen users there referring others to this site.

---

### Post by Aedes on 2008-10-23
> **Yoke & Chung said:**
> Are you using it on an eee PC?
Yes, I'm using a eeePC 900A.

> **Hexagoon said:**
> Discovered the same problem yesterday, feels like a bug only in ubuntu eee. The solution however, is to create a folder like /media/sd and then mount the memory as root in the terminal.

```
sudo mkdir /media/sd
sudo mount /dev/sdb1 /media/sd
```

Then you can browse to /media/sd in nautilus and use the files... Seems like the only way right now :/

> **panhandle said:**
> This is a known problem.

Start here:

[http://ubuntuforums.org/showthread.php?t=931755](http://ubuntuforums.org/showthread.php?t=931755)

Also try the eee boards, though I have seen users there referring others to this site.

This did the trick.  Thank you both very much.

---

### Post by panhandle on 2008-10-23
You're welcome. Happy to hear it worked out for you.

---

