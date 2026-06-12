---
title: "Which is the fastest browser? (the shocking truth...)"
date: 2007-01-16
forum: Recurring Discussions
---

### Post by floke on 2007-01-16
Ok, so I was bored...

Was reading some threads about browsers and decided to do my own incredibly scientific test to see which was the fastest.

The test times were based on a reload of the following link:

[http://scragz.com/tech/mozilla/test-rendering-time.php](http://scragz.com/tech/mozilla/test-rendering-time.php)

Reloads were made three consecutive times from a 1mbp wireless connection, and the average time was taken.
Browsers were running with no other programs running on the system.
Clearly, start-up times etc. are not included in the analysis - but the results were surprising.

Here they are (in reverse order)...

Firefox (!) 8.79 seconds (maybe this was due to my extensions??)
Swiftfox (!) 8.75
Epiphany 8.7
Opera 7.84 (that's more like it)
Konqueror - wins with 7.24 (and was running in gnome)

Blimey!

This make Konqueror 8.3% faster than Opera, its nearest rival, and a huge 21.4% faster than Firefox.

By my estimates, if I spend 3hrs a day on the web, then Konqueror will get me an extra 35 minutes worth of web-time - so, by this time tomorrow, the time saved will have compensated for the time spent on this experiment!

---

### Post by bodhi.zazen on 2007-01-16
Yes, extensions slow down firefox, which is why I cut down on them as much as possible ....

You should try firefox without extensions.

In a terminal type:

firefox -P

Create a new profile, say Test, then

firefox -P Test

This will give you a clean firefox to test :p

You can firefox -P and delete the profile later if you like ;)

Also, there are some mods you can do with firefox to make it faster.

Last, try a light weight browser like dillo. I often use dillo for speed and save firefox if I want graphics.

---

### Post by floke on 2007-01-16
Have just tried dillo - supadupa quick! But, unfortunately it doesn't do graphics, so couldn't get a reading on the test. Also, it's not very functional for quick use, since you can't do mouse gestures etc., so time saved on lightning quick downloads is lost elsewhere - still I was very impressed!

Haven't tried the bare FF yet (will do it tomorrow morning) - but think in advance that this might defeat the objective - since I want ad-blocking, mouse gestures, rewind, etc. for functionality.

Anyway, thanks for the tip :)

---

### Post by bodhi.zazen on 2007-01-16
LOL :lol:

Like i said:

> dillo for speed and save firefox if I want graphics ;)

8)

---

### Post by 23meg on 2007-01-16
> since you can't do mouse gestures etc., so time saved on lightning quick downloads is lost elsewhereThat would sum up why rendering speed doesn't necessarily mean overall operation speed.

---

### Post by mexlinux on 2007-01-16
> **Steve.K said:**
> 
Konqueror - wins with 7.24 (and was running in gnome)

Of course!

---

### Post by lotacus on 2007-01-16
heh. I get 4.32 seconds with Internet Explorer. :P

---

### Post by aktiwers on 2007-01-16
what about Lynx? :D

I get 6.5 with firefox and lots of extentions..

---

### Post by ardchoille42 on 2007-01-16
> **lotacus said:**
> heh. I get 4.32 seconds with Internet Explorer. :P

Which proves faster does not equal better :)

---

### Post by Bou on 2007-01-16
> **Steve.K said:**
> Here they are (in reverse order)...

Firefox (!) 8.79 seconds (maybe this was due to my extensions??)
Swiftfox (!) 8.75
Epiphany 8.7
Opera 7.84 (that's more like it)
Konqueror - wins with 7.24 (and was running in gnome)

Blimey!

5.85 using epiphany :D

---

### Post by ekravche on 2007-01-16
If you want true performance try lynx. It will blow every other browser out of the water! :)

---

### Post by floke on 2007-01-17
Internet explorer? Are people seriously still using it?
Proof, if ever it were needed, that evolution proceeds unequally!

Am envious about your epiphany time - what's your connection speed?

[EDIT: Have just tried Lynx - nearly as funny as IE! Are you serious? You do know that the world has moved beyond text-only don't you? How is this functional in any way? You should be forced to use IE for a week in Win '98 with no virus protection for suggesting such a thing]

---

### Post by PetePete on 2007-01-17
i'm at work (so being forced to use IE) and it loaded in 4.3 seconds 

maybe its something to do with the obscenly fast internet connection they have here though :D

---

### Post by Rui Pais on 2007-01-17
i get (based on 1 trial and with the credit that such method deserve ;)):
**brower   load    reload**
opera    4.643   4.993
swiftfox 6.296   6.237
firefox2(PT from mozilla site) 
  6.644   6.195
firefox1.5(dapper)
  7.397   6.533

most interesting... i download a copy of that page and redo from my home folder:
**brower   load    reload**
opera    2.287   2.175
swiftfox 1.803   1.764
firefox2(PT from mozilla site)   
  2.219   2.046 
firefox1.5(dapper)  
  2.186   2.175

if this mean anything... would be that opera is faster to access the web, and not -strangely- rendering the pages. Maybe tweaking with the settings (pipelines...) should deserve a better look.

