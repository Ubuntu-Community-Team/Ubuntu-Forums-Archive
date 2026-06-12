---
title: "FAQ: Common misconceptions about Mac OS X"
date: 2009-05-26
forum: Recurring Discussions
---

### Post by schauerlich on 2009-05-26
Within the greater Linux community, and on these forums in particular, I have noticed a great deal of misinformation with respect to Mac OS X and Apple's contributions to the Unix community. I'd like to address these topics in an FAQ-style post. This is by no means a comprehensive list of issues, and I plan on adding to this post in the future. Feel free to suggest topics and I'll address them as I have time.

**[color=red]Have you noticed any "myths" or  "misconceptions" about Mac OS X that aren't on this list? Do you think I've said something inaccurate or misleading? Let me know! Respond to this thread, quoting the relevant sections, and you just might see your argument incorporated into this FAQ.[/color]**

**[color=blue]Much of the first few pages of this thread are responses to an older version of this post. Please keep in mind that it has changed a lot since those responses were written.[/color]**


**Commonly stated: Mac OS X only runs on Apple Hardware.**
More accurate description: Well, sort of. True, its license states it can only be run on Apple hardware; However, options do exist to run OS X on non-Apple hardware, such as the excellent [OSx86](http://en.wikipedia.org/wiki/OSx86) project. [s]Similarly, [Psystar](http://en.wikipedia.org/wiki/Psystar) and PearC offer prebuilt computers which come with OS X preinstalled. Psystar is in the middle of a suit with Apple over the legitimacy of certain pertinent sections the Apple EULA. [/s]*UPDATE: both companies have gone under.*  It's not that OS X **doesn't** run on non-Apple hardware, it's just not Apple-sanctioned to do so. Currently whether this is legal is up for debate. However, it is true that Mac OS X does not run *out of the box* on non-Apple hardware, and you have to enter legally murky waters to get there. Depending on your perspective, this may count as running on non-Apple hardware or not. It is not like NetBSD where it is open and ready to be installed on anything. It's more like getting Linux to run on a wrist watch. You can get there, but it takes some finangling. And also, Swatch might sue you for licensing violations. Details...




**CS: Mac OS X is closed source.**
MAD: Parts of it are, parts of it aren't. Much of the core of OS X is [fully open source](http://www.apple.com/opensource/). Apple maintains a Unix distribution known as [Darwin](http://en.wikipedia.org/wiki/Darwin_(operating_system)), which serves as the base for each release of OS X. For a while, Darwin was distributed in binary form and available on Apple's website to download. Currently you can download Darwin's source in full [here](http://www.opensource.apple.com/). [Apple has never intended Darwin to be a distribution for every day use](http://lists.apple.com/archives/Darwinos-users/2007/Oct/msg00006.html); however, a community effort called [PureDarwin](http://www.puredarwin.org/) has sprung up to make it more usable. *UPDATE: I think it's safe to say the PureDarwin project is no more.* Mac OS X is proprietary, there is no doubt about it. However, proprietary does not necessarily mean that it does not contain open source components which are released for modification and redistribution. [Mac OS Forge](http://www.macosforge.org/) is a community project that helps develop the FOSS components of Mac OS X.

Apple has also released several of their own projects under FOSS licenses. The most recent and most significant example of this is [Grand Central Dispatch](http://en.wikipedia.org/wiki/Grand_central_dispatch). GCD is a C library (also useable with C based languages such as Objective-C, C++, etc) which makes it easy for programmers to make their apps multi-threaded. For a summary of the technology, see the [Ars Technica review of Mac OS X 10.6](http://arstechnica.com/apple/reviews/2009/08/mac-os-x-10-6.ars/12), as well as [Apple's Developer Connection page on it](http://developer.apple.com/library/mac/#documentation/Performance/Reference/GCD_libdispatch_Ref/Reference/reference.html). Apple's motive for open sourcing one of the main selling points of Snow Leopard is unclear, but the consensus seems to be that their use of [blocks](http://en.wikipedia.org/wiki/Blocks_(C_language_extension)) is a non-standard extension of C, and encouraging other Unix based systems to adopt it would benefit everyone. GCD has already been [ported to FreeBSD](http://www.freebsd.org/news/status/report-2009-04-2009-09.html#Grand-Central-Dispatch---FreeBSD-port), and will most likely make its way to the other BSDs soon.

Another significant FOSS project at Apple is [CUPS](http://en.wikipedia.org/wiki/Common_Unix_Printing_System), the Common Unix Printing System. CUPS has found its way into many Linux distributions, and is licensed under the GNU GPL/LGPLv2 (although it has some exceptions which allow Apple's proprietary code to link against it).



**CS: Apple ripped off BSD/GNU/FOSS advocates**
MAD: Apple has released all of the open source code it's integrated into Darwin/OS X back to the community. See [Apple's Open Source page](http://www.apple.com/opensource/) for more details. While Apple has not released the more "important parts" of the OS (to the end user) such as Cocoa or Aqua, it has released all of the code it used from open source projects back to the community.




**CS: Mac OS X is "just BSD with a shiny exterior," or "just an expensive version of Linux."**
MAD: Apple has incorporated a good amount of BSD code into Darwin. No one disputes the valuable contributions made to the Unix community at large and indirectly to Apple by the BSD community. However, to say that Mac OS X is simply BSD with a shiny exterior, or an expensive version of Linux, is misleading at best. OS X is based on the [XNU kernel](http://en.wikipedia.org/wiki/XNU), a [Mach](http://en.wikipedia.org/wiki/Mach_kernel)/[BSD](http://en.wikipedia.org/wiki/BSD#4.3BSD) hybrid kernel (with Apple's additions in [I/O Kit](http://en.wikipedia.org/wiki/I/O_Kit)), and incorporates a good amount of the base system from FreeBSD and various Unixes (although there are some GNU programs in there, such as screen, grep and bash). There is a standard [POSIX](http://en.wikipedia.org/wiki/Posix) environment, but most of the more visible portions of the OS are either [descended from](http://en.wikipedia.org/wiki/Cocoa_(API)) [NeXTSTEP](http://en.wikipedia.org/wiki/Nextstep) or [made](http://en.wikipedia.org/wiki/Core_Foundation) [in-house](http://en.wikipedia.org/wiki/Quartz_(graphics_layer)) [by](http://en.wikipedia.org/wiki/Aqua_(user_interface)) [Apple](http://en.wikipedia.org/wiki/Carbon_(API)).

The most visible contribution Apple has made to OS X is the [Cocoa API](http://en.wikipedia.org/wiki/Cocoa_(API)). Written in Objective-C, Cocoa was based off of the [OpenStep API](http://en.wikipedia.org/wiki/OpenStep) developed for NeXTSTEP. Cocoa provides developers a common palette to give their applications access to many key Core services, and help to standardize the interface across applications. A FOSS implementation of the OpenStep API exists, named [GNUstep](http://en.wikipedia.org/wiki/Gnustep). The project now aims to match Cocoa's public interface instead of the OpenStep standard, although it has a long way to go.

See [here](http://en.wikipedia.org/wiki/Architecture_of_Mac_OS_X) for more information about Mac OS X's architecture.




**CS: Mac OS X is bloated and slow.**
MAD: This is largely subjective. Sure, if you're installing Leopard on an original iMac, it's going to go slower than RMS in a pool of molasses.  I run Lion on a MacBookPro6,2 and find it runs quite smoothly. Like with ANY operating system, your mileage may vary.




**CS: Mac OS X caters to grandmas and creative types, not power users.**
MAD: While Apple does do its best to make its software simple and easy to use, and provides great multimedia applications, OS X is by no means limited to bearded twentysomethings and their grandmothers. Apple provides the [Xcode](http://en.wikipedia.org/wiki/Xcode) development suite with every installation of OS X to encourage development on their platform. A fully POSIX compliant environment is provided, making it easy to port applications originally written for other Unix distributions. [MacPorts](http://en.wikipedia.org/wiki/Macports), [Fink](http://en.wikipedia.org/wiki/Fink) and [homebrew](http://mxcl.github.com/homebrew/) make it relatively painless to install your favorite Unix tools on OS X.

In addition, the great community of developers has made several utilities which simplify daily tasks and center navigation on the keyboard, the most famous example of which is [QuickSilver](http://en.wikipedia.org/wiki/Quicksilver_(software)). This excellent tool is what Gnome Do is based on, and it makes it easy to get around with just the keyboard. 

It is true that Aqua is not very customizable as far as interfaces go. In the end, it comes down to a decision made by Apple that you may or may not agree with: to sacrifice customizability for consistency. Third party applications and Library hacks have made Mac OS X a little more flexible, and often times editing a plist will reveal a bundle of hidden options (somewhat like the gconf editor in GNOME). However, this customizability pales in comparison to that of Linux. For some, this may not be a big deal. For others, it may be a deal breaker. In the end, it's a matter of preference. Choose what makes you feel comfortable.




**CS: Mac OS X isn't REAL Unix.**
MAD: With Leopard, Mac OS X has been [SUSv3](http://en.wikipedia.org/wiki/SUSv3) certified, and is an Open Brand UNIX 03 registered product (when run on Intel processors). Whether this qualifies as a "real" Unix depends on what you mean by "real" Unix. If you mean "it's just like Linux," then it probably doesn't qualify. If you mean that it fits the Open Group's standards for using the Unix trademark, then it does. 




**CS: "Mac OS X 10.0/10.1/10.2/10.3 was a nightmare, I'll never touch OS X again."**
MAD: 10.0-10.3 are quite different from the last few point releases. Apple was struggling to stay afloat when Steve Jobs returned to Apple in 1997, and Apple was stuck using an outdated and slow OS on their computers. After [attempts to modernize the OS](http://en.wikipedia.org/wiki/Copland_(operating_system)) failed, Apple decided to abandon the OS 9 platform and move to a completely new OS. When Mac OS X 10.0 was released in 2000, it was buggy, slow, feature-poor and pinstripe-rich. It was Apple's effort to put *something* out to keep their business going. Once Apple had [a reliable source of income](http://en.wikipedia.org/wiki/Ipod), it was able to put more time and money into developing OS X into what it should have been. This goal (in my mind) was realized in 10.4, and further refined since. The last few point releases of OS X are radically different from the first four. If you tried any of the earlier versions and were put off by it, I strongly encourage you to plop down in a chair at your local Apple store and check out Mac OS X for 15 minutes or so. You might find your opinion of it has changed. Or, you might not.




**CS: Mac OS X doesn't have any good free (libre or beer) software available.**
MAD: [MacPorts](http://en.wikipedia.org/wiki/Macports), [Fink](http://en.wikipedia.org/wiki/Fink) and [homebrew](http://mxcl.github.com/homebrew/) are a few efforts to port Linux/BSD apps to OS X, and make them accessible through repositories. Lots of great software is available through these avenues, and Apple even has an implementation of X11 for GUI applications. X11 support isn't great, and I prefer to wait for apps to be ported to Cocoa, but if you're in a pinch and need to use something, it will do. In addition, sites such as [MacUpdate](http://www.macupdate.com/) are great for finding OS X freeware. For a given functionality found in a shareware application, there's almost always an equivalent functionality in a free application. I've never run into any trouble finding free (beer) software to do what I need on Mac OS X.




**CS: The Mac OS X command line is incomplete/different from Linux/not as good as Linux's.**
MAD: It is true that Apple does not put as much effort into refining the command line as it does to the GUI. However, complete access is given to the command line through Terminal.app. Terminal runs GNU bash by default, and a whole host of command line goodies are provided either by default or are easily obtainable through MacPorts/Fink. Apple provides command line versions of many of their GUI Apps, such as Disk Utility (diskutil), Software Update (softwareupdate), Universal Access speech synthesizer (say), and so on. 

Linux has a very powerful command line. Most problems that can be fixed from the GUI can be fixed even quicker from the command line. This isn't always going to be the case on Mac OS X. Perhaps this is a case of differing audiences: most OS X users don't want to see the terminal, whereas many Linux users expect it. Whatever the reason, the Mac OS X terminal may not be all you expect it to be when switching from Linux. However, Mac OS X is POSIX compliant and has a wealth of command line tools ported from Linux/BSD available. 




That's it for now. Feel free to suggest topics or call me out on inaccurate statements I may have made.

---

### Post by tubezninja on 2009-05-26
+1 your efforts sir. :)

---

### Post by Giant Speck on 2009-05-26
You're wrong.   [COLOR=White]Just kidding.[/COLOR]

---

### Post by ghindo on 2009-05-26
What prompted this?

---

### Post by schauerlich on 2009-05-26
> **ghindo said:**
> What prompted this?

I refer you to the first sentence of my post.

---

### Post by Tipped OuT on 2009-05-26
> **Giant Speck said:**
> You're wrong.   [COLOR=White]Just kidding.[/COLOR]

You're wrong. [COLOR="White"] [Invisible Text Goes Here][/COLOR]

---

### Post by schauerlich on 2009-05-26
> **Tipped OuT said:**
> You're wrong.

I suggest you hit Ctrl+A a read Giant Speck's post again. :)

---

### Post by Firestem4 on 2009-05-26
Great job on the write-out. I found out somet things I never before knew about Mac's/Apple. 

+1

---

### Post by Rainstride on 2009-05-26
> **EDavidBurg said:**
> Within the greater Linux community, and on these forums in particular, I have noticed a great deal of ignorance with respect to Mac OS X and Apple's contributions to the Unix community. I'd like to address these topics FAQ-style post, trying to avoid bias when possible. This is by no means a comprehensive list of issues that are commonly brought up, and I plan on adding to this post in the future. Feel free to suggest topics and I'll address them as I have time.




**Misconception: Mac OS X only runs on Apple Hardware.**
Truth: Well, sort of. True, its license states it can only be run on Apple hardware; However, Apple has done nothing to discourage the use of [OSx86](http://en.wikipedia.org/wiki/OSx86) and similar projects which enable you to run Leopard on non-Apple x86 hardware. Similarly, [Psystar](http://en.wikipedia.org/wiki/Psystar) and [PearC](https://www.pearc.de/) offer prebuilt computers which come with OS X preinstalled. It's not the OS X **doesn't** run on non-Apple hardware, it's just not Apple-sanctioned to do so. Currently whether this is legal is up for debate. Psystar is in the middle of a suit with Apple over the legitimacy of the Apple EULA. 




**M: Mac OS X is closed source.**
T: Parts of it are, parts of it aren't. Much of the core of OS X is [fully open source](http://www.apple.com/opensource/). Apple maintains a Unix distribution known as [Darwin](http://developer.apple.com/referencelibrary/Darwin/), which serves as the base for each release of OS X. Until recently, Darwin was distributed in binary form and available on Apple's website to download. Currently you can download Darwin's source in full [here](http://www.opensource.apple.com/). Apple has never intended Darwin to be a distribution for every day use; however, a community effort called [PureDarwin](http://www.puredarwin.org/) has sprung up to make it more usable.




**M: Apple is evil/ripped off BSD/GNU/FOSS advocates/kills babies.**
T: Apple has released all of the code it's integrated into Darwin/OS X back to the community. See [Apple's Open Source page](http://www.apple.com/opensource/) for more details.




**M: Mac OS X is just BSD with a shiny exterior.**
T: Apple has incorporated a good amount of BSD code into Darwin. No one disputes the valuable contributions made to the Unix community at large and indirectly to Apple by the BSD community. However, to say that Mac OS X is simply BSD with a shiny exterior is misleading at best. OS X's kernel, [XNU](http://en.wikipedia.org/wiki/XNU), is a hybrid kernel incorporating the [Mach Kernel](http://en.wikipedia.org/wiki/Mach_kernel), components from 4.3BSD, and [I/O Kit](http://en.wikipedia.org/wiki/I/O_Kit). 

What really makes Mac OS X unique are its Core services: [Core OpenGL](http://en.wikipedia.org/wiki/Core_OpenGL), [Core Image](http://en.wikipedia.org/wiki/Core_Image), [Core Video](http://en.wikipedia.org/wiki/Core_Video), and [Core Animation](http://en.wikipedia.org/wiki/Core_Animation), to name but a few. These frameworks provide a solid foundation upon which applications may be developed, and provide access to key components of the Darwin system lying beneath. 

The most visible contribution Apple has made to OS X is the [Cocoa API](http://en.wikipedia.org/wiki/Cocoa_(API)). Written in Objective-C, Cocoa was based off of the [OpenStep API](http://en.wikipedia.org/wiki/OpenStep) developed for NeXTSTEP. Cocoa is what gives Mac OS X applications their "shiny" Apple-y look and feel, and provides a standard across all applications to keep a consistent interface. A FOSS implementation of the OpenStep API exists, named [GNUstep](http://en.wikipedia.org/wiki/Gnustep).




**M: Mac OS X is bloated and slow.**
T: This is largely subjective. Sure, if you're installing Leopard on an original iMac, it's going to go slower than RMS in a pool of molasses.  I run Leopard on a MacBook2,1 and find it runs quite smoothly. Like with ANY operating system, your mileage may vary, and just because you have a bad experience, it does not mean the rest of the world has the same.




**M: Mac OS X caters to grandmas and creative types, not power users.**
T: This is not true at all. While Apple does do its best to make its software simple and easy to use, and provides great multimedia applications, OS X is by no means limited to bearded twentysomethings and their grandmothers. Apple provides the [Xcode](http://en.wikipedia.org/wiki/Xcode) development suite with every installation of OS X to encourage development on their platform. A fully POSIX compliant environment is provided, making it easy to port applications originally written for other Unix distributions. 

In addition, the great community of developers has made several utilities which simplify daily tasks and center navigation on the keyboard, the most famous example of which is [QuickSilver](http://en.wikipedia.org/wiki/Quicksilver_(software)). This excellent tool is what Gnome Do is based on, and it makes it easy to get around with just the keyboard. 




**M: Mac OS X isn't REAL Unix.**
T: Au contraire. With Leopard, Mac OS X has been [SUSv3](http://en.wikipedia.org/wiki/SUSv3) certified, and are Open Brand UNIX 03 registered products. That makes them more of a "real" Unix than Linux is.




**M: "Mac OS X 10.0/10.1/10.2/10.3 were a nightmare, I'll never touch it again."**
T: 10.0-10.3 *did* suck. Apple was struggling to stay afloat when Steve Jobs returned to Apple in 1997, and Apple was stuck using an outdated and slow OS on their computers. After [attempts to modernize the OS](http://en.wikipedia.org/wiki/Copland_(operating_system)) failed, Apple decided to abandon the OS 9 platform and move to a completely new OS. When Mac OS X 10.0 was released in 2000, it was buggy, slow, feature-poor and pinstripe-rich. It was Apple's effort to put *something* out to keep their business going. Once Apple had [a reliable source of income](http://en.wikipedia.org/wiki/Ipod), it was able to put more time and money into developing OS X into what it should have been. This goal was realized in 10.4, and further refined in 10.5. The last two point releases of OS X are radically different from the first four. 




**M: Mac OS X doesn't have any good free (libre or beer) software available.**
T: Not true at all. [MacPorts](http://en.wikipedia.org/wiki/Macports) and [Fink](http://en.wikipedia.org/wiki/Fink) are two efforts to port Linux/BSD apps to OS X, and make them accessible through repositories. Lots of great software is available through these avenues, and Apple even has an implementation of X11 for GUI applications. I use irssi on my MacBook with no trouble. In addition, sites such as [MacUpdate](http://www.macupdate.com/) are great for finding OS X freeware. For each shareware application, there's almost always an equivalent free application. I've never run into any trouble finding software to do what I need on Mac OS X.




That's it for now. Feel free to suggest topics or call me out on inaccurate statements I may have made.
trolling?

---

### Post by Firestem4 on 2009-05-26
> **Rainstride said:**
> trolling?

How is that trolling?

---

### Post by mcduck on 2009-05-26
I think I should add one about Macs in general:

[B]
M: Macs are over-priced[/B]
T: Depends on your model. Cheap, consumer-level stuff has more extra price, but when you move towards the high-end models the "mac-tax" in the price gets lower and lower, to the point where you really have hard time even building same level machine for the same price yourself, not to even mention buying a ready-built brand machine.

In other words, if you buy a entry-level mac you will pay extra for the brand name. If you buy one of the professional models it's pretty good value for your money.

---

### Post by schauerlich on 2009-05-26
> **Rainstride said:**
> trolling?

How do you figure?

> **mcduck said:**
> I think I should add one about Macs in general:

I'm focusing on the software, not the hardware.

---

### Post by Firestem4 on 2009-05-26
Ive never had much of a problem with the OS itself...but I can NOT justify the price for the machines...

---

### Post by tubezninja on 2009-05-26
> **Rainstride said:**
> trolling?


I fail to see how posting facts that correct common misinformation being spread on these forums is trolling.

---

### Post by Tipped OuT on 2009-05-26
> **EDavidBurg said:**
> I suggest you hit Ctrl+A a read Giant Speck's post again. :)

:lolflag: That's cool!

---

### Post by Warpnow on 2009-05-26
> **EDavidBurg said:**
> 
**Misconception: Mac OS X only runs on Apple Hardware.**
Truth: Well, sort of. True, its license states it can only be run on Apple hardware; However, Apple has done nothing to discourage the use of [OSx86](http://en.wikipedia.org/wiki/OSx86) and similar projects which enable you to run Leopard on non-Apple x86 hardware. Similarly, [Psystar](http://en.wikipedia.org/wiki/Psystar) and [PearC](https://www.pearc.de/) offer prebuilt computers which come with OS X preinstalled. It's not the OS X **doesn't** run on non-Apple hardware, it's just not Apple-sanctioned to do so. Currently whether this is legal is up for debate. Psystar is in the middle of a suit with Apple over the legitimacy of the Apple EULA. 


They are suing them yet you claim they aren't discouraging it? That's the only way to discourage it...


> **EDavidBurg said:**
> 
**M: Mac OS X is closed source.**
T: Parts of it are, parts of it aren't. Much of the core of OS X is [fully open source](http://www.apple.com/opensource/). Apple maintains a Unix distribution known as [Darwin](http://developer.apple.com/referencelibrary/Darwin/), which serves as the base for each release of OS X. Until recently, Darwin was distributed in binary form and available on Apple's website to download. Currently you can download Darwin's source in full [here](http://www.opensource.apple.com/). Apple has never intended Darwin to be a distribution for every day use; however, a community effort called [PureDarwin](http://www.puredarwin.org/) has sprung up to make it more usable.


Darwin is so stripped down and crappy that the distributions basing off of it are primitive versions of linux 20 years ago. Its nothing short of unusable code.


> **EDavidBurg said:**
> 
**M: Apple is evil/ripped off BSD/GNU/FOSS advocates/kills babies.**
T: Apple has released all of the code it's integrated into Darwin/OS X back to the community. See [Apple's Open Source page](http://www.apple.com/opensource/) for more details.


Appple has released Darwin. That is not OSX. Don't try and pretend they're the same. 


> **EDavidBurg said:**
> 
**M: Mac OS X is just BSD with a shiny exterior.**
T: Apple has incorporated a good amount of BSD code into Darwin. No one disputes the valuable contributions made to the Unix community at large and indirectly to Apple by the BSD community. However, to say that Mac OS X is simply BSD with a shiny exterior is misleading at best. OS X's kernel, [XNU](http://en.wikipedia.org/wiki/XNU), is a hybrid kernel incorporating the [Mach Kernel](http://en.wikipedia.org/wiki/Mach_kernel), components from 4.3BSD, and [I/O Kit](http://en.wikipedia.org/wiki/I/O_Kit). 

What really makes Mac OS X unique are its Core services: [Core OpenGL](http://en.wikipedia.org/wiki/Core_OpenGL), [Core Image](http://en.wikipedia.org/wiki/Core_Image), [Core Video](http://en.wikipedia.org/wiki/Core_Video), and [Core Animation](http://en.wikipedia.org/wiki/Core_Animation), to name but a few. These frameworks provide a solid foundation upon which applications may be developed, and provide access to key components of the Darwin system lying beneath. 

The most visible contribution Apple has made to OS X is the [Cocoa API](http://en.wikipedia.org/wiki/Cocoa_(API)). Written in Objective-C, Cocoa was based off of the [OpenStep API](http://en.wikipedia.org/wiki/OpenStep) developed for NeXTSTEP. Cocoa is what gives Mac OS X applications their "shiny" Apple-y look and feel, and provides a standard across all applications to keep a consistent interface. A FOSS implementation of the OpenStep API exists, named [GNUstep](http://en.wikipedia.org/wiki/Gnustep).


Say its not just shiny then the only example you give is of code that improves its interface's look?

> **EDavidBurg said:**
> 
**M: Mac OS X is bloated and slow.**
T: This is largely subjective. Sure, if you're installing Leopard on an original iMac, it's going to go slower than RMS in a pool of molasses.  I run Leopard on a MacBook2,1 and find it runs quite smoothly. Like with ANY operating system, your mileage may vary, and just because you have a bad experience, it does not mean the rest of the world has the same.


There is not a single operating system in existance that is slow on the fasest hardware. How it scales to older hardware, and how it treats the average user is the only real test of bloated or slow. People real experiences matter more than lab expiriments.


> **EDavidBurg said:**
> 
**M: Mac OS X caters to grandmas and creative types, not power users.**
T: This is not true at all. While Apple does do its best to make its software simple and easy to use, and provides great multimedia applications, OS X is by no means limited to bearded twentysomethings and their grandmothers. Apple provides the [Xcode](http://en.wikipedia.org/wiki/Xcode) development suite with every installation of OS X to encourage development on their platform. A fully POSIX compliant environment is provided, making it easy to port applications originally written for other Unix distributions. 


I fail to see how including a development environment makes it productive or for power users. Every operating system has a development environment.

> **EDavidBurg said:**
>  
In addition, the great community of developers has made several utilities which simplify daily tasks and center navigation on the keyboard, the most famous example of which is [QuickSilver](http://en.wikipedia.org/wiki/Quicksilver_(software)). This excellent tool is what Gnome Do is based on, and it makes it easy to get around with just the keyboard. 


Several utilities? Proof of concept, perhaps, but not results.


> **EDavidBurg said:**
> 
**M: Mac OS X isn't REAL Unix.**
T: Au contraire. With Leopard, Mac OS X has been [SUSv3](http://en.wikipedia.org/wiki/SUSv3) certified, and are Open Brand UNIX 03 registered products. That makes them more of a "real" Unix than Linux is.


When people say that, they aren't talking about ceritifications. They're talking about customization, and power. OSX is not the same as any other unix derivative because it prevents the total customization options that are available in other types. 


> **EDavidBurg said:**
> 
**M: "Mac OS X 10.0/10.1/10.2/10.3 were a nightmare, I'll never touch it again."**
T: 10.0-10.3 *did* suck. Apple was struggling to stay afloat when Steve Jobs returned to Apple in 1997, and Apple was stuck using an outdated and slow OS on their computers. After [attempts to modernize the OS](http://en.wikipedia.org/wiki/Copland_(operating_system)) failed, Apple decided to abandon the OS 9 platform and move to a completely new OS. When Mac OS X 10.0 was released in 2000, it was buggy, slow, feature-poor and pinstripe-rich. It was Apple's effort to put *something* out to keep their business going. Once Apple had [a reliable source of income](http://en.wikipedia.org/wiki/Ipod), it was able to put more time and money into developing OS X into what it should have been. This goal was realized in 10.4, and further refined in 10.5. The last two point releases of OS X are radically different from the first four. 


Yet, OSXs primary means of bragging its own power is to compare it to Windows Vista. Hrm, hypocrite much?


> **EDavidBurg said:**
> 
**M: Mac OS X doesn't have any good free (libre or beer) software available.**
T: Not true at all. [MacPorts](http://en.wikipedia.org/wiki/Macports) and [Fink](http://en.wikipedia.org/wiki/Fink) are two efforts to port Linux/BSD apps to OS X, and make them accessible through repositories. Lots of great software is available through these avenues, and Apple even has an implementation of X11 for GUI applications. I use irssi on my MacBook with no trouble. In addition, sites such as [MacUpdate](http://www.macupdate.com/) are great for finding OS X freeware. For each shareware application, there's almost always an equivalent free application. I've never run into any trouble finding software to do what I need on Mac OS X.


Software to do what you need should never be a problem. If it is, then it isn't really much of an operating system. The trick here lies in choice. In linux, I don't just find one app for what I want to do, I find 20, and pick my favorite.

---

### Post by tubezninja on 2009-05-26
> **mcduck said:**
> I think I should add one about Macs in general:

[B]
Macs are over-priced[/B]
Depends on your model. Cheap, consumer-level stuff has more extra price, but when you move towards the high-end models the "mac-tax" in the price gets lower and lower, to the point where you really have hard time even building same level machine for the same price yourself, not to even mention buying a ready-built brand machine.

In other words, if you buy a entry-level mac you will pay extra for the brand name. If you buy one of the professional models it's pretty good value for your money.

There's also something very interesting about mac hardware: they retain their value much more than non-Apple hardware does.  Check the prices on eBay for older Apple gear, and you'll see they command high prices, unlike commodity PC hardware which is largely worthless in a couple of years.  it's not uncommon to be able to sell your "old" mac and use the proceeds to significantly fund upgrading to new stuff.

The hardware is also supported longer.  I've seen 7 year old dual G4 Mac pros run the latest version of OS X quite well.

---

### Post by tubezninja on 2009-05-26
> **Warpnow said:**
> 
Darwin is so stripped down and crappy that the distributions basing off of it are primitive versions of linux 20 years ago. Its nothing short of unusable code.

Darwin is not linux.  Please do not purport to make statements of fact when you are not aware of them.



> 
Apple has released Darwin. That is not OSX. Don't try and pretend they're the same. 

Darwin is the basis behind OS X.  And he didn't say they released OS X in its entirety.  He said Apple followed the spirit of FOSS by contributing their changes to the Open source code they DID use back to the FOSS community.

> There is not a single operating system in existance that is slow on the fasest hardware. How it scales to older hardware, and how it treats the average user is the only real test of bloated or slow. People real experiences matter more than lab expiriments.

I beleive he is using real world experiences, and not lab data.  So what is your point here?




> I fail to see how including a development environment makes it productive or for power users. Every operating system has a development environment.

Not Windows; you must pay for it.



> Several utilities? Proof of concept, perhaps, but not results.

QuickSilver is not proof of concept, it's the real thing.



> When people say that, they aren't talking about ceritifications. They're talking about customization, and power. OSX is not the same as any other unix derivative because it prevents the total customization options that are available in other types. 

Sorry, but this is not correct.  The certifications require that the power, customization and behaviors are all there.  And so they are with OS X.


> Yet, OSXs primary means of bragging its own power is to compare it to Windows Vista. Hrm, hypocrite much?

No, it's just common sense to go after the majority market share.  Linux hasn't made a dent yet.
And when you get down to it, a lot of the semantics arguments and nitpicking I see here is all caused by an inferiority complex at its base.  The point is, the linux community would be better suited making Linux better than sitting and dissing OS X.  OS X improves and evolves... Linux..?

---

### Post by schauerlich on 2009-05-26
> **Warpnow said:**
> They are suing them yet you claim they aren't discouraging it? That's the only way to discourage it...


What they are discouraging is *profiting* on Mac OS X by distributing it on non-Apple hardware. If Apple wanted to, it could shut down the [OSx86 Project](http://www.osx86project.org/). It hasn't.

> 
Say its not just shiny then the only example you give is of code that improves its interface's look?


Core services do much more than just improve the interface.

---

### Post by Warpnow on 2009-05-26
> **"scaredpoet"]Darwin is not linux. Please do not purport to make statements of fact when you are not aware of them.[/quote]

Nor did I say it was. What I meant was the the only darwin based operating systems are at that level of development.

[quote="scaredpoet"]I beleive he is using real world experiences, and not lab data. So what is your point here?[/quote]

My point is to refute his idea that people's negative experiences are irrelevent.

[quote="scaredpoet"]Not Windows said:**
> 

Express is free, actually.

[quote="scaredpoet"]QuickSilver is not proof of concept, it's the real thing.

Wasn't referring the application itself, but rather his assertion of what it represented.

[quote="scaredpoet"]Sorry, but this is not correct. The certifications require that the power, customization and behaviors are all there. And so they are with OS X.[/quote]

Its certified, therefore it must be. It must be because its certified.

X is true, therefore Y is true, therfore X is true.

Circular logic, my friend.

[quote="scaredpoet"]No, it's just common sense to go after the majority market share. Linux hasn't made a dent yet.
And when you get down to it, a lot of the semantics arguments and nitpicking I see here is all caused by an inferiority complex at its base. The point is, the linux community would be better suited making Linux better than sitting and dissing OS X. OS X improves and evolves... Linux..?[/quote]

Compare Ubuntu 9 to Ubuntu 6 and tell me there's no evolution. To propose there isn't is nothing but silly.

I, for one, don't measure Linux's success based on usershare. It makes no difference to me if people use it. I prefer it, and so I use it. Other people can use whatever they want. But I feel this way because I'm not a fan boy. I don't actually dislike OSX, I just dislike what this thread is trying to do. Its not an honest representation. ITs blatent fanboyism and a very biased representation of OSX.

[quote="EDavidBurg"]What they are discouraging is profiting on Mac OS X by distributing it on non-Apple hardware. If Apple wanted to, it could shut down the OSx86 Project. It hasn't.[/quote]

Yeah, just like Microsoft stomped out all that Windows pirating, right?

Apple could not shut down OSX86 any more than it could blot out the sun shining on North America. It could try. It could pour money into monitoring and attorneys, and shut out some of the light, but some would always peak through. Newsgroups, forums, distributed via torrent. It would be a fruitless endeavor that lost them money.

A company, though, that's an organized body they can sue. Its the only actual way they can discourage OSX becoming cross platform.

---

### Post by mcduck on 2009-05-26
> **EDavidBurg said:**
> 
I'm focusing on the software, not the hardware.

Just look at the post below yours, and you'll see why I decided to add that one.. :D

---

### Post by schauerlich on 2009-05-26
> **Warpnow said:**
> Nor did I say it was. What I meant was the the only darwin based operating systems are at that level of development.

Linux didn't exist 20 years ago.

> 
Wasn't referring the application itself, but rather his assertion of what it represented.


I'm a power user who is comfortable on OS X. Are you saying my experiences are not legitimate?

> 
Its certified, therefore it must be. It must be because its certified.

X is true, therefore Y is true, therfore X is true.

Circular logic, my friend.


The people who decide what can be called Unix have decided that Mac OS X meets their standards. Therefore, Mac OS X is Unix. I fail to see any circular logic in that.


> I don't actually dislike OSX, I just dislike what this thread is trying to do. Its not an honest representation. ITs blatent fanboyism and a very biased representation of OSX.

Can you quote these very biased instances of blatant fanboyism?

---

### Post by Rainstride on 2009-05-26
> **EDavidBurg said:**
> How do you figure?



I'm focusing on the software, not the hardware.

i was mostly asking not accusing, it just seemed a bit weird to me that a long MAC thread about "Common misconceptions" would popup on the ubuntu forums. though it is mostly the fact you typed it like an infomercial:D. (read it in billy maze's voice:D). guess i was wrong:(.

---

### Post by Warpnow on 2009-05-26
> **Rainstride said:**
> t you typed it like an infomercial

Exactly. Its a representation of the pure upsides of OSX without any thought on the truth behind these "myths". There are always truths behind lies, if they are in fact lies, but the approach here is that these things are totally 100% wrong, when they are actually half-truths. 

Presenting one side without heeding the other side, my friends, is the making of fanboyism.

---

### Post by schauerlich on 2009-05-26
> **Rainstride said:**
> i was mostly asking not accusing, it just seemed a bit weird to me that a long MAC thread about "Common misconceptions" would popup on the ubuntu forums. though it is mostly the fact you typed it like an infomercial:D. (read it in billy maze's voice:D). guess i was wrong:(.

Well, this community has its misconceptions about OS X. It's frustrating to encounter these every time an Apple-related thread pops up. Hopefully in the future people will be able to refer back to this thread when a common misconception is rehashed, similar to how one might link to an FAQ when a common question is brought up.

---

### Post by Warpnow on 2009-05-26
> **EDavidBurg said:**
> Well, this community has its misconceptions about OS X. It's frustrating to encounter these every time an Apple-related thread pops up. Hopefully in the future people will be able to refer back to this thread when a common misconception is rehashed, similar to how one might link to an FAQ when a common question is brought up.

And if they read your thread and still are of the opinion these "misconceptions" are not misconceptions but rather vague generalizations about the operating system that might have gone too far, but are rooted in truth?

---

### Post by schauerlich on 2009-05-26
> **Warpnow said:**
> Exactly. Its a representation of the pure upsides of OSX without any thought on the truth behind these "myths". There are always truths behind lies, if they are in fact lies, but the approach here is that these things are totally 100% wrong, when they are actually half-truths.

You'll notice I qualify many of my statements with "sort of" or "partly," and then go on to explain what I mean.

I'm addressing common **negative misrepresentations** of Mac OS X. How am I to explain the real situation without mentioning the upsides of OS X?

---

### Post by schauerlich on 2009-05-26
> **Warpnow said:**
> And if they read your thread and still are of the opinion these "misconceptions" are not misconceptions but rather vague generalizations about the operating system that might have gone too far, but are rooted in truth?

This is merely an adverbial clause; I will allow you another post to finish this sentence so that I might respond to it.

---

### Post by Warpnow on 2009-05-26
> **EDavidBurg said:**
> This is merely an adverbial clause; I will allow you another post to finish this sentence so that I might respond to it.

No thanks. You're aware of what I meant, and I don't really care enough about grammar to "correct it".

---

### Post by schauerlich on 2009-05-26
If the vague generalization has gone too far, couldn't you say that it's a misunderstanding of the OS? Perhaps... a misconception about it?

---

### Post by Warpnow on 2009-05-26
> **EDavidBurg said:**
> If the vague generalization has gone too far, couldn't you say that it's a misunderstanding of the OS? Perhaps... a misconception about it?

Only if you ignore the word "misconception". The notion is not erroneous, nor is it mistakenly made. It is simply exaggerated.

---

### Post by Rainstride on 2009-05-26
> **EDavidBurg said:**
> Well, this community has its misconceptions about OS X. It's frustrating to encounter these every time an Apple-related thread pops up. Hopefully in the future people will be able to refer back to this thread when a common misconception is rehashed, similar to how one might link to an FAQ when a common question is brought up.

ok, now this thread makes more since to me:D. keep in mind thought there will always be that small group that won't listen to reason or facts(fanboys;)).

---

### Post by schauerlich on 2009-05-26
> **Warpnow said:**
> Only if you ignore the word "misconception". The notion is not erroneous, nor is it mistakenly made. It is simply exaggerated.

Baseball is a horrible, terrible sport. The men who play it are bad people. Sometimes, they just throw the ball at the other team's batter's head! Pitchers should be arrested for murder!


There is a kernel of truth in my statements: Lots of bad people have played baseball. People have been struck in the head by pitches, some of which were thrown there intentionally. However, the idea that baseball players are bad people and that baseball is a horrible sport are misconceptions based on a notion that's not entirely unfounded.

---

### Post by kernelhaxor on 2009-05-26
> **Warpnow said:**
> 
Apple could not shut down OSX86 any more than it could blot out the sun shining on North America. It could try. It could pour money into monitoring and attorneys, and shut out some of the light, but some would always peak through. Newsgroups, forums, distributed via torrent. It would be a fruitless endeavor that lost them money.

A company, though, that's an organized body they can sue. Its the only actual way they can discourage OSX becoming cross platform.

Dead on!

---

### Post by collinp on 2009-05-26
OS X is a operating system.. actually, a version of a operating system. Linux is Linux, and Windows is Windows. Use what you prefer.

I agree with the OP in that there are many misconceptions about OS X in the Ubuntu community and in the Linux community as a whole. People label OS X as a closed-source POS without looking at the facts beforehand. OS X has its uses: it is easy to use and is supported widely in the commercial software industry. Linux also has uses, and so does Windows. So, please actually take a look at the facts before bashing something.

---

### Post by Warpnow on 2009-05-26
> **EDavidBurg said:**
> Baseball is a horrible, terrible sport. The men who play it are bad people. Sometimes, they just throw the ball at the other team's batter's head! Pitchers should be arrested for murder!


That is a misconception. You are drawing erroneous conclusions from what you are seeing. You think he's throwing at the other batter's head, rather than across the plate.

However, the things in this thread, are not misconceptions. They are not based on erroneous conclusions. They are simply generalizations of the truth.

---

### Post by koshatnik on 2009-05-26
I cannot take seriously anyone that says that OSX isnt slow.

---

### Post by 3rdalbum on 2009-05-26
> **EDavidBurg said:**
> 
**M: Mac OS X isn't REAL Unix.**
T: Au contraire. With Leopard, Mac OS X has been [SUSv3](http://en.wikipedia.org/wiki/SUSv3) certified, and are Open Brand UNIX 03 registered products. That makes them more of a "real" Unix than Linux is.

Try using Mac OS X on the command-line. Fsck is available, Pico is available, Grep is available, Mount is available. Everything else is completely different to any Unix I've ever used. Some commands that are available on OS X simply don't do anything! They seem to be there just to wave the flag for BSD.

> **M: "Mac OS X 10.0/10.1/10.2/10.3 was a nightmare, I'll never touch OS X again."**
T: 10.0-10.3 *did* suck.

Why did Mac fans keep telling me that it was the greatest thing since sliced bread?

---

### Post by collinp on 2009-05-26
> **koshatnik said:**
> I cannot take seriously anyone that says that OSX isnt slow.

OS X isnt slow. Seriously, it isnt slow on any of the latest computers by Apple.

---

### Post by mr.propre on 2009-05-26
> **M: Mac OS X is closed source.**
T: Parts of it are, parts of it aren't. Much of the core of OS X is fully open source. Apple maintains a Unix distribution known as Darwin, which serves as the base for each release of OS X. Until recently, Darwin was distributed in binary form and available on Apple's website to download. Currently you can download Darwin's source in full here. Apple has never intended Darwin to be a distribution for every day use; however, a community effort called PureDarwin has sprung up to make it more usable.

Bad bad argument, I once saw an article about an "open source" OS X version, the only thing you had was a terminal screen. You aren't wrong, Apple is indeed partly open-source, but without the closed source it worthless. See it as a car where the engine is open-source but the rest is closed source. No end user will ever be happy with just the engine. Most people won't even call it a car.


About the hardware, all the OS X versions running on non-apple hardware are modified, so OS X doesn't run on other systems, unless you modified it. The only reason why Apple allows it is because almost nobody uses a modified OS X version. It would cost apple just to much to do something about it and next to dad, it's bad PR. But look @ Psystar as soon as somebody is making money from it you can explain it to a judge.

---

### Post by schauerlich on 2009-05-26
> **3rdalbum said:**
> Try using Mac OS X on the command-line. Fsck is available, Pico is available, Grep is available, Mount is available. Everything else is completely different to any Unix I've ever used. Some commands that are available on OS X simply don't do anything! They seem to be there just to wave the flag for BSD.

Um. I do. Daily. Mac OS X is fully POSIX compliant. It's got everything a *nix distro is supposed to, and through MacPorts/Fink, has a whole lot more. I use irssi, wget, and a bunch of other "linux" programs on OS X. I have no idea where you got the notion that the Mac OS X command line is "incomplete." Sounds like I should add a new section.

> **mr.propre said:**
> Bad bad argument, I once saw an article about an "open source" OS X version, the only thing you had was a terminal screen. You aren't wrong, Apple is indeed partly open-source, but without the closed source it worthless. See it as a car where the engine is open-source but the rest is closed source. No end user will ever be happy with just the engine. Most people won't even call it a car.



I never said Mac OS X was an open source OS. It's just not entirely closed source. Apple used a good amount of open source code in Mac OS X, and has release their modifications back to the community. I specifically said that Darwin was never meant to be a day-to-day OS and was simply a collection of all of Mac OS X's FOSS components.

---

### Post by Sublime Porte on 2009-05-26
EDavidBurg,

Whilst I  understand you just wanna defend something you think is worth defending and set the record straight and all that, and in most points that's what you did, but.. you had to mention a few things, just to rub people up the wrong way, and continue the hostility... why?

> **Misconception: Mac OS X only runs on Apple Hardware.**This one is fine, no problem limiting yourself to a known set of hardware, certainly makes getting things working a lot easier, I can certainly undertsand Apple doing this, and think it's fine.No need to defend anything here..
> **M: Mac OS X is closed source.**They're in it for the profits, so of course it's gotta be closed source. Again, don't really blame them for this. Might not agree or like it, but it's their perogative. However, I do think they should give back something more to the Open source movement though, since they've taken quite a lot from it. KHTML and quite a few GNU tools, as well as the X server, probably heaps more I forgot.> **M: Apple is evil/ripped off BSD/GNU/FOSS advocates/kills babies.**As above, they should give back more. No problem with them taking it, but support the Open source movement, and help it to grow more. As I see it, we are both in the same boat against Microsoft, so why not help one another?> **M: Mac OS X is just BSD with a shiny exterior.**This contradicts your later point about people claiming it's not Unix... Either it's just BSD with a flashy GUI, or it's not Unix at all.. which one? I personally think the Aqua GUI is much more a part of OSX than the BSD base is.> **M: Mac OS X is bloated and slow.**I found it to be quite light and snappy. Gotta break the mould of the stereotypical Linux user there. I think it makes great usage of resources. It's compositor is quite smooth, certainly works better than compiz on my Eee 1000.> **M: Mac OS X caters to grandmas and creative types, not power users.**Again, nothing to apologise for there.> **M: Mac OS X isn't REAL Unix.**It's certainly based on real Unix, but you just spoil this point by making outrageous statements like this one... **"**That makes them more of a "real" Unix than Linux is.". Having enough money to buy yourself a shiney certificate doesn't mean it's more of a Unix than Linux. Linux has far more in common with other Unix flavours than OSX does anyday, we just aren't wasting money to write it on a certificate.

---

### Post by bryonak on 2009-05-26
Well... let's take a look on it... (trying an alternative form of quoting as to try to save a bit of vertical space)


*[color=green]I'd like to address these topics FAQ-style post, **trying to avoid bias** when possible.[/color]*

You didn't succeed... your OP has plenty of rhetoric that can't be called anything other than bias.
Nothing wrong with that, everyone is entitled to their opinion... but I'm not sure whether it's really productive to take ones bias about a product to the "competitor's fan zone" ;)


*[color=green]This thread concerns Mac OS X, the operating system. It it not for debating the price of Apple hardware, Apple's business tactics, or the color purple. Thank you.[/color]*

In your initial paragraph, you wrote that you want to fix misconceptions about (among others) Apple's contributions to FOSS... this spans a bit more than just OSX itself.
I suggest removing that line and it'll be OK


[i][color=green]**Mac OS X only runs on Apple Hardware.**
Truth: Well, sort of. True, its license states it can only be run on Apple hardware; However, Apple has done nothing to discourage the use of [OSx86](http://en.wikipedia.org/wiki/OSx86) and similar projects which enable you to run Leopard on non-Apple x86 hardware. Similarly, [Psystar](http://en.wikipedia.org/wiki/Psystar) and [PearC](https://www.pearc.de/) offer prebuilt computers which come with OS X preinstalled.[/color][/i]

For a bias rhetoric example: you try to placate the argument that this is true.
If you take the "misconception" at factual value, it's obviously false, because there exist non-Macs that run (a hacked) OSX.
If you consider the legal aspect, then it's clearly (and not "sort of") true, because Apple explicitly forbids it. When users mention "runs on ... hardware", you should always consider if it's illegal to do so. Right now we have a situation where it's de-facto illegal, and I really wouldn't like to be the test case.
They do threaten legal action against those who put up tutorials on installing OSX on non-Macs (Wired anyone?).
And Psystar... well, they get attacked as forcibly as Apple is capable of.
The reason they're not taking steps against OSx86 is that it'd be obviously a silly endavour. It'd hurt their PR way too much without any benefit whatsoever (they couldn't stop it).


[i][color=green]**Mac OS X is closed source.**
T: Parts of it are, parts of it aren't.[/color][/i]

This partially belongs to the "contributions" topic.
When talking about GPL'd code (KHTML or CUPS for instance), they have to return the changes... which is where they do the minimum to stay legal. Correct me if I'm wrong, but I don't know of any significant GPL'd Apple project they built from scratch themselves. So much for the most community-fostering FOSS license.
They do keep their BSD parts open, which is very commendable (since they legally don't have to). Then again, those are widely availably anyway... without having to pay a vastly overpriced (my personal view. I prefer to get my source code for free) sum.
The crucial point is what Apple does with its original, in-house code, which they couldn't get for free from somewhere. This is what differentiates them from the BSDs, this is what characterises Apple... and it's closed and proprietary.


[i][color=green]**Apple is evil/ripped off BSD/GNU/FOSS advocates/kills babies.**
T: Apple has released all of the open source code it's integrated into Darwin/OS X back to the community. See [Apple's Open Source page](http://www.apple.com/opensource/) for more details.[/color][/i]

*"As the first major computer company to make Open Source development a key part of its ongoing software strategy"*
What? IBM? Oracle? Sun?

What also astounds me is that they don't list WebKit as their project (they do however mention a a rendering engine), but bash? GNU bash?
When did they improve Ed, PHP or ZFS (all listed) the last time?
Or do they simply list projects they use? But what "credit for contribution" would that deserve then?

In my opinion this page is quite a blemish for Apple.


*[color=green]**Mac OS X is just BSD with a shiny exterior.**[/color]*

This is one of the simplifications used for mindless bashing...
You do tactically well with including such easily refutable phrases with the other issues.


[i][color=green]**Mac OS X is bloated and slow.**
T: This is largely subjective. Sure, if you're installing Leopard on an original iMac, it's going to go slower than RMS in a pool of molasses.[/color][/i]

Are you implying something? Never mind ;)
I think this point is moot, since I'm not allowed to try OSX on my Pentium2, which runs Ubuntu/XFCE (at the moment, alternating with other lightweight options). And old Macs are just much rarer (not as easy to get) as old PCs.
But you're right, it *is* subjective and Apple ensures that their current machines fit the specs.


[i][color=green]**Mac OS X caters to grandmas and creative types, not power users.**
T: This is not true at all. [...] A fully POSIX compliant environment is provided, making it easy to port applications originally written for other Unix distributions.
[...]This excellent tool is what Gnome Do is based on, and it makes it easy to get around with just the keyboard.[/color][/i]

First and last sentence are just left as an example of the mentioned bias rhetoric.
They do make it easy to port Unix apps, but they neither improve their support for X11 nor wine... today there's way more users and applications for those two that could enhance OSX than Unix applications which need to be ported. POSIX (a term that has been created by Richard Stallman - whoops, talk about bias rhetoric ;)) compliance is not exactly something to brag about. The BSDs don't bother, even though it wouldn't be hard for them.
GNU/Linux on the other hand usually targets LSB compliance, which is an extension of POSIX.


[i][color=green]**M: Mac OS X isn't REAL Unix.**
T: Au contraire. With Leopard, Mac OS X has been [SUSv3](http://en.wikipedia.org/wiki/SUSv3) certified, and are Open Brand UNIX 03 registered products. That makes them more of a "real" Unix than Linux is.[/color][/i]

Again tactially well placed.
As for Linux being an Unix... repeat after me:
GNU - GNU is not Unix.
GNU - ...


[i][color=green]**M: "Mac OS X 10.0/10.1/10.2/10.3 was a nightmare, I'll never touch OS X again."**
T: 10.0-10.3 *did* suck. Apple was struggling [...][/color][/i]

Way too many apologies to make it a good argument. And it's crude to bad-mouth the thing you had before at the moment you get a newer version, nevermind that you use it for contrasting.
Just to say the first third needs argumentational improvement, otherwise it's OK.


*[color=green]**Mac OS X doesn't have any good free (libre or beer) software available.**[/color]*

Are people honestly claiming this?
Another tought... I have no numbers here, but I bet both Linux and Windows have more Free software than OSX. Don't set me up on that though ;)


OSX is a very well designed and stable system. I've been using 10.4 and 10.5 for some time, but the usability (hand-holding) didn't suit me.

Apple on the other hand... I fail to see how anyone can put them in the Linux-friendly category.
They don't show hostile behaviour towards FOSS in general... but that's not the point on a Linux forum, in a Linux community, is it?

---

### Post by schauerlich on 2009-05-26
For some reason quoting isn't working for me right now, so I get to copy and paste all of this. YAY!

> They're in it for the profits, so of course it's gotta be closed source. Again, don't really blame them for this. Might not agree or like it, but it's their perogative. However, I do think they should give back something more to the Open source movement though, since they've taken quite a lot from it.

Well, a good chunk of it *is* closed source. No one is denying that. However, a large portion of it is open source, and many are quick to decry Apple for exploiting the FOSS community and play up the significance of the FOSS contributions to the project, yet at the same time make the argument that OS X is all closed source. Neither statement is entirely true, and I tried to explain as best I could what the current situation looks like.

Apple pushes all of the changes it makes to FOSS software back to the community. This helps to improve BSD/GNU/wherever they got it from. Short of open sourcing their in-house code, how would you like them to contribute more back to the FOSS movement?

> This contradicts your later point about people claiming it's not Unix... Either it's just BSD with a flashy GUI, or it's not Unix at all.. which one?

I don't accept the premise of your dichotomy. Linux is Unix-like without being BSD based... Solaris is SUS certified Unix and is not BSD. It's plenty easy to be Unix-y without being "just BSD with a flashy GUI".

> Linux has far more in common with other Unix flavours than OSX does anyday, we just aren't wasting money to write it on a certificate.

Linux has always beens classified as Unix-like. I will grant you that Linux has more in common with Unix-like systems than Mac OS X does. But to say Linux is more Unix-y than something that has been certified as Unix... just doesn't make sense.

---

### Post by schauerlich on 2009-05-26
> For a bias rhetoric example: you try to placate the argument that this is true.

I'm biased because I disagree with you...?

The fact of the matter is: Mac OS X runs on non-Apple hardware. That is the question I set out to answer.

> f you consider the legal aspect, then it's clearly (and not "sort of") true, because Apple explicitly forbids it.

The legality of that language from Apple's EULA is under dispute at the moment. It's legally murky.

> They do keep their BSD parts open, which is very commendable (since they legally don't have to). Then again, those are widely availably anyway... without having to pay a vastly overpriced (my personal view. I prefer to get my source code for free) sum.

You can get the BSD version of these programs all over the internet, but the Apple-modified versions are also distributed by Apple. Apple's modifications are a "widely available," as you say.

The source code is available for free. Take a look at the links in the OP.

> Way too many apoligies to make it a good argument. And it's crude to bad-mouth the thing you had before the moment you get a newer version, nevermind that you use it for contrasting.

The crux of my argument is that the first four point releases were of much lower quality than the last two, and that one shouldn't be put off by their experiences of those releases and not like OS X because of it.

---

### Post by sujoy on 2009-05-26
certifications can be bought. i am not saying that OS X bought it. i never used any apple product so i know nothing about them. however, just having a certificate proves nothing.

---

### Post by Simian Man on 2009-05-26
So basically your saying that OSX:
[LIST]
[*]Can sort of run on lots of hardware
[*]Is sort of open source
[*]Is sort of hackable
[*]Is not too slow
[*]Has some Linux software
[/LIST]

Why would I want that when Linux:
[LIST]
[*]Will run on anything
[*]Is totally open source
[*]Is completely hackable
[*]Is as fast as you want it to be
[*]Has tons of great software
[*]And costs nothing
[/LIST]

And don't try to pretend that Apple is a good-willed company.  If they had a 90% market-share, they would be more vindictive than Microsoft.
[IMG]http://www.heandfi.org/wp-content/uploads/2007/06/mac_pc_linux.jpg[/IMG]

---

### Post by Matthewthegreat on 2009-05-26
> **Simian Man said:**
> So basically your saying that OSX:
[LIST]
[*]Can sort of run on lots of hardware
[*]Is sort of open source
[*]Is sort of hackable
[*]Is not too slow
[*]Has some Linux software
[/LIST]

Why would I want that when Linux:
[LIST]
[*]Will run on anything
[*]Is totally open source
[*]Is completely hackable
[*]Is as fast as you want it to be
[*]Has tons of great software
[*]And costs nothing
[/LIST]

And don't try to pretend that Apple is a good-willed company.  If they had a 90% market-share, they would be more vindictive than Microsoft.
[IMG]http://www.heandfi.org/wp-content/uploads/2007/06/mac_pc_linux.jpg[/IMG]

:lolflag:

---

### Post by aysiu on 2009-05-26
I agree with Simian Man.

A lot of this defense of Mac OS X seems to be in a "Well, sort of, technically, that's not exactly true, really" tone.

If I can't just plop a Mac OS X DVD in an optical drive of a non-Apple computer and install OS X without having to refer to intricate instructions on a website and without having to worry about updates breaking my installation, then I consider Mac OS X to more or less run only on Apple computers. And that's discounting the Apple lawsuit against Psystar, which (as others have pointed out) seems to indicate Apple is not a fan of such EULA-breaking practices.

The fact that you have to resort to kind of, well, sort of reasoning really discounts what your arguing against as being *common misconceptions* and being more simplifications of truth. But cases could be made (and have been by some other people in this thread) that your points are also simplifications of another kind.

Bottom line: I consider any assessment of an OS that is all-positive or all-negative to be biased. Tons of people on these forums are biased against OS X. And you clearly are biased in favor of it.

---

### Post by tubezninja on 2009-05-26
> **aysiu said:**
> 
Bottom line: I consider any assessment of an OS that is all-positive or all-negative to be biased. Tons of people on these forums are biased against OS X. And you clearly are biased in favor of it.

In the final analysis, This statement sums up the true nature  of UF: the linux/FOSS bias is pervasive in these forums, and it's kind of sad, really.

I don't believe Edavidburg once attempted to say OS X is all positive.  yet it was interpreted that way, because that made it more convenient for you to attack his position if it was so misinterpreted.

---

### Post by aysiu on 2009-05-26
> **scaredpoet said:**
> In the final analysis, This statement sums up the true nature  of UF: the linux/FOSS bias is pervasive in these forums, and it's kind of sad, really. It makes logical sense for a Linux/FOSS bias to exist on a Linux forum, doesn't it? I'm actually surprised at how relatively (not completely, of course) unbiased users are here toward Windows and Mac OS X. I see a lot more Windows and Mac defenders here than I would expect to see Linux defenders on a Windows or Mac forum.

> I don't believe Edavidburg once attempted to say OS X is all positive.  yet it was interpreted that way, because that made it more convenient for you to attack his position if it was so misinterpreted. It was interpreted that way, because everything in the original post was in defense of Mac OS X. No bad points were mentioned at all. I consider that bias. It has nothing to do with convenience and everything to do with logic.

All positives, no negatives: bias.
All defense, no offense: bias.

There's nothing convenient about bias existing in the OP. In fact, I'd have preferred it if the misconceptions in the original post went both ways--exposing how people attack Mac OS X unnecessarily *and also* exposing how people defend Mac OS X unnecessarily. Macs are not evil or all bad. Neither are they perfect and all good.

---

### Post by Keithhed on 2009-05-26
I completely disagree, as I find the colour purple repulsive. ;)

---

### Post by kernelhaxor on 2009-05-26
> **EDavidBurg said:**
> I'm biased because I disagree with you...?

The fact of the matter is: Mac OS X runs on non-Apple hardware. That is the question I set out to answer.


I think you are biased because you say that OSX runs on non-Apple hardware but don't even mention a key related point that the OS needs to be hacked for it to do so.  Out of the box doesn't work - so technically, Apple OSX doesn't run on Apple hardware, only a modified version of it (once you modify, I don't know if you can still call it truly Apple OSX)

Your talk about legitimacy(which is totally unrelated to the "misconception" you set to answer) in the "truth"  just shows how much you want to defend Apple.  Mentioning explicitly in the license isn't enough discouragement from Apple to not run their OS on non-Apple hardware?  Sure, the technical legality might be under dispute, but don't we all understand what the license says in a nutshell about running it on which hardware.  Any Apple/Mac store from where you buy the OS would tell you not to run it on non-Apple hardware, but oh wait, thats not enough discouragement, I got a few spare millions of dollars to go after Apple on some legality of language.

---

### Post by collinp on 2009-05-26
> **aysiu said:**
> It was interpreted that way, because everything in the original post was in defense of Mac OS X. No bad points were mentioned at all. I consider that bias. It has nothing to do with convenience and everything to do with logic.

I think he stated in a earlier post that he was only attacking the negative misconceptions about OS X. I'm not sure if a person would call that bias or not.

---

### Post by nickld on 2009-05-26
F**k Apple and Steve Jobs.

---

### Post by Icehuck on 2009-05-26
> **Hellow said:**
> I think he stated in a earlier post that he was only attacking the negative misconceptions about OS X. I'm not sure if a person would call that bias or not.

If it's on this forum and anything but pro-linux then it's biased.

---

### Post by aysiu on 2009-05-26
> **Icehuck said:**
> If it's on this forum and anything but pro-linux then it's biased.
No, if it's pro-Linux only then it's also biased.

In fact, few things annoy me more than when people try to present Linux as a cure-all for all computing problems and a drop-in replacement for Windows.

Windows, Linux, and Mac OS X all have their respective pros and cons.

---

### Post by aysiu on 2009-05-26
Can folks please refrain from making generalized statements that indirectly end up being *ad hominem* attacks? If you want to **disagree** with what someone has said, then disagree with what she has said.

**Don't** try to **dismiss** it with contempt as some kind of "typical" behavior of the forums.

Also, please, no personal attacks--that includes non-forum members. I've already given one infraction for a personal attack on Steve Jobs.

Stay on topic and be civil. Thanks.

---

### Post by Sublime Porte on 2009-05-26
> In fact, few things annoy me more than when people try to present Linux as a cure-all for all computing problems and a drop-in replacement for Windows.

But Linux is an OS, and therefore is a replacement for Windows or OSX. You cannot deny this. To claim all OS's have their niche, and can co-exist nice and peacefully is just being detached from the reality. They _are_ competitors, they _do_ fill the same position. Is that so bad?

---

### Post by kk0sse54 on 2009-05-26
> **EDavidBurg said:**
> 
Apple pushes all of the changes it makes to FOSS software back to the community. This helps to improve BSD/GNU/wherever they got it from. Short of open sourcing their in-house code, how would you like them to contribute more back to the FOSS movement?


What code contributions have apple ever made to any BSD project particularly FreeBSD or NetBSD? What significant code contributions have they made really to any FOSS project?

---

### Post by schauerlich on 2009-05-26
> **aysiu said:**
> It was interpreted that way, because everything in the original post was in defense of Mac OS X. No bad points were mentioned at all. I consider that bias. It has nothing to do with convenience and everything to do with logic.

I never said OS X was heaven. I simply took many wrong things people seem to keep throwing out there and giving a more accurate explanation of the situation. The reason I used "sort of" or "not really" is because nothing is black and white.

---

### Post by Tibuda on 2009-05-26
> **mr.propre said:**
> Bad bad argument, I once saw an article about an "open source" OS X version, the only thing you had was a terminal screen. You aren't wrong, Apple is indeed partly open-source, but without the closed source it worthless. See it as a car where the engine is open-source but the rest is closed source. No end user will ever be happy with just the engine. Most people won't even call it a car.

Darwin without Cocoa/Aqua won't let you run OS X applications like Textmate, Photoshop. If you want a GUI, what can you install? X Server, Gnome, XFCE, KDE...

---

### Post by schauerlich on 2009-05-26
> **danielrmt said:**
> Darwin without Cocoa/Aqua won't let you run OS X applications like Textmate, Photoshop. If you want a GUI, what can you install? X Server, Gnome, XFCE, KDE...

Which is what PureDarwin is all about.

---

### Post by aysiu on 2009-05-26
> **Sublime Porte said:**
> But Linux is an OS, and therefore is a replacement for Windows or OSX. You cannot deny this. To claim all OS's have their niche, and can co-exist nice and peacefully is just being detached from the reality. They _are_ competitors, they _do_ fill the same position. Is that so bad? I didn't say Linux wasn't a competitor. I also don't deny that in some situations it can replace Windows or OS X. In fact, for me, Linux is a full-time replacement for Windows.

What I said is that it is not a *drop-in replacement* for Windows. That means it can serve generally the same functions as Windows, but if you expect it to operate exactly the way Windows does and to run all the same software as Windows does, then you will be sorely disappointed (especially if you use AutoCAD or have a Lexmark printer).

> **EDavidBurg said:**
> I never said OS X was heaven. I simply took many wrong things people seem to keep throwing out there and giving a more accurate explanation of the situation. The reason I used "sort of" or "not really" is because nothing is black and white. And I never said you said OS X was heaven. I simply said you showed bias in your post.

---

### Post by saulgoode on 2009-05-26
> **C!oud said:**
> What code contributions have apple ever made to any BSD project particularly FreeBSD or NetBSD? What significant code contributions have they made really to any FOSS project?
Apple does seem to be a good steward of [CUPS (Common Unix Printing System)]("http://www.cups.org/"); though a bit ironically, CUPS is licensed under the GPL and LGPL licenses.

---

### Post by Faolan84 on 2009-05-26
> **saulgoode said:**
> Apple does seem to be a good steward of [CUPS (Common Unix Printing System)]("http://www.cups.org/"); though a bit ironically, CUPS is licensed under the GPL and LGPL licenses.

I have to agree with that. I think Apple does a lot of good to push open source and open standards. This is coming from someone who isn't a fan of OSX and someone who isn't really a fan of their products for the most part. However they do create and contribute and have also created many open source products:

- KHTML / WebKit
- CUPS
- Darwin and Darwine

They also create their products in such a manner as to honor open standards such as proper XHTML+CSS rendering. They also have supported the OpenDocument to create a standard office file format.

---

### Post by schauerlich on 2009-05-26
I have just finished making significant changes to the OP. I focused on softening some of the language, trying to remove bias, and giving a better view of the opposing side. In addition, I've changed the Misconception/Truth layout to a more neutral Commonly Stated/More Accurate Description layout.


 Please reread the OP if you have not already done so, and let me know if my changes made this article more accurate.

---

### Post by jimi_hendrix on 2009-05-26
> **EDavidBurg said:**
> 


**Commonly stated: Mac OS X only runs on Apple Hardware.**
More accurate description: Well, sort of. True, its license states it can only be run on Apple hardware; However, options do exist to run OS X on non-Apple hardware, such as the excellent [OSx86]("http://en.wikipedia.org/wiki/OSx86") project. Similarly, [Psystar]("http://en.wikipedia.org/wiki/Psystar") and [PearC]("https://www.pearc.de/") offer prebuilt computers which 


about psystar

[http://yro.slashdot.org/article.pl?sid=09/05/26/1942250](http://yro.slashdot.org/article.pl?sid=09/05/26/1942250)

---

### Post by Sublime Porte on 2009-05-26
EDavidBurg,

> Which is what PureDarwin is all about.Tried running PureDarwin lately?? Apple don't even provide a binary distribution of it anymore, so unless you're good at compiling and assembling your own OS forget it. PureDarwin cannot run any of those desktop environments mentioned, you're lucky if you can get X11 to run on it at all, in a Virtual Machine.

Faolan Devyn,

> However they do create and contribute and have also created many open source products:

- KHTML / WebKitAre you kidding? Apple didn't create KHTML, KHTML is the rendering engine of KDE's Konqueror web browser. They borrowed it and renamed it Webkit. And even though they've contributed back to KHTML some of their work, it hasn't always been forthcoming:

> However, the exchange of code patches between the two branches of KHTML has previously been difficult and the code base diverged because both projects had different approaches in coding.[[5]]("http://en.wikipedia.org/wiki/Webkit#cite_note-4") One of the reasons for this is that Apple worked on their version of KHTML for a year before making their fork public.
At one point KHTML developers said they were unlikely to accept Apple's changes and claimed the relationship between the two groups was a "bitter failure".[[7]]("http://en.wikipedia.org/wiki/Webkit#cite_note-6") Apple submitted their changes in large patches that contained a great number of changes with inadequate documentation, often to do with future feature additions. Thus, these patches were difficult for the [KDE]("http://en.wikipedia.org/wiki/KDE") developers to integrate back into KHTML. Furthermore, Apple had demanded developers to sign nondisclosure agreements before looking at Apple's source code and even then they were unable to access Apple's bug database.[[8]]("http://en.wikipedia.org/wiki/Webkit#cite_note-7")([Wikipedia: Webkit]("http://en.wikipedia.org/wiki/Webkit"))

---

### Post by dmizer on 2009-05-26
> **EDavidBurg said:**
> I have just finished making significant changes to the OP. I focused on softening some of the language, trying to remove bias, and giving a better view of the opposing side. In addition, I've changed the Misconception/Truth layout to a more neutral Commonly Stated/More Accurate Description layout.


 Please reread the OP if you have not already done so, and let me know if my changes made this article more accurate.

Very nicely done revision.

---

### Post by schauerlich on 2009-05-26
> **Sublime Porte said:**
> Tried running PureDarwin lately?? Apple don't even provide a binary distribution of it anymore, so unless you're good at compiling and assembling your own OS forget it. PureDarwin cannot run any of those desktop environments mentioned, you're lucky if you can get X11 to run on it at all, in a Virtual Machine.

Darwin is not meant to be an every-day or even particularly useful Unix distribution *on its own*. It is simply a collection of open source components which serve as the base of Mac OS X. Apple is not in the FOSS Unix distribution market.

> **dmizer said:**
> Very nicely done revision.

Thanks. :)

---

### Post by p_quarles on 2009-05-26
> **EDavidBurg said:**
> Darwin is not meant to be an every-day or even particularly useful Unix distribution *on its own*. It is simply a collection of open source components which serve as the base of Mac OS X. Apple is not in the FOSS Unix distribution market.

You know, I think the fact that the above needs to be stated at all confirms another common misconception that I find distressing: open source does not mean, nor should it need to, free working binaries for all architectures. 

Seriously: whether or not the end user has any use for the Darwin source code or its builds is immaterial to whether or not it's open source. And all the high-minded rhetoric about open source is precisely about the source code, not the free binaries. 

I really do think people have a duty to understand these sorts of things if they want to consider themselves advocates. I don't have much of an opinion about OS X one way or the other, but I'm kind of astounded that this attempt at rebutting the usual group of knee-jerk slams against it is greeted as everything from "trolling" to evangelism. It seems pretty obvious to me that the intent was precisely to combat those things.

---

### Post by Sublime Porte on 2009-05-27
p_quarles,

I think what people were responding to was the fact that releasing Darwin's source is not that great a feat as it's touted to be. Sure they don't have to, but my feeling is they released it to try and get some sort of input from the open source community to help them incorporate more of the open source components.  Darwin was originally a promising project, but it seems it wasn't profitable/beneficial enough for Apple, so they pulled the rug out from under it.

---

### Post by zubin71 on 2009-05-27
Real nice effort here.... every OS has its boons and banes... 
being a linux addict has never stopped me from appreciating any of apples products...

Awesome post.

---

### Post by bryonak on 2009-05-27
@EDavidBurg: you have improved greatly!

The only significant blunder I still see is the sidekick remark about Stallman... I think it wouldn't go well with the Mac community if someone was to write a pro-Linux posting on one of their forums portraying Jobs in a similar picture. And you really don't need the inflammation.


> **EDavidBurg said:**
> I'm biased because I disagree with you...?
You know better ;)

> The crux of my argument is that the first four point releases were of much lower quality than the last two, and that one shouldn't be put off by their experiences of those releases and not like OS X because of it.

I wasn't critisizing your point at all, just the argumentational form (which is rhetorically weak). The point comes over well, no big deal here.


> **saulgoode said:**
> Apple does seem to be a good steward of [CUPS (Common Unix Printing System)]("http://www.cups.org/"); though a bit ironically, CUPS is licensed under the GPL and LGPL licenses.
CUPS was GPL'd before Apple bought it. One reason they kept it open was because it was heavily used by RedHat, who would have forked instantly if it were to get closed.

---

### Post by schauerlich on 2009-05-27
> **bryonak said:**
> @EDavidBurg: you have improved greatly!

The only significant blunder I still see is the sidekick remark about Stallman... I think it wouldn't go well with the Mac community if someone was to write a pro-Linux posting on one of their forums portraying Jobs in a similar picture. And you really don't need the inflammation.


I'm pretty sure everyone is slow in molasses. :)

---

### Post by dmizer on 2009-05-28
> **EDavidBurg said:**
> I'm pretty sure everyone is slow in molasses. :)

I giggled. I think it would be similar to going to a Mac forum and saying something like "Ubuntu gets more updates than Jobs has keynote fans." To which I expect (knowing) MAC users would giggle as well.

---

### Post by schauerlich on 2009-05-28
> **dmizer said:**
> I giggled. I think it would be similar to going to a MAC forum and saying something like "Ubuntu gets more updates than Jobs has keynote fans." To which I expect (knowing) MAC users would giggle as well.

/me cringes

It's Mac. MAC is [Media Access Control](http://en.wikipedia.org/wiki/Media_Access_Control) as in MAC address, or [the make-up store](http://en.wikipedia.org/wiki/Make-up_Art_Cosmetics). Maybe I should add that to my OP... :)

---

### Post by dmizer on 2009-05-28
> **EDavidBurg said:**
> /me cringes

It's Mac. MAC is [Media Access Control](http://en.wikipedia.org/wiki/Media_Access_Control) as in MAC address, or [the make-up store](http://en.wikipedia.org/wiki/Make-up_Art_Cosmetics). Maybe I should add that to my OP... :)

I am aware. It was habit. I've corrected that ... sorry.

---

### Post by schauerlich on 2009-05-28
> **dmizer said:**
> I am aware. It was habit. I've corrected that ... sorry.

Another thing that bugs me is when people say they're going to "The Mac Store," especially because in our mall, MAC and the Apple Store are right across from each other. But then again, I'm just a picky grammar nazi. :)

---

### Post by Sunnz on 2009-05-28
What I hate about Apple is its lack of transparency when it comes to fixing bugs. Any rational Mac user knows that any complicated piece of code is going to have some bugs and OS X is no exception. For example sometime in 2008 the MacPro had serious issues and Mac users all over the web had reported such problem and gave feedback to Apple.

Apple did fix the problem later in 2008, which is good news for MacPro users, whom are not necessarily just random internet fanboy trying to be cool and all that, but largely consist of professional whose business dependent on the well being of the machine!! This fix means a lot to them.

Anyway, when Apple finally released the fix, it actually worked, but they had the standard ambiguous description: "this update fixes a number of bugs". Nobody actually knows if it does address the issue, it is a hit and miss, people are just left essentially uninformed as usual.

Now I use a Mac myself and I enjoy using OS X, and I understand the way Apple do things, they typically don't announce new things till they are ready, and their marketing strategy is to portray OS X as this perfect miracle to Windows PC users... but it is important to be responsible to exiting user-base as well, which consist of mostly loyal customers.

It is even worse when it comes to security, it may have a good Unix foundation and had good design decision as not to repeat mistakes Windows had; but that's all they had, "better than Windows", which isn't very amazing when considering every other serious OS had better security than Windows anyway... very talented people had reported security problems and possible fixes to Apple over and over again, but it is indeed a hit and miss problem, there are some problems that's very trivial to fix, but Apple just doesn't care enough to even say that they won't fix it, such bug reports are just ignored - often people would report a bug just to be told by other people that this had been reported 5 years ago and there never heard anything from Apple.

You got to wonder how well OS X does when it comes to being as secure as their ad says - there is an interesting exploit called the "blue pill" on newer x86_64 hardware, which Vista had taken into consideration since it beta stage, but what about OS X? No one knows, it is probably not considered by Apple as most users don't know much about computer security that Apple cannot invest in something that doesn't pull a publicity stunt for them.

Alright that's enough of me ranting about OS X, as I said I actually enjoy using OS X and I actually posted this on an Unibody MacBook; but there are approaches that I think Apple isn't doing right, and I guess these are from a Mac user point of view rather than "common misconceptions" from people who doesn't know that much about Macs; but I hope that these are misconception as well that someone may be able to shred the light about what are the actual fact and what's going on with Apple and OS X.

---

### Post by jimi_hendrix on 2009-05-28
> **Sunnz said:**
> 

their marketing strategy is to portray OS X as this perfect miracle to Windows PC users... but it is important to be responsible to exiting user-base as well, which consist of mostly loyal customers.

It is even worse when it comes to security, it may have a good Unix foundation and had good design decision as not to repeat mistakes Windows had; but that's all they had, "better than Windows", which isn't very amazing when considering every other serious OS had better security than Windows anyway... very talented people had reported security problems and possible fixes to Apple over and over again, but it is indeed a hit and miss problem, there are some problems that's very trivial to fix, but Apple just doesn't care enough to even say that they won't fix it, such bug reports are just ignored - often people would report a bug just to be told by other people that this had been reported 5 years ago and there never heard anything from Apple.

You got to wonder how well OS X does when it comes to being as secure as their ad says - there is an interesting exploit called the "blue pill" on newer x86_64 hardware, which Vista had taken into consideration since it beta stage, but what about OS X? No one knows, it is probably not considered by Apple as most users don't know much about computer security that Apple cannot invest in something that doesn't pull a publicity stunt for them.

This is what I hate about Macs.  They say they are better than windows, and they maybe, but not by much.  I always feel like 90% of OS X users really want linux but dont know it

---

### Post by schauerlich on 2009-05-28
> **jimi_hendrix said:**
> I always feel like 90% of OS X users really want linux but dont know it

That might be true if most OS X users were looking for Unix... but most OS X users don't even know what Unix is other than that their OS has it and that makes it better somehow.

---

### Post by cprofitt on 2009-05-28
> **scaredpoet said:**
> 
Not Windows; you must pay for it.

Actually -- The development environment is free with Windows as well. You can get [several development environments]("http://www.microsoft.com/express/default.aspx") at no cost for Windows. The ones I linked too are just the Microsoft ones... there are others.

---

### Post by Sunnz on 2009-05-29
> **EDavidBurg said:**
> That might be true if most OS X users were looking for Unix... but most OS X users don't even know what Unix is other than that their OS has it and that makes it better somehow.

Most Mac user will go back to Windows if OS X cease to exist. They could have a Ubuntu CD and would still use Windows full time. It just happens that OS X have a Unix base that some geeks can use it to its fullest.

---

### Post by Chame_Wizard on 2009-05-29
> **EDavidBurg said:**
> Within the greater Linux community, and on these forums in particular, I have noticed a great deal of misinformation with respect to Mac OS X and Apple's contributions to the Unix community. I'd like to address these topics FAQ-style post. This is by no means a comprehensive list of issues, and I plan on adding to this post in the future. Feel free to suggest topics and I'll address them as I have time.

[b][color=purple]This thread concerns Mac OS X, the operating system. It it not for debating the price of Apple hardware, Apple's business tactics, or the color purple. Thank you.[/color]

[color=green]I have made significant changes since I first posted this. Please reread it if you have not already done so, and let me know if my changes made this article more accurate.[/color][/b]


**Commonly stated: Mac OS X only runs on Apple Hardware.**
More accurate description: Well, sort of. True, its license states it can only be run on Apple hardware; However, options do exist to run OS X on non-Apple hardware, such as the excellent [OSx86](http://en.wikipedia.org/wiki/OSx86) project. Similarly, [Psystar](http://en.wikipedia.org/wiki/Psystar) and [PearC](https://www.pearc.de/) offer prebuilt computers which come with OS X preinstalled. It's not that OS X **doesn't** run on non-Apple hardware, it's just not Apple-sanctioned to do so. Currently whether this is legal is up for debate. Psystar is in the middle of a suit with Apple over the legitimacy of certain pertinent sections the Apple EULA. However, it is true that Mac OS X does not run *out of the box* on non-Apple hardware, and you have to enter legally murky waters to get there. Depending on your perspective, this may count as running on non-Apple hardware or not. It is not like NetBSD where it is open and ready to be installed on anything. It's more like getting Linux to run on a wrist watch. You can get there, but it takes some finangling. And also, Swatch might sue you for licensing violations. Details...




**CS: Mac OS X is closed source.**
MAD: Parts of it are, parts of it aren't. Much of the core of OS X is [fully open source](http://www.apple.com/opensource/). Apple maintains a Unix distribution known as [Darwin](http://developer.apple.com/referencelibrary/Darwin/), which serves as the base for each release of OS X. Until recently, Darwin was distributed in binary form and available on Apple's website to download. Currently you can download Darwin's source in full [here](http://www.opensource.apple.com/). _Apple has never intended Darwin to be a distribution for every day use_; however, a community effort called [PureDarwin](http://www.puredarwin.org/) has sprung up to make it more usable. _Mac OS X is proprietary, there is no doubt about it_. However, proprietary does not necessarily mean that it does not contain open source components which are released for modification and redistribution.




**CS: Apple is evil/ripped off BSD/GNU/FOSS advocates/kills babies.**
MAD: Apple has released all of the open source code it's integrated into Darwin/OS X back to the community. See [Apple's Open Source page](http://www.apple.com/opensource/) for more details. While Apple has not released the more "important parts" of the OS (to the end user) such as Cocoa or Aqua, it has released all of the code it used from open source projects back to the community.




**CS: Mac OS X is "just" BSD with a shiny exterior.**
MAD: Apple has incorporated a good amount of BSD code into Darwin. No one disputes the valuable contributions made to the Unix community at large and indirectly to Apple by the BSD community. However, to say that Mac OS X is simply BSD with a shiny exterior is misleading at best. OS X's kernel, [XNU](http://en.wikipedia.org/wiki/XNU), is a hybrid kernel incorporating the [Mach Kernel](http://en.wikipedia.org/wiki/Mach_kernel), components from 4.3BSD, and [I/O Kit](http://en.wikipedia.org/wiki/I/O_Kit). 

What really makes Mac OS X unique are its Core services: [Core OpenGL](http://en.wikipedia.org/wiki/Core_OpenGL), [Core Image](http://en.wikipedia.org/wiki/Core_Image), [Core Video](http://en.wikipedia.org/wiki/Core_Video), and [Core Animation](http://en.wikipedia.org/wiki/Core_Animation), to name but a few. These frameworks provide a solid foundation upon which applications may be developed, and provide access to key components of the Darwin system lying beneath. 

The most visible contribution Apple has made to OS X is the [Cocoa API](http://en.wikipedia.org/wiki/Cocoa_(API)). Written in Objective-C, Cocoa was based off of the [OpenStep API](http://en.wikipedia.org/wiki/OpenStep) developed for NeXTSTEP. Cocoa provides developers a common palette to give their applications access to many key Core services, and help to standardize the interface across applications. A FOSS implementation of the OpenStep API exists, named [GNUstep](http://en.wikipedia.org/wiki/Gnustep).

See [here](http://developer.apple.com/macosx/architecture/index.html) for more information about Mac OS X's architecture.




**CS: Mac OS X is bloated and slow.**
MAD: This is largely subjective. Sure, if you're installing Leopard on an original iMac, it's going to go slower than RMS in a pool of molasses.  I run Leopard on a MacBook2,1 and find it runs quite smoothly. Like with ANY operating system, your mileage may vary.




**CS: Mac OS X caters to grandmas and creative types, not power users.**
MAD: While Apple does do its best to make its software simple and easy to use, and provides great multimedia applications, OS X is by no means limited to bearded twentysomethings and their grandmothers. Apple provides the [Xcode](http://en.wikipedia.org/wiki/Xcode) development suite with every installation of OS X to encourage development on their platform. A fully POSIX compliant environment is provided, making it easy to port applications originally written for other Unix distributions. 

In addition, the great community of developers has made several utilities which simplify daily tasks and center navigation on the keyboard, the most famous example of which is [QuickSilver](http://en.wikipedia.org/wiki/Quicksilver_(software)). This excellent tool is what Gnome Do is based on, and it makes it easy to get around with just the keyboard. 

It is true that Aqua is not very customizable as far as interfaces go. In the end, it comes down to decision made by Apple that you may or may not agree with: to sacrifice customizability for consistency. Third party applications and Library hacks have made Mac OS X a little more flexible, and often times editing a plist will reveal a bundle of hidden options (a la the gconf editor in GNOME). However, this customizability pales in comparison to that of Linux. For some, this may not be a big deal. For others, it may be a deal breaker. In the end, it's a matter of preference. Choose what makes you feel comfortable.




**CS: Mac OS X isn't REAL Unix.**
MAD: With Leopard, Mac OS X has been [SUSv3](http://en.wikipedia.org/wiki/SUSv3) certified, and is an Open Brand UNIX 03 registered product (when run on Intel processors). Whether this qualifies as a "real" Unix depends on what you mean by "real" Unix. If you mean like Linux, then it means very little. If you mean that it fits the Open Group's standards for using the Unix trademark, then it qualifies. 




**CS: "Mac OS X 10.0/10.1/10.2/10.3 was a nightmare, I'll never touch OS X again."**
MAD: 10.0-10.3 are quite different from the last two point releases. Apple was struggling to stay afloat when Steve Jobs returned to Apple in 1997, and Apple was stuck using an outdated and slow OS on their computers. After [attempts to modernize the OS](http://en.wikipedia.org/wiki/Copland_(operating_system)) failed, Apple decided to abandon the OS 9 platform and move to a completely new OS. When Mac OS X 10.0 was released in 2000, it was buggy, slow, feature-poor and pinstripe-rich. It was Apple's effort to put *something* out to keep their business going. Once Apple had [a reliable source of income](http://en.wikipedia.org/wiki/Ipod), it was able to put more time and money into developing OS X into what it should have been. This goal (in my mind) was realized in 10.4, and further refined in 10.5. The last two point releases of OS X are radically different from the first four. If you tried any of the earlier versions and were put off by it, I strongly encourage you to plop down in a chair at your local Apple store and check Mac OS X for 15 minutes or so. You might find your opinion of it has changed. Or, you might not.




**CS: Mac OS X doesn't have any good free (libre or beer) software available.**
MAD: [MacPorts](http://en.wikipedia.org/wiki/Macports) and [Fink](http://en.wikipedia.org/wiki/Fink) are two efforts to port Linux/BSD apps to OS X, and make them accessible through repositories. Lots of great software is available through these avenues, and Apple even has an implementation of X11 for GUI applications. X11 support isn't great, and I prefer to wait for apps to be ported to Aqua, but if you're in a pinch and need to use something, it will do. In addition, sites such as [MacUpdate](http://www.macupdate.com/) are great for finding OS X freeware. For a given functionality found in a shareware application, there's almost always an equivalent functionality in a free application. I've never run into any trouble finding software to do what I need on Mac OS X.




**CS: The Mac OS X command line is incomplete/different from Linux/not as good as Linux's.**
MAD: It is true that Apple does not put as much effort into refining the command line as it does to the GUI. However, complete access is given to the command line through Terminal.app. Terminal runs GNU bash by default, and a whole host of command line goodies are provided either by default or are easily obtainable through MacPorts/Fink. Apple provides command line versions of many of their GUI Apps, such as Disk Utility (diskutil), Software Update (softwareupdate), Universal Access speech synthesizer (say), and so on. 

Linux has a very powerful command line. Most problems that can be fixed from the GUI can be fixed even quicker from the command line. This isn't always going to be the case on Mac OS X. Perhaps this is a case of differing audiences: most OS X users don't want to see the terminal, whereas many Linux users expect it. Whatever the reason, the Mac OS X terminal may not be all you expect it to be when switching from Linux. However, Mac OS X is POSIX compliant and has a wealth of command line tools ported from Linux/BSD available. 




That's it for now. Feel free to suggest topics or call me out on inaccurate statements I may have made.

I love it+1.:lolflag:

---

### Post by Sunnz on 2009-05-29
Apple has an interesting "idea policy": [http://www.apple.com/legal/policies/ideas.html](http://www.apple.com/legal/policies/ideas.html)

How would look at it from an open source perspective?

---

### Post by jimi_hendrix on 2009-05-29
> **EDavidBurg said:**
> That might be true if most OS X users were looking for Unix... but most OS X users don't even know what Unix is other than that their OS has it and that makes it better somehow.

lets put aside the unix point

i dont really see anything on a mac that you cant get an equivalent program on linux for besides games and video editing software.  Not having ever owned a mac, what draws people to them?  if  its because they look nice and they claim they are easy to use (in my experience, no less so than windows) and virus free, then i dont see how they are worth the extra money that it would cost to get a mac vs a pc + ubuntu.  i am not a mac hater, i just dont get the hype

also, with the secure part, if i recall there was a major exploit where someone from the outside can hack into a mac and watch you via your webcam

like all OS's, they come with their bugs and Macs arnt perfect

---

### Post by unknownPoster on 2009-05-29
> **jimi_hendrix said:**
> lets put aside the unix point

i dont really see anything on a mac that you cant get an equivalent program on linux for besides games and video editing software.  Not having ever owned a mac, what draws people to them?  if  its because they look nice and they claim they are easy to use (in my experience, no less so than windows) and virus free, then i dont see how they are worth the extra money that it would cost to get a mac vs a pc + ubuntu.  i am not a mac hater, i justrfect dont get the hype



I think part of it is the fact that you are %100 guaranteed that your hardware will be fully compliant/compatible with your OS with a mac.

Even Windows has a few iffy points in hardware support. And we all know how linux is about it.

Also, the last time that I checked, in order to develop applications for the iPhone you must use a Mac. Granted, this is a small demographic, but it is relevant nonetheless.

I could probably keep going with this...

---

### Post by bashveank on 2009-05-30
> **jimi_hendrix said:**
> lets put aside the unix point

i dont really see anything on a mac that you cant get an equivalent program on linux for besides games and video editing software.  Not having ever owned a mac, what draws people to them?  if  its because they look nice and they claim they are easy to use (in my experience, no less so than windows) and virus free, then i dont see how they are worth the extra money that it would cost to get a mac vs a pc + ubuntu.  i am not a mac hater, i just dont get the hype

also, with the secure part, if i recall there was a major exploit where someone from the outside can hack into a mac and watch you via your webcam

like all OS's, they come with their bugs and Macs arnt perfect

Games and video editing are huge.
But as someone who is only a moderate gamer and a hobbyist videographer, I use OS X because its faster, more stable, and way more polished than Linux, not to mention the booming, high quality, third party app market.
As a graphic design student, I use OS X because the font rendering is top notch, and CS3 runs on it perfectly.
Also, I would probably strangle myself if I had to use an ugly and utilitarian Dell or Lenovo or HP or something.
And finally, Apple tech support is top notch.


> **jimi_hendrix said:**
> This is what I hate about Macs.  They say they are better than windows, and they maybe, but not by much.  I always feel like 90% of OS X users really want linux but dont know it

The uninformed majority doesn't care what they use, they're generally better off using what their geeky friend uses so he can support them, but the gurus on Linux, OS X, or Windows have very valid reasons for keeping their OS.

---

### Post by Swarms on 2009-05-30
> **Faolan Devyn Aodfin said:**
> I have to agree with that. I think Apple does a lot of good to push open source and open standards. This is coming from someone who isn't a fan of OSX and someone who isn't really a fan of their products for the most part. However they do create and contribute and have also created many open source products:

- KHTML / WebKit
- CUPS
- Darwin and Darwine

They also create their products in such a manner as to honor open standards such as proper XHTML+CSS rendering. They also have supported the OpenDocument to create a standard office file format.

I also believe that Safari (though I would never use it) through competition; have helped Firefox stay on their toes, keeping up the development pace.
Just like Firefox forced Microsoft to start doing something about IE. (Bringing better security for the general public).

---

### Post by bashveank on 2009-06-01
> **Swarms said:**
> I also believe that Safari (though I would never use it) through competition; have helped Firefox stay on their toes, keeping up the development pace.
Just like Firefox forced Microsoft to start doing something about IE. (Bringing better security for the general public).

Just curious, why don't you use Safari? I've always considered it one of the best browsers available, but I know that some people disagree, I just don't get why.

---

### Post by zerothis on 2009-06-18
What follows is mostly a suggestion of topics.

> **EDavidBurg said:**
> 
**Commonly stated: Mac OS X only runs on Apple Hardware.**
More accurate description: Well, sort of. True, its license states it can only be run on Apple hardware; *snip*
A very good point. To many people equate violating an EULA to violating a law. Think about it. Any company or individual can write an EULA and restrict the user however they want. Can any company or individual write a law then? If so, so much for democracy then, since we don't need representatives to pass it, an executive government to enforce it, or a judicial system to keep an eye on it. As a matter of fact, all governments become pointless if someone can just create their own law at whim and legally enforce them. An EULA is not a law. It is a type of contract. Its not actually a contract either, contract is too generous of a word. In legal terms, and EULA is an adhesion contract. Which most legal systems agree, is very problematic when it comes to enforcing it (look it up). First, contracts are negotiable *before* the parties agree to it. Every tried calling a company and negotiating to make a change in their EULA that you both can agree on? Their policy is take it or leave it. Also, certain conditions allow for any contract to be renegotiated after the contract is agreed too. This is not done with EULAs. Finally, a contract can be declared null and void under certain conditions. Especially if it violates someone's rights. Note the EULA of GlovePIE [url]http://carl.kenner.googlepages.com/glovepie[url] says it cannot be downloaded in Israel until certain condition are changed in the country. It also says it cannot be used by missionaries. If such clauses were included in a real contract, it would be declared null and void, the writers could bet liable for financial penalties, they even be sentenced to prison term. This won't happen over a EULA, because the law does not take adhesion contract that seriously. EULA's violate people's rights and there isn't a thing either party in an can do about it. Most importantly, all parties in a contract have responsibilities. Have you ever tried to make a company fulfill the responsibilities they include in their own EULA? You cannot legally make them do it. For instance, most PC vendors that sell Windows are under EULA obligation to provide a full and unmodified copy of Windows suitable for use on any computer system. But they don't. They provide customized version that may not even run on the computer they provide if certain custom conditions are not met. Call them and see if they will fulfill this obligation. Of course, their's something to be said for honesty. It is inherently dishonest to agree to an EULA (by clicking or unwrapping, etc.) then violate it. Fortunately, FLOSS provides a sane alternative and insane EULA's can be avoided in all situations. Which brings up a very, very, very important point. FLOSS is entirely dependent on copyright and the enforceability of the GPL, which is *GASP* an adhesion contract. So when you talk about violating EULA's you are indirectly attacking FLOSS buy weakening the thin thread on which EULA's hang (including the GPL). I believe that someday that the law will be modified so that there will be no need for EULA's to protect freedoms. But until then, EULA's are necessary and should not be attacked.

> **EDavidBurg said:**
> **CS: Mac OS X is closed source.**
Partially libre, parts of it are closed source, hmmm. 'You can have all the freedom of Open Source and long as you do it behind the bars of our EULA.' Well, Windows is partially libre too. [http://sourceforge.net/projects/wix/](http://sourceforge.net/projects/wix/). I have no objections to Darwin. Occasionally I have attempted to install and use it. But OS X is not Darwin. The fact is, I cannot acquire any OS X application and run in on Darwin. Granted, I can modify a FLOSS application to run on Darwin, had I the skills. I'd like to do everything practical to encourage more FLOSS apps for Darwin, including buying copies of applications. Keep me posted. In the meantime, OS X is not Darwin, is not fully open source, and is not libre. Since you are dispelling myths, I have met many Mac users that are convinced that OS X and everything that comes from Apple is full Open Source. Thanks for point out this error.

> **EDavidBurg said:**
> **CS: Apple is evil/ripped off BSD/GNU/FOSS advocates/kills babies.**
In a FLOSS world, 'rip-offs' are to be encouraged for the improvements they can bring. I commend Apple for their efforts. But bear in mind even GPL'd sharks with laser beams can benefit everyone. Its good that you've pointed out that Apple is obligated under FLOSS agreements to give back to the community. The list at the link you provided is pretty impressive for a company so dedicated to proprietary software. But they have their foot in both worlds. As such, it leaves me skeptical they are zealous about fulfilling their FLOSS obligations. I'd prefer to have an independent review to insure Apple is complaint with FLOSS. If you know of any such review, please tell us. He he, its nice to know they only release *unimportant* parts of their code to improve their software and help their neighbor.


> **EDavidBurg said:**
> **CS: Mac OS X is "just" BSD with a shiny exterior.**
Good point. Compiz is just Linux with a shiny exterior:) That's no reason to diminish Linux or BSD. Its important to know that the Mac OS X is no BSD, Mach, UNIX, or even Linux as some yahoos content. It is merely based on those things to one degree or another.

> **EDavidBurg said:**
> **CS: Mac OS X is bloated and slow.**MAD: This is largely subjective.
Agree, after subjective observation, Mac OS X is bloated and slow.

> **EDavidBurg said:**
> **CS: Mac OS X caters to grandmas and creative types, not power users.**
Can't fault OS X for being simple and accessible to many users. And they do in fact have tools for power users. But, it is simpler to be a power user on any other system but OS X. For example, I wanted to connect my WiiMote to my computers for whiteboard presentations, Impress presentations, range finding, a precision level for home improvement projects, easy remote control of my system including mouse movement, and games. I opened synaptic in Linux. Searched for Wii. Installed everything from the results. Read some docs. Made some scripts. It took about 9 hours of effort to accomplish everything I had set out to do. Some of the things I'd done for my system could benefit a local organization I provide occasional help to. They are Mac zealots, so I agreed to do these things on their iMac. 3 months later (an estimated 24 hours of effort). I have remote control working but not in a way simple enough for them. Cursor movement is intermittent due to a problem I cannot track down. No other of the tasks have been accomplished. I have encountered this over and over. Doing strange and powerful things in Linux is simple where doing the same on Mac is seemingly impossible. Meeting the requirements of a fully POSIX environment is not all that impressive. If this minimum standard was maintained in Linux, it would suck just as bad. When my boss was still forcing me to use WindowsXP, I installed a fully POSIX environment and bash. It helped take the edge of XP's suckage but didn't make it and ideal power user environment. So since, XP can be made fully POSIX compliant, does that make it as good as OS X for power users? You won't find me bashing Quicksilver, its nice. But its rather pointless to tell Linux and Windows users about it. Mac users are the ones that need to be told. None of the Mac users I know will use it. The mouse *everything*. I've seen them clicking an on-screen keyboard to type paragraphs! As for customizing the desktop, Linux not only lets me choose what I am comfortable with, it lets me choose what's most efficient for me.


> **EDavidBurg said:**
> **CS: Mac OS X isn't REAL Unix.**
Agreed, UNIX is not all that great. At least for the average user.

> **EDavidBurg said:**
> **CS: "Mac OS X 10.0/10.1/10.2/10.3 was a nightmare, I'll never touch OS X again."**
Strange, IMO, they keep getting worse. And I haven't just sat down with them. In the course of my job I'm required to use them. Aren't all these difficulties/excuses supposedly avoided by the advantages of proprietary software?

> **EDavidBurg said:**
> **CS: Mac OS X doesn't have any good free (libre or beer) software available.**
And Windows has libre stuff also. Good that you point this out.


> **EDavidBurg said:**
> **CS: The Mac OS X command line is incomplete/different from Linux/not as good as Linux's.**
I have only found the OS X terminal useful by compiling and installing Linux apps for it. This feels like a waste of time since most of it is so much easier to install, compile, or is already present on Linux systems. I do have to compliment OS X for being much less hostile to the process of compiling from source. But its still not as easy as in Linux. Most problems shouldn't need to be fixed from GUI or CLI, they shouldn't happen. That said, GUI is slow and inefficient for tracking down a problem. If you don't want to see a Terminal, don't get a computer. Get a TV, and/or a Wii, or a radio, or a coloring book. Computers are technical. Even OS X is technical.



> **EDavidBurg said:**
> What follows is mostly a suggestion of topics.

[QUOTE=EDavidBurg;7347446]
**Commonly stated: Mac OS X only runs on Apple Hardware.**
More accurate description: Well, sort of. True, its license states it can only be run on Apple hardware; *snip*
A very good point. To many people equate violating an EULA to violating a law. Think about it. Any company or individual can write an EULA and restrict the user however they want. Can any company or individual write a law then? If so, so much for democracy then, since we don't need representatives to pass it, an executive government to enforce it, or a judicial system to keep an eye on it. As a matter of fact, all governments become pointless if someone can just create their own laws at whim and legally enforce them. An EULA is not a law. It is a type of contract. Its not actually a contract either, contract is too generous of a word. In legal terms, and EULA is an adhesion contract. Which most legal systems agree, is very problematic when it comes to enforcing it (look it up). First, contracts are negotiable *before* the parties agree to it. Ever tried calling a company and negotiating to make a change in their EULA that you both can agree on? Their policy is take it or leave it. Also, certain conditions allow for any contract to be renegotiated after the contract is agreed too. This is not done with EULAs. Finally, a contract can be declared null and void under certain conditions. Especially if it violates someone's rights. Note the EULA of GlovePIE [url]http://carl.kenner.googlepages.com/glovepie[url] says it cannot be downloaded in Israel until certain condition are changed in the country. It also says it cannot be used by missionaries. If such clauses were included in a real contract, it would be declared null and void, the writers could be liable for financial penalties, they might even be sentenced to a prison term. This won't happen over a EULA, because the law does not take adhesion contracts that seriously. EULA's can violate people's rights and there is very little either party in an can do about it. Most importantly, all parties in a contract have responsibilities. Have you ever tried to make a company fulfill the responsibilities they include in their own EULA? You cannot legally make them do it. For instance, most PC vendors that sell Windows are under EULA obligation to provide a full and unmodified copy of Windows suitable for use on any computer system. But they don't. They provide customized version that may not even run on the computer they provide if certain custom conditions are not met. Call them and see if they will fulfill this obligation. Of course, their's something to be said for honesty. It is inherently dishonest to agree to an EULA (by clicking or unwrapping, etc.) then violate it. Fortunately, FLOSS provides a sane alternative and insane EULA's can be avoided in all situations. Which brings up a very, very, very important point. FLOSS is entirely dependent on copyright and the enforceability of the GPL, which is *GASP* an adhesion contract. So when you talk about violating EULA's you are indirectly attacking FLOSS buy weakening the thin thread on which EULA's hang (including the GPL). I believe that someday that the law will be modified so that there will be no need for EULA's to protect freedoms. But until then, EULA's are necessary and should not be attacked.

> **EDavidBurg said:**
> **CS: Mac OS X is closed source.**
Partially libre, parts of it are closed source, hmmm. 'You can have all the freedom of Open Source and long as you do it behind the bars of our EULA.' Well, Windows is partially libre too. [http://sourceforge.net/projects/wix/](http://sourceforge.net/projects/wix/). I have no objections to Darwin. Occasionally I have attempted to install and use it. But OS X is not Darwin OS. The fact is, I cannot acquire any OS X application and run in on Darwin. Granted, I can modify a FLOSS application to run on Darwin, had I the skills. I'd like to do everything practical to encourage more FLOSS apps for Darwin, including buying copies of applications. Keep me posted. In the meantime, OS X is not Darwin, is not fully open source, and is not libre.

> **EDavidBurg said:**
> **CS: Apple is evil/ripped off BSD/GNU/FOSS advocates/kills babies.**
In a FLOSS world, 'rip-offs' are to be encouraged for the improvements they can bring. I commend Apple for their efforts. But bear in mind even GPL'd sharks with laser beams can benefit everyone. Its good that you've pointed out that Apple is obligated under FLOSS agreements to give back to the community. The list at the link you provided is pretty impressive for a company so dedicated to proprietary software. But they have their foot in both worlds. As such, it leaves me skeptical they are zealous about fulfilling their FLOSS obligations. I'd prefer to have an independent review to insure Apple is complaint with FLOSS. If you know of any such review, please tell us. He he, its nice to know they only release *unimportant* parts of their code to improve their software and help their neighbor.


> **EDavidBurg said:**
> **CS: Mac OS X is "just" BSD with a shiny exterior.**
Good point. Compiz is just Linux with a shiny exterior:) That's no reason to diminish Linux or BSD. Its important to know that the Mac OS X is no BSD, Mach, UNIX, or even Linux as some yahoos content. It is merely based on those things to one degree or another.

> **EDavidBurg said:**
> **CS: Mac OS X is bloated and slow.**MAD: This is largely subjective.
Agree, after subjective observation, Mac OS X is bloated and slow.

> **EDavidBurg said:**
> **CS: Mac OS X caters to grandmas and creative types, not power users.**
Can't fault OS X for being simple and accessible to many users. And they do in fact have tools for power users. But, it is simpler to be a power user on any other system but OS X. For example, I wanted to connect my WiiMote to my computers for whiteboard presentations, Impress presentations, range finding, a precision level for home improvement projects, easy remote control of my system including mouse movement, and games. I opened synaptic in Linux. Searched for Wii. Installed everything from the results. Read some docs. Made some scripts. It took about 9 hours of effort to accomplish everything I had set out to do. Some of the things I'd done for my system could benefit a local organization I provide occasional help to. They are Mac zealots, so I agreed to do these things on their iMac. 3 months later (an estimated 24 hours of effort). I have remote control working but not in a way simple enough for them. Cursor movement is intermittent due to a problem I cannot track down. No other of the tasks have been accomplished. I have encountered this over and over. Doing strange and powerful things in Linux is simple where doing the same on Mac is seemingly impossible. Meeting the requirements of a fully POSIX environment is not all that impressive. If this minimum standard was maintained in Linux, it would suck just as bad. When my boss was still forcing me to use WindowsXP, I installed a fully POSIX environment and bash. It helped take the edge of XP's suckage but didn't make it and ideal power user environment. So since, XP can be made fully POSIX compliant, does that make it as good as OS X for power users? You won't find me bashing Quicksilver, its nice. But its rather pointless to tell Linux and Windows users about it. MAc users are the ones that need to be told. None of the Mac user I know will use it. The mouse *everything*. I've seen them clicking an on-screen keyboard to type paragraphs! As for customizing the desktop, Linux not only lets me choose what I am comfortable with, it lets me choose what's most efficient for me.


> **EDavidBurg said:**
> **CS: Mac OS X isn't REAL Unix.**
Agreed, UNIX is not all that great.

> **EDavidBurg said:**
> **CS: "Mac OS X 10.0/10.1/10.2/10.3 was a nightmare, I'll never touch OS X again."**
Strange, IMO, they keep getting worse. And I haven't just sat down with them. In the course of my job I'm required to use them. Aren't all these difficulties/excuses supposedly avoided by the advantages of proprietary software?

> **EDavidBurg said:**
> **CS: Mac OS X doesn't have any good free (libre or beer) software available.**
And Windows has libre stuff also. Good that you point this out.


> **EDavidBurg said:**
> **CS: The Mac OS X command line is incomplete/different from Linux/not as good as Linux's.**
I have only found the OS X terminal useful by compiling and installing Linux apps for it. This feels like a waste of time since most of it is so much easier to install, or all ready present on Linux systems. Most problems shouldn't need to be fixed from GUI or CLI, they shouldn't happen. That said, GUI is slow and inefficient for tracking down a problem. If you don't want to see a Terminal, don't get a computer. Get a TV, and/or a Wii, or a radio, or a coloring book. Computers are technical. Even OS X is technical.


Keep of the good work.

---

### Post by starcannon on 2009-06-19
In my view Apple is the next MS on the block.
[http://www.theregister.co.uk/2009/06/17/w3c_apple_prior_art/](http://www.theregister.co.uk/2009/06/17/w3c_apple_prior_art/)

With this sort of behaviour, for me its all to clear where Apple is going, and how they intend to get there, as a company.

Here's the patent:
[http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO1&Sect2=HITOFF&d=PALL&p=1&u=%2Fnetahtml%2FPTO%2Fsrchnum.htm&r=1&f=G&l=50&s1=5764992.PN.&OS=PN/5764992&RS=PN/5764992](http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO1&Sect2=HITOFF&d=PALL&p=1&u=%2Fnetahtml%2FPTO%2Fsrchnum.htm&r=1&f=G&l=50&s1=5764992.PN.&OS=PN/5764992&RS=PN/5764992)

I should start patenting every obvious notion that comes to mind, I could make a million dollars.

---

### Post by Sublime Porte on 2009-06-19
> In my view Apple is the next MS on the block.

Next??? They were the FIRST!!!! They were more Microsoft, before even Microsoft revealed themselves to be Microsoft! In fact they probably taught Microsoft how to be Microsoft in the first place.

[Apple vs. Microsoft](http://en.wikipedia.org/wiki/Apple_Computer,_Inc._v._Microsoft_Corporation)

---

### Post by Frak on 2009-06-27
I think a handy tidbit of information to add would be:

> Mac OS Forge is a community project **started and maintained by Apple** that helps develop the FOSS components of Mac OS X.

So if you say Apple really wants to "KILL TEH OPEN SAUCE", just look at their track record of Open Source commitments.

---

### Post by zerothis on 2009-06-28
> **Sublime Porte said:**
> They were more Microsoft, before even Microsoft revealed themselves to be Microsoft! In fact they probably taught Microsoft how to be Microsoft in the first place.
I doubt they taught Microsoft. more like a Microsoft employee disguised himself as a student, taped the lessens, then made a fortune selling the tapes.


Ofcourse Apple doesn't want to > KILL TEH OPEN SAUCE
That would be like killing the golden goose. I'm concerned they want to feed it cheep food laced with sawdust, keep it penned in a 10cm by 10cm but 10cm cage, and inject it with whatever hormones will increase egg production.

> Fsck is available, Pico is available, Grep is available, Mount is available.
Strange, all these things I find more efficient (as in usability) to do from GUI. Except mount, that's pretty much handled automatically these days. But, if I am on a system with 64MB RAM then those things are great. I don't think I can go to the Mac store and get a Mac with 64MB of memory.

> I use irssi, wget, and a bunch of other "linux" programs on OS X. I have no idea where you got the notion that the Mac OS X command line is "incomplete."
I've use "Linux" programs on WindowsXP. I guess if you add enough "Linux" programs, then any CLI becomes complete.

---

### Post by Sublime Porte on 2009-06-28
> I doubt they taught Microsoft. more like a Microsoft employee disguised himself as a student, taped the lessens, then made a fortune selling the tapes.

Read the wiki article, and check out the movie "Pirates of Silicon Valley", it might not be 100% accurate, but it should give you some idea. Apple were the founders of all this GUI-patent crap that now plagues software development, and which is one of the main scourges free software advocates are fighting. And they first sued Microsoft, for... wait.... developing a GUI. Apple are/were just as bad if not worse than Microsoft.

---

### Post by schauerlich on 2009-09-06
I've updated the FAQ, generally cleaning it up, expanding/rewriting a section based on [a post I made](http://ubuntuforums.org/showpost.php?p=7905691&postcount=45), and updating links and references to recent Mac OS X releases. Enjoy.

---

### Post by Frak on 2009-09-06
> **EDavidBurg said:**
> I've updated the FAQ, generally cleaning it up, expanding/rewriting a section based on [a post I made](http://ubuntuforums.org/showpost.php?p=7905691&postcount=45), and updating links and references to recent Mac OS X releases. Enjoy.
You forgot that part about Safari being snappier as of the Snow Leopard update. Fix, nao.

---

### Post by Giant Speck on 2009-09-06
> **Frak said:**
> You forgot that part about Safari being snappier as of the Snow Leopard update. Fix, nao.

[img]http://i279.photobucket.com/albums/kk122/SpecKtacle/216785.gif[/img]

---

### Post by schauerlich on 2009-09-14
Updated "CS: Mac OS X is closed source" section with information about Grand Central Dispatch.

---

### Post by chris200x9 on 2009-09-14
> **Hellow said:**
> OS X isnt slow. Seriously, it isnt slow on any of the latest computers by Apple.

...slower than linux on my macbook....and alot stupider...

---

### Post by jzacsh on 2009-09-15
awesome post. at the very least i think it takes care of silly, silly, silly posts like this one:
[http://ubuntuforums.org/showthread.php?t=1266547](http://ubuntuforums.org/showthread.php?t=1266547)
that post ^ has nothing to say. it also seems like the author (not to *single out *the author, as I've heard others say the same things) is really just having a hard time failing at personafying Apple, Inc.
> **hoppipolla said:**
> [...]they seem to just take way more than they give and have no real interest or desire to just "be nice". [...] ... why would a company need anything more than **appear** to be nice? this isn't my next door neighbor, this is simply a company, a business.

---

### Post by schauerlich on 2009-09-19
Updated the OP asking for suggestions for new topics - if you have a topic you'd like me to cover and it's not on the list, feel free to suggest them here. Remember, this is about Mac OS X the operating system, and not Apple the company.

---

### Post by HappinessNow on 2009-09-22
> **Rainstride said:**
> trolling?Maybe?...but it is of the finest quality and nice and geeky.

> **Firestem4 said:**
> How is that trolling? read thread?

> **scaredpoet said:**
> 
I don't believe Edavidburg once attempted to say OS X is all positive.  yet it was interpreted that way, because that made it more convenient for you to attack his position if it was so misinterpreted.

I honestly saw no attack by aysiu, yet merely points were being made.

> **EDavidBurg said:**
> Updated "CS: Mac OS X is closed source" section with information about Grand Central Dispatch.

> **EDavidBurg said:**
> Updated the OP asking for suggestions for new topics - if you have a topic you'd like me to cover and it's not on the list, feel free to suggest them here. Remember, this is about Mac OS X the operating system, and not Apple the company.

Great recovery in edits. 

Thanks for the fun topic (I read the whole thread) :P

The [Recurring Discussions]("http://ubuntuforums.org/forumdisplay.php?f=302") are awesome, I should visit more often.

---

### Post by Exodist on 2009-09-22
I have a Mac, guess what its running Ubuntu alot faster then it did OSX. But thats not why I dislike apples. I dislike their over the top pricing. Apple IMHO will be the death of their selfs unless they bring pricing back down to earth.

---

### Post by mikeeve on 2009-09-22
Thanks for the FAQ. My son just purchased a MacBook, and I was curious about how much Unix actually is in Apple's underlying OS.  The original post was very informative, much more informative than some of the rebuttals to the post!

---

### Post by Giant Speck on 2009-09-22
> **Exodist said:**
> I have a Mac, guess what its running Ubuntu alot faster then it did OSX. But thats not why I dislike apples. I dislike their over the top pricing. Apple IMHO will be the death of their selfs unless they bring pricing back down to earth.

So wait... you bought a Mac and you're complaining about their pricing *after* the fact?

---

### Post by schauerlich on 2009-09-22
> **Giant Speck said:**
> So wait... you bought a Mac and you're complaining about their pricing *after* the fact?

= 19:25:32 | EDavidBurg > ~really really really really late | Exodist
= 19:25:32 | Lawnbot > Exodist: The author is dead now

---

### Post by schauerlich on 2009-09-27
> **Frak said:**
> A tad bit off topic, mostly on, but why do people rag on Apple for being proprietary? They've open-source most of the underlying important parts of the system, their own open-source browser engine is the most compliant (and uber-light and well documented), and even their kernel is open source. Besides those, they gave the source away for Grand Central Dispatch so that others could use it.

Before we say "Google's godly and Apple's the devil" because Google is "more" open source (I don't think that's possible), remember that Apple heavily contributes in Open Source too. Even Microsoft has released some things under the GPL, like [this]("http://port25.technet.com/archive/2009/07/21/the-live-services-plug-in-for-moodle-debuts.aspx").

That's about half of the FAQ in my sig.

---

### Post by Colonel Kilkenny on 2009-09-27
> **Frak said:**
> their own open-source browser engine is the most compliant (and uber-light and well documented), and even their kernel is open source.

remember that Apple heavily contributes in Open Source too

Perhaps you should also remember that Apple may contribute so much to open source because it has to... they're using GPL / LGPL based stuff.

WebKit (or actually just the WebCore and JavascriptCore parts of it) was open sourced because they had to as they took it from the KDE project. It took them several years to open source the whole WebKit.

---

### Post by HappinessNow on 2009-09-27
> **Colonel Kilkenny said:**
> Perhaps you should also remember that Apple may contribute so much to open source because it has to... they're using GPL / LGPL based stuff.

WebKit (or actually just the WebCore and JavascriptCore parts of it) was open sourced because they had to as they took it from the KDE project. It took them several years to open source the whole WebKit.Great Point! that many people forget.

---

### Post by BackwardsDown on 2009-09-27
> **Colonel Kilkenny said:**
> Perhaps you should also remember that Apple may contribute so much to open source because it has to... they're using GPL / LGPL based stuff.

Not totally true. The Kernel is released on the Darwin/Apple License, which is far less restricting than GPL, so they don't *have* to share the code.

---

### Post by Frak on 2009-09-27
> **Colonel Kilkenny said:**
> Perhaps you should also remember that Apple may contribute so much to open source because it has to... they're using GPL / LGPL based stuff.

WebKit (or actually just the WebCore and JavascriptCore parts of it) was open sourced because they had to as they took it from the KDE project. It took them several years to open source the whole WebKit.

The fact that they decided to open up the full webkit engine and not just stop at WebCore and JavaScriptCore is admirable. They weren't required to open source those, and they weren't required to open source them under such a permissive license.

---

### Post by schauerlich on 2009-09-27
> **Colonel Kilkenny said:**
> Perhaps you should also remember that Apple may contribute so much to open source because it has to... they're using GPL / LGPL based stuff.

Actually, most of it is released under either [the BSD license](http://en.wikipedia.org/wiki/Bsd_license), [the Apache license](http://en.wikipedia.org/wiki/Apache_license), or [Apple's own permissive open source license](http://en.wikipedia.org/wiki/Apple_Public_Source_License).

---

### Post by starcannon on 2009-09-28
> **simian man said:**
> so basically your saying that osx:
[list]
[*]can sort of run on lots of hardware
[*]is sort of open source
[*]is sort of hackable
[*]is not too slow
[*]has some linux software
[/list]

why would i want that when linux:
[list]
[*]will run on anything
[*]is totally open source
[*]is completely hackable
[*]is as fast as you want it to be
[*]has tons of great software
[*]and costs nothing
[/list]

and don't try to pretend that apple is a good-willed company.  If they had a 90% market-share, they would be more vindictive than microsoft.
[img]http://www.heandfi.org/wp-content/uploads/2007/06/mac_pc_linux.jpg[/img]
+1

---

### Post by stepstools on 2009-11-22
The problem with their open source is that the charge you for them program to develop mac programs, i-phone apps, etc.  At least Microsoft gives you C# free!

---

### Post by Frak on 2009-11-22
> **stepstools said:**
> The problem with their open source is that the charge you for them program to develop mac programs, i-phone apps, etc.  At least Microsoft gives you C# free!
?

XCode is free.

---

### Post by danbuter on 2009-11-22
Apple is super-secretive, to the point where it will even murder employees who lose iPhone prototypes, at least if they are in China/Korea.

---

### Post by schauerlich on 2009-11-22
> **danbuter said:**
> Apple is super-secretive, to the point where it will even murder employees who lose iPhone prototypes, at least if they are in China/Korea.

You honestly believe it was an Apple-ordered hit?

---

### Post by tubezninja on 2009-11-22
> **danbuter said:**
> Apple is super-secretive, to the point where it will even murder employees who lose iPhone prototypes, at least if they are in China/Korea.

[citation needed], especially if you're accusing a corporation of murder.

---

### Post by JDShu on 2009-11-22
Sounds like he is referring to[COLOR=Blue] **[this]("http://news.bbc.co.uk/2/hi/8162325.stm")**.[/COLOR]

---

### Post by enduser000 on 2009-12-24
New reply, I'm bumping this one up :P. My 2&#65504;:

OSX May appear slow to a linux/windows user simply because you don't know your way around it. This is my biggest thing.  The only thing I would say is apples fault here is lack of customization.  In ubuntu I can set my own hotkeys with ccsm (I use <super> + f for firefox, ect).  There are third party programs for this in osx, but they don't feel the same to me.

OSX's biggest setback is the lack of repositories. Every time I find a cool new program it's awesome I can just apt-get install it in ubuntu and don't have to find an installer or gather up the dependencies and install it from the source. 
MacPorts and Fink are great, don't get me wrong, and I actually use MacPorts on my osx box, but running geany in X11 for osx just isn't the same, it seems like it was just ported to this environment, not completely osx.  The hotkeys still use ctrl and it's odd switching between programs.

As for the OSS-ness of osx I think it's obliviously not the essential stuff, but it's not to be overlooked either.  After installing osx I was delighted to find that it comes with apache preinstalled!  php too?  possibly, I don't remember.  The great thing here is both that you don't have to install something else, BUT greater, that apple doesn't feel the need to re-make every kind of program in their own stupid image (not that it's stupid, but if it's done well, just send it off with your os... don't mess with it.).  I'm referring here to MS-SQL, VC++, and all the other stuff that forgoes standards and just spits in plenty of devs (except perhaps beginners and experts) faces.

In conclusion I'd say osx is a great os, but for me falls short on lack of customization and ultimately freedom,

end

---

### Post by schauerlich on 2010-02-16
Added a small section on CUPS. If anyone else has stuff to add there, let me know. I honestly don't know much about it.

---

### Post by Brv on 2010-03-11
schauerlich, +10, you're right

I have been use mac for 13 years. Mac FTW :o

---

### Post by madnessjack on 2010-03-12
I have nothing against macs, it's the morons that use them that piss me off :P

---

### Post by Tibuda on 2010-03-12
> **madnessjack said:**
> I have nothing against macs, it's the morons that use them that piss me off :P

yep. the same about windows. the same about linux.

---

### Post by Post Monkeh on 2010-03-12
> **danielrmt said:**
> yep. the same about windows. the same about linux.

well aren't you just a bundle of joy :D

---

### Post by prodigy_ on 2010-03-13
Darwin isn't FOSS. Darwin is a spit in the face of the whole FOSS community. Like in: "Hey, we've used your GPL code and just because GPL requires it, we "sort of contribute" these pieces of unusable code back to you. See how we've just raped you? Ha-ha."

I think GPL needs to become much more restrictive to prevent this sort of abuse. That is, you want to use GPL code in your project? Alright, but you make **all your code open-source without exceptions**. Or leave FOSS alone and build your own apps from scratch. If you can. (Obviously Aplle can't, because Mac OS classic was just one big fail. In fact, they couldn't even write their own HTML rendering engine.)

Aplle is worse than M$ actually. They just don't a big enough market share to be as mean as they'd like to be.

---

### Post by Bachstelze on 2010-03-13
> **prodigy_ said:**
> 
I think GPL needs to become much more restrictive to prevent this sort of abuse. That is, you want to use GPL code in your project? Alright, but you make **all your code open-source without exceptions**.

[img]http://i442.photobucket.com/albums/qq142/bigzeesh92/u-mad1.jpg[/img]

---

### Post by Frak on 2010-03-13
> **prodigy_ said:**
> Darwin isn't FOSS. Darwin is a spit in the face of the whole FOSS community. Like in: "Hey, we've used your GPL code and just because GPL requires it, we "sort of contribute" these pieces of unusable code back to you. See how we've just raped you? Ha-ha."

I think GPL needs to become much more restrictive to prevent this sort of abuse. That is, you want to use GPL code in your project? Alright, but you make **all your code open-source without exceptions**. Or leave FOSS alone and build your own apps from scratch. If you can. (Obviously Aplle can't, because Mac OS classic was just one big fail. In fact, they couldn't even write their own HTML rendering engine.)

Aplle is worse than M$ actually. They just don't a big enough market share to be as mean as they'd like to be.
Company takes source code, becomes more popular than Linux.

More at 11.

---

### Post by prodigy_ on 2010-03-13
> **Bachstelze said:**
> [img]http://i442.photobucket.com/albums/qq142/bigzeesh92/u-mad1.jpg[/img]
[I]"No, I'm not. No. I'm not."

- Joker[/i]

---

> **Frak said:**
> Company takes source code, becomes more popular than Linux.
/yawn
It's niche popularity. Outside of the US no-one regards OS X as a desktop, only as a design workstation OS.

---

### Post by schauerlich on 2010-03-13
> **prodigy_ said:**
> I think GPL needs to become much more restrictive to prevent this sort of abuse. That is, you want to use GPL code in your project? Alright, but you make **all your code open-source without exceptions**. 

I guess you can't use Linux, then. It's got plenty of code contributed to it by companies and individuals who also put out proprietary software.

---

### Post by Frak on 2010-03-13
> **prodigy_ said:**
> /yawn
It's niche popularity. Outside of the US no-one regards OS X as a desktop, only as a design workstation OS.

Except for the Japanese, Canadians, and all of Europe. Not sure about Russia, but it's probably there too considering many of my Russian friends use Mac's as desktops.

"niche popularity" means something different to you than everybody else it seems.

---

### Post by prodigy_ on 2010-03-13
> **Frak said:**
> and all of Europe
I see. You're just trolling. Have a nice day and welcome to my ignore.

---

### Post by Frak on 2010-03-13
> **prodigy_ said:**
> I see. You're just trolling. Have a nice day and welcome to my ignore.
[IMG]http://i442.photobucket.com/albums/qq142/bigzeesh92/u-mad1.jpg[/IMG]

I know you're going to read this.

---

### Post by schauerlich on 2010-03-13
Try not to get my thread closed, guys...

---

### Post by Bachstelze on 2010-03-13
> **schauerlich said:**
> Try not to get my thread closed, guys...

you mad?

---

### Post by schauerlich on 2010-03-13
> **Bachstelze said:**
> you mad?

Yee, mayne.

---

### Post by ElSlunko on 2010-03-13
*headdesk*

---

### Post by superarthur on 2010-03-13
> **schauerlich said:**
> **CS: Apple is evil/ripped off BSD/GNU/FOSS advocates**
MAD: Apple has released all of the open source code it's integrated into Darwin/OS X back to the community. See [Apple's Open Source page](http://www.apple.com/opensource/) for more details. While Apple has not released the more "important parts" of the OS (to the end user) such as Cocoa or Aqua, it has released all of the code it used from open source projects back to the community.

I see your point about Apple is not ripped off BSD/GNU/FOSS advocates. But how does it make Apple not evil? :p

---

### Post by Frak on 2010-03-13
> **superarthur said:**
> I see your point about Apple is not ripped off BSD/GNU/FOSS advocates. But how does it make Apple not evil? :p
Wasn't aware that corporations had morals.

---

### Post by ElSlunko on 2010-03-13
> **Frak said:**
> Wasn't aware that corporations had morals.

Not morals but I'm sure they'd like to keep customers happy -- some who have morals.

---

### Post by Frak on 2010-03-13
> **ElSlunko said:**
> Not morals but I'm sure they'd like to keep customers happy -- some who have morals.
That's their only goal: To make a profit.

---

### Post by ElSlunko on 2010-03-13
> **Frak said:**
> That's their only goal: To make a profit.

Right and it's directly associated to a social context. Corps don't magically make profits, they need customers.

---

### Post by Frak on 2010-03-13
> **ElSlunko said:**
> Right and it's directly associated to a social context. Corps don't magically make profits, they need customers.
Um, yes?

---

### Post by ElSlunko on 2010-03-13
> **Frak said:**
> Um, yes?

So they have to at least (in some cases) appear to have morals.

---

### Post by schauerlich on 2010-03-13
> **ElSlunko said:**
> So they have to at least (in some cases) appear to have morals.

It's a Machiavellian situation.

---

### Post by jrothwell97 on 2010-03-13
> **prodigy_ said:**
> Darwin isn't FOSS. Darwin is a spit in the face of the whole FOSS community. Like in: "Hey, we've used your GPL code and just because GPL requires it, we "sort of contribute" these pieces of unusable code back to you. See how we've just raped you? Ha-ha."
...except they didn't, they used their own code, derived from NeXTSTEP, whose kernel was in turn based on Mach.

(Also, "unusable"? I point you to [PureDarwin](http://www.puredarwin.org/), [Midori](http://www.twotoasts.de/index.php?/pages/midori_summary.html), [Chromium](http://www.chromium.org/) and CUPS, all of which are perfectly usable and bear at least some contribution from Apple.)

> **prodigy_ said:**
> I think GPL needs to become much more restrictive to prevent this sort of abuse. That is, you want to use GPL code in your project? Alright, but you make **all your code open-source without exceptions**. Or leave FOSS alone and build your own apps from scratch.
What you're proposing there is economic protectionism, which is totally at odds with the FLOSS ideology.

> **prodigy_ said:**
> If you can. (Obviously Aplle can't, because Mac OS classic was just one big fail. In fact, they couldn't even write their own HTML rendering engine.)
[list=1][*]Mac OS Classic was good for its time, and only stagnated due to weak management failing to provide a next-generation OS in the mid-90s. (The fact they *did* eventually transition to a new architecture should also reveal that Apple knows when to change things.)
[*]They *did* write their own HTML rendering engine. Or, to be more precise, they took KHTML (Konqueror's rendering engine) and, true to the spirit of open-source, forked it as WebKit, improved upon it *vastly*, and released the result (or *cough* **contributed**) under the LGPL/BSD licenses.[/list]

> **prodigy_ said:**
> Aplle is worse than M$ actually. They just don't a big enough market share to be as mean as they'd like to be.
M$? Seriously? The only place I find that tired old joke now is in the dark recesses of the Slashdot comment boards, trawling through the cess at -1.

Steve Jobs is no saint, but if you're going to make an argument at least check your facts beforehand and don't resort to name-calling.

---

### Post by Frak on 2010-03-13
> **jrothwell97 said:**
> ...except they didn't, they used their own code, derived from NeXTSTEP, whose kernel was in turn based on Mach.

(Also, "unusable"? I point you to [PureDarwin](http://www.puredarwin.org/), [Midori](http://www.twotoasts.de/index.php?/pages/midori_summary.html), [Chromium](http://www.chromium.org/) and CUPS, all of which are perfectly usable and bear at least some contribution from Apple.)

You forgot my favorite, [Grand Central Dispatch]("http://libdispatch.macosforge.org/"), which can run unmodified on FreeBSD. Apple is taking great strides to make it run as well as possible under FreeBSD. They've even modified the LLVM compiler to support [C blocks runtime]("http://compiler-rt.llvm.org/"). Licensed under the Apache license, this is 100% Apple code, completely given away to anybody who wants/needs it.

---

### Post by swoll1980 on 2010-03-13
Why on god's green earth doesn't Apple release a PC version of OSX? They could make so much more money, and since the switch to x86 there isn't even anything special about Mac hardware. This just irritates me.

---

### Post by NightwishFan on 2010-03-13
If I could easily run it on PC hardware I would consider it. Technically the Mac kernel is open source, and that is my main requirement for an OS. The problem is im not sure if I have the right to remove any or all of the non-free bits (even if I don't actually want to remove them).

---

### Post by Frak on 2010-03-13
> **swoll1980 said:**
> Why on god's green earth doesn't Apple release a PC version of OSX? They could make so much more money, and since the switch to x86 there isn't even anything special about Mac hardware. This just irritates me.
Casual PC users aren't their target demographic. It seems stupid, but there are many great reasons why it'd be their downfall. Greatest one, they'd be stepping into Microsoft's territory, and as we've seen with other companies *cough* Be *cough* it doesn't end well. Besides, the target market they're aiming for now, the post $1000 market (which they dominate over 90% of), they make tons of money by convincing software companies to develop highly polished and specialty applications. By doing this, their target demographic (a wealthier bunch) will pay more per unit for a software whose Windows equivalent may cost much less. Combining user experience, a clean modern interface, exclusive offerings, and a highly polished experience with great support gives them an upper hand on their competitors.

tl;dr
Apple holds OS X to only run on the Mac platform because they're afraid of Microsoft, and by aiming at another demographic, they can still make ludicrous amounts of money and not butt heads with Microsoft.

---

### Post by Paqman on 2010-03-13
> **Frak said:**
> 
Apple holds OS X to only run on the Mac platform because they're afraid of Microsoft, and by aiming at another demographic, they can still make ludicrous amounts of money and not butt heads with Microsoft.

Couldn't agree more. They've grabbed themselves a niche market that's extremely lucrative. They've branded themselves as a luxury PC maker, to make a play for the rest of the market would be shooting themselves in the foot.

---

### Post by schauerlich on 2010-03-13
Selling OS X for generic x86 PCs would not jive at all with Apple's philosophy: they are primarily sellers of mobile devices. Yes, they develop, maintain and distribute OS X - but only because they need it to make their hardware do something useful. OS X, to Apple, is inseparable from their hardware. They are not marketing certain hardware which runs certain software - they are marketing a Mac.

---

### Post by ElSlunko on 2010-03-14
Well they're primarily a hardware company, no? I mean they design software FOR their hardware, at least that's the way I interpret it.

---

### Post by Frak on 2010-03-14
> **ElSlunko said:**
> Well they're primarily a hardware company, no? I mean they design software FOR their hardware, at least that's the way I interpret it.
They're primarily a software company. They design very little, if any, hardware on-site.

---

### Post by swoll1980 on 2010-03-14
Steve Jobs said "We're a software company. We sell software. The hardware is just a pretty wrapper we put on it."

---

### Post by aysiu on 2010-03-14
> **swoll1980 said:**
> Steve Jobs said "We're a software company. We sell software. The hardware is just a pretty wrapper we put on it."
When did he say that? I'm having trouble finding the source of that quotation via search.

---

### Post by schauerlich on 2010-03-14
[Tim Cook: Apple is "a mobile-device company"](http://techcrunch.com/2010/02/23/tim-cook-apple-mobile-device-company/)

This was said a few weeks ago.

Apple doesn't sell certain software on certain hardware, it sells whole products. That's always been their philosophy.

---

### Post by Paqman on 2010-03-14
> **schauerlich said:**
> 
Apple doesn't sell certain software on certain hardware, it sells whole products. That's always been their philosophy.

These days they're also very much a content provider. Their closest analogue is probably Sony, who also make content and devices to watch it on. The difference is that Apple go out of their way to ensure that you use their hardware and software to consume their content.

---

### Post by impert on 2010-03-15
schauerlich,

You have made a good, informative post which didn't deserve the flaming it got.
That said, my Mac mini never looked so good as it does now with Debian on it. :)

---

### Post by Kenny_Strawn on 2010-03-17
You know, it's interesting: Aqua, the GUI on Mac OS X, and Plasma, the widget engine for KDE 4, have the exact same color scheme (blue and white) - when, essentially, Aqua deals with water and Plasma deals with gases - you get the idea.

Back on topic: Any efforts by Apple to open source any code have been countered (and even surpassed) by Apple's external locks, such as crippling to hardware, marking up the hardware's prices, and making it extremely hard to change the OS without dual-booting. You can dual-boot on a Mac, but if you want to have Windows or Linux as your only OS, tough luck.

---

### Post by schauerlich on 2010-03-17
> **Kenny_Strawn said:**
> You can dual-boot on a Mac, but if you want to have Windows or Linux as your only OS, tough luck.

1) Install another operating system
2) Use that other operating system
3) THERE IS NO STEP 3!

---

### Post by Kenny_Strawn on 2010-03-17
> **schauerlich said:**
> 1) Install another operating system
2) Use that other operating system
3) THERE IS NO STEP 3!

What I was saying was that because the bootloader for OS X is on the motherboard and cannot be erased with a Linux or Windows install, erasing the OS X partition will render the Mac unbootable, because the bootloader will look for OS X before it looks for anything else.

Or so I can infer from the fact that OS X does not come with its own bootloader and that you have to install a bootloader separately if you want OS X to be installed on anything other than a Mac.

---

### Post by schauerlich on 2010-03-17
> **Kenny_Strawn said:**
> What I was saying was that because the bootloader for OS X is on the motherboard and cannot be erased with a Linux or Windows install, erasing the OS X partition will render the Mac unbootable, because the bootloader will look for OS X before it looks for anything else.

Or so I can infer from the fact that OS X does not come with its own bootloader and that you have to install a bootloader separately if you want OS X to be installed on anything other than a Mac.

[https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation#Single-Boot:%20Ubuntu%20Only](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation#Single-Boot:%20Ubuntu%20Only)

Yes, there are special considerations because of the EFI vs BIOS and GPT vs MBR scheme, but in the end, there's nothing preventing you from running only Linux on a Mac.

---

### Post by Frak on 2010-03-17
> **Kenny_Strawn said:**
> Back on topic: Any efforts by Apple to open source any code have been countered (and even surpassed) by Apple's external locks, such as crippling to hardware, marking up the hardware's prices, and making it extremely hard to change the OS without dual-booting. You can dual-boot on a Mac, but if you want to have Windows or Linux as your only OS, tough luck.

I think everything in this post is false. Pretty sure. Windows 7 has native EFI, and yes, that means Windows doesn't need a BIOS in order to boot.

---

### Post by KiwiNZ on 2010-03-17
> **Kenny_Strawn said:**
> What I was saying was that because the bootloader for OS X is on the motherboard and cannot be erased with a Linux or Windows install, erasing the OS X partition will render the Mac unbootable, because the bootloader will look for OS X before it looks for anything else.

Or so I can infer from the fact that OS X does not come with its own bootloader and that you have to install a bootloader separately if you want OS X to be installed on anything other than a Mac.

You really need to think and research a little before you post [-X

---

### Post by a.walker on 2010-03-17
While we are posting all sorts of things unrelated to Mac OS X (the software). I have two points about apple products / tools... I will first start with the tools.

1) I'm sick of watching Justin Long act like a d-bag and having people emulate him.

2) I'm not terribly impressed with apple's hardware. I have a macbook 4.1. I almost never take it outside of the house and I don't abuse it, yet one year after I got it, the bezel, palmrest, and parts of the chassis were cracked and I had pieces of plastic falling off of it.  Two years after having it, the inverter board went out and the power supply started falling apart. These may be issues related to macbook 4.1s (in later macbooks they redesigned the bezel so that it would break pieces of plastic off the palmrests), but my opinion of their hardware is that it is craptacular.

On the plus side, they were pretty good about fixing it. I only had to pay for the inverter board (no labor) and they replaced the palmrest and bezel for free.

---

### Post by Frak on 2010-03-18
> **Kenny_Strawn said:**
> Or so I can infer from the fact that OS X does not come with its own bootloader and that you have to install a bootloader separately if you want OS X to be installed on anything other than a Mac.

OS X's bootloader is called BootX. It is tied to the hardware, because OS X was only meant to run on Macs.

---

### Post by schauerlich on 2010-03-18
> **Frak said:**
> OS X's bootloader is called BootX. It is tied to the hardware, because OS X was only meant to run on Macs.

Only on PPC Macs. Intel macs have boot.efi instead.

[http://developer.apple.com/mac/library/DOCUMENTATION/MacOSX/Conceptual/BPSystemStartup/Articles/BootProcess.html](http://developer.apple.com/mac/library/DOCUMENTATION/MacOSX/Conceptual/BPSystemStartup/Articles/BootProcess.html)

---

### Post by Frak on 2010-03-18
> **schauerlich said:**
> Only on PPC Macs. Intel macs have boot.efi instead.

[http://developer.apple.com/mac/library/DOCUMENTATION/MacOSX/Conceptual/BPSystemStartup/Articles/BootProcess.html](http://developer.apple.com/mac/library/DOCUMENTATION/MacOSX/Conceptual/BPSystemStartup/Articles/BootProcess.html)
Didn't know that. I just kept getting error messages on my Mac's about BootX (I only own PowerPC Macs). I was under the presumption they kept it.

---

### Post by Giant Speck on 2010-03-18
> **a.walker said:**
> 1) I'm sick of watching Justin Long act

I agree with this, even if I did misquote you.  :p

---

### Post by Kenny_Strawn on 2010-03-18
> **Frak said:**
> OS X's bootloader is called BootX. It is tied to the hardware, because OS X was only meant to run on Macs.

Yeah, and it also means that wiping out OS X will break BootX (or DUBL, whichever you want to call it) and render your system unbootable. That is, unless you hack it.

On second thought, partition table changes also work.

---

### Post by Frak on 2010-03-18
> **Kenny_Strawn said:**
> Yeah, and it also means that wiping out OS X will break BootX (or DUBL, whichever you want to call it) and render your system unbootable. That is, unless you hack it.

On second thought, partition table changes also work.
BootX/Boot.efi is only used for OS X. Windows and Linux have their own bootloaders. Windows has BCDEFI and Linux uses plain old Grub. PowerPC Linux uses Yaboot.

BootX and Boot.efi are OS X specific. Boot.efi can also chainload virtual Windows partitions.

---

### Post by libssd on 2010-05-26
> **a.walker said:**
> 
2) I'm not terribly impressed with apple's hardware. I have a macbook 4.1. I almost never take it outside of the house and I don't abuse it, yet one year after I got it, the bezel, palmrest, and parts of the chassis were cracked and I had pieces of plastic falling off of it.  Two years after having it, the inverter board went out and the power supply started falling apart. These may be issues related to macbook 4.1s (in later macbooks they redesigned the bezel so that it would break pieces of plastic off the palmrests), but my opinion of their hardware is that it is craptacular.
While there may be individual problems (every manufacturer sells the occasional lemon), I have to disagree with this statement. I've owned Macs since May 1984, and have **never** had a hardware failure of any kind. 

In 2006 I took a G4 Macbook on an 11,000 mile motorcycle ride to Alaska, and subjected it to extremes of temperature (upper 30's to well over 100 degrees in luggage), shocks from potholes and dirt roads, and a beer spilled on the keyboard. I never turned it off, unless I expected to be out of range of a power source for more than 24 hours, or had to swap for a battery with a fresh charge. The Macbook never skipped a beat, and worked as well at the end of the trip as at the beginning. 

As John Cameron Swayze used to say in ads for Timex wristwaches, it "takes a licking and keeps on ticking."

[http://userwww.service.emory.edu/~libssd/Alaska2006/](http://userwww.service.emory.edu/~libssd/Alaska2006/)

---

### Post by aysiu on 2010-05-26
> **libssd said:**
> While there may be individual problems (every manufacturer sells the occasional lemon), I have to disagree with this statement. I've owned Macs since May 1984, and have **never** had a hardware failure of any kind. How do you know your experience is typical?

My wife had a G4 Powerbook she used for 3.5 years, at which point its hard drive failed. Before the hard drive failed, the power cord got frayed at the input point (a good thing Apple moved to the MagSafe power cords). Then she got a Macbook Pro, which 2.5 years later had a graphics card that failed.

Apple rightly [admitted it was a **common problem**](http://support.apple.com/kb/ts2377) and fixed it for free, but it did fail, and it was not a singular occurrence.

In fact, if you [Google *flickering macbook pro*](http://www.google.com/search?hl=en&source=hp&q=flickering+macbook+pro&btnG=Google+Search), you'll see it's quite common.

**Macs do not use special internal hardware.** My Macbook Pro, which I inherited from my wife, (yes, the one with the failed graphics card) has an Nvidia graphics card and Fujitsu SATA hard drive. I forgot the original brand of the RAM, but it wasn't anything special before I replaced it. From what I've seen in my friends' Facebook posts, Macs seem to have just about the same hardware failure rate as Windows PCs, and that totally makes sense, considering they use the same internal hardware.

---

### Post by Roasted on 2010-05-26
> **libssd said:**
> While there may be individual problems (every manufacturer sells the occasional lemon), I have to disagree with this statement. I've owned Macs since May 1984, and have **never** had a hardware failure of any kind. 



Consider yourself lucky.

I worked at a school district for 4 months during my internship. There were constant issues with the Macs in the library. Every day, 3-4 wouldn't work. The fix? We found re-imaging them seemed to buy them a new lease on life. Ultimately, we had to threaten suit with Apple, because the systems were about to be out of warranty (within another 2-3 weeks) and they said "it's too close to the end of the warranty period for us to support that". Wow. Fail, Apple. However we discovered ALL of the system boards had issues. A few google searches revealed this was actually, a common problem. Apple did however end up coming in with a large box truck and a few techs to replace all of the boards. +1 to Apple for upholding their original agreement, -10 for trying to swindle their way out of it.

While I would agree that Mac tends to do a better overall job with their system builds and how tight-knit things can feel, the thing is, it's typical hardware inside. I'm sorry, but it is. Sure, they tweak the hardware to work "better" with their software, but the hardware is nothing out of Area51 from recovered alien spacecraft, or blessed by the hand of Jesus.

Anyway, my point is, an Apple is a computer. Computers can have problems. Computers can fail. I know it's hard for a lot of Mac users out there to bite down on this, but that's the reality in the grand scheme of life.

---

### Post by aysiu on 2010-05-26
> **Roasted said:**
> 
Anyway, my point is, an Apple is a computer. Computers can have problems. Computers can fail. I know it's hard for a lot of Mac users out there to bite down on this, but that's the reality in the grand scheme of life. This.

The school I work in has both Macs and Windows PCs. I am not officially part of the tech department, but I do have access to the help desk, and I help every now and then. Guess what--the Macs have just as many problems as the Windows PCs do. Macs are computers, not magic. I like Macs. I use a Mac as my main computer now (Ubuntu netbook became secondary). They are great. They are not perfect, though. And the internal hardware is not blessed by some fairy with pixie dust.

I guess the common misconception, in line with the title of this thread, would be "Macs have special hardware that makes them impervious to hardware failure."

---

### Post by KiwiNZ on 2010-05-26
> **aysiu said:**
> This.

The school I work in has both Macs and Windows PCs. I am not officially part of the tech department, but I do have access to the help desk, and I help every now and then. Guess what--the Macs have just as many problems as the Windows PCs do. Macs are computers, not magic. I like Macs. I use a Mac as my main computer now (Ubuntu netbook became secondary). They are great. They are not perfect, though. And the internal hardware is not blessed by some fairy with pixie dust.

I guess the common misconception, in line with the title of this thread, would be "Macs have special hardware that makes them impervious to hardware failure."

The internals maybe similar but the assembly is superior. And that makes a huge difference. Take for instance the assembly of the HP consumer range the DV****** range , the assembly quality is terrible and as a result the failure rate is very high.

Open a Mac Pro Tower  and compare the assembly to a Dell or HP Tower and see what is better.

Macs are not blessed with fairy dust , they are blessed with good design and good quality control.

---

### Post by aysiu on 2010-05-26
> **KiwiNZ said:**
> 
Macs are not blessed with fairy dust , they are blessed with good design and good quality control. Tell that to the graphics card that failed in my 2.5-year-old Macbook Pro.

External hardware design, great. Internal assembly, also great. That doesn't mean the hardware itself won't fail. And my laptop also suffers from quite a bit of overheating (it's the Macbook Pro 3,1). My wife's new Macbook Pro suffers no such problem, thankfully!

To someone with a failed graphics card or a failed hard drive, the beauty of the inner assembly doesn't really matter, to be honest.

---

### Post by Joeb454 on 2010-05-26
I have to agree with Kiwi on the build quality - I have an early 2009 MacBook, which was - at the time - the top spec MacBook - I have to say, I've had nothing but good experiences with it, I've been very impressed with the build of it, by far and away more sturdy than any other laptop I've owned.

That said - I know the hardware isn't anything special, I think the only difference at the time was that Apple had already started putting DDR3 RAM into the laptops, where most manufacturers hadn't.

---

### Post by mickie.kext on 2010-05-26
> **KiwiNZ said:**
> The internals maybe similar but the assembly is superior. And that makes a huge difference. Take for instance the assembly of the HP consumer range the DV****** range , the assembly quality is terrible and as a result the failure rate is very high.

Open a Mac Pro Tower  and compare the assembly to a Dell or HP Tower and see what is better.

Macs are not blessed with fairy dust , they are blessed with good design and good quality control.

Most "PCs" are made in by same company as Macs. [Foxconn]("http://www.foxconn.com/").

Argument about Apple having better hardware lost all validity when they switched to Intel. It is stylish and looks better, but that's about it.

---

### Post by KiwiNZ on 2010-05-26
> **aysiu said:**
> Tell that to the graphics card that failed in my 2.5-year-old Macbook Pro.

External hardware design, great. Internal assembly, also great. That doesn't mean the hardware itself won't fail. And my laptop also suffers from quite a bit of overheating (it's the Macbook Pro 3,1). My wife's new Macbook Pro suffers no such problem, thankfully!

To someone with a failed graphics card or a failed hard drive, the beauty of the inner assembly doesn't really matter, to be honest.

Even the finest  Cars cars , watches  whatever will have some failure rate . To say they wont is plain stupid.

But the quality of assembly goes a long way to eliminate the risk of failure. As electrical connections are sounder, impedance's are more constant, cooling is more constant. Standards are adhered to etc etc .

---

### Post by KiwiNZ on 2010-05-26
There is also the consistency of how the OS manages the Mac therefore maintaing the environment for the internals as designed. Mac does this better than Windows as they design OSX only for their hardware.

---

### Post by jrothwell97 on 2010-05-26
> **mickie.kext said:**
> Most "PCs" are made in by same company as Macs. [Foxconn]("http://www.foxconn.com/").
The blueprints, however, are far from identical. That's like saying all the stuff that a food factory turns out is turkey twizzlers.

Consider this, the inside of a normal computer:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=158355&stc=1&d=1274904064[/IMG]

And now, the inside of a Mac Pro:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=158356&stc=1&d=1274904064[/IMG]

While the hardware within may not be all that different from the inside of a bog-standard Dell workstation, how it all fits together matters as well.

> **mickie.kext said:**
> Argument about Apple having better hardware lost all validity when they switched to Intel. It is stylish and looks better, but that's about it.
I won't say this is completely untrue, because Macintoshes certainly did lose their performance advantage when they switched to Intel CPUs (you can argue that they now draw less power, but that doesn't make Photoshop macros run any faster.)

However, as I mentioned, the little things matter. MacBook (Pro)s , for example, have a battery monitor built into the body of the battery itself. The keyboards are backlit. Aluminium is prettier than plastic and harder-wearing (some also think it also takes on a rugged attractiveness when deformed.) The touchpad, whilst of debatable utility, is at least different.

So, in terms of raw performance, you're right: in terms of practicality, however, you're wrong.

---

### Post by libssd on 2010-05-26
> **aysiu said:**
> How do you know your experience is typical?

My wife had a G4 Powerbook she used for 3.5 years, at which point its hard drive failed. Before the hard drive failed, the power cord got frayed at the input point (a good thing Apple moved to the MagSafe power cords). Then she got a Macbook Pro, which 2.5 years later had a graphics card that failed.

Apple rightly [admitted it was a **common problem**](http://support.apple.com/kb/ts2377) and fixed it for free, but it did fail, and it was not a singular occurrence.

In fact, if you [Google *flickering macbook pro*](http://www.google.com/search?hl=en&source=hp&q=flickering+macbook+pro&btnG=Google+Search), you'll see it's quite common.

**Macs do not use special internal hardware.** My Macbook Pro, which I inherited from my wife, (yes, the one with the failed graphics card) has an Nvidia graphics card and Fujitsu SATA hard drive. I forgot the original brand of the RAM, but it wasn't anything special before I replaced it. From what I've seen in my friends' Facebook posts, Macs seem to have just about the same hardware failure rate as Windows PCs, and that totally makes sense, considering they use the same internal hardware.
I don't know that my experience is typical or atypical, although you would think that in 26 years, I would have encountered *some* hardware failures along the way.

I neither stated nor implied that Apple uses any special hardware. Macs are mostly (if not exclusively) built in China from the same generic components that everybody else uses.

This thread is drifting quite far from the original topic, which was OS X.

---

### Post by mickie.kext on 2010-05-26
@jrothwell97
That is not quite exactly what I meant. 

Argument was that Apple are somehow more enduring and more quality computers, so they do not fail so often. For that to be true, it would require more advanced manufacturing process, not just different blueprints. Since Apple outsource to Foxconn like most "PC" OEMs, that argument does not stick. They are same quality. Changing standard ATX motherboard format to [BTX]("http://en.wikipedia.org/wiki/File:BTX-Gehaeuse_IMGP1405.jpg") is not Apple's special sauce. Dell and HP have some models with BTX motherboards too. And it does not change durability in any way.

I was not talking about practicality. As I said, Macs are more stylish than most other other computers, but do not have that fairy dust that some people believe they have.

---

### Post by KiwiNZ on 2010-05-26
> **mickie.kext said:**
> @jrothwell97
That is not quite exactly what I meant. 

Argument was that Apple are somehow more enduring and more quality computers, so they do not fail so often. For that to be true, it would require more advanced manufacturing process, not just different blueprints. Since Apple outsource to Foxconn like most "PC" OEMs, that argument does not stick. They are same quality. Changing standard ATX motherboard format to [BTX]("http://en.wikipedia.org/wiki/File:BTX-Gehaeuse_IMGP1405.jpg") is not Apple's special sauce. Dell and HP have some models with BTX motherboards too. And it does not change durability in any way.

I was not talking about practicality. As I said, Macs are more stylish than most other other computers, but do not have that fairy dust that some people believe they have.

You need to get in touch on how things are done and controlled when outsourced.

---

### Post by NightwishFan on 2010-05-26
My Asus laptop has been very reliable for me so far. Survived a fire, and months of travel. I would rather have it than a Mac so far.

---

### Post by jrothwell97 on 2010-05-26
> **mickie.kext said:**
> @jrothwell97
That is not quite exactly what I meant. 

Argument was that Apple are somehow more enduring and more quality computers, so they do not fail so often. For that to be true, it would require more advanced manufacturing process,

I point you to the process they devised for the Unibody MBPs - that's an entirely different (and arguably more advanced) manufacturing process.

Q.E.D.

---

