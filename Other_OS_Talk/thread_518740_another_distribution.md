---
title: "another distribution"
date: 2007-08-06
forum: Other OS Talk
---

### Post by ESPOiG on 2007-08-06
hey yall,

i wish to use another distribution, ubuntu is much to user friendly for me now, i like a challenge

im not sure what to use, ive heard good things about Arch and Zenwalk.

the problem is that ive had problems with Arch and install issues and it is annoying me, i have downloaded the latest Arch but im yet to install it, the major factor is that i have only a 1.5mb dsl connection and 10gig download limit and i cant afford to wait days for a distros like fedora

also i not concerned about wether it is debian based or what, but i dont want to go as far as that im using slackware

so any suggestions would be helpful,
thankyou

---

### Post by corney91 on 2007-08-06
I don't have much personal experience with different distros but [this]("http://www.zegeniestudios.net/ldc/") could help.

---

### Post by igknighted on 2007-08-06
> **ESPOiG said:**
> hey yall,

i wish to use another distribution, ubuntu is much to user friendly for me now, i like a challenge

im not sure what to use, ive heard good things about Arch and Zenwalk.

the problem is that ive had problems with Arch and install issues and it is annoying me, i have downloaded the latest Arch but im yet to install it, the major factor is that i have only a 1.5mb dsl connection and 10gig download limit and i cant afford to wait days for a distros like fedora

also i not concerned about wether it is debian based or what, but i dont want to go as far as that im using slackware

so any suggestions would be helpful,
thankyou

Fedora is a one disk liveCD like Ubuntu...

You might want to look at Debian Etch or Gentoo, both are great options.  Gentoo's download is only like 100mb, so that might be ideal.

---

### Post by Steve1961 on 2007-08-06
Try Debian or Slackware

---

### Post by ESPOiG on 2007-08-06
fedora is 1cd since wen :D, ill look at that thankyou there is only one problem with fedora the package manager last time i used it is very slow and crappy, but ill look into it now

ill try that test to thankyou

doesnt it sound weird to say i have 1.5mb dsl and it is crap just a few years ago all i could get was dialup, i shouldnt complain should i but australia isps are really crap along with the phonelines

thankyou

---

### Post by ESPOiG on 2007-08-06
just a quick q is the fedora live cd installable or not?

---

### Post by igknighted on 2007-08-06
> **ESPOiG said:**
> just a quick q is the fedora live cd installable or not?

Yes.  It has a different set of packages.  The only one that really confuses me that is not there is wget, but thats easy to add (yum install wget).  It also comes with Abiword/Gnumeric instead of OO.o (a nice change, IMO) and comes with no non-free software (including things Ubuntu includes, like madwifi), so be aware.  I recommend using the Livna repository (just download and double click the proper file from rpm.livna.org) and you can add non-free stuff from here.  While technically unofficial, Livna is maintained by Fedora devs and is generally considered the best repo for non-free software for Fedora.  There are other options (freshRPMs for example), but be careful if you choose to mix them, as they may conflict at times (hence the phrase RPM hell... kind of a misnomer because it has nothing to do with RPMs, but rather its a result of mixing repos that are not intended to be mixed and happens just as easily in Debian based and RPM based distros)

EDIT: Yum in Fedora 7 is fairly quick and much more tunable than apt.  I consider it the finest package manager available on linux, but as a Fedora user what do you expect :).  I do not use the GUI package tools at all though, and I have heard those are way behind synaptic.  You can install apt/synaptic and use that instead of yum if you prefer, or use the smart package manager.  Its up to you.

---

### Post by mips on 2007-08-06
Gentoo or Sabayon ?

---

### Post by dca on 2007-08-06
F7 did have a problem w/ auto-mounting USB thumb-drives, have they fixed that, yet?

---

### Post by igknighted on 2007-08-06
> **dca said:**
> F7 did have a problem w/ auto-mounting USB thumb-drives, have they fixed that, yet?

I think I heard something about one particular brand not working (kingston maybe?), but I have yet to find a thumb drive that doesn't work.  I regularly use a PNY Atache and some no-name promotional thumb drive (as well as an ipod nano and my WD MyBook external HD) and all are automounted properly.  With the new 2.6.22 kernels they appear to have made some significant changes, so perhaps the kingston drives now work, but I cannot tell you for sure.

PS, my sound (Nvidia MCP55 using HDA_INTEL driver) doesn't work in Ubuntu, have they fixed that yet?

---

### Post by fistfullofroses on 2007-08-06
How is Slackware too difficult? They have installpkg removepkg, netpkg, slapt-get all those package management tools... and then how hard is compiling from source ./configure make make install

---

### Post by ESPOiG on 2007-08-21
sorry was that Slackware comment directed at me, if so it aint that it difficult i guess i just not interested in that path for the moment, saying that i did find the distro for me :D

it is much like Slackware but aint, if you know what i mean Arch Linux is great pacman is a perfect package manager and with arch you only install what you want

my total install was around 400mb :D

thanks for all the help, of course ill keep running Ubuntu on the side

---

### Post by fistfullofroses on 2007-08-21
I recently tried Arch. It is pretty cool. BLAZINGLY FAST!!!!!!!!!!! Very nice. Slackware just has this special place in my heart because it was the first distribution I ever used, and has been the most secure and stable in my experience. I know what people mean though when they say that they do not like it. All of that stability comes at a cost. Tedium.

---