About your saving of time... are you serious? for each 5 secs you hit a page you spend minutes (lots!!) reading it... 1 or 2 sec for each page don't mean a thing. Unleass you are a machine, random and mechanically access pages and quick step to another...

On the other side, a factor that irritates me a lot is starting times. Opera is kind of too slow for my taste, ubuntu versions are always too slow (never get why), konqueror the unique time i tried take ages and the really fast ones, in my box, are swiftfox and mozilla pre-compiled versions.



PetePete, of course page loading have to do with internet connection speed. You must test things with the same condictions. (Last time i used IE it was on a modem with 56k phone line and it was slow :lol: how many years??)

---

### Post by spockrock on 2007-01-17
here are my results, just rough

firefox ~6seconds
epiphany ~4.5seconds
opera ~2.0seconds
konqueror ~1.9seconds

all done in the a custom edgy ubuntu live disc.

granted konqueror was run in gnome, but it still was a bit faster then opera.  the results are making me think of switching my browser.

btw does running konqueror in gnome slow down web rendering? I cannot see it being slower if the kde libs are installed..... :s

btw changing the firefox pipelining and fasterfox extentions did nothing, and I ran the test on a clean firefox and then with the fasterfox extension.

---

### Post by 3rdalbum on 2007-01-17
Links2 in Graphical mode running on an X server: Lowest was 0.864, highest was 1.1.

This was while running Firefox, Gaim and XMMS.

Strangely enough, running it in Firefox gave me 24 seconds.

---

### Post by PetePete on 2007-01-17
im not an IE supporter or anything, but id still like to see somone who's got dual boot try the test with IE and firefox on windows.

---

### Post by floke on 2007-01-17
Rui Pais - of course I'm not serious about the time saved (although in the long-run it must all add-up!).

Also - remember the test was conducted on a 1mbs wireless connection, so comparisons with megafast connections at work are not scientific (which my original test obviously was ;) )

After seeing the results I was also tempted to switch to Konqueror, but I can't find how to use mouse gestures (or even if it supports them), so it was back to Opera (I like FF and Swifty, but also like switching for fun: variety being the spice of browsing life etc.).

I think I'd feel tainted if I booted into WIndows to try my IE and FF times, but might try it out of curiousity. The result though would be completely irrelevant, since even if IE loaded at the speed of light there's no way I would use it :mrgreen:

---

### Post by Rhapsody on 2007-01-17
I've now tested this with various browsers, all running on Kubuntu Edgy. Minefield, Gran Paradiso, and Mozilla Firefox are all the official versions from the Mozilla Foundation. Internet Explorer is being run through Wine. The average is taken from three consecutive reloads after the initial load of the page and rounded off to two decimal points.

**_Minefield 3.0a2pre (Build 2007011604)_**

1st reload: 12.551000118255615 seconds
2nd reload: 11.625999927520752 seconds
3rd reload: 11.80299997329712 seconds

Average time: 11.99 seconds

**_Gran Paradiso 3.0a1 (Build 2006120408)_**

1st reload: 14.047000169754028 seconds
2nd reload: 12.009 999990463257 seconds
3rd reload: 11.927000045776367 seconds

Average time: 12.66 seconds

**_Mozilla Firefox 2.0.0.1 (Build 2006120814)_**

1st reload: 13.246999979019165 seconds
2nd reload: 13.950999975204468 seconds
3rd reload: 13.605000019073486 seconds

Average time: 13.60 seconds

**_Konqueror 3.5.5_**

1st reload: 3.5960001945495605 seconds
2nd reload: 4.758999824523926 seconds
3rd reload: 4.681999921798706 seconds

Average time: 4.35 seconds

**_Opera 9.10_**

1st reload: 4.13100004196167 seconds
2nd reload: 5.098999977111816 seconds
3rd reload: 4.39900016784668 seconds

Average time: 4.54 seconds

**_Internet Explorer 6.0.2800.1106 SP1_**

1st reload: 6.107999801635742 seconds
2nd reload: 5.5299999713897705 seconds
3rd reload: 9.092999935150149 seconds

Average time: 6.91 seconds

---

### Post by sethvath on 2007-01-17
Rhapsody, all 3 mozilla browsers with a clean profile and no extensions?

---

### Post by Rui Pais on 2007-01-17
> **Steve.K said:**
> Rui Pais - of course I'm not serious about the time saved (although in the long-run it must all add-up!).
Sorry, i couldn't get if you are serious or not... 
(there are people who install the latest OOo or buy the latest MSOffice, 'cause they are faster and then use it to make documents full of clipart and typing with 1 or 2 fingers...)
> 
After seeing the results I was also tempted to switch to Konqueror, but I can't find how to use mouse gestures (or even if it supports them), so it was back to Opera (I like FF and Swifty, but also like switching for fun: variety being the spice of browsing life etc.).

Now you said a great truth. Switching and try is not only funny, but the way one discover things :)

