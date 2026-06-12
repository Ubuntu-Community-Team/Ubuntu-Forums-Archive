---
title: "Incremental updates?"
date: 2008-10-14
forum: Other OS Talk
---

### Post by Phasmus on 2008-10-14
A use case, to illustrate my irk!

===

Phasmus is using Ubuntu version X.  A program he enjoys releases a new version with a feature he's been wanting for months.  He wants to upgrade to the new version of this program.  With Ubuntu his only options are to wait until Ubuntu version Y comes out (and hope it includes the most recent release of the program and that the upgrade goes smoothly), hope for (or build his own) deb of the new version or install the program from source and jump through various dependency, previous-version-conflict and desktop-integration hoops.

===

Okay, okay, we all know Linux is not Windows.  Maybe the issues above are not insurmountable.  But I'm getting tired of surmounting them.  When I want to upgrade one little nugget of software without throwing my whole OS into turmoil the repository system sometimes falls short.  

So my question is this: are there any sound Linux distros that handle this better?  Perhaps by either updating repositories incrementally as new software versions become available, or providing more straightforward, foolproof means of replacing default software versions?

---

### Post by Vorian Grey on 2008-10-14
Debian handles it very well. PCLinuxOS does as well. I believe Arch is another. 

Personally, I would use Debian. If you want a sleek, fast Debian, try sidux.

---

### Post by SunnyRabbiera on 2008-10-14
yeh there are times I wish Ubuntu would become more of a rolling release type distro as opposed to having to go from version a of ubuntu that has worked well on your system since the day you installed it to version of b of ubuntu that might have some nice bells and whistles but it works like crap on your hardware.
Thats why I am using linux mint, its the best of both worlds

---

### Post by WWSmith36 on 2008-10-14
There are numerous ways to get newer version of software without upgrading your version of ubuntu.

First thing to consider is checking the backports.
[https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports)
If the new version is not available in backports, you can request it by creating a new bug report in the Backports Product of Launchpad.

Some software developers maintain there own repositories which you can add to your /etc/apt/sources.list so you will always have the most recent release (ex. Avant, Opera, Skype, Firefox, Compiz Fusion, Wine).  There are also third party repositories like Medibuntu and Googles Linux Repository.

The Official Ubuntu Repositories are concerned really only about stability.  So if you want something that they dont have, feel free to install it from another source.  Thats what I do.

:guitar:

---

### Post by smoker on 2008-10-14
> **SunnyRabbiera said:**
> 
Thats why I am using linux mint, its the best of both worlds

was going to mention mintupdate, doesn't that give you the chance to use the latest updated apps?
[http://en.wikipedia.org/wiki/Linux_Mint](http://en.wikipedia.org/wiki/Linux_Mint)

---

### Post by SunnyRabbiera on 2008-10-14
> **smoker said:**
> was going to mention mintupdate, doesn't that give you the chance to use the latest updated apps?
[http://en.wikipedia.org/wiki/Linux_Mint](http://en.wikipedia.org/wiki/Linux_Mint)

It does, I have gotten firefox and Thunderbird updates through that

---

### Post by kpkeerthi on 2008-10-15
[www.getdeb.net](www.getdeb.net) ???

or use rolling release distros.

---

### Post by mips on 2008-10-16
If you don't want to jump through hoops to get newer stuff then move to a rolling release distro.

---

### Post by handy on 2008-10-16
Though rolling release will make you jump through hoops every now & then also...

As I've been experiencing for the last couple of days.

---

### Post by Rumor on 2008-10-16
> **Phasmus said:**
> 
So my question is this: are there any sound Linux distros that handle this better?  Perhaps by either updating repositories incrementally as new software versions become available, or providing more straightforward, foolproof means of replacing default software versions?

One of the reasons I jumped from Ubuntu to Arch a couple years ago was the headache caused by the upgrade from one version to the next. in Arch I found what you are describing, an incrementally updated distro. Arch is ideally designed to be installed once only, and then updated periodically as the user sees fit. As such, there is no reason to download and burn each new release as it comes out, as explained in the [wiki]("http://wiki.archlinux.org/index.php/FAQ#Q.29_When_will_the_new_release_be_made.3F"). 

There are several folks in the Arch community whose installs are several years old and every bit as current as the person who installed it yesterday.

---

### Post by snowpine on 2008-10-16
Every Linux distro has its own development and release cycle. It is well-publicized that Ubuntu has a 6-month, non-rolling cycle. One should take this information into consideration when deciding which distro to use.

I would take issue with your sentence that begins "With Ubuntu his only options are..." When asking for help and advice on the forums, it's good to keep an open mind that there may be options you haven't yet considered. :) For example, in this case, you did not take the backports repository into consideration.

---

### Post by Phasmus on 2008-10-16
Thanks for all the info, folks.  Consensus seems to fall toward rolling release.  So it seems Mint, Arch, some Debianoids and PCLOS are the premiere rolling release distros?

Does anyone have any particular recommendations or anecdotes relevant to these?  I've been using Linux for quite a while but I disdain spending a great deal of time tweaking things.  This makes me more hesitant to go for something like Arch which, though I have heard good things about it, I gather requires quite a bit of hand-holding before it will do what is expected of it (i.e. run my applications).

---

### Post by Phasmus on 2008-10-16
> **snowpine said:**
> Every Linux distro has its own development and release cycle. It is well-publicized that Ubuntu has a 6-month, non-rolling cycle. One should take this information into consideration when deciding which distro to use.

I would take issue with your sentence that begins "With Ubuntu his only options are..." When asking for help and advice on the forums, it's good to keep an open mind that there may be options you haven't yet considered. :) For example, in this case, you did not take the backports repository into consideration.

