---
title: "Which version to install on old Dell Latitude D520"
date: 2015-05-26
forum: New to Ubuntu
---

### Post by lorem_ipsum2 on 2015-05-26
Hi,

I have an old Dell Latitude D520 on which I would like to install some version of Linux.  In addition to being old, the CD drive has failed, so I will need to install the new OS via USB.  I have read that some versions function better in this capacity than others.  

I tried installing Ubuntu and Kubuntu on it years ago before the disk drive failed, but I recall running into some problem related to the hardware (video?) which prevented the install from being successful.  The details escape me, but I mention in case it wasn't user error.  

The specs are:
1.66 Ghz
504 Mb Ram
~37 Gb HDD

I intend to use it for learning via webpages like coursera, lynda, etc in addition to coding, reading pdfs, general web browsing, and typesetting the occasional LaTeX document.  I suspect these shouldn't be too great of demands, although it would certainly be better if it had more ram.  

Any suggestions you can make would be greatly appreciated!

---

### Post by TheFu on 2015-05-26
The best distro depends on your linux-fu.  For example, if you are an expert, then there is a mini-distro that will install in 1G of disk. Then you can add whatever programs and GUI you want.  However, it isn't friendly for GUI-only users.

There are a few GUIs that have lower system requirements. Lubuntu, Xubuntu for example. There are others. That amount of RAM will be difficult for most current-generation Linux desktops. If you drop that and go with a pure Window Manager environment, you will be amazed.  Something like TinyCore will scream on your box, but it isn't nearly as friendly and definitely NOT for writing webapps.  If that RAM is shared with the video card, it will be even worse.  You are almost better getting a $25 raspberry-Pi for the webapp stuff.

---

### Post by v3.xx on 2015-05-26
I have had fair success installing Lubuntu on similar systems.  Lu will run fast, but apps like firefox/chrome and others will eat up the 500M of ram.  But I still think Lubuntu is a good place to start, just need to be aware of the demands you place on it.  If you could come up with another 500M stick, it would make for a much better setup.

> Intel ® Graphics Media Accelerator 950 (Up to 128MB shared with 256MB system memory or up to 224MB shared with 512MB system memory

Is what I found.

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=gma+950&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=gma+950&sa=Search&cof=FORID:9)

---

### Post by Vladlenin5000 on 2015-05-26
Just a complement to the previous post:
The amount of RAM is 512MB -> 504MB = 512MB-8MB (system reserved for the integrated graphics)
504MB is already the total memory available for OS and apps.

Adding another 512MB, if doable, would make a huge difference. However, older memory modules are hard to find and often more expensive than the current generation.

For reference:
Dell Latitude D520 uses DDR2. The typical configurations is as yours: 1x512MB. It can be expanded up to 2BG (2x1GB).
Maxing out the RAM would make the most demanding Ubuntu - the standard one with Unity - run with an acceptable performance. Other lighter desktops, as previously suggested, would run surprisingly well. Cost: &#8364;30-35 in Europe.
Yes, this upgrade alone would cost more than the aforementioned Raspberry PI.

---

### Post by TheFu on 2015-05-26
Just to clarify - I wouldn't ever suggest a R-pi as a desktop replacement. 
There are many things this laptop will do better.  OTOH, if you have $80 and aren't tied to having a laptop, it is possible to build a low-end desktop cheap (MB+APU+RAM) and reuse old HDD, PSU, case, keybaord, monitor, mouse ... and $120 will provide an amazing "non-gaming" desktop (MB+CPU+RAM) with integrated GPU and reuse the same stuff above.

Alas - using the old laptop with lubuntu is probably where I'd start.

---

### Post by mattharris4 on 2015-05-26
> **lorem_ipsum2 said:**
> Hi,

I have an old Dell Latitude D520 on which I would like to install some version of Linux.  In addition to being old, the CD drive has failed, so I will need to install the new OS via USB.  I have read that some versions function better in this capacity than others.  

I tried installing Ubuntu and Kubuntu on it years ago before the disk drive failed, but I recall running into some problem related to the hardware (video?) which prevented the install from being successful.  The details escape me, but I mention in case it wasn't user error.  

The specs are:
1.66 Ghz
504 Mb Ram
~37 Gb HDD

