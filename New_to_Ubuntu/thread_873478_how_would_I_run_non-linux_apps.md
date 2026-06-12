---
title: "how would I run non-linux apps?"
date: 2008-07-29
forum: New to Ubuntu
---

### Post by philippet on 2008-07-29
I want to switch away from Vista. 
Ubuntu supported apps seem to do everything I need EXCEPT
I need to use iRise for work (a web prototyping application which runs on Windows and requires Word & IE too)
What are my options for using ubuntu and irise on the same pc (or Quickbooks or any other application built for a windows environment ) ?

thank you

philippe

---

### Post by Elfy on 2008-07-29
You have 3 basic options 

1 - dualboot and use vista when you need to
2 - wine will work with some windows programs - check the site
3 - run a virtual machine and install windows on it - not 3d gfraphics so it isn't for games
[http://www.winehq.org/](http://www.winehq.org/)
[http://appdb.winehq.org/](http://appdb.winehq.org/)

There is a virtualization forum [http://ubuntuforums.org/forumdisplay.php?f=308](http://ubuntuforums.org/forumdisplay.php?f=308) - I use virtualbox - if you get the version from them it has usb support

There are plenty of sites dealing with dual booting

[http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)
[http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm](http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm)

I find this site easier to search with - it is buntu specific [http://www.uboontu.com/](http://www.uboontu.com/)

a search for quicken 2008 gets recent results for instance.

---

### Post by El Conquistador on 2008-07-29
You can either install wine and hope your program works if it doesnt do some research there may be fixes. to install wine go to winehq.org and follow the directions to install on your distro. then just double click your .exe and istall it.

your other choice would be to install a virtual machine and install windows on it then run your programs in the virtualmachine. i recommend virtualbox.

Edit: YEAH what forestpixie said. did a better job too.

---

### Post by loneowais on 2008-07-29
Try xVM VirtualBox

**[http://www.sun.com/software/products/virtualbox/index.jsp](http://www.sun.com/software/products/virtualbox/index.jsp)**
features
**[http://www.sun.com/software/products/virtualbox/features.jsp](http://www.sun.com/software/products/virtualbox/features.jsp)**

Download
**[http://www.sun.com/software/products/virtualbox/get.jsp](http://www.sun.com/software/products/virtualbox/get.jsp)**

---

### Post by kdb424 on 2008-07-29
I recommend dual booting, Virtualbox (Virtual machine) and then wine in that order for your situation.

---

### Post by Bucky Ball on 2008-07-29
> runs on Windows and requires Word & IE too

This gives you about one option ... virtual machine.

---

### Post by SunnyRabbiera on 2008-07-29
Dual booting is always a good option, but wine might work too.
You wont know until you try.
But to me anything that demands IE and word is stupid.

---

### Post by philippet on 2008-07-29
thank you for the quick response. can I ask why in that order?
cheers
p

---

### Post by El Conquistador on 2008-07-29
> **Bucky Ball said:**
> This gives you about one option ... virtual machine.

not necessarily because after wine then you could intall Wine-Doors and intall IE from then. although to be honest i havent tried it so i dont know how good it will be. but the option is there. but yes dual-booting is also a good suggestion.

---

### Post by philippet on 2008-07-29
thank you for a great response. ill have a look

p

---

### Post by Elfy on 2008-07-29
> **philippet said:**
> thank you for the quick response. can I ask why in that order?
cheers
p

If you're talking about my post - because that's how I thought of them - if you want my preferred order it would be

virtualmachine 
dualboot 
wine

---

### Post by kdb424 on 2008-07-29
> **philippet said:**
> thank you for the quick response. can I ask why in that order?
cheers
p

That way you can keep work and play separated with dual boot. Then VM, sucks down your system resources. (Vista.........) and Wine is cool, but never really works that well without a lot of research and modifying (most of the time, so no one yell at me for saying that) If you need the newest internet explorer it's rarely compatible from what I hear.

---

### Post by SunnyRabbiera on 2008-07-29
Well not in my case, wine has surprised me many times,

---

### Post by El Conquistador on 2008-07-29
yes plus another reason would be that it goes from 100% working to Possibly working. and since you say this is for your job then you might be better off going for the sure thing..that way you dont get fired!

---

### Post by kdb424 on 2008-07-29
Thinking of work first is why I suggested dual boot first. Virtual machines are great, but only on newer machines with vista. lol. If you could, maybe try XP and Ubuntu dual boot...

---

### Post by Elfy on 2008-07-29
To be honest whatever I was going to do I would start with a dualboot - you do not want to be trying to start using a new os, work out how to use either a vm or wine inside of your chosen buntu - at the same time as working :)

There is one other option which I always forget about - you can install ubuntu inside of windows using the wubi installer - afaik putting the cd in while running windows will bring up the wubi installer. 

I don't however have the first idea how good it is. You can later transfer the ubuntu wubi install to a full blown ubuntu install.

---

### Post by kdb424 on 2008-07-29
I don't like wubi as it relies on windows living, and Vista of all versions....

---

### Post by Elfy on 2008-07-29
> **kdb424 said:**
> I don't like wubi as it relies on windows living, and Vista of all versions....You might not - I have no idea myself - but it's more about giving the op options to make a sensible choice in his circumstance. I don't like windows - but then I don't need it to run particular programs :D

---

### Post by kdb424 on 2008-07-29
Dual boot is just as easy, but whatever.  let us know what you choose before we start a war. lol jk.

---

### Post by Elfy on 2008-07-29
> **kdb424 said:**
> Dual boot is just as easy, but whatever.  let us know what you choose before we start a war. lol jk.You're ok - I don't do wars ever - [SIZE="1"]don't like macs either[/SIZE] :lol:

---

### Post by kdb424 on 2008-07-29
Love macs, different topic. What I really want to say is that if you have the hardware to back it up, than you might want to run a virtual machine so you can do everything at once. Just use 2 desktops. 1 fullscreen windows, the other Ubuntu. I would recommend putting windows in the virtual machine though. It runs better.

---

### Post by Bucky Ball on 2008-07-29
> intall Wine-Doors and intall IE from then. although to be honest i havent tried it

I guess that's my point, yes, achievable but could take a very long time to set up with not much advice available because it is pretty specific. VM on the other hand ... which, incidentally, I don't use at all. I try to go native Linux where-ever possible. (boot windows for one program which doesn't run under wine anyhow and that is soon to go!) :)

---

