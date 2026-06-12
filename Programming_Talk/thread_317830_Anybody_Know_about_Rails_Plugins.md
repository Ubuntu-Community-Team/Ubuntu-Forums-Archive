---
title: "Anybody Know about Rails Plugins??"
date: 2006-12-13
forum: Programming Talk
---

### Post by daz4126 on 2006-12-13
Hi,

I'm tryin to install the haml plugin for rails. It says that I have to run the following command:

./script/plugin install -x svn://hamptoncatlin.com/haml/trunk

When I do, I get the following message:

Cannot install using externals because this project is not under subversion.

I know absolutely nothing about subversion and can't find an easy guide online. Could anybody point me in the right direction about how to install this (or any) plugins?

thanks in advance,

DAZ

---

### Post by Blacktalon on 2006-12-13
Simiply to say you need your project to be a Subversion.  It is most likely you are using the default which is probably CVS, just change it to subversion and you should be ok. (Not to sure on how to change at the moment...finals week got me brain fried!!!)

Edit:
I did think of something I should probably have asked, have you done sudo gem install Subversion in your rails project?  If not give it a try its either that or sudo gem install svn  ........I think this will help.

Good Luck
~BT

---

