---
title: "What are the things that you do NOT like about Firefox ?"
date: 2008-02-28
forum: Recurring Discussions
---

### Post by verb3k on 2008-02-28
Hi,

I like Firefox. It's a great web browser, but there are many things that bother me about it, and I am sure you also have some, so I will post mine and you post yours here and hopefully developers will look at our suggestions and demands. I will start:

1-When I click on a tiny file on the web and choose "open" it pops up the download window just to raise my blood pressure, how many times should I close this window? I don't need to see the download window, I just want to open the file. (probably the window should show up only if the file size is considerable)

2- Downloads are always separated into two files while they are being downloaded: example.zip and example.zip.part. That is not the case with other browsers.

3-Work offline doesn't operate on cache by default, I mean you can't browse your cache, you can only tell it to make X site available offline. (that's not the case with IE, you can browse the cache without any configuration)

I can only think of these right now, but I am sure there are many :)

So what do you have?

---

### Post by tdrusk on 2008-02-28
It crashes with flash, along with other browsers.

The tab bar isn't enabled by default.

---

### Post by TeoBigusGeekus on 2008-02-28
I use Opera, therefore I don't know whether I am entitled to post, but what a hell...
1)Does not have a lot of functionality by default - requires extensions
2)Once extensions have been added it can become major bloatware
3)Difficult to add search engines compared to Opera
4) Say you have 4 tabs open (1,2,3 and 4). You are in tab 1 and you click on tab 4 and close it. You will go to tab 3, whereas in Opera you would return to tab 1(the last visited tab)

---

### Post by verb3k on 2008-02-28
> **TeoBigusGeekus said:**
> 
4) Say you have 4 tabs open (1,2,3 and 4). You are in tab 1 and you click on tab 4 and close it. You will go to tab 3, whereas in Opera you would return to tab 1(the last visited tab)

yeah, I agree. That's really annoying.

---

### Post by aysiu on 2008-02-28
> **verb3k said:**
> yeah, I agree. That's really annoying.
Actually, the Opera behavior is what annoys me.

Sometimes I keep a certain tab open for later while I deal with all the tabs to the right. In Firefox, I can do this, and I won't get back to the original tab until all the tabs to the right have closed.

In Opera, I can't do this, as every tab I close will bring me back to the tab I've reserved for later.

I guess in the ideal world you'd be able to choose which behavior you want, regardless of what browser you're using. I don't see why it shouldn't be available as an option in about:config somewhere.

---

### Post by verb3k on 2008-02-28
Also, the right-click context menu has two problems: 

1. The menu opens directly at the tip of the mouse cursor.
2. It accepts right clicking.

The above 2 points mean that when I press the right mouse button on something to get the context menu, the cursor may move a tiny bit over the menu and releasing the button will choose an option which I didn't really want,  all this happens in split second and it's annoying (especially on low-end machines)

An appropriate solution might be moving the context menu a bit away of the cursor upon right clicking, or disabling selection with the right mouse button.

---

### Post by kerry_s on 2008-02-28
i love firefox, but it does have it's minor faults.

1. it's fat, even without extensions. i just want a trim browser that can do flash and media.

2. requires fixing to get it up to speed->

```

in /etc/environment
MOZ_DISABLE_PANGO=1
FLASH_GTK_LIBRARY=libgtk-x11-2.0.so.0

in about:config, just going to take from my pref.js to save typing. :)
user_pref("content.notify.backoffcount", 5);
user_pref("network.dns.disableIPv6", true);
user_pref("network.http.keep-alive.timeout", 600);
user_pref("network.http.pipelining", true);
user_pref("network.http.pipelining.maxrequests", 8);
user_pref("network.http.proxy.pipelining", true);
user_pref("network.prefetch-next", false);
user_pref("plugin.expose_full_path", true);

```

3. slow to start

4. when you select "in tabs", some still open new windows. requires changing about: config setting to get them all in tabs.
```
user_pref("browser.link.open_newwindow.restriction", 0);
```

i think that's it, everything else works fine or i can live with.

---

### Post by PiggiePaul on 2008-02-28
For some reason, (for no reason) I look at my CPU display and it's running at 100% (have 2 or 3 tabs in firefox) but nothing actually going on.

Shutting Firefox down and re-opening it, brings me back to me normal idle of around 5% cpu.

Dunno why, just happens every now and again.

---

### Post by verb3k on 2008-02-28
> **PiggiePaul said:**
> For some reason, (for no reason) I look at my CPU display and it's running at 100% (have 2 or 3 tabs in firefox) but nothing actually going on.

Shutting Firefox down and re-opening it, brings me back to me normal idle of around 5% cpu.

