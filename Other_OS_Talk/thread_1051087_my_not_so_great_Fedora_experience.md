---
title: "my not so great Fedora experience"
date: 2009-01-26
forum: Other OS Talk
---

### Post by wolfen69 on 2009-01-26
to the mods, first off, i would like this to thread to remain in this section if possible. i don't want to get flamed in the fedora forums. plus i want opinions from people that might not go to the fedora threads. thanks.

i decided it was time to do another distro world tour, and try and catch up on what's going on in non-ubuntuland.

i popped in a spare hard drive and fired up the fedora 10 live cd. it took a while to load, but no big deal. i get to the desktop and everything looks great. nice theme. i check to see if my wireless card is detected, and it is. awesome.

i didn't want to waste too much time, so i went for the install immediately. it complained about my partitions for some reason, and did not offer me a whole disk install. so i went the manual route and created the necessary partitions. install was quick, (10 min or so) and painless. reboot.

after getting to the desktop for the first time, i went about getting my tv tuner card to work. (mandatory) all of a sudden, a pop up notifies me that there is firmware available, so i click to see what's up. it wants to download and install the firmware for my tv card. OK! nice. it does its thing and i'm off to the races. i'll check to see if it works after i get vlc.

on to getting codecs and such. i heard about rpm fusion, so i went to the website and added the non free repos. on to installing some stuff.

i went to download vlc first. downloading speed was VERY slow. ok, go get a cup of tea. come back to find out that installing it isn't any quicker. hmmm. :-k  the hard drive keeps thrashing about like i was doing the world's most intensive operation possible. after that is done, i check the menus for vlc. not there. ok. i try to get some codecs installed and the same thing happens. extreme slowness. only this time, the package manager freezes up and i'm relegated to doing ctrl-alt-bksp. i try again. same thing. so i say to myself screw it, i'll just play around for a bit.

the hard drive at times is working so hard that i can't do anything else until it stops. keeping this shorter than it could be, there were a couple other things that did not endear me to fedora. my computer runs fairly well with every distro i have tried, so i know i don't have any exotic hardware. i won't be back to fedora any time soon.

i'm sure there are people that are running fedora happily, but i was not to be one of them. now i know why i like debian/debian based distros the best. because they work near flawless for me, my friends and customers.

anyone else have an experience like this with fedora? btw, right after i tried opensuse 11.1 and had a much better experience. package management still left alot to be desired, but at least my computer was usable.

---

### Post by kabloink on 2009-01-26
I ran into the same problem as you did with the painfully slow download speeds. I discovered later that they have a plugin that allows the yum package manager to choose the fastest mirror. Which sped things up considerably after install 

In a terminal:
su -c 'yum install yum-fastestmirror'

---

### Post by Sorivenul on 2009-01-26
Yeah, the fastestmirror plugin is almost necessary. IMO, it should be installed and enabled by default. You are far from the first user to complain about this, and it remains pretty much my only gripe with the default Fedora install.

I find myself uninstalling less from the default install from LiveCD than I do with the default Ubuntu LiveCD install. However, my other gripe is that the Fedora netinstall or minimal install does not compare to either the Debian or Ubuntu netinstalls. 

Overall, I find Fedora 10 to be a great improvement over Fedora 9, which was a major letdown after Fedora 8. As Fedora as a project and community settles into its niche I expect to see better and better releases. 

Just my two cents.

---

### Post by jseiser on 2009-01-26
I use fedora at work and have no problems with it.  I use the fastest mirror plugin.  I also recommend you use the presto plugin which only downloads the changes in packages, so that creates very small downloads that are being downloaded from the mirror that is the fastest for you.

---

### Post by kaldor on 2009-01-26
I have used Fedora in the past. I did not like it a whole lot. Just did not fit my standards, I guess.

I always keep coming back to Ubuntu. I keep having problems with every distro I try.

---

### Post by cardinals_fan on 2009-01-26
I don't really like the large size of the default install, but Fedora is my favorite of the "big" (popularity, not size) distros.  It's very clear that the system is targeted for the enterprise.  It has lots of very interesting under-the-hood features and some pretty advanced security out of the box.

---

### Post by Sorivenul on 2009-01-26
> **cardinals_fan said:**
> It has lots of very interesting under-the-hood features and some pretty advanced security out of the box.
Very true. Despite its complexity compared to AppArmor, SELinux is a great security feature.

---

### Post by Antman on 2009-01-27
Fedora is one of my top 3 OS's. It's not perfect, but not many distros are now-a-days.

---

### Post by Mason Whitaker on 2009-01-27
In my experience, it never recognized any of my drivers out of the box :(

Only Distros to do that were Ubuntu, Opensuse, and Arch.

---

### Post by wolfen69 on 2009-01-27
i don't know if i was a little harsh in my review or not, but i realize that there are people that use fedora, opensuse, mandriva, slackware, etc. all very happily. we are only limited by how many machines we can test, x/ number of distros on. that's what i do. i test computers and distros.

---

### Post by BrokenKingpin on 2009-01-28
I tried Fedore Core 9 on my new desktop and it kept crashing during the install. I used Fedora Core 4 a few years back and loved it at the time as it was the only distro to work with my laptop... I haven't had much luck with it since.

---

### Post by Simian Man on 2009-01-28
I am a big fan of Fedora and have found that it works great on every computer I have tried it on.  I have experienced the issue where one mirror will be ridiculously slow, but the fastest-mirror plugin does fix that.

---

### Post by cardinals_fan on 2009-01-28
> **wolfen69 said:**
> i don't know if i was a little harsh in my review or not, but i realize that there are people that use fedora, opensuse, mandriva, slackware, etc. all very happily. we are only limited by how many machines we can test, x/ number of distros on. that's what i do. i test computers and distros.
That's fine.  Each distro will work differently for each person.

---

### Post by Antman on 2009-01-28
"Use what works" - is my motto....:guitar:

---

