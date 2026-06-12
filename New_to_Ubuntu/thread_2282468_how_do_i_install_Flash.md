---
title: "how do i install Flash?"
date: 2015-06-14
forum: New to Ubuntu
---

### Post by mlvmhn on 2015-06-14
I have recently installed Flash on my laptop, but i need to install Flash. 

On Adobe website, there is several options for Linux. 

Which one is best and easiest to install?

How do i install Flash?

---

### Post by Steve_Horan on 2015-06-14
Run below:
> sudo apt-get install flashplugin-installer

---

### Post by deadflowr on 2015-06-14
Install the package from the software center Adobe Flash Plugin.
It'll automatically install and keep updating flash just like any other update.

Note though, that flash on linux is old version 11.2.XXXX.

There are a few ways to use newer flash but they can be cumbersome.
One is installing the Google Chrome Web Browser.
Another is installing the package pepperflashplugin-nonfree.
Both the chrome method and the pepperflashplugin-nonfree method are browser plugins only, as from what I can tell.

And another is adding a specialized package known as pipelight.
Explained here:
[http://pipelight.net/cms/about.html](http://pipelight.net/cms/about.html)

---

### Post by sammiev on 2015-06-14
Hi,

Use your software package manager and do a search under flash.

Choose flashplugin-installer or Adobe Flash Player plugin installer.

You really never told us which Browser you are using.

---

### Post by LastDino on 2015-06-14
I would personally only recommend sticking with Chrome though. And if you're looking for flash just to play Youtube, please go with HTML5. Even an updated Flash is not considered to be secure, and the one Ubuntu has is quite old. So, you can imagine.

---

### Post by mlvmhn on 2015-06-14
Now  i have  installed it from Software Center, and it is working fine.

---

### Post by ajgreeny on 2015-06-14
For the last couple of months I have been using only the latest version of flash in both Chromium and Firefox.

Chromium is very easy; just install pepperflashplugin-nonfree.
Firefox requires you to uninstall whatever flashplugin installer you have just added, add a PPA repository and use terminal, but you can easily copy these three commands one by one.
```
sudo add-apt-repository ppa:nilarimogard/webupd8
sudo apt-get update
sudo apt-get install freshplayerplugin
```

I have had no problems with this and my chromium and firefox are both using flash 17.0.0.188

Worth a try I think?  If it does not work you can just uninstall freshplayerplugin and install and use the version you have now.

---

### Post by monkeybrain20122 on 2015-06-14
> **LastDino said:**
> I would personally only recommend sticking with Chrome though. And if you're looking for flash just to play Youtube, please go with HTML5. Even an updated Flash is not considered to be secure, and the one Ubuntu has is quite old. So, you can imagine.

Flash 11.2 is quite old but it does get security updates. Just that the version is not updated. There are many methods to watch Youtube without flash, that should be the least of the concerns. It may be a bit tricky on other sites than Youtube. mpv add on for Firefox is the best non best method that works on a lot of video streaming sites. 
[https://addons.mozilla.org/en-us/firefox/addon/watch-with-mpv/](https://addons.mozilla.org/en-us/firefox/addon/watch-with-mpv/)

You need to have up to date mpv and Youtube-dl in your system.
Get mpv from 
[https://launchpad.net/~mc3man/+archi...u/trusty-media]("https://launchpad.net/%7Emc3man/+archive/ubuntu/trusty-media")
and youtube-dl from 
[https://launchpad.net/~nilarimogard/...ubuntu/webupd8]("https://launchpad.net/%7Enilarimogard/+archive/ubuntu/webupd8")

---

### Post by monkeybrain20122 on 2015-06-14
> **ajgreeny said:**
> For the last couple of months I have been using only the latest version of flash in both Chromium and Firefox.

Chromium is very easy; just install pepperflashplugin-nonfree.
Firefox requires you to uninstall whatever flashplugin installer you have just added, add a PPA repository and use terminal, but you can easily copy these three commands one by one.
```
sudo add-apt-repository ppa:nilarimogard/webupd8
sudo apt-get update
sudo apt-get install freshplayerplugin
```

I have had no problems with this and my chromium and firefox are both using flash 17.0.0.188

Worth a try I think?  If it does not work you can just uninstall freshplayerplugin and install and use the version you have now.

Current flash version in Chrome 18.0.0.160. Looks like pepperflashplugin-nonfree is not being updated. There are a few issues in freshplayerplugin 0.30 since updated last week. So if your current version is working you should not upgrade the package for a week or so [https://github.com/i-rinat/freshplayerplugin/issues](https://github.com/i-rinat/freshplayerplugin/issues)

Edited: OK, it seems that in Firefox's addon > plugin page it still shows flash 17, but if right click video it shows flash 18.

---

### Post by LastDino on 2015-06-15
> **monkeybrain20122 said:**
> Flash 11.2 is quite old but it does get security updates. Just that the version is not updated. There are many methods to watch Youtube without flash, that should be the least of the concerns. It may be a bit tricky on other sites than Youtube. mpv add on for Firefox is the best non best method that works on a lot of video streaming sites. 
[https://addons.mozilla.org/en-us/firefox/addon/watch-with-mpv/](https://addons.mozilla.org/en-us/firefox/addon/watch-with-mpv/)

You need to have up to date mpv and Youtube-dl in your system.
Get mpv from 
[https://launchpad.net/~mc3man/+archi...u/trusty-media]("https://launchpad.net/%7Emc3man/+archive/ubuntu/trusty-media")
and youtube-dl from 
[https://launchpad.net/~nilarimogard/...ubuntu/webupd8]("https://launchpad.net/%7Enilarimogard/+archive/ubuntu/webupd8")


Thanks for the info and the links!

---

### Post by mattharris4 on 2015-06-17
> **ajgreeny said:**
> For the last couple of months I have been using only the latest version of flash in both Chromium and Firefox.

Chromium is very easy; just install pepperflashplugin-nonfree.
Firefox requires you to uninstall whatever flashplugin installer you have just added, add a PPA repository and use terminal, but you can easily copy these three commands one by one.
```
sudo add-apt-repository ppa:nilarimogard/webupd8
sudo apt-get update
sudo apt-get install freshplayerplugin
```

I have had no problems with this and my chromium and firefox are both using flash 17.0.0.188

Worth a try I think?  If it does not work you can just uninstall freshplayerplugin and install and use the version you have now.

Pepper Flash seems to work fine with recent versions of Firefox for me.  I know I don't recall installing Fresh on any of my computers although if it works go for it, there can be more than one solution to a problem.  I actually have more problems with HTML5 than with Flash and then only on a couple of adult rated sites (I am reluctant to say which ones as some teenagers do have an interest in computers and may use this site -- at least one mod seems to agree with me on this, I know this stymies anyone attempting to help with the issue) that seem to only work with Microsoft Explorer, Firefox causes these videos to skip and jump when using recent Windows versions as well.  

YouTube works fine for me although my understanding is videos uploaded after some date late last year run on HTML5, I read that Google is gong to convert the older videos as well but I don't know how that effort is coming along or how far back date-wise they are in doing so.

---

