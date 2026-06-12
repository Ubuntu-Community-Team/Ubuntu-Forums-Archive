---
title: "OOo vs Go-oo"
date: 2010-01-03
forum: Recurring Discussions
---

### Post by Jestersage on 2010-01-03
Obviously, this is more of a Win/Mac issue, but for everyone around here, would you go with Go-oo or OOo?

---

### Post by mkendall on 2010-01-03
I use Go-OO by default because OOo doesn't like to play with Xubuntu for me.

---

### Post by jollysnowman on 2010-01-03
Go-oo... I'm not a fan of Java...

---

### Post by andrewabc on 2010-01-03
go-oo because it is default in ubuntu. But it has a lot of bugs that are not present in windows version.

---

### Post by Dayofswords on 2010-01-03
i thought OOo was defualt in ubuntu

---

### Post by mamamia88 on 2010-01-03
what exactly is the difference?

---

### Post by LeifAndersen on 2010-01-03
Go-oo is the open source rip off of the open source Open Office, wait, I don't think that came out right. :lolflag:

Anyway, there are a few changes in Go-oo, not much though, with enough time, you could turn a Go-oo installation into an OOo one, and vice versa.

---

### Post by Xbehave on 2010-01-03
> **mamamia88 said:**
> what exactly is the difference?
I had to look it too, my best understanding is
[QUOTE=wikipedia]For a long time various Linux distributions, including SUSE  Debian and Ubuntu, have cooperated in maintaining a large set of patches to the upstream OpenOffice.org that for various technical or semi-political reasons have not been accepted or not even submitted upstream. Some of the companies behind those distributions have also offered Windows builds of OpenOffice.org for example, OxygenOffice Professional and OpenOffice.org Novell Edition. Go-oo is just a more concentrated branding effort for these patches and patched builds of OpenOffice.org. Whether this can be called a fork is open to debate.[/QUOTE]
From that summary it's clear that go-oo is the better choice as it's OO + patches from novell+ibm+co

---

### Post by starcannon on 2010-01-03
Open Office gets the job done for me; I tried one of the OOo derivatives a few months back, I don't miss it.

---

### Post by mkendall on 2010-01-03
> **Xbehave said:**
> I had to look it too, my best understanding is *{stuff}*

From that summary it's clear that go-oo is the better choice as it's OO + patches from novell+ibm+co

Not quite. Go-OO tends to be an update version or two behind. Open Office from the Ubuntu repositories is v3.0.1 while it's up to v3.1.1 with a 3.2 candidate available from the openoffice.org website.

---

### Post by FuturePilot on 2010-01-03
> **mkendall said:**
> Not quite. Go-OO tends to be an update version or two behind. Open Office from the Ubuntu repositories is v3.0.1 while it's up to v3.1.1 with a 3.2 candidate available from the openoffice.org website.

That has nothing to do with Go-OO. That's how the Ubuntu release cycle works. The repos get frozen at release time.
The latest version at [http://go-oo.org/download/]("http://go-oo.org/download/") is also 3.1.1

---

### Post by slooksterpsv on 2010-01-03
On Windows, Go-oo runs a lot faster, I like it a lot. In Ubuntu, I use OpenOffice, runs as fast as Go-oo in Windows so yeah.

---

### Post by phrostbyte on 2010-01-04
> **slooksterpsv said:**
> On Windows, Go-oo runs a lot faster, I like it a lot. In Ubuntu, I use OpenOffice, runs as fast as Go-oo in Windows so yeah.

Ubuntu uses Go-oo. :)

---

### Post by slooksterpsv on 2010-01-04
Ok, that makes sense, I was thinking Ubuntu used regular OpenOffice, but it doesn't use Java cause it doesn't require java to run, so yeah makes sense, I was thinking when they said Ubuntu uses Go-oo I was thinking how it's OpenOffice and says OpenOffice - yeah my confusion, sorry. --  At least I'm not getting flamed... yet lol

---

### Post by m0o on 2010-01-04
I've tested Go-OO and it does give a noticeable performance in the Windows environment. In Ubuntu I believe it's shipped with it.

---

### Post by Xbehave on 2010-01-05
> **slooksterpsv said:**
> Ok, that makes sense, I was thinking Ubuntu used regular OpenOffice,
ubuntu uses OO+patches, which is effectively the same as go-oo
> but it doesn't use Java cause it doesn't require java to run,
I think it does, OO (and go-oo) depends on openoffice.org-java-common, which depends on some form of java (sun/openjdk/gcj), it's probably just set up right so you don't notice any of the nasty side effects java used to have.

