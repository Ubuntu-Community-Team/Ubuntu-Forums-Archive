---
title: "How much proprietary software does Ubuntu contain?"
date: 2013-05-06
forum: Recurring Discussions
---

### Post by Bufeu on 2013-05-06
Hi!
I have thought of this a long time now.
"How much proprietary software does Ubuntu really contain?"
I actually asked this question on Ubuntu-On-Air a few month ago and got the answer "None". Of course, that statement are false. To begin with, the Linux kernel includes proprietary software itself, so called "binary blobs". "Binary blobs" are mostly [firmware code and other stuff]("https://lists.ubuntu.com/archives/gobuntu-devel/2008-January/000538.html"). Despite this, there are 100 % free distros, like [gNewSense]("http://www.gnewsense.org/") (used by RMS himself). Also, the [GNU Linux-libre kernel]("http://www.fsfla.org/ikiwiki/selibre/linux-libre/index.en.html") is 100 % free. In the 2.6.33 release of the Linux kernel, 2.5 MB in its compressed tarball was totally non free code.
There's a program called *vrms* (Virtual Richard M. Stallman :lol:) that's searches the computer for non free packages and lists them. It also explains why they're not free.

Ubuntu's trademark policy prohibits commercial redistribution of exact copies of Ubuntu, denying an important freedom.
Canonical is having ads for, and selling, proprietary software through the Ubuntu Software Center (the Ubuntu Software Cneter do send stats to Canonical by default). Shouldn't the Software Center be a program where you can download and install free programs, anonymously, without having ads?
Ubuntu comes with Totem (not my favorite player) instead of VLC. VLC comes with a lot of codecs (in fact, all you'll ever need) and it's released under free licenses. To play videos using Totem, you'll need to download and install non free codecs. I think some code in VLC is non free, though, but compared to completely non free codecs, VLC is still a much better choice.
As of October 2012, Ubuntu sends personal data about users' searches to a server belonging to Canonical, which sends back ads to buy things from Amazon. This does not, strictly speaking, affect whether Ubuntu is free software, but it is a violation of users' privacy. It also encourages buying from Amazon, a company associated with DRM as well as mistreatment of workers, authors and publishers.
Technically, when you search for something in Dash, your computer makes a secure HTTPS connection to productsearch.ubuntu.com, sending along your search query and your IP address. If it returns Amazon products to display, your computer then insecurely loads the product images from Amazon's server over HTTP. This means that a passive eavesdropper, such as someone sharing a wireless network with you, will be able to get a good idea of what you're searching for on your own computer based on Amazon product images.
With the aim of protecting the privacy of all Ubuntu users that might not dig into their settings, “Disable ‘Include online search results’ by default”, was the one that they most staunchly refused to budge on. Only, sadly, Ubuntu’s interface includes sending your search terms to an undefined list of companies, every time, without the option to opt-in. Privacy is clearly not on the top of Canonical's priority list.
Will the next step be that proprietary drivers, to e.g. graphic cards, will be installed by default? Or send the Zietgeist logs to third parties?

My worry is that Ubuntu will become non-free. It's sad that completely (or almost completely) systems uses old software and just is YEARS behind. For example, Arch, Fedora, openSUSE is not exactly "user friendly", and requires some knowledge about GNU-programs, UNIX-like systems and how to configure them. So, I just wonder how much proprietary software Ubuntu includes, how "free" is Ubuntu? And what path is Canonical going to take? It's sad that Canonical ruins what once was a quite good, stable and free system.

Sources/Read more:
[https://micahflee.com/2013/01/why-im-leaving-ubuntu-for-debian/](https://micahflee.com/2013/01/why-im-leaving-ubuntu-for-debian/)
[https://www.eff.org/deeplinks/2012/10/privacy-ubuntu-1210-amazon-ads-and-data-leaks](https://www.eff.org/deeplinks/2012/10/privacy-ubuntu-1210-amazon-ads-and-data-leaks)
[http://www.jejik.com/articles/2006/11/is_ubuntu_set_to_become_non-free/](http://www.jejik.com/articles/2006/11/is_ubuntu_set_to_become_non-free/)
[http://www.osnews.com/story/24009/FSFLA_Linux_Kernel_Is_Torvalds_Bait_and_Switch_](http://www.osnews.com/story/24009/FSFLA_Linux_Kernel_Is_Torvalds_Bait_and_Switch_)
[http://lwn.net/1999/0211/a/lt-binary.html](http://lwn.net/1999/0211/a/lt-binary.html)

---

### Post by iamkuriouspurpleoranj on 2013-05-06
In general, there's a worrying trend to "getting it all out of the box". Mint and CrunchBang (peace be upon him) and other "user-friendly" distros suffer from this too. Patents etc. to my mind are a far bigger worry than the Amazon lens, which sins primarily by being rubbish and the fact that it's a beta passed off as a release. Besides, Google already knows what I want to do and who I want to do it with/to. In fact, Google knows me better than anyone, probably even better than I know myself. So if I have concerns over privacy, well it's a bit late, eh.

Frivolity aside, I would now actually like to see Linux not become a major gaming platform because I think the realities of game development will weaken "free software" on Linux. Of course, these things aren't important until they are and you wake up one morning and everything is just shopping malls, fear and stories about celebzzz.

---

### Post by Perfect Storm on 2013-05-06
Moved to recurring.

---

### Post by Bufeu on 2013-05-06
Of course, Google knows alot about the users. That's not what the thing is about. The thing is that freedom means that *you* choose when and what to be logged. If you are using Google, you have accepted the ToS, and then, it's your choice. And yes, patent trolls, patent wars and the copyright law in the US is a far bigger worry, but to see Canonical choose to actually ruin Ubuntu is not fun either. You didn't answer my question about how much proprietary software Ubuntu contains. Does Ubuntu come with proprietary software, except the "binary blops" in the Linux kernel itself?

---

### Post by iamkuriouspurpleoranj on 2013-05-06
I don't seek doctrinaire perfection, I just want the big players (Microsoft, Google) to be confused enough and for long enough by one of the small players (Canonical) so we can make a break for the exit.

---

### Post by Version Dependency on 2013-05-07
> **Bufeu said:**
> Ubuntu's trademark policy prohibits commercial redistribution of exact copies of Ubuntu, denying an important freedom.


How is protecting their trademark denying you freedom? 

> **Bufeu said:**
> Canonical is having ads for, and selling, proprietary software through the Ubuntu Software Center (the Ubuntu Software Cneter do send stats to Canonical by default). Shouldn't the Software Center be a program where you can download and install free programs, anonymously, without having ads?

You are "free" to remove all shopping lenses from Unity.  You are also "free" to use other software centers other than the Ubuntu Software Center.  You see I keep using the "free" word?  Picking up on a theme?


> **Bufeu said:**
> Ubuntu comes with Totem (not my favorite player) instead of VLC. VLC comes with a lot of codecs (in fact, all you'll ever need) and it's released under free licenses. To play videos using Totem, you'll need to download and install non free codecs. I think some code in VLC is non free, though, but compared to completely non free codecs, VLC is still a much better choice.

Wait...wHAT>!?  You complain about Ubuntu containing proprietary software, yet you want them to ship with VLC, a program that comes installed with a ton of proprietary codecs (which may or may not be "legal" for Canonical to do). 

> **Bufeu said:**
> As of October 2012, Ubuntu sends personal data about users' searches to a server belonging to Canonical, which sends back ads to buy things from Amazon. This does not, strictly speaking, affect whether Ubuntu is free software, but it is a violation of users' privacy.

You are correct.  The shopping lenses have nothing to do with Ubuntu being "free software."  In fact, I am pretty sure those lenses are open source.  Violation of privacy?  There are privacy notices in the Unity dash and on Ubuntu.com, as well as an on/off switch in System Settings. 

 > **Bufeu said:**
> My worry is that Ubuntu will become non-free. 

Why are you worried?  Mark Shuttleworth has stated many times over the years (including recently) that Ubuntu is and always will be free.  Do you know something that he doesn't?

> **Bufeu said:**
> It's sad that Canonical ruins what once was a quite good, stable and free system.

Ubuntu is on many millions of computers and continues to grow it's userbase.  Alot of people seem to think it's "quite good" and "stable."  Oh...it's also still "free."

---

### Post by craig10x on 2013-05-07
Recent quote from Mark Shuttleworth:  "The Ubuntu Manifesto: Ubuntu IS and will ALWAYS BE free to get and use" (unquote)....

The Amazon Shopping Lens (and that's all it is...not spyware) is just a little way to get some revenue flowing into ubuntu....(and the option to shut it off is offered)...Ubuntu may be free but developing it isn't...

---

### Post by vasa1 on 2013-05-07
> **Bufeu said:**
> ...
"How much proprietary software does Ubuntu really contain?"
...
There's a program called *vrms* (Virtual Richard M. Stallman :lol:) that's searches the computer for non free packages and lists them. It also explains why they're not free.
...
Run it

---

### Post by Bufeu on 2013-05-07
> **Version Dependency said:**
> How is protecting their trademark denying you freedom?
Ubuntu's trademark policy **prohibits commercial redistribution of exact copies of Ubuntu**, denying an important freedom.


> **Version Dependency said:**
> You are "free" to remove all shopping lenses from Unity.  You are also "free" to use other software centers other than the Ubuntu Software Center.  You see I keep using the "free" word?  Picking up on a theme?
The problem here is that new users may not know how to to that, and cursing Ubuntu for send their searches. For me, it's not really a problem. It just take a little bit longerb time to remove all the sh*tty spyware packages. It's the new users I'm talking about. If Ubuntu included spyware like features when I started using it, and I had not idea how to remove it, I probably wouldn't use Linux **at all**.



> **Version Dependency said:**
> Wait...wHAT>!?  You complain about Ubuntu containing proprietary software, yet you want them to ship with VLC, a program that comes installed with a ton of proprietary codecs (which may or may not be "legal" for Canonical to do). 
From Wikipedia:
"*The default distribution of VLC includes a large number of free decoding  and encoding libraries, **avoiding the need for finding/calibrating  proprietary plugins*****.**"
Also, you can find a list of all libraries that is included in VLC on [VLC's wiki]("http://wiki.videolan.org/index.php/Contrib_Status"). As you can see, almost all libraries are in fact released under a free license.
A also removed the restricted and multiverse repos in a virtual machine and then tried to install VLC.
This is what I got:
```
Reading package lists...
Building dependency tree...
Reading state information...
Package lua is a virtual package provided by:
  lua5.2:i386 5.2.0-2
  lua5.1:i386 5.1.4-12ubuntu1
  lua50 5.0.3-6
  lua5.2 5.2.0-2
  lua5.1 5.1.4-12ubuntu1

Package faac is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

Package libdap10 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  libdapserver7:i386 libdapclient3:i386 libdap11:i386 libdapserver7
  libdapclient3 libdap11


```
So, only these packages are non free. Compare that to the packages you must download and install if you want to use Totem. And, VLC is actually a much better video player.

> **Version Dependency said:**
> You are correct.  The shopping lenses have nothing to do with Ubuntu being "free software."  In fact, I am pretty sure those lenses are open source.  Violation of privacy?  There are privacy notices in the Unity dash and on Ubuntu.com, as well as an on/off switch in System Settings.
 As I said, Canonical tries to make money and ruins the OS with ads. New users may not like it and curse Linux for that.


> **Version Dependency said:**
> Why are you worried?  Mark Shuttleworth has stated many times over the years (including recently) that Ubuntu is and always will be free.  Do you know something that he doesn't?
Free is in "gratis", "Free of charge" or as in "free as freedom"? Freedom is to choose whatever and whenever you want to being monitored or logged by someone else, not to have the ability to search in the settings to find the right place to turn it off.



> **Version Dependency said:**
> Ubuntu is on many millions of computers and continues to grow it's userbase.  Alot of people seem to think it's "quite good" and "stable."  Oh...it's also still "free."
Ubuntu Server is still a good OS. It's Unity that Canonical is destroying.
If Canonical just gave more options (especially at the installation) about the ads and other proprietary programs, I'd be happy. As long as I can freely choose **before** anything is enabled, I would be fine with that. And that day when Canonical is telling exactly what proprietary code that's included and what they are for, I will gladly support them.

> **vasa1 said:**
> Run it

It only tells what packages that are non-free. It can't tell how much proprietary code the kernel or the drivers contains. It just tells me what **package****s** that's non-free. It can't tell if Canonical's own code and drivers are FOSS or not.

---

### Post by monkeybrain2012 on 2013-05-07
> **Bufeu said:**
> Ubuntu's trademark policy **prohibits commercial redistribution of exact copies of Ubuntu**, denying an important freedom.

First disclaimer, I am not a lawyer, so I may be missing something. But I am not sure how this is an "important freedom" to make a buck (commercial use) from redistributing EXACT COPIES of something that is available for free. Based on my naive reading of the policy, it seems that you are allowed to charge for services (say setting up ubuntu for someone else) or shipping Ubuntu to someone else , or OEMs setting up Ubuntu in the machines they sell,  you are allowed to repackage, rebrand Ubuntu and distribute it either freely or commercially. The source codes are open. I am not sure what reasonable freedom is being violated here. If someone were to sell me an exact copy of Ubuntu I would think he is trying to rip me off instead of exercising "an important freedom" 



> The problem here is that new users may not know how to to that, and cursing Ubuntu for send their searches. For me, it's not really a problem. It just take a little bit longerb time to remove all the sh*tty spyware packages. It's the new users I'm talking about. If Ubuntu included spyware like features when I started using it, and I had not idea how to remove it, I probably wouldn't use Linux **at all**.

I agree this is bad form, though calling it spyware is unhelpful button pushing. I think they should implement a popup when the Dash is first launch to ask user to opt in or out of the feature (depending on the default), that way it would go a long way to address legitimate concerns for privacy.


> So, only these packages are non free. Compare that to the packages you must download and install if you want to use Totem. And, VLC is actually a much better video player.

Well Ubuntu is not the only distro that comes with totem instead of vlc. Same with (for examples) Debian,  Fedora and Trisque (a free respin of Ubuntu endorsed by the FSF) In Fedora and Trisque VLC is not even in the official repos (have to add RPM fusion for Fedora). I think you are barking up the wrong tree here if you try to accuse Canonical of forcing you to use proprietary codecs by using as default something which would work poorly without such codecs. It may have something to do with legality.

Another thing is that totem is part of the gnome package. So it is a natural choice as default if you use a gnome desktop. But it is not installed in, for example, Kubutu which comes with kde's own player.


 > As I said, Canonical tries to make money and ruins the OS with ads. New users may not like it and curse Linux for that.



I am not sure if many people think of it as "ruining the OS", there are pros and cons to commercializing Linux, for people who use social networking sites, google services and various apps on mobile platform "ads" that you can turn on and off may not be that big a deal. And if one dose use Amazon one may actually find this very convenient.




> f Canonical just gave more options (especially at the installation) about the ads and other proprietary programs, I'd be happy. As long as I can freely choose **before** anything is enabled, I would be fine with that. And that day when Canonical is telling exactly what proprietary code that's included and what they are for, I will gladly support them.
It only tells what packages that are non-free. It can't tell how much proprietary code the kernel or the drivers contains. It just tells me what **package****s** that's non-free. It can't tell if Canonical's own code and drivers are FOSS or not.

I have addressed the ads, as for the proprietary program, you install  the Ubuntu restricted extras and proprietary drivers on your own free  choice. There is also an option to install Ubuntu with only free  components, and there is always Trisque if you are purist.(which uses a free kernel) Oh, and you can also grab a kernel from kernel.org and build it yourself. 

However I doubt that many ordinary users would think Canonical is "ruining the OS" and prefer an "unruined" version like Trisque.

---

