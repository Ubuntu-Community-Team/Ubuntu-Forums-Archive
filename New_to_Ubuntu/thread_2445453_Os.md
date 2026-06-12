---
title: "Os"
date: 2020-06-14
forum: New to Ubuntu
---

### Post by basamrkalj on 2020-06-14
Helo!

Which version of ubuntu or linux is best choice for my netbook samsung n150 plus with 1G ram and atom processor?

---

### Post by CelticWarrior on 2020-06-14
Welcome.

It's an old and very underpowered computer and already was when released. There are no recommendation possible within the Ubuntu family, all the current releases are for 64-bit only. Debian is an option; any very lightweight distro still supporting 32-bit should work still. For how long is anyone's guess.

---

### Post by tea for one on 2020-06-14
> **basamrkalj said:**
> Helo!

Which version of ubuntu or linux is best choice for my netbook samsung n150 plus with 1G ram and atom processor?

If I were in your position, I would have a look at Peppermint 32 BIT

[https://peppermintos.com/](https://peppermintos.com/)

---

### Post by ajgreeny on 2020-06-14
On a similarly spec'd Netbook with Atom 270N cpu and 1G ram I have Debian 10, 32bit, running with LXDE and openbox, installed using the netinstall iso.  I generally use openbox for speed.

Not surprisingly it is pretty slow but just about usable for browsing and email, and some office docs, but not using Libreoffice, use Abiword and Gnumeric instead.

---

### Post by Yellow Pasque on 2020-06-14
Personally, I wouldn't try to use such a low-power system for general web browsing nowadays. If I did, I'd lay out the $10 to upgrade to a 2GB RAM module.

> **CelticWarrior said:**
> There are no recommendation possible within the Ubuntu family, all the current releases are for 64-bit only.

The N150 Plus does support 64-bit. Xubuntu 20.04 should be okay, especially if you cut out some of the cruft.

---

### Post by guiverc on 2020-06-14
I would check to see if it's i586 or i686 capable.   (my n270 is i686, yours maybe too but sorry I don't know)

If it's i686 then I'd consider Lubuntu 18.04 LTS.  Xubuntu 18.04 LTS would be my second *Ubuntu* choice, but the move from GTK2 to GTK3 adds weight which I noticed causes slow down on pentium M processors and thus 18.04 was slower than older releases (which are EOL now) which is why I'm suggesting Lubuntu/LXDE.  I use LXDE on my n270 (1gb ram) eeepc.

Lubuntu 18.04 LTS only has a year of support left (as all 18.04 flavors do, 3 years from 2018-April) so next choice if you need longer support (*or your cpu is i586*) is debian buster (10) as @ajgreeny suggested earlier.

However in the end, the best for you is whatever you're most comfortable with.

---

### Post by Yellow Pasque on 2020-06-14
> **guiverc said:**
> I would check to see if it's i586 or i686 capable.

Huh? All mainstream Intel/AMD CPU's in the last 25 years or so (since the Pentium Pro in 1995) are i686 capable*. 
*Note: The first gen of Pentium M had a bug where it did not report its PAE support correctly, which fools Ubuntu and other OS installers into thinking it's not 686-capable, but that is not applicable in this thread.

> my n270

The N270 does not support 64-bit. The OP's N450 (unless I googled specs wrong) does. Again, I'd lay out the $10 to upgrade the RAM: [https://www.amazon.com/2048MB-Samsung-Original-PC2-6400-SO-DIMM/dp/B0026SD96G](https://www.amazon.com/2048MB-Samsung-Original-PC2-6400-SO-DIMM/dp/B0026SD96G)
Then it's not an issue that 64-bit uses a bit more RAM.

---

### Post by guiverc on 2020-06-15
> **Yellow Pasque said:**
> Huh? All mainstream Intel/AMD CPU's in the last 25 years or so (since the Pentium Pro in 1995) are i686 capable*. 
*Note: The first gen of Pentium M had a bug where it did not report its PAE support correctly, which fools Ubuntu and other OS installers into thinking it's not 686-capable, but that is not applicable in this thread.


Thanks @Yellow Pasque

I went and re-tested a Lubuntu 18.04.4/rc ISO and it booted on the thinkpad r50p that I wrongly thought was i586  (prior releases/ISOs used to report that on booting; so I only used later t43/t43p/..)   Maybe I drew a wrong conclusion or it was a temporary bug, because it (and two pentium 4 boxes) reported differently to other pentium M & 4 devices (the r50p requires the `forcepae --forcepae` even on 18.04.4 where as other pentium M & 4s haven't for some time)

---

### Post by ActionParsnip on 2020-06-15
Lubuntu will run great. Can you not upgrade the RAM? It's super cheap and will really really help the system

( Hits Google )

You can! There seems to be an opening (Shown below. Not my picture)
[https://i.ytimg.com/vi/VRjmoH6MO7M/maxresdefault.jpg](https://i.ytimg.com/vi/VRjmoH6MO7M/maxresdefault.jpg)

According to
[https://downloadcenter.samsung.com/content/UM/201409/20140902103643755/Win7_Manual_Eng.pdf](https://downloadcenter.samsung.com/content/UM/201409/20140902103643755/Win7_Manual_Eng.pdf)

You can have up to 2Gb RAM maximum. These go for just under £20 GBP (Obviously you can see your local price in local currency if yours is different)

---

