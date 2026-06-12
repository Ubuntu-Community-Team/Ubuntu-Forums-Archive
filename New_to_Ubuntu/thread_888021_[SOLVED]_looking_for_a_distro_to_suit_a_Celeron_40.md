---
title: "[SOLVED] looking for a distro to suit a Celeron 400 with 256Mb Ram"
date: 2008-08-12
forum: New to Ubuntu
---

### Post by stinger30au on 2008-08-12
Can anyone suggest a linux distro i can use on an ooooolllllddddd pc of mine.

its a celeron 400 with 256 meg of ram and 12 gig hdd and dvd burner just for fun.
i think i have a spare 20 gig hdd kicking round i can throw at it to make it even more super duper if needed :-))

i need it to have internet access, samba and CUPS or better and an o/s that does not bog this thing down so much it takes an eternity to do anything what so ever


any ideas????

---

### Post by halitech on 2008-08-12
there are a few, puppy linux and dsl seeming to be the most popular around these parts. I just installed dsl on a P1 266 with 96 meg of ram and while I won't say it flies, it does run pretty good (other then playing movies from the cd rom, darn 4x cd)

edit: xubuntu might even play nicely on it depending on what you consider to be acceptable speed :)

---

### Post by dje on 2008-08-12
try [crunchbang linux]("http://crunchbang.org/projects/linux/"), an ubuntu based distro using the lightweight openbox window manager

dje

---

### Post by starcannon on 2008-08-12
I really like [[SIZE="4"][COLOR="DarkOrange"]Fluxbuntu[/COLOR][/SIZE]]("http://fluxbuntu.org/") for old hardware.

---

### Post by Bigbob22 on 2008-08-12
If you're an intermidiate linux user, try out Arch linux. It's faster than Ubuntu, but your computer has to have a i686 proccessor. more info: [http://www.archlinux.org/](http://www.archlinux.org/)

---

### Post by NoWayBill on 2008-08-12
TinyFlux is another lightwieght distro.

The problem you may find with the light/feather-wieght distros is with your hardware.
Being small has it's advantages and disadvantages.
The disadvantage being light on hardware support.

DSL is not intended for HD install and is based off of an old version of Knoppix, so it will install MOST .deb packages but not all.
As stated above it uses an "old" kernel so not all "new" packages are compatible.
Although it does have an installer the devs don't recommend it.
I installed it on old laptop PII 266mhz 256m RAM 8g HD, it ran well except the audio.

Puppy is it's own beast completely.
Audio worked, but could never get PCMCIA networking to go.

Ended up using a stripped down Debian stable and running with xFCE.

---

### Post by OutOfReach on 2008-08-12
Maybe Fluxbuntu or something like Wolvix?

---

### Post by tango_ninja on 2008-08-12
my vote goes to Puppy linux [here]("http://www.puppylinux.org/")

---

### Post by kerry_s on 2008-08-12
debian, custom install if your linux adept, if not xfce4 version runs fine.
my laptops 450mhz 256mb ram and 12gig hd.

xfce4 version:
[http://cdimage.debian.org/debian-cd/4.0_r4a/i386/iso-cd/debian-40r4a-i386-xfce-CD-1.iso](http://cdimage.debian.org/debian-cd/4.0_r4a/i386/iso-cd/debian-40r4a-i386-xfce-CD-1.iso)

net installer, straight install gives you gnome, but you can also use it to do a custom install just unselect everything at package selection:
[http://cdimage.debian.org/debian-cd/4.0_r4a/i386/iso-cd/debian-40r4a-i386-businesscard.iso](http://cdimage.debian.org/debian-cd/4.0_r4a/i386/iso-cd/debian-40r4a-i386-businesscard.iso)

---

### Post by cariboo on 2008-08-12
NoWayBill, I guess you haven't used DSL lately, I just installed it on a old P1 with 128MB ram, You can set it up on hard hard via the setup menu, and you can also enable apt via a menu selection.

DSL would be a great choice to run on a 400Mhz Cpu with 256MB ram, on something like that it would be smokin` fast.

Jim

---

### Post by halitech on 2008-08-12
> **cariboo907 said:**
> NoWayBill, I guess you haven't used DSL lately, I just installed it on a old P1 with 128MB ram, You can set it up on hard hard via the setup menu, and you can also enable apt via a menu selection.

DSL would be a great choice to run on a 400Mhz Cpu with 256MB ram, on something like that it would be smokin` fast.

Jim

+1 

I just installed it on an old Toshiba Tecra 550cdt laptop, P266 96meg of ram, 4 gig hard drive and everything is working very nicely (for a 10 year old machien :) ) Even got the PCMCIA network card to work with minimal fuss and sound worked after running 1 modprobe.

---

### Post by snowpine on 2008-08-12
> **stinger30au said:**
> Can anyone suggest a linux distro i can use on an ooooolllllddddd pc of mine.

its a celeron 400 with 256 meg of ram and 12 gig hdd and dvd burner just for fun.
i think i have a spare 20 gig hdd kicking round i can throw at it to make it even more super duper if needed :-))

