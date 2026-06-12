---
title: "Problems installing flash"
date: 2008-07-29
forum: New to Ubuntu
---

### Post by mczonie on 2008-07-29
When I go to a site that requires flash, Firefox isn't showing the yellow install bar I need to install it. I think I unwittingly disabled it somehow. Anyone know how I can re-enable it?

TIA.

---

### Post by MatthewPlanchard on 2008-07-29
On second thought, check out this guide:

[_How to Install Flash_]("http://www.psychocats.net/ubuntu/flash")

If that doesn't work, try

```
sudo apt get install libflashsupport flash-plugin-nonfree
```

There's probably a couple more you can install to make sure it works. Search the forums, too, dude. Tons of people have flash problems.

---

### Post by tuxxy on 2008-07-29
You may already have it installed and just need to link to it in your firefox plugins folder, another method I would recommend is to install the ubuntu-restricted-extras package if you didnt already, this will install you Flash among other things like codecs, mp3, dvd etc.

```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by mczonie on 2008-07-29
> **MatthewPlanchard said:**
> On second thought, check out this guide:

[_How to Install Flash_]("http://www.psychocats.net/ubuntu/flash")

If that doesn't work, try

```
sudo apt get install libflashsupport flash-plugin-nonfree
```

There's probably a couple more you can install to make sure it works. Search the forums, too, dude. Tons of people have flash problems.

Didn't work.

---

### Post by tuxxy on 2008-07-29
```
sudo apt-get install flash-plugin-nonfree
```

---

### Post by aysiu on 2008-07-29
Ubuntu makes use of the *ubufox* package for integrating with Firefox to prompt for missing plugins. Make sure in System > Administration > Synaptic Package Manager that *ubufox* is installed.

---

### Post by Liakath on 2008-07-30
> **tuxxy said:**
> ```
sudo apt-get install flash-plugin-nonfree
```

The package is: flashplugin-nonfree (no "-" in flashplugin)

Liakath

---

