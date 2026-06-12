---
title: "What's up with Getdeb?"
date: 2007-12-21
forum: Recurring Discussions
---

### Post by JurB on 2007-12-21
20 days without new packages.
Does anyone know what's going on?:confused:

---

### Post by bruce89 on 2007-12-21
Christmas.

Or perhaps they realised the questionable quality of their packages.

---

### Post by Vadi on 2007-12-21
Yeah, holidays.

bruce89: got a better solution?

---

### Post by TBOL3 on 2007-12-21
> **Vadi said:**
> bruce89: got a better solution?

Umm, they all died of sudden and unexpected hart attacks.

---

### Post by undine on 2007-12-21
> **Vadi said:**
> Yeah, holidays.

bruce89: got a better solution?

CNR.

Haha, I made a funny.

---

### Post by Vadi on 2007-12-21
Yeah, there's a good one! Too bad most of the downloads are in repositories already.

---

### Post by bruce89 on 2007-12-21
*cough*My PPA*cough*

---

### Post by FuturePilot on 2007-12-21
> **bruce89 said:**
> *cough*My PPA*cough*

Ooh! You have Gimp 2.4.2 :D

---

### Post by smartboyathome on 2007-12-21
Awesome! I was thinking of doing a local repo from my comp for GIMP 2.4.2, but I will use your PPA instead (right after I am done with my mockup, that is :P).

---

### Post by macogw on 2007-12-21
> **bruce89 said:**
> Christmas.

Or perhaps they realised the questionable quality of their packages.

Like the Pidgin 2.1 that with certain plugins enabled would eat 700MB of RAM?

---

### Post by S3Indiana on 2007-12-21
> **undine said:**
> CNR.[CNR.com]("http://www.cnr.com/index.seam") has updated packages available (including [Adobe Reader]("http://www.cnr.com/product/productOverview.seam?productId=18106") 8.0 for Linux)...

---

### Post by Vadi on 2007-12-21
Dunno, I only have 512 ram, and Pidgin never ate more than 20mb (that was when I had 6 conversations open for several days, so they were quite long).

---

### Post by JurB on 2007-12-21
> **bruce89 said:**
> *cough*My PPA*cough*
Didn't know about PPA's, but it sure seems like a interesting concept.
This is a relatively new thing, right?

---

### Post by Mateo on 2008-01-01
it appears to be totally dead to me.

---

### Post by Vadi on 2008-01-01
It's only 1st of jan. I'll give them a week or so.

However, if you look on their launchpad.net page, quite a bit of packages were prepared during this period.

---

### Post by MaX on 2008-01-01
Well getdeb seems dead.

I tried to get an account like a month ago but the supposedly automatic mail never arrived so I could confirm my account.

No one answered my question about it either...
To bad, it was a nice way of getting new stuff since backports doesn't seem to work in anyway at all as good as it used to.

---

### Post by Matt Yun on 2008-01-02
Looks like getdeb.net is back up: new packages posted as of Jan 1 and 2, 2008.

---

### Post by picpak on 2008-01-02
I think this comment says it all:

> When i try to install it with gdebi it says that the dependecy is not satisfiable: libawn0

The last time I checked, their package of avant-window-navigator had hardly any applets. Getdeb is a great service, but the quality of their packages leaves something to be desired.

---

### Post by Vadi on 2008-01-02
Better than nothing, or worse yet, letting your system wide-open to security holes (see, cnr.com).

---

### Post by S3Indiana on 2008-01-02
> **Vadi said:**
> Better than nothing, or worse yet, letting your system wide-open to security holes (see, cnr.com).Huh... There are packages available at [CNR.com]("http://www.cnr.com") not available in the native OS repositories, but it's a mirror of the default repositories (are you implying the default repositories are suspect???)...

---

### Post by Vadi on 2008-01-02
No, I'm implying that the software I have to install in order to get stuff from cnr has security problems.

