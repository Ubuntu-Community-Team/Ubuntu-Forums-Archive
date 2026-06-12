---
title: "Second browser, recommendations?"
date: 2013-09-25
forum: Recurring Discussions
---

### Post by josh17 on 2013-09-25
I need a second browser, one for each youtube channel becuase I don't wan to constantly log out from one to the other. I was going to get Comodo IceDragon but it isn't linux compatible :/ Any suggestions for browsers? (Not google chrome, PLEASE)

---

### Post by Vaphell on 2013-09-25
Separate profile(s) in FF
Opera
Chromium

---

### Post by josh17 on 2013-09-25
> **Vaphell said:**
> Separate profile(s) in FF
Opera
Chromium

What do you mean separate profiles?

---

### Post by Vaphell on 2013-09-25
when you run
```
firefox -ProfileManager -no-remote
```
you are presented with the profile manager window

[http://askubuntu.com/questions/226335/how-to-create-shortcuts-to-different-firefox-profiles](http://askubuntu.com/questions/226335/how-to-create-shortcuts-to-different-firefox-profiles)

---

### Post by whatthefunk on 2013-09-25
I really like Opera....  It would maybe be easier to try the separate FF profiles first though.

---

### Post by andrew.46 on 2013-09-25
Perhaps have a look at SeaMonkey? I see there was a release on September 17th 2013 so development still marches on...

---

### Post by dshgna on 2013-09-26
Chromium - can create two or more users
Opera
Midori (not a sophisticated gui but pretty functional)

---

### Post by nerdtron on 2013-09-26
Is this voting time? :D
Mine has 3 browsers:
Firefox
Chromium
Opera
All are configured to "open tabs from last time" so that my 50+ tabs on firefox are preserved.

---

### Post by vasa1 on 2013-09-26
> **nerdtron said:**
> Is this voting time? :D
....
LOL!
Add Xombrero :)

---

### Post by whatthefunk on 2013-09-26
> **nerdtron said:**
> 
All are configured to "open tabs from last time" so that my 50+ tabs on firefox are preserved.

What do you do with 50 tabs in a browser???  I think the most Ive ever had open is 10 or 15 and that was way too confusing to deal with.

---

### Post by Vaphell on 2013-09-26
i sometimes reach ~30 because that's how much space my vertical tab tree in FF has and even then i lose track of things. In case of normal layouts it's definitely insane.

---

### Post by kurt18947 on 2013-09-26
The new Opera does seem like a nice choice on modestly powerful or older machines.  It feels faster than either Firefox or Chromium.

---

### Post by rolltide101x on 2013-09-26
I vote Opera for this thread and once I get over 10 or so it just gets to annoying to find what I want lol

---

### Post by Elfy on 2013-09-26
*Thread moved to **The Cafe**.*

---

### Post by jamesisin on 2013-09-26
Opera:

