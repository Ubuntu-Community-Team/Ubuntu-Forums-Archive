---
title: "Modify php.ini in php5 package"
date: 2010-10-07
forum: Packaging and Compiling Programs
---

### Post by sander3 on 2010-10-07
Hi.

I have modified the ubuntu php5 package.

I have deleted mysql an mssql suport and also some php things, like tidy, i don't need.

So, the packaging went fine. That's not the problem.

The problem is that the php.ini file which is created when I install the php5 package, still contains lines about mysql and mssql. And also, I want to add some lines and modify some settings.

So, I want to modify it, so, that when I install my customized package, the changes are already in the php.ini file.

Can someone explain to me how I can do this? 

I already found a patch, called: 029-php.ini_paranoid.patch

But as I am a beginner with packaging, I don't know how I can edit this.

I mean, is it safe to just use vim and modify this file? Or do i have to use quilt? Or do i have to create an own patch?

I have no idea, and I hope that someone can help me.


Thanks.

---

### Post by sander3 on 2010-10-10
Anyone able to help me with this?

---

