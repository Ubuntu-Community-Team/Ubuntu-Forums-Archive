---
title: "is firefox dying?"
date: 2010-07-27
forum: Recurring Discussions
---

### Post by chris200x9 on 2010-07-27
I recently did some sunspider benchmarks against the latest stable chromium. I found chromium to be nearly 3x faster than firefox 3.6.8 and 2x as fast as firefox 4.0 beta 1. The exact benchmarks are linked to on my blog. I know firefox 4 is beta software and should not be bench-marked but 2x is still ALOT! With vp8 coming to chromium in 6.0 and it being FOSS, has firefox lost or is loosing it's usefulness?

---

### Post by phrostbyte on 2010-07-27
Firefox JS performance has shown constant improvement from release to release. Even though it trails Chromium, if you put it against JS engines from 3 years ago, it would probably win by a sizable margin. :)

---

### Post by pinguy on 2010-07-27
I am still a very fond user of Firefox because you can make it very personal to you. I really not that bothered about speed. As long as web pages load and it doesn't take forever I will stay loyal to Mozilla.

It's going to get to a point where speed is redundant. If a page loads faster then I can blink does it really matter that another browser can load a page 3x faster? As a user I am not going to notice the difference in the speed.

I will always choose ability to do what I like to my browser and a nice user-interface over speed.

---

### Post by Dustin2128 on 2010-07-27
In before moved to recurring :) The hallmark of firefox is and always will be its customizability. Case in point, [chrome frame]("https://addons.mozilla.org/en-US/firefox/addon/8740/"). Not availble for linux users but we would want chrom***ium*** frame anyway :). Point is, even if firefox 4's speed tests all fail, we can intermix it with other browsers to bring up performance if we want to keep our addons. Although that would be pretty pathetic; if I had to do that to maintain acceptable speed, I'd swap full time to chrome or opera.

---

### Post by chris200x9 on 2010-07-27
> **phrostbyte said:**
> Firefox JS performance has shown constant improvement from release to release. Even though it trails Chromium, if you put it against JS engines from 3 years ago, it would probably win by a sizable margin. :)

True but that is a poor excuse, so you have windows it blows linux away but you say well linux blows away older operating systems? I personally feel yes firefox is dying. Why? Chrome is blazing fast and getting adopted super quick, soon google won't need to pay anyone, they will have majority marketshare. At that time I think ff will become abandonware.

---

### Post by SunnyRabbiera on 2010-07-27
> **chris200x9 said:**
> True but that is a poor excuse, so you have windows it blows linux away but you say well linux blows away older operating systems? I personally feel yes firefox is dying. Why? Chrome is blazing fast and getting adopted super quick, soon google won't need to pay anyone, they will have majority marketshare. At that time I think ff will become abandonware.

when pigs fly, Chromes session restore is nowhere near that of tab mix plus and customization and integration are miles off from firefox.

---

### Post by Spr0k3t on 2010-07-27
I completely agree that chrome is hella fast.  However, it doesn't fit.  The browser looks like a red-headed step child with every other productivity app using a GTK or QT framework on a gnome system.  I've tried to make it fit by changing the settings but it just feels so out of place.  I use it when testing html5/canvas sites... for everything else it's firefox.

---

### Post by Mr. Picklesworth on 2010-07-27
> **SunnyRabbiera said:**
> when pigs fly, Chromes session restore is nowhere near that of tab mix plus and customization and **integration** are miles off from firefox.

The others I can agree with, but on integration I very much disagree. Chromium uses straight GTK+ for its user interface. The main UI overrides all the drawing functions for distinctive look, sure, but in terms of functionality, even the unusual looking part is very consistent with the rest of the desktop. (Eg: scroll to switch tabs).
Firefox is somewhat the opposite: it uses its own XUL toolkit, calling Gtk's drawing functions via a somewhat clever but ultimately horrific offscreen drawing method that is responsible for the UI being sluggish (and, at times, ugly).

Any dialogs in Chromium use straight GTK widgets that have not been tampered with. You'll notice that it uses proper tooltips, for example, and right clicking behaves like everything else on the desktop. (Menu appears as soon as the button is pressed, menu is closed as soon as the button is released if it was being held down, and it's a proper menu). The context menu for every text field has the standard text field options like Input Methods. (Can you even use alternative input methods in Firefox?!)

It also (soon) will use Gnome Keyring to store passwords, it cares about global proxy settings, it opens downloaded files properly (instead of maintaining its own wildly incorrect list of file / application associations), there was serious discussion about using libnotify for that fancy new web notifications feature (and there's interest in getting to that point), and it stores its settings according to the [XDG user dirs specification]("http://www.freedesktop.org/wiki/Software/xdg-user-dirs"). When I drag / drop a link or a bookmark, I get a .desktop file (linking to it the right way), and there is a "Create Application Shortcuts" feature that adds said shortcuts straight to your applications menu (or desktop, if you're so inclined), again using a properly formatted .desktop file.
Google obviously really cares about their Linux version. That makes sense, given ChromeOS and their internal use of Ubuntu.

All in all, Chromium is becoming the perfect web browser for any distro to ship by default, because it doesn't behave differently from anything else in the environment. The interactions people get used to in Chromium they can use elsewhere in Ubuntu, and vice versa.


