---
title: "How much RAM is needed to run Ubuntu Smoothly ?"
date: 2008-11-18
forum: New to Ubuntu
---

### Post by rams123 on 2008-11-18
How much RAM (and also other requirements) is needed to run Ubuntu and Kubuntu latest version Smoothly ?

*I think Kubuntu requires less RAM than Ubuntu. **Correct me if I am wrong**.*

---

### Post by philinux on 2008-11-18
IIRc minimum is about 384meg but 512meg min would be better.

---

### Post by NewJack on 2008-11-18
I have a box running Edubuntu right now with 512MB of RAM and it runs perfect.

---

### Post by Bartender on 2008-11-18
Agreed.  512 is enuf.  More would be better!

To give you an idea of what's happening in the background...
On our Acer 5920 laptop dual-booting Vista and Ubuntu 8.04, the Vista OS starts up using just over a Gig of RAM.  If you let it sit there, doing nothing at all, it'll slowly settle down to about 750 - 800 MB RAM.  That's with Aero turned off, several services disabled, and start-up menu stripped down.
Ubuntu uses about 300 MB RAM with several applications up and running.

---

### Post by tjwoosta on 2008-11-18
i have 1GB ram and with that much ram it hardly ever touches the swap partiton even when i have all om my 4 workspaces loaded up with apps

---

### Post by jdong on 2008-11-18
384+swap is enough so that the system is what someone would consider "usable".

512+swap is enough to smoothly handle minor tasks, like a couple apps and a web browser open. Doing too much with 512MB RAM, such as OpenOffice + Firefox, might result in some lag.

1GB should be enough for any reasonably heavy desktop computing tasks without pushing into swap.


So, I'd say the answer to your question is probably 512MB.

---

### Post by mapes12 on 2008-11-18
I've had it running on 128MB RAM. Worked fine.............. Although I've now got another box with 1GB RAM.

---

### Post by binbash on 2008-11-18
That depends what you gonna use(desktop manager) and what you use ubuntu for.But for smoothly min 1gb not 512mb in my opinion.However you can run smoothly with xfce desktop with 512 mb ram.

---

### Post by fluxlizard on 2008-11-18
756 works great on my desktop.

I have a related question- why does ubuntu hog so much memory? I mean what exactly takes up so much? A year ago 256 ran great...

For that matter I've got an old laptop that runs pclinuxos gnome edition just fine and it's only got 256 mb ram, yet everything set up just as easily/in some cases more easily than ubuntu, so it seems just as fully featured, so why does ubuntu need so much more ram/cpu power?

---

### Post by binbash on 2008-11-18
> **fluxlizard said:**
> 756 works great on my desktop.

I have a related question- why does ubuntu hog so much memory? I mean what exactly takes up so much? A year ago 256 ran great...

For that matter I've got an old laptop that runs pclinuxos gnome edition just fine and it's only got 256 mb ram, yet everything set up just as easily/in some cases more easily than ubuntu, so it seems just as fully featured, so why does ubuntu need so much more ram/cpu power?

Gnome is a mem hog.Especially nautilus.

---

### Post by gjoellee on 2008-11-18
I have 2GB RAM and before the RAM upgrade I had 512mb RAM. At that time it was using swap a lot, if you move up to about 700mb RAM you will avoid swap

---

### Post by jdong on 2008-11-18
> **fluxlizard said:**
> 756 works great on my desktop.

I have a related question- why does ubuntu hog so much memory? I mean what exactly takes up so much? A year ago 256 ran great...

For that matter I've got an old laptop that runs pclinuxos gnome edition just fine and it's only got 256 mb ram, yet everything set up just as easily/in some cases more easily than ubuntu, so it seems just as fully featured, so why does ubuntu need so much more ram/cpu power?

Well the biggest culprit today is desktop effects. It needs to keep an in-memory cache of the display being drawn which depending on resolution may use up to a hundred or so MB of RAM.

Also, various applications to improve performance are using RAM to cache more aggressively -- the Firefox back-forward cache is one example -- the trend is towards the use of RAM to improve perceived performance, and for the most part this is a good trend, except that it leaves legacy systems in the dust pretty brutally.

The other issue is the restricted modules which use around 50MB on a RAM disk to store -- many licenses of these modules do not permit permanently storing a linked copy of the module, yet some distributions blatantly ignore such licensing terms. Go figure.

I really don't think 1GB is the "minimum" required as some people claim. You can get away with a lot less than that. I've set up Ubuntu GNOME systems with 384MB RAM and they run just fine -- my Firefox testing VMs have 256 allocated to them with desktop effects disabled and they run just fine too.

---

### Post by jenkinbr on 2008-11-18
I run just fine on 512 MB + Swap.  Bottles up every once in a while, but for the most part, it's nice and clean.

---

### Post by jdong on 2008-11-18
Well, yeah, you are going to swap with 512MB RAM or less, though that's what the system is designed to do -- evict useless idle information like the 50MB restricted module RAMdisk, idle memory from background services, etc to disk to make room for other applications. It's not really a bad thing. If you want a system that doesn't swap AT ALL, yes, you will need more than 384  or 512MB RAM and maybe the 1GB figure is accurate, but IMO that's not really crucial to a usable Ubuntu system.

---

### Post by egalvan on 2008-11-18
> **rams123 said:**
> How much RAM (and also other requirements) is needed to run Ubuntu and Kubuntu latest version **Smoothly** ?

*I think Kubuntu requires less RAM than Ubuntu. **Correct me if I am wrong**.*

OK, the answers are highly dependant on what YOU feel is **SMOOTH**.

Further, how much "eye-candy" you want. Compiz-type spinning cubes, transparent windows and fancy themes need more horsepower/ram/hd.

Now, I am firmly in the camp of "More RAM, please!".
Ubuntu's sweet-spot seems to be about 512M, with simple tasks, e.g. surfing, email, text, etc.

At about 1Gig, swap seems to go away, which can make a system feel "smoother".


Having said that, I feel there is a bit more to the equation...

2) Hard disk size and speed. The larger the drive, the faster it read/writes. The faster the spindle, the faster it read/writes. The faster the heads seek, the faster it read/writes. (more or less).
This will impact loading speed, and also swap performance (which will be impacted by RAM size).

3) CPU cache size. The bigger the cache, the more efficient operation of the CPU.

So it's a balancing act. RAM size, HD speed, CPU cache.

And further, if your system uses DDR2 memory, you will find it dirt-cheap (at NewEgg.com, for instance). Unless your budget is zero, there is no reason not to install a pair of 512M sticks. Vista users are literally throwing theses in the trash as they scramble to install 2-4 gig RAM. Mom&Pop-type computer repair shops are a great source of these.

And we find we haven't even touched on the subject of video cards!

ErnestG

P.S.
I find that KDE is slightly more memory-efficient than Gnome, but I don't think it's that large a difference.
If you want a lighter-weight desktop, try Xubuntu, or even FluxBox.

of course, Puppy will blow these all away. 

The above are all my opinions. Others will vary, and beg to differ.
Long Live Linux!
Long Live Choice!

---

### Post by Keen101 on 2008-11-18
I'd say in this day in age 512 should be the minimum. Plus ram is fairly cheap these day's. I have an old p3 with 320mb ram, and ibex ran terribly slow. Tried it with hardy, and it ran ok but still a little slow.

anyway, 512mb should be the lowest these day's.

---

### Post by Helios1276 on 2008-11-18
look around the house for spare cash, pool it together and instead of a few beers, get some RAM:popcorn:

---

