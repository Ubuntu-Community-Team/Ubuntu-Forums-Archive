---
title: "Epiphany much faster than Firefox??"
date: 2005-09-13
forum: Recurring Discussions
---

### Post by jdong on 2005-09-13
I've been noticing phenomenal, Opera-like speeds with Epiphany 1.8.0 in Breezy.

When viewing long threads on the Forums, Firefox sometimes deadlocks for 1.5 seconds while rendering the page, sometimes even more. Note that this is on an **athlon64 3000+ with 1.5GB RAM**; not a slow system on any scale! Also, I've seen poor graphical performance with Firefox, even with the UI. Javascript alert() dialogs pop up a window border immediately, but it takes another second or two for the text and buttons to show up -- unacceptable on modern equipment like mine.


Epiphany doesn't suffer from these issues. The forums load nearly instantly; and even when they don't, I can still browse in other tabs -- the UI isn't frozen.


I'm currently comparing for a difference in the two browsers. They are using the same Gecko versions, same GCC compile flags...



It might be extensions; I'll try a clean profile and report back.

---

### Post by jdong on 2005-09-13
Alright, fresh profile, Scrags rendering time test ([http://scragz.com/tech/mozilla/test-rendering-time.php](http://scragz.com/tech/mozilla/test-rendering-time.php)) of:


Firefox: **4.60**
Epiphany: **2.42**


Both browsers were given 5 refreshes each running from the hard drive, and were awarded the lowest they got. Epiphany is nearly twice as fast as Firefox at just raw computational rendering...


Why is this?

---

### Post by jdong on 2005-09-13
The official builds (Deer Park and 1.0.6) both render in the 2.10-2.30 second area, with Deer park taking the lead (as one'd expect).


However, why exactly is Breezy's Firefox so slow?!?

---

### Post by majikstreet on 2005-09-13
Jdong,
I have experienced something out of the ordinary on my system
```

SysInfo: uname: Linux 2.6.12-8-686 CPU: Intel(R) Celeron(R) CPU 2.20GHz 2193.131 MHz Bogomips: 4341.76 Mem: 85/250M [||||||||||] Diskspace: 54.30G Free: 43.00G Procs: 63 Uptime: 6 hrs 41 mins 26 secs Load: 0.53 1.04 1.17  | Screen: Intel Corp. 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03) Screen Resolution: 1024x768 (24 bpp) wlan0: In: 116.12M Out: 9.33M

```

It takes a veeeeeeeeeeeeeery long time for epiphany to load. I have breezy by the way and I installed epiphany from the repo's...

They guy's on #epiphany on freenode have NO idea whatsoever.


majikstreet

---

### Post by jdong on 2005-09-13
Hmm, it takes a few seconds to launch Epiphany on cold boot, and it launches nearly instantly subsequenly. You have a fairly decent amount of RAM, so that's probably not it....


What's a "veeeeery long time"? What if you set the startup page to about:blank?

---

### Post by poofyhairguy on 2005-09-13
You need to prelink Epiphany.

Epiphany loads pages faster, with less CPU power used and uses less RAM overall compared to Firefox in Linux. Firefox in Linux is kinda a lame dog- its the slowest out of the Windows, Linux,OSX versions. When I know I'm going to open a lot of tabs or such (like when I researching) I always use Epiphany.

The rest of the time I use Firefox and I don't know why when its so much worse. I'm like and adict or something. I don't even adblock anymore so I don't need it. Truth be told if I could theme Epiphany to look like Firefox (or all some Gnome search bar) I would use it full time.

---

### Post by poofyhairguy on 2005-09-13
[QUOTE=jdong]
Why is this?[/QUOTE]

Because the most active version of Firefox is the Windows one. It gets the love.

---

### Post by Orunitia on 2005-09-13
I also just started using Epiphany on Breezy. It is a LOT faster than firefox, and it's not as ugly as opera.

---

### Post by bored2k on 2005-09-13
[QUOTE=poofyhairguy]You need to prelink Epiphany.

Epiphany loads pages faster, with less CPU power used and uses less RAM overall compared to Firefox in Linux. Firefox in Linux is kinda a lame dog- its the slowest out of the Windows, Linux,OSX versions. When I know I'm going to open a lot of tabs or such (like when I researching) I always use Epiphany.

The rest of the time I use Firefox and I don't know why when its so much worse. I'm like and adict or something. I don't even adblock anymore so I don't need it. Truth be told if I could theme Epiphany to look like Firefox (or all some Gnome search bar) I would use it full time.[/QUOTE]
 I use Smart Bookmars. In my humble opinion they work better than the Firefox search bar. I can type directly in the location bar and I get to search wherever I want from (Wikipedia, google, ___nova, IMDB, wherever I want from). Add to that the no toolbar option and I am a happing epiphaner.

---

### Post by jdong on 2005-09-13
[QUOTE=poofyhairguy]Because the most active version of Firefox is the Windows one. It gets the love.[/QUOTE]

Hmm, well, it's the same Gecko rendering engine, compiled with the same compiler and the same everything. Did you see my comment about official Firefox? It's faster, and actually compiled with GCC 3.3... Has GCC 4.0 really gotten that messed up?


Users of other distros, is there this significant of a difference between Firefox and Epiphany/Galeon?



There's certainly some sites that set off Firefox's slowness -- Slashdot does it on autoscroll, and the Forums does it. Since I visit the forums the most, that's kind of concerning.



Either way, I don't remember seeing THIS kind of speed gap back in Hoary days. I still feel it's abnormal.

---

### Post by majikstreet on 2005-09-13
how do i prelink epiphany?

---

### Post by poofyhairguy on 2005-09-13
[QUOTE=majikstreet]how do i prelink epiphany?[/QUOTE]


Prelink everything:

[http://ubuntuforums.org/showthread.php?t=1971](http://ubuntuforums.org/showthread.php?t=1971)

---

### Post by Curlydave on 2005-09-13
In Epiphany you can't middle-click the home button for a new tab. Bleh.

---

### Post by bored2k on 2005-09-13
[QUOTE=Curlydave]In Epiphany you can't middle-click the home button for a new tab. Bleh.[/QUOTE]
 You can middle click everything else. Hotkeys are much faster. Ctrl T for that. That is the weirdest excuse not to use it, ever-

---

### Post by xequence on 2005-09-13
I noticed epiphany was faster also. This is on my super 700 mhz 192 MB RAM speedster =O

Though epiphany just felt ackward. I have no idea why but it did. I now use opera :)

I think its because firefox is built for windows and runs best on it. Epiphany is optimized for linux or something :)

On a side note, I saw the word epiphany in my english textbook =o

---

### Post by poofyhairguy on 2005-09-13
Perfect time for this:

[http://software.newsforge.com/article.pl?sid=04/05/11/194215&tid=130&tid=79&tid=27&tid=13&tid=31](http://software.newsforge.com/article.pl?sid=04/05/11/194215&tid=130&tid=79&tid=27&tid=13&tid=31)

---

### Post by jdong on 2005-09-13
[QUOTE=xequence]
Though epiphany just felt ackward. I have no idea why but it did. I now use opera :)

I think its because firefox is built for windows and runs best on it. Epiphany is optimized for linux or something :)
[/QUOTE]

As I've said, Epiphany uses the **exact same rendering engine** (Gecko), source-identical, as the Firefox that it ships with -- it's built with firefox-dev! So "optimized for windows" is a pretty unconvincing reason.

---

### Post by xequence on 2005-09-13
[QUOTE=jdong]As I've said, Epiphany uses the **exact same rendering engine** (Gecko), source-identical, as the Firefox that it ships with -- it's built with firefox-dev! So "optimized for windows" is a pretty unconvincing reason.[/QUOTE]

I am not an expert on this, I just heard someone on ubuntufourums say that firefox works best on windows because its optimized/built for it.

---

### Post by poofyhairguy on 2005-09-13
[QUOTE=jdong]As I've said, Epiphany uses the **exact same rendering engine** (Gecko), source-identical, as the Firefox that it ships with -- it's built with firefox-dev! So "optimized for windows" is a pretty unconvincing reason.[/QUOTE]

I know, and yet it just does.

Must be magic.

---

### Post by macgyver2 on 2005-09-13
[QUOTE=poofyhairguy]Perfect time for this:

[http://software.newsforge.com/article.pl?sid=04/05/11/194215&tid=130&tid=79&tid=27&tid=13&tid=31]("http://software.newsforge.com/article.pl?sid=04/05/11/194215&tid=130&tid=79&tid=27&tid=13&tid=31")[/QUOTE]
Meh, that article is over a year old...plus the first two-thirds deals with what are, IMO, totally superficial things.  But dont get me wrong, it's a good read...thanks for the link.

May 2004 was about the last time I tried epiphany and I didn't like it...but after seeing this thread I installed it and fired it up.  I'm pretty impressed now.

---

### Post by Curlydave on 2005-09-13
[QUOTE=bored2k]You can middle click everything else. Hotkeys are much faster. Ctrl T for that. That is the weirdest excuse not to use it, ever-[/QUOTE]

Also, there's no bookmark toolbar and the back and foward buttons on my mouse won't work with it.

That being said, it does seem to load and load web pages significantly faster than firefox in Linux. (about on-par with FF in windows.)

---

### Post by psychicdragon on 2005-09-13
[QUOTE=Curlydave]Also, there's no bookmark toolbar and the back and foward buttons on my mouse won't work with it.

That being said, it does seem to load and load web pages significantly faster than firefox in Linux. (about on-par with FF in windows.)[/QUOTE]

There is a bookmarks bar... View > Bookmarks Bar > check!

---

### Post by Curlydave on 2005-09-13
[QUOTE=psychicdragon]There is a bookmarks bar... View > Bookmarks Bar > check![/QUOTE]


I saw that, but I can't figure out how to add to it. hmm.

---

### Post by jyank on 2005-09-13
I never really tried out Epiphany, but after seeing this thread I thought I would load it up and see any differences.

Running breezy with epiphany 1.8 I notice a huge speed increase over firefox (1.06) My system I wouldn't consider slow, and lots of times while tabbing in firefox, firefox locks up for a second and ctrl+t doesnt do anything, I have to give it a second.  Haven't run into that with epiphany. 

I'll keep running it for the rest of the night, and possibly start using it more often

---

### Post by psychicdragon on 2005-09-13
[QUOTE=Curlydave]I saw that, but I can't figure out how to add to it. hmm.[/QUOTE]
In the edit bookmarks window. Right click on the bookmark you want to add, there's an option to show it on the bookmarks bar. You can do the same with topics.

---

### Post by Mishura on 2005-09-14
For the stat lovers out there.  :)

Moz Firefox Test 1: 4.543
Moz Firefox Test 2: 4.163
Moz Firefox Test 3: 4.026
Moz Firefox Average: 4.244

Opera Test 1: 3.798
Opera Test 2: 3.733
Opera Test 3: 3.482
Opera average: 3.671

Konqueror Test 1: 7.826
Konqueror Test 2: 6.229
Konqueror Test 3: 6.275
Konqueror Average: 6.777

Internet Explorer 6/Wine* Test 1: 7.990
Internet Explorer 6/Wine Test 2: 8.323
Internet Explorer 6/Wine Test 3: 6.048
Internet Explorer 6/Wine Average: 7.454

*Yes, I know its emulated and stuff.  I threw that in for flavor.

Winner is Opera, by a full second.  Suprisingly, Konqueror is slow, which is odd, since it feels fast.  Then again, it does have that "lag" when launching a new site.

Test was done by going to this [site](http://scragz.com/tech/mozilla/test-rendering-time.php), and refreshing 3 times.  Caching *may* be a factor due to the fact the tests get faster by the third refresh, but not usually.  For Konqueror it went slower by a few milliseconds.

Versions used:
Firefox 1.06 (Official Mozilla.org build)
Opera 8.02 (Shared Qt libraries)
Konqueror 3.4.2
Internet Explorer 6 SP 1 on Codeweavers CXOffice 4.2

No epiphany test due to the multitude of dependencies required, that I don't want installed (Gnome's practically a dependency, as well as Firefox (Which is already installed, just not Ubuntu's)).

Oh, and I still use Firefox.  Extensions rock.  But Opera is looking nicer everytime I use it.

---

### Post by aysiu on 2005-09-14
This speed test is quite comprehensive, and it does include Epiphany:

[http://www.howtocreate.co.uk/browserSpeed.html](http://www.howtocreate.co.uk/browserSpeed.html)

---

### Post by Perfect Storm on 2005-09-14
[QUOTE=aysiu]This speed test is quite comprehensive, and it does include Epiphany:

[http://www.howtocreate.co.uk/browserSpeed.html](http://www.howtocreate.co.uk/browserSpeed.html)[/QUOTE]

Meh...But it's a bit old.

---

### Post by GreyFox503 on 2005-09-14
Is Ubuntu's Firefox (from the repositories) supposed to be slower than the regular one?

I just downloaded 1.5 Beta 1 the other day, and it not only loads the program much faster, but renders faster too.  I just thought that was because it was the new beta.

On that test page site I got 2.66 with:

Firefox 1.5 Beta 1
Hoary
AMD 2400+
512MB RAM

---

### Post by endy on 2005-09-14
[QUOTE=Curlydave]Also, there's no bookmark toolbar and the back and foward buttons on my mouse won't work with it.[/QUOTE]

I have just written a monster guide to logitech mice, part of which includes how to get the forward and back mouse buttons to work. If you have a logitech mx510 or similar. Section 2 should do the trick but if you have another mouse it could still serve as a template so you can figure out what to do :)

[http://ubuntuforums.org/showthread.php?p=350088#post350088](http://ubuntuforums.org/showthread.php?p=350088#post350088)

---

### Post by bored2k on 2005-09-14
[QUOTE=Curlydave]Also, there's no bookmark toolbar and the back and foward buttons on my mouse won't work with it.

That being said, it does seem to load and load web pages significantly faster than firefox in Linux. (about on-par with FF in windows.)[/QUOTE]Here is a screenshot of how I set my Epiphany to look. In my opinion, it has nothing envy from Firefox.

[CENTER][IMG]http://img301.imageshack.us/img301/7726/eph8sj.jpg[/IMG][/CENTER]

--------
Going back on topic, epiphany's speeds compared to Firefox's also puzzles me. However, Firefox users accustomed to having the Adblock extension installed should notice the biggest increase as Adblock itself slows down Firefox quite a bit.

---

### Post by doclivingston on 2005-09-14
That screenshot reminds me of one other cool thing that Epiphany can do: you can use *any* smart bookmark in the bookmark bar, and it will have an entry box - not just Google.

So I could (not that I do) have one to do a google search, one to do a lookup  in wikipaedia, one to serach the Ubuntu forums, one to find something on amazon.com et cetera.

---

### Post by bored2k on 2005-09-14
[QUOTE=doclivingston]That screenshot reminds me of one other cool thing that Epiphany can do: you can use *any* smart bookmark in the bookmark bar, and it will have an entry box - not just Google.

So I could (not that I do) have one to do a google search, one to do a lookup  in wikipaedia, one to serach the Ubuntu forums, one to find something on amazon.com et cetera.[/QUOTE]
 Yes. Smart bookmarks are great. I only have that toolbar but I have the Dictionary.com and the Wikipedia searches. I access them by typing what I want to search in the location bar (Ctrl+L) and selecting them. Also the new epiphany-extensions adds the option to automatically look Smart bookmarks up :D.

[[IMG]http://img301.imageshack.us/img301/7403/ha4yh.th.jpg[/IMG]](http://img301.imageshack.us/my.php?image=ha4yh.jpg)

---

### Post by weasel fierce on 2005-09-14
How do you set up the smart links ?

---

### Post by doclivingston on 2005-09-14
See [http://www.gnome.org/projects/epiphany/smartbookmarks.html](http://www.gnome.org/projects/epiphany/smartbookmarks.html)

---

### Post by bored2k on 2005-09-14
[QUOTE=weasel fierce]How do you set up the smart links ?[/QUOTE]
[http://www.gnome.org/projects/epiphany/smartbookmarks.html](http://www.gnome.org/projects/epiphany/smartbookmarks.html)
 Basically go to any website with a search option and look up "%s". Add the result given as a bookmark and make it show in the toolbar.

** Searching for %s anywhere will really search for "%25s", so just remove the "25" from the result and you're set.
[http://www.google.com/search?hl=en&q=%25s&btnG=Google+Search](http://www.google.com/search?hl=en&q=%25s&btnG=Google+Search)

---

### Post by weasel fierce on 2005-09-14
fantastic. That works really well :)

Epiphany's interface is a little odd, if you're used to firefox, but it feels very smooth to use

---

### Post by dcraven on 2005-09-14
I've been trying for the past week to use Epiphany because of the clear speed advantage. My biggest complaint with it is that the tabs are of fixed size. You can't see all tabs that are open (in Firefox, they all squeeze into the visible space). Most other differences I can handle, or I've gotten somewhat used to, but this still drives me crazy.

Is there also a way to make it do keywords? I mean like "gg searchword" in the location bar like Firefox does? I guess ultimately I probably wish it were Firefox, but faster :P

~djc

---

### Post by doclivingston on 2005-09-14
[QUOTE=dcraven]I've been trying for the past week to use Epiphany because of the clear speed advantage. My biggest complaint with it is that the tabs are of fixed size. You can't see all tabs that are open (in Firefox, they all squeeze into the visible space). Most other differences I can handle, or I've gotten somewhat used to, but this still drives me crazy.[/quote]

There was a lot of debate about this on the "should epiphany be the default in Breezy+1" thread. There are were good points for and against.

[QUOTE=dcraven]Is there also a way to make it do keywords? I mean like "gg searchword" in the location bar like Firefox does? I guess ultimately I probably wish it were Firefox, but faster :P[/QUOTE]

I've heard this is going to be an extension in 1.10; because it got done, but not in time for 1.8.

---

### Post by aysiu on 2005-09-14
[QUOTE=Artificial Intelligence]Meh...But it's a bit old.[/QUOTE] It is? I didn't see a date in there. When did it come out?

---

### Post by Perfect Storm on 2005-09-14
[QUOTE=aysiu]It is? I didn't see a date in there. When did it come out?[/QUOTE]

Saw it last year, but I should have written that, sorry.
Things may have changed since that.

---

### Post by wmcbrine on 2005-09-15
[QUOTE=bored2k]However, Firefox users accustomed to having the Adblock extension installed should notice the biggest increase as Adblock itself slows down Firefox quite a bit.[/QUOTE]On the contrary; nothing speeds up page loading more than Adblock, since you save all the time loading ads, which are often the bulkiest part of a web page (being all graphics, where the page is mostly text). Just be sure it's set to "Remove", rather than "Hide"; when on "Hide", I believe it still downloads everything.

---

### Post by jyank on 2005-09-15
I've been trying to keep with Epiphany due to the large speed increase I see, but a few minor things are making it uncomfortable for me.  If I could get these fixed, I would use it much more.

My mouse back/foward buttons don't seem to work in Epiphany, they work everywhere else.  Not having that is like going way back in time for me.

Second, I can't middle click a tab to close it, not really a big deal but that's just what I'm so used to doing.  If theres anyway to get these working, it would be convienent.

Mouse is a MX518, by the way

---

### Post by jdong on 2005-09-15
[QUOTE=wmcbrine]On the contrary; nothing speeds up page loading more than Adblock, since you save all the time loading ads, which are often the bulkiest part of a web page (being all graphics, where the page is mostly text). Just be sure it's set to "Remove", rather than "Hide"; when on "Hide", I believe it still downloads everything.[/QUOTE]

Untrue... Try loading Newegg or other sites that use hundreds of tiles of graphics or IFRAMES.... You'll see adblock easily increase loading time by factors of 10-50.

Privoxy and Dansguardian both filter more efficiently, but at a cost of convenience -- no more one-click rule modifications.

---

### Post by rjwood on 2005-09-15
my epiphany is 1.6.1 and I see the latest release is 1.7.6, can I upgrade or shoud I wait??

---

### Post by bored2k on 2005-09-15
[QUOTE=rjwood]my epiphany is 1.6.1 and I see the latest release is 1.7.6, can I upgrade or shoud I wait??[/QUOTE]
 Upgrade.

---

### Post by rjwood on 2005-09-15
[QUOTE=bored2k]Upgrade.[/QUOTE]
Thanks bored2k.. How...LOL

---

### Post by jdong on 2005-09-15
Actually, the latest on Breezy is 1.8.0, but Hoary-backports only contains 1.7.6...


Add **deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary-backports main restricted universe multiverse** to /etc/apt/sources.list, and use your favorite APT tool to perform an upgrade.

---

### Post by bored2k on 2005-09-15
[QUOTE=rjwood]Thanks bored2k.. How...LOL[/QUOTE]
 1.8 is out by the way.

[http://archive.ubuntu.com/ubuntu/pool/main/e/epiphany-browser/](http://archive.ubuntu.com/ubuntu/pool/main/e/epiphany-browser/)

This is in Breezy's repositories but I'm not sure about Hoary's. Install epiphany-extensions too.

---

### Post by jdong on 2005-09-15
SuSE 9.3's Firefox renders in 2.11 seconds, faster than Ubuntu Breezy altogether.

I'm gonna try a couple recompiles to isolate this issue. Meanwhile, I think this already deserves a bug report.

---

### Post by rjwood on 2005-09-15
[QUOTE=jdong]Actually, the latest on Breezy is 1.8.0, but Hoary-backports only contains 1.7.6...


Add **deb [http://archive.ubuntu.com/ubuntu]("http://archive.ubuntu.com/ubuntu") hoary-backports main restricted universe multiverse** to /etc/apt/sources.list, and use your favorite APT tool to perform an upgrade.[/QUOTE]
thanks guy's-----sorry to sound so stupid--I added the backport and apt-get update/upgrade and some programs upgraded but not epiphany. I dnot know what "APT" means.  sorry again. I usually am able to figure stuff out but I don't want to mess too much with sudo.

---

### Post by poofyhairguy on 2005-09-15
[QUOTE=jdong] Meanwhile, I think this already deserves a bug report.[/QUOTE]

Is it really an Ubuntu thing?

---

### Post by jdong on 2005-09-15
[QUOTE=rjwood]thanks guy's-----sorry to sound so stupid--I added the backport and apt-get update/upgrade and some programs upgraded but not epiphany. I dnot know what "APT" means.  sorry again. I usually am able to figure stuff out but I don't want to mess too much with sudo.[/QUOTE]

Sorry, my  fault... Epiphany never transitioned to the new Backports... You can add unofficial Backports, but I recommend for you to wait another two weeks for Breezy. :)

> Is it really an Ubuntu thing?

Read the bit on SuSE's firefox. Apparently Ubuntu's doing something wrong with the Firefox package :)



**P.S.** [http://bugzilla.ubuntu.com/show_bug.cgi?id=15534](http://bugzilla.ubuntu.com/show_bug.cgi?id=15534)

---

### Post by rjwood on 2005-09-15
[QUOTE=jdong]Sorry, my fault... Epiphany never transitioned to the new Backports... You can add unofficial Backports, but I recommend for you to wait another two weeks for Breezy. :)



Read the bit on SuSE's firefox. Apparently Ubuntu's doing something wrong with the Firefox package :)[/QUOTE]
Thanks j I'll wait.:smile:

---

### Post by wmcbrine on 2005-09-15
[QUOTE=jdong]Untrue... Try loading Newegg or other sites that use hundreds of tiles of graphics or IFRAMES.... You'll see adblock easily increase loading time by factors of 10-50.[/QUOTE]No way. I just loaded the Newegg front page in ten seconds (time from hitting Reload until "Done"). Disable Adblock, reload, same load time. Back and forth again, same time. If you're seeing a slowdown like that, something is wrong with your setup.

Anyway, that's not a good example, since Newegg isn't an ad-supported site (or, to look at it another way, it's one big ad), and nothing is blocked. When I try it with an ad-heavy site, I can see dramatic improvements.

---

### Post by jdong on 2005-09-15
How big is your ruleset? I'm using Filter G, and there's a significant loss of time (you have to clear your cache between tests)

---

### Post by poofyhairguy on 2005-09-15
[QUOTE=jdong]
**P.S.** [http://bugzilla.ubuntu.com/show_bug.cgi?id=15534](http://bugzilla.ubuntu.com/show_bug.cgi?id=15534)[/QUOTE]

Awesome. I hope they fix it, seeing as how I use Firefox for like 3 hours a day.

---

### Post by poofyhairguy on 2005-09-15
I just tried out 1.5 and it is quite faster. Scrolls smoother too.

---

### Post by jdong on 2005-09-15
[QUOTE=poofyhairguy]I just tried out 1.5 and it is quite faster. Scrolls smoother too.[/QUOTE]

As I said, official Deer Park and 1.0.6 binaries do not suffer from this problem.

---

### Post by bored2k on 2005-09-15
Tip for Epiphany users:
[**HOWTO:** [COLOR=DarkRed]Adblocking[/COLOR] in Epiphany Browser](http://ubuntuforums.org/showthread.php?t=66057)  :wink:

---

### Post by drizek on 2005-09-15
[QUOTE=jdong]As I said, official Deer Park and 1.0.6 binaries do not suffer from this problem.[/QUOTE]
 im using suse right now and firefox is still horribly slow. i use konqueror as my main browser, but i am trying out epiphany for comparison. 

It is MUCH faster than firefox and a little faster than konqui maybe too. Ive only used it for a bit, but if it works well, i think im going to be using it until KDE 3.5 comes out.

---

### Post by XDevHald on 2005-09-15
All I have to say is wow to Epiphany compared to Firefox. Firefox is horrifically slow, load time is more than 1minute and the page loads half way and drops the connection to the server of ANY website.

Epiphany auto loads and doesn't waiste time to load a server of any website and does not stall during loading time either.

---

### Post by Curlydave on 2005-09-15
Does anyone know why FF would be so slow in Linux? I first thought that Ubuntu was slow because the main programs I used, OO and FIrefox were really slow, but I guess it's just those programs. OO is slow as hell in WIndows as well, but Firefox is lightning-fast. Why is it only sluggish in Linux? 

Epiphany in Linux runs at the same speed as Firefox in Windows.

---

### Post by wmcbrine on 2005-09-15
[QUOTE=jdong]How big is your ruleset? I'm using Filter G, and there's a significant loss of time (you have to clear your cache between tests)[/QUOTE]I think reloading is sufficient (if caching benefitted one reload, it benefitted the other). But just to humor you, I did another test. I went into another account (a newly created one, for my sister, that she hasn't used yet), where I have Filterset.G loaded. (My usual set is different, perhaps shorter.) Adblock is the only extension in her profile. I started the browser, cleared everything, and loaded Newegg.com. Then I disabled Adblock, cleared everything, exited the browser, restarted, and loaded Newegg.com. Result? *Five* seconds, each time, from hitting Enter on the URL until "Done". No perceptible difference. Of course, I was just counting: "1001, 1002...". I'll use a stopwatch if you like, but I'm pretty sure the results will still be the same, within the margin of error.

I'm using Ubuntu Hoary's Firefox 1.0.6, latest patch, AMD64 version. BTW, Adblock aside, I don't see any of the slowness referred to by others in this thread. I haven't tried Epiphany.

P.S. I just tried it with the 32-bit version I have in a chroot, also the Ubuntu version. Same results.

---

### Post by jdong on 2005-09-15
[QUOTE=wmcbrine]
I'm using Ubuntu Hoary's Firefox 1.0.6, latest patch, AMD64 version. BTW, Adblock aside, I don't see any of the slowness referred to by others in this thread. I haven't tried Epiphany.[/QUOTE]

I'm running Breezy, and I'm seeing much slower firefox performance **than Hoary**, so that may be why.

---

### Post by wmcbrine on 2005-09-15
[QUOTE=jdong]I'm running Breezy, and I'm seeing much slower firefox performance **than Hoary**, so that may be why.[/QUOTE]Ah, sorry. Hmm... When I first installed Hoary, I had huge DNS lookup delays in Firefox, until I disabled IPv6 in about:config. I wonder if it could get reenabled... That's all I can think of.

Oh, you others complaining that Firefox is slow -- do try disabling IPv6, if you haven't. Type "about:config" in the address bar, then "ipv6" in the filter. Toggle the resulting item to "true". That did wonders for me. I'd forgotten about that when I posted the message two up.

---

### Post by jdong on 2005-09-15
[QUOTE=wmcbrine]Ah, sorry. Hmm... When I first installed Hoary, I had huge DNS lookup delays in Firefox, until I disabled IPv6 in about:config. I wonder if it could get reenabled... That's all I can think of.

Oh, you others complaining that Firefox is slow -- do try disabling IPv6, if you haven't. Type "about:config" in the address bar, then "ipv6" in the filter. Toggle the resulting item to "true". That did wonders for me. I'd forgotten about that when I posted the message two up.[/QUOTE]
That certainly doesn't cause 5-second rendering **lockups** on Scragz

---

### Post by XDevHald on 2005-09-15
When I first started to use Breezy's Preview release and the Colony 4, I noticed the connection to the internet of my cable connection would just drop and I would have to restart the connection from the Networking application, and at times that would not even help and I would have to reboot.

This is a constant thing and is very annoying, but it's a process to deal with until Breezy is fixed and released stable in the next few weeks.

---

### Post by wmcbrine on 2005-09-15
OK, I tried my LiveCD of Breezy from August -- not current, I know. Results: 4.5 seconds; no perceptible difference with Adblock or without. Newegg must think I'm crazy by now. Also, the IPv6 setting made no difference (which is an improvement).

P.S. Now I've tried the Scragz benchmark. Using the methodology outlined in the first post of the thread, I get about 3.5 with both Hoary and the LiveCD. Guess I'll try a newer CD next.

P.P.S. OK, got the latest LiveCD. Same results -- 3.5 on Scragz, about 5 on Newegg, with or without Adblock and Filterset G. Can't test Epiphany with the LiveCD.

---

### Post by majikstreet on 2005-09-16
I prelinked epiphany and it still took longer that it would take for me to walk downstairs, eat a brownie, and come back upstairs.

majikstreet

---

### Post by Brunellus on 2005-09-16
[QUOTE=majikstreet]I prelinked epiphany and it still took longer that it would take for me to walk downstairs, eat a brownie, and come back upstairs.

majikstreet[/QUOTE]
 1) those must be short stairs and
2) that must have been a small brownie

---

### Post by aysiu on 2005-09-16
I recently installed Kubuntu's Breezy preview release, and I noticed that my Firefox was much faster (same settings, same internet connection, same computer) than Kubuntu Hoary. Could a newer version of KDE be actually making pages render faster? Is that possible?

---

### Post by majikstreet on 2005-09-16
[QUOTE=Brunellus]1) those must be short stairs and
2) that must have been a small brownie[/QUOTE]
 I live in a townhouse. my computer is on the top story- the brownie is on the middle story (one lower than the top) and the stairs are however long... yes the brownie can be popped in my mouth, but then i grab something to drink etc.... my point was that it takes too long to open. much longer than ffox. i want to use epiphany because i have heard great things about it from evangelists like bored2k and jdong.

---

### Post by jdong on 2005-09-16
**UPDATE**: The bug report produced no much progress, as I expected (this is a difficult issue to debug)

I've recompiled my firefox with i686 optimizations, and re-benched the situation. This is interesting: Though scragz rendering tests show no statistically significant improvement, just the overall feel of Firefox is more responsive, for some reason. I'm blaming a psycological effect for now, and don't recommend anyone to rush out and compile firefox again ;)

---

### Post by papangul on 2005-09-17
Atleast your self compiled firefox is as responsive as the precompiled one.
I had once compiled firefox on gentoo, with cflags optimised for p3, and with -03 optimisation flag, I found my self-compiled firefox to be actually much less responsive than the one that came pre-compiled. This is one of the reasons I don't miss gentoo now.

---

### Post by jdong on 2005-09-17
Well, CFLAGS have to be treated with care... Good experience with Gentoo would tell you that "-O2 -march=i686 -mtune=i686 -pipe -fomit-frame-pointer" is just about as high as you can go without creating hell. (Some package will break even with -O or any -march, like WINE)

---

### Post by BWF89 on 2005-09-17
>  Powered by the Gecko engine, **Epiphany displays webpages with the same speed and accuracy as Mozilla Firefox.** In addition, it provides an elegant, responsive and uncomplicated user interface that fits in perfectly with GNOME, and it has been translated to over thirty languages!
[http://www.gnome.org/projects/epiphany/](http://www.gnome.org/projects/epiphany/)
You'd think that they'd be advertising the fact that Epiphany renders websites around 2x as fast as Firefox

---

### Post by bored2k on 2005-09-17
By the way, in the epiphany-extensions CVS version they are testing out _real_ Adblocking using filterset-g, just liked Adblock.
[http://cvs.gnome.org/viewcvs/epiphany-extensions/extensions/adblock/](http://cvs.gnome.org/viewcvs/epiphany-extensions/extensions/adblock/)

---

### Post by papangul on 2005-09-17
That's great news, seems like I won't miss firefox much, when I start using epiphany . Wish a "flash block" was also there ...

---

### Post by jdong on 2005-09-17
I gotta say, after a few weeks of using Epiphany... I'm liking the simplicity of the interface... I'm fully GNOME-ified now :)

---

### Post by GoA on 2005-09-17
Currently using firefox 1.5 and damn this is fast compared to the 1.06 version.Still konqueror takes the lead with speed.

---

### Post by poofyhairguy on 2005-09-17
Breezy Firefox keeps crashing on me....I might give it up for good.

---

### Post by majikstreet on 2005-09-17
[QUOTE=poofyhairguy]Breezy Firefox keeps crashing on me....I might give it up for good.[/QUOTE]
 Because epiphany doesn't open within say five minutes I may end up not even considering it!

---

### Post by poofyhairguy on 2005-09-17
[QUOTE=majikstreet]Because epiphany doesn't open within say five minutes I may end up not even considering it![/QUOTE]

Looks like we are both in different boats on the same body of water....

(I even thought about installing windows Firefox in WINE today)

---

### Post by majikstreet on 2005-09-17
[QUOTE=poofyhairguy]Looks like we are both in different boats on the same body of water....

(I even thought about installing windows Firefox in WINE today)[/QUOTE]
 LOL... Firefox gets a little slow when I have a lot of tags open..

Post your system specs:
SysInfo: uname: Linux 2.6.12-8-686 CPU: Intel(R) Celeron(R) CPU 2.20GHz 2193.228 MHz Bogomips: 4341.76 Mem: 73/250M [||||||||||] Diskspace: 54.30G Free: 42.54G Procs: 63 Uptime: 3 hrs 41 mins 26 secs Load: 0.30 0.64 0.67  | Screen: Intel Corp. 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03) Screen Resolution: 1024x768 (24 bpp) wlan0: In: 199.55M Out: 18.72M


majikstreet

---

### Post by jdong on 2005-09-17
```
Linux ubuntu 2.6.12-8-k7 #1 Tue Aug 30 23:29:08 BST 2005 i686 GNU/Linux
```

```


jdong@ubuntu:~/livecd$ cat /proc/cpuinfo
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 4
model name      : AMD Athlon(tm) 64 Processor 3000+
stepping        : 8
cpu MHz         : 2002.742
cache size      : 512 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext lm 3dnowext 3dnow
bogomips        : 3923.96

```

---

### Post by zenwhen on 2005-09-17
While I agree that Firefox is no speed demon, I find every other browser to lack many of the things I have become spoiled by with Firefox. Auto-scrolling, Adblock, Gmail Notifier, and the general look and feel of Firefox keep me solidly stuck using Firefox. 

It has its faults, but every application does. I hope speed improvements will come along soon.

---

### Post by dbott67 on 2005-09-17
[QUOTE=zenwhen]While I agree that Firefox is no speed demon, I find every other browser to lack many of the things I have become spoiled by with Firefox. Auto-scrolling, Adblock, Gmail Notifier, and the general look and feel of Firefox keep me solidly stuck using Firefox. 

It has its faults, but every application does. I hope speed improvements will come along soon.[/QUOTE]
 I'm running a P2-300 with 256 MB RAM and have switched to Opera 8.02 --- it flies compared to Firefox on my system.  Epiphany was a bit faster, but with Opera this old system runs pretty good.

Btw, Opera was giving away free S/N a few weeks ago in celebration of their 10th anniversary and I was fortunate enough to get a S/N.  The free version just has a banner ad that runs across the top, but if you register it, the banner goes away.

[http://my.opera.com/community/party/](http://my.opera.com/community/party/)

-Dave

---

### Post by Curlydave on 2005-09-18
[QUOTE=dbott67]I'm running a P2-300 with 256 MB RAM and have switched to Opera 8.02 --- it flies compared to Firefox on my system.  Epiphany was a bit faster, but with Opera this old system runs pretty good.

Btw, Opera was giving away free S/N a few weeks ago in celebration of their 10th anniversary and I was fortunate enough to get a S/N.  The free version just has a banner ad that runs across the top, but if you register it, the banner goes away.

[http://my.opera.com/community/party/](http://my.opera.com/community/party/)

-Dave[/QUOTE]
 Two unresolved ephiphany issues for me: 

1: The tools at the top take up WAY too much space; more than twice the space firefox does for the same set of tools. (including tabs and the bookmark toolbar) 

2: The bookmarks don't show the icon next to them. I do however like how Ephiphany shows the icon in the tilebar and taskbar while FF doesn't. That's cool, but it should also so them by the bookmark.

---

### Post by Lovechild on 2005-09-18
[QUOTE=Curlydave]Two unresolved ephiphany issues for me: 

1: The tools at the top take up WAY too much space; more than twice the space firefox does for the same set of tools. (including tabs and the bookmark toolbar) 

2: The bookmarks don't show the icon next to them. I do however like how Ephiphany shows the icon in the tilebar and taskbar while FF doesn't. That's cool, but it should also so them by the bookmark.[/QUOTE]

1. edit the menu to your liking, remove them icon text and rearrange it a bit - I did - I agree the default it's really optimal maybe filing a bug would be good

2. there's an extension to do this I think epiphany-extensions, just apt-get into it.

---

### Post by ow50 on 2005-09-18
[QUOTE=Curlydave]Two unresolved ephiphany issues for me: 

2: The bookmarks don't show the icon next to them. I do however like how Ephiphany shows the icon in the tilebar and taskbar while FF doesn't. That's cool, but it should also so them by the bookmark.[/QUOTE]
I do get icons for bookmarks. I don't remember what I had to change, but you can try about:config keys "browser.chrome.favicons" and "browser.chrome.site_icons".

Even though I do get some icons, it seems to me that firefox shows icons for many sites for which epiphany doesn't.

---

### Post by jdong on 2005-09-18
It's very sensitive to the link URL. It must be EXACT. i.e."www.ubuntuforums.org" doesn't favicon, but "ubuntuforums.org" does. Make sure it matches the address bar URL.

---

### Post by TravisNewman on 2005-09-18
weird, www,ubuntuforums.org DOES have a favicon for me.

---

### Post by Lovechild on 2005-09-18
[QUOTE=panickedthumb]weird, www,ubuntuforums.org DOES have a favicon for me.[/QUOTE]

None of them have for me, something's fishy

---

### Post by TravisNewman on 2005-09-18
here's the weird thing. They go off and on. On the main page of [www.ubuntuforums.org](www.ubuntuforums.org) the favicon doesn't show up, but as far as I can tell, on any subpages they do show up.

---

### Post by aysiu on 2005-09-18
[QUOTE=Lovechild]None of them have for me, something's fishy[/QUOTE] Yeah, it's fishy. [See? It works for me](http://i22.photobucket.com/albums/b337/psychocats/8f8405a0.png).

I wonder if it's the install or your profile that's messed up.

---

### Post by dtfinch on 2005-09-18
It's the version of Gecko that Firefox 1.0x uses. It's slow as in buggy on Linux. The previous and following releases perform great. In the most extreme cases, pages that took a second take a minute. Something in FireFox 1.0x is easily 100x slower on Linux than on Windows. Some pages just freeze it for longer than I'm willing to wait. If a page takes 5 minutes at 100% cpu to render after it has been downloaded completely, with no plugins or javascript, I consider that a bug. Breezy should have standardized on Deer Park. It's far more stable in this respect.

---

### Post by TravisNewman on 2005-09-18
it's far more stable in most respects.

---

### Post by jdong on 2005-09-18
I foresee a Backports field day :)

---

### Post by Lovechild on 2005-09-18
[QUOTE=jdong]I foresee a Backports field day :)[/QUOTE]

I foresee a repeat of the mono backport episode.

---

### Post by Curlydave on 2005-09-18
[QUOTE=Lovechild]1. edit the menu to your liking, remove them icon text and rearrange it a bit - I did - I agree the default it's really optimal maybe filing a bug would be good

2. there's an extension to do this I think epiphany-extensions, just apt-get into it.[/QUOTE]

How exactly did you go about editing the menus?

---

### Post by Lovechild on 2005-09-18
[QUOTE=Curlydave]How exactly did you go about editing the menus?[/QUOTE]

Edit->Toolbar ?

---

### Post by Curlydave on 2005-09-18
[QUOTE=Lovechild]Edit->Toolbar ?[/QUOTE]

Thanks, that does let you get rid of the text and big icons, but it would be an even more efficient use of space to put up the address bar next to the icons. (right now most of the adress bar is being wasted) This is alot better than before though. Now I just need to spend the next few hours getting back and foward on the mouse to work .  :?

Also, does anyone know if there's a way to enable autoscroll in Epiphany like you can in Firefox? That would rock, especially because I can't find a way to change how many lines my scrollwheel scrolls, because right now it's too slow. 

edit: This is odd... I went to the ephiphany extensions page, and it lists autoscroll!! I then downloaded the extension package in synaptec, and it has all of the extensions, except for one... you guess it: autoscroll! What are the odds... The one advertised extension that I actually want isn't in the package. wonderful. Actually, there are two epiphany extensions pages with nearly identical URLS. (below) One lists autoscroll, the other doesn't. I want autoscroll. bleh

[http://www.gnome.org/projects/epiphany/extensions](http://www.gnome.org/projects/epiphany/extensions)
[http://www.gnome.org/projects/epiphany/extensions.html](http://www.gnome.org/projects/epiphany/extensions.html)

---

### Post by Kyral on 2005-09-18
You wanna know something REALLY odd? Epiphany isn't showing up in any of my GNOME menus even after I did an update-menus and a killall gnome-panel

EDIT: Okay this is kinda screwed up. installing "epiphany" installs a game. Shouldn't the package "epiphany" be the browser?

---

### Post by bored2k on 2005-09-19
[QUOTE=Kyral]You wanna know something REALLY odd? Epiphany isn't showing up in any of my GNOME menus even after I did an update-menus and a killall gnome-panel

EDIT: Okay this is kinda screwed up. installing "epiphany" installs a game. Shouldn't the package "epiphany" be the browser?[/QUOTE]
 epiphany-browser

---

### Post by Lovechild on 2005-09-19
[QUOTE=Curlydave]Thanks, that does let you get rid of the text and big icons, but it would be an even more efficient use of space to put up the address bar next to the icons. (right now most of the adress bar is being wasted) This is alot better than before though. Now I just need to spend the next few hours getting back and foward on the mouse to work .  :?

Also, does anyone know if there's a way to enable autoscroll in Epiphany like you can in Firefox? That would rock, especially because I can't find a way to change how many lines my scrollwheel scrolls, because right now it's too slow. 

edit: This is odd... I went to the ephiphany extensions page, and it lists autoscroll!! I then downloaded the extension package in synaptec, and it has all of the extensions, except for one... you guess it: autoscroll! What are the odds... The one advertised extension that I actually want isn't in the package. wonderful. Actually, there are two epiphany extensions pages with nearly identical URLS. (below) One lists autoscroll, the other doesn't. I want autoscroll. bleh

[http://www.gnome.org/projects/epiphany/extensions](http://www.gnome.org/projects/epiphany/extensions)
[http://www.gnome.org/projects/epiphany/extensions.html](http://www.gnome.org/projects/epiphany/extensions.html)[/QUOTE]

I have Auto Scroll listed as the second extension on my setup, I suspect you need to look harder

---

### Post by Teroedni on 2005-09-19
Ephiany is really faster:)

Maybe i change;)

---

### Post by Curlydave on 2005-09-19
[QUOTE=Lovechild]I have Auto Scroll listed as the second extension on my setup, I suspect you need to look harder[/QUOTE]

How did you acquire the extensions? I used synaptec, which might be an outdated version. As you can see in the links I posted, there looks to be two versions floating around. The first link includes autoscroll second, the second does not include it. The package in synaptec must correspond to the second one. Did you use a different method to get your extensions? Thanks!

---

### Post by Lovechild on 2005-09-19
So in the light of all this, Epiphany being faster, better integrated, having more consistent translation with GNOME, having an easier interface. Should we seriously petition Epiphany as the default browser for Dapper?

I think we should, there are a ton of arguments in favor.

---

### Post by Lovechild on 2005-09-19
[QUOTE=Curlydave]How did you acquire the extensions? I used synaptec, which might be an outdated version. As you can see in the links I posted, there looks to be two versions floating around. The first link includes autoscroll second, the second does not include it. The package in synaptec must correspond to the second one. Did you use a different method to get your extensions? Thanks![/QUOTE]

I installed the lastest epiphany-extensions package in Breezy

---

### Post by doclivingston on 2005-09-19
[QUOTE=Lovechild]So in the light of all this, Epiphany being faster, better integrated, having more consistent translation with GNOME, having an easier interface. Should we seriously petition Epiphany as the default browser for Dapper?

I think we should, there are a ton of arguments in favor.[/QUOTE]

This was discussed (argued) in a thread a while ago, and several of us created a page in the wiki ([https://wiki.ubuntu.com/EpiphanyDefaultBrowser](https://wiki.ubuntu.com/EpiphanyDefaultBrowser)) which lists some points for and against switching to Epiphany in Dapper - feel free to add to it. I think the plan was to bring this up some time after Breezy is released.

---

### Post by Curlydave on 2005-09-19
[QUOTE=Lovechild]I installed the lastest epiphany-extensions package in Breezy[/QUOTE]

Maybe the problem is that I'm in Hoary.

---

### Post by Lovechild on 2005-09-19
[QUOTE=doclivingston]This was discussed (argued) in a thread a while ago, and several of us created a page in the wiki ([https://wiki.ubuntu.com/EpiphanyDefaultBrowser](https://wiki.ubuntu.com/EpiphanyDefaultBrowser)) which lists some points for and against switching to Epiphany in Dapper - feel free to add to it. I think the plan was to bring this up some time after Breezy is released.[/QUOTE]

I was considering just holding a few developers at gunpoint.. but sure that would work as well.

---

### Post by dalani on 2005-09-24
[QUOTE=jdong]Hmm, well, it's the same Gecko rendering engine, compiled with the same compiler and the same everything. Did you see my comment about official Firefox? It's faster, and actually compiled with GCC 3.3... Has GCC 4.0 really gotten that messed up?


Users of other distros, is there this significant of a difference between Firefox and Epiphany/Galeon?



There's certainly some sites that set off Firefox's slowness -- Slashdot does it on autoscroll, and the Forums does it. Since I visit the forums the most, that's kind of concerning.



Either way, I don't remember seeing THIS kind of speed gap back in Hoary days. I still feel it's abnormal.[/QUOTE]
 I agree 100%: Mozilla in Win98 is faster all around than Firefox in Linux. In the same box running dual boot OS. WHy?Why?

---

### Post by Qrk on 2005-09-24
I've switched to epiphany... my last apt-get upgrade broke firefox, and epiphany works just fine... I even like the UI better.

---

### Post by xmastree on 2005-09-24
First thing I didn't like about it is the inability to Ctrl-Tab between panes...

---

### Post by doclivingston on 2005-09-25
Ctrl-PageUp and Ctrl-PageDown work in Epiphany, as they do with pretty much every GTK app.

---

### Post by Goober on 2005-09-25
I don't have Breezy yet, waiting for the official release, but is Epiphany available for Hoary?  I tried installing it because Firefox had gone down from some weird upgrade package that messed it yp, and it didn't work (Konquerer does, but, well, its just not my beloved Firefox).

---

### Post by doclivingston on 2005-09-25
[QUOTE=Goober]I don't have Breezy yet, waiting for the official release, but is Epiphany available for Hoary?  I tried installing it because Firefox had gone down from some weird upgrade package that messed it yp, and it didn't work (Konquerer does, but, well, its just not my beloved Firefox).[/QUOTE]

Hoary has Epiphany 1.6, although if Firefox doesn't work Epiphany may not (Epiphany uses Gecko, from Firefox, to render pages)

---

### Post by bored2k on 2005-09-25
[QUOTE=doclivingston]Hoary has Epiphany 1.6, although if Firefox down't work Epiphany may not (Epiphany uses Geck, from Firefox, to render pages)[/QUOTE]
 You can get 1.7 with Hoary downloading the Ubuntu package from Eph's website (Breezy has .8).

---

### Post by xmastree on 2005-09-25
[QUOTE=doclivingston]Ctrl-PageUp and Ctrl-PageDown work in Epiphany, as they do with pretty much every GTK app.[/QUOTE]Hmmm... That's awkward for me. When I'm web browsing I tend to have my right hand on the mouse, and my left hand covering Ctrl-Tab. Page up/down are nowhere near...
That means I gotta move... :-|

---

### Post by liquidtenmillion on 2005-09-25
I'm just coming in to kind of ease everyone's mind's i guess, but the firefox slowness you are experiencing is by no means ubuntu specific.

I am running it on FreeBSD, and i compiled it myself using -march=pentium3 -O2 -pipe, and it is significantly slower than Epiphany compiled with the same flags.

Maybe it isn't that ubuntu is doing something different, but that the other distros are.  Distros like Arch Linux, Mandrake, Dropline Gnome(slackware) all have firefox running fast.  Maybe they are including a patch that isn't part of the vanilla Firefox sourcecode(which is what i compiled)?

---

### Post by jdong on 2005-09-25
It could very well be the over way around (Ubuntu's including a patch that's slowing things down)

---

### Post by papangul on 2005-09-25
In that case if someone installs firefox-bin directly from Mozilla.org without installing from Ubuntu's repos, the difference should be apparent. Someone needs to try this out.

---

### Post by liquidtenmillion on 2005-09-25
[QUOTE=jdong]It could very well be the over way around (Ubuntu's including a patch that's slowing things down)[/QUOTE]

I compiled firefox from source code with no additional patches and it performs almost exactly the same as ubuntu's packaged firefox.


However, i was starting to think, what if this has something to do with GTK?  My FreeBSD uses GTK 2.8, as does ubuntu breezy, while mandrake/arch/dropline all use gtk 2.6, and the official firefox uses an even early version of gtk.

Maybe gtk 2.8 is slowing things down?


I'm going to build firefox on my machine running gnome 2.10 with gtk2.6 to test.

---

### Post by macewan on 2005-09-25
[QUOTE=Qrk]I've switched to epiphany... my last apt-get upgrade broke firefox, and epiphany works just fine... I even like the UI better.[/QUOTE]

same here

apt-get update yesterday barfed firefox & I had to switch to epiphany

---

### Post by doclivingston on 2005-09-25
[QUOTE=liquidtenmillion]However, i was starting to think, what if this has something to do with GTK?  My FreeBSD uses GTK 2.8, as does ubuntu breezy, while mandrake/arch/dropline all use gtk 2.6, and the official firefox uses an even early version of gtk.[/QUOTE]

Unless they statically linked the Firefox binary (which I seriously doubt), it wouldn't be using 2.6, it would be using whatever you have installed. The only reason I can think of is if it tries to use one of the newer 2.8 features if compiled against it, and uses something else as a fallback when compiled against 2.6, AND whatever they are using in 2.8 is much slower (whether it's GTK's fault or Firefox's).

The way to figure this you would be to profile both the Ubuntu package and the Mozilla-build binary, and see where they are spending their time.

---

### Post by liquidtenmillion on 2005-09-25
[QUOTE=doclivingston]Unless they statically linked the Firefox binary (which I seriously doubt), it wouldn't be using 2.6, it would be using whatever you have installed. The only reason I can think of is if it tries to use one of the newer 2.8 features if compiled against it, and uses something else as a fallback when compiled against 2.6, AND whatever they are using in 2.8 is much slower (whether it's GTK's fault or Firefox's).

The way to figure this you would be to profile both the Ubuntu package and the Mozilla-build binary, and see where they are spending their time.[/QUOTE]

Thats kind of what im saying.  When using gtk2.8 firefox will use cairo, which may infact slow down firefox.

On my Slackware 10.0 pc, the official package from mozilla runs really fast, and it's using gtk 2.4.

---

### Post by beeldings on 2005-09-25
Firefox on Linux is horribly slow. As much as I love Firefox, it takes too long to render most web pages. I've also noticed that some users have mentioned the "lag" when accessing a web site or when a page is rendered, this happens to me all the time. The only thing keeping me from dropping Firefox are the many extensions that I use, it's ad-blocking/pop-up blocking capabilities, and the fact that it is the default Ubuntu web browser.

After reading this thread, I downloaded the static .deb of Opera. Wow, that thing really flies on my computer. No lag, no bullsh*t. I haven't transitioned from FF to Opera yet, because it looks very ugly compared to FF and the extensions I have come to enjoy and employ daily under FF are not available for Opera (Adblock, SwitchProxy, CustomizeGoogle, Flashblock). But, if I use Privoxy with Opera, most ads and flash are blocked, but noticeably more ads are downloaded as opposed to my Adblock-enabled FF.

I was going to test Epiphany today but I receive unmet dependency errors when trying to install it with aptitude or Synaptic, so I'm just giving up and hoping that Breezy's FF is faster than Hoary.

---

### Post by jdong on 2005-09-25
It may in fact be cairo related....

---

### Post by Qrk on 2005-09-25
Strike that last comment. I switched to opera. I know its closed source, but its a free download and a great browser.

---

### Post by doclivingston on 2005-09-25
[QUOTE=liquidtenmillion]Thats kind of what im saying.  When using gtk2.8 firefox will use cairo, which may infact slow down firefox.

On my Slackware 10.0 pc, the official package from mozilla runs really fast, and it's using gtk 2.4.[/QUOTE]

Unless the mozilla-provided binary has been statically linked against GTK, it will use whatever is on your system - it doesn't matter what it was build against, it will use cairo if it's running on a system with GTK 2.8 (as breezy is).

(well unless it uses cairo directly, which I'm certain Firefox 1.0.x doesn't do)

---

### Post by jdong on 2005-09-25
[QUOTE=Qrk]Strike that last comment. I switched to opera. I know its closed source, but its a free download and a great browser.[/QUOTE]

It certainly is a great browser. I've been playing with it more and more recently. File associations are pretty KDE-bound, though. I'm working on fixing that, and if I do, Opera will become my browser of choice, too.

UPDATE: Got it! Tools->Preferences, Advanced, under Downloads and Saved Files Handles, replace kfmclient exec with gnome-open.

---

### Post by liquidtenmillion on 2005-09-25
[QUOTE=jdong]It certainly is a great browser. I've been playing with it more and more recently. File associations are pretty KDE-bound, though. I'm working on fixing that, and if I do, Opera will become my browser of choice, too.[/QUOTE]

you might have to do that.(make sure opera isn't running ;))

anthony@Pismire$ cat .opera/filehandler.ini
Opera Preferences version 2.0
; Do not edit this file while Opera is running
; This file is stored in UTF-8 encoding
[Settings]
Default File Handler=gnome-open ,1
Default Directory Handler=gnome-open ,1
anthony@Pismire$


Make a ~/.opera/filehandler.ini with those settings, and all of your downloads will open with opera.  Also, if you put  "opera -newpage %s" in the Preferred Applications thing for browser it will use opera.

The only problems with opera are.

1.  no flash plugin(for me anyway, there is one for linux) with the Native Port(using opera-linux works)  Ubuntu users can ignore this.
2.  no integration with gnome.  It looks really out of place.
3.  Can not use Mozillla 1.7+ or Firefox plugins, only Netscape 6,4 and Mozilla 1.6 plugins(mplayerplug-in for example)
4.  Some pages render poorly, and freeze alltogether.  [http://www.gentoo-portage.com](http://www.gentoo-portage.com) for example
5.  No java plugin.  Everytime i try to use java the browser crashes.(may be FreeBSD specific, but java works fine in Firefox)

---

### Post by jdong on 2005-09-25
> **liquidtenmillion]you might have to do that.(make sure opera isn't running  said:**
> 
Default File Handler=gnome-open ,1
Default Directory Handler=gnome-open ,1
anthony@Pismire$


Make a ~/.opera/filehandler.ini with those settings, and all of your downloads will open with opera.  Also, if you put  "opera -newpage %s" in the Preferred Applications thing for browser it will use opera.

Thanks! Figured it out at the same time :)

> 
The only problems with opera are.

1.  no flash plugin(for me anyway, there is one for linux) with the Native Port(using opera-linux works)  Ubuntu users can ignore this.

FreeBSD user, huh? Yep, heard this one before.
> 
2.  no integration with gnome.  It looks really out of place.

It does look a bit strange inside GNOME.
> 
3.  Can not use Mozillla 1.7+ or Firefox plugins, only Netscape 6,4 and Mozilla 1.6 plugins(mplayerplug-in for example)

confirmed.
> 
4.  Some pages render poorly, and freeze alltogether.  [http://www.gentoo-portage.com](http://www.gentoo-portage.com) for example

Hmm, works for me.
> 
5.  No java plugin.  Everytime i try to use java the browser crashes.(may be FreeBSD specific, but java works fine in Firefox)
That's definitely FREEBSD related -- it works fine under Linux.

---

### Post by liquidtenmillion on 2005-09-25
I kind of thought it was freebsd related, as the freebsd version sucks.  (it's built against 4.x, even though 90% of freebsd users use 5.x)

But that's why i have this nifty "InFF" button that views the current page in firefox.

[http://img259.imageshack.us/img259/6469/opera1tz.png](http://img259.imageshack.us/img259/6469/opera1tz.png) 

which i got from here [http://nontroppo.org/wiki/CustomButtons](http://nontroppo.org/wiki/CustomButtons)

---

### Post by debaser13 on 2005-09-26
Well, I must say, I just downloaded Epiphany in light of this thread and can't believe how much faster it throws down the pages.  I agree that Adblock, as would some other user-defined extensions, would be nice but if a page is being loaded at nearly twice the speed (which, Epiphany is compared to Firefox), I don't care as much about the ads.  After Firefox broke on the last update, I downloaded Konqueror but was not impressed (K3B is the only K-app I think I like) and I am tiring of Firefox a bit...so, maybe this will mark the change for me.  Plus, I am all for a browser that only works on *unix.  I am now a full fledge seperatist when it comes to OS's.  Screw anything that works on Windows... :)

-C

---

### Post by bored2k on 2005-09-26
[QUOTE=debaser13]Well, I must say, I just downloaded Epiphany in light of this thread and can't believe how much faster it throws down the pages.  I agree that Adblock, as would some other user-defined extensions, would be nice but if a page is being loaded at nearly twice the speed (which, Epiphany is compared to Firefox), I don't care as much about the ads.  

-C[/QUOTE]

Ads:
1. [http://ubuntuforums.org/showthread.php?t=66057&highlight=adblocking](http://ubuntuforums.org/showthread.php?t=66057&highlight=adblocking)
2. The current CVS version of epiphany-extensions already implements the filterset-g used in Firefox' Adblock.

---

### Post by bored2k on 2005-09-26
[QUOTE=debaser13]Well, I must say, I just downloaded Epiphany in light of this thread and can't believe how much faster it throws down the pages.  I agree that Adblock, as would some other user-defined extensions, would be nice but if a page is being loaded at nearly twice the speed (which, Epiphany is compared to Firefox), I don't care as much about the ads.  After Firefox broke on the last update, I downloaded Konqueror but was not impressed (K3B is the only K-app I think I like) and I am tiring of Firefox a bit...so, maybe this will mark the change for me.  Plus, I am all for a browser that only works on *unix.  I am now a full fledge seperatist when it comes to OS's.  Screw anything that works on Windows... :)

-C[/QUOTE]
Screw anything that works on Windows? Just trash your whole computer then.

---

### Post by mrtaber on 2005-09-26
Just for inquiring minds, I also run an official Red Hat Enterprise Linux 4 WS box, and my Firefox 1.07 was consistently throwing down sub 4-second times on that test page.  I wonder what gives with the other versions.? On the Fedora box, 8+ seconds, and also on my Breezy box.  

Just a little added info for those who know more than I do, and might be able to make use of it :)

Mark

---

### Post by jdong on 2005-09-26
[QUOTE=mrtaber]Just for inquiring minds, I also run an official Red Hat Enterprise Linux 4 WS box, and my Firefox 1.07 was consistently throwing down sub 4-second times on that test page.  I wonder what gives with the other versions.? On the Fedora box, 8+ seconds, and also on my Breezy box.  

Just a little added info for those who know more than I do, and might be able to make use of it :)

Mark[/QUOTE]


This was the kind of behavior that I wanted to investigate/bring to light with this thread. The problem appears very complex and confusing, with lots of seemingly overlapping factors.

---

### Post by debaser13 on 2005-09-26
[QUOTE=bored2k]Screw anything that works on Windows? Just trash your whole computer then.[/QUOTE]

Of course my computer works with Windows...that goes without saying but I find it interesting that a Ubuntu Forum Staff takes a moment out of his day in order to provide a bit of backhandedness.  Very constructive.

I am very happy with Linux and Ubuntu.  I find the freedom to be one of the greatest aspects e.g. the ease and ability to even choose Epiphany over Firefox.  This is very unlike a Windows environment as the heirarchy of Windows applications is apparent and limits that choice.  What I have noticed in this thread as well as others is that performance of an application in Ubuntu is good if not great and that it truly boils down to preference on smaller but substantial things.  I am not sure I could say that when I used Windows.

I have no idea why spend this much time answering that post...

-c

---

### Post by bugmenot on 2005-09-26
[QUOTE=jdong]It does look a bit strange inside GNOME.
[/QUOTE]

Check this out: [http://ubuntuforums.org/showthread.php?t=69031](http://ubuntuforums.org/showthread.php?t=69031)

Makes it waaay better. Qt menus still suck. Polymer Qt style helps a little.
Just get rid of the menu bar altogether and use the nifty one-button shortcuts. There's a main menu drop-down at the Opera Wiki for the rare cases where you need the main menu.

---

### Post by beeldings on 2005-09-27
After some tampering with my Hoary, Epiphany is up and running, and I think I found my new default browser. I'll still use Firefox for on-line banking and shopping, but for general web browsing, Epiphany is the new way to go. I still can't get over how fast it is compared to Firefox and Opera, it blows both of them away.

---

### Post by supernaut on 2005-09-28
Why use Firefox for banking and shopping? They are essentially the same browser, with the exception of the interface, so Epiphany should work on all the sites that Firefox does.

---

### Post by mctavish on 2005-09-28
> Why use Firefox for banking
User agent switching, my friend.
Some sites insist on internet explorer. Firefox has an extension that allows it to identify as an ie browser.
Hopefully epiphany will get such an extension eventually.

---

### Post by Curlydave on 2005-09-28
I just installed Breezy, and now Firefox appears to be up to speed, except for launching the application. No more scroll-wheel lag, slow web-page loading etc. Still not quite as fast as epiphany, but better than before.

---

### Post by jeffreyvergara.NET on 2005-09-29
i just switched from FFv1.0.7 to Epiphany 2days ago because based on my experience, FF is slower and laggier than epiphany. so I guess i will be sticking to epiphany on my eveyday surfing.. lol

---

### Post by nix4me on 2005-10-15
Has anyone noticed that Epiphany is faster than Firefox?

Firefox seems to be getting slower and slower.

nix

---

### Post by kairu0 on 2005-10-15
I think that's the idea behind it. Firefox is getting more bloated with every release.

---

### Post by aysiu on 2005-10-15
It's well-documented that Firefox is slower than Epiphany and Opera. People like me use it for other reasons--an amazing selection of extensions being one of them. If you like Firefox and want it to be faster, you can follow these tweaking instructions:

[http://www.freerepublic.com/focus/f-news/1299854/posts](http://www.freerepublic.com/focus/f-news/1299854/posts)

I don't think you should be surprised to find out that this ground has been covered before:

[http://www.ubuntuforums.org/showthread.php?t=69034](http://www.ubuntuforums.org/showthread.php?t=69034)
[http://ubuntuforums.org/showthread.php?p=49071#post49071](http://ubuntuforums.org/showthread.php?p=49071#post49071)

---

### Post by Ubunted on 2005-10-15
Firefox slowness comes from a different source for me - it takes noticeably longer to start up in Ubuntu than it does in XP. Once it's up though, it's plenty fast. I'm sure my 7 mbit connnection helps there too.

I have tried to switch to Epiphany more than once for the speed, but I just miss my AdBlock and GMail Notifier too much. I don't much like the bookmarks interface either. But that's me - I've been a Firefox addict since 0.8.

---

### Post by TravisNewman on 2005-10-15
the thing for me is, if I use the firefox from the ubuntu repos, it is slow as a beast, but if I install it from the website, it's much faster. That's what throws me off.

---

### Post by mortong on 2005-10-15
[QUOTE=aysiu]It's well-documented that Firefox is slower than Epiphany and Opera. People like me use it for other reasons--an amazing selection of extensions being one of them. If you like Firefox and want it to be faster, you can follow these tweaking instructions:

[http://www.freerepublic.com/focus/f-news/1299854/posts](http://www.freerepublic.com/focus/f-news/1299854/posts)

I don't think you should be surprised to find out that this ground has been covered before:

[http://www.ubuntuforums.org/showthread.php?t=69034](http://www.ubuntuforums.org/showthread.php?t=69034)
[http://ubuntuforums.org/showthread.php?p=49071#post49071](http://ubuntuforums.org/showthread.php?p=49071#post49071)[/QUOTE]

Wow, thanks!  That really does work.

---

### Post by aysiu on 2005-10-15
[QUOTE=panickedthumb]the thing for me is, if I use the firefox from the ubuntu repos, it is slow as a beast, but if I install it from the website, it's much faster. That's what throws me off.[/QUOTE] If I haven't found that for Firefox, but I have found that for Thunderbird. I use Mozilla's Thunderbird and Ubuntu's Firefox.

---

### Post by Lovechild on 2005-10-15
[QUOTE=Ubunted]Firefox slowness comes from a different source for me - it takes noticeably longer to start up in Ubuntu than it does in XP. Once it's up though, it's plenty fast. I'm sure my 7 mbit connnection helps there too.

I have tried to switch to Epiphany more than once for the speed, but I just miss my AdBlock and GMail Notifier too much. I don't much like the bookmarks interface either. But that's me - I've been a Firefox addict since 0.8.[/QUOTE]

There is an adblock extension for Epiphany, it isn't currently compiled by default though.

GMail notifer, well that is what evolution is for, and if you ask me that really needs to notify you about new mail in a better way.

There is also a bookmark rework in progress, you can check it out on the mailinglist.

---

### Post by xequence on 2005-10-15
Firefox was great, just slow on ubuntu. Epiphany was faster, but ackward.

Opera is fast and feels natural ;)

---

### Post by gord on 2005-10-15
firefox is way fast with the latest beta's, and much better to use :)

can take a few seconds to start up though.. but i don't mind that, i only really do it once and then pritty much keep it in a workspace until i need it.

---

### Post by gusto5 on 2005-10-16
Ive used both the repo firefox and the site firefox. The loading times are the same for me, though.

I Do notice a difference, on the other hand with ThunderBird.

---

### Post by Sirin on 2005-10-16
Konqueror is the fastest browser I've seen. I really don't know why people say that it sucks, but hey, it's their opinion, not a fact... :cool:

Out of the two of course... things rely on what you put them up to. For example, if you want speed, go with Epiphany. If you want In-Depth browsing, Firefox is for you. ;)

---

### Post by Ubunted on 2005-10-16
[QUOTE=Lovechild]There is an adblock extension for Epiphany, it isn't currently compiled by default though.

GMail notifer, well that is what evolution is for, and if you ask me that really needs to notify you about new mail in a better way.

There is also a bookmark rework in progress, you can check it out on the mailinglist.[/QUOTE]
I've tried using mail clients, but with two computers it's much easier to just use the webmail and keep everything in one spot.

---

### Post by landotter on 2005-10-16
FF starts in five seconds on my 1.1ghz/256mb box and is snappy in use. No complaints.

Epiphany has some decent ideas, but is no faster, doesn't use any fewer resources, and doesn't have the wealth of extensions. 

No contest imho

---

### Post by TravisNewman on 2005-10-16
[QUOTE=gusto5]Ive used both the repo firefox and the site firefox. The loading times are the same for me, though.

I Do notice a difference, on the other hand with ThunderBird.[/QUOTE]
loading times are the same, but the page load time is dramatically better with the one from the site, and there aren't the lockups between said page loads.

---

### Post by BWF89 on 2005-10-16
[quote=aysiu]It's well-documented that Firefox is slower than Epiphany and Opera. People like me use it for other reasons--an amazing selection of extensions being one of them. If you like Firefox and want it to be faster, you can follow these tweaking instructions:

[http://www.freerepublic.com/focus/f-news/1299854/posts]("http://www.freerepublic.com/focus/f-news/1299854/posts")[/quote] Don't do what is written in that HOWTO. It may make your browser run faster but it upps the bandwidth costs for alot of the smaller websites. On the Unnoficial Sega Dreamcast forums (DCForums.co.uk) the moderaters consitered banning all Firefox users because making 50 requests instead of 4 was costing them alot of extra money.

And when I tried it (I have DSL) I didn't notice any difference in speed.

---

### Post by majikstreet on 2005-10-16
Epiphany takes a long time to open for me (NOT ANYMORE!!). I like firefox, but it is rather slow.

Opera is nice, except it has the "Windows 9x gray" menus. If it didn't have those, I would LOVE IT! I installed a theme that looks like firefox on a mac and it's beautiful!:KS

Dude! I just tried epiphany again, it's the fastest browser I've ever used!

---

### Post by poofyhairguy on 2005-10-16
I use both. Firefox for day to day because I have a computer with a half gig of RAM and I want to use it all, then Epiphany when I need to do something important or where speed matter or when I need a lot of tabs.

I would use Epiphany near full time if I could make its tabs do Firefox's relative size trick.

---

### Post by topcop on 2005-10-17
[QUOTE=nix4me]Has anyone noticed that Epiphany is faster than Firefox?

Firefox seems to be getting slower and slower.

nix[/QUOTE]
on my system firefox pwns epiphany! the rendering and loading speed.  Maybe because ive compiled it myself with optimisations for my CPU with GCC 4.0.2

---

### Post by psychicdragon on 2005-10-17
[QUOTE=majikstreet]Opera is nice, except it has the "Windows 9x gray" menus. If it didn't have those, I would LOVE IT! I installed a theme that looks like firefox on a mac and it's beautiful!:KS[/QUOTE]

You can install the qt3-qtconfig package and make the Opera menus look just like your gtk+ applications, you won't even notice the difference. No way to make it use the gtk+ file-choser though. :rolleyes:

---

### Post by Pablo_Escobar on 2005-10-17
Personally I've switched to Epiphany - it is faster (loading pages), the only thing mentioned here before is the tab size trick Firefox has.
We'll have to wait for Firefox 1.5 - heared some great reviews about it (Beta stage that is)

---

### Post by Goober on 2005-10-17
Thanks for that link aysiu.  My Firfefox is a bit quicker as well!

---

### Post by bored2k on 2005-10-17
[QUOTE=poofyhairguy]I would use Epiphany near full time if I could make its tabs do Firefox's relative size trick.[/QUOTE]
One of the reasons why I back with Firefox is because I need the Ctrl+Tab key. Epiphany's Ctrl+PgUp is just silly to me (why would I want to let go of the mouse?). Another thing that helped me go back to Firefox was the fasterfox extension which speeds Firefox dramatically. Of course, it's just a silly GUI to some about:config changes you could copy and use in Epiphany, but it's really nice to see Firefox in acceptable speeds and the loading timer is absolutely wonderful. Besides all that, I am now Azureus free, which means my computer does not feel half as heavy as it felt when I tried using it with both Azureus and Firefox running.

Extensions I love and use: Fasterfox, Extended Preferences (to avoid new windows from spawning) and (sometimes) the Gmail Notifier.

Also, I noticed that after a while Epiphany started getting heavier and heavier, and with all those new windows spawning, its RAM usage would ridiculously scalate. 

Things they're both good at: adblocking using userContent.css and hostperm.1

---

### Post by Lovechild on 2005-10-17
As for ram use, the new fontconfig mmaps everything so we save tons and tons of ram, generally the next version of GNOME is set to be faster and more ram efficent - I'm hoping this will go for Epiphany as well.

---

### Post by majikstreet on 2005-10-17
[QUOTE=psychicdragon]You can install the qt3-qtconfig package and make the Opera menus look just like your gtk+ applications, you won't even notice the difference. No way to make it use the gtk+ file-choser though. :rolleyes:[/QUOTE]
Tsk-Tsk.. Doesn't work. It's the same trick as w/ firefox, but it doesn't work with opera sadly.

---

### Post by mstlyevil on 2006-02-28
I know this is an old thread but I decided to spend the day using Epiphany because of this thread in the Dapper section.

[ Epiphany or Firefox default browser for Dapper? ]("http://www.ubuntuforums.org/showthread.php?t=93219")

I have done a series of test for speed, both opening the browsers and web page rendering. I also checked the memory usage on each one by noting how much RAM was being used with no windows open and then opening each browser and then minimising them in the taskbar one at a time to check how much Ram was being used. The difference between the two was 5 Megs of RAM with Firefox using more. IMHO this is not enough to say that Firefox uses too much RAM vs Epiphany. Both browser opened from a cold start in roughly about the same time and I find that Firefox actually renders web pages about a second faster than Epiphany. I find on my system there just is not a big speed difference between the two.

I find Epiphany to actually be less usable because the browser is too stripped of configuration tools. For example, If I click on a link it opens a whole new window in Epiphany. It gives no options whatsoever to have it open links in a tab or even to configure tabs. Firefox has a vanilla tab configuration tool and allows you add a extention that gives you many different options for tabs. Then there is the preferences menu. If I want multilple tabs to open upon start up on FF I just open the tabs in the order I want then just click Use Current Pages for the home page. Epiphany does not give you that option and will only load one tab at a time at startup. Firefox gives you six different configuration tabs in the preferences window while Epiphany only gives you four. Then these preferences tabs in FF give you a lot more options to configure the browser to your individual taste. 

Finally, Epiphany does not have a bookmarks toolbar by default and I find it difficult to add one. Yet Firefox has this by default making my most used sites accessible without having to browse through a bunch of bookmarks. Firefox's toolbar takes up the same real estate as Epiphany's yet still has the bookmark tabs toolbar. Firefox just does a better job at using valuable screen real estate because the layout is better thought out.

Epiphany is a fine browser but it just lacks too much for me and since FF 1.5 with fasterfox is just as fast (and slightly faster at rendering but not by much) I just do not see no real reason to use it unless I just thought that intergration with Gnome was the most important thing. I will continue to use Epiphany off and on to give myself more time to make a better judgement. But so far I am not impressed.

---

### Post by fuscia on 2006-03-01
if you visit the mozillazine forums, you'll find lots of advice on how to speed up firefox. most of the suggestions boil down to the tweaks that make up the *fasterfox*, or *tweak networks* extensions. although, somewhere in those forums is the suggestion that making the tweaks oneself, in *about:config*, rather than using extensions, will keep firefox from loading as slowly as it does when one uses more extensions.

i've played with a lot of the various suggestions for increasing speed in firefox and, for me, the only suggestions that sped up firefox noticeably, other than the *fasterfox* extension, were changing **network.http.version** and **network.http.proxy.version** from 1.1 to 1.0 and disabling java. one can also disable javascript, ssl 2.0 and 3.0 and tls 1.0, but if you are going to do that, you may just as well use dillo, which is way faster than all of them, including some of the text browsers.

---

### Post by Bragador on 2006-03-01
Plus Firefox has the oh so precious CustomizeGoogle extension ! [https://addons.mozilla.org/extensions/moreinfo.php?id=743&application=firefox](https://addons.mozilla.org/extensions/moreinfo.php?id=743&application=firefox)

Can't live without that now so I'm stuck with Firefox.

---

### Post by puccaso on 2006-04-21
i like it too
yea i love i guess
but whats stopping me from really loving it
is the tabs
i hate themmmmm, some nasty x on each tab --
is there no way i can remcompile or find howto somehow revert back to
the old tabing format, like tabs in firefoxx... where we have one x on the corner
like the firefox setup... one x on the corner for the current tab

---

### Post by Zodiac on 2006-04-21
Does anyone know if Epiphany has a "Bookmarks Toolbar"??

Last time I used it, it did not. Without that, it is a no go.

---

### Post by Wolki on 2006-04-21
[QUOTE=Zodiac]Does anyone know if Epiphany has a "Bookmarks Toolbar"??

Last time I used it, it did not. Without that, it is a no go.[/QUOTE]

Yes, it does. Maybe it's not enabled by default, I'm not sure right now. View -> Toolbars -> Edit Toolbars -> Add new Toolbar. Yo can then drag bookmarks there, add the main bookmarks hierarchy or individual tags, or right-click a bookmark in the manager and select "show in toolbar".

(at least in dapper, but iirc this was also possible with 2.12/Breezy)

---

### Post by abs on 2006-05-01
I was wondering, whats the deffrance between these two, for instance Epiphany renders things faster and handels memory alot better than firefox, however, firefox renders things nicely.

how can i get Epiphany to render things in the same way, i know this is an imposible question, but do i for instance have to file a bug report or something, both browsers use the same engine do they not.

Can anyone shed some light on this as i would really prefer to use Epiphany as its so integrated and fast.


cheers
----

---

### Post by Sef on 2006-05-01
I have noticed that epiphany is faster than firefox.   Partly it is lighter than fox.  Not sure why else.

---

### Post by dabear on 2006-05-01
epiphay uses the same backend as firefox to draw pages ('the gecko engine'), and epiphany uses gtk widgets instead of firefox' XUL. I find epiphany to be better, but again "flock" which is based on firefox is faster and better than both epiphany and firefox.

---

### Post by abs on 2006-05-01
i see,

I just hoped these browsers would render pages in the same way,

so looks like ill have to use firefox for some and others for Epiphynie, bummer :(

---

### Post by missmoondog on 2006-05-06
[QUOTE=nix4me]Has anyone noticed that Epiphany is faster than Firefox?

Firefox seems to be getting slower and slower.

nix[/QUOTE]

you mean firefox just seems to suck more and more? :confused: 

firefox is the slowest browser there is on any of my machines. i'd even use mozilla over firefox anyday, but i prefer opera, galeon and epiphany over either of those browsers.

---

### Post by zba78 on 2006-05-25
Tried Epiphany this morning for the first time for a few minutes. First reactions are that I&#8217;m very impressed. Pages certainly loaded much faster, as does the whole browser.
   
Not tried the smart bookmark thing (didn&#8217;t know they existed until reading this thread) but am looking forward to getting a google search bar.
   
One thing that impressed me the most is that ALL of the plugins from firefox work instantly. Java, flash (non-free version), mplayerplug-in. Even the new yahoo mail beta worked fine.

Could see myself switching if a bit more testing goes successfully

---

### Post by bruce89 on 2006-05-25
The smart bookmark thing is the best feature, but it's only in Ephy => 2.14.0

edit - I'm thinking of ways to make my signature funnier, suggestions?

---

### Post by quixotic-cynic on 2007-09-22
The one thing that stops me using Epiphany is that there is no equivalent to the cookie "Exceptions" on FF: I block all cookies by default and only whitelist the ones I want to allow.

Am I missing something? Is it actually possible?

Thanks if you know/can explain.

---

### Post by Pancetilla on 2007-09-22
> **zba78 said:**
> Not tried the smart bookmark thing (didn’t know they existed until reading this thread) but am looking forward to getting a google search bar

You don't need a google search bar, you already have one, just type the words you want in the adress bar, it serves as google search bar aswell. Don't know if you can change it to wikipedia, amazon or the likes, though...

---

### Post by Wolki on 2007-09-22
> **Pancetilla said:**
> You don't need a google search bar, you already have one, just type the words you want in the adress bar, it serves as google search bar aswell. Don't know if you can change it to wikipedia, amazon or the likes, though...

You can both add search engines to the dropdown (simply add a smart bookmark, they'll automatically appear there), and you can change the default engine (what happens when you just press enter instead of selecting a smart search), check keyword.URL in about:config

---

### Post by bruce89 on 2007-09-22
> **Pancetilla said:**
> You don't need a google search bar, you already have one, just type the words you want in the adress bar, it serves as google search bar aswell. Don't know if you can change it to wikipedia, amazon or the likes, though...

[http://en.wikipedia.org/wiki/Special:Search?search=%s&go=Go](http://en.wikipedia.org/wiki/Special:Search?search=%s&go=Go) is a Wikipedia search, bookmark it.

---

### Post by Wolki on 2007-09-25
> **quixotic-cynic said:**
> The one thing that stops me using Epiphany is that there is no equivalent to the cookie "Exceptions" on FF: I block all cookies by default and only whitelist the ones I want to allow.

Am I missing something? Is it actually possible?

With the new Epiphany, you can have it ask you and only allow the ones you want (per cookie or per site). Don't know if that's enough for you. See: [http://www.0d.be/2007/09/25/new-in-epiphany-2.20/](http://www.0d.be/2007/09/25/new-in-epiphany-2.20/)

---

### Post by quixotic-cynic on 2007-09-26
Thank you for taking the trouble to reply. I did try it like that but it was driving me absolutely nuts ;)

I may try disabling them by default and enabling cookies when I want to use them - but that is probably just as painful unfortunately.

---

### Post by Wolki on 2007-09-26
> **quixotic-cynic said:**
> Thank you for taking the trouble to reply. I did try it like that but it was driving me absolutely nuts ;)

I can definitely see that as being annoying. Positive side is that you only need to do it once per cookie (or site).

I'm not exactly sure how smart it is, if you enable it, visit all sites where you want cookies and allow them, then set it to "never allow cookies", does it keep the cookies it already has?

---

### Post by quixotic-cynic on 2007-09-26
I'm pretty sure it actually remembers the permissions of the cookies (so if you only allow session cookies it will still re-allow them next time)(afaik).

---

