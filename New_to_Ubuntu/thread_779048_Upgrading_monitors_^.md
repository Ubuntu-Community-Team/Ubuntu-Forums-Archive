---
title: "Upgrading monitors :^/"
date: 2008-05-02
forum: New to Ubuntu
---

### Post by kansasnoob on 2008-05-02
OK, my light bill has finally convinced me that it's time to upgrade all three of my old CRT monitors. Before getting too involved I thought I'd ask for some compatibility advice.

I do recall having quite a bit of trouble installing Ubuntu on a friends puter with a Viewsonic, but I did get it working OK.

I'm leaning a bit towards this CHIMEI 22" 5ms 330 cd/m2 800:1 DVI Black Widescreen LCD:

[http://www.clubit.com/product_detail.cfm?itemno=A4693007](http://www.clubit.com/product_detail.cfm?itemno=A4693007)

All computers are Windows (2-XP & 1-98SE)/Ubuntu 8.04 dual boots.

Any and all suggestions would be appreciated.

---

### Post by Fedz on 2008-05-02
Depends on the graphics card but even if you get the default low res at bootup:

Add/install and then goto 'screens and graphics' from add/remove applications.

Choose:
Graphic Card:
driver: vesa-Generic-VESA-compliant video cards
Screen: model: LCD Panel eg: 1280x1024 

Just make sure the V and H range is within a max. acceptable high eg: 65 on both H and V.

Shutdown > reboot.

I've sometimes noticed you have to do this a few times even before rebooting until it asks for you to log-off but, it does do it :)

Ther monitor you posted is 1680x1050 resolution and the above driver and screen doesn't go about 65 H and V max so you should be on a winner with defaults :)

Hope this helps :)

---