There a lot more then a few secs on load. Usability, looks, habit, intuition (on a self-one base)... 
I, as an example, have a problem with opera. It draws the containers of images and objects faster and in a way much *visible* then others browsers. Ok it loads faster but i keep look for pages that seems to me more incomplete when load then FF or even mozilla, that most of the time just shows a blank page and then all text and eventually the bigger images and other heavy stuff. It's a different approach... but that keep refrains me from go back to opera. It annoys me every time i give it a try... 

Anyway this tests should always be looked with a open mind (a bit of salt is the english expression?)  
The greater of all tests is change to a new browser for a day or two and at the end try to avaliate you web surf experience in terms of usability, easiness and the way real world speed (not 1 page on 1 site) appears to you at a long day average. 
In that way i believe they all perform more or less the same. Wins the one who offers what you are more used too...

---

### Post by Rhapsody on 2007-01-17
> **sethvath said:**
> Rhapsody, all 3 mozilla browsers with a clean profile and no extensions?

Ah, forgot to mention. I've been using all three for a while (so no clean profile) and all have 17 extensions installed. The other browsers are fairly clean though.

---

### Post by floke on 2007-01-17
Using FF without extensions is like cutting off your nose to spite your face - why would you do it? so measurements of a 'clean' FF are, to me, pointless - since nobody (sane) does it!

Like Rui says, its all about functionality at the end of the day. Probably some mathematician could work out the proper formula...eg. where the 'optimal' browser is a function of speed, intuition/ease of use, functionality (itself being a function of security and doing the things you want it to, such as turning off adverts in Google - thanks FF for that!, mouse gestures etc.), stability, and aesthetics. 

Speed, though, is really the only one you can try to quantify I guess.

---

### Post by bear54 on 2007-01-24
I recently installed Ubuntu 6.06 on my Compaq Armada  e500 laptop. It has a 650 MHz CPU with 256 MB of RAM. It is running Gnome with Firefox. I also use a highspeed DSL connection to the internet. The problem I'm having is that the internet connection is slow almost like dial-up. When I had Mandriva 2006 edition installed the conection was super fast. Is there any way to speed up the connection? I love Ubuntu but this slow surfing the internet is very irritating to say the least! Any help would be greatly appreciated! Thanks 8)

---

### Post by presbp on 2007-01-24
.55 seconds for me in firefox with every extension downloaded for it.


Actually just kidding.  I got 17 seconds with firefox with imacros, url fixer, web developer, adblock plus, answers, forecastfox, foxytunes, talkback.  But I tried internet explorer 7 which has no extensions and it went at 16 seconds.  But if I want to go to google it takes less than a second.. gamespot.com takes about 1-2 seconds.

---

### Post by Rui Pais on 2007-01-24
> **bear54 said:**
> I recently installed Ubuntu 6.06 on my Compaq Armada  e500 laptop. It has a 650 MHz CPU with 256 MB of RAM. It is running Gnome with Firefox. I also use a highspeed DSL connection to the internet. The problem I'm having is that the internet connection is slow almost like dial-up. When I had Mandriva 2006 edition installed the conection was super fast. Is there any way to speed up the connection? I love Ubuntu but this slow surfing the internet is very irritating to say the least! Any help would be greatly appreciated! Thanks 8)

hi maybe you are suffering from the classic ipv6 slow/blocked internet problem... [check here]("http://ubuntuforums.org/showthread.php?t=87798")

---

### Post by aktiwers on 2007-01-25
try with links2

Install:
```
sudo apt-get install links2
```

Run:
```
links2
```CTRL + G 
opens URL box :)

---

### Post by SoggyCornflake on 2007-03-29
> **Bou said:**
> 5.85 using epiphany :D


I made a couple picky changes to what  you said in you signature:

I'm trying to improve my English, so please let me know if there's anything wrong in my message[SIZE="4"]**[COLOR="Red"].[/COLOR]** [/SIZE]  I'll appreciate it.
 
[SIZE="4"][COLOR="red"]**That** [/COLOR][/SIZE]applies to this signature, too.

[COLOR="Blue"]
I broke the first statement into two sentences  to make it more readable.

I changed it to that since I think most people would more naturally say [B]that.[/B[/COLOR]]

---

### Post by aysiu on 2007-03-29
Since this thread seems to have been revived, I've moved it to the Cafe, since it's basically a discussion (not a support) thread.

---

### Post by FuturePilot on 2007-03-29
I think those times are all off. I got 6.5 with Firefox and with all extensions too:)

---

### Post by mwolfe on 2007-03-29
I'm failing to understand how this would be a good measure of rendering time unless you were running this as a script on your localhost.. This test i'd say is much more dependant on your download speed than your browsers rendering time.. My times were usually about the same between firefox and opera, however it seeemed the time dropped in opera after i loaded it once whereas in firefox it stayed about the same from load to load. It was still a bit random though. Other factors include the fact that this page is created with php it would seem by generating random numbers in a table. I'm not sure if your script uses ob_flush to make sure than nothing gets sent until the script finishes running, but if not then your script time will be effecting output as well.. I understand you need the content to change due to caching but i'm not sure this is a very good representation of true rendering speed. I would take something more complex to determine realistic benefits to using a non mozilla browser. I don tthink mozilla's rendering is all that fast, however firefox gets better support than opera. And konquerer??? Well rendering is good (acid2) but it doesnt do **** in terms of javascript -- especially with ajax. So its pretty much useless fo rme since half the time i'm on the net i'm on a site that uses ajax.

