---
title: "[SOLVED] Linux temp &amp;gt; Vista temp"
date: 2008-11-18
forum: New to Ubuntu
---

### Post by b0yd07 on 2008-11-18
Does anyone have an explanation for this? I've been messing around with several linux distro's and all of them have my laptop running around 130*F or warmer. My vista installation used to run that, however after updating the bios it now runs a cool 100* for some reason (which makes me feel really good inside, lmao).

After searching the net, I've got almost no explanation for it. Mind you, I've only ever ran live cd's, so no video driver has ever been installed. I have an nvidia 8600gt card so it definitely needs its own driver. Would trying to run the standard 'ol display support driver packaged with ubuntu with my card make it run hotter? Thus, with a full installation + correct driver it should cool off?

Also... the only way I've been able to check the temperature was with the terminal line 'acpi -tf'... and it only tells me core temp. In windows I use HWmonitor and it shows hdd temp, core's temp, acpi temp, and gpu temp... how on earth do I get linux to bring those up? Obviously I'm a bit anal concerning my shiny new laptop. I realize almost anyone else would accept 130 degrees, but I know my laptop can do much better and I'd love to have it running at peak performance. Also the left palm rest gets hot which bugs the hell out of me. :rolleyes:

EDIT: Tried ubuntu 8.10, xubuntu, linux mint, opensuse, and fedora. All run same temperature. All ran from live cd.
EDIT 2: Vista FTW at the moment, set at max performance. Boo. [SCREENSHOT](http://img165.imageshack.us/my.php?image=76565847hh4.jpg)

Thanks for all help. -Mike

---

### Post by aeiah on 2008-11-18
things might be getting a bit hot because your dvd drive is spinning up to dump everything to ram when running the livecds perhaps. also, if you havent got your graphics card drivers installed then more CPU power will be being used. 

or perhaps your laptop isnt doing any more work under linux, its just that vista sets the fan to go faster or has a lower threshold for making the fan go quick. this could be changed in linux to suit your needs.

---

### Post by Twitch6000 on 2008-11-18
The livecd is the problem.(well not problem more or less reason)

It is because it is running off of ram and causing more work to be done.

Causing higher temperature and such.

If you installed whichever Linux Distro you might want(I know hard to choose) onto your desktop then tweak it to however you want it should run just fine.

---

### Post by L815 on 2008-11-18
> **aeiah said:**
> things might be getting a bit hot because your dvd drive is spinning up to dump everything to ram when running the livecds perhaps. also, if you havent got your graphics card drivers installed then more CPU power will be being used. 

or perhaps your laptop isnt doing any more work under linux, its just that vista sets the fan to go faster or has a lower threshold for making the fan go quick. this could be changed in linux to suit your needs.

I found this to be similar to my situation. With ubuntu, my fans are at a constant speed, either hot or cool.
Vista on the other hand, variates the speed based on the temp, which I think is better and causes things to keep cool. 
As long as your laptop isn't burning you at the touch, you should be fine. Laptops are built with heat in mind!

---

### Post by b0yd07 on 2008-11-18
> things might be getting a bit hot because your dvd drive is spinning up to dump everything to ram when running the livecds perhaps. also, if you havent got your graphics card drivers installed then more CPU power will be being used.
So consensus says this is correct. But 30(!) degrees more?

> If you installed whichever Linux Distro you might want(I know hard to choose) onto your desktop then tweak it to however you want it should run just fine.I'm torn between Linux Mint and OpenSUSE... both have new versions coming out soon so I've got time to waste researching before I make any drastic changes to my computer. OpenSUSE seems professional though; I like it.

Also, any insight into checking all the temperatures, like the screenshot I put up top?

---

### Post by b0yd07 on 2008-12-02
I thought I might add my end experience to this thread:

Just got done installing Linux Mint after much debate, and it does run a hell of a lot cooler. My laptop runs at 140*F on LiveCD and 104*F on HDD.

Thanks for the help guys. I'll mark this case [SOLVED].

---

### Post by Paqman on 2008-12-02
> **b0yd07 said:**
> 
Also... the only way I've been able to check the temperature was with the terminal line 'acpi -tf'... and it only tells me core temp. In windows I use HWmonitor and it shows hdd temp, core's temp, acpi temp, and gpu temp... how on earth do I get linux to bring those up?

If you install sensors-applet you can add system temp monitors to a panel. If your mobo conforms to the standards properly you should be able to display core, ACPI, HD and GPU temp.

---