i need it to have internet access, samba and CUPS or better and an o/s that does not bog this thing down so much it takes an eternity to do anything what so ever


any ideas????

What are your preferences in terms of graphical apps vs. command line, full desktop environment vs. lightweight windows manager, custom install vs. everything works out-of-the-box, etc? 

A really good "compromise" distro between all those factors is Crunchbang. For your hardware, it is right in its "sweet spot" where you will notice a big performance boost over, for example, Ubuntu, while still being easy to use. *Box-based distros like Crunchbang, Fluxbuntu (which uses Fluxbox) and DSL (used to be Fluxbox, forget what it uses currently).  will be quicker on your hardware than Gnome, KDE, maybe even Xfce. But they not for everybody; if you want a modern, graphical desktop, for example, I agree with the other posters who suggest something like Debian+Gnome for your older hardware. 

Good luck!

---

### Post by stalkier on 2008-08-12
My vote is on Puppy or DSL. I have used both and found them to be very fast on older hardware. They are not for noobs though.

---

### Post by rokytnji on 2008-08-12
Custom Numblex worked out of the box on my Amrel 500mhz,128mb ram laptop. Picked up Belkin Wireless PCMCIA F5D 7010 with Reltek chip and connected right up.

[http://custom.nimblex.net/](http://custom.nimblex.net/)

---

### Post by darrenn on 2008-08-12
If it's just for fun why don't you try sugar?

---

### Post by stalkier on 2008-08-12
> **NoWayBill said:**
> TinyFlux is another lightwieght distro.

The problem you may find with the light/feather-wieght distros is with your hardware.
Being small has it's advantages and disadvantages.
The disadvantage being light on hardware support.

DSL is not intended for HD install and is based off of an old version of Knoppix, so it will install MOST .deb packages but not all.
As stated above it uses an "old" kernel so not all "new" packages are compatible.
Although it does have an installer the devs don't recommend it.
I installed it on old laptop PII 266mhz 256m RAM 8g HD, it ran well except the audio.

Puppy is it's own beast completely.
Audio worked, but could never get PCMCIA networking to go.

Ended up using a stripped down Debian stable and running with xFCE.

I have run XandrOS and FreeSpire on a similar PC. PII 266MHrz, 128MB RAM, 6 GB hdd. Ran well. I even ran Morphix and Ubuntu 6.04 fairly well.

---

### Post by drawhole on 2008-08-12
persoaly i'd say flux is probally the best option .. xfce next ... depends on how goor you are with the console i'd think..

---

### Post by RedSquirrel on 2008-08-12
If you want to stick with Ubuntu, try a minimal installation. For example:

[http://www.psychocats.net/ubuntu/minimal#barebones](http://www.psychocats.net/ubuntu/minimal#barebones)

---

### Post by jayson.rowe on 2008-08-12
I second the nomination for CrunchBand (#!) linux - it's an awesome distro by Philip Newborough ([http://philipnewborough.com/](http://philipnewborough.com/)) and ([http://crunchbang.org/](http://crunchbang.org/)) that combines Ubuntu w/ the awesome (and very lightweight) OpenBox window manager.

Phillip does a great job at making it so awesome and feature rich that you forget that you're running a "minimalist" desktop. 

I think it would run quite ok on your hardware. I would definatly see about getting your RAM up to 512 if you could find a good deal on some PC100 (likely what is in your machine) - if you have a computer store in your area that sells used and salvaged stuff (as I do) you could pick up RAM like that for very little.

---

### Post by robert shearer on 2008-08-12
Puppy or Nimblex  both work well for me.

---

### Post by Glw8z on 2008-08-13
I'm using Xubuntu with a Celeron 800 that currently has only 192MB RAM, and it's not sluggish by any means. Sure, I haven't tried those other distros suggested, but this one works fine for a machine similar to yours.

---

### Post by stinger30au on 2008-08-13
> **starcannon said:**
> I really like [[SIZE=4][COLOR=DarkOrange]Fluxbuntu[/COLOR][/SIZE]]("http://fluxbuntu.org/") for old hardware.

i have d/l it and burnt to disc. twice in fact. it will boot and install form another pc, but on the celeron pc it wont boot. i can put anyother disc in it and it will bot, just not fluxbuntu for some silly reason

---

### Post by Crafty Kisses on 2008-08-13
I'd say DSL, and in some cases EliveGem.

---

### Post by stinger30au on 2008-08-13
> **snowpine said:**
> What are your preferences in terms of graphical apps vs. command line, full desktop environment vs. lightweight windows manager, custom install vs. everything works out-of-the-box, etc? 

A really good "compromise" distro between all those factors is Crunchbang. For your hardware, it is right in its "sweet spot" where you will notice a big performance boost over, for example, Ubuntu, while still being easy to use. *Box-based distros like Crunchbang, Fluxbuntu (which uses Fluxbox) and DSL (used to be Fluxbox, forget what it uses currently).  will be quicker on your hardware than Gnome, KDE, maybe even Xfce. But they not for everybody; if you want a modern, graphical desktop, for example, I agree with the other posters who suggest something like Debian+Gnome for your older hardware. 

Good luck!


id prefer somekind of light weight manager , dont needs kde... something like enlightenment or xfce. would be nice if everything worked out of the box.prefer gui

ubuntu will install on this machine, but 8.04 or 7.10 or 7.04 is so amazinlgy slow

---

### Post by stinger30au on 2008-08-13
> **Codename said:**
> I'd say DSL, and in some cases EliveGem.


Elivegem has no printer and no samba support. i have a full version of it, and tried it.

it does run very smooth on this machine and its a pitty it doesnt have printer/samaba or i would use it

---

### Post by stinger30au on 2008-08-13
> **Glw8z said:**
> I'm using Xubuntu with a Celeron 800 that currently has only 192MB RAM, and it's not sluggish by any means. Sure, I haven't tried those other distros suggested, but this one works fine for a machine similar to yours.


can you do me a favour, can you slow the cpu down to 400 MHz and see whats its performance is like then please just as an experiment. id like to know the results. thanks

---

### Post by Glw8z on 2008-08-14
> **stinger30au said:**
> can you do me a favour, can you slow the cpu down to 400 MHz and see whats its performance is like then please just as an experiment. id like to know the results. thanks

Sorry, but I'm far from competent enough to tweak the system that way. I do have, however, one more abandoned tower gathering dust, a PII 350MHz. The problem is I've ripped its memory, video card and HD off, and am not too eager to reassemble it now that the Celeron's working (the second HD was a pain to add for limited space, so I'm hesitant to remove it now). I can't promise anything, but if I do pull it off, I'll post back with the results.

---

### Post by y@w on 2008-08-14
I've used Zenwalk on my slower machines before as a desktop. It's really fast. It uses XFCE as the window manager out of the box and it's based on Slackware. Which.. Slackware's an awesome choice too :)

---

### Post by stinger30au on 2008-08-14
> **Glw8z said:**
> Sorry, but I'm far from competent enough to tweak the system that way. I do have, however, one more abandoned tower gathering dust, a PII 350MHz. The problem is I've ripped its memory, video card and HD off, and am not too eager to reassemble it now that the Celeron's working (the second HD was a pain to add for limited space, so I'm hesitant to remove it now). I can't promise anything, but if I do pull it off, I'll post back with the results.


