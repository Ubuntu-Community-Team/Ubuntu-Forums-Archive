---
title: "Display too small...squashed into one corner of monitor!!"
date: 2014-06-15
forum: New to Ubuntu
---

### Post by Mike_Walsh on 2014-06-15
Morning, everybody.

I've been using Trusty Tahr on this, my desktop, for a few weeks now, and I'm very pleased with it.

I have an elderly Dell Inspiron laptop (2002 vintage) which I've just installed Lubuntu 14.04 on this morning.

Everything is working nicely.....with one small exception; SMALL being the operative word!

My desktop is squashed up into one corner of the screen; and Monitor Settings insists that I only have a 640 x 480 display. I know for a fact the 15" display on this laptop is 768 x 1024, so; what's happening here, and how can I make the desktop fill my screen the way it should?

It filled the entire screen in the Live Session, which I tried before installing; anybody have any ideas as to why it appears to have shrunk AFTER installation?


Specs:-

Intel Celeron CPU; 'Netburst' architecture, 2.2 GHz
1 Gb of RAM (max for this machine)
20 Gb HDD (!)
Intel 845GL chipset
Intel 82845 (?) Extreme Graphics

Any suggestions would be gratefully received..!

Mike Walsh.

---

### Post by Rob Sayer on 2014-06-15
You want to know exactly what video adapter you have.  Run this in terminal ...

```
lspci
```

... and post result here, wrapped in [CODE] tags.  You'll get much better support if it's more readable.

One thing you could try is enabling nomodeset on your next boot.  See here ...

http://ubuntuforums.org/showthread.php?t=1613132

If it actually is the adapter you mentioned, read this ...

http://ubuntuforums.org/showthread.php?t=2222349

Hope this helps ...

---

### Post by Mike_Walsh on 2014-06-15
Hi, Rob.

Thanks for that; I DO have the adapter I thought I had. I've looked at the two threads in question, and they are exactly what I need. I've substituted 'leafpad' for 'gedit', since that's my text editor; the only problem I now have is that the authentication window WON'T accept my password to start the ball rolling! :confused:

Don't have any ideas, do you? Or do I HAVE to use 'gedit' for the command to accept my password, and work?

As far as I understand it, from the weeks I've been using Ubuntu on my desktop, whenever use of a text editor is required in the terminal, you just use whichever text editor you have installed...am I correct?

So; I can log in with the password, no problem...but the authentication box won't accept it. What am I doing wrong?

You're NEVER too old to ask for help! :)

Mike.

---

### Post by Vladlenin5000 on 2014-06-15
The terminal must accept your password provided it's correct. It should be the same as the one you use to login. It won' t show up when being typed but it's there.
Yes, you're correct by replacing gedit by leafpad, the one by default in LXDE (Lubuntu's desktop environment). Although you can install any other text editor things should work the same way with the one that comes by default in your distro/flavor. The password issue is unrelated.

---

### Post by Bashing-om on 2014-06-15
Mike_Walsh; Hey,

Try this to get  leafpad started with the elevated privileges .
```

gksudo leafpad

```

It is probable that "gksudo' is no longer installed by default: run:
```

sudo apt-get install gksu
##To enable it, type:##
gksu-properties

```
choose for the Authentication Mode: "sudo" 

[INDENT][INDENT]my little bit to try and help
[/INDENT][/INDENT]

---

