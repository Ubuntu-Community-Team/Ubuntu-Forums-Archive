---
title: "Install The Newest Firefox ppa with command &quot;add-apt-repository&quot; (9.10 &amp; above)"
date: 2009-12-11
forum: Outdated Tutorials &amp; Tips
---

### Post by SilverWave on 2009-12-11
[COLOR="Red"]THIS TUTORIAL IS OUTDATED[/COLOR]

[_Install the latest: Beta or Nightly builds of Firefox (firefox _12.0_~b2 or firefox-trunk 14.0a1). _  ]("https://launchpad.net/%7Esilverwave")
A new command makes it easy to add a PPA repository and its key, all at once.

________________________________________[B]
Upcoming Releases  [/B]

*** 2012.03.17  [Add-on Compatibility FF12 - a case in point: Tab Utilities 1.1.3]("http://ubuntuforums.org/showpost.php?p=11772419&postcount=702")

**  Firefox 12 **

  [[IMG]https://wiki.mozilla.org/images/1/1e/Final-50slice.png[/IMG]]("https://wiki.mozilla.org/File:Final-50slice.png")[COLOR=#000]**Currently in BETA channel Moves to RELEASED on April 24, 2012**[/COLOR]
 
**Firefox 13 **

  [[IMG]https://wiki.mozilla.org/images/4/4f/Aurora-50slice.png[/IMG]]("https://wiki.mozilla.org/File:Aurora-50slice.png")[COLOR=Black]**Currently in AURORA channel Moves to BETA on April 24, 2012**
[/COLOR]  
     [B]  Firefox 14 

[/B]   [[IMG]https://wiki.mozilla.org/images/f/fa/Nightly-50slice.png[/IMG]]("https://wiki.mozilla.org/File:Nightly-50slice.png")[COLOR=Black]**Currently in NIGHTLY channel Moves to AURORA on April 24, 2012**[/COLOR]
________________________________________

**Add a Firefox 12.0 Beta PPA**
  I think that the Beta's represent the best reward (in  running the   latest Firefox) for the least risk (very stable and  polished).

* Just a note now that I see how the new rapid release for Firefox is actually working in practice...*

[LIST]
[*] My PPA's will be updated to the latest Beta's as they come out.
[/LIST]

[LIST]
[*] At the end of the cycle they will be updated to the latest firefox.
[/LIST]
 **If you add a Beta PPA from the list below, you will always have the latest FF10, FF11 etc., as soon as they are available.**

> The latest firefox Beta - No other packages.
Copied from firefox-next, Ubuntu Security Proposed & Ubuntu Mozilla Security.
Warning! I am impatient and I copy packages before they have been fully tested.
I even copy packages when status reads "Publishing has been disabled for this archive".
I can do this in good conscience as these ppa's are for my personal use, although I have no problem with others using them.___

**Precise****:**
[https://launchpad.net/~silverwave/+archive/testing8]("https://launchpad.net/%7Esilverwave/+archive/testing8")
```

sudo add-apt-repository ppa:silverwave/testing8 
```**Oneiric:**
[URL="https://launchpad.net/%7Esilverwave/+archive/testing7"]https://launchpad.net/~silverwave/+archive/testing7
[/URL]```

sudo add-apt-repository ppa:silverwave/testing7 
```[B]
Natty:[/B]
[https://launchpad.net/~silverwave/+archive/testing4]("https://launchpad.net/%7Esilverwave/+archive/testing4")
```

sudo add-apt-repository ppa:silverwave/testing4 
```[B]
Lucid
[/B][https://launchpad.net/~silverwave/+archive/testing6]("https://launchpad.net/%7Esilverwave/+archive/testing6")
 ```

sudo add-apt-repository ppa:silverwave/testing6 
```** Update & Install**
     ```

sudo apt-get update
sudo apt-get install firefox
```Note1: This beta will replace your old firefox.

[COLOR=Black]Note2:If you don't wish to replace your firefox, you can use the "***One Nightly A Week***" PPA's below.[/COLOR]
 ___
[CENTER] [Original packages from [firefox-next]("https://launchpad.net/%7Emozillateam/+archive/firefox-next"), [Ubuntu Security Proposed]("https://launchpad.net/%7Eubuntu-security-proposed/+archive/ppa") & [Ubuntu Mozilla Security Team]("https://launchpad.net/%7Eubuntu-mozilla-security/+archive/ppa")]
[/CENTER]
 ________________________________________

**Latest News & Post Highlights:**

*** 2012.03.17  [Add-on Compatibility FF12 - a case in point: Tab Utilities 1.1.3]("http://ubuntuforums.org/showpost.php?p=11772419&postcount=702")

*** 2012.02.25 [Maverik Nightly PPA removed as no longer supported]("http://ubuntuforums.org/showpost.php?p=11716136&postcount=674")

*** 2010.12.16 [Surviving the Statusbar/Add-on Bar Changes -  Barlesque]("http://ubuntuforums.org/showpost.php?p=10243110&postcount=283")

________________________________________

[I]**One Nightly A Week**
 The latest firefox each week[/I].

[LIST]
[*]One ppa per Ubuntu Version (containing firefox-trunk).
[*]Updated at the start of each Week.
[*]This package will not replace your old firefox, (you can use both).
[/LIST]
  ________________________________________

[B]Add a PPA:
[/B]
[One Nightly A Week #2 - Precise]("https://launchpad.net/%7Esilverwave/+archive/testing2") 
```
 sudo add-apt-repository ppa:silverwave/testing2
```[One Nightly A Week #3 - Oneiric]("https://launchpad.net/%7Esilverwave/+archive/testing3") 
```
 sudo add-apt-repository ppa:silverwave/testing3
```[One Nightly A Week #1 - Natty]("https://launchpad.net/%7Esilverwave/+archive/testing1") 
```
 sudo add-apt-repository ppa:silverwave/testing2
```[One Nightly A Week #0 - Lucid]("https://launchpad.net/%7Esilverwave/+archive/testing0") 
```
 sudo add-apt-repository ppa:silverwave/testing0
```**Update & Install**
```
sudo apt-get update
sudo apt-get install firefox-trunk
```Applications   > Internet.
"Nightly Web Browser"

[CENTER] [Original packages from [ubuntu-mozilla-daily]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa?field.series_filter=")]
[/CENTER]
 ________________________________________

**Alternatives**

  Direct from** [ubuntu-mozilla-daily]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa?field.series_filter=")**.[INDENT]**Set-up**
          ```
sudo add-apt-repository ppa:ubuntu-mozilla-daily/ppa
sudo apt-get update
sudo apt-get install firefox-trunk

```[INDENT]*Low safety, daily packages have not undergone any quality assurance.*
* Sometimes very safe but sometimes may not work at all*.
[/INDENT]One potential downside of using ubuntu-mozilla-daily is the number of   updates offered.
Another is that packages other than Firefox are present in the PPA.
[/INDENT]________________________________________

  **Other "add-apt-repository" examples (Non Firefox).**[INDENT]$ sudo add-apt-repository ppa:chromium-daily/beta
$ sudo add-apt-repository ppa:chromium-daily/dev
$ sudo add-apt-repository ppa:chromium-daily/ppa
[/INDENT]**The "add-apt-repository" command.**[INDENT]Creates the file "ubuntu-mozilla-daily-ppa-lucid.list" in the folder /etc/apt/sources.list.d

Adds the key for the ppa.[/INDENT][INDENT] The file ubuntu-mozilla-daily-ppa-lucid.list contains the following line:
deb http ://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu lucid main
[/INDENT]________________________________________

[LEFT]:)[/LEFT]

---

### Post by jpeddicord on 2009-12-13
Modified your title a bit; this is mainly for Karmic [s]and below[/s] (future-proofing; possibly Lucid in the future). Short, but gets the job done. Thanks for your contribution to Tutorials & Tips!

---

### Post by vrkalak on 2009-12-13
I am using the development edition of Xubuntu 10.04 Alpha 1 and I added this to my repository in Software Sources.

[http:// ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu]("http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu") lucid main

And I am now using Firefox 3.7 pre-Alpha 1 as my browser

---

### Post by SilverWave on 2009-12-13
> **vrkalak said:**
> ...And I am now using Firefox 3.7 pre-Alpha 1 as my browser
Yep this is what is available in Karmic today:

>  firefox-3.5      3.5.7~hg20091209r26657+nobinonly-0ubuntu1~umd1~karmic       Fabien Tassin  (2009-12-10)
firefox-3.6     3.6~b6~hg20091212r33356+nobinonly-0ubuntu1~umd1~karmic     Fabien Tassin (18 hours ago)
firefox-3.7     3.7~a1~hg20091213r35651+nobinonly-0ubuntu1~umd1~karmic Fabien Tassin  (18 hours ago) The Firefox 3.6~b6 Beta is pretty stable at this stage but I wouldn't want to risk a 3.7 Alpha1. :D

---

### Post by SilverWave on 2009-12-27
Just installed on new PC this is the expected output:

$ sudo add-apt-repository ppa:ubuntu-mozilla-daily/ppa
[sudo] password for me: 
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv B34505EA326FEAEA07E3618DEF4186FE247510BE
gpg: requesting key 247510BE from hkp server keyserver.ubuntu.com
gpg: key 247510BE: public key "Launchpad PPA for Ubuntu Mozilla Daily Build Team" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
$

---

### Post by Mahngiel on 2009-12-27
So i followed your HowTo, and i appreciate it.  

But i'm not sure why.. but after everything was update and upgraded, i now have two 'FireFox' browsers.  One's named "Shiretoko' and the other 'Namoroka'.

Care to enlighten me on wtf?

---

### Post by Mahngiel on 2009-12-28
here's a screenie.

---

### Post by SilverWave on 2009-12-29
> **Mahngiel said:**
> So i followed your HowTo, and i appreciate it.  

But i'm not sure why.. but after everything was update and upgraded, i now have two 'FireFox' browsers.  One's named "Shiretoko' and the other 'Namoroka'.

Care to enlighten me on wtf?

Shiretoko = FF3.5
Namoroka = FF3.6

You can only use the Firefox Name and Logo if its an official Mozilla build or they have signed off on it.


I had a look here:
[https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa")
The latest offerings in the ppa are...
firefox-3.5     3.5.8~hg20091226r26705+nobinonly-0ubuntu2~umd1~karmic     Fabien Tassin (2009-12-27)
and
firefox-3.6     3.6~b6~hg20091228r33441+nobinonly-0ubuntu1~umd1~karmic     Fabien Tassin (19 hours ago)


Check in Synaptic Package Manager and see which version you have of FF3.5, I would bet you have:
3.5.8~hg20091226r26705+nobinonly-0ubuntu2~umd1~karmic

If so you have updated FF3.5 as well as FF3.6.

Note:
I have updated the How-to regarding the Update Manager and an explanation of how FF3.6 daily is named "Namoroka".

---

### Post by SilverWave on 2009-12-30
The UMD ppa, at the moment, is offering builds of the following:

firefox-3.5
firefox-3.6
firefox-3.7
mozilla-devscripts
prism
thunderbird-3.0
thunderbird-3.1
xulrunner-1.9.1
xulrunner-1.9.2
xulrunner-1.9.3

---

### Post by TSP on 2009-12-31
Already added this repo. My intention is to use thunderbird from here, but keep firefox in sync with current ubuntu repos. If i hold firefox, i don't get any update...is i do and update i get the firefox from this ppa. 
Is there any way to do this? I mean thunderbird from ppa and firefox from official repos?

Cheers.

---

### Post by SilverWave on 2009-12-31
> **TSP said:**
> Already added this repo. My intention is to use thunderbird from here, but keep firefox in sync with current ubuntu repos. If i hold firefox, i don't get any update...is i do and update i get the firefox from this ppa. 
Is there any way to do this? I mean thunderbird from ppa and firefox from official repos?

Cheers.

Easiest way is to add the ppa and use the "Synaptic Package Manager" to install Thunderbird.

Then go to "Software Sources" and deselect the ppa from "Other Software".

Just turn it back on whenever you want to get a more up to date Thunderbird (then turn it back off).

"Synaptic Package Manager" is your friend. :)

---

### Post by SilverWave on 2010-01-02
Now successfully running the 2010 build of 3.6

Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.2b6pre) Gecko/20100102 Ubuntu/9.10 (karmic) Namoroka/3.6b6pre

---

### Post by nanotube on 2010-01-04
For those who'd like to play it safer and stick to the latest mozilla releases (rather than the alphas, betas, and daily trunk builds which you get from this ppa), there's the ubuntuzilla repository:
[http://ubuntuzilla.sourceforge.net/](http://ubuntuzilla.sourceforge.net/)

---

### Post by SilverWave on 2010-01-05
> **nanotube said:**
> For those who'd like to play it safer and stick to the latest mozilla releases (rather than the alphas, betas, and daily trunk builds which you get from this ppa), there's the ubuntuzilla repository:
[http://ubuntuzilla.sourceforge.net/](http://ubuntuzilla.sourceforge.net/)

Thanks.

I always advise people to be careful and not to install packages except from official sources.

I'm sort of stretching a point with the UMD PPA which is semi-official but I don't like 3rd party scripts. I do like that the UMD uses the same protections as the normal repositories use, such as PGP key signing.

I'm mainly adding the UMD PPA to get the 3.6Beta which has no official package in Ubuntu yet.

Some  questions re ubuntuzilla:

[LIST]
[*]  Are your packages PGP key signed.
[*] Why don't you use a PPA?
[*] Is there a 3.6Beta available now?
[*] Are there 64bit versions?
[*] Do your packages install to separate directories to the Official Ubuntu Firefox?
[*] Can I use my normal 3.5 at the same time as I use your package?
[/LIST]

---

### Post by nanotube on 2010-01-05
> **SilverWave said:**
> 
Some  questions re ubuntuzilla:


all of these questions are answered on the ubuntuzilla website ... but i'll answer them again :)

> 
[*]  Are your packages PGP key signed.


yes

> ]
[*] Why don't you use a PPA?

well, the ubuntuzilla repository /is/ a ppa (it is a 'personal package archive'). but i know that what you're really asking is that why it's not a ppa hosted on launchpad, so i'll answer that question.

the problem with using launchpad is that it requires source package uploads ([https://help.launchpad.net/Packaging/PPA/Uploading](https://help.launchpad.net/Packaging/PPA/Uploading)), and then builds the packages. the ubuntuzilla packages, however, are simply repacks of the official binary mozilla builds, rather than builds from source. so there are no 'source' packages to upload. 

> 
[*] Is there a 3.6Beta available now?


no, the repository follows only the official mozilla release stream. 

i think the 'unsafe' versions are already quite well served with the daily and security launchpad ppas, so at this point there's no plan to add the betas and alphas and friends.

> 
[*] Are there 64bit versions?


no, mozilla doesn't release 64bit builds, so there are no 64bit packages.

> 
[*] Do your packages install to separate directories to the Official Ubuntu Firefox?


yes, the stuff goes into /opt.

> 
[*] Can I use my normal 3.5 at the same time as I use your package?


yes you can use any other firefoxes that may be present from the ubuntu repositories. (just be careful not to share the same profile between different major versions of firefox - but that applies to any package regardless of it being from ubuntuzilla or not.)

let me know if you have any other questions! :)

---

### Post by SilverWave on 2010-01-05
Thanks for the reply I was looking though the FAQ...

Ubuntuzilla has moved forward a lot from the last time I looked, very nice :)
[B]
The problem for me is that Ubuntuzilla is the wrong tool for the job in this case.[/B]

The only reason I am using the UMD is that Ubuntu has not provided an up to date 3.6b for me at this time.
Your repository is of no help in this regard as you do not provide  beta packages either :(
Also as I run a 64 OS, it would be a step back to start installing 32bit packages at this late stage in the game.

TBH I think Ubuntuzilla addressed a real need 2 years ago, I remember that Ubuntu seemed very slow in releasing Firefox security updates  at that time.

**Your problem is that Ubuntu are now very fast in releasing updates and they release 64bit packages.**

I would suggest that if Ubuntuzilla is to stay relevant it needs to offer beta packages and 64bit builds.
(As Mozilla don't do 64bit builds I'm not sure you can do anything about that given that you repackage but its a real deal breaker).

---

### Post by nanotube on 2010-01-05
> **SilverWave said:**
> 
Ubuntuzilla has moved forward a lot from the last time I looked, very nice :)


yea we switched from script to repository very recently. :)

> 
[B]
The problem for me is that Ubuntuzilla is the wrong tool for the job in this case.[/B]

The only reason I am using the UMD is that Ubuntu has not provided an up to date 3.6b for me at this time.
Your repository is of no help in this regard as you do not provide  beta packages either :(

indeed, if your goal is to use beta or alpha or daily trunk builds, ubuntuzilla is not for you. but since your post title was "install newest firefox", i figured installing the latest /release/ was also applicable, and people looking at this thread might want to know about it.

> 
Also as I run a 64 OS, it would be a step back to start installing 32bit packages at this late stage in the game.

indeed - but until mozilla starts releasing 64bit builds, there's nothing to repack into .deb and stick into the repository... 

> 
TBH I think Ubuntuzilla addressed a real need 2 years ago, I remember that Ubuntu seemed very slow in releasing Firefox security updates  at that time.

**Your problem is that Ubuntu are now very fast in releasing updates and they release 64bit packages.**


well, it still takes a week or two for a point-release of firefox to make it to the repositories; even longer than that for a point-release of thunderbird; and approximately never for a point-release of seamonkey. 

furthermore, major-releases /never/ make it as an update into the repos. if you're on hardy, intrepid, or jaunty, you're stuck with ff3.0. if you're on hardy, intrepid, jaunty, or karmic, you're stuck with tb2. if you're on hardy, intrepid, jaunty, or karmic, you're stuck with seamonkey1. and all of these are currently /supported/ ubuntu releases. 

so, imho, ubuntuzilla is still quite relevant and addresses a real need, which is to get the latest mozilla release of $package on your ubuntu install in a timely manner.

> 
I would suggest that if Ubuntuzilla is to stay relevant it needs to offer beta packages and 64bit builds.
(As Mozilla don't do 64bit builds I'm not sure you can do anything about that given that you repackage but its a real deal breaker).

well, as far as beta packages - what would be the point of duplicating the effort of the UMD ppa? 

as far as 64bit builds... yes, as soon as mozilla starts making 64bit builds (which, afaik, they are planning to do at /some/ point in the medium-term future - as soon as they get the tracemonkey javascript engine working ono 64bit, at any rate), i'll include 64bit builds in the ubuntuzilla repository. until then, 32bit is all i can do.

---

### Post by SilverWave on 2010-01-05
> **nanotube said:**
> yea we switched from script to repository very recently. :)

furthermore, major-releases /never/ make it as an update into the repos. if you're on hardy, intrepid, or jaunty, you're stuck with ff3.0. [...]

**Thats not correct, I used a Firefox-3.5beta in Jaunty and that was offered from Ubuntu.**

See here:
[https://help.ubuntu.com/community/FirefoxNewVersion](https://help.ubuntu.com/community/FirefoxNewVersion)

"Jaunty and Karmic 
[install  the following package]("https://help.ubuntu.com/community/InstallingSoftware#installing-a-package"): [firefox-3.5]("apt:firefox-3.5").  Firefox 3.5 will  be installed alongside Firefox 3.0."

I was looking for something similar for FF3.6 in Karmic, but as it was originally due out as a quick release, I imagine that it wont be available until it is complete this time.
> 

well, as far as beta packages - what would be the point of duplicating the effort of the UMD ppa? 
Because they are a moving target(and bleeding edge) and you don't get the equivalent to the present official offering from Mozilla(which is only cutting edge) like this one:

[http://www.mozilla.com/en-US/firefox/all-beta.html](http://www.mozilla.com/en-US/firefox/all-beta.html)

[ Free Download 3.6b5 for Linux i686 English (US) (9.4MB)]("http://www.mozilla.com/products/download.html?product=firefox-3.6b5&os=linux&lang=en-US")

---

### Post by nanotube on 2010-01-05
> **SilverWave said:**
> **That not correct, I used a Firefox-3.5beta in Jaunty and that was offered from Ubuntu.**

See here:
[https://help.ubuntu.com/community/FirefoxNewVersion]("https://help.ubuntu.com/community/FirefoxNewVersionThats")

"Jaunty and Karmic 
[install  the following package]("https://help.ubuntu.com/community/InstallingSoftware#installing-a-package"): [firefox-3.5]("apt:firefox-3.5").  Firefox 3.5 will  be installed alongside Firefox 3.0."


ah yes, the firefox-3.5 package is there, but it doesn't exist on hardy or intrepid, and comes with "shiretoko" branding. 

> 
Because they are a moving target and you don't have the equivalent to the present official offering from Mozilla like this one:
[http://www.mozilla.com/en-US/firefox/all-beta.html](http://www.mozilla.com/en-US/firefox/all-beta.html)

[ Free Download 3.6b5 for Linux i686 English (US) (9.4MB)]("http://www.mozilla.com/products/download.html?product=firefox-3.6b5&os=linux&lang=en-US")

ah hmm... well that's a good point... i'll consider it, but i think following betas would be more work than i'm willing to deal with. ;)

---

### Post by SilverWave on 2010-01-05
Latest builds installed and working:

3.6~b6~hg20100104r33473+nobinonly-0ubuntu1~umd1~karmic
1.9.2~b6~hg20100104r33473+nobinonly-0ubuntu1~umd1~karmic

3.7~a1~hg20100105r36838+nobinonly-0ubuntu1~umd1~karmic
1.9.3~a1~hg20100105r36838+nobinonly-0ubuntu1~umd1~karmic

---

### Post by SilverWave on 2010-01-05
**Other "add-apt-repository" examples:**
**1. **```
sudo add-apt-repository ppa:ubuntu-mozilla-security/ppa
```**2.**```
sudo add-apt-repository ppa:ubuntu-mozilla-daily/ppa 
```**3. **Gain access to the latest chromium-daily ppa.
     ```
sudo add-apt-repository ppa:chromium-daily
```Looking at the chromium-daily example above, it may be that the "/ppa" at the end of the other examples is not required :)

But as there is no Man page or Help who knows!

[EDIT][B]
Tested and confirmed, I have updated the command in the How-to[/B].
```

sudo add-apt-repository ppa:ubuntu-mozilla-security
```Successful as below:

```
$ sudo add-apt-repository ppa:ubuntu-mozilla-security
[sudo] password for me: 
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv AF316E81A155146718A6FBD7A6DCF7707EBC211F
gpg: requesting key 7EBC211F from hkp server keyserver.ubuntu.com
gpg: key 7EBC211F: public key "Launchpad PPA for Ubuntu Mozilla Security Team" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
:~$ 
``````
sudo add-apt-repository ppa:ubuntu-mozilla-daily
```Successful as below:

```
:~$ sudo add-apt-repository ppa:ubuntu-mozilla-daily
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv B34505EA326FEAEA07E3618DEF4186FE247510BE
gpg: requesting key 247510BE from hkp server keyserver.ubuntu.com
gpg: key 247510BE: public key "Launchpad PPA for Ubuntu Mozilla Daily Build Team" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
:~$ 
```

---

### Post by nanotube on 2010-01-05
well, fwiw, ff 3.5.7 was released today, and is already present in the ubuntuzilla repository. let's see how long it takes to percolate to the repos for the supported ubuntu releases... ;)

---

### Post by SilverWave on 2010-01-05
> **nanotube said:**
> well, fwiw, ff 3.5.7 was released today, and is already present in the ubuntuzilla repository. let's see how long it takes to percolate to the repos for the supported ubuntu releases... ;)

great minds think alike:

[Firefox security and stability update for version 3.5.7 and 3.0.17 available for download]("http://isc.sans.org/diary.html?storyid=7885&rss")

[s]And this is a fair test as it is a Security Update - so it is important.[/s]

[EDIT: Correction]
[quote=isc.sans.org]Just a quick note - Mozilla released Firefox 3.5.7 and 3.0.17 yesterday.  Having looked through the patch list, it doesn't appear that there are  any security issues though there are some stability fixes added. [[link]("http://isc.sans.org/diary.html?storyid=7897&rss")_]_[/quote]
[status1.9.1: .7-fixed](https://bugzilla.mozilla.org/buglist.cgi?quicksearch=ALL%20status1.9.1%3A.7-fixed)
[ ]("http://isc.sans.org/diary.html?storyid=7897&rss")

---

### Post by nanotube on 2010-01-06
let's wait, but in the meantime here's some data about earlier firefox releases:

firefox 3.5.6, released on December 15, 2009:
the package made it into the karmic repository on 18-Dec-2009

3.5.5, and 3.5.4 did not make it into the karmic repository at all, it seems

3.5.3 was released on September 9, 2009, before karmic was released. so looking at the jaunty repository, the file is dated October 20, 2009. (that's quite a long wait... guess they were waiting for karmic?)

at any rate, let's see how it goes with 3.5.7. 

Seamonkey 2.0.2 is slated for release on january 13, but seeing as how karmic and all previous releases are still on seamonkey1 in the repos, it's never going to make it in...

btw: release date data from [https://wiki.mozilla.org/Releases](https://wiki.mozilla.org/Releases)
package date data from packages.ubuntu.com

---

### Post by SilverWave on 2010-01-07
> **nanotube said:**
> let's wait, but in the meantime here's some data about earlier firefox releases:

firefox 3.5.6, released on December 15, 2009:
the package made it into the karmic repository on 18-Dec-2009

3.5.5, and 3.5.4 did not make it into the karmic repository at all, it seems


I would expect a security update to be released within a week, but even then its urgency depends on the seriousness of the exploit.

Also there has to be _by definition_ some time for the new package to be tested, with a reasonable number of testers, to have assurance that it will not break any other software. In the windows enterprise world the turnaround from the ms updates to deployment is 2-4weeks, sometimes a lot longer (and you pay big bucks for it). Also as my OS is Linux I am not really sweating it, as its damn secure by default and not targeted by the huge majority of malware (if at all). Coming from windows a lot of first time users are jumpy about updating their browser which is understandable :)

Users, who decide that partial quality assurance is sufficient, can get the updates earlier by using the security ppa (and actually helping by being testers and reporting bugs).

```
sudo add-apt-repository ppa:ubuntu-mozilla-security
```[I]Medium safety, halfway through the quality-assurance process.
Bugs are rare but no guarantees are given.[/I]

---

### Post by SilverWave on 2010-01-07
> **nanotube said:**
> well, fwiw, ff 3.5.7 was released today, and is  already present in the ubuntuzilla repository. let's see how long it  takes to percolate to the repos for the supported ubuntu releases... ;)

**Available now in ubuntu-mozilla-security**

```
sudo add-apt-repository ppa:ubuntu-mozilla-security 
```[I]Medium safety, halfway through the quality-assurance process.
Bugs are rare but no guarantees are given.
[/I] 
[Here is the full list]("https://launchpad.net/%7Eubuntu-mozilla-security/+archive/ppa?field.series_filter=")

                firefox-3.0      3.0.17+nobinonly-0ubuntu0.9.04.1      Alexander Sack (2010-01-06)
firefox-3.0     3.0.17+nobinonly-0ubuntu0.8.10.1     Alexander Sack (2010-01-06)
firefox-3.0     3.0.17+nobinonly-0ubuntu0.8.04.1     Alexander Sack (2010-01-06)

firefox-3.5     3.5.7+nobinonly-0ubuntu1                                 Alexander Sack (2010-01-06)
firefox-3.5     3.5.7+nobinonly-0ubuntu0.9.10.1      Alexander Sack (2010-01-06)
firefox-3.5     3.5.7+nobinonly-0ubuntu0.9.04.1      Alexander Sack (2010-01-06)

---

### Post by SilverWave on 2010-01-07
[B]Available now in ubuntu-mozilla-security

[/B]```
sudo add-apt-repository ppa:ubuntu-mozilla-security 
```
[I]Medium  safety, halfway through the quality-assurance process.
Bugs are rare but no guarantees are given.
[/I] [B]
OK as above I added the [/B]**ubuntu-mozilla-security PPA and then ran "Update Manager"**
I received the notification below advising me that 3.5.7 was available.

Changes for the versions:
3.5.6+nobinonly-0ubuntu0.9.10.1
3.5.7+nobinonly-0ubuntu0.9.10.1

**I proceeded with the update and I now have Firefox~3.5.7**

Mozilla/5.0 (X11; U; Linux x86_64; en-GB; rv:1.9.1.7)
Gecko/20100106 Ubuntu/9.10 (karmic)
Firefox/3.5.7 - Build ID: 20091215231754

**easypeasy ;)**

---

### Post by SilverWave on 2010-01-07
Now:
firefox-3.6                                               3.6~hg20100107r33493+nobinonly-0ubuntu1~umd1~karmic                                

Previously:
firefox-3.6     3.6~b6~hg

[Firefox 3.6 RC1 Available for Download Tomorrow January 8th, 2010, Mozilla hopes]("http://news.softpedia.com/news/Firefox-3-6-RC1-Available-for-Download-Tomorrow-131466.shtml")

---

### Post by SilverWave on 2010-01-07
**Gain access to the latest ubuntu-mozilla-daily ppa.**
      ```
sudo add-apt-repository ppa:ubuntu-mozilla-daily 
```[I]Low safety, daily packages have not undergone any quality  assurance.
Sometimes very safe but sometimes may not work at all[/I].

**Checked "Update Manager" and this is what is reported:**

Changes for the versions:
3.6~b6~hg20100104r33473+nobinonly-0ubuntu1~umd1~karmic
3.6~hg20100107r33493+nobinonly-0ubuntu1~umd1~karmic

**Installed proposed changes and I am now running 3.6pre** :D

Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.2pre)
Gecko/20100107 Ubuntu/9.10 (karmic)
Namoroka/3.6pre - Build ID: 20100107062717

---

### Post by nanotube on 2010-01-08
So, ff 3.5.7 made it into the karmic repo today. that makes 3 days since mozilla release. 

Well, not too bad - before, it used to be at least a week.

---

### Post by SilverWave on 2010-01-08
> **nanotube said:**
> So, ff 3.5.7 made it into the karmic repo today. that makes 3 days since mozilla release. 

Well, not too bad - before, it used to be at least a week.

I think you may have missed [**Post 26#**]("http://ubuntuforums.org/showpost.php?p=8623657&postcount=26")

> **SilverWave said:**
> [B]Mozilla Firefox 3.5.7 out 6th. Available in  ubuntu-mozilla-security Same Day!


[/B]firefox-3.0      3.0.17+nobinonly-0ubuntu0.9.04.1      Alexander Sack  (2010-01-06)
firefox-3.0     3.0.17+nobinonly-0ubuntu0.8.10.1     Alexander Sack  (2010-01-06)
firefox-3.0     3.0.17+nobinonly-0ubuntu0.8.04.1     Alexander Sack  (2010-01-06)

firefox-3.5     3.5.7+nobinonly-0ubuntu1                                  Alexander Sack (2010-01-06)
firefox-3.5     3.5.7+nobinonly-0ubuntu0.9.10.1      Alexander Sack  (2010-01-06)
firefox-3.5     3.5.7+nobinonly-0ubuntu0.9.04.1      Alexander Sack  (2010-01-06)And my updated help[B]:
[/B]
> **Latest Firefox Packages**

[LIST]
[*]If you want to have them earlier, enable [ubuntu-mozilla-security PPA]("https://launchpad.net/%7Eubuntu-mozilla-security/+archive/ppa?field.series_filter=")  where the bits will  land first. Enabling this PPA  also will help us test security updates  before they get rolled to the  masses in future; so if you don’t mind a  slightly increased risk of  breakage keep this enabled; in the unlikely  event that you see a  regression from this archive, instantly report  them to the [ubuntu   mozillateam]("http://wiki.ubuntu.com/MozillaTeam").
[/LIST]
This is the Holy Grail for a user who just wants the updates immediately.

[B]You just add the security ppa once and forget about it :)


[/B]

---

### Post by nanotube on 2010-01-08
no, i didn't miss your post about the ubuntu mozilla security ppa. 

i was talking about the official ubuntu repositories. 

that ppa is not part of the 'official ubuntu repositories' which is what most people have in their sources.list.

further, they seem to only be tracking firefox, and not thunderbird and seamonkey.

---

### Post by SilverWave on 2010-01-08
> **nanotube said:**
> no, i didn't miss your post about the ubuntu mozilla security ppa. 

i was talking about the official ubuntu repositories. 

that ppa is not part of the 'official ubuntu repositories' which is what most people have in their sources.list.


Well... I think given the people involved and that they are hosted as a ppa... that their reputation is good enough for me :)
Also advising on how to add a ppa to your sources.list is the focus of this How-to :wink:

> **nanotube said:**
> further, they seem to only be tracking firefox, and not thunderbird and seamonkey.

True  but "Install The Newest **Firefox**..." is the focus of this How-to ;)

---

### Post by SilverWave on 2010-01-09
Note that although based on the man for **apt_preferences** [COLOR=SeaGreen]I am altering it for my own use[/COLOR].
__________________

**apt_preferences(5) - Linux man page**

  **Name**

 apt_preferences - Preference control file for APT

**Description**

   The APT preferences file [COLOR=SeaGreen]**/etc/apt/preferences.d/file**[/COLOR] can be used to  control which versions of packages will be selected for installation.

[B][COLOR=SeaGreen]Example[/COLOR]

[/B] [COLOR=SeaGreen]/etc/apt/preferences.d/ubuntu-mozilla-daily-pin-400
[/COLOR]```
Package: *
Pin: release o=LP-PPA-ubuntu-mozilla-daily
Pin-Priority: 400 
```[COLOR=SeaGreen]
Make sure the file name does not have a dot in  it![/COLOR][COLOR=SeaGreen]
[s]ubuntu-mozilla-daily.pin[/s] < Nope!
ubuntu-mozilla-daily-pin < OK[/COLOR]  

[COLOR=SeaGreen]**Needs to  document which files are considered below /etc/apt/preferences.d**[/COLOR] [APT    Bug #505880]("https://bugs.launchpad.net/apt/+bug/505880")
> **Loïc Minier][Loïc Minier]("https://launchpad.net/%7Elool")              wrote             on 2010-01-11:                                                              [ #1]("https://bugs.launchpad.net/apt/+bug/505880/comments/1")                                   
                     [COLOR=SeaGreen]This is correct said:**
> Several versions of a package may be available for installation  when the ***[I]sources.list***(5)[/I] file contains references  to more than one distribution (for example, stable and testing). APT assigns a priority  to each version that is available. Subject to dependency constraints, **apt-get** selects the version with the highest priority for installation. The APT  preferences file overrides the priorities that APT assigns to package  versions by default, thus giving the user control over which one is selected for  installation. 

Several instances of the same version of a package may be  available when the ***[I]sources.list***(5)[/I] file contains  references to more than one source. In this case **apt-get** downloads the instance listed  earliest in the ***[I]sources.list***(5)[/I] file. The APT  preferences file does not affect the choice of instance, only the choice of version. 
[B]
Apt's Default Priority Assignments[/B]

 If there is no preferences file or if there is no entry in the file  that applies to a particular version then the priority assigned to that  version is the priority of the distribution to which that version belongs. It is  possible to single out a distribution, "the target release", which  receives a higher priority than other distributions do by default. The target release can be set on  the **apt-get** command line or in the APT configuration file */etc/apt/apt.conf*. For example, 

apt-get install -t testing some-package

APT: : Default-Release "stable";

If the target release has been  specified then APT uses the following algorithm to set the priorities of  the versions of a package. 

Assign:

**priority 100**
 To the version that is already installed (if any). [B]

priority 500[/B] 
 To the versions that are not installed and do not belong to the  target release. [B]

priority 990
[/B] To the versions that are not installed and belong to the target  release.

If the target release has not been specified then APT simply assigns  priority 100 to all installed package versions and priority 500 to all  uninstalled package versions. 

APT then applies the following rules, listed in order of  precedence, to determine which version of a package to install. 

[LIST]
[*]Never downgrade unless the priority of an available version exceeds  1000. ("Downgrading" is installing a less recent version of a package in  place of a more recent version. Note that none of APT's default priorities exceeds  1000; such high priorities can only be set in the preferences file. Note  also that downgrading a package can be risky.)
[*]Install the highest priority version.
[*]If two or more versions have the same priority, install the  most recent one (that is, the one with the higher version number).
[*]If two or more versions have the same priority and version  number but either the packages differ in some of their metadata or the  --reinstall option is given, install the uninstalled one.
[/LIST]
 In a typical situation, the installed version of a package (priority  100) is not as recent as one of the versions available from the sources  listed in the ***[I]sources.list***(5)[/I] file (priority 500 or 990). Then  the package will be upgraded when **apt-get install *some-package***  or **apt-get upgrade** is executed. 

More rarely, the installed version of a package is **more**  recent than any of the other available versions. The package will not be  downgraded when **apt-get install *some-package*** or **apt-get upgrade** is  executed. 

Sometimes the installed version of a package is more recent than  the version belonging to the target release, but not as recent as a  version belonging to some other distribution. Such a package will indeed be upgraded when **apt-get  install *some-package*** or **apt-get upgrade** is executed,  because at least **one** of the available versions has a higher priority than  the installed version. 
[B]
The Effect of Apt Preferences[/B]

 The APT preferences file allows the system administrator to control  the assignment of priorities. The file consists of one or more  multi-line records separated by blank lines. Records can have one of two forms, a specific  form and a general form. 

[LIST]
[*]The specific form assigns a priority (a "Pin-Priority") to a  specified package and specified version or version range. For example,  the following record assigns a high priority to all versions of the *perl* package whose  version number begins with "5.8".

 Package: perl
Pin: version 5.8*
Pin-Priority: 1001
[*]The general form assigns a priority to all of the package  versions in a given distribution (that is, to all the versions of  packages that are listed in a certain *Release* file) or to all of the package versions coming  from a particular Internet site, as identified by the site's fully  qualified domain name.

 This general-form entry in the APT preferences file applies only to  groups of packages. For example, the following record assigns a high  priority to all package versions available from the local site. 

Package: *
Pin: origin ""
Pin-Priority: 999

A note of caution: the keyword used here is  "origin". This should not be confused with the Origin of a distribution  as specified in a *Release* file. What follows the "Origin:" tag in a *Release* file is not an  Internet address but an author or vendor name, such as "Debian" or  "Ximian". 

The following record assigns a low priority to all package versions  belonging to any distribution whose Archive name is "unstable". 

Package: *
Pin: release a=unstable
Pin-Priority: 50

The following record assigns a high priority to  all package versions belonging to any release whose Archive name is  "stable" and whose release Version number is "3.0".

 Package: *
Pin: release a=unstable, v=3.0
Pin-Priority: 50
[/LIST]
 **How Apt Interprets Priorities**

 Priorities (P) assigned in the APT preferences file must be positive  or negative integers. They are interpreted as follows (roughly  speaking): 

**[FONT=Courier New][COLOR=SeaGreen][1001, 1002][/COLOR][/FONT]... P > 1000**
 causes a version to be installed even if this constitutes a  downgrade of the package 

**[FONT=Courier New][COLOR=SeaGreen][991 - 1000][/COLOR][/FONT]****... 990 < P <=1000**
causes a version to be installed even if it does not come from  the target release, unless the installed version is more recent [B][COLOR=SeaGreen]

[FONT=Courier New][501 to 990][/FONT][/COLOR][/B][B]... 500 < P <=990
[/B] causes a version to be installed unless there is a version  available belonging to the target release or the installed version is  more recent
[FONT=Courier New]
**[COLOR=SeaGreen][101 to 500][/COLOR]**[/FONT][B]... 100 < P <=500
[/B] causes a version to be installed unless there is a version  available belonging to some other distribution or the installed version  is more recent

[FONT=Courier New]**[COLOR=SeaGreen][001 to 100][/COLOR]**[/FONT][B]... 0 < P <=100
[/B] causes a version to be installed only if there is no installed  version of the package

[FONT=Courier New]**[COLOR=SeaGreen][-001, -002][/COLOR]**[/FONT][B]... P < 0
[/B] prevents the version from being installed

If any specific-form records match an available package version then  the first such record determines the priority of the package version. Failing that, if any general-form records match an available package version then the  first such record determines the priority of the package version. 

For example, suppose the APT preferences file contains the three  records presented earlier: 

Package: perl
Pin: version 5.8*
Pin-Priority: 1001

Package: *
Pin: origin ""
Pin-Priority: 999

Package: *
Pin: release unstable
Pin-Priority: 50 

Then: 
[LIST]
[*]The most recent available version of the perl package will be  installed, so long as that version's version number begins with "5.8".  If **any** 5.8* version of perl is available and the installed version is 5.9*, then  perl will be downgraded.
[*]A version of any package other than perl that is available from  the local system has priority over other versions, even versions  belonging to the target release.
[*]A version of a package whose origin is not the local system but  some other site listed in ***[I]sources.list***(5)[/I] and  which belongs to an unstable distribution is only installed if it is selected for  installation and no version of the package is already installed.
[/LIST]
 **Determination of Package Version and Distribution Properties**

 The locations listed in the ***[I]sources.list***(5)[/I] file  should provide *Packages* and *Release* files to describe the  packages available at that location. 

The *Packages* file is normally found in the directory *.../dists/dist-name/component/arch*:  for example, *.../dists/stable/main/binary-i386/Packages*. It consists of a  series of multi-line records, one for each package available in that  directory. Only two lines in each record are relevant for setting APT priorities: 

[B]The Package: line
[/B] gives the package name

[B]The Version: line
[/B] gives the version number for the named package

The Release file is normally found in the directory *.../dists/dist-name*:  for example, *.../dists/stable/Release*, or *.../dists/woody/Release*. It consists of a single multi-line  record which applies to **all** of the packages in the directory tree  below its parent. Unlike the *Packages* file, nearly all of the lines in a *Release*  file are relevant for setting APT priorities: 

**The Archive: line**
 names the archive to which all the packages in the directory  tree belong. For example, the line "Archive: stable" specifies that all  of the packages in the directory tree below the parent of the *Release* file are in a  stable archive. Specifying this value in the APT preferences file would  require the line:

 Pin: release a=stable

**The Version: line**
 names the release version. For example, the packages in the  tree might belong to Debian GNU/Linux release version 3.0. Note that  there is normally no version number for the testing and unstable distributions because they  have not been released yet. Specifying this in the APT preferences file  would require one of the following lines. 

Pin: release v=3.0
Pin: release a=stable, v=3.0
Pin: release 3.0 

**The Component: line**
 names the licensing component associated with the packages in  the directory tree of the *Release* file. For example, the line  "Component: main" specifies that all the packages in the directory tree are from the main  component, which entails that they are licensed under terms listed in  the Debian Free Software Guidelines. Specifying this component in the APT preferences  file would require the line: 

Pin: release c=main [B]

The Origin: line
[/B] names the originator of the packages in the directory tree of  the *Release* file. Most commonly, this is Debian. Specifying this  origin in the APT preferences file would require the line: 

Pin: release o=Debian [B]

The Label: line
[/B] names the label of the packages in the directory tree of the *Release*  file. Most commonly, this is Debian. Specifying this label in the APT preferences file would require the line: 

Pin: release l=Debian

All of the *Packages* and *Release* files retrieved from  locations listed in the ***[I]sources.list***(5)[/I] file are  stored in the directory */var/lib/apt/lists*, or in the file named by the  variable Dir::State::Lists in the *apt.conf* file. For example, the  file *debian.lcs.mit.edu_debian_dists_unstable_contrib_binary-i386_Release*  contains the *Release* file retrieved from the site  debian.lcs.mit.edu for binary-i386 architecture files from the contrib component of the  unstable distribution. 

**Optional Lines in an Apt Preferences Record**

 Each record in the APT preferences file can optionally begin with one  or more lines beginning with the word Explanation:. This provides a  place for comments. 

The Pin-Priority: line in each APT preferences record is  optional. If omitted, APT assigs a priority of 1 less than the last  value specified on a line beginning with Pin-Priority: release .... 
[B]
Examples[/B]

 **Tracking Stable**

 The following APT preferences file will cause APT to assign a  priority higher than the default (500) to all package versions belonging  to a stable distribution and a prohibitively low priority to package versions  belonging to other Debian distributions. 

Explanation: Uninstall or do not install any Debian-originated
Explanation: package versions other than those in the stable distro
Package: *
Pin: release a=stable
Pin-Priority: 900

Package: *
Pin: release o=Debian
Pin-Priority: -10

With a suitable ***[I]sources.list***(5)[/I]  file and the above preferences file, any of the following commands will  cause APT to upgrade to the latest stable **version**(s).

apt-get install package-name
apt-get upgrade
apt-get dist-upgrade

The following command will cause APT to  upgrade the specified package to the latest version from the testing  distribution; the package will not be upgraded again unless this command is given again.

apt-get install package/testing [B]

Tracking Testing or Unstable[/B]

 The following APT preferences file will cause APT to assign a high  priority to package versions from the testing distribution, a lower  priority to package versions from the unstable distribution, and a prohibitively low  priority to package versions from other Debian distributions. 

Package: *
Pin: release a=testing
Pin-Priority: 900

Package: *
Pin: release a=unstable
Pin-Priority: 800

Package: *
Pin: release o=Debian
Pin-Priority: -10

With a suitable ***[I]sources.list***(5)[/I]  file and the above preferences file, any of the following commands will  cause APT to upgrade to the latest testing **version**(s).

apt-get install package-name
apt-get upgrade
apt-get dist-upgrade

The following command will cause APT to  upgrade the specified package to the latest version from the unstable  distribution. Thereafter, **apt-get upgrade** will upgrade the package to the most recent testing version  if that is more recent than the installed version, otherwise, to the  most recent unstable version if that is more recent than the installed version.

apt-get install package/unstable [B]

See Also[/B]

 ***apt-get**(8 )  **apt-cache**(8 ) **[I]apt.conf***(5)  ***sources.list***(5)[/I] 
[B]
Bugs[/B]

 See the APT bug page [http://bugs.debian.org/src:apt](http://bugs.debian.org/src:apt).  If you wish to report a bug in APT, please see */usr/share/doc/debian/bug-reporting.txt* or the ***reportbug**(1)*  command. 
[B]
Author[/B]

 APT was written by the APT team <[EMAIL="apt@packages.debian.org"]apt@packages.debian.org[/EMAIL]>.   
[B]
Referenced By[/B]

 **apt.conf**(5)

__________________

Note that although based on the man for **apt_preferences** [COLOR=SeaGreen]I am altering it for my own use[/COLOR].

**Useful Commands**
apt-cache policy
apt-cache policy firefox-3.5

---

### Post by SilverWave on 2010-01-09
> **TSP said:**
> Already added this repo. My intention is to use thunderbird from here, but keep firefox in sync with current ubuntu repos. If i hold firefox, i don't get any update...is i do and update i get the firefox from this ppa. 
Is there any way to do this? I mean thunderbird from ppa and firefox from official repos?

Cheers.

I think this is exactly what you are looking for:

[http://www.dataforte.net/blog/2009/11/10/firefox-3-6-and-thunderbird-3-0-on-karmic/](http://www.dataforte.net/blog/2009/11/10/firefox-3-6-and-thunderbird-3-0-on-karmic/)

> **Firefox 3.6 and Thunderbird 3.0 on Karmic**

     "               I regularly use Thunderbird 3.0 betas on my Karmic via the [Ubuntu  Daily Mozilla PPA]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa"). Unfortunately the PPA also contains snapshot  builds of Firefox 3.5 and XulRunner 1.9.1, which I want to keep at their  standard Ubuntu versions. To make *apt-get upgrade*ing as  painless as possible I am using package pinning to stop unwanted  packages from other repositories to override the defaults."[EDIT]
[s]hmm... unfortunately that does not seem to work for me.[/s] :(

[EDIT]
**Wow what a gotcha!**
Make sure the file name does not have a dot in it!  :eek: [APT  Bug #505880]("https://bugs.launchpad.net/apt/+bug/505880")
[s]ubuntu-mozilla-daily.pin[/s] < Nope!
ubuntu-mozilla-daily-pin < OK

Although the code in the blog above does work there is an easier way to do this:

file: ubuntu-mozilla-daily-pin-400
     ```

Package: *
Pin: release o=LP-PPA-ubuntu-mozilla-daily
Pin-Priority: 400
```For details see the next post...

But it does work as advertised :D

---

### Post by SilverWave on 2010-01-09
"I regularly use a package from the [Ubuntu  Daily Mozilla PPA]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa"). Unfortunately the PPA   also contains snapshot  builds of Firefox 3.5 and XulRunner 1.9.1, which   I want to keep at their  standard Ubuntu versions". 

_**The Pinning Solution**_

To make apt-get upgrading as painless as possible set a lower Pin-Priority on the PPA, this will stop unwanted package versions from installing. Once set, packages from the ubuntu-mozilla-daily PPA will always lose in any contest with packages from other repositories, even if they have a higher version.

Create the file: 

[LIST=1]
[*][COLOR=SeaGreen] [COLOR=Black]/etc/apt/preferences.d/ubuntu-mozilla-daily-pin-400

[/COLOR][/COLOR]
[*][COLOR=SeaGreen][COLOR=Black]Add the following to the  file:[/COLOR]
[/COLOR]```
Package: *
Pin: release o=LP-PPA-ubuntu-mozilla-daily
Pin-Priority: 400 
```
[/LIST]
**_The Rules_**

If the target release has not been specified then APT simply assigns   priority 100 to all installed package versions and priority 500 to all   uninstalled package versions. 

APT then applies the following rules, listed in order of  precedence, to  determine which version of a package to install. 

[LIST]
[*]Never downgrade unless the priority of an available version  exceeds  1000. ("Downgrading" is installing a less recent version of a  package in  place of a more recent version. Note that none of APT's  default priorities exceeds  1000; such high priorities can only be set  in the preferences file. Note  also that downgrading a package can be  risky.)
[*]**Install the highest priority version**.
[*]If two or more versions have the same priority, install the  most  recent one (that is, the one with the higher version number).
[*]If two or more versions have the same priority and version  number  but either the packages differ in some of their metadata or the   --reinstall option is given, install the uninstalled one. [Details]("http://ubuntuforums.org/showpost.php?p=8635511&postcount=34").
[/LIST]

_** Before Pinning**_

apt-cache policy

```
:~$ apt-cache policy
Package files:
 100 /var/lib/dpkg/status
     release a=now
 500 http://ppa.launchpad.net karmic/main Packages
     release v=9.10,o=LP-PPA-ubuntu-mozilla-security,a=karmic,n=karmic,l=PPA for Ubuntu Mozilla Security Team,c=main
     origin ppa.launchpad.net
 500 http://ppa.launchpad.net karmic/main Packages
     release v=9.10,o=LP-PPA-ubuntu-mozilla-daily,a=karmic,n=karmic,l=PPA for Ubuntu Mozilla Daily Build Team,c=main
     origin ppa.launchpad.net
 500 http://packages.medibuntu.org karmic/non-free Packages
     release v=9.10,o=Medibuntu,a=karmic,n=karmic,l=Medibuntu,c=non-free
     origin packages.medibuntu.org
 500 http://packages.medibuntu.org karmic/free Packages
     release v=9.10,o=Medibuntu,a=karmic,n=karmic,l=Medibuntu,c=free
     origin packages.medibuntu.org
 500 http://security.ubuntu.com karmic-security/multiverse Packages
     release v=9.10,o=Ubuntu,a=karmic-security,n=karmic,l=Ubuntu,c=multiverse
     origin security.ubuntu.com
 500 http://security.ubuntu.com karmic-security/universe Packages
     release v=9.10,o=Ubuntu,a=karmic-security,n=karmic,l=Ubuntu,c=universe
     origin security.ubuntu.com
 500 http://security.ubuntu.com karmic-security/restricted Packages
     release v=9.10,o=Ubuntu,a=karmic-security,n=karmic,l=Ubuntu,c=restricted
     origin security.ubuntu.com
 500 http://security.ubuntu.com karmic-security/main Packages
     release v=9.10,o=Ubuntu,a=karmic-security,n=karmic,l=Ubuntu,c=main
     origin security.ubuntu.com
 500 http://gb.archive.ubuntu.com karmic-updates/multiverse Packages
     release v=9.10,o=Ubuntu,a=karmic-updates,n=karmic,l=Ubuntu,c=multiverse
     origin gb.archive.ubuntu.com
 500 http://gb.archive.ubuntu.com karmic-updates/universe Packages
     release v=9.10,o=Ubuntu,a=karmic-updates,n=karmic,l=Ubuntu,c=universe
     origin gb.archive.ubuntu.com
 500 http://gb.archive.ubuntu.com karmic-updates/restricted Packages
     release v=9.10,o=Ubuntu,a=karmic-updates,n=karmic,l=Ubuntu,c=restricted
     origin gb.archive.ubuntu.com
 500 http://gb.archive.ubuntu.com karmic-updates/main Packages
     release v=9.10,o=Ubuntu,a=karmic-updates,n=karmic,l=Ubuntu,c=main
     origin gb.archive.ubuntu.com
 500 http://gb.archive.ubuntu.com karmic/multiverse Translation-en_GB
 500 http://gb.archive.ubuntu.com karmic/multiverse Packages
     release v=9.10,o=Ubuntu,a=karmic,n=karmic,l=Ubuntu,c=multiverse
     origin gb.archive.ubuntu.com
 500 http://gb.archive.ubuntu.com karmic/universe Translation-en_GB
 500 http://gb.archive.ubuntu.com karmic/universe Packages
     release v=9.10,o=Ubuntu,a=karmic,n=karmic,l=Ubuntu,c=universe
     origin gb.archive.ubuntu.com
 500 http://gb.archive.ubuntu.com karmic/restricted Translation-en_GB
 500 http://gb.archive.ubuntu.com karmic/restricted Packages
     release v=9.10,o=Ubuntu,a=karmic,n=karmic,l=Ubuntu,c=restricted
     origin gb.archive.ubuntu.com
 500 http://gb.archive.ubuntu.com karmic/main Translation-en_GB
 500 http://gb.archive.ubuntu.com karmic/main Packages
     release v=9.10,o=Ubuntu,a=karmic,n=karmic,l=Ubuntu,c=main
     origin gb.archive.ubuntu.com
Pinned packages:
:~$

```apt-cache policy firefox-3.5

```
:~$ apt-cache policy firefox-3.5
firefox-3.5:
  Installed: 3.5.7+nobinonly-0ubuntu0.9.10.1
  Candidate: 3.5.8~hg20100105r26710+nobinonly-0ubuntu2~umd1~karmic
  Version table:
     3.5.8~hg20100105r26710+nobinonly-0ubuntu2~umd1~karmic 0
        500 http://ppa.launchpad.net karmic/main Packages
 *** 3.5.7+nobinonly-0ubuntu0.9.10.1 0
        500 http://gb.archive.ubuntu.com karmic-updates/main Packages
        500 http://security.ubuntu.com karmic-security/main Packages
        500 http://ppa.launchpad.net karmic/main Packages
        100 /var/lib/dpkg/status
     3.5.3+build1+nobinonly-0ubuntu6 0
        500 http://gb.archive.ubuntu.com karmic/main Packages
:~$

```**_Pinning_**

/etc/apt/preferences.d/ubuntu-mozilla-daily-pin-400
```
Package: *
Pin: release o=LP-PPA-ubuntu-mozilla-daily
Pin-Priority: 400
```_**After Pinning**_

```
:~$ apt-cache policy firefox-3.5
firefox-3.5:
  Installed: 3.5.7+nobinonly-0ubuntu0.9.10.1
  Candidate: 3.5.7+nobinonly-0ubuntu0.9.10.1
  Version table:
     3.5.8~hg20100105r26710+nobinonly-0ubuntu2~umd1~karmic 0
        400 [http://ppa.launchpad.net]("http://ppa.launchpad.net/") karmic/main Packages
 *** 3.5.7+nobinonly-0ubuntu0.9.10.1 0
        500 [http://gb.archive.ubuntu.com]("http://gb.archive.ubuntu.com/") karmic-updates/main Packages
        500 [http://security.ubuntu.com]("http://security.ubuntu.com/") karmic-security/main Packages
        500 [http://ppa.launchpad.net]("http://ppa.launchpad.net/") karmic/main Packages
        100 /var/lib/dpkg/status
     3.5.3+build1+nobinonly-0ubuntu6 0
        500 [http://gb.archive.ubuntu.com]("http://gb.archive.ubuntu.com/") karmic/main Packages
:~$
``````
:~$ apt-cache policy
Package files:
 100 /var/lib/dpkg/status
     release a=now
 500 http://ppa.launchpad.net karmic/main Packages
     release v=9.10,o=LP-PPA-ubuntu-mozilla-security,a=karmic,n=karmic,l=PPA for Ubuntu Mozilla Security Team,c=main
     origin ppa.launchpad.net
 400 http://ppa.launchpad.net karmic/main Packages
     release v=9.10,o=LP-PPA-ubuntu-mozilla-daily,a=karmic,n=karmic,l=PPA for Ubuntu Mozilla Daily Build Team,c=main
     origin ppa.launchpad.net
[...]
 500 http://gb.archive.ubuntu.com karmic/main Packages
     release v=9.10,o=Ubuntu,a=karmic,n=karmic,l=Ubuntu,c=main
     origin gb.archive.ubuntu.com
Pinned packages:
:~$
```Nice :)

Run "Update Manager" and check the section called *"Other  updates (LP-PPA-ubuntu-mozilla-daily)"* to confirm all is well.

__________________

Note that the name of the file you create can not contain a dot.

Based mainly on [Pin down the official Firefox version in Ubuntu]("http://applocator.blogspot.com/2009/11/pin-down-oficial-firefox-version-in.html") and the [Linux man page for apt_preferences]("http://ubuntuforums.org/showpost.php?p=8635511&postcount=34").
With bits from [Firefox 3.6 and Thunderbird 3.0 on Karmic]("http://www.dataforte.net/blog/2009/11/10/firefox-3-6-and-thunderbird-3-0-on-karmic/")[COLOR=#000000][FONT=Sans][COLOR=#002244][FONT=verdana].
[/FONT][/COLOR][/FONT][/COLOR]

---

### Post by SilverWave on 2010-01-12
[APT  Bug #505880]("https://bugs.launchpad.net/apt/+bug/505880")

> **Bug Description**

      The  APT preferences file does not work if its filename contains a dot.
/etc/apt/preferences.d/ubuntu-mozilla-daily-pin.400   < Nope!
/etc/apt/preferences.d/ubuntu-mozilla-daily-pin-400    < OK
 Linux neon 2.6.31-17-generic #54-Ubuntu SMP Thu Dec 10 17:01:44 UTC  2009 x86_64 GNU/Linux
__________________
 Example that works:
/etc/apt/preferences.d/ubuntu-mozilla-daily-pin-400
Code:
 Package: *
Pin: release o=LP-PPA-ubuntu-mozilla-daily
Pin-Priority: 400
__________________
 Notes:
The example at the link below didn't work for me:
[https://wiki.ubuntu.com/MozillaTeam/PPAs](https://wiki.ubuntu.com/MozillaTeam/PPAs)
 Found the problem here:
[http://ubuntuforums.org/showpost.php?p=8636003&postcount=35](http://ubuntuforums.org/showpost.php?p=8636003&postcount=35)
[http://ubuntuforums.org/showpost.php?p=8636047&postcount=36](http://ubuntuforums.org/showpost.php?p=8636047&postcount=36)

               [Loïc  Minier]("https://launchpad.net/%7Elool")          on 2010-01-11   
                                                 **summary**:                       - apt_preferences APT preferences filename can not contain a  dot.
+ Needs to document which files are considered below
+  /etc/apt/preferences.d                   
 
                                                                                  [Loïc  Minier]("https://launchpad.net/%7Elool")          on 2010-01-11   
                                Changed in apt (Ubuntu):                                  **status**:                       New &#8594; Triaged                   
 
                                                                                  [Loïc  Minier]("https://launchpad.net/%7Elool")          on 2010-01-11   
                                Changed in apt (Ubuntu):                                  **importance**:                       Undecided &#8594; Low                   
 
                                                                                  [Loïc  Minier]("https://launchpad.net/%7Elool")          on 2010-01-11   
                                Changed in apt:                                  **status**:                       New &#8594; Confirmed                   
 
                                                                                                      [Loïc Minier]("https://launchpad.net/%7Elool")             wrote             on 2010-01-11:                                                             [ #1]("https://bugs.launchpad.net/apt/+bug/505880/comments/1")                                   
                     This is correct; the code will skip  files which start with a dot, or if it contains a character which is not  alpha numeric or "-" or "_"; it will also only consider regular files  for some reason (ignoring e.g. symbolic links and subdirs).
 This is supposed to be some run-parts-alike filter mechanism to avoid  reading editor backup files, or files leftover by the dpkg conffile  mechanism.
 However, this should be documented in the man page.
 See the sources.list man page and the section on .list files for some  example filenames (ignore the requirement of files ending in .list).

---

### Post by SilverWave on 2010-01-17
Changes for the versions:
3.6~hg20100108r33503+nobinonly-0ubuntu1~umd1~karmic
3.6~hg20100117r33523+nobinonly-0ubuntu1~umd1~karmic

This change is not coming from a source that supports changelogs.

---

### Post by SilverWave on 2010-01-18
Mozilla Developer News » Blog Archive » Firefox 3.6 Release Candidate updated [http://bit.ly/8L9yYn](http://bit.ly/8L9yYn)
> 
An update to the Firefox 3.6 Release Candidate is now available. This  second release candidate is available for     free  download and  has been issued as an automatic update to all   Firefox 3.6 Beta and Release Candidate users.

---

### Post by SilverWave on 2010-01-21
This is the latest 14:20 PM UK

> 
**firefox**       3.6~hg20100120r33527+nobinonly-0ubuntu1~umd2~karmic       Fabien Tassin  (8 hours ago)
firefox-3.5     3.5.8~hg20100121r26729+nobinonly-0ubuntu1~umd1~karmic     Fabien Tassin (8 hours ago)
**firefox-3.6**     3.6~hg20100119r33526+nobinonly-0ubuntu1~umd1~karmic     Fabien Tassin (2010-01-20)
firefox-3.7     3.7~a1~hg20100121r37362+nobinonly-0ubuntu1~umd1~karmic     Fabien Tassin (8 hours ago)

xulrunner-1.9.1     1.9.1.8~hg20100121r26729+nobinonly-0ubuntu2~umd1~karmic     Fabien Tassin (8 hours ago)
xulrunner-1.9.2     1.9.2~hg20100120r33527+nobinonly-0ubuntu1~umd1~karmic     Fabien Tassin (8 hours ago)
xulrunner-1.9.3     1.9.3~a1~hg20100121r37362+nobinonly-0ubuntu1~umd1~karmic     Fabien Tassin (8 hours ago) 
I was only offered xulrunner as an update:
> xulrunner-1.9.2                                               1.9.2~hg20100120r33527+nobinonly-0ubuntu1~umd1~karmic                                                                  [Fabien Tassin]("https://launchpad.net/%7Efta")                                      (8 hours ago)Looking at apt-cache policy  for firefox-3.6

But my machine says latest is: 3.6~hg20100117r33523+nobinonly-0ubuntu1~umd1~karmic

So I seem to be missing out on:
> firefox-3.6     3.6~hg20100119r33526+nobinonly-0ubuntu1~umd1~karmic      Fabien Tassin (2010-01-20)```
:~$ apt-cache policy firefox-3.6
firefox-3.6:
  Installed: 3.6~hg20100117r33523+nobinonly-0ubuntu1~umd1~karmic
  Candidate: 3.6~hg20100117r33523+nobinonly-0ubuntu1~umd1~karmic
  Version table:
 *** 3.6~hg20100117r33523+nobinonly-0ubuntu1~umd1~karmic 0
        400 [http://ppa.launchpad.net]("http://ppa.launchpad.net/") karmic/main Packages
        100 /var/lib/dpkg/status

```If I check apt-cache policy firefox instead:

```
:~$ apt-cache policy firefox
firefox:
  Installed: 3.5.7+nobinonly-0ubuntu0.9.10.1
  Candidate: 3.5.7+nobinonly-0ubuntu0.9.10.1
  Version table:
     3.6~hg20100120r33527+nobinonly-0ubuntu1~umd2~karmic 0
        400 [http://ppa.launchpad.net]("http://ppa.launchpad.net/") karmic/main Packages
 *** 3.5.7+nobinonly-0ubuntu0.9.10.1 0
        500 [http://gb.archive.ubuntu.com]("http://gb.archive.ubuntu.com/") karmic-updates/main Packages
        500 [http://gb.archive.ubuntu.com]("http://gb.archive.ubuntu.com/") karmic-security/main Packages
        500 [http://ppa.launchpad.net]("http://ppa.launchpad.net/") karmic/main Packages
        100 /var/lib/dpkg/status
     3.5.3+build1+nobinonly-0ubuntu6 0
        500 [http://gb.archive.ubuntu.com]("http://gb.archive.ubuntu.com/") karmic/main Packages
```OK that is a little clearer, The package **firefox** is now pointing to a 3.6 package not 3.5. So that must be a change relating to the change from a release candidate to the real thing.

And because I have Pinned the UMD PPA to priority 400, it loses against 3.5.
Great, this is the behaviour that I wanted, although I did not expect it to manifest in exactly this way ;)

That is a didn't want the Official Ubuntu Karmic 3.5 to be replaced by a daily build.

So I suppose that my next update from the dailies will be **firefox-3.6** *something* odd as I did not get 
3.6~hg20100119r**33526**

hmm... could it be because Firefox is  3.6~hg20100120r**33527**?

I'll wait for the next build and see.

Of course once an official Firefox 3.6 is available via the Ubuntu repositories that will be interesting.


================================================================
**[UPDATE 2010/01/21 UK 9:41PM]**

OK I disabled the Pinning against UDM and allowed the updates after a refresh...
What happened was that the Official Ubuntu 3.5 was upgraded to 3.6 which I did not want.
So via Synaptic Package Manager I uninstalled 3.5 and 3.6 then reinstalled the Official Ubuntu 3.5 after turning off the UDM PPA.
Then, after once again enabling the UDM PPA, I installed 3.6.

So now I am back to having the Official Ubuntu Firefox 3.5 and a separate install of the daily 3.6.

Looking at the UDM builds the **firefox** package is marked as **umd2** and firefox-3.6 as **umd1.**
```

firefox       3.6~hg20100120r33527+nobinonly-0ubuntu1~umd2~karmic        Fabien Tassin  (8 hours ago)
firefox-3.6      3.6~hg20100119r33526+nobinonly-0ubuntu1~umd1~karmic     Fabien Tassin  (2010-01-20)
```This is my latest "apt-cache policy" info, with no pinning:
```
:~$ apt-cache policy firefox-3.6
firefox-3.6:
  Installed: 3.6~hg20100117r33523+nobinonly-0ubuntu1~umd1~karmic
  Candidate: 3.6~hg20100117r33523+nobinonly-0ubuntu1~umd1~karmic
  Version table:
 *** 3.6~hg20100117r33523+nobinonly-0ubuntu1~umd1~karmic 0
        500 http://ppa.launchpad.net karmic/main Packages
        100 /var/lib/dpkg/status

:~$ apt-cache policy firefox-3.5
firefox-3.5:
  Installed: 3.5.7+nobinonly-0ubuntu0.9.10.1
  Candidate: 3.6~hg20100120r33527+nobinonly-0ubuntu1~umd2~karmic
  Version table:
     3.6~hg20100120r33527+nobinonly-0ubuntu1~umd2~karmic 0
        500 http://ppa.launchpad.net karmic/main Packages
 *** 3.5.7+nobinonly-0ubuntu0.9.10.1 0
        500 http://gb.archive.ubuntu.com karmic-updates/main Packages
        500 http://gb.archive.ubuntu.com karmic-security/main Packages
        100 /var/lib/dpkg/status
     3.5.3+build1+nobinonly-0ubuntu6 0
        500 http://gb.archive.ubuntu.com karmic/main Packages

:~$ apt-cache policy firefox
firefox:
  Installed: 3.5.7+nobinonly-0ubuntu0.9.10.1
  Candidate: 3.6~hg20100120r33527+nobinonly-0ubuntu1~umd2~karmic
  Version table:
     3.6~hg20100120r33527+nobinonly-0ubuntu1~umd2~karmic 0
        500 http://ppa.launchpad.net karmic/main Packages
 *** 3.5.7+nobinonly-0ubuntu0.9.10.1 0
        500 http://gb.archive.ubuntu.com karmic-updates/main Packages
        500 http://gb.archive.ubuntu.com karmic-security/main Packages
        100 /var/lib/dpkg/status
     3.5.3+build1+nobinonly-0ubuntu6 0
        500 http://gb.archive.ubuntu.com karmic/main Packages
:~$ 


```With Pinning

```
:~$ apt-cache policy firefox-3.6
firefox-3.6:
  Installed: 3.6~hg20100117r33523+nobinonly-0ubuntu1~umd1~karmic
  Candidate: 3.6~hg20100117r33523+nobinonly-0ubuntu1~umd1~karmic
  Version table:
 *** 3.6~hg20100117r33523+nobinonly-0ubuntu1~umd1~karmic 0
        400 http://ppa.launchpad.net karmic/main Packages
        100 /var/lib/dpkg/status

:~$ apt-cache policy firefox-3.5
firefox-3.5:
  Installed: 3.5.7+nobinonly-0ubuntu0.9.10.1
  Candidate: 3.5.7+nobinonly-0ubuntu0.9.10.1
  Version table:
     3.6~hg20100120r33527+nobinonly-0ubuntu1~umd2~karmic 0
        400 http://ppa.launchpad.net karmic/main Packages
 *** 3.5.7+nobinonly-0ubuntu0.9.10.1 0
        500 http://gb.archive.ubuntu.com karmic-updates/main Packages
        500 http://gb.archive.ubuntu.com karmic-security/main Packages
        100 /var/lib/dpkg/status
     3.5.3+build1+nobinonly-0ubuntu6 0
        500 http://gb.archive.ubuntu.com karmic/main Packages

:~$ apt-cache policy firefox
firefox:
  Installed: 3.5.7+nobinonly-0ubuntu0.9.10.1
  Candidate: 3.5.7+nobinonly-0ubuntu0.9.10.1
  Version table:
     3.6~hg20100120r33527+nobinonly-0ubuntu1~umd2~karmic 0
        400 http://ppa.launchpad.net karmic/main Packages
 *** 3.5.7+nobinonly-0ubuntu0.9.10.1 0
        500 http://gb.archive.ubuntu.com karmic-updates/main Packages
        500 http://gb.archive.ubuntu.com karmic-security/main Packages
        100 /var/lib/dpkg/status
     3.5.3+build1+nobinonly-0ubuntu6 0
        500 http://gb.archive.ubuntu.com karmic/main Packages

```

So Firefox-3.6 build 33523 is seen as the latest even though 33526 looks to be available. hmm interesting.
xulrunner-1.9.2 has updated to the latest build 33527.

```

:~$ apt-cache policy xulrunner-1.9.2
xulrunner-1.9.2:
  Installed: 1.9.2~hg20100120r33527+nobinonly-0ubuntu1~umd1~karmic
  Candidate: 1.9.2~hg20100120r33527+nobinonly-0ubuntu1~umd1~karmic
  Version table:
 *** 1.9.2~hg20100120r33527+nobinonly-0ubuntu1~umd1~karmic 0
        400 http://ppa.launchpad.net karmic/main Packages
        100 /var/lib/dpkg/status
```

---

### Post by SilverWave on 2010-01-21
> Firefox:

Changes for the versions:
3.5.7+nobinonly-0ubuntu0.9.10.1
3.6~hg20100120r33527+nobinonly-0ubuntu1~umd2~karmic

This change is not coming from a source that supports changelogs.Firefox 3.6 Final Available (Note: upgrades existing the Official 3.5 if you haven't used Pinning as per previous posts).

**Its Official.**
> The Mozilla Blog "Mozilla Delivers Firefox 3.6 to Millions of Users" [http://bit.ly/8PRhuF](http://bit.ly/8PRhuF)

---

### Post by SilverWave on 2010-01-21
Just tested this on a standard Karmic install and it still works fine :)
     
     ```
sudo add-apt-repository ppa:ubuntu-mozilla-daily
sudo apt-get update
sudo apt-get install firefox-3.6
```> :~$ sudo apt-get install firefox-3.6
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  firefox-3.6-branding xulrunner-1.9.2
Suggested packages:
  firefox-3.6-gnome-support
The following NEW packages will be installed
  firefox-3.6 firefox-3.6-branding xulrunner-1.9.2
0 upgraded, 3 newly installed, 0 to remove and 3 not upgraded.
Need to get 0B/11.3MB of archives.
After this operation, 34.0MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Selecting previously deselected package xulrunner-1.9.2.
(Reading database ... 195129 files and directories currently installed.)
Unpacking xulrunner-1.9.2 (from .../xulrunner-1.9.2_1.9.2~hg20100120r33527+nobinonly-0ubuntu1~umd1~karmic_amd64.deb) ...
Selecting previously deselected package firefox-3.6-branding.
Unpacking firefox-3.6-branding (from .../firefox-3.6-branding_3.6~hg20100117r33523+nobinonly-0ubuntu1~umd1~karmic_amd64.deb) ...
Selecting previously deselected package firefox-3.6.
Unpacking firefox-3.6 (from .../firefox-3.6_3.6~hg20100117r33523+nobinonly-0ubuntu1~umd1~karmic_amd64.deb) ...
Processing triggers for desktop-file-utils ...
Processing triggers for menu ...
Setting up xulrunner-1.9.2 (1.9.2~hg20100120r33527+nobinonly-0ubuntu1~umd1~karmic) ...

Setting up firefox-3.6-branding (3.6~hg20100117r33523+nobinonly-0ubuntu1~umd1~karmic) ...
Setting up firefox-3.6 (3.6~hg20100117r33523+nobinonly-0ubuntu1~umd1~karmic) ...
Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox-3.6
Please restart all running instances of firefox-3.6, or you will experience problems.

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for menu ...
:~$ 

---

### Post by SilverWave on 2010-01-22
[COLOR=RoyalBlue]Note that the way Firefox is being built and maintained in Ubuntu is changing.[/COLOR][COLOR=Blue]

[/COLOR]As an example, they are quite far along with reducing   dependencies.
Unlike a few days ago, installing firefox-3.6 now does   not install xulrunner-1.9.2.
See the notes section below for full details (Firefox New Support Model & Blueprint etc.).

**Installing Firefox-3.6** via the ubuntu-mozilla-daily PPA
You can't now run firefox-3.6 side-by-side with 3.5 as  you could previously.
Rather you are upgrading your existing Firefox-3.5 to the   Firefox-3.6.1  package.
The old "sudo apt-get install firefox-3.6" command will no longer work.

**New Firefox 3.6 Installation Instructions** (Karmic)
     ```

sudo add-apt-repository ppa:ubuntu-mozilla-daily

```  **Now install Firefox as below** (or via the Synaptic Package  Manager).
     ```

sudo apt-get update
sudo apt-get install firefox
```(Alternatively "sudo apt-get install firefox-3.5" works as well).

________________________________________________

**Log** (sudo apt-get install firefox-3.5)
```
silverwave@blue:~$ sudo apt-get update
...
Reading package lists... Done


silverwave@blue:~$ sudo apt-get install firefox-3.5
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  xulrunner-1.9.1-gnome-support firefox-3.5 firefox-3.5-branding
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  firefox firefox-3.5-branding firefox-3.5-gnome-support firefox-branding
Suggested packages:
  firefox-gnome-support
The following NEW packages will be installed
  firefox-branding
The following packages will be upgraded:
  firefox firefox-3.5 firefox-3.5-branding firefox-3.5-gnome-support
4 upgraded, 1 newly installed, 0 to remove and 2 not upgraded.
Need to get 0B/12.4MB of archives.
After this operation, 32.1MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 194866 files and directories currently installed.)
Preparing to replace firefox-3.5-gnome-support 3.5.7+nobinonly-0ubuntu0.9.10.1 (using .../firefox-3.5-gnome-support_3.6.1~hg20100122r33533+nobinonly-0ubuntu1~umd1~karmic_all.deb) ...
Unpacking replacement firefox-3.5-gnome-support ...
Preparing to replace firefox-3.5-branding 3.5.7+nobinonly-0ubuntu0.9.10.1 (using .../firefox-3.5-branding_3.6.1~hg20100122r33533+nobinonly-0ubuntu1~umd1~karmic_all.deb) ...
Unpacking replacement firefox-3.5-branding ...
Selecting previously deselected package firefox-branding.
Unpacking firefox-branding (from .../firefox-branding_3.6.1~hg20100122r33533+nobinonly-0ubuntu1~umd1~karmic_amd64.deb) ...
Preparing to replace firefox-3.5 3.5.7+nobinonly-0ubuntu0.9.10.1 (using .../firefox-3.5_3.6.1~hg20100122r33533+nobinonly-0ubuntu1~umd1~karmic_all.deb) ...
Unpacking replacement firefox-3.5 ...
dpkg: warning: unable to delete old directory '/usr/lib/firefox-3.5.7/components': Directory not empty
dpkg: warning: unable to delete old directory '/usr/lib/firefox-3.5.7': Directory not empty
dpkg: warning: unable to delete old directory '/etc/firefox-3.5/pref': Directory not empty
dpkg: warning: unable to delete old directory '/etc/firefox-3.5/profile/chrome': Directory not empty
dpkg: warning: unable to delete old directory '/etc/firefox-3.5/profile': Directory not empty
dpkg: warning: unable to delete old directory '/etc/firefox-3.5': Directory not empty
Preparing to replace firefox 3.5.7+nobinonly-0ubuntu0.9.10.1 (using .../firefox_3.6.1~hg20100122r33533+nobinonly-0ubuntu1~umd1~karmic_amd64.deb) ...
Unpacking replacement firefox ...
Processing triggers for desktop-file-utils ...
Processing triggers for menu ...
Setting up firefox-3.5-gnome-support (3.6.1~hg20100122r33533+nobinonly-0ubuntu1~umd1~karmic) ...
Setting up firefox-branding (3.6.1~hg20100122r33533+nobinonly-0ubuntu1~umd1~karmic) ...
Setting up firefox-3.5-branding (3.6.1~hg20100122r33533+nobinonly-0ubuntu1~umd1~karmic) ...
Setting up firefox (3.6.1~hg20100122r33533+nobinonly-0ubuntu1~umd1~karmic) ...
update-alternatives: warning: alternative /usr/bin/firefox-3.5 (part of link group x-www-browser) doesn't exist. Removing from list of alternatives.
Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox
Please restart all running instances of firefox, or you will experience problems.

Setting up firefox-3.5 (3.6.1~hg20100122r33533+nobinonly-0ubuntu1~umd1~karmic) ...
Processing triggers for menu ...
silverwave@blue:~$ 


silverwave@blue:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED
  firefox-3.5 firefox-3.5-branding xulrunner-1.9.1-gnome-support
0 upgraded, 0 newly installed, 3 to remove and 1 not upgraded.
After this operation, 455kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 194996 files and directories currently installed.)
Removing firefox-3.5 ...
Removing firefox-3.5-branding ...
Removing xulrunner-1.9.1-gnome-support ...
silverwave@blue:~$ 
```For completeness I tried "sudo apt-get install firefox", this also works.
```
silverwave@blue:~$ sudo apt-get update
[sudo] password for silverwave: 
...
Reading package lists... Done


silverwave@blue:~$ apt-cache policy firefox
firefox:
  Installed: 3.5.7+nobinonly-0ubuntu0.9.10.1
  Candidate: 3.6.1~hg20100122r33535+nobinonly-0ubuntu1~umd1~karmic
  Version table:
     3.6.1~hg20100122r33535+nobinonly-0ubuntu1~umd1~karmic 0
        500 http://ppa.launchpad.net karmic/main Packages
 *** 3.5.7+nobinonly-0ubuntu0.9.10.1 0
        500 http://gb.archive.ubuntu.com karmic-updates/main Packages
        500 http://gb.archive.ubuntu.com karmic-security/main Packages
        100 /var/lib/dpkg/status
     3.5.3+build1+nobinonly-0ubuntu6 0
        500 http://gb.archive.ubuntu.com karmic/main Packages


silverwave@blue:~$ sudo apt-get install firefox
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  xulrunner-1.9.1-gnome-support
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  firefox-3.5-gnome-support firefox-branding
Suggested packages:
  firefox-gnome-support
The following packages will be REMOVED
  firefox-3.5 firefox-3.5-branding
The following NEW packages will be installed
  firefox-branding
The following packages will be upgraded:
  firefox firefox-3.5-gnome-support
2 upgraded, 1 newly installed, 2 to remove and 2 not upgraded.
Need to get 73.0kB/12.2MB of archives.
After this operation, 31.8MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get: 1 http://ppa.launchpad.net karmic/main firefox-3.5-gnome-support 3.6.1~hg20100122r33535+nobinonly-0ubuntu1~umd1~karmic [73.0kB]
Fetched 73.0kB in 0s (265kB/s)                 
(Reading database ... 194866 files and directories currently installed.)
Preparing to replace firefox-3.5-gnome-support 3.5.7+nobinonly-0ubuntu0.9.10.1 (using .../firefox-3.5-gnome-support_3.6.1~hg20100122r33535+nobinonly-0ubuntu1~umd1~karmic_all.deb) ...
Unpacking replacement firefox-3.5-gnome-support ...
dpkg: firefox-3.5-branding: dependency problems, but removing anyway as you requested:
 firefox-3.5 depends on firefox-3.5-branding | abrowser-3.5-branding; however:
  Package firefox-3.5-branding is to be removed.
  Package abrowser-3.5-branding is not installed.
 firefox depends on firefox-3.5-branding.
(Reading database ... 194864 files and directories currently installed.)
Removing firefox-3.5-branding ...
Processing triggers for desktop-file-utils ...
Selecting previously deselected package firefox-branding.
(Reading database ... 194846 files and directories currently installed.)
Unpacking firefox-branding (from .../firefox-branding_3.6.1~hg20100122r33535+nobinonly-0ubuntu1~umd1~karmic_amd64.deb) ...
Processing triggers for desktop-file-utils ...
dpkg: firefox-3.5: dependency problems, but removing anyway as you requested:
 firefox depends on firefox-3.5.
(Reading database ... 194864 files and directories currently installed.)
Removing firefox-3.5 ...
Processing triggers for menu ...
(Reading database ... 194775 files and directories currently installed.)
Preparing to replace firefox 3.5.7+nobinonly-0ubuntu0.9.10.1 (using .../firefox_3.6.1~hg20100122r33535+nobinonly-0ubuntu1~umd1~karmic_amd64.deb) ...
Unpacking replacement firefox ...
Processing triggers for menu ...
Setting up firefox-3.5-gnome-support (3.6.1~hg20100122r33535+nobinonly-0ubuntu1~umd1~karmic) ...
Setting up firefox-branding (3.6.1~hg20100122r33535+nobinonly-0ubuntu1~umd1~karmic) ...
Setting up firefox (3.6.1~hg20100122r33535+nobinonly-0ubuntu1~umd1~karmic) ...
Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox
Please restart all running instances of firefox, or you will experience problems.

Processing triggers for menu ...


silverwave@blue:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED
  xulrunner-1.9.1-gnome-support
0 upgraded, 0 newly installed, 1 to remove and 1 not upgraded.
After this operation, 193kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 194996 files and directories currently installed.)
Removing xulrunner-1.9.1-gnome-support ...
silverwave@blue:~$ 

silverwave@blue:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  xulrunner-1.9.1
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/9,394kB of archives.
After this operation, 532kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 194992 files and directories currently installed.)
Preparing to replace xulrunner-1.9.1 1.9.1.7+nobinonly-0ubuntu0.9.10.1 (using .../xulrunner-1.9.1_1.9.1.8~hg20100121r26730+nobinonly-0ubuntu2~umd1~karmic_amd64.deb) ...
Removing obsolete conffile /etc/gre.d/1.9.1.7.system.conf ...
Unpacking replacement xulrunner-1.9.1 ...
Setting up xulrunner-1.9.1 (1.9.1.8~hg20100121r26730+nobinonly-0ubuntu2~umd1~karmic) ...
update-alternatives: using /usr/bin/xulrunner-1.9.1 to provide /usr/bin/xulrunner (xulrunner) in auto mode.

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
silverwave@blue:~$ 

```________________________________________________

**Notes**

From: [blueprints.launchpad.net]("https://blueprints.launchpad.net/ubuntu/+spec/desktop-lucid-new-firefox-support-model") > 
[Prepare Firefox for Major-Minor Version upgrades]("https://blueprints.launchpad.net/ubuntu/+spec/desktop-lucid-new-firefox-support-model")

Mozilla moved to a monthly security update cycle early in 2009; next  step planned is to stop doing stable release branches for any  distro-relevant amount of time. For instance, they consider to release  firefox 3.6 as a minor update to firefox 3.5 and want to a 3-4 month  cycle for such minor-major version upgrades. Also it happens more  frequently now that they bump requirements on system libs like cairo  and sqlite3 in minor version upgrades.
 This is in line with what is planned by chromium and it's unfeasible  to try to do our own stable release branch maintenance as this would  require far more resources than we can get at any point in the future.
 Instead we should prepare for what is coming and ensure that we can  follow major-minor version upgrades in a timely fashion.
 Main topics addressed by this blueprint are:
  1. how to prepare the firefox package so we can follow the  major-minor version upgrade path.
 2. how to deal with xulrunner reverse-dependencies
From: [wiki.ubuntu.com]("https://wiki.ubuntu.com/DesktopTeam/Specs/Lucid/FirefoxNewSupportModel")
 > 
[DesktopTeam/Specs/Lucid/FirefoxNewSupportModel]("https://wiki.ubuntu.com/DesktopTeam/Specs/Lucid/FirefoxNewSupportModel")

[LIST]
[*]DesktopTeam/Specs/Lucid/FirefoxNewSupportModel
[/LIST]
  
[LIST]
[*]**Blueprint**:  [desktop-lucid-new-firefox-support-model]("https://blueprints.launchpad.net/ubuntu/+spec/desktop-lucid-new-firefox-support-model")
[*]**Contributors**:  Alexander Sack
[*]**Packages involved**: firefox, xulrunner  and its reverse (build) dependencies
[/LIST]
 
**Summary**

 This spec is about reviewing the current support model  for firefox in stable ubuntu releases. Goal is to identify tasks and  procedures that are work intensive or incur risk while not giving  appropriate value for the distributions. For those tasks and procedures  alternatives are presented that involve rolling major version updates to  stable ubuntu releases. 
This spec  covers two parts: 

[LIST=1]
[*]ensure that from lucid onward updating firefox versions to  the next stable branch in security updates does not involve huge porting  efforts
[*]minimize  regressions in existing ubuntu releases when updating firefox/xulrunner  and friends to the latest supported upstream branch
[/LIST]
 
**Rational**

 In short or long term firefox is  expected to move to a changed branch policy; this most likely will  involve even shorter support for stable release branches. Numbers  discussed are: 4-6 weeks for minor security/stability updates and 4-6  month for major version updates; at the same time security/stability  support for old branches will be dropped. 
In consequence, using our "old" way of backporting  patches for firefox becomes more and more unfeasible. The risks of  incurring distribution regressions is high, while the win is debatable. 
 
**Design - New releases**

 The change in support model  suggested by this spec involves changes to various areas outlined in  separate sub sections below. On top this spec defines how a switch to  this new support model for existing ubuntu releases can be accomplished  in a diligent fashion. 
 
**Major version  upgrades instead of backporting**

 Instead of backporting patches to  EOL branches, ubuntu releases will be updated to the next still  supported firefox branch once the current firefox branch of that ubuntu  release goes EOL upstream. This will reduce the workload on developer  and QA side considerably and reduce the risk of incurring additional  regressions due to backporting bugs. 
 
**Use  in-source libraries rather than system libs**

 enabling  system libs is not officially supported upstream and supporting this  caused notable work in the past while sometimes leading to a suboptimal  user experience due to version variants in the ubuntu released compared  to the optimize version shipped in the firefox upstream tarballs. 
 
**Reduce  in-archive reverse dependencies to a minimum**

 Not backporting security fixes,  but upgrading to new firefox branches would come with a considerable  effort for backporting reverse dependencies in the archive. To keep this  approach sustainable the ubuntu archive needs to be reviewed and only  the most important packages can be kept. 
 
**Move extensions to a PPA**

 Extension packages are useful,  but the archives stable support properties doesn't fit their release  policies and user expectations well. Hence, extensions should be moved  to a PPA which then can be made available prominently in the software  center or even through the firefox extension manager at some point. 
 
**Design - stable ubuntu  releases**

 Stable ubuntu releases, will  require a full security coverage in main. This also includes the  xulrunner-1.9.1 packages. Assuming that xulrunner 1.9.1 cannot be kept  secure we will need to update xulrunner to latest branch in much the  same way as suggested for firefox. 
 
**Eliminate embedders**

 non-trivial gecko embedders must  be eliminated in stable ubuntu releases; this needs to happen by moving  them to an existing webkit variant; if no webkit port exists, porting  them to next xulrunner branch needs to be done. 
 
**port plugins**

 Plugins need to be ported in time  to the new firefox/xulrunner major version. Usually this should work  well, however, there are potential issues with java in particular. 
 
**upgrade extensions**

 Extensions that ship binary  components must be updated to latest upstream version. For extensions  that are hosted on AMO (addons.mozilla.org) and do not have binary  components we need to ensure that extensions get updated to the profile  version. For that we ship an install.rdf in an otherwise empty extension  package with a special hint that triggers a system to profile upgrade  on next firefox start. 
 
**Implementation - Lucid**

 
[LIST]
[*]produce a firefox package that does not use  system-libxul
[*]remove  as many system libs from firefox build as possible; revert to in-source  libs where possible
[*]assemble  a table of reverse dependencies
[LIST]
[*]prioritize  reverse dependencies
[*]mark  packages that we cannot or do not need to support for removal
[*]mark packages that use the  gecko embedding API
[*]mark  and categorize extensions in archive:
[LIST]
[*]extensions  with binary components
[*]extensions  without AMO (addons.mozilla.org) support
[*]arch-independent extensions available from  AMO (addons.mozilla.org)
[/LIST]
 
[/LIST]
 
[*]take  decision on support/removal/porting to webkit on all individual  packages
[*]decide on  demotion vs. droppage of xulrunner-1.9.x from the archive.
[*]port/implement/remove  packages as decided
[/LIST]
 
**Implementation for  existing releases**

 
[LIST]
[*]prepare firefox major  version upgrade; base on the lucid branch
[*]assemble tables for reverse dependencies  for all supported ubuntu releases
[LIST]
[*]prioritize  reverse dependencies
[*]mark  reverse dependencies that are not exposed to unsafe content and hence  do not need to be upgraded/replaced
[*]mark  packages that we cannot or do not need to support
[*]mark packages that use the gecko embedding  API
[*]mark extension  packages in the archive for each individual release:
[LIST]
[*]extensions with binary  components
[*]extensions  without AMO (addons.mozilla.org) support
[*]arch-independent extensions available from  AMO (addons.mozilla.org)
[/LIST]
 
[/LIST]
 
[*]take  decision on support/removal/porting to webkit on all individual  packages
[*]backport  karmic/lucid packages for reverse dependencies that moved to webkit or  something else
[/LIST]
 
**Implementation background**

 Moving to this new support model  has some implications on what packages can be accepted in the ubuntu  repository in future: 

[LIST]
[*]xulrunner  embedders must be removed or replaced with webkit backend alternatives
[*]xulrunner npapi plugins  should be maintainable accross multiple firefox branches and hence can  still be in the archive
[*]xulrunner/firefox  extensions must be reduced to the very minimum in archive. Main reason  for archive inclusion should one of the following:
[LIST=1]
[*]required for an ubuntu image or  essential use case
[*]has  binary components - rational is that upstream binary components usually  do not support amd64 or other supported ubuntu archs.
[*]considered useful and is not  distributed in AMO (addons.mozilla.org).
[/LIST]
 
[/LIST]
  **Package Details**
firefox - 3.6.1~hg20100122r33535+nobinonly-0ubuntu1~umd1~karmic
(changesfile)        fta       6 hours ago      Published      Karmic       Web       All builds were built successfully.

**Changelog**
```

firefox (3.6.1~hg20100122r33535+nobinonly-0ubuntu1~umd1~karmic) karmic; urgency=low

  * New upstream release v3.6 (FIREFOX_3_6_RELEASE)
    + fix LP: #449744 - Firefox crashes when attempting to load Firebug 1.5
    + fix LP: #66015 - Duplicate spell checking dictionaries for every entry
    + fix LP: #132938 - tooltips dont work in sidebar
    + fix LP: #195698 - Password asked separately for each tab that requires it
                        (proxy)
    + fix LP: #239462 - tooltips disappear too fast
    + fix LP: #385816 - Resize corner grab stays visible after maximize
    + fix LP: #429476 - firefox crash on javascript page
    + fix LP: #432876 - Icons missing in Firefox searchbox drop down list
    + fix LP: #486284 - maxlength on input box can be overriden by autocomplete
    + fix LP: #501393 - Integrate Firefox notifications with notify-osd bling

  [ H. Montoliu <email address hidden> ]
  * fix LP: #361052 - firefox apport hook fails to retrieve pluginreg.dat file
  * update debian/apport/firefox-3.6.py - removed unused code and minor refactoring.

  [ Fabien Tassin <email address hidden> ]
  * Update the location of the upsteam branch now that 3.6/Namoroka has its own
    branch, and trunk moved on to 3.7
    - update debian/mozclient/firefox-3.6.conf
  * Use Namoroka instead of Shiretoko as brand name and use it for snapshots.
    Name it Namoroka in the Preferred Application UI too
    - update debian/firefox-3.6-shiretoko.desktop => debian/firefox-3.6-namoroka.desktop
    - update debian/firefox-3.6.xml
    - update debian/rules
  * Target the 'default' branch instead of tip
    - add debian/moz-rev.sh
    - update debian/mozclient/firefox-3.6.conf
  * Drop upstreamed patch now that it has landed and add --with-system-libxul
    to configure.
    - update debian/rules
    - drop debian/patches/installer_shouldnt_copy_xulrunner.patch
    - update debian/patches/series
  * Add libstartup-notification0-dev to build-deps as it now seems to be
    mandatory on lpia
    - update debian/control
  * Update MOZCLIENT_GETDATE to make it use pushlog so it is not confused by merges with
    dates in the past
    - update debian/mozclient/firefox-3.6.conf
  * Add firefox 3.6 to the list of Preferred Applications in Gnome
    - add debian/firefox-3.6.xml
    - update debian/firefox-3.6-gnome-support.install
  * Fix profile migrator broken when using abrowser-3.6
    - update debian/firefox.sh.in
  * Call update-menus
    - update debian/firefox-3.6.postinst.in
  * Fix bogus prerm rule removing the wrong alternative
    - update renamed debian/firefox-3.6.prerm -> debian/firefox-3.6.prerm.in
    - update debian/rules
  * Fix startup page, release notes and first run bogus URLs when
    using non official brandings. Also fix bogus addons URLs due
    to our change of appname
    - update debian/patches/firefox-profilename
  * Fix postinst to also consider firefox-3.6 for the update-notifier
    restart notification
    - update debian/firefox-3.6.postinst.in
  * Bump Standards-Version to 3.8.1
    - update debian/control
  * Add ${misc:Depends} to all non-transitional packages, make firefox-3.6-dbg
    depend on firefox-3.6 with the exact same version, move -dbg packges to
    priority extra and add firefox-3.6-gnome-support-dbg
    - update debian/control
  * Update diverged patches:
    - update debian/patches/browser_branding.patch
    - update debian/patches/firefox-profilename
    - update debian/patches/ubuntu_bookmarks.patch
    - update debian/patches/lp185622_system_path_default_browser.patch
    - update debian/patches/dont_depend_on_nspr_sources.patch

  [ Alexander Sack <email address hidden> ]
  * add libnotify-dev to build-depends
    - update debian/control
  * fix LP: #398121 - firefox-3.5-gnome-support failed to install/upgrade; we
    make the postinst script more failsafe
    - update debian/firefox-3.6-gnome-support.postinst.in
  * add libiw-dev to build-depends to fix build failure
    - update debian/control
  * set BUILD_OFFICIAL = 1 to enable all official build features
    - update debian/rules
  * fix LP: #404827 - Firefox doesn't warn about Attack Sites!?; add
    --enable-safe-browsing to configure flags
    - update debian/rules
  * fix restart issues by installing proper versioned binary (without firefox-fsh
    patch changing the dist binary name); in turn drop unversioned firefox link
    from .install; dropping versioned binary part from firefox-fsh accordingly
    - update debian/rules
    - update debian/firefox-3.6.install
    - update debian/patches/firefox-fsh
  * fix LP: #422365 - apport hook fails because profiles_d is not initialized
    in add_info if no profiles.ini exist; we ensure that profiles_d gets instantiated
    as an empty map even if no profiles.ini exist.
    - update debian/apport/firefox-3.6.py
  * hook firefox-addons/searchplugins as the distribution/searchplugins
    directory to support localized distro search engines.
    - update debian/rules
  * in case localized search engines are available the main searchplugins
    directory is not scanned anymore; to fix this we provide a compatibility
    link /usr/lib/firefox-addons/searchplugins/common => /usr/lib/firefox-addons/searchplugins
    - update debian/firefox-3.5.links
  * until we move searchplugins to a separate package provided only by the current default
    firefox, we need to make firefox-3.6 replace all the older firefox binary packages:
    firefox-3.5, firefox-3.2, firefox-3.1, firefox-3.0
    - update debian/control
  * fix localized search engine upstream code to use ChromeRegistry locale
    information rather than a char pref; also change plugin dir order to allow
    locale specific searchplugins to overlay the ones shipped in
    "searchplugins/common"
    - add debian/patches/bz515232_att399338_distro_locale_searchplugins.patch
    - update debian/patches/series
  * fix LP: #423610 - daily build failures after landing of mozilla-nss.pc droppage
    (bug 422829); we drop our previously used nspr pkgconfig patch and fix
    configure.in to not require in-source nspr if libxul-sdk is used
    - delete debian/patches/nspr_flags_by_pkg_config_hack.patch
    - add debian/patches/bzXXX_libxul_sdk_nspr.patch
    - update debian/patches/series
  * implement MIN_SYS_DEPS approach that does not use system xulrunner
    and only a minimal set of system dependencies.
    + drop patches not required anymore:
      - delete debian/patches/dont_depend_on_nspr_sources.patch
      - update debian/patches/series
    + update browser directory provider patch
      - update debian/patches/bz515232_att399338_distro_locale_searchplugins.patch
    + move .install lines that depend on whether MIN_SYS_DEPS is used or not
      to debian/rules in ifneq (,$(MIN_SYS_DEPS)) blocks
      - update debian/rules
      - update debian/firefox-3.5.install
    + ship gnome support .so's inside of the main package, but keep dependencies in
      the (now empty) gnome-support package; to achieve this, we first install
      the gnome support files in the -gnome-support package and move them to the
      main package _after_ shlib depends where generated
      - update debian/rules
    + do not build-depend on xulrunner dev package anymore; local xulrunner builds
      with MIN_SYS_DEPS=0 should still work though
      - update debian/control
    + make firefox-3.5 conflict firefox-3.5-gnome-support as it shipps the gnome
      files directly now
      - update debian/control
  * add patch for armv7 support
    - add debian/patches/bz532198_lp488354_ns_invokebyindex_not_thumb2_safe.patch
    - update debian/patches/series
  * move to unversioned binary and source package name for "archive" firefox
    + generalize final version dependent pieces in debian/rules
      - update debian/rules
    + update mozclient/ files to create unversioned sources/tarballs
      - rename debian/mozclient/firefox-3.6.conf => debian/mozclient/firefox.conf
      - update debian/mozclient/firefox.conf
      - rename debian/mozclient/firefox-3.6.mk => debian/mozclient/firefox.mk
    + rename and update previously versioned debhelper files
      - rename debian/firefox-3.6-dev.install => debian/firefox-dev.install
      - rename debian/firefox-3.6-dev.links => debian/firefox-dev.links
      - rename debian/firefox-3.6-gnome-support.install => debian/firefox-gnome-support.install
      - rename debian/firefox-3.6-gnome-support.postinst.in => debian/firefox-gnome-support.postinst.in
      - rename debian/firefox-3.6.dirs => debian/firefox.dirs
      - rename debian/firefox-3.6.install => debian/firefox.install
      - update debian/firefox.install
      - rename debian/firefox-3.6.links => debian/firefox.links
      - update debian/firefox.links
    + rename versioned maintainer scripts
      - rename debian/firefox-3.6.postinst.in => debian/firefox.postinst.in
      - rename debian/firefox-3.6.postrm.in => debian/firefox.postrm.in
      - rename debian/firefox-3.6.preinst.in => debian/firefox.preinst.in
      - rename debian/firefox-3.6.prerm.in => debian/firefox.prerm.in
    + rename and update previously versioned .desktop, gnome helper and other debian
      integration files
      - rename debian/abrowser-3.6.desktop => debian/abrowser.desktop
      - rename debian/firefox-3.6-final.desktop => debian/firefox-final.desktop
      - update debian/firefox-final.desktop
      - rename debian/firefox-3.6-minefield.desktop => debian/firefox-minefield.desktop
      - update debian/firefox-minefield.desktop
      - rename debian/firefox-3.6-namoroka.desktop => debian/firefox-namoroka.desktop
      - update debian/firefox-namoroka.desktop
      - rename debian/firefox-3.6.menu => debian/firefox.menu
      - update debian/firefox.menu
      - rename debian/firefox-3.6.xml => debian/firefox.xml
      - update debian/firefox.xml
      - rename debian/firefox-3.6-restart-required.update-notifier => debian/firefox-restart-required.update-notifier
      - update debian/firefox-restart-required.update-notifier
      - update debian/control
    + disable patches for versioned directories and binaries
      - update debian/patches/series
    + add fix issues in libpr0n for make syntax issues after lucid dash/bash update;
      patch by Kees Cook <email address hidden>
      - add debian/patches/fix-build-glitch.patch
      - update debian/patches/series
  * ease transition for daily firefox-3.6 users by adding conflicts/replaces on firefox-3.6-gnome-support
    to firefox binary package which now ships bits previously in there.
    - update debian/control
  * update to firefox.sh.in start script from firefox-3.5 branch and add firefox-3.6 transition
    accordingly; also adjust a bunch of wrongly worded debug messages
    - update debian/firefox.sh.in
  * fix version number used in profile migration dialog
    - update debian/migrator/main.c
  * fix wrapper startscript to properly handle all-static firefox build
    - update debian/firefox.sh.in

  [ Micah Gersten <email address hidden> ]
  * Rebase/minor code change after upstream landing of unified manifest (bmo: 511642)
    - update debian/patches/awesome_browser_branding_install.patch
    - update debian/patches/browser_branding.patch
    - update debian/patches/bzXXX_moz_app_name_inconsistencies.patch
  * Bump minimum system cairo to 1.8.8
    - update debian/rules

  [ Jamie Strandboge <email address hidden> ]
  * add AppArmor profile (disabled by default)
    - debian/firefox-3.6.dirs: add etc/apparmor.d/disable
    - add debian/firefox-3.6.preinst.in: disable the profile on new installs,
      installs where the last modified profile is disabled and upgrades to
      this version
    - debian/firefox-3.6.postinst.in: reload profile
    - add debian/firefox-3.5.postrm.in: cleanup force-complain and disable
      directories
    - add debian/usr.bin.firefox.apparmor.in
    - add debian/README.Debian.in with note about AppArmor
    - debian/apport/firefox-3.6.py: add AppArmor information if the profile is
      not disabled
    - debian/rules: install profile and update subst_files
    - allow dirname and pwd. Thanks to Thomas Templin. (LP: #510644)
    - allow the IBM jre
    - debian/usr.bin.firefox.apparmor.in: use @LIBDIR@/firefox-*bin as binary
      confined by AppArmor

  [ Benjamin Drung <email address hidden> ]
  * Add metadata for mozilla-devscripts
    - update debian/control

  [ Kees Cook <email address hidden> ]
  * enable PIE build for stronger security (LP: #507744)
    - update debian/rules
    - update debian/control

  [ Fabien Tassin ]
 -- Fabien Tassin <email address hidden>   Fri, 22 Jan 2010 21:51:11 +0100

Available diffs

    * 3.6.1~hg20100122r33533+nobinonly-0ubuntu1~umd1~karmic to 3.6.1~hg20100122r33535+nobinonly-0ubuntu1~umd1~karmic (4.2 KiB)

```Interesting...
>     * implement MIN_SYS_DEPS approach that does not use system xulrunner
      and only a minimal set of system dependencies.
   
    + ship gnome support .so's inside of the main package, but keep dependencies in
      the (now empty) gnome-support package; to achieve this, we first install
      the gnome support files in the -gnome-support package and move them to the
      main package _after_ shlib depends where generated
      - update debian/rules
    + do not build-depend on xulrunner dev package anymore; local xulrunner builds
      with MIN_SYS_DEPS=0 should still work though
      - update debian/control
    + make firefox-3.5 conflict firefox-3.5-gnome-support as it shipps the gnome
      files directly now
      - update debian/control


---

### Post by lovinglinux on 2010-01-23
> **SilverWave said:**
> **Everything is Changing**
[COLOR=RoyalBlue]OK the old instructions, noted in the last post, may no longer work as things have changed.[/COLOR][COLOR=Blue]
[/COLOR] This is because Firefox-3.6 is now considered to be a minor version upgrade to 3.5 and the Ubuntu Mozilla Daily PPA packages have been rebuilt to reflect this. :)

It was already updating firefox-3.5 package to 3.6 since the official release from Mozilla, if you just updated Firefox after adding *ubuntu-mozilla-daily* ppa. So I guess they were already following the new policy of major-minor versions. Nevertheless, you was able to install firefox-3.6 separately until yesterday. I can confirm this can no longer be done. Now, even if you try to install firefox-3.6 package, you get an update instead of a separate application.

---

### Post by SilverWave on 2010-01-23
> **lovinglinux said:**
> It was already updating firefox-3.5 package to 3.6 since the official release from Mozilla, if you just updated Firefox after adding *ubuntu-mozilla-daily* ppa. So I guess they were already following the new policy of major-minor versions. Nevertheless, you was able to install firefox-3.6 separately until yesterday. I can confirm this can no longer be done. Now, even if you try to install firefox-3.6 package, you get an update instead of a separate application.

Thanks for the independent confirmation.

BTW have you seen this?

> Interesting...
     Quote:
                                                     * implement MIN_SYS_DEPS approach that does not use system  xulrunner
      and only a minimal set of system dependencies.
   
    + ship gnome support .so's inside of the main package, but keep  dependencies in
      the (now empty) gnome-support package; to achieve this, we first  install
      the gnome support files in the -gnome-support package and move  them to the
      main package _after_ shlib depends where generated
      - update debian/rules
    + do not build-depend on xulrunner dev package anymore; local  xulrunner builds
      with MIN_SYS_DEPS=0 should still work though
      - update debian/control
    + make firefox-3.5 conflict firefox-3.5-gnome-support as it shipps  the gnome
      files directly now
      - update debian/control                      I think its interesting as to how far along they are with reducing dependencies to xulrunner...

I noticed that unlike a few days ago, installing firefox-3.6 now does not install xulrunner-1.9.2

---

### Post by lovinglinux on 2010-01-23
> **SilverWave said:**
> Thanks for the independent confirmation.

BTW have you seen this?

I think its interesting as to how far along they are with reducing dependencies to xulrunner...

I noticed that unlike a few days ago, installing firefox-3.6 now does not install xulrunner-1.9.2

I have noticed that too. Although I have installed it manually and removed version 1.9.1. I'm about to remove both and see what happens. Synaptic doesn't complain about dependencies (I use KDE) :)

EDIT: it works! Wicked. I was wondering why Namoroka didn't show xulrunner info in the about page. As far as I remember, this info was included in Firefox 3.5, wasn't it? I guess we have found why it isn't anymore.

---

### Post by zika on 2010-01-23
> **lovinglinux said:**
> I have noticed that too. Although I have installed it manually and removed version 1.9.1. I'm about to remove both and see what happens. Synaptic doesn't complain about dependencies :)

EDIT: it works! Wicked. I was wondering why Namoroka didn't show xulrunner info in the about page. As far as I remember, this info was included in Firefox 3.5, wasn't it? I guess we have found why it isn't anymore.If I try to remove 1.9.1 it wants to remove a bunch of couchdb stuff...```
~$ sudo aptitude purge xulrunner-1.9.1
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following packages are BROKEN:
  couchdb-bin xulrunner-1.9.1-gnome-support 
The following packages will be REMOVED:
  xulrunner-1.9.1{p} 
0 packages upgraded, 0 newly installed, 1 to remove and 16 not upgraded.
Need to get 0B of archives. After unpacking 27.9MB will be freed.
The following packages have unmet dependencies:
  xulrunner-1.9.1-gnome-support: Depends: xulrunner-1.9.1 (= 1.9.1.8~hg20100122r26732+nobinonly-0ubuntu1~umd1) but it is not installable
  couchdb-bin: Depends: xulrunner-1.9.1 but it is not installable
The following actions will resolve these dependencies:

Remove the following packages:
couchdb-bin
desktopcouch
evolution-couchdb
python-desktopcouch
python-desktopcouch-records
xulrunner-1.9.1-gnome-support

Leave the following dependencies unresolved:
ubuntu-desktop recommends evolution-couchdb
Score is 264

Accept this solution? [Y/n/q/?]
```

---

### Post by lovinglinux on 2010-01-23
> **zika said:**
> If I try to remove 1.9.1 it wants to remove a bunch of couchdb stuff...

I forgot a little detail...I use KDE :)

While Firefox does not need xulrunner anymore, there are other gnome dependencies. So don't do it.

Or look at [this](http://www.freedesktop.org/wiki/Specifications/desktopcouch) and decide for yourself.

Anyway, I don't see a reason to remove xulrunner other than testing if Firefox doesn't need it.

---

### Post by SilverWave on 2010-01-23
> **zika said:**
> If I try to remove 1.9.1 it wants to remove a bunch of ...
Accept this solution? [Y/n/q/?]

**Definitely No.**

I was referring to Firefox-3.6 not needing **xulrunner-1.9.2**.

As you can see Karmic was built with the expectation that lots of different packages could call on xulrunner-1.9.1.

---

### Post by SilverWave on 2010-01-23
**RE: ubuntu-mozilla-daily**

>  ffox36-daily-transition-special       3.6+karmic       Alexander Sack  (2010-01-21)

[COLOR=RoyalBlue]firefox     3.6.1~hg20100122r33535+nobinonly-0ubuntu1~**umd2**~karmic     Fabien Tassin (19 hours ago)[/COLOR]
firefox-3.5     3.5.8~hg20100122r26732+nobinonly-0ubuntu1~umd1~karmic     Fabien Tassin (19 hours ago)
firefox-3.6     3.6~hg20100119r33526+nobinonly-0ubuntu1~umd1~karmic     Fabien Tassin (2010-01-20)
firefox-3.7     3.7~a1~hg20100123r37429+nobinonly-0ubuntu1~umd1~karmic     Fabien Tassin (19 hours ago)
mozilla-devscripts     0.20~umd8~karmic     Fabien Tassin (2010-01-13)
prism     1.0b3pre+svn20100114r59888-0ubuntu1~umd1~karmic     Fabien Tassin (2010-01-15)
thunderbird-3.0     3.0.2~hg20100123r4647+nobinonly-0ubuntu1~umd1~karmic     Fabien Tassin (19 hours ago)
thunderbird-3.1     3.1~a1~hg20091229r4604+nobinonly-0ubuntu1~umd1~karmic     Fabien Tassin (2010-01-02)
xulrunner-1.9.1     1.9.1.8~hg20100122r26732+nobinonly-0ubuntu1~umd1~karmic     Fabien Tassin (19 hours ago)
xulrunner-1.9.2     1.9.2.1~hg20100122r33535+nobinonly-0ubuntu1~umd1~karmic     Fabien Tassin (19 hours ago)
xulrunner-1.9.3     1.9.3~a1~hg20100123r37429+nobinonly-0ubuntu1~umd1~karmic     Fabien Tassin (19 hours ago) Interesting. I wondered why I was being offered an update which looked to have the same build.

```
:~$ apt-cache policy firefox
firefox:
  Installed: 3.6.1~hg20100122r33535+nobinonly-0ubuntu1~umd1~karmic
  Candidate: 3.6.1~hg20100122r33535+nobinonly-0ubuntu1~umd2~karmic
  Version table:
     3.6.1~hg20100122r33535+nobinonly-0ubuntu1~umd2~karmic 0
        500 http://ppa.launchpad.net karmic/main Packages
 *** 3.6.1~hg20100122r33535+nobinonly-0ubuntu1~umd1~karmic 0
        100 /var/lib/dpkg/status
     3.5.7+nobinonly-0ubuntu0.9.10.1 0
        500 http://gb.archive.ubuntu.com karmic-updates/main Packages
        500 http://gb.archive.ubuntu.com karmic-security/main Packages
     3.5.3+build1+nobinonly-0ubuntu6 0
        500 http://gb.archive.ubuntu.com karmic/main Packages
:
```  Installed: 3.6.1~hg20100122r33535+nobinonly-0ubuntu1~**umd1**~karmic
  Candidate: 3.6.1~hg20100122r33535+nobinonly-0ubuntu1~**umd2**~karmic

```
:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  firefox firefox-3.5-gnome-support firefox-branding xulrunner-1.9.1
4 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 21.6MB of archives.
After this operation, 24.6kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get: 1 http://ppa.launchpad.net karmic/main firefox-branding 3.6.1~hg20100122r33535+nobinonly-0ubuntu1~umd2~karmic [147kB]
Get: 2 http://ppa.launchpad.net karmic/main firefox 3.6.1~hg20100122r33535+nobinonly-0ubuntu1~umd2~karmic [12.0MB]
Get: 3 http://ppa.launchpad.net karmic/main firefox-3.5-gnome-support 3.6.1~hg20100122r33535+nobinonly-0ubuntu1~umd2~karmic [72.7kB]                                                                          
Get: 4 http://ppa.launchpad.net karmic/main xulrunner-1.9.1 1.9.1.8~hg20100122r26732+nobinonly-0ubuntu1~umd1~karmic [9,400kB]                                                                                 
Fetched 21.6MB in 1min 44s (207kB/s)                                                                                                                                                                          
(Reading database ... 194993 files and directories currently installed.)
Preparing to replace firefox-branding 3.6.1~hg20100122r33535+nobinonly-0ubuntu1~umd1~karmic (using .../firefox-branding_3.6.1~hg20100122r33535+nobinonly-0ubuntu1~umd2~karmic_amd64.deb) ...
Unpacking replacement firefox-branding ...
Preparing to replace firefox 3.6.1~hg20100122r33535+nobinonly-0ubuntu1~umd1~karmic (using .../firefox_3.6.1~hg20100122r33535+nobinonly-0ubuntu1~umd2~karmic_amd64.deb) ...
Unpacking replacement firefox ...
Preparing to replace firefox-3.5-gnome-support 3.6.1~hg20100122r33535+nobinonly-0ubuntu1~umd1~karmic (using .../firefox-3.5-gnome-support_3.6.1~hg20100122r33535+nobinonly-0ubuntu1~umd2~karmic_all.deb) ...
Unpacking replacement firefox-3.5-gnome-support ...
Preparing to replace xulrunner-1.9.1 1.9.1.8~hg20100121r26730+nobinonly-0ubuntu2~umd1~karmic (using .../xulrunner-1.9.1_1.9.1.8~hg20100122r26732+nobinonly-0ubuntu1~umd1~karmic_amd64.deb) ...
Unpacking replacement xulrunner-1.9.1 ...
Processing triggers for desktop-file-utils ...
Processing triggers for menu ...
Setting up firefox-3.5-gnome-support (3.6.1~hg20100122r33535+nobinonly-0ubuntu1~umd2~karmic) ...
Setting up xulrunner-1.9.1 (1.9.1.8~hg20100122r26732+nobinonly-0ubuntu1~umd1~karmic) ...
update-alternatives: using /usr/bin/xulrunner-1.9.1 to provide /usr/bin/xulrunner (xulrunner) in auto mode.

Setting up firefox-branding (3.6.1~hg20100122r33535+nobinonly-0ubuntu1~umd2~karmic) ...
Setting up firefox (3.6.1~hg20100122r33535+nobinonly-0ubuntu1~umd2~karmic) ...
Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox
Please restart all running instances of firefox, or you will experience problems.

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for menu ...
:~$ 
```

Also did a test install of firefox-3.7

```
:~$ apt-cache policy firefox-3.7
firefox-3.7:
  Installed: (none)
  Candidate: 3.7~a1~hg20100123r37429+nobinonly-0ubuntu1~umd1~karmic
  Version table:
     3.7~a1~hg20100123r37429+nobinonly-0ubuntu1~umd1~karmic 0
        500 http://ppa.launchpad.net karmic/main Packages


:~$ sudo apt-get install firefox-3.7
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  firefox-3.7-branding xulrunner-1.9.3
Suggested packages:
  firefox-3.7-gnome-support
The following NEW packages will be installed
  firefox-3.7 firefox-3.7-branding xulrunner-1.9.3
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 12.2MB of archives.
After this operation, 36.4MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get: 1 http://ppa.launchpad.net karmic/main xulrunner-1.9.3 1.9.3~a1~hg20100123r37429+nobinonly-0ubuntu1~umd1~karmic [11.2MB]
Get: 2 http://ppa.launchpad.net karmic/main firefox-3.7-branding 3.7~a1~hg20100123r37429+nobinonly-0ubuntu1~umd1~karmic [143kB]                                                                               
Get: 3 http://ppa.launchpad.net karmic/main firefox-3.7 3.7~a1~hg20100123r37429+nobinonly-0ubuntu1~umd1~karmic [917kB]                                                                                        
Fetched 12.2MB in 23s (521kB/s)                                                                                                                                                                               
Selecting previously deselected package xulrunner-1.9.3.
(Reading database ... 194992 files and directories currently installed.)
Unpacking xulrunner-1.9.3 (from .../xulrunner-1.9.3_1.9.3~a1~hg20100123r37429+nobinonly-0ubuntu1~umd1~karmic_amd64.deb) ...
Selecting previously deselected package firefox-3.7-branding.
Unpacking firefox-3.7-branding (from .../firefox-3.7-branding_3.7~a1~hg20100123r37429+nobinonly-0ubuntu1~umd1~karmic_amd64.deb) ...
Selecting previously deselected package firefox-3.7.
Unpacking firefox-3.7 (from .../firefox-3.7_3.7~a1~hg20100123r37429+nobinonly-0ubuntu1~umd1~karmic_amd64.deb) ...
Processing triggers for desktop-file-utils ...
Processing triggers for menu ...
Setting up xulrunner-1.9.3 (1.9.3~a1~hg20100123r37429+nobinonly-0ubuntu1~umd1~karmic) ...

Setting up firefox-3.7-branding (3.7~a1~hg20100123r37429+nobinonly-0ubuntu1~umd1~karmic) ...
Setting up firefox-3.7 (3.7~a1~hg20100123r37429+nobinonly-0ubuntu1~umd1~karmic) ...
Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox-3.7
Please restart all running instances of firefox-3.7, or you will experience problems.

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for menu ...
:~$ 

```

---

### Post by SilverWave on 2010-01-25
```
sudo add-apt-repository ppa:mozillateam/firefox-stable
```[Packages in &#8220;Firefox Stable Channel Packages&#8221;]("https://launchpad.net/%7Emozillateam/+archive/firefox-stable/+packages")

firefox - 3.6+nobinonly-0ubuntu1~mfs~karmic1 (changesfile) asac 2010-01-24 Published Karmic Web

**I haven't had a chance to reset my system back to Official Firefox Defaults then test this yet so use at your own risk.**

---

### Post by jijoejv on 2010-01-26
> **SilverWave said:**
> ```
sudo add-apt-repository ppa:mozillateam/firefox-stable
```[Packages in “Firefox Stable Channel Packages”]("https://launchpad.net/%7Emozillateam/+archive/firefox-stable/+packages")

firefox - 3.6+nobinonly-0ubuntu1~mfs~karmic1 (changesfile) asac 2010-01-24 Published Karmic Web



Tried this  on top of stock FF 3.5. Same issue with font hinting as others here have noted. 

I already have the .fonts.conf changes in place, fontconfig reconfigured, etc. Merely switching between stock FF 3.5.7 and FF 3.6 can reproduce the issue.

---
Ubuntu 9.10 (karmic) x86_64
Gnome 2.28.1
Kernel 2.6.31-17-generic
Intel(R) Core(TM)2 Duo CPU, 8GB RAM
Intel(R) 82Q35 Express Integrated Graphics Controller (rev 02)

---

### Post by SilverWave on 2010-01-29
> **jijoejv said:**
> Tried this  on top of stock FF 3.5. Same issue with font hinting as others here have noted. 

I already have the .fonts.conf changes in place, fontconfig reconfigured, etc. Merely switching between stock FF 3.5.7 and FF 3.6 can reproduce the issue.

---
Ubuntu 9.10 (karmic) x86_64
Gnome 2.28.1
Kernel 2.6.31-17-generic
Intel(R) Core(TM)2 Duo CPU, 8GB RAM
Intel(R) 82Q35 Express Integrated Graphics Controller (rev 02)

As I wanted text to be **optimized for display quality** I set  ```
browser.display.auto_quality_min_font_size = 0

```**Much Much better!**

---

### Post by SilverWave on 2010-01-29
**browser.display.auto_quality_min_font_size**

> **Possible values and their effects**
 
  A non-negative integer, specifying device pixels. Text rendered at   this size or larger is optimized for display quality rather than display   speed. Default is 20. 
 **Caveats**
 
   
[LIST]
[*] Text in chrome (the UI) is always rendered with the   high-quality path.
[*] Web pages can override the effects of this  preference by  specifying the text-rendering CSS property.
[/LIST]
   **Recommended  settings**
 
  To use the highest quality display and legibility settings for all   rendered text, set this preference to 0. Conversely, setting this   preference to a very high number will cause Mozilla to use the fastest   rendering methods for all text. 
 [http://kb.mozillazine.org/Browser.display.auto_quality_min_font_size](http://kb.mozillazine.org/Browser.display.auto_quality_min_font_size)

As I wanted text to be **optimized for display quality** I set  ```
browser.display.auto_quality_min_font_size = 0

```**Much Much better!**

---

### Post by SilverWave on 2010-01-29
**Firefox3.6 via **Firefox Stable  Channel Packages [B]ppa

Gain access to the latest [mozillateam/firefox-stable]("https://launchpad.net/%7Emozillateam/+archive/firefox-stable") ppa.[/B] 
          ```
sudo add-apt-repository  ppa:mozillateam/firefox-stable
```   **Now install Firefox as below**  (or via the Synaptic Package    Manager).
          ```
sudo apt-get update
sudo apt-get install firefox
```Note on text quality:
As I wanted text to be **optimized for display quality** I set (about:config)
     ```
browser.display.auto_quality_min_font_size = 0  
```________________________________________

Tested successfully details below:

Reset back to Official Firefox 3.5...
```
silverwave@blue:~$ apt-cache policy firefox-3.5
firefox-3.5:
  Installed: 3.5.7+nobinonly-0ubuntu0.9.10.1
  Candidate: 3.5.7+nobinonly-0ubuntu0.9.10.1
  Version table:
 *** 3.5.7+nobinonly-0ubuntu0.9.10.1 0
        500 http://gb.archive.ubuntu.com karmic-updates/main Packages
        500 http://gb.archive.ubuntu.com karmic-security/main Packages
        100 /var/lib/dpkg/status
     3.5.3+build1+nobinonly-0ubuntu6 0
        500 http://gb.archive.ubuntu.com karmic/main Packages
silverwave@blue:~$ apt-cache policy firefox
firefox:
  Installed: 3.5.7+nobinonly-0ubuntu0.9.10.1
  Candidate: 3.5.7+nobinonly-0ubuntu0.9.10.1
  Version table:
 *** 3.5.7+nobinonly-0ubuntu0.9.10.1 0
        500 http://gb.archive.ubuntu.com karmic-updates/main Packages
        500 http://gb.archive.ubuntu.com karmic-security/main Packages
        100 /var/lib/dpkg/status
     3.5.3+build1+nobinonly-0ubuntu6 0
        500 http://gb.archive.ubuntu.com karmic/main Packages
silverwave@blue:~$ apt-cache policy xulrunner-1.9
xulrunner-1.9:
  Installed: (none)
  Candidate: (none)
  Version table:
silverwave@blue:~$ apt-cache policy xulrunner-1.9.1
xulrunner-1.9.1:
  Installed: 1.9.1.7+nobinonly-0ubuntu0.9.10.1
  Candidate: 1.9.1.7+nobinonly-0ubuntu0.9.10.1
  Version table:
 *** 1.9.1.7+nobinonly-0ubuntu0.9.10.1 0
        500 http://gb.archive.ubuntu.com karmic-updates/main Packages
        500 http://gb.archive.ubuntu.com karmic-security/main Packages
        100 /var/lib/dpkg/status
     1.9.1.3+build1+nobinonly-0ubuntu6 0
        500 http://gb.archive.ubuntu.com karmic/main Packages

```Added ppa...
```
silverwave@blue:~$ sudo add-apt-repository ppa:mozillateam/firefox-stable
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv 0AB215679C571D1C8325275B9BDB3D89CE49EC21
gpg: requesting key CE49EC21 from hkp server keyserver.ubuntu.com
gpg: key CE49EC21: public key "Launchpad PPA for Mozilla Team" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)

```Updated
```
silverwave@blue:~$ sudo apt-get update
Hit http://gb.archive.ubuntu.com karmic Release.gpg
...
Get: 1 http://ppa.launchpad.net karmic Release.gpg [307B]                    
...       
Hit http://packages.medibuntu.org karmic/free Packages                      
Hit http://packages.medibuntu.org karmic/non-free Packages
Get: 3 http://ppa.launchpad.net karmic/main Packages [4,023B]
Fetched 70.3kB in 0s (181kB/s)  
Reading package lists... Done

```Check apt-cache policy firefox...
```
silverwave@blue:~$ apt-cache policy firefox
firefox:
  Installed: 3.5.7+nobinonly-0ubuntu0.9.10.1
  Candidate: 3.6+nobinonly-0ubuntu1~mfs~karmic1
  Version table:
     3.6+nobinonly-0ubuntu1~mfs~karmic1 0
        500 http://ppa.launchpad.net karmic/main Packages
 *** 3.5.7+nobinonly-0ubuntu0.9.10.1 0
        500 http://gb.archive.ubuntu.com karmic-updates/main Packages
        500 http://gb.archive.ubuntu.com karmic-security/main Packages
        100 /var/lib/dpkg/status
     3.5.3+build1+nobinonly-0ubuntu6 0
        500 http://gb.archive.ubuntu.com karmic/main Packages

```sudo apt-get install firefox
```
silverwave@blue:~$ sudo apt-get install firefox
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  firefox-branding
Suggested packages:
  firefox-gnome-support
The following packages will be REMOVED
  firefox-3.5 firefox-3.5-branding
The following NEW packages will be installed
  firefox-branding
The following packages will be upgraded:
  firefox
1 upgraded, 1 newly installed, 2 to remove and 0 not upgraded.
Need to get 12.0MB/12.2MB of archives.
After this operation, 31.9MB of additional disk space will be used.
Do you want to continue [Y/n]? 
Get: 1 http://ppa.launchpad.net karmic/main firefox 3.6+nobinonly-0ubuntu1~mfs~karmic1 [12.0MB]
Fetched 9,523kB in 17s (552kB/s)                                                                                                                                                                              
dpkg: firefox-3.5-branding: dependency problems, but removing anyway as you requested:
 firefox-3.5 depends on firefox-3.5-branding | abrowser-3.5-branding; however:
  Package firefox-3.5-branding is to be removed.
  Package abrowser-3.5-branding is not installed.
 firefox depends on firefox-3.5-branding.
(Reading database ... 194871 files and directories currently installed.)
Removing firefox-3.5-branding ...
Processing triggers for desktop-file-utils ...
Selecting previously deselected package firefox-branding.
(Reading database ... 194853 files and directories currently installed.)
Unpacking firefox-branding (from .../firefox-branding_3.6+nobinonly-0ubuntu1~mfs~karmic1_amd64.deb) ...
Processing triggers for desktop-file-utils ...
dpkg: firefox-3.5: dependency problems, but removing anyway as you requested:
 firefox depends on firefox-3.5.
(Reading database ... 194871 files and directories currently installed.)
Removing firefox-3.5 ...
Processing triggers for menu ...
(Reading database ... 194782 files and directories currently installed.)
Preparing to replace firefox 3.5.7+nobinonly-0ubuntu0.9.10.1 (using .../firefox_3.6+nobinonly-0ubuntu1~mfs~karmic1_amd64.deb) ...
Unpacking replacement firefox ...
Processing triggers for menu ...
Setting up firefox-branding (3.6+nobinonly-0ubuntu1~mfs~karmic1) ...
Setting up firefox (3.6+nobinonly-0ubuntu1~mfs~karmic1) ...
Installing new version of config file /etc/apparmor.d/usr.bin.firefox ...
Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox
Please restart all running instances of firefox, or you will experience problems.

Processing triggers for menu ...

```

All working OK :D

---

### Post by foxy123 on 2010-01-31
I am having this problem with opening files from links after updating firefox from the stable repo:

```
/tmp/22-9-3.doc could not be opened, because the associated helper application does not exist. Change the association in your preferences.
```

Does anyone know anything about it?

I have rolled the update back and the error is gone. I wonder if it is a bug in firefox or something else?

---

### Post by zika on 2010-01-31
> **foxy123 said:**
> I am having this problem with opening files from links after updating firefox from the stable repo:

```
/tmp/22-9-3.doc could not be opened, because the associated helper application does not exist. Change the association in your preferences.
```

Does anyone know anything about it?Associate .doc with OO in FF.

---

### Post by foxy123 on 2010-01-31
> **zika said:**
> Associate .doc with OO in FF.

it is actually associated there. When I click on a link to a doc file I am presented with a choice: either to open it with OpenOffice Writer (default) or save on disk. If I choose the first, I've got the aforementioned error.

---

### Post by SilverWave on 2010-01-31
> **foxy123 said:**
> it is actually associated there. When I click on a link to a doc file I am presented with a choice: either to open it with OpenOffice Writer (default) or save on disk. If I choose the first, I've got the aforementioned error.

I am running 3.6 from stable:
> Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.2) Gecko/20100123 Ubuntu/9.10 (karmic) Firefox/3.6 - Build ID: 20100123214900I am not experiencing the issue you have reported.
I clicked on a gmail attachment a .doc and was presented with the same options as yourself.
Choosing OOO worked fine for me.

I would be tempted to try again. If the same issue presents then I would recommend creating a new profile and test again.

[EDIT]Just a thought... ensure that you close firefox before updating to 3.6.

---

### Post by SilverWave on 2010-02-06
[         ]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+sourcepub/954246/+listing-archive-extra")**FF3.7 Alpha 2!**

[[IMG]https://launchpad.net/@@/treeExpanded[/IMG]         [IMG]https://launchpad.net/@@/package-source[/IMG]         firefox-3.7 -  3.7~a2~hg20100206r37933+nobinonly-0ubuntu1~umd1~karmic       ]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+sourcepub/954246/+listing-archive-extra")                                  [(changes  file)]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+files/firefox-3.7_3.7%7Ea2%7Ehg20100206r37933+nobinonly-0ubuntu1%7Eumd1%7Ekarmic_source.changes")                                 [fta]("https://launchpad.net/%7Efta")                        8 hours ago     Published     Karmic     Web            [IMG]https://launchpad.net/@@/yes[/IMG]                             **Publishing details**

        
[LIST]
[*]       **Published**       8 hours ago
[/LIST]
                   **Changelog**

         firefox-3.7 (3.7~a2~hg20100206r37933+nobinonly-0ubuntu1~umd1~karmic) karmic; urgency=low

  [ Fabien Tassin ]
  * Mass update from 3.6 to 3.7
  * Drop libnkgnomevfs.so from firefox-3.7-gnome-support, it's already
    shippped in xulrunner-1.9.3-gnome-support (see bmo #512671)
    - update debian/firefox-3.7-gnome-support.install
  * Target the 'default' branch instead of tip
    - add debian/moz-rev.sh
    - update debian/mozclient/firefox-3.7.conf

  [ Micah Gersten ]
  * Add mesa-common-dev to build-depends after landing of configure test aka
    (bmo: 517566) which is for WebGL aka (bmo: 516213)
    - update debian/control
  * Refresh patch/install files after landing of (bmo: 507073) aka
    Don't build nsBrowserDirectoryProvider as a separate library
    - update debian/firefox-3.7.install
    - update debian/patches/bz515232_att399338_distro_locale_searchplugins.patch
  * Drop unnecessary patch to block updates since we disable updates in
    debian/rules
    - drop debian/patches/ubuntu_no_app_updates.patch
    - update debian/patches/series

  [ Jamie Strandboge ]
  * add AppArmor profile (disabled by default)
    - debian/firefox-3.7.dirs: add etc/apparmor.d/disable
    - add debian/firefox-3.7.preinst.in: disable the profile on new installs,
      installs on Ubuntu 9.04 and earlier (requires abstractions only found
      in 9.10 and higher), installs where the last modified profile is
      disabled and upgrades to this version
    - debian/firefox-3.7.postinst.in: reload profile
    - add debian/firefox-3.7.postrm.in: cleanup force-complain and disable
      directories
    - add debian/usr.bin.firefox.apparmor.in
    - add debian/README.Debian.in with note about AppArmor
    - debian/apport/firefox-3.7.py: add AppArmor information if the profile is
      not disabled
    - debian/rules: install profile and update subst_files
    - debian/control: have firefox-3.7 Depends on lsb-release (needed in
      preinst)

  [ Benjamin Drung <email address hidden> ]
  * Add metadata for mozilla-devscripts
    - update debian/control

  [ Fabien Tassin ]
 -- Fabien Tassin <email address hidden>   Sat, 06 Feb 2010 05:00:55 +0100            **Available diffs**

     
[LIST]
[*]                         3.7~a1~hg20100205r37915+nobinonly-0ubuntu1~umd1~karmic to  3.7~a2~hg20100206r37933+nobinonly-0ubuntu1~umd1~karmic (pending)
[/LIST]

---

### Post by SilverWave on 2010-02-06
Firefox 3.7 A2!

 **Gain access to the latest [ubuntu-mozilla-daily]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa?field.series_filter=") ppa.**
     ```
sudo add-apt-repository ppa:ubuntu-mozilla-daily 
```[I]Low safety, daily packages have not undergone any quality  assurance.
Sometimes very safe but sometimes may not work at all[/I].

**Now install Firefox as below** (or via the Synaptic Package  Manager).
     ```
sudo apt-get update
sudo apt-get install firefox-3.7 
```The new FF3.7 will be found under the name "Minefield 3.7 Web  Browser".

________________________________________

Check install Candidate
```
silverwave@blue:~$ apt-cache policy firefox-3.7
firefox-3.7:
  Installed: (none)
  Candidate: 3.7~a2~hg20100206r37933+nobinonly-0ubuntu1~umd1~karmic
  Version table:
     3.7~a2~hg20100206r37933+nobinonly-0ubuntu1~umd1~karmic 0
        500 http://ppa.launchpad.net karmic/main Packages
     3.7~a1~hg20100129r37619+nobinonly-0ubuntu1~umd1~karmic 0
        100 /var/lib/dpkg/status

```Install firefox-3.7
```
silverwave@blue:~$ sudo apt-get install firefox-3.7
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  firefox-3.7-branding xulrunner-1.9.3
Suggested packages:
  firefox-3.7-gnome-support
The following NEW packages will be installed
  firefox-3.7 firefox-3.7-branding xulrunner-1.9.3
0 upgraded, 3 newly installed, 0 to remove and 3 not upgraded.
Need to get 12.3MB of archives.
After this operation, 36.6MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get: 1 http://ppa.launchpad.net karmic/main xulrunner-1.9.3 1.9.3~a2~hg20100206r37933+nobinonly-0ubuntu1~umd1~karmic [11.2MB]
Get: 2 http://ppa.launchpad.net karmic/main firefox-3.7-branding 3.7~a2~hg20100206r37933+nobinonly-0ubuntu1~umd1~karmic [142kB]                                                                               
Get: 3 http://ppa.launchpad.net karmic/main firefox-3.7 3.7~a2~hg20100206r37933+nobinonly-0ubuntu1~umd1~karmic [917kB]                                                                                        
Fetched 9,414kB in 15s (616kB/s)                                                                                                                                                                              
Selecting previously deselected package xulrunner-1.9.3.
(Reading database ... 215629 files and directories currently installed.)
Unpacking xulrunner-1.9.3 (from .../xulrunner-1.9.3_1.9.3~a2~hg20100206r37933+nobinonly-0ubuntu1~umd1~karmic_amd64.deb) ...
Selecting previously deselected package firefox-3.7-branding.
Unpacking firefox-3.7-branding (from .../firefox-3.7-branding_3.7~a2~hg20100206r37933+nobinonly-0ubuntu1~umd1~karmic_amd64.deb) ...
Selecting previously deselected package firefox-3.7.
Unpacking firefox-3.7 (from .../firefox-3.7_3.7~a2~hg20100206r37933+nobinonly-0ubuntu1~umd1~karmic_amd64.deb) ...
Processing triggers for desktop-file-utils ...
Processing triggers for menu ...
Setting up xulrunner-1.9.3 (1.9.3~a2~hg20100206r37933+nobinonly-0ubuntu1~umd1~karmic) ...

Setting up firefox-3.7-branding (3.7~a2~hg20100206r37933+nobinonly-0ubuntu1~umd1~karmic) ...
Setting up firefox-3.7 (3.7~a2~hg20100206r37933+nobinonly-0ubuntu1~umd1~karmic) ...
Installing new version of config file /etc/apparmor.d/usr.bin.firefox-3.7 ...
Please restart all running instances of firefox-3.7, or you will experience problems.

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for menu ...
silverwave@blue:~$

```Check Installed/Candidate
```
silverwave@blue:~$ apt-cache policy firefox-3.7
firefox-3.7:
  Installed: 3.7~a2~hg20100206r37933+nobinonly-0ubuntu1~umd1~karmic
  Candidate: 3.7~a2~hg20100206r37933+nobinonly-0ubuntu1~umd1~karmic
  Version table:
 *** 3.7~a2~hg20100206r37933+nobinonly-0ubuntu1~umd1~karmic 0
        500 http://ppa.launchpad.net karmic/main Packages
        100 /var/lib/dpkg/status
silverwave@blue:~$ 

```Check firefox (I don't want to use the ff3.6.2 daily so I will now disable the UMD ppa).
```

silverwave@blue:~$ apt-cache policy firefox
firefox:
  Installed: 3.6+nobinonly-0ubuntu1~mfs~karmic1
  Candidate: 3.6.2~hg20100205r33566+nobinonly-0ubuntu1~umd1~karmic
  Version table:
     3.6.2~hg20100205r33566+nobinonly-0ubuntu1~umd1~karmic 0
        500 http://ppa.launchpad.net karmic/main Packages
 *** 3.6+nobinonly-0ubuntu1~mfs~karmic1 0
        500 http://ppa.launchpad.net karmic/main Packages
        100 /var/lib/dpkg/status
     3.5.7+nobinonly-0ubuntu0.9.10.1 0
        500 http://gb.archive.ubuntu.com karmic-updates/main Packages
        500 http://gb.archive.ubuntu.com karmic-security/main Packages
     3.5.3+build1+nobinonly-0ubuntu6 0
        500 http://gb.archive.ubuntu.com karmic/main Packages

```All working great :) 3.7 installs in its own folder as expected.

Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.3a2pre) Gecko/20100206 Ubuntu/9.10 (karmic) Minefield/3.7a2pre

---

### Post by foxy123 on 2010-02-06
> **SilverWave said:**
> I am running 3.6 from stable:
I am not experiencing the issue you have reported.
I clicked on a gmail attachment a .doc and was presented with the same options as yourself.
Choosing OOO worked fine for me.

I would be tempted to try again. If the same issue presents then I would recommend creating a new profile and test again.

[EDIT]Just a thought... ensure that you close firefox before updating to 3.6.

tried to reinstall and use a new profile. still the same error :(

---

### Post by SilverWave on 2010-02-06
> **foxy123 said:**
> tried to reinstall and use a new profile. still the same error :(

Hmm how odd :(
How about 3.7a2?
It installs separately - I don't think using an Alpha2 is usually a good idea... but for trouble shooting in this case, I would give it a go. Once installed check if you are experiencing the same issues.

Also have a look at this:
[The associated helper application does not exist]("http://kb.mozillazine.org/The_associated_helper_application_does_not_exist")

Details:
Are you using Karmic 64bit?
Are you using gnome?

[EDIT]Final thought - Open firefox from a root terminal and see if that works... just to rule out permission issues.

---

### Post by SilverWave on 2010-02-10
Interesting :)

> **[Mozilla Developer Preview (Gecko  1.9.3a1) available for download]("http://developer.mozilla.org/devnews/index.php/2010/02/10/mozilla-developer-preview-gecko-1-9-3a1-available-for-download/")**

                                   A Mozilla Developer Preview of improvements in the Gecko  layout engine is now available for download.  This is a pre-release  version of the Gecko 1.9.3 platform, which forms the core of rich  Internet applications such as Firefox. Please note that this release is  intended for developers and testers only.Update:
I have updated to:
Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.3a2pre) Gecko/20100207 Ubuntu/9.10 (karmic) Minefield/3.7a2pre
I don't see any of the changes mentioned... so may be they are referring to a separate dev build?

---

### Post by urd on 2010-02-12
i have a problem, since i tried to install firefox 3.6 i can't use flash, pages like youtube don't work ... what can i do?? .. i have karmic(wubi)

thanks

---

### Post by ron999 on 2010-02-12
Hi
Check that you have got Adobe Flash Player installed and enabled.
Look in Firefox > Tools > Add-ons > Plugins
It will be listed as 'Shockwave Flash'.

---

### Post by foxy123 on 2010-02-13
> **SilverWave said:**
> Hmm how odd :(
How about 3.7a2?
It installs separately - I don't think using an Alpha2 is usually a good idea... but for trouble shooting in this case, I would give it a go. Once installed check if you are experiencing the same issues.

Also have a look at this:
[The associated helper application does not exist]("http://kb.mozillazine.org/The_associated_helper_application_does_not_exist")

Details:
Are you using Karmic 64bit?
Are you using gnome?

[EDIT]Final thought - Open firefox from a root terminal and see if that works... just to rule out permission issues.

I have enabled the daily repository and updated Firefox from there. The problem exists there as well. However what I have discovered is that I have this error only on a particular site. Everywhere else it works fine (at lease on the version of Firefox fom the daily repo). However I do not have the error with the standard version of Firefox. So I do not know what is going on. It's a pity but I guess I will have to stick to the standard 3.5 version.

---

### Post by SilverWave on 2010-02-13
> **foxy123 said:**
> ... I have discovered is that I have this error only on a particular site. Everywhere else it works fine ...
Well at least you have narrowed the problem down.
If its only one site is it a deal breaker?
If its only an occasional problem perhaps you could, as a work around, download the doc then open it as normal?

I guess its a cost benefit thing that only you can decide on.

Still a very odd issue...

Note: In my first post are instructions on how to install chromium as that has a different architecture you could run it side by side with firefox and see it it has any issues with this site...

---

### Post by SilverWave on 2010-02-23
Updated to:
  Candidate: 3.6+nobinonly-0ubuntu4~mfs~karmic1                                     (2010-02-18 )

All working fine so far.

```
:~$ apt-cache policy firefox
firefox:
  Installed: 3.6+nobinonly-0ubuntu1~mfs~karmic1
  Candidate: 3.6+nobinonly-0ubuntu4~mfs~karmic1
  Version table:
     3.6+nobinonly-0ubuntu4~mfs~karmic1 0
        500 http://ppa.launchpad.net karmic/main Packages
 *** 3.6+nobinonly-0ubuntu1~mfs~karmic1 0
        100 /var/lib/dpkg/status
     3.5.8+build1+nobinonly-0ubuntu0.9.10.1 0
        500 http://gb.archive.ubuntu.com karmic-updates/main Packages
        500 http://gb.archive.ubuntu.com karmic-security/main Packages
     3.5.3+build1+nobinonly-0ubuntu6 0
        500 http://gb.archive.ubuntu.com karmic/main Packages

```

---

### Post by SilverWave on 2010-03-01
Changes for the versions:
3.6+nobinonly-0ubuntu4~mfs~karmic1
3.6+nobinonly-0ubuntu5~mfs~karmic1

> **Publishing details**

        
[LIST]
[*]       **Published**       13 hours ago
[/LIST]
                   **Changelog**

         firefox (3.6+nobinonly-0ubuntu5~mfs~karmic1) karmic; urgency=low

  * Backport to karmic -- no source changes

  [ Micah Gersten <email address hidden> ]
  * fix LP: [#514108]("https://launchpad.net/bugs/514108") - Cookie Accept Dialog Not Shown on Firefox 3.6; install chrome/comm.* libraries
    - update debian/rules
  * fix LP: [#525181]("https://launchpad.net/bugs/525181") - "Make a Support Request to the Ubuntu Community" bookmark
    woefully out of date; update bookmark
    - update debian/patches/ubuntu_bookmarks.patch

  [ Felix Geyer <email address hidden> ]
  * fix LP: [#396786]("https://launchpad.net/bugs/396786") - Default theme missing in Firefox 3.6
    - update debian/firefox.install

  [ Alexander Sack <email address hidden> ]
  * use preference way to set yahoo search code 'chr-ubuntu-os' rather
    than patching source
    - update debian/firefox.js
    - delete debian/patches/ubuntu_codes_yahoo.patch
    - update debian/patches/series
 -- Micah Gersten <email address hidden>   Sun, 28 Feb 2010 20:09:27 -0600

---

### Post by SilverWave on 2010-03-01
firefox-3.7 a3 available! 

> **Publishing details**

        
[LIST]
[*]       **Published**       11 hours ago
[/LIST]
                   **Changelog**

         firefox-3.7 (3.7~a3~hg20100301r38798+nobinonly-0ubuntu1~umd1~karmic) karmic; urgency=low

  [ Fabien Tassin ]
  * Mass update from 3.6 to 3.7
  * Drop libnkgnomevfs.so from firefox-3.7-gnome-support, it's already
    shippped in xulrunner-1.9.3-gnome-support (see bmo #512671)
    - update debian/firefox-3.7-gnome-support.install
  * Target the 'default' branch instead of tip
    - add debian/moz-rev.sh
    - update debian/mozclient/firefox-3.7.conf

  [ Micah Gersten ]
  * Add mesa-common-dev to build-depends after landing of configure test aka
    (bmo: 517566) which is for WebGL aka (bmo: 516213)
    - update debian/control
  * Refresh patch/install files after landing of (bmo: 507073) aka
    Don't build nsBrowserDirectoryProvider as a separate library
    - update debian/firefox-3.7.install
    - update debian/patches/bz515232_att399338_distro_locale_searchplugins.patch
  * Drop unnecessary patch to block updates since we disable updates in
    debian/rules
    - drop debian/patches/ubuntu_no_app_updates.patch
    - update debian/patches/series

  [ Jamie Strandboge ]
  * add AppArmor profile (disabled by default)
    - debian/firefox-3.7.dirs: add etc/apparmor.d/disable
    - add debian/firefox-3.7.preinst.in: disable the profile on new installs,
      installs on Ubuntu 9.04 and earlier (requires abstractions only found
      in 9.10 and higher), installs where the last modified profile is
      disabled and upgrades to this version
    - debian/firefox-3.7.postinst.in: reload profile
    - add debian/firefox-3.7.postrm.in: cleanup force-complain and disable
      directories
    - add debian/usr.bin.firefox.apparmor.in
    - add debian/README.Debian.in with note about AppArmor
    - debian/apport/firefox-3.7.py: add AppArmor information if the profile is
      not disabled
    - debian/rules: install profile and update subst_files
    - debian/control: have firefox-3.7 Depends on lsb-release (needed in
      preinst)

  [ Benjamin Drung <email address hidden> ]
  * Add metadata for mozilla-devscripts
    - update debian/control

  [ Fabien Tassin ]
 -- Fabien Tassin <email address hidden>   Mon, 01 Mar 2010 05:00:55 +0100

---

### Post by zika on 2010-03-01
What do You make of this```
~$ firefox-3.7
Could not find compatible GRE between version 1.9.3a2pre and 1.9.3a2pre.
~$ 
```after months of successful usage...

---

### Post by SilverWave on 2010-03-01
> **SilverWave said:**
> firefox-3.7 a3 available!

XULRunner1.9.3
Changes for the versions:
1.9.3~a2~hg20100207r37958+nobinonly-0ubuntu1~umd1~karmic
1.9.3~a3~hg20100301r38798+nobinonly-0ubuntu1~umd1~karmic

firefox-3.7
Changes for the versions:
3.7~a2~hg20100207r37958+nobinonly-0ubuntu1~umd1~karmic
3.7~a2~hg20100227r38786+nobinonly-0ubuntu1~umd1~karmic

Firefox branding 
Changes for the versions:
3.7~a2~hg20100207r37958+nobinonly-0ubuntu1~umd1~karmic
3.7~a2~hg20100227r38786+nobinonly-0ubuntu1~umd1~karmic

---

### Post by SilverWave on 2010-03-01
> **SilverWave said:**
> XULRunner1.9.3
Changes for the versions:
1.9.3~a2~hg20100207r37958+nobinonly-0ubuntu1~umd1~karmic
1.9.3~a3~hg20100301r38798+nobinonly-0ubuntu1~umd1~karmic

firefox-3.7
Changes for the versions:
3.7~a2~hg20100207r37958+nobinonly-0ubuntu1~umd1~karmic
3.7~a2~hg20100227r38786+nobinonly-0ubuntu1~umd1~karmic

Firefox branding 
Changes for the versions:
3.7~a2~hg20100207r37958+nobinonly-0ubuntu1~umd1~karmic
3.7~a2~hg20100227r38786+nobinonly-0ubuntu1~umd1~karmic


OK that did not allow me to run firefox3.7!

I have uninstalled reinstalled to no avail.

Maybe a bad build?

---

### Post by dot2kode on 2010-03-01
Thanks works great...I just did it on an EeePC 1005HA with Ubuntu Netbook remix (Karmic)...

p.s.  I love the ```
add-apt-repository
``` ;)

---

### Post by zika on 2010-03-02
> **SilverWave said:**
> OK that did not allow me to run firefox3.7!

I have uninstalled reinstalled to no avail.

Maybe a bad build?Upgrade fixed that, today. Flash still doesn't work in 3.7.

---

### Post by SilverWave on 2010-03-03
Installed firefox-3.7a3 from umd and its working fine again :-)
```
 sudo apt-get install firefox-3.7

```
Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.3a3pre) Gecko/20100303  Ubuntu/9.10 (karmic) Minefield/3.7a3pre

(The previous issue looks to have been that only xulrunner was at version ~a3. Now both firefox and xulrunner are).

```
:~$ apt-cache policy firefox-3.7
firefox-3.7:
  Installed: (none)
  Candidate: 3.7~a3~hg20100303r38865+nobinonly-0ubuntu1~umd1~karmic
  Version table:
     3.7~a3~hg20100303r38865+nobinonly-0ubuntu1~umd1~karmic 0
        500 http://ppa.launchpad.net karmic/main Packages



:~$ apt-cache policy xulrunner-1.9.3
xulrunner-1.9.3:
  Installed: (none)
  Candidate: 1.9.3~a3~hg20100303r38865+nobinonly-0ubuntu1~umd1~karmic
  Version table:
     1.9.3~a3~hg20100303r38865+nobinonly-0ubuntu1~umd1~karmic 0
        500 http://ppa.launchpad.net karmic/main Packages

```> firefox-3.7 (3.7~a3~hg20100303r38865+nobinonly-0ubuntu1~umd1~karmic) karmic; urgency=low

  [ Fabien Tassin <email address hidden> ]
  * Mass update from 3.6 to 3.7
  * Drop libnkgnomevfs.so from firefox-3.7-gnome-support, it's already
    shippped in xulrunner-1.9.3-gnome-support (see bmo #512671)
    - update debian/firefox-3.7-gnome-support.install
  * Target the 'default' branch instead of tip
    - add debian/moz-rev.sh
    - update debian/mozclient/firefox-3.7.conf

  ...

  [ Fabien Tassin ]
 -- Fabien Tassin <email address hidden>   Wed, 03 Mar 2010 05:00:38 +0100
________________________________________

**Gain access to the latest [ubuntu-mozilla-daily]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa?field.series_filter=") ppa.**
     ```
sudo add-apt-repository ppa:ubuntu-mozilla-daily
```

---

### Post by SilverWave on 2010-03-11
Updated from Stable 3.6 to Daily 3.6.2 :D

Installed: 3.6.2~hg20100310r33728+nobinonly-0ubuntu1~umd1~karmic

 Installed: 1.9.1.9~hg20100310r26839+nobinonly-0ubuntu1~umd1~karmic

Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.2.2pre) Gecko/20100311 Ubuntu/9.10 (karmic) Namoroka/3.6.2pre - Build ID: 20100311102157

```
sil@blue:~$ apt-cache policy firefox
firefox:
  Installed: 3.6.2~hg20100310r33728+nobinonly-0ubuntu1~umd1~karmic
  Candidate: 3.6.2~hg20100310r33728+nobinonly-0ubuntu1~umd1~karmic
  Version table:
 *** 3.6.2~hg20100310r33728+nobinonly-0ubuntu1~umd1~karmic 0
        100 /var/lib/dpkg/status
     3.5.8+build1+nobinonly-0ubuntu0.9.10.1 0
        500 http://gb.archive.ubuntu.com karmic-updates/main Packages
        500 http://gb.archive.ubuntu.com karmic-security/main Packages
     3.5.3+build1+nobinonly-0ubuntu6 0
        500 http://gb.archive.ubuntu.com karmic/main Packages



sil@blue:~$ apt-cache policy xulrunner-1.9.1
xulrunner-1.9.1:
  Installed: 1.9.1.9~hg20100310r26839+nobinonly-0ubuntu1~umd1~karmic
  Candidate: 1.9.1.9~hg20100310r26839+nobinonly-0ubuntu1~umd1~karmic
  Version table:
 *** 1.9.1.9~hg20100310r26839+nobinonly-0ubuntu1~umd1~karmic 0
        100 /var/lib/dpkg/status
     1.9.1.8+build1+nobinonly-0ubuntu0.9.10.1 0
        500 http://gb.archive.ubuntu.com karmic-updates/main Packages
        500 http://gb.archive.ubuntu.com karmic-security/main Packages
     1.9.1.3+build1+nobinonly-0ubuntu6 0
        500 http://gb.archive.ubuntu.com karmic/main Packages
sil@blue:~$ 
```

Looks OK ATM .

---

### Post by SilverWave on 2010-03-16
Firefox 3.6.3 in UMD

> Changes for the versions:
3.6.2~hg20100314r33734+nobinonly-0ubuntu1~umd1~karmic
3.6.3~hg20100315r33738+nobinonly-0ubuntu1~umd1~karmic


XULRunner
Changes for the versions:
1.9.1.9~hg20100310r26839+nobinonly-0ubuntu1~umd1~karmic
1.9.1.10~hg20100315r26845+nobinonly-0ubuntu1~umd1~karmic

---

### Post by SilverWave on 2010-03-16
Odd firefox-3.7a4 is in UMD as:

> firefox-3.7 - 3.7~a4~hg20100316r39479+nobinonly-0ubuntu1~umd1~karmic but I dont see it...

> apt-cache policy firefox-3.7
firefox-3.7:
  Installed: (none)
  Candidate: 3.7~a3~hg20100304r38917+nobinonly-0ubuntu1~umd1~karmic
  Version table:
     3.7~a3~hg20100304r38917+nobinonly-0ubuntu1~umd1~karmic 0
        500 [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages

---

### Post by SilverWave on 2010-03-22
Time to upgrade to 3.6.3 as there is a **Zero Day Exploit in 3.6!** and it wont be fixed until the 30th.

Details Here:
[Firefox 3.6 contains the zero-day vulnerability]("http://www.computerworld.com/s/article/9173874/German_government_urges_users_to_scrap_Firefox_3.6")

---

### Post by SilverWave on 2010-03-22
I'm on Lucid 10.04 Beta 1. 

I did this:

**Gain access to the latest [ubuntu-mozilla-daily]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa?field.series_filter=") ppa.**
     ```
sudo add-apt-repository ppa:ubuntu-mozilla-daily 
```

**Now install Firefox as below** (or via the Synaptic Package    Manager).
     ```
sudo apt-get update
sudo apt-get install firefox 
```
__________________

Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.2.3pre) Gecko/20100316  Ubuntu/10.04 (lucid) Namoroka/3.6.3pre - Build ID: 20100316073122

---

### Post by SilverWave on 2010-04-03
3.6.3~hg20100401r33777+nobinonly-0ubuntu1~umd1
3.6.4~hg20100402r33789+nobinonly-0ubuntu1~umd1

Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.2.4pre) Gecko/20100403 Ubuntu/10.04 (lucid) Namoroka/3.6.4pre - Build ID: 20100403043550

---

### Post by SilverWave on 2010-04-15
Nothing new has been built successfully at the ubuntu-mozilla-daily PPA for a few days.

I think they are adjusting to changes upstream at Mozilla but I cant find any info one way or the other.

I'll update when I have more information.

>      **Latest updates**

                  
[LIST]
[*]           **xulrunner-1.9.3**                        17 hours             ago           
          Failed to build:                        [amd64]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+build/1693389")             [i386]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+build/1693390")             [lpia]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+build/1693391")           
[*]           **firefox-3.7**                        17 hours             ago           
          Failed to build:                        [amd64]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+build/1693400")             [i386]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+build/1693401")             [lpia]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+build/1693402")           
[*]           **xulrunner-1.9.2**                        17 hours             ago           
          Failed to build:                        [amd64]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+build/1693411")             [i386]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+build/1693412")             [lpia]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+build/1693413")           
[*]           **firefox**                        17 hours             ago           
          Failed to build:                        [amd64]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+build/1693422")             [i386]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+build/1693423")             [lpia]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+build/1693424")           
[*]           **mozilla-devscripts**                        17 hours             ago           
          Successfully built
[/LIST]
          


---

### Post by SilverWave on 2010-04-16
> [        firefox -  3.6.5~hg20100414r34076+nobinonly-0ubuntu1~umd2~karmic       ]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+sourcepub/1079925/+listing-archive-extra")                                  [(changes  file)]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+files/firefox_3.6.5%7Ehg20100414r34076+nobinonly-0ubuntu1%7Eumd2%7Ekarmic_source.changes")                                 [fta]("https://launchpad.net/%7Efta")                        20 hours ago     Published     Karmic     Web            [IMG]https://launchpad.net/@@/yes[/IMG]                             **Publishing details**

        
[LIST]
[*]       **Published**       20 hours ago
[/LIST]
                   **Changelog**

         firefox (3.6.5~hg20100414r34076+nobinonly-0ubuntu1~umd2~karmic) karmic; urgency=low

  * New upstream release v3.6.4 (FIREFOX_3_6_4_BUILD1)

  [ Micah Gersten <email address hidden> ]
  * Rebase patch after upstream landing of Lorentz branch
    - update debian/patches/bz460917_att350845_reload_new_plugins.patch
  * Drop patch after upstream landing of (bmo: 544481) aka
    Build fails on Ubuntu Lucid Lynx using 'dash' shell
    - drop debian/patches/fix-build-glitch.patch
    - update debian/patches/series

  [ Jamie Strandboge <email address hidden> ]
  * AppArmor:
    - add read access to /etc/xul-ext/**, now needed by adblock

  [ Chris Coulson <email address hidden> ]
  * Create checksums for NSS libraries to make FIPS mode work (LP: [#559881]("https://launchpad.net/bugs/559881"))
    - update debian/rules

  [ Fabien Tassin ]
 -- Fabien Tassin <email address hidden>   Fri, 16 Apr 2010 05:28:50 +0200


Installed: 3.6.5~hg20100414r34076+nobinonly-0ubuntu1~umd2

Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.2.5pre) Gecko/20100416 Ubuntu/10.04 (lucid) Namoroka/3.6.5pre - Build ID: 20100416142024

---

### Post by SilverWave on 2010-04-24
Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.3a5pre) Gecko/20100422 Ubuntu/10.04 (lucid) Minefield/3.7a5pre

Lucid


[LIST]
[*]       [firefox_3.6.5~hg20100423r34115+nobinonly-0ubuntu1~umd1_amd64.deb]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+files/firefox_3.6.5%7Ehg20100423r34115+nobinonly-0ubuntu1%7Eumd1_amd64.deb")          (12.0 MiB)
[*]       [firefox_3.6.5~hg20100423r34115+nobinonly-0ubuntu1~umd1_i386.deb]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+files/firefox_3.6.5%7Ehg20100423r34115+nobinonly-0ubuntu1%7Eumd1_i386.deb")          (10.7 MiB)
[/LIST]


Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.2.5pre) Gecko/20100423 Ubuntu/10.04 (lucid) Namoroka/3.6.5pre - Build ID: 20100423041529

Lucid


[LIST]
[*]       [firefox-3.7_3.7~a5~hg20100424r41235+nobinonly-0ubuntu1~umd1_amd64.deb]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+files/firefox-3.7_3.7%7Ea5%7Ehg20100424r41235+nobinonly-0ubuntu1%7Eumd1_amd64.deb")          (874.1 KiB)
[*]       [firefox-3.7_3.7~a5~hg20100424r41235+nobinonly-0ubuntu1~umd1_i386.deb]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+files/firefox-3.7_3.7%7Ea5%7Ehg20100424r41235+nobinonly-0ubuntu1%7Eumd1_i386.deb")          (858.8 KiB)
[/LIST]
Full details here:

[PPA for Ubuntu Mozilla Daily Build Team]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/?field.series_filter=")

---

### Post by SilverWave on 2010-04-27
> Firefox-3.6  - One Daily A Month
 One daily a month from ubuntu-mozilla-daily.
 The latest firefox without the update hassle
 $ sudo add-apt-repository ppa:silverwave/one-daily-a-month-0
**I have created a PPA so that I have a reasonably  up-to-date Firefox but don't get overwhelmed with updates**.

[https://launchpad.net/~silverwave/+archive/one-daily-a-month-0]("https://launchpad.net/%7Esilverwave/+archive/one-daily-a-month-0")

Firefox 3.6 and xulrunner will be the only Packages in this PPA so you  wont update other stuff in error.

>                  
[IMG]https://launchpad.net/@@/package-source[/IMG]  firefox                                                3.6.5~hg20100427r34130+nobinonly-0ubuntu1~umd1                                                                   [Fabien Tassin]("https://launchpad.net/%7Efta")                                       (1 hour ago)
[IMG]https://launchpad.net/@@/package-source[/IMG]                  xulrunner-1.9.2                                                1.9.2.5~hg20100427r34130+nobinonly-0ubuntu1~umd1                                                                   [Fabien Tassin]("https://launchpad.net/%7Efta")                                       (1 hour ago)                                   Its for Lucid users - I have tested the 64bit version  OK.

Same idea for Firefox-3.7
> 
Firefox-3.7 - One Daily A Month
 One daily a month from ubuntu-mozilla-daily.
 The latest firefox without the update hassle
 $ sudo add-apt-repository ppa:silverwave/one-daily-a-month-1

I will be updating the packages on the 1st of each month.
(unless there is a security issue etc.).

Note:
[I]Low safety, daily packages have not undergone any quality  assurance.
Sometimes very safe but sometimes may not work at all[/I].

Note2:
[I]The packages are copied direct from ubuntu-mozilla-daily.
  
[/I] [I]I have tested the packages a virtual machine running Lucid 10.04, 32bit and 64bit.
Both Firefox-3.6 and 3.7 install and open with no problem.[/I]

---

### Post by SilverWave on 2010-04-27
I Have added PPA's for Karmic Users as well.

> Firefox-3.6 Karmic - One Daily A Month
 One daily a month from ubuntu-mozilla-daily.
 The latest firefox without the update hassle
 $ sudo add-apt-repository ppa:silverwave/one-daily-a-month-2
>       Firefox-3.7 Karmic - One Daily A Month
 One daily a month from ubuntu-mozilla-daily.
 The latest firefox without the update hassle
 $ sudo add-apt-repository ppa:silverwave/one-daily-a-month-3

Note:
[I]Low safety, daily packages have not undergone any quality  assurance.
Sometimes very safe but sometimes may not work at all[/I].

Note2:
[I]The packages are copied direct from ubuntu-mozilla-daily.

[/I] [I]I have tested the packages a virtual machine running Karmic 9.04, 32bit and 64bit.
Both Firefox-3.6 and 3.7 install and open with no problem.


[/I]

---

### Post by SilverWave on 2010-04-28
I have given it some thought and will support both Lucid and Karmic with  separate PPA's for Firefox-3.6 and 3.7.

[https://launchpad.net/~silverwave]("https://launchpad.net/%7Esilverwave")

Details follow:

> Firefox-3.6 - One Daily A Month -  Lucid
 One daily a month from ubuntu-mozilla-daily.
 The latest firefox without the update hassle
 $ sudo add-apt-repository ppa:silverwave/one-daily-a-month-0


Firefox-3.7  - One Daily A Month - Lucid
 One daily a month from ubuntu-mozilla-daily.
 The latest firefox without the update hassle.
 $ sudo add-apt-repository ppa:silverwave/one-daily-a-month-1[I]I  have tested the packages in a virtual machine running Lucid  10.04, 32bit  and 64bit.
Both Firefox-3.6 and 3.7 install and open with no problem.[/I]

> Firefox-3.6  - One Daily A Month - Karmic
 One daily a month from ubuntu-mozilla-daily.
 The latest firefox without the update hassle.
 $ sudo add-apt-repository ppa:silverwave/one-daily-a-month-2


Firefox-3.7  - One Daily A Month - Karmic
 One daily a month from ubuntu-mozilla-daily.
 The latest firefox without the update hassle.
 $ sudo add-apt-repository ppa:silverwave/one-daily-a-month-3[I]I  have tested the packages in a virtual machine running Karmic 9.10,  32bit  and 64bit.
Both Firefox-3.6 and 3.7 install and open with no problem.[/I]

---

### Post by teohhanhui on 2010-04-30
It's rather unfortunate that there are no ppa's for alpha/beta releases. I'm not willing to put up with the frequent updates and possible problems of daily builds, but stable releases are at the opposite end of the spectrum.

Sometimes beta releases add features that are highly sought after without sacrificing much stability. Case in point: OOPP in 3.6.4 beta.

---

### Post by SilverWave on 2010-04-30
> **teohhanhui said:**
> It's rather unfortunate that there are no ppa's for alpha/beta releases. I'm not willing to put up with the frequent updates and possible problems of daily builds, but stable releases are at the opposite end of the spectrum.

Sometimes beta releases add features that are highly sought after without sacrificing much stability. Case in point: OOPP in 3.6.4 beta.

Yes there is a little lull in the building of dailies atm I would imagine that will be related to the release of Lucid :-)

But on your point - I agree and that is why I have created the one-daily-a-month line of ppa's.

I have not had one "problem" daily from umd and have been using them for over a year iirc.

My main issue is that for my purposes, 31 updates a month is overkill. So my proposed schedule is 1 a month.

Also having lots of different packages in the same ppa is also problematic so the 4 one-daily-a-month ppa's will each only have one firefox package in each.
e.g.
ODAM0 (Firefox-3.6 *Lucid) ppa:silverwave/one-daily-a-month-0
ODAM1 (Firefox-3.7 *Lucid) ppa:silverwave/one-daily-a-month-1
ODAM2 (Firefox-3.6 Karmic) ppa:silverwave/one-daily-a-month-2
ODAM3 (Firefox-3.7 Karmic) ppa:silverwave/one-daily-a-month-3

Although I make no guarantees, the plan is to at least test each in a vm.

---

### Post by teohhanhui on 2010-04-30
> **SilverWave said:**
> Yes there is a little lull in the building of dailies atm I would imagine that will be related to the release of Lucid :-)

But on your point - I agree and that is why I have created the one-daily-a-month line of ppa's.

I have not had one "problem" daily from umd and have been using them for over a year iirc.

My main issue is that for my purposes, 31 updates a month is overkill. So my proposed schedule is 1 a month.

Also having lots of different packages in the same ppa is also problematic so the 4 one-daily-a-month ppa's will each only have one firefox package in each.
e.g.
ODAM0 firefox-3.6 *Lucid
ODAM1 firefox-3.7 *Lucid
ODAM2 firefox-3.6 Karmic
ODAM3 firefox-3.7 Karmic

Although I make no guarantees, the plan is to at least test each in a vm.
Unlike the daily builds you pick which may or may not be significant, beta builds such as 3.6.4 promise a more meaningful rollup of fixes/features/enhancements while maintaining compatibility. And aren't beta tests meant to reach out to a wider audience, many of whom may not be comfortable with the idea/willing to deal with the hassles of running nightlies? I would argue that in this case it's actually in Mozilla's and its users' best interests for there to be a PPA for beta builds.

---

### Post by SilverWave on 2010-04-30
> **teohhanhui said:**
> Unlike the daily builds you pick which may or may not be significant, beta builds such as 3.6.4 promise a more meaningful rollup of fixes/features/enhancements while maintaining compatibility. And aren't beta tests meant to reach out to a wider audience, many of whom may not be comfortable with the idea/willing to deal with the hassles of running nightlies? I would argue that in this case it's actually in Mozilla's and its users' best interests for there to be a PPA for beta builds.

You have a valid point, I wonder what the reason could be that this has not already been implemented...

The first that comes to mind is number of users, 12 million, is for Mozilla, pretty small beer I would imagine.

Particularly when you consider what smaller percentage would want to install the beta, if it was say 1% that's only 120,000 users.

The dailies are in my experience, a pleasant surprise tbh, as I say I have not had an issue and what's the worst that can happen?

It wouldn't be the end of the world if I had to install the stable FF, if there was a problem, and use that for a day or two.

I do take a copy of my ff profile just to be safe, but that's about it.

---

### Post by Sandiep on 2010-04-30
[COLOR=Magenta]**To run a script "icecream.sh" can it be written as "/bin/bas icecream.bash"?**[/COLOR]

---

### Post by SilverWave on 2010-05-01
> **Sandiep said:**
> [COLOR=Magenta]**To run a script "icecream.sh" can it be written as "/bin/bas icecream.bash"?**[/COLOR]

If I understand your question correctly, no.

Using the terminal, you could cd to the directory containing the script then issue the following command:

```
./my-script.sh
```Note the script will need to be executable:

```
chmod +x my-script.sh
```Also if its a bash script the first line in the script needs to read:

```
#!/bin/bash
```

---

### Post by teohhanhui on 2010-05-01
For anyone looking for Firefox 3.6.4 beta: [https://launchpad.net/~ubuntu-mozilla-security/+archive/ppa/](https://launchpad.net/~ubuntu-mozilla-security/+archive/ppa/)

---

### Post by SilverWave on 2010-05-01
> **teohhanhui said:**
> For anyone looking for Firefox 3.6.4 beta: [https://launchpad.net/~ubuntu-mozilla-security/+archive/ppa/]("https://launchpad.net/%7Eubuntu-mozilla-security/+archive/ppa/")

Nice :-)

Interesting, usually they put a package there for testing before making it the next official release...

Have you a link to the information indicating that this is a beta?

Its marked as 0.10.04.2... hmmm

> firefox (3.6.4+build1+nobinonly-0ubuntu0.10.04.2) lucid-security; urgency=low

  * New upstream release v3.6.4 (FIREFOX_3_6_4_BUILD1)
    - see USN-930-1
    - fix LP: [#469752]("https://launchpad.net/bugs/469752") - KDE/Gnome startup notification not disappearing
      when app window is up

  [ Micah Gersten <email address hidden> ]
  * Rebase patch after upstream landing of Lorentz branch
    - update debian/patches/bz460917_att350845_reload_new_plugins.patch
  * Drop patch after upstream landing of (bmo: 544481) aka
    Build fails on Ubuntu Lucid Lynx using 'dash' shell
    - drop debian/patches/fix-build-glitch.patch
    - update debian/patches/series

  [ Chris Coulson <email address hidden> ]
  * Fix LP: [#513887]("https://launchpad.net/bugs/513887") - Install the plugin-container binary for OOPP support
    - update debian/firefox.install
 -- Chris Coulson <email address hidden>   Sat, 17 Apr 2010 01:16:08 +0100

I have just installed Lucid RTM today and have:

Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.2.3) Gecko/20100423 Ubuntu/10.04 (lucid) Firefox/3.6.3 - Build ID: 20100423141150

---

### Post by SilverWave on 2010-05-01
> **teohhanhui said:**
> For anyone looking for Firefox 3.6.4 beta: [https://launchpad.net/~ubuntu-mozilla-security/+archive/ppa/]("https://launchpad.net/%7Eubuntu-mozilla-security/+archive/ppa/")

**  Current Schedule **

 As always, these dates may move if there are problems with builds,  showstopper bugs discovered in beta testing, or an urgent security  release required. 
 
[LIST]
[*] Code freeze: April 27, 11:59pm
[*] Build 2 is generated: April 30
[*] Build 2 is avaliable: May 3 (morning PST)
[*] Build 2 is offered as an automatic update to users of  Build 1: May 3 (afternoon PST)
[*] QA begins testing: May 3
[*] Build 2 offered as minor update to remaining 3.6.x beta  channel: May 5
[*] Final release: May 13 (afternoon PST)
[/LIST]
[https://wiki.mozilla.org/Releases/Firefox_3.6.4](https://wiki.mozilla.org/Releases/Firefox_3.6.4)

---

### Post by onecallednick on 2010-05-12
I installed the 3.7 one-daily-a-month build ppa but it won't upgrade me from 3.6.5 (from the firefox daily ppa), says i have the current version.  Does 3.7 exist anymore?  I read on the firefox 4 slideshow that they won't be releasing it, so is it gone now?

---

### Post by lovinglinux on 2010-05-12
> **onecallednick said:**
> I installed the 3.7 one-daily-a-month build ppa but it won't upgrade me from 3.6.5 (from the firefox daily ppa), says i have the current version.  Does 3.7 exist anymore?  I read on the firefox 4 slideshow that they won't be releasing it, so is it gone now?

It is still being build on [electrolysis repository](ftp://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/2010-05-12-11-electrolysis/).

---

### Post by SilverWave on 2010-05-13
> **lovinglinux said:**
> It is still being build on [electrolysis repository]("ftp://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/2010-05-12-11-electrolysis/").


hmm the link is to mozilla ftp site (not a ppa or repository), just source e.g. No built packages, no .debs.

But I see what you are saying, development is continuing.

---

### Post by SilverWave on 2010-05-13
> **onecallednick said:**
> I installed the 3.7 one-daily-a-month build ppa but it won't upgrade me from 3.6.5 (from the firefox daily ppa), says i have the current version.  Does 3.7 exist anymore?  I read on the firefox 4 slideshow that they won't be releasing it, so is it gone now?

Yes 3.7 wiil change to 4.0 at some point.
But from the video presentation I think it will be later in the process, although I could be wrong.

---

### Post by SilverWave on 2010-05-13
> **onecallednick said:**
> **I installed the 3.7 one-daily-a-month build ppa but it won't upgrade me from 3.6.5 **(from the firefox daily ppa), says i have the current version.  Does 3.7 exist anymore?  I read on the firefox 4 slideshow that they won't be releasing it, so is it gone now?
[B]
hmm re reading your post a couple of things occur to me.[/B]

1. Installing Firefox 3.7 will not upgrade your Firefox 3.6.5.
They are installed separately so you can run both.

Firefox 3.7 can be found here:
Check in Applications > Internet > Minefield 3.7 Web Browser

2. Ensure you have added the correct PPA for 3.7

**Either**
Firefox-3.7 **Lucid**:
```
sudo add-apt-repository  ppa:**silverwave/one-daily-a-month-1**
sudo apt-get update
sudo apt-get install firefox-3.7
```**Or**
Firefox-3.7 **Karmic**:
```
sudo add-apt-repository  ppa:**silverwave/one-daily-a-month-3**
sudo apt-get update
sudo apt-get install firefox-3.7
```

---

### Post by SilverWave on 2010-05-13
_**Just a note as we haven't had any **__**working builds of **__**Firefox 3.7 since 2010/05/05**_


[https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa/+packages?field.name_filter=firefox-3.7&field.status_filter=published&field.series_filter=lucid]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+packages?field.name_filter=firefox-3.7&field.status_filter=published&field.series_filter=lucid")
If you visit:
[https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa/+packages?field.name_filter=&field.status_filter=published&field.series_filter=lucid]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+packages?field.name_filter=&field.status_filter=published&field.series_filter=lucid")

Then check Firefox3.7 you will see that it is not getting built, as it  depends on xulrunner 1.9.3 which is failing.

________________________________________

Firefox3.6.5 is being built fine and is up to date.
The team have now created a new series for Lucid:
[firefox -   3.6.5~hg20100512r34186+nobinonly-0ubuntu1~umd1~lucid       ]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+sourcepub/1134668/+listing-archive-extra")

The package
[firefox -   3.6.5~hg20100512r34186+nobinonly-0ubuntu1~umd1       ]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+sourcepub/1134667/+listing-archive-extra")
Is now now tracking the Maverick series.

________________________________________

So...

**The options are**:

[LIST]
[*] That the FF3.7 daily is just having build issues.
 This happens from time to time, and they will be fixed in due time.
[*]That this may involve a name change from 3.7 to 4.0.
We will have to wait and see.
[/LIST]

---

### Post by zika on 2010-05-13
[ftp://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-mozilla-central/](ftp://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-mozilla-central/) is going ahead.

---

### Post by lovinglinux on 2010-05-13
> **SilverWave said:**
> hmm the link is to mozilla ftp site (not a ppa or repository), just source e.g. No built packages, no .debs.

But I see what you are saying, development is continuing.

I didn't mean a deb repository. But it is still a [repository](http://dictionary.reference.com/browse/repository), isn't it? :)

---

### Post by SilverWave on 2010-05-13
```
Changes for the versions:
-3.7~a5~hg20100427r41436+nobinonly-0ubuntu1~umd1
+3.7~a5~hg20100506r41949+nobinonly-0ubuntu1~umd1

-1.9.3~a5~hg20100427r41436+nobinonly-0ubuntu1~umd1
+1.9.3~a5~hg20100506r41949+nobinonly-0ubuntu1~umd
```Disclaimer: No guarantees use at your own risk

That said I have tested the packages in Virtual Machines For Lucid and Karmic (amd64 and i386).

[LIST]
[*]Installs.
[*]Display Web Page "Silverwav's Journal".
[*]Displays YouTube video.
[/LIST]
[Firefox-3.7 - One Daily A Month #1 - Lucid]("https://launchpad.net/%7Esilverwave/+archive/one-daily-a-month-1")

[Firefox-3.7 - One Daily A Month #3 - Karmic]("https://launchpad.net/%7Esilverwave/+archive/one-daily-a-month-3")

________________________________________


Firefox-3.7 **Lucid**:
```
sudo add-apt-repository  ppa:**silverwave/one-daily-a-month-1**
sudo apt-get update
sudo apt-get install firefox-3.7
```
Firefox-3.7 **Karmic**:
```
sudo add-apt-repository  ppa:**silverwave/one-daily-a-month-3**
sudo apt-get update
sudo apt-get install firefox-3.7
```

---

### Post by SilverWave on 2010-05-14
> **lovinglinux said:**
> I didn't mean a deb repository. But it is still a [repository]("http://dictionary.reference.com/browse/repository"), isn't it? :)

True, true. :-)

---

### Post by SilverWave on 2010-05-28
Just a note that **ubuntu-mozilla-daily** packages are building OK now for firefox-3.6.5 and firefox-3.7 (aka ff4).

There had been a lot of build failures over a period of days, but it looks like they have sorted it out. :-D

---

### Post by SilverWave on 2010-06-02
OK I have copied the 4 dailies to Testing as we have working builds for FF3.6.5 and 3.7a5 available for Lucid and Karmic :-D

So I will need to test each of the 4 packages in 32 and 64 bit before pushing them out to the production ppa's.

> 
Connect to Service and Register Application.

Check Configuration.
Distribution: Ubuntu
Copy From Archive: 
PPA for Ubuntu Mozilla Daily Build Team

Retrieve the list of Published Packages.

Copy To TEST Archive:
Firefox-3.6 Lucid: ppa:silverwave/testing0
Firefox-3.7 Lucid: ppa:silverwave/testing0
Firefox-3.6 Karmic: ppa:silverwave/testing1
Firefox-3.7 Karmic: ppa:silverwave/testing1

List UMD - FF3.6 *Lucid? [y]|n: 
3.6.5~hg20100601r34267+nobinonly-0ubuntu1~umd1~lucid
1.9.2.5~hg20100601r34267+nobinonly-0ubuntu1~umd1~lucid

Copy to testing? [n]|y: y
Copied to: One Daily A Month - Testing #0 - Lucid
Package: firefox - 3.6.5~hg20100601r34267+nobinonly-0ubuntu1~umd1~lucid

Copied to: One Daily A Month - Testing #0 - Lucid
Package: xulrunner-1.9.2 - 1.9.2.5~hg20100601r34267+nobinonly-0ubuntu1~umd1~lucid

List UMD - FF3.7 *Lucid? [y]|n: 
3.7~a5~hg20100602r43005+nobinonly-0ubuntu1~umd1~lucid
1.9.3~a5~hg20100602r43005+nobinonly-0ubuntu1~umd1~lucid

Copy to testing0? [n]|y: y
Copied to: One Daily A Month - Testing #0 - Lucid
Package: firefox-3.7 - 3.7~a5~hg20100602r43005+nobinonly-0ubuntu1~umd1~lucid

Copied to: One Daily A Month - Testing #0 - Lucid
Package: xulrunner-1.9.3 - 1.9.3~a5~hg20100602r43005+nobinonly-0ubuntu1~umd1~lucid

List UMD - FF3.6 Karmic? [y]|n: 
3.6.5~hg20100601r34267+nobinonly-0ubuntu1~umd1~karmic
1.9.2.5~hg20100601r34267+nobinonly-0ubuntu1~umd1~karmic

Copy to testing1? [n]|y: y
Copied to: One Daily A Month - Testing #1 - Karmic
Package: firefox - 3.6.5~hg20100601r34267+nobinonly-0ubuntu1~umd1~karmic

Copied to: One Daily A Month - Testing #1 - Karmic
Package: xulrunner-1.9.2 - 1.9.2.5~hg20100601r34267+nobinonly-0ubuntu1~umd1~karmic

List UMD - FF3.7 Karmic? [y]|n: 
3.7~a5~hg20100602r43005+nobinonly-0ubuntu1~umd1~karmic
1.9.3~a5~hg20100602r43005+nobinonly-0ubuntu1~umd1~karmic

Copy to testing1? [n]|y: y
Copied to: One Daily A Month - Testing #1 - Karmic
Package: firefox-3.7 - 3.7~a5~hg20100602r43005+nobinonly-0ubuntu1~umd1~karmic

Copied to: One Daily A Month - Testing #1 - Karmic
Package: xulrunner-1.9.3 - 1.9.3~a5~hg20100602r43005+nobinonly-0ubuntu1~umd1~karmic

done.
Closing... [y]|n: 
[https://launchpad.net/~silverwave/+archive/testing0/+packages?field.name_filter=&field.status_filter=&field.series_filter=lucid]("https://launchpad.net/%7Esilverwave/+archive/testing0/+packages?field.name_filter=&field.status_filter=&field.series_filter=lucid")

[https://launchpad.net/~silverwave/+archive/testing1/+packages?field.name_filter=&field.status_filter=&field.series_filter=karmic]("https://launchpad.net/%7Esilverwave/+archive/testing1/+packages?field.name_filter=&field.status_filter=&field.series_filter=karmic")

---

### Post by SilverWave on 2010-06-02
Testing completed - All OK.
Copying Packages over to Prod PPA's.

> 
Connect to Service and Register Application.

Check Configuration.
Distribution: Ubuntu
Copy From Archive: 
PPA for Ubuntu Mozilla Daily Build Team

Retrieve the list of Published Packages.

Copy To PROD Archive:
Firefox-3.6 Lucid: ppa:silverwave/one-daily-a-month-0
Firefox-3.7 Lucid: ppa:silverwave/one-daily-a-month-1
Firefox-3.6 Karmic: ppa:silverwave/one-daily-a-month-2
Firefox-3.7 Karmic: ppa:silverwave/one-daily-a-month-3

List UDM - FF3.6 *Lucid? [y]|n: 
3.6.5~hg20100601r34267+nobinonly-0ubuntu1~umd1~lucid
1.9.2.5~hg20100601r34267+nobinonly-0ubuntu1~umd1~lucid

Copy to ODAM0? [n]|y: y
Copied to: Firefox-3.6 - One Daily A Month #0 - Lucid
Package: firefox - 3.6.5~hg20100601r34267+nobinonly-0ubuntu1~umd1~lucid

Copied to: Firefox-3.6 - One Daily A Month #0 - Lucid
Package: xulrunner-1.9.2 - 1.9.2.5~hg20100601r34267+nobinonly-0ubuntu1~umd1~lucid

List UDM - FF3.7 *Lucid? [y]|n: 
3.7~a5~hg20100602r43005+nobinonly-0ubuntu1~umd1~lucid
1.9.3~a5~hg20100602r43005+nobinonly-0ubuntu1~umd1~lucid

Copy to ODAM1? [n]|y: y
Copied to: Firefox-3.7 - One Daily A Month #1 - Lucid
Package: firefox-3.7 - 3.7~a5~hg20100602r43005+nobinonly-0ubuntu1~umd1~lucid

Copied to: Firefox-3.7 - One Daily A Month #1 - Lucid
Package: xulrunner-1.9.3 - 1.9.3~a5~hg20100602r43005+nobinonly-0ubuntu1~umd1~lucid

List ODAM2 - FF3.6 Karmic? [y]|n: 
3.6.5~hg20100601r34267+nobinonly-0ubuntu1~umd1~karmic
1.9.2.5~hg20100601r34267+nobinonly-0ubuntu1~umd1~karmic

Copy to ODAM2? [n]|y: y
Copied to: Firefox-3.6 - One Daily A Month #2 - Karmic
Package: firefox - 3.6.5~hg20100601r34267+nobinonly-0ubuntu1~umd1~karmic

Copied to: Firefox-3.6 - One Daily A Month #2 - Karmic
Package: xulrunner-1.9.2 - 1.9.2.5~hg20100601r34267+nobinonly-0ubuntu1~umd1~karmic

List ODAM3 - FF3.7 Karmic? [y]|n: 
3.7~a5~hg20100602r43005+nobinonly-0ubuntu1~umd1~karmic
1.9.3~a5~hg20100602r43005+nobinonly-0ubuntu1~umd1~karmic

Copy to ODAM3? [n]|y: y
Copied to: Firefox-3.7 - One Daily A Month #3 - Karmic
Package: firefox-3.7 - 3.7~a5~hg20100602r43005+nobinonly-0ubuntu1~umd1~karmic

Copied to: Firefox-3.7 - One Daily A Month #3 - Karmic
Package: xulrunner-1.9.3 - 1.9.3~a5~hg20100602r43005+nobinonly-0ubuntu1~umd1~karmic

done.
Closing... [y]|n: 


---

### Post by SilverWave on 2010-06-02
[I]One daily a month from ubuntu-mozilla-daily.
 The latest firefox without the update hassle[/I].

[LIST]
[*]One ppa for each Firefox.
[*]Updated at the start of each  month.
[*]Tested in a virtual machine.
[/LIST]
 [Firefox-3.6 - One Daily A Month #0 - Lucid]("https://launchpad.net/%7Esilverwave/+archive/one-daily-a-month-0")
 ```

sudo add-apt-repository ppa:silverwave/one-daily-a-month-0
sudo apt-get update
sudo apt-get install firefox

```[Firefox-3.7 - One Daily A Month #1 - Lucid]("https://launchpad.net/%7Esilverwave/+archive/one-daily-a-month-1")
 ```

sudo add-apt-repository ppa:silverwave/one-daily-a-month-1
sudo apt-get update
sudo apt-get install firefox-3.7

```[Firefox-3.6 - One Daily A Month #2 - Karmic]("https://launchpad.net/%7Esilverwave/+archive/one-daily-a-month-2")
 ```

sudo add-apt-repository ppa:silverwave/one-daily-a-month-2
sudo apt-get update
sudo apt-get install firefox

```[Firefox-3.7 - One Daily A Month #3 - Karmic]("https://launchpad.net/%7Esilverwave/+archive/one-daily-a-month-3")
 ```

sudo add-apt-repository ppa:silverwave/one-daily-a-month-3
sudo apt-get update
sudo apt-get install firefox-3.7

```The new FF3.6 will be found under the name "Namoroka" in  Applications   > Internet.
The new FF3.7 will be found under  the name "Minefield 3.7 Web Browser".

________________________________________

**Tested and Updated for June 2010**

---

### Post by SilverWave on 2010-06-03
Interesting.... ubuntu-mozilla-daily

> Changes for the versions:
3.6.5~hg20100601r34267+nobinonly-0ubuntu1~umd1~lucid
3.6.6~hg20100603r34273+nobinonly-0ubuntu1~umd1~lucidMozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.2.6pre) Gecko/20100603 Ubuntu/10.04 (lucid) Namoroka/3.6.6pre - Build ID: 20100603035657

I have copied it to testing0 for the moment, lucid only (no build for Karmic yet). 

[https://launchpad.net/~silverwave/+archive/testing0/+packages?field.name_filter=&field.status_filter=&field.series_filter=lucid]("https://launchpad.net/%7Esilverwave/+archive/testing0/+packages?field.name_filter=&field.status_filter=&field.series_filter=lucid")

---

### Post by SilverWave on 2010-06-08
No new builds of Karmic 3.6 last still showing as "firefox -
3.6.5~hg20100601r34267

> Maverick
firefox - 3.6.6~hg20100607r34288+nobinonly-0ubuntu1~umd1
(changes file)          fta    5 hours ago

Lucid
firefox - 3.6.6~hg20100607r34288+nobinonly-0ubuntu1~umd1~lucid   (changes
file)  fta     5 hours ago

Jaunty
firefox - 3.6.6~hg20100607r34288+nobinonly-0ubuntu1~umd1~jaunty
(changes file)  fta     5 hours ago

Hardy
firefox - 3.6.6~hg20100607r34288+nobinonly-0ubuntu1~umd1~hardy   (changes
file)  fta     5 hours ago

Karmic
firefox - 3.6.5~hg20100601r34267+nobinonly-0ubuntu1~umd1~karmic  (changes
file)           fta    2010-06-02


Related to this [https://bugs.edge.launchpad.net/soyuz/+bug/589068](https://bugs.edge.launchpad.net/soyuz/+bug/589068)

---

### Post by SilverWave on 2010-06-11
3.7~a6 just in...

> 

Connect to Service and Register Application.

Check Configuration.
Distribution: Ubuntu
Copy From Archive: 
PPA for Ubuntu Mozilla Daily Build Team

Retrieve the list of Published Packages.

Copy To TEST Archive:
Firefox-3.6 Lucid: ppa:silverwave/testing0
Firefox-3.7 Lucid: ppa:silverwave/testing0
Firefox-3.6 Karmic: ppa:silverwave/testing1
Firefox-3.7 Karmic: ppa:silverwave/testing1

List UMD - FF3.6 *Lucid? [y]|n: 
3.6.6~hg20100609r34293+nobinonly-0ubuntu1~umd1~lucid
1.9.2.6~hg20100609r34293+nobinonly-0ubuntu1~umd1~lucid

Copy to testing? [n]|y: y
Copied to: One Daily A Month - Testing #0 - Lucid
Package: firefox - 3.6.6~hg20100609r34293+nobinonly-0ubuntu1~umd1~lucid

Copied to: One Daily A Month - Testing #0 - Lucid
Package: xulrunner-1.9.2 - 1.9.2.6~hg20100609r34293+nobinonly-0ubuntu1~umd1~lucid

List UMD - FF3.7 *Lucid? [y]|n: y
3.7~a6~hg20100611r43493+nobinonly-0ubuntu1~umd1~lucid
1.9.3~a6~hg20100611r43493+nobinonly-0ubuntu1~umd1~lucid

Copy to testing0? [n]|y: y
Copied to: One Daily A Month - Testing #0 - Lucid
Package: firefox-3.7 - 3.7~a6~hg20100611r43493+nobinonly-0ubuntu1~umd1~lucid

Copied to: One Daily A Month - Testing #0 - Lucid
Package: xulrunner-1.9.3 - 1.9.3~a6~hg20100611r43493+nobinonly-0ubuntu1~umd1~lucid

List UMD - FF3.6 Karmic? [y]|n: y
3.6.5~hg20100601r34267+nobinonly-0ubuntu1~umd1~karmic
1.9.2.6~hg20100609r34293+nobinonly-0ubuntu1~umd1~karmic

Copy to testing1? [n]|y: n

List UMD - FF3.7 Karmic? [y]|n: y
3.7~a6~hg20100611r43493+nobinonly-0ubuntu1~umd1~karmic
1.9.3~a6~hg20100611r43493+nobinonly-0ubuntu1~umd1~karmic

Copy to testing1? [n]|y: y
Copied to: One Daily A Month - Testing #1 - Karmic
Package: firefox-3.7 - 3.7~a6~hg20100611r43493+nobinonly-0ubuntu1~umd1~karmic

Copied to: One Daily A Month - Testing #1 - Karmic
Package: xulrunner-1.9.3 - 1.9.3~a6~hg20100611r43493+nobinonly-0ubuntu1~umd1~karmic

done.
Closing... [y]|n: 



---

### Post by SilverWave on 2010-06-22
Looks like the official 3.6.4 is out from Mozilla

[http://ftp.ankara.edu.tr/mozilla/firefox/releases/3.6.4/linux-i686/en-US/firefox-3.6.4.tar.bz2](http://ftp.ankara.edu.tr/mozilla/firefox/releases/3.6.4/linux-i686/en-US/firefox-3.6.4.tar.bz2)

[Firefox 3.6.4 with Crash Protection Now Available]("http://blog.mozilla.com/blog/2010/06/22/firefox-3-6-4-with-crash-protection-now-available/")



Of course we are way ahead with 3.6.6 from the ppa's :-)

---

### Post by lovinglinux on 2010-06-22
> **SilverWave said:**
> Looks like the official 3.6.4 is out from Mozilla

[http://ftp.ankara.edu.tr/mozilla/firefox/releases/3.6.4/linux-i686/en-US/firefox-3.6.4.tar.bz2](http://ftp.ankara.edu.tr/mozilla/firefox/releases/3.6.4/linux-i686/en-US/firefox-3.6.4.tar.bz2)

[Firefox 3.6.4 with Crash Protection Now Available]("http://blog.mozilla.com/blog/2010/06/22/firefox-3-6-4-with-crash-protection-now-available/")

Yes, it is.

> **SilverWave said:**
> Of course we are way ahead with 3.6.6 from the ppa's :-)

Yes, we are :)

---

### Post by SilverWave on 2010-06-29
Hmm so when will we see 4.0b2? :-)

Oh and ubuntu-mozilla-daily still has a problem with the 3.6 ppa package for Karmic. Until this bug is squashed its stuck at 3.6.5...

The good news is that the patch just needs to be deployed to the pps system on launchpad so this will be fixed RSN.

Oh and the Lucid firefox daily is now up to version 3.6.7

---

### Post by SilverWave on 2010-07-02
> **SilverWave said:**
> Hmm so when will we see 4.0b2? :-)




And so it begins :-)


[http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-trunk/](http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-trunk/)

[firefox-4.0b2pre.en-US.linux-x86_64.tar.bz2]("http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-trunk/firefox-4.0b2pre.en-US.linux-x86_64.tar.bz2")

> Oh and ubuntu-mozilla-daily still has a problem with the 3.6 ppa package  for Karmic. Until this bug is squashed its stuck at 3.6.5...Fixed!

List UMD - FF3.6 Karmic? [y]|n: 
3.6.8~hg20100701r34421+nobinonly-0ubuntu1~umd1~karmic
1.9.2.8~hg20100701r34421+nobinonly-0ubuntu1~umd1~karmic

Copy to testing1? [n]|y: y
Copied to: One Daily A Month - Testing #1 - Karmic
Package: firefox - 3.6.8~hg20100701r34421+nobinonly-0ubuntu1~umd1~karmic

Copied to: One Daily A Month - Testing #1 - Karmic
Package: xulrunner-1.9.2 - 1.9.2.8~hg20100701r34421+nobinonly-0ubuntu1~umd1~karmic


______________

Note: As 10.10 a2 is being pushed out updates to ppa's will take a while to return to normall

> **      [IMG]https://edge.launchpad.net/@@/ppa-icon[/IMG]            PPA build status    **

                             Processor          Builders          Queue
 amd64          11                                      8733                              jobs               (four days)
 i386          14                                      17479                              jobs               (five days)
 lpia          3                                      9                              jobs               (18 minutes)                                    

---

### Post by SilverWave on 2010-07-06
Looks like things are getting back to normal...

> **PPA build status    **

                             Processor          Builders          Queue
 amd64          3                                      35                              jobs               (2 hours 40 minutes)
 i386          4                                      122                              jobs               (13 hours)
 lpia          3                                      9                              jobs               (2 hours 10 minutes)

---

### Post by SilverWave on 2010-07-07
[http://www.mozilla.com/en-US/firefox/beta/](http://www.mozilla.com/en-US/firefox/beta/)

No PPA yet ;-)

---

### Post by SilverWave on 2010-07-12
[firefox-4.0 - 4.0~b2~hg20100712r47317+nobinonly-0ubuntu1~umd1~lucid]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+sourcepub/1230327/+listing-archive-extra")

waiting for the build to finish on 64bit

---

### Post by zika on 2010-07-12
On 32-bit install I get:

~$ /usr/bin/firefox-4.0 
/usr/bin/firefox-4.0: 175: Syntax error: end of file unexpected (expecting "fi")

I've tried to add "fi" but... No time to parse the whole file...

On the "+" side it uninstalled 3.7 and xulrunner1.9.3... xulrunner is now 2.0...

Update: The same happens in 64-bit install... Both are on Maverick...
No 4.0 today, except the one from nightly... :)

---

### Post by zika on 2010-07-12
Fixed, new version arrived!
(32-bit, 64-bit still in works...)

---

### Post by SilverWave on 2010-07-12
> **zika said:**
> Fixed, new version arrived!


Heh just got in from work and started testing... got and error message  and googled for it... and the seach pointed to my how-to!

heh , spooky or what?

So off to get the latest build and start again.

---

### Post by SilverWave on 2010-07-13
> Mozilla/5.0 (X11; Linux x86_64; en-US; rv:2.0b2pre) Gecko/20100712 Ubuntu/10.04 (lucid) MozillaDeveloperPreview/4.0b2preheh 64bit finally built !

FF4.0 is here:
[https://launchpad.net/~silverwave/+archive/testing0/]("https://launchpad.net/%7Esilverwave/+archive/testing0/")
[https://launchpad.net/~silverwave/+archive/testing1/]("https://launchpad.net/%7Esilverwave/+archive/testing1/")

only tested superficially on 64bit Lucid :-)

---

### Post by zika on 2010-07-13
It lasted less than a day...
```
Errors were encountered while processing:
 firefox-4.0
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up firefox-4.0 (4.0~b2~hg20100712r47341+nobinonly-0ubuntu1~umd1) ...
update-alternatives: error: alternative path /usr/bin/firefox-4.0 doesn't exist.
dpkg: error processing firefox-4.0 (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 firefox-4.0
```(32-bit, did not test 64-bit yet...)

---

### Post by SilverWave on 2010-07-13
> **zika said:**
> It lasted less than a day...
```
Errors were encountered while processing:
 firefox-4.0
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up firefox-4.0 (4.0~b2~hg20100712r47341+nobinonly-0ubuntu1~umd1) ...
update-alternatives: error: alternative path /usr/bin/firefox-4.0 doesn't exist.
dpkg: error processing firefox-4.0 (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 firefox-4.0
```(32-bit, did not test 64-bit yet...)


try :
Installed: 4.0~b2~hg20100712r47317+nobinonly-0ubuntu1~umd2~lucid

---

### Post by zika on 2010-07-13
> **SilverWave said:**
> try :
Installed: 4.0~b2~hg20100712r47317+nobinonly-0ubuntu1~umd2~lucidI'm on Maverick. I do not like to mix... But, thank You, nevertheless...
It'll be fixed soon, I hope. That makes me use Chrom{e,ium} more... :)

---

### Post by SilverWave on 2010-07-13
> **zika said:**
> I'm on Maverick. I do not like to mix... But, thank You, nevertheless...
It'll be fixed soon, I hope. That makes me use Chrom{e,ium} more... :)

try :
Installed: 4.0~b2~hg20100712r47317+nobinonly-0ubuntu1~umd2

What I mean is just go back a version...

Saying which a new one was being built as I posted, so hopefully that build will work.

---

### Post by SilverWave on 2010-07-13
> **Firefox-4.0 - One Daily A Month #1 - Lucid       **
[SilverWave]("https://launchpad.net/%7Esilverwave")Firefox-4.0 - One Daily A Month #1 - ...              
                                                                                
      **PPA description**
The latest firefox without the update hassle.
 One daily a month from ubuntu-mozilla-daily.
______________________________
 Firefox-4.0 - One Daily A Month #1 - Lucid
One update a month.
Firefox and xulrunner only.
Tested in a virtual machine.
______________________________
 sudo add-apt-repository  ppa:silverwave/one-daily-a-month-1
sudo apt-get update
sudo apt-get install firefox-4.0
______________________________
 Disclaimer: Use at your own risk, no guarantees.
> 
                                                    **Firefox-4.0 - One Daily A Month #3 - Karmic       **
[SilverWave]("https://launchpad.net/%7Esilverwave")Firefox-4.0 - One Daily A Month #3 - ...              
                                                                                
      **PPA description**
   The latest firefox without the update hassle.
 One daily a month from ubuntu-mozilla-daily.
______________________________
 Firefox-4.0 - One Daily A Month #3 - Karmic
One update a month.
Firefox and xulrunner only.
Tested in a virtual machine.
______________________________
 sudo add-apt-repository ppa:silverwave/one-daily-a-month-3
sudo apt-get update
sudo apt-get install firefox-4.0
______________________________
 Disclaimer: Use at your own risk, no guarantees.
All tested and working :-)

Based on:

4.0~b2~hg20100712r47317+nobinonly-0ubuntu1~umd2
2.0~b2~hg20100712r47317+nobinonly-0ubuntu1~umd1                                

Enjoy!

---

### Post by Chame_Wizard on 2010-07-14
I have 3.6.8pre.:P

---

### Post by SilverWave on 2010-07-14
> **Chame_Wizard said:**
> I have 3.6.8pre.:P

So have I :-) 

Its very good!

---

### Post by lovinglinux on 2010-07-14
Hi SilverWave,

Since there is already users trying Firefox 4 Beta and you are distributing it, I thought would by wise to leave a warning for add-ons users.

Firefox 4 introduced some radical changes in the add-ons manager, as you can see from the new manager design. These changes will probably break several add-ons, even if you don't think they are broken. 

Usually when Firefox releases a new major version, we can override the extension compatibility check to force extensions to work. In this particular case, some extensions might appear to be working, but they could have issues with updates.

The problem is that whenever such extensions update, they grab the version number from the extension manager, in order to determine if they need to perform changes in associated databases, extension settings and profiles. Since the add-on manager has changed drastically, they won't be able to update properly. They will appear to be working, but won't be able to update some files and perform some functions dependent on extension version.

So if you are using Firefox 4, I would recommend using a separate profile, until all your extensions are updated to work with it.

---

### Post by SilverWave on 2010-07-14
> **lovinglinux said:**
> Hi SilverWave,
[...] if you are using Firefox 4, I would recommend using a separate profile, until all your extensions are updated to work with it.

If you use the PPA's I have set up (ppa:silverwave/one-daily-a-month-1 and ppa:silverwave/one-daily-a-month-3) then this is the default behaviour.

e.g.

The 4.0 profile is saved in:

/home/sil/.mozilla/firefox-4.0

The 3.6.8 profile is saved in:

/home/sil/.mozilla/firefox

---

### Post by lovinglinux on 2010-07-14
> **SilverWave said:**
> If you use the PPA's I have set up (ppa:silverwave/one-daily-a-month-1 and ppa:silverwave/one-daily-a-month-3) then this is the default behaviour.

e.g.

The 4.0 profile is saved in:

/home/sil/.mozilla/firefox-4.0

The 3.6.8 profile is saved in:

/home/sil/.mozilla/firefox

Cool. Nice job.

---

### Post by hackel on 2010-07-15
It would be much more useful if this PPA, instead of taking a random daily snapshot once a month, actually took the tested, official releases from Mozilla...  FF4b1 for now, and b2 as soon as Mozilla releases it.  The way it is now is completely pointless--I can do the same thing extremely easily by randomly picking a day to update from mozilla-daily.  And where is firefox-4.0-gnome-support?

---

### Post by SilverWave on 2010-07-15
> **hackel said:**
> It would be much more useful if this PPA, instead of taking a random daily snapshot once a month, 
Well... there is no guarantee that any particular daily from UMD will actually work. So using my PPA's you at least know that it has had basic testing. 

So my "value added" to the process is:

Firefox has its own PPA so nothing else gets updated.
You don&#8217;t get swamped with updates.
You do get the latest Firefox each month.
Tested in a virtual machine.

Lucid 64bit gets more testing as I actually use that package day-to-day.

> **hackel said:**
>  ...actually took the tested, official releases from Mozilla...  FF4b1 for now, and b2 as soon as Mozilla releases it.

Well that would be a huge amount of work and very challenging technically, to ensure a stable integrated package for Lucid and Karmic.

I am rather "Standing On the Shoulders of Giants", and basing my ppa's on the fantastic work of the Ubuntu Mozilla Daily Build Team (I actually do a copy of the relevant daily packages).

Of course if you were to produce such a ppa that would be great.
I would encourage you post your ppa details here once you have completed it.

> **hackel said:**
>  The way it is now is completely pointless--I can do the same thing extremely easily by randomly picking a day to update from mozilla-daily.  And where is firefox-4.0-gnome-support?

Some observations on your post:

Please moderate your tone and be polite, I actually do this in my spare time and don't work for you.

I think I have answered your points above and disagree :p

Cheers.

---

### Post by SilverWave on 2010-07-15
> **lovinglinux said:**
> Cool. Nice job.

heh cant take the credit as that's what is set by the packager.

I copy and test and add convenience.

I am rather "Standing On the Shoulders of Giants", and basing my ppa's  on the fantastic work of the Ubuntu Mozilla Daily Build Team (I actually  do a copy of the relevant daily packages).

But this is "A Good Thing" as you can confirm that I haven't tampered with the packages and as long as you trust the "Ubuntu Mozilla Daily Build Team" you are good to go :-)

---

### Post by SilverWave on 2010-07-17
Q: PPA Builds Very Slow(10hours)?
A: "Someone is doing a rebuild of all Python packages in Maverick, we have to wait until it's finished I'm afraid."

---

### Post by SilverWave on 2010-07-17
OK for this month I have went with the following updates:

**Packages in “Firefox-3.6 - One Daily A Month #0 - Lucid”**
[https://launchpad.net/~silverwave/+archive/one-daily-a-month-0/+packages]("https://launchpad.net/%7Esilverwave/+archive/one-daily-a-month-0/+packages")

[ 3.6.8~hg20100714r34432+nobinonly-0ubuntu1~umd1~lucid]("https://launchpad.net/%7Esilverwave/+archive/one-daily-a-month-0/+sourcepub/1238995/+listing-archive-extra")
[B]
Packages in “Firefox-3.6 - One Daily A Month #2 - Karmic”[/B]
[https://launchpad.net/~silverwave/+archive/one-daily-a-month-2/+packages]("https://launchpad.net/%7Esilverwave/+archive/one-daily-a-month-2/+packages")

[firefox - 3.6.8~hg20100714r34432+nobinonly-0ubuntu1~umd1~karmic       ]("https://launchpad.net/%7Esilverwave/+archive/one-daily-a-month-2/+sourcepub/1238758/+listing-archive-extra")

---

### Post by vajras on 2010-07-21
May i ask what happens to this when the official version is released, i.e. finally out?

Do your "ppa's" then cease to work?

Will you/do you then provide code to "uninstall" Firefox?

Sorry if my Q's are incorrectly formed - hoping you'll understand!

[i'm using - Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.2.8pre) Gecko/20100720 Ubuntu/10.04 (lucid) Namoroka/3.6.8pre]

---

### Post by vajras on 2010-07-21
P.S - How can i revert from Namaroka to Lucid's Firefox?

i am finding with Namaroka (and in Sea Monkey) there are a couple of web sites i need that are so poorly designed FF is my only option!

---

### Post by lovinglinux on 2010-07-21
> **vajras said:**
> P.S - How can i revert from Namaroka to Lucid's Firefox?

i am finding with Namaroka (and in Sea Monkey) there are a couple of web sites i need that are so poorly designed FF is my only option!

To revert to the default Firefox, disable the the ppa repository and re-install firefox.

If you need other version for just a couple of sites, then you could run another version in parallel. You can run multiple versions of Firefox simultaneously by simply downloading them from Mozilla and [installing manually]("http://firefox-tutorials.blogspot.com/2010/05/installing-other-versions.html") or using my [FoxTester]("http://foxtester-extension.blogspot.com/") extension. With my extension is easier, because you don't need to run any commands to install or to launch another version of Firefox. See [demo]("http://foxtester-extension.blogspot.com/p/features.html").

---

### Post by SilverWave on 2010-07-23
> **vajras said:**
> May i ask what happens to this when the official version is released, i.e. finally out?

Do your "ppa's" then cease to work?

Will you/do you then provide code to "uninstall" Firefox?

Sorry if my Q's are incorrectly formed - hoping you'll understand!

[i'm using - Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.2.8pre) Gecko/20100720 Ubuntu/10.04 (lucid) Namoroka/3.6.8pre]


Hi,
No they will not stop working, when "Firefox 4.0 official" is released then the dailies just bump up to 4.1.

Also when I do stop producing updated packages for say... Karmic, then you would still be OK as once the official Ubuntu repositories caught-up (version wise) then you would start getting updates again.

Hope that answers your question, sorry I was a little tardy answering, but I have a new job etc. :-)

__________________
Now regarding Ubuntu Distribution versions:
I will only be supporting the latest 2 Versions of Ubuntu at any one time so...

My latest plan is something like this...

Now:
ODAM0 -- FF3.6 Lucid
ODAM1 -- FF4.0 Lucid
ODAM2 -- FF3.6 Karmic
ODAM3 -- FF4.0 Karmic

Later:
ODAM0 -- FF3.6 Lucid
ODAM1 -- FF4.0 Lucid
ODAM2 -- FF3.6 Maverick
ODAM3 -- FF4.0 Maverick

Not sure when Karmic will be dropped, but I would hazard a guess at about Maverick beta1.
It will really depends on when I start using Maverick.
__________________

Of course sometime during Maverick, Firefox 4.0 will be released and the dailies will bump up to 4.1/4.5? but 3.6 will still be supported for a year? So the outline above should work for a while. In the long term the ppa will support 4.0 (Production) and 4.1/4.5? (Development). Then again things change rapidly :-)

---

### Post by SilverWave on 2010-07-23
> **vajras said:**
> P.S - How can i revert from Namaroka to Lucid's Firefox?

i am finding with Namaroka (and in Sea Monkey) there are a couple of web sites i need that are so poorly designed FF is my only option!

hmm Namaroka IS Firefox 3.6.8pre so if that doesn't work I don't think Firefox 3.6 Lucid will either.

But if you want to revert, go to...
System > Administration > Software sources.
Other Software.

Untick:

ppa.launchpad.net/silverwave/one-daily-a-month-0/ubuntu

Close.

Go to Synaptic Package Manager
Uninstall firefox,
Refresh
Reinstall firefox.

Done :-)

---

### Post by SilverWave on 2010-07-23
Mozilla/5.0 (X11; Linux x86_64; rv:2.0b3pre) Gecko/20100723 Ubuntu/10.04 (lucid) MozillaDeveloperPreview/4.0b3pre

In testing...

Lucid
[https://launchpad.net/~silverwave/+archive/testing0/+packages]("https://launchpad.net/%7Esilverwave/+archive/testing0/+packages")
64bit Tested and working.

Karmic
[https://launchpad.net/~silverwave/+archive/testing1/+packages]("https://launchpad.net/%7Esilverwave/+archive/testing1/+packages")

Not tested yet

---

### Post by vajras on 2010-07-23
> **SilverWave said:**
> hmm Namaroka IS Firefox 3.6.8pre so if that doesn't work I don't think Firefox 3.6 Lucid will either.
Done :-)

Actually it does which is surprising so have 'downgraded' to 3.6.7.

Thanks for the hints and tips - saved to a text file! :-)

---

### Post by SilverWave on 2010-07-24
> **vajras said:**
> Actually it does which is surprising so have 'downgraded' to 3.6.7.

Thanks for the hints and tips - saved to a text file! :-)

Hmm that's odd, as I wouldn't have thought the changes between 3.6.7 and 3.6.8 would affect site rendering.

It is more likely that the sites are checking the "user agent" string and don't know that "Namoroka" is Firefox.

---

### Post by JohnnyC35 on 2010-07-24
got 3.6.9pre on here. works fine. seems to be no appreciable difference tho

---

### Post by SilverWave on 2010-07-24
> **JohnnyC35 said:**
> got 3.6.9pre on here. works fine. seems to be no appreciable difference tho

Great at least it works for you :-)

Just snagged a copy for testing

___

[https://launchpad.net/~silverwave/+archive/testing1/+packages]("https://launchpad.net/%7Esilverwave/+archive/testing1/+packages")

[        firefox - 3.6.9~hg20100723r34459+nobinonly-0ubuntu1~umd1~karmic       ]("https://launchpad.net/%7Esilverwave/+archive/testing1/+sourcepub/1247753/+listing-archive-extra")

Oh and

[firefox-4.0 - 4.0~b3~hg20100724r48157+nobinonly-0ubuntu1~umd1~karmic]("https://launchpad.net/%7Esilverwave/+archive/testing1/+sourcepub/1247755/+listing-archive-extra")


___

[https://launchpad.net/~silverwave/+archive/testing0/+packages]("https://launchpad.net/%7Esilverwave/+archive/testing0/+packages")

[        firefox - 3.6.9~hg20100723r34459+nobinonly-0ubuntu1~umd1~lucid       ]("https://launchpad.net/%7Esilverwave/+archive/testing0/+sourcepub/1247751/+listing-archive-extra")

[firefox-4.0 - 4.0~b3~hg20100724r48157+nobinonly-0ubuntu1~umd1~lucid]("https://launchpad.net/%7Esilverwave/+archive/testing0/+sourcepub/1247750/+listing-archive-extra")
[B]
[Update]

[/B]Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.2.9pre) Gecko/20100724 Ubuntu/10.04 (lucid) Namoroka/3.6.9pre [B]
Works OK for me.

As does[/B]
Mozilla/5.0 (X11; Linux x86_64; rv:2.0b3pre) Gecko/20100724 Ubuntu/10.04 (lucid) MozillaDeveloperPreview/4.0b3pre[B]

Bookmark button is included as is Tabs on Top, but no show for the App button to replace the menus, yet.
[/B]

---

### Post by SilverWave on 2010-07-24
With the start of the new 4.0b3 dailies and the security updates to 3.6 I thought it best to push out an extra update this month.

I have tested each in a VM. (The browser opens and displays Web sites and youtube).

So:

**[Packages in &#8220;Firefox-3.6 - One Daily A Month #0 - Lucid&#8221;]("https://launchpad.net/%7Esilverwave/+archive/one-daily-a-month-0/+packages")**

> [           firefox - 3.6.9~hg20100723r34459+nobinonly-0ubuntu1~umd1~lucid       ]("https://launchpad.net/%7Esilverwave/+archive/one-daily-a-month-0/+sourcepub/1247788/+listing-archive-extra")                                  [(changes file)]("https://launchpad.net/%7Esilverwave/+archive/one-daily-a-month-0/+files/firefox_3.6.9%7Ehg20100723r34459+nobinonly-0ubuntu1%7Eumd1%7Elucid_source.changes")**[Packages in &#8220;Firefox-4.0 - One Daily A Month #1 - Lucid&#8221;]("https://launchpad.net/%7Esilverwave/+archive/one-daily-a-month-1/+packages")**

> [firefox-4.0 - 4.0~b3~hg20100724r48157+nobinonly-0ubuntu1~umd1~lucid       ]("https://launchpad.net/%7Esilverwave/+archive/one-daily-a-month-1/+sourcepub/1247789/+listing-archive-extra")                                  [(changes file)]("https://launchpad.net/%7Esilverwave/+archive/one-daily-a-month-1/+files/firefox-4.0_4.0%7Eb3%7Ehg20100724r48157+nobinonly-0ubuntu1%7Eumd1%7Elucid_source.changes")                      
    
                                      [         xulrunner-2.0 - 2.0~b3~hg20100724r48157+nobinonly-0ubuntu1~umd1~lucid       ]("https://launchpad.net/%7Esilverwave/+archive/one-daily-a-month-1/+sourcepub/1247790/+listing-archive-extra")                                  [(changes file)]("https://launchpad.net/%7Esilverwave/+archive/one-daily-a-month-1/+files/xulrunner-2.0_2.0%7Eb3%7Ehg20100724r48157+nobinonly-0ubuntu1%7Eumd1%7Elucid_source.changes")**[Packages in &#8220;Firefox-3.6 - One Daily A Month #2 - Karmic&#8221;]("https://launchpad.net/%7Esilverwave/+archive/one-daily-a-month-2/+packages")**

> [firefox - 3.6.9~hg20100723r34459+nobinonly-0ubuntu1~umd1~karmic       ]("https://launchpad.net/%7Esilverwave/+archive/one-daily-a-month-2/+sourcepub/1247784/+listing-archive-extra")                                  [(changes file)]("https://launchpad.net/%7Esilverwave/+archive/one-daily-a-month-2/+files/firefox_3.6.9%7Ehg20100723r34459+nobinonly-0ubuntu1%7Eumd1%7Ekarmic_source.changes")
**[Packages in &#8220;Firefox-4.0 - One Daily A Month #3 - Karmic&#8221;]("https://launchpad.net/%7Esilverwave/+archive/one-daily-a-month-3/+packages")**

> [firefox-4.0 - 4.0~b3~hg20100724r48157+nobinonly-0ubuntu1~umd1~karmic       ]("https://launchpad.net/%7Esilverwave/+archive/one-daily-a-month-3/+sourcepub/1247785/+listing-archive-extra")                                  [(changes file)]("https://launchpad.net/%7Esilverwave/+archive/one-daily-a-month-3/+files/firefox-4.0_4.0%7Eb3%7Ehg20100724r48157+nobinonly-0ubuntu1%7Eumd1%7Ekarmic_source.changes")
                                      [         xulrunner-2.0 - 2.0~b3~hg20100724r48157+nobinonly-0ubuntu1~umd1~karmic       ]("https://launchpad.net/%7Esilverwave/+archive/one-daily-a-month-3/+sourcepub/1247786/+listing-archive-extra")                                  [(changes file)]("https://launchpad.net/%7Esilverwave/+archive/one-daily-a-month-3/+files/xulrunner-2.0_2.0%7Eb3%7Ehg20100724r48157+nobinonly-0ubuntu1%7Eumd1%7Ekarmic_source.changes")

---

### Post by vajras on 2010-07-24
> **SilverWave said:**
> Hmm that's odd, as I wouldn't have thought the changes between 3.6.7 and 3.6.8 would affect site rendering.

It is more likely that the sites are checking the "user agent" string and don't know that "Namoroka" is Firefox.

Yes, that could be right but also was using Seamonkey to see if it was a Namoroka or Shiretoko error but in Seamonkey, 

Build identifier: Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.1.11) Gecko/20100722 SeaMonkey/2.0.6

the financial site hell desk concerned was just a bit too thick! They suggested i install Safari and contact my Apple Service Centre to rectify their no "<BR> expected" and "XML Parsing" errors in their logon page.

Now with a vanilla FF i can login.

---

### Post by SilverWave on 2010-07-25
> **vajras said:**
> Yes, that could be right but also was using Seamonkey to see if it was a Namoroka or Shiretoko error but in Seamonkey, 

Build identifier: Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.1.11) Gecko/20100722 SeaMonkey/2.0.6

the financial site hell desk concerned was just a bit too thick! They suggested i install Safari and contact my Apple Service Centre to rectify their no "<BR> expected" and "XML Parsing" errors in their logon page.

Now with a vanilla FF i can login.

This may do the job :-)

[User Agent Switcher 0.7.2](https://addons.mozilla.org/en-US/firefox/addon/59/)

---

### Post by Holmen on 2010-07-28
Since two days back I cant get it to open. Segfault...

---

### Post by vajras on 2010-07-28
> **SilverWave said:**
> This may do the job :-)

[User Agent Switcher 0.7.2](https://addons.mozilla.org/en-US/firefox/addon/59/)

i think the problem was around the way Flash/Videos etc were not interacting properly, and together with the fact that FF/Namaroka etc. were not installed in the correct locations, exacerbated the issue.

Problem now solved so thanks for your suggestions.

see this thread - [http://ubuntuforums.org/showthread.php?p=9645578#post9645578](http://ubuntuforums.org/showthread.php?p=9645578#post9645578)

---

### Post by SilverWave on 2010-07-29
> **Holmen said:**
> Since two days back I cant get it to open. Segfault...

> Hi,

I've got it working now. I was looking trough my PPA-list and found one
that I couldn't remeber why I used. So I removed it, purged all the
packages and now it works again.

I'm sorry for the inconvenience.

Yours sincerely,

Glad to see you got it fixed.

---

### Post by SilverWave on 2010-07-29
> **vajras said:**
> i think the problem was around the way Flash/Videos etc were not interacting properly, and together with the fact that FF/Namaroka etc. were not installed in the correct locations, exacerbated the issue.

Problem now solved so thanks for your suggestions.

see this thread - [http://ubuntuforums.org/showthread.php?p=9645578#post9645578](http://ubuntuforums.org/showthread.php?p=9645578#post9645578)

Great news :-)

---

### Post by SilverWave on 2010-08-09
Here we go...
[https://wiki.mozilla.org/Releases/Firefox_4.0b3](https://wiki.mozilla.org/Releases/Firefox_4.0b3)

---

### Post by SilverWave on 2010-08-10
> **SilverWave said:**
> Here we go...
[https://wiki.mozilla.org/Releases/Firefox_4.0b3](https://wiki.mozilla.org/Releases/Firefox_4.0b3)

Here we go Testing seemed OK so copying to Production:

[> ]("https://launchpad.net/%7Esilverwave/+archive/testing1/+sourcepub/1262538/+listing-archive-extra")[firefox-4.0 - 4.0~b4~hg20100809r49183+nobinonly-0ubuntu1~umd1~karmic       ]("https://launchpad.net/%7Esilverwave/+archive/testing1/+sourcepub/1262538/+listing-archive-extra")                                  [(changes file)]("https://launchpad.net/%7Esilverwave/+archive/testing1/+files/firefox-4.0_4.0%7Eb4%7Ehg20100809r49183+nobinonly-0ubuntu1%7Eumd1%7Ekarmic_source.changes")                      10 hours ago     Published     Karmic     Web            [IMG]https://launchpad.net/@@/no[/IMG]                [           lpia         ]("https://launchpad.net/%7Esilverwave/+archive/testing1/+build/1911427")                                   
                                                         [xulrunner-2.0 - 2.0~b4~hg20100809r49180+nobinonly-0ubuntu1~umd1~karmic       ]("https://launchpad.net/%7Esilverwave/+archive/testing1/+sourcepub/1262539/+listing-archive-extra")                                  [(changes file)]("https://launchpad.net/%7Esilverwave/+archive/testing1/+files/xulrunner-2.0_2.0%7Eb4%7Ehg20100809r49180+nobinonly-0ubuntu1%7Eumd1%7Ekarmic_source.changes")                      10 hours ago     Published     Karmic     Devel            [IMG]https://launchpad.net/@@/yes[/IMG]



[         firefox-4.0 - 4.0~b4~hg20100809r49183+nobinonly-0ubuntu1~umd1~lucid       ]("https://launchpad.net/%7Esilverwave/+archive/testing0/+sourcepub/1262537/+listing-archive-extra")                                  [(changes file)]("https://launchpad.net/%7Esilverwave/+archive/testing0/+files/firefox-4.0_4.0%7Eb4%7Ehg20100809r49183+nobinonly-0ubuntu1%7Eumd1%7Elucid_source.changes")                      10 hours ago     Published     Lucid     Web            [IMG]https://launchpad.net/@@/yes[/IMG]                            
                                                         [xulrunner-2.0 - 2.0~b4~hg20100809r49180+nobinonly-0ubuntu1~umd1~lucid       ]("https://launchpad.net/%7Esilverwave/+archive/testing0/+sourcepub/1262536/+listing-archive-extra")                                  [(changes file)]("https://launchpad.net/%7Esilverwave/+archive/testing0/+files/xulrunner-2.0_2.0%7Eb4%7Ehg20100809r49180+nobinonly-0ubuntu1%7Eumd1%7Elucid_source.changes")                      10 hours ago     Published     Lucid     Devel            [IMG]https://launchpad.net/@@/yes[/IMG]                            

---

### Post by SilverWave on 2010-08-10
**Firefox-4.0 - One Daily A Month #1 - Lucid**
[SilverWave]("https://launchpad.net/%7Esilverwave")Firefox-4.0 - One Daily A Month #1 - ...              
                                                                                
      **PPA description**
   The latest firefox without the update hassle.
 One daily a month from ubuntu-mozilla-daily.
______________________________
 Firefox-4.0 - One Daily A Month #1 - Lucid
One update a month.
Firefox only.
Tested in a virtual machine.
______________________________
 sudo add-apt-repository  ppa:silverwave/one-daily-a-month-1
sudo apt-get update
sudo apt-get install firefox-4.0
______________________________
 Disclaimer: Use at your own risk, no guarantees.


____________________


      [B]Firefox-4.0 - One Daily A Month #3 - Karmic
[/B][SilverWave]("https://launchpad.net/%7Esilverwave")
Firefox-4.0 - One Daily A Month #3 - ...              

**PPA description**
The latest firefox without the update hassle.
 One daily a month from ubuntu-mozilla-daily.
______________________________
 Firefox-4.0 - One Daily A Month #3 - Karmic
One update a month.
Firefox only.
Tested in a virtual machine.
______________________________
 sudo add-apt-repository ppa:silverwave/one-daily-a-month-3
sudo apt-get update
sudo apt-get install firefox-4.0
______________________________
 Disclaimer: Use at your own risk, no guarantees.

---

### Post by SilverWave on 2010-08-10
Interesting I don't think xulrunner-2.0 is needed...

Its not listed as a dependency of firefox-4.0b4

Also the Firefox-4.0b4 file size is now 40MB... the same size as xulrunner...

This package comment seems to confirm it.

> 
[ Chris Coulson <[chris.coulson@canonical.com]("https://launchpad.net/%7Echrisccoulson")> ]
* Implement DEB_MIN_SYSDEPS approach that does not use system xulrunner
    and only a minimal set of system dependencies.
    + drop patches not required anymore:
      - delete debian/patches/dont_depend_on_nspr_sources.patch
      - update debian/patches/series
    + move .install lines that depend on whether MIN_SYS_DEPS is used or not
      to debian/rules in ifneq (,$(MIN_SYS_DEPS)) blocks
      - update debian/rules
      - update debian/firefox-4.0.install
    + ship gnome support .so's inside of the main package, but keep dependencies in
      the (now empty) gnome-support package; to achieve this, we first install
      the gnome support files in the -gnome-support package and move them to the
      main package _after_ shlib depends where generated
      - update debian/rules
    + **do not build-depend on xulrunner dev package anymore**; local xulrunner builds
      with DEB_MIN_SYSDEPS=0 should still work though
      - update debian/control
    + make firefox-4.0 conflict firefox-4.0-gnome-support as it shipps the gnome
      files directly now
      - update debian/control
    + copy some patches from xulrunner
      - add debian/patches/add_syspref_dir.patch
      - add debian/patches/bz467738_att351145_lockPref_everywhere.patch
      - add debian/patches/lp548866_bz467766_att351173-dont-reset-user-prefs-on-upgrade.patch
      - add debian/patches/bzXXX_plugin_for_mimetype_pref.patch
      - update debian/patches/series
Off to test this out :-)

UPDATE

> :~$ sudo apt-get install firefox-4.0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
**The following extra packages will be installed:**
  firefox-4.0-branding
**Suggested packages:**
 firefox-4.0-gnome-support
The following NEW packages will be installed
  firefox-4.0 firefox-4.0-branding
0 upgraded, 2 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B/14.0MB of archives.
After this operation, 41.9MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Selecting previously deselected package firefox-4.0-branding.
(Reading database ... 235048 files and directories currently installed.)
Unpacking firefox-4.0-branding (from .../firefox-4.0-branding_4.0~b4~hg20100809r49183+nobinonly-0ubuntu1~umd1~lucid_amd64.deb) ...
Selecting previously deselected package firefox-4.0.
Unpacking firefox-4.0 (from .../firefox-4.0_4.0~b4~hg20100809r49183+nobinonly-0ubuntu1~umd1~lucid_amd64.deb) ...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_GB.utf8.cache...
Processing triggers for menu ...
Processing triggers for python-support ...
Setting up firefox-4.0-branding (4.0~b4~hg20100809r49183+nobinonly-0ubuntu1~umd1~lucid) ...
Setting up firefox-4.0 (4.0~b4~hg20100809r49183+nobinonly-0ubuntu1~umd1~lucid) ...
Please restart all running instances of firefox-4.0, or you will experience problems.

Processing triggers for menu ...
:~$ 

---

### Post by lovinglinux on 2010-08-10
> **SilverWave said:**
> Interesting I don't think xulrunner-2.0 is needed...

Its not listed as a dependency of firefox-4.0b3

Also the Firefox-4.0b3 file size is now 40MB... the same size as xulrunner...

This package comment seems to confirm it.

Off to test this out :-)

UPDATE

They are probably shipping xulrunner with Firefox, to avoid dependency issues. They have done that before, after Mozilla announced the new minor-major update policy.

This was included in the new policy blueprint.

---

### Post by SilverWave on 2010-08-10
> **lovinglinux said:**
> They are probably shipping xulrunner with Firefox, to avoid dependency issues. They have done that before, after Mozilla announced the new minor-major update policy.

This was included in the new policy blueprint.

True, true, but xulrunner was still needed the last time I updated the 4.0 ppa's so its nice to see that they are on target.

I have retested everything in vm's again, without xulrunner being present in the ppa's, and can confirm that they all still work :-)

Heh one less think to worry about, even though its not strictly best practice ;-)

---

### Post by lovinglinux on 2010-08-10
> **SilverWave said:**
> True, true, but xulrunner was still needed the last time I updated the 4.0 ppa's so its nice to see that they are on target.

Indeed. Last time I tried FF 4 from the repos it did install xulrunner. I'm running b3 from Mozilla tho.

BTW, I have posted a Firefox 4 support thread, with links to your PPA, plus tips on optimization and customization.

[http://ubuntuforums.org/showthread.php?t=1544124](http://ubuntuforums.org/showthread.php?t=1544124)

Firefox 4 rocks!

I can't wait to get TabCandy and the new UI. I'm also waiting for 27 extensions updates, since they don't even work with compatibility check disabled. I have 51 extensions that work tho.

---

### Post by SilverWave on 2010-08-11
> **lovinglinux said:**
> ...Firefox 4 rocks!

I can't wait to get TabCandy and the new UI. I'm also waiting for 27 extensions updates, since they don't even work with compatibility check disabled. I have 51 extensions that work tho.

Well, I like FF4.0 but it is not able to replace FF3.6 in my workflow yet as my extensions are such a key part of the game for me.

There has been a lot of changes to the firefox internals so I would expect there will be a lot of extension breakage :-(

Oh well hopefully with Jetpack, eventually, this will be a thing of the past!

---

### Post by klepto on 2010-08-11
I updated to grab Firefox 4 Beta 4Pre and there's a nasty bug:


klepto@LUNASYLUM /usr/lib/firefox-4.0b4pre $ firefox-4.0
exec: 159: usr/lib/firefox-4.0b4pre/run-mozilla.sh: not found
klepto@LUNASYLUM /usr/lib/firefox-4.0b4pre $ ./run-mozilla.sh 

run-mozilla.sh: Cannot execute .

---

### Post by SilverWave on 2010-08-11
> **klepto said:**
> I updated to grab Firefox 4 Beta 4Pre and there's a nasty bug:


klepto@LUNASYLUM /usr/lib/firefox-4.0b4pre $ firefox-4.0
exec: 159: usr/lib/firefox-4.0b4pre/run-mozilla.sh: not found
klepto@LUNASYLUM /usr/lib/firefox-4.0b4pre $ ./run-mozilla.sh 

run-mozilla.sh: Cannot execute .

Please provide more information.

Did you use a PPA or download direct from Mozilla?
If you did use a PPA, which PPA did you use?

Which package did you install?
Are you running 64bit or 32bit?
Are you running Lucid or Karmic?

Note that I have tested the packages in my silverwave PPA's and they worked OK.

Please post the results of the command "apt-cache policy firefox-4.0"

> E.G.
:~$ apt-cache policy firefox-4.0
firefox-4.0:
  Installed: 4.0~b4~hg20100809r49183+nobinonly-0ubuntu1~umd1~lucid
  Candidate: 4.0~b4~hg20100809r49183+nobinonly-0ubuntu1~umd1~lucid
  Version table:
 *** 4.0~b4~hg20100809r49183+nobinonly-0ubuntu1~umd1~lucid 0
        500 [http://ppa.launchpad.net/silverwave/one-daily-a-month-1/ubuntu/](http://ppa.launchpad.net/silverwave/one-daily-a-month-1/ubuntu/) lucid/main Packages
        100 /var/lib/dpkg/status
:~$ 
[UPDATE]You wouldn't be running [Linuxmint]("http://forums.linuxmint.com/viewtopic.php?f=47&t=53188&p=305492") by any chance ;-)

---

### Post by SilverWave on 2010-08-13
[QUOTE=lovinglinux]I have asked a moderator to move our Jetpack discussion to a new thread. I hope you don't mind. I don't want to stop the discussion, but also don't want to hijack your thread, which seems was already happening.[/QUOTE]

Moved to [Jetpack Talk]("http://ubuntuforums.org/showthread.php?t=1552131")

---

### Post by SilverWave on 2010-08-13
[Mozilla bolting Tab Candy on to Firefox 4 today]("http://www.downloadsquad.com/2010/08/12/tab-candy-firefox-4/")

I wonder if I will end up using this...

I am happy with Tree Style Tabs... but this looks cool and it is built-in... hmmm.

---

### Post by lovinglinux on 2010-08-13
> **SilverWave said:**
> [Mozilla bolting Tab Candy on to Firefox 4 today]("http://www.downloadsquad.com/2010/08/12/tab-candy-firefox-4/")

I wonder if I will end up using this...

I am happy with Tree Style Tabs... but this looks cool and it is built-in... hmmm.

Wooohooo! I'm going to replace my 4.0b3 with the 4.0b4pre right away. Great news! Thanks for sharing.

---

### Post by lovinglinux on 2010-08-13
> **SilverWave said:**
> I wonder if I will end up using this...

I am happy with Tree Style Tabs... but this looks cool and it is built-in... hmmm.

Try it. I had tried it before, but now that is officially built in, I'm incorporating it into my workflow. I'm loving it. I can create groups of tabs and save them, so whenever I start the browser I have everything I need already opened, organized by activities. 

I would recommend using [BarTab]("https://addons.mozilla.org/en-US/firefox/addon/67651/"), to prevent the content from loading until you need it.

BTW, Firefox Sync is already built-in too. You can sync bookmarks, passwords, preferences, history and tabs.

Firefox 4 will definitely shake the browser market!

---

### Post by SilverWave on 2010-08-14
> **lovinglinux said:**
> Try it. I had tried it before, but now that is officially built in, I'm incorporating it into my workflow. I'm loving it. I can create groups of tabs and save them, so whenever I start the browser I have everything I need already opened, organized by activities. 

I would recommend using [BarTab]("https://addons.mozilla.org/en-US/firefox/addon/67651/"), to prevent the content from loading until you need it.

BTW, Firefox Sync is already built-in too. You can sync bookmarks, passwords, preferences, history and tabs.

Firefox 4 will definitely shake the browser market!
Already using "BarTab" with "TreeStyle Tabs" for instant start with 37 tabs, I honestly don't know how ppl work without it :-)

Oh re Sync, its vital with 6+ desktops, although tab integration isnt as good as I would like.

---

### Post by lovinglinux on 2010-08-14
> **SilverWave said:**
> Already using "BarTab" with "TreeStyle Tabs" for instant start with 37 tabs, I honestly don't know how ppl work without it :-)

Oh re Sync, its vital with 6+ desktops, although tab integration isnt as good as I would like.

I must admit I never tried "Tree Style Tabs" before because the screenshots on the extension page weren't very appealing to me. But I'm trying it now and I'm impressed with the quality and quantity of options. I guess it will take some time before I get used to it, but it is a lot better then scrolling the tabs on the top.

---

### Post by SilverWave on 2010-08-14
Wow TabCandy is fantastic!

Checking out the latest Firefox-4.0B4pre in my Testing PPA and I'm so impressed that I am going to publish an extra update to my "One Daily A Month" PPA's

This is the Firefox innovation that we have been missing!

---

### Post by lovinglinux on 2010-08-14
> **SilverWave said:**
> Wow TabCandy is fantastic!

Checking out the latest Firefox-4.0B4pre in my Testing PPA and I'm so impressed that I am going to publish an extra update to my "one daily a month" PPA's

This is the Firefox innovation that we have been missing!

You should try combining it with Speed Dial. You can put a copy of speed dial on every TabCandy group, and make each one use a different dial group. I'm going nuts with this stuff :)

BTW, anyone experiencing issues with saving TabCandy? When I restart the browser, my groups are reset.

---

### Post by SilverWave on 2010-08-14
Get your TabCandy goodness here ;-)

[firefox-4.0 - 4.0~b4~hg20100814r50538+nobinonly-0ubuntu1~umd1~lucid       ]("https://launchpad.net/%7Esilverwave/+archive/one-daily-a-month-1/+sourcepub/1267188/+listing-archive-extra")

[firefox-4.0 - 4.0~b4~hg20100814r50538+nobinonly-0ubuntu1~umd1~karmic       ]("https://launchpad.net/%7Esilverwave/+archive/one-daily-a-month-3/+sourcepub/1267191/+listing-archive-extra")


Also the latest 3.6.9pre

[firefox - 3.6.9~hg20100813r34524+nobinonly-0ubuntu1~umd1~lucid]("https://launchpad.net/%7Esilverwave/+archive/one-daily-a-month-0/+sourcepub/1267187/+listing-archive-extra")

[firefox - 3.6.9~hg20100813r34524+nobinonly-0ubuntu1~umd1~karmic       ]("https://launchpad.net/%7Esilverwave/+archive/one-daily-a-month-2/+sourcepub/1267190/+listing-archive-extra")

---

### Post by SilverWave on 2010-08-14
> **lovinglinux said:**
> 
BTW, anyone experiencing issues with saving TabCandy? When I restart the browser, my groups are reset.

Nope.

Just tested my 64bit Lucid and saving fine.

Maybe try my PPA and see if there is any difference, its a Daily from the 14th.

If you are using Lucid...

sudo add-apt-repository  ppa:silverwave/one-daily-a-month-1
sudo apt-get update
sudo apt-get install firefox-4.0

---

### Post by lovinglinux on 2010-08-14
> **SilverWave said:**
> Nope.

Just tested my 64bit Lucid and saving fine.

Maybe try my PPA and see if there is any difference, its a Daily from the 14th.

If you are using Lucid...

sudo add-apt-repository  ppa:silverwave/one-daily-a-month-1
sudo apt-get update
sudo apt-get install firefox-4.0

The Mozilla build from 14th is not working well here. But I guess is because of many extensions I have forced to work or perhaps some settings that are deleting the tabs.

I'm using the build from Friday 13th. Wooooooo, scary :)

---

### Post by SilverWave on 2010-08-14
> **lovinglinux said:**
> ...because of many extensions I have forced to work...

hmm if I want to force an extension I usually install MrTech Toolbox or just bump the max version what's your preferred option?

Firefox-4.0 is starting to interest me so I may want to start playing with it again :-)

---

### Post by lovinglinux on 2010-08-14
> **SilverWave said:**
> hmm if I want to force an extension I usually install MrTech Toolbox or just bump the max version what's your preferred option?

I have used both in the past and also Nightly tester tools, but nowadays I prefer [Add-on Compatibility Reporter]("https://addons.mozilla.org/en-US/firefox/addon/15003/"), which is developed by Mozilla.

Currently, I have 50 extensions enabled and 26 disabled. Only 23 are fully compatible and among those, 11 are developed by me.

---

### Post by SilverWave on 2010-08-14
> **SilverWave said:**
> Nope.

Just tested my 64bit Lucid and saving fine.



Might have spoke too soon, with an upgraded profile, after some sorting into groups and bouncing firefox a few times I have noticed some issues...

Incorrect grouping and some missing pages etc..

I created a new profile and have seen some weirdness there as well.

Oh well, problems with such a new feature are only to be expected :-)

---

### Post by SilverWave on 2010-08-15
> **lovinglinux said:**
> I must admit I never tried "Tree Style Tabs" before because the screenshots on the extension page weren't very appealing to me. But I'm trying it now and I'm impressed with the quality and quantity of options. I guess it will take some time before I get used to it, but it is a lot better then scrolling the tabs on the top.

In that case you may wish to try [Informational Tab]("https://addons.mozilla.org/en-US/firefox/addon/4930/").
It works with "Tree Style Tabs" to provide small thumbnails of the tab.
It is  a good, low resource, way of identifying a page at a glance.
My settings are "Show Whole of Page", "36 Pixels", "Scroll Thumbnails too".

---

### Post by lovinglinux on 2010-08-15
> **SilverWave said:**
> In that case you may wish to try [Informational Tab]("https://addons.mozilla.org/en-US/firefox/addon/4930/").
It works with "Tree Style Tabs" to provide small thumbnails of the tab.
It is  a good, low resource, way of identifying a page at a glance.
My settings are "Show Whole of Page", "36 Pixels", "Scroll Thumbnails too".

I use "Tab Scope" bu thanks for the suggestion,.

---

### Post by lovinglinux on 2010-08-15
> **SilverWave said:**
> Might have spoke too soon, with an upgraded profile, after some sorting into groups and bouncing firefox a few times I have noticed some issues...

Incorrect grouping and some missing pages etc..

I created a new profile and have seen some weirdness there as well.

Oh well, problems with such a new feature are only to be expected :-)

It works fine if I restart the browser from the add-ons manager or using quick restart extension. It resets if I close Firefox and open it again. Additionally, if I restart Ubuntu without closing Firefox, then it works fine.

BTW, I'm loving "Tree Style Tabs".

---

### Post by lovinglinux on 2010-08-15
I have made a video showing TabCandy, SpeedDial, TabScope and Tree Style Tab in action together.

[http://lovinglinuxblog.blogspot.com/2010/08/firefox-4-tab-show.html](http://lovinglinuxblog.blogspot.com/2010/08/firefox-4-tab-show.html)

---

### Post by SilverWave on 2010-08-15
> **lovinglinux said:**
> I have made a video showing TabCandy, SpeedDial, TabScope and Tree Style Tab in action together.

[http://lovinglinuxblog.blogspot.com/2010/08/firefox-4-tab-show.html](http://lovinglinuxblog.blogspot.com/2010/08/firefox-4-tab-show.html)

Great demo.

Here is my Firefox with "Tree Style Tabs", its a little different ;-)

[http://silverwav.files.wordpress.com/2010/06/screenshot-tabs-expanded.png](http://silverwav.files.wordpress.com/2010/06/screenshot-tabs-expanded.png)

[http://silverwav.files.wordpress.com/2010/06/screenshot-tabs-grouped.png](http://silverwav.files.wordpress.com/2010/06/screenshot-tabs-grouped.png)

As you can see I love the grouping feature in "Tree Style Tabs" and [Informational Tab]("https://addons.mozilla.org/en-US/firefox/addon/4930/") thumbnails.
Note: Both are from the same developer.

---

### Post by lovinglinux on 2010-08-15
> **SilverWave said:**
> Great demo.

Here is my Firefox with "Tree Style Tabs", its a little different ;-)

[http://silverwav.files.wordpress.com/2010/06/screenshot-tabs-expanded.png](http://silverwav.files.wordpress.com/2010/06/screenshot-tabs-expanded.png)

[http://silverwav.files.wordpress.com/2010/06/screenshot-tabs-grouped.png](http://silverwav.files.wordpress.com/2010/06/screenshot-tabs-grouped.png)

As you can see I love the grouping feature in "Tree Style Tabs" and [Informational Tab]("https://addons.mozilla.org/en-US/firefox/addon/4930/") thumbnails.
Note: Both are from the same developer.

Yep, the grouping feature is awesome.

---

### Post by lovinglinux on 2010-08-17
Firefox 4.0b4 candidates are available, with TabCandy. Nevertheless, Tree Style Tab and AdblockPlus doesn't work.

[ftp://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/4.0b4-candidates/](ftp://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/4.0b4-candidates/)

---

### Post by SilverWave on 2010-08-17
> **lovinglinux said:**
> Firefox 4.0b4 candidates are available, with TabCandy. Nevertheless, Tree Style Tab and AdblockPlus doesn't work.

[ftp://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/4.0b4-candidates/](ftp://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/4.0b4-candidates/)

**  Release Tracking & Schedule **

    **step**  **owner**  **date**  [B]status
[/B]code freeze on mozilla-central  beltzner, gavin  Aug 17  [b51b190b9fcc]("http://hg.mozilla.org/mozilla-central/rev/b51b190b9fcc") 
   build1 available  Aug 17, late PT  *estimated* 
   QA signoff  juanb  Aug 20, late PT  *estimated* 
   relnotes published  beltzner & pascalc  Aug 20, late PT  *estimated*    
websites pushed  beltzner & pascalc  Aug 23, early PT  *estimated* 
   release announced  beltzner  Aug 23, early PT  *estimated* 

Retrieved from "[https://wiki.mozilla.org/Releases/Firefox_4.0b4](https://wiki.mozilla.org/Releases/Firefox_4.0b4)"

---

### Post by SilverWave on 2010-08-22
In testing the first daily after the Firefox b4 I noticed that a new package **firefox-core** is installed. Details here:

> [ Chris Coulson <[chris.coulson@canonical.com]("https://launchpad.net/%7Echrisccoulson")> ] * Completely rework packaging layout after langing of (bmo: 556644) aka Enable     omnijar for desktop Firefox by default. We rename firefox-branding and     abrowser-branding to just firefox and abrowser. Each of these now depend     on **firefox-core** (which used to be firefox). firefox and abrowser each     ship a set of icons, desktop file, symlink in /usr/bin and an omni.jar     file with alternative branding. firefox-core ships all of the non-branded     and common components shared between the variants that aren't compressed in     omni.jar. We also introduce an abrowser-gnome-support which does the same     as firefox-gnome-support but registers /usr/bin/abrowser as an alternative     for gnome-www-browser
 - added debian/TODO     - added debian/abrowser-gnome-support.install.in
 - added debian/abrowser-gnome-support.postinst.in
 - renamed debian/abrowser-branding.install.in => debian/abrowser.install.in
 - renamed debian/abrowser-branding.links.in => debian/abrowser.links.in
 - renamed debian/firefox.dirs.in => debian/firefox-core.dirs.in
 - renamed debian/firefox.docs.in => debian/firefox-core.docs.in
 - renamed debian/firefox.install.in => debian/firefox-core.install.in
 - renamed debian/firefox.links.in => debian/firefox-core.links.in
 - renamed debian/firefox.postinst.in => debian/firefox-core.postinst.in
 - renamed debian/firefox.postrm.in => debian/firefox-core.postrm.in
 - renamed debian/firefox.preinst.in => debian/firefox-core.preinst.in
 - renamed debian/firefox.prerm.in => debian/firefox-core.prerm.in
 - renamed debian/firefox-branding.install.in => debian/firefox.install.in
 - renamed debian/firefox-branding.links.in => debian/firefox.links.in
 - update debian/abrowser.install.in     - update debian/abrowser.links.in
 - update debian/control     - update debian/firefox-core.install.in
 - update debian/firefox-core.links.in
 - update debian/firefox-gnome-support.postinst.in
 - update debian/firefox.install.in     - update debian/firefox.links.in
 - update debian/rules     - update debian/patches/browser_branding.patch
 * Unregister the gnome-www-browser alternatives on uninstall
 - add debian/firefox-gnome-support.prerm.in     - add debian/abrowser-gnome-support.prerm.in
 - update debian/rules 
  * There is currently no support for system-wide preferences with omnijar,     so we disable add_syspref_dir.patch and     bz467738_att351145_lockPref_everywhere.patch for now
 - update debian/patches/series 
  * Ensure that omni.jar is created when running "make install"
 - add debian/patches/bz588410_fix_make_install_with_omnijar.patch     - update debian/patches/series 


> 
**Firefox-4.0-core**
Firefox delivers safe, easy web browsing. A familiar user interface, enhanced security features including protection from online identity theft, and integrated search let you get the most out of the web.
This package contains the common components shared between the abrowser-4.0 and firefox-4.0 packages

---

### Post by SilverWave on 2010-08-22
First daily of Firefox-4.0 after 4.0b4

[firefox-4.0 - 4.0~b5~hg20100821r51155+nobinonly-0ubuntu1~umd1~lucid       ]("https://launchpad.net/%7Esilverwave/+archive/one-daily-a-month-1/+sourcepub/1274183/+listing-archive-extra")

sudo add-apt-repository  ppa:silverwave/one-daily-a-month-1
sudo apt-get update
sudo apt-get install firefox-4.0

[firefox-4.0 - 4.0~b5~hg20100821r51155+nobinonly-0ubuntu1~umd1~karmic       ]("https://launchpad.net/%7Esilverwave/+archive/one-daily-a-month-3/+sourcepub/1274184/+listing-archive-extra")

sudo add-apt-repository ppa:silverwave/one-daily-a-month-3
sudo apt-get update
sudo apt-get install firefox-4.0

All tested and now in production PPA's enjoy :-D

---

### Post by lovinglinux on 2010-08-24
Firefox Beta 4 is out. Is not available from the Beta page yet, but you can get it from Mozilla FTP site:

[ftp://ftp.mozilla.org/pub/mozilla.org/firefox/releases/4.0b4/](ftp://ftp.mozilla.org/pub/mozilla.org/firefox/releases/4.0b4/)

Are you able to run Tree Style Tabs? I'm stuck in Beta 3.

---

### Post by SilverWave on 2010-08-24
> **lovinglinux said:**
> ...

[ftp://ftp.mozilla.org/pub/mozilla.org/firefox/releases/4.0b4/](ftp://ftp.mozilla.org/pub/mozilla.org/firefox/releases/4.0b4/)

Are you able to run Tree Style Tabs? I'm stuck in Beta 3.

No :-( 

It just removes my Menu (tabs overwrite same area).

---

### Post by SilverWave on 2010-08-24
> **lovinglinux said:**
> Firefox Beta 4 is out. Is not available from the Beta page yet, but you can get it from Mozilla FTP site:


Or you can run the **Firefox 4.0b5pre** from my ppa's :-)

---

### Post by lovinglinux on 2010-08-24
> **SilverWave said:**
> No :-( 

It just removes my Menu (tabs overwrite same area).

Same here.

> **SilverWave said:**
> Or you can run the **Firefox 4.0b5pre** from my ppa's :-)

I'm stuck with 4.0b3, 4.0b5pre doesn't work with Tree Style Tab either.

---

### Post by lovinglinux on 2010-08-27
> **SilverWave said:**
> No :-( 

It just removes my Menu (tabs overwrite same area).

I have changed my Firefox 4 interface and workflow again. This time, I'm using a tabless setup. Tree Style Tabs and TabScope go out, FireGestures go in ;)

Video, how-to and explanation available in [my blog]("http://lovinglinuxblog.blogspot.com/2010/08/firefox-4-customization-tabless.html"). 

[IMG]http://tinyurl.com/232oe6j[/IMG]

---

### Post by SilverWave on 2010-09-01
> **lovinglinux said:**
> Same here.



I'm stuck with 4.0b3, 4.0b5pre doesn't work with Tree Style Tab either.


> **New UI Features**

 Beta 4 shipped with a new feature called [Firefox Panorama]("http://www.azarask.in/blog/post/designing-tab-candy")  (previously known as Tab Candy). This is a major new feature and a new  way to look at and manage tabs in Firefox. Unfortunately this also means  that some tab manager add-ons may break due to the changes introduced  in the Firefox tab code. I’ve been told that the changes to the tab code  are minimal, **but I know that at least Tree Style Tab (a personal  favorite) is broken since beta 4**. There’s a new button in the tab bar  that triggers Panorama, and also a context menu option.
[http://blog.mozilla.com/addons/2010/08/31/compatibility-firefox-4-beta-4/](http://blog.mozilla.com/addons/2010/08/31/compatibility-firefox-4-beta-4/)

---

### Post by lovinglinux on 2010-09-01
> **SilverWave said:**
> [http://blog.mozilla.com/addons/2010/08/31/compatibility-firefox-4-beta-4/](http://blog.mozilla.com/addons/2010/08/31/compatibility-firefox-4-beta-4/)

Yep. I've got that yesterday. I also got a message that extensions can now be compatible with 4.0b6pre. Fortunately, I didn't need to change my extensions code since b1, just the compatibility info.

---

### Post by lovinglinux on 2010-09-10
There is a new version of Tree Style Tab available, which is compatible with FF 4.0b6pre.

[https://addons.mozilla.org/en-US/firefox/addon/5890/versions/#version-0.10.2010091001](https://addons.mozilla.org/en-US/firefox/addon/5890/versions/#version-0.10.2010091001)

---

### Post by SilverWave on 2010-09-11
> **lovinglinux said:**
> There is a new version of Tree Style Tab available, which is compatible with FF 4.0b6pre.

[https://addons.mozilla.org/en-US/firefox/addon/5890/versions/#version-0.10.2010091001](https://addons.mozilla.org/en-US/firefox/addon/5890/versions/#version-0.10.2010091001)

Cheers I will give it a shot.

Been busy with RL stuff lately and had missed it.

---

### Post by lovinglinux on 2010-09-12
> **SilverWave said:**
> Cheers I will give it a shot.

Been busy with RL stuff lately and had missed it.

It's still buggy. :(

I have been very busy too, but I get the updates via rss feed. I'm monitoring many extensions.

---

### Post by lovinglinux on 2010-09-14
> **lovinglinux said:**
> It's still buggy. :(

There is a new beta version with many fixes.

---

### Post by SilverWave on 2010-09-19
First daily of Firefox-4.0 after 4.0b6

[firefox-4.0 - 4.0~b7~hg20100916r54125+nobinonly-0ubuntu1~umd1~lucid ]("https://launchpad.net/%7Esilverwave/+archive/one-daily-a-month-1/+sourcepub/1298128/+listing-archive-extra")

sudo add-apt-repository  ppa:silverwave/one-daily-a-month-1
sudo apt-get update
sudo apt-get install firefox-4.0

[        firefox-4.0 - 4.0~b7~hg20100916r54125+nobinonly-0ubuntu1~umd1~karmic       ]("https://launchpad.net/%7Esilverwave/+archive/one-daily-a-month-3/+sourcepub/1298131/+listing-archive-extra")

sudo add-apt-repository ppa:silverwave/one-daily-a-month-3
sudo apt-get update
sudo apt-get install firefox-4.0

All tested and now in production PPA's enjoy :grin:

---

### Post by SilverWave on 2010-09-19
Here are the latest 3.6 dailies.

[firefox - 3.6.11~hg20100915r34578+nobinonly-0ubuntu1~umd1~lucid       ]("https://launchpad.net/%7Esilverwave/+archive/one-daily-a-month-0/+sourcepub/1298127/+listing-archive-extra")

sudo add-apt-repository  ppa:silverwave/one-daily-a-month-0
sudo apt-get update
sudo apt-get install firefox

[        firefox - 3.6.11~hg20100915r34578+nobinonly-0ubuntu1~umd1~karmic       ]("https://launchpad.net/%7Esilverwave/+archive/one-daily-a-month-2/+sourcepub/1298156/+listing-archive-extra")

sudo add-apt-repository ppa:silverwave/one-daily-a-month-2
sudo apt-get update
sudo apt-get install firefox

All tested and now in production PPA's enjoy :grin:

---

### Post by SilverWave on 2010-10-07
**The release of of 3.6.12 dailies means 3.6.11 has been completed.**

Changes for the versions:
3.6.11~hg20100915r34578+nobinonly-0ubuntu1~umd1~lucid
3.6.12~hg20101004r34661+nobinonly-0ubuntu1~umd1~lucid

This change is not from a source that supports changelogs.

Just added to Testing for the moment.

---

### Post by SilverWave on 2010-10-07
**The release of of 4.0~b8**** dailies means 4.0~b7**[B] has been completed.

[/B]Changes for the versions:
4.0~b7~hg20100916r54125+nobinonly-0ubuntu1~umd1~lucid
4.0~b8~hg20101007r55015+nobinonly-0ubuntu1~umd1~lucid

This change is not from a source that supports changelogs.

Just added to Testing for the moment.

---

### Post by SilverWave on 2010-10-07
> **SilverWave said:**
> **The release of of 4.0~b8**** dailies means 4.0~b7**[B] has been completed.

[/B]Changes for the versions:
4.0~b7~hg20100916r54125+nobinonly-0ubuntu1~umd1~lucid
4.0~b8~hg20101007r55015+nobinonly-0ubuntu1~umd1~lucid

This change is not from a source that supports changelogs.

Just added to Testing for the moment.



First daily of Firefox-4.0 after 4.0b7
**Lucid**
sudo add-apt-repository  ppa:silverwave/one-daily-a-month-1
sudo apt-get update
sudo apt-get install firefox-4.0
**Karmic**
sudo add-apt-repository ppa:silverwave/one-daily-a-month-3
sudo apt-get update
sudo apt-get install firefox-4.0

All tested and now in production PPA's enjoy :grin:

---

### Post by SilverWave on 2010-10-07
> **SilverWave said:**
> **The release of of 3.6.12 dailies means 3.6.11 has been completed.**

Changes for the versions:
3.6.11~hg20100915r34578+nobinonly-0ubuntu1~umd1~lucid
3.6.12~hg20101004r34661+nobinonly-0ubuntu1~umd1~lucid

This change is not from a source that supports changelogs.

Just added to Testing for the moment.

Here are the latest 3.6 dailies.
[B]
Lucid[/B] 
sudo add-apt-repository  ppa:silverwave/one-daily-a-month-0
sudo apt-get update
sudo apt-get install firefox

**Karmic**
sudo add-apt-repository ppa:silverwave/one-daily-a-month-2
sudo apt-get update
sudo apt-get install firefox

All tested and now in production PPA's enjoy :grin:

---

### Post by SilverWave on 2010-10-07
in about:config

Set:
general.useragent.compatMode.firefox

To true.

This allows extensions at AMO to be installed.

---

### Post by SilverWave on 2010-10-07
This has got a lot harder to do with 4.0 the best way is to download the xpi from AMO and alter the max ver.

1. find the extension on AMO 
[https://addons.mozilla.org/af/firefox/addon/5890/](https://addons.mozilla.org/af/firefox/addon/5890/)
right click the link or dl button and "save as" to your desktop.

e.g.
tree_style_tab-0.10.2010091901-fx.xpi

If you get some odd name then go to "       [         View all versions       ]("https://addons.mozilla.org/af/firefox/addon/5890/versions/")     "

Then try again.

One you have it on your desktop click it to open the archive.

Locate the "install.rdf" file and click it.

gedit opens up locate the firefox section:

```
        <!-- Firefox --> 
        <em:targetApplication> 
            <Description> 
                <em:id>{ec8030f7-c20a-464f-9b0e-13a3a9e97384}</em:id> 
                <em:minVersion>1.5</em:minVersion> 
                <em:maxVersion>4.*</em:maxVersion>
```bump to 4.* as I have.

Save save done.

The final trick is to open the addons manager and drag and drop the xpi from your desktop to the managers page.

This will install it!

Done :-)

**Note: Don't forget if you are using Minefield to do this 1st:**
> **SilverWave said:**
> in about:config

Set:
general.useragent.compatMode.firefox

To true.

This allows extensions at AMO to be installed.

I have successfully installed:
NewTabURL 2.20
Readability 1.2
Tree Style Tab 0.10.2010091901 (some issues)
ToolbarButtons - buttons for "add-ons" and "options", show/hide Menu, clean data etc..

Failed
NoSquint - installed but does not work.
RequestPolicy  - installed but does not work.


YMMV (I save my profile prior to installing .... so I can go back if the install goes wrong) :D

I should note that Adblock 1.3a.20101002 works fine but I went to his site for a dev copy no bumping needed.

---

### Post by iClouseau88 on 2010-10-09
Hi,

Do you have the latest Firefox PPA for Maverick (RC)?

Thanks in advance!

---

### Post by lovinglinux on 2010-10-09
> **SilverWave said:**
> This has got a lot harder to do with 4.0 the best way is to download the xpi from AMO and alter the max ver.

1. find the extension on AMO 
[https://addons.mozilla.org/af/firefox/addon/5890/](https://addons.mozilla.org/af/firefox/addon/5890/)
right click the link or dl button and "save as" to your desktop.

e.g.
tree_style_tab-0.10.2010091901-fx.xpi

If you get some odd name then go to "       [         View all versions       ]("https://addons.mozilla.org/af/firefox/addon/5890/versions/")     "

Then try again.

One you have it on your desktop click it to open the archive.

Locate the "install.rdf" file and click it.

gedit opens up locate the firefox section:

```
        <!-- Firefox --> 
        <em:targetApplication> 
            <Description> 
                <em:id>{ec8030f7-c20a-464f-9b0e-13a3a9e97384}</em:id> 
                <em:minVersion>1.5</em:minVersion> 
                <em:maxVersion>4.*</em:maxVersion>
```bump to 4.* as I have.

Save save done.

The final trick is to open the addons manager and drag and drop the xpi from your desktop to the managers page.

This will install it!

Done :-)

**Note: Don't forget if you are using Minefield to do this 1st:**


I have successfully installed:
NewTabURL 2.20
Readability 1.2
Tree Style Tab 0.10.2010091901 (some issues)
ToolbarButtons - buttons for "add-ons" and "options", show/hide Menu, clean data etc..

Failed
NoSquint - installed but does not work.
RequestPolicy  - installed but does not work.


YMMV (I save my profile prior to installing .... so I can go back if the install goes wrong) :D

I should note that Adblock 1.3a.20101002 works fine but I went to his site for a dev copy no bumping needed.

I wouldn't recommend doing that. It is a lot simpler and safer to use [Addon Compatibility Reporter]("https://addons.mozilla.org/en-US/firefox/addon/15003/") extension. If you want to disable compatibility check manually, then you need to add the proper **about[noparse]:[/noparse]config** entries. For Firefox 4.0b8pre would be **extensions.checkCompatibility.4.0b** and the value **false**.

---

### Post by SilverWave on 2010-10-09
> **lovinglinux said:**
> I wouldn't recommend doing that. It is a lot simpler and safer to use [Addon Compatibility Reporter]("https://addons.mozilla.org/en-US/firefox/addon/15003/") extension. If you want to disable compatibility check manually, then you need to add the proper **about:config** entries. For Firefox 4.0b8pre would be **extensions.checkCompatibility.4.0b** and the value **false**.

We will have to agree to disagree :-)
[B]
I think Mozilla have made a mistake in making it so hard to use old extensions if I want to.[/B]

1. I have tried the "Addon Comparability Reporter" and its not a good replacement for Nightly Tester Tools. Also the interface is cluttered and confusing.

2. The about:config setting never seems to work correctly.

On the contrary I would argue that:  

My way of bumping the max.version is simple and robust.

Also if I save the extension, then I only ever need to do this once regardless of the different versions of Firefox 4 :-)

A caveat I would note is that you do need to know what you are doing! But if you don't then you have no one to blame but your self ;-)

Its a freedom thing.

---

### Post by SilverWave on 2010-10-09
> **iClouseau88 said:**
> Hi,

Do you have the latest Firefox PPA for Maverick (RC)?

Thanks in advance!

Hmm... I'm considering it but as I will not be using Maverick, I'm not sure.

TBH I cant see any "must have" features in Maverick and Lucid is a long term release...

If I do I will need to stop supporting Karmic, as I only have a limited amount of time for testing etc..

**If anyone else would like a Maverick PPA... post a comment so I can see if there is any demand for it.**

Cheers.

---

### Post by lovinglinux on 2010-10-09
> **SilverWave said:**
> We will have to agree to disagree :-)
[B]
I think Mozilla have made a mistake in making it so hard to use old extensions if I want to.[/B]

1. I have tried the "Addon Comparability Reporter" and its not a good replacement for Nightly Tester Tools. Also the interface is cluttered and confusing.

2. The about:config setting never seems to work correctly.

On the contrary I would argue that:  

My way of bumping the max.version is simple and robust.

Also if I save the extension, then I only ever need to do this once regardless of the different versions of Firefox 4 :-)

A caveat I would note is that you do need to know what you are doing! But if you don't then you have no one to blame but your self ;-)

Its a freedom thing.

I will have to agree to disagree :-)

The "Addon Comparability Reporter" is pretty simple imo. Just need to install it and forget about it. 
The method you use is problematic because once you update the extension it will no longer work, since the install.rdf file is replaced. Additionally, Firefox 4 no longer extract the contents of extensions xpi files, so you will have to extract the xpi after each update, modify it and replace the xpi in the extension folder. If you have a lot of extensions this will be a pita. It is way much simpler using "Addon Comparability Reporter".

---

### Post by lovinglinux on 2010-10-09
> **SilverWave said:**
> TBH I cant see any "must have" features in Maverick and Lucid is a long term release...

I must agree with you. I'm skipping the upgrade for the first time in a long time. I'm happy with Lucid and didn't have a good experience with Maverick Beta.

---

### Post by SilverWave on 2010-10-09
> **lovinglinux said:**
> I will have to agree to disagree :-)

The method you use is problematic because once you update the extension it will no longer work, since the install.rdf file is replaced.

hmm I don't understand you there... I have done this with the extensions mentioned successfully and that is with the new FF4.b8.

> **lovinglinux said:**
> 
 Additionally, Firefox 4 no longer extract the contents of extensions xpi files, so you will have to extract the xpi after each update, modify it and replace the xpi in the extension folder. If you have a lot of extensions this will be a pita. It is way much simpler using "Addon Comparability Reporter".

hmm again I'm not sure what you mean, I do it this way because it is so simple. 

Download extension.
Double click extension.
Double click install.rdf
Update max.version to 4.*
Save
Save
Done

This is a very simple procedure, no?

---

### Post by lovinglinux on 2010-10-09
> **SilverWave said:**
> hmm I don't understand you there... I have done this with the extensions mentioned successfully and that is with the new FF4.b8.

I works, but once you get an extension update, it will no longer works, because the install.rdf file is replaced. In fact, the entire xpi file is replaced on every extension update.

> **SilverWave said:**
> hmm again I'm not sure what you mean, I do it this way because it is so simple. 

Download extension.
Double click extension.
Double click install.rdf
Update max.version to 4.*
Save
Save
Done

This is a very simple procedure, no?

Maybe for one or two extensions that are not updated frequently, but why I would want to do that with 60 extensions, if I can do it automatically with Add-on Compatibility Reporter"?

You are missing the point that you need to do the procedure again for every extension that gets updated, regardless of Firefox 4 version you are using.

---

### Post by SilverWave on 2010-10-09
> **lovinglinux said:**
> I works, but once you get an extension update, it will no longer works, because the install.rdf file is replaced. In fact, the entire xpi file is replaced on every extension update.[...]

Oh I see your point, but I don't think it applies...

1. I am only using this method to force install of extensions that don't work with FF4.0b8

So if they update the extension to work with FF4.0b8 that's cool :-)

2. Also I can drag and drop multiple xpi files so numbers shouldn't be an issue.
Also this is just to test ff4 so I only install the core extensions I cant do without.

3. I could also stop auto updates if needed.
Tools > Add-ons Manager > Automatic Updates Default/On/Off.

---

### Post by SilverWave on 2010-10-09
As Firefox 4 rushes to RC status I thought it was high time I started using it in anger.

I have been testing FF4 but up to now it was evolving at too fast a pace for me to use day to day.

Even now I could not use it as a complete replacement for my Firefox 3.6 and its 35 extensions... so what to do?

**Well my solution may be a little extreme ;-) but it gets the job done. **

I have just added another Samsung TFT to my original and now with 2 monitors, I can have my cake (A stable and extension perfect Firefox 3.6) as well as eat it (Get used to Firefox 4.0).

**The key I have found is to use Firefox Sync between the two Firefox versions**, this means my password and bookmarks are available on both profiles as well as tabs... so so cool :-)

Anyway I am finally testing Firefox 4 with a will and finding ways of working around issues of missing extensions etc., without being tripped up by the same in my day to day browsing... I just switch between them instantly.

Eat Cake - Have Cake.

LOL

---

### Post by SilverWave on 2010-10-09
:-)

Hey!

Just tested Firefox 4.08b and after the 1st JS query on a HUGE table being a little slow, following queries were as fast as Chromium!

WHOOT!

Initial page load was a LOT better as well :-)

The page is 11MB (Total Rows 22983) .... heh

I was using Chromium just for this one task... but maybe I can dump it for Firefox 4? Well Well....

Are We Fast Now?

Maybe... maybe... we are? :-D

---

### Post by lovinglinux on 2010-10-09
> **SilverWave said:**
> :-)

Hey!

Just tested Firefox 4.08b and after the 1st JS query on a HUGE table being a little slow, following queries were as fast as Chromium!

WHOOT!

Initial page load was a LOT better as well :-)

The page is 11MB (Total Rows 22983) .... heh

I was using Chromium just for this once task... but maybe I can dump it for Firefox 4? Well Well....

Are We Fast Now?

Maybe... maybe... we are? :-D

I'm still having issues with Bookmark search performance due to Sqlite 3.7, but this has been reported already.

While 4.0b8pre is already available, we still don't have a 4.0b7. It seems they are working on b8pre and b7pre simultaneously now, because of the issues blocking b7 release. It also seems we won't see Firefox 4 final until next year.

---

### Post by SilverWave on 2010-10-09
> **lovinglinux said:**
> [...]While 4.0b8pre is already available, we still don't have a 4.0b7. It seems they are working on b8pre and b7pre simultaneously now, because of the issues blocking b7 release. It also seems we won't see Firefox 4 final until next year.

Well the schedule **always** slips, LOL so that's par for the course, and TBH I am not worried as they are doing an insane amount of fundamental changes and it would be a miracle if they all went smoothly.

Also this means that end of support for Firefox 3.6 will be pushed back further so... hmm I'm a little conflicted I guess ;-)

---

### Post by lovinglinux on 2010-10-09
> **SilverWave said:**
> Well the schedule **always** slips, LOL so that's par for the course, and TBH I am not worried as they are doing an insane amount of fundamental changes and it would be a miracle if they all went smoothly.

I agree. The only problem I see is that some developers choose to update their extensions only after the final release, so until then we can be sure if some extensions will be updated or if their developers are no longer supporting them.

I'm trying to replace extensions that haven't been updated yet with other extensions that are already compatible, but some of them can't be replaced.

> **SilverWave said:**
> Also this means that end of support for Firefox 3.6 will be pushed back further so... hmm I'm a little conflicted I guess ;-)

I'm not. As soon as everybody moves to 4.0 the better for me, because then they will be forced to upgrade their extensions. There are many users that still use old versions of my extensions and that bothers me a little.

---

### Post by SilverWave on 2010-10-09
Test post from htc desire.

I have took the plunge and installed the mobile firefox b1.

Not perfect yet, but it's almost usable.

The killer feature is sync.

Main issue is a lack of text re-flow on pinch zoom and scrolling in landscape.

Still from nowhere to this beta 1 is a great leap forward.

---

### Post by SilverWave on 2010-10-11
I was considering dropping support for Karmic so I could include Maveric.
> "If I do I will need to stop supporting Karmic, as I only have a limited amount of time for testing etc..But I have a better solution.

The part of the work that I do, in connection with the PPA's, that does not scale well is the [B]testing.
[/B]
__________________
[B] 
I test each of the new packages in a VM[/B]

Karmic Firefox 4 32Bit
Karmic Firefox 4 64Bit
Lucid Firefox 4 32Bit
Lucid Firefox 4 64Bit

Karmic Firefox 3.6 32Bit
Karmic Firefox 3.6 64Bit
Lucid Firefox 3.6 32Bit
Lucid Firefox 3.6 64Bit

So that's 8 x VM's to manage and update etc., etc..

Adding Maverick would add another 4... which would be unsustainable.

Another interesting fact is that in all the testing I have not had a single problem with a package :-)

__________________

**With this in mind I am going to make some changes in how I run my "One Daily A Month" PPA's.**

The "One Daily A Month" PPA's will continue to be updated once a month, but the only testing will be on "Lucid Firefox 4 64Bit" (as I use this day today).

I will be adding PPA's for Maverick shortly.

I also have PPA's "testing1 (Lucid ) and "testing2" (Karmic) which I previously used for testing Firefox 3.6 and Firefox 4.

I will be re purposing these for "One Daily A Week" use.
__________________

**That is, with the time I will have freed up I can now offer more choices.**

_Updated: Monthly_
 Firefox-3.6 - One Daily A Month #0 - Lucid
Firefox-4.0 - One Daily A Month #1 - Lucid
Firefox-3.6 - One Daily A Month #2 - Karmic
Firefox-4.0 - One Daily A Month #3 - Karmic
Firefox-3.6 - One Daily A Month #4 - Maverick
Firefox-4.0 - One Daily A Month #5 - Maverick

_Updated: Weekly_
One Daily A Week - Testing #0 - Lucid (Firefox-3.6 & 4.0)
One Daily A Week - Testing #1 - Karmic (Firefox-3.6 & 4.0)
One Daily A Week - Testing #2 - Maverick (Firefox-3.6 & 4.0)

You can add whichever PPA suits you best.

I should be able to get this done by the end of today.

---

### Post by SilverWave on 2010-10-11
> **iClouseau88 said:**
> Hi,

Do you have the latest Firefox PPA for Maverick (RC)?

Thanks in advance!

Here you go:

```
 sudo add-apt-repository ppa:silverwave/testing3
```[**Packages in “One Daily A Week #2 - Maverick”**]("https://launchpad.net/%7Esilverwave/+archive/testing2/+packages")

[firefox - 3.6.12~hg20101010r34670+nobinonly-0ubuntu1~umd1       ]("https://launchpad.net/%7Esilverwave/+archive/testing3/+sourcepub/1333223/+listing-archive-extra")

[firefox-4.0 - 4.0~b8~hg20101009r55239+nobinonly-0ubuntu1~umd1       ]("https://launchpad.net/%7Esilverwave/+archive/testing3/+sourcepub/1333222/+listing-archive-extra")

---

### Post by SilverWave on 2010-10-11
**PPA description**

      The latest firefox without the update hassle.
 One daily a month from ubuntu-mozilla-daily.
______________________________
 Firefox-3.6 - One Daily A Month #4 - Maverick
One update a month.
Firefox only.
______________________________
 sudo add-apt-repository ppa:silverwave/one-daily-a-month-4
sudo apt-get update
sudo apt-get install firefox
______________________________


> 
Packages:

                 3.6.12~hg20101010r34670+nobinonly-0ubuntu1~umd1

---

### Post by SilverWave on 2010-10-11
**PPA description**

      The latest firefox without the update hassle.
 One daily a month from ubuntu-mozilla-daily.
______________________________
 Firefox-4.0 - One Daily A Month #5 - Maverick
One update a month.
Firefox only.
______________________________
 sudo add-apt-repository ppa:silverwave/one-daily-a-month-5
sudo apt-get update
sudo apt-get install firefox-4.0
______________________________
 

> 
Packages:
firefox-4.0                                               4.0~b8~hg20101009r55239+nobinonly-0ubuntu1~umd1

---

### Post by SilverWave on 2010-10-12
I have updated this tutorial's first post with the new PPA's and Maverick details [[here]]("http://ubuntuforums.org/showthread.php?t=1352580")

You may want to look there first :smile:

Also same place for details on this addition:

> [I]**One Daily A Week **(from ubuntu-mozilla-daily).
 The latest firefox without the update hassle[/I].

[LIST]
[*]One ppa per Ubuntu Version (containing both Firefox 4.0 & Firefox 3.6).
[*]Updated at the start of each Week
[/LIST]


---

### Post by iClouseau88 on 2010-10-12
Hello,

I am running Maverick on a x86_64 system.  Just installed FF 3.6.12-pre Namoroka via your one-daily-a-month ppa. Firefox runs OK but I got the following error message:

Javascript Application
Error: Component is not available

I did enable javacript for distrowatch and ubuntuforums sites.
Please help me!  Thanks a lot!

---

### Post by iClouseau88 on 2010-10-12
Hi,
 
I solved the above problem with "Javascript Application Error: Component not available" by removing the ppa line for 3.6.12-pre, uninstalling firefox, unticking the remaining ppa line (per one of the posts) for firefox 4,refreshing/reloading Synaptic and re-installing firefox.  So now I got both firefox (i.e.3.6.10 (Ubuntu branding)) and firefox 4.0b08.  This is great!

However, now I cannot get into Synaptic to put the ppa line for Firefox 4 back, in case it has to be updated on the first day of each month to come.  Here's the error message:

```

E: Type 'ain' is not known on line 3 in source list /etc/apt/sources.list.d/silverwave-one-daily-a-month-5-maverick.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

```

I never typed "ain" into the sources.list file.  Don't know how this happened.  How do I go to the repository dialog? Please help!

:confused:

---

### Post by iClouseau88 on 2010-10-12
Hi,

PROBLEM SOLVED! Thanks to plucky's Post#7 dated Jan. 10/2010 "Howto repair/reinstall Synaptic Package Manager (thread#855267)":

```

$ [COLOR="Blue"]cat /etc/apt/sources.list.d[/COLOR]/silverwave-one-daily-a-month-5-maverick.list

```
shows:

```
deb http://ppa.launchpad.net/silverwave/one-daily-a-month-5/ubuntu maverick main
deb-src http://ppa.launchpad.net/silverwave/one-daily-a-month-5/ubuntu maverick main
[COLOR="Blue"]ain[/COLOR]

```

Solution:
```

sudo gedit /etc/apt/sources.list.d/silverwave-one-daily-a-month-5-maverick.list

```

then remove "ain" from the last line of the above file and save.

Now I got Synaptic Package Manager back!

---

### Post by SilverWave on 2010-10-12
> **iClouseau88 said:**
> Hi,

PROBLEM SOLVED! Thanks to plucky's Post#7 dated Jan. 10/2010 "Howto repair/reinstall Synaptic Package Manager (thread#855267)":

```

$ [COLOR=Blue]cat /etc/apt/sources.list.d[/COLOR]/silverwave-one-daily-a-month-5-maverick.list

```shows:

```
deb http://ppa.launchpad.net/silverwave/one-daily-a-month-5/ubuntu maverick main
deb-src http://ppa.launchpad.net/silverwave/one-daily-a-month-5/ubuntu maverick main
[COLOR=Blue]ain[/COLOR]

```Solution:
```

sudo gedit /etc/apt/sources.list.d/silverwave-one-daily-a-month-5-maverick.list

```then remove "ain" from the last line of the above file and save.

Now I got Synaptic Package Manager back!

Wow that was very odd, but you fixed it!

hmm I supose it it could be "main" with the "m" missing...

---

### Post by SilverWave on 2010-10-12
> **iClouseau88 said:**
> Hello,

I am running Maverick on a x86_64 system.  Just installed FF 3.6.12-pre Namoroka via your one-daily-a-month ppa. Firefox runs OK but I got the following error message:

Javascript Application
Error: Component is not available

I did enable javacript for distrowatch and ubuntuforums sites.
Please help me!  Thanks a lot!

I have tested this again myself in a VM and I don't get any errors.
So... it could be a one off or it may be your installation of Maverick.

---

### Post by SilverWave on 2010-10-15
> **lovinglinux said:**
> I'm still having issues with Bookmark search performance due to Sqlite 3.7, but this has been reported already.

While 4.0b8pre is already available, we still don't have a 4.0b7. It seems they are working on b8pre and b7pre simultaneously now, because of the issues blocking b7 release. It also seems we won't see Firefox 4 final until next year.

[http://www.h-online.com/open/news/item/Firefox-4-falling-behind-schedule-1108796.html](http://www.h-online.com/open/news/item/Firefox-4-falling-behind-schedule-1108796.html)

> Mozilla has missed the [scheduled]("https://wiki.mozilla.org/Releases")  date for releasing Firefox 4 Beta 7. The update was originally due in  the last two weeks of September, but did not appear then or later. At  Mozilla's most [recent developer meeting]("https://wiki.mozilla.org/Platform/2010-10-12"),  there were 17 blockers, problems which could be a reason for delaying a  release, for the beta 7 release and an overall total of 901 blockers in  the queue for the eventual Firefox 4 release. 

Hmm... 901, that's a Lot of blockers!

---

### Post by SilverWave on 2010-10-15
Changes for the versions:
3.6.12~hg20101004r34661+nobinonly-0ubuntu1~umd1~lucid
3.6.12~hg20101012r34674+nobinonly-0ubuntu1~umd1~lucid

This change is not from a source that supports changelogs.

Changes for the versions:
4.0~b8~hg20101007r55015+nobinonly-0ubuntu1~umd1~lucid
4.0~b8~hg20101015r55834+nobinonly-0ubuntu1~umd1~lucid

This change is not from a source that supports changelogs.

---

### Post by lovinglinux on 2010-10-15
> **SilverWave said:**
> Hmm... 901, that's a Lot of blockers!

Indeed :)

---

### Post by SilverWave on 2010-10-19
> **lovinglinux said:**
> I wouldn't recommend doing that. It is a lot simpler and safer to use [Addon Compatibility Reporter]("https://addons.mozilla.org/en-US/firefox/addon/15003/") extension. If you want to disable compatibility check manually, then you need to add the proper **about[noparse]:[/noparse]config** entries. For Firefox 4.0b8pre would be **extensions.checkCompatibility.4.0b** and the value **false**.

Hmm interesting!
**[Nightly Tester Tools Resurrection]("http://harthur.wordpress.com/2010/10/18/nightly-tester-tools-resurrection/")**

---

### Post by SilverWave on 2010-10-23
Changes for the versions:
3.6.12~hg20101012r34674+nobinonly-0ubuntu1~umd1~lucid
3.6.12~hg20101022r34696+nobinonly-0ubuntu1~umd1~lucid

This change is not from a source that supports changelogs.

Changes for the versions:
4.0~b8~hg20101015r55834+nobinonly-0ubuntu1~umd1~lucid
4.0~b8~hg20101020r56162+nobinonly-0ubuntu1~umd1~lucid

This change is not from a source that supports changelogs.

---

### Post by SilverWave on 2010-10-31
Changes for the versions:
3.6.12+build1+nobinonly-0ubuntu0.10.04.1
3.6.13~hg20101029r34715+nobinonly-0ubuntu1~umd1~lucid

This change is not from a source that supports changelogs.

Changes for the versions:
4.0~b8~hg20101025r56422+nobinonly-0ubuntu1~umd1~lucid
4.0~b8~hg20101031r56708+nobinonly-0ubuntu1~umd1~lucid

This change is not from a source that supports changelogs.

---

### Post by SilverWave on 2010-11-01
> **SilverWave said:**
> 
3.6.13~hg20101029r34715+nobinonly-0ubuntu1~umd1~lucid

4.0~b8~hg20101031r56708+nobinonly-0ubuntu1~umd1~lucid


All the ppa's updated: for:
Lucid
Maverick
Karmic

---

### Post by SilverWave on 2010-11-11
Changes for the versions:
4.0~b8~hg20101031r56708+nobinonly-0ubuntu1~umd1~lucid
4.0~b8~hg20101110r57184+nobinonly-0ubuntu1~umd1~lucid

This change is not from a source that supports changelogs.


Changes for the versions:
3.6.13~hg20101029r34715+nobinonly-0ubuntu1~umd1~lucid
3.6.13~hg20101108r34732+nobinonly-0ubuntu1~umd1~lucid

This change is not from a source that supports changelogs.

---

### Post by SilverWave on 2010-11-19
Changes for the versions:
4.0~b8~hg20101110r57184+nobinonly-0ubuntu1~umd1~lucid
4.0~b8~hg20101119r57887+nobinonly-0ubuntu1~umd1~lucid

This change is not from a source that supports changelogs.

Changes for the versions:
3.6.13~hg20101108r34732+nobinonly-0ubuntu1~umd1~lucid
3.6.13~hg20101119r34758+nobinonly-0ubuntu1~umd1~lucid

This change is not from a source that supports changelogs.

---

### Post by SilverWave on 2010-11-27
Changes for the versions:
3.6.13~hg20101119r34758+nobinonly-0ubuntu1~umd1~lucid
3.6.14~hg20101125r34782+nobinonly-0ubuntu1~umd1~lucid

Changes for the versions:
4.0~b8~hg20101119r57887+nobinonly-0ubuntu1~umd1~lucid
4.0~b8~hg20101127r58302+nobinonly-0ubuntu1~umd1~lucid

Cant be many changes (if any) between this pre and the release of 4.0~b8 due out the 30th.

---

### Post by lovinglinux on 2010-11-27
> **SilverWave said:**
> Cant be many changes (if any) between this pre and the release of 4.0~b8 due out the 30th.

I doubt b8 will be released on schedule. There isn't a candidate build yet.

---

### Post by SilverWave on 2010-11-28
> **lovinglinux said:**
> I doubt b8 will be released on schedule. There isn't a candidate build yet.

You could be right but I have been using the 4.0b8pre and there doesn't seem to be much wrong with it...

The USA holidays could also be having an impact.

---

### Post by lovinglinux on 2010-11-28
> **SilverWave said:**
> You could be right but I have been using the 4.0b8pre and there doesn't seem to be much wrong with it...

The USA holidays could also be having an impact.

I have been using it too, not as I used to tho, since Opera 11 is my primary browser now. I haven't noticed anything wrong, except for extensions bugs due to incompatibilities. However, there are still some [blocking issues]("https://bugzilla.mozilla.org/buglist.cgi?quicksearch=blocking2.0:beta8+") and I haven't received any words about making my extensions compatible with beta 9 or RC yet, which usually happens a couple of days before the release. But I think the most important clue is that there aren't any candidates in the [nightly ftp directory]("ftp://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/").

The holidays could also be having an impact, but it is weird that they scheduled the release for November 30th, without considering this.

---

### Post by SilverWave on 2010-11-28
> **lovinglinux said:**
> I have been using it too, not as I used to tho, since Opera 11 is my primary browser now.

OMG Opera :-(

I was once tempted to try it on my HTC Desire but the EULA is execrable.

Reading through it I came to the conclusion they would own the soul of my first male born heir, among other things...

And its proprietary.

---

### Post by lovinglinux on 2010-11-28
> **SilverWave said:**
> OMG Opera :-(

I must admit I never really gave Opera any attention and I was unaware of it's capabilities. But since Opera 11 supports extensions, I decided to give it a try and port some of my extensions to it. After a month using it for real, I must admit is a great browser and I'm really enjoying it. I still miss some Firefox extensions tho, because Opera extension framework is similar to Chrome and thus not very powerful like Firefox. But after exploring Opera, I was able to configure it to my liking and my workflow is going really well with it. Plus, it looks gorgeous with the theme I'm using.

I'm still using Firefox for development tho. At least I'm not using Chrome, otherwise people could think I went nuts :). However, I'm also porting extension to Chrome, because they are very similar to Opera and don't require much work to make them compatible.

> **SilverWave said:**
> I was once tempted to try it on my HTC Desire but the EULA is execrable.

Reading through it I came to the conclusion they would own the soul of my first male born heir, among other things...

And its proprietary.

Well, being proprietary is one of the major drawbacks. However, extensions can be released as open source, which is the most important factor for me.

The EULA looks like standard proprietary software license agreement or am I missing something?

---

### Post by Enigmapond on 2010-11-28
Just as a short testimonial, I really LUV the new FF! It's quick and has a few great features and the tab placement it just wonderful. The only problem is with some extensions but that will be sorted out when it's released, I guess. Thanks for all the work on this. :D

---

### Post by hawthornso23 on 2010-11-29
Looks like there have been some nasty regressions in firefoxb8pre over the last few days. I'm seeing frequent orphaned processes that have to be killed with killall firefox-4.0-bin,sudden crashes for no apparent reason, and a bizarre bug whereby each click of the launcher would open two minefield instances. And if you try to report the issues via the help menu you get a snarky message telling you to update to firefox 4.0b7 first. Not useful when you are already running b8pre. 

It was stable and nice. But a couple days back somebody broke something bigtime and they still havn't got it fixed. A shame - I was enjoying the HTML5 on youtube. Now I've had to switch back to Namoroka because Minefield is just too frustrating to use.

---

### Post by SilverWave on 2010-12-01
> **lovinglinux said:**
> I...
Well, being proprietary is one of the major drawbacks. However, extensions can be released as open source, which is the most important factor for me.

The EULA looks like standard proprietary software license agreement or am I missing something?

Well it has been the first one I have actually read for some time tbh... but the stuff regarding 3rd party use of your info was a no-no for me.

In Mozilla I trust.

---

### Post by SilverWave on 2010-12-01
> **Enigmapond said:**
> Just as a short testimonial, I really LUV the new FF! It's quick and has a few great features and the tab placement it just wonderful. The only problem is with some extensions but that will be sorted out when it's released, I guess. Thanks for all the work on this. :D

Yeah I am starting to like it as well.... it took some time as so much is changing.

I run 4 and 3.6 at the same time and I have changed 3.6 to more of a "4" look and feel.

Day to day most of my browsing is in 3.6 but gmail and Shelvelogger log I view in 4 with no problem.

As more extensions start working on 4 I will move more of my browsing and hopefully swap to mainly browsing with 4 sometime next year :-)

---

### Post by SilverWave on 2010-12-01
> **hawthornso23 said:**
> Looks like there have been some nasty regressions in firefoxb8pre over the last few days. I'm seeing frequent orphaned processes that have to be killed with killall firefox-4.0-bin,sudden crashes for no apparent reason, and a bizarre bug whereby each click of the launcher would open two minefield instances. And if you try to report the issues via the help menu you get a snarky message telling you to update to firefox 4.0b7 first. Not useful when you are already running b8pre. 

It was stable and nice. But a couple days back somebody broke something bigtime and they still havn't got it fixed. A shame - I was enjoying the HTML5 on youtube. Now I've had to switch back to Namoroka because Minefield is just too frustrating to use.

Hmm have you tried the one I have in my Weekly testing PPA?

4.0~b8~hg20101127r58302+nobinonly-0ubuntu1~umd1~lucid

I am using that and I have no problems.

[One Daily A Week #0 - Lucid]("https://launchpad.net/%7Esilverwave/+archive/testing0") 
     ```
sudo add-apt-repository ppa:silverwave/testing0
```

---

### Post by SilverWave on 2010-12-01
> **lovinglinux said:**
> ... However, there are still some [blocking issues]("https://bugzilla.mozilla.org/buglist.cgi?quicksearch=blocking2.0:beta8+") and I haven't received any words about making my extensions compatible with beta 9 or RC yet, which usually happens a couple of days before the release. But I think the most important clue is that there aren't any candidates in the [nightly ftp directory]("ftp://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/").

> [Mozilla]("http://www.mozilla.org/")  Project has confirmed that it plans to ship the eighth beta for version  4 of its open source Firefox web browser on Tuesday, the 7th of  December. It looks as if they have only sipped a week, nice to see them back on track.

[http://www.h-online.com/open/news/item/Mozilla-Firefox-4-Beta-8-coming-next-Tuesday-1145550.html](http://www.h-online.com/open/news/item/Mozilla-Firefox-4-Beta-8-coming-next-Tuesday-1145550.html)

P.S.

"Mozilla says that Firefox 4 Beta 8 will ship at the same time as Firefox 4 Beta 3 for Mobile devices"

Excellent.

---

### Post by SilverWave on 2010-12-04
Changes for the versions:
3.6.14~hg20101125r34782+nobinonly-0ubuntu1~umd1~lucid
3.6.14~hg20101203r34803+nobinonly-0ubuntu1~umd1~lucid

Changes for the versions:
4.0~b8~hg20101127r58302+nobinonly-0ubuntu1~umd1~lucid
4.0~b8~hg20101204r58593+nobinonly-0ubuntu1~umd1~lucid

---

### Post by SilverWave on 2010-12-05
Changes for the versions:
3.6.14~hg20101203r34803+nobinonly-0ubuntu1~umd1~lucid

Changes for the versions:
4.0~b8~hg20101204r58593+nobinonly-0ubuntu1~umd1~lucid

---

### Post by SilverWave on 2010-12-10
Changes for the versions:
3.6.14~hg20101203r34803+nobinonly-0ubuntu1~umd1~lucid
3.6.14~hg20101210r34811+nobinonly-0ubuntu1~umd1~lucid

Changes for the versions:
4.0~b8~hg20101204r58593+nobinonly-0ubuntu1~umd1~lucid
4.0~b8~hg20101210r59052+nobinonly-0ubuntu1~umd1~lucid

The beta8 has been delayed again  now probably sometime in December.

---

### Post by SilverWave on 2010-12-11
The latest FF4b8pre updates your back end sync data (held on Mozilla servers).

The problem is that any FF3.6 machines still on 1.5.1 cant read the new format yet.

 So you wont be able to sync with your FF3.6 machines until they release an update.

Joy :sad:

__________________

>  Upon upgrading to Sync 1.5.1, sync suddenly 
 refuses to sync (“Error While Syncing”) and demands to upgrade to the latest version (“You need to update Firefox Sync to continue syncing your data”). Problem is, 1.5.1 ***IS*** the latest version!!!

 [Latest version of sync demands to be upgraded to latest version... WTF??]("https://groups.google.com/group/mozilla-labs-weave/browse_thread/thread/10cbe6e6bf96ee63?hide_quotes=no")

>     
Mike Connor       
First off, I'm sorry this has been confusing for you and your friends.
 Storage format changes, while rare, are occasionally necessary, and
sometimes are incompatible.  This is something that used to happen
with every version released, but we've only changed things twice since
February, and this is anticipated to be the final incompatible change
we make to Sync.  The plan is to release stable builds at the same
time for all affected products. Unfortunately, we did not communicate
this well to users of nightly and/or developer builds, who would hit
this sooner, and in less of a controlled fashion.

To clarify what you're seeing here, I suspect that at least one of
your clients is running a nightly build of Firefox, or a developer
channel version of Firefox Sync (1.6b2), which would include the
newest version of sync, which uses a simpler and more performant
crypto component, as well as some internal changes necessary to
support some near-future performance work.  Again, this is expected to
be the last compatibility-breaking change, but it was expected (and,
indeed, the clients check for this type of change before syncing). 

---

### Post by SilverWave on 2010-12-11
hmm found this but not tested yet!

[Latest Update: Firefox Sync 1.6b4 (December 11, 2010)]("https://services.mozilla.com/sync/updated/?version=1.5&channel=dev")

time to take a backup me thinks ;-)
> **[Recent changes]("https://services.mozilla.com/sync/updated/changelog.html")**

           
[LIST]
[*](1.6b4) Fix reliability issues in crypto procedures and key caching
[*](1.6b3) Better error handling and recovery for various key errors
[*](1.6b3) Fix HKDF implementation in crypto
[*](1.6b2) Performance and correctness fixes
[*](1.6b1) Employ a simpler crypto infrastructure. **This provides a  newer storage format and requires that all computers connected to the  account are upgraded to this verfsion of Firefox Sync or higher**.
[*](1.6b1) Several performance improvements.
[*](1.6b1) Improved preference sync.
[*](1.5.1b3) Overlong wizard page titles (in translations) are now wrapped over multiple lines
[*](1.5.1b2) Re-enable locales, not all strings are translated, so you may see en-US equivalents
[*](1.5.1b2) History sync now ignores invalid entries that sometimes appear
[*](1.5b7) Fixed a bug that prevented some form data generated by Firefox 4 from being synced.
[*](1.5b7) Fixed several UI warts in the setup wizard.
[*](1.5b7) Make use of plural forms where appropriate.
[*](1.5b6) Implement a newer storage format. Note: **This requires all  computers connected to the account are upgraded to this version of  Firefox Sync or higher**.
[*](1.5b6) Show a strength meter for custom Sync Keys
[*](1.5b6) Removed option to email the Sync Key
[*](1.5b6) Improved localization of the quota dialog
[*](1.5b5) Updated the Fennec UI to support email address based accounts and dashed Sync Keys
[*](1.5b5) Provide explanatory text for the Sync Key artifact and email
[*](1.5b5) Fixed an issue that prevented users from signing up
[*](1.5b4) Fixed UI issues in the setup wizard
[*](1.5b3) Sync no longer asks for a user name on sign up, just an email address
[*](1.5b3) Sync now syncs which engines are enabled across all clients
[*](1.5b3) Added support for server-side quota
[*](1.5b3) Improved default client name on mobile devices
[*](1.5b3) Fixed UI issues caused by the changes to the setup wizard
[*](1.5b2) Improved setup wizard
[*](1.5b1) Enable bookmark and tabs sync on Seamonkey
[*](1.5b1) Memory and performance improvements
[/LIST]


---

### Post by SilverWave on 2010-12-11
> **SilverWave said:**
> hmm found this but not tested yet!

[Latest Update: Firefox Sync 1.6b4 (December 11, 2010)]("https://services.mozilla.com/sync/updated/?version=1.5&channel=dev")

time to take a backup me thinks ;-)

Well the install worked but then I received:* Wrong Sync Key* error... OK WTF!

The *key* here is not to panic ;-)  looking at my working FF4.0b8 I knew I had a key just how to find it!

What's happened is that they have **changed your sync key without telling you**!
[I]
Oh bad Mozilla, **bad** Mozilla, no biscuit for you![/I]

Anyway I did what you always do in a case like this and Googled it... here we go:

[Your old Firefox Sync key is no good!]("http://tech.mahesha.com/2010/12/07/your-old-firefox-sync-key-is-no-good/")

> **Mahesh Asolkar]Once I figured that the *Wrong Sync Key* error was  not because of broken Minefield, but because Minefield indeed changed my  key, I could quickly bring all the other installations of Firefox in  sync again.
 All that needs to be done is, grab your new key like so:
 
[LIST]
[*]Open *Minefield (or Firefox) button* &#8594 said:**
> Go to the *Sync* tab
[*]Expand the *Manage Account* group
[*]Click on the *My Sync Key* item
[*]Copy/Print/Write down/Passpack your Sync Key displayed in the dialog that shows up
[/LIST]
 Then in the installation of Firefox where you get the *Wrong Sync Key*  error, update the Sync Key with the new key. This pretty much involves  resetting Sync information and setting it up anew, like so:
 
[LIST]
[*]Open *Minefield (or Firefox) button* &#8594; *Options* &#8594; *Options* (Which is *Minefield (or Firefox) button* &#8594; *Preferences* &#8594; *Preferences* in Linux).
[*]Go to the *Sync* tab
[/LIST]


[LIST]
[*]Go to the *Wrong Sync key* item and correct it.
[/LIST]

**WHOOT! Sync has now completed on my ff3.6.14pre!**

---

### Post by SilverWave on 2010-12-11
Well this explains quite a lot about the key change.> [[...]("https://groups.google.com/group/mozilla-labs-weave/browse_thread/thread/10cbe6e6bf96ee63?hide_quotes=no")]the passphrase was previously used with PBKDF2 to generate an AES key.  
Generating even stronger secrets was actually unnecessary, since we were converting to an AES key.
For new users, we now generate a 128-bit AES key directly, and existing users will have their passphrases converted as a one-off.
This is the same end level of security, since any extra entropy was lost in the conversion in the previous scheme. 
In the future, **the standard setup path will use J-PAKE to securely transfer credentials to new clients, rather than manually entering keys**, so we feel the added length for all users is not a major problem. And this is the plan for J-PAKE:

> [Explore using J-PAKE to securely pass credentials to another device.]("https://wiki.mozilla.org/Services/Sync/SyncKey/J-PAKE")

**User Requirements  **

 
[LIST]
[*]Setting up a new mobile device should only involve entering a short code on the desktop device
[*]Secondary request, not a hard requirement, is that if  the user has a mobile device, and is setting up a desktop device, that  the flow is similar and still involves entering the key on the desktop
[/LIST]
 **  Desired User Flow  **

 
[LIST=1]
[*]User chooses "quick setup" on new device
[*]Device displays a setup key that contains both the initial secret and a channel ID
[*]On a device that is authenticated, user chooses "add another device" and is prompted for that key
[*]The two devices exchange messages to build the secure tunnel
[*]The already-authenticated device passes all credentials (username/password/passphrase) to the new device
[*]New device completes setup and starts syncing
[/LIST]


---

### Post by SilverWave on 2010-12-12
[QUOTE=Mark342][URL="http://forums.mozillazine.org/viewtopic.php?f=23&t=1951751&start=338"]Linux has the Firefox button in the nightly builds.
[/URL] It has been there for at least a week now.
It IS very rough right now (It needs a lot of polish and styling), but it works well.
I think the initial plan for the Firefox button on Linux was to make it movable, but currently it isn't movable.

The Fx button is placed in the tabbar when you uncheck "Menubar" after a right-click.
The Title of the page is still displayed on Linux because firefox still uses your window manager's window decorations.
Linux will still display the page's title in Firefox 4 and their are no plans to change it.[/QUOTE]Heh I had missed this! Excelent :-)

It is easy to miss! It looks like a tab and its called **Minefield**.

---

### Post by SilverWave on 2010-12-12
[UPDATE] this is out of date go here instead:

[**Installing old extensions for use with Firefox: Addon Compatibility Reporter**]("http://ubuntuforums.org/showpost.php?p=10253879&postcount=291")
__________________


With FF4.0b8pre I think things are really starting to come together.

With this in mind I have started to look at small hacks to workaround compatibility issues with existing key Add-ons.

So that other users of the Latest Firefox can benefit I will add them to this post.

*Warning: Use the attached Add-ons at your own risk, I have had no issues but YMMV.* :-)
__________________

[B]Using Minefield? 
[/B]To allows extensions at AMO to be installed:
```
in about:config
Set:
general.useragent.compatMode.firefox
To true.

```__________________

**Working Add-ons List**


[LIST]
[*]Adblock Plus 1.3.2
[/LIST]

[LIST]
[*]Barlesque 1.14
[LIST]
[*]Note: Collapses the wide grey add-on bar into a neat set of add-on buttons
[/LIST]
 
[/LIST]

[LIST]
[*]Download Statusbar 0.9.7.2
[/LIST]

[LIST]
[*]Link Target Display 1.7
[LIST]
[*]Note: Bottom Left alternative to it being jammed into the right of the address bar..
[/LIST]
 
[/LIST]

[LIST]
[*]Make Link 10.8
[/LIST]

[LIST]
[*]NewTabURL 2.2.0
[LIST]
[*]Config: Set to [https://encrypted.google.com/webhp?complete=1&hl=en](https://encrypted.google.com/webhp?complete=1&hl=en)
[/LIST]
 
[/LIST]

[LIST]
[*]OptimizeGoogle 0.78.2
[/LIST]

[LIST]
[*]Places&#8217; Full Titles 3.2.4
[LIST]
[*]It will work for the bookmarks menu but not for the bookmarks toolbar  (which is where I keep my RSS feeds). You will need to adjust the code  manually - but it's not difficult.  Inside your Firefox profile,  navigate to  extensions\{7bf7c1c3-d8e7-4020-ab38-a829c76693d5}\chrome\placesfulltitles\skin  and open placesfulltitles.css in a text editor. Do a find-and-replace:  replace all instances of bookmarksBarContent with PlacesToolbar and then  close the file and restart Firefox. Great fix by [Bas]("https://addons.mozilla.org/en-US/firefox/user/61629/").
[/LIST]
 
[/LIST]
   
[LIST]
[*]Reliby 1.5.0
[/LIST]
  
[LIST]
[*]RequestPolicy 0.5.16
[LIST]
[*]Note: The Toolbar button is not working, use the Add-on Bar Button instead.
[/LIST]
 
[/LIST]

[LIST]
[*]Stay-Open Menu 1.5.6
[/LIST]

[LIST]
[*]Tab Counter 1.8.7
[/LIST]
   
[LIST]
[*]Toolbar Buttons 0.6.0.8
[/LIST]

[LIST]
[*]Tree Style Tab 0.11.2010120903
[LIST]
[*]Only the first style "Metal" is readable for me under Linux.
[*]Right Click Menu over tabs* seems* not to be working, but a Right Click on the grey below the tabs, or on the "New Tab Plus", works OK.
[/LIST]
 
[/LIST]
 __________________

** Hacked Add-ons List**

  
[LIST]
[*]Locationbar² 1.0.5
[LIST]
[*]maxVersion bumped to 4.*
[*]Date: 2010.12.12
[*]Notes:  the new link URL-on-hover feature isn&#8217;t supported (so use Link Target Display).
[*]Config: Double-click selects all; Grey Directories and file name; strong; on top.
[*]Shows bread crumbs regardless of preferences.
[/LIST]
 
[/LIST]

[LIST]
[*]Menu Editor 1.2.6
[LIST]
[*]maxVersion bumped to 4.*
[*]Date: 2010.12.12
[*]CTRL+SHIFT+S brings up the Menu Editor Options dialogue.
[*]I use this to hide a lot of the Main Context Menu(right click menu) items - you just toggle hide/unhide.
But there are 2 things I use it for that I cant do without.
[LIST=1]
[*]Add a "Close tab" item just above "Back" in the right click menu.
[LIST]
[*]Note that the "Close tab" that works is from the File Menu.
[/LIST]
 
[*]Add an "Undo Close Tab" item just below "Stop" in the right click menu.
[/LIST]
 
[/LIST]
 
[/LIST]

[LIST]
[*]nosquint-2.0.5
[LIST]
[*]maxVersion bumped to 4.*
[*]Date: 2010.12.12
[/LIST]
 
[/LIST]

[LIST]
[*]Readability 1.2
[LIST]
[*]maxVersion bumped to 4.*
[*]Date: 2010.12.12
[/LIST]
 
[/LIST]

[LIST]
[*]Shelve 1.22
[LIST]
[*]maxVersion bumped to 4.*
[*]Date: 2010.12.12
[/LIST]

[LIST]
[*]Built from source at GitHub.
[/LIST]
 
[/LIST]
__________________

**Add-ons built-in**** to FF4.0**


[LIST]
[*][BarTab]("https://philikon.wordpress.com/2010/11/10/firefox-4-0b7-updates/") 2.0 (Now a Built-in feature of FF)
[LIST]
[*]To duplicate BarTab behaviour alter the following setting:
[*]about:config
[/LIST]
 
[/LIST]
[INDENT][INDENT]```
[INDENT]browser.sessionstore.max_concurrent_tabs
set 
value = 0
[/INDENT]
```[/INDENT][/INDENT]
[LIST]
[*]Fission 1.0.9 (Waiting for this feature to land).
[/LIST]
__________________

**Non-Working Add-ons List**


[LIST]
[*]Boox 2.6 (Developer will update when he has time).
[/LIST]

[LIST]
[*]Informational Tab 0.3.2010062901 (Will be a built-in to Firefox, if not Developer will probably update).
[/LIST]

[LIST]
[*]Platypus 0.81 (Developer no longer maintaining this Add-on).
[LIST]
[*]Save the Platypus script in FF3.6 and then export to FF4.0 until a fix is found.
[/LIST]
 
[/LIST]
 __________________

**Add-ons ****Awaiting Testing** [B]List
[/B]

[LIST]
[*] [DownThemAll!]("http://downthemall.net/") 1.1.10
[*] [Greasemonkey]("http://www.greasespot.net/") 0.8.20100408.6
[*] [HTTPS-Everywhere]("https://www.eff.org/https-everywhere") 0.9.2
[*] [Image Zoom]("http://imagezoom.yellowgorilla.net/") 0.4.4
[*] [Linkification]("http://yellow5.us/firefox/linkification/") 1.3.8
[*] [Pronounce]("http://www.netgents.com/") 1.4
[*] [repagination]("http://andreineculau.com/blog/2008/06/repagination/") 2006.4.5.1
[*] [SQLite Manager]("http://sqlite-manager.googlecode.com/") 0.6.5
[/LIST]
__________________

**Tips**

Web Console short cut:
CTRL+SHIFT+K and CTRL+R

[https://arantius.com/misc/gm-nightly/](https://arantius.com/misc/gm-nightly/)
__________________

---

### Post by libssd on 2010-12-13
I have gone through this twice, to confirm the behavior I'm reporting with Ubuntu 10.04.

1. Added [http://ppa.launchpad.net/ubuntu-mozi...ily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozi...ily/ppa/ubuntu) to software sources
2. Installed Firefox 4.08b from this repository
3. The next time I applied software updates, Firefox 3.6.13 was replaced by Namaroka
4. Uninstalled Namaroka
5. De-activateed [http://ppa.launchpad.net/ubuntu-mozi...ily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozi...ily/ppa/ubuntu) (Synaptic)
6. Activate [http://ppa.launchpad.net/silverwave/...month-1/ubuntu](http://ppa.launchpad.net/silverwave/...month-1/ubuntu) (Synaptic)
7. Uninstall firefox-4.0(Synaptic)
8. sudo apt-get update (terminal)
9. sudo apt-get install firefox-4.0 (terminal or synaptic, dependency errors):

[i]firefox-4.0:
  Depends: firefox-4.0-core (=4.0~b8~hg20101204r58593+nobinonly-0ubuntu1~umd1~lucid) but 4.0~b8~hg20101213r59154+nobinonly-0ubuntu1~umd1~lucid is to be installed[/i]

It's not that hard to re-install firefox-4.0 from the daily PPA, or to uninstall Namaroka and re-install firefox 3.6.13, just annoying, and subject to operator error if I don't watch updates closely.

---

### Post by SilverWave on 2010-12-13
> **libssd said:**
> I have gone through this twice, to confirm the behavior I'm reporting with Ubuntu 10.04.

1. Added [http://ppa.launchpad.net/ubuntu-mozi...ily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozi...ily/ppa/ubuntu) to software sources
2. Installed Firefox 4.08b from this repository
3. The next time I applied software updates, Firefox 3.6.13 was replaced by Namaroka
4. Uninstalled Namaroka
5. De-activateed [http://ppa.launchpad.net/ubuntu-mozi...ily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozi...ily/ppa/ubuntu) (Synaptic)
6. Activate [http://ppa.launchpad.net/silverwave/...month-1/ubuntu](http://ppa.launchpad.net/silverwave/...month-1/ubuntu) (Synaptic)
7. Uninstall firefox-4.0(Synaptic)
8. sudo apt-get update (terminal)
9. sudo apt-get install firefox-4.0 (terminal or synaptic, dependency errors):

[I]firefox-4.0:
  Depends: firefox-4.0-core (=4.0~b8~hg20101204r58593+nobinonly-0ubuntu1~umd1~lucid) but 4.0~b8~hg20101213r59154+nobinonly-0ubuntu1~umd1~lucid is to be installed[/I]

It's not that hard to re-install firefox-4.0 from the daily PPA, or to uninstall Namaroka and re-install firefox 3.6.13, just annoying, and subject to operator error if I don't watch updates closely.

Hmm before #5, I would have uninstalled the Firefox 4.08b that you installed in #2. Then with things back to normal... I would have done #6 and then installed Firefox 4.08b from the silverwave PPA. [If that makes sense ;-)]

On your second point, with so many packages included in the ** [ubuntu-mozilla-daily]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa?field.series_filter=")** ppa it is way to easy to accidentally update the wrong one as you have found to your cost.
Hence why I created single package ppa's like silverwave/one-daily-a-month-1 in the first place, the same had thing had happened to me :-(.
Conversely with [Firefox-4.0 - One Daily A Month #1 - Lucid]("https://launchpad.net/%7Esilverwave/+archive/one-daily-a-month-1")  you can set it and forget it.

---

### Post by libssd on 2010-12-13
> **SilverWave said:**
> Hmm before #5, I would have uninstalled the Firefox 4.08b that you installed in #2. Then with things back to normal... I would have done #6 and then installed Firefox 4.08b from the silverwave PPA. [If that makes sense ;-)]
It makes sense, so I just tried that sequence of steps, but  ended up with the same outcome.

> **SilverWave said:**
> On your second point, with so many packages included in the ** [ubuntu-mozilla-daily]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa?field.series_filter=")** ppa it is way to easy to accidentally update the wrong one as you have found to your cost.
Hence why I created single package ppa's like silverwave/one-daily-a-month-1 in the first place, the same had thing had happened to me :-(.
Yup. Been there, done that (more than once), which is why I'm trying to install from the silverwave PPA.

> **SilverWave said:**
> Conversely with [Firefox-4.0 - One Daily A Month #1 - Lucid]("https://launchpad.net/%7Esilverwave/+archive/one-daily-a-month-1")  you can set it and forget it.
That is my goal.

---

### Post by SilverWave on 2010-12-13
> **libssd said:**
> It makes sense, so I just tried that sequence of steps, but  ended up with the same outcome.


Yup. Been there, done that (more than once), which is why I'm trying to install from the silverwave PPA.


That is my goal.

So if that didn't work... I would be tempted to uninstall any thing related to ff4.0 and then have a look through your software sources to ensure that nothing is still remaining.

Then:

 ```
sudo add-apt-repository ppa:silverwave/one-daily-a-month-1
```Followed by:

```
sudo apt-get update
sudo apt-get install firefox-4.0
```Best of luck.

P.S.

This command can be useful in trouble shooting as well...
```

apt-cache policy firefox-4.0

apt-cache policy firefox-4.0-core
```

---

### Post by libssd on 2010-12-13
> **SilverWave said:**
> So if that didn't work... I would be tempted to uninstall any thing related to ff4.0 and then have a look through your software sources to ensure that nothing is still remaining.

Then:

 ```
sudo add-apt-repository ppa:silverwave/one-daily-a-month-1
```Followed by:

```
sudo apt-get update
sudo apt-get install firefox-4.0
```Best of luck.

P.S.

This command can be useful in trouble shooting as well...
```

apt-cache policy firefox-4.0

apt-cache policy firefox-4.0-core
```
> **SilverWave said:**
> So if that didn't work... I would be tempted  to uninstall any thing related to ff4.0 and then have a look through  your software sources to ensure that nothing is still remaining.   

I'm pretty sure that the first thing I did upon encountering the  dependency error was to do a complete uninstall of firefox-4.0, followed  by what you suggest; no dice.    

I'm assuming that production firefox-4.0 will be released in the near   future (less than 3 months), so I'm just going to let things ride until  then. Both versions are functional, and I have both PPAs de-activated at  the moment. Once a week or so I'll re-activate the firefox daily PPA,  check for updates, and make sure to uncheck any FF 3 updates before  applying them.  This is more of an intellectual puzzle than a roadblock,  and at the moment I'm tired of beating my head against the wall over this minor problem. ](*,)

Thanks again for all your suggestions.

---

### Post by SilverWave on 2010-12-14
> **libssd said:**
> I'm pretty sure that the first thing I did upon encountering the  dependency error was to do a complete uninstall of firefox-4.0, followed  by what you suggest; no dice.    

I'm assuming that production firefox-4.0 will be released in the near   future (less than 3 months), so I'm just going to let things ride until  then. Both versions are functional, and I have both PPAs de-activated at  the moment. Once a week or so I'll re-activate the firefox daily PPA,  check for updates, and make sure to uncheck any FF 3 updates before  applying them.  This is more of an intellectual puzzle than a roadblock,  and at the moment I'm tired of beating my head against the wall over this minor problem. ](*,)

Thanks again for all your suggestions.


Well as you say everything is working :-)

One thing that I have remembered that may help if you ever have an issue like this again is being able to Force a Version in Synaptic.

Note: I have Show packaging properties in the main window enabled (Edit > Preferences > General).
Also in "Columns and Fonts" you may find it helpfull to enable some more Columns.

**How to Force a Version in Synaptic.**

Select "firefox-4.0-core" in Synaptic

Click on the "Versions" tab to see the multible versions on offfer. There is a Note displayed at the botton of the screen:
"To install a version different from the default one, choose **Package -> Force Version..**. from the menu."

This pops a dialogue box up which allows you to choose. :-)

---

### Post by libssd on 2010-12-14
> **SilverWave said:**
> Well as you say everything is working :-)

One thing that I have remembered that may help if you ever have an issue like this again is being able to Force a Version in Synaptic.

Note: I have Show packaging properties in the main window enabled (Edit > Preferences > General).
Also in "Columns and Fonts" you may find it helpful to enable some more Columns.

**How to Force a Version in Synaptic.**

Select "firefox-4.0-core" in Synaptic

Click on the "Versions" tab to see the multible versions on offfer. There is a Note displayed at the botton of the screen:
"To install a version different from the default one, choose **Package -> Force Version..**. from the menu."

This pops a dialogue box up which allows you to choose. :-)
Thanks for another useful tip. I'm guessing you are referring to Synaptic in a release other than Lucid, as I am seeing a slightly different path to this option.

Mark package for installation > Package menu > Force Version

However, I noted this caution in the Synaptic help:

>  If you force a different version from the default one, errors in the dependency handling can occur.
But, while reading the help (what a novel idea: RTFM) I noted another option on that menu: Lock Version

Would this prevent Namaroka from being installed? "Debian only" in Synaptic help suggests not:

> **3.10.&#8195;To Lock a Package to the Current Version (Debian only)**

To lock a package to the current version follow these steps:

1. Select the package that you want to lock in the package list.
      		
2. Choose Package &#9656; Lock Version.
      
The Synaptic Package Manager will reload the package information. 
You should now see that the menu item Package &#9656; Lock Version is checked.

**Update**: Ah hah! "Lock Version" appears to do the trick. After locking Firefox 3.6, I re-activated the daily PPA, checked for updates, and none were offered for firefox, but were for firefox-4.0; ran the updates, and Namaroka was not installed. 

Great discussion!

---

### Post by SilverWave on 2010-12-14
> **libssd said:**
> Thanks for another useful tip. I'm guessing you are referring to Synaptic in a release other than Lucid, as I am seeing a slightly different path to this option.

Mark package for installation > Package menu > Force Version

However, I noted this caution in the Synaptic help:


But, while reading the help (what a novel idea: RTFM) I noted another option on that menu: Lock Version

Would this prevent Namaroka from being installed? "Debian only" in Synaptic help suggests not:



**Update**: Ah hah! "Lock Version" appears to do the trick. After locking Firefox 3.6, I re-activated the daily PPA, checked for updates, and none were offered for firefox, but were for firefox-4.0; ran the updates, and Namaroka was not installed. 

Great discussion!

Result! I think I was reluctant to use that option as I was sure I would forget which packages I had locked. ;-)

Great to see that you have found a solution. :-)

---

### Post by SilverWave on 2010-12-14
> **SilverWave said:**
> hmm found this but not tested yet!

[Latest Update: Firefox Sync 1.6b4 (December 11, 2010)]("https://services.mozilla.com/sync/updated/?version=1.5&channel=dev")

time to take a backup me thinks ;-)

**Latest Update: Firefox Sync 1.6b5 (December 14, 2010)**

           **Recent changes**

           
[LIST]
[*](1.6b5) Backward-compatibility fix for old Sync Keys
[/LIST]


[LIST]
[*](1.6b4) Fix reliability issues in crypto procedures and key caching
[*](1.6b3) Better error handling and recovery for various key errors
[*](1.6b3) Fix HKDF implementation in crypto
[*](1.6b2) Performance and correctness fixes
[*](1.6b1) Employ a simpler crypto infrastructure. This  provides a newer storage format and requires that all computers  connected to the account are upgraded to this verfsion of Firefox Sync  or higher.
[*](1.6b1) Several performance improvements.
[*](1.6b1) Improved preference sync.
[/LIST]

---

### Post by SilverWave on 2010-12-15
[Download Firefox 4.0 Beta 8 Preview](http://news.softpedia.com/news/Download-Firefox-4-0-Beta-8-Preview-172892.shtml)

> Early adopters can grab the Firefox 4.0 Beta 8 Candidate bits from **[Mozilla’s FTP servers]("ftp://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/")** and test drive the release to get an idea of what’s coming in the Beta. 

I'm updating the one-daily-a-week ppa's with the new ff-4.0b9pre's as we speak :D

---

### Post by libssd on 2010-12-15
Got it, and my strategy of checking the "don't update" box for ff 3.6+ worked -- no Namaroka. Unfortunately 4.09b breaks Adblock Plus 3.1.2, Better Privacy 1.48.3, and Blacksheep 1.5. The perils of a beta release.

---

### Post by SilverWave on 2010-12-15
> **libssd said:**
> Got it, and my strategy of checking the "don't update" box for ff 3.6+ worked -- no Namaroka. Unfortunately 4.09b breaks Adblock Plus 3.1.2, Better Privacy 1.48.3, and Blacksheep 1.5. The perils of a beta release.

Yes all looks OK in my testing on Lucid but as you say most add-on are reporting as non compatible... hmm I'll see what our options are.

---

### Post by SilverWave on 2010-12-15
Changes for the versions:
3.6.14~hg20101210r34811+nobinonly-0ubuntu1~umd1~lucid
3.6.14~hg20101214r34821+nobinonly-0ubuntu1~umd1~lucid

Changes for the versions:
4.0~b8~hg20101210r59052+nobinonly-0ubuntu1~umd1~lucid
**4.0~b9**~hg20101215r59188+nobinonly-0ubuntu1~umd1~lucid

As FF4.0b8 is on its way to release here is the first Firefox 4.0b9pre!

---

### Post by SilverWave on 2010-12-15
3.6.14~hg20101214r34821+nobinonly-0ubuntu1~umd1~lucid

**4.0~b9**~hg20101215r59188+nobinonly-0ubuntu1~umd1~lucid

Have fun :-)

The FF4.0 development is getting to a stage where it is almost possible to use it day-today ;-)

---

### Post by SilverWave on 2010-12-15
> **libssd said:**
> ...Unfortunately 4.09b breaks Adblock Plus 3.1.2, Better Privacy 1.48.3, and Blacksheep 1.5. The perils of a beta release.

All the big hitters are starting to be be updated as compatible... Adblock Plus is now OK.

This should help with the rest:

[Add-on Compatibility Reporter 0.7](https://addons.mozilla.org/en-US/firefox/addon/15003/?src=discovery-pane)

---

### Post by lovinglinux on 2010-12-15
> **SilverWave said:**
> All the big hitters are starting to be be updated as compatible... Adblock Plus is now OK.

Updating extensions already compatible with b8pre at this point (feature freeze) is just a matter of visiting the developer hub and changing the compatibility of the extension to the new version available in mozilla-central, in this case b9pre. However, Mozilla needs to add that version to the list, so we developers can apply the update. They only did that a couple of hours ago, so some extensions are still showing as compatible with b8pre. I just updated my extensions, but they still show as b8pre compatible because of the site cache. So you can expect that most popular extensions will be compatible later today.

> **SilverWave said:**
> 
[Add-on Compatibility Reporter 0.7](https://addons.mozilla.org/en-US/firefox/addon/15003/?src=discovery-pane)

That solves the problem for all extensions that are already compatible with beta 7. Be careful tho, with extensions that are only compatible with Firefox 3.6, because they can break things really bad, since Firefox 4 has major changes in the extension API. Launch the "Error Console" (CTRL+SHIFT+J) to check if any extension produces errors.

---

### Post by SilverWave on 2010-12-15
If you are using **FF4.0b9 **the changes to the statusbar can be a wrench...

After a lot of research I recommend these add-ons:


[LIST]
[*][Barlesque]("https://addons.mozilla.org/en-US/firefox/addon/259879/") 1.14
[LIST]
[*]Collapses the wide grey add-on bar into a neat set of add-on buttons.
[*]Can minimise to only an arrow until needed.
[/LIST]

[IMG]https://addons.mozilla.org/img/uploads/previews/full/51/51462.png?modified=1291322880[/IMG]
(Note: Barlesque is very new and so it *could* be regarded as possibly a little more risky than the others).
[/LIST]
 
[LIST]
[*][s][Link Target Display]("https://addons.mozilla.org/en-US/firefox/addon/55724/") 1.7[/s]
[LIST]
[*][s]Bottom Left alternative to it being jammed into the right of the Locationbar, only shows when needed.[/s]
[/LIST]

[IMG]https://addons.mozilla.org/img/uploads/previews/full/40/40370.png?modified=1262553214[/IMG]
[/LIST]

[LIST]
[*]Oh and I use [Locationbar²]("https://addons.mozilla.org/en-US/firefox/addon/4014/") 1.0.5
[LIST]
[*] This turns off the Link in the Locationbar and puts emphasis on the domain to reduce spoofing risk.
[/LIST]
 
[/LIST]
[INDENT][IMG]https://addons.mozilla.org/img/uploads/previews/full/21/21090.png?modified=1211739738[/IMG]

[/INDENT]**Observations**

I do agree with the the creation of an Add-on Bar, but it is too big as it stands.
Luckily I can use Barlesque to makes it perfect.

I cannot say I agree with the Link Target being jammed into the right of the Locationbar.
Again thanks to an Add-on we can avoid this problem until the devs correct it or change the implementation.
[COLOR=Blue][update] WHOOT! Sanity has prevailed! The Devs have dumped this brain-dead idea.[/COLOR]
[Bug 541656 - Display hyperlink URLs at bottom of window (instead of right side of location bar)]("https://bugzilla.mozilla.org/show_bug.cgi?id=541656")

---

### Post by lovinglinux on 2010-12-15
> **SilverWave said:**
> If you are using **FF4.0b9 **the changes to the statusbar can be a wrench...

After a lot of research I recommend these add-ons:


[LIST]
[*][Barlesque]("https://addons.mozilla.org/en-US/firefox/addon/259879/") 1.14
[LIST]
[*]Collapses the wide grey add-on bar into a neat set of add-on buttons.
[*]Can minimise to only an arrow until needed.
[/LIST]

Awesome.

I also recommend [Status-4-Evar]("https://addons.mozilla.org/en-US/firefox/addon/235283/"). Don't how it would behave with Barlesque tho.

---

### Post by SilverWave on 2010-12-16
> Sometime soon [s]after the beta 8 code freeze[/s], the Places team  will be merging the Places branch into mozilla-central.  There are a lot  of changes we&#8217;ve been working on, the most important of which is some  major re-architecting how we store data[http://shawnwilsher.com/archives/473](http://shawnwilsher.com/archives/473)

This just struck me as being a big change rather late in the day...

Under the hood speed-ups so maybe that explains it. 

I suppose we are still in beta and this would not be a GUI change... so interesting.

---

### Post by SilverWave on 2010-12-18
Someone asked me if Firefox was still relevant and my take on the Firefox 4.0 changes... here is my response:


> Firefox is an amazing browser but it was in danger of being eclipsed by  chrome. I am particularly impressed by the way Mozilla have not shrank  from taking the hard choices that were needed to meet this challenge.

1. A large part of  Firefox's success is because of it extensions but the old system was  causing some drag and would be an increasing burden in the future... so  they have created a new architecture "JetPack" that will solve this. It  addresses the main problem of extensions needing updating after each new  Firefox version by providing a separate api and a new way of assigning  permissions that looks to be very scalable.

2. Firefox Sync. This is  the killer app atm for Firefox and enormously extends its relevance and  usefulness working hand-in-hand with Firefox Mobile.

3. Firefox  Mobile, basing it on 4.0 code and running it as a native application  under Android is a master stroke and will pay huge dividends in the  future. An incredibly ballsy move, bravo Mozilla.

4. Speed audits and rewrites of bottlenecks in the code. Some of this is yet to land IIRC e.g. the Places storage code.

5. HTML 5 support. 

So  yes Chrome was a disruptive change but Mozilla have used it a driver  for renewing Firefox's direction and rearchitecturing the fundamentals  that it is based on.

They will not reap all the rewards  immediately, JetPack for instance is a more long term play, but Mozilla  are punching well above their weight and serving their users and the  open web well.

---

### Post by SilverWave on 2010-12-18
Well this is interesting...

[Visualizing Firefox Plugins]("http://eaves.ca/2010/12/17/visualizing-firefox-plugins-memory-consumption/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+EavescaMozilla+%28eaves.ca+%C2%BB+mozilla%29")
> Presently, if you run Firefox you can go to the [Plugin Check page]("http://www.mozilla.com/en-US/plugincheck/")  to see if your plugins are up to date. We thought: Wouldn't it be great  if that page ALSO showed you memory consumption rates? Maybe something  like this (**note the Memory Consumption column, it doesn't exist on the  real webpage** [...] Please understand (and we are quite proud of this). **All of the data in this mockup *is real***. Memory consumptions are estimates we derived by analyzing the Test Pilot data.So I already disable Java... do I use DivX? hmmm...

[IMG]http://eaves.ca/wp-content/uploads/2010/Firefox%20data%20visualization.png[/IMG]

---

### Post by libssd on 2010-12-18
Well stated summary of "Why Firefox". Chrome (among other things) seems to have shaken up the Firefox developers in a positive way. I had more or less consigned Firefox 3+ to irrelevancy, except for the few extensions it ran that had unique functionality. Now, I'm back as a regular user

---

### Post by SilverWave on 2010-12-18
As I was getting toolbar issues* on upgrating my previous profile from FF4.0b7 to FF4.0b8, I have pulled in a later daily build... 4.0~b9~hg20101218r59459, which does not display this issue.

*The toolbar was being reset to the default.

Changes for the versions:
4.0~b9~hg20101215r59188+nobinonly-0ubuntu1~umd1~lucid
4.0~b9~hg20101218r59459+nobinonly-0ubuntu1~umd1~lucid

While I was on I updated FF3.6 as well.

Changes for the versions:
3.6.14~hg20101214r34821+nobinonly-0ubuntu1~umd1~lucid
3.6.14~hg20101218r34829+nobinonly-0ubuntu1~umd1~lucid

---

### Post by SilverWave on 2010-12-18
> **SilverWave said:**
> As I was getting toolbar issues* on upgrating my previous profile from FF4.0b7 to FF4.0b8, I have pulled in a later daily build... 4.0~b9~hg20101218r59459, which does not display this issue.

*The toolbar was being reset to the default.

Changes for the versions:
4.0~b9~hg20101215r59188+nobinonly-0ubuntu1~umd1~lucid
4.0~b9~hg20101218r59459+nobinonly-0ubuntu1~umd1~lucid

While I was on I updated FF3.6 as well.

Changes for the versions:
3.6.14~hg20101214r34821+nobinonly-0ubuntu1~umd1~lucid
3.6.14~hg20101218r34829+nobinonly-0ubuntu1~umd1~lucid

As there was an issue with the previous daily I have updated the Monthly PPA's as well.

---

### Post by SilverWave on 2010-12-18
With the new 4.0b9pre release I decided to try using the [Add-on Compatibility Reporter]("https://addons.mozilla.org/en-US/firefox/addon/15003/") again and this time it worked fine.

It also allowed me to advise the developers that most of my Add-ons worked OK as well, which was the cherry on top :-)

__________________

Note: With previous unofficial compatibility add-ons, the procedure was to individually select the add-on to be forced to be compatible.

With this official one its all or nothing.

__________________

**With the Add-on Compatibility Reporter you need to do the following:**

[LIST]
[*]Install the [Add-on Compatibility Reporter]("https://addons.mozilla.org/en-US/firefox/addon/15003/") and restart Firefox.
[/LIST]

[LIST]
[*]Go to Add-ons > Extensions, there should be a note at the top saying:
 "Add-on compatibility checking is disabled. You may have incompatible add-ons."
[/LIST]

[LIST]
[*]There will be an "Enable" link to the right. **Do not click this! **Its a trap. [B];-)
[/B]
[/LIST]

[LIST]
[*]None of your old Extensions will work at this point!
[/LIST]

[LIST]
[*]Restart Firefox again (No I'm not kidding).
[/LIST]

[LIST]
[*]Now your old Extensions will be enabled and *may* be working.
[/LIST]
**Optional **

[LIST]
[*]Go to Add-ons > Extensions. This time use the "Compatibility" button to report if the add-on is working or not.
[/LIST]
Your add-ons will still display a warning that it is "incompatible with 4.0b9pre".
If you have reported that it still works then the  "Compatibility" button turns in to a green tick with the words "Works properly."
[B]
Observations[/B]

It works... so thats great but I have to say that I found it very unintuitive.

---

### Post by SilverWave on 2010-12-22
**Latest Update: Firefox Sync 1.6 (December 22, 2010)**

           **Recent changes**


[LIST]
[*](1.6) Accept old-style 20 character Sync Keys in dashed form
[*](1.6b5) Backward-compatibility fix for old Sync Keys
[*](1.6b4) Fix reliability issues in crypto procedures and key caching
[*](1.6b3) Better error handling and recovery for various key errors
[*](1.6b3) Fix HKDF implementation in crypto
[*](1.6b2) Performance and correctness fixes
[*](1.6b1) Employ a simpler crypto infrastructure. This  provides a newer storage format and requires that all computers  connected to the account are upgraded to this verfsion of Firefox Sync  or higher.
[*](1.6b1) Several performance improvements.
[*](1.6b1) Improved preference sync.
[/LIST]
 
Works fine in 3.6 but still not showing "Add Device", which does show in FF4.0b9pre

Firefox Mobile Beta3 Sync worked like a dream - All you do is connect and you are presented with a code to input on your desktop PC browser. That's it all done :-)

---

### Post by SilverWave on 2010-12-24
Any one interested in Sync and Security may wish to watch this bug:

[Bug 592772 - Fennec should offer to use master password]("https://bugzilla.mozilla.org/show_bug.cgi?id=592772")

This comment sums things up nicely:

> Quote: Michael Coates 2010-11-10 14:05:18 PST

I'd like to reopen the discussion on this issue. I understand we may not be
willing to block fennec for the master password. However, I think we do need to
carefully make a few design decisions in the interest of security.

Current Sync Deployment:
1. Any sync'ed passwords (from desktops/other devices) will be sync'ed to the
mobile
2. Passwords on the mobile are stored in clear text
3. A phone without builtin encryption (e.g. most of them) provides zero defense
from an attacker inspecting and removing the passwords (either via running
script or forensic inspection)
4. Mobile phones are much more likely to be lost or stolen then laptop/desktop
computers which increases the risk of unencrypted stored passwords.

Possible Solutions
1. Master password (as discussed)
2. Default to not sync passwords to mobile devices at all
3. Idea #2 by default plus user option to enable password sync with a huge
warning message on the risk they're about to accept

We need to adopt some sort of solution to mitigate this risk before we launch
fennec with sync. Otherwise our users will be caught of guard by the large
security risk they've unknowingly assumed.I also fear we will receive
significant backlash from media/security/privacy groups. Mobile banking apps
are already receiving bad press for poor security practices on mobile devices
and hackers are definitely targeting mobile devices.You have been warned :-)

---

### Post by SilverWave on 2010-12-27
Changes for the versions:
4.0~b9~hg20101218r59459+nobinonly-0ubuntu1~umd1~lucid
4.0~b9~hg20101227r59681+nobinonly-0ubuntu1~umd1~lucid

---

### Post by lovinglinux on 2010-12-29
I just got the greenlight to make extensions compatible with Firefox 4.0 instead of 4.0b9. That doesn't mean the next version will be 4.0 final, but means we are closer to the final release and no more compatibility breaking changes are expected.

:guitar:

---

### Post by SilverWave on 2011-01-05
> **lovinglinux said:**
> I just got the greenlight to make extensions compatible with Firefox 4.0 instead of 4.0b9. That doesn't mean the next version will be 4.0 final, but means we are closer to the final release and no more compatibility breaking changes are expected.

:guitar:

Well that's great news!

Firefox 4.0 is looking good :-)

---

### Post by lovinglinux on 2011-01-05
> **SilverWave said:**
> Well that's great news!

Firefox 4.0 is looking good :-)

Looks like beta 9 is scheduled for release on January 13th.

---

### Post by SilverWave on 2011-01-06
Changes for the versions:
3.6.14~hg20101218r34829+nobinonly-0ubuntu1~umd1~lucid
3.6.14~hg20110104r34855+nobinonly-0ubuntu1~umd1~lucid

Changes for the versions:
4.0~b9~hg20101227r59681+nobinonly-0ubuntu1~umd1~lucid
4.0~b9~hg20110104r59999+nobinonly-0ubuntu1~umd1~lucid

---

### Post by SilverWave on 2011-01-06
> **SilverWave said:**
> Changes for the versions:
3.6.14~hg20101218r34829+nobinonly-0ubuntu1~umd1~lucid
3.6.14~hg20110104r34855+nobinonly-0ubuntu1~umd1~lucid

Changes for the versions:
4.0~b9~hg20101227r59681+nobinonly-0ubuntu1~umd1~lucid
4.0~b9~hg20110104r59999+nobinonly-0ubuntu1~umd1~lucid

This will be the last updates until Firefox 4.0b9 is released, probably next week.

---

### Post by SilverWave on 2011-01-06
> **SilverWave said:**
> Any one interested in Sync and Security may wish to watch this bug:

[Bug 592772 - Fennec should offer to use master password]("https://bugzilla.mozilla.org/show_bug.cgi?id=592772")

You have been warned :-)

A patch has been landed for this bug...

>                                        Comment 17                   silverwav                                                  2010-12-23 22:55:53 PST                
    Created [attachment 499633]("https://bugzilla.mozilla.org/attachment.cgi?id=499633") [[details]]("https://bugzilla.mozilla.org/attachment.cgi?id=499633&action=edit")
unlock addition to master-password-question.png

>how long does that "unlock" last, especially in a world where the user might leave Firefox running for days in the background?

How about:

Ask again in; 1 Hour; 2 Hours; 3 Hours; 4 Hours; 1 Day.     


                                  Comment 18                   Vivien Nicolas (:vingtetun)                                                  2010-12-27 07:16:28 PST                
    I think adding duration for asking the master password again is an other bug,
this one is about adding a master password UI to mobile-browser.
Feel free to open a new one depending on this bug, or to create an addon to
experiment with the provided concept of master password "session"     
                                  
Comment 19                   Vivien Nicolas (:vingtetun)                                                  2010-12-27 07:57:02 PST                
    Created [attachment 499830]("https://bugzilla.mozilla.org/attachment.cgi?id=499830&action=diff") [[details]]("https://bugzilla.mozilla.org/attachment.cgi?id=499830&action=edit")
Patch - updated on the trunk

The patch is updated to work on trunk, the UI is the same as the previous
screenshot except that the style is the new one.     
Nice to see that this is being sorted :-)

This is why I love Firefox and Mozilla, decision making transparency and that they take security seriously.

---

### Post by SilverWave on 2011-01-07
> **SilverWave said:**
> A patch has been landed for this bug...

[Bug 592772 - Fennec should offer to use master password]("https://bugzilla.mozilla.org/show_bug.cgi?id=592772")

Nice to see that this is being sorted :-)

This is why I love Firefox and Mozilla, decision making transparency and that they take security seriously.

Here is a add-on to test the patch from Matt:

> [EMAIL="mbrubeck@mozilla.com"] Matt Brubeck (:mbrubeck)[/EMAIL]                                                  2011-01-07 11:16:15 PST                    I took Vivien's patch and made it into an add-on, with essentially no
modifications:
[https://addons.mozilla.org/en-US/mobile/addon/270907/](https://addons.mozilla.org/en-US/mobile/addon/270907/)

Please try out this add-on if you would like to have Master Password support. 
Any feedback or bug reports on the add-on will help when we incorporate the
feature into the browser itself.Thanks to Matt and Vivien you ppl are stars :-)

---

### Post by SilverWave on 2011-01-12
> **Notices / Schedule **

 ** Firefox 4 ** 
  Beta 9 has been built and handed off to QA (based on [this revision]("http://hg.mozilla.org/mozilla-central/rev/badef0f336d2")) Here we go!

  Unfortunately the automated builds failed so we will have to wait until tomorrow.

---

### Post by SilverWave on 2011-01-14
Changes for the versions:
3.6.14~hg20110104r34855+nobinonly-0ubuntu1~umd1~lucid
3.6.14~hg20110112r34868+nobinonly-0ubuntu1~umd1~lucid

Changes for the versions:
4.0~b9~hg20110104r59999+nobinonly-0ubuntu1~umd1~lucid
4.0~b10~hg20110114r60482+nobinonly-0ubuntu1~umd1~lucid

So this the first working Firefox 4.0b10pre daily :-)

---

### Post by SilverWave on 2011-01-14
> **SilverWave said:**
> Changes for the versions:
3.6.14~hg20110104r34855+nobinonly-0ubuntu1~umd1~lucid
3.6.14~hg20110112r34868+nobinonly-0ubuntu1~umd1~lucid

Changes for the versions:
4.0~b9~hg20110104r59999+nobinonly-0ubuntu1~umd1~lucid
4.0~b10~hg20110114r60482+nobinonly-0ubuntu1~umd1~lucid

So this the first working Firefox 4.0b10pre daily :-)

Seemed to be OK in limited testing on Lucid 64bit so I have loaded to the Monthly PPA's as well.

---

### Post by SilverWave on 2011-01-15
[Let me check out some demos!]("http://blog.vlad1.com/2010/12/21/webgl-in-firefox-4-beta-8/")

[http://webglsamples.googlecode.com/hg/aquarium/aquarium.html](http://webglsamples.googlecode.com/hg/aquarium/aquarium.html)

[IMG]http://blog.vlad1.com/wp-content/uploads/2010/12/aquarium.png[/IMG]

[http://videos.mozilla.org/serv/mozhacks/flight-of-the-navigator/](http://videos.mozilla.org/serv/mozhacks/flight-of-the-navigator/)

[IMG]http://blog.vlad1.com/wp-content/uploads/2010/12/fotn.png[/IMG][IMG]http://blog.vlad1.com/wp-content/uploads/2010/12/fotn.png[/IMG]

[http://bodybrowser.googlelabs.com/body.html#](http://bodybrowser.googlelabs.com/body.html#)

[IMG]http://blog.vlad1.com/wp-content/uploads/2010/12/bodybrowser.png[/IMG]

well... at least if you have a NVIDIA GeForce 8600 GTS :-)

[Why Firefox On Linux Is Not Accelerated]("http://weblogs.mozillazine.org/gerv/archives/2011/01/why_firefox_on_linux_is_not_accelerated.html?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+HackingForChrist+%28Hacking+for+Christ%29")

---

### Post by SilverWave on 2011-01-16
> Recent Firefox betas replaced the menu bar with a Firefox button. Under  Linux, this is not enabled by default, but right-clicking on the menu  bar allows to disable the menu bar, which enables the Firefox button.

The button is not exactly very appealing, and takes quite a lot of  horizontal space on the tab bar. But with a few lines of CSS, this can  fortunately be changed. Edit the chrome/userChrome.css file under your user profile, and add the following lines:[Replacing the Firefox button with an icon]("http://glandium.org/blog/?p=1547")
```
#appmenu-toolbar-button {
  list-style-image: url("chrome://branding/content/icon16.png");
}
#appmenu-toolbar-button > .toolbarbutton-text,
#appmenu-toolbar-button > .toolbarbutton-menu-dropmarker {
  display: none !important;
}
```Well that worked... but I had to copy the chrome/userChrome.css from my ff3.6 profile.

That is I had no chrome/ folder... weird.

---

### Post by SilverWave on 2011-01-16
**[How to use feed auto-discovery in Firefox 4]("http://decafbad.com/blog/2011/01/15/how-to-use-feed-auto-discovery-in-firefox-4")**


Customize which buttons and controls appear on the toolbar.

If you scroll down in the panel, you&#8217;ll see a &#8220;**Subscribe**&#8221; button. Drag that from the panel to a position in the toolbar.
[IMG]http://decafbad.com/blog/wp-content/uploads/2011/01/feed-sub-04.png[/IMG]
Note1:
**If you actually used RSS you would, unlike this author of the above screen shot, have the bookmarks bar viable and have all your RSS feeds showing on it for ease of access ;-)**

Note2:
I think Mozilla missed fully exploiting RRS in Firefox after a great start with LiveBookMarks...

You can fix it like I did with some small add-ons...

I use Boox with Places Full Tiles and Stay-Open Menu.

RSS nirvana :-)

Boox is still at 3.6  and I cant move to FF 4.0 only until its updated.

---

### Post by SilverWave on 2011-01-20
Changes for the versions:
3.6.14~hg20110112r34868+nobinonly-0ubuntu1~umd1~lucid
3.6.14~hg20110119r34882+nobinonly-0ubuntu1~umd1~lucid


Changes for the versions:
4.0~b10~hg20110114r60482+nobinonly-0ubuntu1~umd1~lucid
4.0~b10~hg20110120r60909+nobinonly-0ubuntu1~umd1~lucid

---

### Post by SilverWave on 2011-01-21
> [B][Firefox 4 beta logistics](http://christian.legnitto.com/blog/2011/01/20/firefox-4-beta-logistics/)
[/B]

**Summary**

 
[LIST=1]
[*] We’ll take the most recent green changeset from mozilla-central this Friday, 2011-01-21 at 2:00 pm PST and call that beta 10
[LIST]
[*]The tree will close for < 15 minutes for this (if at all)
[*]We’ll freeze nightly updates at or around the changeset we branched from (likely only for the weekend)
[*]Any problems with the beta will be dealt with on the relbranch
[/LIST]
 
[*]We will release beta 10 as soon as possible during the week of the 24th
[*]We’ll take the most recent green changeset from mozilla-cental on Friday, 2011-01-28 at 2:00 pm PST (or sooner if the remaining [&field0-1-0=status_whiteboard&field0-0-0=cf_blocking_20&type0-0-0=anywordssubstr&value0-0-0=beta&resolution=---"]betaN hardblockers]("https://bugzilla.mozilla.org/buglist.cgi?type0-1-0=anywordssubstr&query_format=advanced&value0-1-0=[hardblocker) are finished) and call that beta 11
[LIST]
[*]The tree will close for < 15 minutes for this (if at all)
[*]We’ll freeze nightly updates at or around the changeset we branched from (likely only for the weekend)
[*]Any problems with the beta will be dealt with on the relbranch
[/LIST]
 
[*]We will release beta 11 as soon as possible during the week of the 31st
[/LIST]
 

Well that's interesting!

---

### Post by SilverWave on 2011-01-23
> **Latest Update: Firefox Sync 1.6.2 (January 20, 2010)**

           **[Recent changes]("https://services.mozilla.com/sync/updated/changelog.html")**

           
[LIST]
[*](1.6.2) Fix bookmark reordering and duplication issues on upgrade
[*](1.6.2) Fix history and form sync compatibility issues
[*](1.6.2) Network reliability fixes
[/LIST]


This may help if you have had some issues lately.

---

### Post by SilverWave on 2011-01-26
[[IMG]https://launchpad.net/@@/treeCollapsed[/IMG]         [IMG]https://launchpad.net/@@/package-source[/IMG]         firefox-4.0 - 4.0~b11~hg20110126r61302+nobinonly-0ubuntu1~umd1~lucid]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+sourcepub/1474079/+listing-archive-extra")

Oh well we will keep checking but its not that long until the next beta!

---

### Post by SilverWave on 2011-01-29
After a week of build failures 

[[IMG]https://launchpad.net/@@/treeCollapsed[/IMG]         [IMG]https://launchpad.net/@@/package-source[/IMG]         firefox-4.0 - 4.0~b11~hg20110129r61581+nobinonly-0ubuntu1~umd1~lucid       ]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+sourcepub/1477854/+listing-archive-extra")

Looks the business.

Testing as we speak :-)

---

### Post by SilverWave on 2011-01-29
Changes for the versions:
3.6.14~hg20110119r34882+nobinonly-0ubuntu1~umd1~lucid
3.6.15~hg20110129r34899+nobinonly-0ubuntu1~umd1~lucid

Changes for the versions:
4.0~b10~hg20110120r60909+nobinonly-0ubuntu1~umd1~lucid
4.0~b11~hg20110129r61581+nobinonly-0ubuntu1~umd1~lucid

So that means you have all the 4.0b10 stuff plus all the code for 4.0b11 that's landed to date.

---

### Post by SilverWave on 2011-01-29
> **SilverWave said:**
> Changes for the versions:
3.6.14~hg20110119r34882+nobinonly-0ubuntu1~umd1~lucid
3.6.15~hg20110129r34899+nobinonly-0ubuntu1~umd1~lucid

Changes for the versions:
4.0~b10~hg20110120r60909+nobinonly-0ubuntu1~umd1~lucid
4.0~b11~hg20110129r61581+nobinonly-0ubuntu1~umd1~lucid

So that means you have all the 4.0b10 stuff plus all the code for 4.0b11 that's landed to date.

Updated the monthly PPA's as well.

Well done Mozilla! Firfox 4.0 is almost done :-)

---

### Post by SilverWave on 2011-02-03
Changes for the versions:
3.6.15~hg20110129r34899+nobinonly-0ubuntu1~umd1~lucid
3.6.15~hg20110202r34916+nobinonly-0ubuntu1~umd1~lucid


Changes for the versions:
4.0~b11~hg20110129r61581+nobinonly-0ubuntu1~umd1~lucid
4.0~b12~hg20110203r61824+nobinonly-0ubuntu1~umd1~lucid


So that means you have all the 4.0b11 stuff plus all the code for 4.0b12 that's landed to date.

---

### Post by SilverWave on 2011-02-03
> **SilverWave said:**
> 
Changes for the versions:
4.0~b11~hg20110129r61581+nobinonly-0ubuntu1~umd1~lucid
4.0~b12~hg20110203r61824+nobinonly-0ubuntu1~umd1~lucid


So that means you have all the 4.0b11 stuff plus all the code for 4.0b12 that's landed to date.

Updated the monthly PPA's as well.

The tempo is getting faster... the B12pre followed on very quickly :smile:

---

### Post by SilverWave on 2011-02-05
[Boox 3 alpha 1 for Firefox 4 is Available!]("http://joliclic.free.fr/blog/index.php?post/2011/01/22/Boox-3-alpha-1-for-Firefox-4&pub=1#pr")

> Yes!!!!!!!!!!!!!!!
   My Deepest Thanks :-)
   OK... it works! WHOOT!
   I think I can now move over to FF4.0 fulltime :-D


---

### Post by SilverWave on 2011-02-05
> **SilverWave said:**
> [Boox 3 alpha 1 for Firefox 4 is Available!]("http://joliclic.free.fr/blog/index.php?post/2011/01/22/Boox-3-alpha-1-for-Firefox-4&pub=1#pr")


[Tab Utilities 1.0]("https://addons.mozilla.org/en-US/firefox/addon/tab-utilities/") is a great find... it does the job of various different add-ons while it also allows a lot of tab related fine control.

So far I have uninstalled: NewTabUrl TabCounter and Stay Open Menu.  :-)

To enable middle clicking to allow you to open multiple items from the LiveBookMarks feed in Boox do this:

Add-ons > Preferences > Mouse > M-Click >
   On Bookmarks > Stay menu open

---

### Post by SilverWave on 2011-02-05
[QUOTE=SilverWave]Works with FF4.0b12pre so that's good :-)
Was able to just copy all my 3.6 scripts over to my 4.0 profile.
The new scripts show in Add-ons under User Scripts.

The ability to easily add [www.example.com*]("http://www.example.com*") from the manager has been lost though :-(

Its  going to be a pain but I will keep FF3.6 around so I can create the  script from Platypus and save in the old Greasemonkey. Then I can use  the old manager to update includes.

I may just provide a link to my FF3.6 profile actually hmm will have to investigate if that will work correctly under Ubuntu.
Anyway  nasty workaround or not this was one of the last "must have" add-ons  that were stopping me moving to FF4.0 full-time. so worth the  aggravation ;-) 
[/QUOTE]

Not happy with the new manager but as I can only use Platypus with FF3.6 I was going to have to do something similar in any case.

And I was really missing my 60 scripts!



Note:
FF3.6 had updated Greasemonkey so I had to uninstall and reinstall with the Version [0.8.20100408.6]("https://addons.mozilla.org/en-US/firefox/addon/greasemonkey/versions/") from April 8 2010.

---

### Post by SilverWave on 2011-02-05
[How to Block Distracting Animated Favicons]("http://lifehacker.com/5036881/how-to-block-distracting-animated-favicons")


> Lifehacker: **Blocking for a Single Site**

 If there's a single site that is giving you trouble, you can use [the Adblock Plus Firefox extension]("http://adblockplus.org/en/")  to block the offending favicon. Just open up Blockable items, find the  favicon in the list and choose "Block this item" to get rid of it. Here is an example:

[http://news.softpedia.com/cat/Science/](http://news.softpedia.com/cat/Science/)

How annoying is that!

I blocked ||s2.softpedia-static.com/favicon_a.gif

---

### Post by SilverWave on 2011-02-10
Changes for the versions:
4.0~b12~hg20110203r61824+nobinonly-0ubuntu1~umd1~lucid
4.0~b12~hg20110210r62284+nobinonly-0ubuntu1~umd1~lucid

This change is not from a source that supports changelogs.

---

### Post by SilverWave on 2011-02-13
**WHOOT! Sanity has prevailed!**

[Bug 541656 - Display hyperlink URLs at bottom of window (instead of right side of location bar)](https://bugzilla.mozilla.org/show_bug.cgi?id=541656)

Devs have dumped the brain-dead idea of displaying hyperlink URLs in the location bar.

[COLOR=Red]Which had to be the worst UI design decision of all time.[/COLOR]

Now just doing        the same as chrome... thank god.

---

### Post by SilverWave on 2011-02-18
Changes for the versions:
4.0~b12~hg20110214r62499+nobinonly-0ubuntu1~umd1~lucid
4.0~b12~hg20110217r62724+nobinonly-0ubuntu1~umd1~lucid

---

### Post by SilverWave on 2011-02-24
So that means 4.0b12 is done :-)

Changes for the versions:
4.0~b12~hg20110223r62975+nobinonly-0ubuntu1~umd1~lucid
4.0~b13~hg20110224r63035+nobinonly-0ubuntu1~umd1~lucid

Ever closer to the Final release of 4.0!

---

### Post by SilverWave on 2011-02-24
> **SilverWave said:**
> So that means 4.0b12 is done :-)

Changes for the versions:
4.0~b13~hg20110224r63035+nobinonly-0ubuntu1~umd1~lucid

Ever closer to the Final release of 4.0!

Nice.

---

### Post by SilverWave on 2011-03-05
Changes for the versions:
4.0~b13~hg20110303r63299+nobinonly-0ubuntu1~umd1~lucid
4.0~b13~hg20110305r63332+nobinonly-0ubuntu1~umd1~lucid

Obviously this will be the next RC.

---

### Post by SilverWave on 2011-03-05
Updated Monthly and Weekly PPA's as there were a lot of security fixes.

firefox - 3.6.16~hg20110303r34968+nobinonly-0ubuntu1~umd1~karmic

---

### Post by SilverWave on 2011-03-12
Oh oh! Looks like chrisccoulson is annoyed at Ubuntuzilla :-) > 

  [ Fabien Tassin ]  -- Fabien Tassin <[fta@ubuntu.com]("https://launchpad.net/%7Efta")>   Sat, 12 Mar 2011 05:00:57 +0100
Fix up the mess left by Ubuntuzilla rather than leaving our official     package in a broken and inconsistent state, which ends up with users     reporting bugs to Launchpad and giving us a bad reputation. If     /usr/bin/firefox has been diverted and there is no /usr/bin/firefox     provided on the system, just do the job of whatever package it was that     broke the users install and remove the diversion for them. This should     hopefully stop the frequently reported bugs we get from Ubuntuzilla users     about /usr/bin/firefox being missing     - update debian/firefox.postinst.in     - Fixes LP: [#512937]("https://launchpad.net/bugs/512937"), LP: [#529136]("https://launchpad.net/bugs/529136"), LP: [#552919]("https://launchpad.net/bugs/552919"), LP: [#572733]("https://launchpad.net/bugs/572733"), LP: [#574111]("https://launchpad.net/bugs/574111"),       LP: [#599978]("https://launchpad.net/bugs/599978"), LP: [#600271]("https://launchpad.net/bugs/600271"), LP: [#610522]("https://launchpad.net/bugs/610522"), LP: [#610756]("https://launchpad.net/bugs/610756"), LP: [#610907]("https://launchpad.net/bugs/610907"),       LP: [#612162]("https://launchpad.net/bugs/612162"), LP: [#620400]("https://launchpad.net/bugs/620400"), LP: [#623980]("https://launchpad.net/bugs/623980"), LP: [#625014]("https://launchpad.net/bugs/625014"), LP: [#630643]("https://launchpad.net/bugs/630643"),       LP: [#635166]("https://launchpad.net/bugs/635166"), LP: [#638342]("https://launchpad.net/bugs/638342"), LP: [#641838]("https://launchpad.net/bugs/641838"), LP: [#658828]("https://launchpad.net/bugs/658828"), LP: [#668809]("https://launchpad.net/bugs/668809"),       LP: [#672282]("https://launchpad.net/bugs/672282"), LP: [#676239]("https://launchpad.net/bugs/676239"), LP: [#707704]("https://launchpad.net/bugs/707704"), LP: [#724090]("https://launchpad.net/bugs/724090")   * Don't allow users to report bugs with apport-bug when /usr/bin/firefox     has been diverted     - update debian/firefox.py.in

Update:
> **chrisccoulson said:**
> No, that was actually me. Fabien's name is  in the changelog because he runs the nightly builds, but that change  was actually committed by me

Fixed :-D

---

### Post by chrisccoulson on 2011-03-12
> **SilverWave said:**
> Oh oh! Looks like Fabien is annoyed at Ubuntuzilla :-)

No, that was actually me. Fabien's name is in the changelog because he runs the nightly builds, but that change was actually committed by me

---

### Post by SilverWave on 2011-03-12
> **chrisccoulson said:**
> No, that was actually me. Fabien's name is in the changelog because he runs the nightly builds, but that change was actually committed by me

Fixed :-D

---

### Post by SilverWave on 2011-03-12
Changes for the versions:
4.0~b13~hg20110308r63349+nobinonly-0ubuntu1~umd1~lucid
4.0~b13~hg20110312r63396+nobinonly-0ubuntu1~umd1~lucid

---

### Post by SilverWave on 2011-03-19
Well it looks like this could be very useful for a lot of people who want the latest official release but not a nightly build.
[https://launchpad.net/~mozillateam/+archive/firefox-next](https://launchpad.net/~mozillateam/+archive/firefox-next)
> 
This PPA will contain Milestone builds of the next version of Firefox (alpha, beta, RC)


**Add a Firefox 4.0 PPA:**
```

sudo add-apt-repository ppa:mozillateam/firefox-next
```[B]
Update & Install[/B]
     ```

sudo apt-get update
sudo apt-get install firefox-4.0
```

---

### Post by SilverWave on 2011-03-20
> ________________________________________

[I]**One Daily A Week **(from ubuntu-mozilla-daily).
 The latest firefox without the update hassle[/I].

[LIST]
[*]One ppa per Ubuntu Version (containing both Firefox 4.0 & Firefox 3.6).
[*]Updated at the start of each Week.
[/LIST]
  ________________________________________

Note that I'm dropping Firefox 3.6 from the "***One Daily A Week***" PPA's

---

### Post by SilverWave on 2011-03-20
[Mozilla outlines 16-week Firefox development cycle]("http://arstechnica.com/open-source/news/2011/03/mozilla-outlines-16-week-firefox-development-cycle.ars?utm_source=rss&utm_medium=rss&utm_campaign=rss")

[Mozilla Firefox: Development Process]("http://people.mozilla.com/%7Esayrer/2011/temp/process.html")

Well this is great news!

It will be interesting to see how the Ubuntu Mozilla Team respond :-)

Although Firefox-Next is a good start.

---

### Post by SilverWave on 2011-03-20
[firefox-4.0 - 4.0~rc1+build1+nobinonly-0ubuntu1~mfn~lucid1]("https://launchpad.net/%7Esilverwave/+archive/one-daily-a-month-1/+sourcepub/1559106/+listing-archive-extra")

Now that we have the Firefox-Next PPA the need for a "One Daily A Month" PPA for Firefox 4 is questionable...

...Short term I am just going to mirror Firefox-Next.

Pity we don't have usage figures on our PPA's as this would allow me to see if I could close them down without affecting to many ppl.

So to summarise:

**"One Daily A Week" PPA's for ****Firefox 4.0**[B] are still going to be updated from the daily builds.

[/B]**"One Daily A Month" PPA's for ****Firefox 4.0**** are going to mirror Firefox-Next.**
**"One Daily A Month" PPA's for ****Firefox 3.6**** are still going to be updated from the daily builds.**

---

### Post by lovinglinux on 2011-03-20
> **SilverWave said:**
> [Mozilla outlines 16-week Firefox development cycle]("http://arstechnica.com/open-source/news/2011/03/mozilla-outlines-16-week-firefox-development-cycle.ars?utm_source=rss&utm_medium=rss&utm_campaign=rss")

[Mozilla Firefox: Development Process]("http://people.mozilla.com/%7Esayrer/2011/temp/process.html")

Well this is great news!

It will be interesting to see how the Ubuntu Mozilla Team respond :-)

Although Firefox-Next is a good start.

[sarcasm]This will be great for extension developers[/sarcasm]

---

### Post by SilverWave on 2011-03-20
> **lovinglinux said:**
> [sarcasm]This will be great for extension developers[/sarcasm]

From Ars:

> Arguably the biggest challenge for faster iteration is going to be the  question of extension compatibility. The proposal document acknowledges  that the problem exists but doesn't provide any suggested solutions.  It's an area where Mozilla is going to have to do some serious  problem-solving.

Interesting.

---

### Post by SilverWave on 2011-03-20
This will be the landing page for anyone who needs the "One Daily A Month" instructions.

[I]One Daily A Month PPAs for Firefox 4.0 are now just mirrors of Firefox-Next

[/I]One Daily A Month PPAs for Firefox 3.6 are the same as normal but moving details here as they will have diminishing relevance.
________________________________________

[I]**One Daily A Month **(from ubuntu-mozilla-daily).
 The latest firefox without the update hassle[/I].

[LIST]
[*]One ppa for each Firefox.
[*]Updated at the start of each month.
[/LIST]
________________________________________

[B]Add a Firefox 4.0 PPA:
[/B]
[Firefox-4.0 - One Daily A Month #5 - Maverick]("https://launchpad.net/%7Esilverwave/+archive/one-daily-a-month-5") 
```
sudo add-apt-repository ppa:silverwave/one-daily-a-month-5
```[Firefox-4.0 - One Daily A Month #1 - Lucid]("https://launchpad.net/%7Esilverwave/+archive/one-daily-a-month-1")
```
  sudo add-apt-repository ppa:silverwave/one-daily-a-month-1
```[Firefox-4.0 - One Daily A Month #3 - Karmic]("https://launchpad.net/%7Esilverwave/+archive/one-daily-a-month-3")
```
 sudo add-apt-repository ppa:silverwave/one-daily-a-month-3
```**Add a Firefox 3.6 PPA:**

[Firefox-3.6 - One Daily A Month #4 - Maverick]("https://launchpad.net/%7Esilverwave/+archive/one-daily-a-month-4")
```
 sudo add-apt-repository ppa:silverwave/one-daily-a-month-4
```[Firefox-3.6 - One Daily A Month #0 - Lucid]("https://launchpad.net/%7Esilverwave/+archive/one-daily-a-month-0")
```
 sudo add-apt-repository ppa:silverwave/one-daily-a-month-0
```[Firefox-3.6 - One Daily A Month #2 - Karmic]("https://launchpad.net/%7Esilverwave/+archive/one-daily-a-month-2")
```
sudo add-apt-repository ppa:silverwave/one-daily-a-month-2
```**Update & Install**
```
sudo apt-get update
sudo apt-get install firefox
sudo apt-get install firefox-4.0
```Applications   > Internet.
FF3.6 is called "Namoroka  Web Browser" (Firefox pre-release).
FF4.0 is called "Minefield 4.0 Web Browser" (Browse the Bleeding Edge).

________________________________________

:)

---

### Post by SilverWave on 2011-03-20
Changes for the versions:
3.6.16~hg20110308r34972+nobinonly-0ubuntu1~umd1~lucid
3.6.17~hg20110319r35006+nobinonly-0ubuntu1~umd1~lucid

---

### Post by SilverWave on 2011-03-20
[IMG]http://mozcom-cdn.mozilla.net/img/firefox/beta/4/firstrun/illustration-rc.jpg[/IMG]

Testing out the new PPA:

Changes for the versions:
4.0~b13~hg20110319r63446+nobinonly-0ubuntu1~umd1~lucid
4.0~rc1+build1+nobinonly-0ubuntu1~mfn~lucid1

As you can see the RC1 trumps the daily build.

2 days to go for the full release :-)

Mozilla/5.0 (X11; Linux x86_64; rv:2.0) Gecko/20110310 Firefox/4.0 Firefox/4.0 ID:20110310030225

[Update]

After updating my add-ons I needed to uninstall/reinstall the Add-on Compatibility Reporter to get it working again.

---

### Post by SilverWave on 2011-03-21
> **SilverWave said:**
> 

Testing out the new PPA:

Changes for the versions:
4.0~b13~hg20110319r63446+nobinonly-0ubuntu1~umd1~lucid
4.0~rc1+build1+nobinonly-0ubuntu1~mfn~lucid1

As you can see the RC1 trumps the daily build.

2 days to go for the full release :-)

Mozilla/5.0 (X11; Linux x86_64; rv:2.0) Gecko/20110310 Firefox/4.0 Firefox/4.0 ID:20110310030225

[Update]

After updating my add-ons I needed to uninstall/reinstall the Add-on Compatibility Reporter to get it working again.

Issues with "Add-on Compatibility Reporter" forgetting it should be enabled after a reboot...

Don't have the time to troubleshoot so:

Uninstalled 4.0~rc1+build1+nobinonly-0ubuntu1~mfn~lucid1

Disabled the Firefox-next PPA in Software Sources.

Installed Firefox-4.0 from my [One Daily A Week]("https://launchpad.net/%7Esilverwave/+archive/testing0") PPA.

4.0~b13~hg20110319r63446+nobinonly-0ubuntu1~umd1~lucid

___

Cant beat backups ;-)

---

### Post by lovinglinux on 2011-03-21
Lots of things going on. The new ppa, Ubuntuzilla ceasing operations and all that stuff you have been posting. :shock:

I also have decided to cease the development of FoxTester. Now I am recommending the new Mozilla's profile Manager for managing multiple versions and profiles.

> **SilverWave said:**
> Issues with "Add-on Compatibility Reporter" forgetting it should be enabled after a reboot...

Don't have the time to troubleshoot so:

Uninstalled 4.0~rc1+build1+nobinonly-0ubuntu1~mfn~lucid1

Disabled the Firefox-next PPA in Software Sources.

Installed Firefox-4.0 from my [One Daily A Week]("https://launchpad.net/%7Esilverwave/+archive/testing0") PPA.

4.0~b13~hg20110319r63446+nobinonly-0ubuntu1~umd1~lucid
__

Cant beat backups ;-)

I am not experiencing such issue.

---

### Post by SilverWave on 2011-03-21
> **lovinglinux said:**
> Lots of things going on.


Very true!

> The new ppa,Yeah long overdue IMHO :-)

> Ubuntuzilla ceasing operationsWow I missed that, but it makes sense as its really not needed any more. 

>  and all that stuff you have been posting. :shock:Yes Firefox-Next was just what I wanted (easy installs of Firefox betas, RC's etc., for all Ubuntu users).
Particularly as Mozilla are upping the tempo of releases.
Its going to pretty much match what I was trying to accomplish with my One Daily A Month PPA's.

One less thing I need to worry about :D (Although it did necessitate a major rewrite of the How to).

> I also have decided to cease the development of FoxTester. Now I am recommending the new Mozilla's profile Manager for managing multiple versions and profiles.Oh I will have to have a look into it, thanks for the tip.

> 
I am not experiencing such issue [re Add-on Compatibility Reporter].
Good! that means its probably either my profile or on of my many add-ons ;-)

Although... everything works with the daily I swapped the RC1 out for... hmm interesting!

---

### Post by lovinglinux on 2011-03-21
> **SilverWave said:**
> Oh I will have to have a look into it, thanks for the tip.

Here is the link:

[https://developer.mozilla.org/en/Profile_Manager](https://developer.mozilla.org/en/Profile_Manager)

Is pretty good and can also do profile backups.

---

### Post by SilverWave on 2011-03-22
[https://launchpad.net/~mozillateam/+archive/firefox-stable](https://launchpad.net/~mozillateam/+archive/firefox-stable)

**Add a Firefox 4.0 PPA:**
```

sudo add-apt-repository ppa:mozillateam/firefox-stable 
```[B]
Update & Install[/B]
     ```

sudo apt-get update
sudo apt-get install firefox
```

---

### Post by SilverWave on 2011-03-22
[SIZE=4][COLOR=Red]**Warning!**[/COLOR][/SIZE][COLOR=Red]

Just tested and bear in mind that this will upgrade your Firefox 3.6 to 4.0...[/COLOR] [COLOR=Red]

That is you will no longer have access to Firefox 3.6![/COLOR] 


> **SilverWave said:**
> [https://launchpad.net/~mozillateam/+archive/firefox-stable]("https://launchpad.net/%7Emozillateam/+archive/firefox-stable")

**Add a Firefox 4.0 PPA:**
```

sudo add-apt-repository ppa:mozillateam/firefox-stable 
```[B]
Update & Install[/B]
     ```

sudo apt-get update
sudo apt-get install firefox
```

---

### Post by SilverWave on 2011-03-22
> **SilverWave said:**
> [SIZE=4][COLOR=Red]**Warning!**[/COLOR][/SIZE][COLOR=Red]

Just tested and bear in mind that this will upgrade your Firefox 3.6 to 4.0...[/COLOR] [COLOR=Red]

That is you will no longer have access to Firefox 3.6![/COLOR]

If you need to undo the upgrade and put Firefox 3.6 back as it was:

(Hopefully you have a backup of your Firefox folder :-|)

Uninstall Firefox from Package Manager.
[LIST=1]
[*]Optional: Replace you Firefox folder with your saved backup copy.
[*]In Software sources remove the entry for Firefox-stable.
[*]Via Package Manager install Firefox. (Version should be 3.6)
[/LIST]
You are now sorted! :-)

---

### Post by jquest71 on 2011-03-22
Sweet! I was really excited about fx4 when I put the RC on my Win7 netbook, but now that I'm running Ubuntu it's running even better. Thanks for posting the instructions on how to get the stable update. Now, is there an easy way to uninstall the Minefield developer preview version?

Thanks!

JQ


> **SilverWave said:**
> [https://launchpad.net/~mozillateam/+archive/firefox-stable]("https://launchpad.net/%7Emozillateam/+archive/firefox-stable")

**Add a Firefox 4.0 PPA:**
```

sudo add-apt-repository ppa:mozillateam/firefox-stable 
```[B]
Update & Install[/B]
     ```

sudo apt-get update
sudo apt-get install firefox
```

---

### Post by SilverWave on 2011-03-22
> **jquest71 said:**
> Sweet! I was really excited about fx4 when I put the RC on my Win7 netbook, but now that I'm running Ubuntu it's running even better. Thanks for posting the instructions on how to get the stable update. Now, is there an easy way to uninstall the Minefield developer preview version?

Thanks!

JQ

Hi,

Uninstall firefox-4.0
Then remove firefox-next from your "Software Sources"

That should do it as the firefox-stable package is "firefox".

Cheers.

---

### Post by SilverWave on 2011-03-22
Changes for the versions:
4.0~b13~hg20110319r63446+nobinonly-0ubuntu1~umd1~lucid
4.0~b13~hg20110321r63449+nobinonly-0ubuntu1~umd1~lucid

---

### Post by vagrale13 on 2011-03-23
> **SilverWave said:**
> Hi,

Uninstall firefox-4.0
Then remove firefox-net from your "Software Sources"

That should do it as the firefox-stable package is "firefox".

Cheers.
One safe way to back Firefox 3.6*
go *System* - *Administration* - *Software sources* - 
and **other software** category uncheck
for **Ubuntu 10.10** *=>* *ppa.launchpad.net/mozillateam/firefox-stable/ubuntu *maverick main 
for **Ubuntu 10.04** *=>* *ppa.launchpad.net/mozillateam/firefox-stable/ubuntu lucid main* 
  **Close** and in the question **Reload**.
Then close **Firefox**, open terminal and run the following commands
```
sudo apt-get remove firefox ubufox xul-ext-ubufox
sudo apt-get update
```then run
```
sudo apt-get install firefox firefox-gnome-support
```and then
```
sudo apt-get update && sudo apt-get upgrade
```After just open  **Firefox,** and you have again the old version **Firexox 3.6* **

---

### Post by SilverWave on 2011-03-23
> Originally Posted by **jquest71**                     [[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=10589477#post10589477")                 
                 [I]Sweet! I was really excited about fx4  when I put  the RC on my Win7 netbook, but now that I'm running Ubuntu  it's running  even better. Thanks for posting the instructions on how to  get the  stable update. [COLOR=Blue]Now, is there an easy way to uninstall the  Minefield  developer preview version?[/COLOR]

Thanks!

JQ

[/I]> **SilverWave said:**
> Hi,

Uninstall firefox-4.0
Then remove firefox-next from your "Software Sources"

That should do it as the firefox-stable package is "firefox".

Cheers.

[QUOTE=vagrale13;10593216]One safe way to back Firefox 3.6*
go *System* - *Administration* - *Software sources* - 
and **other software** category uncheck
for **Ubuntu 10.10** *=>* *ppa.launchpad.net/mozillateam/firefox-stable/ubuntu *maverick main 
for **Ubuntu 10.04** *=>* *ppa.launchpad.net/mozillateam/firefox-stable/ubuntu lucid main* 
  **Close** and in the question **Reload**.
Then close **Firefox**, open terminal and run the following commands
```
sudo apt-get remove firefox ubufox xul-ext-ubufox
sudo apt-get update
```then run
```
sudo apt-get install firefox firefox-gnome-support
```and then
```
sudo apt-get update && sudo apt-get upgrade
```After just open  **Firefox,** and you have again the old version **Firexox 3.6* **



[/QUOTE]hmm I think he needed the Firefox-4.0 RC1 Milestone removed...

---

### Post by vagrale13 on 2011-03-24
> **SilverWave said:**
> hmm I think he needed the Firefox-4.0 RC1 Milestone removed...
I think you have right. This is for *mozillateam/firefox-stable *PPA.

Thanks for *PPA* :popcorn:

---

### Post by SilverWave on 2011-03-24
Changes for the versions:
3.6.17~hg20110319r35006+nobinonly-0ubuntu1~umd1~lucid
3.6.17~hg20110324r35011+nobinonly-0ubuntu1~umd1~lucid

___

  Separate XULRunner update:

Changes for the versions:
1.9.2.15+build1+nobinonly-0ubuntu0.10.04.1
1.9.2.16+build1+nobinonly-0ubuntu0.10.04.1

Version 1.9.2.16+build1+nobinonly-0ubuntu0.10.04.1: 

  * New upstream release v1.9.2.16 (FIREFOX_3_6_16_BUILD1)
    - see USN-1091-1 
___

---

### Post by SilverWave on 2011-03-24
You've been updated to the latest version of Firefox Sync!
> Latest Update: Firefox Sync 1.7 (March 9, 2011)
Recent changes

    * (1.7) Performance improvements
    * (1.6.3) Better handling of smart bookmarks
    * (1.6.3) Handle restoring bookmarks from backup better
    * (1.6.2) Fix bookmark reordering and duplication issues on upgrade
    * (1.6.2) Fix history and form sync compatibility issues
    * (1.6.2) Network reliability fixes
    * (1.6.1) Provide the "Add a Device" link under Sync Options for Firefox 3.5/3.6
    * (1.6) Accept old-style 20 character Sync Keys in dashed from
    * (1.6b5) Backward-compatibility fix for old Sync Keys
    * (1.6b4) Fix reliability issues in crypto procedures and key caching
    * (1.6b3) Better error handling and recovery for various key errors
    * (1.6b3) Fix HKDF implementation in crypto
    * (1.6b2) Performance and correctness fixes
    * (1.6b1) Employ a simpler crypto infrastructure. This provides a newer storage format and requires that all computers connected to the account are upgraded to this verfsion of Firefox Sync or higher.
    * (1.6b1) Several performance improvements.
    * (1.6b1) Improved preference sync.


---

### Post by SilverWave on 2011-04-01
> Source         Uploader         Published         Status         Series         Section         Build Status
[[IMG]https://launchpad.net/@@/treeCollapsed[/IMG]         [IMG]https://launchpad.net/@@/package-source[/IMG]         firefox-4.0 - 4.0~b13~hg20110323r63531+nobinonly-0ubuntu1~umd1~lucid       ]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+sourcepub/1562732/+listing-archive-extra")                                  [(changes file)]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+files/firefox-4.0_4.0%7Eb13%7Ehg20110323r63531%2Bnobinonly-0ubuntu1%7Eumd1%7Elucid_source.changes")                                 [fta]("https://launchpad.net/%7Efta")                        2011-03-23     Published     Lucid     Web            [IMG]https://launchpad.net/@@/no[/IMG] []("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+buildjob/2338799")
[]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+buildjob/2338800")[[IMG]https://launchpad.net/@@/treeCollapsed[/IMG]         [IMG]https://launchpad.net/@@/package-source[/IMG]         firefox-4.0 - 4.0~b13~hg20110321r63449+nobinonly-0ubuntu1~umd1~lucid       ]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+sourcepub/1560946/+listing-archive-extra")                                  [(changes file)]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+files/firefox-4.0_4.0%7Eb13%7Ehg20110321r63449%2Bnobinonly-0ubuntu1%7Eumd1%7Elucid_source.changes")                                 [fta]("https://launchpad.net/%7Efta")                        2011-03-22     Superseded     Lucid     Web            [IMG]https://launchpad.net/@@/yes[/IMG]
                                              [         [IMG]https://launchpad.net/@@/treeCollapsed[/IMG]         [IMG]https://launchpad.net/@@/package-source[/IMG]         firefox-4.0 - 4.0~b13~hg20110319r63446+nobinonly-0ubuntu1~umd1~lucid       ]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+sourcepub/1557591/+listing-archive-extra")                                  [(changes file)]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+files/firefox-4.0_4.0%7Eb13%7Ehg20110319r63446%2Bnobinonly-0ubuntu1%7Eumd1%7Elucid_source.changes")                                 [fta]("https://launchpad.net/%7Efta")                        2011-03-19     Superseded     Lucid     Web What's next?

Cant see any new builds since the 23rd of March 2011, and that failed...

---

### Post by SilverWave on 2011-04-02
**OK I think its time to move on... so I am prepared to dump 3.6 and upgrade Firefox to 4.0 (Stable PPA).**

So if I am going to do it, lets do it right, yes its time for a clean profile :-D

After updating I still have a separate Firefox 4.0 folder.
I have deleted the contents of the Firefox folder and a new profile is created automatically on running Firefox.

---

### Post by SilverWave on 2011-04-02
> **SilverWave said:**
> **OK I think its time to move on... so I am prepared to dump 3.6 and upgrade Firefox to 4.0 (Stable PPA).**

So if I am going to do it, lets do it right, yes its time for a clean profile :grin:

After updating I still have a separate Firefox 4.0 folder.
I have deleted the contents of the Firefox folder and a new profile is created automatically on running Firefox.

Set-up a master password first.

I have set-up sync by authorising Another Device via my Minfield Firefox 4.0 package (from the dailies), all done in under 5min :-)

If you wait a few minutes all your passwords and history is pulled across :-D

Heh even your Persona's Cool! 

I am closing Firefox down and saving an archive from time to time in case I screw-up, as I don't want to have to start from the beginning :-|

---

### Post by SilverWave on 2011-04-02
First issue

[Firefox crashes with XML Parsing Error]("https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/677815")

> Binary package hint: firefox
 The newest version of Firefox installed from the Natty repositories crashes on startup with the following message:
 XML Parsing Error: undefined entity
Location: chrome://browser/content/browser.xul
Line Number 232, Column 5:    <key id="key_openAddons" key="&addons.commandkey;" command="Tools:Addons" modifiers="accel,shift"/>Here is the workaround:

> 
[Gabriel de Perthuis]("https://launchpad.net/%7Eg2p")             wrote             on 2011-03-25:                                                             [ #13]("https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/677815/comments/13")                                                        It was working when running firefox-4.0 from ubuntu-mozilla-daily/ppa which has the betas and nightlies, and quit working with mozillateam/firefox-stable which has the final firefox 4. This is because the language packs are in /usr/lib/firefox-addons/extensions/ and not /usr/lib/firefox-4.0-addons/extensions/ .
 Here is a workaround: `firefox -uilocale en`, go to the addons manager, open the language pack pane, disable language packs.
 I filed a bug over there: [https://bugzilla.mozilla.org/show_bug.cgi?id=644933](https://bugzilla.mozilla.org/show_bug.cgi?id=644933)
        
Note1: I only experienced this issue one I added [Add-on *Compatibility Reporter.*]("https://addons.mozilla.org/en-US/firefox/addon/add-on-compatibility-reporter/")
Note2: I went back to a previous backup and disabled the 3.6 GB Language Pack.

Working fine now :-)

---

### Post by SilverWave on 2011-04-02
OK now installing all my extensions (this should be part of Sync IMNSHO), but its not too bad.

The search feature of the new Add-ons Manager is fantastic!

You no longer need to visit AMO to search and download your extensions.

Instead you can do it all from within the Add-ons Manager :-)

Impressed!

---

### Post by SilverWave on 2011-04-02
Copied my greasemonkey scripts:

/home/silverwave/.mozilla/firefox-4.0/lkj9c9k1.default/gm_scripts

...to the firefox folder.

They imported fine :-D

---

### Post by SilverWave on 2011-04-02
OK nearly Done ;-)

Disabled all the plugins except Shockwave and VLC

---

### Post by SilverWave on 2011-04-02
> **History             There is the updating history and the list of known problems.**

          0.11.2011032401
[LIST]
[*]Fixed: On Firefox 4, toolbar buttons in the tab bar were unexpectedly hidden.
[*]Fixed: On Firefox 4, switching of tab groups broke tree of tabs.
[*][COLOR=RoyalBlue]Fixed: Works with [Locationbar2]("https://addons.mozilla.org/firefox/addon/locationbar%C2%B2/") correctly.[/COLOR]
[/LIST]
0.11.2011031901
[LIST]
[*]Fixed: Flexible toolbar items (like search bar) were wrongly shrunken and hidden if there were too many tabs.
[*]Fixed: Clicking on an extra toolbar item in the tab bar wrongly selected overflow-ed tabs behind the toolbar item.
[*]Fixed: In secondary browser window, bookmarks couldn't be opened after the primary browser window was closed.
[*]Fixed: Toolbar customization unexpectedly moved toolbar items before tabs, to the place after tabs.
[*]Fixed: Extra toolbar items in the tab bar can be removed by dragging correctly.
[*]Fixed: Clicks on extra toolbar items were wrongly ignored.
[*]Fixed: Tree Style Tab freezed Firefox itself when you close a last tree of tabs in the tab bar.
[*]Fixed: Pinned tabs never accept dropping of tabs.
[*]Fixed: Pinned tabs were sometimes wrongly positioned.
[*]Fixed: Tree view was unexpectedly disabled by [Personal Titlebar]("https://addons.mozilla.org/ja/firefox/addon/personal-titlebar/").
[*]Fixed: Broken appearance of pinned tabs with Tab Mix Plus gone.
[*]Fixed: Misplaced favicons in pinned tabs with Tab Mix Plus gone.
[*]Improved: A new secret preference to control collapsed/expanded  state of restored tabs,  "extensions.treestyletab.collapseExpandSubtree.sessionRestore". -1  restores the last state, 0 collapses all of restored trees, 1 expands  all of them.
[*]German locale was updated by Andy Pillip.
[/LIST]
0.11.2011021901
[LIST]
[*]Fixed: TST wrongly handled drag and drop actions on the tab bar even if it is fired in the toolbar customization.
[*]Fixed: Pinned tabs are shown with highlighted background correctly when their titles are changed.
[*]Fixed: Better compatibility with [TotalToolbar]("http://totaltoolbar.mozdev.org/").
[/LIST]
0.11.2011021601
[LIST]
[*]Improved: Buttons in the information bar to confirm how restore  other closed tabs in the tree (it is shown when you do "undo close tab"  for a tab which was in a tree) now have their suitable accesskey.
[*]Improved: Focusring is shown in tabs if tabs are focusable by userChrome.css.
[*]Improved: On Firefox 3.6 or olders, the background of the  transparent tab bar is no longer drawn if the secret pref  "extensions.treestyletab.tabbar.transparent.partialTransparency" has a  value equals to or larger than "1".
[*]Improved: An alternative drop-marker for drag and drop onto the vertical tab bar is available, for the "Default" skin.
[*]Fixed: On Minefield, closing of the current tab didn't back the focus to the owner tab.
[*]Fixed: Tearing off of multiple tabs was failed unexpectedly when [Multiple Tab Handler]("http://piro.sakura.ne.jp/xul/_multipletab.html.en") is installed.
[*]Fixed: Needless blank window was wrongly opened when a tab was teared off from the window by drag-and-drop.
[*]Fixed: On Minefield, dragging on the grippy in the splitter for the tab bar failed to resize the tab bar.
[*]Fixed: Restored tab from "Undo Close Tab" was unexpectedly opened in a collapsed tree, when [BarTab]("https://addons.mozilla.org/firefox/addon/bartab/") is installed.
[*][COLOR=RoyalBlue]Fixed: On Minefield, the appearance of the tab bar was unexpectedly broken if [RequestPolicy]("https://addons.mozilla.org/firefox/addon/requestpolicy/") is installed.[/COLOR]
[*]zh-CN locale is updated by hzhbest. Thanks!
[*]es-ES locale is updated by Tito Bouzout. Thanks!
[*]sv-SE (Swedish) locale is available, translated by Mikael Hiort af Ornäs. Thanks!
[/LIST]
0.11.2011020402
[LIST]
[*]Fixed: An error in the initialization process disappeared.
[/LIST]
0.11.2011020401
[LIST]
[*]Modified: The status panel on Minefield is shown in the another side by default, for vertical tab bar.
[*]Fixed: The API "TreeStyleTabService.position" didn't work.
[/LIST]
0.11.2011020301
[LIST]
[*]Improved: Now you can open a new blank tab in existing tree.
[*]Improved: Tabs restored from about:sessionrestore become children of the tab.
[*]Improved: Works with [DragNDrop Toolbars]("https://addons.mozilla.org/firefox/addon/dragndrop-toolbars/").
[*][COLOR=RoyalBlue]Fixed: [The status panel]("https://bugzilla.mozilla.org/show_bug.cgi?id=628654") is repositioned for bottom tab bar.[/COLOR]
[*]Fixed: Tabs in a moved tree were expanded wrongly, if the tree was collapsed.
[*]Fixed: Tabs can't be dragged if there is Tab Mix Plus.
[*]Modified: The transparency of the tab bar (for auto-hide mode) is fixed. It is no longer customizable.
[/LIST]
0.11.2011012302
[LIST]
[*]Fixed: pl locale was broken.
[/LIST]
0.11.2011012301
[LIST]
[*]Improved: The tab bar can be moved to another place with [Peronal Titlebar]("https://addons.mozilla.org/irefox/addon/personal-titlebar/")  (or otehr addons provide customizability of the tab bar). If the tab  bar is moved to another toolbar, then whole the toolbar becomes "tab  bar" for Tree Style Tab.
[*]Improved: In bookmark group tabs (about:treestyletab-group),  the existing text in the text field is automatically selected when you  click the title.
[*]Modified: TreeStyleTabService.currentTabbarPosition was renamed to TreeStyleTabService.position. For backward compatibility, the old name is still available.
[*]Fixed: Tooltip on tabs were not updated after it was shown on a twisty of a tab.
[*]Fixed: Icons of tabs were unexpectedly stretched if Tab Mix Plus is installed.
[*]Fixed: The drop position indicator for horizontal tab bar was unexpectedly shown even if the tab bar was vertical.
[*]Fixed: When TreeStyleTabService.treeViewEnabled becomes "false", then stacked tabs in horizontal tab bar are correctly unstacked.
[/LIST]
0.11.2011011301The final issue was with Tree Style Tabs, the developer has updated the extension a lot but I couldn't update as the StatusPanel was positioning itself on the right instead of the left in the new versions!

It was driving me nuts :-|

I had a look at his blog and I identified that he would call this setting "StatusPanel".

I did a search in about.config and found it!!!

Set "extensions.treestyletab.autoRepositionStatusPanel" to false and it displays correctly on the left again. :-)

---

### Post by SilverWave on 2011-04-02
All the following extensions are installed and working :-)

> *Aardvark 3.0
Adblock Plus 1.3.5
Add-on Compatibility Reporter 0.8.2
Barlesque 1.15
Boox 3.0a1
Download Statusbar 0.9.8
Greasemonkey 0.9.1
Image Zoom 0.4.6
Locationbar² 1.0.6
Make Link 11.03
Menu Editor 1.2.7
Nightly Tester Tools 3.1.2
NoSquint 2.1
OptimizeGoogle 0.78.2
Places&#8217; Full Titles 4
Re-Pagination 2011.03.24
Readability 1.3
Reliby 1.5.0
RequestPolicy 0.5.20
Shelve 1.23
Tab Utilities 1.0.2
Toolbar Buttons 1.0
Tree Style Tab 0.11.2011032401

*Officially incompatible with Firefox 4.0... but works anyway ;-)
The amazing thing is that all bar one are fully compatible with Firefox 4.0!

**This is a fantastic result for Mozilla, as incompatible key extensions can hold ppl back from updating Firefox. **
e.g. Boox is not 100% yet but I wouldn't be updating if the developer hadn't found time to release this alpha.

I remember that compatibility was much worse with Firefox 3.0 and Firefox 3.5.

---

### Post by SilverWave on 2011-04-02
Do you want to stop using this account?
This will reset all of your Sync account information and preferences.

[Cancel] [Reset All information]

[QUOTE=Richard Soderberg, Mozilla Services Operations ]Hi, the Firefox 4 desktop option "Deactivate this device" will only disconnect your desktop browser from Firefox Sync. Your existing data (bookmarks, history, passwords, etc.) will remain intact, both on your desktop and also on the Firefox Sync servers.
[/QUOTE]

I can confirm that this works as advertised (in spite of the scary message, which I think is a little misleading).

__________________

The reason I was looking into this was as follows...

I had successfully created a new clean profile using the Stable Firefox 4.0 package (profile in /home/silverwave/.mozilla/firefox) and I wanted to repurpose it for use with the Minefield Firefox 4.0 package (profile in /home/silverwave/.mozilla/firefox4.0).

But if I did that both profiles would be using the same Sync client ID... which would be bad ;-)

Using **"Deactivate this device" **on the copied profile did the trick allowing me to re authorise it via "Add A Device" on the original profile.

Heh Sync is loads and loads of fun :-D

__________________

Note:
Prior to all of this I used the old Minefield Firefox 4.0 profile to authorise the new clean profile I had created with Stable Firefox 4.0.

Round and round we go ;-)

---

### Post by SilverWave on 2011-04-03
> **SilverWave said:**
> [Boox 3 alpha 1 for Firefox 4 is Available!]("http://joliclic.free.fr/blog/index.php?post/2011/01/22/Boox-3-alpha-1-for-Firefox-4&pub=1#pr")
> Yes!!!!!!!!!!!!!!!
   My Deepest Thanks :smile:
   OK... it works! WHOOT!
   I think I can now move over to FF4.0 fulltime :grin:


                    **Workaround for "Mark as read." issue.**

   Set History to "Boox History" and Restart.
   Right Click the feed and then click "Mark as read"
Click one of the feed items to update the feed status from bold.

---

### Post by SilverWave on 2011-04-03
Here is a list of the adjustments I make to the default profile:

The usual voodoo:[INDENT]browser.display.show_image_placeholders: False
network.http.max-connections: 48
network.http.max-connections-per-server: 32
network.http.max-connections-per-proxy: 16
network.http.max-persistent-connections-per-server : 32
network.http.pipelining: True
network.http.pipelining.maxrequests: 8 (Hard-coded Limit)
network.http.proxy.pipelining: True
[/INDENT][INDENT] ui.submenuDelay: 0


[/INDENT]Specials:[INDENT]browser.sessionstore.max_concurrent_tabs: 0
[/INDENT]

---

### Post by lovinglinux on 2011-04-07
Check this out:

[https://developer.mozilla.org/devnews/index.php/2011/04/07/new-development-channels-and-repositories-for-rapid-releases/](https://developer.mozilla.org/devnews/index.php/2011/04/07/new-development-channels-and-repositories-for-rapid-releases/)

---

### Post by SilverWave on 2011-04-07
> **lovinglinux said:**
> Check this out:

[https://developer.mozilla.org/devnews/index.php/2011/04/07/new-development-channels-and-repositories-for-rapid-releases/](https://developer.mozilla.org/devnews/index.php/2011/04/07/new-development-channels-and-repositories-for-rapid-releases/)


Wow a true Watershed moment in Firefox development!

So lets save the whole thing for posterity:

>  			**[New development channels and repositories for rapid releases]("https://developer.mozilla.org/devnews/index.php/2011/04/07/new-development-channels-and-repositories-for-rapid-releases/")**

 	 			     		    Recently we [announced additional details]("http://mozilla.github.com/process-releases/draft/development_specifics/")  about the channels for the new Firefox development and release process.  We are confident this process will enable us to ship quality Firefox  releases to users at a faster cadence and ask for your patience as we  hammer out the final remaining items.
 **Reasoning behind the new update channel and repositories**

 Firefox currently has three update channels, all of which contain updates built out of the same code repository:
 
[LIST=1]
[*]**Nightly** – builds created out of the mozilla-central repository every night. These are not qualified by QA
[*]**Beta** – builds created out of the mozilla-central repository, qualified by QA as being of sufficient quality to release to beta users
[*]**Release** – builds created out of the mozilla-central  repository, qualified by QA as being of sufficient quality to release  to hundreds of millions of people
[/LIST]
 Because the updates we put on the Nightly channel aren’t tested  before they are offered to users, we use a different icon and name  (“Minefield”) to indicate they are risky and not the stable Firefox most  users expect:
 [[IMG]http://christian.legnitto.com/blog/wp-content/uploads/2011/04/minefield.png[/IMG]]("http://christian.legnitto.com/blog/wp-content/uploads/2011/04/minefield.png")
 While this approach has treated us well we feel there are some issues inherent in the current structure:
 
[LIST=1]
[*]The quality expectation for updates on the Beta channel is vastly higher than the updates on the Nightly channel
[*]Users on the Beta channel may not even know they are running pre-release (but hopefully decent) versions of Firefox
[*]Due to #1 above, development on the mozilla-central repository is  frozen while we stabilize for an update to the Beta channel. This causes  a huge backlog of patches and adds additional risk for the next beta
[*]3rd parties must track Firefox development closely to know when a  milestone they care about (such as feature complete, API freeze, or  string freeze) is reached
[*]For developers, the tree rules are constantly changing on mozilla-central depending on when we last shipped an update from it
[/LIST]
 Because of these issues we came up with a modified process:
 [IMG]http://mozilla.github.com/process-releases/draft/development_specifics/img/channels.png[/IMG]
 
[LIST=1]
[*]**Nightly** – builds created out of the mozilla-central repository every night. These are not qualified by QA
[*]**Aurora** – builds created out of the mozilla-aurora repository, which is synced from mozilla-central every 6 weeks[1]("https://developer.mozilla.org/devnews/index.php/2011/04/07/new-development-channels-and-repositories-for-rapid-releases/#6_weeks"). There is a small amount of QA at the start of the 6 week[1]("https://developer.mozilla.org/devnews/index.php/2011/04/07/new-development-channels-and-repositories-for-rapid-releases/#6_weeks") period before the updates are offered
[*]**Beta** – builds created out of the mozilla-beta  repository, qualified by QA as being of sufficient quality to release to  beta users
[*]**Release** – builds created out of the mozilla-release   repository, qualified by QA as being of sufficient quality to release   to hundreds of millions of people
[/LIST]
 With the new structure, all these issues go away:
 
[LIST=1]
[*][I]The quality expectation for updates on the Beta channel is vastly higher than the updates on the Nightly channel.
[/I]We address this by creating the Aurora channel. This  channel has  higher expectations of quality than the Nightly channel but  lower  expectations than Beta. At the start of the 6 week[1]("https://developer.mozilla.org/devnews/index.php/2011/04/07/new-development-channels-and-repositories-for-rapid-releases/#6_weeks")  Aurora period for a particular release, the quality will be closer to   the Nightly channel. At the end of the 6 week Aurora period quality will   have converged to match the Beta channel
[*]*Users on the Beta channel may not even know they are running pre-release (but hopefully decent) versions of Firefox*.
To fix this issue we are branding builds from individual channels with  new icons.  This should allow users to know at a glance what channel  they are on and  set stability expectations accordingly
[*][I]Due to #1 above, development on the mozilla-central repository  is frozen while we stabilize for an update to the Beta channel. This  causes a huge backlog of patches and adds additional risk for the next  beta.
[/I]Because we are using a repo-per-channel model,  mozilla-central  development (and thus the updates on the Nightly  channel) never have to  freeze…quality convergence takes place on other  repositories while  Firefox development continues on mozilla-central  unaffected by the  release process
[*]*3rd parties must track Firefox development closely to know when a  milestone they care about (such as feature complete, API freeze, or  string freeze) is reached*.
With the new process what happens where and when is a lot more explicit   and consistent. No longer will 3rd parties need to know that beta 8 was   API complete while beta 9 was string frozen. Instead we can make   assurances such as “no new en-US strings will be added through updates   on the Aurora channel” and “no extension API changes will be delivered   to users via the Beta channel”. This allows 3rd parties to accurately   plan and encourages sticking to the rules and schedule
[*][I]For developers, the tree rules are constantly changing on mozilla-central depending on when we last shipped an update from it.
[/I]Lastly, the new repositories (which map to the channels) allow   developers to do what they do best—develop. No longer should a   developer need to know we are in blocker-only mode for a particular   release. Instead, they will be  allowed to land their fixes on  mozilla-central at any time provided they  stick to the mozilla-central  tree rules. The mozilla-aurora repository  will have different rules,  and mozilla-beta will have different (and  stricter) rules still. The  rules for each of these repositories will not  change over time or from  release to release, which should help  alleviate a lot of developer  confusion and annoyance
[/LIST]
 **Repository and channel mechanics**

 The repository and channel mechanics can get very specific and  involved. Most developers won’t care about the specifics and will  instead just focus on landing their fixes on mozilla-central. If you do  care about the specifics, please take a look at the previously posted [process specifics document]("http://mozilla.github.com/process-releases/draft/development_specifics/"). The document is where we are collecting the decisions about how to best handle the nuts and bolts of releases.
 **Feedback**

 As with most Mozilla process changes, questions and comments from the  community are highly encouraged. The best place to ask questions is the  [mozilla-dev-planning newsgroup]("https://groups.google.com/group/mozilla.dev.planning/topics").  Please be sure to read the previous threads to make sure your question  hasn’t already been answered as there have already been some great  discussions taking place.
 Feedback and changes to the [process specifics document]("http://mozilla.github.com/process-releases/draft/development_specifics/") can be submitted directly as [pull requests on GitHub]("https://github.com/mozilla/process-releases"). You can also use the history view to see the iterations the process document has already gone through.
 Finally, I understand there are a lot of details in the specifics  document and sometimes it is easier to just talk to someone directly. I  am available via [EMAIL="clegnitto@mozilla.com"]email[/EMAIL] and IRC (LegNeato on irc.mozilla.org) for any community members with questions or comments.
 
1 Please see the [process specifics document]("http://mozilla.github.com/process-releases/draft/development_specifics/") for reasons why the steps for Firefox 5 are not in 6 week increments
 					 				     			    This entry was posted by Christian Legnitto on Thursday, April 7th, 2011 at 3:26 pm					and is filed under [General]("https://developer.mozilla.org/devnews/index.php/categories/1/"). 				
 			
 		


---

### Post by SilverWave on 2011-04-07
> **SilverWave said:**
> Wow a true Watershed moment in Firefox development!

[https://developer.mozilla.org/devnews/index.php/2011/04/07/new-development-channels-and-repositories-for-rapid-releases/](https://developer.mozilla.org/devnews/index.php/2011/04/07/new-development-channels-and-repositories-for-rapid-releases/)

So lets save the whole thing for posterity:


> **Aurora** &#8211; builds created out of the mozilla-aurora repository, which is synced from mozilla-central every 6 weeks[1]("https://developer.mozilla.org/devnews/index.php/2011/04/07/new-development-channels-and-repositories-for-rapid-releases/#6_weeks"). There is a small amount of QA at the start of the 6 week[1]("https://developer.mozilla.org/devnews/index.php/2011/04/07/new-development-channels-and-repositories-for-rapid-releases/#6_weeks") period before the updates are offeredThis is probably the one most ppl will find most useful, some QA so it will at least work. :-)

But the latest and greatest every 6 weeks!

Cool.

---

### Post by SilverWave on 2011-04-07
> **SilverWave said:**
> What's next?

Cant see any new builds since the 23rd of March 2011, and that failed...

[         [IMG]https://launchpad.net/@@/treeCollapsed[/IMG]         [IMG]https://launchpad.net/@@/package-source[/IMG]         firefox-trunk - 4.2~a1~hg20110407r67597+nobinonly-0ubuntu1~umd1~lucid]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+sourcepub/1635874/+listing-archive-extra")                                 [fta]("https://launchpad.net/%7Efta")                        
5 hours ago     Published     Lucid     Web            [IMG]https://launchpad.net/@@/no[/IMG]                [           amd64         ]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+buildjob/2433556")                       [           i386         ]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+buildjob/2433557")

Hmm pity it failed but nice to see we are moving on :-)

---

### Post by SilverWave on 2011-04-09
> **SilverWave said:**
> [         [IMG]https://launchpad.net/@@/treeCollapsed[/IMG]         [IMG]https://launchpad.net/@@/package-source[/IMG]         firefox-trunk - 4.2~a1~hg20110407r67597+nobinonly-0ubuntu1~umd1~lucid]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+sourcepub/1635874/+listing-archive-extra")                                 [fta]("https://launchpad.net/%7Efta")                        
5 hours ago     Published     Lucid     Web            [IMG]https://launchpad.net/@@/no[/IMG]                [           amd64         ]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+buildjob/2433556")                       [           i386         ]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+buildjob/2433557")

Hmm pity it failed but nice to see we are moving on :-)

The Lucid build failed again:

[         firefox-trunk - 4.2~a1~hg20110408r67700+nobinonly-0ubuntu1~umd1~lucid       ]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+sourcepub/1637409/+listing-archive-extra")                                  [(changes file)]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+files/firefox-trunk_4.2%7Ea1%7Ehg20110408r67700%2Bnobinonly-0ubuntu1%7Eumd1%7Elucid_source.changes")
 [fta]("https://launchpad.net/%7Efta")                        5 hours ago     Published     Lucid     Web            [IMG]https://launchpad.net/@@/no[/IMG]                [           amd64         ]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+buildjob/2436162")                       [           i386]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+buildjob/2436163")

As did Karmic and Hardy.

Maverick looks OK.

[firefox-trunk - 4.2~a1~hg20110408r67700+nobinonly-0ubuntu1~umd1~maverick       ]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+sourcepub/1637408/+listing-archive-extra")                                  [(changes file)]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+files/firefox-trunk_4.2%7Ea1%7Ehg20110408r67700%2Bnobinonly-0ubuntu1%7Eumd1%7Emaverick_source.changes")                                 
[fta]("https://launchpad.net/%7Efta")                        5 hours ago     Published     Maverick     Web            [IMG]https://launchpad.net/@@/yes[/IMG]

---

### Post by SilverWave on 2011-04-09
[Mozilla shoots for June 21 release of Firefox 5]("http://www.computerworld.com/s/article/9215660/Mozilla_shoots_for_June_21_release_of_Firefox_5?source=rss_news&utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+computerworld%2Fnews%2Ffeed+%28Latest+from+Computerworld%29")

Wow!

[Update]

This [Firefox/Features/UX Priorities]("https://wiki.mozilla.org/Firefox/Projects/UX_Priorities") is a bit of a goldmine for information on what is coming next :-)
[URL="https://wiki.mozilla.org/Firefox/Projects/UX_Priorities"]
[/URL]

---

### Post by SilverWave on 2011-04-13
[firefox-trunk - 6.0~a1~hg20110413r68036+nobinonly-0ubuntu1~umd1~lucid       ]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+sourcepub/1643001/+listing-archive-extra")                                  [(changes file)]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+files/firefox-trunk_6.0%7Ea1%7Ehg20110413r68036%2Bnobinonly-0ubuntu1%7Eumd1%7Elucid_source.changes")                                 [fta]("https://launchpad.net/%7Efta")                        27 minutes ago     Published     Lucid     Web            [IMG]https://launchpad.net/@@/no[/IMG]                [           amd64         ]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+buildjob/2444496")                       [           i386]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+buildjob/2444497")

Maverick looks OK...

Oh well with so much new happening it was possible that it could take some time to get Lucid to build...

Pity though as I would like to play as well :-)

---

### Post by lovinglinux on 2011-04-13
> **SilverWave said:**
> [firefox-trunk - 6.0~a1~hg20110413r68036+nobinonly-0ubuntu1~umd1~lucid       ]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+sourcepub/1643001/+listing-archive-extra")                                  [(changes file)]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+files/firefox-trunk_6.0%7Ea1%7Ehg20110413r68036%2Bnobinonly-0ubuntu1%7Eumd1%7Elucid_source.changes")                                 [fta]("https://launchpad.net/%7Efta")                        27 minutes ago     Published     Lucid     Web            [IMG]https://launchpad.net/@@/no[/IMG]                [           amd64         ]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+buildjob/2444496")                       [           i386]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+buildjob/2444497")

Maverick looks OK...

Oh well with so much new happening it was possible that it could take some time to get Lucid to build...

Pity though as I would like to play as well :-)

I am working like crazy to keep up :-)

Just released a new version of FoxTester with support for the new aurora and beta repositories.

---

### Post by SilverWave on 2011-04-14
> **lovinglinux said:**
> I am working like crazy to keep up :-)

Just released a new version of FoxTester with support for the new aurora and beta repositories.

Here we go first working 6.0A1 for Lucid :D

[[IMG]https://launchpad.net/@@/treeCollapsed[/IMG]         [IMG]https://launchpad.net/@@/package-source[/IMG]         firefox-trunk - 6.0~a1~hg20110413r68036+nobinonly-0ubuntu1~umd1~lucid       ]("https://launchpad.net/%7Esilverwave/+archive/one-daily-a-month-1/+sourcepub/1666101/+listing-archive-extra")

That's all for now but lots more later... once I have updated everything.

---

### Post by SilverWave on 2011-04-14
> **SilverWave said:**
> Here we go first working 6.0A1 for Lucid :D

[[IMG]https://launchpad.net/@@/treeCollapsed[/IMG]         [IMG]https://launchpad.net/@@/package-source[/IMG]         firefox-trunk - 6.0~a1~hg20110413r68036+nobinonly-0ubuntu1~umd1~lucid       ]("https://launchpad.net/%7Esilverwave/+archive/one-daily-a-month-1/+sourcepub/1666101/+listing-archive-extra")

That's all for now but lots more later... once I have updated everything.


OK that went surprisingly well :-)

Here are the gory details:

> firefox-4.0
Changes for the versions:
4.0~b13~hg20110321r63449+nobinonly-0ubuntu1~umd1~lucid
6.0~a1~hg20110413r68036+nobinonly-0ubuntu1~umd1~lucid

This change is not from a source that supports changelogs.
(This is a transitional package to ensure that upgrades work correctly. It can be safely removed).

firefox-4.0-globalmenu
Changes for the versions:
4.0~b13~hg20110321r63449+nobinonly-0ubuntu1~umd1~lucid
6.0~a1~hg20110413r68036+nobinonly-0ubuntu1~umd1~lucid

This change is not from a source that supports changelogs.
(This is a transitional package to ensure that upgrades work correctly. It can be safely removed).

firefox-trunk (New install)
Changes for the versions:
None
6.0~a1~hg20110413r68036+nobinonly-0ubuntu1~umd1~lucid

This change is not from a source that supports changelogs.
(Firefox delivers safe, easy web browsing. A familiar user interface, enhanced security features including protection from online identity theft, and integrated search let you get the most out of the web).


firefox-4.0-globalmenu (New install)
Changes for the versions:
None
6.0~a1~hg20110413r68036+nobinonly-0ubuntu1~umd1~lucid

This change is not from a source that supports changelogs.
(This package provides an extension which adds support for the Unity appmenu to Firefox).




---

### Post by SilverWave on 2011-04-14
> **SilverWave said:**
> OK that went surprisingly well :-)

Here are the gory details:

What happens is that your firefox folder is copied across to firefox-trunk and you also get a cool  new icon:

> [Home]("http://www.mozilla.org/") /  
       [IMG]http://www.mozilla.org/images/projects/nightly_logo.jpg[/IMG]   **Firefox Nightlies**

   Thank you for trying a nightly build and helping improve future  versions of Firefox.  Learn more about how you can get involved with our  testing and developer community.
     **Getting Started**

   Use these links to find and report issues.
    
[LIST]
[*][Submit crash reports]("http://support.mozilla.com/en-US/kb/Mozilla%20Crash%20Reporter")
[*][Run test cases in Litmus]("https://litmus.mozilla.org/")
[*][Report bugs in Bugzilla]("https://bugzilla.mozilla.org/enter_bug.cgi?product=Firefox")
[*][Subscribe to Nightly-Testers mailing list]("https://mail.mozilla.org/listinfo/nightly-testers")
[/LIST]
On start-up I upgraded Add-ons Compatibility reporter and after a reboot all my add-on look to be working!

Before sync'ing I changed the Sync name and reset Sync to pull in all new data from the cloud copy.

This took a while but worked fine... I did reboot it a few times to help the process along a bit.

The only pref that I noticed hasn't replicated yet is all the No-Squint stuff.

So... in shot things are going well and I am writing this from 6.0a1!!!

How cool is that!

---

### Post by SilverWave on 2011-04-14
Yep that's right none of my PPA's will carry Firefox 3.6.
Also Karmic will no longer be supported either.

Most of the old Karmic PPa's are being re-purposed for the new upcoming Natty :-)

**Personal package archives**

[One Daily A Month #0 - Not in use]("https://launchpad.net/%7Esilverwave/+archive/one-daily-a-month-0")
[Firefox-trunk - One Daily A Month #1 - Lucid]("https://launchpad.net/%7Esilverwave/+archive/one-daily-a-month-1")
[One Daily A Month #2 - Not in use]("https://launchpad.net/%7Esilverwave/+archive/one-daily-a-month-2")
[Firefox-trunk - One Daily A Month #3 - Natty]("https://launchpad.net/%7Esilverwave/+archive/one-daily-a-month-3")
[One Daily A Month #4 - Not in use]("https://launchpad.net/%7Esilverwave/+archive/one-daily-a-month-4")
[Firefox-trunk - One Daily A Month #5 - Maverick]("https://launchpad.net/%7Esilverwave/+archive/one-daily-a-month-5")
[One Daily A Week #0 - Lucid]("https://launchpad.net/%7Esilverwave/+archive/testing0")
[One Daily A Week #1 - Natty]("https://launchpad.net/%7Esilverwave/+archive/testing1")
[One Daily A Week #2 - Maverick]("https://launchpad.net/%7Esilverwave/+archive/testing2")

Any more changes will depend on there being "Aurora" packages made available.

---

### Post by SilverWave on 2011-04-14
Ignore this post LOL

Deleting the following text from the main page as it looks to be no longer relevant.
(Just making a note in case I need to add it back at a later time).

> [Firefox-Next from the Mozilla Team]("https://launchpad.net/%7Emozillateam/+archive/firefox-next")

This PPA contains Milestone builds of the next version of Firefox (alpha, beta, RC).

*High safety, easy install. Milestone** packages have undergone quality assurance.*
*Take notice of the version (alpha, beta, RC**) for a measure of stability.*

**Add The Firefox Next PPA:**
```

sudo add-apt-repository ppa:mozillateam/firefox-next
```[B]
Update & Install[/B]
     ```

sudo apt-get update
sudo apt-get install firefox-4.0
```Note that this is best option for most users as:
This PPA only contains Firefox.
You will not be swamped with updates.
Milestone builds are quite polished.

---

### Post by Jinx13 on 2011-04-15
Just want to say thanks very much for this all this information helps n00bs like me :D

---

### Post by SilverWave on 2011-04-16
> **Jinx13 said:**
> Just want to say thanks very much for this all this information helps n00bs like me :D

Thank you for saying so.

I am pleased you find it useful.

:-)

---

### Post by SilverWave on 2011-04-16
> **SilverWave said:**
> ...Most of the old Karmic PPa's are being re-purposed for the new upcoming Natty :-)


**Personal package archives**

[One Daily A Month #0 - Not in use]("https://launchpad.net/%7Esilverwave/+archive/one-daily-a-month-0")
[Firefox-trunk - One Daily A Month #1 - Lucid]("https://launchpad.net/%7Esilverwave/+archive/one-daily-a-month-1")
[One Daily A Month #2 - Not in use]("https://launchpad.net/%7Esilverwave/+archive/one-daily-a-month-2")
[Firefox-trunk - One Daily A Month #3 - Natty]("https://launchpad.net/%7Esilverwave/+archive/one-daily-a-month-3")
[One Daily A Month #4 - Not in use]("https://launchpad.net/%7Esilverwave/+archive/one-daily-a-month-4")
[Firefox-trunk - One Daily A Month #5 - Maverick]("https://launchpad.net/%7Esilverwave/+archive/one-daily-a-month-5")
[One Daily A Week #0 - Lucid]("https://launchpad.net/%7Esilverwave/+archive/testing0")
[One Daily A Week #1 - Natty]("https://launchpad.net/%7Esilverwave/+archive/testing1")
[One Daily A Week #2 - Maverick]("https://launchpad.net/%7Esilverwave/+archive/testing2")

Updated Natty PPA's with latest firefox-trunk 6.0a1

---

### Post by SilverWave on 2011-04-17
Just a note in case anyone else is having the same problems...

It looked as if FF was trying to sync but, when I checked it hadn't been successful for 4 days.

I tried various strategies but in the end went back to my ff4.0 backup from Monday last (7 days ago).

All is working again thank goodness :-)

As a precaution I have wiped the contents of my FF6.0a1 profile (just leaving the empty firefox-trunk folder) and let ff create a new one on start-up.

This seems to be working OK and I have used Sync on FF4.0 to authorise it (ff6.0a1) successfully.

Was getting a little worried there... I had went back through 4 different backups before I found one that would Sync!

Now I just need to add the extensions back in one at a time for my new ff6.0a1 - oh joy :-( LOL

---

### Post by SilverWave on 2011-04-17
> **SilverWave said:**
> ...I tried various strategies but in the end went back to my ff4.0 backup from Monday last (7 days ago).

All is working again thank goodness :-)
...

I have done a little more trouble shooting...
I originally thought it could be a new beta2 of Boox that I had just installed but I no longer think that Boox is the cause.

I think it may be related to my history settings or the size of my sync data.

I have set Firefox to use "custom settings for history" with most of the setting enabled.

I don't see a "specific number of days to remember" setting that was an option in previous ff's.

I will continue to test and report back but for now sync is working again.

---

### Post by SilverWave on 2011-04-17
> **SilverWave said:**
> I have done a little more trouble shooting...
I think it may be related to my history settings or the size of my sync data.

I have set Firefox to use "custom settings for history" with most of the setting enabled...

I have** cleared active logins** as a test on my ff6.0a1 and that seems to have done the trick.

Prior to that I was getting Sync encountered an unknown error.

---

### Post by lovinglinux on 2011-04-20
I just wanted to let you know that Mozilla is working on a new [compatibility workflow for add-ons]("http://blog.mozilla.com/addons/2011/04/19/add-on-compatibility-rapid-releases/"). Basically add-ons compatible with the latest release will be automatically marked as compatible when a new Firefox version is released, instead of requiring all add-ons authors to bump the compatibility themselves. They will implement automatic tests to prevent bumping compatibility of those add-ons flagged with incompatibilities.  This new scheme should be ready for Firefox 5 beta.

---

### Post by SilverWave on 2011-04-20
> **lovinglinux said:**
> I just wanted to let you know that Mozilla is working on a new [compatibility workflow for add-ons]("http://blog.mozilla.com/addons/2011/04/19/add-on-compatibility-rapid-releases/") ...


Well that is simply amazing :-)

---

### Post by lovinglinux on 2011-04-20
> **SilverWave said:**
> Well that is simply amazing :-)

Indeed. That will save add-ons developers a lot of time and will reduce the wait for compatibility patches considerably.

---

### Post by SilverWave on 2011-04-24
> **SilverWave said:**
> Not happy with the new manager but as I can only use Platypus with FF3.6 I was going to have to do something similar in any case.

And I was really missing my 60 scripts!



Note:
FF3.6 had updated Greasemonkey so I had to uninstall and reinstall with the Version [0.8.20100408.6]("https://addons.mozilla.org/en-US/firefox/addon/greasemonkey/versions/") from April 8 2010.

OK it seems to be a time of radical decisions so here is mine:
[B]
I have uninstalled Greasemonkey.[/B]

I am completley replacing it with [Stylish 1.1.2]("https://addons.mozilla.org/en-US/firefox/addon/stylish/") and the [DOM Inspector.]("https://addons.mozilla.org/en-US/firefox/addon/dom-inspector-6622/")

:o

---

### Post by SilverWave on 2011-04-24
> **SilverWave said:**
> OK it seems to be a time of radical decisions so here is mine:
[B]
I have uninstalled Greasemonkey.[/B]

I am completely replacing it with [Stylish 1.1.2]("https://addons.mozilla.org/en-US/firefox/addon/stylish/") and the [DOM Inspector.]("https://addons.mozilla.org/en-US/firefox/addon/dom-inspector-6622/")

:o

I originally used Greasemonkey and Platypus to allow me to clean up websites that were cluttered.

But first Platypus was abandoned and then changes were made to the way Greasemonkey scripts were managed.

So I did my first serious test of Stylish for years and found a surprisingly professional product.

** Better than Greasemonkey for my uses in the following areas:**[INDENT] 1. Speed, Stylish appears to be instantaneous, whereas Greasemonkey slowed page loads appreciably.[/INDENT][INDENT][LEFT]2. CSS not JS so no security issues.[/LEFT]

3. A huge number of great ready made styles at  [http://userstyles.org/](http://userstyles.org/) presented in a nice clean manor.
[/INDENT][INDENT]4. Fantastic extra tools to help you such as the [DOM Inspector]("https://addons.mozilla.org/en-US/firefox/addon/dom-inspector-6622/") and the [Stylish-Custom]("https://addons.mozilla.org/en-US/firefox/addon/stylish-custom/?src=collection&collection_id=aa7d5fd9-1937-8e54-58ee-dffc9bc63499") add-ons for example.
[/INDENT][INDENT]5. Great developer support for both the main add-on and the extra tools.
[/INDENT]TBH now that I look at it I cant see how it took me so long to move :-)

That said the main issue with Stylish was a lack of an easy how to... more on that next.

---

### Post by SilverWave on 2011-04-24
> **SilverWave said:**
> ... That said the main issue with Stylish was a lack of an easy how to... more on that next.

From the stylish statusbar icon:

Left Click > Write new style

Name:
> Ubuntu Forums. Big Edit.CSS:
> @namespace url([http://www.w3.org/1999/xhtml);]("http://www.w3.org/1999/xhtml%29;")

@-moz-document url-prefix([http://ubuntuforums.org/editpost.php](http://ubuntuforums.org/editpost.php)), url-prefix(http://ubuntuforums.org/newreply.php){

DIV[align="left"][style="width:640px"] {width:1000px!important}
#vB_Editor_001_iframe {  width: 1000px!important; height: 650px!important; }

}
There you go sorted :-D

__________________

On the web its a one click install here:

[http://userstyles.org/styles/47039/silverwave-ubuntuforums-big-edit](http://userstyles.org/styles/47039/silverwave-ubuntuforums-big-edit)

Or, from the stylish statusbar icon > Left Click > Find styles for this site...

__________________

Notes:

The trick to using Stylish is finding out what the elements, that you want to alter, are called.

e.g. how to find the names:

#vB_Editor_001_iframe
DIV[align="left"][style="width:640px"]

That will be the subject of the next post on the [DOM Inspector]("https://addons.mozilla.org/en-US/firefox/addon/dom-inspector-6622/") but the quick answer is right click > "Copy Selector".

---

### Post by SilverWave on 2011-04-24
Install [Stylish]("https://addons.mozilla.org/en-US/firefox/addon/stylish/")
Install the [DOM Inspector]("https://addons.mozilla.org/en-US/firefox/addon/dom-inspector-6622/")

From the stylish statusbar icon:

Left Click > Write new style > For bbc.co.uk...

Add the code below:

> @namespace url([http://www.w3.org/1999/xhtml);]("http://www.w3.org/1999/xhtml%29;") 

@-moz-document domain("bbc.co.uk") {

.layout-block-b  { display: none !important; }
.layout-block-a  { width: 100% !important; }
.story-body { width: 816px !important; }

}To find out which elements to select do the following:

Firefox > Web Developer > DOM inspector > 

Click on the Top Left Icon (Magnifying glass with white mouse cursor bottom right.)
**"Find a node to inspect by clicking on it"**

Then go back to the BBC web page and click on the sidebar that we want to remove...
(A red box will surround the object).

In the DOM inspector it is now displaying a tree view of the web page and the item "hyperpuff".

If you move a little up the tree you will see ".layout-block-b" is the one we want to hide and 
".layout-block-a" the one to maximise.

How cool is that!

Note: The element selector "name" can be a LOT more involved, especially if its in a table.
**But the solution is to  right click the element and choose "Copy Selector"** and then type of selector.

More examples of my newbie fumblings here [http://userstyles.org/users/98352](http://userstyles.org/users/98352)

                __________________

General Note:

This relates to the newest version of Firefox only in that this Stylish replacement, for an unsupported add-on (platypus + greasemonkey), finally enables me to say goodbye to Firefox 3.6 and look forward to Firefox 5 and 6, with the confidence that none of my add-ons will be holding me back.

:-)

---

### Post by SilverWave on 2011-04-24
From a blog post "[Deliberacy]("http://blog.johnath.com/2011/04/19/deliberacy/")" this is interesting:

[Features/Firefox]("https://wiki.mozilla.org/Features/Firefox")

Here is a snapshot of the Top Ten P1 items:

---

### Post by SilverWave on 2011-04-29
**Almost Tempted with 11.04 Very Impressed.**

                       [IMG]http://www.theregister.co.uk/Design/graphics/icons/comment/go_48.png[/IMG]I had promised myself that, as 10.04 is great and rock solid, I would stick with Lucid until the next LTS release...
  But having tried 11.04 in a VM I am very tempted...
Surprised that it is so usable so early in the development process TBH.

Decisions, decisions! 
;-)

hmm it doesn't look as if you can add the System Monitor or Parcellite to the top bar :-(
Oh well maybe next year.
___

Oh one point about Firefox: If you want the Firefox Button to show once you turn off the Menu Bars, go into Add-ons and disable the "Global Menu Bar Integration".

---

### Post by SilverWave on 2011-05-02
I have just clean installed Natty 11.04 and I love it :-) ([http://wp.me/pOd5E-qe](http://wp.me/pOd5E-qe)).

[IMG]http://silverwav.files.wordpress.com/2011/04/stunning-and-beautiful1.jpeg?w=700&h=210[/IMG]

Well done to everyone.

Global Menu Bar Integration is a great idea once you use it for a while ;-)

Firefox looks cool.

---

### Post by SilverWave on 2011-05-09
The latest and greatest successful build:

[IMG]https://launchpad.net/@@/package-source[/IMG]                 firefox-trunk                                               6.0~a1~hg20110508r69097+nobinonly-0ubuntu1~umd1

---

### Post by SilverWave on 2011-05-21
[Firefox 5 Compatibility Bump]("http://blog.mozilla.com/addons/2011/05/21/firefox-5-compatibility-bump/")

> Earlier tonight we updated compatibility information for add-ons that  work with Firefox 4 to also work with Firefox 5, except in certain  cases where we think the add-on may be incompatible. This coincided with  the [beta release]("http://www.mozilla.com/en-US/firefox/channel/") of Firefox 5, though normally it would occur when the Nightly channel is promoted to Aurora, as described in the [Rapid Releases Compatibility Plan]("http://blog.mozilla.com/addons/2011/04/19/add-on-compatibility-rapid-releases/").
 We were able to mark 3,890 add-ons as compatible with Firefox 5.  There were 256 that failed our automatic scanners either due to  including binary components or using navigator.language,  which was changed in Firefox 5. All affected add-on authors received an  email about the compatibility update and instructions depending on  whether they passed or failed.


Hmm interesting...

I wonder if the Ubuntu Mozilla team are going to open a Beta channel...

---

### Post by SilverWave on 2011-05-21
> **SilverWave said:**
> [Firefox 5 Compatibility Bump]("http://blog.mozilla.com/addons/2011/05/21/firefox-5-compatibility-bump/")

Hmm interesting...

I wonder if the Ubuntu Mozilla team are going to open a Beta channel...

Looks as if they will, in time, support the Beta Channel but not the Aurora Channel.

[firefox aurora channel]("https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/779646")
> 
[Chris Coulson]("https://launchpad.net/%7Echrisccoulson")             wrote             on 2011-05-10:                                                             [ #2]("https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/779646/comments/2")                                                        Sorry, I spend enough of my time  maintaining the daily builds from mozilla-central, and we will support  the beta channel too. There's no compelling reason to provide aurora PPA  builds at the moment, as hardly anything has changed in Firefox 5.

        


---

### Post by lovinglinux on 2011-05-21
> **SilverWave said:**
> [Firefox 5 Compatibility Bump]("http://blog.mozilla.com/addons/2011/05/21/firefox-5-compatibility-bump/")

Hmm interesting...

Indeed. I received the update bump information yesterday. Mozilla has done a great job. The automated validation informed me that most of my extensions were compatible, but warned me about FoxTester using navigator.language and provided the correct method, so I could update the extension. Done.

BTW, Fast Dial is completely broken in FF 5 Beta.

---

### Post by SilverWave on 2011-05-21
[IMG]https://launchpad.net/@@/package-source[/IMG]                 firefox-trunk                                               6.0~a1~hg20110520r69818+nobinonly-0ubuntu1~umd1~natty

---

### Post by SilverWave on 2011-05-21
**PPA description**

   > The latest firefox without the update hassle.
 One Nightly a week from ubuntu-mozilla-daily.
______________________________
 One Nightly A Week #3 - Oneiric
One update a week.
firefox-trunk only
______________________________
 sudo add-apt-repository ppa:silverwave/testing3
sudo apt-get update
sudo apt-get install firefox-trunk
______________________________
 Disclaimer: Use at your own risk, no guarantees.

---

### Post by SilverWave on 2011-05-24
[B]Firefox Beta - Natty
[/B]
[https://launchpad.net/~silverwave/+archive/testing4]("https://launchpad.net/%7Esilverwave/+archive/testing4")

The latest firefox Beta.
From mozillateam/firefox-next.
______________________________
 Firefox Beta - Natty #testing4
firefox only
______________________________
 sudo add-apt-repository ppa:silverwave/testing4
sudo apt-get update
sudo apt-get install firefox
______________________________
 

**Firefox Beta - Maverick**

[https://launchpad.net/~silverwave/+archive/testing5]("https://launchpad.net/%7Esilverwave/+archive/testing5")
The latest firefox Beta.
 From mozillateam/firefox-next.
______________________________
 Firefox Beta - Maverick #testing5
firefox only
______________________________
 sudo add-apt-repository ppa:silverwave/testing5
sudo apt-get update
sudo apt-get install firefox
______________________________


**Firefox Beta - Lucid**

[https://launchpad.net/~silverwave/+archive/testing6]("https://launchpad.net/%7Esilverwave/+archive/testing6")

The latest firefox Beta.
 From mozillateam/firefox-next.
______________________________
 Firefox Beta - Lucid #testing6
firefox only
______________________________
 sudo add-apt-repository ppa:silverwave/testing6
sudo apt-get update
sudo apt-get install firefox
______________________________


Beta &#8211; builds created out of the mozilla-beta repository.
Qualified by QA as being of sufficient quality to release to beta users

Note1: I haven't tested these yet but the should be OK as they are beta's :-)
Note2: We are up to [firefox - 5.0~b2+build1+nobinonly-0ubuntu0       ]("https://launchpad.net/%7Emozillateam/+archive/firefox-next/+sourcepub/1742194/+listing-archive-extra")

---

### Post by chrisccoulson on 2011-05-24
> **SilverWave said:**
> [B]Firefox Beta - Natty
[/B]
[https://launchpad.net/~silverwave/+archive/testing4]("https://launchpad.net/%7Esilverwave/+archive/testing4")

The latest firefox Beta without the update hassle.
 From mozillateam/firefox-next.
______________________________
 Firefox Beta - Natty #testing4
firefox only
______________________________
 sudo add-apt-repository ppa:silverwave/testing4
sudo apt-get update
sudo apt-get install firefox
______________________________
 

**Firefox Beta - Maverick**

[https://launchpad.net/~silverwave/+archive/testing5]("https://launchpad.net/%7Esilverwave/+archive/testing5")
The latest firefox Beta without the update hassle.
 From mozillateam/firefox-next.
______________________________
 Firefox Beta - Maverick #testing5
firefox only
______________________________
 sudo add-apt-repository ppa:silverwave/testing5
sudo apt-get update
sudo apt-get install firefox
______________________________


**Firefox Beta - Lucid**

[https://launchpad.net/~silverwave/+archive/testing6]("https://launchpad.net/%7Esilverwave/+archive/testing6")

The latest firefox Beta without the update hassle.
 From mozillateam/firefox-next.
______________________________
 Firefox Beta - Lucid #testing6
firefox only
______________________________
 sudo add-apt-repository ppa:silverwave/testing6
sudo apt-get update
sudo apt-get install firefox
______________________________


Beta – builds created out of the mozilla-beta repository.
Qualified by QA as being of sufficient quality to release to beta users

Note1: I haven't tested these yet but the should be OK as they are beta's :-)
Note2: We are up to [firefox - 5.0~b2+build1+nobinonly-0ubuntu0       ]("https://launchpad.net/%7Emozillateam/+archive/firefox-next/+sourcepub/1742194/+listing-archive-extra")

You say "The latest firefox Beta without the update hassle", but what hassle is that with the beta PPA?

---

### Post by SilverWave on 2011-05-24
> **chrisccoulson said:**
> You say "The latest firefox Beta without the update hassle", but what hassle is that with the beta PPA?

Not much its just about perfect...

Except Firefox is not the only package in the PPA.

It was also pretty much boiler plate text, so I have removed it now it has been pointed out :-)

---

### Post by chrisccoulson on 2011-05-24
> **SilverWave said:**
> Not much its just about perfect...

Except Firefox is not the only package in the PPA.



The reason for that is because users who had those packages installed before installing the beta will want the updates from the PPA so that they carry on working.

---

### Post by SilverWave on 2011-05-24
[https://launchpad.net/~mozillateam/+archive/firefox-next/+sourcepub/1742194/+listing-archive-extra](https://launchpad.net/~mozillateam/+archive/firefox-next/+sourcepub/1742194/+listing-archive-extra)

>   * Rebase packaging on Natty, some notable changes:   * Drop abrowser. The abrowser branding doesn't work since Firefox 4, and     is going to be difficult to maintain going forwards. The Firefox logo     is freely licensed now, which was the main reason for the existance of     abrowser. Current abrowser users will be migrated to Firefox

-- Chris Coulson 



>The Firefox logo is freely licensed now

Well that's good news :-)

---

### Post by SilverWave on 2011-05-24
> **SilverWave said:**
> [B]Firefox Beta - Natty
[/B]
[https://launchpad.net/~silverwave/+archive/testing4]("https://launchpad.net/%7Esilverwave/+archive/testing4")

The latest firefox Beta.
From mozillateam/firefox-next.
______________________________
 Firefox Beta - Natty #testing4
firefox only
______________________________
 sudo add-apt-repository ppa:silverwave/testing4
sudo apt-get update
sudo apt-get install firefox
______________________________
 

Beta &#8211; builds created out of the mozilla-beta repository.
Qualified by QA as being of sufficient quality to release to beta users

Note1: I haven't tested these yet but the should be OK as they are beta's :-)
Note2: We are up to [firefox - 5.0~b2+build1+nobinonly-0ubuntu0       ]("https://launchpad.net/%7Emozillateam/+archive/firefox-next/+sourcepub/1742194/+listing-archive-extra")


Updated Firefox to 5b2 on Natty 64bit and I have some issues:

1. Zoom not working [Fixed             #[**413**]("http://ubuntuforums.org/showpost.php?p=10861721&postcount=413")]
2. The "About Help" gives an error (see screenshot)             [Fixed#[**412**]("http://ubuntuforums.org/showpost.php?p=10861425&postcount=412")]

Note that this is **not** a clean profile and I have a lot of add-ons.

Mozilla/5.0 (X11; Linux x86_64; rv:5.0) Gecko/20100101 Firefox/5.0 ID:20110523215551

[Update]
>1. Zoom not working
This was down to NoSquint - disable, reboot and Zoom works OK.

---

### Post by chrisccoulson on 2011-05-25
> **SilverWave said:**
> Updated Firefox to 5b2 on Natty 64bit and I have some issues:

1. Zoom not working
2. The "About Help" gives an error (see screenshoot)

Note that this is **not** a clean profile and I have a lot of add-ons.

Mozilla/5.0 (X11; Linux x86_64; rv:5.0) Gecko/20100101 Firefox/5.0 ID:20110523215551

[Update]
>1. Zoom not working
This was down to NoSquint - disable, reboot and Zoom works OK.

I'm guessing you have the addon compatibility reporter installed? If so, then the incompatible Firefox 4 translation packs will still be enabled, causing the error you see in Help -> About

---

### Post by SilverWave on 2011-05-25
> **chrisccoulson said:**
> I'm guessing you have the addon compatibility reporter installed? If so, then the incompatible Firefox 4 translation packs will still be enabled, causing the error you see in Help -> About

Yes thanks for the advice, it did the trick :-)

hmm now, how to uninstall them... /goes looking

---

### Post by SilverWave on 2011-05-25
[https://launchpad.net/~mozillateam/+archive/firefox-next/+sourcepub/1742194/+listing-archive-extra]("https://launchpad.net/%7Emozillateam/+archive/firefox-next/+sourcepub/1742194/+listing-archive-extra")

> 

* Build language packs directly from the firefox source
    + Fixes LP:[#294187]("https://launchpad.net/bugs/294187") - Firefox Locales should install locale specific
      search plugins
    + Rip out the bits to create a en-US.xpi
      - update debian/rules
      - remove debian/translation-support/install.rdf.in
    + Include compare-locales FIREFOX_5_0b1_BUILD1 from
      [http://hg.mozilla.org/build/compare-locales](http://hg.mozilla.org/build/compare-locales). It's needed for merging
      en-US strings with incomplete locales
    + Pull l10n data in to tarball from bzr
      - update debian/mozclient/firefox.conf
    + Configure build for creating language packs by configuring with
      "--with-l10n-base="
      - update debian/mozconfig.in
    + Store the list of locales to ship, and provide a way of automatically
      generating that list and the control file entries from the upstream
      source. Also provide a way to blacklist languages. We map languages
      to package names using langpack-o-matic (and also get descriptions
      from there too)
      - update debian/rules
      - add debian/locales.shipped
      - add debian/control.langpacks
      - update debian/control.in
      - add debian/locale.blacklist
      - add debian/refresh-supported-locales.pl
    + Add common-build-indep hook to build the translation xpi's
      - update debian/rules
    + Add common-binary-post-install-indep to install the xpi's and
      searchplugins in to the correct debian packages
      - update debian/rules
      - add debian/get-xpi-id.py



---

### Post by SilverWave on 2011-05-25
> **chrisccoulson said:**
> I'm guessing you have the addon  compatibility reporter installed? If so, then the incompatible Firefox 4  translation packs will still be enabled, causing the error you see in  Help -> About


> **SilverWave said:**
> Yes thanks for the advice, it did the trick :-)

hmm now, how to uninstall them... /goes looking


Looks as if this is what I was looking for:

/usr/lib/firefox-addons/extensions

I just deleted the .xpi files that were language related.

---

### Post by SilverWave on 2011-05-25
> **SilverWave said:**
> Updated Firefox to 5b2 on Natty 64bit and I have some issues:

[Update]
>1. Zoom not working
This was down to NoSquint - disable, reboot and Zoom works OK.

Latest Version 2.1.1 Works fine with FF5B2

[NoSquint Version History]("https://addons.mozilla.org/en-US/firefox/addon/nosquint/versions/")

---

### Post by SilverWave on 2011-05-25
extensions.checkCompatibility.nightly

> We’ve now changed this and any nightly, try, or self-made builds  (anything not on the aurora, beta or release channels) will instead use  the single preference extensions.checkCompatibility.nightly from now on,  regardless of version. This will be available from tonight’s nightly  onwards.

[http://www.oxymoronical.com/blog/2011/05/How-to-disable-extension-compatibility-checking-on-Nightly-builds-of-Firefox](http://www.oxymoronical.com/blog/2011/05/How-to-disable-extension-compatibility-checking-on-Nightly-builds-of-Firefox)

---

### Post by SilverWave on 2011-05-30
And the fast release policy really starts to kick in...

> Changes for the versions:
6.0~a1~hg20110520r69818+nobinonly-0ubuntu1~umd1
7.0~a1~hg20110529r70295+nobinonly-0ubuntu1~umd1

This change is not from a source that supports changelogs.

Details here:

[https://launchpad.net/~silverwave](https://launchpad.net/~silverwave)

---

### Post by SilverWave on 2011-05-30
> **SilverWave said:**
> extensions.checkCompatibility.nightly



[http://www.oxymoronical.com/blog/2011/05/How-to-disable-extension-compatibility-checking-on-Nightly-builds-of-Firefox](http://www.oxymoronical.com/blog/2011/05/How-to-disable-extension-compatibility-checking-on-Nightly-builds-of-Firefox)

I didn't bother with this on the 6.0 to 7.0 bump...

Instead I accepted the add-on upgrade for Add-on Compatibility Reporter and once loaded rebooted.

All OK so far ;-)

---

### Post by SilverWave on 2011-05-30
> **SilverWave said:**
> Looks as if they will, in time, support the Beta Channel but not the Aurora Channel.

[firefox aurora channel]("https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/779646")

**[Packages in “Firefox Aurora”](https://launchpad.net/~ubuntu-mozilla-daily/+archive/firefox-aurora/+packages)**

Well now it gets interesting :-)

Looks as if we are now first class Firefox citizens :-) and have access to all the Firefox channels.

---

### Post by SilverWave on 2011-05-30
> **SilverWave said:**
> **[Packages in &#8220;Firefox Aurora&#8221;]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/firefox-aurora/+packages")**

Well now it gets interesting :-)

Looks as if we are now first class Firefox citizens :-) and have access to all the Firefox channels.

Hmm...

Something to be aware of is that the Aurora packages will replace your existing **firefox**...

I think I prefer to use the Nightly packages as being **firefox-trunk** you get to keep **firefox** as well.

Best of both worlds... :-D

I actually use the Beta packages of **firefox** (atm 5.0b2) in place of the stable 4.0 for my main browser day-to-day.

I use Nightly packages of **firefox-trunk** to keep in touch with the latest developments.

YMMV

---

### Post by lovinglinux on 2011-06-01
The latest Aurora (6.0a2) has an interesting new feature, the Permissions Manager:

[[IMG]http://www5.picturepush.com/photo/a/5774293/640/5774293.png[/IMG]](http://picturepush.com/public/5774293)

To access it, just type **about[noparse]:[/noparse]permissions** in the address bar.

I hope this will evolve into a full-feature site preferences tool like Opera has.

---

### Post by SilverWave on 2011-06-02
> **lovinglinux said:**
> The latest Aurora (6.0a2) has an interesting new feature, the Permissions Manager:

[[IMG]http://www5.picturepush.com/photo/a/5774293/640/5774293.png[/IMG]]("http://picturepush.com/public/5774293")

To access it, just type **about[noparse]:[/noparse]permissions** in the address bar.

I hope this will evolve into a full-feature site preferences tool like Opera has.

Hey this is a good idea! Thanks for the tip.

---

### Post by SilverWave on 2011-06-03
Changes for the versions:
5.0~b2+build1+nobinonly-0ubuntu0.11.04.1~mfn2
5.0~b3+build1+nobinonly-0ubuntu0.11.04.1~mfn1

Details: [[IMG]https://launchpad.net/@@/treeCollapsed[/IMG]         [IMG]https://launchpad.net/@@/package-source[/IMG]         firefox - 5.0~b3+build1+nobinonly-0ubuntu0.11.04.1~mfn1       ]("https://launchpad.net/%7Esilverwave/+archive/testing4/+sourcepub/1756755/+listing-archive-extra") __



> **SilverWave said:**
> [B]Firefox Beta - Natty
[/B]
[https://launchpad.net/~silverwave/+archive/testing4]("https://launchpad.net/%7Esilverwave/+archive/testing4")

The latest firefox Beta.
From mozillateam/firefox-next.
______________________________
 Firefox Beta - Natty #testing4
firefox only
______________________________
 sudo add-apt-repository ppa:silverwave/testing4
sudo apt-get update
sudo apt-get install firefox
______________________________
 

**Firefox Beta - Maverick**

[https://launchpad.net/~silverwave/+archive/testing5]("https://launchpad.net/%7Esilverwave/+archive/testing5")
The latest firefox Beta.
 From mozillateam/firefox-next.
______________________________
 Firefox Beta - Maverick #testing5
firefox only
______________________________
 sudo add-apt-repository ppa:silverwave/testing5
sudo apt-get update
sudo apt-get install firefox
______________________________


**Firefox Beta - Lucid**

[https://launchpad.net/~silverwave/+archive/testing6]("https://launchpad.net/%7Esilverwave/+archive/testing6")

The latest firefox Beta.
 From mozillateam/firefox-next.
______________________________
 Firefox Beta - Lucid #testing6
firefox only
______________________________
 sudo add-apt-repository ppa:silverwave/testing6
sudo apt-get update
sudo apt-get install firefox
______________________________


---

### Post by SilverWave on 2011-06-14
Changes for the versions:
4.0.1+build1+nobinonly-0ubuntu0.11.04.3
5.0~b6+build1+nobinonly-0ubuntu0.11.04.1~mfn1

Details: [[IMG]https://launchpad.net/@@/treeCollapsed[/IMG]         [IMG]https://launchpad.net/@@/package-source[/IMG]         firefox - 5.0~b6+build1+nobinonly-0ubuntu0.11.04.1~mfn1 ]("https://launchpad.net/%7Emozillateam/+archive/firefox-next/+sourcepub/1773382/+listing-archive-extra")

---

### Post by SilverWave on 2011-06-14
The Latest:

[        [IMG]https://launchpad.net/@@/package-source[/IMG]         firefox-trunk - 7.0~a1~hg20110613r71005+nobinonly-0ubuntu1~umd2~natty       ]("https://launchpad.net/%7Esilverwave/+archive/testing1/+sourcepub/1774694/+listing-archive-extra")

---

### Post by SilverWave on 2011-06-17
Interesting...

> [Mozilla to add built-in PDF viewer to Firefox Claims HTML5-JavaScript viewer safer than Chrome's PDF plug-in](http://www.computerworld.com/s/article/9217733/Mozilla_to_add_built_in_PDF_viewer_to_Firefox?source=rss_latest_content&utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+computerworld%2Fnews%2Ffeed+%28Latest+from+Computerworld%29)

---

### Post by SilverWave on 2011-06-17
Here is the latest:

Details: [[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox - 5.0~b7+build1+nobinonly-0ubuntu0.11.04.1~mfn1       ]("https://launchpad.net/%7Esilverwave/+archive/testing4/+sourcepub/1778902/+listing-archive-extra")[]("https://launchpad.net/%7Emozillateam/+archive/firefox-next/+sourcepub/1773382/+listing-archive-extra")[/QUOTE]

---

### Post by lovinglinux on 2011-06-17
> **SilverWave said:**
> Interesting...

Indeed. Very interesting.

---

### Post by SilverWave on 2011-06-18
With the new Firefox Beta PPA's now available there is less of a need for the Monthly PPA's.
So the main page will link here allowing me to streamline the First Post instructions.
______________________________

**[One Nightly A Month #4 - Oneiric]("https://launchpad.net/%7Esilverwave/+archive/one-daily-a-month-4")**
One update a month.
Firefox only.
______________________________
 sudo add-apt-repository ppa:silverwave/one-daily-a-month-4
sudo apt-get update
sudo apt-get install firefox-trunk
______________________________

**[One Nightly A Month #3 - Natty]("https://launchpad.net/%7Esilverwave/+archive/one-daily-a-month-3")**
One update a month.
Firefox only.
______________________________
 sudo add-apt-repository ppa:silverwave/one-daily-a-month-3
sudo apt-get update
sudo apt-get install firefox-trunk
______________________________

**[One Nightly A Month #5 - Maverick]("https://launchpad.net/%7Esilverwave/+archive/one-daily-a-month-5")**
One update a month.
Firefox only.
______________________________
 sudo add-apt-repository ppa:silverwave/one-daily-a-month-5
sudo apt-get update
sudo apt-get install firefox-trunk
______________________________

 **[One Nightly A Month #1 - Lucid]("https://launchpad.net/%7Esilverwave/+archive/one-daily-a-month-1")**
 One update a month.
Firefox only.
______________________________
 sudo add-apt-repository  ppa:silverwave/one-daily-a-month-1
sudo apt-get update
sudo apt-get install firefox-trunk
______________________________

 

[URL="https://launchpad.net/%7Esilverwave/+archive/one-daily-a-month-5"]
[/URL]

---

### Post by SilverWave on 2011-06-18
[Firefox Beta]("https://launchpad.net/%7Emozillateam/+archive/firefox-next")
[Firefox Aurora]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/firefox-aurora")
[Firefox Nightly]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa?field.series_filter=")

As the Nightly packages are not called firefox, rather firefox-trunk, they can be run side-by-side with firefox.

 ** I think this this is highly desirable and very useful.**

The Firefox Beta Channel is working great but it does replace your existing firefox :-(

The same is true for Firefox Aurora Channel :-(

It seems a real shame tbh.

I wonder if the naming of the packages in the other channels could be changed to follow that of the Nightly Channel?

e.g.

**Firefox Beta Channel:**
firefox-beta

**Firefox Aurora Channel:**
firefox-aurora

hmmm...

---

### Post by lovinglinux on 2011-06-18
> **SilverWave said:**
> [Firefox Beta]("https://launchpad.net/%7Emozillateam/+archive/firefox-next")
[Firefox Aurora]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/firefox-aurora")
[Firefox Nightly]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa?field.series_filter=")

As the Nightly packages are not called firefox, rather firefox-trunk, they can be run side-by-side with firefox.

 ** I think this this is highly desirable and very useful.**

The Firefox Beta Channel is working great but it does replace your existing firefox :-(

The same is true for Firefox Aurora Channel :-(

It seems a real shame tbh.

I wonder if the naming of the packages in the other channels could be changed to follow that of the Nightly Channel?

e.g.

**Firefox Beta Channel:**
firefox-beta

**Firefox Aurora Channel:**
firefox-aurora

hmmm...

I disagree. I think it is great that *firefox-next* replaces your existing firefox. This way, there is no more confusion with cloned profiles and customized launchers. It is easier for new users to adopt it.

---

### Post by chrisccoulson on 2011-06-18
Indeed, lovinglinux is right.

Firstly, the beta packages are where we test packages that are eventually going to end up in the distro. Making them parallel installable introduces several problems:
[LIST=1]
[*]The packaging is totally different, so they are completely useless for testing future distro upgrades. The beta packages should be production quality packages
[*]They rely on ugly hacks to make them fully parallel installable (ie, changing the profile location)
[*]We can't distribute them with the official branding turned on (because of reason 2
[/LIST]

The aurora package isn't parallel installable because it makes it impossible for people to swap between channels, for the reason that lovinglinux mentioned. In addition to this, I wanted to hook the channel switcher UI in to the package manager at some point (that was, until Mozilla disabled the UI). Also, having them all parallel installable means maintaining 4 lots of packaging, which is a total headache.

There is a genuine use-case for people wanting to test nightly builds alongside a more stable version (which is what I do), and this is why the nightly build is parallel installable.

We're not going to change the aurora or beta package to be parallel installable.

Also, your beta packages are out-of-date already. The latest beta fixes a critical security issue, so distributing out-of-date packages (with my name on too!) is quite irresponsible. Please fix that. People should be running the latest beta anyway, there is no point in people testing out-of-date builds.

---

### Post by SilverWave on 2011-06-18
> **chrisccoulson said:**
> Indeed, lovinglinux is right.

Firstly, the beta packages are where we test packages that are eventually going to end up in the distro. Making them parallel installable introduces several problems:
[LIST=1]
[*]The packaging is totally different, so they are completely useless for testing future distro upgrades. The beta packages should be production quality packages
[*]They rely on ugly hacks to make them fully parallel installable (ie, changing the profile location)
[*]We can't distribute them with the official branding turned on (because of reason 2
[/LIST]

The aurora package isn't parallel installable because it makes it impossible for people to swap between channels, for the reason that lovinglinux mentioned. In addition to this, I wanted to hook the channel switcher UI in to the package manager at some point (that was, until Mozilla disabled the UI). Also, having them all parallel installable means maintaining 4 lots of packaging, which is a total headache.

There is a genuine use-case for people wanting to test nightly builds alongside a more stable version (which is what I do), and this is why the nightly build is parallel installable.

We're not going to change the aurora or beta package to be parallel installable.

Also, your beta packages are out-of-date already. The latest beta fixes a critical security issue, so distributing out-of-date packages (with my name on too!) is quite irresponsible. Please fix that. People should be running the latest beta anyway, there is no point in people testing out-of-date builds.

>Also, your beta packages are out-of-date already. 

What are you referring to I don't see a Beta 8 in the Beta Channel?

---

### Post by chrisccoulson on 2011-06-18
Oh, you're right, sorry. I only saw when you copied beta 6 in my inbox, I didn't get another notification after that

---

### Post by SilverWave on 2011-06-18
> **chrisccoulson said:**
> Indeed, lovinglinux is right.

Firstly, the beta packages are where we test packages that are eventually going to end up in the distro. Making them parallel installable introduces several problems:
[LIST=1]
[*]The packaging is totally different, so they are completely useless for testing future distro upgrades. The beta packages should be production quality packages
[*]They rely on ugly hacks to make them fully parallel installable (ie, changing the profile location)
[/LIST]
Fair enough.

> 3. We can't distribute them with the official branding turned on (because of reason 2Hmm I get the Official "Nightly" branding with firefox-trunk are the terms different for Aurora and Beta?

> The aurora package isn't parallel installable because it makes it impossible for people to swap between channels, for the reason that lovinglinux mentioned. In addition to this, I wanted to hook the channel switcher UI in to the package manager at some point (that was, until Mozilla disabled the UI). Also, having them all parallel installable means maintaining 4 lots of packaging, which is a total headache.Yes I can see that, pity as I think a lot of ppl would like to use Aurora in place of Nightly.

> There is a genuine use-case for people wanting to test nightly builds alongside a more stable version (which is what I do), and this is why the nightly build is parallel installable.Agreed.

>  We're not going to change the aurora or beta package to be parallel installable.Hmm I'll take that as a tentative "No" then. :-)

---

### Post by SilverWave on 2011-06-18
> **lovinglinux said:**
> I disagree. I think it is great that *firefox-next* replaces your existing firefox. This way, there is no more confusion with cloned profiles and customized launchers. It is easier for new users to adopt it.

Hmm I can see that from a support point of view that this is better. :-)

Although I think side-by-side installs for aurora would encourage a lot more users to become Aurora Channel testers.

Which would be a "Good Thing".

---

### Post by chrisccoulson on 2011-06-18
> **SilverWave said:**
> Fair enough.

Hmm I get the Official "Nightly" branding with firefox-trunk are the terms different for Aurora and Beta?



The official branding is the Firefox name and logo

---

### Post by lovinglinux on 2011-06-18
> **SilverWave said:**
> Hmm I can see that from a support point of view that this is better. :-)

Although I think side-by-side installs for aurora would encourage a lot more users to become Aurora Channel testers.

Which would be a "Good Thing".

I haven't thought about that. My main concern is the support, after all I need to regularly test more versions than those provided by aurora and nightly. So I don't use the repositories for testing anyway.

---

### Post by SilverWave on 2011-06-22
5.0+build1+nobinonly-0ubuntu0.11.04.1
[B]
Changes for the versions:[/B]
```
Changes for the versions:
5.0~b7+build1+nobinonly-0ubuntu0.11.04.1~mfn1
5.0+build1+nobinonly-0ubuntu0.11.04.1

Version 5.0+build1+nobinonly-0ubuntu0.11.04.1: 

  * New upstream release from the stable channel (FIREFOX_5_0_BUILD1)
    - see LP: #798484 for USN information

  * Update globalmenu-extension to 1.0.6
  * Switch to mozilla-beta
    - update debian/mozclient/firefox.conf
  * Drop the ability to build with an external xulrunner, and all the packaging
    complexity which went with it
    - update debian/apport/firefox.in
    - update debian/firefox.install.in
    - update debian/firefox.lintian-overrides.in
    - update debian/firefox.sh.in
    - update debian/mozconfig.in
    - update debian/rules
  * Build language packs directly from the firefox source
    + Fixes LP: #294187 - Firefox Locales should install locale specific
      search plugins 
    + Rip out the bits to create a en-US.xpi
      - update debian/rules
      - remove debian/translation-support/install.rdf.in
    + Include compare-locales FIREFOX_5_0b1_BUILD1 from
      [http://hg.mozilla.org/build/compare-locales](http://hg.mozilla.org/build/compare-locales). It's needed for merging
      en-US strings with incomplete locales
    + Pull l10n data in to tarball from bzr
      - update debian/mozclient/firefox.conf
    + Configure build for creating language packs by configuring with
      "--with-l10n-base="
      - update debian/mozconfig.in
    + Store the list of locales to ship, and provide a way of automatically
      generating that list and the control file entries from the upstream
      source. Also provide a way to blacklist languages. We map languages
      to package names using langpack-o-matic (and also get descriptions
      from there too)
      - update debian/rules
      - add debian/locales-supported
      - add debian/control.langpacks
      - update debian/control
      - add debian/locale-blacklist
      - add debian/refresh-supported-locales.pl
    + Add common-build-indep hook to build the translation xpi's
      - update debian/rules
    + Add common-binary-post-install-indep to install the xpi's and
      searchplugins in to the correct debian packages
      - update debian/rules
      - add debian/get-xpi-id.py
    + When rebuilding debian/control in the clean target, fail the build
      if the control file was out-of-date. This ensures that we don't
      accidentally drop language packs, and forces me to maintain an
      up-to-date control file in bzr
      - update debian/rules
    + Apply vendor patches to localized searchplugins too
      - update debian/patches/ubuntu-codes-amazon.patch
      - add debian/patches/ubuntu-codes-baidu.patch
      - update debian/patches/ubuntu-codes-google.patch
  * Ditch all the version-number based branding selection. Do this all
    purely on the channel name now
    - remove debian/firefox-beta.desktop.in
    - remove debian/firefox-nightly.desktop.in
    - remove debian/firefox-unofficial.desktop.in
    - rename debian/firefox-final.desktop.in => debian/firefox.desktop.in
    - update debian/firefox.desktop.in
    - update debian/rules
    - update debian/firefox.sh.in
  * Drop the DEB_ENABLE_IPC option, now that IPC is mandatory
    - update debian/rules
    - update debian/apport/firefox.in
    - update debian/firefox.install.in
    - update debian/mozconfig.in
  * Add some missing options to the manpage
    - update debian/firefox.1.in
  * Ensure we set LD_LIBRARY_PATH before running "firefox -h"
    - update debian/firefox.sh.in
  * Drop patches merged upstream:
    - 64-bit-be-fix.patch
  * Refresh patches:
    - mozilla-kde.patch
  * Ship channel-prefs.js. We used to ship this in Firefox 3.6, and it's
    required by Test Pilot now
    - update debian/firefox.install.in
  * Backport patch from mozilla-central to fix powerpc build failure
    - add debian/patches/powerpc-build-fix.patch
    - update debian/patches/series
  * Support storing language descriptions in locales.unavailable. This
    will be useful for translations which disappear temporarily
    - update debian/rules
    - update debian/refresh-supported-locales.pl
  * Add languages that are currently dropped in FF5 (compared with FF4) to
    locales.unavailable. Having transitional packages now will make
    transitioning easier later on if they come back
    - update debian/locales.unavailable
  * Refresh debian/control to pick up transitional packages
  * Don't bundle our vendor preferences in the omni.jar. This needs a distro
    patch and it turns out that Firefox does still read prefs from
    $LIBDIR/defaults/pref, so just install it there instead
    - update debian/rules
    - update debian/firefox.install.in
    - remove debian/patches/install-vendor-prefs.patch
    - update debian/patches/series
  * Add a global pref file again (/etc/firefox/syspref.js) and add the
    necessary preinst/postinst magic to move the old file there if it
    was previously customized
    - add debian/syspref.js
    - update debian/firefox.install.in
    - update debian/firefox.links.in
    - update debian/firefox.postinst.in
    - update debian/firefox.preinst.in
  * Ensure "Depends: ${misc:Depends}" is added to all transitional
    language packs
    - update debian/control.langpacks.unavail
    - refresh debian/control
  * Ship testpilot on aurora too
    - update debian/firefox.install.in
  * Set the right Vcs-Bzr URL
    - update debian/control.in
    - refresh debian/control
  * Update list of language packs to include new ones added upstream
    - refresh debian/locales.shipped and debian/locals.unavailable
    - refresh debian/control

```**apt-cache policy firefox**```
sil@irop:~$ apt-cache policy firefox
firefox:
  Installed: 5.0+build1+nobinonly-0ubuntu0.11.04.1
  Candidate: 5.0+build1+nobinonly-0ubuntu0.11.04.1
  Version table:
 *** 5.0+build1+nobinonly-0ubuntu0.11.04.1 0
        500 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main amd64 Packages
        500 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) natty-security/main amd64 Packages
        100 /var/lib/dpkg/status
     5.0~b7+build1+nobinonly-0ubuntu0.11.04.1~mfn1 0
        500 [http://ppa.launchpad.net/silverwave/testing4/ubuntu/](http://ppa.launchpad.net/silverwave/testing4/ubuntu/) natty/main amd64 Packages
     4.0+nobinonly-0ubuntu3 0
        500 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty/main amd64 Packages
sil@irop:~$ 
```

---

### Post by SilverWave on 2011-06-22
Interesting :-)

[Firefox 5 Benchmarked – Faster And Better Than Ever Before!]("http://digitizor.com/2011/06/21/firefox-5-benchmark/")

- Uses Less Memory Than Chrome

[IMG]http://files.digitizor.com/wp-content/uploads/2011/06/ff5-memory.png[/IMG]

---

### Post by SilverWave on 2011-06-22
Changes for the versions:
7.0~a1~hg20110619r71298+nobinonly-0ubuntu1~umd1~natty

---

### Post by SilverWave on 2011-06-22
Hmm interesting...

[Asa to write a channels blog post about running different channels side-by-side]("http://blog.mozilla.com/channels/2011/06/22/aurora-channeltriage-meeting-%e2%80%93-june-21st-2011/")

... one to watch out for.

---

### Post by SilverWave on 2011-06-22
oh oh...

> Christian wanted to talk about why [Aurora seems to have a higher crash rate than both Nightly and Beta]("https://crash-stats.mozilla.com/products/Firefox"). We discussed at the last meeting and expected it to come down but it has not

---

### Post by SilverWave on 2011-06-22
[Mozilla retires Firefox 4 from security support](http://www.computerworld.com/s/article/9217837/Mozilla_retires_Firefox_4_from_security_support)
> 
Christian Legnitto, the Firefox release manager, put it most succinctly  in a May 25 message. "Firefox 5 will be the security update for Firefox  4," Legnitto said.

Wow.

---

### Post by lovinglinux on 2011-06-22
> **SilverWave said:**
> [Mozilla retires Firefox 4 from security support](http://www.computerworld.com/s/article/9217837/Mozilla_retires_Firefox_4_from_security_support)


Wow.

Yes, Firefox 5 replaces Firefox 4 completely. There won't be multiple supported versions anymore, as soon as they drop support for Firefox 3.5 and 3.6. Then, Firefox will become essentially a "rolling distribution". However, I don't think they have figured out everything yet. There is still the possibility of the release of a 4.0.2, although that is very unlikely.

---

### Post by SilverWave on 2011-06-23
> **lovinglinux said:**
> Yes, Firefox 5 replaces Firefox 4 completely. There won't be multiple supported versions anymore, as soon as they drop support for Firefox 3.5 and 3.6. Then, Firefox will become essentially a "rolling distribution". However, I don't think they have figured out everything yet. There is still the possibility of the release of a 4.0.2, although that is very unlikely.


Good move by Mozilla.

This whole new fast release change, has breathed a new lease of life into to Firefox development.

I was surprised by the security support stop for ff4, but it makes a lot of sense once I gave it some thought, you concentrate your efforts on the main game instead of wasting them on yesterdays tech.

The add-on issue is being addressed in the short-term by auto bumping all working add-ons.

Long term Jetpack and other initiatives will sort this out.

Well done Mozilla, Well done.

Of course not everyone is going to be happy with this change ;-)

---

### Post by lovinglinux on 2011-06-23
> **SilverWave said:**
> Good move by Mozilla.

This whole new fast release change, has breathed a new lease of life into to Firefox development.

I was surprised by the security support stop for ff4, but it makes a lot of sense once I gave it some thought, you concentrate your efforts on the main game instead of wasting them on yesterdays tech.

The add-on issue is being addressed in the short-term by auto bumping all working add-ons.

Long term Jetpack and other initiatives will sort this out.

Well done Mozilla, Well done.

Indeed. 

> **SilverWave said:**
> Of course not everyone is going to be happy with this change ;-)

See [this thread]("http://ubuntuforums.org/showthread.php?t=1788496") for example.

---

### Post by SilverWave on 2011-06-23
> **lovinglinux said:**
> Indeed. 
See [this thread]("http://ubuntuforums.org/showthread.php?t=1788496") for example.


Just a final thought...
Previously we would get very few firefox updates and we received them late...
Under the new model this is no longer the case.
This is a big win for Linux firefox users.

---

### Post by graabein on 2011-06-24
Hey what's the Firefox 5 PPA for us guys on Ubuntu 10.10?

---

### Post by SilverWave on 2011-06-24
> **graabein said:**
> Hey what's the Firefox 5 PPA for us guys on Ubuntu 10.10?

The Stable FF5 is here:

**10.04 & 10.10****:**
[https://launchpad.net/~mozillateam/+archive/firefox-stable]("https://launchpad.net/%7Emozillateam/+archive/firefox-stable")
    ```
sudo add-apt-repository ppa:mozillateam/firefox-stable 
```**Update & Install**
     ```
sudo apt-get update 
sudo apt-get install firefox
```

---

### Post by SilverWave on 2011-06-25
This is a great article full of interesting information:

[Why do Firefox updates break add-ons?]("http://www.oxymoronical.com/blog/2011/06/Why-do-Firefox-updates-break-add-ons")

> The crux of the matter is in how deeply we allow add-ons integrate  with Firefox. Most browsers separate add-ons from their code using what  can be called an add-on API. All the add-on can see and use is what the  browser makes available through that API and this is normally a  restricted set of functionality. Firefox has no such separation. Add-on  code runs in exactly the same setting as the browser code, they can call  any of the internal functionality that we write to make the browser  work in the first place.
 There are big advantages to the Firefox way:
 
[LIST]
[*]Add-ons can do basically anything, allowing really complicated add-ons like Firebug and NoScript to exist.
[*]Authors don’t have to wait for features to be exposed through some  API to be able to use it, as soon as the feature is in the application  add-ons can use it.
[/LIST]
 There are also some disadvantages:
 
[LIST]
[*]Add-ons can do basically anything so you should be wary about installing add-ons from people you don’t trust!
[*]Because we aren’t forced to provide an API specifically for add-ons  sometimes what is there can be cumbersome for add-ons to use.
[*]Add-ons rely on internal functions, if we make a change to one then it breaks the add-on.
[/LIST]
 It is that last point which explains why Firefox updates break  add-ons. Any time we add, remove or change some code we run a risk that  some add-on depends on it and so will break. Some bits of code are more  important than others but we have such a vast library of add-ons now  that it’s probably getting to the point where almost everything is in  use. When people say that Firefox updates shouldn’t break add-ons what  they don’t realise is that they’re asking us to stop making changes to  Firefox: no new features, no bug fixes.


And here is the fix for a lot of add-ons, at least in theory...

> **How does the Add-ons SDK fit in?**

 With the most recent update to Firefox we also made the first official release of the new [add-ons SDK]("https://addons.mozilla.org/en-US/developers/builder")  available. These are tools designed to make developing add-ons for  Firefox easier and faster and they largely serve as an add-ons API  sitting between the add-on and Firefox with one difference, the API is  actually a part of the add-on so you can actually write your own  additional APIs to supplement those in the core SDK.
 Add-ons written with the SDK (and only using the core APIs) gain a  lot of the benefits of add-ons for other browsers. The APIs in the SDK  can be far more stable than those in the browser itself, as the browser  code changes the internal SDK code can adapt to match allowing add-ons  to work just by rebuilding with the newer SDK. This makes the problem of  Firefox updates much smaller for those that can move their add-ons to  the SDK.
 I don’t foresee a future where the only add-ons are SDK based though.  We’d lose too many really important add-ons that way so the SDK doesn’t  completely solve the problem.


---

### Post by lovinglinux on 2011-06-25
> **SilverWave said:**
> [Why do Firefox updates break add-ons?]("http://www.oxymoronical.com/blog/2011/06/Why-do-Firefox-updates-break-add-ons")

Also why Firefox add-ons are better than other browsers, in terms of functionality.

---

### Post by SilverWave on 2011-06-25
> **lovinglinux said:**
> Also why Firefox add-ons are better than other browsers, in terms of functionality.

True true... 

I should also point out that you are giving the add-on developer a lot of trust, as he has such low level access to your browser.

---

### Post by lovinglinux on 2011-06-25
> **SilverWave said:**
> True true... 

I should also point out that you are giving the add-on developer a lot of trust, as he has such low level access to your browser.

Indeed, but Mozilla scan and review all ad-ons, including new versions, prior to making them public.

I hope you don't mind, but I am leeching your posts with nice articles and [reposting in the Mega Thread]("http://ubuntuforums.org/showpost.php?p=10979968&postcount=1036"). You find some really nice stuff. :-)

---

### Post by graabein on 2011-06-25
Thanks for the link :)

---

### Post by geazzy on 2011-06-25
nice threads :)

---

### Post by SilverWave on 2011-06-27
[Telemetry is on in Nightly Firefox builds](http://blog.mozilla.com/tglek/2011/06/27/telemetry-is-on-in-nightly-firefox-builds/)

> Telemetry went live in Firefox Nightly builds over the weekend. Everyone  who wants to contribute to making Firefox better now has an easy new  way: opt-in to telemetry.
There are two ways to opt in:
A) Click yes when prompted to report performance
B) Enable it by going to Options/Preferences, then Advanced/General tab

---

### Post by SilverWave on 2011-06-29
[Firefox 6 will be released in eight weeks]("http://blog.mozilla.com/nnethercote/2011/06/28/firefox-6-will-be-released-in-six-weeks/")

> **Update:** Mike Hommey has kindly corrected me;  there  will be 8 weeks between FF5 and FF6.  There will then be 6 weeks between  all subsequent releases.  The 12 week gap between FF4 and FF5 and the  8-week gap between FF5 and FF6 were artifacts of the timeline used to  get the rapid release process up to speed.> Nicholas Nethercote                         Glandium: thanks for the correction. [https://wiki.mozilla.org/RapidRelease](https://wiki.mozilla.org/RapidRelease) doesn&#8217;t have much detail beyond FF5, but I just found [https://wiki.mozilla.org/RapidRelease/Calendar](https://wiki.mozilla.org/RapidRelease/Calendar) which has this:
 2011-07-05: Firefox 7  -> mozilla-aurora; Firefox 6  -> mozilla-beta
2011-08-16: Firefox 8  -> mozilla-aurora; Firefox 7  -> mozilla-beta; Firefox 6  -> mozilla-release
2011-09-27: Firefox 9  -> mozilla-aurora; Firefox 8  -> mozilla-beta; Firefox 7  -> mozilla-release
2011-11-08: Firefox 10 -> mozilla-aurora; Firefox 9  -> mozilla-beta; Firefox 8  -> mozilla-release
2011-12-20: Firefox 11 -> mozilla-aurora; Firefox 10 -> mozilla-beta; Firefox 9  -> mozilla-release


---

### Post by SilverWave on 2011-06-29
> Add-ons can do basically anything, allowing really complicated add-ons like Firebug and NoScript to exist.
> **lovinglinux said:**
> Also why Firefox add-ons are better than other browsers, in terms of functionality.> I don&#8217;t foresee a future where the only add-ons are SDK based though.   We&#8217;d lose too many really important add-ons that way so the SDK doesn&#8217;t   completely solve the problem.I have a real world example of this with [Boox 3.0]("https://addons.mozilla.org/en-US/firefox/addon/boox/")
> **joliclic said:**
> Unfortunatly, it's impossible to develop Boox with the sdk.

[QUOTE=SilverWave;]Oh that's a shame :-(   I am just concerned regarding the new FF fast release being every 6 weeks in future (8weeks for ff6).
   Well... they are apparently doing more testing of Add-ons to help to keep the breakage to a minimum

Hopefully they wont make any changes that affect Boox ;-)
[/QUOTE]

So I am in the same boat as everyone else regarding add-ons, as this one add-on is a deal breaker for me re updating...
...while wanting to be as secure as possible, and so needing the latest security updates :-|

---

### Post by lovinglinux on 2011-06-29
> **SilverWave said:**
> I have a real world example of this with [Boox 3.0]("https://addons.mozilla.org/en-US/firefox/addon/boox/")

So I am in the same boat as everyone else regarding add-ons, as this one add-on is a deal breaker for me re updating.

But Boox is already compatible with FF 6.

---

### Post by SilverWave on 2011-06-29
> **lovinglinux said:**
> But Boox is already compatible with FF 6.

Indeed but as the author can not use the SDK there is no guarantee that this will be so with later versions.

And with new versions hitting every 6 weeks... well I am keeping my fingers crossed :-D

---

### Post by lovinglinux on 2011-06-29
> **SilverWave said:**
> Indeed but as the author can not use the SDK there is no guarantee that this will be so with later versions.

And with new versions hitting every 6 weeks... well I am keeping my fingers crossed :-D

At least you are safe for at least the next 14 weeks.

---

### Post by SilverWave on 2011-06-30
[Firefox 5 A Success For Mozilla]("http://www.conceivablytech.com/8186/products/firefox-5-a-success-for-mozilla")

> This is a browser that was created as a launch platform for future  Mozilla browsers. In some way, Firefox 5 is a browser that Mozilla made  for itself.> After one week of availability, Firefox 5 was listed with a market share  of 10.78%, which translates to about 38.5% of Firefox’ entire user  base. Firefox 4 had only 5.34% of share after one week, or about 18.0%  of the Firefox user base. Firefox 3.6 was even slower, capturing only  3.06% market share or 9.6% of the Firefox user base within the first  week.

[IMG]http://www.conceivablytech.com/wp-content/uploads/2011/06/browsertransition.jpg[/IMG]

---

### Post by SilverWave on 2011-07-02
Changes for the versions:
7.0~a1~hg20110619r71298+nobinonly-0ubuntu1~umd1~natty
7.0~a1~hg20110701r72120+nobinonly-0ubuntu1~umd1~natty

[[IMG]https://launchpad.net/@@/treeCollapsed[/IMG]         [IMG]https://launchpad.net/@@/package-source[/IMG]         firefox-trunk - 7.0~a1~hg20110701r72120+nobinonly-0ubuntu1~umd1~natty]("https://launchpad.net/%7Esilverwave/+archive/testing1/+sourcepub/1803685/+listing-archive-extra")


Interesting...
> 
* Drop the profile migrator, as it doesn't really make any sense with the new
    release cycle. Instead, just copy the firefox profile (if it exists) to
    firefox-trunk (if it doesn't exist)
    - remove debian/migrator/xulapp-profilemigrator
    - update debian/firefox.sh.in
    - update debian/firefox.install.in
    - update debian/rules
    - update debian/control{.in}
  * Now we have no profile migrator and upstream lazily load libxul, drop our
    shell wrapper for eveerything except firefox-trunk builds (where we want
    to clone the firefox profile)
    - update debian/firefox.sh.in
    - update debian/rules
    - update debian/firefox.install.in
  * Ensure we install dependentlibs.list so that Firefox knows which libs
    to dlopen before libxul
    - update debian/firefox.install.in
 -- Chris Coulson <chris.coulson@canonical.com>   Fri, 01 Jul 2011 11:37:13 +0100

---

### Post by SilverWave on 2011-07-02
Interesting...

[Behind the scene mechanics of Firefox5.0 / Fennec5.0](http://oduinn.com/blog/2011/07/01/behind-the-scene-mechanics-of-firefox5-0-fennec5-0/)

> **3) In the days leading up to the Firefox5.0/Fennec5.0/3.6.18 release, [we did nine last-minute betas/releases in quick succession]("http://oduinn.com/blog/2011/06/20/10-releases-in-9-days/"). **
This fast turnaround was only possible because RelEng’s ongoing  automation improvements has reduced our build times from 45hours down to  8hours. It was only because of this fast turnaround that Mozilla could  accommodate some last minute fixes without impacting the release  schedule. I feel its important to point out that, while there were tight  deadlines, and  a lot of very precise fast moving footwork, this was  all done without burning out the humans in RelEng working those  releases.

---

### Post by SilverWave on 2011-07-05
So here we go again :-)

> **Source Migration Notice: FINISHED mozilla-central &#8594; mozilla-aurora**

                                **Source Migration Notice:** We have finished the mozilla-central &#8594; mozilla-aurora source code migration.
 
                                                                                                                  This entry was posted on Tuesday, July 5th, 2011 at 9:48 am                        and is filed under [Source Migration]("http://blog.mozilla.com/channels/category/source-migration/").

[here](http://blog.mozilla.com/channels/2011/07/05/source-migration-notice-finished-mozilla-central-mozilla-aurora-2/)

---

### Post by SilverWave on 2011-07-06
Changes for the versions:
7.0~a1~hg20110701r72120+nobinonly-0ubuntu1~umd1~natty
8.0~a1~hg20110706r72416+nobinonly-0ubuntu1~umd1~natty

[[IMG]https://launchpad.net/@@/treeCollapsed[/IMG]         [IMG]https://launchpad.net/@@/package-source[/IMG]         firefox-trunk - 8.0~a1~hg20110706r72416+nobinonly-0ubuntu1~umd1~natty       ]("https://launchpad.net/%7Esilverwave/+archive/testing1/+sourcepub/1808813/+listing-archive-extra")

---

### Post by SilverWave on 2011-07-06
hmmm...

[Firefox 8 First Taste, Firefox 6 Beta and Firefox 7 Aurora Soon](http://news.softpedia.com/news/Firefox-8-First-Taste-Firefox-6-Beta-and-Firefox-7-Aurora-Soon-210100.shtml)

> Various sources claimed that July 5 would bring with it the availability of Firefox 6 Beta and Firefox 7 Aurora. Obviously, this was not the case.

The reason for this is that July 5 was actually the merge date for Firefox 6 Beta and Firefox 7 Aurora, and not the launch deadline for the two development milestones.

It will still be some time before the fully-fledged Firefox 6 Beta and Firefox 7 Aurora are ready to be shipped to testers, which will be soon enough. 

---

### Post by SilverWave on 2011-07-06
> **SilverWave said:**
> hmmm...

[Firefox 8 First Taste, Firefox 6 Beta and Firefox 7 Aurora Soon]("http://news.softpedia.com/news/Firefox-8-First-Taste-Firefox-6-Beta-and-Firefox-7-Aurora-Soon-210100.shtml")

Well the [Aurora](https://launchpad.net/~ubuntu-mozilla-daily/+archive/firefox-aurora/+packages) packages are being built as I write this...

---

### Post by lovinglinux on 2011-07-06
Firefox 8 brings memory tests page. Just type **about:memory** in the address bar.

[[IMG]http://www4.picturepush.com/photo/a/6043007/640/6043007.png[/IMG]](http://picturepush.com/public/6043007)

---

### Post by SilverWave on 2011-07-06
[This was the final week of development for Firefox 7, and lots of exciting MemShrink stuff happened.](http://blog.mozilla.com/nnethercote/2011/07/06/memshrink-progress-week-3/)

Well this is great news -)

>  Parts of Firefox itself are implemented in JavaScript, and many objects  belonging to Firefox itself (more specifically, objects in the “system  principal” and “atoms” compartments) are long-lived.  So Gregor added  simple chunk segregation;  objects belonging to Firefox get put in one  group of chunks, and all other objects (i.e. those from websites) get  put in a second group of chunks.  This made a huge difference.  See [this comment]("https://bugzilla.mozilla.org/show_bug.cgi?id=666058#c31")  and subsequent comments for some detailed measurements of a short  browsing session;  in short, the size of the heap was over 5x smaller  (21MB vs. 108MB) after closing a number of tabs and forcing garbage  collection.

---

### Post by SilverWave on 2011-07-06
> **lovinglinux said:**
> Firefox 8 brings memory tests page. Just type **about:memory** in the address bar.

[[IMG]http://www4.picturepush.com/photo/a/6043007/640/6043007.png[/IMG]]("http://picturepush.com/public/6043007")

Thanks just starting to play about with that :-)

---

### Post by SilverWave on 2011-07-06
> **SilverWave said:**
> hmmm...

[Firefox 8 First Taste, Firefox 6 Beta and Firefox 7 Aurora Soon]("http://news.softpedia.com/news/Firefox-8-First-Taste-Firefox-6-Beta-and-Firefox-7-Aurora-Soon-210100.shtml")

And here we go with the [Beta](https://launchpad.net/~mozillateam/+archive/firefox-next/+packages) :-)

[[IMG]https://launchpad.net/@@/treeCollapsed[/IMG]         [IMG]https://launchpad.net/@@/package-source[/IMG]         firefox - 6.0~b1+build1+nobinonly-0ubuntu0.11.04.1~mfn1       ]("https://launchpad.net/%7Emozillateam/+archive/firefox-next/+sourcepub/1809007/+listing-archive-extra")

Again building as I write this...

---

### Post by SilverWave on 2011-07-06
________________________________________

**Firefox 6** currently in BETA channel moves to RELEASED on August 16, 2011**.**

[[IMG]https://wiki.mozilla.org/images/1/1e/Final-50slice.png[/IMG]]("https://wiki.mozilla.org/File:Final-50slice.png")
  
**Firefox 7 **currently in AURORA channel moves to BETA on August 16, 2011.

     [[IMG]https://wiki.mozilla.org/images/4/4f/Aurora-50slice.png[/IMG]]("https://wiki.mozilla.org/File:Aurora-50slice.png")  

**Firefox 8 **currently in NIGHTLY channel moves to AURORA on August 16, 2011.

     [[IMG]https://wiki.mozilla.org/images/f/fa/Nightly-50slice.png[/IMG]]("https://wiki.mozilla.org/File:Nightly-50slice.png")  

________________________________________

---

### Post by SilverWave on 2011-07-07
> **SilverWave said:**
> And here we go with the [Beta]("https://launchpad.net/%7Emozillateam/+archive/firefox-next/+packages") :-)

[[IMG]https://launchpad.net/@@/treeCollapsed[/IMG]         [IMG]https://launchpad.net/@@/package-source[/IMG]         firefox - 6.0~b1+build1+nobinonly-0ubuntu0.11.04.1~mfn1       ]("https://launchpad.net/%7Emozillateam/+archive/firefox-next/+sourcepub/1809007/+listing-archive-extra")

Again building as I write this...


Updated Firefox on my Natty box to the new beta 1 and all looks OK so far.

Note: The other builds failed.

---

### Post by chrisccoulson on 2011-07-08
> **SilverWave said:**
> Updated Firefox on my Natty box to the new beta 1 and all looks OK so far.

Note: The other builds failed.

Publishing is currently disabled for the firefox-next PPA because Mozilla haven't even officially released 6.0 to beta testers yet (that might happen later today). Could you please not copy these pre-release builds and publish them to everyone before they are released?

---

### Post by SilverWave on 2011-07-08
> **chrisccoulson said:**
> Publishing is currently disabled for the firefox-next PPA because Mozilla haven't even officially released 6.0 to beta testers yet (that might happen later today). Could you please not copy these pre-release builds and publish them to everyone before they are released?

Yes I stopped after Natty, once I noticed Publishing was disabled.

Saying which the natty build looks OK and I am using it to post this reply.

---

### Post by SilverWave on 2011-07-09
[Firefox 6 arrives in Beta Channel]("http://www.h-online.com/open/news/item/Firefox-6-arrives-in-Beta-Channel-1274620.html")

[Release Notes]("http://www.mozilla.com/en-US/firefox/6.0beta/releasenotes/")

---

### Post by SilverWave on 2011-07-09
The Beta 1's are now Published.

Changes for the versions:
6.0~b1+build1+nobinonly-0ubuntu0.11.04.1~mfn1
6.0~b1+build1+nobinonly-0ubuntu0.11.04.1~mfn2

Natty
Maverick
Lucid

[[IMG]https://launchpad.net/@@/treeExpanded[/IMG]         [IMG]https://launchpad.net/@@/package-source[/IMG]         firefox - 6.0~b1+build1+nobinonly-0ubuntu0.11.04.1~mfn2       ]("https://launchpad.net/%7Esilverwave/+archive/testing4/+sourcepub/1812529/+listing-archive-extra")

---

### Post by SilverWave on 2011-07-11
Here we go...

[IMG]https://launchpad.net/@@/package-source[/IMG]                 firefox-trunk                                               8.0~a1~hg20110711r72585+nobinonly-0ubuntu1~umd1~natty

As I have heard great things regarding the new nightlies I am going to see if I cant use 8.0a as my main browser...
we shall see :-)

---

### Post by SilverWave on 2011-07-12
> **SilverWave said:**
> Here we go...

[IMG]https://launchpad.net/@@/package-source[/IMG]                 firefox-trunk                                               8.0~a1~hg20110711r72585+nobinonly-0ubuntu1~umd1~natty

As I have heard great things regarding the new nightlies I am going to see if I cant use 8.0a as my main browser...
we shall see :-)

Happy to report that everything works perfectly - you would think it was a Beta rather than a nightly :-D

All I did was add the PPA for the Natty Nightly then update and accept the package offered.

Once it had updated I copied my profile from firefox to firefox-trunk(after deleting the contents of firefox-trunk).

All my add-ons work! Nice :smile:

---

### Post by SilverWave on 2011-07-12
> **SilverWave said:**
> ...

All my add-ons work! Nice :smile:

Here is a dump of everything I have loaded in the Nightly:

> Adblock Plus 1.3.9
Add-on Compatibility Reporter 0.8.5
Barlesque 1.15
Boox 3.0
Default 8.0a1
DivX® Web Player  [DISABLED]
DOM Inspector 2.0.10
Download Statusbar 0.9.8
Gawker 2011 - Vintage Gawker (Removed Sidebar) FIX 
Global Menu Bar integration 1.8pre
IcedTea-Web Plugin (using IcedTea-Web 1.1pre (1.1~20110420-0ubuntu1.1))  [DISABLED]
Image Zoom 0.4.6
Locationbar² 1.0.6
Make Link 11.03
Menu Editor 1.2.7
Mozilla Labs 1260925626 [DISABLED]
Nightly Tester Tools 3.1.7
NoSquint 2.1.2
OPML Support 1.6
OptimizeGoogle 0.78.2
Places&#8217; Full Titles 4
QuickTime Plug-in 7.6.6  [DISABLED]
Re-Pagination 2011.03.24
Readability 1.5
Reliby 1.5.0
RequestPolicy 0.5.21
Shelve 1.23
Shockwave Flash 
SilverWave - ARS0. No Sidebar. arstechnica.com 
SilverWave - BB00. No Sidebar. bloomberg.com 
SilverWave - BBC0. No Sidebar. bbc.co.uk 
SilverWave - BF00. No Sidebar. blogs.forbes.com 
SilverWave - CNET. No Sidebar. cnet.com 
SilverWave - CTEC. No Sidebar. conceivablytech.com 
SilverWave - CW00. No Sidebar. computerworld.com 
SilverWave - CWU0. No Sidebar. computerworlduk.com 
SilverWave - FOOL. No Sidebar. fool.com 
SilverWave - H000. No Sidebar. h-online.com 
SilverWave - MP00. No Sidebar. [www.maximumpc.com]("http://www.maximumpc.com/") 
SilverWave - NYT0. No Sidebar. nytimes.com 
SilverWave - PCM0. No Sidebar. pcmag.com 
SilverWave - PCO0. No Sidebar. paidcontent.org 
SilverWave - PCW0. No Sidebar. [www.pcworld.com]("http://www.pcworld.com/") 
SilverWave - REG0. No Sidebar. theregister.co.uk 
SilverWave - RWW0. No Sidebar. [www.readwriteweb.co]("http://www.readwriteweb.co/") 
SilverWave - SEL0. No Sidebar. searchengineland.co 
SilverWave - SH00. No Sidebar. singularityhub.com 
SilverWave - SP00. No Sidebar. softpedia.com 
SilverWave - TC00. No Sidebar. techcrunch.com 
SilverWave - TCRU. No Sidebar. techcrunch.com 
SilverWave - TD00. No Sidebar. techdrivein.com 
SilverWave - TFLA. No Sidebar. techflash.com 
SilverWave - TNW0. No Sidebar. thenextweb.com 
SilverWave - TR00. No Sidebar. [www.techrepublic.co]("http://www.techrepublic.co/") 
SilverWave - TST0. No Sidebar. tested.com 
SilverWave - TT00. No Sidebar. searchsqlserver.tec 
SilverWave - UF00. Big Edit. ubuntuforums.org/edit 
SilverWave - UG00. No Sidebar. ubuntugeek.com 
SilverWave - UT00. No Sidebar. universetoday.com 
SilverWave - VARG. No Sidebar. thevarguy.com 
SilverWave - WASH. No Sidebar. washingtonpost.com 
SilverWave - WSJ0. No Sidebar. online.wsj.com 
SilverWave - ZDNT. No Sidebar. zdnet.com 
Stylish 1.2
Stylish-Custom 0.7.7
Tab Utilities 1.1
Toolbar Buttons 1.0
Tree Style Tab 0.12.2011061701
Ubuntu Firefox Modifications 0.9.1
VLC Multimedia Plugin (compatible Totem 2.32.0) 
Web Developer 1.1.9
Windows Media Player Plug-in 10 (compatible; Totem)  [DISABLED]

---

### Post by SilverWave on 2011-07-16
[[IMG]https://launchpad.net/@@/treeCollapsed[/IMG]         [IMG]https://launchpad.net/@@/package-source[/IMG]         firefox - 6.0~b2+build1+nobinonly-0ubuntu0.11.04.1~mfn1       ]("https://launchpad.net/%7Emozillateam/+archive/firefox-next/+sourcepub/1818348/+listing-archive-extra")

---

### Post by SilverWave on 2011-07-16
[[IMG]https://launchpad.net/@@/treeCollapsed[/IMG]         [IMG]https://launchpad.net/@@/package-source[/IMG]         firefox-trunk - 8.0~a1~hg20110714r72818+nobinonly-0ubuntu1~umd1~natty]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+sourcepub/1819249/+listing-archive-extra")

All look OK except the i386 Oneiric build.

---

### Post by SilverWave on 2011-07-16
> **SilverWave said:**
> [[IMG]https://launchpad.net/@@/treeCollapsed[/IMG]         [IMG]https://launchpad.net/@@/package-source[/IMG]         firefox - 6.0~b2+build1+nobinonly-0ubuntu0.11.04.1~mfn1       ]("https://launchpad.net/%7Emozillateam/+archive/firefox-next/+sourcepub/1818348/+listing-archive-extra")

Just updated with the latest Beta refresh aka b2

---

### Post by SilverWave on 2011-07-19
[Every Six Weeks](http://blog.johnath.com/2011/07/18/every-six-weeks/comment-page-1/)

[IMG]http://blog.johnath.com/wp-content/uploads/2011/07/rrprocess2-1024x965.png[/IMG]

---

### Post by lovinglinux on 2011-07-19
Electrolysis project coming back:

[http://arstechnica.com/open-source/news/2011/07/mozilla-outlines-goals-for-multiprocess-browsing-implementation.ars](http://arstechnica.com/open-source/news/2011/07/mozilla-outlines-goals-for-multiprocess-browsing-implementation.ars)

[http://blog.mozilla.com/products/2011/07/15/goals-for-multi-process-firefox/](http://blog.mozilla.com/products/2011/07/15/goals-for-multi-process-firefox/)

[http://www.conceivablytech.com/8478/products/electrolysis-firefox-gets-atomized-to-run-faster](http://www.conceivablytech.com/8478/products/electrolysis-firefox-gets-atomized-to-run-faster)

---

### Post by SilverWave on 2011-07-20
> **lovinglinux said:**
> Electrolysis project coming back:

[http://arstechnica.com/open-source/news/2011/07/mozilla-outlines-goals-for-multiprocess-browsing-implementation.ars](http://arstechnica.com/open-source/news/2011/07/mozilla-outlines-goals-for-multiprocess-browsing-implementation.ars)

[http://blog.mozilla.com/products/2011/07/15/goals-for-multi-process-firefox/](http://blog.mozilla.com/products/2011/07/15/goals-for-multi-process-firefox/)

[http://www.conceivablytech.com/8478/products/electrolysis-firefox-gets-atomized-to-run-faster](http://www.conceivablytech.com/8478/products/electrolysis-firefox-gets-atomized-to-run-faster)


Interesting but I don’t think I will be holding my breath while we wait ;-)

---

### Post by lovinglinux on 2011-07-20
> **SilverWave said:**
> Interesting but I don’t think I will be holding my breath while we wait ;-)

It will certainly take a lot of time to land on our hands.

---

### Post by lovinglinux on 2011-07-21
Good news about Panorama feature. 

[http://www.conceivablytech.com/8520/products/mozilla-overhauls-firefox-panorama](http://www.conceivablytech.com/8520/products/mozilla-overhauls-firefox-panorama)

The new improvements are already available in Firefox 6, 7 and 8.

I am becoming a big fan of the fast release cycle :-)

---

### Post by SilverWave on 2011-07-21
Well natty 64bit is done and working fine ATM, but the rest may take a little longer show up in the PPA's

Changes for the versions:
8.0~a1~hg20110714r72818+nobinonly-0ubuntu1~umd1~natty
8.0~a1~hg20110721r73087+nobinonly-0ubuntu1~umd1~natty

This change is not from a source that supports changelogs.

---

### Post by lovinglinux on 2011-07-21
[Automated daily builds now only occur if there are changes]("http://blog.mozilla.com/channels/2011/07/21/automated-daily-builds-now-only-occur-if-there-are-changes/")

> 
Previously, early in the morning the build system blindly updated to the latest tip of tree, built it, generated updates, and made them available on the proper channel–even if there were no changes since the last time. This was inefficient for users, a poor use of build system resources, and unnecessarily contributed to update fatigue for less-active channels.

The new behavior makes it so automated morning builds only occur when the code or dependent localizations have actually changed since the last update.

---

### Post by SilverWave on 2011-07-21
> **lovinglinux said:**
> Good news about Panorama feature. 

[http://www.conceivablytech.com/8520/products/mozilla-overhauls-firefox-panorama](http://www.conceivablytech.com/8520/products/mozilla-overhauls-firefox-panorama)

The new improvements are already available in Firefox 6, 7 and 8.

Hmm may give it another go...
TBH its going to have to go some to beat "Tree Style Tabs" though.

> I am becoming a big fan of the fast release cycle :-)So am I its just starting but you can see how good thing are going to get :-)

---

### Post by SilverWave on 2011-07-22
Just to underline how much cross site stuff this add-on protects you from, have a look at the screen shot!

You are cutting out 99% of the risk with this one add-on.

I am highlighting it here as having this type of add-on is *the* difference between Firefox and Chrome, and as expected it always gets bumped to work whenever a new Firefox comes out.


[RequestPolicy]("https://addons.mozilla.org/en-US/firefox/addon/requestpolicy/")

> 
Be in control of which cross-site requests are allowed. Improve the  privacy of your browsing by not letting other sites know your browsing  habits. Secure yourself from Cross-Site Request Forgery (CSRF) and other  attacks.

---

### Post by lovinglinux on 2011-07-22
> **SilverWave said:**
> Just to underline how much cross site stuff this add-on protects you from, have a look at the screen shot!

You are cutting out 99% of the risk with this one add-on.

I am highlighting it here as having this type of add-on is *the* difference between Firefox and Chrome, and as expected it always gets bumped to work whenever a new Firefox comes out.


[RequestPolicy]("https://addons.mozilla.org/en-US/firefox/addon/requestpolicy/")

Nice. Thanks for sharing. So far it seems to catch all the stuff Ghostery blocks and more.

---

### Post by SilverWave on 2011-07-24
> 6.0~b3+build2+nobinonly-0ubuntu0.11.04.1~mfn1                                Not copied to my PPA's yet as Chris has Publishing disabled atm.

So the polishing of Firefox 6.0 continues with this beta refresh from Mozilla... nice :-)

---

### Post by SilverWave on 2011-07-26
[[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox - 6.0~b3+build2+nobinonly-0ubuntu0.11.04.1~mfn1       ]("https://launchpad.net/%7Esilverwave/+archive/testing4/+sourcepub/1833242/+listing-archive-extra")

---

### Post by SilverWave on 2011-07-26
> **SilverWave said:**
> [[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox - 6.0~b3+build2+nobinonly-0ubuntu0.11.04.1~mfn1       ]("https://launchpad.net/%7Esilverwave/+archive/testing4/+sourcepub/1833242/+listing-archive-extra")

Interesting...

> 
**Changelog**

         firefox (6.0~b3+build2+nobinonly-0ubuntu0.11.04.1~mfn1) natty; urgency=low    * New upstream release from the beta channel (FIREFOX_6_0b3_BUILD2)    * Unconditionally build with --disable-elf-hack. It's basically a noop     on Ubuntu, as we don't get any of the nice space saving and startup     time improvements that upstream builds get with it. Enabling it is     problematic (it fails to build on all architectures in Ubuntu from     Firefox 7 onwards, and is problematic on armel when building on     older Ubuntu versions)     - update debian/rules     - update debian/mozconfig.in   * Refresh debian/patches/reload-new-plugins.patch  -- Chris Coulson <[chris.coulson@canonical.com]("https://launchpad.net/%7Echrisccoulson")>   Fri, 22 Jul 2011 17:29:01 +0100**Elfhack**

                                                       [Home]("http://wiki.mozilla.org/") » [Elfhack]("http://wiki.mozilla.org/Elfhack")                
                                                                                                                                    **elfhack** is a part of the  Mozilla build system that optimizes relocations in compiled libraries.   For more information about elfhack, see: 
 
[LIST]
[*] [bug 606145]("https://bugzilla.mozilla.org/show_bug.cgi?id=606145") - Compress/pack relocations in ELF binaries (elfhack)
[*] [Improving libxul startup I/O by hacking the ELF format with elfhack]("http://glandium.org/blog/?p=1177")
[*] [Link-Time Optimization (LTO)]("http://blog.mozilla.com/respindola/2011/02/22/lto/")
[/LIST]

---

### Post by ron999 on 2011-07-26
@SilverWave
I can't use that version "firefox (6.0~b3+build2+nobinonly-0ubuntu0.11.04.1~mfn1)" with Lucid Lynx.
But I'm interested to find out what build options have been used.
Please will you post the "Configure arguments" from about:buildconfig.

---

### Post by SilverWave on 2011-07-26
> **ron999 said:**
> @SilverWave
I can't use that version "firefox (6.0~b3+build2+nobinonly-0ubuntu0.11.04.1~mfn1)" with Lucid Lynx.
But I'm interested to find out what build options have been used.
Please will you post the "Configure arguments" from about:buildconfig.

You need to use this PPA for Lucid:

> [B]Lucid
[/B][https://launchpad.net/~silverwave/+archive/testing6]("https://launchpad.net/%7Esilverwave/+archive/testing6")
     ```
sudo add-apt-repository ppa:silverwave/testing6 
```
** Update & Install**
          
     ```
sudo apt-get update sudo apt-get install firefox 
```
I have just tested in a VM and it upgrades from FF3.6 fine.

---

### Post by SilverWave on 2011-07-26
> **ron999 said:**
> @SilverWave
I can't use that version "firefox (6.0~b3+build2+nobinonly-0ubuntu0.11.04.1~mfn1)" with Lucid Lynx.
But I'm interested to find out what build options have been used.
Please will you post the "Configure arguments" from about:buildconfig.

Just in case you still need this...

```
about:buildconfig
Build platform
target
x86_64-unknown-linux-gnu
Build tools
Compiler     Version     Compiler flags
gcc     gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5)     -Wall -W -Wno-unused -Wpointer-arith -Wcast-align -W -pedantic -Wno-long-long -g -fno-strict-aliasing -pthread -pipe -DNDEBUG -DTRIMMED -g -Os -freorder-blocks -fomit-frame-pointer
c++     gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5)     -fno-rtti -fno-exceptions -Wall -Wpointer-arith -Woverloaded-virtual -Wsynth -Wno-ctor-dtor-privacy -Wno-non-virtual-dtor -Wcast-align -Wno-invalid-offsetof -Wno-variadic-macros -Werror=return-type -pedantic -Wno-long-long -g -fno-strict-aliasing -fshort-wchar -pthread -pipe -DNDEBUG -DTRIMMED -g -Os -freorder-blocks -fomit-frame-pointer
Configure arguments

--build=x86_64-linux-gnu --prefix=/usr --localstatedir=/var --libexecdir=/usr/lib/firefox-6.0 '--with-l10n-base=/build/buildd/firefox-6.0~b3+build2+nobinonly/build-tree/mozilla/l10n' --disable-maintainer-mode --disable-dependency-tracking --disable-silent-rules '--srcdir=/build/buildd/firefox-6.0~b3+build2+nobinonly/build-tree/mozilla' --disable-elf-dynstr-gc --disable-install-strip --disable-strip --disable-updater --enable-application=browser --enable-default-toolkit=cairo-gtk2 --enable-startup-notification --enable-pango --enable-svg --enable-mathml --enable-safe-browsing --with-distribution-id=com.ubuntu --without-system-jpeg --without-system-png --without-system-zlib --enable-optimize --enable-tests --enable-mochitest --enable-ipdl-tests --disable-system-cairo --without-system-nspr --without-system-nss --disable-system-sqlite --disable-system-hunspell --enable-crashreporter --enable-official-branding --enable-gnomevfs --enable-update-channel=beta --disable-debug --disable-elf-hack
```

---

### Post by ron999 on 2011-07-26
> **SilverWave said:**
> Just in case you still need this...


Yes, thanks.:)

---

### Post by chrisccoulson on 2011-07-27
> **SilverWave said:**
> You need to use this PPA for Lucid:

Or you could just use the official PPA ;)

```
sudo add-apt-repository ppa:mozillateam/firefox-next
```

---

### Post by SilverWave on 2011-07-27
> **chrisccoulson said:**
> Or you could just use the official PPA ;)

True, true. Although as I am a bit of a control freak, I find having only one package per ppa to be oddly reassuring ;-)

---

### Post by SilverWave on 2011-07-31
[[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox-trunk - 8.0~a1~hg20110730r73544+nobinonly-0ubuntu1~umd1~natty       ]("https://launchpad.net/%7Esilverwave/+archive/testing1/+sourcepub/1841273/+listing-archive-extra")

---

### Post by SilverWave on 2011-08-01
:P> **rongden said:**
> great guide . thank you very much :)

Cheers! Nice to be of help.

---

### Post by lovinglinux on 2011-08-01
Looks like we might see additional radical UI changes in future versions of Firefox.

**Article:** 

[http://www.extremetech.com/computing/91652-mozilla-unveils-new-firefox-interface-for-firefox-9-and-beyond]("http://www.extremetech.com/computing/91652-mozilla-unveils-new-firefox-interface-for-firefox-9-and-beyond")

**Mockup:**

[IMG]http://www.extremetech.com/wp-content/uploads/2011/08/firefox-new-ux-settings-menu-640x426.jpg[/IMG]

It seems a new Home Tab is also on the works:

**Articles:** 

[http://blog.mozilla.com/faaborg/2011/04/13/the-firefox-home-tab/](http://blog.mozilla.com/faaborg/2011/04/13/the-firefox-home-tab/)

[http://www.neowin.net/news/firefox-4-home-tab-design-challenge-winner-announced](http://www.neowin.net/news/firefox-4-home-tab-design-challenge-winner-announced)

**Video:** 

[http://www.youtube.com/watch?v=plNNQJ6pm70](http://www.youtube.com/watch?v=plNNQJ6pm70)
[B]
Mockup:[/B]

[IMG]http://neowin.net/images/uploaded/Firefox_conceptdesign1_287d022f-e854-4da6-b942-df39783a4b3f.jpg[/IMG]

---

### Post by SilverWave on 2011-08-01
> **lovinglinux said:**
> Looks like we might see additional radical UI changes in future versions of Firefox.



[IMG]http://neowin.net/images/uploaded/Firefox_conceptdesign1_287d022f-e854-4da6-b942-df39783a4b3f.jpg[/IMG]

TBH its not that far away from what I am running now.

They have cut the chrome down so much already that any further changes can only be quite small really.

If they wanted to do Radical they should have added an option to stack tabs on the left...

... but this probably does not fit in with the current emphasise on mobile computing.

---

### Post by SilverWave on 2011-08-02
[[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox - 6.0~b4+build1+nobinonly-0ubuntu0.11.04.1~mfn1]("https://launchpad.net/%7Esilverwave/+archive/testing4/+sourcepub/1843422/+listing-archive-extra")

Nice :-)

---

### Post by lovinglinux on 2011-08-03
More interesting proposed changes in Firefox 9.

Mozilla is discussing the possibility of making add-ons compatible by default and disabling those that are incompatible.

[https://wiki.mozilla.org/Features/Add-ons/Add-ons_Default_to_Compatible](https://wiki.mozilla.org/Features/Add-ons/Add-ons_Default_to_Compatible)

> Stage 1: Definition
1. Feature overview

Firefox's switch to rapid releases has been stressful for add-on developers. Add-ons not hosted on AMO are especially pained, as they must update compatibility every 6 weeks without the benefit of automatic compatibility bumping.

Since the release of Firefox 4 and 5, we've learned that there are many more non-hosted add-ons than we previously thought, mostly those installed by other software. Whether users make use of these add-ons or not, seeing an incompatible add-on prevents many users from upgrading to new versions of Firefox.

More than 90% of add-ons are compatible from one version of Firefox to the next, and the ones that aren't usually have binary components that will need to be recompiled every release. If we change the default compatibility assumption, we can reduce the action needed to only the very small number of add-ons broken by the new release, rather than 100% of add-on developers.

We would move to a model where Firefox assumes add-ons are compatible unless they have binary components, the author has explicitly said to strictly observe stated compatibility, or it is reported to AMO as incompatible through the Add-on Compatibility Reporter.

It's possible and likely we will occasionally enable add-ons that don't actually work, but as we omit add-ons with binary components, this should not cause crashes and users will simply not have the functionality they expect, and will complain to the add-on author.

This process would not remove the need for AMO's automatic compatibility bumping, as it's still preferred for authors to be aware of changes in Firefox and learn about upcoming deprecations and other changes. 

> Stage 2: Design
5. Functional specification

When Firefox needs to determine an add-on's compatibility, it should do the following:

1. If the add-on is marked as compatible with the version, nothing needs to be done. The add-on remains enabled.

2. If the add-on is not marked as compatible, Firefox will look at its install.rdf to see if the author has requested strict compatibility qualification. If they have, the add-on is incompatible and disabled.

3. Next, Firefox will look for binary components in the add-on. If binary components are found, the add-on is incompatible and should be treated as such (disabled).

4. If the add-on is not marked as compatible and does not contain binary components, Firefox should look at the metadata it received from AMO about the add-on. If the add-on is not reported as incompatible from AMO, it should be enabled as compatible.

For AMO, this will involve returning information on compatibility reports received in response to metadata API requests, and support for returning information on non-hosted add-ons. 

---

### Post by SilverWave on 2011-08-06
> **lovinglinux said:**
> More interesting proposed changes in Firefox 9.

Mozilla is discussing the possibility of making add-ons compatible by default and disabling those that are incompatible.

[https://wiki.mozilla.org/Features/Add-ons/Add-ons_Default_to_Compatible](https://wiki.mozilla.org/Features/Add-ons/Add-ons_Default_to_Compatible)

Well this is a welcome change, so now the default is to assume an add-on will work until proved otherwise.

This will save a lot of users unnecessary pain when upgrading.

---

### Post by SilverWave on 2011-08-06
[         > ]("https://launchpad.net/%7Emozillateam/+archive/firefox-next/+sourcepub/1845188/+listing-archive-extra")[[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox - 6.0~b5+build1+nobinonly-0ubuntu0.11.04.1~mfn1       ]("https://launchpad.net/%7Emozillateam/+archive/firefox-next/+sourcepub/1845188/+listing-archive-extra")                                  [(changes file)]("https://launchpad.net/%7Emozillateam/+archive/firefox-next/+files/firefox_6.0%7Eb5%2Bbuild1%2Bnobinonly-0ubuntu0.11.04.1%7Emfn1_source.changes")                                 [chrisccoulson]("https://launchpad.net/%7Echrisccoulson")                        13 hours ago     Published     Natty     Web            [IMG]https://launchpad.net/@@/yes[/IMG]                             **Publishing details**

         firefox (6.0~b5+build1+nobinonly-0ubuntu0.11.04.1~mfn1) natty; urgency=low    * New upstream release from the beta channel (FIREFOX_6_0b5_BUILD1)

Yes a new Beta :-)

---

### Post by lovinglinux on 2011-08-06
> **SilverWave said:**
> Well this is a welcome change, so now the default is to assume an add-on will work until proved otherwise.

This will save a lot of users unnecessary pain when upgrading.

Essentially yes, but it is just a proposal. It hasn't been implemented yet.

---

### Post by SilverWave on 2011-08-12
[Firefox 8 to block unapproved add-ons Puts an end to sneaky add-ons installed by other software](http://www.computerworld.com/s/article/9219144/Firefox_8_to_block_unapproved_add_ons)

Interesting.

---

### Post by SilverWave on 2011-08-12
[B]firefox-trunk - 8.0~a1~hg20110811r74250

[/B] Working fine but I am mainly keeping to the Betas these days.

Speaking of which we should be seeing a new firefox 6  shortly :-)

---

### Post by SilverWave on 2011-08-12
[> ]("https://launchpad.net/%7Emozillateam/+archive/firefox-stable/+sourcepub/1855988/+listing-archive-extra")[[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox - 6.0+build1+nobinonly-0ubuntu0.10.10.1~mfs1]("https://launchpad.net/%7Emozillateam/+archive/firefox-stable/+sourcepub/1855988/+listing-archive-extra")

Publishing has been disabled for this archive.

Chris is keeping busy by the looks of the [Packages in “Firefox Stable”](https://launchpad.net/~mozillateam/+archive/firefox-stable/+packages?field.name_filter=firefox&field.status_filter=published&field.series_filter=)

---

### Post by Sierra-X on 2011-08-14
So why exactly is publishing disabled?  Fx6 is out now, I can see no reason not to publish it.

---

### Post by SilverWave on 2011-08-14
> **Sierra-X said:**
> So why exactly is publishing disabled?  Fx6 is out now, I can see no reason not to publish it.

Probably not an official release yet?

---

### Post by chrisccoulson on 2011-08-14
> **Sierra-X said:**
> So why exactly is publishing disabled?  Fx6 is out now, I can see no reason not to publish it.

It's not released until Tuesday, so I'm not sure where you got your information from

---

### Post by Sierra-X on 2011-08-14
> **chrisccoulson said:**
> It's not released until Tuesday, so I'm not sure where you got your information from

My mistake, I could have sworn I read somewhere about it being released earlier than planned.  At any rate, good to know it's not an actual problem, and I apologize for any confusion on my part.

Edit: A-ha, I knew I wasn't crazy: [http://gizmodo.com/5830629/firefox-6-is-out-ahead-of-schedule](http://gizmodo.com/5830629/firefox-6-is-out-ahead-of-schedule)
But yes, I note it's final, but unofficial.

---

### Post by chrisccoulson on 2011-08-14
Hmmm, that website is wrong. The builds are available (as they always are a few days before release), but it's not offered as an upgrade to anyone except beta testers, and isn't offered as a download on any websites (unless you search for it on their ftp server). That will happen on Tuesday, when it's actually released

---

### Post by SilverWave on 2011-08-15
[Removing Firefox Version Number ](http://groups.google.com/group/mozilla.dev.usability/browse_thread/thread/fe75ec92c02be934#)

Interesting.

[Last Comment Bug 678775 - Remove version from About window ](https://bugzilla.mozilla.org/show_bug.cgi?id=678775)

---

### Post by SilverWave on 2011-08-16
The Stable FF6 is here:

**10.04 & 10.10****:**
[https://launchpad.net/~mozillateam/+archive/firefox-stable]("https://launchpad.net/%7Emozillateam/+archive/firefox-stable")
    ```
sudo add-apt-repository ppa:mozillateam/firefox-stable 
```**Update & Install**
     ```
sudo apt-get update 
sudo apt-get install firefox
```


[[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox - 6.0+build1+nobinonly-0ubuntu0.10.04.1~mfs1]("https://launchpad.net/%7Emozillateam/+archive/firefox-stable/+sourcepub/1855990/+listing-archive-extra")
[[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox - 6.0+build1+nobinonly-0ubuntu0.10.10.1~mfs1       ]("https://launchpad.net/%7Emozillateam/+archive/firefox-stable/+sourcepub/1855988/+listing-archive-extra")

---

### Post by SilverWave on 2011-08-16
[[IMG]https://edge.launchpad.net/@@/package-source[/IMG]         firefox - 6.0+build1+nobinonly-0ubuntu0.11.04.1]("https://edge.launchpad.net/%7Eubuntu-mozilla-security/+archive/ppa/+sourcepub/1856754/+listing-archive-extra")

The Stable FF6 is here:

11.04:
[https://edge.launchpad.net/~ubuntu-mozilla-security/+archive/ppa]("https://edge.launchpad.net/%7Eubuntu-mozilla-security/+archive/ppa")
```
sudo add-apt-repository ppa:ubuntu-mozilla-security/ppa 
```Update & Install
```
sudo apt-get update
sudo apt-get install firefox
```

---

### Post by SilverWave on 2011-08-16
**Silverwav's Firefox Beta PPA's**

> **Natty:**
[https://launchpad.net/~silverwave/+archive/testing4]("https://launchpad.net/%7Esilverwave/+archive/testing4")
```

sudo add-apt-repository ppa:silverwave/testing4 
```**Maverick****:**
[https://launchpad.net/~silverwave/+archive/testing5]("https://launchpad.net/%7Esilverwave/+archive/testing5")
```

sudo add-apt-repository ppa:silverwave/testing5 
```[B]Lucid
[/B][https://launchpad.net/~silverwave/+archive/testing6]("https://launchpad.net/%7Esilverwave/+archive/testing6")
 ```

sudo add-apt-repository ppa:silverwave/testing6 
```** Update & Install**
     ```

sudo apt-get update
sudo apt-get install firefox
```Note1: This beta will replace your old firefox.Just a note now that I see how the new rapid release for Firefox is actually working in practice...

My PPA's will be updated to the latest Beta's as they come out.
At the end of the cycle they will be updated to the latest release firefox.

So if you add a PPA from the list above, you will always have the latest FF6, FF7 etc., as soon as they are available.

I think that the Beta's, at least for me, represent the best reward (in running the latest Firefox) for the least risk (very stable and polished).

---

### Post by SilverWave on 2011-08-17
Less need for these as you have very regular releases of the Beta's.

---

### Post by SilverWave on 2011-08-17
[firefox - 7.0~b1+build1+nobinonly-0ubuntu0.11.04.1~mfn1]("https://launchpad.net/%7Emozillateam/+archive/firefox-next/+sourcepub/1880859/+listing-archive-extra")

So here we go again :-)

Much better memory use coming with this one apparently.

I will update the Beta PPA's ASAP.

---

### Post by SilverWave on 2011-08-17
> **Sierra-X said:**
> My mistake, I could have sworn I read somewhere about it being released earlier than planned.  At any rate, good to know it's not an actual problem, and I apologize for any confusion on my part.

Edit: A-ha, I knew I wasn't crazy: [http://gizmodo.com/5830629/firefox-6-is-out-ahead-of-schedule](http://gizmodo.com/5830629/firefox-6-is-out-ahead-of-schedule)
But yes, I note it's final, but unofficial.

Hi I found this which explains what to expect next:

** [ Merge and Release Dates ]("https://wiki.mozilla.org/RapidRelease#Merge_and_Release_Dates")**

 These are planned branch migration dates based on the current [Development Specifics draft]("http://mozilla.github.com/process-releases/draft/development_specifics/").  They may change if the process changes.  **Note:**  Code is not always released to users on the same day as the branch  migration. The release to users may be a few days later, to allow for  manual testing and sign-off.  
 
[LIST]
[*] 2011-06-21: Firefox 5 -> mozilla-release
[*] 2011-07-05: Firefox 7 -> mozilla-aurora; Firefox 6 -> mozilla-beta
[*] 2011-08-16: Firefox 8 -> mozilla-aurora; Firefox 7 -> mozilla-beta; Firefox 6 -> mozilla-release
[*] 2011-09-27: Firefox 9 -> mozilla-aurora; Firefox 8 -> mozilla-beta; Firefox 7 -> mozilla-release
[/LIST]

---

### Post by SilverWave on 2011-08-19
[         [IMG]https://launchpad.net/@@/package-source[/IMG]         firefox-trunk - 9.0~a1~hg20110817r75407+nobinonly-0ubuntu1~umd1~natty       ]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+sourcepub/1881404/+listing-archive-extra")

---

### Post by SilverWave on 2011-08-20
[[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox - 7.0~b1+build1+nobinonly-0ubuntu0.11.04.1~mfn2]("https://launchpad.net/%7Esilverwave/+archive/testing4/+sourcepub/1903268/+listing-archive-extra")

> 
"Improvements in memory usage, overall, will be on  the order of 20 percent to 30 percent, but will go up to 50 percent in  some cases."
[Firefox 7 Beta Is the Slimmest Firefox Ever, Thanks to Huge Memory Performance Leaps]("http://news.softpedia.com/news/Firefox-7-Beta-Is-the-Slimmest-Firefox-Ever-Thanks-to-Huge-Memory-Performance-Leaps-217557.shtml")

---

### Post by SilverWave on 2011-08-20
> **SilverWave said:**
> [[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox - 7.0~b1+build1+nobinonly-0ubuntu0.11.04.1~mfn2]("https://launchpad.net/%7Esilverwave/+archive/testing4/+sourcepub/1903268/+listing-archive-extra")

Everything seems to be working OK :-)

**Help > Troubleshooting Information**

 > **Application Basics**
Name: Firefox Version 7.0
User Agent: Mozilla/5.0 (X11; Linux x86_64; rv:7.0) Gecko/20100101 Firefox/7.0

**Add-ons**
        Adblock Plus 1.3.9
Add-on Compatibility Reporter 0.8.7
Barlesque 1.15
Boox 3.0
Default 7.0
DivX® Web Player  [DISABLED]
DOM Inspector 2.0.10
Download Statusbar 0.9.8
English (GB) Language Pack 7.0
English (South Africa) Language Pack 7.0
Feedback 1.1.2
Global Menu Bar integration 1.0.7
Hack The Web 1.0.5
IcedTea-Web Plugin (using IcedTea-Web 1.1.1 (1.1.1-0ubuntu1~11.04.1))  [DISABLED]
Image Zoom 0.4.6
Locationbar² 1.0.6
Make Link 11.03
Menu Editor 1.2.7
Mozilla Labs 1260925626 [DISABLED]
Nightly Tester Tools 3.1.7
NoSquint 2.1.2
OPML Support 1.6
OptimizeGoogle 0.78.2
Places&#8217; Full Titles 4
QuickTime Plug-in 7.6.6  [DISABLED]
Re-Pagination 2011.03.24
Readability 1.5
Reliby 1.5.0
RequestPolicy 0.5.22
Shelve 1.25
Shockwave Flash 
Stylish 1.2
Stylish-Custom 0.7.7
Tab Utilities 1.1
Toolbar Buttons 1.0
Tree Style Tab 0.12.2011061701
Ubuntu Firefox Modifications 0.9.1
VLC Multimedia Plugin (compatible Totem 2.32.0) 
Web Developer 1.1.9
Windows Media Player Plug-in 10 (compatible; Totem)  [DISABLED]

  **Graphics**
Adapter Description
        NVIDIA Corporation -- GeForce 8600 GTS/PCI/SSE2

        Driver Version
        3.3.0 NVIDIA 270.41.06

        WebGL Renderer
        NVIDIA Corporation -- GeForce 8600 GTS/PCI/SSE2 -- 3.3.0 NVIDIA 270.41.06

        GPU Accelerated Windows
        0/1

---

### Post by lovinglinux on 2011-08-24
This sounds really interesting:

> 
**From:** [http://www.conceivablytech.com/9058/business/firefox-gets-googles-spdy-chrome-gets-omnibox-sync](http://www.conceivablytech.com/9058/business/firefox-gets-googles-spdy-chrome-gets-omnibox-sync)

Mozilla&#8217;s Firefox team appears to have adjusted its pace to the new rapid release cycle and is working on a wave of new features that should make the browser race much more interesting again. Among the most interesting features are the previously covered Electrolysis as well as WebAPI and an integration of Google&#8217;s SPDY protocol. Google isn&#8217;t standing still either and is evolving the Chrome interface and recently added Omnibox syncing.

> 
**From:** [http://en.wikipedia.org/wiki/SPDY](http://en.wikipedia.org/wiki/SPDY)

SPDY (pronounced "speedy") is a TCP-based application-level protocol for transporting web content. It is proposed by Google and is being developed as one of their Chromium open-source projects. The SPDY white paper states that it is intended to "augment," rather than replace, HTTP.

The name "SPDY" is not an acronym. It comes from the word "SPeeDY" and represents speed through compression, which is one of the project's key goals.

The goal of SPDY is to reduce web page load time. This is achieved by prioritizing and multiplexing the transfer of several files so that only one connection per client is required. All transmissions are TLS encrypted and gzip compressed by design (in contrast to HTTP, where the headers are not compressed). Moreover, servers may hint or even push content instead of awaiting individual requests for each resource of a web page.

---

### Post by lovinglinux on 2011-08-25
See Firefox release schedule, published by Asa Dotzler on [his blog]("http://weblogs.mozillazine.org/asa/archives/2011/08/every_six_weeks.html"):

[[IMG]http://www4.picturepush.com/photo/a/6401952/640/6401952.png[/IMG]](http://picturepush.com/public/6401952)

---

### Post by SilverWave on 2011-08-27
> **lovinglinux said:**
> See Firefox release schedule, published by Asa Dotzler on [his blog]("http://weblogs.mozillazine.org/asa/archives/2011/08/every_six_weeks.html"):

[[IMG]http://www4.picturepush.com/photo/a/6401952/640/6401952.png[/IMG]]("http://picturepush.com/public/6401952")

Heh I wonder when we get to Firefox 999? :-)

LOL

---

### Post by SilverWave on 2011-08-27
[Why Rapid Releases Can Improve Stability]("http://home.kairo.at/blog/2011-08/why_rapid_releases_can_improve_stability")

Wow very well set out.

Spot on.

> In all this, we always have only six weeks of new development work  isolated in every such snapshot (or "version") and not more than a year  like previously, so pinpointing a cause gets easier. Then, we less of a  rush to get a feature into a specific version as there's another one  coming just six weeks earlier, so things will only go into the code in a  better thought-out state. Even more, we have switches of some way we  can throw to disable problematic code and give developers six more weeks  to get it into shape if needed. And over all that, we have roughly  three months (twelve weeks) of pure fixing and stabilization period on  every snapshot/version to get problems worked out, with different sizes  of testing audiences.

---

### Post by SilverWave on 2011-08-27
[...something surprising happened. We released Firefox 5, **and Firefox didn&#8217;t get crashier**.]("http://www.squarefree.com/2011/08/27/rapid-releases-and-crashes/")

> In the months before Firefox's first rapid release, one concern echoed throughout engineering: crashes.
  We had always relied on long stabilization periods to get crash rates  down. Firefox 4 would be our last high-stability release. We hoped  improvements on other aspects of quality would outweigh the decreased  stability.
  But then something surprising happened. We released Firefox 5, and *Firefox didn&#8217;t get crashier*.


  VersionCrashes per 100 active daily users
3.6.20     [1.8]("https://crash-stats.mozilla.com/products/Firefox/versions/3.6.20")
4.0.1       [1.6]("https://crash-stats.mozilla.com/products/Firefox/versions/4.0.1") 
5.0.1       [1.4]("https://crash-stats.mozilla.com/products/Firefox/versions/5.0.1")
6.0          [1.6]("https://crash-stats.mozilla.com/products/Firefox/versions/6.0")


Excellent :-)

---

### Post by SilverWave on 2011-08-27
> **SilverWave said:**
> [...something surprising happened. We released Firefox 5, **and Firefox didn&#8217;t get crashier**.]("http://www.squarefree.com/2011/08/27/rapid-releases-and-crashes/")

Still Firefox 7 and 8 will be the real confirmation as 5 was a test of the new rapid release system and didn&#8217;t contain much in the was of change.

---

### Post by SilverWave on 2011-08-27
[IMG]https://launchpad.net/@@/package-source[/IMG]                 firefox                                               7.0~b2+build1+nobinonly-0ubuntu0.11.04.1~mfn1

And on we go :-)

---

### Post by SilverWave on 2011-08-27
[IMG]https://launchpad.net/@@/package-source[/IMG]                 firefox-trunk                                               9.0~a1~hg20110826r75916+nobinonly-0ubuntu1~umd1~natty

9!

LOL.

---

### Post by SilverWave on 2011-08-29
[A web browser is not a document viewer, it is a full-blown programming environment](http://blog.mozilla.com/nnethercote/2011/08/29/browser-x-is-using-y-mb-of-memory-with-z-tabs-open-is-a-meaningless-observation/)

Interesting...

> Why do people so often make these meaningless “Y  MB of memory with Z tabs open” comments?  My theory is that it’s  because most people have no idea how complicated web browsers and web  pages are.  Mild experience with HTML authoring is endemic — heaps of  people have thrown together a basic web page, and it’s just a document  with with some structure and styling, right?  So they think the  difference between the website they wrote for their scout troop in 1997  (the one with the “under construction” animated GIF) and the front page  of [TechCrunch]("http://techcrunch.com/") is merely a difference of degree, not kind.
 They’re wrong.  For one, HTML and related  technologies are hugely more powerful and complicated now than they were  a few years ago.  Also, their scout troop website probably didn’t  contain multiple megabytes of JavaScript code tracking its visitors’  every move. A web browser is not a document viewer, it is a full-blown  programming environment with some very sophisticated text and graphical  capabilities.  A web page is not a document but a program.  Therefore,  the memory (and CPU) usage of different web pages varies dramatically.


Well said :-)

---

### Post by lovinglinux on 2011-08-30
[Iran May Have Acquired Google SSL Certificate, Prompts Browser Security Alerts]("http://ubuntuforums.org/showthread.php?t=1836052")

Users are urged to update their browsers. It seems Mozilla will release an update today.

More info and discussion at [http://ubuntuforums.org/showthread.php?t=1836052](http://ubuntuforums.org/showthread.php?t=1836052)

---

### Post by SilverWave on 2011-08-31
> **lovinglinux said:**
> [Iran May Have Acquired Google SSL Certificate, Prompts Browser Security Alerts]("http://ubuntuforums.org/showthread.php?t=1836052")

Users are urged to update their browsers. It seems Mozilla will release an update today.

More info and discussion at [http://ubuntuforums.org/showthread.php?t=1836052](http://ubuntuforums.org/showthread.php?t=1836052)

2 Min job :-)

[Deleting the DigiNotar CA certificate](http://support.mozilla.com/en-US/kb/deleting-diginotar-ca-cert)

---

### Post by lovinglinux on 2011-08-31
Very interesting article:

[Firefox 9 Gets 30% Boost In JavaScript Performance]("http://www.conceivablytech.com/9188/products/firefox-9-gets-30-boost-in-javascript-performance")

---

### Post by SilverWave on 2011-08-31
> **lovinglinux said:**
> Very interesting article:

[Firefox 9 Gets 30% Boost In JavaScript Performance]("http://www.conceivablytech.com/9188/products/firefox-9-gets-30-boost-in-javascript-performance")

Well that makes me think about running the nightly as my main browser again :-)

Lately I have just been running the latest Beta...

Or I could just wait 12 weeks? I love the Rapid release process for Firefox!

---

### Post by lovinglinux on 2011-08-31
> **SilverWave said:**
> Or I could just wait 12 weeks? I love the Rapid release process for Firefox!

Me too.

---

### Post by SilverWave on 2011-08-31
Off Topic but I am Upgrading to 11.10 Beta 1 _now_ :-)

See you on the other side ;-)

I suppose it is relevant as we will see how the new OS handles Firefox heh.

...

[EDIT]Everything is looking good so far :-D

---

### Post by SilverWave on 2011-09-03
Well this is new, when adding a PPA the PPA details are shown...

> silv@ion:~$  sudo add-apt-repository ppa:silverwave/testing3
You are about to add the following PPA to your system:
 One Nightly A Week #3 - Oneiric
 The latest firefox - No other packages.
One Nightly a week from ubuntu-mozilla-daily.
______________________________

One Nightly A Week #3 - Oneiric
One update a week.
firefox-trunk only
______________________________

sudo add-apt-repository ppa:silverwave/testing3
sudo apt-get update
sudo apt-get install firefox-trunk
______________________________

Disclaimer: Use at your own risk, no guarantees.
______________________________

Nightly – builds created out of the mozilla-central repository every night.
These are not qualified by QA

Aurora – builds created out of the mozilla-aurora repository, which is synced from mozilla-central every 6 weeks.
There is a small amount of QA at the start of the 6 week period before the updates are offered

Beta – builds created out of the mozilla-beta repository.
Qualified by QA as being of sufficient quality to release to beta users

Release – builds created out of the mozilla-release repository.
Qualified by QA as being of sufficient quality to release to hundreds of millions of people
 More info: [https://launchpad.net/~silverwave/+archive/testing3](https://launchpad.net/~silverwave/+archive/testing3)
Press [ENTER] to continue or ctrl-c to cancel adding it

Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /tmp/tmp.1tWNJIvte8 --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver hkp://keyserver.ubuntu.com:80/ --recv 4E0614F88874AF754D66E9C1EBD6062C6DE6117C
gpg: requesting key 6DE6117C from hkp server keyserver.ubuntu.com
gpg: key 6DE6117C: "Launchpad PPA for SilverWav" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
silv@ion:~$ 


I wonder if that is just 11.10?

---

### Post by ron999 on 2011-09-03
> **SilverWave said:**
> Off Topic but I am Upgrading to 11.10 Beta 1 _now_ :-)

See you on the other side ;-)

I suppose it is relevant as we will see how the new OS handles Firefox heh.

...

[EDIT]Everything is looking good so far :-D

Hi
Now that you've installed Beta 1, will you be able to update it to Beta 2, Release Candidate and Final Release using Update Manager?
Or will you need to un-install Beta 1 and start over?

---

### Post by SilverWave on 2011-09-03
Here is the latest just installed it on 11.10.

[IMG]https://launchpad.net/@@/package-source[/IMG]                 firefox-trunk                                               9.0~a1~hg20110901r76368+nobinonly-0ubuntu1~umd1

---

### Post by SilverWave on 2011-09-03
> **ron999 said:**
> Hi
Now that you've installed Beta 1, will you be able to update it to Beta 2, Release Candidate and Final Release using Update Manager?
Or will you need to un-install Beta 1 and start over?

Yes I just did:

Alt+F2 key combination and typed in:

```
update-manager -d
```

My latest posts on my blog are here:  [The best is yet to come… Posts Tagged ‘11.10’](http://silverwav.wordpress.com/tag/11-10/)

---

### Post by ron999 on 2011-09-03
> **SilverWave said:**
> Yes I just did:

Alt+F2 key combination and typed in:

```
update-manager -d
```

OK, I understand.
Like you said, "_updated_".
I thought that you meant you had re-installed 11.10 from CD.
(My bad):lolflag:

---

### Post by SilverWave on 2011-09-03
> **ron999 said:**
> OK, I understand.
Like you said, "_updated_".
I thought that you meant you had re-installed 11.10 from CD.
(My bad):lolflag:
Heh well at least you havent tried something daft like...

> un-installed zeitgeist-datahub hmm lets see how that plays out&#8230; :-)Hint: Don&#8217;t do it LOL.

---

### Post by ron999 on 2011-09-03
> **SilverWave said:**
> Heh well at least you havent tried something daft like...

I have a spare hard drive.
Maybe i will install Oneiric Beta 1 next week using mini.iso...
From here:- [http://archive.ubuntu.com/ubuntu/dists/oneiric/main/installer-i386/beta-1/images/netboot/]("http://archive.ubuntu.com/ubuntu/dists/oneiric/main/installer-i386/beta-1/images/netboot/")
Then build it up slowly from **gnome-core** and **gdm**.

---

### Post by SilverWave on 2011-09-03
7b3 installed with 11.10 

The live bookmarks on the toolbar are small as well...

Playing around with customize reveals that the bookmark toolbar is stuck at small icon size.

You can change the icon size for the other toolbars but not the bookmark toolbar...

Hmm this looks the same in the FF9a nightly but the text is a different font and size for the menus and rss feeds...

Maybe just a 7 beta thing?

/goes searching...
___
Mozilla/5.0 (X11; Linux x86_64; rv:7.0) Gecko/20100101 Firefox/7.0 ID:20110830191244

---

### Post by ron999 on 2011-09-04
Hi
For Firefox-beta with Natty Narwhal...
Do these two PPAs now provide exactly the same program?
ppa:silverwave/testing4
ppa:mozillateam/firefox-next
Or is one PPA better than the other for some reason.

---

### Post by SilverWave on 2011-09-05
> **ron999 said:**
> Hi
For Firefox-beta with Natty Narwhal...
Do these two PPAs now provide exactly the same program?
ppa:silverwave/testing4
ppa:mozillateam/firefox-next
Or is one PPA better than the other for some reason.

ppa:mozillateam/firefox-next is the official one that I copy from.

No diff except that mine has only Firefox in the ppa and no other packages.

---

### Post by ron999 on 2011-09-05
> **SilverWave said:**
> ppa:mozillateam/firefox-next is the official one that I copy from.
No diff except that mine has only Firefox in the ppa and no other packages.

Thanks.

---

### Post by chrisccoulson on 2011-09-05
Well, there is a slight difference. You can report bugs from the packages in the official PPA, as we whitelist the official PPA source in apport. Reporting bugs from other PPA's will fail with a "This is not a genuine Ubuntu package" error

---

### Post by ron999 on 2011-09-05
> **chrisccoulson said:**
> Well, there is a slight difference. You can report bugs from the packages in the official PPA, as we whitelist the official PPA source in apport.
Thanks.

---

### Post by SilverWave on 2011-09-07
Beta 4 is out :-)

[[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox - 7.0~b4+build2+nobinonly-0ubuntu0.11.04.1~mfn1       ]("https://launchpad.net/%7Esilverwave/+archive/testing4/+sourcepub/1928917/+listing-archive-extra")

---

### Post by SilverWave on 2011-09-10
Beta 5 is out :-)

[[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox - 7.0~b5+build1+nobinonly-0ubuntu0.11.04.1~mfn1       ]("https://launchpad.net/%7Emozillateam/+archive/firefox-next/+sourcepub/1932294/+listing-archive-extra")

---

### Post by SilverWave on 2011-09-10
Changes for the versions:
Installed version: 9.0~a1~hg20110901r76368+nobinonly-0ubuntu1~umd1
Available version: 9.0~a1~hg20110908r76769-0ubuntu1~umd1

[[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox-trunk - 9.0~a1~hg20110908r76769-0ubuntu1~umd1       ]("https://launchpad.net/%7Esilverwave/+archive/testing3/+sourcepub/1934201/+listing-archive-extra")

For Oneiric and Natty.

[[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox-trunk - 9.0~a1~hg20110907r76644-0ubuntu1~umd1~lucid       ]("https://launchpad.net/%7Esilverwave/+archive/testing0/+sourcepub/1934210/+listing-archive-extra")

For Maverick and Lucid.

> 
 -- Chris Coulson
* Drop the 'nobinonly' suffix from the version number. All this really does     is make the version number longer without adding any useful information,

---

### Post by SilverWave on 2011-09-10
> **ron999 said:**
> I have a spare hard drive.
Maybe i will install Oneiric Beta 1 next week using mini.iso...
From here:- [http://archive.ubuntu.com/ubuntu/dists/oneiric/main/installer-i386/beta-1/images/netboot/](http://archive.ubuntu.com/ubuntu/dists/oneiric/main/installer-i386/beta-1/images/netboot/)
Then build it up slowly from **gnome-core** and **gdm**.

Bit of an off topic post but if you are into Firefox then you are probably privacy conscious and so this may be interesting...

...and Zeitgeist does log "websites visits"...

> 
Is Zeitgeist logging too much information about you?

     Quote:
                                                 "Zeitgeist is a service which logs the user&#8217;s activities and events   (files opened, websites visits, conversations held with other people,   etc.) and makes relevant information available to other applications. It   is able to establish relationships between items based on similarity   and usage patterns."[How to Delete the Zeitgeist History and Set Privacy Defaults ]("http://ubuntuforums.org/showthread.php?p=11221598#post11221598")

---

### Post by SilverWave on 2011-09-16
Oneiric & Natty
[[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox-trunk - 9.0~a1~hg20110915r77009-0ubuntu1~umd1       ]("https://launchpad.net/%7Esilverwave/+archive/testing3/+sourcepub/1944221/+listing-archive-extra")

Maverick & Lucid
[[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox-trunk - 9.0~a1~hg20110913r76916-0ubuntu1~umd1~maverick       ]("https://launchpad.net/%7Esilverwave/+archive/testing2/+sourcepub/1944225/+listing-archive-extra")

---

### Post by SilverWave on 2011-09-19
[[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox - 7.0~b6+build1+nobinonly-0ubuntu0.11.04.1~mfn1       ]("https://launchpad.net/%7Esilverwave/+archive/testing4/+sourcepub/1947245/+listing-archive-extra")

---

### Post by SilverWave on 2011-09-22
Interesting...

[Firefox 8 or 9 May Be an Extended Support Release and Receive Updates for a Year](http://news.softpedia.com/news/Firefox-8-or-9-May-Be-an-Extended-Support-Release-and-Receive-Security-Updates-for-a-Year-223120.shtml)

Details here:

[Enterprise/Firefox/ExtendedSupport:Proposal](https://wiki.mozilla.org/Enterprise/Firefox/ExtendedSupport:Proposal)

> The ESR is specifically targeted at groups looking to deploy it within a  managed environment. It is not intended for use by individuals, nor as a  method to mitigate compatibility issues with addons or other software.  Public (re)distribution of Mozilla-branded versions of the ESR will not  be permitted.

---

### Post by SilverWave on 2011-09-22
[A five week release cycle?](https://groups.google.com/forum/#!topic/mozilla.dev.planning/mvVweF8xQRw)

---

### Post by SilverWave on 2011-09-22
[[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox-trunk - 9.0~a1~hg20110922r77296-0ubuntu1~umd1]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+sourcepub/1951139/+listing-archive-extra")
[IMG]https://launchpad.net/@@/package-source[/IMG]                 firefox-trunk                                               9.0~a1~hg20110920r77186-0ubuntu1~umd2~lucid

---

### Post by SilverWave on 2011-09-24
Interesting...

[Also added is MultiarchSpec that lets you install 32-bit libraries and application packages on 64-bit systems.]("http://www.theregister.co.uk/2011/09/23/ubuntu_11_10_second_beta/")

[MultiarchSpec]("https://wiki.ubuntu.com/MultiarchSpec")

> **Summary**

 Integrate  support for cross-architecture installation of binary packages  (particularly i386<->amd64, but also other combinations) in dpkg  and apt. 
 
**Release Note**

 Ubuntu  11.04 introduces support for installing packages from multiple  architectures on a single system.  This makes a wider array of 32-bit  applications available to users of 64-bit Ubuntu. 
 
**Rationale**

 The  current handling of 32-bit software on the amd64 architecture is  unwieldy in the extreme.  A handful of libraries are packaged as  "biarch" packages, building -386 variants using gcc -m32; most do not, and as a result are only available if they're included in ia32-libs,  a monstrous source package that has to be updated to be kept in sync  with each change to one of the component libraries, and now contains so  many libraries that its "source" package (consisting primarily of copies  of the i386 binary packages) weighs in as a 550MB tarball.   Furthermore, many of these libraries have to be patched to specially  handle running in a 64-bit environment because they load various plugins  from a system path that is already occupied by the 32-bit library,  resulting in added complexity in the code due to special-casing. 
In all cases, the libraries (and some executables) have to be repackaged as amd64 packages, because dpkg and apt do not support sensible handling of cross-installation of i386 packages.  This consumes archive space and developer time on an ongoing basis. hmm... I wonder what the implications are for Firefox packages and plug-ins?

---

### Post by SilverWave on 2011-09-24
Interesting...

[Ubuntu Mozilla Security Team]("https://launchpad.net/%7Eubuntu-mozilla-security/+archive/ppa/+packages?field.name_filter=firefox&field.status_filter=published&field.series_filter=")

[[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox - 7.0+build2+nobinonly-0ubuntu0.11.04.1       ]("https://launchpad.net/%7Eubuntu-mozilla-security/+archive/ppa/+sourcepub/1953043/+listing-archive-extra")                                  [(changes file)]("https://launchpad.net/%7Eubuntu-mozilla-security/+archive/ppa/+files/firefox_7.0%2Bbuild2%2Bnobinonly-0ubuntu0.11.04.1_source.changes")                                 [micahg]("https://launchpad.net/%7Emicahg")                        2011-09-23     Published     Natty     Web            [IMG]https://launchpad.net/@@/yes[/IMG]

---

### Post by SilverWave on 2011-09-24
The new rapid release is having some knock-on effects re add-ons review times I see:

> [here]("https://groups.google.com/forum/#%21topic/mozilla.dev.planning/mvVweF8xQRw")

     Sep 21 (3 days ago) 
        - show quoted text -

That'd be definitely a big help for the AMO Editors team. More  
realistically, though, we just need to bring the queues back down to the  
acceptable levels, which are 10 days for full nominations, 5 days for  
updates and 3 days for preliminary reviews. 

We're working on some other measures to reduce waiting times, like  
hiring a full time editor who joined us last week, but it is unclear at  
the moment if this will be sufficient. 

- Jorge 

It looks as if Mozilla is prepared to put their money behind a new hire to solve this, sweet. :-)

Firefox is just as good as its Add-ons.

---

### Post by SilverWave on 2011-09-27
From the Stable PPA
Lucid
[[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox - 7.0+build2+nobinonly-0ubuntu0.10.04.1~mfs1]("https://launchpad.net/%7Emozillateam/+archive/firefox-stable/+sourcepub/1952739/+listing-archive-extra")
Maverick
[[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox - 7.0+build2+nobinonly-0ubuntu0.10.10.1~mfs1       ]("https://launchpad.net/%7Emozillateam/+archive/firefox-stable/+sourcepub/1952738/+listing-archive-extra")

From the Security PPA
Natty
      [         [IMG]https://launchpad.net/@@/package-source[/IMG]         firefox - 7.0+build2+nobinonly-0ubuntu0.11.04.1       ]("https://launchpad.net/%7Eubuntu-mozilla-security/+archive/ppa/+sourcepub/1953043/+listing-archive-extra")

---

### Post by SilverWave on 2011-09-29
[[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox - 8.0~b1+build1-0ubuntu0.11.10.1~mfn2       ]("https://launchpad.net/%7Emozillateam/+archive/firefox-next/+sourcepub/1961324/+listing-archive-extra")

---

### Post by SilverWave on 2011-09-29
Oneiric
[[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox-trunk - 10.0~a1~hg20110928r77757-0ubuntu1~umd1]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+sourcepub/1960845/+listing-archive-extra")
Natty
[[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox-trunk - 10.0~a1~hg20110928r77757-0ubuntu1~umd1~natty       ]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+sourcepub/1960846/+listing-archive-extra")

---

### Post by SilverWave on 2011-10-01
[[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox - 8.0~b1+build1-0ubuntu0.11.10.1~mfn2       ]("https://launchpad.net/%7Emozillateam/+archive/firefox-next/+sourcepub/1961324/+listing-archive-extra")                  
[[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox - 8.0~b1+build1-0ubuntu0.11.04.1~mfn2       ]("https://launchpad.net/%7Emozillateam/+archive/firefox-next/+sourcepub/1961325/+listing-archive-extra")                  
                                        [         [IMG]https://launchpad.net/@@/package-source[/IMG]         firefox - 8.0~b1+build1-0ubuntu0.10.10.1~mfn2       ]("https://launchpad.net/%7Emozillateam/+archive/firefox-next/+sourcepub/1961330/+listing-archive-extra")                  
    [[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox - 8.0~b1+build1-0ubuntu0.10.04.1~mfn2]("https://launchpad.net/%7Emozillateam/+archive/firefox-next/+sourcepub/1961359/+listing-archive-extra")

*[I]Also Added a PPA for the new Oneiric Beta.*[/I]

---

### Post by SilverWave on 2011-10-01
Beta  upgrade wizard is very nice (ff7.0 to ff8.0b1) - Screenshots.

---

### Post by SilverWave on 2011-10-10
[         [IMG]https://launchpad.net/@@/package-source[/IMG]         firefox - 8.0~b2+build2-0ubuntu0.11.10.1~mfn1]("https://launchpad.net/%7Emozillateam/+archive/firefox-next/+sourcepub/1974930/+listing-archive-extra")

Nice. :-)

---

### Post by SilverWave on 2011-10-10
[[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox-trunk - 10.0~a1~hg20111009r78410-0ubuntu1~umd1]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+sourcepub/1976601/+listing-archive-extra")

Lastest and greatest.

---

### Post by zika on 2011-10-11
10.0a1 (2011-10-11) crashes repeatedly, as soon as I try to open page... Am I alone?
(Reverted to 10.0a1 (2011-10-10), steady as a rock, as it was for days...)

Update: [http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-trunk/firefox-10.0a1.en-US.linux-x86_64.tar.bz2](http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-trunk/firefox-10.0a1.en-US.linux-x86_64.tar.bz2) works like clockwork... Also 10.0a1 (2011-10-11)...
Strange... ;)
(After some playing with latest-trunk, firefox-trunk settled down and, now, works as it should... even more strange... ;))

---

### Post by SilverWave on 2011-10-11
> **zika said:**
> 10.0a1 (2011-10-11) crashes repeatedly, as soon as I try to open page... Am I alone?
(Reverted to 10.0a1 (2011-10-10), steady as a rock, as it was for days...)

Update: [http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-trunk/firefox-10.0a1.en-US.linux-x86_64.tar.bz2](http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-trunk/firefox-10.0a1.en-US.linux-x86_64.tar.bz2) works like clockwork... Also 10.0a1 (2011-10-11)...
Strange... ;)
(After some playing with latest-trunk, firefox-trunk settled down and, now, works as it should... even more strange... ;))

oneiric works fine for me...

ah... just checked I am using [firefox-trunk - 10.0~a1~hg20111009r78410-0ubuntu1~umd1]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+sourcepub/1976601/+listing-archive-extra")

User Agent:
            Mozilla/5.0 (X11; Linux x86_64; rv:10.0a1) Gecko/20111010 Firefox/10.0a1

---

### Post by SilverWave on 2011-10-11
> **zika said:**
> 10.0a1 (2011-10-11) 
(After some playing with latest-trunk, firefox-trunk settled down and, now, works as it should... even more strange... ;))


How odd :/

---

### Post by SilverWave on 2011-10-11
> **zika said:**
> 10.0a1 (2011-10-11) crashes repeatedly, as soon as I try to open page... Am I alone?
(Reverted to 10.0a1 (2011-10-10), steady as a rock, as it was for days...)

Update: [http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-trunk/firefox-10.0a1.en-US.linux-x86_64.tar.bz2](http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-trunk/firefox-10.0a1.en-US.linux-x86_64.tar.bz2) works like clockwork... Also 10.0a1 (2011-10-11)...
Strange... ;)
(After some playing with latest-trunk, firefox-trunk settled down and, now, works as it should... even more strange... ;))

Hmm looking at chris's ppa there were a lot of failed builds up to the last couple...

  [         10.0~a1~hg20111010r78496-0ubuntu1~umd2       ]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+sourcepub/1978275/+listing-archive-extra")                                  [(changes file)]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+files/firefox-trunk_10.0%7Ea1%7Ehg20111010r78496-0ubuntu1%7Eumd2_source.changes")                                 [chrisbot]("https://launchpad.net/%7Echrisbot")                        9 hours ago     Superseded     Oneiric     Web            [IMG]https://launchpad.net/@@/yes[/IMG] [         10.0~a1~hg20111010r78496-0ubuntu1~umd1       ]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+sourcepub/1977878/+listing-archive-extra")                                  [(changes file)]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+files/firefox-trunk_10.0%7Ea1%7Ehg20111010r78496-0ubuntu1%7Eumd1_source.changes")                                 [chrisbot]("https://launchpad.net/%7Echrisbot")                        18 hours ago     Superseded     Oneiric     Web            [IMG]https://launchpad.net/@@/yes[/IMG] [         10.0~a1~hg20111009r78410-0ubuntu1~umd1       ]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+sourcepub/1976601/+listing-archive-extra")                                  [(changes file)]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+files/firefox-trunk_10.0%7Ea1%7Ehg20111009r78410-0ubuntu1%7Eumd1_source.changes")                                 [chrisbot]("https://launchpad.net/%7Echrisbot")                        2011-10-10     Superseded     Oneiric     Web            [IMG]https://launchpad.net/@@/yes[/IMG] [         10.0~a1~hg20111008r78356-0ubuntu1~umd1       ]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+sourcepub/1975346/+listing-archive-extra")                                  [(changes file)]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+files/firefox-trunk_10.0%7Ea1%7Ehg20111008r78356-0ubuntu1%7Eumd1_source.changes")                                 [chrisbot]("https://launchpad.net/%7Echrisbot")                        2011-10-09     Superseded     Oneiric     Web            [IMG]https://launchpad.net/@@/yes[/IMG] [         10.0~a1~hg20111007r78350-0ubuntu1~umd1       ]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+sourcepub/1973241/+listing-archive-extra")                                  [(changes file)]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+files/firefox-trunk_10.0%7Ea1%7Ehg20111007r78350-0ubuntu1%7Eumd1_source.changes")                                 [chrisbot]("https://launchpad.net/%7Echrisbot")                        2011-10-08     Superseded     Oneiric     Web            [IMG]https://launchpad.net/@@/no[/IMG]                [           amd64         ]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+build/2830292")                       [           i386 ]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+build/2830293")[         10.0~a1~hg20111007r78227-0ubuntu1~umd3       ]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+sourcepub/1973024/+listing-archive-extra")                                  [(changes file)]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+files/firefox-trunk_10.0%7Ea1%7Ehg20111007r78227-0ubuntu1%7Eumd3_source.changes")                                 [chrisbot]("https://launchpad.net/%7Echrisbot")                        2011-10-07     Superseded     Oneiric     Web **X**                [           amd64         ]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+build/2829937")                       [           i386 ]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+build/2829938")[         10.0~a1~hg20111007r78227-0ubuntu1~umd2       ]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+sourcepub/1972828/+listing-archive-extra")                                  [(changes file)]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+files/firefox-trunk_10.0%7Ea1%7Ehg20111007r78227-0ubuntu1%7Eumd2_source.changes")                                 [chrisbot]("https://launchpad.net/%7Echrisbot")                        2011-10-07     Superseded     Oneiric     Web **X**                [           amd64         ]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+build/2829646")                       [           i386 ]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+build/2829647")[ 10.0~a1~hg20111007r78227-0ubuntu1~umd1       ]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+sourcepub/1971213/+listing-archive-extra")                                  [(changes file)]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+files/firefox-trunk_10.0%7Ea1%7Ehg20111007r78227-0ubuntu1%7Eumd1_source.changes")                                 [chrisbot]("https://launchpad.net/%7Echrisbot")                        2011-10-07     Superseded     Oneiric     Web **X**                [           amd64         ]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+build/2827609")                       [           i386 ]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+build/2827610")[10.0~a1~hg20111006r78161-0ubuntu1~umd1       ]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+sourcepub/1969908/+listing-archive-extra")                                  [(changes file)]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+files/firefox-trunk_10.0%7Ea1%7Ehg20111006r78161-0ubuntu1%7Eumd1_source.changes")                                 [chrisbot]("https://launchpad.net/%7Echrisbot")                        2011-10-06     Superseded     Oneiric     Web **X**                [           amd64         ]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+build/2825805")                       [           i386]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+build/2825806")[ 10.0~a1~hg20111004r78117-0ubuntu1~umd1       ]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+sourcepub/1968336/+listing-archive-extra")                                  [(changes file)]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+files/firefox-trunk_10.0%7Ea1%7Ehg20111004r78117-0ubuntu1%7Eumd1_source.changes")                                 [chrisbot]("https://launchpad.net/%7Echrisbot")                        2011-10-05     Superseded     Oneiric     Web **X**                [           amd64         ]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+build/2823621")                       [           i386]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+build/2823622")[ 10.0~a1~hg20111004r78044-0ubuntu1~umd1       ]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+sourcepub/1966731/+listing-archive-extra")                                  [(changes file)]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+files/firefox-trunk_10.0%7Ea1%7Ehg20111004r78044-0ubuntu1%7Eumd1_source.changes")                                 [chrisbot]("https://launchpad.net/%7Echrisbot")                        2011-10-04     Superseded     Oneiric     Web **X**                [           amd64         ]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+build/2821435")                       [           i386]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+build/2821436")[ 10.0~a1~hg20111002r77971-0ubuntu1~umd1       ]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+sourcepub/1965405/+listing-archive-extra")                                  [(changes file)]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+files/firefox-trunk_10.0%7Ea1%7Ehg20111002r77971-0ubuntu1%7Eumd1_source.changes")                                 [chrisbot]("https://launchpad.net/%7Echrisbot")                        2011-10-03     Superseded     Oneiric     Web            **X **[amd64         ]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+build/2819374")                       [           i386]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+build/2819375")[ 10.0~a1~hg20111001r77958-0ubuntu1~umd1       ]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+sourcepub/1964529/+listing-archive-extra")                                  [(changes file)]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+files/firefox-trunk_10.0%7Ea1%7Ehg20111001r77958-0ubuntu1%7Eumd1_source.changes")                                 [chrisbot]("https://launchpad.net/%7Echrisbot")                        2011-10-02     Superseded     Oneiric     Web **X**                [           amd64         ]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+build/2818071")                       [           i386]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+build/2818072")[ 10.0~a1~hg20111001r77918-0ubuntu1~umd1       ]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+sourcepub/1963501/+listing-archive-extra")                                  [(changes file)]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+files/firefox-trunk_10.0%7Ea1%7Ehg20111001r77918-0ubuntu1%7Eumd1_source.changes")                                 [chrisbot]("https://launchpad.net/%7Echrisbot")                        2011-10-01     Superseded     Oneiric     Web **X**                [           amd64         ]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+build/2816762")                       [           i386]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+build/2816763")[ 10.0~a1~hg20110930r77869-0ubuntu1~umd1       ]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+sourcepub/1962380/+listing-archive-extra")                                  [(changes file)]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+files/firefox-trunk_10.0%7Ea1%7Ehg20110930r77869-0ubuntu1%7Eumd1_source.changes")                                 [chrisbot]("https://launchpad.net/%7Echrisbot")                        2011-09-30     Superseded     Oneiric     Web **X**                [           amd64         ]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+build/2815095")                       [           i386]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+build/2815096")[ 10.0~a1~hg20110928r77757-0ubuntu1~umd1       ]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+sourcepub/1960845/+listing-archive-extra")                                  [(changes file)]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+files/firefox-trunk_10.0%7Ea1%7Ehg20110928r77757-0ubuntu1%7Eumd1_source.changes")                                 [chrisbot]("https://launchpad.net/%7Echrisbot")                        2011-09-29     Superseded     Oneiric     Web            [IMG]https://launchpad.net/@@/yes[/IMG]

---

### Post by SilverWave on 2011-10-14
[[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox - 8.0~b3+build1-0ubuntu0.11.10.1~mfn1       ]("https://launchpad.net/%7Esilverwave/+archive/testing7/+sourcepub/2002458/+listing-archive-extra")

:-)

---

### Post by SilverWave on 2011-10-16
**Oneiric & Natty**

[[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox-trunk - 10.0~a1~hg20111014r78748-0ubuntu1~umd1]("https://launchpad.net/%7Esilverwave/+archive/testing3/+sourcepub/2005628/+listing-archive-extra")
[[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox-trunk - 10.0~a1~hg20111014r78748-0ubuntu1~umd1~natty       ]("https://launchpad.net/%7Esilverwave/+archive/testing1/+sourcepub/2005629/+listing-archive-extra")

**Maverick & Lucid**

[[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox-trunk - 10.0~a1~hg20111011r78571-0ubuntu1~umd1~maverick       ]("https://launchpad.net/%7Esilverwave/+archive/testing2/+sourcepub/2005641/+listing-archive-extra")
[[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox-trunk - 10.0~a1~hg20111011r78571-0ubuntu1~umd1~lucid       ]("https://launchpad.net/%7Esilverwave/+archive/testing0/+sourcepub/2005642/+listing-archive-extra")

---

### Post by SilverWave on 2011-10-17
[Native Android GUI developing for Firefox]("http://www.h-online.com/open/news/item/Native-Android-GUI-developing-for-Firefox-1362076.html")

Well that’s interesting.

I wonder if the could just go web-kit next ;-)

---

### Post by SilverWave on 2011-10-22
[[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox - 8.0~b4+build1-0ubuntu0.11.10.1~mfn1]("https://launchpad.net/%7Esilverwave/+archive/testing7/+sourcepub/2035071/+listing-archive-extra")

:-)

---

### Post by SilverWave on 2011-10-23
> **SilverWave said:**
> [[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox - 8.0~b4+build1-0ubuntu0.11.10.1~mfn1]("https://launchpad.net/%7Esilverwave/+archive/testing7/+sourcepub/2035071/+listing-archive-extra")

:-)

**Sound problem caused by npviewer.bin**

I was experiencing issues when playing video with Movie Player and mplayer.

I initially thought it was caused by pulseaudio but traced it down to Firefox and npviewer.bin usage.

If I kill npviewer.bin the sound works.

Will look for a bug to report it under.

---

### Post by SilverWave on 2011-10-27
Well we will see if the back-out  strategy for the rapid release actually works in real life:

[https://bugzilla.mozilla.org/show_bug.cgi?id=690227](https://bugzilla.mozilla.org/show_bug.cgi?id=690227)


Looks like its been backed out...

Yeah!

---

### Post by SilverWave on 2011-10-27
[[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox-trunk - 10.0~a1~hg20111027r79248-0ubuntu1~umd1]("https://launchpad.net/%7Esilverwave/+archive/testing3/+sourcepub/2045607/+listing-archive-extra")

Hopefully this one will have the **tab drag/detach animations** backed out, allowing me to use Tree Style Tabs in peace :-D

---

### Post by SilverWave on 2011-10-27
> **SilverWave said:**
> [[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox-trunk - 10.0~a1~hg20111027r79248-0ubuntu1~umd1]("https://launchpad.net/%7Esilverwave/+archive/testing3/+sourcepub/2045607/+listing-archive-extra")

Hopefully this one will have the **tab drag/detach animations** backed out, allowing me to use Tree Style Tabs in peace :-D

Yes! All now working great :-)

WHOOT!

---

### Post by SilverWave on 2011-11-04
[[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox - 8.0~b6+build2-0ubuntu0.11.10.1~mfn1]("https://launchpad.net/%7Emozillateam/+archive/firefox-next/+sourcepub/2056372/+listing-archive-extra")

Nice :-)

Almost ready for release.

---

### Post by SilverWave on 2011-11-04
> **SilverWave said:**
> [[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox - 8.0~b6+build2-0ubuntu0.11.10.1~mfn1]("https://launchpad.net/%7Emozillateam/+archive/firefox-next/+sourcepub/2056372/+listing-archive-extra")

Nice :-)

Almost ready for release.

No explanation for the jump from b4 to b6...

---

### Post by SilverWave on 2011-11-04
[[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox-trunk - 10.0~a1~hg20111104r79707-0ubuntu1~umd1       ]("https://launchpad.net/%7Esilverwave/+archive/testing3/+sourcepub/2059152/+listing-archive-extra")

---

### Post by SilverWave on 2011-11-08
> Just a note now that I see how the new rapid release for Firefox is actually working in practice...

My PPA's will be updated to the latest Beta's as they come out.
At the end of the cycle they will be updated to the latest release firefox.

So if you add a Beta PPA from the list below, you will always have the latest FF9, FF10 etc., as soon as they are available.

I think that the Beta's, at least for me, represent the best reward (in   running the latest Firefox) for the least risk (very stable and   polished).[[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox - 8.0+build1-0ubuntu0.11.10.2]("https://launchpad.net/%7Eubuntu-mozilla-security/+archive/ppa/+sourcepub/2064753/+listing-archive-extra")
[[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox - 8.0+build1-0ubuntu0.11.04.2       ]("https://launchpad.net/%7Eubuntu-mozilla-security/+archive/ppa/+sourcepub/2064760/+listing-archive-extra")

Updated the Beta PPA's so that they have the final release package ASAP.

---

### Post by SilverWave on 2011-11-08
Changes for the versions:
Installed version: 8.0~b6+build2-0ubuntu0.11.10.1~mfn1
Available version: 8.0+build1-0ubuntu0.11.10.2

This update does not come from a source that supports changelogs.

---

### Post by SilverWave on 2011-11-08
[[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox - 8.0+build1-0ubuntu0.10.10.1~mfs1       ]("https://launchpad.net/%7Emozillateam/+archive/firefox-stable/+sourcepub/2063277/+listing-archive-extra")

[[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox - 8.0+build1-0ubuntu0.10.04.1~mfs1]("https://launchpad.net/%7Emozillateam/+archive/firefox-stable/+sourcepub/2063278/+listing-archive-extra")

Still Pending ATM

---

### Post by SilverWave on 2011-11-12
[         [IMG]https://launchpad.net/@@/package-source[/IMG]         firefox-trunk - 11.0~a1~hg20111111r80170-0ubuntu1~umd1       ]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+sourcepub/2071906/+listing-archive-extra")                                  [(changes file)]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+files/firefox-trunk_11.0%7Ea1%7Ehg20111111r80170-0ubuntu1%7Eumd1_source.changes")                                 [chrisbot]("https://launchpad.net/%7Echrisbot")                        5 hours ago     Published     Oneiric     Web            [IMG]https://launchpad.net/@@/no[/IMG]                [           amd64         ]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+build/2919924")                       [           i386         ]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+build/2919925")






[]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+build/2919925")

---

### Post by SilverWave on 2011-11-12
> **SilverWave said:**
> [[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox - 8.0+build1-0ubuntu0.10.10.1~mfs1       ]("https://launchpad.net/%7Emozillateam/+archive/firefox-stable/+sourcepub/2063277/+listing-archive-extra")

[[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox - 8.0+build1-0ubuntu0.10.04.1~mfs1]("https://launchpad.net/%7Emozillateam/+archive/firefox-stable/+sourcepub/2063278/+listing-archive-extra")

Still Pending ATM

Still set to "Publishing has been disabled for this archive"

Weird.

---

### Post by lovinglinux on 2011-11-12
> **SilverWave said:**
> Still set to "Publishing has been disabled for this archive"

Weird.

They found some issues and are holding back the upgrade.

---

### Post by SilverWave on 2011-11-12
> **lovinglinux said:**
> They found some issues and are holding back the upgrade.

Ah that explains it then.

Thanks for the update :-)

---

### Post by SilverWave on 2011-11-16
[Multi-Process Firefox Project Put on Hold]("http://news.softpedia.com/news/Multi-Process-Firefox-Project-Put-on-Hold-235032.shtml")
> 
"[Mozilla made] a decision to put the Electrolysis  initiative on hold for the foreseeable future and focus on other  initiatives aimed at improving responsiveness in the browser," About  lmandel, Electrolysis' program manager [**explained**]("http://lawrencemandel.com/2011/11/15/update-on-multi-process-firefox-electrolysis-development/").

---

### Post by SilverWave on 2011-11-16
[[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox - 9.0~b1+build1-0ubuntu0.11.10.1~mfn1]("https://launchpad.net/%7Emozillateam/+archive/firefox-next/+sourcepub/2077708/+listing-archive-extra")

*Whoot!* - out at last :-)

---

### Post by SilverWave on 2011-11-16
[[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox-trunk - 11.0~a1~hg20111115r80292-0ubuntu1~umd1]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+sourcepub/2078007/+listing-archive-extra")

Yes!

---

### Post by SilverWave on 2011-11-16
> **SilverWave said:**
> [[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox - 9.0~b1+build1-0ubuntu0.11.10.1~mfn1]("https://launchpad.net/%7Emozillateam/+archive/firefox-next/+sourcepub/2077708/+listing-archive-extra")

*Whoot!* - out at last :-)

> Changes for the versions:
Installed version: 8.0+build1-0ubuntu0.11.10.2
Available version: 9.0~b1+build1-0ubuntu0.11.10.1~mfn1

This update does not come from a source that supports changelogs.


Looking good so far :-)

---

### Post by SilverWave on 2011-11-19
**[Solving Firefox&#8217;s add-on compatibility problem]("http://theunfocused.net/2011/11/19/solving-firefoxs-add-on-compatibility-problem/")**

> **How does this work? The gritty details.**

 [LEFT][COLOR=#000000][FONT=arial][LEFT]The problem with incompatible add-ons is that most of them **are**  actually compatible - they just don't know it. Unfortunately, blindly  enabling all add-ons will enable some that are really are just  incompatible, which will end in something breaking. So we needed a way  to detect which add-ons would most likely be affected by incompatible  changes to new versions of Firefox.[/LEFT]
[/FONT][/COLOR][/LEFT]
 [LEFT][COLOR=#000000][FONT=arial][LEFT]Assuming the extensions.strictCompatibility preference is set to false,  add-ons will use the new compatible-by-default behavior. However, there  are several reasons the Add-ons Manager will revert to using the old  method of strict compatibility checking for a given add-on:[/LEFT]
[/FONT][/COLOR][/LEFT]
 
[LIST]
[*]The add-on author chose to opt-in to strict compatibility checking by adding <em:strictCompatibility>true</em:strictCompatibility> to the add-on's [install.rdf]("https://developer.mozilla.org/en/Install_Manifests")
[*]The  add-on has been tested and determined to not be compatible with that  version of Firefox (the Add-ons Manager gets this information from [AMO]("https://addons.mozilla.org/"))
[*]The add-on uses a binary component
[*]The  add-on hasn't been updated in an extremely long time (the compatibility  data needs to state that it is at least compatible with Firefox 4, or  Toolkit 2.0)
[*]The  add-on declares that is it only compatible with future versions of  Firefox (we assume that add-ons are not backwards-compatible)
[/LIST]


> [here is the] [project]("https://wiki.mozilla.org/Features/Add-ons/Add-ons_Default_to_Compatible")  to fix it. The end result will be that most add-ons will automatically  be compatible with Firefox, starting with (hopefully) Firefox 10.

---

### Post by SilverWave on 2011-11-19
[Mozilla makes progress on Firefox silent updates]("http://www.computerworld.com/s/article/9222011/Mozilla_makes_progress_on_Firefox_silent_updates")
> 
Computerworld -  Mozilla is making progress on adding a silent update mechanism to  Firefox, with plans to integrate the new service in Firefox 10 early  next year.

But one of the developers working on the feature cautioned that silent update might slip.


> Akhgari's part of the project is to minimize the amount of time it takes Firefox to launch after downloading an update.
  To do so, he's come up with a way to stage the downloaded update --  essentially an updated copy of Firefox -- in a separate Windows  directory, then swap the older edition with the newer one the next time  the user starts up Firefox.


---

### Post by SilverWave on 2011-11-27
[Improving font size readability on Firefox for Android]("http://dbaron.org/log/20111126-font-inflation")

Yeah well I had given up on using Firefox on my android in the foreseeable future but this looks promising.

---

### Post by SilverWave on 2011-11-27
[[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox - 9.0~b3+build1-0ubuntu0.11.10.1~mfn1       ]("https://launchpad.net/%7Emozillateam/+archive/firefox-next/+sourcepub/2092092/+listing-archive-extra")

---

### Post by SilverWave on 2011-11-27
[[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox-trunk - 11.0~a1~hg20111126r80830-0ubuntu1~umd1~oneiric]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+sourcepub/2095245/+listing-archive-extra")

Nice.

---

### Post by SilverWave on 2011-12-04
[[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox-trunk - 11.0~a1~hg20111203r81355-0ubuntu1~umd1~oneiric]("https://launchpad.net/%7Esilverwave/+archive/testing3/+sourcepub/2106938/+listing-archive-extra")

:-)

---

### Post by SilverWave on 2011-12-10
[[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox - 9.0~b4+build1-0ubuntu0.11.10.1~mfn1       ]("https://launchpad.net/%7Esilverwave/+archive/testing7/+sourcepub/2116954/+listing-archive-extra")

---

### Post by SilverWave on 2011-12-10
[[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox-trunk - 11.0~a1~hg20111205r81460-0ubuntu1~umd1~oneiric       ]("https://launchpad.net/%7Esilverwave/+archive/testing3/+sourcepub/2116964/+listing-archive-extra")

The rest are all all 81355

[[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox-trunk - 11.0~a1~hg20111203r81355-0ubuntu1~umd1       ]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+sourcepub/2106190/+listing-archive-extra")

---

### Post by lovinglinux on 2011-12-14
Add-ons in Aurora are now considered compatible by default!!!!!

[http://blog.mozilla.com/addons/2011/12/12/help-test-default-compatibility-for-add-ons-on-aurora/](http://blog.mozilla.com/addons/2011/12/12/help-test-default-compatibility-for-add-ons-on-aurora/)

No more need for the Add-on Compatibility Reporter, unless you want to report add-ons that don't work.

If you want the old behavior, enter **about:config**, search for **extensions.strictCompatibility** and double click it to set it to true.

---

### Post by SilverWave on 2011-12-15
> **lovinglinux said:**
> Add-ons in Aurora are now considered compatible by default!!!!!

[http://blog.mozilla.com/addons/2011/12/12/help-test-default-compatibility-for-add-ons-on-aurora/](http://blog.mozilla.com/addons/2011/12/12/help-test-default-compatibility-for-add-ons-on-aurora/)

No more need for the Add-on Compatibility Reporter, unless you want to report add-ons that don't work.

If you want the old behavior, enter **about:config**, search for **extensions.strictCompatibility** and double click it to set it to true.


Fantastic news :-)

Now we just need invisible updating...

---

### Post by lovinglinux on 2011-12-15
> **SilverWave said:**
> Fantastic news :-)

Now we just need invisible updating...

It will come eventually, but does it matter for us?

---

### Post by SilverWave on 2011-12-15
> **lovinglinux said:**
> It will come eventually, but does it matter for us?

Well... tbh no ;-)

Except:

...I believe a strong Firefox is needed for a healthy Internet.

...the silent updates thing helps Firefox gain users.

... a strong Firefox is a great advertisement for foss.

 and it was my pathway to Linux, so... tbh yes ;-)

---

### Post by lovinglinux on 2011-12-16
> **SilverWave said:**
> Well... tbh no ;-)

Except:

...I believe a strong Firefox is needed for a healthy Internet.

...the silent updates thing helps Firefox gain users.

... a strong Firefox is a great advertisement for foss.

 and it was my pathway to Linux, so... tbh yes ;-)

Indeed. It will come with FF 11.

BTW, even IE will silent update soon:

[http://windowsteamblog.com/ie/b/ie/](http://windowsteamblog.com/ie/b/ie/)

---

### Post by SilverWave on 2011-12-16
> **lovinglinux said:**
> Indeed. It will come with FF 11.

BTW, even IE will silent update soon:

[http://windowsteamblog.com/ie/b/ie/](http://windowsteamblog.com/ie/b/ie/)


Yes hopefully the end of IE6 :-D

---

### Post by SilverWave on 2011-12-16
[[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox - 9.0~b6+build1-0ubuntu0.11.10.1~mfn1]("https://launchpad.net/%7Emozillateam/+archive/firefox-next/+sourcepub/2125019/+listing-archive-extra")

:-)

---

### Post by SilverWave on 2011-12-17
[[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox-trunk - 11.0~a1~hg20111213r82471-0ubuntu1~umd1~oneiric       ]("https://launchpad.net/%7Esilverwave/+archive/testing3/+sourcepub/2128271/+listing-archive-extra")

---

### Post by SilverWave on 2011-12-19
[[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox - 9.0+build1-0ubuntu0.11.10.1       ]("https://launchpad.net/%7Esilverwave/+archive/testing7/+sourcepub/2131845/+listing-archive-extra")
[[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox - 9.0+build1-0ubuntu0.11.04.1]("https://launchpad.net/%7Eubuntu-mozilla-security/+archive/ppa/+sourcepub/2131282/+listing-archive-extra")

> **Changelog**

         firefox (9.0+build1-0ubuntu0.11.10.1) oneiric-security; urgency=low    * New upstream stable release (FIREFOX_9_0_BUILD1)     - see LP: [#906389]("https://launchpad.net/bugs/906389") for USN information

From: [PPA for Ubuntu Mozilla Security Team]("https://launchpad.net/%7Eubuntu-mozilla-security/+archive/ppa")

---

### Post by SilverWave on 2011-12-20
> **SilverWave said:**
> [[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox - 9.0+build1-0ubuntu0.11.10.1       ]("https://launchpad.net/%7Esilverwave/+archive/testing7/+sourcepub/2131845/+listing-archive-extra")
[[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox - 9.0+build1-0ubuntu0.11.04.1]("https://launchpad.net/%7Eubuntu-mozilla-security/+archive/ppa/+sourcepub/2131282/+listing-archive-extra")



From: [PPA for Ubuntu Mozilla Security Team]("https://launchpad.net/%7Eubuntu-mozilla-security/+archive/ppa")

Here are the other two:

[        firefox - 9.0+build1-0ubuntu0.10.10.1       ]("https://launchpad.net/%7Esilverwave/+archive/testing5/+sourcepub/2133565/+listing-archive-extra")
[firefox - 9.0+build1-0ubuntu0.10.04.1       ]("https://launchpad.net/%7Esilverwave/+archive/testing6/+sourcepub/2133559/+listing-archive-extra")

From: [PPA for Ubuntu Security Proposed]("https://launchpad.net/%7Eubuntu-security-proposed/+archive/ppa")

> firefox (9.0+build1-0ubuntu0.10.10.1) maverick-proposed; urgency=low    * New upstream stable release (FIREFOX_9_0_BUILD1)

---

### Post by SilverWave on 2011-12-22
[[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox - 9.0.1+build1-0ubuntu0.11.10.1]("https://launchpad.net/%7Eubuntu-mozilla-security/+archive/ppa/+sourcepub/2137348/+listing-archive-extra")
[[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox - 9.0.1+build1-0ubuntu0.11.04.1       ]("https://launchpad.net/%7Eubuntu-mozilla-security/+archive/ppa/+sourcepub/2137344/+listing-archive-extra")
[[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox - 9.0.1+build1-0ubuntu0.10.04.1       ]("https://launchpad.net/%7Eubuntu-security-proposed/+archive/ppa/+sourcepub/2137478/+listing-archive-extra")
[[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox - 9.0.1+build1-0ubuntu0.10.10.1       ]("https://launchpad.net/%7Eubuntu-security-proposed/+archive/ppa/+sourcepub/2137480/+listing-archive-extra")

Just in case...

---

### Post by SilverWave on 2011-12-22
[[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox-trunk - 12.0~a1~hg20111222r83196-0ubuntu1~umd1~oneiric]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+sourcepub/2141603/+listing-archive-extra") 64bit only.

[[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox-trunk - 12.0~a1~hg20111222r83196-0ubuntu1~umd1~natty       ]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+sourcepub/2141604/+listing-archive-extra")

[[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox-trunk - 12.0~a1~hg20111222r83196-0ubuntu1~umd1~maverick       ]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+sourcepub/2141605/+listing-archive-extra")

Nothing for Lucid yet.

---

### Post by SilverWave on 2011-12-22
[Firefox hits the jackpot with almost billion dollar Google deal]("http://www.zdnet.com/blog/networking/firefox-hits-the-jackpot-with-almost-billion-dollar-google-deal/1780?tag=mantle_skin;content")

Excellent news :-D

So it looks like Mozilla will be hiring ;-)

Great news for the freedom of the web.

Great news for Firefox on Linux.

---

### Post by lovinglinux on 2011-12-23
> **SilverWave said:**
> [Firefox hits the jackpot with almost billion dollar Google deal]("http://www.zdnet.com/blog/networking/firefox-hits-the-jackpot-with-almost-billion-dollar-google-deal/1780?tag=mantle_skin;content")

Excellent news :-D

So it looks like Mozilla will be hiring ;-)

Great news for the freedom of the web.

Great news for Firefox on Linux.

I didn't know about the values yet. That is a lot of money compared to previous deals.

---

### Post by SilverWave on 2011-12-23
> **lovinglinux said:**
> I didn't know about the values yet. That is a lot of money compared to previous deals.

Yes we wont be able to confirm those numbers until they post their financial's next year.
But a lot of ppl will know if they are wrong.

---

### Post by SilverWave on 2011-12-23
[[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox - 10.0~b1+build1-0ubuntu0.11.10.1~mfn1]("https://launchpad.net/%7Esilverwave/+archive/testing7/+sourcepub/2143462/+listing-archive-extra")
[[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox - 10.0~b1+build1-0ubuntu0.11.04.1~mfn1       ]("https://launchpad.net/%7Esilverwave/+archive/testing4/+sourcepub/2143463/+listing-archive-extra")
[[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox - 10.0~b1+build1-0ubuntu0.10.10.1~mfn1       ]("https://launchpad.net/%7Esilverwave/+archive/testing5/+sourcepub/2143464/+listing-archive-extra")
[[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox - 10.0~b1+build1-0ubuntu0.10.04.1~mfn1       ]("https://launchpad.net/%7Esilverwave/+archive/testing6/+sourcepub/2143465/+listing-archive-extra")
A warning taken from the PPA's and the front post:
> 
**If you add a Beta PPA from the list below, you will always have the latest FF10, FF11 etc., as soon as they are available.**
 
  	  The latest firefox Beta - No other packages.

Copied from firefox-next, Ubuntu Security Proposed & Ubuntu Mozilla Security.
Warning! I am impatient and I copy packages before they have been fully tested.
I even copy packages when status reads "Publishing has been disabled for this archive".
I can do this in good conscience as these ppa's are for my personal use, although I have no problem with others using them. 			 		


---

### Post by SilverWave on 2012-01-01
[[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox-trunk - 12.0~a1~hg20111231r83575-0ubuntu1~umd1~oneiric]("https://launchpad.net/%7Esilverwave/+archive/testing3/+sourcepub/2155931/+listing-archive-extra")
[[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox-trunk - 12.0~a1~hg20111231r83575-0ubuntu1~umd1~natty       ]("https://launchpad.net/%7Esilverwave/+archive/testing1/+sourcepub/2155932/+listing-archive-extra")
[[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox-trunk - 12.0~a1~hg20111231r83575-0ubuntu1~umd1~maverick       ]("https://launchpad.net/%7Esilverwave/+archive/testing2/+sourcepub/2155933/+listing-archive-extra")

No build for Lucid yet as they have all failed.

---

### Post by amol_free on 2012-01-01
After installing the firefox 9, it is starting very slow ..what to do.

---

### Post by SilverWave on 2012-01-01
> **amol_free said:**
> After installing the firefox 9, it is starting very slow ..what to do.

I would need some info to really help:

What version were you on before the upgrade to 9?

What version of Ubuntu are you on?

If you go to about:support and copy the top bit that would help.

Here is mine:

>       
        Name
            Firefox
          Version
            10.0
          User Agent
            Mozilla/5.0 (Ubuntu; X11; Linux x86_64; rv:10.0) Gecko/20100101 Firefox/10.0
            

Update: Try disabling your extensions, if that helps then you know its one of them and you can work your way through them to determine which one is causing the problem.

If that does not help then backup your profile and try creating a new clean profile, does that help?

On and lastly how many tabs do you have open?

---

### Post by r1ft on 2012-01-02
> **SilverWave said:**
> ...No build for Lucid yet as they have all failed.

Does anyone know why? The last update (Lucid Lynx x64) was from almost a month ago (Dec 4)!

---

### Post by SilverWave on 2012-01-02
> **r1ft said:**
> Does anyone know why? The last update (Lucid Lynx x64) was from almost a month ago (Dec 4)!

[https://launchpadlibrarian.net/88862354/buildlog_ubuntu-lucid-amd64.firefox-trunk_12.0~a1~hg20111231r83575-0ubuntu1~umd1~lucid_FAILEDTOBUILD.txt.gz](https://launchpadlibrarian.net/88862354/buildlog_ubuntu-lucid-amd64.firefox-trunk_12.0~a1~hg20111231r83575-0ubuntu1~umd1~lucid_FAILEDTOBUILD.txt.gz)

> Session terminated, killing shell...make[1]: *** wait: No child processes.  Stop. make[1]: *** Waiting for unfinished jobs.... make[1]: *** wait: No child processes.  Stop. make: *** [debian/stamp-xpcshell-tests] Terminated  ...killed. Build killed with signal 15 after 150 minutes of inactivity ****************************************************************************** Build finished at 20120101-0741 FAILED [dpkg-buildpackage died] Purging chroot-autobuild/build/buildd/firefox-trunk-12.0~a1~hg20111231r83575

hmm no maybe Chris can advise?

---

### Post by r1ft on 2012-01-02
Thank you for the quick reply! Does Chris frequent this forum? I've messaged him (and Fabien) previously when we didn't see Chromium updates for 3 months, but he didn't reply.

---

### Post by chrisccoulson on 2012-01-02
> **r1ft said:**
> Thank you for the quick reply! Does Chris frequent this forum? I've messaged him (and Fabien) previously when we didn't see Chromium updates for 3 months, but he didn't reply.

I wouldn't advise sending me e-mail if you want a quick reply. My inbox is currently running at ~25000 unread, and growing daily ;)

I'm aware of the issue on Lucid (the tests hang). I'll fix it when I have some spare time. In the meantime if you want new builds for Lucid, feel free to help figuring out why it doesn't work :)

---

### Post by SilverWave on 2012-01-02
> **r1ft said:**
> Thank you for the quick reply! Does Chris frequent this forum? I've messaged him (and Fabien) previously when we didn't see Chromium updates for 3 months, but he didn't reply.

Yes he usually keeps and eye on us ;-) , if not you could try #ubuntu-mozillateam on freenode.

> **PPA description**

   
   daily (or even multiple builds per day) for various mozilla projects and branches.
 For questions and bugs with software in this archive, please contact [EMAIL="ubuntu-mozillateam@lists.ubuntu.com"]ubuntu-mozillateam@lists.ubuntu.com[/EMAIL] or visit #ubuntu-mozillateam on freenode.

  
      


UPDATE: see Chris's reply above.

---

### Post by SilverWave on 2012-01-04
> **r1ft said:**
> Does anyone know why? The last update (Lucid Lynx x64) was from almost a month ago (Dec 4)!


here is a link so we can easily keep an eye on progress:
[https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa/+packages?field.name_filter=firefox-trunk&field.status_filter=&field.series_filter=lucid]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+packages?field.name_filter=firefox-trunk&field.status_filter=&field.series_filter=lucid")

---

### Post by SilverWave on 2012-01-05
[Enterprise/Firefox/ExtendedSupport:Proposal]("https://wiki.mozilla.org/Enterprise/Firefox/ExtendedSupport:Proposal")

Interesting stuff:

> 
[LIST]
[*]**Firefox 10 will be the base version for the initial ESR** and, assuming this is the case, **Firefox 3.6 will be end-of-lifed on April 24th, 2012**  (when Firefox 3.6 is end-of-lifed, an update to the current version of  Desktop Firefox will be offered through the Application Update Service).
[*] The ESR release will use the same version number as the  version of Firefox it is based upon (e.g. if the ESR is based off of  Firefox 10, the ESR version will also be 10)
[*] The ESR point releases will follow Firefox conventions for point releases (e.g. 10.0.1, 10.0.2, etc.)
[*] The ESR release will use the same application GUID as Firefox
[*] Mozilla will backport security bugs qualified as ["Critical" and "High"]("https://wiki.mozilla.org/Security_Severity_Ratings")  to the ESR where feasible (there may be cases where a backport cannot  be applied with reasonable effort, and those cases are expected to be  exceptional). Other security and stability backports to the ESR will be  included at Mozilla's discretion.
[/LIST]


---

### Post by chrisccoulson on 2012-01-05
The next Lucid build *should* be successful:

[http://bazaar.launchpad.net/~mozillateam/firefox/firefox-trunk.head/revision/1091]("http://bazaar.launchpad.net/~mozillateam/firefox/firefox-trunk.head/revision/1091")

---

### Post by SilverWave on 2012-01-08
Interesting: 

[The Future of Firefox Security]("http://www.esecurityplanet.com/browser-security/the-future-of-firefox-security.html")
> 
One of these efforts focused on making Firefox easier to update is called "hotfix addons."
 "What hotfix does is it gives us an extra tool to address issues we  see in the field without having to push a brand new update," Nightingale  explained. "It lets us push out updates in a targeted way and it lets  us deliver a fix to our users without introducing a lot of the current  interruption that a full software update involves."
 The hotfix feature will give Mozilla a way to patch a vulnerability  or fix an important issue without requiring a full build. In some cases,  there won't even be a need to restart the browser.


---

### Post by SilverWave on 2012-01-08
[[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox - 10.0~b3+build2-0ubuntu0.11.10.1~mfn1]("https://launchpad.net/%7Emozillateam/+archive/firefox-next/+sourcepub/2164071/+listing-archive-extra")

:-)

---

### Post by SilverWave on 2012-01-08
[[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox-trunk - 12.0~a1~hg20120107r84013-0ubuntu1~umd1~oneiric]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+sourcepub/2168490/+listing-archive-extra")
[[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox-trunk - 12.0~a1~hg20120107r84013-0ubuntu1~umd1~natty       ]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+sourcepub/2168491/+listing-archive-extra")
[        ]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+sourcepub/2168492/+listing-archive-extra")[[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox-trunk - 12.0~a1~hg20120107r84013-0ubuntu1~umd1~maverick       ]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+sourcepub/2168492/+listing-archive-extra")

Lucid Failed.

---

### Post by ShaneOSDN on 2012-01-09
worked great here Natty 11.10

---

### Post by SilverWave on 2012-01-09
> **ShaneOSDN said:**
> worked great here Natty 11.10

Nice :-)

---

### Post by SilverWave on 2012-01-11
[Firefox 3.6, the default browser of Ubuntu 10.04 LTS, reaches &#8216;end of life&#8217; status in April this year.]("http://www.omgubuntu.co.uk/2012/01/older-versions-of-ubuntu-to-get-latest-firefox-releases")

> **From February 17th Ubuntu 10.04 and 10.10 users will be automatically upgraded to the latest release of Firefox.**

---

### Post by SilverWave on 2012-01-15
[[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox - 10.0~b4+build1-0ubuntu0.11.04.1~mfn1]("https://launchpad.net/%7Esilverwave/+archive/testing4/+sourcepub/2179820/+listing-archive-extra")

Nice :-)

---

### Post by SilverWave on 2012-01-15
> **SilverWave said:**
> here is a link so we can easily keep an eye on progress:
[https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa/+packages?field.name_filter=firefox-trunk&field.status_filter=&field.series_filter=lucid]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+packages?field.name_filter=firefox-trunk&field.status_filter=&field.series_filter=lucid")

hmmm:

> **Build status**

            [IMG]https://launchpad.net/@@/build-depwait[/IMG]       Dependency wait                       on [pluot (virtual-64)]("https://launchpad.net/builders/pluot")                          
      
[LIST]
[*]         Missing build dependencies: *yasm (>= 1.1)*
[*]           Started 12 hours ago
[*]         Finished 12 hours ago                    (took 6 minutes, 47.4 seconds)
[*]         [buildlog]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+build/3094581/+files/buildlog_ubuntu-lucid-amd64.firefox-trunk_12.0%7Ea1%7Ehg20120114r84451-0ubuntu1%7Eumd1%7Elucid_MANUALDEPWAIT.txt.gz")         (22.4 KiB)
[/LIST]
              
         


---

### Post by SilverWave on 2012-01-15
[[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox-trunk - 12.0~a1~hg20120114r84451-0ubuntu1~umd1~oneiric]("https://launchpad.net/%7Esilverwave/+archive/testing3/+sourcepub/2180546/+listing-archive-extra") OK
[[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox-trunk - 12.0~a1~hg20120114r84451-0ubuntu1~umd1~natty        ]("https://launchpad.net/%7Esilverwave/+archive/testing1/+sourcepub/2180547/+listing-archive-extra")OK

[[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox-trunk - 12.0~a1~hg20120114r84451-0ubuntu1~umd1~maverick       ]("https://launchpad.net/%7Esilverwave/+archive/testing2/+sourcepub/2180548/+listing-archive-extra")i386 OK AMD64 failed

Lucid failed as per previous post.

---

### Post by SilverWave on 2012-01-21
[Firefox Beta Tests Add-on Hotfix Feature]("http://news.softpedia.com/news/Firefox-Beta-Tests-Add-on-Hotfix-Feature-247885.shtml")

Interesting...

> *Add-on is visible in the Add-ons Manager as “Mozilla Firefox hotfix”*                                                                                                                                                                                                                                                                                           **Starting with [Firefox]("http://www.softpedia.com/get/Internet/Browsers/Mozilla-Firefox-Final.shtml")  10, Mozilla will start delivering hotfixes for its web browser, via an  add-on, in order to have fewer full updates pushed to users.**

Firefox beta users are the first testers of the feature, as Mozilla  pushes today an automatically downloaded test add-on. The component is  visible in the Add-ons Manager as “Mozilla Firefox hotfix” and will not  affect the way the browser acts.


---

### Post by SilverWave on 2012-01-21
[[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox - 10.0~b5+build1-0ubuntu0.11.10.1~mfn1]("https://launchpad.net/%7Emozillateam/+archive/firefox-next/+sourcepub/2188237/+listing-archive-extra")

:-)

---

### Post by chrisccoulson on 2012-01-29
Hi,

You might want to update the information in the original post now (see [http://www.chriscoulson.me.uk/blog/?p=100]("http://www.chriscoulson.me.uk/blog/?p=100"))

Thanks!

---

### Post by SilverWave on 2012-01-29
> **chrisccoulson said:**
> Hi,

You might want to update the information in the original post now (see [http://www.chriscoulson.me.uk/blog/?p=100](http://www.chriscoulson.me.uk/blog/?p=100))

Thanks!


> **[Retiring the Firefox Stable PPA]("http://www.chriscoulson.me.uk/blog/?p=100")**

 		 					 [Mozilla]("http://www.chriscoulson.me.uk/blog/?cat=4"), [Ubuntu]("http://www.chriscoulson.me.uk/blog/?cat=3") 							 [Add comments]("http://www.chriscoulson.me.uk/blog/?p=100#respond") 					
 		
 		Jan 292012
 	
 	 		 			 With the announcement that users of Ubuntu 10.04 LTS and Ubuntu 10.10 will be [upgraded to the latest version of Firefox]("https://lists.ubuntu.com/archives/ubuntu-security-announce/2012-January/001544.html"), we are going to be retiring the [Firefox Stable PPA]("https://launchpad.net/%7Emozillateam/+archive/firefox-stable").
 Since the release of Firefox 4 last year, we have been providing this  PPA so that Ubuntu 10.04 LTS and Ubuntu 10.10 users didn’t have to miss  out on the new features, performance improvements, security  enhancements and improved compatibility with newer web technologies  provided by the latest releases of Firefox.
 The next version of Firefox (Firefox 10, to be released on [Tuesday]("https://wiki.mozilla.org/RapidRelease/Calendar")  of this week) will be delivered as a security update to all Ubuntu  releases – hopefully by the end of the week. This means that users will  receive the update without having to do anything.
 I have no plans to upload the next release to the Firefox Stable PPA.
 If you’re aware of any online resource (eg, on the [Ubuntu Wiki]("https://wiki.ubuntu.com/"), [Ubuntu Forums]("http://ubuntuforums.org/"), [Ask Ubuntu]("http://askubuntu.com/")  or any other site providing help to Ubuntu users) which recommends to  use this PPA to receive the latest version of Firefox, I would  appreciate you taking the time to either correct this information (or  removing it, if more appropriate).


Thanks Chris.

---

### Post by SilverWave on 2012-01-29
[Firefox Rapid Release Migration in Ubuntu 10.04 LTS and Ubuntu 10.10]("https://lists.ubuntu.com/archives/ubuntu-security-announce/2012-January/001544.html")

> **Firefox Rapid Release Migration in Ubuntu 10.04 LTS and Ubuntu 10.10**

     **Micah Gersten**      [EMAIL="ubuntu-security-announce%40lists.ubuntu.com?Subject=Re%3A%20Firefox%20Rapid%20Release%20Migration%20in%20Ubuntu%2010.04%20LTS%20and%20Ubuntu%2010.10&In-Reply-To=%3C4F0B1A59.7090206%40canonical.com%3E"]micah at canonical.com        [/EMAIL]
    *Mon Jan  9 16:48:25 UTC 2012*     
[LIST]
[*]Previous message: [[USN-1322-1] Linux kernel vulnerabilities ]("https://lists.ubuntu.com/archives/ubuntu-security-announce/2012-January/001543.html")
[*]Next message: [[USN-1323-1] Linux kernel vulnerabilities ]("https://lists.ubuntu.com/archives/ubuntu-security-announce/2012-January/001545.html")
[*] **Messages sorted by:**                [[ date ]]("https://lists.ubuntu.com/archives/ubuntu-security-announce/2012-January/date.html#1544")               [[ thread ]]("https://lists.ubuntu.com/archives/ubuntu-security-announce/2012-January/thread.html#1544")               [[ subject ]]("https://lists.ubuntu.com/archives/ubuntu-security-announce/2012-January/subject.html#1544")               [[ author ]]("https://lists.ubuntu.com/archives/ubuntu-security-announce/2012-January/author.html#1544")
[/LIST]
         The upstream Mozilla Firefox web browser has moved to a rapid release cycle. New Firefox versions are being released every six weeks and contain new features and security enhancements. Until now, Ubuntu 10.04 LTS and Ubuntu 10.10 have been getting 3.6 point releases of Firefox. As such, users have not been benefiting from new features, support for new web technologies, security enhancements, and performance improvements. Firefox 3.6 will be reaching its end of life soon, so we need to migrate users to rapid release so that they will continue to receive security updates in a timely fashion.  * What is changing? *  Starting on January 17, Ubuntu 10.04 LTS and Ubuntu 10.10 users will be migrated to the latest Firefox version, and will track the rapid releases going forward, as is currently done in newer releases of Ubuntu. This will enable users to get the numerous improvements offered by new Firefox versions.  * What is the impact of this migration? *  Add-ons that were previously in the Ubuntu archive, such as flashblock or webdeveloper, will be automatically migrated to reside in your user profile so that they may be updated through the regular update process using addons.mozilla.org. This is necessary to ensure that you automatically get a working version of these addons, if one is available, when a new version of Firefox is released.  As Firefox will be updated to a new version every 6 weeks, the browsing experience might change slightly with each update.  * What do I need to do? *  These updates will be pushed automatically through the regular update process once testing has been completed. No action is required on your part.  Users who access specialized web sites, such as intranets or corporate portals, need to make sure they are compatible with the latest Firefox releases before the migration occurs.  * Can I help with testing? *  If you would like to assist with testing, you can enable the proposed repository on non-production Ubuntu 10.04 LTS or Ubuntu 10.10 systems [1].  * For more information *  Please see the following wiki page for information on the migration: [2]  You may also track progress of the update in the tracking bug: [3]  [1] - [https://wiki.ubuntu.com/Testing/EnableProposed](https://wiki.ubuntu.com/Testing/EnableProposed)  [2] - [https://wiki.ubuntu.com/LucidLynx/ReleaseNotes/FirefoxRapidReleaseMigration](https://wiki.ubuntu.com/LucidLynx/ReleaseNotes/FirefoxRapidReleaseMigration)  [3] - [https://bugs.launchpad.net/bugs/904594](https://bugs.launchpad.net/bugs/904594)

---

### Post by SilverWave on 2012-01-29
[[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox - 10.0~b6+build1-0ubuntu0.11.10.1~mfn1]("https://launchpad.net/%7Esilverwave/+archive/testing7/+sourcepub/2206938/+listing-archive-extra")
[[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox - 10.0~b6+build1-0ubuntu0.11.04.1~mfn1       ]("https://launchpad.net/%7Esilverwave/+archive/testing4/+sourcepub/2206941/+listing-archive-extra")
[[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox - 10.0~b6+build1-0ubuntu0.10.10.1~mfn1       ]("https://launchpad.net/%7Esilverwave/+archive/testing5/+sourcepub/2206943/+listing-archive-extra")
[[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox - 10.0~b6+build1-0ubuntu0.10.04.1~mfn1       ]("https://launchpad.net/%7Esilverwave/+archive/testing6/+sourcepub/2206944/+listing-archive-extra")

All updated :-)

---

### Post by SilverWave on 2012-01-29
[[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox-trunk - 12.0~a1~hg20120129r85589-0ubuntu1~umd1~oneiric]("https://launchpad.net/%7Esilverwave/+archive/testing3/+sourcepub/2206962/+listing-archive-extra")
[[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox-trunk - 12.0~a1~hg20120129r85589-0ubuntu1~umd1~natty       ]("https://launchpad.net/%7Esilverwave/+archive/testing1/+sourcepub/2206952/+listing-archive-extra")
[[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox-trunk - 12.0~a1~hg20120129r85589-0ubuntu1~umd1~lucid       ]("https://launchpad.net/%7Esilverwave/+archive/testing0/+sourcepub/2206955/+listing-archive-extra")

---

### Post by SilverWave on 2012-01-29
> **r1ft said:**
> Does anyone know why? The last update (Lucid Lynx x64) was from almost a month ago (Dec 4)!


> here is a link so we can easily keep an eye on progress:
[https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa/+packages?field.name_filter=firefox-trunk&field.status_filter=&field.series_filter=lucid]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+packages?field.name_filter=firefox-trunk&field.status_filter=&field.series_filter=lucid")

Yeah! Working now :-D

---

### Post by r1ft on 2012-01-31
Unfortunately, today's (nightly) build broke my nightly install on 10.04 x86_64. I filed a bug (my first 'automatic' bug submission on LP), but it seemed to have gone to the main Firefox LP instead.

Anyway, here's what I got when I tried to perform the following steps (after the failed nightly update from the PPA):
```
sudo apt-get remove firefox-trunk (successfully done)
sudo apt-get install firefox-trunk
```

```
Initializing download: [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu/pool/main/f/firefox-trunk/firefox-trunk-globalmenu_12.0~a1~hg20120131r85707-0ubuntu1~umd3~lucid_amd64.deb](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu/pool/main/f/firefox-trunk/firefox-trunk-globalmenu_12.0~a1~hg20120131r85707-0ubuntu1~umd3~lucid_amd64.deb)
File size: 8968 bytes
Opening output file firefox-trunk-globalmenu_12.0~a1~hg20120131r85707-0ubuntu1~umd3~lucid_amd64.deb
Starting download

Connection 1 finished                                                          ]
Connection 0 finished                                                          ]

Downloaded 8.8 kilobytes in 0 seconds. (29.10 KB/s)
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  firefox-trunk-globalmenu
Suggested packages:
  latex-xft-fonts firefox-trunk-gnome-support kmozillahelper
The following NEW packages will be installed:
  firefox-trunk firefox-trunk-globalmenu
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/19.7MB of archives.
After this operation, 42.7MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Selecting previously deselected package firefox-trunk.
(Reading database ... 192592 files and directories currently installed.)
Unpacking firefox-trunk (from .../firefox-trunk_12.0~a1~hg20120131r85707-0ubuntu1~umd3~lucid_amd64.deb) ...
Selecting previously deselected package firefox-trunk-globalmenu.
Unpacking firefox-trunk-globalmenu (from .../firefox-trunk-globalmenu_12.0~a1~hg20120131r85707-0ubuntu1~umd3~lucid_amd64.deb) ...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for man-db ...
Processing triggers for python-support ...
Setting up firefox-trunk (12.0~a1~hg20120131r85707-0ubuntu1~umd3~lucid) ...
update-alternatives: error: alternative path /usr/bin/firefox-trunk doesn't exist.
dpkg: error processing firefox-trunk (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of firefox-trunk-globalmenu:
 firefox-trunk-globalmenu depends on firefox-trunk (= 12.0~a1~hg20120131r85707-0ubuntu1~umd3~lucid); however:
  Package firefox-trunk is not configured yet.
dpkg: error processing firefox-trunk-globalmenu (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 firefox-trunk
 firefox-trunk-globalmenu
E: Sub-process /usr/bin/dpkg returned an error code (1)
-e
```

---

### Post by SilverWave on 2012-01-31
All theses updated:

[[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox - 10.0+build1-0ubuntu0.11.10.1]("https://launchpad.net/%7Eubuntu-mozilla-security/+archive/ppa/+sourcepub/2206546/+listing-archive-extra")
[[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox - 10.0+build1-0ubuntu0.11.04.1       ]("https://launchpad.net/%7Eubuntu-mozilla-security/+archive/ppa/+sourcepub/2206550/+listing-archive-extra")
[[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox - 10.0+build1-0ubuntu0.10.10.1       ]("https://launchpad.net/%7Eubuntu-mozilla-security/+archive/ppa/+sourcepub/2206551/+listing-archive-extra")

I haven’t updated 10.04 as the 64bit build failed. 
[[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox - 10.0+build1-0ubuntu0.10.04.2       ]("https://launchpad.net/%7Eubuntu-mozilla-security/+archive/ppa/+sourcepub/2206958/+listing-archive-extra")

---

### Post by SilverWave on 2012-01-31
> **r1ft said:**
> Unfortunately, today's (nightly) build broke my nightly install on 10.04 x86_64. I filed a bug (my first 'automatic' bug submission on LP), but it seemed to have gone to the main Firefox LP instead.

Anyway, here's what I got when I tried to perform the following steps (after the failed nightly update from the PPA):


[https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa/+packages?field.name_filter=firefox-trunk&field.status_filter=&field.series_filter=lucid]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+packages?field.name_filter=firefox-trunk&field.status_filter=&field.series_filter=lucid")

hmm you may want to have another go in a couple of hours as Chris has another one building now.

Oh and its marked firefox-trunk - 13.0a1 :-)

---

### Post by SilverWave on 2012-02-01
[[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox-trunk - 13.0~a1~hg20120131r85845-0ubuntu1~umd1~oneiric]("https://launchpad.net/%7Esilverwave/+archive/testing3/+sourcepub/2231798/+listing-archive-extra")
[[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox-trunk - 13.0~a1~hg20120131r85845-0ubuntu1~umd1~natty       ]("https://launchpad.net/%7Esilverwave/+archive/testing1/+sourcepub/2231799/+listing-archive-extra")
[[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox-trunk - 13.0~a1~hg20120131r85845-0ubuntu1~umd1~lucid       ]("https://launchpad.net/%7Esilverwave/+archive/testing0/+sourcepub/2231801/+listing-archive-extra")

Maverick is MIA possibly EOL?

---

### Post by Skara Brae on 2012-02-04
Firefox 6, 7, 8, 9, 10...

The update manager installed Firefox 10 and broke some add-ons.

I know this is off-topic, but... how do I get an "older-than-Firefox 10" back? This is already hard enough in Windows... ](*,)

---

### Post by SilverWave on 2012-02-05
> **Skara Brae said:**
> Firefox 6, 7, 8, 9, 10...

The update manager installed Firefox 10 and broke some add-ons.

I know this is off-topic, but... how do I get an "older-than-Firefox 10" back? This is already hard enough in Windows... ](*,)


Hmm it depends ;-)

This may be of use: [http://ubuntuforums.org/showthread.php?t=1856481](http://ubuntuforums.org/showthread.php?t=1856481)

But first I would try the Add-ons Compatibility Reporter, as there shouldn&#8217;t be much breakage between ff9 and ff10.

---

### Post by SilverWave on 2012-02-05
[[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox - 11.0~b1+build1-0ubuntu0.11.10.1~mfn1]("https://launchpad.net/%7Esilverwave/+archive/testing7/+sourcepub/2239716/+listing-archive-extra")
[[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox - 11.0~b1+build1-0ubuntu0.11.04.1~mfn1       ]("https://launchpad.net/%7Esilverwave/+archive/testing4/+sourcepub/2239717/+listing-archive-extra")
[[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox - 11.0~b1+build1-0ubuntu0.10.10.1~mfn3       ]("https://launchpad.net/%7Esilverwave/+archive/testing5/+sourcepub/2239718/+listing-archive-extra")
[[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox - 11.0~b1+build1-0ubuntu0.10.04.1~mfn3       ]("https://launchpad.net/%7Esilverwave/+archive/testing6/+sourcepub/2239720/+listing-archive-extra")

First of the new ff11.0 beta's

---

### Post by SilverWave on 2012-02-07
[Adobe adds Flash sandboxing to Firefox]("http://www.theregister.co.uk/2012/02/07/adobe_sandbox_firefox/")

> Adobe has released [beta code]("http://labs.adobe.com/downloads/flashplatformruntimes_incubator.html")  for sandboxing its heavily hacked Flash code within Firefox, in a  similar fashion to the Chrome security protections added to its Reader  software and Google&#8217;s Chrome browser.
  &#8220;Sandboxing technology has proven very effective in protecting users  by increasing the cost and complexity of authoring effective exploits,&#8221;  said Peleus Uhley, senior security researcher for Adobe in a [blog post]("http://blogs.adobe.com/asset/2012/02/flash-player-sandboxing-is-coming-to-firefox.html").
Interesting stuff.

but then...

> The code will work with Firefox 4.0 or later versions running on Windows 7 or Vista.

:-(

---

### Post by SilverWave on 2012-02-07
[USER-TRACKING Firefox sparks Mozilla civil war - Devs spar over unique identifiers in MetricsDataPing code]("http://www.theregister.co.uk/2012/02/07/mozilla_telemetry_controversy/")

hmm Opt Out... shirley not :/

> **To UUID, or not to UUID**

  Bucksch is concerned because a proposal has been put forward for  Telemetry to include a universally unique identifier (UUID) for  longitudinal analysis.
  He claimed that the presence of that UUID would mean that personally  identifiable information was being collected and added that it must not  happen, not only because of the privacy implications but also due to the  potential damage to Mozilla's reputation.


---

### Post by lovinglinux on 2012-02-08
> **SilverWave said:**
> [USER-TRACKING Firefox sparks Mozilla civil war - Devs spar over unique identifiers in MetricsDataPing code]("http://www.theregister.co.uk/2012/02/07/mozilla_telemetry_controversy/")

hmm Opt Out... shirley not :/

Not a good idea.

---

### Post by SilverWave on 2012-02-08
> **lovinglinux said:**
> Not a good idea.

Clarification from the reg:

[Mozilla explains user-tracking proposal for Firefox   - Telemetry has no UUID, Metrics Data Ping might]("http://www.theregister.co.uk/2012/02/08/mozilla_difference_between_telemetry_metrics_data_ping/")

> In a story published yesterday your humble Reg writer wrongly confused Mozilla's Telemetry project with the open-source outfit's so-called Metrics Data Ping proposal. Mozilla has been in touch to clear things up.

---

### Post by SilverWave on 2012-02-12
Here are the latest beta's

[[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox - 11.0~b2+build1-0ubuntu0.11.10.1~mfn1       ]("https://launchpad.net/%7Emozillateam/+archive/firefox-next/+sourcepub/2247192/+listing-archive-extra")
[[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox - 11.0~b2+build1-0ubuntu0.11.04.1~mfn1       ]("https://launchpad.net/%7Emozillateam/+archive/firefox-next/+sourcepub/2247196/+listing-archive-extra")
[[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox - 11.0~b2+build1-0ubuntu0.10.10.1~mfn1       ]("https://launchpad.net/%7Emozillateam/+archive/firefox-next/+sourcepub/2247198/+listing-archive-extra")
[[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox - 11.0~b2+build1-0ubuntu0.10.04.1~mfn2       ]("https://launchpad.net/%7Emozillateam/+archive/firefox-next/+sourcepub/2247232/+listing-archive-extra")

---

### Post by SilverWave on 2012-02-12
Latest Nightly.

[[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox-trunk - 13.0~a1~hg20120211r86660-0ubuntu1~umd1~oneiric ]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+sourcepub/2251402/+listing-archive-extra")
[[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox-trunk - 13.0~a1~hg20120211r86660-0ubuntu1~umd1~natty       ]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+sourcepub/2251403/+listing-archive-extra")

Maverick is missing/eol.
Lucid failed.

---

### Post by SilverWave on 2012-02-15
Interesting if true:

[Firefox Will Get a Built-in "Reader" View]("http://news.softpedia.com/news/Firefox-Will-Get-a-Built-in-quot-Reader-quot-View-253110.shtml")

I actually use a "Reader" as a last resort. I feel you lose something when you reduce all your sites to the same bland grey.

Saying which its great to have such a feature as a last resort, for when other tools don’t cut it.

It would be interesting if it could determine the most likely element containing the content and remove the rest automatically.

Maybe as a fall-back the user could point to it?

---

### Post by ayesha14 on 2012-02-16
Thanks for information

---

### Post by SilverWave on 2012-02-17
[[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox - 11.0~b3+build2-0ubuntu0.11.10.1~mfn1]("https://launchpad.net/%7Emozillateam/+archive/firefox-next/+sourcepub/2259221/+listing-archive-extra") i386 still building.
[[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox - 11.0~b3+build2-0ubuntu0.11.04.1~mfn1       ]("https://launchpad.net/%7Emozillateam/+archive/firefox-next/+sourcepub/2259227/+listing-archive-extra")
[[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox - 11.0~b3+build2-0ubuntu0.10.10.1~mfn2       ]("https://launchpad.net/%7Emozillateam/+archive/firefox-next/+sourcepub/2259238/+listing-archive-extra")
[[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox - 11.0~b3+build2-0ubuntu0.10.04.1~mfn1       ]("https://launchpad.net/%7Emozillateam/+archive/firefox-next/+sourcepub/2259237/+listing-archive-extra")

Here we go :-)

---

### Post by JMB74 on 2012-02-18
> **SilverWave said:**
> [[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox - 11.0~b3+build2-0ubuntu0.11.10.1~mfn1]("https://launchpad.net/%7Emozillateam/+archive/firefox-next/+sourcepub/2259221/+listing-archive-extra") i386 **still building.**

Build seems to have stalled.

---

### Post by SilverWave on 2012-02-18
> **JMB74 said:**
> Build seems to have stalled.

hmmm yeah.

On the bright side the 64 bit package installed OK on my box ;-)

---

### Post by SilverWave on 2012-02-24
[[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox-trunk - 13.0~a1~hg20120223r87452-0ubuntu1~umd1~oneiric]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+sourcepub/2269300/+listing-archive-extra")
[[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox-trunk - 13.0~a1~hg20120222r87313-0ubuntu1~umd1~natty]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+sourcepub/2267433/+listing-archive-extra")
[[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox-trunk - 13.0~a1~hg20120222r87313-0ubuntu1~umd1~lucid       ]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+sourcepub/2267438/+listing-archive-extra")

Maverick no longer supported AFAICS.

---

### Post by SilverWave on 2012-02-24
> **SilverWave said:**
> 

Maverick no longer supported AFAICS.

I have disabled the Maverick Nightly PPA
```
 sudo add-apt-repository ppa:silverwave/testing1
```[One Nightly A Week #2 - Maverick]("https://launchpad.net/%7Esilverwave/+archive/testing2")

---

### Post by SilverWave on 2012-02-28
[[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox - 11.0~b4+build1-0ubuntu0.11.10.1~mfn3]("https://launchpad.net/%7Emozillateam/+archive/firefox-next/+sourcepub/2277433/+listing-archive-extra")
[[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox - 11.0~b4+build1-0ubuntu0.11.04.1~mfn1       ]("https://launchpad.net/%7Emozillateam/+archive/firefox-next/+sourcepub/2272647/+listing-archive-extra")
[[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox - 11.0~b4+build1-0ubuntu0.10.10.1~mfn1       ]("https://launchpad.net/%7Emozillateam/+archive/firefox-next/+sourcepub/2272650/+listing-archive-extra")
[[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox - 11.0~b4+build1-0ubuntu0.10.04.1~mfn1       ]("https://launchpad.net/%7Emozillateam/+archive/firefox-next/+sourcepub/2272655/+listing-archive-extra")

Very close to release :-)

---

### Post by SilverWave on 2012-03-03
Added a new nightly PPA for 12.04

> [B]Add a PPA:
[/B]
[One Nightly A Week #2 - Precise]("https://launchpad.net/%7Esilverwave/+archive/testing2") 
 	 	```
 sudo add-apt-repository ppa:silverwave/testing2
```


---

### Post by SilverWave on 2012-03-03
[[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox-trunk - 13.0~a1~hg20120228r87911-0ubuntu1~umd1]("https://launchpad.net/%7Esilverwave/+archive/testing2/+sourcepub/2286201/+listing-archive-extra")
[[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox-trunk - 13.0~a1~hg20120228r87911-0ubuntu1~umd1~oneiric       ]("https://launchpad.net/%7Esilverwave/+archive/testing3/+sourcepub/2286189/+listing-archive-extra")
[[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox-trunk - 13.0~a1~hg20120228r87911-0ubuntu1~umd1~natty       ]("https://launchpad.net/%7Esilverwave/+archive/testing1/+sourcepub/2286187/+listing-archive-extra")
[[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox-trunk - 13.0~a1~hg20120228r87911-0ubuntu1~umd1~lucid       ]("https://launchpad.net/%7Esilverwave/+archive/testing0/+sourcepub/2286188/+listing-archive-extra")

Here we go :-)

---

### Post by SilverWave on 2012-03-03
[What can go wrong? Hitting the: “update-manager -d” to PrecisePangolin 12.04]("http://silverwav.wordpress.com/2012/03/03/what-can-go-wrong-hitting-the-update-manager-d-to-precisepangolin-12-04/")

The short answer nothing so far ;-)

I had a rush of blood to the head and upgraded today... so far so good.

Sweet.

---

### Post by SilverWave on 2012-03-04
[[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox - 11.0~b5+build1-0ubuntu0.11.10.1~mfn2]("https://launchpad.net/%7Esilverwave/+archive/testing7/+sourcepub/2287698/+listing-archive-extra")
[[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox - 11.0~b5+build1-0ubuntu0.11.04.1~mfn1       ]("https://launchpad.net/%7Esilverwave/+archive/testing4/+sourcepub/2287700/+listing-archive-extra")
[[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox - 11.0~b5+build1-0ubuntu0.10.10.1~mfn1       ]("https://launchpad.net/%7Esilverwave/+archive/testing5/+sourcepub/2287701/+listing-archive-extra")
[[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox - 11.0~b5+build1-0ubuntu0.10.04.1~mfn1       ]("https://launchpad.net/%7Esilverwave/+archive/testing6/+sourcepub/2287702/+listing-archive-extra")

Nearly there :-)

---

### Post by SilverWave on 2012-03-09
[Mozilla Doesn't Want Pepper for Linux Flash]("http://www.internetnews.com/blog/skerner/mozilla-doesnt-want-pepper-for-linux-flash.html")

Hmm I wonder if they will find another way around the flash for Linux issue?
> 
A couple week ago, Adobe announced  that is was abandoning Flash on Linux to Google. The idea being that  Chrome integrates Flash and Google can be the place where Linux users go  for Flash.
 But what about Firefox? Why can't Firefox on Linux also get the same benefit?
 As it turns out, that's a bug that Mozilla WONTFIX.


---

### Post by SilverWave on 2012-03-10
[[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox - 11.0~b6+build1-0ubuntu0.11.10.1~mfn1]("https://launchpad.net/%7Esilverwave/+archive/testing7/+sourcepub/2297848/+listing-archive-extra")
[[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox - 11.0~b6+build1-0ubuntu0.11.04.1~mfn1       ]("https://launchpad.net/%7Esilverwave/+archive/testing4/+sourcepub/2297849/+listing-archive-extra")
[[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox - 11.0~b6+build1-0ubuntu0.10.10.1~mfn1       ]("https://launchpad.net/%7Esilverwave/+archive/testing5/+sourcepub/2297850/+listing-archive-extra")
[[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox - 11.0~b6+build1-0ubuntu0.10.04.1~mfn1       ]("https://launchpad.net/%7Esilverwave/+archive/testing6/+sourcepub/2297851/+listing-archive-extra")

b7 up shortly...

---

### Post by SilverWave on 2012-03-10
[[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox-trunk - 13.0~a1~hg20120308r88518-0ubuntu1~umd1]("https://launchpad.net/%7Esilverwave/+archive/testing2/+sourcepub/2297860/+listing-archive-extra")
[[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox-trunk - 13.0~a1~hg20120308r88518-0ubuntu1~umd1~oneiric       ]("https://launchpad.net/%7Esilverwave/+archive/testing3/+sourcepub/2297861/+listing-archive-extra")
[[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox-trunk - 13.0~a1~hg20120306r88331-0ubuntu1~umd2~natty       ]("https://launchpad.net/%7Esilverwave/+archive/testing1/+sourcepub/2297858/+listing-archive-extra")
[[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox-trunk - 13.0~a1~hg20120306r88331-0ubuntu1~umd2~lucid       ]("https://launchpad.net/%7Esilverwave/+archive/testing0/+sourcepub/2297864/+listing-archive-extra")

Working well so far...

---

### Post by SilverWave on 2012-03-13
[[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox - 11.0~b7+build1-0ubuntu0.11.10.1~mfn1]("https://launchpad.net/%7Emozillateam/+archive/firefox-next/+sourcepub/2296596/+listing-archive-extra")
[[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox - 11.0~b7+build1-0ubuntu0.11.04.1~mfn1       ]("https://launchpad.net/%7Emozillateam/+archive/firefox-next/+sourcepub/2296599/+listing-archive-extra")
[[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox - 11.0~b7+build1-0ubuntu0.10.10.1~mfn1       ]("https://launchpad.net/%7Emozillateam/+archive/firefox-next/+sourcepub/2296600/+listing-archive-extra")
[[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox - 11.0~b7+build1-0ubuntu0.10.04.1~mfn1       ]("https://launchpad.net/%7Emozillateam/+archive/firefox-next/+sourcepub/2296601/+listing-archive-extra")

Here we go...

---

### Post by SilverWave on 2012-03-13
[[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox-trunk - 13.0~a1~hg20120313r88815-0ubuntu1~umd1]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+sourcepub/2302973/+listing-archive-extra")
[[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox-trunk - 13.0~a1~hg20120313r88815-0ubuntu1~umd1~oneiric       ]("https://launchpad.net/%7Esilverwave/+archive/testing3/+sourcepub/2304140/+listing-archive-extra")
[[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox-trunk - 13.0~a1~hg20120310r88692-0ubuntu1~umd1~natty       ]("https://launchpad.net/%7Esilverwave/+archive/testing1/+sourcepub/2304142/+listing-archive-extra")
[[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox-trunk - 13.0~a1~hg20120310r88692-0ubuntu1~umd1~lucid       ]("https://launchpad.net/%7Esilverwave/+archive/testing0/+sourcepub/2304143/+listing-archive-extra")

Up to date :-)

---

### Post by SilverWave on 2012-03-13
[Mozilla nixes Firefox 11 delay, will launch upgrade today]("http://www.computerworld.com/s/article/9225149/Mozilla_nixes_Firefox_11_delay_will_launch_upgrade_today?source=rss_latest_content&utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+computerworld%2Fnews%2Ffeed+%28Latest+from+Computerworld%29")

> **Says concern over last week's Pwn2Own bug unwarranted because it was already patched**

 				 			 				                  				 				                By [Gregg Keizer]("http://www.computerworld.com/s/author/9000163/Gregg+Keizer")
                                                         												March 13, 2012 01:07 PM ET
 								 				                                   					                                                    	                                                                                                                                                                  				                                      
                                                                                                                                                    	  	                  		          		                                                           	              	                                                                           	                  	                 		                  	                 	                 				 				 									Computerworld -  Mozilla on Monday announced it was postponing the release of Firefox  11, but changed its mind today, saying that the browser upgrade would go  out on schedule.
  

---

### Post by cheekybuddha on 2012-03-14
> **SilverWave said:**
> I have disabled the Maverick Nightly PPA
```
 sudo add-apt-repository ppa:silverwave/testing1
```[One Nightly A Week #2 - Maverick]("https://launchpad.net/%7Esilverwave/+archive/testing2")
Hi,

If I am using maverick, what do I need to do to get nightlies/dailies(thunderbird)?

Should I replace my ppa's with silverware/testing1 or just choose a lucid or natty ppa?

Please advise.

TIA,

d

---

### Post by SilverWave on 2012-03-14
> **cheekybuddha said:**
> Hi,

If I am using maverick, what do I need to do to get nightlies/dailies(thunderbird)?

Should I replace my ppa's with silverware/testing1 or just choose a lucid or natty ppa?

Please advise.

TIA,

d


hmm I only do Firefox here...

---

### Post by SilverWave on 2012-03-14
[[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox-trunk - 14.0~a1~hg20120313r88953-0ubuntu1~umd2]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+sourcepub/2305100/+listing-archive-extra")
[[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox-trunk - 14.0~a1~hg20120313r88953-0ubuntu1~umd2~oneiric       ]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+sourcepub/2305101/+listing-archive-extra")
[[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox-trunk - 14.0~a1~hg20120313r88953-0ubuntu1~umd2~natty       ]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+sourcepub/2305102/+listing-archive-extra")
[[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox-trunk - 14.0~a1~hg20120313r88953-0ubuntu1~umd2~natty       ]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+sourcepub/2305102/+listing-archive-extra")

:-)

---

### Post by SilverWave on 2012-03-14
Interesting...

[Firefox 11 is Smaller and Faster]("http://autonome.wordpress.com/2012/03/14/firefox-11-is-smaller-and-faster/")

> We quietly shipped Firefox 11 with a bunch of performance fixes that  both reduce the amount of memory that Firefox uses, and improve the  responsiveness of it’s user interface.
 These types of changes are not easy to talk about. Often they’re very  technical, and meaningless to anyone but the developers involved, which  is probably why we usually don’t enumerate them in the the [release notes]("http://www.mozilla.org/en-US/firefox/11.0/releasenotes/") or other public announcements.

---

### Post by SilverWave on 2012-03-14
> Kwjor 		  		[ 			March 14, 2012 at 8:49 am]("http://autonome.wordpress.com/2012/03/14/firefox-11-is-smaller-and-faster/#comment-1430")		
  		Say, whatever happened to Chrome-style process separation, i.e.  with different processes for different tabs?  Is that still on the  table?
  		 		[Reply]("http://autonome.wordpress.com/2012/03/14/firefox-11-is-smaller-and-faster/?replytocom=1430#respond")


[> [URL="http://gravatar.com/mrlachatte"]Josh Matthews]("http://gravatar.com/mrlachatte") 		  		[/URL][ 			March 14, 2012 at 11:02 am]("http://autonome.wordpress.com/2012/03/14/firefox-11-is-smaller-and-faster/#comment-1434")		
  		Kwjor – that was shelved in November or December, as it was a very  long-term project which required significant resource investment,  promised to break the vast majority of existing addons, and did not  promise equivalently extraordinary gains in responsiveness, etc. We  decided to invest the engineering efforts required in working on a  number of other projects that promised much more tangible and  quantifiable responsiveness benefits in a much quicker timeframe.  Project Snappy is the result of that decision.


hmm...

---

### Post by cheekybuddha on 2012-03-15
> **SilverWave said:**
> hmm I only do Firefox here...

Sorry, I should have been clearer! I'm after Firefox Nightlies and Thuderbird Dailies!

I just wondered if you knew whether I could use a different Firefox Nightly build on Maverick (eg Natty) or if it might cause issues.

What is the build at the top of your list with no Ubuntu version - is it a generic build, or maybe it's for Precise?

d

---

### Post by SilverWave on 2012-03-15
> **cheekybuddha said:**
> Sorry, I should have been clearer! I'm after Firefox Nightlies and Thuderbird Dailies!

I just wondered if you knew whether I could use a different Firefox Nightly build on Maverick (eg Natty) or if it might cause issues.

What is the build at the top of your list with no Ubuntu version - is it a generic build, or maybe it's for Precise?

d


[Original packages from [ubuntu-mozilla-daily]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa?field.series_filter=")]

If  you create your own PPA then you do get some options on how you copy packages from Ubuntu-mozilla-daily 

e.g.

> [View package details]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+packages") [>]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+packages") [Copy packages]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+copy-packages")

                         Select the destination PPA.
                    
                                                                                                                                                                                                         Destination series:                                                            
                         Select the destination series.
                    
                                                                                                                                                                                                         Copy options:                                 Rebuild the copied sources
 Copy existing binaries                 
                         How the selected sources should be copied to the destination archive.
                    
                                                                                                                                                            or                 [                   Cancel]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+packages")But I haven't really played about with these settings much...

I would recommend a VM and a bit of testing before using such a package (if it even builds successfully).

I would say you would be better off getting your Nightly  from Mozilla direct.

[http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-trunk/](http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-trunk/)

---

### Post by SilverWave on 2012-03-15
Hmm interesting...

[Mozilla will start Firefox silent updates in June]("http://www.computerworld.com/s/article/9225235/Mozilla_will_start_Firefox_silent_updates_in_June?source=rss_latest_content&utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+computerworld%2Fnews%2Ffeed+%28Latest+from+Computerworld%29")

 > "Updates will now be downloaded and installed silently in the background," wrote Nyman in a Wednesday post to the [Hacks Mozilla blog]("http://hacks.mozilla.org/2012/03/firefox-in-2011-firefox-plans-for-2012/"). "Silent updates are currently planned to land in Firefox 13."

---

### Post by SilverWave on 2012-03-15
**Firefox Beta - Precise    **


                          
[LIST=1]
[*]     [SilverWave]("https://launchpad.net/%7Esilverwave")
[*]     Firefox Beta - Precise
[/LIST]
                                                
                                                                    
                                                                              
     **PPA description**

   
   The latest firefox Beta - No other packages.
Copied from firefox-next, Ubuntu Security Proposed & Ubuntu Mozilla Security.
Warning! I am impatient and I copy packages before they have been fully tested.
I even copy packages when status reads "Publishing has been disabled for this archive".
I can do this in good conscience as these ppa's are for my personal use, although I have no problem with others using them.
______________________________
 Firefox Beta - Precise #testing8
firefox only
______________________________
 sudo add-apt-repository ppa:silverwave/testing8
sudo apt-get update
sudo apt-get install firefox
______________________________
 Disclaimer: Use at your own risk, no guarantees.
______________________________

---

### Post by SilverWave on 2012-03-15
> **SilverWave said:**
> **Firefox Beta - Precise    **
**PPA description**

   The latest firefox Beta - No other packages.
Copied from firefox-next, Ubuntu Security Proposed & Ubuntu Mozilla Security.
Warning! I am impatient and I copy packages before they have been fully tested.
I even copy packages when status reads "Publishing has been disabled for this archive".
I can do this in good conscience as these ppa's are for my personal use, although I have no problem with others using them.
______________________________
 Firefox Beta - Precise #testing8
firefox only
______________________________
 sudo add-apt-repository ppa:silverwave/testing8
sudo apt-get update
sudo apt-get install firefox
______________________________
 Disclaimer: Use at your own risk, no guarantees.
______________________________


> Changes for the versions:
Installed version: 11.0+build1-0ubuntu1
Available version: 12.0~b1+build2-0ubuntu0.12.04.1~mfn2

So far so good ;-)

My Tree Style Tabs look a little fat but I can live with that...

---

### Post by SilverWave on 2012-03-16
[[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox - 12.0~b1+build2-0ubuntu0.12.04.1~mfn2]("https://launchpad.net/%7Emozillateam/+archive/firefox-next/+sourcepub/2307470/+listing-archive-extra")
[[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox - 12.0~b1+build2-0ubuntu0.11.10.1~mfn2       ]("https://launchpad.net/%7Emozillateam/+archive/firefox-next/+sourcepub/2307468/+listing-archive-extra")
[[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox - 12.0~b1+build2-0ubuntu0.11.04.1~mfn2       ]("https://launchpad.net/%7Emozillateam/+archive/firefox-next/+sourcepub/2307472/+listing-archive-extra")
[[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox - 12.0~b1+build2-0ubuntu0.10.04.1~mfn1       ]("https://launchpad.net/%7Emozillateam/+archive/firefox-next/+sourcepub/2307474/+listing-archive-extra")

So far so good... YMMV

---

### Post by SilverWave on 2012-03-17
[Compatible by Default and the Add-ons Compatibility Reporter]("http://brian.kingsonline.net/talk/2012/02/compatible-by-default-and-the-add-ons-compatibility-reporter/")

> In short, the ACR settings that make add-ons compatible are  themsleves not compatible with Compatible By Default in Firefox. So  these settings have been disabled in ACR, and the extension acts now  only as a reporting tool. To put it another way, ACR no longer makes old  add-ons work, deferring completely this task to Firefox. Compatible By Default does not enable all extensions. The types not enabled include the following:
 
[LIST=1]
[*]Add-ons marked to work with a Firefox version less than 4.0
[*]Add-ons with binary components
[*]Add-ons explicitly marked by the author as incompatible, i.e. opt-out of Compatible By Default
[*]Add-ons tested and determined to not be compatible with a given version of Firefox, and marked as incompatible by Mozilla
[*]Themes
[/LIST]


---

### Post by SilverWave on 2012-03-17
[Solving Firefox’s add-on compatibility problem  "I want to upgrade Firefox, but my add-ons won't be compatible."]("http://theunfocused.net/2011/11/19/solving-firefoxs-add-on-compatibility-problem/")
> 
*"I want to upgrade Firefox, but my add-ons won't be compatible."*
 This makes me sad. And it's a problem that's been magnified by the  switch to rapid release. One of the strengths of Firefox is it's rich  selection of add-ons. In fact, [85% of Firefox users]("https://blog.mozilla.com/addons/2011/06/21/firefox-4-add-on-users/") have chosen to install an add-on. On average, those users have 5 add-ons installed. Firefox users *really*  love their add-ons. So it's not surprising that they get frustrated  when one of their favorite add-ons gets disabled because it's not marked  as being compatible with the new Firefox update they just installed.
 So I started working on a [project]("https://wiki.mozilla.org/Features/Add-ons/Add-ons_Default_to_Compatible")  to fix it. The end result will be that most add-ons will automatically  be compatible with Firefox, starting with (hopefully) Firefox 10.


---

### Post by SilverWave on 2012-03-17
[Add-on Compatibility Reporter 1.1 by Mozilla]("https://addons.mozilla.org/en-US/firefox/addon/add-on-compatibility-reporter/")
> 
**Update to ACR:** Due to "Default To Compatible" changes  in Firefox 10+, the ACR's functionality has changed. It can no longer be  used for force add-ons to be installed. [Read more about the changes.]("http://brian.kingsonline.net/talk/2012/02/compatible-by-default-and-the-add-ons-compatibility-reporter/")Have to agree with the review below:

> **[B]From useful to useless in one single update...**                 Rated 1 out of 5 stars            [/B]

                by [Scorzonera]("https://addons.mozilla.org/en-US/firefox/user/948715/") on March 11, 2012            ·     [permalink]("https://addons.mozilla.org/en-US/firefox/addon/add-on-compatibility-reporter/reviews/340300/")   
   "The ACR's functionality has changed. It can no longer be used for force add-ons to be installed."

Wouldn't be such a problem if this did it's job:
""Default To Compatible" changes in Firefox 10+"

I  don't mind reporting add-on's that work/don't work anymore, but if  add-on's clearly work but cannot be activated by the built in 'Default  To Compatible' feature, than users are left with quite a useless  reporting tool with this add-on.

I understand the developer's  reasons for this decision, I also understand that as a user I have  nothing to gain with it. So, as a user I'll give two stars for trying to  get an active community involvement, minus three stars for it's more  than useless implementation because reporting working add-on's isn't  visible in an actual working add-on as end result. Leaving that same  community empty handed.

And again: Useful workarounds come from  the community itself, developers have placed themselves outside that  same community. That means I'll have to give this add-on a one star  rating.


---

### Post by SilverWave on 2012-03-17
hmmm Tab Utilities 1.1.3, some of the compatibilities reports say it is OK....

But how do I test it if its marked non-compatible?

Add-on Compatibility Reporter no longer allows the user to force compatibility.

Oh. Dear. Me.

This sound just like the bad old days :-(

---

### Post by SilverWave on 2012-03-17
> **SilverWave said:**
> hmmm Tab Utilities 1.1.3 some of the compatibilities reports say is OK....

But how do I test it if its marked non-compatible?

Add-on Compatibility Reporter no longer allows the user to force compatibility.

Oh. Dear. Me.

This sound just like the bad old days :-(


Hmm the advice seems a little confused...

> 
**Reviews**

                            **                       [B]Great extension**                       Rated 5 out of 5 stars          [/B]

                    by [mkouman]("https://addons.mozilla.org/en-US/firefox/user/5863476/") on March 17, 2012          ·           [permalink]("https://addons.mozilla.org/en-US/firefox/addon/tab-utilities/reviews/341238/")         
         It is a great tool, but the only draw  back is the incompatibility issues with the new FF versions. Problem can  be solved by disabling compatibility check  (extensions.checkCompatibility)
               
                    **                       [B]Not compatible yet with FF 12 beta**                       Rated 4 out of 5 stars          [/B]

                    by [Ralphbusdriver]("https://addons.mozilla.org/en-US/firefox/user/791106/") on March 16, 2012          ·           [permalink]("https://addons.mozilla.org/en-US/firefox/addon/tab-utilities/reviews/341174/")         
         I miss it.  Hope the Tab Utilities addon  updates automatically when it is made compatible with new FF releases.   I'll keep checking back.
               
                    **                       [B]Try keeping up**                       Rated 4 out of 5 stars          [/B]

                    by [Martijn]("https://addons.mozilla.org/en-US/firefox/user/5716612/") on March 16, 2012          ·           [permalink]("https://addons.mozilla.org/en-US/firefox/addon/tab-utilities/reviews/341090/")         
         Very nice add-on, have been using it for quite a while, but:

Would  be nice if you updated the add-on to newer firefox versions _before_  these versions are released instead of afterwards. At he moment we have  to postpone updating FF only because this add-on hasn't been updated  yet. (All my other add-ons are already compatible. (And I use a LOT of  them.)



---

### Post by SilverWave on 2012-03-17
> **SilverWave said:**
> hmmm Tab Utilities 1.1.3 some of the compatibilities reports say it is OK....

But how do I test it if its marked non-compatible?

Add-on Compatibility Reporter no longer allows the user to force compatibility.

Oh. Dear. Me.

This sound just like the bad old days :-(

Ah Hah!

Here we go:

extensions.checkCompatibility.12.0 = false
extensions.checkCompatibility.12.0a = false
extensions.checkCompatibility = false

I had uninstalled it and previously the site would not allow me to reinstall.

After the addition of the preferences above I was allowed to install and all looks OK so far.

---

### Post by ron999 on 2012-03-17
Hi
Something broke when Firefox-12 b1 from PPA was updated to build 2.
Ubuntu Natty.
Is there a problem with the PPA build?

---

### Post by SilverWave on 2012-03-17
> **ron999 said:**
> Hi
Something broke when Firefox-12 b1 from PPA was updated to build 2.
Ubuntu Natty.
Is there a problem with the PPA build?


Hmm 

Haven't got any natty boxes around so I tried an install on a old VM...
Looks OK but the this is a 64bit OS...
.

---

### Post by SilverWave on 2012-03-17
> **SilverWave said:**
> Hmm 

Haven't got any natty boxes around so I tried an install on a old VM...
Looks OK but the this is a 64bit OS...
.

I'm downloading natty 32bit and I'll see how we get on with that and post my results later.

---

### Post by SilverWave on 2012-03-17
> **ron999 said:**
> Hi
Something broke when Firefox-12 b1 from PPA was updated to build 2.
Ubuntu Natty.
Is there a problem with the PPA build?

Looks as if the problem is at your end and not the PPA...

Tested in a newly built VM all working OK.

---

### Post by ron999 on 2012-03-17
> **SilverWave said:**
> Looks as if the problem is at your end and not the PPA...

Tested in a newly built VM all working OK.

Hi
Thanks for testing that.
I don't know what went wrong.
Fixed it by tinkering and using -f.:)

---

### Post by SilverWave on 2012-03-18
Hah one little change you would think...

[Last Comment Bug 419231 - The styling of the Customize Toolbar window could be improved]("https://bugzilla.mozilla.org/show_bug.cgi?id=419231")

Made me smile ;-)

---

### Post by SilverWave on 2012-03-18
> **ron999 said:**
> Hi
Thanks for testing that.
I don't know what went wrong.
Fixed it by tinkering and using -f.:)

No problem just glad you have installed it successfully  :-)

---

### Post by SilverWave on 2012-03-19
[H.264]("http://blog.lizardwrangler.com/2012/03/18/video-user-experience-and-our-mission/")

Very disappointing.

> 
We’ve declined to adopt a technology that improves user experience in  the hopes this will bring greater user sovereignty.  Not many would try  this strategy, but we did.  Brendan’s [piece]("http://hacks.mozilla.org/2012/03/video-mobile-and-the-open-web/")  details why our current approach of not supporting encumbered codec  formats hasn’t worked, and why today’s approach regarding existing  encumbered formats is even less likely to work in the future.

Oh well it was worth a shot.

---

### Post by SilverWave on 2012-03-22
[[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox - 12.0~b1+build2-0ubuntu0.12.04.1~mfn2]("https://launchpad.net/%7Esilverwave/+archive/testing8/+sourcepub/2308717/+listing-archive-extra")
[[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox - 12.0~b2+build1-0ubuntu0.11.10.1~mfn1       ]("https://launchpad.net/%7Esilverwave/+archive/testing7/+sourcepub/2321332/+listing-archive-extra")
[[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox - 12.0~b2+build1-0ubuntu0.11.04.1~mfn1       ]("https://launchpad.net/%7Esilverwave/+archive/testing4/+sourcepub/2321333/+listing-archive-extra")
[[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox - 12.0~b2+build1-0ubuntu0.10.04.1~mfn1       ]("https://launchpad.net/%7Esilverwave/+archive/testing6/+sourcepub/2321334/+listing-archive-extra")


Time to test... :-)

---

### Post by SilverWave on 2012-03-22
[[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox-trunk - 14.0~a1~hg20120322r90003-0ubuntu1~umd1]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+sourcepub/2321120/+listing-archive-extra") Currently building
[[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox-trunk - 14.0~a1~hg20120322r90003-0ubuntu1~umd1~oneiric       ]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+sourcepub/2321121/+listing-archive-extra")Currently building
[[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox-trunk - 14.0~a1~hg20120320r89816-0ubuntu1~umd1~natty       ]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+sourcepub/2318060/+listing-archive-extra")
[[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox-trunk - 14.0~a1~hg20120320r89816-0ubuntu1~umd1~lucid       ]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+sourcepub/2318061/+listing-archive-extra")

Here we are for this week...

---

### Post by chrisccoulson on 2012-03-22
> **SilverWave said:**
> [[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox - 12.0~b1+build2-0ubuntu0.12.04.1~mfn2]("https://launchpad.net/%7Esilverwave/+archive/testing8/+sourcepub/2308717/+listing-archive-extra")
[[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox - 12.0~b2+build1-0ubuntu0.11.10.1~mfn1       ]("https://launchpad.net/%7Esilverwave/+archive/testing7/+sourcepub/2321332/+listing-archive-extra")
[[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox - 12.0~b2+build1-0ubuntu0.11.04.1~mfn1       ]("https://launchpad.net/%7Esilverwave/+archive/testing4/+sourcepub/2321333/+listing-archive-extra")
[[IMG]https://launchpad.net/@@/package-source[/IMG]         firefox - 12.0~b2+build1-0ubuntu0.10.04.1~mfn1       ]("https://launchpad.net/%7Esilverwave/+archive/testing6/+sourcepub/2321334/+listing-archive-extra")

Time to test... :-)

Can you please stop publishing packages with my name on before I've had a chance to test them (and before Mozilla releases them)? :(

If you do, can you please make it clear at the top of the thread that this is not the official way to test the Firefox beta in Ubuntu, and direct them to the official PPA that you're copying them from.

People with the Flash plugin installed are going to struggle upgrading from your PPA in any case

---

### Post by lovinglinux on 2012-03-22
[color="red"]this tutorial is outdated[/color]

---

