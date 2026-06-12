---
title: "Eclipse repository site"
date: 2007-08-23
forum: Programming Talk
---

### Post by aitorcalero on 2007-08-23
Is there out there any Synaptic repository with the latest versions of Eclipse?
Currently I am using Eclipse Europa (3.3) but I have download it manually. It would be great to haver a repository which holds the latest version.

---

### Post by Ramses de Norre on 2007-08-23
Eclipse has its own update system built in which uses the eclipse repo (it's somewhere in the help menu).

---

### Post by aitorcalero on 2007-08-23
Yes, but yo cannot upgrade form 3.2 to 3.3 in this update system, and the installation from repository is different

---

### Post by zachtib on 2007-08-23
im interested in this as well, or if anyone has debs built for 3.3

---

### Post by progressnerd on 2007-10-10
no, it's not in the repo, and apparently there's no immediately plan to add it. Fortunately, Eclipse is a standalone application -- no real "installation" involved. So you can download the latest version from Eclipse.org and just drop it in a directory somewhere like /opt/eclipse or /home/username/eclipse and run it. You can also add a custom launcher to your applications menu using the Eclipse executable as the command and the icon.xpm file for the icon.

Also, it's pretty important to install Sun's java, because GCJ will give you all sorts of problems in Eclipse.

---

### Post by mrweektor on 2009-01-21
i know i'm resurecting an old thread... but i'd like to find a solution to this other than just running an executable.
i'm having the same problem as aitorcalero. is there a way to install it from the files i downloaded from eclipse.org so that it does basically everything apt would do?

---

### Post by mövenpick on 2009-03-29
Hi,

I just installed Ubuntu myself and was wondering myself how to install eclipse. I used aptitude which installed eclipse 3.2.
[LIST]
[*]open terminal
[*]start aptitude
[*]goto Not Installed Packages
[*]search for eclipse ('/' and eclipse)
[*]select it ('+')
[*]start installation ('g')
[/LIST]

After the initial installation every user can upgrade and install additional plugins with the integrated update feature.

Cheers - mövenpick

---

### Post by Can+~ on 2009-03-29
> **mrweektor said:**
> i know i'm resurecting an old thread... but i'd like to find a solution to this other than just running an executable.
i'm having the same problem as aitorcalero. is there a way to install it from the files i downloaded from eclipse.org so that it does basically everything apt would do?

That's one of the nice things of eclipse, it requires 0 installation, you can drag it, drop it in a folder and run it.

---

### Post by Reiger on 2009-03-29
Yes but this gives you 2 problems:
(1) GCJ. Ubuntu's version of eclipse uses the GCJ and the GCJ is partly Java 1.4, partyl 1.5 and partly unimplemented. Currently Java is at 1.6 update 13 already!
(2) Eclipse from the repositories, even in Jaunty is at version 3.2 and the current version is 3.4. As posted before, you can't directly upgrade from 3.2 to 3.3 nevermind now about 3.4...

---

### Post by gunnar123 on 2009-04-28
Why is there a 3.2 Eclipse version from 2007 in the latest Ubuntu release (Jaunty) when nobody can use it anyway but instead needs to do a manual install of a later Eclipse version ?

Isn't it better to remove Eclipse altogether from Ubuntu repositories if there is no ambition to keep it up to date ?  A two year old IDE can be past its primes in the Internet era. 

One concrete example of failure is installing the Google Android SDK which requires Eclipse 3.3 as minimum.

---

### Post by codedash on 2009-05-31
As much as it hurts me, here is why
[http://packages.debian.org/unstable/devel/eclipse-platform](http://packages.debian.org/unstable/devel/eclipse-platform)

Edit: It is so easy to install it from the site that i was stunned. Install sun java 6 jdk then download eclipse for java devs for linux, extract and run the file eclipse.

---

### Post by pho3nixf1re on 2009-11-12
this did it for me.
[http://blog.yogarine.com/2009/08/eclipse-35-galileo-packages-for-ubuntu.html](http://blog.yogarine.com/2009/08/eclipse-35-galileo-packages-for-ubuntu.html)

---

### Post by cgb223 on 2009-12-19
is this still a problem? if so please point me in the direction of the person in charge of the ubuntu repos, its 2009 (2010 soon too) it about time we see the latest... (or maybe the 64 bit version too... or a decent flash driver....... or bringing gcj up to standards and like forwards 2 years.........) 

were ubuntu, were better than this. point me in the direction of the people who can change it (because i cant) and I'll see what i can do

ty

---

### Post by cgb223 on 2009-12-19
my bad its fixed, shoulda read the above link lol...

nothing like posting at 2:15 in the morning lol

my apologies

---

### Post by iansane on 2011-06-08
Resurrection again yet 2 years later.

Installed 3.5 from synaptic, frowned when I saw open jdk as part of the installation process but moved on. Installed GWT, WTK, and PDT plugins(all went well), then tried following a beginner tutorial for GWT and found that some things are missing or not called the same in this version. The latest version recommended by google for GWT is 3.6 of course not the version that is available in ubuntu repos.

It's only one version difference but I don't understand the reason behind modifying eclipse for a deb package and scattering the files all over the system when it is, as has been pointed out, already a completely stand alone system. And, it should run off java jdk and jre as it was built to do, not open jdk.

I'm going to dl the latest version along with dling jre and jdk and I'll bet all my problems will be resolved. I am prepared for the taste of "foot in mouth" if they aren't though.

---

