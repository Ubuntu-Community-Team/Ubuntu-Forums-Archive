---
title: "Upgrading Gutsy to Hardy -- WINE?"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by zuhl on 2008-04-27
When I upgrade from Gutsy to Hardy, what do I do with WINE?  Can I just update the repository location or do I have to unistall it then reinstall it from the new repository? Or anything else?

Thanks

---

### Post by scragar on 2008-04-27
repo location should update automaticaly. And then it should update fine after the upgrade.

---

### Post by nowshining on 2008-04-27
if you want you can use the one from winehq.com :) the main site for WINE. That's what I use. Also you'll get updates to newer Versions of WINE when they come out.

---

### Post by JoshuaRL on 2008-04-28
> **scragar said:**
> repo location should update automaticaly. And then it should update fine after the upgrade.

True, if you want the same version of Wine for about 6 months.  The Ubuntu repos use the same version during the whole release, allowing a stable version.  In Hardy's case that would be version 0.9.59.  What this doesn't do is allow you to have a fully updated version in the mean time.  In fact, Wine is already at 0.9.60, so its a version behind after only a couple days.

And from what I can tell, Wine will only get better in the next couple months.  I'm sure the Wine devs are pouring over the hundreds of thousands of pages of Windows APIs that Microsoft recently released.  I'm really looking forward to what's coming down the road.

> **nowshining said:**
> if you want you can use the one from winehq.com :) the main site for WINE. That's what I use. Also you'll get updates to newer Versions of WINE when they come out.

Yep, that's the way I use and suggest to others.  Not as easy as using Add/Remove, but a better experience all in all.  The full install/upgrade instructions can be found [here,](http://www.winehq.org/site/download-deb) but it can be boiled down to three steps:

[B]Upgrade HOWTO for Wine in Hardy
[/B]
1).  Install the Wine repostitory's key to the trusted list of APT keys by putting the following command into the terminal:
```

wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -

```

2).  Add the Wine repostitory to your APT list:
```

sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/hardy.list -O /etc/apt/sources.list.d/winehq.list

```

3).  Make sure Wine is the newest version:
```

sudo apt-get install --reinstall wine

```

That should make sure your version of Wine is the latest and greatest, and that it will continue to be.  A word of caution, Wine may sometimes be unstable on the latest version.  I haven't ever had any specific problems I can trace back to that, but it's a good thing to keep in mind.

Hope that helps.

---

