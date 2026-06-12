---
title: "graphic : unknown"
date: 2013-03-14
forum: New to Ubuntu
---

### Post by acepro71 on 2013-03-14
ok i just insalled ubuntu 12.10 on my system

and if i  go to 
about this computer > graphics 

it says driver : unknown
          experince : standard 


how can i fix the driver issue ?
i am a total noob at this .
This is the first time i am using ubuntu 
my vedio card is 
[B]SAPPHIRE HD 7870 GHz Edition 2GB GDDR5 
[/B][http://www.sapphiretech.com/presentation/product/?cid=1&gid=3&sgid=1160&pid=1473&psn=&lid=1&leg=0](http://www.sapphiretech.com/presentation/product/?cid=1&gid=3&sgid=1160&pid=1473&psn=&lid=1&leg=0)


~~~~~~

my system specs - 
motherboard - GA-970A-DS3


ram(8GB) [1600mhz] - Corsair CMZ4GX3M1A1600C9


processor  - fx 8350


harddrive - SAMSUNG 1TB 7200 RPM 


gpu -  SAPPHIRE HD 7870 GHz Edition 2GB GDDR5


 case - cooler master elite 310



supply box  - cooler master Thunder 500W

---

### Post by deadflowr on 2013-03-14
It's a standard message, as you are using the open-source radeon drivers by default.
You can get it to show the driver name by adding the program mesa-utils.

You can also install the proprietary drivers through the ubuntu repositories.
Open up the system setting and go to the section software sources. Open this up and the new window will show a tab for additional drivers, click on it and look over the choices. Best bet is to try the regular fglrx drivers (not the fglrx-update drivers)

Follow this page to help generate an xorg file, and help if problems arise:

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

### Post by acepro71 on 2013-03-14
ok i am downloading it off amd site
they gave me a zip file

how to extract it ? 
and 
will it install just by double clicking on it ?

also is there a way to download it via terminal  ?

---

### Post by ManamiVixen on 2013-03-14
No... do not use what ATI gives. Use the Ubuntu versions provided in software center/jockey-gtk. The one you have WILL BREAK EVERYTHING.

---

### Post by acepro71 on 2013-03-14
what do u mean 

darn it i am a damn noob at this

can not any of u team view my pc and install driver?

---

### Post by deadflowr on 2013-03-14
> **ManamiVixen said:**
> No... do not use what ATI gives. Use the Ubuntu versions provided in software center/jockey-gtk. The one you have WILL BREAK EVERYTHING.

Ubuntu 12.10 and beyond doesn't use jockey anymore. It uses software-properties-gtk.

But yes, best practice is to install from the repos, as they have more stable versions, and usually take care of any prerequisites that may be needed.

---

### Post by ManamiVixen on 2013-03-14
What I mean is that the one Ubuntu provides was tested for, and fixed against ubuntu bugs and such and the one straight from AMD/ATI isn't. To install the Ubuntu Version, open "software sources" by searching the Unity Dash and go to the "additonal drivers" tab, there click on fglrx-installer, not the updates one as it is known to be wonky at times with some cards.

---

### Post by QIII on 2013-03-14
Hello!

If you are familiar with the terminal, the easiest thing to do is this:

Install the driver:
```
sudo apt-get install fglrx fglrx-amdcccle
```

Initialize the settings (some say this is unnecessary, but enough people have had problems by not doing it that I still suggest it):
```
sudo amdconfig --initial
```

Reboot.

Best wishes!

---

### Post by acepro71 on 2013-03-14
> **ManamiVixen said:**
> What I mean is that the one Ubuntu provides was tested for, and fixed against ubuntu bugs and such and the one straight from AMD/ATI isn't. To install the Ubuntu Version, open "software sources" by searching the Unity Dash and go to the "additonal drivers" tab, there click on fglrx-installer, not the updates one as it is known to be wonky at times with some cards.

i did what u said
after installing it worked fine
for 1 minute
but then i open about this computer > graphic 

to see if it is still unknown

the ubuntu crashed

and now when i restarted

i only see desktop background and nothing else help !!!!!!!!!

---

### Post by QIII on 2013-03-14
Sometimes the graphical installer does not work.

From the screen you see, press Ctrl-Alt-T to get to the terminal.

Do

```
sudo apt-get purge fglrx fglrx-amdcccle
```

Reboot.

Then follow the instructions I posted before.

---

### Post by stinkeye on 2013-03-14
> **QIII said:**
> Sometimes the graphical installer does not work.

From the screen you see, press Ctrl-Alt-T to get to the terminal.

Do

```
sudo apt-get purge fglrx fglrx-amdcccle
```

Reboot.

Then follow the instructions I posted before.

Do  you still need to install linux-headers-generic in 12.10?

---

### Post by QIII on 2013-03-14
> **stinkeye said:**
> Do  you still need to install linux-headers-generic in 12.10?

Ayeeeee!

Of course!

So --

To recap:

```
sudo apt-get purge fglrx fglrx-amdcccle
```

Reboot

```
sudo apt-get install linux-headers-generic
```

```
sudo apt-get install fglrx fglrx-amdcccle
```

```
sudo amdconfig --initial
```

Reboot.

Thanks for helping a forgetful old man, stinkeye!

---

### Post by acepro71 on 2013-03-14
> **QIII said:**
> Hello!

If you are familiar with the terminal, the easiest thing to do is this:

Install the driver:
```
sudo apt-get install fglrx fglrx-amdcccle
```

Initialize the settings (some say this is unnecessary, but enough people have had problems by not doing it that I still suggest it):
```
sudo amdconfig --initial
```

Reboot.

Best wishes!


i re installed ubuntu (fresh install )

and after doing this with terminal 

again all i see is background of desktop nothing else :(
does that mean i can not use ubuntu ?

---

### Post by QIII on 2013-03-14
Did you see my update just above your post?

---

### Post by acepro71 on 2013-03-14
> **QIII said:**
> Did you see my update just above your post?
yes i do see ur post  now what should i do i am pretty confused

---

### Post by QIII on 2013-03-14
Follow the instructions in post #12.

I had forgotten that linux-headers-generic needs to be installed.

---

### Post by acepro71 on 2013-03-15
> **QIII said:**
> Ayeeeee!

Of course!

So --

To recap:

```
sudo apt-get purge fglrx fglrx-amdcccle
```

Reboot

```
sudo apt-get install linux-headers-generic
```

```
sudo apt-get install fglrx fglrx-amdcccle
```

```
sudo amdconfig --initial
```

Reboot.

Thanks for helping a forgetful old man, stinkeye!

i did all this and hwn it reboot all i see is the same damn background T_T

---

