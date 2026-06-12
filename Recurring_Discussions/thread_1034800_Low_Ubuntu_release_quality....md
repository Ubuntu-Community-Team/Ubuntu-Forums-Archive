---
title: "Low Ubuntu release quality..."
date: 2009-01-09
forum: Recurring Discussions
---

### Post by PryGuy on 2009-01-09
Good day!
Don't get me wrong, I'm Ubuntu fan, I think Ubuntu is the most flexible and user friendly Linux distribution so far. But I'm seriously worried of the quality of Ubuntu releases. Hardy had lots of problems, and only 8.4.1 could fix it for me. I felt fine with 8.4.1, then came Intrepid. Here's a small list of very serious bugs that I found in Intrepid:
1. System hangs on shutdown (fixed now)
2. setupcon that localises console fonts does not work (fixed now)
3. nVidia driver breaks window titlebars (can be fixed with original nVidia drivers)

Yes, yes, I've fixed it, but I'm not an ordinary user on the other hand. What seriously worries me is that Ubuntu goes Windows way more and more. I can compare Ubuntu with Fedora 10 that has no such problems (yum is a disaster though ;)), distribution is very polished and I haven't found a single glitch in it. You'll certainly say, "well, go ahead, switch to Fedora then", but I'm a system administrator, I install the Linux thing, and apt is the best package manager under the sun! I love Ubuntu, for God's sake! I just want Canonical to be a bit more serious about the quality of their releases. It really should work out of the box without any patches or something, and, sorry, it doesn't (the 1st bug I've mentioned).

I don't think it that's hard, we don't need a superstable OS, there's good old Debian for that, Canonical should make a list of things to test pre-release on. Such as startup/shutdown, XDMCP, you name it... Ubuntu should just work out of the box!

---

### Post by Zack McCool on 2009-01-09
I had none of the problems that you did.

Now, I am not saying that the release is perfect and you are the problem.  Clearly, there are things, though, that hit different hardware combinations in different ways.  Considering the lack of support given by HW manufacturers, I think Canonical does a decent job.

---

### Post by Bachstelze on 2009-01-09
Moved to Recurring Discussions.

---

### Post by jrusso2 on 2009-01-09
I plan on using 8.04 LTS for as long as possible until its too old to run the new software.

Just because something is new does not mean you have to upgrade.  Six months is not long enough to develop a whole Operating System.

Heck the beta period for Windows 7 will be longer then the whole development of Jaunty.

---

### Post by Trail on 2009-01-09
Except, Ubuntu primarily distributes, rather than develops. Your comparison to Windows' development is flawed.

---

### Post by PryGuy on 2009-01-09
> **jrusso2 said:**
> Heck the beta period for Windows 7 will be longer then the whole development of Jaunty.Well, probably Canonical should make one release per year?

---

### Post by picturefreedom on 2009-01-09
regression in the upstream and packaging is something I have come to accept, you should too. because you didn't pay for anyone of them. 

near superstable? buy a mac.

---

### Post by jrusso2 on 2009-01-09
> **PryGuy said:**
> Well, probably Canonical should make one release per year?

This suggestion has been made before as well as rolling release but Ubuntu does not really take to suggestions from its users.

---

### Post by PryGuy on 2009-01-09
You probably think I kinda complain or something... You're not right, Ubuntu is fantastic! I said it 4 years ago and I will repeat it today! But Canonical team, test releases a little bit, please. Fedora team does that...

---

### Post by loell on 2009-01-09
> **PryGuy said:**
>  But Canonical team, test releases a little bit, please. Fedora team does that...

if i may butt in, I don't think there is such a thing as "canonical team", there is [ubuntu release team]("https://launchpad.net/~ubuntu-release") though.

---

### Post by PryGuy on 2009-01-09
> **loell said:**
> if i may butt in, I don't think there is such a thing as "canonical team", there is [ubuntu release team]("https://launchpad.net/~ubuntu-release") though.Okay, sorry, sorry, but you got it, right? ;)

---

### Post by koenn on 2009-01-09
> **picturefreedom said:**
> regression in the upstream and packaging is something I have come to accept, you should too. because you didn't pay for anyone of them. 