---

### Post by RAV TUX on 2007-03-29
> **Steve.K said:**
> Ok, so I was bored...

Was reading some threads about browsers and decided to do my own incredibly scientific test to see which was the fastest.

The test times were based on a reload of the following link:

[http://scragz.com/tech/mozilla/test-rendering-time.php](http://scragz.com/tech/mozilla/test-rendering-time.php)

Reloads were made three consecutive times from a 1mbp wireless connection, and the average time was taken.
Browsers were running with no other programs running on the system.
Clearly, start-up times etc. are not included in the analysis - but the results were surprising.

Here they are (in reverse order)...

Firefox (!) 8.79 seconds (maybe this was due to my extensions??)
Swiftfox (!) 8.75
Epiphany 8.7
Opera 7.84 (that's more like it)
Konqueror - wins with 7.24 (and was running in gnome)

Blimey!

This make Konqueror 8.3% faster than Opera, its nearest rival, and a huge 21.4% faster than Firefox.

By my estimates, if I spend 3hrs a day on the web, then Konqueror will get me an extra 35 minutes worth of web-time - so, by this time tomorrow, the time saved will have compensated for the time spent on this experiment!

I thought Lynx and Dillo were faster.

---

### Post by floke on 2007-03-29
Yes but you don't get pictures. 
I like pictures.

:)

---

### Post by karellen on 2007-03-29
I care much more about how good the browser renders the pages than about speed. (for example the new my yahoo portal doesn't work with opera, so for now I have to use firefox even it's opera is a little faster overall). and all those fast-text browsers and/or konqueror which displays my gmail accout page soo poorly are no option for me.

---

### Post by floke on 2007-03-29
The limits of your browser mean the limits of your world;)

---

### Post by karellen on 2007-03-29
> **Steve.K said:**
> The limits of your browser mean the limits of your world;)

:). that was a nice one ;))

---

### Post by STREETURCHINE on 2007-03-29
i will just pop this in out of the blue,anyone used "galeon".i find it quite fast :)

---

### Post by karellen on 2007-03-29
> **STREETURCHINE said:**
> i will just pop this in out of the blue,anyone used "galeon".i find it quite fast :)

I use epiphany sometimes in ubuntu, it's almost identical with galeon

---

### Post by fuscia on 2007-03-29
i find opera much faster than konqueror. anytime i use kde, i'll try konqueror for a while (for the komplete experience), but it's always too slow so i end up switching back to opera.

---

### Post by RAV TUX on 2007-03-29
I find seamonkey the fastest

---

### Post by Tachyon_ on 2007-03-29
>  By my estimates, if I spend 3hrs a day on the web, then Konqueror will get me an extra 35 minutes worth of web-time - so, by this time tomorrow, the time saved will have compensated for the time spent on this experiment!

Okay, so you read the page **while** it's rendering and move to the next one in an instant :) 

If one reads one line of numbers in that page in 15 seconds, he uses 74985 (4999*15) seconds to read the whole page. You say that konqueror renders it in 7.24 seconds. Konqueror therefore uses more like 0.0001 (0,000096552644) percent of your surfing time in rendering (provided you cant really read the page in a second, that takes 20 hours to read for normal user). Your firefox uses more like 0.00011 (rounded) percent of time rendering.
So, the time difference in 3 hour browsing -provided that all pages contain similar content to render, no images etc.- is (3*3600*0,00011722344)-3*3600*0,000096552644 amazing **0.2 seconds !**

So now, you're not going to save 35 minutes ;)
I use konqueror too, but not for time saving.

EDIT: And how am I supposed to get my time back! :D

---

### Post by justin whitaker on 2007-03-29
> **Steve.K said:**
> [EDIT: Have just tried Lynx - nearly as funny as IE! Are you serious? You do know that the world has moved beyond text-only don't you? How is this functional in any way? You should be forced to use IE for a week in Win '98 with no virus protection for suggesting such a thing]

It is very, very functional. Spend some time with it, get used to the keyboard shortcuts....it is very fast, and if all you want is the content (that is, the actual text) it is one of the better ways to get it.

Just because we have GUIs for everything does not mean that we should automatically discredit text-mode....

---

### Post by fuscia on 2007-03-29
i like lynx, but reading forums on it is a nightmare.

---

### Post by spinflick on 2007-03-29
4.1 using Firefox

---

### Post by justin whitaker on 2007-03-29
> **fuscia said:**
> i like lynx, but reading forums on it is a nightmare.

On this one, to be sure...I use it to filter out all the advertisting crap on other forums, such as Gamers With Jobs. I really don't need to see everyone's avatar, the smilies, etc...just get me to the the time on the server, and get on with it!

---

### Post by aysiu on 2007-03-29
> **Steve.K said:**
> Yes but you don't get pictures. 
I like pictures.

