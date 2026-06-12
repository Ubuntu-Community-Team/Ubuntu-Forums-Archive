---
title: "New to Ubuntu questions"
date: 2014-06-25
forum: New to Ubuntu
---

### Post by anon6 on 2014-06-25
I'm going to get a new computer and I wan't to install Ubuntu on it. However, I have a few questions:

- What things I need to do after instalation? I've read that you need to install something else to be able to play some video formats. Also I've read that the file search shows you Amazon ads and I'll want to disable it (obviusly). There are more "traps" like this?

- I've also read that there isn't any Flash Player for Firefox on Linux (it seems there's one for Chrome, but I've allways used Firefox and I wouldn't want to change it). Do I really need it? (Youtube also uses HTML5, but I don't know what will hapen with other sites) There is any good alternative?

I think these are for now. Thanks.

---

### Post by Frogs Hair on 2014-06-25
Hello and Welcome

1. The Ubuntu restricted extras package includes codec/s for audio/video formats. Amazon search results can be disabled in the privacy and security settings . 

2. A version of flash is available for Firefox , but Adobe has stopped development for Linux other than providing security updates for a limited time. There is an Youtube HTML 5 un-block extension for Firefox , Chrome , and Opera . Mozilla is working on flash alternatives including HTML 5 and Pepper.

---

### Post by Quarkrad on 2014-06-25
Why not download ubuntu onto a usb stick, or burn to a CD, and try it out on your 'old' pc?  Using this method you can 'try' ubuntu by playing it in RAM and not installing it on your pc.  You can then play with it and see what it is like, including some of your fears.  If you then have any more detailed questions you can come back to this forum.

---

### Post by buzzingrobot on 2014-06-25
> **anon6 said:**
> 

  I've read that you need to install something else to be able to play some video formats. 

At the install you will be offered the option of adding some software to handle video, music, etc.  After the install completes, install the "Ubuntu Restricted Extras" package to get Flash, more media software, Microsoft fonts, etc.

The reasons for this are a bit complex but are rooted in the open source licenses Linux uses and the closed, proprietary, nature of much media software.

> I've read that the file search shows you Amazon ads and I'll want to disable it (obviusly). 

You are not shown ads as such.  By default, Unity's desktop search includes results from Amazon.  E.g., if you search for a song by name, you will also see icons linked to songs, etc., at Amazon's site.  

The simplest way to disable this is to turn off online search, which you can do in Systems Settings. (That does also disable use of the many other potentially useful online searches available in Unity.)

Systems Setting is one of the very first places to visit, and tweak things to your liking.  Also, install "Unity Tweak Tool", which allows additional adjustment, including changing fonts and activating new themes/icons you may have installed.

---

### Post by sameermw on 2014-06-26
If you would like to install Ubuntu 14.04 here is steps to make perfect Machine. 

[http://www.webupd8.org/2014/04/10-things-to-do-after-installing-ubuntu.html](http://www.webupd8.org/2014/04/10-things-to-do-after-installing-ubuntu.html)

[http://www.omgubuntu.co.uk/2014/04/10-things-to-do-after-installing-ubuntu-14-04](http://www.omgubuntu.co.uk/2014/04/10-things-to-do-after-installing-ubuntu-14-04)

[http://www.noobslab.com/2014/04/thingstweaks-to-do-after-install-of.html](http://www.noobslab.com/2014/04/thingstweaks-to-do-after-install-of.html)

Please read these articles top to bottom before you try.

---

### Post by Rob Sayer on 2014-06-26
Many newbies don't seem to realize that there are actually 4 different GUI versions of ubuntu.

The 'default' Unity DE is the only one that includes amazon etc search in the DE search.  Which, as mentioned, can be turned off easily.  I don't like Unity, for other reasons.  I use kubuntu (KDE desktop) at home mostly.

On my netbook I have xubuntu (xfce DE) 14.04 installed.  I had lubuntu (Lxde DE) 13.10 previously and recently installed lubuntu 14.04.  But it's a frakking bugfest.  And the development is stagnant because they're porting it to a new version, which I've tried and may install when it's done.

My advice would be to download all 4 DE versions of the live CD, burn to a USB stick (much faster response), and try them all.  Don't forget to do an md5sum check on the iso files before burning.

I think the lack of support for current versions of flash in firefox is a big problem, but you can just install Chrome.  Google have a deal with Adobe so their linux version is properly supported.

FWIW, I hate the new firefox anyway.  They've made it work more like Chrome but they didn't do a very good jpb of it.  After years of using firefox Mozilla have turned me into a chrome user.

You could install Chromium instead, which is am open source version of Chrome, but I just don't see the point unless you're a real open source fanatic.  Which I'm not.  The ideal of pure open source doesn't actually exist in the real world.

---

