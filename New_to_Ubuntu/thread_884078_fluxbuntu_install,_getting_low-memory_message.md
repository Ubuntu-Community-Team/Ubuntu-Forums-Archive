---
title: "fluxbuntu install, getting low-memory message"
date: 2008-08-08
forum: New to Ubuntu
---

### Post by grumol on 2008-08-08
greetings, and thanks for being here -- not much happening on the fluxbuntu forum, so i'm trying here -- i'm doing an install on a thinkpad with 32mb ram, which is the minimum for fluxbuntu, but i keep getting the message that the machine doesn't have enough memory, and needs a minimum of 32mb -- windows 95 is on it now, and i just want to get rid of that, replace it with fluxbuntu -- is this message i'm getting correct?

bob

---

### Post by snowpine on 2008-08-08
> **grumol said:**
> greetings, and thanks for being here -- not much happening on the fluxbuntu forum, so i'm trying here -- i'm doing an install on a thinkpad with 32mb ram, which is the minimum for fluxbuntu, but i keep getting the message that the machine doesn't have enough memory, and needs a minimum of 32mb -- windows 95 is on it now, and i just want to get rid of that, replace it with fluxbuntu -- is this message i'm getting correct?

bob

Hi Bob, I've never heard of anyone installing Fluxbuntu on 32mb; I've always heard that 64mb was the minimum, but I haven't been able to get the terminal working right on 64mb (I have a thread open both here and on the Fluxbuntu forums, but nobody has posted any suggestions yet:(). I would recommend 96mb as the "comfortable minimum." 

I am a big Fluxbuntu fan, so I will be following this thread in case you learn anything from your experiment. Unfortunately I do not know of anything in the current *Buntu family that is 32mb-friendly; that is DSL territory. Good luck!

---

### Post by rossjman1 on 2008-08-08
I would suggest DamnSmall Linux, which has Fluxbox installed by default (then in the menus there's an option to enable apt and synaptic). Or Puppy Linux which has a special XFCE DE on it.
[http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/)
[http://www.puppylinux.org/home](http://www.puppylinux.org/home)

---

### Post by st33med on 2008-08-08
Puppy Linux might not be the best to use... It uses 128MB of memory.

DSL is your most likely candidate. The disc installs on the hard drive using only 50MB of memory, and I can guarantee it will work on 32 MB of RAM because I did that to an old IBM Aptiva.

---

### Post by InfinityCircuit on 2008-08-08
Alternatively, if you need a 2.6.x kernel/you want something newer than DSL, you can try just installing Debian.  If you load it with "expert" for the mode you can install the lowmem udeb which will install on 32M.

---

### Post by grumol on 2008-08-08
thanks, i have dsl here and will give that a try

---

### Post by snowpine on 2008-08-10
Hi Grumol, I believe that it's possible to install Debian on your 32mb machine and then build a "fluxbuntu remix" that uses a combination of packages from the Debian repository and artwork and settings from the Fluxbuntu install CD. Is this something you'd be willing to help me test, or are you happy with DSL? Are you interested in Fluxbuntu specifically, or just something that works well on that computer?

---

### Post by grumol on 2008-08-10
snowpine - obviously, i don't know what i'm doing, but knew enough to choose linux -- for my first experience with it, i would have liked to use ubuntu, because of what appears to be incredible support, but of course, soon realized that my computers don't have what it takes -- so i got fluxbuntu, which seems fine to me, but won't go on the 760xl, but will go fine on the 600e(it is currently dual booted with win2k) -- no big reason for choosing fluxbuntu, just that it worked, and had access to the ubuntu repositories, though not the support as there is for ubuntu -- and once i chose fluxbuntu, thought it would be nice to have the same distro on both laptops 

 since i had already gotten rid of win95 on the 760, i needed something, and as you guys advised, i installed dsl, or tried to -- i'm having display problems, but thats another matter

so to be honest, i'm still too new to this to be happy or sad with dsl, assuming i get it installed, or with fluxbuntu -- i would just like to put something on the 760, and so, sure, i'm open to anything you might suggest -- if it doesn't work, or screws things up, its no big deal, and we've both learned something?

i also tried the "low-memory" install of the ubuntu 7.10 alternate cd, but same as with fluxbuntu, i get the "not enough memory, need atleast 32mb" -- which i don't understand, since i have 32mb(just)

my laptops: thinkpad 760xl/2gb hd/32mb/166mhz
                     600e/6gb/130mb/366mhz
both using orinico card for wireless

---

### Post by snowpine on 2008-08-10
> **grumol said:**
> snowpine - obviously, i don't know what i'm doing, but knew enough to choose linux -- for my first experience with it, i would have liked to use ubuntu, because of what appears to be incredible support, but of course, soon realized that my computers don't have what it takes -- so i got fluxbuntu, which seems fine to me, but won't go on the 760xl, but will go fine on the 600e(it is currently dual booted with win2k) -- no big reason for choosing fluxbuntu, just that it worked, and had access to the ubuntu repositories, though not the support as there is for ubuntu -- and once i chose fluxbuntu, thought it would be nice to have the same distro on both laptops 

 since i had already gotten rid of win95 on the 760, i needed something, and as you guys advised, i installed dsl, or tried to -- i'm having display problems, but thats another matter

so to be honest, i'm still too new to this to be happy or sad with dsl, assuming i get it installed, or with fluxbuntu -- i would just like to put something on the 760, and so, sure, i'm open to anything you might suggest -- if it doesn't work, or screws things up, its no big deal, and we've both learned something?

i also tried the "low-memory" install of the ubuntu 7.10 alternate cd, but same as with fluxbuntu, i get the "not enough memory, need atleast 32mb" -- which i don't understand, since i have 32mb(just)

my laptops: thinkpad 760xl/2gb hd/32mb/166mhz
                     600e/6gb/130mb/366mhz
both using orinico card for wireless

Grumo, here is my theory. Fluxbuntu (and the Alternate CDs for Ubuntu, Xubuntu, etc.) borrowed its text based installer from Debian Linux. Debian is a little bit "lighter" than the current Ubuntu, so its base system will install with 32mb. The error message that you're seeing is a "relic" from the installer's Debian origins. 

I think DSL is a good choice for you, if you can get it working. If you're looking for a fun DIY project, I think you could install Debian (the base system, without the desktop environment), then install fluxbox and your choice of light-weight applications to build a very efficient little system. Because Fluxbox is configured with text files in your ~/.fluxbox folder (keys, menu, startup, etc.), you can copy and paste these files from your Fluxbuntu laptop to your Debian laptop. It would be a good learning experience for you, but definitely not as "plug and play" as DSL. It also would not accomplish your goal of using the Ubuntu repositories--that may be impossible for you. :(

---

### Post by grumol on 2008-08-10
snowpine - a part of me wants to try out the debian idea, as i can see i would learn a lot from that -- but on the other hand, i think i should learn how to work out these display issues on dsl, and i suppose its the "safer" approach -- and since i won't have access to the repositories anyway -- although its a bit more difficult because i can't post on the dsl board, even though i'm registered -- must be a waiting period -- but if it doesn't work, i'd like to try your theory - thanks

---

### Post by snowpine on 2008-08-10
I suggest you start a new thread with your DSL display issues, with a descriptive title so the experts can find it. Good luck!

---