Dunno why, just happens every now and again.

I think I know why, it's the flash plugin. If you have a page with an embedded flash video, it will consume some of your CPU power even if you did NOT play it, and if you have more than one embedded flash video your CPU will be maxed at 100%. This problem isn't Firefox's fault. It's Adobe's fault for supplying a very buggy flash plugin for Linux.

---

### Post by capink on 2008-02-29
> **aysiu said:**
> Actually, the Opera behavior is what annoys me.

Sometimes I keep a certain tab open for later while I deal with all the tabs to the right. In Firefox, I can do this, and I won't get back to the original tab until all the tabs to the right have closed.

In Opera, I can't do this, as every tab I close will bring me back to the tab I've reserved for later.

I guess in the ideal world you'd be able to choose which behavior you want, regardless of what browser you're using. I don't see why it shouldn't be available as an option in about:config somewhere.

I think this can be done in opera > tools > preferences > tabs > cycle in tab bar order. I have not tried this because I prefer the default opera behaviour, but I think it is what you are looking for.

---

### Post by aysiu on 2008-02-29
> **capink said:**
> I think this can be done in opera > tools > preferences > tabs > cycle in tab bar order. I have not tried this because I prefer the default opera behaviour, but I think it is what you are looking for.
That's what you'd think, but I've tried that option, and it still behaves the same way.

---

### Post by chewearn on 2008-02-29
1. The default toolbar does not include "New Tab" button.

2. By default, bookmark toolbar is enabled, and automatically loaded with some lame RSS feed.

3. If the website in one tab is stucked/busy with some heavy javascript, or something (sometimes even happened in ubuntuforums.org), the entire Firefox locks up (include another Firefox window you open separately, thinking the lock-up will be isolated to one window).

---

### Post by samwyse on 2008-02-29
1. slow UI
2. I have to install an extension to get mouse wheel on tab bar
3. the context menu doesn't have "Back" on the top when the pointer is on an image, which makes it necessary to install mouse gestures for consistant navigation.
4. focus issues, I seem to have to do extra clicking get the Firefox window to get focus.
5. the keyboard doesn't work when the pointer is on flash content.
6. ctrl+pgup and ctrl+pgdown doesn't work when the focus is on a search field.
7. The GTK file dialog is kind of crappy.
8. The settings dialog is a mess. Why is disk cache in Advanced/Network with proxy settings?

I think 1 and 4 are fixed in Firefox 3.

---

### Post by verb3k on 2008-02-29
> **samwyse said:**
> 1. slow UI
2. I have to install an extension to get mouse wheel on tab bar
3. the context menu doesn't have "Back" on the top when the pointer is on an image, which makes it necessary to install mouse gestures for consistant navigation.
4. focus issues, I seem to have to do extra clicking get the Firefox window to get focus.
5. the keyboard doesn't work when the pointer is on flash content.
6. ctrl+pgup and ctrl+pgdown doesn't work when the focus is on a search field.
7. The GTK file dialog is kind of crappy.
8. The settings dialog is a mess. Why is disk cache in Advanced/Network with proxy settings?

I think 1 and 4 are fixed in Firefox 3.

#5 has also been solved with the latest flash plugin + FF3

One thing I am not sure of is how we can communicate these problems to the devs.  I took a look at their bugzilla and there's literally hundreds of thousands of unconfirmed bugs, which means that every FF dev thinks that he's got bigger things to worry about, and in the end it's users that must pay all the bills  :mad:

---

### Post by samwyse on 2008-02-29
> **verb3k said:**
> #5 has also been solved with the latest flash plugin + FF3

I meant #5, I had edited my list and forgot to change the numbering.

---

### Post by akiratheoni on 2008-02-29
> **TeoBigusGeekus said:**
> 1)Does not have a lot of functionality by default - requires extensions


Not sure if you know but IIRC having a Firefox that had the bare essentials was the whole intention of the developers, to create a minimal browser (as in features... maybe not so much on resources).

---

### Post by TeoBigusGeekus on 2008-02-29
> **akiratheoni said:**
> Not sure if you know but IIRC having a Firefox that had the bare essentials was the whole intention of the developers, to create a minimal browser (as in features... maybe not so much on resources).
If these are the standards then the best browser should be Epiphany.

---

### Post by verb3k on 2008-03-16
Look at what I found:
[http://www.firefoxmyths.com/](http://www.firefoxmyths.com/)
It does make some valid points :)

---

### Post by vexorian on 2008-03-16
> **verb3k said:**
> Look at what I found:
[http://www.firefoxmyths.com/](http://www.firefoxmyths.com/)
It does make some valid points :)
Yeah, thanks for linking a troll page which had the only intention to raise clicks on their adsense account.

