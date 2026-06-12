---
title: "svnserve on login?"
date: 2008-05-22
forum: New to Ubuntu
---

### Post by Ansible on 2008-05-22
I would like this command to run when I log in to ubuntu:

svnserve -d -r /home/username/svnrepository

After I log in to ubuntu I can type that in the terminal and then I can access the svn repository from my windows machine.  I tried putting this into 

.bash_profile
.bash_login

But that doesn't work.  I also tried installing openbsd-inetd and using that, but tortoisesvn on windows gets a "malformed data" or something like that.  I used this page as a reference for the inetd method:

[http://kennethfinnegan.blogspot.com/2007/06/my-ubuntu-setup.html](http://kennethfinnegan.blogspot.com/2007/06/my-ubuntu-setup.html)

At this point I just want to know how to run a script automatically when I log into ubuntu.

---

### Post by garyedwardjohnston on 2008-05-22
Why not set it up as a start-up service in System > Preferences > Sessions?

---

### Post by Ansible on 2008-05-22
I guess because I had no idea that existed?  Works like a charm, thx.

---

### Post by garyedwardjohnston on 2008-05-22
"I love it when a plan comes together."

- The A-Team

---

