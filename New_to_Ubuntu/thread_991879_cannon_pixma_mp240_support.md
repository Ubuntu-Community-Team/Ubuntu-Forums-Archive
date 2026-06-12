---
title: "cannon pixma mp240 support?"
date: 2008-11-24
forum: New to Ubuntu
---

### Post by waxyfresh on 2008-11-24
Anyone know how to get this working?

---

### Post by cozmicharlie on 2008-11-24
Cannon itself does not support Linux but a number of drivers are available.  Does the printer show up when you plug it in (go to menu>systems>administrative>printing)?  If so you need to see if the drivers are available.   Right click on the printer and a dialogue opens.  Go to "make/model" and click on change.  This should bring up a list of drivers.  Check to see if your model is in the list.  If it isn't don't panic you may still be able to use one of the other drivers.  If your particular driver is not listed, type in the printer name and model in the search for the forums and see if anyone has posted an alternative driver that works.  If they have use it, if not you may just have to go down the list and see if one works.  Start with a printer that has a similar model.

Hope this helps

---

### Post by rmockler on 2008-11-24
The link below worked for me.  

[http://support-au.canon.com.au/EN/se...os%3d%3dLinux&](http://support-au.canon.com.au/EN/se...os%3d%3dLinux&)

Sorry about the link above, try the one below.....

[http://www.canon.com.au/drivers/default.aspx](http://www.canon.com.au/drivers/default.aspx)

---

### Post by cozmicharlie on 2008-11-24
> **rmockler said:**
> The link below worked for me.  

[http://support-au.canon.com.au/EN/se...os%3d%3dLinux&](http://support-au.canon.com.au/EN/se...os%3d%3dLinux&)

The link goes to canon but it says "page not found".  You may want to check the link.  Maybe they moved the page.

---

### Post by C.S.Cameron on 2008-11-24
Had a HP 1310 that was plug and play in Ubuntu, it busted.
Tried the Pixma MP 240 and could not find working drivers.
I plan on returning it today, but will wait to see if you get any good answers.

---

### Post by waxyfresh on 2008-11-24
> **cozmicharlie said:**
> Cannon itself does not support Linux but a number of drivers are available.  Does the printer show up when you plug it in (go to menu>systems>administrative>printing)?  If so you need to see if the drivers are available.   Right click on the printer and a dialogue opens.  Go to "make/model" and click on change.  This should bring up a list of drivers.  Check to see if your model is in the list.  If it isn't don't panic you may still be able to use one of the other drivers.  If your particular driver is not listed, type in the printer name and model in the search for the forums and see if anyone has posted an alternative driver that works.  If they have use it, if not you may just have to go down the list and see if one works.  Start with a printer that has a similar model.

Hope this helps



My printer is listed but dosent print a test page,nor does my scanner work.

The printer is fine and know to work perfect.

---

### Post by halitech on 2008-11-24
according to [www.linuxprinting.org](www.linuxprinting.org), it's not even on the list but the mp 210 is supposed to partially work. the driver *might* work for you as well

[http://support-au.canon.com.au/contents/AU/EN/0100083403.html](http://support-au.canon.com.au/contents/AU/EN/0100083403.html)

---

### Post by cozmicharlie on 2008-11-24
> **waxyfresh said:**
> My printer is listed but dosent print a test page,nor does my scanner work.

The printer is fine and know to work perfect.

OK - follow the advice of halitech and use the mp 210 driver.  You switch drivers in the printer make & model dialog.  Where it says "make & model" click on the "change" button and select the driver halitech recommended then try to print a test page.

---

### Post by SunnyRabbiera on 2008-11-24
just turn it in for a HP, HP works better and besides cannon sucks except for cameras

---

### Post by sirwilliamthenice on 2008-12-05
I've been searching every few days for this.. and finally it popped up

canon now have a 32 bit debian driver.. not yet tried.. but hopefully work for any debian based distro.. 

cheers . 

****************************************************

they also have an rpm at the bottom of the page.
[I][B][U]

I checked back a few hours later and the drivers had been removed. so i edited the link out.. i still have them. but i don't know the forusm rules about sharing such things. 
are the canon drivers gpl?[/U][/B][/I]

---

### Post by cozmicharlie on 2008-12-05
Excellent - post back and let us know if it worked for you.

---

### Post by sirwilliamthenice on 2008-12-06
Solution is here!

Icore skippy got it going on this thread

[http://ubuntuforums.org/showpost.php?p=6316300&postcount=11](http://ubuntuforums.org/showpost.php?p=6316300&postcount=11)

Good luck peeps

---

### Post by waxyfresh on 2009-02-13
Thanks! But it dosent seem to be working i downloaded the pacakge and installed all the debs but still no scanner support..

---

### Post by teejay17 on 2012-04-28
There's a PPA: [https://launchpad.net/~michael-gruz/+archive/canon](https://launchpad.net/~michael-gruz/+archive/canon)

```
sudo add-apt-repository ppa:michael-gruz/canon
sudo apt-get update
sudo apt-get install cnijfilter-common cnijfilter-mp240series
```

---

