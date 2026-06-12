---
title: "libre office 4.3.0"
date: 2014-07-31
forum: New to Ubuntu
---

### Post by Val87 on 2014-07-31
Hi Guys,
I installed a fresh copy of Ubuntu 14.04 64. 
It comes with Libre office 4.2.4.2.

Would like to upgrade to available 4.3.0 can i do that via terminal? 

Thanks

---

### Post by monkeybrain20122 on 2014-07-31
Yes, install from this ppa [https://launchpad.net/~libreoffice/+archive/ubuntu/ppa](https://launchpad.net/~libreoffice/+archive/ubuntu/ppa)
LO 4.3 is not there yet, just wait for may be a few days it should be there.

---

### Post by Val87 on 2014-07-31
That is weird. 
If you go to Libre homepage it says download 4.3. Thought its there just go to their website you will see.
So i will be able just to update it in few days from terminal?

---

### Post by Impavidus on 2014-07-31
Ubuntu 14.04 will stay at LO 4.2, there will only be occasional bugfixes. If you install the [PPA]("https://help.ubuntu.com/community/PPA") mentioned by monkeybrain you'll get updated to 4.3 as soon as it has been pushed into that PPA. This may take a few days from the moment the release has been anounced on LO's website.

---

### Post by Val87 on 2014-07-31
I have no idea how to do the PPA thing ... as i am a noob... so ill be better of probably to leave it as it is.

---

### Post by monkeybrain20122 on 2014-07-31
It is very simple to upgrade LO with the ppa
1. the command line way, open a terminal session and type one after the other
```
sudo add-apt-repository ppa:libreoffice/ppa
sudo apt-get update
sudo apt-get upgrade
```

2. gui way
find software & update from the dash, open it, go to other software, click Add and put the line
```
ppa:libreoffice/ppa
```
in the textbox, reload and you will get new version of LO when you update normally via synaptic or update-manager (provided there is a new version of course, as noted it will take a few days for LO 4.3 to be pushed to the ppa)

---

### Post by Val87 on 2014-07-31
Thanks, i will try that in a couple of days when the 4.3 is out! :)

---

### Post by monkeybrain20122 on 2014-08-05
LO 4.3 is avaliable from the LO ppa today (has been available for a few days in the LO4.3 ppa)

---

### Post by Dr. McKay on 2014-08-06
> **Impavidus said:**
> Ubuntu 14.04 will stay at LO 4.2, there will only be occasional bugfixes. If you install the [PPA]("https://help.ubuntu.com/community/PPA") mentioned by monkeybrain you'll get updated to 4.3 as soon as it has been pushed into that PPA. This may take a few days from the moment the release has been anounced on LO's website.

Ok, so updating to 4.3 with PPA is easy. But... is it safe ?  Can it potentially break something ?
Can we just install new software versions on a LTS install or should we think twice before we do it ?
In other words, is it worth it ?

---

### Post by The Spectre on 2014-08-06
There is always a chance but I have been using the LibreOffice PPA since Ubuntu 12.10 and I have never had a problem.
 
 
 I also use the PPA's for VLC, XBMC, Gimp and a couple of others and I haven’t had any problems with them either.
 
 
 If you stick with Official PPA's of reputable software you should be fine.

---

### Post by ian-weisser on 2014-08-06
> **Dr. McKay said:**
> Can it potentially break something ?

Yes. PPAs are NOT SUPPORTED. You add them and use them at your own risk.

Software in the Ubuntu repositories is supported...but also is not usually updated to fresh upstream releases during a 6-month Ubuntu release cycle.
Fresh versions of software are currently being added to the 14.10 repositories. 14.10 will be released in October 2014.

> **Dr. McKay said:**
> Can we just install new software versions on a LTS install or should we think twice before we do it ?

In the Ubuntu software model, you get *supported* new upstream releases every 6 months: April and October (except LTS).
LTS gets no new upstream application releases for two years (with exceptions, of course). It's intended for users who DON'T want the latest software.  
You can, of course, add anything you want anytime you wish --it's your system-- but it will be *unsupported*.

If you really want newer software, migrate to 14.10 in October, and forget about using LTS. That's what the semiannual releases are for.

---

### Post by Dr. McKay on 2014-08-06
> **ian-weisser said:**
> Yes. PPAs are NOT SUPPORTED. You add them and use them at your own risk.

Software in the Ubuntu repositories is supported...but also is not usually updated to fresh upstream releases during a 6-month Ubuntu release cycle.
Fresh versions of software are currently being added to the 14.10 repositories. 14.10 will be released in October 2014.



In the Ubuntu software model, you get *supported* new upstream releases every 6 months: April and October (except LTS).
LTS gets no new upstream application releases for two years (with exceptions, of course). It's intended for users who DON'T want the latest software.  
You can, of course, add anything you want anytime you wish --it's your system-- but it will be *unsupported*.

If you really want newer software, migrate to 14.10 in October, and forget about using LTS. That's what the semiannual releases are for.

Well then, I made the wrong choice in opting for Ubuntu 14.04. I was under the impression that the most popular apps like web browsers, VLC, LibreOffice, etc. would get regular updates. 
Perhaps I should have gone with Mint after all, which will be following a different upgrade patch from Mint 17 onwards. I suppose Mint 17 users WILL continue to get all the latest software until 2nd quarter 2016, when a new LTS is released.

---

### Post by cwmoser on 2014-08-06
Just got Libre Office 4.3 this morning.

$  sudo  apt-get  dist-upgrade

Carl

---

### Post by monkeybrain20122 on 2014-08-16
> **Dr. McKay said:**
> Well then, I made the wrong choice in opting for Ubuntu 14.04. I was under the impression that the most popular apps like web browsers, VLC, LibreOffice, etc. would get regular updates. 
Perhaps I should have gone with Mint after all, which will be following a different upgrade patch from Mint 17 onwards. I suppose Mint 17 users WILL continue to get all the latest software until 2nd quarter 2016, when a new LTS is released.

The LibreOffice ppa is managed by the same people who package LO for Ubuntu release. I wouldn't  worry about it. I don't see how Mint will get the latest software since it is based on Ubuntu unless they package the applications themselves but that is not likely. If what you say is true I think they just activate some ppas by default. If it is LMDE then you will get continue updates but not the latest (Debian testing is sort of 'rolling' but old because by the time when software gets to testing it is hardly 'latest')

---

### Post by ian-weisser on 2014-08-16
> **Dr. McKay said:**
> Well then, I made the wrong choice in opting for Ubuntu 14.04. I was under the impression that the most popular apps like web browsers, VLC, LibreOffice, etc. would get regular updates. 

Well, no, you didn't make a wrong choice.
There's no "14.04 LTS" and "14.04 Non-LTS." It's all 14.04. Same install image. One changed setting is the difference. You installed the correct version of Ubuntu.
You can change it (if, indeed, it needs to be changed) easily.

14.04 will be superseded by 14.10. Regular users will upgrade to 14.10 and get updated supported software.
LTS users will ignore 14.10 and remain on 14.04 for until 16.04. They will get some updated (security, backport) software, but most new-release software will come from unsupported PPAs.

The whole point of Ubuntu's six-month releases is that you get all the updated system and software, and it's *all tested together* before release. Any distro that promises both great stability *and* the latest supported software simply sounds (and is) too good to be true.

---

