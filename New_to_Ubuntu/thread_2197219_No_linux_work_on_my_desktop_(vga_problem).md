---
title: "No linux work on my desktop (vga problem?)"
date: 2014-01-02
forum: New to Ubuntu
---

### Post by tkdpiki on 2014-01-02
Hi 
I tried to install ubuntu 13.10 many times on my old desktop (Gigabyte M61PME-S2, Athlon 4450e, 1gb ram)

Results are terribly wrong. Installation looks ok, no problems. But, when the login screen shows, there is system crash, next time even earlier:
[http://w619.wrzuta.pl/film/5PIdvy3RKAp/ubu](http://w619.wrzuta.pl/film/5PIdvy3RKAp/ubu)

 On Live situation is the same, only this time I have few seconds more...
[http://w619.wrzuta.pl/film/auqWmJqngRP/live](http://w619.wrzuta.pl/film/auqWmJqngRP/live)

I tried to use Suse 13.1
Exactly the same situation - system crashes with the same effect of shuttered screen as at the end of live video from my link.

Ram is ok, memtest shows no errors, totally no problems with Windows XP.

I'm quite experienced with windows, but total newbie with linux (everytime, when i try to convince myself for migration, something go wrong... this time  it looks like graphic card problem)
Anybody can help?

---

### Post by chkneater on 2014-01-02
You said you tried many times, was it with the same disk? and if so did you check the MD5 sum before burning it?  Doesn't sound like graphic prob or the live DVD would work.  Sounds more like bad disk burn, burn the DVD at slowest speed possible and check MD5 sums before installing.

---

### Post by sudodus on 2014-01-02
Welcome to the Ubuntu Forums :-)

It is worthwhile to check if it could be a problem with the graphics cards anyway. Please let us know what card or chip it is (from the control panel in Windows). Is there a wifi card/chip too (in that case let us know about it)?

You can use a [boot option]("https://help.ubuntu.com/community/BootOptions"),  start with ***nomodeset***, but try several of them. You can even use the boot option ***text***, to see if you can boot into a text screen (and maybe from there try to install a proprietary driver for the graphics).

---

### Post by mörgæs on 2014-01-03
Are you able to run Lubuntu 13.10 in a live boot?

---

### Post by grahammechanical on 2014-01-03
I find it interesting that you cannot load to a working Ubuntu desktop user interface but the live session does load to a working Ubuntu desktop user interface. The live session does not run a proprietary video driver but the open source video driver (Nouveau).

Now when we install Ubuntu and tick the box "Install Third Party software" we get a proprietary video driver installed. And it could be that the proprietary video driver is not very good at working that old video adapter that you have. Try installing Ubuntu without ticking the box "Install Third Party Software." Then when we reboot we will be loading Ubuntu with the Nouveau driver or a subset of it for graphic adapters that cannot provide accelerated graphics.

We can always install a proprietary video driver after Ubuntu is installed. In 13.10 we go to System Settings>Software and Updates>Additional Drivers tab. We must be connected to the Internet and allow the utility time to find the drivers. And we may need to experiment with different drivers. If we cannot get to a desktop when we reboot, then we can try at the Grub boot menu going to Advanced Options for Ubuntu (it is a sub-menu) and selecting Recovery Mode and then at the Recovery menu we select Resume. That may get us to a desktop and from there we can change video drivers.

Regards.

---

### Post by tkdpiki on 2014-01-05
Two different HDDs, i didn't check MD5, but it's rather not cd problem either. I used two cds (one with ubuntu, one with suse, and few times with bootable pendrive. During the installation process everything looks ok, no errors, and visually it's ok too.

This is the MB:
[http://www.gigabyte.com/products/product-page.aspx?pid=2755#sp](http://www.gigabyte.com/products/product-page.aspx?pid=2755#sp)

No external cards (wifi, nor vga)

Second link is recorded with Live pendrive, it chrashes, but after about minute till login. Interesting thing is that , that on the firs run from hdd, i saw login screen. It crashed after i entered the password. Next time it crashed like on teh record. Even before login screen. I'll won't be able to check everything one more time until  day after tommorow.

PS. I didn't get any notifications about answers in this thread, and i can't see where to change this...

---

### Post by mörgæs on 2014-01-06
> **tkdpiki said:**
> 
I didn't get any notifications about answers in this thread, and i can't see where to change this...

I don't think there will be many answers. People are still waiting for your response to the suggestion about boot options.

Please also post the output from ```
lspci  | grep -i vga
``` , if you get a live session running long time enough.

---

