---
title: "Installing Google Chrome"
date: 2012-03-31
forum: Recurring Discussions
---

### Post by fiatveritas on 2012-03-31
I remember having trouble installing Google Chrome for my Ubuntu 11.10 (64bit), so here's the general layout for how I installed Chrome on Ubuntu: 

After I downloaded [Google Chrome]("http://google.com/chrome"), I unpackaged the file. You can look up how to unpackage a file by looking up the extension (e.g. *.deb). The version I downloaded was "64 bit .deb (For Debian/Ubuntu)"--which you depackage with sudo dpkg -i <name_of_the_file_.deb>--on the terminal screen. 

Before running any code make sure you're absolutely sure that the code you run is safe. In addition, I pointed my terminal to the directory where I saved the *.deb file. This requires you to move over to the appropriate directory with the command 'dir'.

After you run the depackaging command, the terminal screen indicated that I run sudo apt-get -f install (this command downloaded an interface so Chrome installs itself after you run apt-get -f install). Afterwards, I was cruising with a 64bit browser optimized for a 64bit O.S.. I'm a little biased in writing this post because Mozilla hasn't released a 64bit version of Firefox. Moreover, Chrome uses my system resources more efficiently than a 32bit browser (though, internet users will not notice the difference in speeds). Another reason I like Chrome is because of its sandbox feature wherein errors cause tabs to crash rather than crashing the entire browser. 

You can run benchmarks between your browsers over at [Dromaeo]("http://dromaeo.com/") (the Mozilla Benchmark site) to see the difference.

---

### Post by lovinglinux on 2012-03-31
> **fiatveritas said:**
> I remember having trouble installing Google Chrome for my Ubuntu 11.10 (64bit), so here's the general layout for how I installed Chrome on Ubuntu: 

After I downloaded [Google Chrome]("http://google.com/chrome"), I unpackaged the file. You can look up how to unpackage a file by looking up the extension (e.g. *.deb). The version I downloaded was "64 bit .deb (For Debian/Ubuntu)"--which you depackage with sudo dpkg -i <name_of_the_file_.deb>--on the terminal screen. 

Before running any code make sure you're absolutely sure that the code you run is safe. In addition, I pointed my terminal to the directory where I saved the *.deb file. This requires you to move over to the appropriate directory with the command 'dir'.

After you run the depackaging command, the terminal screen indicated that I run sudo apt-get -f install (this command downloaded an interface so Chrome installs itself after you run apt-get -f install). Afterwards, I was cruising with a 64bit browser optimized for a 64bit O.S..