:)
Actually, Dillo does give you pictures; though, it doesn't have a lot of perks of the other heavier-weight graphical browsers.

---

### Post by daynah on 2007-03-29
Considering I just have a difficult time wrapping my brain around how to use konqueror... I'm using the right browser! Yes!

Go Opera Go! Go Opera Go!

I love seeing fat ladies run. :)

---

### Post by Rui Pais on 2007-03-29
> **aysiu said:**
> Actually, Dillo does give you pictures; though, it doesn't have a lot of perks of the other heavier-weight graphical browsers.

well, something between dillo and heavier browsers may be [kazehakaze]("http://kazehakase.sourceforge.jp"). 
Although the version on repos is very old...

---

### Post by Mateo on 2007-03-29
> **justin whitaker said:**
> On this one, to be sure...I use it to filter out all the advertisting crap on other forums, such as Gamers With Jobs. I really don't need to see everyone's avatar, the smilies, etc...just get me to the the time on the server, and get on with it!

I read the forums with elinks, which is a fork of lynx.  I've never had a problem doing so.  it has tabbed browsing too.  You can open several forum threads by pressing Shift+T on the links to open a new tab in the background.

---

### Post by justin whitaker on 2007-03-29
> **Mateo said:**
> I read the forums with elinks, which is a fork of lynx.  I've never had a problem doing so.  it has tabbed browsing too.  You can open several forum threads by pressing Shift+T on the links to open a new tab in the background.

Nice tip! Thanks! I will install it tonight!

---

### Post by igknighted on 2007-03-29
> **karellen said:**
> I care much more about how good the browser renders the pages than about speed. (for example the new my yahoo portal doesn't work with opera, so for now I have to use firefox even it's opera is a little faster overall). and all those fast-text browsers and/or konqueror which displays my gmail accout page soo poorly are no option for me.

To be fair to opera, they are the most standards compliant browser of those tried.  So when websites do not load in Opera, it is because web devs aren't sticking to standards because other browsers aren't.

To the OP... Konqueror doesn't have mouse gestures at this time, but if your mouse has enough buttons you can map them to the forward/backward keyboard shortcuts (alt left and alt right) with xbindkeys.  It works really well.  I have two scroll wheels on my mouse, and I use one for scrolling the page and the other for forward back.  The other extra buttons are bound to beryl to rotate the cube and other various functions.  These extra button mice are really neat, I got mine for $10 US at Target, highly recommend checking them out.

EDIT: also, the fact that konqueror beat opera while in gnome doesn't impress me much... Opera is qt based as well, so should suffer about as much, yes?

---

### Post by Mateo on 2007-03-29
> **justin whitaker said:**
> Nice tip! Thanks! I will install it tonight!

hope you like it.  you might have to get used to the shortcut keys because i think they are a bit different.

one other nice feature elinks has is an equivalent of firefox's search bar.  when you press 'g' to bring up the new address screen, if you type 'g ubuntu' for example, it searches Google for the term ubuntu.  I think you can also set it up to work with other search engines, like 'y ubuntu' to search yahoo for ubuntu.  i'm not sure how to set these up though.

---

### Post by Arisna on 2007-03-29
> **igknighted said:**
> To the OP... Konqueror doesn't have mouse gestures at this time...

I think it's worth pointing out that Mouse Gestures can be created and configured globally with KDE.  In Kubuntu, at least, there is a built-in gesture set for Konqueror that is disabled by default.  I realize that this does not do non-KDE-users much good, though. :(

---

### Post by chavo on 2007-03-29
> **Arisna said:**
> I think it's worth pointing out that Mouse Gestures can be created and configured globally with KDE.  In Kubuntu, at least, there is a built-in gesture set for Konqueror that is disabled by default.  I realize that this does not do non-KDE-users much good, though. :(

Actually you can use khotkeys outside of KDE. I have used it before in Gnome and Xfce with no problems. System wide mouse gestures rock.

---

### Post by Erunno on 2007-03-29
> **igknighted said:**
> EDIT: also, the fact that konqueror beat opera while in gnome doesn't impress me much... Opera is qt based as well, so should suffer about as much, yes?

Opera uses an in-house toolkit called Quick or Swift (I always mix up the names) since 9.0 with some odd Qt dependencies. I never actually found out for what exactly the remaining Qt dependencies are for.

---

### Post by Colonel Kilkenny on 2007-03-29
> **Erunno said:**
> Opera uses an in-house toolkit called Quick or Swift (I always mix up the names) since 9.0 with some odd Qt dependencies. I never actually found out for what exactly the remaining Qt dependencies are for.

It's the save- and print-dialogs (I guess). And I'd say all menus (menubar etc.) as well are qt-based.

---

### Post by Stone123 on 2007-03-29
> **Steve.K said:**
> Ok, so I was bored...

Was reading some threads about browsers and decided to do my own incredibly scientific test to see which was the fastest.

The test times were based on a reload of the following link:

