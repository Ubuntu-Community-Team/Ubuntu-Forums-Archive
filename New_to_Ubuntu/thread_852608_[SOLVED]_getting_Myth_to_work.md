---
title: "[SOLVED] getting Myth to work"
date: 2008-07-07
forum: New to Ubuntu
---

### Post by Ducatiboy Stu on 2008-07-07
I dowloaded the myth front and back end apps onto my laptop, along with mythbuntu control cent

Basically I am wanting to test out the look and feel before moving to a dedicated PC. 

Note I will only be using it for playing stored music/movies

When I run either the front or back end, the first screen i get is "No Upnp backends found"...then after the next screens I get " cannot log onto database"

Now I figure that it is to do with mysql...but I cant fine where/how to set it up...


I know the prob is simple, but I cant seem to work it out

---

### Post by wolfen69 on 2008-07-07
when i built my myth box, i started with regular ubuntu and installed mythtv on top of it. i could never get it to work right. then i installed [Mythbuntu]("http://cdimage.ubuntu.com/mythbuntu/releases/8.04/release/") (it's basically xubuntu with myth pre-installed) and added ubuntu-desktop.(i prefer gnome) and got it to work perfectly. think about trying that approach.

---

### Post by fenian on 2008-07-07
Try running this command...

> sudo dpkg-reconfigure mythtv-database

---

### Post by tagra123 on 2008-07-07
fenian's command may work 

I had some permissions trouble when setting mine up too I ended up using phpmyadmin to manually set permission the way I wanted to get it to work.

Here's a thread that may help.

[http://ubuntuforums.org/archive/index.php/t-287844.html](http://ubuntuforums.org/archive/index.php/t-287844.html)

also google for 

mythtv db permissions
mythtv db phpmyadmin
mythconverge permissions

---

### Post by Ducatiboy Stu on 2008-07-08
> **fenian said:**
> Try running this command...

Yes this worked.

Thanks

---