Why complicate things? Just visit [Google Chrome download page](https://www.google.com/chrome/), click the download button, select the deb option according to your architecture and save the file. After downloading, right-click on the downloaded deb file, select "Open with >> Ubuntu Software Center". Wait for it to load and click install.

You can also install the open source version from the repositories. Just launch Ubuntu Software Center and search for chromium. Click Install button.


> **fiatveritas said:**
> I'm a little biased in writing this post because Mozilla hasn't released a 64bit version of Firefox. Moreover, Chrome uses my system resources more efficiently than a 32bit browser (though, internet users will not notice the difference in speeds).

Well, unfortunately I must disagree.

Mozilla has been providing 64bit builds of Firefox for a long time. They just don't make it available on the Firefox main page. However, if you are using 64bit Ubuntu, then your Firefox is 64bit. If you want to download it form Mozilla, visit [ftp://ftp.mozilla.org/pub/firefox/releases/](ftp://ftp.mozilla.org/pub/firefox/releases/)

Chrome doesn't use the resources more efficiently. If fact benchmarks and personal experience shows that it uses more RAM than a vanilla Firefox. 

[IMG]http://media.bestofmicro.com/S/E/326318/original/memuse40tabswbgp9.png[/IMG]

See explantion and other tests at [http://www.tomshardware.com/reviews/chrome-17-firefox-10-ubuntu,3129-14.html](http://www.tomshardware.com/reviews/chrome-17-firefox-10-ubuntu,3129-14.html)

Additionally, when running flash videos, it uses more CPU than both Firefox and Opera.

**Chrome:**

[IMG]http://i.imgur.com/VEQ2I.png[/IMG]


**Opera:**

[IMG]http://i.imgur.com/G9dvh.png[/IMG]


**Firefox**

[IMG]http://i.imgur.com/vgMrG.png[/IMG]


About the benchmarks, here is a recent article comparing all major browsers with various benchmark tools:

[http://www.zdnet.com/blog/hardware/the-big-browser-benchmark-chrome-17-vs-opera-11-vs-firefox-11-vs-ie9-vs-safari-5/19079](http://www.zdnet.com/blog/hardware/the-big-browser-benchmark-chrome-17-vs-opera-11-vs-firefox-11-vs-ie9-vs-safari-5/19079)


.

---

### Post by fiatveritas on 2012-04-01
I have to start off by re-mentioning that my post was biased. In addition, I feel that your post is also biased because you're skewing your argument by showing me how much memory Chrome consumes when you open 40 tabs at once. Frankly, I only have about 10 tabs open at any given session; so, it's safe to say that Chrome does well for lite internet browsing. In fact, you linked me to benchmarks showing me that Chrome is, indeed, better whenever you have a few tabs open--which streghthens the claim I made in my first post because you provided evidence for my claim. However, I agree that when you have about 40 tabs open with Firefox it [Firefox] is the better browser--this is of course when you look at the benchmark.

There's a few other mistakes in my post that need so fixing: I'm running Ubuntu 11.10 (64bit) on a netbook with 2GB of RAM. In addition, my system has a 1.83 Atom processor (Duo Core), so the benchmark you cited doesn't apply to my system because you linked me to a system that has a processor with four cores. Also, the other link (zdnet.com) also illustrates my point that Chrome is actually better because Firefox 11.0 beat Chrome in only one benchmark test (at least from what I understood); in all other tests Chrome beat Firefox relative to each other. 

What I found most surprising is that when I ran Mozilla's Dromaeo benchmark, Chrome did perform better in some aspects than in others. I thought that Dromaeo would skew performance towards Firefox, but the results show otherwise. Another highlight, Dromaeo identified my version of Firefox as 32bit (not 64bit as should ship with Ubuntu 64bit)--which means that either Mozilla does not know how program their benchmark algorithms to detect their own web broswer or Ubuntu does not ship with 64bit versions of Firefox. 

I think we're being nitpicky with performance and preferences here. I used to be a huge Mozilla fan myself, but opted over to Chrome for its 64bit browser, especially, when Mozilla is still experimenting with its 64bit browser under the name Waterfox. In addition, "who can argue with Chrome's sandbox interface?"

On another note, my system was having trouble installing Chrome via Ubuntu Software Center, therefore, I opted for the terminal route to help anyone who may happen to run into the same trouble.

This was a fun post to write.

> **lovinglinux said:**
> Why complicate things? Just visit [Google Chrome download page](https://www.google.com/chrome/), click the download button, select the deb option according to your architecture and save the file. After downloading, right-click on the downloaded deb file, select "Open with >> Ubuntu Software Center". Wait for it to load and click install.

You can also install the open source version from the repositories. Just launch Ubuntu Software Center and search for chromium. Click Install button.




Well, unfortunately I must disagree.

Mozilla has been providing 64bit builds of Firefox for a long time. They just don't make it available on the Firefox main page. However, if you are using 64bit Ubuntu, then your Firefox is 64bit. If you want to download it form Mozilla, visit [ftp://ftp.mozilla.org/pub/firefox/releases/](ftp://ftp.mozilla.org/pub/firefox/releases/)

Chrome doesn't use the resources more efficiently. If fact benchmarks and personal experience shows that it uses more RAM than a vanilla Firefox. 

[IMG]http://media.bestofmicro.com/S/E/326318/original/memuse40tabswbgp9.png[/IMG]

See explantion and other tests at [http://www.tomshardware.com/reviews/chrome-17-firefox-10-ubuntu,3129-14.html](http://www.tomshardware.com/reviews/chrome-17-firefox-10-ubuntu,3129-14.html)

Additionally, when running flash videos, it uses more CPU than both Firefox and Opera.

**Chrome:**

[IMG]http://i.imgur.com/VEQ2I.png[/IMG]


**Opera:**

[IMG]http://i.imgur.com/G9dvh.png[/IMG]


**Firefox**

[IMG]http://i.imgur.com/vgMrG.png[/IMG]


About the benchmarks, here is a recent article comparing all major browsers with various benchmark tools:

[http://www.zdnet.com/blog/hardware/the-big-browser-benchmark-chrome-17-vs-opera-11-vs-firefox-11-vs-ie9-vs-safari-5/19079](http://www.zdnet.com/blog/hardware/the-big-browser-benchmark-chrome-17-vs-opera-11-vs-firefox-11-vs-ie9-vs-safari-5/19079)


.

---

### Post by lovinglinux on 2012-04-01
Please read the following quote. I have highlighted the important things:

> **64-bit nightly builds for Windows are available**, but due to incompatibilities, including with popular plugins, **official 64-bit releases are not provided**.

**Waterfox** and Palemoon are **unaffiliated projects** that provide **unofficial** 64bit builds.

**The official releases of Firefox for OS X are universal builds that include both 32-bit and 64-bit versions of the browser in one package.** A typical browsing session uses a combination of the 64-bit browser process and a 32-bit plugin process, because some popular plugins still are 32-bit.

**For Linux, vendor-backed, performance optimized, stable 64-bit builds exist (such as for Novell-Suse Linux, Red Hat Enterprise Linux, and Ubuntu), in addition to the nightly builds.**

Source: [http://en.wikipedia.org/wiki/Firefox#64-bit_builds](http://en.wikipedia.org/wiki/Firefox#64-bit_builds)


As you can see, the only problematic 64bit builds are those for Windows and Waterfox is not a Mozilla browser, is a third party project.

---

### Post by Copper Bezel on 2012-04-01
Performance (in the sense of the user's actual experience) and usage aren't tightly interrelated, either. Chrome does perform faster on my netbook than Firefox, but it's using more memory to do it. 

But seriously, these aren't the real reasons most people end up choosing a browser, anyway. I mean, I use Chrome primarily because of the tab management, and now with the Adobe issues, it looks like I'm stuck with it if I want decent Flash support, which is itself an unpleasant necessity. If you want a fast, lightweight browser with numbers you can show off on the internet, use uzbl. = P

---

### Post by alexcckll on 2012-04-04
Do Canonical have plans to offer Chrome through the Partner repository?  Thus making it easier to get and manage?

Maybe have something akin to the Flash installer package of old...?

---

### Post by winh8r on 2012-04-04
> **alexcckll said:**
> Do Canonical have plans to offer Chrome through the Partner repository?  Thus making it easier to get and manage?

Maybe have something akin to the Flash installer package of old...?

I don't think there is an easier way than illustrated in the screenshot below. Click install and it loads the repositories and updates itself and does what it wants /needs to.

Besides , as has already been mentioned Chromium is available in the repositories. (Google Chrome without the branding and all the data mining stuff)

---

### Post by alexcckll on 2012-04-04
> **winh8r said:**
> I don't think there is an easier way than illustrated in the screenshot below. Click install and it loads the repositories and updates itself and does what it wants /needs to.

Besides , as has already been mentioned Chromium is available in the repositories. (Google Chrome without the branding and all the data mining stuff)
Yeah - but also without Flash and other stuff - especially if the requirements for services like iPlayer go beyond Flash 11...

Just would be safer than going off around the web for all the software reqd...

---

### Post by SemiExpert on 2012-04-04
Why does anyone want to use Chrome when Chromium is already in the repositories?  Chromium=Chrome.

---

### Post by malspa on 2012-04-04
> **SemiExpert said:**
> Why does anyone want to use Chrome when Chromium is already in the repositories?  Chromium=Chrome.

Good question. In Ubuntu, I use Chromium because it's in the repos and it's kept fairly up-to-date. In Debian Stable, chromium-browser is still at version 6.xxx, so I've installed Chrome there.

---

### Post by SemiExpert on 2012-04-04
> **Copper Bezel said:**
> Performance (in the sense of the user's actual experience) and usage aren't tightly interrelated, either. Chrome does perform faster on my netbook than Firefox, but it's using more memory to do it. 

But seriously, these aren't the real reasons most people end up choosing a browser, anyway. I mean, I use Chrome primarily because of the tab management, and now with the Adobe issues, it looks like I'm stuck with it if I want decent Flash support, which is itself an unpleasant necessity. If you want a fast, lightweight browser with numbers you can show off on the internet, use uzbl. = P

Adobe has announced that 11.2 is the last version of Flash for Linux, but will continue to provide security updates, much in the same way that the last version of Acrobat Reader for Linux was Acrobat 9, but security updates have continued.  So there is still Flash support for Linux into the foreseeable future, and by the time the security updates end, the transition to HTML5 will be complete.

---

### Post by lovinglinux on 2012-04-04
> **SemiExpert said:**
> Adobe has announced that 11.2 is the last version of Flash for Linux, but will continue to provide security updates, much in the same way that the last version of Acrobat Reader for Linux was Acrobat 9, but security updates have continued.  So there is still Flash support for Linux into the foreseeable future, and by the time the security updates end, the transition to HTML5 will be complete.

No, Adobe is no longer supporting Flash on Linux. They are not even addressing bug reports. They will provide security updates, but that doesn't mean the plugin will still work.

I doubt some of the services that I subscribe that depend on flash will change to HTML5 in 5 years.

---

### Post by Paqman on 2012-04-05
> **SemiExpert said:**
> Why does anyone want to use Chrome when Chromium is already in the repositories?  Chromium=Chrome.

Chrome is a bit more stable than Chromium (if you care) and includes extra gubbins like an integrated pdf viewer. But apart from that you're right, they're pretty much interchangeable. Using the .deb from Google actually adds their repo, so Chrome even updates just as easily as Chromium.

---

### Post by Copper Bezel on 2012-04-05
Yeah, Chrome has a prettier icon, the .pdf viewer, and Pepper Flash. That's reason enough for me to use the branded version (and then use Chrome as my default .pdf viewer.) But the browser part of the browser is the same, so if you're not actively using it for the unique Chrome features, there's nothing wrong with Chromium.

---

### Post by d.atanasov on 2012-04-05
I must agree with lovinglinux, because Chrome browser is doing every tab in a separate process. This is the main reason for Chrome to be faster, but it consume more memory. I would like to have browser that is fast but don`t uses all of the available ram memory. But the plus in the Chrome browser is in the quick synchronization (I know Firefox also have it but one should take into account the google glory). In summary I want to tell you that if you have the both browsers you have the best quality and there is no need for discussion here :)

---

### Post by lovinglinux on 2012-04-05
> **d.atanasov said:**
> I must agree with lovinglinux, because Chrome browser is doing every tab in a separate process. This is the main reason for Chrome to be faster, but it consume more memory. I would like to have browser that is fast but don`t uses all of the available ram memory. But the plus in the Chrome browser is in the quick synchronization (I know Firefox also have it but one should take into account the google glory). In summary I want to tell you that if you have the both browsers you have the best quality and there is no need for discussion here :)

Then try Opera. Is faster than Firefox, doesn't use much memory like Chrome, and can be customized a lot. The main problems of Opera are, in my opinion, the incompatibility with some sites and the poor availability of extensions. For instance, I can't upload to my Wordpress RokGallery.

---

### Post by SemiExpert on 2012-04-06
> **lovinglinux said:**
> No, Adobe is no longer supporting Flash on Linux. They are not even addressing bug reports. They will provide security updates, but that doesn't mean the plugin will still work.

I doubt some of the services that I subscribe that depend on flash will change to HTML5 in 5 years.

 Flash 11.2 seems to be working better on Linux than on Windows, at least from my experience.  Who knows what the future will bring?  Adobe doomed flash to extinction when they backed away from mobile platforms.  My guess is that OS X support will be the next to go.  In any case, HTML5 is the prefered solution, and if you don't have Flash, Youtube defaults to HTML5.  In any case, with the sheer numbers of mobile devices that don't support Flash and never will, I think that most services will drop Flash very quickly, long before the security updates end in 5 years.

---

### Post by lovinglinux on 2012-04-06
> **SemiExpert said:**
> Flash 11.2 seems to be working better on Linux than on Windows, at least from my experience.  Who knows what the future will bring?  Adobe doomed flash to extinction when they backed away from mobile platforms.  My guess is that OS X support will be the next to go.  In any case, HTML5 is the prefered solution, and if you don't have Flash, Youtube defaults to HTML5.  In any case, with the sheer numbers of mobile devices that don't support Flash and never will, I think that most services will drop Flash very quickly, long before the security updates end in 5 years.

Perhaps, because if it depends on Linux desktop market share, then we are doomed.

---

### Post by SemiExpert on 2012-04-06
> **lovinglinux said:**
> Perhaps, because if it depends on Linux desktop market share, then we are doomed.

 If it was a matter of marketshare, Adobe wouldn't have abandoned the mobile device market?  Flash is going to disappear, probably sooner, rather than later.  This is not an x86 Linux specific issue.  Oh, and the fact that Mozilla didn't jump on board with Pepper, and made that decision as early as 2010, says more about the future prospects of Flash than anything else.

---

### Post by cbennett926 on 2012-04-07
I recommend Chromium as well!

---

### Post by lovinglinux on 2012-04-07
> **SemiExpert said:**
> If it was a matter of marketshare, Adobe wouldn't have abandoned the mobile device market?  Flash is going to disappear, probably sooner, rather than later.  This is not an x86 Linux specific issue.  Oh, and the fact that Mozilla didn't jump on board with Pepper, and made that decision as early as 2010, says more about the future prospects of Flash than anything else.

Don't forget Mozilla didn't support h.264 and now will support it.

---

### Post by xmastree on 2012-04-21
> **cbennett926 said:**
> I recommend Chromium as well!

This is odd. I'm trying to install Chrome but I get a dependency error, so I looked here for a possible solution.

chromium? According to my package manager that's a "fast paced, arcade-style, scrolling space shooter"

Not quite what I'm after.

---

### Post by tmaranets on 2012-04-21
Why go through a whole coding process? You can just click on the download and open it with Ubuntu Software Centre. If that doesn't work, you can just download Chromium Web Browser off Ubuntu Software Centre. Chromium is the exact same thing as Chrome.

---

### Post by Paqman on 2012-04-21
> **xmastree said:**
> 
chromium? According to my package manager that's a "fast paced, arcade-style, scrolling space shooter"


The package is [chromium-browser]("apt:chromium-browser").

---

### Post by xmastree on 2012-04-21
> **Paqman said:**
> The package is [chromium-browser]("apt:chromium-browser").

chris@chris-desktop:~$ sudo apt-get install chromium-browser
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package chromium-browser is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package chromium-browser has no installation candidate
chris@chris-desktop:~$

---

### Post by xmastree on 2012-04-21
I suspect [this]("http://news.softpedia.com/news/Google-Chrome-13-0-Drops-Support-for-Ubuntu-8-04-LTS-201102.shtml") is my main problem. Trouble is, I removed the older (working) one to allow the new one to install. And I no longer have the installer for the old one.

I really ought to update this thing.

---