---

### Post by L4U on 2010-01-05
[How to make OpenOffice run faster in Ubuntu](http://www.zolved.com/synapse/view_content/28209/How_to_make_OpenOffice_run_faster_in_Ubuntu)

:)

---

### Post by scouser73 on 2010-01-05
OpenOffice, it just works, & I've never had a problem with it.  OpenOffice.org are releasing ver 3.2 sometime this month.

---

### Post by Twitch6000 on 2010-01-05
I use go-oo :D.

---

### Post by SecretCode on 2010-01-05
> **mkendall said:**
> Not quite. Go-OO tends to be an update version or two behind. Open Office from the Ubuntu repositories is v3.0.1 while it's up to v3.1.1 with a 3.2 candidate available from the openoffice.org website.

3.1.1 is in the Karmic repos. In fact, it's included in the Karmic release CD.

> **Xbehave said:**
> I think it does, OO (and go-oo) depends on openoffice.org-java-common, which depends on some form of java (sun/openjdk/gcj), it's probably just set up right so you don't notice any of the nasty side effects java used to have.
Ubuntu doesn't include all of go-oo by default - specifically, it doesn't include Base. I think this is the only component that *requires* Java ... and maybe that's the reason.

---

### Post by Xbehave on 2010-01-05
> **SecretCode said:**
> Ubuntu doesn't include all of go-oo by default - specifically, it doesn't include Base. I think this is the only component that *requires* Java ... and maybe that's the reason.
openoffice.org-writer (indluced by default) requires openoffice.org-java-common
ure (required by calc and impress) needs java too

I don't know if java is used by them when you run them but looking at the dependencies suggests it has to be installed

---

### Post by SecretCode on 2010-01-06
> **Xbehave said:**
> openoffice.org-writer (indluced by default) requires openoffice.org-java-common
ure (required by calc and impress) needs java too

I don't know if java is used by them when you run them but looking at the dependencies suggests it has to be installed

"Suggests" being the operative word
```
$ sudo aptitude show openoffice.org-writer 
Package: openoffice.org-writer
State: installed
Automatically installed: no
Version: 1:3.1.1-5ubuntu1
Priority: optional
Section: editors
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 26.8M
Depends: openoffice.org-core (= 1:3.1.1-5ubuntu1), openoffice.org-base-core (= 1:3.1.1-5ubuntu1), libc6 (>= 2.3.4), libgcc1 (>=
         1:4.1.1), libicu40 (>= 4.0-1), libstdc++6 (>= 4.4.0), libwpd8c2a, libwps-0.1-1, ure (>= 1.5.1), zlib1g (>= 1:1.1.4)
Recommends: openoffice.org-emailmerge, openoffice.org-math
Suggests: openoffice.org-gcj, openoffice.org-base, openoffice.org-filter-binfilter, default-jre | gcj-jre | java-gcj-compat |
          openjdk-6-jre | sun-java5-jre | sun-java6-jre | java5-runtime | jre, openoffice.org-java-common (> 2.2.0-4)
Conflicts: openoffice.org-debian-files, openoffice.org-java-common (<= 1:2.3.1), openoffice.org2-writer (< 1:3.1.1-5ubuntu1)
Replaces: openoffice.org (< 1.9), openoffice.org-common (< 1:2.3.1), openoffice.org-debian-files, openoffice.org2-writer (<
          1:3.1.1-5ubuntu1)
Provides: openoffice.org2-writer
Description: full-featured office productivity suite -- word processor
 OpenOffice.org is a full-featured office productivity suite that provides a near drop-in replacement for Microsoft(R) Office. 
 
 This package contains the wordprocessor component for OpenOffice.org.
Homepage: http://www.go-oo.org
```

Booting the live CD, openoffice.org-writer is installed, but there are no java packages:

