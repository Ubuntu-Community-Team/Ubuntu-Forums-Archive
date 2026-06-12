---
title: "Complete Ubuntu disc(s) with Common applications!"
date: 2008-05-04
forum: New to Ubuntu
---

### Post by geoffic on 2008-05-04
Is it possible to obtain, either by download or purchase, Ubuntu together with ready installed applications?

I mean like for example OPEN OFFICE and Firefox which are bundled.

I have difficulty with the many commands, some work, others not. Some require "Alien" some seem to be "rpm"

Sometimes I get a message about recoding or Codecs.  - with Totem.

As someone typically who moved from Windows, I expect AVI or MP3 
or commonly used things like YouTube to open more or or less automatically.

Also I am lacking a Glossary of Names and  Commands.

I bought 2 books - one with a disk ( Ubuntu Linux for non -Geeks)

and "Ubuntu Hacks".

Sometime the instructions function. Sometimes it says  "... no Public Key so cannot get Multiverse something something!

Are the main programs or packets available on disc?  eg Multiverse

Thanks ..

Geoffic

---

### Post by imT on 2008-05-04
ubuntu comes with all the basic applications that you may need, just try the live cd, and if they are not in the live cd there are a bunch of linux app in the repositories(you'll have to download them).

---

### Post by Paqman on 2008-05-04
If you want a disk with more software than you get on the LiveCD, then you can get a DVD instead.

[Hardy DVD downloads](http://cdimage.ubuntu.com/dvd/current/)

> **geoffic said:**
> 
As someone typically who moved from Windows, I expect AVI or MP3 
or commonly used things like YouTube to open more or or less automatically.

Install the package [ubuntu-restricted-extras](apt:ubuntu-restricted-extras), that will install all sorts of codecs, Flash, Java, etc. The reason they aren't included with the default install is that the companies that own them restrict their availability. You're allowed to install them as an end-user, but the company behind Ubuntu isn't allowed to distribute them for free. A couple of extra mouse clicks is the price you pay for getting Ubuntu for free.

---

### Post by ugm6hr on 2008-05-04
> **geoffic said:**
> I mean like for example OPEN OFFICE and Firefox which are bundled.

I have difficulty with the many commands, some work, others not. Some require "Alien" some seem to be "rpm"

Sometimes I get a message about recoding or Codecs.  - with Totem.

As someone typically who moved from Windows, I expect AVI or MP3 
or commonly used things like YouTube to open more or or less automatically.

Also I am lacking a Glossary of Names and  Commands.

I bought 2 books - one with a disk ( Ubuntu Linux for non -Geeks)

and "Ubuntu Hacks".

As stated, Ubuntu CD comes with Firefox and OpenOffice.  I presume you are using the CD that came with the book?  If so, it is probably out-of-date now, but I think Ubuntu has always had OO and Firefox installed.

You do not need Alien or rpms for the vast majority of software.  Software is available to download directly from "repositories" - just search in Synaptic Package Manager (or look in Add/Remove...)

As for avi or mp3 - you need to download "codecs" to make these play.  This is a good reference for getting everything to work: [http://ubuntuforums.org/showthread.php?t=661833](http://ubuntuforums.org/showthread.php?t=661833)  If this is too complicated, an alternative Linux called LinuxMint may be better suited for you, which comes with a lot of codecs pre-installed.

For all Linux Terminal commands - I find this useful: [http://www.oreillynet.com/linux/cmd/](http://www.oreillynet.com/linux/cmd/)

As a starter, I would recommend you read this: [http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

---

### Post by geoffic on 2008-05-05
Many thanks for very informative and practical advice.
I have meanwhile downloaded the DVD.

Geoffic

---

### Post by SunnyRabbiera on 2008-05-05
Yeh ubuntu comes with a LOT pre installed, firefox, open office, a IM program (pidgin) and all sorts of stuff to get you started :D

---

### Post by geoffic on 2008-05-07
Thanks very much 
The DVD with Hardy Heron worked much better than all previous.

So did the Codec repository.

I have seen references to something called "Multiverse" . Do I require this. And how to get it without to much trouble?

And now I need to setup Network with my Windows XP  (SP2) on a WiFi connected PC in different location.

With the Ubuntu I am cable ethernet connected to the Router.

How do I setup the Network and the sharing from the Ubuntu to the XP?

Grateful thanks to all of you

Geoff

---

### Post by kesman on 2008-05-07
Multiverse is a software repository, and you can check if it's enabled under these menu items: system -> administration -> software sources.

For file sharing, share the desired folder in your XP-pc, make it use a workgroup named WORKGROUP and then browse the places -> network menu from ubuntu. You should now be able to connect to the shared folder. It may promt for downloading SAMBA-packages, they are required for windows -> linux networking to work.

---

### Post by geoffic on 2008-05-07
> **kesman said:**
> Multiverse is a software repository, and you can check if it's enabled under these menu items: system -> administration -> software sources.

For file sharing, share the desired folder in your XP-pc, make it use a workgroup named WORKGROUP and then browse the places -> network menu from ubuntu. You should now be able to connect to the shared folder. It may promt for downloading SAMBA-packages, they are required for windows -> linux networking to work.
Sorry about this but where do I mark "Solved" ?

---

### Post by kesman on 2008-05-07
If it doesn't appear in the "thread tools" drop-down menu right at the top of the thread, then it's not yet implemented in this new version of the forums.

---

