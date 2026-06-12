---
title: "Why Two Ubuntu Versions?"
date: 2015-11-28
forum: New to Ubuntu
---

### Post by stephen91 on 2015-11-28
Hello,

I am an experienced Windows user newly branching into the Ubuntu world and I have a few questions please.

I see that Ubuntu is offered in two versions on the Ubuntu website, version 14.04.3 and version 15.10. Why is development spread over two versions instead of just upgrading and enhancing one version?

As a general user I can see the advantage of using 14.04.3 (which has a five year support period) versus 15.10 (which only has a nine month support cycle). Why would someone use 15.10 (unless it has some feature that you need) when it would be frozen after nine months? It almost seems to me that 14.04.3 is the General Release version of the OS and 15.10 is like a Beta Release.

While browsing through the forums and articles I see mention of version 15.04. Is 15.04 a predecessor version of 15.10?

Let me thank you in advance for your help. Being new to the world of Ubuntu perhaps I am missing the implied nuances of these versions so I would like to get up to speed.

Cheers!

---

### Post by SlidingHorn on 2015-11-28
Basically, it's to allow the user to choose whether they want to keep a more stable environment with long-term support vs choosing to keep up with the latest releases, which can include new or updated software. 

Generally, for home use, I go with the latest versions so that I have the latest and greatest in updates, hardware support, etc.  If you're in a business environment, or just don't feel like upgrading every 9 months, then take the LTS :)

---

### Post by Bashing-om on 2015-11-28
stephen91; Hi ! Welcome to the forum .

Yeah, You do have the right of  it.

Presently there are 4 active releases of (u)buntu.
12.04 - (LTS) support til April of 2017
15.04 short term - in my opinion the beta for the next LTS release
15.10 ... same same, a short term release -> looking forward to release 16.04
14.04  (LTS) support til April of 2019.

There is a new release every 6 months, the 2 year release is Long Term Support ( 5 years ).

The nomenclature of the release:
the year released as in 12, 14, 15, 16
the month released as in 04 or 10

The short term support is out here with the newest and greatest of what will be .. Thrown out here for us to beat up on and see what breaks in the real world.

[INDENT][INDENT][INDENT]takes the world to raise
[INDENT][INDENT][INDENT][INDENT]ubuntu
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by stephen91 on 2015-11-28
Thank you and understood.

To upgrade from one Ubuntu version to another is it a matter of downloading the new package and running the installation process or is there a special procedure to follow? I would of course backup any personal files in case the installation wipes the HDD.

---

### Post by Bucky Ball on 2015-11-28
Welcome. 14.04 LTS = 14=2014; 04=April. April 2014, if that makes sense. So the release number gives the year and date.

For Ubuntu LTS = long-term support release, supported for five years from the release date (some spins, like Xubuntu, are three). Everything else is an interim release. They have nine months support.  

Currently, there are four supported releases: 12.04 LTS, 14.04 LTS, 15.04 and 15.10. 14.04 LTS and 15.10 can be upgraded to 16.04 LTS later in 2016. Ubuntu releases can be upgraded *to the next release* online. LTS releases can be upgraded to the next LTS online. The only other option is a clean install. 

From looking at the release numbers of the current releases you should be able to work out their support life. For instance, not much point installing 15.04 when 15.10 has both longer support and is upgradeable to 16.04 LTS (which will then get you five years support). 

As alluded to by SlidingHorn, LTS is aimed at production machines, servers and stability. And for those who don't want to install/upgrade every six months (which is the case with interim releases).

Interim releases help to keep Ubuntu developing and up-to-date, put simplistically. There are others more involved who can give more detail about that and hopefully will. :)

Hope that helps.

* Oops, ninja-ed by Bashing-Om. Some redundant info here now, but there you go, two versions for the price of one! ;)

---

### Post by Bashing-om on 2015-11-28
stephen91; Nope;

Although one may ( and many do ) there is a easier way .. within the system is the "update-manager" - just hit the button when a new release becomes available. The system will advise you when this new release is available.
Just make sure the current install is fully updated and as well that any PPAs that you have added to that current install has support in the new install. ( -P-ersnal -P-ackage -A-rchive; not a direct component of the operating system .. some clever programming from a 3rd party )
But yes, always keep current backups ... never can tell what might happen !

[INDENT][INDENT]all good
[/INDENT][/INDENT]

---

### Post by stephen91 on 2015-11-28
Thanks once again for everyone's help.

Just to be clear on the point about "update-manager" this button will appear when a new release becomes available and only then? So if I am running 14.04.3 I wouldn't expect any "update-manager" button to appear until the five year cycle is up while if I was running 15.10 I would get this button when the nine month cycle is up?

Once I got 14.04.3 installed one of the first things I did was to go into the Ubuntu Software Centre and install Chromium. Is Chromium an example of a PPA? Or are PPA's only for packages I install outside of the Ubuntu Software Centre (e.g. through Terminal commands)?

