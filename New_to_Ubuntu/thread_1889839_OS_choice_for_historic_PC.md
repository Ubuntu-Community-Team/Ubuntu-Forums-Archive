---
title: "OS choice for historic PC"
date: 2011-12-02
forum: New to Ubuntu
---

### Post by Anakunda on 2011-12-02
Hello, need some advice. I'm looking for something oerational on my backup PC that will be able to run web browser quite smoothly. Unfortunatelly the backup PC is pretty old, some archaic AMD CPU and about 100MB of installed RAM. Since I only use it for temporary cases I don't want to upgrade it any way. For now there's Windows XP SP3 with Chrome which seems be the least demanding browser but still helly slow (too much disk swapping etc.). Now I'm thinking of replacing WinXP by Ubuntu 32bit. The question is whether I can expect Ubuntu beeing any smoother performance that XP on this old machine. I don't have any more specific requests, just an OS with some web browser and Keepass. Is Ubuntu a good idea for this case?

---

### Post by Lars Noodén on 2011-12-02
For really underpowered systems you might look at [Puppy Linux](http://puppylinux.org/main/Overview%20and%20Getting%20Started.htm).

---

### Post by Anakunda on 2011-12-02
Thx for suggestion. Just for Ubuntu yet, is it expected to perform more or less smooth compared to Windows XP on low resource system like mentioned?

/edit:

Does the Puppy thing offer software center like Ubuntu so that I can install 3rd party software like Keepassx or Chrome (if I find builtin Firefox too slow)?

---

### Post by 3rdalbum on 2011-12-02
> **Anakunda said:**
> Thx for suggestion. Just for Ubuntu yet, is it expected to perform more or less smooth compared to Windows XP on low resource system like mentioned?

Ubuntu 11.10 requires 384 MiB of RAM. It won't even boot up with 128 MiB of RAM. So you'd need a lightweight distro rather than a general-purpose distro.

> Does the Puppy thing offer software center like Ubuntu so that I can install 3rd party software like Keepassx or Chrome (if I find builtin Firefox too slow)?

All Linux distros have something similar to Software Center. I believe there's a variety of Puppy Linux that can handle Ubuntu/Debian packages and their repositories, so you should have the full range of software available if you choose to run that variety of Puppy.

---

### Post by mörgæs on 2011-12-02
You might get something running on 100 MB memory (from which the screen card is taking a bite, by the way), but it will not be worth the struggle. 

Put this one to rest. I guess you will be able to get some 4-5 years old gear for free or for a very low price if you ask around.

---

### Post by mikewhatever on 2011-12-02
Ubuntu will not perform well with only 100MB of RAM. In fact, anything with Chrome or Firefox will be very slow, as they can easily consume all the available RAM. Try something like DSL or Tiny Core (links below).

[http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/)
[http://distro.ibiblio.org/tinycorelinux/welcome.html](http://distro.ibiblio.org/tinycorelinux/welcome.html)

---

### Post by Anakunda on 2011-12-02
Ok thanks for all suggestion given, that makes me to decide give up with Ubuntu definitely and give a try to Puppy.

---

### Post by mörgæs on 2011-12-02
Of the distros mentioned, Puppy and Tiny Core are the only options, it you still want to give it a try.

Damn Small Linux is a dead project and should not be recommended in this forum. Security holes have not been fixed for several years.

---

### Post by mikewhatever on 2011-12-02
> **mörgæs said:**
> Of the distros mentioned, Puppy and Tiny Core are the only options, it you still want to give it a try.

Damn Small Linux is a dead project and should not be recommended in this forum. Security holes have not been fixed for several years.

Very true. Unfortunately, all of the light weight distros I've tried (Puppy, Slitaz, SimplyMepis, CrunchBang) were outdated, not to mention Debian.

---

### Post by bkratz on 2011-12-02
Been playing with Bohdilinux lately and am really impressed (based on 10.04): here are the system requirements.

[http://www.bodhilinux.com/system.php](http://www.bodhilinux.com/system.php)

---

### Post by mörgæs on 2011-12-03
> **mikewhatever said:**
> Very true. Unfortunately, all of the light weight distros I've tried (Puppy, Slitaz, SimplyMepis, CrunchBang) were outdated, not to mention Debian.

What do you mean by outdated? The ones you mention are in active development.

---

### Post by mikewhatever on 2011-12-03
> **mörgæs said:**
> What do you mean by outdated? The ones you mention are in active development.

Yes, so I was surprised to find Chromium 9 in Crunchbang, when the current version was 13 or 14. There was also an outdated version of Adobe Flash 10 and a re-branded Firefox 3.5 in the repositories, none of which were supported at the time of testing.

---

### Post by Anakunda on 2011-12-04
I have tried some of the mentioned distros and after all it seems that Win XP is still the fastest choice. The TinyCore is too much barebone, didnot even success to install and run Firefox on it, The Bodhian Linux didnot boot at all due to unsupported CPU feature, so Slacko Puppy comes out of this as a most usable alternative to Windows but I can't say it's better. The OS start is fast but Chrome for Win performs opening a page lightning fast(when not swapping) compared to any of browsers tried on Puppy. Maybe it is due to generic and not tuned up drivers but probably my research stays unfinished here as I'm tomorrow back to normal PC. Nevertheless thanks for all efforts ;P

---

### Post by realitykid on 2011-12-04
If you can, find some more ram for it. Try to get at least 512MB and the machine will run fine after that.

[http://www.oempcworld.com/](http://www.oempcworld.com/)

---

### Post by mastablasta on 2011-12-04
> **mikewhatever said:**
> Yes, so I was surprised to find Chromium 9 in Crunchbang, when the current version was 13 or 14. There was also an outdated version of Adobe Flash 10 and a re-branded Firefox 3.5 in the repositories, none of which were supported at the time of testing.

The might be older versions of programmes, but they are still supported by security pacthes and possibly bugfixes. That is why they are in stable versions of the system. tried and tested and pacthed as much as they could be. 

Ubuntu on the other hand for example uses newer programmes that are kind of still in beta.

the mentione probelms with DSL is that although it work on older hardware it is not activelly maintained, so any security flaws were not fixed unlike for example in Debian.

There is a reason why Debian uses those (old) programmes. it makes it a super stable operating system. those programems were screened so many times before they got to the stable repositories that it also makes it a very safe system.

additionally you can use certain commands and install newer verson of programmes if you actually need them.

for the very latets you need to try something like Fedora, but expect crashes and  incomatibilities...

---

### Post by cmcanulty on 2011-12-04
ebay has dirt cheap old ram just carefully write down all the numbers or check spec of your machine on web the exact match is quite important

---

### Post by cmcanulty on 2011-12-04
ebay has dirt cheap old ram just carefully write down all the numbers or check spec of your machine on web the exact match is quite important. Crucial.com you can enter the specs and it will tell you what you need.

---

### Post by snowpine on 2011-12-04
> **mikewhatever said:**
> Yes, so I was surprised to find Chromium 9 in Crunchbang, when the current version was 13 or 14. There was also an outdated version of Adobe Flash 10 and a re-branded Firefox 3.5 in the repositories, none of which were supported at the time of testing.

Actually Mike there was a new CrunchBang release last week with Iceweasel 8, newer kernel, etc. Sounds like you might have been using the older February 2011 release. :)

---

### Post by ki4jgt on 2011-12-04
If you're familiar with Windows, I would suggest ReactOS. It's awesome and only runs on 32megs of RAM. It's still in BETA though so it does have some MAJOR bugs. It runs any Windows program which doesn't require genuine Windows verification.

---

### Post by Chaz46 on 2011-12-04
I would definitely have a look on eBay for some extra ram, it can be had dead cheap! You'll be impressed at the improvement!

---

### Post by mastablasta on 2011-12-05
> **snowpine said:**
> Actually Mike there was a new CrunchBang release last week with Iceweasel 8, newer kernel, etc. Sounds like you might have been using the older February 2011 release. :)
 
 
yes, only the new release is Openbox only and has issues of it's own (with slim it seems).

---

### Post by snowpine on 2011-12-05
> **mastablasta said:**
> yes, only the new release is Openbox only and has issues of it's own (with slim it seems).

Yes, it fixes some old problems and introduces some new problems, like any software release. :)

---

### Post by mikewhatever on 2011-12-05
> **snowpine said:**
> Actually Mike there was a new CrunchBang release last week with Iceweasel 8, newer kernel, etc. Sounds like you might have been using the older February 2011 release. :)
I've used what was available at the time of testing, and don't see how the fact that a new ISO arrived a month later is relevant. The interesting question would be, is Iceweasel going to be updated, or is it going to remaint at version 8 till the next ISO is out.

