---
title: "No more updates?"
date: 2012-11-16
forum: New to Ubuntu
---

### Post by fractalman on 2012-11-16
I'm using natty 11.04 and as i understand it has reached the end of it's support a few weeks ago so there will be no more updates available,  so i was just wondering...

how safe will natty be from now on?  

will i have any major security issues?

---

### Post by raja.genupula on 2012-11-16
I am going to mainly concern about security updates here . 

so as i know if your Ubuntu version is reached its END age then you are not going to get any security updates . 


PS: we got many good features with new version . is there any specific reason that binds you to be with the 11.04 ?

---

### Post by ibjsb4 on 2012-11-16
Your security issues stopped on Oct 26  :(

[http://www.ubuntu.com/usn/natty/](http://www.ubuntu.com/usn/natty/)

---

### Post by newb85 on 2012-11-16
Well, it's not quite like Windows, where you need to keep updating your virus definitions to keep up with new viruses.

The point of security updates is to address security vulnerabilities in Ubuntu packages.  You already have the fixes for all the vulnerabilities that were discovered and addressed in the first 18 months of Natty.  (Depending on whether you had Recommended, Pre-Release, or Unsupported Updates enabled, more vulnerabilities may have been introduced during those 18 months.)  You won't develop new vulnerabilities after hitting EOL.  However, the bottom line in security isn't having *no* vulnerabilities, but rather minimizing the time between when the vulnerabilities crop up and when they are eliminated.  So, while you won't develop new vulnerabilites, you will become more vulnerable.

Depending on how you use your system, you may run into other compatibility issues.  You don't run your system in a vacuum.  The world keeps moving on to newer formats, and you don't...

---

### Post by Zill on 2012-11-16
> **newb85 said:**
> ...The point of security updates is to address security vulnerabilities in Ubuntu packages.  You already have the fixes for all the vulnerabilities that were discovered and addressed in the first 18 months of Natty.  (Depending on whether you had Recommended, Pre-Release, or Unsupported Updates enabled, more vulnerabilities may have been introduced during those 18 months.)  You won't develop new vulnerabilities after hitting EOL.  However, the bottom line in security isn't having *no* vulnerabilities, but rather minimizing the time between when the vulnerabilities crop up and when they are eliminated.  So, while you won't develop new vulnerabilites, you will become more vulnerable...
+1

newb85 has described the problem very clearly.  :-)  A lot depends on exactly *what* you do with your system.  For example, a "normal" home user will be exposed to far fewer risks than someone running websites and various servers etc.

Assuming you are in the "low risk" home user category then I suggest your system should be quite secure for a while yet so there is no urgency to upgrade.  On this basis, I recommend you have a planned migration from your old to your new system.  Firstly, identify exactly which OS and release you wish to upgrade to.  Then make sure you have all the data you wish to keep securely backed up.  Finally, make a note of any non-standard configurations or applications you have installed that you would need to re-install to the new system.  When all this has been done then just do a clean install of the system of your choice and tweak it as required.

---

### Post by fractalman on 2012-11-17
Well there is no specific reason that binds me to 11.04 per se.  I use my pc as a media centre, for listening to music and watching films, maybe a bit of browsing, skype and some drawing on the gimp, nothing too serious really.

I tried 11.10 a while ago but didn't like it.  I like the gnome 2 desktop environment and found that the gnome3/ gnome fallback desktops had a lot of functions missing.  i also dislike unity a lot.  i like my pc to be a pc, not a pc that someone else thinks should look like a tablet or a mobile phone because that's the trendiest thing on the market.  truth is unity looks awful and i  don't like the way linux forces people to use it if they want the latest  distro

I can appreciate linux needs to compete to stay popular but couldn't you guys leave us pc users alone and develop a separate system for phones and tablets instead of expecting us all to just lump it?

I also found i couldn't tweak 11.10 as much, things like the option to disable the zietgeist passive loggers has been removed,  i'm sure it could still be done if i went into the guts of the system but that's not what i want to be doing.

I also don't want to be upgrading my system every 6 months.  I'm a basic user and it takes me a while to get used to the set up of my o/s,  i could do without having to re learn everything every 6 months because you guys feel the need to keep releasing a new distro like their going out of fashion and keep changing everything within. 

  i would be quite happy if lts was for 5-8 years and a new distro came out every 2 or 3 years,  that way you guys could test everything properly and when it came to release the new distro, it wouldn't be full of bugs and would work properly like it's meant to, instead of every 6 months it's hit and miss wether i get a copy of a distro that isn't going to be full of glitches and take up loads of my time trying to sort out. 

As much as i prefer using linux to windows , it really is a chore for the basic user to keep up with  the release schedule, having to back up my data, wipe my hd, reinstall system, reinstall programmes and then reinstall all my data just to have a usable computer with the trendiest version of linux that isn't going to work properly because it's constantly being rushed and released full of glitches

---

### Post by Cheesemill on 2012-11-17
This is the reason for LTS (Long Term Support) releases. Every 2 years a release is designated as having long term support. For example Ubuntu 12.04 has 5 years of support, meaning it will receive security updates until April 2017. Even if you don't like Unity there has been a lot of improvement in Gnome fallback mode since 11.04 so you may find that it's now suitable for you.

Another option is to switch to a different DE, a lot of people switched to Xubuntu when Unity was released as it has a much more 'classic' style of environment. You can try booting from a Live CD to see if it's something you would be interested in. Xubuntu also has LTS releases, with 12.04 being supported until April 2015.

If you really don't want to use anything except Gnome 2 you could always switch distros altogether. Debian Stable still uses the Gnome 2 desktop and will be supported for at least another couple of years. Being the base on which Ubuntu is built there is no real learning curve switching between the two, they both use the same package management system and the same apt-get commands for installing software.

---

### Post by verymadpip on 2012-11-17
You could try the XFCE desktop environment, Xubuntu desktop, or maybe Xubuntu itself if you like the GNOME2 panel type feel.  It's very customizable.

I've come across one or two minor niggles in 12.10, but 12.04 is LTS which I *think* is only 3 years with Xubuntu this time around.

I'd suggest running Xubuntu from a Live CD or USB to try it out.

Edit: Ah, sorry to duplicate, Cheesemill is way quicker than me.

---

### Post by monkeybrain2012 on 2012-11-17
> **fractalman said:**
>  i also dislike unity a lot.  i like my pc to be a pc, not a pc that someone else thinks should look like a tablet or a mobile phone because that's the trendiest thing on the market.  truth is unity looks awful and i  don't like the way linux forces people to use it if they want the latest  distro



What is a pc supposed to look like? It is just old prejudice to think that a pc must look stuffy and boring like Windows 98, the world is always changing. IMO it is a good thing that Linux desktop breaks the mold with Unity and G3.

Anyway no one is forcing anything on you, there are many DEs you can install and there are Ubuntu flavours that look more traditional (xubuntu, Lubuntu). In the Linux world you always have choices.

I haven't upgraded either, but then I haven't been using my 11.04 partition since its eol (which I could, as others have said, it is not like I am going to be hit by some massive viral attack if I go online, it is not Windows). I am working out of my 12.04 partition at the moment (originally for testing), just too lazy to bother reinstalling yet as I have other things to do. I always do clean install, I don't ubgrade.

---

### Post by Zill on 2012-11-17
> **fractalman said:**
> ...I can appreciate linux needs to compete to stay popular but couldn't you guys leave us pc users alone and develop a separate system for phones and tablets instead of expecting us all to just lump it?..  
Sorry but this is simply not true.  "Linux" is *not* a commercial product and so there is no need whatsoever to "stay popular".  GNU/Linux is Free and Open Source Software (FOSS) produced *by* the community *for* the community and, as you are a user, *you* are as much a part of the community as the rest of *us* guys!  Unpaid volunteer developers work on what they wish to work on and so we cannot *demand* that they change something to suit us.  I just have huge respect for the armies of developers who are willing to donate so much brilliant software to the community.  They have my gratitude.

You seem to be, mistakenly, associating "linux" with Unity. The Unity DE has been created by Ubuntu and so you will not find it in other Linux systems.  If you do not wish to use Unity then there are plenty of other Linux based choices.  From your comments, I guess you would be happier with a more "Gnome 2" type environment.

Although "Gnome 2" is now defunct, a fork called "[Mate]("http://en.wikipedia.org/wiki/MATE_(desktop_environment)")" has very similar functionality and so may meet your requirements.

IMHO, one of the best distros that uses Mate is [Linux Mint]("http://en.wikipedia.org/wiki/Linux_Mint").  Although the "standard" Mint is based on Ubuntu, the Mate (and Cinnamon) Desktops do make this a more "traditional" choice than Unity.  Because Mint is based on Ubuntu, the release cycles are very similar.

However, if you wanted to avoid the regular upgrading required by the Ubuntu base, you could choose [Linux Mint Debian Edition (LMDE)]("http://www.linuxmint.com/download_lmde.php") which is actually a "semi-rolling" release.

This kind of release is quite unique in the Linux world as LMDE is based on Debian Testing but brings a high level of stability by using regular "update packs" to delay upgrades until they have been tested.

You might find this is just what you want. ;-)

