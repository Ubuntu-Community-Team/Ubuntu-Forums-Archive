---
title: "what happens if i remove the computer janitor application?"
date: 2012-08-31
forum: New to Ubuntu
---

### Post by tojonukokhadush on 2012-08-31
what if i removed these using computer janitor? is these necessary to upgrate my system from 10.04 to 12.04???

---

### Post by Frogs Hair on 2012-08-31
Open the synaptic package manager and see if the package is listed as an installed autoremovable package. If it is reload synaptic before removing the package from there. I have avoided Computer Janitor on previous releases because more experienced users suggested extreme caution when using it. Computer Janitor is no longer installed by default.

---

### Post by jerrrys on 2012-08-31
Amen to synaptic

[http://www.google.com/cse?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=synaptic+package+manager&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2F&ad=n9&num=10&rurl=http%3A%2F%2Fwww.googlubuntu.com%2Fresults%2F%3Fcx%3D006238239194895611142%253Au-ocqbntw_o%26cof%3DFORID%253A9%26ie%3DUTF-8%26q%3Dsynaptic%2Bpackage%2Bmanager%26as_qdr%3Dall%26sa%3DGoogle%2BSearch%26lang%3Den%26siteurl%3Dhttp%253A%252F%252Fwww.googlubuntu.com%252F#gsc.tab=0&gsc.q=synaptic%20package%20manager&gsc.page=1](http://www.google.com/cse?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=synaptic+package+manager&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2F&ad=n9&num=10&rurl=http%3A%2F%2Fwww.googlubuntu.com%2Fresults%2F%3Fcx%3D006238239194895611142%253Au-ocqbntw_o%26cof%3DFORID%253A9%26ie%3DUTF-8%26q%3Dsynaptic%2Bpackage%2Bmanager%26as_qdr%3Dall%26sa%3DGoogle%2BSearch%26lang%3Den%26siteurl%3Dhttp%253A%252F%252Fwww.googlubuntu.com%252F#gsc.tab=0&gsc.q=synaptic%20package%20manager&gsc.page=1)

---

### Post by tojonukokhadush on 2012-09-01
thankyou Frogs Hair! i do have a next screenshot! seeing this i can guess these are required as a transition from 10.04 to 12.04! i would rather hide computer janitor from main menu as per your and expert's suggestions about computer janitor just to prevent myself from using it!
thanks again very much!

---

### Post by NikTh on 2012-09-01
> **tojonukokhadush said:**
> what if i removed these using computer janitor? is these necessary to upgrate my system from 10.04 to 12.04???

Hello. 

If you want to Upgrade from 10.04 to 12.04 , I suggest : 

1st. Disable ALL external Repositories (PPA) you may have been added in 10.04 (Software Sources - "Other Software")

2nd. BackUp all your important data to an External HDD - USB. 

3rd. Use bellow commands to clean up your system from unwanted - UN-configured  or/and mis-installed packages. 

```
sudo apt-get --purge autoremove
sudo apt-get autoclean && sudo apt-get clean all
sudo apt-get purge $(dpkg -l | awk '/^rc/ { print $2 }')
sudo find /var/lib/apt/lists/ -type f -delete
sudo apt-get update
```After that , you can proceed to Upgrade your 10.04 to 12.04 

You must have in mind that this Upgrade is BIG. I mean big changes. 
A better Idea might be a fresh install of 12.04. 

And leave the janitor in peace :P

Thanks

---

### Post by tojonukokhadush on 2012-09-01
thankyou very much! and since it is an old laptop, i needed an external dvd player coz 12.04 is not in compact disk i guess!  so i was expecting to network upgrade it!  what's the risk in that?

---

### Post by uRock on 2012-09-01
I use BleachBit. It cleans all of that stuff out and frees up space.

---

### Post by deadflowr on 2012-09-01
> **tojonukokhadush said:**
> what if i removed these using computer janitor? is these necessary to upgrate my system from 10.04 to 12.04???

First off, do you really want to upgrade to 12.04?
Have you read up the release notes for 12.04 ,yet?
Note that it is a night and day difference between the two releases. I hope you know this already.
Second, just follow Nikth's advice for preparing your system for the upgrade.

> **tojonukokhadush said:**
> thankyou very much! and since it is an old laptop, i needed an external dvd player coz 12.04 is not in compact disk i guess!  so i was expecting to network upgrade it!  what's the risk in that?

The standard iso from Ubuntu is around 693-698MB(at last check. 12.04.1) It fits on a CD, no need to get a external DVD Player.
I know this because I just burned a fresh copy last week on to a CD.

---

### Post by NikTh on 2012-09-01
> **tojonukokhadush said:**
> thankyou very much! and since it is an old laptop, i needed an external dvd player coz 12.04 is not in compact disk i guess!  so i was expecting to network upgrade it!  what's the risk in that?

Hello. 

You can download the .iso of 12.04 from here > [http://releases.ubuntu.com/12.04/](http://releases.ubuntu.com/12.04/) , 
I assume 32bit version (cuz you said "Old Laptop") and burn it to a usb / CD
Does your laptop have the ability to boot from Usb ? 

You can make a Live-bootable Usb , using Unetbootin > [http://unetbootin.sourceforge.net/#install](http://unetbootin.sourceforge.net/#install)

The risks.. hmmm.. not working after the upgrade completes.
Lot of changes.. GTK libraries , Gnome , Unity plugin ... and more.. must be done. But this is MY opinion. 
Canonical offers this upgrade , so you can do it. 
All above in my previous post is a little housekeeping before the upgrade. 

Thanks

---

### Post by tojonukokhadush on 2012-09-01
thank you all! you all have been so liberal to help! thanks!

---