near superstable? buy a mac.

The fact that it's free (as in beer) should never be an excuse for being substandard. Open source claims to produce high quality software, so their quality control should include some form of regression testing.

---

### Post by snowpine on 2009-01-09
The current LTS (long term support) release, 6.06 will be reaching its end-of-life in a few months. At that time, you can dist-upgrade to the next LTS, 8.04. Since 8.04 will be a year old at that time, most of the major problems will be solved. :)

The above is one way to look at the development/release cycle. I personally do not subscribe to it (I am using 8.10) but my point is, the Ubuntu release cycle is broad enough to accomodate everyone from the highly risk-tolerant (people already using Jaunty 9.04) to the stability seekers (using the LTS until it reaches end-of-life). Nobody is forcing you to upgrade the day a new release comes out. :-)

I also think that having a regular 6-month cycle generates a lot of "buzz" for the distro, and is probably part of the reason Ubuntu is so well-known and popular.

---

### Post by igknighted on 2009-01-09
> **PryGuy said:**
> You probably think I kinda complain or something... You're not right, Ubuntu is fantastic! I said it 4 years ago and I will repeat it today! But Canonical team, test releases a little bit, please. Fedora team does that...

Such a team does exist... it is you, me, and every other Ubuntu user.  It is our job to try the alpha/beta releases and see what bugs there may be, then report them in launchpad so they can be fixed.  We are all the QC team, so if quality is poor, it is us who need to step it up.

---

### Post by galenanderson on 2009-01-09
I agree. I started using ubuntu 18 months ago and had 8.04 and then 8.4.1 but I waited for 8.10 until january. I was very disapointed. I thought that in the few months that it would have its bugs fixed and it performance tuned. I installed and no sooner was it done than I realized that my computer would never run as fast again. The bootup takes forever, the apps take longer to load. It doesnt seem to have any upgrades really from as far as I can tell, but it is a lot slower. Will the next upgrade solve this problem or should I bite the bullet and re-install 8.04?

---

### Post by Hallvor on 2009-01-10
There should be two versions of Ubuntu - one rolling release with two repositories - one experimental and one for packages that have been tested for a few weeks.

The second one should be an LTS designed for corporate environments or users who want stability.

It would still be possible to launch a new version every six months  with fresh kernels and new artwork.

Today you get to choose between something experimental and buggy and a software museum. Not for me.

---

### Post by PryGuy on 2009-01-12
@Hallvor: Yeah, Debian - like release scheme is a good idea.

---

### Post by SunnyRabbiera on 2009-01-12
Indeed, taking a debian like stance is a good idea.

---

### Post by Alex_B on 2009-01-15
It is not just the releases, the updates have been dismantling my system.

[LIST]
[*]After updating to 8.10 titlebars flickered, until ...
[*]Last weeks updates have limited my computer to low graphics mode.
[*]At some point printing from gedit broke post 8.10
[*]Connecting to network drives via samba broke post 8.10
[*]The version of PulseAudio that shipped with 8.10 caused various sound issues
[/LIST]

Really, I have used Ubuntu and other distributions for years.  Ubuntu has been my primary os for over a year.  I have generally had a very positive experience. Lately... this is just horrible.  I would absolutely not recommend Ubuntu to anyone, not even someone I strongly disliked.  Honestly, in it's current state it is one of the least appealing options available.

If one cannot provide quality software for free, then charge a reasonable price and hire someone to do some testing.  The reason for providing cash-free software should not be that no one would pay for it.

---

### Post by aceinthenight on 2009-01-15
I was very impressed with this latest release. I can remember the pain of Dapper Drake, with drivers and using NDISwrapper... but now, my drivers are already installed finally! It is pretty awesome.

---

### Post by Alex_B on 2009-01-15
ndiswrapper is no longer necessary because of drivers that were added to 2.6.24 and later kernels.
What is wrong here is breaking of existing functionality.  Not that this is limited to Ubuntu, Fedora actually broke yum with an update a few weeks ago but Fedora updates are generally more stable.  Maybe that's the way to go? 
At the very least canonical, or whoever should slow down and do some more testing.

---

