---
title: "IBM JDK in Feisty"
date: 2007-04-23
forum: Programming Talk
---

### Post by joseelsegundo on 2007-04-23
I'm having a problem with the IBM JDK on Feisty in that if i try to run anything in the <IBM JDK>/bin or <IBM JDK>/jre/bin, I get a "Failed to find VM - aborting" error message.

I have some JDKs from Sun (1.5.0_05 and \1.5.0_09), and the executables in those directories run just fine.  Also, the IBM JDK executables ran fine in Edgy.

I've fiddled with the update-alternatives and galternatives to no avail.  But the values for the alternatives shouldn't matter if I'm in <IBM JDK>/bin and I try to run "./java".

I'd kinda like to be able to run the IBM jdks because our target platform uses an IBM jdk.  The server is a pSeries PPC.  Happily we we will soon be migrating to an intel box and then we won't be tied to the IBM JDK.  But in the meantime it would be nice to have my IBM JDKs working.

Cheers -
Rob

---

### Post by phossal on 2007-04-23
How does anyone *get* IBM's JDK?

---

### Post by joseelsegundo on 2007-04-24
It is pretty simple to get the IBM JDKs.  They are available at [http://www.ibm.com/developerworks](http://www.ibm.com/developerworks).

I am in the process of backing up my home directory so that I can try to do a clean install of Feisty.  I've found a few more things that got broken so it's likely that I did a distro upgrade too soon after the release date of Fiesty, before most of the bugs in the upgrade were fixed.

---

### Post by joseelsegundo on 2007-04-24
Nope.  No love from a fresh install of Feisty.  

harumph.

---

### Post by phossal on 2007-04-24
IBM makes it a microsoft-like pain to download their SDK. I don't *want* a membership to their site. I just want to use their trash. Plus, their site sucks. It's not exactly easy to find. No wonder it doesn't work. Their roll-out team can't even get the delivery right. Pathetic.

---

### Post by joseelsegundo on 2007-04-25
No need to beat around the bush with this, **phossal**.  How do you really feel? :P

Well I've since found out, this error stems from a bug in glibc2.5 on amd64 platforms.  The relevant info is found here: [http://www.cygwin.com/bugzilla/show_bug.cgi?id=4131](http://www.cygwin.com/bugzilla/show_bug.cgi?id=4131)

Yeah, the developerworks site can be a bit frustrating.  However my travels have been among companies that use IBM hardware so it's an occupational hazard.  At least our servers are running Linux (SuSE), though!

---