[http://scragz.com/tech/mozilla/test-rendering-time.php](http://scragz.com/tech/mozilla/test-rendering-time.php)

Reloads were made three consecutive times from a 1mbp wireless connection, and the average time was taken.
Browsers were running with no other programs running on the system.
Clearly, start-up times etc. are not included in the analysis - but the results were surprising.

Here they are (in reverse order)...

Firefox (!) 8.79 seconds (maybe this was due to my extensions??)
Swiftfox (!) 8.75
Epiphany 8.7
Opera 7.84 (that's more like it)
Konqueror - wins with 7.24 (and was running in gnome)

Blimey!

This make Konqueror 8.3% faster than Opera, its nearest rival, and a huge 21.4% faster than Firefox.

By my estimates, if I spend 3hrs a day on the web, then Konqueror will get me an extra 35 minutes worth of web-time - so, by this time tomorrow, the time saved will have compensated for the time spent on this experiment!

I've done this with reading of XML vs SQL with PHP . Well I got IE + wine as fastest . Not that it should effect XML vs SQL since its server side , but i had to test browers. And FF as slowest.

---

### Post by Nils Olav on 2007-03-29
Links2 won for me.

---

### Post by lian1238 on 2009-08-26
A poll would've been nice for this thread :D

---

### Post by itreius on 2009-08-26
> **lian1238 said:**
> A poll would've been nice for this thread :D
Because statistical data should be open to subjective opinions/interpretation? O.o

---

### Post by HappinessNow on 2009-08-26
> **floke said:**
> Ok, so I was bored...

Was reading some threads about browsers and decided to do my own incredibly scientific test to see which was the fastest.

The test times were based on a reload of the following link:

[http://scragz.com/tech/mozilla/test-rendering-time.php](http://scragz.com/tech/mozilla/test-rendering-time.php)

Reloads were made three consecutive times from a 1mbp wireless connection, and the average time was taken.
Browsers were running with no other programs running on the system.
Clearly, start-up times etc. are not included in the analysis - but the results were surprising.

Here they are (in reverse order)...

Firefox (!) 8.79 seconds (maybe this was due to my extensions??)
Swiftfox (!) 8.75
Epiphany 8.7
Opera 7.84 (that's more like it)
Konqueror - wins with 7.24 (and was running in gnome)

Blimey!

This make Konqueror 8.3% faster than Opera, its nearest rival, and a huge 21.4% faster than Firefox.

By my estimates, if I spend 3hrs a day on the web, then Konqueror will get me an extra 35 minutes worth of web-time - so, by this time tomorrow, the time saved will have compensated for the time spent on this experiment!

You left out a few browsers:

Google Chrome/Chromium
Flock
etc.
etc.

---

### Post by RabbitWho on 2009-08-26
9.57 with firefox... yay! what do i win?

---

### Post by MyR on 2009-08-30
Comparing benchmarks is only valid on the same system under similar conditions.

---

### Post by darco on 2009-08-31
Opera 10 RC..... 2.037 

Chromium 4.0.204.0 (Ubuntu build 24866) ...3.133

FF 3.0.13 ....3.26

darco

---

### Post by mrgnash on 2009-08-31
For me at least, a browser's resource usage is more important than how quickly it renders webpages.

---

### Post by jaxxstorm on 2009-08-31
I'd say Midori is lighter and quicker than all of the above. it's like lightning for me and has all the features I need of it.

---

### Post by sydbat on 2009-08-31
> **&#20170 said:**
> You left out a few browsers:

Google Chrome/Chromium
Flock
etc.
etc.Google wasn't making a browser when this thread was originally started in 2007. Damn threadcromancy...

---

### Post by insane_alien on 2009-09-02
3.68 seconds with firefox 3.5 and a bunch of extentions.

---

### Post by fela on 2009-09-02
4.316 with firefox 3.0 and a bunch of extensions ;)

---

### Post by sideaway on 2009-09-02
This test is rather flawed, I ran two tests in quick succession with the same browser...

10.2 seconds
7.5 seconds

wth?

---

### Post by calrogman on 2009-09-02
I just ran (very non-scientific this) time chromium-browser and closed the browser as fast as I could (like I said, not very scientific).

```
real	0m1.124s
user	0m0.588s
sys	0m0.308s
```

Do I win anything?

---

### Post by dcclabough on 2009-10-03
So I did some research on this, as the thread itself was not enough to get me to switch back to opera...

fastfox is the best gecko, but it still lacks the rendering speed of many others (relevant if you need to use gecko)...

midori is the only non mac browser i could find that passed acid3 (liked functionality more than the chromes too)...

epiphany is pretty baller, and it uses gecko and webkit (from what i can tell), but no forms management or ad blocking...

Konqueror has the most image extension support (might be good for someone who surfs a lot of image heavy sites)...

in the end though... pound for pound... I have to *subjectively* choose Opera.  when you weigh the unmatched functionality vs speed vs aesthetically pleasing experience, it comes out on top.

Now, I just have to figure out how to map my thumb buttons (thats why i tried ff in the first place... by the way... ff's addon for speed dial is atrocious [midori has speed dial too btw])

[solved] xbindkeys (works in nautilus too... yay!!!)

hope that helps someone out there... again

---

### Post by dragos240 on 2009-10-03
Links is teh fastest browser.

---

### Post by motang on 2009-10-03
> **RAV TUX said:**
> I find seamonkey the fastest

Finally someone mentioned it. I love Seamonkey 2, and I got 3.8 seconds with it!

---

### Post by tzs on 2009-10-04
> **floke said:**
> 
By my estimates, if I spend 3hrs a day on the web, then Konqueror will get me an extra 35 minutes worth of web-time - so, by this time tomorrow, the time saved will have compensated for the time spent on this experiment!

You can only conclude that from your experiment if when you normally spend time on the web, you reload each page you visit 3 times. :)

---

### Post by renkinjutsu on 2009-10-04
This count for anything? :D

---

### Post by hoppipolla on 2009-10-04
Ah the days before Google Chrome! lol :)

---

### Post by renkinjutsu on 2009-10-04
> **hoppipolla said:**
> Ah the days before Google Chrome! lol :)
i've always wanted to try the "/thread" thing.. :roll:

---

### Post by hoppipolla on 2009-10-04
> **renkinjutsu said:**
> i've always wanted to try the "/thread" thing.. :roll:

hehehe! And I finally actually understand your image (I've never tested browser rendering times before) and wow that really is fast :)

Chromium on here did it in 4.something :)

---

### Post by renkinjutsu on 2009-10-04
> **hoppipolla said:**
> hehehe! And I finally actually understand your image (I've never tested browser rendering times before) and wow that really is fast :)

Chromium on here did it in 4.something :)

```
time chromium-browser --enable-plugins --enable-extensions --enable-user-scripts

```
```
real	0m0.395s
user	0m0.177s
sys	0m0.044s

```:D

love this browser... i wish it would let be PRINT though..

---

### Post by surfed on 2009-10-04
Firefox3.5 5.01 (lots of extentions) 
Opera 5.35
Konqueror 5.20
IE8 (in virtualbox3 winxppro clean install) 4.83

So for some reason that makes my FF faster than Opera or Konqueror....

Intel Quad 9550
4gb Ram
Jaunty 64bit

---

### Post by d3v1150m471c on 2010-01-05
From personal experience, i strongly suggest switching to "swiftfox". When i installed it, it kept all my firefox settings AND plugins/addons, which was extremely nice. I also noticed a 100-300 kb/s increase to my download speeds, my ping is about 20 ms faster, and my upload speed improved by approximately 50 kb/s. [www.speedtest.net]("http://www.speedtest.net") , give it a shot. 

Also, look into turning on pipelining and if your computer can spare the RAM, i'd suggest running your browser out of it. For me, it runs temendously faster. 

A few good websites :

[http://swik.net/Ubuntu/Only+Ubuntu/How+to+Optimize+your+Internet+Connection+using+MTU+and+RWIN/cbnda](http://swik.net/Ubuntu/Only+Ubuntu/How+to+Optimize+your+Internet+Connection+using+MTU+and+RWIN/cbnda)

[http://www.techradar.com/news/software/applications/8-hacks-to-make-firefox-ridiculously-fast-468317](http://www.techradar.com/news/software/applications/8-hacks-to-make-firefox-ridiculously-fast-468317)

There is plenty of advice floating around like this which will vary in results from user to user and computer to computer. IE blocking flash actually made my browser slower. Also, you cannot add more than 8 pipelines, as firefox (or swiftfox) sets any integer above 8 to 8.

---

### Post by Ylon on 2010-01-05
Opera 10.10 7.4
Opera 10.50 (pre-alpha for linux) 14.52 :popcorn:


On IBM Thinkpad T42

---

### Post by MichealH on 2010-01-05
Google Chrome Beta I am using It now and I have never browsed the forums this fast it is like I have upgraded my internet package form 10/Mbts to 100/Mbts

---

### Post by gradinaruvasile on 2010-01-05
Chromium 4.0.290.0 (35464) -  2.8
This is with 9 other tabs open, extensions loaded.

---

### Post by alakazam on 2010-01-05
3.73    Firefox Mac 8)
)

---

### Post by del_diablo on 2010-01-06
Randomly from 4,8 to 16,+!
This test seems extremely fishy.
Opera 10.10 on Windows XP with a ye old dated Intel Centrino :P

---

### Post by docus on 2010-01-06
5.84 using IE6 (at work)...

Will try it with Midori at home later.

---

### Post by d3v1150m471c on 2010-01-09
Can chrome be configured to use axel? I heard chrome was uber fast and i'm stuck using ppp0 for a while so i'll take whatever extra speed i can get.

---

### Post by aktiwers on 2010-01-10
Chrome:1.9779999256134033
Firefox: 4.50600004196167

I miss the times when Firefox was the fastest browser :(

---

### Post by d3v1150m471c on 2010-01-10
Firefox (swiftfox, truth be told which basically identical to firefox) is the fastest browser i've found actually with some modifications. The only one i haven't tried yet is chrome.

---

### Post by Regenweald on 2010-01-10
Opera 10.5 alpha. Not stable though.

---

### Post by Barrucadu on 2010-01-10
I get 2.4 in Opera 10.10, and 3.3 in Opera 10.50.

---

### Post by bashveank on 2010-01-10
1.55 on Chrome
4.46 on IE8
5.19 on Firefox

They seem to fluctuate quite a bit though. Chrome is the only one that stayed consistent. IE and FF both varied by 3 or 4 seconds.

---

### Post by kk0sse54 on 2010-01-10
Opera 10.10 - 2.8440001010894775
Chrome - 3.308000087738037
Firefox 3.5.7 - 5.953999996185303
IE 8 - 7.0929999351501465

---

### Post by juancarlospaco on 2010-01-11
*eLinks is the fastest...*

---

### Post by starcannon on 2010-01-11
> **juancarlospaco said:**
> *eLinks is the fastest...*
Lynx is faster still.

---

### Post by juancarlospaco on 2010-01-11
> **starcannon said:**
> Lynx is faster still.

We need a benchmark Lynx VS eLinks2 :)

---

### Post by ~sHyLoCk~ on 2010-01-12
> **juancarlospaco said:**
> We need a benchmark Lynx VS eLinks2 :)