[http://jamesisin.com/a_high-tech_blech/index.php/2008/09/add-opera-to-ubuntus-update-manager-synaptic/](http://jamesisin.com/a_high-tech_blech/index.php/2008/09/add-opera-to-ubuntus-update-manager-synaptic/)

---

### Post by anachronism2 on 2013-09-26
[Fascinating,]("http://www.comodo.com/home/browsers-toolbars/icedragon-browser.php") a more secure yet more lightweight Firefox with a cooler name. A-ha-ha. Sorry. What prevents it from being compatible with Linux?

---

### Post by su:bhatta on 2013-09-27
Hey ! today only I installed Opera after years of using FF!

& I like it. But Comodo! a cool name, got that link open hafta try! 

BTW, Opera MAil, is it coming to Linux? When?

---

### Post by stalkingwolf on 2013-09-27
I use epiphany as a second.

---

### Post by su:bhatta on 2013-09-27
Hey, I used epiphany as second for a month, today switched to Opera, quiet loving it!

P.S. That Comodo doesnot have a Linux version :(

---

### Post by nerdtron on 2013-09-27
> **whatthefunk said:**
> What do you do with 50 tabs in a browser???  I think the most Ive ever had open is 10 or 15 and that was way too confusing to deal with.

Not all 50 tabs are visible. I use tab groups in Firefox, 3 separate tab groups for each task I'm currently working on and 1 more group for misc. Also, I have 8 pinned tabs to conserve space. :D

---

### Post by pqwoerituytrueiwoq on 2013-09-28
> **whatthefunk said:**
> What do you do with 50 tabs in a browser???  I think the most Ive ever had open is 10 or 15 and that was way too confusing to deal with.
i have over double that, i use tab groups to manage them and i have ff set to not load them till i select them

multiple ff profiles is not that usable then you need both open at the same time, i have chromium around for that

---

### Post by blackbird34 on 2013-10-02
I use multiple profiles in firefox, two atm but sometimes more. 

Instead of fiddling around with command line I set firefox to start on my main profile, and made a [desktop file]("https://help.ubuntu.com/community/UnityLaunchersAndDesktopFiles") for the second (and other extra) profiles, which I called "Redpanda". I use Synapse so it's really fast starting either of them up, no lag, no hassle. If anyone wants to use my computer, I give them the Redpanda profile, as i keep it completely empty. This works with Synapse, but also with the Xfce menu (I run Xfce on my buntu), classicMenu indicator, and (i assume) Cinnamon, Unity...

Thus I only actually used the ```
firefox -P --no-remote
``` command once, when I set these multiple profiles up.

---

### Post by vance_2 on 2013-10-02
I started using Opera just a few weeks ago and am loving it.

---

### Post by RichardET on 2013-10-03
Needing a "second browser to run youtube" doesn't seem like a problem to me.......I know what!  Buy another computer!  Run two at once on your desk.  Or do what I do - get an i7 with 24 GB of memory and run several VM's at once.

---

### Post by TeamRocket1233c on 2013-10-03
Firefox Nightly, but since this is Ubuntu you're most likely running, you gotta add the ubuntu-mozilla-daily PPA, and enabling root access could help too:

```
[user@ubuntu ~]$ sudo passwd root
```

...and when prompted, put whatever password you wanna use for root. Then..

```
[user@ubuntu ~]$ su
root password:
```

...and you should be in Root. Or you can use sudo su..

```
[user@ubuntu ~]$ sudo su
password for user:
```

Finally..

```
[root@ubuntu user ~]# add-apt-repository ppa:ubuntu-mozilla-daily && apt-get update && apt-get remove firefox && apt-get install firefox-trunk
```

...and you should have Firefox Nightly installed.



PS: Aptitude is better than apt-get in a lot of ways, so in order to install it, go into the Root account...

```
[user@ubuntu ~]$ su
root password:
```

Or use sudo su, whichever works for you...

```
[user@ubuntu ~]$ sudo su
password for user:
```

And then type in the following to install aptitude...

```
[root@ubuntu user ~]# apt-get install aptitude
```

Now Debian comes with aptitude no matter what you do, and from what I found out when playing with 13.10 for a while in Vbox when I was running Fedora, Ubuntu netinstalls also seem to come with aptitude, meanwhile regular Ubuntu/Kubuntu/Lubuntu/Ubuntu GNOME/Xubuntu installs require you to install aptitude if you want it, at least in my experience.

---

### Post by pqwoerituytrueiwoq on 2013-10-03
don't do that 1st sudo command in the previous post, it is not needed and will make the system less secure, it also enabled root gui login
the second command should be [FONT=courier new]sudo su[/FONT]

---

### Post by TeamRocket1233c on 2013-10-03
Meh, I just prefer to have root access enabled, and the distro I run now has it enabled by default, more convenient, and hey, haven't screwed anything up yet. lol

---

### Post by nerdtron on 2013-10-04
> **TeamRocket1233c said:**
> Meh, I just prefer to have root access enabled, and the distro I run now has it enabled by default, more convenient, and hey, haven't screwed anything up yet. lol

You will easily learn the lesson to not enable root password when you are dealing with servers facing the public internet.

---

### Post by vasa1 on 2013-10-04
> **TeamRocket1233c said:**
> Meh, I just prefer to have root access enabled, and the distro I run now has it enabled by default, more convenient, and hey, haven't screwed anything up yet. lol

All the best to you but why do you recommend it to others?

---

### Post by TeamRocket1233c on 2013-10-04
> **vasa1 said:**
> All the best to you but why do you recommend it to others?

They can also use sudo su, of course.

---

### Post by TeamRocket1233c on 2013-10-04
> **pqwoerituytrueiwoq said:**
> don't do that 1st sudo command in the previous post, it is not needed and will make the system less secure, it also enabled root gui login
the second command should be [FONT=courier new]sudo su[/FONT]

I revised it by adding sudo su in there, and a little tidbit about installing aptitude.

---

### Post by vasa1 on 2013-10-05
@TeamRocket1233c, So you're recommending `sudo su` just to install a ppa?

---

### Post by TeamRocket1233c on 2013-10-05
And to install the browser itself or anything else that need be installed, or to run system updates if need be.

---

### Post by vegan.philosophy on 2013-11-02
Chrome is probably the lightest web browser. It is also fast. Firefox is good because of its consistent updates and very good add-ons. Safari is probably useless for Linux users even if it is used with 'Playonlinux'.

---

### Post by jamesisin on 2013-11-04
TeamRocket1233c - Your post still implies one needs to enable root in order to install the Firefox PPA or Aptitude.  That is simply not the case.  I would say this is poor advice and would not recommend to any user that they enable root.

Everyone else - Please don't enable root unless you know exactly what you are doing, and if you know exactly what you are doing please don't enable root.

---

### Post by rencemc on 2013-11-04
I'm curious - Why not Chrome ? I don't use it on Linux often, but I always use it on Winblows.

---

### Post by monkeybrain20122 on 2013-11-04
> **whatthefunk said:**
> What do you do with 50 tabs in a browser???  I think the most Ive ever had open is 10 or 15 and that was way too confusing to deal with.

I have 150. :) Stuffs I have not finished reading, things I intend to read but haven't got time yet but not worthy enough to be bookmarked, technical sites that cross reference each others etc.

I use Firefox as my main browser, but also have chrome in case I need up to date flash (very rarely). I can't see the point of chromium at all.

---

### Post by neu5eeCh on 2013-11-04
> **vegan.philosophy said:**
> Chrome is probably the lightest web browser. It is also fast. Firefox is good because of its consistent updates and very good add-ons. Safari is probably useless for Linux users even if it is used with 'Playonlinux'.

I think Midori is lighter than Chrome, probably the lightest browser that still runs Flash? There are _much_ lighter browsers if Flash isn't needed.

---

### Post by su:bhatta on 2013-11-06
Currently Using Opera as my second browser, just shifted from Epiphany ! 

With Gnome Shell 3.10, Epiphany version is a lot better than saucy repos version! 

Firefox is numero uno, as usual !

---

### Post by philinux on 2013-11-08
Moved to recurring.

---

### Post by whatthefunk on 2013-11-10
> **monkeybrain20122 said:**
> I have 150. :) Stuffs I have not finished reading, things I intend to read but haven't got time yet but not worthy enough to be bookmarked, technical sites that cross reference each others etc.

Why not use bookmarks?

---

