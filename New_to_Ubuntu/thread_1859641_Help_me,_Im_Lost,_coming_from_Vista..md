---
title: "Help me, Im Lost, coming from Vista."
date: 2011-10-14
forum: New to Ubuntu
---

### Post by Filby1 on 2011-10-14
I need/want to Install Catalyst control center to run my ATI HD2400 card. thing is i need these:

[http://wiki.cchtml.com/index.php/11.9](http://wiki.cchtml.com/index.php/11.9)

where on earth do i get them? and even when i do how the hell do i install them ?

Im eager to learn the Linux Game, but coming from Windows step by step method, im feeling a little lost.

---

### Post by sirvinniei on 2011-10-14
> **Filby1 said:**
> I need/want to Install Catalyst control center to run my ATI HD2400 card. thing is i need these:

[http://wiki.cchtml.com/index.php/11.9](http://wiki.cchtml.com/index.php/11.9)

where on earth do i get them? and even when i do how the hell do i install them ?

Im eager to learn the Linux Game, but coming from Windows step by step method, im feeling a little lost.

In ubuntu you can get almost everything by using this code in terminal```
sudo apt-install [program you want to install]
```

---

### Post by jtarin on 2011-10-14
You would need to look for the fglrx-amdcccle package. Use Synaptic package manager or the command line as suggested above.

---

### Post by Johnb0y on 2011-10-14
you can try [this ]("http://www.ubuntugeek.com/how-to-install-ati-radeon-hd-2600-drivers-in-ubuntu.html")to see if it helps! basically the same i believe....

---

### Post by thunk77 on 2011-10-14
OK, step by step then..

Ubuntu version please?

---

### Post by Filby1 on 2011-10-14
Sorry: im running natty, wont let e upgrade at the moment


Thanks, I have downloaded Synaptic, i shall take it home tonight on a memory stick and see how i go.

I find allot of the help pages i find looking though google assume you know too much.

I had 2 hours going mad with the Pc last nigh tryig to find this terminal thing only to find what looked like a Windows Cmd Promt type thing, almost instantly i wanted windows back i thought if i was going to have to do everything Via this.

All the reviews of Linux said it was very easy to use and put windows to shame but to me this sound s like a long way round.

Does anything "Autorun" at the click of an icon ?

I originally wanted to run Linux as it was a free 64 bit system that could read all the ram i have in the pc where as the Vista 32 bit could not.

Im hoping i get the hang of the Linux game as i like the Apple look desktop and it boots up and shuts down quicker than Vista to do just a boot up.

---

### Post by clive littlewood on 2011-10-14
Hi Filby

Just remember that most programs or packages can be simply found in either the software center or synaptic package manager.

Old school Linux users prefer to use the terminal as it can be quicker when you know what you are doing.

Stick to the easier method at first and you will be rewarded with a better experience.

Clive

---

### Post by thunk77 on 2011-10-14
OK. 

Open the dash and search for ''Hardware Drivers''

If you are using classic GNOME instead of Unity, then it's System->Administration->Hardware Drivers

Launch the application, You should see a window that says ''searching for available drivers''. Wait a bit, then the main window will show. You will see some info about proprietary drivers and then something like ''ATI/AMD accelerated 3D driver blah blah''.. Click on it, and then click the ''Activate'' button. 

Presto! the program will automatically download and install the appropriate ATI driver for your hardware.

Reboot.

Good Luck!

---

### Post by Johnb0y on 2011-10-14
just as a little reminder, Linux is not Windows. Linux expects you to know what your doing, once you get the hang of it, it is amazing. and yes it can be so easy and simple, once you have decided what you want to do with it...

all i say is please be patient and understanding... take your time. Enjoy the ride.

p.s. one good difference between windows and linux... you have forums like this, that have plenty of people willing to help you for free.. as you can see... :p

---

### Post by Filby1 on 2011-10-14
Thanks people, im gona stick at it. really like it.

On another note, anybody else having trouble with the new upgrade?

Keep getting the Error, cant download release notes?

---

### Post by mastablasta on 2011-10-14
> **Filby1 said:**
> Thanks people, im gona stick at it. really like it.
 
On another note, anybody else having trouble with the new upgrade?
 
Keep getting the Error, cant download release notes?
 
servers are likely busy as people have the urge to upgrade. 
 
Upgrade is different than Update. update is security patches and various bug fixes. Upgrade is a while system wide upgrade (like "upgrading" WinXP to Vista).
 
what you could do if you wish to cupgrade is to change the source server. because there are plenty servers and mirror servers arround the world. you could chose another one close to you for faster download speed.

---

### Post by Johnb0y on 2011-10-14
can you confirm which version of ubuntu you are trying?

also got a screen shot of error?

---

### Post by Filby1 on 2011-10-14
Natty at the moment

---

### Post by collisionystm on 2011-10-14
Just

sudo apt-get install fglrx

That installed the catalyst drivers and control center.

---

### Post by TomTemple on 2011-10-14
> **clive littlewood said:**
> Hi Filby

Just remember that most programs or packages can be simply found in either the software center or synaptic package manager.

Old school Linux users prefer to use the terminal as it can be quicker when you know what you are doing.

Stick to the easier method at first and you will be rewarded with a better experience.

Clive

Im hearing you on FM

---

