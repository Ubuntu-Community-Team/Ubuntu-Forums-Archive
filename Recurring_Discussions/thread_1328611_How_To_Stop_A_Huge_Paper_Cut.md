---
title: "How To Stop A Huge Paper Cut"
date: 2009-11-16
forum: Recurring Discussions
---

### Post by booksnmore4you on 2009-11-16
Instead of having parts of a program thrown at /usr/bin, other parts at /etc and yet more parts thrown at /usr/share/something/or/another, each program gets its own directory tree, keeping them all neatly separated and allowing you to see everything that's installed in the system and which files belong to which programs in a simple and obvious way.   

~] cd /
/] ls
Programs
Users
System
Files
Mount
Depot

This is what [http://www.gobolinux.org/?page=at_a_glance](http://www.gobolinux.org/?page=at_a_glance) does and it would be a huge advantage for newly migrating Ubuntu users.  HUGE.

---

### Post by Tibuda on 2009-11-16
no, this is not a paper cut

---

### Post by NoaHall on 2009-11-16
It's really not a problem. It's perfect as it is. It stops newbies trying to delete programs from there.

---

### Post by Keyper7 on 2009-11-16
This is a huge and controversial change that requires careful planning.

Definitely not a paper cut.

---

### Post by running_rabbit07 on 2009-11-16
Then we can change their names to make them unrecognizable so that only Linux+ Certified people know what they are looking at.

No. 

Ubuntu's dev worries about quality of product, not having an organized files system for the new. The new can open a book or google and learn the system.

---

### Post by hoppipolla on 2009-11-16
> **booksnmore4you said:**
> Instead of having parts of a program thrown at /usr/bin, other parts at /etc and yet more parts thrown at /usr/share/something/or/another, each program gets its own directory tree, keeping them all neatly separated and allowing you to see everything that's installed in the system and which files belong to which programs in a simple and obvious way.   

~] cd /
/] ls
Programs
Users
System
Files
Mount
Depot

This is what [http://www.gobolinux.org/?page=at_a_glance](http://www.gobolinux.org/?page=at_a_glance) does and it would be a huge advantage for newly migrating Ubuntu users.  HUGE.

that is quite a bit simpler than the one used currently, but it's just not worth it, it wouldn't make any difference. And NoaHall is right, we don't want users deleting programs themselves from there, that would create problems.

It really is ok as it is, I can see what you're saying about the current system being confusing, but I really think there are far bigger issues and this would take a long time.

---

### Post by skatinjj on 2009-11-16
This is what windows does with the Program Files directory but it becomes an issue when users think by deleting the folder in Program Files it uninstalls the program when in reality it is still there, you just can not access it.

Just like above, I think ubuntu devs have a good way to prevent issues with users not properly uninstalling programs.

Plus, common users probably do not have a reason to know where the parts to a program are so long it works.

---

### Post by lisati on 2009-11-16
Hmmmmm. /me pauses for thought. There's probably advantages and disadvantages to any scheme for organizing where each of a package's components end up on a system.

On the rare occasions I do any programming these days, my own preference for small projects that I create just for my own use is to keep all the components in one place, perhaps organized into subdirectories for source, binaries, data, etc, as required, all within the one folder relating to that particular project.

For larger projects, more careful planning is a good idea, particularly if one is likely to scatter the different components around different parts of the systemm. In this situation some kind of uninstaller can be useful.

---

### Post by Chronon on 2009-11-16
> **lisati said:**
> 

For larger projects, more careful planning is a good idea, particularly if one is likely to scatter the different components around different parts of the systemm. In this situation some kind of uninstaller can be useful.

Shouldn't that all be tracked by a properly crafted .deb?

---

### Post by lisati on 2009-11-16
> **Chronon said:**
> Shouldn't that all be tracked by a properly crafted .deb?

You're right. Most (all?) of the the programming stuff I've done lately has been fairly trivial and didn't need the bells and whistles that a .deb package provides.

---

