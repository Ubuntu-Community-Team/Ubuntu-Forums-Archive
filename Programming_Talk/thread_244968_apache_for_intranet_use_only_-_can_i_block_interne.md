---
title: "apache for intranet use only - can i block internet access?"
date: 2006-08-27
forum: Programming Talk
---

### Post by pulper on 2006-08-27
I'm still in the process of trying out a number of Linux programming languages briefly before i decide on which to learn first.  i'm trying PHP now and have a simple question.

I want to set up Apache/PHP/Mysql on my home computer running Ubuntu. Is there anything specific i have to do to the apache configuration so that this is only used for INTERNAL development of programs, and the webserver cannot be seen/accessed from the internet?

Thanks,

Paul

---

### Post by amo-ej1 on 2006-08-27
offcourse it is for example possible to have it only listen on the localhost interface instead of the interface (eth0 probably) connected to the internet. 
Or you could use htaccess on the directory where you wish to play around and keep a part public and a part private ... you could even use iptables to lock out all traffic except the one from the host yoru are on ... so there are a lot of paths to choose but all depend on your specific situation.

---

### Post by indytim on 2006-08-27
pulper,

Check this link as I think it will provide what you are looking for in the security section.

[https://help.ubuntu.com/community/ApacheMySQLPHP#head-967a645a6dc898f3e00c3dc7063c6949a4957d52]("https://help.ubuntu.com/community/ApacheMySQLPHP#head-967a645a6dc898f3e00c3dc7063c6949a4957d52")

Good Luck,

IndyTim

---

### Post by pulper on 2006-08-27
Indytim, your link is exactly what i was looking for.  precisely!  thanks.

btw, you have a packers symbol buy your nickname is indytim??  what gives??

Paul

---

### Post by indytim on 2006-08-27
Born and raised and spent the better part of my adult life in WI.  It's sorta like a birth-rite... once a Packer fan, it never leaves you. Even though our local team down here will probably do a whole lot better than the Pack (assuming the "locals" don't choke on their own reputation again this year ](*,) 

IndyTim

---

