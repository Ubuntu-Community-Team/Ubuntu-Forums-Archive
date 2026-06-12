---
title: "Help Needed During Installation"
date: 2008-11-29
forum: New to Ubuntu
---

### Post by rdusewicz on 2008-11-29
I would like to be a Ubuntu user and am trying to install using a CD that was provided through MediaMotion (Canonical).  I have a Dell Latitude and have set it to install off the CD Drive.
Everything went fine for awhile.  Then I received the following message several times with different numbers:
[333.591437] aufs au_xino_do_write :242 :apport[5893] : I/O Error , write failed (-28)

This was the first of 8 errors listed.  Any ideas on what is wrong and how I can right it?

Thanks,

Russ

---

### Post by Olivier2371 on 2008-11-29
Hello there, and Welcome,

Have you tried to use the live option first?

---

### Post by paultag on 2008-11-29
> **rdusewicz said:**
> I would like to be a Ubuntu user and am trying to install using a CD that was provided through MediaMotion (Canonical).  I have a Dell Latitude and have set it to install off the CD Drive.
Everything went fine for awhile.  Then I received the following message several times with different numbers:
[333.591437] aufs au_xino_do_write :242 :apport[5893] : I/O Error , write failed (-28)

This was the first of 8 errors listed.  Any ideas on what is wrong and how I can right it?

Thanks,

Russ

Odd. It looks like the initrd is bombing on startup. If you could log all of the errors and file a bug on Launchpad, that would be great!

( read, you did nothing wrong )

Thank You,
Tag

---

