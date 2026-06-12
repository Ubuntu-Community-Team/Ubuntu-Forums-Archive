---
title: "Viewing Protected Content Online"
date: 2015-10-13
forum: New to Ubuntu
---

### Post by jacob91 on 2015-10-13
Hello all,

I am a total newbie to the Linux world, so I am trying to read and absorb everything I can.  But in order to speed up the process and also make the wife a little happier I have attempted to re-purpose an old PC to be dedicated to our TV.

We are total cheapskates and so we like to view some of the content online from the networks on their website.  My grandparents have a DirecTV subscription but do not use any of their online features, so we use their login credentials to sign into sights like abc.com in order to watch the current season of various series.

The problem I have is that I wiped the computer and installed Xubuntu, everything seems to work great except some websites like HULU will not play their content.  With ABC.com it will ask me to sign in with my DirectTV credentials so I do, the page reloads and we are back at square one, it is just a viscous cycle.  Then on directv.com I cannot use their WatchDirecTV feature at all.  Is this a Linux incompatibility problem?  I have installed the latest version of Flash Player I think, because I had problems with even youtube, but now it plays fine.

Any Ideas?

Do I need to give more information? If so, what?


Thanks in advance,
Jake

---

### Post by Dennis N on 2015-10-13
I and others solved this problem by installing HAL. There is a thread about the issue affecting Hulu here, but it is not just a Hulu problem:
[http://ubuntuforums.org/showthread.php?t=2290743](http://ubuntuforums.org/showthread.php?t=2290743)
The solution is given in post #39.
With that solution, I can now watch my cable systems internet video on demand, and other links like syfy.com, etc. Works for Firefox.

---

### Post by jim_deadlock on 2015-10-13
Installing Hal will fix many issues but not all...

The final  version of Flash for Linux (which still gets security patches) is 11.2  but the Windows version is now up to v. 19 and you'll find that some  websites refuse to allow older versions. Chrome (not Chromium) for Linux  has the latest Flash version built-in, but unfortunately the plugin  does not support DRM so you can't use it on many streaming sites. The  next step is to install pipelight-plugin here: [http://pipelight.net/cms/installation.html](http://pipelight.net/cms/installation.html) and then:

```
sudo pipelight-plugin --enable flash
```

This  will give you the latest Flash in Firefox with DRM support. This is  supposedly the complete solution. However, I'm still having problems: 
[URL="http://ubuntuforums.org/showthread.php?t=2298623"]http://ubuntuforums.org/showthread.php?t=2298623
[/URL]
All in all, Flash in Linux is becoming a pain.

---

### Post by SeijiSensei on 2015-10-13
You may also find that you need to use a Firefox add-on to spoof your "User-Agent" string if you use Silverlight via pipelight.  I use [UA Control]("https://addons.mozilla.org/en-us/firefox/addon/uacontrol/") to tell Netflix and Amazon Instant Video that my computer is using:
```
Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:41.0) Gecko/20100101 Firefox/41.0
```

---

### Post by jacob91 on 2015-10-14
Success!!

I wish I would have asked here two weeks ago!  Thanks!

---

