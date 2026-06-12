---
title: "Ubuntu Hardy 64-bit - Could not install Wine - E: Broken packages"
date: 2008-05-04
forum: New to Ubuntu
---

### Post by Th3_uN1Qu3 on 2008-05-04
Wow, been more than an year since i've last been here. I miss that P2B-DS mobo a lot, got fried due to a power surge back last year in March. But anyway, let me get to the topic. 

Built a new C2D computer a few months ago and had 2 8600GTs die on me, while i send the 2nd one to warranty i got a Radeon X300SE so i could at least use the computer. And as i can't game much on it, i thought i should play around with Ubuntu a bit more. 

Downloaded the last 64-bit version and burned it, not really needed 64-bit as i have only 2GB of RAM, but i just wanted to see how it runs. Just about everything including Compiz works great right out of the box, but i can't seem to be able to install Wine. I followed the instructions [here](http://www.winehq.org/site/download-deb), but when i get to clicking the link for the package (or when i type sudo apt-get install wine in a terminal), the following error message is displayed:

```
ubuntu@Kaori:~$ sudo apt-get install wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  wine: Depends: binfmt-support (>= 1.1.2) but it is not installable
        Depends: ia32-libs (>= 1.6) but it is not installable
        Depends: lib32nss-mdns (>= 0.10-3) but it is not installable
E: Broken packages
```

Any suggestions? Or does it just not work on 64-bit Ubuntu and i'll have to use the 32-bit one?

Off-topic: All desktop Linux i've been running in the meantime was the lightweight Puppy Linux on my PIII laptop, but i dropped that in favor of windows me (and no, it's not that bad if configured well and thank God i found the MSFN forums) because of issues with the crappy trident drivers. I seem to be luckier with Ubuntu as it has Compiz running right out of the box. Hope i'll get everything working okay, and maybe it'll get in my multi-boot, along with XP and vista. Though i don't know why i keep vista, it sucks, i use XP 99.9 of the time.

---

### Post by gsmanners on 2008-05-04
Those packages it complains about are in the normal "universe" repo. I assume you disabled that somehow. Make sure those are enabled, then install wine again. 64-bit does not exclude anything but the most obscure closed source apps, and even many of those can be included with some simple workarounds.

[http://ubuntuguide.org/wiki/Ubuntu:Gutsy#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#How_to_add_extra_repositories)

---

### Post by Th3_uN1Qu3 on 2008-05-04
Come to think of it, it did say something about universe. I dunno how that got disabled, maybe because i changed the host name?

Anyway, i'll reboot now and give it a try. Thanks.

Edit: Now installing, thank you. I think the CD didn't read properly last time as it was the only blank disc i found around and it wasn't in very good condition when i burned it.

Another edit: Wine is now installed okay and works. Thank you very much. :)

---