Most of the stuff in that page is BS, for example the free software one, just the name and logo are not reproduceable, nothing stops you from making your own web browser from firefox not missing any feature, ask debian if you have doubts.

The rest of the page mostly involves inventing an statement and then debunking it, it is a nice usage of strawman and other fallacies, but nothing else.

..

I am just testing firefox 3 beta since today and I am excessively impressed, if you were to compare between the 1->2 upgrade and the 2->3 you wouldn't think it is a fair comparison, firefox 3 makes firefox 2 not look like an improvement over 1. Really.

---

### Post by LaRoza on 2008-03-16
> **vexorian said:**
> Yeah, thanks for linking a troll page which had the only intention to raise clicks on their adsense account.

Most of the stuff in that page is BS, for example the free software one, just the name and logo are not reproduceable, nothing stops you from making your own web browser from firefox not missing any feature, ask debian if you have doubts.

The rest of the page mostly involves inventing an statement and then debunking it, it is a nice usage of strawman and other fallacies, but nothing else.


The page linked had valid points. I see a big difference in speed, startup times, and features in Opera. (Opera user) I used to use Firefox, then I found Opera...

The page may find faults that aren't faults really, but it does point out the truth in many areas.

---

### Post by verb3k on 2008-03-16
> **vexorian said:**
> Yeah, thanks for linking a troll page which had the only intention to raise clicks on their adsense account.

Most of the stuff in that page is BS, for example the free software one, just the name and logo are not reproduceable, nothing stops you from making your own web browser from firefox not missing any feature, ask debian if you have doubts.

The rest of the page mostly involves inventing an statement and then debunking it, it is a nice usage of strawman and other fallacies, but nothing else.

..

I am just testing firefox 3 beta since today and I am excessively impressed, if you were to compare between the 1->2 upgrade and the 2->3 you wouldn't think it is a fair comparison, firefox 3 makes firefox 2 not look like an improvement over 1. Really.

I agree, I am using the nightly builds and it's really improved, especially memory consumption, a vanilla FF3 consumption is now equal to Opera but not less, but there are still areas where even FF3 doesn't perform well and most of what's mentioned in this topic remains true for FF3.

I've got to tip my hat to Opera, it's a great piece of software really. it's ultra-fast.  I am confident that if Opera had an extension system it will be the most popular browser on the net.

---

### Post by vexorian on 2008-03-16
Opera is not even open source, and obviously not free software, there's no point of comparison.

I haven't really seen any major performance differences between both browsers anyways, certainly not anything that was good enough in Opera to make it worth moving to a proprietary web browser with less features. The page is a troll anyways. Firefox 3 just improved speed and acid2 works, so the only 2 kind of valid points, so it doesn't really work anymore.

My favorite part was the part in which after all those opera hints it recommended "maxthon" (or  something like that) a browser that just used IE's rendering engine but had tabbed browsing... It was so embarassing , the guy must be relieved now that IE7 got tabbed browser he could remove that silly part from the page... Anyways, now that it has lost most of its previous splendor, let's stick to [firefoxFables](http://nanobox.chipx86.com/FirefoxFables/)

---

### Post by LaRoza on 2008-03-16
Firefox is a good browser, but it is hardly the best.

Opera, Safari, and Mozilla are sometimes better.

---

### Post by Rhapsody on 2008-03-16
It's pretty slow, though it seems to be getting better with Firefox 3.

Gecko is sometimes behind other layout engines when it comes to standards support (i.e. the stable version still doesn't pass Acid2), though they also seem to be doing better here recently, and anything's better than Trident.

The GUI can be horrifically unresponsive (not sure what the long-term plan is on this).

It uses GTK+ (guess I'll have to live with this, is there any specific reason there's no fork using Qt?).

---

### Post by durand on 2008-03-16
> **TeoBigusGeekus said:**
> I use Opera, therefore I don't know whether I am entitled to post, but what a hell...
1)Does not have a lot of functionality by default - requires extensions
2)Once extensions have been added it can become major bloatware
3)Difficult to add search engines compared to Opera
4) Say you have 4 tabs open (1,2,3 and 4). You are in tab 1 and you click on tab 4 and close it. You will go to tab 3, whereas in Opera you would return to tab 1(the last visited tab)

ditto....I think firefox is going in the right direction but it still seems very resource hungry for having so few features.....Well, at least its better than IE..

---

### Post by clanky on 2008-03-16
I don't think there is actually anything that I don't like about firefox, have been using it with windows for a while and now with Ubuntu, and it is by far the best browser that I have come across.

