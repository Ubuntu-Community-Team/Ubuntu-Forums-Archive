---
title: "Web based School Information System"
date: 2008-01-20
forum: Programming Talk
---

### Post by mitchi on 2008-01-20
Hi! I'm trying to set-up a web-based system for our school using Linux Apache/MySQL/PHP, and I would like to ask for your ideas.

There's centre-sis and focus-sis but they're postgresql based. I would prefer using MySQL.

Also, I would to ask about printing reports and forms from my system. I haven't tried this before and it would be very helpful if you could list down some tips or tricks on how to do this.

Thank you.

---

### Post by pmasiar on 2008-01-20
Most decently written web based apps can run on multiple databases - framework ensures that. Are you sure that yours require postgres? Even if they do, porting them to MySQL might be simpler than writing them from the scratch - and simpler to build supporting community too. This is assuming that functionality of centre-sis and focus-sis is exactly what you want - you did not commented on that.

Another source of info might be edubuntu: they are specialized on schools.

You might not be aware that state Illinois in USA is switching all schools to Linux, they might have some projects which you can join.

If you despite my advice decide to go alone and create your apps from scratch, School Information System is not too different from any other X Information System, for wide range of X. All the standard comments about PHP-based web apps apply (simpler deployment, messy unmaintanable code etc). Just check archives, or maybe some good gnome will link it for you - or even you can do it :-)

---

