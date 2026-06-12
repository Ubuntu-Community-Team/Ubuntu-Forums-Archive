---
title: "Laptop not going in to hibernation when the lid is shut, since upgrade to 11.10"
date: 2012-02-29
forum: New to Ubuntu
---

### Post by HeyLynx on 2012-02-29
Hello all

Was hoping that you could help, since the upgrade, via package manager, my toshiba laptop no longer goes into hibernation when you close the lid.  The old version was 11.04

Hibernation works well from the menu and worked fine before.

Thanks for the help.

---

### Post by musicman10489 on 2012-02-29
Perhaps this can be of some assistance? 
[http://askubuntu.com/questions/70140/closing-lid-does-not-suspend-laptop](http://askubuntu.com/questions/70140/closing-lid-does-not-suspend-laptop)

---

### Post by HeyLynx on 2012-03-01
Thanks but lubuntu doesn't seem to have that option in the file menus.

---

### Post by musicman10489 on 2012-03-01
Is there a way you can get to any sort of **Power Management** settings? Because according to ([this]("https://wiki.ubuntu.com/Lubuntu/Announcement/11.10")) you *should* have **xfce4-power-manager** installed which from what I'm reading allows you set the proper option to hibernate on lid close. 

Or is the issue you have already configured the power manager to do so and your machine simply doesn't do it?

*Edit:*([This]("http://askubuntu.com/questions/71033/closing-the-lid-isnt-toggeling-standby-anymore-after-update-in-lubuntu-how-can")) is the "reading" that I am referring to. You may or may not find it useful.

---

### Post by HeyLynx on 2012-03-01
When I do the sudo leafpad command it opens an empty file with nothing in it.

Sorry if I'm being odd, this was an update and now wishing that I hadn't done it.

---

### Post by dFlyer on 2012-03-01
What does free -tom say form the command line about your swap file. It needs to be at least the same size of your ram installed to hibernate.

---

### Post by musicman10489 on 2012-03-01
> **HeyLynx said:**
> When I do the sudo leafpad command it opens an empty file with nothing in it.

Sorry if I'm being odd, this was an update and now wishing that I hadn't done it.

Nah, you're fine. Perhaps you can try searching to see if that file is for some reason located in a different place than suggested in the link.

I'm not running lubuntu so I apologize for the limited help I can offer. Luckily, there are plenty of folks around here like *@dFlyer* who have far more experience with linux systems than I do.

---

### Post by HeyLynx on 2012-03-04
output from free -tom

```
       total       used       free     shared    buffers     cached
Mem:           495        443         52          0          3         90
Swap:          508        101        407
Total:        1004        544        460
```

---

### Post by Azyx on 2012-03-07
HeyLynx.
I have problem to find the Power-manager..And have now find that Lubuntu 11.10 use xfce4-power-manager. I can not find Power-management in the menues :(

But I have find it now :) I click on Lulubuntu (logo)-->Run and there type 'xfce4-power-manager' and a little symbol appear in the panel. If you right-click the symbol and select Preferences, you may change setting for power safe on your computer. Hope this help? It helped me :) 
/Cheers

---

### Post by HeyLynx on 2012-03-07
Ah it says file not found.  Maybe I should load it.

Look at the package manager gnome is loaded but not the xfce power manager, will see what happened.

---

### Post by Azyx on 2012-03-07
Because you made an upgrade, maybe you not get xfce4-power-manager installed. I don't know how well gnome power manager work with 11.10, so I you don't can run it you should try to install xfce4-power-manager.

Open a Accesories-->LXterminal (Not Leafpad) and type:

```
sudo apt-get install xfce4-power-manager
```

And type you password, or you can install it from synaptic.

---

### Post by HeyLynx on 2012-03-07
Hello

Installed with package manager... but still not anywhere on the menus.  This is Lubuntu by the way.

But it is running in task manager......

---