Throw in w3m ;)

---

### Post by rookcifer on 2010-01-14
OP,

It's no surprise that Konqueror is faster than the others in your test as it uses a faster rendering engine (KHTML) and is the engine Apple modified to create Safari.

You didn't list Chrome I noticed.  I would wager it would outperform Konqueror.

---

### Post by Matt_Johnson on 2010-01-14
> **mexlinux said:**
> Of course!
I have fasterfox and other plugins and its been faster for me :l

---

### Post by Marvin666 on 2010-01-15
38 the first try, 8 the second one, and 5 for all subsequent ones. I have a very large cache that is infrequently if ever cleared, so most of my browsing is pretty fast. Firefox loaded with addons over a 600k peak connection (300-400k typical). It should be faster once I tweak firefox's config, and get a new router.

---

### Post by DrTravia on 2010-02-06
Opera first time 2.67 seconds
Opera Second time 2.35 seconds

Firefox first time 27.48 seconds 
Firefox second time 8.82 seconds

Any questions?

lol......

2000k connection lets you know which browser is up for it. :popcorn:

I ran this off my brothers computer using an ubuntu cd (try it before you use it option) but I've already done this on my desktop with basically the exact same results, except firefox got a 23 second hit on the first time

hehe let me know if anyone beats 2.35 seconds, I want to see a screeny of it ;)

