---
title: "compiling router's firmware on Ubuntu"
date: 2009-08-04
forum: Programming Talk
---

### Post by boosta on 2009-08-04
hi everybody,
i'm new here, and i'm a newbie since my knowledges and skills are still limited.
i wanted to do something but i realized, by doing, that i'm not able to bring it to a positive result.

i wanted to compile these router's firware in order to run it on a x86 (Windows or Linux);
the router is a D-Link DI-524, it runs a Linix-based software on MIPS processor.

i don't need the compliling of the entire firmware, but ONLY this executable called "rgbin", which can be found in these archive's paths:
.\di524\userland\target\usr\sbin\rgbin
.\di524\progs.priv\rgbin\Makefile
.\di524\progs.priv\rgbin\rgbin

here's btw the source code archive:
[ftp://ftp.dlink.co.uk/GPL/DI-524_E1_GPL.tgz](ftp://ftp.dlink.co.uk/GPL/DI-524_E1_GPL.tgz)
or
[ftp://ftp.dlink.se/Products/di-products/di-524/drivers_firmware/di524.source.tgz](ftp://ftp.dlink.se/Products/di-products/di-524/drivers_firmware/di524.source.tgz)

i hope someone can lend me a hand in doing that.
i'd be very thankful.
Regards!

PS: i read this (old) news:
[http://digg.com/linux_unix/DLINK_Sweden_providing_a_LINUX_port_for_the_DI_524_ROUTER](http://digg.com/linux_unix/DLINK_Sweden_providing_a_LINUX_port_for_the_DI_524_ROUTER) 
but i wasn't able to find it on dlink.se site (also asked the support: vacation!)
maybe this? ...not sure
[ftp://ftp.dlink.se/Products/di-products/di-524/drivers_firmware/di524.source.tgz](ftp://ftp.dlink.se/Products/di-products/di-524/drivers_firmware/di524.source.tgz)


...Besides, i got a config.bin file, which i wanted to decrypt
it's MIPS binary: could it be disassemled and decoded ?

---

### Post by boosta on 2009-08-06
help please...:(

---

### Post by Vadi on 2009-08-06
Try the [http://ubuntuforums.org/forumdisplay.php?f=336](http://ubuntuforums.org/forumdisplay.php?f=336) subsection?

---

### Post by boosta on 2009-08-06
ok, i'll copy this thread in that section
if Mods want to delete this (to avoid crossposting), please do it
thanks

---

### Post by slavik on 2009-08-06
1. what language is the code written in?
2. that binary could depend on many other things
3. there might be mips assembly that needs to be assembled
4. please see gcc documentation for cross compiling
5. If you have a binary, you do not need to compile anything

---