---

### Post by newb85 on 2012-11-17
For that matter, you could install Mate or Cinnamon on Ubuntu.  If you use 12.04, you shouldn't need to upgrade until 2017.

---

### Post by I2k4 on 2012-11-17
This hits one of my pet peeves:  the release/support cycle.  As far as I'm concerned the only releases worth installing are LTS versions, unless the user is a developer or an operating system junkie.  Operating systems are not intrinsically interesting to other, ordinary users.  They just aren't all that fascinating.  

As far as I'm concerned, _all of Ubuntu 11.x was BETA_ and should have been labelled as such.  I think the support cycle should be much more prominently explained up front to new users, who might mistakenly install a version that is going to run out of support much sooner than any normal Windows or Apple user would expect.  Nobody cares about Ubuntu's silly mechanical six month releases except developers and junkies, and naive first-timers should have the system clearly explained to them so they can avoid interim projects and install something ready for prime time.

---

### Post by newb85 on 2012-11-17
There are several things that should be explained more clearly up front.  However, Canonical is trying to broaden its base to more casual users.  Out of a somewhat valid concern that lengthy, in-depth, or technical explanations will outlast the attention span of or scare off some such casual users, they basically limit their website to self-advertisement and installation instructions.

---

### Post by offgridguy on 2012-11-17
There is a Sabayon version that has mate desktop as well.

---

