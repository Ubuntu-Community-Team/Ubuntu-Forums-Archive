---
title: "How do I upgrade from 10.04 to 12.04?"
date: 2012-06-16
forum: New to Ubuntu
---

### Post by Old Jimma on 2012-06-16
Hi Community:

I'm just an old man and want to find out how to upgrade from 10.04 to 12.04.

I've backed everything up and am ready for Unity!

;)

Could someone kindly
[LIST]
[*]suggest an easy way to do this,
[*] I have backed everything up on another HD. Should I unmount that HD during the upgrade?
[*] I have / (root) , /swap, and grub and an SSD and /home on another HD. Will the automatic upgrade be smart enough to account for this?
[*]indicate the types of problems I might have when I do this (eg, will all of the programs I use be installed? Will the crontab I was using still be functional?)
[*]indicate whether a fresh install is preferable.
[/LIST] 



Doing fresh installs of new LTS's is getting a little hard on my old bones! :redface:

But I'm still on the Ubuntu bus! :-\"
 
Thanks!
Phil de Duluthistan

---

### Post by sudodus on 2012-06-16
I think the easiest way is to wait for approximately another month. Then we expect that an automatic update will be offered from the old 10.04 LTS to the new 12.04 LTS version. (It was like that from 8.04 LTS to 10.04 LTS.)

The reason for the delay is that the worst bugs should be found and removed, so that the LTS user should have a smooth ride.

---

### Post by Paqman on 2012-06-16
> **Phil Smith said:**
> 
[LIST]
[*]suggest an easy way to do this,
[*] I have backed everything up on another HD. Should I unmount that HD during the upgrade?
[*] I have / (root) , /swap, and grub and an SSD and /home on another HD. Will the automatic upgrade be smart enough to account for this?
[*]indicate the types of problems I might have when I do this (eg, will all of the programs I use be installed? Will the crontab I was using still be functional?)
[*]indicate whether a fresh install is preferable.
[/LIST] 


[list=1]
[*]Update Manager can handle this.
[*]No need to unmount anything
[*]Yes, it will preserve all your current partitioning scheme.
[*]Everything should work as it did before. Where it might fall down is any customisations or tweaks you've made, which will either get ridden over roughshod, or will cause some breakage. The closer your system is to the default, the more smoothly the upgrade will go.
[*]That's personal preference. Personally I tend to upgrade, but some swear by reinstalls. I'm of the opinion that those who claim upgrades are unreliable are doing so on the basis of outdated information. Upgrade used to be flaky, but aren't these days.
[/list]

---

### Post by Old Jimma on 2012-06-16
Thanks, sudodus and Paqueman for your replies!

Among the big reasons why I'm sticking with Ubuntu is the expert advice available on the Ubuntu forums. 

On the Ubuntu forums I get replies to my queries that 
[LIST]
[*]provide specific information that directly address my questions,
[*]accurate,
[*]useful, and
[*]friendly!
[/LIST]

[COLOR="Blue"]**There are no other forums like the Ubuntu forums!**[/COLOR]

:smile:

Many thanks!
Phil de Duluthistan

---

### Post by mparillo on 2012-06-16
> **Phil Smith said:**
> 
[COLOR=Blue]**There are no other forums like the Ubuntu forums!**[/COLOR]

:smile:

Many thanks!
Phil de Duluthistan

+1. Without minimizing Canonical's upstream contributions, facilitating the xbuntu way is IMHO the biggest contribution they return to the Linux community. You seldom see RTFM or GIYF around here. I appreciated that long before I got around to signing the code of conduct over on Launchpad.

---

### Post by waynefoutz on 2012-06-16
If you already have your /home on another drive, the easiest way, in my opinion, is to do a fresh install and reinstall all your applications. Using the Update Manager to go from one release to another takes 2-3 hours, even if you have a fast internet connection. You can do a fresh install in less than 15 minutes. 

As for going from one LTS to another, my last attempt, going from 8.04 to 10.04, resulted in a slow booting, bloated mess. I ended up doing a fresh install anyway, and chalked up the wasted afternoon as a learning experience.

---

### Post by Paqman on 2012-06-16
> **waynefoutz said:**
> You can do a fresh install in less than 15 minutes. 


Plus the time it takes to download the ISO, which is probably about the same it takes to download all the packages for an upgrade anyway.

Using a fresh ISO from a torrent is worthwhile around relase day when the repos are slow, but the rest of the time I don't think there's much in it either way.

---

### Post by waynefoutz on 2012-06-16
> **Paqman said:**
> Plus the time it takes to download the ISO, which is probably about the same it takes to download all the packages for an upgrade anyway.

Using a fresh ISO from a torrent is worthwhile around relase day when the repos are slow, but the rest of the time I don't think there's much in it either way.

You're probably going to download the same amount of data either way, after updating your applications after a fresh install. But it's my experience with Update Manager is that it's messy and slow. 
Going from one LTS to another compounds that problem even more. For me, going from 8.04 to 10.04 left me without a computer for the better part of a day and the result was a barely usable system. 
The OP even has his /home on another drive, which makes the fresh install option even more simpler.

---

### Post by Paqman on 2012-06-16
> **waynefoutz said:**
> You're probably going to download the same amount of data either way, after updating your applications after a fresh install.

If you're not put off by a command line, using the minimal image can avoid this. You'll only download the latest packages.

---