(Why couldn't they just use .packages, but instead had to come up with yet another format?)

---

### Post by angryfirelord on 2008-01-02
Simple, compile from source. Yes, it's a scary though, but trust me, it's not that bad.

---

### Post by S3Indiana on 2008-01-02
> **Vadi said:**
> No, I'm implying that the software I have to install in order to get stuff from cnr has security problems.

(Why couldn't they just use .packages, but instead had to come up with yet another format?)The CNR Client uses a standard .deb package (post install found /var/cache/cnr/client/pool); a very small .cnr file is used to invoke the install (IOW set the proper mime type), all else is a standard Debian install...

---

### Post by Vadi on 2008-01-02
Uh huh, that small .cnr one is the one to blame for security, I believe.

Why can't I have access to the .debs directly? I'm already familiar with how to install those, gdebi get those done for me easily. In fact every project that provides a .deb I can use gdebi with.

---

### Post by S3Indiana on 2008-01-03
> **Vadi said:**
> Uh huh, that small .cnr one is the one to blame for security, I believe.

Why can't I have access to the .debs directly? I'm already familiar with how to install those, gdebi get those done for me easily. In fact every project that provides a .deb I can use gdebi with.You can if you want, but then you're kinda not using [CNR.com]("http://www.cnr.com") :):
```
# Additional Sources
deb     http://apt2.freespire.org/CNRUbuntuExtra gutsy-extra main restricted
deb-src http://apt2.freespire.org/CNRUbuntuExtra gutsy-extra main restricted
# Uncomment the following two lines to add software from the 'backports' repository.
deb     http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

```BTW the .cnr file does nothing unless you've given access to use the associated mime type (IOW a non-privileged user account can't use CNR); isn't that the security design in a Linux enviroment??

---

### Post by Vadi on 2008-01-03
Yeah I'm not. I just want the programs, whatever else Linspire,Inc. has in store for me.

getdeb.net is working after the holidays again btw.

---

### Post by S3Indiana on 2008-01-04
> **Vadi said:**
> Yeah I'm not. **I just want** the programs, whatever else Linspire,Inc. has in store for me.What do you think will happen (installing a non-existent Linux virus)??? Thought contributing was the base of this community...

---

### Post by Vadi on 2008-01-04
What do you mean, non-existent. Anyone can write a "virus". Even I can.

I dount that Linspire, Inc. is contributing to the community. They're a private company who seeks to make profit, using Ubuntu (after their own OS failed? They were founded in 2001, and Ubuntu wasn't around back then), a product of another company (but a much more open one), Canonical.

To look at the history of Linspire and security, you can just do a quick google search of "linspire security". If it's good, it'll be praised, if it's bad, it won't be. So lets see what I get:

