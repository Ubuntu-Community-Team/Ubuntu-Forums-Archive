---
title: "Wich is the latest version of Chromium Browser?"
date: 2013-06-16
forum: Recurring Discussions
---

### Post by WhiteHatGuy on 2013-06-16
Hi

I have intalled Lubuntu 13.04, I did all the updates. And my Chromium Browser sais I have:

[COLOR=#303942][FONT=Ubuntu]Version 25.0.1364.160 Ubuntu 13.04 (25.0.1364.160-0ubuntu3)
[/FONT][/COLOR]
I just need to know if this is the latest version. Cause according to this website:

[http://en.wikipedia.org/wiki/Chromium_(web_browser)](http://en.wikipedia.org/wiki/Chromium_(web_browser))

The latest version is [COLOR=#000000][FONT=sans-serif]29.0.1538.2 for 2013, so I am confused.

I need to know if I am being running all this time an old outdated Chromium Browser. I dont think that Lubuntu 13.04, with all the updates done, will come with and old outdated version of [/FONT][/COLOR][COLOR=#000000][FONT=sans-serif]Chromium Browser. That will be weird and does not make sense at all.

I am worried, cause this would be an extremely easy target for hackers.

In the future where can I check the latest version of Chromium Browser for Lubuntu? In wich website? I tried this one, but it does not provide that information:

[/FONT][/COLOR][http://www.chromium.org/Home](http://www.chromium.org/Home)

Thanks

---

### Post by vasa1 on 2013-06-17
Sorry, but it's highly unfortunate that that's the "latest" available in the standard repos. There's talk of ppas that have later versions. But you can show that you're affected on this bug page: [https://bugs.launchpad.net/ubuntu/+source/chromium-browser/+bug/1183086](https://bugs.launchpad.net/ubuntu/+source/chromium-browser/+bug/1183086)

---

### Post by Hungry Man on 2013-06-17
It's moronic that they include Chromium in the PPAs but don't update it. I don't think they even backport security issues.

---

### Post by WhiteHatGuy on 2013-06-17
WOW


Thats shocking news for me.


I always liked Chromium because its lite. And because I was able to use it in the guest (light) account. I cant do that with Google Chrome, it wont start on the guest account, cause of the problem off apparmor and the sandbox of Google Chrome.


But now that I know that, I am going to be forced to switch to Google Chrome or Firefox.


And please, dont tell me that what happen to chromium regarding updates, happen also to Google Chrome and Firefox. Because if it does, I will probably remove the internet from my computer and never surf the web again.


According to this information for Google Chrome and Firefox:


[http://en.wikipedia.org/wiki/Google_Chrome](http://en.wikipedia.org/wiki/Google_Chrome)
[https://www.google.com/intl/en/chrome/browser/](https://www.google.com/intl/en/chrome/browser/)


[http://en.wikipedia.org/wiki/Firefox](http://en.wikipedia.org/wiki/Firefox)
[http://www.mozilla.org/en-US/firefox/new/](http://www.mozilla.org/en-US/firefox/new/)


The links for the official Google Chrome and Firefox websites, allow me to download the latest stable version. I suppose that once I install these two browsers they update automatically if a new latest stable version comes up. If I have to do the updates manually over and over, OMG.


Now I got all paranoid, I am checking if is the same thing for the Kernel. And old outdated kernel all this time, full of holes, and vulnerabilities.


Hopefully not. Its sais I got a kernel 3.8.0-25-generic. I think we are good there.


[https://www.kernel.org/](https://www.kernel.org/)


Thanks guys.

---

### Post by malspa on 2013-06-17
Ubuntu isn't even keeping up with Debian Stable, which has Chromium 27!!! Not cool.

---

### Post by Hungry Man on 2013-06-17
Chrome and Firefox are maintained. No one maintains Chromium for Ubuntu. The kernel is maintained and security fixes tend to be backported, there are no issues there specific to Ubuntu. Most packages still get updates, Chromium is an exception, and it's pretty lame that they allow it to continue.

---

### Post by monkeybrain2012 on 2013-06-17
It is more lame that some people in Canonical are trying to get Chromium to replace FF as the defauly browser for Ubuntu.

---

### Post by Hungry Man on 2013-06-17
Not really, it's an understandable move given Chromium's popularity. And naturally if they made it the default they'd assign someone to update it.

---

### Post by vasa1 on 2013-06-17
Chromium has and has had a Canonical employee as "maintainer" for several months now if [this page]("https://launchpad.net/~chromium-team") is anything to go by. I don't know why Chromium stable isn't being updated. And just like there's no way to determine any browser's "true" popularity, talking of Chromium's popularity isn't meaningful. Using Chrome's supposed popularity to claim that Chromium is popular is even less meaningful.

---

### Post by malspa on 2013-06-17
Looks like someone's dropping the ball, at least right now. Whether or not Chromium becomes the default, I hope the situation gets fixed and somebody keeps Chromium updated in the Ubuntu repos. Doesn't seem to be a problem in any of the other distros I'm using here, so it seems strange to me that, as a "major" Linux distribution, Ubuntu can't stay on top of this.  Interesting bug report mentioned above by vasa1.

---

### Post by uRock on 2013-06-18
Thread has entered the realm of recurring discussions.

I highly doubt it will take Firefox's place as the default browser at this rate.

---

### Post by vasa1 on 2013-06-18
To back up the first sentence in my post #9, here's a link: [https://lists.ubuntu.com/archives/lubuntu-users/2012-November/003006.html](https://lists.ubuntu.com/archives/lubuntu-users/2012-November/003006.html)

---

### Post by malspa on 2013-06-18
> **vasa1 said:**
> To back up the first sentence in my post #9, here's a link: [https://lists.ubuntu.com/archives/lubuntu-users/2012-November/003006.html](https://lists.ubuntu.com/archives/lubuntu-users/2012-November/003006.html)

OK. So is this the PPA to use, then?  [https://launchpad.net/~cmiller/+archive/chromium-browser-stable-daily](https://launchpad.net/~cmiller/+archive/chromium-browser-stable-daily)

---

### Post by vasa1 on 2013-06-18
> **malspa said:**
> OK. So is this the PPA to use, then?  [https://launchpad.net/~cmiller/+archive/chromium-browser-stable-daily](https://launchpad.net/~cmiller/+archive/chromium-browser-stable-daily)

I'm sorry I don't know anything about that. I think OP was interested in the version available from the Software Center, in other words, no ppa.

(BTW, I use Firefox beta direct from Mozilla, Chrome beta from Google's ppa, Seamonkey from seamonkey-project.org, Chromium from the Software Center and play a little with xombrero from a lubuntu ppa.)

---

### Post by craig10x on 2013-06-18
I love Ubuntu but sometimes the way they do things like this can drive me crazy...Chromium still in version 25 with no newer versions?  It's a good thing i use Chrome...it puts a chrome ppa in your software updater and in fact i just got version 28 which was just released to the stable channel....i get the new stable like 1 day after it's available in the channel...

And that bug report about the touchpad settings changes not locking in and reverting to the default when you close the window... i reported in FEBRUARY and still hasn't been assigned to fix yet...a very obvious bug too...hasn't even been fixed in 13.10 (i checked)....unbelievable...and this is supposed to be a good replacement for windows or mac?  

Let's not forget Brasero, the default disc burner...hasn't worked right in years...even XF-BURN is far far superior and of course K3b as well...

Or the MS-Core Fonts agreement not popping up right when downloading Ubuntu Restricted Extras (that windows hides underneath the software center window so it can be easy to miss) broken for quite a long time now...and still broken on 13.10 as well...all obvious problems...

I wish they would get on the stick...Ubuntu has been getting so nicely polished, has great features and looks great too...so it really saddens me when i see stuff like this...:(

---

### Post by malspa on 2013-06-18
Well, I tried it in Kubuntu 12.04 but couldn't get chromium-browser to launch, so I'd say no, don't try it.

```
steve[~]$ chromium-browser
./third_party/tcmalloc/chromium/src/free_list.h:118] Memory corruption detected.
Segmentation fault (core dumped)
steve[~]$
```

I removed the PPA and got rid of that version of Chromium, then reinstalled Chromium 25. Whatever.

---

### Post by malspa on 2013-06-18
I'm with you, craig10x. In Ubuntu and Kubuntu, I simply use Chrome.

---

### Post by craig10x on 2013-06-18
Yep...the only way to go, malspa ;)

---

### Post by vasa1 on 2013-06-18
> **craig10x said:**
> ... i just got version 28 which was just released to the stable channel....
Interesting that it's just for Linux currently!

---

### Post by MadmanRB on 2013-06-18
I dont get what the big fuss about with Chromium not being up to date, if its not a security update or improves features then its not really worth the fuss.

---

### Post by craig10x on 2013-06-18
Well Chrome seems to improve with each new version...also, there have been flash updates too in newer versions, so those running Chromium get left behind....Chrome is very prompt about bringing you the latest stable release and each time there is any interim updates (new version in same series) you also get them like immediately...With Chromium, you are dependent on Canonical and they really fall off the boat on the Chromium updates and simple fixes and refinements on the types of items i mentioned in my previous post...

Ubuntu is my favorite distro and that's probably why i get a bit annoyed about things like this because it doesn't make the best impression to newer users coming over to us...

---

