---
title: "Trying to get Ecplise - PHP to work"
date: 2009-07-27
forum: Programming Talk
---

### Post by edpatterson on 2009-07-27
Right area/site/forum?

I had used Eclipse for some java programming (learning) then moved to NetBeans. I then decided to try to add support for PHP. Turns out you can not use the Ubuntu package for Eclipse and the Zend PDT plug in. I removed the package, downloaded the .gz extracted it and moved it into the /usr/share directory.

I get the following error every time I try to make a project:
Build path contains duplicate entry: 'usr/shate/eclipse/plugins/
org.eclipse.php.core_2.10.v20090617-2341/Resources/language/php5' for
project testProject

Any ideas? I searched the Eclipse site and saw other complaints but they all related to Java, not PHP.

Thanks for any and all assistance.
Ed

---

### Post by Mirge on 2009-07-27
Download Eclipse PDT All-In-One from: [http://www.zend.com/en/community/pdt](http://www.zend.com/en/community/pdt)

It runs in its own directory, as usual... so you'll have 2 separate Eclipse versions, but it's the version I use (well, besides plugins I've added/modified) daily for PHP work.

---

### Post by edpatterson on 2009-07-27
> **Mirge said:**
> Download Eclipse PDT All-In-One from: [http://www.zend.com/en/community/pdt](http://www.zend.com/en/community/pdt)

It runs in its own directory, as usual... so you'll have 2 separate Eclipse versions, but it's the version I use (well, besides plugins I've added/modified) daily for PHP work.

That is exactly what I did. I went to do the 1st tutorial and got the error.

---