The first result I get ([http://lwn.net/Articles/128869/](http://lwn.net/Articles/128869/)) confirms why Linspire is made CnR for - making more money. Then again, Linspire's founder is the same of mp3.com's, so his goals aren't really concealed.

> As far as Linspire's view of computer security is concerned, not much has changed since earlier releases, and the default state is still "run as passwordless root". That said, a superuser password can be optionally entered during installation and new user accounts can be created from a configuration screen, right after the first boot. I had a lengthy email exchange about these issues with Linspire's president Kevin Carmony. He insisted that enforcement of passwords and user accounts is an annoying and inconvenient "hoop", similar to enforcing strict airport security or placing 12 extra locks on one's house. More interestingly, he also disclosed that Linspire was sponsoring work "at the file system level that will make the OS more secure than it has ever been before, and all without expecting grandma to jump through complicated hoops."

So as you see, security was terrible there. There's a reason why Windows now implemented UAC in Vista, and Linspire back then was like windows XP in regards to security.

The second result ([click]("http://www.usatoday.com/money/industries/technology/2004-11-29-honeypot_x.htm"))  is just about firewalls. Gladly, Linspire's firewall was on, so just like the Windows machines, it wasn't affected.

Third result is from linspire.com. Skipping that. Fourth is another announcement, skip that too. Fourth is titled "Microsoft inks Linux patent deal with Linspire". 

Actually the rest are just linspire annuncements, or annoucements about it. One is from linuxforums.com which wasn't too convincing either.

So, no, I'm afraid that my doubts in Linspire, Inc.'s view on security aren't settled. And since I read that cnr's installer abuses some method that it shouldn't to be root, so... I'll pass, thanks.

---

### Post by S3Indiana on 2008-01-04
> **Vadi said:**
> What do you mean, non-existent. Anyone can write a "virus". Even I can.Request a link to a Linux virus that spread in the wild (not that one has never been created, just not spread)...
> **Vadi said:**
> I dount that Linspire, Inc. is contributing to the community. They're a private company who seeks to make **profit**, using Ubuntu (after their own OS failed? They were founded in 2001, and Ubuntu wasn't around back then), a product of another company (but a much more open one), **Canonical**.Pls. review the history you've given and you'll see contributions provided by Linspire (both code and cash), but what does that have to do with the original question???
> **Vadi said:**
> To look at the history of Linspire and security, you can just do a quick google search of "linspire security". If it's good, it'll be praised, if it's bad, it won't be. So lets see what I get:

The first result I get ([http://lwn.net/Articles/128869/](http://lwn.net/Articles/128869/)) confirms why Linspire is made CnR for - making more money.

So as you see, security was terrible there. There's a reason why Windows now implemented UAC in Vista, and Linspire back then was like windows XP in regards to security.Yes in the beginning Linspire's default account ran as root (won't go into the lack of documented cases of any illicit activity due to a single Linux user account, not on a network, running as root), but as you've stated that's history (Freespire - the community version - has never run under root as default).   And any responsible admin would create a non-privileged user account providing the full security designed into Linux... 
> **Vadi said:**
> The second result ([click]("http://www.usatoday.com/money/industries/technology/2004-11-29-honeypot_x.htm"))  is just about firewalls. Gladly, Linspire's firewall was on, so just like the Windows machines, it wasn't affected.The firewall preinstalled with Linspire and Freespire has been activated by default since the initial general release (not so for all OS's released during that time), and why do you think Linspire was chosen as the standard Linux distribution for the test???
> **Vadi said:**
>  So, no, I'm afraid that my doubts in Linspire, Inc.'s view on security aren't settled. And since I read that cnr's installer abuses some method that it shouldn't to be root, so... I'll pass, thanks.Again access to installing applications in an admin level function, so any system should have non-privileged user accounts for daily use (wouldn't that be the prudent thing to do). You appear to be quick to spread the bad news...

---

### Post by Vadi on 2008-01-04
Nono, you didn't mention spread. You said non-existent. And ones do exist. Spread and existence are different things.

And somehow, I can install applications just fine, so that does not justify the "workaround".

---

### Post by Kernel Sanders on 2008-01-04
What's wrong with CNR??? :confused:

---

### Post by Vadi on 2008-01-04
Just suspicions for now. Although there hasn't yet been an overview of the service that I know of, several knowledgable people looked at their code and did find flaws. The way their installer works is well by abusing something it shouldn't be too.

---

### Post by S3Indiana on 2008-01-04
> **Vadi said:**
> Just suspicions for now. Although there hasn't yet been an overview of the service that I know of, several knowledgable people looked at their code and did find flaws. The way their installer works is well by abusing something it shouldn't be too.That's [inaccurate]("http://community.cnr.com/message/1153#1153")...

---

### Post by Vadi on 2008-01-04
... wait, CnR does not ask for password at all?

That's just greeeat. I can leave my laptop by accident, someone can come along, install some sh*t without a password. Whereas they would never be able to via apt.

Yeah, no. It's like removing root passwords entirely.

---

### Post by Mateo on 2008-01-04
> **angryfirelord said:**
> Simple, compile from source. Yes, it's a scary though, but trust me, it's not that bad.

well, unless you decide you don't like the software, and then you have to try and track down the 10 dependencies you had to install, to uninstall all of them.  Actually, it is pretty bad.  It's a nightmare, as a matter of fact.

---

### Post by macogw on 2008-01-05
> **Vadi said:**
> Dunno, I only have 512 ram, and Pidgin never ate more than 20mb (that was when I had 6 conversations open for several days, so they were quite long).

Oh it wasn't a matter of time or number of conversations.  It would happen *immediately* as soon as Pidgin started.  700MB would go missing when Pidgin started without me starting any convos or anything.  Less than 5 seconds of runtime, and it made it so I could barely get top open to see what was wrong and kill it.  I don't know exactly why it happened, but all I can figure is that some combination of the plugins I had enabled with their deb did it.  When I recompiled Pidgin 2.1 and kept the same plugins enabled, it was fine.

---

### Post by S3Indiana on 2008-01-05
> **Vadi said:**
> ... wait, CnR does not ask for password at all?

That's just greeeat. I can leave my laptop by accident, someone can come along, install some sh*t without a password. Whereas they would never be able to via apt.

Yeah, no. It's like removing root passwords entirely.For clarification only packages that are in the CNR repositories can be installed via the CNR Client (IOW you can't just point to any repository and install errant packages - running as an non-privileged user should be the standard if there's concern and CNR will not be available for that account). Also anyone that leaves their machine available in an unprotected area (especially without locking the machine) is exposing their data (truly the critical element on any device) to harmful activity...

---

### Post by wana10 on 2008-01-05
> **Mateo said:**
> well, unless you decide you don't like the software, and then you have to try and track down the 10 dependencies you had to install, to uninstall all of them.  Actually, it is pretty bad.  It's a nightmare, as a matter of fact.

at the end instead of 'sudo make install' run 'sudo checkinstall' this creates a .deb file of the program for easy removal. ;)

---

### Post by picpak on 2008-01-05
> **wana10 said:**
> at the end instead of 'sudo make install' run 'sudo checkinstall' this creates a .deb file of the program for easy removal. ;)

That doesn't help for all the *-dev packages you have to install...

---

### Post by Vadi on 2008-01-05
> **S3Indiana said:**
> For clarification only packages that are in the CNR repositories can be installed via the CNR Client (IOW you can't just point to any repository and install errant packages - running as an non-privileged user should be the standard if there's concern and CNR will not be available for that account). Also anyone that leaves their machine available in an unprotected area (especially without locking the machine) is exposing their data (truly the critical element on any device) to harmful activity...

Yes, and with CnR, that includes installing/uninstalling programs at will :KS.

(so, no, I see this "feature", one that violates the standards also, as a security flaw)

Getdeb is up anyway, so I'm off :popcorn:.

---

### Post by macogw on 2008-01-05
> **picpak said:**
> That doesn't help for all the *-dev packages you have to install...

Well, I don't know about uninstalling, but to install all of the -dev packages you need, if you're just compiling a new version of something already in the repos or recompiling something that's in there, you can do "sudo apt-get build-dep <package>" so if you wanted to compile an updated GSynaptics because it has more features than the one in the repos, you'd do "sudo apt-get build-dep gsynaptics"

---

### Post by S3Indiana on 2008-01-05
> **Vadi said:**
> Yes, and with CnR, that includes installing/uninstalling programs at will.

(so, no, I see this "feature", one that violates the standards also, as a security flaw)What standards (link pls.)???

---

### Post by xArv3nx on 2008-01-05
It makes me sick how divided this community is.

---

### Post by Sef on 2008-01-05
moved to reoccurring discussions.

---