I intend to use it for learning via webpages like coursera, lynda, etc in addition to coding, reading pdfs, general web browsing, and typesetting the occasional LaTeX document.  I suspect these shouldn't be too great of demands, although it would certainly be better if it had more ram.  

Any suggestions you can make would be greatly appreciated!


I did some basic research to augment what you have listed.  The CPU that came with this computer running at 1.66 GHz (assuming you haven't changed the CPU to something else running at the same speed) is a Intel Core Duo T2300.  The Passmark for this CPU is 742 which with today's standards is quite slow and not very capable. You can forget the full Ubuntu OS with Unity on this computer due to the slow processor, Edubuntu would probably work as long as you used GNOME Metacity as your GUI (not Unity) and you put at least another 2GB of RAM in the computer to bring it up to 2.5GB. The big issue here is that you only have 504MB of RAM.  Lubuntu and Xubuntu will boot and load the Google home page when Firefox is booted up but not surf the net reliably unless you can get at least another 1GB (1024MB) of RAM.  If you could get another 512MB of RAM, Firefox would load about 80% of websites using Lubuntu or Xubuntu but that other 20% would slow your computer to a crawl when it started using swap.

If you wish to put music, documents, videos, etc. on this computer you need a larger hard disk drive.  A 250GB 2.5" HDD can be bought for less than $50 (Newegg has one for $35 currently as of 26 May 2015), you would change out the HDD (quite easy on most laptops of this era, YouTube it for instructions) and then install Lubuntu or Xubuntu in the normal manner.  Make sure you have a SATA HDD on the computer currently, if you have the old IDE you will need to cruise eBay for a used replacement, those start at about $20 and are usually 80 or 120GB, 250GB HDDs are available for a bit more.

I see this computer came with a 56K dial-up modem from the factory.  I don't know if any Canonical OS still supports dial-up modems, those haven't came standard on computers for 7-8 years now.  If you don't use dial-up this is a moot point.  Your wireless and Ethernet cards should be supported without any trouble.  Bluetooth also came with this computer, some cards are supported if you happen to use that feature, some are not but we mainly find that a problem with Toshiba laptops.  This may be a moot point as well, I would estimate 95% of people don't even know how to use bluetooth on their computer which makes data limited for supporting that feature here.

Regarding your defective CD burner a replacement can be bought for about $25 at Newegg, Tiger Direct or your local computer shop, be sure to order the slim DVD burner (CD only burners are not manufactured in that size any more but the DVD version will work fine and yes, you would be able to use and burn DVDs even on this old of a computer using Brasero in Linux) and not the normal size so it will fit in your computer.  That should also be easy to replace and you can YouTube that as well.  Linux should support a new drive without any issue or driver loading.

Your issue in installing Kubuntu was likely because you were using the GUI install and you don't have enough RAM to use it.  Use the text based install (download the Alternate Installer DVD or USB instead of the usual one using the appropriate website for your chosen OS) and you should be fine installing any Canonical OS.  This computer came with the Intel 950 graphics card (I doubt it has been changed) so video should be supported fine.  It is actually using it (and using the GUI installer) that the lack of RAM is a problem.

I think this computer could be brought up to being reasonably smooth using Lubuntu or Xubuntu as an OS.  However, it would cost about $100-$120 to replace the RAM sticks with higher-capacity sticks, install a new DVD drive and a larger HDD.  You can buy a slightly better and faster refurb laptop with 2GB RAM, a DVD-RW drive (watch out, some refurbs only come with a DVD-ROM that only burns CDs) for about $130 with an 80GB HDD at Newegg (you might be able to get by with that size HDD if you don't dual-boot with Windows and don't put too much music/documents/etc on it.  If you can live with a DVD-ROM/CD-RW drive you can buy a refurb laptop with a 160GB HDD and 3GB RAM for about $165 at Newegg (you can replace the optical drive with a DVD burner for about $25 after you actually get the computer and the DVD-RW drive in your hands).  Both have Intel Core 2 Duo CPUs which are slightly faster than the CPU in your laptop.  Tiger Direct also sells refurb laptops in the same general price range.  The cost of bringing your computer up to today's requirements is so close to the cost of another laptop that has been completely tested and bad parts replaced on it that I don't really have any good advice one way or the other.  The computer with 3GB of RAM would run Ubuntu fine, the ones with only 2GB of RAM would need the lighter OSes such as Lubuntu or Xubuntu.  They do come with Windows 7 on them as well.

---

### Post by monkeybrain20122 on 2015-05-26
I don't think any *buntu would be satisfactory. Lubuntu may work but won't be great. Better try something like puppy linux.[http://puppylinux.org/main/Overview%20and%20Getting%20Started.htm](http://puppylinux.org/main/Overview%20and%20Getting%20Started.htm)

---

### Post by QIII on 2015-05-26
Personally, I wouldn't put much money into it.

I suggest Bodhi Linux with Enlightenment.  Enlightenment is a WM more than a DE, and it is very light.  

The main release of Bodhi is based on Ubuntu.

---

### Post by lorem_ipsum2 on 2015-05-27
I got lubuntu installed and am on my way.  If it turns out to be too bulky, I'll try out Bohdi and Puppy.  Both look like excellent suggestions!  Thank you everyone!

---

### Post by night_sky2 on 2015-05-27
> **lorem_ipsum2 said:**
> I got lubuntu installed and am on my way.  Thank you everyone for your suggestions.

Lubuntu should work ''correct'' on a 512MB machine but don't expect optimal performances. The Lubuntu team itself recommend 1GB of RAM.

If I were in your situation, I might give a shot at ToriOS instead. It is in Beta release now but it should be fine overall. It is based on Ubuntu and designed to be even lighter on ressources than Lubuntu and the (LXDE) desktop environment. A think the devs behind the project are targeting these very low specs machines specifically.

[http://torios.org/](http://torios.org/)

---

### Post by DuckHook on 2015-05-27
> **QIII said:**
> Personally, I wouldn't put much money into it.+1> I suggest Bodhi Linux...++1> **night_sky2 said:**
> ...give a shot at ToriOS instead.+++1

---

### Post by mörgæs on 2015-05-27
Like many other threads this one is focusing on the desktop environment on order to be light, but the real question is which applications, especially browsers, one wants to run.

Which of the light desktops to choose does not make a big difference. Which light- or heavyweight browser does.

Don't put money into this before you have experimented with the applications.

---

### Post by DuckHook on 2015-05-27
> **mörgæs said:**
> Don't put money into this before you have experimented with the applications....and mörgæs strikes at the heart of the matter. Even if your DE is light as a feather, the apps you choose to run may make this old puppy well-nigh unusable.

I have an old D600 with 512 MB running Bodhi. To be frank, it is mainly a lark, as I don't do any real work on it. More proof of concept than anything else. But it works&#8213;very well, I might add&#8213;provided I take care to use only the most modest apps and then run them only one at a time. When it comes to surfing, Midori is fine if you don't open too many tabs or try to run complex graphics, but the real ringer is Links2 which has a very crude graphical mode that can run in X. Since I don't surf video or gaming sites, and most of my browsing is static information content, this setup is great for me, but it probably does not work for most users these days.

If you stick to absolutely lightweight apps, then the performance will likely be bearable, if not outright reasonable. Anything 3D is out of the question.

---

### Post by mörgæs on 2015-05-27
Thanks for mentioning links2. I've now added it into the Old Hardware thread.

---

### Post by DuckHook on 2015-05-27
> **mörgæs said:**
> Thanks for mentioning links2. I've now added it into the Old Hardware thread....a word to the wise (or wary)...

It is actually *very* primitive. No cookies, no scripting capability at all, and stuck on only a subset of HTML4. It can be manually compiled to use an old version of Javascript, but most users ain't goin' near dat, so that isn't a real-world option. In its favour, it uses X as a framebuffer, so can also be run in graphics mode in a pure CLI (though this requires some obscure config file tweaks that won't be a problem to a console jockey). Last but not least, it is as ugly as sin. I find its retro awkward homeliness rather quaint, but am definitely in the minority.

There have been a number of forks and derivatives produced over the years, including the original Links, Lynx, and Elinks, to name only a few. AFAIK, only Links2 has the graphics engine.

You may wish to fence in your recommendation with above caveats in the interest of setting realistic expectations.

---

### Post by mattharris4 on 2015-05-27
> **night_sky2 said:**
> Lubuntu should work ''correct'' on a 512MB machine but don't expect optimal performances. The Lubuntu team itself recommend 1GB of RAM.

If I were in your situation, I might give a shot at ToriOS instead. It is in Beta release now but it should be fine overall. It is based on Ubuntu and designed to be even lighter on ressources than Lubuntu and the (LXDE) desktop environment. A think the devs behind the project are targeting these very low specs machines specifically.

[http://torios.org/](http://torios.org/)

Conceptually there are also other Linux-basd OSes such as Tiny Core that may work as well (I haven't tried it so I don't know, they claim to work with hardware such as the OP's).  However, I am afraid to send people that direction due to lack of support (and one moderator which I won't name as I think his advice is reasonable but I don't want to drag him into a debate with either other mods or Canonical employees agrees that we should not grasp at straws for solutions in situations too quickly when a reasonable solution is available without going there).  I am afraid that if I send someone in that direction and there is an issue he will not be able to get support to solve it.  I am leery of even Puppy's level of support but at least there is some with that OS unlike many other thinly used OSes which what you see on the website is all the support you get.  Someone with actual considerable experience using these OSes on a daily computer would need to chime in here before I would even consider recommending them to someone for anything but use on a computer that is not needed for daily use.

---

### Post by mattharris4 on 2015-05-27
> **mörgæs said:**
> Like many other threads this one is focusing on the desktop environment on order to be light, but the real question is which applications, especially browsers, one wants to run.

Which of the light desktops to choose does not make a big difference. Which light- or heavyweight browser does.

Don't put money into this before you have experimented with the applications.

This is true.  However, most people I know run either Firefox or Chrome (whether running Linux or Windows) which IME requires at least 1GB of RAM to run reasonably well on even Lubuntu (and that isn't even enough for sites such as SFGate, that site requires about 1.25GB to run properly).  For example I have tried the Midori web browser, for text pages it works fine.  It uses almost no RAM even with several tabs running (I tried it with the SFGate site, keeping an eye on the RAM used) and conceptually would work on the OP's laptop.  However, if there are picture galleries or videos on the page accessing them is either impossible or cumbersome.  With the usability of Midori I am reluctant to recommend it to anyone. The websites accessed themselves make a big difference as well.  For example on Lubuntu this site runs on less than 650MB RAM but SFGate requires 1100 plus MB RAM to run (both depend on how many tabs are open and what is on the particular pages).  Unfortunately most people don't know what the RAM requirements of the websites they browse require to run and it is unreasonable to ask people to list every website they browse even if it is only the ones they browse at least once a week (for many people that number is over 50 and for many some of those are pornographic and inappropriate to list on a site such as this where teenagers may be reading).  For these reasons I use my worst-case numbers in Firefox (IME Chrome uses about the same RAM in general) and the listed hardware to recommend OSes for someone unless they state another use such as only using the computer for word processing.

---

### Post by PhilGil on 2015-05-27
> **DuckHook said:**
> ...a word to the wise (or wary)...

It is actually *very* primitive. No cookies, no scripting capability at all, and stuck on only a subset of HTML4. It can be manually compiled to use an old version of Javascript, but most users ain't goin' near dat, so that isn't a real-world option. In its favour, it uses X as a framebuffer, so can also be run in graphics mode in a pure CLI (though this requires some obscure config file tweaks that won't be a problem to a console jockey). Last but not least, it is as ugly as sin. I find its retro awkward homeliness rather quaint, but am definitely in the minority.

There have been a number of forks and derivatives produced over the years, including the original Links, Lynx, and Elinks, to name only a few. AFAIK, only Links2 has the graphics engine.

You may wish to fence in your recommendation with above caveats in the interest of setting realistic expectations.
I recently tried out several lightweight graphical browser for a project I was working on and rather liked Dillo. Again, as DuckHook said, keeping expectations realistic is a necessity when exploring all types of ultra-lightweight applications. 

In  addition to being a very suitable OS for old devices, Puppy Linux is also great for  discovering and testing lightweight applications that could then be  incorporated into a Lubuntu/Xubuntu/Ubuntu Mate install. There's a whole  ecosystem of lightweight Linux software that most of us that use  relatively modern PC's and stick to the default applications will never  discover.

---