Thanks.

---

### Post by matt_symes on 2015-11-28
Hi

Hopefully I'm going to muddy the waters here but there are some things to point out.

Long term support (LTS) releases now have what's called the "hardware enablement stack" upgrades.

This allows the LTS releases to use the kernel, drivers and X stack from later releases. 

As has been pointed out, later releases of Ubuntu generally support newer hardware and have updated drivers.

I'm on 14.04 (Trusty) but using the Utopic (14.10) hardware stack so i have all the new and updated Utopic (14.10) drivers.

There is a new hardware enablement stack for 15.04 (Vivid) that i could upgrade to if i needed to but i have no need to.

BTW: All the adjectives above in parenthesis above are the codenames for those release.

The benefits of upgrading include new and updated applications software, updated languages such as new versions of python, newer compliers and newer windows managers etc.

You can run, as i do, multiple versions of Ubuntu but for you main Ubuntu installation:

If the benefits of the newer software outweigh the downside of 9 months support then using the interim release pays for you.

If, like me, it doesn't then stick to LTS releases. 

That being said, i just about to move to a testing release because i want to test for the next LTS release that is released April next year (16.04).

Kind regards

---

### Post by Bashing-om on 2015-11-28
stephen91; Welp:

> 
Just to be clear on the point about "update-manager"

configurable; one may set a current LTS release to point to the next short term release if ya want . the upgrade path is generally LTS to LTS .

> 
Once I got 14.04.3 installed one of the first things I did was to go into the Ubuntu Software Centre and install Chromium. Is Chromium an example of a PPA? Or are PPA's only for packages I install outside of the Ubuntu Software Centre (e.g. through Terminal commands)?


If a package is in the software repository then that package is not obtained from a PPA in this instance. Now that said ... as Mat says -- to cloud the waters... though a package is available in the repo ( repository) it is entirely possible that the programmer(s) are hard at work and have made up a newer version. The newer version 'can' be installed via a PPA ; IF the package maintainer has made an available PPA .

[INDENT][INDENT]the web we weave
[INDENT][INDENT][INDENT]ourselves
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by grahammechanical on 2015-11-28
We get a new Ubuntu version every six months. That is the way of Ubuntu development at present. The releases come out at the end of April and at the end of October. Every two years the April release is given 5 years support and is called a Long Term Support (LTS) version.

When we install an LTS version Software Updater is set by default to notify us of the next LTS release. If we install an Interim release Software Updater is set by default to notify us of any new version. We get notification when the time comes and then it is our choice to allow the upgrade of not. We can, of course, change these settings in System Settings>Software & Updates>Updates tab.

For a few days after a version of Ubuntu is released we get nagged by Software Updater when it checks for updates. It will show us a clickable button to start the upgrade.

The idea behind a 26 week development cycle is to drive the development of Ubuntu. Other Linux distributions do things differently. With those distributions you get a new version whenever its developers think the version is finished.

Regards.

---

### Post by Bucky Ball on 2015-11-28
You can switch reminders from the update manager off completely if you like. I always do them manually, usually once or twice a week.

---

### Post by Bucky Ball on 2015-11-28
You can switch reminders from update manager off completely if you like. I update manually once or twice a week. :)

I am talking about updates here, regular updates to the system should be done at least weekly. These are updates to your currently installed system, NOT upgrades of the OS to a newer release. 

There is a difference between updates and upgrades. :)

---

### Post by coldraven on 2015-11-29
Regarding PPAs: If you open "Software and Updates" and select the tab "Other Software" you can add PPAs there. So, for example, I use a utility called get-iplayer but the version in the Software Centre is slightly out of date. By adding the PPA from the developers web-site it will automatically update to the latest version.
One caveat is that you need to trust that the developer is not going to add any malicious code to their software. Of course this applies to any program that you find on the internet especially if you run Windows.
You might want to install Synaptic package manager, you can think of it as "Software Centre Pro". I find that it's useful for discovering things that I had no idea about and also gives information about where application files are stored.
You cannot run Synaptic and the Software Centre at the same time as they are both just front-ends of the same underlying process.
Happy Ubuntuing! :)

---

### Post by moebob24 on 2015-11-29
I recommend running the current LTS for your main box. Best support, most stable, updates will be coming out for it until 2019.

---

### Post by Topsiho on 2015-11-30
I have read the information given so far, and all of it seems to be correct, though somewhat repetitive.
What i miss is that the upgrade path is very time consuming: be prepared that it may take far longer to upgrade then downloading a .iso file, burn it o a DVD or USB-stick, and then install it, and then install newer updates (according to my experience (YMMV). Only: you have to reinstall your applications not included in the .iso (giving you a chance to do a nice cleanup :) ).
Upgrading may lead, depending on what you have installed, to a download far exceeding the contents of the .iso file, and after that a really giant update-session.
So: upgrading is easy, but be prepared for a very time consuming process.

Topsiho

---