So, yeah, I think Firefox is doomed to become the emacs of web browsers unless they take integration more seriously. (Not that there's anything wrong with emacs). They're doing good stuff with FF 4 and it looks like they're moving away from the very foolish &#8220;one size fits all&#8221; philosophy they had before. Still a lot of work to be done.

They could learn a lot from Chromium, whose simplicity has allowed for much better performance and integration with its target platforms. Sure, extensions can't bend the entire user interface like in Firefox, but that means Chromium doesn't have its own special UI toolkit; it uses whatever is native to its target platform and it's free to change that at any time without breaking anything.

Chromium is *beautifully* robust that way. They can rapidly add platform-specific code to make the browser better for each individual target. The end result is awesome.

---

### Post by smellyman on 2010-07-27
bah.  benchmarks shemnchmarks.  Real world brwosing it isn't a a big deal to me.
 
Until Chromium/ome looks better, uses less RAM and gets text zoom only, I'll pass on the google hype.

---

### Post by ubunterooster on 2010-07-27
It *works* but has so few options... I like Icecat, firefox, and Iceweasel for those infinite options

---

### Post by chris200x9 on 2010-07-27
> **SunnyRabbiera said:**
> when pigs fly, Chromes session restore is nowhere near that of tab mix plus and customization and integration are miles off from firefox.

now that is: [http://www.taranfx.com/google-chrome-6-7-8-release](http://www.taranfx.com/google-chrome-6-7-8-release) I mean is mozilla gonna get left behind? How small of a marketshare is worth $50 million?

---

### Post by pinguy on 2010-07-27
As I probably spend most of my time in the browser I have got quite a few add-ons and scripts now for Firefox for doing all sorts of things.
When I am using chromium *(as many of the add-ons I use there isn't a chromium version)* I feel like I am surfing the web with one arm tied behind my back.
Plus chromium looks awful. Who wants to use a browser that looks like a fisher price toy? 

Chromium for me is no were near as good as Firefox. I really don't care how fast it is, if I want speed I will use Opera.

---

### Post by handy on 2010-07-27
Many people greatly prefer the Firefox GUI to the opposition. This apart from anything else will keep a very large Firefox following I think.

---

### Post by chriswyatt on 2010-07-27
Yeah, most people won't care that Chrome/Chromium is faster.  That is until HTML5 / Javascript becomes more and more demanding which I'm sure it will, though by then Firefox may have caught up.  At the moment Firefox is rubbish at running the HTML5 / Javascript demos I've chucked at it compared to Chrome, haven't tried Firefox 4 yet though.

I tried introducing Chrome to my dad, but he ended up going back to Firefox.  He prefers the GUI, he doesn't care if it runs slightly faster and probably didn't even notice.  Most people won't care, people stuck with Internet Explorer and that's a turd of a browser.

---

### Post by collinp on 2010-07-27
Firefox is far from dying or dead. It's still one of the biggest browsers out there, second only to Internet Exploder.

Firefox is older, has more extensions, has a bigger user base, and probably has a bigger development team.

Chrome is fast, but that's about it. I've had crash issues with Chrome before. It also has fewer users, and less support.

Chrome/Chromium are absolute, complete, and utter RAM hogs. I compared Chrome and Chromium to Firefox on Linux - Chrome and Chromium both managed to use all of my 1GB of RAM with the same number of tabs as Firefox had open.

If you're wondering where I'm pulling my statistics from, here are a few sources:

[LIST]
[*][http://weblogs.mozillazine.org/asa/archives/2010/05/for_every_new_user_o.html](http://weblogs.mozillazine.org/asa/archives/2010/05/for_every_new_user_o.html)
[*][http://www.w3schools.com/browsers/browsers_stats.asp](http://www.w3schools.com/browsers/browsers_stats.asp)
[*][http://www.netmarketshare.com/browser-market-share.aspx?qprid=0](http://www.netmarketshare.com/browser-market-share.aspx?qprid=0)
[*][http://www.axiis.org/examples/BrowserMarketShare.html](http://www.axiis.org/examples/BrowserMarketShare.html)
[*][http://gs.statcounter.com/](http://gs.statcounter.com/)
[/LIST]

---

### Post by gradinaruvasile on 2010-07-27
Well in theory its true but ive seen Chromium on low RAM/CPU machines and blows Firefox away.
Not with memory usage but with speed - firefox starts forever, Chromium in a blink. With Firefox the computer crawls when switching tabs, Chromium does it in a blink of an eye. Firefox starts crashing at ~10 tabs when opening new tabs/closing older tabs.
Once i seen 100 (!) tabs open in Chromium and it worked and did not crash when closing about 80-90 of them.
The above examples i have seen om my wife's Dell C640 laptop with P4@1800 CPU and 512 MB RAM while she was working (at least half of those tabs had flash objects on them).
Chromium was the buildbot one (generic Linux build), Firefox the latest 3.6 generic Linux build from their site. OS: Ubuntu 8.10.

But yes, you are right, Firefox used less memory (until it crashed that is...).

---

### Post by odiseo77 on 2010-07-28
I haven't used chrome thoroughly, maybe because I can't stand it for a long time, but in spite the fact that I find it faster than firefox, I think firefox has more functions and is more comfortable to use. And, since nowadays browsers have tabs, there's no need to open new windows very often, and hence, the initial speed is not so important (at least for me).

---

### Post by Paqman on 2010-07-28
Firefox isn't dying yet, but it has ceased to grow. For a browser that was gaining new users like clockwork that's a sign of real change. Chrome has been hugely successful, while IE's percentage continues to fall. Personally I interpret that as Chrome cannibalising a fair number of Firefox users, while IE users continue to switch to both Chrome and Firefox.

---

### Post by Perfect Storm on 2010-07-28
> **Spr0k3t said:**
> I completely agree that chrome is hella fast.  However, it doesn't fit.  The browser looks like a red-headed step child with every other productivity app using a GTK or QT framework on a gnome system.  I've tried to make it fit by changing the settings but it just feels so out of place.  I use it when testing html5/canvas sites... for everything else it's firefox.

Really?

[[img]http://artificial-intelligence.smugmug.com/Computers/Ubuntu-Linux-OS/PreScreenshot/950204992_ygZtZ-X3.png[/img]](http://artificial-intelligence.smugmug.com/Computers/Ubuntu-Linux-OS/Screenshot/950205013_TN3dM-X3.png)

---

### Post by earthpigg on 2010-07-28
> **Artificial Intelligence said:**
> Really?

details on what you have done to my beloved gnome-panel?

---

### Post by Perfect Storm on 2010-07-28
> **earthpigg said:**
> details on what you have done to my beloved gnome-panel?

I've used gnome-applet-globalmenu

---

### Post by murderslastcrow on 2010-07-28
Let's see- if Internet Explorer still has so many users, and people are so familiar with Firefox anyway, I don't think it will die. However, tech savvy users, even those crazy about extensions, may start asking themselves when confronted with Chrome/Chromium, "why not?" And just leave.

Until they started doing more broad advertising, Mozilla's Firefox was basically used among the few intelligent people who picked up on it. I don't think it's going away any time soon- they will improve just like everyone else who's catching up.

Personally, until one of these browsers supports KDE fully so I can enjoy consistency with my radial gradients and rounded menus, I'll probably just ignore them. The beauty of Linux is that I don't really need a certain application due to work on open standards.

---

### Post by v1ad on 2010-07-28
firefox 4.0 is coming out btw.

---

### Post by JustinR on 2010-07-28
I hope Firefox dies out. Its ugly - and slow. To me.

I don't like Chrome - I don't mind it's existance but its clunky and a RAM hog.

I prefer Opera. Its fast and uses maybe 250-300MB of RAM even if there are many tabs open. Its JS engine is also fast(er?) like Chrome's.

---

### Post by handy on 2010-07-28
> **JustinR said:**
> I hope Firefox dies out. Its ugly - and slow. To me.

I don't like Chrome - I don't mind it's existance but its clunky and a RAM hog.

I prefer Opera. Its fast and uses maybe 250-300MB of RAM even if there are many tabs open. Its JS engine is also fast(er?) like Chrome's.

:lolflag:

Obviously, anyone else's needs &/or desires are totally inconsequential to you! You are also obviously quite young, & as yet have not learned that other people & their preferences also matter.

As time goes by, your values will become more valuable. :)

---

### Post by JustinR on 2010-07-28
> **handy said:**
> :lolflag:

Obviously, anyone else's needs &/or desires are totally inconsequential to you! You are also obviously quite young, & as yet have not learned that other people & their preferences also matter.

As time goes by, your values will become more valuable. :)

Jeez calmdown!:-k

Browser Wars are nothing new - all browsers have their pros and cons. I like Opera thats all I was saying.

---

### Post by McRat on 2010-07-28
Chrome has some bugs that stop it from being my sole browser.  Like it can't open pull down menu picks on some sites.

So I run both Chrome and Firefox.

---

### Post by Grenage on 2010-07-28
There's no doubt that Chrome is a lot faster, but on all of my machines (modern spec),  they run at the same speed.  I prefer the interface and add-ons for Firefox, so I can't see myself changing any time soon.

I'd agree with a previous poster, when using Chrome I feel like I'm browsing with a hand tied behind my back.

FF will be around for a very long time, even if it becomes gimped and slow; many people just stick to what they know.

---

### Post by HappinessNow on 2010-07-28
I don't know about dying, but it is killing my computer, Firefox locks up, locks up my whole computer until I have to restart. This is not desirable or enjoyable.

For now I primarily us Canary Chrome on XP and Chromium on Peppermint Ice.

---

### Post by handy on 2010-07-28
> **JustinR said:**
> Jeez calmdown!:-k

Browser Wars are nothing new - all browsers have their pros and cons. I like Opera thats all I was saying.

:lolflag:

If there is one thing I am, it is calm. :)

My reply was to your post, no more...

---

### Post by asddf on 2010-07-28
Chrome is just better.

It's faster, looks better and from what I've seen is more secure.

---

### Post by Nick_Jinn on 2010-07-28
I dont like how minamalist Chrome is. I dont like how by default you cant change the font size like you can in firefox. Little things like that **** me off.

But I like Opera, and firefox is my second choice.

---

### Post by nrs on 2010-07-28
I can't -- well, won't -- live without NoScript. Apparently with Chrome it's not just the case that nobody has bothered to develop an equivalent extension, they can't develop an equivalent extension because it doesn't have the required infrastructure.

Otherwise I hate Firefox, I hate Gecko, and I *ESPECIALLY* hate XUL.

---

### Post by pinguy on 2010-07-28
[Enable WebGL, Direct2D Rendering In Firefox 4 Beta]("http://www.ghacks.net/2010/07/28/enable-webgl-direct2d-rendering-in-firefox-4-beta/")

---

### Post by Nick_Jinn on 2010-07-28
Yeah, you can hack it, but its just not as nice out of the box. Once you start adding stuff to it you start seeing speeds similar to firefox.

Opera is FASTER than Chrome....I think its the fastest in the world right now, isnt it? That and you can change fonts and there are tons of cool widgets. It even has a build in torrent program and you can host websites and stream videos right from your browser.

---

### Post by ubunterooster on 2010-07-28
> **nrs said:**
> I can't -- well, won't -- live without NoScript. Apparently with Chrome it's not just the case that nobody has bothered to develop an equivalent extension.
  NoScript FTW!

---

### Post by Paqman on 2010-07-28
> **nrs said:**
> I can't -- well, won't -- live without NoScript. Apparently with Chrome it's not just the case that nobody has bothered to develop an equivalent extension, they can't develop an equivalent extension because it doesn't have the required infrastructure.


There's no need for an extension, because it's built right in.

---

### Post by Nick_Jinn on 2010-07-28
Paqman....are you the developer Paqman that I heard about who worked on some pretty significant linux projects?

Sorry OT.

If Chrome just had an option out of the box to change fonts and page settings like Firefox had I would use it. For now Firefox is the default and I generally gravitate to Opera once I get settled in to a new installation.

---

### Post by Spr0k3t on 2010-07-28
> **Artificial Intelligence said:**
> Really?

[[img]http://artificial-intelligence.smugmug.com/Computers/Ubuntu-Linux-OS/PreScreenshot/950204992_ygZtZ-X3.png[/img]](http://artificial-intelligence.smugmug.com/Computers/Ubuntu-Linux-OS/Screenshot/950205013_TN3dM-X3.png)

Seriously?  You don't even see it?  Gimp, XUL, and QT fit into gnome better than what you see from the chrome browser.  Odd looking tabs, incorrect coloration on form buttons, no gradient blending... and don't get me started on the missing menu.  To me, chrome feels like I'm trying to use IE in Linux with a different rendering engine.  It's faster than snot yes... but why would I want to drive a sports car when a general utility vehicle can give me the same results with more options?

My question, besides speed, what does chrome offer that I can't get from Firefox?

---

### Post by Paqman on 2010-07-28
> **Nick_Jinn said:**
> Paqman....are you the developer Paqman that I heard about who worked on some pretty significant linux projects?


Nope, i'm just another dumb user.

---

### Post by sXeChris on 2010-07-28
There are a ton of things that you can do to your FF browser to enhance speed. Look it up online. Although if you do make some alterations it might make FF a bit unstable.

---

### Post by handy on 2010-07-28
Perhaps for people using less than mediocre hardware (I use mediocre hardware), then the browser speed thing matters?

For me on a variety of systems (both hardware & software) I don't have a problem with the speed of Ff, & as already stated somewhere... I much prefer the GUI of Ff to any other browser I have tried, by far in some instances.

That's not to say the Chrome or Opera or whatever aren't valid browsers; it all comes down to personal choice in the end, as usual.

---

### Post by RiceMonster on 2010-07-28
I use chrome, but I don't think Firefox is dying. I still think addons are better overall in Firefox than they are in Chrome, because adons seem a little limited in terms of what they are capable of compared to Firefox.

---

### Post by Jaecyn42 on 2010-07-28
I use a little of both; but generally prefer Firefox.

While I concede Chromium's superiority in benchmark tests; Firefox seems more time-efficient overall, in my own personal,real-world browsing experience.  For example, FF's built-in Search Engine List vs. Chromium's "Search Box" extension.  If I need to quickly make 7 Wikipedia queries or perhaps lookup 4-5 different actors/films on IMDB (perhaps off of a fresh install), I find I will complete that set of tasks quicker with Firefox, despite the fact each page loaded a couple dozen ms (/ballpark) slower than in Chromium.  Obviously, YMMV, depending on what/how you browse.

I will say that FF's fate probably rests largely on [Tab Candy]("http://www.youtube.com/watch?v=1Nfx98L_nUk&feature=related").  If TC is implemented as well as Razkin's projections, it will certainly raise the bar significantly the Chromium project.  In that case, Google would either have to implement their own built-in version, taking a chunk out of their superior benchmark speeds; or leave it to independent extension developers, potentially resulting in reduced functionality and/or increased bugginess, as is the case with Search Box.

All said, I don't really see any need for either project to engage in cutthroat competition for the other's market share.  There are still plenty of untapped IE users for Mozilla and Google to divvy up between themselves. :D

---

### Post by nrs on 2010-07-28
> **Paqman said:**
> There's no need for an extension, because it's built right in.
It isn't.

---

### Post by philinux on 2010-07-28
Moved to Recurring Discussions. There's no beans to be had there either. :D

---

### Post by handy on 2010-07-28
> **philinux said:**
> Moved to Recurring Discussions. There's no beans to be had there either. :D

It's always nice to know that the people who post in the Cafe sub-forum are doing so out of the kindness of their hearts & not due to their caffeine addiction.

---

### Post by mojo risin on 2010-07-28
I don't like chrome at all. it looks ugky and it has hidden menus , a great mistake if a browser wants me to use it xD.

I like the add ons and what not on firefox and it still has a lay out as they always had, clearly defined :D

---

### Post by Simian Man on 2010-07-28
A browser's performance on some unrealistic set of Javascript benchmarks means nothing to me.  I care only that it's fast enough for my uses, and has features and customizability.  In all of those areas Firefox is the best.

Firefox may not integrate perfectly with GTK+ (ie it'd be nice if you could scroll through tabs with the mouse wheel), but it's a *hell* of a lot better than Chrome.

In that screenshot posted earlier by ArtificialIntelligence, Chrome only looks reasonable because it was unfocused.  If it had been focused, you would have seen the ugly couloured tab bar and the fact that the global menu would have been empty - because Chrome has no main menu.

---

### Post by prodigy_ on 2010-07-28
I like Firefox and its addons. Maybe it's slow in benchmarks but in real life I fail to notice any difference. Chrome/Chromium is ugly and it doesn't have some features I need.

P.S. BTW, I really despise the name of this thread. It just reeks of trolling.

---

### Post by koleoptero on 2010-07-28
I prefer midori.

Why are there no opinions on other browsers like midori, rekonq, arora, etc?

---

### Post by Perfect Storm on 2010-07-28
> **Spr0k3t said:**
> Seriously?  You don't even see it?  Gimp, XUL, and QT fit into gnome better than what you see from the chrome browser.  Odd looking tabs, incorrect coloration on form buttons, no gradient blending... and don't get me started on the missing menu.  To me, chrome feels like I'm trying to use IE in Linux with a different rendering engine.  It's faster than snot yes... but why would I want to drive a sports car when a general utility vehicle can give me the same results with more options?

My question, besides speed, what does chrome offer that I can't get from Firefox?

Actually I think it fit nice, especially with Elementary themes. At first it bothered me with the tabs, but now I'm quite fond of it.

---

### Post by Mr. Picklesworth on 2010-07-28
> **Artificial Intelligence said:**
> Actually I think it fit nice, especially with Elementary themes. At first it bothered me with the tabs, but now I'm quite fond of it.

The trick is they aren't tabs in the traditional sense; they are open web pages, and you can drag them around however you want ;)
Think of it like a dock. Docky, or the window list, doesn't need a GtkNotebook widget, does it?

The popular tab bar design (as in Firefox and gedit) is horrifically broken anyway, because we are using the same widget for many different purposes. A multi-document interface is not the same as a configuration dialog with multiple pages. For the sake of good design, that needs to be accepted within the UI toolkit by offering designs specifically tuned to MDIs.

---

### Post by keithpeter on 2010-07-28
Hello All

[http://www.zotero.org/blog/standalone-zotero/](http://www.zotero.org/blog/standalone-zotero/)

I'll soon have a choice of browsers - at present when doing serious work I have to use Firefox because of add-ons/extensions/whatever Zotero is.

---

### Post by qamelian on 2010-07-28
> **asddf said:**
> Chrome is just better.

It's faster, looks better and from what I've seen is more secure.
No, it isn't "just better". I can run Chrome/Chromium for about an hour with the same mix of tabs I use in Firefox. After that, Chrome drags my PC down to a crawl. Firefox on the other hand runs just fine all day long on the same PC. For my needs, Chrome is utterly useless.

---

### Post by aysiu on 2010-07-28
Firefox isn't dying just because *you* decide you don't like it any more.

I've tried just about every browser there is out there (Firefox, Opera, Chrome, Safari, Camino, Konqueror, Internet Explorer, Lynx, Dillo, Epiphany, etc.), and I keep coming back to Firefox because it offers the kind of user experience and tab behavior that works best for me. It doesn't work best for everyone, but I haven't declared Opera, Chrome, Safari, or Internet Explorer to be "dying" just because they aren't as useful for me as Firefox.

---

### Post by ElSlunko on 2010-07-28
It's nice to have options and opinions. We're all different and have different preferences. I keep trying chromium because it's fast but there are other things that I don't like about it so I do always end up in FF for the majority of my web browsing.

There isn't one single answer for every technological need!

---

### Post by earthpigg on 2010-07-28
When is FF going to have the sandboxed tabs that Chrome has?

That's probably my #1 feature request for firefox.

---

### Post by NCLI on 2010-07-28
> **earthpigg said:**
> When is FF going to have the sandboxed tabs that Chrome has?

That's probably my #1 feature request for firefox.

I believe that's on-track for Firefox 4.

---

### Post by Twitch6000 on 2010-07-28
> **phrostbyte said:**
> Firefox JS performance has shown constant improvement from release to release. Even though it trails Chromium, if you put it against JS engines from 3 years ago, it would probably win by a sizable margin. :)

Which doesn't matter it isn't three years ago. It is now. Firefox has lost its flare (well it has been lost since 1.x,but oh well).

There are newer more stable and speedy web browsers today. Opera and Google Chrome.

---

### Post by oldsoundguy on 2010-07-28
> **NCLI said:**
> I believe that's on-track for Firefox 4.


Yep .. it is in FF 4 .. and beta 2 was released today (or maybe yesterday .. depending on your time zone)

Sandboxing is the one thing I am looking forward to.  Hate it when one site hangs up the whole browser and you have to re start the browser or even go so far as a quick reboot to correct the problem. (just happened to me in FF as a matter of fact!)(social networking sites DO suk in that aspect!!)

---

### Post by pithdillinja on 2010-07-28
For a while I tried to use Firefox instead of chrome for old times sake - you know, before chrome was even released. Firefox started to take longer to open, it looked bad, I couldn't get a good webpage resolution, too much stuff everywhere - I just couldn't adjust. Just the other day I switched to chrome and I have been happy since. 

My only issue with chrome is the lack of an auto scroll (middle click) function - but I believe that's because it uses pure GTK+ and GTK+ doesn't really seem to have much of one either.

---

### Post by NCLI on 2010-07-28
> **Twitch6000 said:**
> Which doesn't matter it isn't three years ago. It is now. Firefox has lost its flare (well it has been lost since 1.x,but oh well).

There are newer more stable and speedy web browsers today. Opera and Google Chrome.
What does it matter that they're faster!!!???? Firefox renders pages on my dual-core laptop faster than I blink my eyes it won't be long beore this is also true for netbooks, why do you need that extreme speed???
> **pithdillinja said:**
> For a while I tried to use Firefox instead of chrome for old times sake - you know, before chrome was even released. Firefox started to take longer to open, it looked bad, I couldn't get a good webpage resolution, too much stuff everywhere - I just couldn't adjust. Just the other day I switched to chrome and I have been happy since. 
You know that you can remove the various bars to free space in Firefox, right? Also, Firefox takes 10 seconds to open on my netbook, is that really so terrible?
> My only issue with chrome is the lack of an auto scroll (middle click) function - but I believe that's because it uses pure GTK+ and GTK+ doesn't really seem to have much of one either.
That's got nothing to do with GTK. If the Chrome developers wanted to implement middle-click functionality, they could.

---

### Post by aysiu on 2010-07-28
> **NCLI said:**
> What does it matter that they're faster!!!???? Firefox renders pages on my dual-core laptop faster than I blink my eyes it won't be long beore this is also true for netbooks, why do you need that extreme speed??? Yes, if rendering speed differences aren't noticeably to the human eye and we need benchmarks to tell the difference between browser speeds, at that point, I don't consider "faster" to be a factor in my browser choice.

Firefox is fast enough for me, so what I really care about is the interface and behavior, and the interface and behavior of Chrome and Opera just don't work for me.

Use what works for you. If Chrome works for you, great. It doesn't work for me.

---

### Post by chris200x9 on 2010-07-28
> **aysiu said:**
> Yes, if rendering speed differences aren't noticeably to the human eye and we need benchmarks to tell the difference between browser speeds, at that point, I don't consider "faster" to be a factor in my browser choice.

Firefox is fast enough for me, so what I really care about is the interface and behavior, and the interface and behavior of Chrome and Opera just don't work for me.

Use what works for you. If Chrome works for you, great. It doesn't work for me.

Well, just because each render html pages faster than you can blink does little when dealing with alot of javascript. If we do actually see a vast migration to html5 canvas and javascript like some say it will matter very much.

---

### Post by Simian Man on 2010-07-28
> **chris200x9 said:**
> Well, just because each render html pages faster than you can blink does little when dealing with alot of javascript. If we do actually see a vast migration to html5 canvas and javascript like some say it will matter very much.

Then "some day" I may care about Firefox's JavaScript performance.  As it is now, FF is more than fast enough for the web apps I use.

---

### Post by ElSlunko on 2010-07-28
> **chris200x9 said:**
> Well, just because each render html pages faster than you can blink does little when dealing with alot of javascript. If we do actually see a vast migration to html5 canvas and javascript like some say it will matter very much.

In how many years and how relevant will this discussion be then.

---

### Post by RabbitWho on 2010-07-28
argggggggggghhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhh i can't even post a screenshot anymore...

---

### Post by khelben1979 on 2010-07-28
Google Chrome has bugs which did not pop up on my Firefox browser and I compare against the latest stable version of Firefox. That's not acceptable in my opinion, so unless they sort them out, I don't see why I would leave Firefox.

Browser speed is good, but when most people eventually got hex core cpu's at home, I'm not really sure how important this will be compared to lack of features.. :-k

*B.t.w. this post is written on my old Powerbook Lombard which uses Debian 6.0 "Squeeze" and I feel that the speed of the browser really outperforms that of what I could install on MacOS 9.2.1 when I tried out Netscape 6.02. Linux performs faster on older hardware and it's nice to be able to use modern software in the process. **Linux is simply the best!***

---

### Post by ubunterooster on 2010-07-28
> **RabbitWho said:**
> argggggggggghhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhh i can't even post a screenshot anymore...
Sweet

---

### Post by Ast_risk on 2010-07-29
I use and am happy with Firefox 4 beta, and I sense no difference in speed between Firefox and Chrome, but I don't like Chrome's GUI. I guess whatever works with different people, that's what they should use.

---

### Post by lovinglinux on 2010-07-29
I have spent the last two days testing extensions on Firefox 4 and when I come back to the forums looks like the Chrome Brigade is more active than ever. One thread is asking if Firefox is dying and the other is asking when it will be replaced on all major distros. Seriously? I guess I will make a new Chrome extension called "Reality Check". Should be included by default with Chrome :)

This thread is too long and I'm tired of arguing why Firefox is way much better than Chrome. But the quote below describes my feeling about Chrome pretty well:

> **pinguy said:**
> As I probably spend most of my time in the browser I have got quite a few add-ons and scripts now for Firefox for doing all sorts of things. When I am using chromium *(as many of the add-ons I use there isn't a chromium version)* I feel like I am surfing the web with one arm tied behind my back. Plus chromium looks awful. Who wants to use a browser that looks like a fisher price toy? 

Chromium for me is no were near as good as Firefox. I really don't care how fast it is, if I want speed I will use Opera.

Just to let the Chrome users dreaming about customization, here is the screenshot of my Firefox 4 new look. BTW, look closely at the statusbar.

[http://ubuntuforums.org/attachment.php?attachmentid=164878&d=1280388560](http://ubuntuforums.org/attachment.php?attachmentid=164878&d=1280388560)

---

### Post by sikander3786 on 2010-07-29
That is always a matter of choice until there are not much differences in performance.

Chrome is light, lighter that any Firefox version. It has a different GUI, better at least thats what I feel.

I sense that what Firefox did to IE, now it is going to happen to Firefox itself by Chrome. A lot of guys jumping in and developing extensions, the library of Chrome, if not rising above Firefox, will be able to equal it in a few months I believe.

Stability is always an issue. Google Chrome was not that much stable when I tested it a few months ago on Windows 7 (I don't remember which version), but now it is rock solid.

Firefox vs Internet Explorer vs Google Chrome = Benefit of the internet users.

Regards.

---

### Post by Grenage on 2010-07-29
Competition is always healthy, and it really emphasises the importance of standards.

New applications frequently appear, with the advantage of being 'new code'.  Because of this, they are often lean and snappy; maintaining that form over the years is the hard part.

---

### Post by ElSlunko on 2010-07-29
I don't think it's quite like IE vs Firefox. FF was a great alternative because it had a few features that IE didn't as well as less security holes (at the time anyways, not sure how it compares now).

So IE had to do some catching up with FF. The main differences between FF & Chrome seem to be performance. I'm not sure how it differs from a developers point of view because I'm not remotely close to a dev, but from a users standpoint there's a few things I can do in FF that I can't do in Chrome, and nothing in Chrome I can't do in FF4.

---

### Post by earthpigg on 2010-07-29
> **lovinglinux said:**
> 
Just to let the Chrome users dreaming about customization, here is the screenshot of my Firefox 4 new look. BTW, look closely at the statusbar.

[http://ubuntuforums.org/attachment.php?attachmentid=164878&d=1280388560](http://ubuntuforums.org/attachment.php?attachmentid=164878&d=1280388560)

just to clarify, it adheres to normal window manager conventions prior to everything you customized there... right?

---

### Post by lovinglinux on 2010-07-29
> **sikander3786 said:**
> I sense that what Firefox did to IE, now it is going to happen to Firefox itself by Chrome. A lot of guys jumping in and developing extensions, the library of Chrome, if not rising above Firefox, will be able to equal it in a few months I believe.

No way. 

Firefox = 5 years + 6000 extensions + 2 billion extensions downloads

Besides, compare similar Firefox extensions with Chrome to see the difference.

---

### Post by lovinglinux on 2010-07-29
> **earthpigg said:**
> just to clarify, it adheres to normal window manager conventions prior to everything you customized there... right?

I'm not sure if I follow your question. This is Firefox on KDE 4.4 with QtCurve Klearlooks style. The only thing unconventional I did was to install [a Firefox theme]("https://addons.mozilla.org/en-US/firefox/addon/162069/") for Windows only, which was supposed to look like the image below. The rest is the built-in customization of Firefox combined with extensions.

[IMG]https://addons.mozilla.org/img/uploads/previews/full/46/46111.png?modified=1277825841[/IMG]

---

### Post by smellyman on 2010-07-29
The google PR and name recognition is strong.  It even affects Linux users.
 
 
I fixed a guys windows laptop once and he went to youtube and there was an ad to download Google Chrome and it said it makes the internet faster....or something like that.
 
He asked if he had to download it.  I said no it's just a different kind of browser but he can try it if he wants to.
 
His response:  "but isn't the Google the internet?"

---

### Post by pinguy on 2010-07-29
Chrome is the ugly retarded love child of Firefox and Opera that should of been left in the dumbster.

Chrome wants to be able to be as customizable as Firefox, but its not. It also wants to be as fast as Opera, but its not.

Choice is a good thing because it forces other browsers to become better but Chrome isn't better at anything. [I](not anymore)
[/I]

I really don't see what everyone sees in it :confused:
Chrome maybe good when HTML5 becomes the norm, but at the moment it's like that guy who went out and bought a 2 grand HD-TV before HD was the norm and telling you how great it was. Only to find out a couple of years later that it didn't have any HDMI sockets.

---

### Post by ubunterooster on 2010-07-29
My older sister uses Chromium because she "can understand it".

---

### Post by Nick_Jinn on 2010-07-29
I bet the best operating system has not been developed yet. It will probably render images in 3d.

---

### Post by sikander3786 on 2010-07-29
> **lovinglinux said:**
> No way. 

Firefox = 5 years + 6000 extensions + 2 billion extensions downloads

Besides, compare similar Firefox extensions with Chrome to see the difference.


Hmmmm. Let's see. I bet and hope to see lots of lots of extensions for Chrome in the near future. And what do you think will happen once Google releases Chrome OS? Wouldn't that help the Chrome browser itself?

---

### Post by sikander3786 on 2010-07-29
> **Nick_Jinn said:**
> I bet the best operating system has not been developed yet. It will probably render images in 3d.

The best operating system has not been developed yet at least I do agree. The one that renders 3d images might be the best one as far as we can dream now. But once it gets developed the expectations would have raised to such a level that users at that time will be dreaming of something even better.

Might be they dream of wearing a helmet, think of a website or a local file and view it on the screen. :p

---

### Post by endotherm on 2010-07-29
> **chris200x9 said:**
> I recently did some sunspider benchmarks against the latest stable chromium. I found chromium to be nearly 3x faster than firefox 3.6.8 and 2x as fast as firefox 4.0 beta 1. The exact benchmarks are linked to on my blog. I know firefox 4 is beta software and should not be bench-marked but 2x is still ALOT! With vp8 coming to chromium in 6.0 and it being FOSS, has firefox lost or is loosing it's usefulness?
ummm, no. there is no replacement. opera is not sufficiently supported, chrome is spyware, and safari/IE are bad jokes. so no, ff better not be dying, as it is the only browser in its class.

---

### Post by lovinglinux on 2010-07-29
> **sikander3786 said:**
> Hmmmm. Let's see. I bet and hope to see lots of lots of extensions for Chrome in the near future. And what do you think will happen once Google releases Chrome OS? Wouldn't that help the Chrome browser itself?

Chrome extensions are not the same thing as Firefox extensions. To be honest I haven't explored the Chrome extension API in much detail, but from what I have seen and from my experience with Firefox extensions that were ported to Chrome, it seems Chrome extensions are very limited. For instance, you can't modify the browser UI. Below you can see a screenshot of an extension I'm developing for Firefox, that allows to organize, manage and view videos, music and games from Firefox's sidebar. You can't do that in Chrome because it doesn't have a sidebar and it doesn't allow much flexibility in regard to UI modification. So is not a matter of time, but what the extension API and the browser can provide for the developers.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=164907&stc=1&d=1280428468[/IMG]

---

### Post by ElSlunko on 2010-07-29
Before judging where firefox is headed as far as the graveyard goes one should definitely check out the new beta.

---

### Post by Bachstelze on 2010-07-29
Not until the fat lady sings and Oracle buys Mozilla.

---

### Post by NMFTM on 2010-07-29
[QUOTE=pinguy;9652621Choice is a good thing because it forces other browsers to become better but Chrome isn't better at anything. *(not anymore)*[/QUOTE]
As a hardcore Firefox fan who has no plans of switching to Chromium I have to disagree. Chromium sandboxes each tab as a separate process. Which greatly improves stability. One website in one tab crashing won't take down the entire browser. It's such a great feature that Mozilla not only plans to implement it in Firefox but is also taking much of the code necessary to do so directly from Chromium.

---

### Post by Grenage on 2010-07-30
> It's such a great feature that Mozilla not only plans to implement it in Firefox but is also taking much of the code necessary to do so directly from Chromium.

Assuming that's true, it's another fine example of why people should spend more time encouraging or helping in diversification, and less time being fanboys.

---

### Post by pinguy on 2010-07-30
> **NMFTM said:**
> As a hardcore Firefox fan who has no plans of switching to Chromium I have to disagree. Chromium sandboxes each tab as a separate process. Which greatly improves stability. One website in one tab crashing won't take down the entire browser. It's such a great feature that Mozilla not only plans to implement it in Firefox but is also taking much of the code necessary to do so directly from Chromium.

That's really good, so Chromium *is* bringing something new to the table.
After reading that I do remember reading that somewhere before about sandboxes, but tab browsing in Chromium is still pretty poor tho, but again it's not great in Firefox either. There both pretty memory hungry when you have a few tabs open.

---

### Post by Shpongle on 2010-07-30
Its losing market share to chromium but its still unmatched in terms of extensions , IMO chromiums extensions are terrible , the adblockers load the ads first and then remove them, youll see this if your on a fast connection. Its the same story for user scripts the page loads and then the script is applied. the fact you can tweak ff to your hearts content and all the great addons like noscript and abp , makes it hard for many of us to just drop it, the speed will get better with time but as long as its not crawling along il continue to use it

---

### Post by endotherm on 2010-07-30
> **Shpongle said:**
> the adblockers load the ads first and then remove them, youll see this if your on a fast connection. 
seriously? I wonder if that is so the page makes money (because the ads were loaded) but relieves the user of having to look at them. that would be best-of-both-worlds, if they could make it work at wirespeed.

---

### Post by Mr. Picklesworth on 2010-07-30
> **endotherm said:**
> seriously? I wonder if that is so the page makes money (because the ads were loaded) but relieves the user of having to look at them. that would be best-of-both-worlds, if they could make it work at wirespeed.

It was a technical limitation, now resolved in newer Chromium and the latest [AdBlock extension]("https://chrome.google.com/extensions/detail/gighmmpiobklfepjocnamgkkbiglidom").
(Not much need for it, though. Not being slowed down by ads is one of those nice side-effects of having a fast, responsive web browser :b).

---

### Post by Shpongle on 2010-07-30
> **Mr. Picklesworth said:**
> It was a technical limitation, now resolved in newer Chromium and the latest [AdBlock extension]("https://chrome.google.com/extensions/detail/gighmmpiobklfepjocnamgkkbiglidom").
(Not much need for it, though. Not being slowed down by ads is one of those nice side-effects of having a fast, responsive web browser :b).

true but it still saves bandwidth , we get enough ads on buses, tv , billboards radio. I like having an ad free experience on the net.

---

### Post by endotherm on 2010-07-30
> **Shpongle said:**
> true but it still saves bandwidth , we get enough ads on buses, tv , billboards radio. I like having an ad free experience on the net.
I have to agree, but i get torn when dealing with sites like ars, since i do want to support what they do, but I don;t want to have to reconfigure noscript and adblock based on whether i like a site or not. that just seems silly. same with sourceforge and codeplex.

---

### Post by CuXe on 2010-07-30
I was a die-hard firefox fan because of all of its plugins but since more and more of those plugins are being made available for Chrome/Chromium browsers and the fact that Chrome based browsers which are hella fast, even with a boatload of tabs open, I was highly motivated to move over.

I have found replacements for almost all of the plugins I used in FF including a website screenshot plugin, url shortener, notepad, roboform (big one right thur), session manager, firebug!, proxy switching app, bookmarking sync extension... U name it!

I may go back to FF and IE but only for cross-browser testing and thats about it.

---

### Post by lovinglinux on 2010-07-31
See the death of Chrome starting with [Firefox's TabCandy]("http://ubuntuforums.org/showthread.php?t=1542777").

---

### Post by HappinessNow on 2010-07-31
> **lovinglinux said:**
> See the death of Chrome starting with [Firefox's TabCandy]("http://ubuntuforums.org/showthread.php?t=1542777").it's boring...I'm sticking with Chrome.

Even Tab Candy can not revive Firefox ;)

---

### Post by lovinglinux on 2010-07-31
> **HappinessNow said:**
> it's boring...I'm sticking with Chrome.

Even Tab Candy can not revive Firefox ;)

:lol:

You say that until you try it ;)

---

### Post by smellyman on 2010-07-31
> **HappinessNow said:**
> it's boring...I'm sticking with Chrome.

Even Tab Candy can not revive Firefox ;)

Kind of odd thing to say.

If you want boring....I give you Chrome.

---

### Post by kajankow on 2010-07-31
See I switch between the two. I like stumble upon and I use firefox for that because of the channels. I also use firefox for just a few other things like downloads maybe but I do that between the two browsers. I use chrome for online banking and looking at pictures and stuff because for me it seems I get more screen in chrome. Not bothered by the title bar, toolbar, etc. But that is just me.

---

### Post by HappinessNow on 2010-08-01
> **kajankow said:**
> See I switch between the two. I like stumble upon and I use firefox for that because of the channels. I also use firefox for just a few other things like downloads maybe but I do that between the two browsers. I use chrome for online banking and looking at pictures and stuff because for me it seems I get more screen in chrome. Not bothered by the title bar, toolbar, etc. But that is just me.Stumble Upon works in Chrome as well: [http://goo.gl/rn5g](http://goo.gl/rn5g)

---

### Post by AllenGG on 2010-08-01
Chrome and Opera are much faster than Firefox.......................
............................................................................................in Windows XP
Opera is a joke.   Chrome is fast, but confusing. And it lacks , mucho.
now Ephiphany, that&#347; fast , but also lacking. 
Firefox is bloated, because we all demanded the features.  
yes, we discovered the enemy and
they is us.

---

### Post by lovinglinux on 2010-08-01
> **AllenGG said:**
> Chrome and Opera are much faster than Firefox.......................
............................................................................................in Windows XP
Opera is a joke.   Chrome is fast, but confusing. And it lacks , mucho.
now Ephiphany, that&#347; fast , but also lacking. 
Firefox is bloated, because we all demanded the features.  
yes, we discovered the enemy and
they is us.

Bloated with what? You can customize Firefox to make it almost completely chromeless and if you don't bloat it yourself with extensions, then it is super fast and uses less memory than Chrome. I normally run it with 60 extensions or more, but it still performs great and uses about 150 Mb.

---

### Post by Lucifer The Dark on 2010-08-01
Be thankful we're not stuck with Intorweb Exploder or Nutscrape or even worse AOHELL!

---

### Post by mikewhatever on 2010-08-01
This is a silly thread. How can the best browser in the world be dying? Well, it sure could, but Firefox is certainly not.

---

### Post by markinf on 2010-08-01
I tried to like chrome(ium) but I can't live with firefox. Peopple it's not about rendering extension what makes fox the best browser there it's inumerous cool extensions.

Right now I'm running 14 extensions. Which almost none have a replacement on chrome(ium).

---

### Post by CuXe on 2010-08-01
^ mind telling us which add-ons are those? I have found replacements for most of FF addons and I do heavy SEO stuff.

I also found a replacement for TabCandy so Chromium is running very nice on my end :)

---

### Post by lovinglinux on 2010-08-02
> **markinf said:**
> I tried to like chrome(ium) but I can't live with firefox. Peopple it's not about rendering extension what makes fox the best browser there it's inumerous cool extensions.

Right now I'm running 14 extensions. Which almost none have a replacement on chrome(ium).

Is not just about the extensions. You can't customize Chrome interface to your liking, which seriously damage my web experience. Is not about the beauty of the browser interface, but about usability. In Firefox I have everything located where I need. For instance I have several extensions buttons that are placed on the left, because they open on the sidebar. If Chrome had a sidebar, which it doesn't, then every time I needed to open a sidebar extension I would need to go to the extension menu on the right side of the toolbar, scroll down all the buttons to find the one I want, then go all the way back to the sidebar to use it. This sound laziness, but imagine if I'm working with more than one sidebar extension simultaneously an I need to switch between them several times (which I do very frequently)? In Firefox I can optimize my workflow, in Chrome I can't. 

Basically, Chrome lock you down with what they think is the best way to interact with the browser and the web, while Firefox allows me to do the way is better for my needs.

Extensions of course play an important role in customization too, because there are tons of extensions that do not add features,  but modify Firefox interface. These can't be found in Chrome, because you can't modify Chrome interface.

Currently I have 75 extensions installed.

---

### Post by HappinessNow on 2010-08-02
> **markinf said:**
> I tried to like chrome(ium) but I can't live with firefox. Peopple it's not about rendering extension what makes fox the best browser there it's inumerous cool extensions.

Right now I'm running 14 extensions. Which almost none have a replacement on chrome(ium).please list the extensions, I am sure we can find suitable replacements for most of them.


Firefox is going down hill fast, just was using it with adblock and got 2 pop-up ads, haven't seen those since IE years ago!

---

### Post by lovinglinux on 2010-08-02
> **HappinessNow said:**
> please list the extensions, I am sure we can find suitable replacements for most of them.

Lovely. If you succeed, I promise to change my username to **lovingchrome**. To be fair, I give you 5 five years to complete the task :lol:

[AdBlock Plus]("https://addons.mozilla.org/en-US/firefox/addon/1865/")
[Add To Search Bar]("https://addons.mozilla.org/en-US/firefox/addon/3682/")
[All-in-One Sidebar]("https://addons.mozilla.org/en-US/firefox/addon/1027/")
[Bar Tab]("https://addons.mozilla.org/en-US/firefox/addon/67651/")
[BBCode]("https://addons.mozilla.org/en-US/firefox/addon/128/")
[Better Cache]("https://addons.mozilla.org/en-US/firefox/addon/6371/")
[Brief]("https://addons.mozilla.org/en-US/firefox/addon/4578/")
[ChatZilla]("https://addons.mozilla.org/en-US/firefox/addon/16/")
[Check Places]("https://addons.mozilla.org/en-US/firefox/addon/10897/")
[Compact Menu 2]("https://addons.mozilla.org/en-US/firefox/addon/4550/")
[Context Search]("https://addons.mozilla.org/en-US/firefox/addon/240/")
[Download Helper]("https://addons.mozilla.org/en-US/firefox/addon/3006/")
[Download Statusbar]("https://addons.mozilla.org/en-US/firefox/addon/26/")
[Echofon]("https://addons.mozilla.org/en-US/firefox/addon/5081/")
[Extended Statusbar]("https://addons.mozilla.org/en-US/firefox/addon/1433/")
[Favicon Picker]("https://addons.mozilla.org/en-US/firefox/addon/3176/")
[FEBE]("https://addons.mozilla.org/en-US/firefox/addon/2109/")
[Feed Sidebar]("https://addons.mozilla.org/en-US/firefox/addon/4869/")
[Firefox Sync]("https://addons.mozilla.org/en-US/firefox/addon/10868/")
[FoxTab]("https://addons.mozilla.org/en-US/firefox/addon/8879/")
[GMail Checker]("https://addons.mozilla.org/en-US/firefox/addon/3179/")
[Google Reader Watcher]("https://addons.mozilla.org/en-US/firefox/addon/4808/")
[gPDF]("https://addons.mozilla.org/en-US/firefox/addon/14814/")
[IMDB Ripper]("https://addons.mozilla.org/en-US/firefox/addon/8347/")
[KDE Wallet Password Integration]("https://addons.mozilla.org/en-US/firefox/addon/49357/")
[MeasureIt]("https://addons.mozilla.org/en-US/firefox/addon/539/")
[Menu Editor]("https://addons.mozilla.org/en-US/firefox/addon/710/")
[Mozilla Archive Format]("https://addons.mozilla.org/en-US/firefox/addon/212/")
[NoScript]("https://addons.mozilla.org/en-US/firefox/addon/722/")
[NoSquint]("https://addons.mozilla.org/en-US/firefox/addon/2592/")
[Open With]("https://addons.mozilla.org/en-US/firefox/addon/11097/")
[OPML Support]("https://addons.mozilla.org/en-US/firefox/addon/2625/")
[Organize Search Engines]("https://addons.mozilla.org/en-US/firefox/addon/4565/")
[Organize Status Bar]("https://addons.mozilla.org/en-US/firefox/addon/1759/")
[Password Exporter]("https://addons.mozilla.org/en-US/firefox/addon/2848/")
[Password Generator]("https://addons.mozilla.org/en-US/firefox/addon/12441/")
[Premium Proxy Switcher]("https://addons.mozilla.org/en-US/firefox/addon/161958/")
[Quick Restart]("https://addons.mozilla.org/en-US/firefox/addon/3559/")
[Remove It Permanently]("https://addons.mozilla.org/en-US/firefox/addon/521/")
[Scrapbook]("https://addons.mozilla.org/en-US/firefox/addon/427/")
[Screengrab]("https://addons.mozilla.org/en-US/firefox/addon/1146/")
[Secure Login]("https://addons.mozilla.org/en-US/firefox/addon/4429/")
[Selective Cookie Delete]("https://addons.mozilla.org/en-US/firefox/addon/11044/")
[ShowIP]("https://addons.mozilla.org/en-US/firefox/addon/590/")
[Speed Dial]("https://addons.mozilla.org/en-US/firefox/addon/4810/")
[SQLite Manager]("https://addons.mozilla.org/en-US/firefox/addon/5817/")
[SQLite Optimizer]("https://addons.mozilla.org/en-US/firefox/addon/11198/")
[Stylish]("https://addons.mozilla.org/en-US/firefox/addon/2108/")
[TagSieve]("https://addons.mozilla.org/en-US/firefox/addon/124046/")
[TextArea Cache]("https://addons.mozilla.org/en-US/firefox/addon/5761/")
[TinyURL Generator]("https://addons.mozilla.org/en-US/firefox/addon/10586/")
[Compress Bookmarks Bar]("https://addons.mozilla.org/en-US/firefox/addon/207644/")
[TabScope]("https://addons.mozilla.org/en-US/firefox/addon/4882/")
[Saved Password Editor]("https://addons.mozilla.org/en-US/firefox/addon/60265/")
[CheckIt]("https://addons.mozilla.org/en-US/firefox/addon/127758/")
[FLASH-AID]("https://addons.mozilla.org/en-US/firefox/addon/161939/")
[FlashVideoReplacer]("https://addons.mozilla.org/en-US/firefox/addon/161869/")
[FoxRunner]("https://addons.mozilla.org/en-US/firefox/addon/98430/")
[FoxTester]("https://addons.mozilla.org/en-US/firefox/addon/141505/")
[Umarks]("https://addons.mozilla.org/en-US/firefox/addon/13153/")

---

### Post by ElSlunko on 2010-08-02
> **HappinessNow said:**
> 

Firefox is going down hill fast, just was using it with adblock and got 2 pop-up ads, haven't seen those since IE years ago!

Disagree. Especially considering the improvements in FF4.

I mean with so many claims made in time-line form you'd have to be testing where each component of your opinion is currently headed to make that sort of assumption. So I can only assume you're beta testing FF4 too.

---

### Post by markinf on 2010-08-02
> **CuXe said:**
> ^ mind telling us which add-ons are those? I have found replacements for most of FF addons and I do heavy SEO stuff.

I also found a replacement for TabCandy so Chromium is running very nice on my end :)

Sorry for my bad english, I was kinda "drug" yersteday.

My firefox extension list:

1 Click Youtube Video Downloader - Didn't found one so intuitive on Chrome.

Adblock Plus - I found chrome version quite limited.

AutoPager - Automatically loads the next page of the website (uses a web db for the pattern). Works okay on both

BugMeNot - Login on forced authenticate websites (chrome version kinda buggy)

DownloadHelper - Addition to 1ClickYoutubeVideoDownloader - This one have a mapped version on chrome

Download StatusBar - Chrome Default

DownThemAll - My favorite extension. I don't need a download manager anymore. This one is not available on chrome :3

Firebug - Limited version on chrome.

Flagfox - Okay on both

FoxProxy - I use for justin.tv and other websites.

Mouse Gestures Redox - The compatible version to chrome is kinda non intuitive.

Tab Mix Plus - The kingdom of tabs! Didn't found a mapped/compatible version on chrome :/

Tab Scope - Preview the tabs like windows :), Not found on chrome

Xmarks - Password and Bookmark sharing. Need two or more extension to do the same on chrome (like bookmark builtin + lastpass for passwords).

---

### Post by JohnnyC35 on 2010-08-02
if there was a Chrome alternative of the Air Miles toolbar I would try it out

---

### Post by Denis Krajnc on 2010-08-18
I will stay loyal to Firefox, it's very friendly, good secured, fast. It's enough fast for me.

---