ok, thanks

---

### Post by Glw8z on 2008-08-15
All right, here's what came of my experiment with the PII 350MHz 192MB RAM. Not exactly breaking Olympic records here, but I let you be the judge.

The [COLOR="Blue"]Xubuntu[/COLOR] installation (from the Alternate CD) took just shy of two hours (1h56min to be precise), but I'm sure you can find something to occupy yourself during that. I didn't encounter any problems with the installation.

Then to boot times, to the login screen and total time to the xfce-session:
First boot (after installation complete) 1.05 1.35 total
Regular boot (after the first try and changing some settings) 1.20 1.50 total

I did try rebooting several times to check the performance, without any deviation from those numbers. All in all, it didn't feel too long to me, but then, those with modern machines (or 15-second attention spans) might feel differently. 

Next, a few supposedly resource-hogging apps installed by default and their loading times (first runs and following tries listed, as there can be noticeable differences):
Firefox  1st run 35 sec, then 7 sec and 17 sec
OOo Writer 1st run 45 sec, then 27 sec
GIMP 1st run 40 sec, then 35 sec
AbiWord 1st run 10 sec, then 10 sec
Totem (just for comparison) a couple sec.

If you're not sure about those times, or fear they equal eternity in the computer realm, you need to try it on your own. 

I also checked the memory use (which some may fear will utterly paralyze your modest system). That can be proved wrong here. The total memory used as shown in System Monitor:
GIMP 72.3MB, later after opening and closing other apps 102MB
Firefox 100.5MB, second try 105.9MB
AbiWord 94MB
OOo Writer 105.2MB

