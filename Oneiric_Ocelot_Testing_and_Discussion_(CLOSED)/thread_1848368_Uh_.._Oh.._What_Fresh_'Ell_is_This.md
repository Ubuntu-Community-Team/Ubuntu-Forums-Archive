---
title: "Uh .. Oh.. What Fresh 'Ell is This ?"
date: 2011-09-22
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by ventrical on 2011-09-22
Just wondering if this is the Beta 2 upgrade?

---

### Post by Quackers on 2011-09-22
Don't know but I'm not OK'ing the removal of gnome-shell just yet :-)

---

### Post by fjgaude on 2011-09-22
> **ventrical said:**
> Just wondering if this is the Beta 2 upgrade?

I would say it is, but a moving target by tomorrow.

I use Unity 3D and upgraded without issue. All seems to work as it should, at this point.

---

### Post by paul_in_london on 2011-09-22
Yes, I saw that too when I checked what synaptic would want to do.

The strange thing is, I seem to remember **libcogl2** was removed by synaptic the other day when **libcogl5** was installed?!

Sticking with **aptitude safe-upgrade** in the meantime...

---

### Post by philinux on 2011-09-22
> **paul_in_london said:**
> 

Sticking with **aptitude safe-upgrade** in the meantime...

Ditto here. :p

---

### Post by ventrical on 2011-09-22
All went well here. Thing is , GNOME shell wasn't installed? I don't get it.

 Only difference is that Firefox started up really slow.

Time for a hard boot.

---

### Post by Quackers on 2011-09-22
As I'm using gnome-shell I'll wait and see what develops - maybe next week.

---

### Post by ventrical on 2011-09-22
OK.. hard boot went ok .. but I'm keeping an eye on Firefox.. somthings up!!

Compiz and all , cube, 3D working great!

---

### Post by ventrical on 2011-09-22
It used to be 52 MiBs and now it's 109!

Hmmmm..!!!

---

### Post by ventrical on 2011-09-22
Would someone check their FF in System monitor please and report back.

Thanks !

---

### Post by JMB74 on 2011-09-22
> **ventrical said:**
> Just wondering if this is the Beta 2 upgrade?

I think it's because there is a new version of Gnome Shell waiting to build that would fix that, with dependencies updated for todays other newer packages.

Unfortunately, the build of the new Gnome Shell is hung waiting for yet another different build dep. 

[https://launchpad.net/ubuntu/+source/gnome-shell/3.1.92-0ubuntu1/+build/2799897](https://launchpad.net/ubuntu/+source/gnome-shell/3.1.92-0ubuntu1/+build/2799897)

>                                         **Build status**

            [IMG]https://launchpad.net/@@/build-depwait[/IMG]       Dependency wait                       on [vernadsky (i386)]("https://launchpad.net/builders/vernadsky")                   
      
[LIST]
[*]         Missing build dependencies: *libcaribou-dev*
[/LIST]
Once that is sorted and the new gnome shell is built and available, then I think all the other dependency problems that make apt want to remove GS and other packages will all shake down and sort themselves out.

---

### Post by castrojo on 2011-09-22
> **ventrical said:**
> Just wondering if this is the Beta 2 upgrade?

If you've been keeping up to date you're probably already at Beta 2, all the stuff coming in now is everything over the past week that couldn't be uploaded due to freeze, so it'll likely churn today/tomorrow for a while.

---

### Post by ventrical on 2011-09-22
Thanks for you feedback.

Regards,
Ventrical

---

### Post by Harry33 on 2011-09-22
New clutter (libclutter0_1.8.0-1) and mutter (libmutter0_3.1.92) depend on libcogl5 instead of old libcogl2. This is why you cannot install them now or else, gnome-shell is removed. Gnome-shell must also be build against libcogl5. And that build is now waiting for caribou (gir1.2-caribou-1.0, libcaribou0) to be build.
So, just wait.
This is for people using Gnome-shell from Oneiric repos only.

But those using Gnome-shell from Ricotz Testing PPA, the new gnome-shell has already been installed with caribou and libcogl5. So no problem there.

---

### Post by ronacc on 2011-09-22
thanks for the heads up Harry , I run GS from the repos not the PPA .

---

### Post by ventrical on 2011-09-22
> **Harry33 said:**
> New clutter (libclutter0_1.8.0-1) and mutter (libmutter0_3.1.92) depend on libcogl5 instead of old libcogl2. This is why you cannot install them now or else, gnome-shell is removed. Gnome-shell must also be build against libcogl5. And that build is now waiting for caribou (gir1.2-caribou-1.0, libcaribou0) to be build.
So, just wait.
This is for people using Gnome-shell from Oneiric repos only.

But those using Gnome-shell from Ricotz Testing PPA, the new gnome-shell has already been installed with caribou and libcogl5. So no problem there.

Thanks for that explanation harry33.

Best regards,

Ventrical

---

