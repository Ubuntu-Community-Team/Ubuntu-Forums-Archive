---
title: "[SOLVED] Trying to update to GIMP 2.6"
date: 2008-10-01
forum: New to Ubuntu
---

### Post by IdiotWind on 2008-10-01
I don't see it in synaptic package manager, how to install it from the .tar.bz2 file is beyond me, and apt-get says I have the latest version of gimp where all I have is the 2.4.5 or whatever that came with hardy heron.

Uh, help? :( Please and thanks

---

### Post by overdrank on 2008-10-01
Hi and welcome, moved :)

---

### Post by iponeverything on 2008-10-01
> **IdiotWind said:**
> I don't see it in synaptic package manager, how to install it from the .tar.bz2 file is beyond me, and apt-get says I have the latest version of gimp where all I have is the 2.4.5 or whatever that came with hardy heron.

Uh, help? :( Please and thanks

synaptic is just nice frontend for dpkg and apt-get, your not going find something that available in one that is not available in the other.

if you did a "apt-get update" and "apt-get install gimp" it reports that you have the latest version -- you have latest version that has been packaged for your distribution. hardy heron is the latests distro for Ubuntu, so your good.  If you want get your hands dirty, google around for how to rebuild debs. Find the source package for (not hard) gimp in Intrepid Ibex, if it is a newer version -- rebuild the deb for your hardy machine.  It is a fairly safe route.

---

### Post by Paqman on 2008-10-01
Head over to [this thread](http://ubuntuforums.org/showthread.php?t=935155) in the Community Cafe to get some installation instructions. On Hardy you'll need to download all those .debs to satisfy the dependencies.

---

### Post by mike1234 on 2008-10-01
It is available but I'm not going to bother with it. I would imagine Ubuntu will provide it to heron later.

[http://ubuntuforums.org/showthread.php?t=935155](http://ubuntuforums.org/showthread.php?t=935155)

M.

---

### Post by IdiotWind on 2008-10-01
Cool just got 2.6 installed. Thanks very much.

---

### Post by fabbaz on 2008-10-02
for several reasons i cannot upgrade to hardy (essential hardware partially not supported, which is fun, since it worked fine since dapper and started making problems with the first hardy alpha - nothing of it was solved until 8.04.1... really frustrating story, to be told another time...), so i still use gutsy.
is there any chance of getting gimp 2.6 in gutsy? the getdeb packages for hardy obviously (and in my desperation i even tried that...) wont work.

---

### Post by nowshining on 2008-10-02
just enable the backports in software sources :) reload and 2.6 should be available..

---

### Post by fabbaz on 2008-10-02
> **nowshining said:**
> just enable the backports in software sources :) reload and 2.6 should be available..

i.o.u.!

[I]it is installed now - but curiously, it still starts 2.4.6 instead of the now installed 2.6 - somethings not right. i'll see what i can find out.

thanks again[/I]

wait. turns out i'm stupid. there _was_ an update in the backports, but it didn't update to 2.6 - so 2.6 isn't installed, which answers my last question, but not my initial one. you think it will be in the repos soon?

---

### Post by billgoldberg on 2008-10-02
> **mike1234 said:**
> It is available but I'm not going to bother with it. I would imagine Ubuntu will provide it to heron later.

[http://ubuntuforums.org/showthread.php?t=935155](http://ubuntuforums.org/showthread.php?t=935155)

M.

No they wont.

Ubuntu only provides security updates for packages, not new versions.

Distro's that do this tend to be less stable.

---

### Post by magnus0 on 2008-10-02
Just donload it from [http://www.getdeb.net/app/Gimp](http://www.getdeb.net/app/Gimp)

---

### Post by fabbaz on 2008-10-02
This would be an awesome idea for anyone running hardy, but as posted this is not an option for me for the time being. thank you anyway!

---

### Post by billgoldberg on 2008-10-02
> **fabbaz said:**
> This would be an awesome idea for anyone running hardy, but as posted this is not an option for me for the time being. thank you anyway!

It's available here:

[ftp://ftp.gimp.org/pub/gimp/v2.6/](ftp://ftp.gimp.org/pub/gimp/v2.6/)

I presume the readme file will have install instructions.

---

### Post by silkstone on 2008-10-03
I've installed GIMP 2.6.0 on my laptop using the six .deb files from...

[http://www.getdeb.net/app/Gimp](http://www.getdeb.net/app/Gimp)

However, it is necessary to uninstall the old version of the GIMP, or there is a dependency error. Uninstalling the old version also means that you have to uninstall the ubuntu-desktop package. I have done this and everything seems to work, but I am not sure of the implications or side-effects of removing ubuntu-desktop.

I'd be grateful if someone could comment on this.

---

### Post by nowshining on 2008-10-03
if u plan on upgrading via apt-get/synaptic, etc.. then u'd need ubuntu-desktop :) - so far i've have not had any probs once i removed the -desktop part.. :) of course i use kde or kubuntu so kubuntu-desktop or so is what i removed..

---

### Post by silkstone on 2008-10-03
Thanks. So does that mean that normal updates are OK, but distro upgrades need the ubuntu-desktop package?

---

### Post by nowshining on 2008-10-03
pretty much yes :)

---

### Post by Mikorist on 2008-11-26
Gimp-2.6 For: Ubuntu Hardy (32 bits)

1.completely remove old Gimp
```

sudo apt-get remove gimp --purge

sudo apt-get autoremove

```
2.install in the following order:
```

~$ wget http://cesium.di.uminho.pt/pub/getdeb/ubuntu/hardy/li/libgimp2.0_2.6.0-1~getdeb1_i386.deb
~$ sudo dpkg -i  libgimp2.0_2.6.0-1~getdeb1_i386.deb

~$ wget http://getdeb.agetta.de/ubuntu/hardy/li/libbabl-0.0-0_0.0.22-1~getdeb1_i386.deb
~$ sudo dpkg -i libbabl-0.0-0_0.0.22-1~getdeb1_i386.deb

~$ wget http://ftp.heanet.ie/mirrors/www.getdeb.net/getdeb/ubuntu/hardy/li/libgegl-0.0-0_0.0.18-1~getdeb1_i386.deb
~$ sudo dpkg -i libgegl-0.0-0_0.0.18-1~getdeb1_i386.deb

~$ wget http://ftp.heanet.ie/mirrors/www.getdeb.net/getdeb/ubuntu/hardy/gi/gimp-data_2.6.0-1~getdeb1_all.deb
~$ sudo dpkg -i gimp-data_2.6.0-1~getdeb1_all.deb

~$ wget http://ftp.heanet.ie/mirrors/www.getdeb.net/getdeb/ubuntu/hardy/gi/gimp_2.6.0-1~getdeb1_i386.deb
~$ sudo dpkg -i gimp_2.6.0-1~getdeb1_i386.deb

~$ wget http://ftp.heanet.ie/mirrors/www.getdeb.net/getdeb/ubuntu/hardy/gi/gimp-python_2.6.0-1~getdeb1_i386.deb
~$ sudo dpkg -i gimp-python_2.6.0-1~getdeb1_i386.deb

```

:)

---

### Post by hansum_rahul on 2010-06-07
The back-ports version is 2.4.7 on my Hardy Heron.

The getdeb has unsatisfiable dependencies

---

