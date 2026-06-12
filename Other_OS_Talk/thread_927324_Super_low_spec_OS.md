---
title: "Super low spec OS?"
date: 2008-09-22
forum: Other OS Talk
---

### Post by NintendoTogepi on 2008-09-22
My father wanted me to ask what the most low-spec OS around is.

He has a Pentium 2 Celeron with 64GM of RAM in his basement and wants to see if anything will work on it.

---

### Post by Antman on 2008-09-22
[DSL]("http://www.damnsmalllinux.org/")
or
Debian... see this thread: [http://ubuntuforums.org/showthread.php?t=870061]("http://ubuntuforums.org/showthread.php?t=870061")

---

### Post by I-75 on 2008-09-22
DSL Linux will run on it fine. Problem is that it is limiting in what it can do. Here is how to install it.

[http://www.youtube.com/watch?v=PhP17LPOCOU](http://www.youtube.com/watch?v=PhP17LPOCOU)



Your computer is a Pentium II which could mean it has a upper limit of 256 MB RAM. If so it probably uses the common PC 100 SDRAM ram sticks, these can be found on E-Bay for about $4 each for a 128 MB stick. I would try to get 256 MB ram in it and then install Xubuntu on it.

---

### Post by zmjjmz on 2008-09-22
Lowest spec OS...
I'd say getting lower than CP/M is pretty hard.
Or, CV20 BASIC
In all seriousness, before there are a flood of Puppy suggestions, I would recommend DeLi or DSL.
Please try to stick to their respective wikis when installing though, they aren't as easy as Puppy.

---

### Post by Sorivenul on 2008-09-22
I'm assuming you mean 64MB of RAM, not 64GB.
DeLi Linux or DSL would be your best bets, IMO.

---

### Post by loboc on 2008-09-22
if you put debian on it go back and put debian woody or potato on it rather than one wiht the newer kernels and what not

---

### Post by cardinals_fan on 2008-09-22
SliTaz.

---

### Post by snowpine on 2008-09-23
> **cardinals_fan said:**
> SliTaz.

I haven't had much luck with SliTaz on my 64mb virtual machine. It really seems designed for 128mb or more (160mb for the 'cooking' version). The 'loram' flavor, once installed to hard drive, uses a miniscule 25mb or so at boot,  however, it crashes every time I try to use the browser... any suggestions Cardinals Fan?

DSL is probably your best bet. I-75, I am curious what you mean by "it's limiting in what it can do"? In my limited experience, it is pretty full-featured, if kind of ugly. :)

---

### Post by mips on 2008-09-23
[**MenuetOS**]("http://www.menuetos.net/")

---

### Post by Sorivenul on 2008-09-23
> **mips said:**
> [**MenuetOS**]("http://www.menuetos.net/")
Another good, and *extremely* small system.  Fits on a single 1.44MB floppy.  
A fork of this project with similar goals is [**KolibriOS**]("http://www.kolibrios.org/").
Both of these run with 8MB RAM.

---

### Post by smoker on 2008-09-23
i would have a look at puppy:
[http://www.puppylinux.org/](http://www.puppylinux.org/)

there are also a whole load of options here:
[http://www.linuxlinks.com/Distributions/Mini_Distributions/](http://www.linuxlinks.com/Distributions/Mini_Distributions/)

best of luck

---

### Post by VCSkier on 2008-09-23
I would strongly recommend Puppy Linux.  In my opinion, it's much more user friendly than the others mentioned here.  A friend of mine used Puppy 3.01 on a laptop just like yours (PII with 64mb RAM) for a while.  He had never used Linux before, but found it nice enough.  It was slow but usable.

If you're going to try it, definitely make a swap partition ahead of time with something like SystemRescueCD or GParted.  From there, give it a try.  Like I said, the official releases would be sluggish on a system with only 64mb of ram, but if you want something quicker, there are some puplets (Puppy Linux derivitives) that would run great.  Possibly consider "Mean Puppy," or "Fat Free Puppy."  Good luck, and let us know how things go!

---

### Post by Sorivenul on 2008-09-23
> **VCSkier said:**
> I would strongly recommend Puppy Linux.  In my opinion, it's much more user friendly than the others mentioned here.  A friend of mine used Puppy 3.01 on a laptop just like yours (PII with 64mb RAM) for a while.
For more information on Puppy and its minimum requirements, I would suggest reading this page:
[http://www.puppylinux.org/wiki/hardware/general/minreq]("http://www.puppylinux.org/wiki/hardware/general/minreq")
An older release (pre-1.0.2) may actually be better if seeking actual functionality as opposed to just getting a system to boot on your hardware, if you were to choose Puppy.

I still suggest DeLi.

---

### Post by Bungo Pony on 2008-09-23
I wouldn't recommend Puppy for anything with less than 128M of RAM. Actually, I wouldn't recommend Puppy for anything. My recommendation for systems that have 128M or more of RAM is TinyMe. Fantastic system, functional, looks good, uses synaptic, and a fair amount of software for it.

For 64M, I'd recommend DSL. You won't be able to do video editing on it, but you'll be able to get some decent functionality out of the machine.

As for it's ugliness, I think DSL 4.x looks allright (but I prefer the functionality of 3.x better)

---

### Post by NintendoTogepi on 2008-09-23
> **Bungo Pony said:**
> 
For 64M, I'd recommend DSL. You won't be able to do video editing on it, but you'll be able to get some decent functionality out of the machine.

What would it run? Would it run a internet browser, a word editor, an IM client and an Email service?

---

### Post by zmjjmz on 2008-09-23
> **NintendoTogepi said:**
> What would it run? Would it run a internet browser, a word editor, an IM client and an Email service?

Yes.
I personally recommend Skipstone browser for something that old, but it's not very well featured. Kazehakase is another option, but it will be slow and very featureless. Flash will be slow.
Abiword should do as a Word replacement.
AYTTM should be a nice IM client.
Sylpheed/Claws would do well for e-mail.

---

### Post by volkswagner on 2008-09-24
> **NintendoTogepi said:**
> My father wanted me to ask what the most low-spec OS around is.

He has a Pentium 2 Celeron with 64GM of RAM in his basement and wants to see if anything will work on it.

Since you did not specify Linux, I must say Win95.  It will run with 16megs of ram, I believe the minimum is 8megs.

That box will run DSL.

If your Dad is looking for a project, I vote with an earlier post.  Get more RAM.  Max it out if you can.

Then install Ubuntu-server on it.  It will make a decent file/ftp/web server and a great project.  

My Pent2 400, 384meg ram serves well running Ubuntu server 6.06. 
See for yourself, my pet project in the works, Ubuntu LAMP 6.06 with Postfix/SquirrelMail, Webmin, proftp, etc.
[http://www.volkswagner.com]("http://www.volkswagner.com")  

What I like about these older Pent2 boxes is power consumption is a fraction of Pent3, and Pent4 machines.  I don't have a kill-a-watt device, but I checked the running current at 110v was .35 amps vs pent 4 and AMD Athalon 700mhz at .95-1.2amps and .9amps respectively.

---

### Post by gjoellee on 2008-09-24
SliTaz is a whole system that is a little under **30mb** large, you still have everything you need for the office.

You also have Damn Small Linux which is slightly heavier, and Puppy Linux as well.

---

### Post by sertse on 2008-09-24
One of the one misconceptions was the idea that the size of the distro is directly related to the specs of the comp that is able to run it.

Slitaz is 25-30mb, but afaik, Deli or DSL while being bigger tends to do better of low spec systems..

---

### Post by ukripper on 2008-09-24
puppylinux will be really good for the spec you metnioned [http://www.puppylinux.org/](http://www.puppylinux.org/)

---

### Post by snowpine on 2008-09-24
(double post)

---

### Post by snowpine on 2008-09-24
> **sertse said:**
> One of the one misconceptions was the idea that the size of the distro is directly related to the specs of the comp that is able to run it.

Slitaz is 25-30mb, but afaik, Deli or DSL while being bigger tends to do better of low spec systems..

This is true; SliTaz is actually ~80mb compressed down to 25mb. So on a slow computer, you have to wait a bit while it's being uncompressed. As I mentioned previously, I recommend 128mb for SliTaz (160mb for the Cooking version).

---

### Post by darrelljon on 2008-09-24
Have a look at [Operating Systems for old computers]("http://ubuntuforums.org/showthread.php?t=575456").

I'd maybe give DeLi a try - if you know how to partition and don't want a live CD.

---

### Post by NintendoTogepi on 2008-09-25
Cool, but unfortunately the project seems to have been aborted. My Mom didn't want him to bring it up as it could have hundreds of bugs/spiders hiding in it.

---

### Post by chungy on 2008-09-25
OpenBSD never gets anymore bloated than it needs to be.  With no net, sshd, or sendmail running, the system uses only around 3MB of RAM with one user and /usr/bin/top.

Add a lightweight window manager (OpenBSD comes with FVWM by default, and the default config isn't very pretty, but you can customize it of course if you have the patience to learn FVWM syntax), and it'll start to be very usable for a desktop.  Abiword and Gnumeric should do nicely for word processing and spreadsheets...

As for web browsing, Firefox might be a bit much for a 64MB RAM system, you can get Opera running on OpenBSD (with Linux emulation), though I haven't looked at Opera for years to tell if it's still as light as it claims.  SeaMonkey in general uses less RAM than Firefox, though it's still a beast...

---

### Post by stuv829 on 2008-09-25
An exasperated mother, whose son was always getting into mischief, finally asked him, "How do you expect to get into Heaven?" The boy thought it over and said, "Well, I'll run in and out and in and out and keep slamming the door until St. Peter says, 'For Heaven's sake, Dylan, come in or stay out!'"[wow gold](http://www.mmoinn.com),[world of warcraft gold](http://www.mmoinn.com),[wow power leveling](http://www.mmoinn.com/mmoinn_pl/)my site [http://www.mmoinn.com](http://www.mmoinn.com)

---

### Post by mips on 2008-09-25
> **NintendoTogepi said:**
> Cool, but unfortunately the project seems to have been aborted. My Mom didn't want him to bring it up as it could have hundreds of bugs/spiders hiding in it.

Why can it not be cleaned outside?

---

### Post by darrelljon on 2008-09-25
When things are out in the open, bugs cannot hide and don't survive as long.
This applies to software as much as your situation.

---

### Post by VCSkier on 2008-09-25
> **darrelljon said:**
> When things are out in the open, bugs cannot hide and don't survive as long.
This applies to software as much as your situation.

nice

---

### Post by basenvironment on 2008-09-25
debian...

Easy to make it whatever you want and unlimited in possibilities as well.

---

### Post by zmjjmz on 2008-09-26
> **NintendoTogepi said:**
> Cool, but unfortunately the project seems to have been aborted. My Mom didn't want him to bring it up as it could have hundreds of bugs/spiders hiding in it.

Wait what.
It takes serious effort for a bug to go in there, especially considering there's nothing there to attract them.
Maybe there's a cobweb or too, but it will be blown out by the fan and dissipated into the air.

---

