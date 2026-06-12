---
title: "How to mount windows partition on startup?"
date: 2008-10-30
forum: New to Ubuntu
---

### Post by gnuvistawouldbecool on 2008-10-30
I would guess that i should edit fstab or similar, as that is where it is stored, but I would expect there is a program that can do it somewhere.  in the past i have used Mandriva, and in that it was a very simple matter to load diskdrake and do it and it would take all of about 5 seconds to do, but what program can I use in Ubuntu?  I looked at Gparted, but it doesn't seem to be able to do what I want to do.

I forgot to do this during the install, so I am wondering how to do it now.

---

### Post by em4r1z on 2008-10-30
While I'd use fstab (to have more control over the mounting options), you might want to try NTFS Configuration Tool.
Read this [http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by echo.whoami on 2008-10-30
The only gui tha will do your job is storage device manager. You can find it in applications->Add/Remove-> and then type in the search bar "storage device manager".

---

### Post by gnuvistawouldbecool on 2008-10-30
> **em4r1z said:**
> While I'd use fstab (to have more control over the mounting options), you might want to try NTFS Configuration Tool.
Read this [http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

It worked, thanks.

The other thing, the storage device manager one, seemed more complicated, but thanks anyway.

---