---

### Post by k2t0f12d on 2008-03-16
> **durand said:**
> it still seems very resource hungry for having so few features

I dunno about that.  I'm using ff3b4 and have four instances running with a grand total of 30 open tabs with absolutely no slowdown, stuttering, or any adversity whatsoever.

---

### Post by PoopSlayer on 2008-03-17
The only thing I don't like about FireFox is the bulkiness of the UI. The tabs are freaking HUMONGOUS and just one toolbar takes up so much space on the screen. That's why I use Epiphany (although I can't get flash to work...). And Opera seems to spend a long time "Contacting www.example.com".

---

### Post by daengbo on 2008-03-17
Google docs is broken in FF3. That's killing me.

---

### Post by aysiu on 2008-03-17
I don't know what you're talking about (see the attached screenshots). If any UI seems bulky to me, it's Epiphany.

By the way, you can adjust the minimum tab width to be smaller with *about:config*

---

### Post by verb3k on 2008-03-17
> **Rhapsody said:**
> 
It uses GTK+ (guess I'll have to live with this, is there any specific reason there's no fork using Qt?).

The Linux version of Opera officially uses Qt.

---

### Post by durand on 2008-03-17
Hmm...on my old computer that's attached to my tv, opera is very fast and loads quickly while ff is quite clunky. And this is on gentoo with a fair amount of optimisation...

---

### Post by verb3k on 2008-03-17
I hope the Opera company makes Opera open-source to compete with FF. Many companies release their software as oper-source when they go bakrupt like Blender for example.

---

### Post by durand on 2008-03-17
> **verb3k said:**
> I hope the Opera company makes Opera open-source to compete with FF. Many companies release their software as oper-source when they go bakrupt like Blender for example.

Thats such a cruel thing to say! I really doubt opera will go bankrupt, they really are excelling in new browser technology. Wasn't blender bought by the blenderfoundation?

---

### Post by Lord Illidan on 2008-03-17
Err, you don't have to go bankrupt to release Open source software :lolflag:

I'm using Firefox 3 beta 4, and it's miles better than Firefox 2. It's faster, doesn't take as much RAM..and stable, too. It's been on for about a day and a half, and hasn't had a noticeable increase in RAM despite me loading numerous tabs.

Also, it's very GTK integrated now. And as for Epiphany..bleh. Never got used to it.

*1-When I click on a tiny file on the web and choose "open" it pops up the download window just to raise my blood pressure, how many times should I close this window? I don't need to see the download window, I just want to open the file. (probably the window should show up only if the file size is considerable)*

There's an extension called [Download Statusbar]("https://addons.mozilla.org/en-US/firefox/addon/26"), try it out.

---

### Post by jacob01 on 2008-03-17
ummm well its free, works very well for me, lets me browse the web, download files, lots of plugins... i cant complain.

well the only complain is that it doesn't cook for me :lolflag:

but one thing i noticed is that on webpage with pull down bars sometimes the bar is hidden behind an image but this may not be firefox.

---

### Post by Rhapsody on 2008-03-17
> **verb3k said:**
> The Linux version of Opera officially uses Qt.
Yeah, but I don't want to use Opera. Partly because it's closed source, partly because it doesn't have Firefox's great extensions, partly because Konqueror uses Qt as well, partly because the system tray icon forces my system tray from two rows to one row for some reason (making it eat up over twice as much space), but mostly because I have a white text on dark grey colour scheme, and Opera seems completely baffled by this setup. Only the bundled 'Windows Native' theme actually works, everything else I've tried (including the default!) gives me white text on a light background, which is completely unreadable. Firefox themes seem to be more flexible on this issue, and the default works too.

---

### Post by verb3k on 2008-03-17
> **durand said:**
> Thats such a cruel thing to say! I really doubt opera will go bankrupt, they really are excelling in new browser technology. Wasn't blender bought by the blenderfoundation?

I don't really recall the story, It shouldn't really be bankruptcy per say,  if you take Firefox's story for example, Netscape couldn't compete with Microsoft's IE, and it seemed that Netscape would soon come to an end, but it was revived as a new open source project, many things happened and now we have our beloved Firefox :)
 (correct me if I'm wrong, I'm not a historian :lolflag: )

---

### Post by Jim! on 2008-03-18
Flash kind of freezes in Firefox on Ubuntu (not sure if its the same on windows)
Large CPU usage from what I remember when using windows, not sure about in Ubuntu though.

---

### Post by verb3k on 2008-03-18
> **Lord Illidan said:**
> 
There's an extension called [Download Statusbar]("https://addons.mozilla.org/en-US/firefox/addon/26"), try it out.

Thank you ! 
It's really a nice extension, works even with the nightlies.

---

### Post by najames on 2008-03-18
Tasks: 138 total,   1 running, 137 sleeping,   0 stopped,   0 zombie
Cpu(s): 12.9%us,  1.7%sy,  0.0%ni, 85.4%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   1814772k total,  1368548k used,   446224k free,   180612k buffers
Swap:  5695000k total,        0k used,  5695000k free,   431880k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
** 6355 najames  15   0  424m 153m  26m S   22  8.7 147:35.69 firefox-bin    **    
 4983 root      15   0  377m  80m  20m S    7  4.5  14:44.29 Xorg               
    1 root      15   0  2956 1852  532 S    0  0.1   0:01.38 init               
    2 root      10  -5     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0        
    4 root      34  19     0    0    0 S    0  0.0   0:00.00 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 mig

2 tabs of Firefox @ 22% CPU, 12 tabs of Opera onot even listed in the top 6, acutally wasn't listed at all.

---

### Post by chewearn on 2008-03-18
Let get back on topic: "Things you do not like about Firefox"

Sure, Opera is this and that, and Firefox is *not *this and that.  The thing is, Firefox is like Windows; it's not the "best" thing out there.  But boo-hoo, it's still sits high up in the list.

---

### Post by kamaboko on 2008-03-18
FF has lost it in my opinion.  Damn near 70% of the time I'm looking at something that requires flash, FF craps out.  Time to find something better.

---

### Post by your.pal.cookie on 2008-03-19
Similar to the tab closing behaviour, it would be nice if ctrl+tab would behave the way alt+tab does for switching between windows, which is that it jumps to the next most recently used window. Right now, ctrl+tab just cycles through the tabs from left to right.

---

### Post by aysiu on 2008-03-19
> **your.pal.cookie said:**
> Similar to the tab closing behaviour, it would be nice if ctrl+tab would behave the way alt+tab does for switching between windows, which is that it jumps to the next most recently used window. Right now, ctrl+tab just cycles through the tabs from left to right.
Actually, that behavior you find annoying in Firefox is one of the major reasons I use Firefox and not Opera. I hate having the tab revert to the most recently used tab. I like them to cycle in order.

---

### Post by TeoBigusGeekus on 2008-03-19
About tab behaviour in Opera:

> **TeoBigusGeekus said:**
> There's another one:
When you have a lot of tabs opened, right click anywhere on a page and keeping the mouse button pressed roll your mouse wheel. A menu will pop up letting you choose which tab you want to open.

Is there anything similar in FF?

---

### Post by TorqueyPete on 2008-03-19
> **tdrusk said:**
> It crashes with flash, along with other browsers.
.

Have to agree with that. :mad:

And ,come on people, if we're talking technical issues here, you shouldn't compare Firefix to 'windows', as any web browser opens 'windows' on your desktop. They are just part of any GUI. And if you mean 'Windows', it's a whole operating system, not a web browser, that's Internet Explorer.
:)
;)