After closing all the apps and leaving just the xfce-session running normally, the memory use dropped between 50 and 59MB, a very modest figure IMO. I must mention that I only tried to run one app at a time, as might be wise with older hardware. Anyway, the apps themselves ran just fine, no sign of unnecessary/unbearable slowdown. Again, my perceptions only.

Now, what I didn't do was boot while connected to the internet. It would have started upgrading the system and installing a zillion packages, coupled with possible vulnerabilities in the system. As far as going online, it may be less tolerable, but then, you'd have to recognize the limitations of the system and not despair.

Perhaps there are (still) others who have experience of older processors and their online performance. Also bear in mind you may get better performance/results since you have 256MB RAM. 

I hope this gives you some insight into the whole issue.

---

### Post by LiNuXxToOthEMaX on 2008-08-15
> **kerry_s said:**
> debian, custom install if your linux adept, if not xfce4 version runs fine.
my laptops 450mhz 256mb ram and 12gig hd.

xfce4 version:
[http://cdimage.debian.org/debian-cd/4.0_r4a/i386/iso-cd/debian-40r4a-i386-xfce-CD-1.iso](http://cdimage.debian.org/debian-cd/4.0_r4a/i386/iso-cd/debian-40r4a-i386-xfce-CD-1.iso)

net installer, straight install gives you gnome, but you can also use it to do a custom install just unselect everything at package selection:
[http://cdimage.debian.org/debian-cd/4.0_r4a/i386/iso-cd/debian-40r4a-i386-businesscard.iso](http://cdimage.debian.org/debian-cd/4.0_r4a/i386/iso-cd/debian-40r4a-i386-businesscard.iso)

lol

---

### Post by LiNuXxToOthEMaX on 2008-08-15
> **Codename said:**
> I'd say DSL, and in some cases EliveGem.

yea i believe that would work in this case.

---

### Post by snowpine on 2008-08-15
> **Glw8z said:**
> 
Now, what I didn't do was boot while connected to the internet. It would have started upgrading the system and installing a zillion packages, coupled with possible vulnerabilities in the system. As far as going online, it may be less tolerable, but then, you'd have to recognize the limitations of the system and not despair.


Glad Xubuntu is working for you! Just to clarify, the system will not install any updates unless you specifically tell it to do so. :) So you can connect to the internet without worrying. I would recommend installing the updates sometime when you have the time to spare. Generally speaking, unless you are browsing pages with video or other multimedia, the limiting factor is the speed of your internet connection, not the speed of the computer.

Good luck!

---

### Post by stinger30au on 2008-08-15
> **Codename said:**
> I'd say DSL, and in some cases EliveGem.



i have a full version of EliveGem

and it runs well on the celeron 400, the problem is that it wont let me print as i cant find anything to do with cups and i cant find anything to access samba for my lan either.

any ideas???

---

### Post by stinger30au on 2008-08-15
currently installing Maryan Linux - ubuntu but with an enlightment desktop manager

[http://www.maryanlinux.com/](http://www.maryanlinux.com/)

still have a few other distros to try.

have vector linux lite 5.9

Ozos - based on ubuntu

and Nimble X

---

### Post by stinger30au on 2008-08-15
have just installed maryan linux and posting this using it on my celeron 400 machine. it is useable but a little sluggish, but it is Ubuntu 8.04 with enlightenment.

at least i can talk to my lan via samba and print to my shared printers. top stuff.
might use this on my daughers laptop in october when 7.04 updates stop.

oh well... on with the testing. a few other distros to install and test

---

### Post by stinger30au on 2008-08-15
ok, reinstalling Maryan linux now. Ozos locked up and had a spit about the hardware

vectorlinux has a spit about the hardware as well

nimblex also had a spit about the hardware


if i get a chnace next week i will d/l Xubuntu, in meantime  will stick with maryan

---

### Post by Okicombo on 2008-08-15
I just thought this might be of interest to you, Stinger.

"[DeLi Linux]("http://www.delilinux.de/") needs a 386 with 32 MB RAM as a minimum. It should work smoothly with a 486. A full installation with all packages requires nearly 400 MB of hard disk space."

---

### Post by stinger30au on 2008-08-16
> **Okicombo said:**
> I just thought this might be of interest to you, Stinger.

"[DeLi Linux]("http://www.delilinux.de/") needs a 386 with 32 MB RAM as a minimum. It should work smoothly with a 486. A full installation with all packages requires nearly 400 MB of hard disk space."

thanks for the info. going to check it out now.
have just finished reinstalling maryan linux.
its fairly smmoth for this liitle rig, but i need to check out Deli, look good.

incase your interested the mainboard im running is this

emcore-i612
[http://www.arbor-usa.com/mini/emcore-i612.htm](http://www.arbor-usa.com/mini/emcore-i612.htm)

i dont have much cash to spend so i have made this "luggable pc"out of old pats and shoved them inside an old army ammunication case made of pine. the case is usually for carrying 3 x 81mm mortar shells. picked up the case from the recycle shop at one of the local rubbinsh dumps for just $5 and added a 15 inch lcd and speakers.... i should post some pix, im sure someone would get a laught out of what i have built. i have used this rig a few times to reconfigure some xeries ibm servers and cisco routers and a few other goodies too

---

### Post by Glw8z on 2008-08-16
> **snowpine said:**
> Glad Xubuntu is working for you! Just to clarify, the system will not install any updates unless you specifically tell it to do so. :) So you can connect to the internet without worrying. I would recommend installing the updates sometime when you have the time to spare. Generally speaking, unless you are browsing pages with video or other multimedia, the limiting factor is the speed of your internet connection, not the speed of the computer.

Good luck!

Not to hijack this thread, but just as clarification: I installed Xubuntu only for the sake of experiment on that old PII. I'm not planning on using it, as it's already working decently on my Celeron 800. stinger30au just wanted some info, which I provided.

---

### Post by mikjp on 2008-08-16
I would suggest any of the distros mentioned in my blog posting [here](http://lightlinux.blogspot.com/2008/06/top-10-of-lightweight-linux_24.html). I myself would take Slackware.

Mikko

---

### Post by stinger30au on 2008-08-16
well im currently trying a puplet of puuy linux, its called dingo plus, about 200 meg d/l.

it is amazingly fast for this little ubit but i cant get it to print on my lan....

i might well d/l a copy of xubuntu yet, the specs for it is here


[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

at least i know that ubuntu 8.04 will work on this system.... notice i says work, not run, but work.] as its sssssooooo slow. but i have high hopes of xubuntu

im yet to try DeLi

---

### Post by stinger30au on 2008-08-20
after trying a number of different linux distro today i have [URL="http://mirror.internode.on.net/pub/ubuntu/xubuntu/8.04/release/xubuntu-8.04.1-alternate-i386.iso"]d/l Xubuntu Alternative 386 .iso 
[/URL]
i have just finished installing this to my pc and writing this post on it now.

it is in now way share or form any where near as fast as a few other super tiny distros i have tried like puppy linus or dsl, no did i even expect it to be any where near as fast.

but... it is most definately faster then Ubuntu 8.04  plus the fact i can actually understand whats going on with out having to learn another distro

so...

Xubuntu 8.04 is here to stay on this world beating Celeron 400 with 256 Meg of Ram, the world dominating Quantum bigfoot 5.25 incg 12 gigabyte hdd, and dual layer dvd burner


Thanks to all for the various responces and suggestions.

Man oh man, is there some Variations round on linux or what????

i will stick to this.

Thanks all

---