Does anyone have an easily parsed list of what applications/versions are actually in backports?  I enable the backports repository upon installation of any Ubuntu release, and I have yet to detect significant updates for applications I actually use.  It is possible I've just overlooked them, or that the backporters are not working on older versions of Ubuntu (I'm still on Gutsy at work).  Getdeb is trailing off in support for older releases too.  

Now, it might be argued I'm asking for it by not upgrading to a newer, more actively supported version of Ubuntu.  But, as I have learned, the fixed release cycles makes this state of affairs inevitable unless I'm willing to reshuffle my OS every year or so.  (Even LTS releases only receive extended security, not application, updates, right?)

---

### Post by crimesaucer on 2008-10-16
> **handy said:**
> Though rolling release will make you jump through hoops every now & then also...

As I've been experiencing for the last couple of days.


Me too..... I just spent 1.5 days re-installing Arch, and re-building everything from source.


I have almost gotten it back to the way I had it before I broke somethings.



The one good thing about this re-install is I've changed my C[XX]FLAGS to "-Os" instead of "O2" to give that a try.




And to get back on topic..... I love the rolling release, but sometimes you have to restrain yourself from the old habit of updating everyday just to do it...... and I've basically given up on the Testing repository forever..... especially once you've put the time and effort of building everything from source, it's not a whole lot of fun to destroy an install like it used to be when it would only take an hour or two to get it back to the way it was.

---

### Post by snowpine on 2008-10-16
> **Phasmus said:**
> Does anyone have an easily parsed list of what applications/versions are actually in backports?  I enable the backports repository upon installation of any Ubuntu release, and I have yet to detect significant updates for applications I actually use.  It is possible I've just overlooked them, or that the backporters are not working on older versions of Ubuntu (I'm still on Gutsy at work).  Getdeb is trailing off in support for older releases too.  

Now, it might be argued I'm asking for it by not upgrading to a newer, more actively supported version of Ubuntu.  But, as I have learned, the fixed release cycles makes this state of affairs inevitable unless I'm willing to reshuffle my OS every year or so.  (Even LTS releases only receive extended security, not application, updates, right?)

Here's a list of the hardy-backports (with links at the top for intrepid, gutsy, etc.): [http://packages.ubuntu.com/hardy-backports/](http://packages.ubuntu.com/hardy-backports/)

---

### Post by handy on 2008-10-16
> **crimesaucer said:**
> Me too..... I just spent 1.5 days re-installing Arch, and re-building everything from source.


I have almost gotten it back to the way I had it before I broke somethings.

...

And to get back on topic..... I love the rolling release, but sometimes you have to restrain yourself from the old habit of updating everyday just to do it...... and I've basically given up on the Testing repository forever..... especially once you've put the time and effort of building everything from source, it's not a whole lot of fun to destroy an install like it used to be when it would only take an hour or two to get it back to the way it was.

I happened to luck out badly, both of my Arch machines hadn't been updated for a while, one I decided to do a total rebuild on because it was a mess, the other I installed xfce on, which I really like, after an -Syy & & -Syu I caught a new kernel & some other files, which have messed up my internet, going back to previous versions does not repair the problem.

So, at the moment I have one install that is great for everything but the internet, & another which I can not proceed any further with the installation.

Rolling release, has its problems, it is a good idea to check what is coming in, & especially if it is a new kernel, be sure that it has been around for a couple of weeks as it could save you days of work if your particular hardware setup is vulnerable to an untested problem.

I don't think that rolling release is a great idea for a server system.

[I]**[Edit:]**

Redid the downgrade again, rebooted & now I have fully functioning internet on the iMac.  Will look into the stalled install on #2 machine with fresh knowledge. [/I]

---