> **mastablasta said:**
> The might be older versions of programmes, but they are still supported by security pacthes and possibly bugfixes. That is why they are in stable versions of the system. tried and tested and pacthed as much as they could be. 

Ubuntu on the other hand for example uses newer programmes that are kind of still in beta.

the mentione probelms with DSL is that although it work on older hardware it is not activelly maintained, so any security flaws were not fixed unlike for example in Debian.

There is a reason why Debian uses those (old) programmes. it makes it a super stable operating system. those programems were screened so many times before they got to the stable repositories that it also makes it a very safe system.

additionally you can use certain commands and install newer verson of programmes if you actually need them.

for the very latets you need to try something like Fedora, but expect crashes and  incomatibilities...

Are you saying that Chromium 9 Firefox 3.5 and Adobe Flash 10 are still supported? By who? AFAIK, none of the above versions are supported by their respective upstreams.

---

### Post by snowpine on 2011-12-05
> **mikewhatever said:**
> I've used what was available at the time of testing, and don't see how the fact that a new ISO arrived a month later is relevant. The interesting question would be, is Iceweasel going to be updated, or is it going to remaint at version 8 till the next ISO is out.

I was providing relevant, updated information for anyone who might be interested to know of the new release. It is a fresh start for CrunchBang: new website, new repos, new release. The plan is to mirror the latest Iceweasel as far as I know.

