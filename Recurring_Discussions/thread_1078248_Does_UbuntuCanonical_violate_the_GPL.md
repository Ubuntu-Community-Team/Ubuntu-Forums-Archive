---
title: "Does Ubuntu/Canonical violate the GPL?"
date: 2009-02-23
forum: Recurring Discussions
---

### Post by Hoddo Frökyard on 2009-02-23
I am from the "Ubuntu Privacy Remix"-Team. The goal of
Ubuntu Privacy Remix ([https://www.privacy-cd.org](https://www.privacy-cd.org)) is to provide an isolated, working environment where private data can be dealt with safely. It is a tool to protect your data against unsolicited access.

Now my question: The GPL says, that a provider of GPL-software has to offer the sources of his software for three years. Debian e.g. fulfilles this by providing the source-cd's. Ubuntu does not provide source-cd's.
We want to make sure that our project complies with the GPL. We do have
the sources for all modifications made to the original live CD, but we
do not yet have the sources of the original live CD.

At ubuntu.org/DerivativeTeam/ I read: "For derivatives, enforcement of
that compliance is up to them, we are
happy for them to point at our archives of source packages if they don't
want to re-host the same source for packages which they have not
modified." My questions are:
1. Where exactly can these Archives be found? And do they also include Live-cd-only-packages like casper?
2. The FSF writes "Each derivative makes an agreement with Ubuntu like
you described. This agreement should probably explain how long Ubuntu
promises to host the source, and what derivatives should do when that
time passes. A blanket agreement -- i.e., something that Ubuntu posts on
its web site, valid for all derivatives -- is acceptable." Does such a
blanket agreement exist and where is it posted?

I am trying to get an answer to this simple question since november last
year, but nobody at Canonical even replies - Is the great community-support by Canonical a myth? Maybe one of you can help us.

---

### Post by mb_webguy on 2009-02-23
In the terminal, type "cat /etc/apt/sources.list" to see your software sources.  If you'll notice, for every line that begins with "deb", there is another nearly identical line that begins with "deb-src".  There's the location of your source files.  Every mirror of the Ubuntu repositories also mirrors the source code of all open-source software in those repositories.

In fact, if you want to download and install source code, it's as easy as checking the "Source Code" check box on the Ubuntu Software tab of Software Sources.  Thereafter, you'll be able to see source code packages for all of the software in Synaptic.

If your project uses the Ubuntu repositories, then the user already has access to all of the source code for Ubuntu, and the only source code your project would have to be concerned about providing would be that which you altered.

---

### Post by Hoddo Frökyard on 2009-02-23
Thank you for your fast reply.

> **mb_webguy said:**
> 
If your project uses the Ubuntu repositories, then the user already has access to all of the source code for Ubuntu, and the only source code your project would have to be concerned about providing would be that which you altered.

I knew how to install source-packages, but I did not understand the structure of the archive.ubuntu.com-server. Now I see, that the source code of different versions/different Ubuntu-releases can be found under /pool/main/<packagename>. So far, so good. 

But the second question is unanswered: Everybody, who (re)distributes GPL-Software must keep the following conditions of the GPL(v2):

" 3. You may copy and distribute the Program (or a work based on it,
under Section 2) in object code or executable form under the terms of
Sections 1 and 2 above provided that you also do one of the following:
(...)
 b) Accompany it with a written offer, valid for at least three
    years, to give any third party, for a charge no more than your
    cost of physically performing source distribution, a complete
    machine-readable copy of the corresponding source code, (...)"

> **Hoddo Frökyard said:**
> 
At ubuntu.org/DerivativeTeam/ I read: "For derivatives, enforcement of
that compliance is up to them, we are
happy for them to point at our archives of source packages if they don't
want to re-host the same source for packages which they have not
modified." 
2. The FSF writes "Each derivative makes an agreement with Ubuntu like
you described. This agreement should probably explain how long Ubuntu
promises to host the source, and what derivatives should do when that
time passes. A blanket agreement -- i.e., something that Ubuntu posts on
its web site, valid for all derivatives -- is acceptable." Does such a
blanket agreement exist and where is it posted?


If I get that comment by the FSF right, it is not sufficient if a derivate-project just refers to archive.ubuntu.com. An official agreement is necessary. My question still is: Does such a
blanket agreement exist and where is it posted?

---

### Post by Hoddo Frökyard on 2009-02-23
Maybe members of other devivate-teams could tell us, how the solve this?

---

### Post by alum on 2009-02-25
I would be interested in this too. Can anybody tell, if this

> **Hoddo Frökyard said:**
> 
"For derivatives, enforcement of
that compliance is up to them, we are
happy for them to point at our archives of source packages if they don't
want to re-host the same source for packages which they have not
modified."

is sufficient to comply with the GPL, if a derivate points to the official ubuntu-archives?

---

### Post by handy on 2009-02-25
They are a very smart bunch of dude's that are running Canonical, & one of the things that they are really switched on about is the LAW.

There is no way that Canonical is going to make itself vulnerable to any kind of sewing.

They have the money to buy the legal brains to make sure that they don't embarrass themselves that way.

---

### Post by bodhi.zazen on 2009-02-25
I am going to close this thread now as this is not really the proper forum for your questions and your claims are frankly outlandish, so much so it seems like trolling (either that or you just do not know what your are talking about) and as such I am going to move your thread to recurring discussions. The accusation that Ubuntu does not contribute to Debian is both false and a topic of great trolling.

I can not understand your question exactly, but Ubuntu provides source code in the source or "deb-src" directories. As much as Debian developers hate to admit it Ubuntu has contributed and continues to contribute to Debian. In addition entire distros are based on the Ubuntu code (Can yiou say Linspire, Linux Mint, Mepis ? )

There is an entire thread on where and how to obtain the source code here :

[http://ubuntuforums.org/showthread.php?t=14756](http://ubuntuforums.org/showthread.php?t=14756)

Furthermore this page explains how the Ubunt udevelopers contribute to the open source community :

[https://wiki.ubuntu.com/Website/Content/UbuntuContributions](https://wiki.ubuntu.com/Website/Content/UbuntuContributions)

There is nothing in the GPL that states that the source code must be provided on a CD or DVD nor is there a requirement that the source code be provided "free of charge".

Contact information can be found here :

[http://www.ubuntu.com/aboutus/contactus](http://www.ubuntu.com/aboutus/contactus)

---

