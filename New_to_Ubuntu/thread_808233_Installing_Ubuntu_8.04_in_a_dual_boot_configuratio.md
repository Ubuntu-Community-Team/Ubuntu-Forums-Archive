---
title: "Installing Ubuntu 8.04 in a dual boot configuration"
date: 2008-05-26
forum: New to Ubuntu
---

### Post by xie_jiabao on 2008-05-26
Hi All,

I am taking the plunge and installing Ubuntu 8.04 on an Intel Core2 duo system with Windows vista (32 bit). I intend to install the 64 bit Ubuntu OS in dual boot configuration. But I would like a few clarifications before doing this.

a)What is the easiest way of running 32 bit applications once I install Ubuntu 64 bit?

b) Must I use the 64-bit PC (AMD64) alternate install CD [and not the 64-bit PC (AMD64) desktop CD] in order to create a dual boot machine?

c) What is the minimum number of partitions I must create, and in general, how large should these be? I have roughly 60gb of disk space available and I have a 2 gb RAM.

Thanks in advance,
Xie

---

### Post by Duck2006 on 2008-05-26
This may help.

[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm)

---

### Post by louieb on 2008-05-26
Welcome.
b) either can bet used to setup a dual boot PC. (please be careful and read each page or you could wind up with a Ubuntu only machine).  Doesn't bother me but some people get upset when they find the devil they know is gone.  

c)  just need 1 for / (root). unless you plan to hibernate. Then you'll want a swap partition about the the same size or a little larger that the amount of ram you have. 
Although  you just need one partition. Using more that one has it advantages. Just a suggestion. 

[LIST]
[*]/ (root) 5-7GB
[*]/home  4-5GB  for user configuration files. Nice to have if you need to reinstall for some reason.
[*]swap  half a gig is plenty (unless you hibernate).
[*]/data keep all you music, photos, etc here. Handy to keep your data out of the way come upgrade, or reinstall time. Also makes backups much simpler.
[/LIST]
Setting up dual boot isn't that hard but its scary if you haven't done it before. The **psychocats** and **dual boot** links in my signature have good overviews of useing the Ubuntu CD to set up a dual boot PC.
Good Luck.
lou

---