---

### Post by durand on 2008-03-19
Actually the only reason I use firefox sometimes is that opera doesn't seem to like flash anymore..it plays two seconds and then stops. Anyway, back to firefox! I do like the fact that it uses xulrunner. Makes it fit very nicely with the rest of the DE.

---

### Post by pbpersson on 2008-03-19
I gave up on Firefox like two days ago.  Now I am using Opera.  I don't need to do anything fancy like videos or flash, I just want to read the news, check the weather, read/write email.  Firefox was crashing several times a day and I said "in the Linux world with all the choices I have, I sure don't need to deal with this nonsense"  :(

---

### Post by verb3k on 2008-03-19
Mozilla is an American corporation, so crashes to be expected :lolflag:
(joking :))

---

### Post by daengbo on 2008-03-19
I've attached a screenshot of the "black box" behavior, as requested by another poster. It's quite random. The jpeg on the right renders, but the one on the left doesn't. Clicking the linkshows the image correctly, though. There are also instances of the image being improperly placed, filling only the top half of the box, or other images from cache (not related to the page) appearing in random spots.

---

### Post by SirBismuth on 2009-07-10
There is virtually nothing I don't like about Firefox, in any OS.  

What I cannot stand, is the friggin' download window that pops up every time I initiate a download.  It's not too bad when doing one file, but drives me to distraction with multiple downloads.

What does alleviate this considerably, is an addon called DownThemAll!.  Much less intrusive, and it uses MD5 Checksums where available.

Otherwise wouldn't choose any other browser.

B

---

