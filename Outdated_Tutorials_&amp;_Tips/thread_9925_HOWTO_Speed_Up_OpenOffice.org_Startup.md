---
title: "HOWTO: Speed Up OpenOffice.org Startup"
date: 2005-01-02
forum: Outdated Tutorials &amp; Tips
---

### Post by angrylittleman on 2005-01-02
This is something that I usually do as a post install tweak.  I have 512+ plus RAM systems that work well with this, although I have noticed *speedier* results with 256 mb RAM.  

Applications-->OpenOffice.org Writer-->Tools-->Options

Under the OpenOffice.org heading, select Memory

Under Graphics Cache change the "Use for OpenOffice.org" to 30 MB
Change "Memory per Object" to 2.0 MB

Close OpenOffice.org

Restart OpenOffice and marvel at the speed!!!

Your mileage may vary, consult your doctor before begining any physical exercise program.  

Please note this is my first howto.  I have tried to follow the howto format as best I can.  Please give me any feedback you see fit.

---

### Post by Hikaru79 on 2005-01-02
Not bad :) My speed about doubled, and I've only got 128 MB of RAM. Impressive ^__^

---

### Post by wallijonn on 2005-01-03
angrylittleman,

Thanks for the tip. I was trying to remember what the setting is for WXP (setting the prefetch flag on the app. command line in file launcher properties) and knew that there had to be something like it in Linux. 

I did see a speed up of about 50%, or 3 seconds to startup on my PC.

---

### Post by angrylittleman on 2005-01-03
Glad you found it useful!

---

### Post by thepoch on 2005-01-04
Running on a Thinkpad T30 (P4 1.8ghz, 256mb RAM, 40gb HDD), this has sped up OOo loading tremendously. Although it is quite late where I am, so I have no idea if my perception is accurate.

On my aging Dell Optiplex GX1 (P3 500mhz, 320mb RAM, 80gb HDD), it now loads up in 4 seconds instead of the old 8 seconds.

If there was a rating system for howtos, this would be "Howto of the Year". Forgive me for being corny... it's late.

dex

---

### Post by LB06 on 2005-01-05
Startup time decreased from 10s to 2s. But that could also be because OO.org got cached during/after the first startup (most progs start faster upon second boot due to cache). I'll try to remember that I have to measure OO.org startup time after my next reboot :)

---

### Post by badriram on 2005-01-05
[QUOTE=angrylittleman]This is something that I usually do as a post install tweak.  I have 512+ plus RAM systems that work well with this, although I have noticed *speedier* results with 256 mb RAM.  
..........[/QUOTE]
 Wow... that was great. I cannot believe the difference in speed. Is there a reason why the default settings are soooo slow compared to these? 
Either way thanks for the tip.... (does this also work in windows OO) :-)

---

### Post by angrylittleman on 2005-01-05
When OO is cached, it will start up much faster that after a fresh restart.  That is the same reason that IE seems to start much faster than Firefox for some people in Windows.  I have found that even after restarting, the startup time for OO will still be a lot faster.   

I don't know if this tweak will work in XP.  I have never had an oppertunity to test it in an XP enviroment.  But if it does, hey, great!

Glad this helps a lot of people.

---

### Post by Jesus Franco on 2005-01-07
Not to sound mean....but I have 1024 mbs and it is exactly the same speed. Loading at least. I haven't used it to see if its any faster. Maybe this only works on lower end machines.  :confused:

---

### Post by hardcandy on 2005-01-08
There is also ooqstart-gnome and oooqs-kde found in the universe repository which are applets that keep OO preloaded to start fast.
After you install it, right click on the bottom panel and "add" the applet. After it shows up, right click on the applet and then preferences. Enable it and make sure the path to OO is correct.
Then right click and choose which OO application to start.

---

### Post by angrylittleman on 2005-01-08
This may not work with systems with so much RAM....it does seems to help people with  less than 1gb of RAM....No offense taken, Jesus....