---

### Post by mwolfe on 2010-02-07
I have a slow network so I can't really test the page over the network. Instead, I saved the file locally and ran it in a few different browsers. Honestly though, this is the only real way to test this and compare results with others.
Windows 7 Home Premium 64 bit, Athlon II X4 620 Quad core@2.6 ghz,
6GB of ram. NVideo geforce 9100

Results:
IE 8        - 2.65s (2.61 - 2.68 )
Firefox 3.6 - 2.1s (1.7 - 2.4) 
Opera 10.10 - 0.74s (0.69-0.82) 
Chrome 4.0  - 0.52s (0.51-0.54)

---

### Post by lotuspsychje on 2010-02-25
> **aktiwers said:**
> try with links2

Install:
```
sudo apt-get install links2
```Run:
```
links2
```CTRL + G 
opens URL box :)


very cool thank you for this, im a lynx fan and this one even rox more

---

### Post by pratikk on 2011-06-24
> **PetePete said:**
> im not an IE supporter or anything, but id still like to see somone who's got dual boot try the test with IE and firefox on windows.

I dual boot with XP. FF with developer extensions is about the same speed as IE
no-addons and  perceptibly faster when a whole lot of tabs are open. 

I'm surprised that this discussion mentions Lynx, which was great about 15 years ago, but not Midori. I use it routinely when I don't need bells and whistles but have to sift through large volumes of info very quickly. In fact, it's my default graphical browser now. Konqueror comes second. Lucid + XFCE + Midori works very fast for me.

---

### Post by el_koraco on 2011-06-24
Midori. Chrome does't come close.

---

### Post by beew on 2011-06-24
Why are you in such a rush?

---

### Post by pratikk on 2011-06-24
> **beew said:**
> Why are you in such a rush?

er, because speed was the issue at the time. different time. sorry, mahakal.

---

### Post by Maheriano on 2011-06-24
This is a better browser comparison: [http://en.wikipedia.org/wiki/Acid3](http://en.wikipedia.org/wiki/Acid3)

---

### Post by FlameReaper on 2011-06-26
Can't really give a damn about fastest browsers or anything; if they can't do the job I need them to then they fail with no exception.

Some other parts of the globe *require* me: 

1. Use a freaking Firefox/Chrome/Opera you can use IMEs in...
2. ... oh, not to forget, be able to use IMEs in Flash(!!!) applets. So far only ibus does the magic for me.

... in which speed is basically a moot point...

---

### Post by juancarlospaco on 2011-06-27
Im learning HTML5, the only browsers that works properly are the WebKit (KDE HTML) based,
i hope some day i can do sudo apt-get install firefox-webkit

---