> **mikewhatever said:**
> Are you saying that Chromium 9 Firefox 3.5 and Adobe Flash 10 are still supported? By who? AFAIK, none of the above versions are supported by their respective upstreams.

By Debian of course, they released security updates for Chromium 9 and Iceweasel 3.5 as recently as September and November, respectively. Debian Stable will never have the latest version of anything, but you get semi-regular updates with any show-stopping security patches.

Debian never has and never will provide support for Adobe Flash Player; it's an ideological decision.

---

### Post by mikewhatever on 2011-12-06
> **snowpine said:**
> I was providing relevant, updated information for anyone who might be interested to know of the new release. It is a fresh start for CrunchBang: new website, new repos, new release. The plan is to mirror the latest Iceweasel as far as I know.

The refresh of Chrunchbang is most welcome, sure, but it wasn't relevant when I tested it. Thought you've implied that by replying to one of my posts.

> By Debian of course, they released security updates for Chromium 9 and Iceweasel 3.5 as recently as September and November, respectively. Debian Stable will never have the latest version of anything, but you get semi-regular updates with any show-stopping security patches.

Debian never has and never will provide support for Adobe Flash Player; it's an ideological decision.

Just what I thought, and I am rather skeptical of how efficient and practical that approach is. That said, Debian has its own way, and I respect it.

---

### Post by Flymo on 2011-12-06
The Puppy Linux 'Wary' variant would be my recommendation for older hardware. Currently at V5.2.2, released a few weeks ago.  

You can pick which browser you use, too.   Info [here]("http://puppylinux.org/main/Long-Term-Supported%20WaryPuppy.htm")

---

### Post by mastablasta on 2011-12-06
> **mikewhatever said:**
> 
 Just what I thought, and I am rather skeptical of how efficient and practical that approach is. That said, Debian has its own way, and I respect it.
 
 
that said, you can always install a newer version of the programme (just like in Ubuntu). you can even go alpha on the software if you wish.

---

### Post by mikewhatever on 2011-12-06
For that particular computer, I was looking for something stable, but not ancient. It's gone to the new owner with Ubuntu 10.04 in the end.

---

### Post by mastablasta on 2011-12-06
> **mikewhatever said:**
> For that particular computer, I was looking for something stable, but not ancient. It's gone to the new owner with Ubuntu 10.04 in the end.
 
 
10.04 also has old version of firefox (3.5 or something). unless they changed that with newer images. still a very good choice.

---

### Post by mikewhatever on 2011-12-06
> **mastablasta said:**
> 10.04 also has old version of firefox (3.5 or something). unless they changed that with newer images. still a very good choice.

10.04 has firefox 3.6. which is still supported by Mozilla, and when it reaches EoL, it will most likely get upgraded to the current version.

---

