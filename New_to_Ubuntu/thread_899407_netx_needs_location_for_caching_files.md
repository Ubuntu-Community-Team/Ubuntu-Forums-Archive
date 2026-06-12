---
title: "netx needs location for caching files"
date: 2008-08-24
forum: New to Ubuntu
---

### Post by saratchandra on 2008-08-24
I'm getting this message quite often. Is this a security risk? I don't remember installing any software like that. I'm adding a screenshot below.

[ATTACH]82641[/ATTACH]

---

### Post by huntwell on 2008-08-24
I am having the exact same thing happen to me. This just started happening lately. I have had Hardy installed for a few months now and have not seen this before.

Hopefully someone out there can provide some insight into this problem. Sorry I am not writing this post as a solution.

---

### Post by momist on 2008-08-29
Me too.  Reading at [http://jnlp.sourceforge.net/netx/](http://jnlp.sourceforge.net/netx/) I get the impression that this is safe, but where should we create the cache directory?  The default /tmp seems a good idea, but is this optimal?  How come this is just popping up now, and has had no introduction to us users?

Oh well, I'll give it a go and see what happens.

---

### Post by headshrinker on 2008-09-06
I'm getting exactly the same thing. What I have just noticed is that I get it whenever I browse onto a website that has some sort of java applet - I went to this website with some java games on it:

[http://www.popcap.com/online_games.php](http://www.popcap.com/online_games.php)

I imagine if you click on any one of the games (I tried Ning Po Mahjong), after the 15 secs advert has gone and the game tries to launch, the Netx window appears.

Surely, this should not be happening - this sort of random thing popping up out of nowhere should set anyones alarm bells ringing. I downloaded ClamAV and ClamTk from Synaptic and am currently doing a full virus scan of the filesystem. I've never really used this before - it's probably overkill, but I thought I'd try it out. (Currently at 15% the way through and claims to have found 9 viruses!)

I also looked at my update history and a couple of weeks ago some openjdk packages were updated, which were the only java related things I noticed.

I'm going to try uninstalling or rolling back a version and will report back

---

### Post by headshrinker on 2008-09-06
Ok, an update.

Firstly, I think the ClamAv thing is a red herring - the viruses that it says it is detecting are things like:

> fl8_tutorials.pdf    Files number limit exceeded

which having a quick look around on google looked like it was nothing.

So, in my update history, on 16th Aug I updated the following packages:

openjdk-6-jre
openjdk-6-jre-headless
openjdk-6-jre-lib

when I went to uninstall these, it also uninstalled:

icedtea-gcjwebplugin

because it was a dependency. After uninstalling, I went to the same Ning Po Mahjong game and I didn't get the Netx window popping up. (I also didn't get the game, so it looks like java applets don't work now!)

Reinstalling the 3 openjdk packages had the same effect (no java applets). 

Then, after reinstalling the icedtea package, the Netx popup came back, so it looks like this is the culprit. I'm going to look into this further - I am starting to think it is a genuine thing but can't be sure. If it is, then the guys that wrote this need to sort their act out - I don't really find this sort of thing acceptable. The package description says:

> 
Java plugin based on IcedTea and gcjwebplugin
icedtea-gcjwebplugin is a little web browser plugin to execute Java applets.
It is targeted for Mozilla and compatible browsers that support the NPAPI.


I'll maybe look for an alternative java plugin for firefox.

---

### Post by huntwell on 2008-09-07
headshrinker,

Thanks for checking this out, I also had alarm bells when I saw it and also ran Clam, but nothing came up on my system. I agree that it appears to be some kind of Java applet, but I don't plan on doing anything with it until I get some solid info on what it is and why it is happening.

---

### Post by fain on 2008-09-14
I too am paranoid about this. I was on fackbook trying to upload some photos and this box popped up. Never seen it before, and I am pretty sure I uploaded photos on hardy before. Must be a new java script in facebook? Either way im not running it till its deemed safe.

---

### Post by headshrinker on 2008-10-27
Added a question onto launchpad about this:

[https://answers.launchpad.net/ubuntu/+question/46133](https://answers.launchpad.net/ubuntu/+question/46133)

but got no response after 1 month.

However, I have uninstalled the icedtea-gcjwebplugin package (the 3 openjdk packages are still installed) and installed the following:

sun-java6-bin
sun-java6-jre
sun-java6-plugin

java applets now seem to work happily in firefox

---

### Post by simplysimple on 2008-11-20
This happened to me twice today...I had the same reaction... something doesn't look right to me. Nonetheless, I was relieved that it wans't anything malicious. 

One strange addition I can add....the moment the Netx dialog box appears, anything I type into in the browser it flips it backwards....for example...I'll type google.com and when I finish typing it flips to 
moc.elgoog...even stranger...if I type it backwards then it flips to read the proper way. I enter moc.elgoog and it flips it to google.com. This makes surfing the web a very tricky task. 

For what it's worth I'm running 8.10 64 bit...I do have a 32bit version of java installed to run Eclipse PDT w/xdebug but have not had this issue until today. 

I'm going to give the suggestion above a go and see what happens. :confused:

---

### Post by Xpictoc on 2008-11-22
I noticed the same backwards phenomenon when i tried to search for netx when its dialog box was up.

---

### Post by pandammonium on 2009-02-04
> **headshrinker said:**
> ...
However, I have uninstalled the icedtea-gcjwebplugin package (the 3 openjdk packages are still installed) and installed the following:

sun-java6-bin
sun-java6-jre
sun-java6-plugin

java applets now seem to work happily in firefox

Thanks for posting this, headshrinker.  I had [FONT="Courier New"]cacao-oj6-<xxx>[/FONT] installed, which is some odd version of icedtea, and still produces the dodgy-looking pop-up.  I uninstalled everything to do with that using Synaptic Package Manager.  I don't think I ever had the openjdk packages installed.

I have now installed the three packages you list using [FONT="Courier New"]sudo apt-get install sun-java6-<xxx>[/FONT].  The first two were already installed, but the third one wasn't.  I can confirm that Java applets work a treat now, with no dubious pop-ups appearing to worry the poor user!

---