alm

---

### Post by wallijonn on 2005-01-08
[QUOTE=Jesus Franco]I have 1024 mbs and it is exactly the same speed. Loading at least.[/QUOTE]

Are you running an i386 kernel? To take advantage of 1G or more you need to install an i686 kernel or i686-smp kernel. Check your /var/log/kern.log. Does it look like this?:
```

klogd 1.4.1#14ubuntu4, log source = /proc/kmsg started.
localhost kernel: Inspecting /boot/System.map-2.6.8.1-3-386
localhost kernel: Loaded 28166 symbols from /boot/System.map-2.6.8.1-3-386.
localhost kernel: Symbols match kernel version 2.6.8.
localhost kernel: **Warning only 896MB will be used**.
localhost kernel: **Use a HIGHMEM enabled kernel.**
localhost kernel: **896MB LOWMEM available.**

```

This is what an -686 kernel looks like:
```

klogd 1.4.1#14ubuntu4, log source = /proc/kmsg started.
localhost kernel: Inspecting /boot/System.map-2.6.8.1-4-686-smp
localhost kernel: Loaded 27787 symbols from /boot/System.map-2.6.8.1-4-686-smp.
localhost kernel: Symbols match kernel version 2.6.8.
localhost kernel: Linux version 2.6.8.1-4-686-smp (buildd@rockhopper) (gcc version 3.3.4 (Debian 1:3.3.4-9ubuntu5)) #1 SMP Wed  
localhost kernel: **1150MB HIGHMEM available.**
localhost kernel: **896MB LOWMEM available.**

```

---

### Post by jetta92 on 2005-01-13
another way to speed openoffice......

sudo apt-get install prelink 

sudo oooprelink -f

openoffice comes with it's own prelink utility that uses your system prelink (if installed) should increase performance remarkably combined with the quickstarter

have fun

---

### Post by John McClane on 2005-01-25
Tnx!

---

### Post by Eejay on 2005-01-25
Thanks for the Tweak Worked like a charm
oo is now opening much faster then it was before :D

---

### Post by macewan on 2005-01-25
wow, this will be extremely helpful at the office.

thanks

---

### Post by angrylittleman on 2005-01-25
Gald it helps everyone!!!!

---

### Post by HerrSieben on 2005-02-22
[QUOTE=angrylittleman]Gald it helps everyone!!!![/QUOTE]
 What a real good hint.

I have got an  old Laptop with just 128 mb of Ram. Now the time isnt enough to take a shower  after starting OO ;)

---

### Post by jsgotangco on 2005-02-23
Wow it did work on my 256MB RAM laptop with a 686 kernel!

---

### Post by Jason-X on 2005-03-23
I've got 256mb of memory on my system and this tip made a massive difference. Open Office was always a bit slow to start up.

Thanks for sharing this!

Jason :)

---

### Post by beeldings on 2005-03-23
You're guide worked, but OpenOffice still takes too long to load and is generally too much of a strain on my system, so I'll probably run something else instead.

---

### Post by Heliode on 2005-03-24
This worked great! The tweak by the original poster, combined with the quickstarter applet and the prelink tip, make OOo start in no time at all! Maybe this should be added to the Ubuntu Wiki?

Now, if only we could get something like this for Firefox, we'd be set!

---

### Post by Nonno Bassotto on 2005-07-10
Why is it? I have the prelink package installed, but

$ sudo oooprelink -f
sudo: oooprelink: command not found

this is the output of oooprelink. Isn't it installed together with prelink anymore?

Andrea

---

### Post by manicka on 2005-07-10
I notice that the latest Ooo2 beta 113 has similar settings to this by default

---

### Post by thenetizen on 2006-12-23
please tell me where do i find "APPLICATIONS" & openoffice.org in my PC .......Windows XP professional is my OS

---

### Post by hakimaki on 2006-12-23
Thanks!  It increased my startup speed by at least 2x

---

