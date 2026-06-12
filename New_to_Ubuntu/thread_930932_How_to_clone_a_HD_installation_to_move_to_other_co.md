---
title: "How to clone a HD installation to move to other computer"
date: 2008-09-26
forum: New to Ubuntu
---

### Post by Sudan on 2008-09-26
I'm a newbie running Hardy Heron.  I need to buy a new computer.  I want to transfer my hard drive as it is now exactly setup to the new computer.  Since I installed Hard Heron, I've done a lot of updates and installed applications, excuse me, packages (I think that is term).  

Can this be done?  What software should I use to do this?  I have an external USB HD plugged in with plenty of space on it.  Can the clone file(s) be written to the USB HD?

Also I have the current computer setup to dual boat Win XP.  I don't have need to clone that virtual HD.

I will not have physical possesion of both current and new computer at the same time.  So I need to make the clone or backup or mirror of the current computer HD to the external USB HD.

Thanks

---

### Post by Sef on 2008-09-26
Check out [Clonezilla]("http://clonezilla.org/") and [Partimage]("http://www.partimage.org/Main_Page").

---

### Post by pyromanic123boom on 2008-09-26
Keep the new harddrive and switch it to master in your new computer, and put the other one as slave. What I mean is, keep your existing hard drive for what is is, and use the new hard drive as storage.

---

### Post by bumanie on 2008-09-26
Would look at dd commands if I were you. > dd if=/dev/sda of=/dev/sdbYou would have to insert the names of your hard drives, but this will make an exact copy from one drive to the other. Do some pre-reading about dd.

---

