---
title: "Ubuntu Oneiric Ocelot now open for development"
date: 2011-04-29
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Technoviking on 2011-04-29
[From ubuntu-devel mailing list]

> Oneiric is now open for development, with syncs from unstable starting shortly.  The development version starts with an updated GCC and binutils, some soname changes (gmp, libffi, boost) and re-enables the default linker settings, which were disabled just before the natty release.

When merging or requesting a sync, please look at the list of known build failures [1]; bugs (tagged `ftbfs') are filed for every packages which fails to build from source. Please close these with the merged uploads.

Please check your uploads in an oneiric chroot, don't just test in a natty environment. See [2] how to setup such a development chroot.

[1] [http://people.ubuntuwire.org/~wgrant/rebuild-ftbfs-test/test-rebuild-20110413-natty.html](http://people.ubuntuwire.org/~wgrant/rebuild-ftbfs-test/test-rebuild-20110413-natty.html)
[2] [https://wiki.ubuntu.com/DebootstrapChroot](https://wiki.ubuntu.com/DebootstrapChroot)

-- 
ubuntu-devel mailing list
[email]ubuntu-devel@lists.ubuntu.com[/email]
Modify settings or unsubscribe at: [https://lists.ubuntu.com/mailman/listinfo/ubuntu-devel](https://lists.ubuntu.com/mailman/listinfo/ubuntu-devel)

Cheers,
T-V

---

### Post by afv on 2011-04-29
Let's go! :) :popcorn:

---

### Post by go7Ul1ai on 2011-04-29
Getting ready for another exciting 6 months of development :)

---

### Post by MBybee on 2011-04-29
Looking forward to it - got a spare machine all ready :)

---

### Post by rockstarrem on 2011-04-29
Sounds great!

---

### Post by _outlawed_ on 2011-04-29
Time to fire up virtualbox :D

---

### Post by christoph411 on 2011-04-29
Breakage time!!    :popcorn:

---

### Post by amauk on 2011-04-29
> **MBybee said:**
> Looking forward to it - got a spare machine all ready :)Spare machine, ha!
Come on, main machine. Be a man

---

### Post by catlover2 on 2011-04-29
LOL, the day after the release of 11.04, they are starting on 11.10!

I guess not really surprising, but i thought it was funny.

---

### Post by andymorton on 2011-04-29
Right then, I've managed to set up the chroot environment. It's my first time doing this so hopefully I'll learn a lot, contribute quite a bit and won't break my system too badly. Here's to another development cycle! :D

andy

---

### Post by _outlawed_ on 2011-04-29
> **amauk said:**
> Spare machine, ha!
Come on, main machine. Be a man

My main machine is Windows 7, lol. I'm either gonna use virtualbox, my laptop as a tester (already got 11.04, Fedora 15 and Mint 10 on it)...or both.

---

### Post by RJ12 on 2011-04-29
I can't wait for the surprises that will come in the next 6 months of development and testing :)

---

### Post by Harry33 on 2011-04-30
Well what the heck.
Full steam ahead.
Just updated the sources.list into Oneiric and upgraded all packages there were in Oneiric official repos. Like these:
- gcc 4.6
- apt 0.8.14
- libavahi 0.6.30-2
- python-apt
- dpkg 1.16.0
- eglibc
- base-files
- linux 2.6.39-0

Not this one:
- libav 0.7 b1 this would break vlc among others, though

---

### Post by Kevbert on 2011-04-30
Will Oneiric being using Gnome 3.0 ?

---

### Post by Harry33 on 2011-04-30
> **Kevbert said:**
> Will Oneiric being using Gnome 3.0 ?

A number of packages concerning GTK+3 and Gnome3 have been updated and uploaded into Oneiric.
However, this does not mean the desktop shell would be Gnome-shell with Gnome3-panel as a fallback.
No, in Oneiric the desktop shell will be Unity3D and Unity2d as a fallback.
The Unity may be ported into Gnome3 during this dev cycle.

So, Oneiric will likely have Gnome3 desktop with Unity shell.

---

### Post by ninjaaron on 2011-05-01
Call me when the Alphas start rolling out. I'm a bit too much of a sissy for the unstables (which is just as well, being that I'm not a developer)

But seriously, is there a release schedule?

---

### Post by macroshaft on 2011-05-01
> **ninjaaron said:**
> Call me when the Alphas start rolling out. I'm a bit too much of a sissy for the unstables (which is just as well, being that I'm not a developer)

But seriously, is there a release schedule?

[https://wiki.ubuntu.com/OneiricReleaseSchedule]("https://wiki.ubuntu.com/OneiricReleaseSchedule")

---

### Post by Mr_VeRiTy on 2011-05-01
Hopefully Unity will be much improved by the time Oneiric comes out.

---

### Post by Yofel on 2011-05-01
Let the fun times start again! :D

---

### Post by buzzmandt on 2011-05-01
> **Harry33 said:**
> A number of packages concerning GTK+3 and Gnome3 have been updated and uploaded into Oneiric.
However, this does not mean the desktop shell would be Gnome-shell with Gnome3-panel as a fallback.
No, in Oneiric the desktop shell will be Unity3D and Unity2d as a fallback.
The Unity may be ported into Gnome3 during this dev cycle.

So, Oneiric will likely have Gnome3 desktop with Unity shell.

does this mean it will be much easier to integrate (or switch back and forth between unity and) gnome-shell?

---

### Post by el_koraco on 2011-05-01
> **buzzmandt said:**
> does this mean it will be much easier to integrate (or switch back and forth between unity and) gnome-shell?

It means that you will be able to download s stable version of Gnome Shell from the repos and switch between the two at the login screen. The reason this is not possible now with adding the PPA, is that Unity was ported to the GTK2 stack, because of the late release of Gnome 3.

---

### Post by buzzmandt on 2011-05-01
and do we know for sure unity is going to be ported to gnome3?

---

### Post by Johnsie on 2011-05-01
I'm in this time. I've missed the last few versions, but I need to make sure things aren't left out of the next release. My main priorities will making sure there is an adequate replacement for 'Places' menu from the gnome2 panel and also making sure there is a quick and simple way to open applications. These are the two main issues I had with Unity so I'm going to push for a resolution on them.I had alot of bookmarked shares that I kept in 'Places' and it really frustrates me that I now need to click into nautilus first to access my bookmarks. I'm also having alot of issues multitasking with Unity and will be pushing for improvement in that.

---

### Post by el_koraco on 2011-05-01
> **buzzmandt said:**
> and do we know for sure unity is going to be ported to gnome3?

Yup, been said so from the powers that be many times.

---

### Post by TivA on 2011-05-02
I'd rather not do anything, I'm pretty much a numnut. I only have a good concept on GB's and MB's and so on(and a bit of the terminal...

---

### Post by ZarathustraDK on 2011-05-02
I've never been alpha-testing, and I really don't have time to do the whole "launchpad-committed" kinda testing atm.

But I will give the alphas a whirl from time to time on my eee 901 and post some feedback. If Unity is going to change for the better it's going to happen in alpha.

---

### Post by Harry33 on 2011-05-02
I hope we will see thorough GTK+3 and Gnome3 porting into Oneiric.
It would make it easier to choose Gnome-shell for a personal desktop shell option.
That is possible only if Unity (the default shell) is ported into GTK+3.

---

### Post by gsmanners on 2011-05-02
If this Unity is stable by 12.04, it's going to need a LOT of testing between then and now. I can see that.

---

### Post by howefield on 2011-05-03
Usually jump in with the late Alphas, time to get in at the start and try to help with the testing.

:P

---

### Post by Dutch70 on 2011-05-03
I don't really know what this is all about, but I do have some extra partitions on my hdd that I'd like to contribute & help out. 

Can someone tell me what this is all about & what I need to do to help & give me some links please? 

Wow! :P Getting in a the beginning is really exciting. 

Responses here would be very nice, it may help someone else as well, but feel free to pm me with any additional information.

---

### Post by VinDSL on 2011-05-06
> **christoph411 said:**
> Breakage time!!    :popcorn:
Bwahahahaha!

If it ain't broke -- break it!  :D

```

vindsl@Zuul:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu oneiric (development branch)"

vindsl@Zuul:~$ uname -a
Linux Zuul 2.6.39-020639rc6-generic #201105050905 SMP Thu May 5 09:12:03 UTC 2011 i686 i686 i386 GNU/Linux

vindsl@Zuul:~$ unity --version
unity 3.8.12

vindsl@Zuul:~$ /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce 7600 GT/AGP/SSE2
OpenGL version string:  2.1.2 NVIDIA 270.41.06

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity supported:          yes
vindsl@Zuul:~$ 

```

---

### Post by zika on 2011-05-06
```
:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu oneiric (development branch)"
:~$ unity --version
unity 3.8.12
:~$ /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   X.Org
OpenGL renderer string: Gallium 0.4 on AMD RV635
OpenGL version string:  2.1 Mesa 7.11-devel

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity supported:          yes
```And, still, I can not use Unity. Unity-2D works fine.
Problem is that Unity &#8222;works&#8220; but it does not erase items drawn on the screen and, in a second, everything is a mess. No other problem, windows are opening, it works, just with that side-effect...
Any ideas what to toggle to get rid of that...?
It is like that from the very beginning of its appearance in Natty...

---

### Post by VMC on 2011-05-06
In the past all testing releases were held in the Development & Programming sub-section. 

Is this the new home for all our testing comments & questions?

Its right out in the open. No where's to hide. :)

If so, I'm sure we will gather a lot more attention from the passers by.

No complaint, just an observation.

---

### Post by VinDSL on 2011-05-06
> **VMC said:**
> If so, I'm sure we will gather a lot more attention from the passers by.

No complaint, just an observation.
I took me a week for me to find this sub-section.  Then, again, I was suffering from dev release withdrawals...

I'm soooo happy they cranked up this forum early, I can't complain, just an observation..

If had to read, "I used Unity for a whole day and it sucks," one more time, I would have burst!  :D

As it is, I earned a "serious infraction" (never expires) for a comment I made to one of them.

I *think* it's safer in here, regardless...  ;)

---

### Post by MAFoElffen on 2011-05-08
> **VinDSL said:**
> I took me a week for me to find this sub-section.  Then, again,[COLOR=Red] I was suffering from dev release withdrawals...
[/COLOR] 
I'm soooo happy they cranked up this forum early, I can't complain, just an observation..

If had to read, "I used Unity for a whole day and it sucks," one more time, I would have burst!  :D

As it is, I earned a "serious infraction" (never expires) for a comment I made to one of them.

I *think* it's safer in here, regardless...  ;)
LOL, Me also!  I'm in this time with 2 dedicated boxes. 1 for server and 1 for desktop.

---

### Post by Anutesyn on 2011-05-11
> **VMC said:**
> In the past all testing releases were held in the Development & Programming sub-section. 

Is this the new home for all our testing comments & questions?

Its right out in the open. No where's to hide. :)

If so, I'm sure we will gather a lot more attention from the passers by.

No complaint, just an observation.

Same here, hehehe, took me a while before I managed to find this subforum. Not complaining either, this way is a lot better; less clicks. ;)

---

### Post by zemikit on 2011-05-12
Hi!

You don't have a problems with Unity on 11.10?

---

### Post by cariboo on 2011-05-12
> **zemikit said:**
> Hi!

You don't have a problems with Unity on 11.10?

If you have a problem, start a new thread, your questions won't get answered here.

---

### Post by zemikit on 2011-05-12
> **cariboo907 said:**
> If you have a problem, start a new thread, your questions won't get answered here.
I don't have a problem. But I want upgrade to 11.10 and don't have problem with Unity:)

---

### Post by cariboo on 2011-05-12
Have a look at this[ thread]("http://ubuntuforums.org/showthread.php?t=1743440"), the info in the first post should get you going.

---

### Post by corrytonapple on 2011-05-20
I've got a stupid question, but where do I download the desktop beta?  All I found were server betas in a tar.gz format.
Thanks

---

### Post by seeker5528 on 2011-05-20
> **corrytonapple said:**
> I've got a stupid question, but where do I download the desktop beta?  All I found were server betas in a tar.gz format.
Thanks

Beta images are not available until there is a beta.

I think the first official images come when the first alpha is ready, but should be daily builds some time before that.

[http://cdimage.ubuntu.com/daily/](http://cdimage.ubuntu.com/daily/)

It's a little early at this point.

Later, Seeker

---

### Post by novatillasku on 2011-05-20
When Daily Build Oneiric start?
Is when show (oneiric ocelot) here? [http://cdimage.ubuntu.com/daily-live/current/]("http://cdimage.ubuntu.com/daily-live/current/")

---

### Post by Yellow Pasque on 2011-06-06
This subforum was not where I expected it to be.

---

### Post by Makova on 2011-06-06
In alpha1 oneiric may now have Unity and GNOME shell?. Adding repositories?.:)
 Thanks and greeting ...

---

### Post by cariboo on 2011-06-06
Unity is the default desktop in Oneiric, gnome-shell is in the regular repositories.

---

### Post by Penguin360 on 2011-06-10
In the past, when a new version is in development, a new forum section will be created under Development and Programming, how come it is different for Oneiric Ocelot? What it is called Ubuntu +1?

---

### Post by PaulW2U on 2011-06-10
> **CodingBeaver said:**
> In the past, when a new version is in development, a new forum section will be created under Development and Programming, how come it is different for Oneiric Ocelot?
I can't give you an answer because I don't know but the development forum should now be a little easier to find. In the past there have been far too many questions posted about '*upgrading*' to the latest alpha or beta in the main forums and the moderators have had to move all the posts/threads. May be there will be less of that now?

---

### Post by Yellow Pasque on 2011-06-10
> **CodingBeaver said:**
> In the past, when a new version is in development, a new forum section will be created under Development and Programming, how come it is different for Oneiric Ocelot? What it is called Ubuntu +1?
I asked about this and got this response:
> It was moved to the front page to promote it more.
Mike

---

### Post by plurworldinc on 2011-06-28
Sweet, time for some action! :popcorn:

---

### Post by MG&amp;TL on 2011-06-28
Are Linux newbies (relatively, I'm been using Ubuntu for about a month now) allowed to just "jump in" here and start helping, or do we need to go somewhere to get 'trained up' first?

I'm assuming if I get shouted at or moved, then it's a "yes, go away and learn a lot more linux first" :)

And what defines 'help'? I'm quite good at finding errors and very good at complaining, :D and I can use a terminal, but that's about it. Do I need to know/have anything else to start helping, or is it just download alpha versions, test, complain about errors to those who can fix it?

---

### Post by kaldor on 2011-06-28
> **MG&TL said:**
> Are Linux newbies (relatively, I'm been using Ubuntu for about a month now) allowed to just "jump in" here and start helping, or do we need to go somewhere to get 'trained up' first?

I'm assuming if I get shouted at or moved, then it's a "yes, go away and learn a lot more linux first" :)

And what defines 'help'? I'm quite good at finding errors and very good at complaining, :D and I can use a terminal, but that's about it. Do I need to know/have anything else to start helping, or is it just download alpha versions, test, complain about errors to those who can fix it?

Community help is always appreciated. Report all the bugs you encounter, providing nobody else already has. I suggest you create a Launchpad account and check around there. 

This isn't an official development forum; it's a community discussion forum for Ubuntu development, and the devs rarely check here. Posting here is a good way to get help or help others with the testing releases of Ubuntu.

Just become familiar with how things work and you'll do just fine. Discuss problems here, report problems on Launchpad. That's what I usually do.

Edit: No need to worry about getting shouted at around here. Pretty calm community :)

Edit 2: Check out [https://launchpad.net/ubuntu/oneiric](https://launchpad.net/ubuntu/oneiric) for Ubuntu 11.10 development and bug reporting.

---

### Post by MG&amp;TL on 2011-06-28
Thanks kaldor, I know it's a good community, I make a point of saying so on most forums I post, that's just how it gets referred to in my family. :)

Thanks for the links and help, kaldor, "extra foam sugar free ubuntu":shock:

Might sort out my first bug-probably a spelling error -  this afternoon. :)

---

### Post by TyraeClouds on 2011-07-01
Just wanted to say right quick that this is absolutely amazing.

I'm new to Linux and of course Ubuntu. The idea that you guys just come together and do all this work for us is just... astonishing. People see others nature as being inherently selfish but, I see this community and am completely blown away.

So...sorry if this is the wrong place for this message but...

Thank you all

---

### Post by MG&amp;TL on 2011-07-02
Agreed, tyraeclouds. Ubuntu is a beautiful thing :D

---

### Post by leelika08 on 2011-08-16
> **catlover2 said:**
> LOL, the day after the release of 11.04, they are starting on 11.10!

I guess not really surprising, but i thought it was funny.
Right then, I've managed to set up the chroot environment. It's my first  time doing this so hopefully I'll learn a lot, contribute quite a bit  and won't break my system too badly. Here's to another development  cycle!

---

### Post by buntu63 on 2011-09-21
2 b honest more bugs than a thai hotel! :x

---

### Post by VinDSL on 2011-09-22
> **buntu63 said:**
> 2 b honest more bugs than a thai hotel! :x
Buy some RAID.  That's why we test dev releases.  Where you coming from?

"2 b honest" I can't stand it when things just work.

Keep them bugs a comin' Canonical...  :D

---

### Post by ventrical on 2011-09-23
> **VinDSL said:**
> Buy some RAID.  That's why we test dev releases.  Where you coming from?

"2 b honest" I can't stand it when things just work.

Keep them bugs a comin' Canonical...  :D

Here...s lunch... you earned it :)

---

