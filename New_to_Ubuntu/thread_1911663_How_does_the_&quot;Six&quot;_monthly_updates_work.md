---
title: "How does the &quot;Six&quot; monthly updates work"
date: 2012-01-19
forum: New to Ubuntu
---

### Post by cliveT on 2012-01-19
Hi guys
 
What time of year do the "Six monthly" updates occur and how does it work -do they automatically install ?
 
Or do we get a choice and is it wise to keep updating or not?
 
Regards
 
Clive

---

### Post by sffvba[e0rt on 2012-01-19
Every April a X.04 gets released and every October a X.10.

Upgrading to these are optional but suggested if your current version will be coming to its end of life (Normal desktop releases are supported for 18 months and LTS releases for 3 years (but starting from 12.04 it will be for 5 years)).


404

---

### Post by Double.J on 2012-01-19
Hi there CliveT

They come out april and october - the next one is expected on the 26th April if I'm not mistaken.

there are two types, a regular release that's "supported" with new updates for packages for 6 months, and then security and bug fixes for 12 months after that (18months total) And LTS (Long Term Support) releases that previously had 3 years of hardware and bug /security updates, but will be going to 5 years at the next release.

The current release is 11.10, and the current LTS is 10.04. By using the numbers of the releases rather than the animal related names of the release we can see when they were released:
10.04 - April 2010
11.10 - November 2011

What does LTS matter if it doesn't keep updating it's packages throughout its life? - Well the Idea is that this is the most stable version of ubuntu, aimed at those who do not need the latest thing, but require a very stable as bug free as possible system - i.e. business. 

For this reason Ubuntu released Unity to the desktop 1 year prior to the LTS, and the linux 3 kernel 6 months before - we still get the latest things, but there is plenty of time to test and perfect before the LTS is released in April - Don't expect as large changes in April as there has been in the last couple of releases.

As a testimony to this 12.04 is still at the Alpha 1 milestone on my machine (there are 3 more before final release) and Almost everything is working for me - this is quite rare in distro releases, often things don't start to come together until the beta/RC stage :)

As I say 12.04 is both the next release and an LTS - it will be supported for 5 years. That said if you run a server or business, it would be common to keep using 10.04 until nearer the end of it's life then switch to 12.04 several months to a year after release to ensure kinks are ironed out.

As for upgrade/re-install, I think the majority of people upgrade, judging by the posts, but a re install is often recommended - many users create a separate /home partition so that they just add this back into their new install :)

Hope it helps!

---

### Post by cliveT on 2012-01-19
gnu/mirow -you said
 
As for upgrade/re-install, [COLOR=red]I think the majority of people upgrade[/COLOR], judging by the posts, but a [COLOR=red]re install is often recommended[/COLOR] - many users create a separate /home partition so that they just add this back into their new install :smile:
 
[COLOR=black]So which is better to do? Upgrade or Re-install?[/COLOR]
 
For me if its quicker I`d rather just upgrade if its safe and wont cause any problems!

---

### Post by Double.J on 2012-01-19
It varies from computer to computer; most people don't have any problems, But as I say we recommend a re-install as the risk is less. But at the end of the day, so long as you back up your home directory, then if an update completely borked... you could just re-install anyway?

I don't expect many issues updating to 12.04 from 11.10 - a lot of people seem to have had difficulty going from 10.X to 11.10, but I think this is because of the massive amount of changes.

If you do an upgrade, it's best to give it a week after the release of the final (just in case there were any massive bugs). it also depends where you're updating from, upgrades should only go to the next release, so 
10.04>10.10>11.04>11.10>12.04

Though If you were coming all the way from 10.04, just re-install ,it's not only safer, it'll be quicker too! 

Always install all available updates prior to an upgrade :)I have found in the past it's helpful to disable proprietary drivers - such as graphics and set them back up again "on the other side"

Hope it helps :)

Personally I just reinstall.. but that's just me!

---

### Post by cliveT on 2012-01-19
> **gnu/mirow said:**
> It varies from computer to computer; most people don't have any problems, But as I say we recommend a re-install as the risk is less. But at the end of the day, so long as you back up your home directory, then if an update completely borked... you could just re-install anyway?
 
I don't expect many issues updating to 12.04 from 11.10 - a lot of people seem to have had difficulty going from 10.X to 11.10, but I think this is because of the massive amount of changes.
 
If you do an upgrade, it's best to give it a week after the release of the final (just in case there were any massive bugs). it also depends where you're updating from, upgrades should only go to the next release, so 
10.04>10.10>11.04>11.10>12.04
 
Though If you were coming all the way from 10.04, just re-install ,it's not only safer, it'll be quicker too! 
 
Always install all available updates prior to an upgrade :)I have found in the past it's helpful to disable proprietary drivers - such as graphics and set them back up again "on the other side"
 
Hope it helps :)
 
Personally I just reinstall.. but that's just me!
 
Thanks gnu/mirow
 
I`m fairly new to using computers in general so forgive my ignorance and the very basic questions I ask!
 
To reinstall what would be the procedure please?
 
How would you "back-up" your Home/directory etc. etc.

---

### Post by Double.J on 2012-01-19
> **cliveT said:**
> Thanks gnu/mirow
 
I`m fairly new to using computers in general so forgive my ignorance and the very basic questions I ask!
 
To reinstall what would be the procedure please?
 
How would you "back-up" your Home/directory etc. etc.

Don't worry at all - always ask, at one time or another every single person in this forum had never heard of Linux ;)

There are two ways - through the terminal using apt, or through the update manager. I don't typically used the update manager, but I did notice the other day that Ubuntu are recommending the update manager, so I'll advise that method.

As usual do your pre upgrade update in the terminal;
```

sudo apt-get update && sudo apt-get upgrade
```

Then open the update manager. Once a newer version is available, it will say so above the box where updates are usually shown; it'll look something like
> 
A new version "11.10" is available
just click the upgrade button next to it and then enter your password.

---

### Post by cliveT on 2012-01-19
Thank you so much for your kind words and advice -much appreciated.
 
Clive :D

---

