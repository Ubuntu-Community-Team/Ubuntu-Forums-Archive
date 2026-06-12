---
title: "Ubuntu 12.04 Wireless Printer Connectivity"
date: 2012-05-08
forum: New to Ubuntu
---

### Post by afz12 on 2012-05-08
I have a hp dv6 notebook running Ubuntu 12.04 and an Epson Stylus NX430 wireless printer. There are 3 things, all or at least either that I'd like to achieve;

1. Print directly from Ubuntu 12.04 via cable - I have seen the printer install but it doesn't have any drivers. Behavior: continuous blank paper printing requiring restart. I've also installed Wine but the printer s/w doesn't want to install vis Wine.

2. If the cable connection can be made to work then I'd like to use it via wireless. This works fine with an older notebook running XP, but not with Ubuntu 12.04. Also, I tried to make a dual boot partition on this HP notebook but it failed to install - stopped half way with an unpleasant error screen.

3. I have XP virtualized on Ubuntu on this HP notebook and the printer works OK via cable. However the s/w won't install on XP, virtualized, for wireless. However the Internet works fine on XP also Thunderbird. Interestingly, wireless printing works via Ubuntu and XP / Virtualbox using a University printer - this has a very different setup though.

So what solutions can I try? Any ideas are welcome

Thanks

---

### Post by jtarin on 2012-05-08
[Manual and drivers for Epson]("http://download.ebz.epson.net/man/linux/")
[Model specific drivers]("http://download.ebz.epson.net/dsc/search/01/search/searchModuleFromResult")(enter nx430 as search term)

---

### Post by afz12 on 2012-05-08
Hi jtarin

I downloaded epson-inkjet-printer-201105w_1.0.0-1lsb3.2_amd64.deb and installed it using GDebi installer and it works with a cable - it printed a test page. However I wonder if there is another driver for wireless access? If not, at least the printer now works with Ubuntu 12.04 - thanks jtarin

---

### Post by jtarin on 2012-05-08
> I wonder if there is another driver for wireless access? 
Your wireless is not working in your Ubuntu networking at all? Aside from the printer.
[Might peruse this topic.]("http://ubuntuforums.org/showthread.php?t=1973041")

---

### Post by pbhj on 2012-07-02
Check your router for the assigned IP address of the printer. Point your browser at that IP address you should get a printer info screen.

I had an [IP address problem using KDE to connect to my Epson]("http://alicious.com/epson-install-kubuntu/").

---