```
ubuntu@ubuntu:~$ sudo aptitude search ~ijava
ubuntu@ubuntu:~$ sudo aptitude search ~iopenoffice
i   openoffice.org-base-core        - full-featured office productivity suite --
i   openoffice.org-calc             - full-featured office productivity suite --
i   openoffice.org-common           - full-featured office productivity suite --
i   openoffice.org-core             - full-featured office productivity suite --
i   openoffice.org-draw             - full-featured office productivity suite --
i   openoffice.org-emailmerge       - full-featured office productivity suite --
i   openoffice.org-gnome            - full-featured office productivity suite --
i   openoffice.org-gtk              - full-featured office productivity suite --
i   openoffice.org-help-en-us       - full-featured office productivity suite --
i   openoffice.org-hyphenation      - Hyphenation patterns for OpenOffice.org   
i   openoffice.org-hyphenation-en-u - US English hyphenation patterns for OpenOf
i   openoffice.org-impress          - full-featured office productivity suite --
i   openoffice.org-math             - full-featured office productivity suite --
i   openoffice.org-style-human      - Human symbol style for OpenOffice.org     
i   openoffice.org-thesaurus-en-au  - Australian English Thesaurus for OpenOffic
i   openoffice.org-thesaurus-en-us  - English Thesaurus for OpenOffice.org      
i   openoffice.org-writer           - full-featured office productivity suite --
```

---

### Post by Hagar Delest on 2010-01-08
OOo doesn't really need Java. But it is needed for some features (there is a list somewhere in the OOo web site IIRC) like wizards and especially Base.

Base is not installed by default in Ubuntu because of space on the live-CD. But it can be added by Synaptic as said above.

Personally, I only use the Sun version (debs from the OOo web site) because there are fewer bugs and you can upgrade easily to the latest version without upgrading the whole OS. But the go-oo.org version has some additional features (better multimedia support under GNU/Linux I think) and even some .docx save capability. It includes patches that are not accepted in the main build (for various reasons).

NB: I use OOo on xubuntu and I've never had any problem with it, the only thing is that I can't use the Ctrl+# combination to apply formatting, it may be something intercepted by XFCE but no big deal.

---

### Post by nomnex on 2010-06-07
> [FONT=Verdana, Arial, Helvetica][SIZE=2][FONT=Verdana,  Arial, Helvetica][SIZE=2]The  objectors  focus  on  Go-OO  features   ranging  from  support  for  VBA  for  scripts  and  file  import  and   export  for  Microsoft  Works  and  [OOXML  format]("http://en.wikipedia.org/wiki/Ooxml")  to  the   use  of  the  Mono  programming  language  for  add-ons.  They  express   concerns  that    Go-OO  is  yet  another  effort  by  Novell  to   corrupt  FOSS  with  Microsoft  technologies  that  might  be   vulnerable  to  patent  claims.  For  instance,  in  response  to  one  [recent  article]("http://www.linux.com/feature/154364")  on   Go-OO,  a  commenter  mused,  "I  wonder  if  this  is  really  an   improvement  or  an  attempt  to  get  mono  code  integrated  into   OOo."[/SIZE][/FONT][/SIZE][/FONT]

article: [http://www.linuxplanet.com/linuxplanet/reports/6636/1/](http://www.linuxplanet.com/linuxplanet/reports/6636/1/)

---

### Post by Dr. C on 2010-06-07
Reading Microsoft Works files is a big plus for go-oo.org.

From experience I have found that by far the easiest way to introduce FLOSS to a Windows user is to replace Works with OpenOffice.org. After the user gets over the shock that they can get OpenOffice.org for free (as in beer) they are typically very grateful. This opens the door for further penetration by FLOSS: Firefox, Thunderbird, GIMP, GNUCash etc., introduction of the Free Software and Open source concepts and of course eventually Ubuntu.

---

### Post by samalex on 2010-06-07
I hadn't heard of Go-oo until this thread... looks interesting, but from looking at the website it doesn't give lots of pro's or con's with using it over OOo, which has always treated me pretty well.

So why switch to Go-oo instead of OOo?  What patches or fixes are there, and why doesn't this group just try to incorporate the fixes into the official OOo project instead of creating a fork?

Sam

---

### Post by nomnex on 2010-06-07
the OOo Linux from Novell is pushing their infected Mono in their extensions, to provide a better support to Mickeysoft formats.

Go-oo is another separate entity, but it offers more or less the same additional features you have with the Linux OOo. You can read about Go-oo features here: [http://en.wikipedia.org/wiki/Go-oo](http://en.wikipedia.org/wiki/Go-oo).

<rant>I loath Novell, and I am finally re-joining Hagard de l'Est (see his posts above).  I remove the Linux OOo and install the vanilla OOo. it has less bugs, it's lighter and it has no Mono dependencies.</rant>

If you use the Vanilla OOo on your Ubuntu system, you will have to re-install the dictionaries. Take note of what's removed when you pass the command

```
sudo apt-get remove openoffice*.*
```Bye

---

### Post by philinux on 2010-06-07
Moved to Recurring.

---

