---
title: "Admin Group vs Sudoer List"
date: 2008-06-06
forum: New to Ubuntu
---

### Post by rossom on 2008-06-06
So I used Likewise Open to bind to Active Directory.  In order to use sudo I added a group to the sudoer list.  Does this basically make them an administrator of the linux box?  What would change if I just added the AD group to the linux Admin group?

---

### Post by Oldsoldier2003 on 2008-06-06
> **rossom said:**
> So I used Likewise Open to bind to Active Directory.  In order to use sudo I added a group to the sudoer list.  Does this basically make them an administrator of the linux box?  What would change if I just added the AD group to the linux Admin group?

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo) gives a basic overview of sudoers but there are many more advanced uses.
By editing sudoers you can give certain groups limited sudo access- IE allowing them to only run certain commands that would not normally be available to them but are essential to their day to day business. This means they can do the things they need *without* becoming an administrator.

[http://www.debian-administration.org/articles/33](http://www.debian-administration.org/articles/33) is a nice walkthrough that shows you the flexibilty of sudoers there are more complete tutorials out there but this should get you on track.

---

