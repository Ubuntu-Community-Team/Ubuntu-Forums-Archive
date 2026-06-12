---
title: "Hardy Heron ATI drivers"
date: 2008-04-24
forum: New to Ubuntu
---

### Post by seamustry on 2008-04-24
I've just installed 8.04 and now I can't use desktop effects because the ATI drivers won't enable...I've gone to Hardware drivers, disabled and enabled it, restarted the system and still I see the message that the driver is "not in use"...what can I do so that it is used?

thanks!

---

### Post by swoll1980 on 2008-04-24
install envy ng it will set the drivers up for you [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

---

### Post by iopo on 2008-04-24
I'm having a similar problem. With 7.10 I could run Compiz in two ways:

- proprietary driver + xgl
- opensource driver + aixgl

I just installed 8.04 and I have been trying to enable desktop effects with no luck. I don't think it is a driver issue: compiz should run fine with the opensource driver if aixgl was enabled!
I think the problem is that aixgl is not enabled or that for some reason compiz does not recognize it.

---

### Post by bgast1 on 2008-04-24
I am still very inexperienced in Linux but I have Hardy Heron installed. I have and ATI Radeon X1950Pro PCIe card. With Gutsy I had to use the proprietary driver + XGL. But with Hardy Heron, I did not have to at all. 

I can't remember though if I used EnvyNG or just used the restricted driver. 

Just installed Advanced Desktop Settings and I was set. Works beautifully and doesn't even consume all of my resources.

---

### Post by the_darkside_986 on 2008-04-24
Did you type first
```

sudo apt-get update

```
Envy shouldn't be necessary anymore.

Anyway, I never could get Nvidia glx drivers installed until I did a sudo apt-get update. But that is a long and painful process since the archive servers are heavily overloaded at the moment.

It's probably the same principle for other proprietary drivers such as ATI.

---

### Post by seamustry on 2008-04-24
so is that why i can't download anything using synaptics??? 

i select the packages i want and then the thing just waits there at the "downloading" stage but doesn't download anything...

---

### Post by iopo on 2008-04-24
Maybe this can help:
[http://ubuntuforums.org/showthread.php?t=764633&highlight=composite](http://ubuntuforums.org/showthread.php?t=764633&highlight=composite)
best

---

### Post by hartleyshc on 2008-04-24
xgl isn't installed by default. you need to install xgl.

```
sudo aptitude update
sudo aptitude install xserver-xgl
```

no need to pick an xgl session when you log in, it will automatically be loaded with gnome.

---

### Post by ali999 on 2008-04-25
I had this problem with in Hardy just after installing it. Went to Hardware Drivers but there it said that my Ati FireGL cad was enabled but not in use. All I had to do was go to my Software Sources through System>Administration>Software Sources and enable restricted drivers and third party drivers. Then went back to my Hardware Drivers through System>Administration>Hardware Drivers and problem solved. The new Ati accelerated drivers show up as disabled, just enable them and you should be good to go.

---

### Post by seamustry on 2008-04-25
ok i can't download anything using a package manager...it opens the dialog box which says downloading but it just waits there forever and nothing gets downloaded

---

### Post by rickatnight11 on 2008-04-25
Had the same issue.  Just give it time.  The servers are flooded from everyone downloading the new release and all the packages from the repositories.  I thought something was wrong with my ATI drivers but after about five minutes it started downloading.  Honestly it looks like they have some sort of queueing system at the moment so that rather than having everyone download slowly, you just wait until a download slot is available.

---

### Post by seamustry on 2008-04-25
ok i'll try to wait a bit longer :)

---

### Post by seamustry on 2008-04-25
yep that was the problem...just waited for the download and it all works nicely now...hopeufully will keep working :)

---

