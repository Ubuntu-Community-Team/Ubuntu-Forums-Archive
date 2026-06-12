---
title: "HOW-TO: Firefox Network Performance"
date: 2005-04-11
forum: Outdated Tutorials &amp; Tips
---

### Post by Heliode on 2005-04-11
**Intro** 
Hello boys and girls, and welcome to the Heliode crash course of successful Firefox tweaking! We'll talk about speeding the thing up, what plugins there are, what some useful extensions are and what to do with them, and more!

First, lets get you a little utility that'll come in handy later, [ChromEdit](http://cdn.mozdev.org/chromedit/). This'll give you an easy (and platform independent) way to edit your user files. Go on and grab it, and restart firefox once its installed to make it work. Notice the new option under 'Extra'.

**Speed it up!** 
Now, lets talk about speeding the thing up. There are a couple of things you can do, depending on the situation. There are tweaks common to all configurations, but also specifically for fast computers with fast connections, for slow computers and fast connections, and so on. Go get them [here](http://www.testingreflections.com/node/view/1549).
Now you can use ChromEdit to just copy and paste those into your user.js.
Next we'll turn off ipv6 support. Don't forget to turn this back on later when the whole internet switches to in in what, 10 years? Anyway, type (in the address bar) 'about:config' (without the quotes) and use the filter to look for 'ipv6'. Set it from false to true.
Don't expect miracles with this but if you spend a lot of time online even the slightest improvement would be a good thing right? Right. 

**Ad blocking** 
Now, lets talk about enhancing your browsing experience even more; lets get rid of all the ads that clutter pages up and use the most annoying tactics to try and get your attention. Head over to [this page](http://www.mozilla.org/support/firefox/adblock) and, using ChromEdit again, copy/paste that stuff into your userContent.css.
That by itself should get rid of a lot of ads, but we want to get rid of all of them right? That's what I thought. 
So, lets get the [Adblock extension](https://addons.update.mozilla.org/extensions/moreinfo.php?application=firefox&version=1.0&os=Windows&category=Miscellaneous&numpg=10&id=10)! Install this, and restart firefox to make it work. Now, this thing by itself won't do anything; you'll need filters. Of course you can make your own, but since someone else has already done so you can just use that and save yourself a lot of time. Go to [this regularly updated page](http://www.pierceive.com/), grab the latest filter and import it into adblock with Extra -> Adblock -> Preferences -> Adblock options -> Import filters.
That, combined with the thing you copied to your userContent.css, should take care of ALMOST anything. What it doesn't take care of you can always block yourself; right click on whatever and select 'Adblock Image' or even 'Adblock iFrame'. You can even get a list of all blockable 'content' on the current page by clicking on 'Adblock' in the lower right hand corner of your firefox window.
There's just one other little thing, and that's [FlashBlock](https://addons.update.mozilla.org/extensions/moreinfo.php?application=firefox&version=1.0&os=Windows&category=Web%20Annoyances&numpg=10&id=433).
What that thing does is sort of 'pause' flash animations so you can click on them if you actually want to see them (for me, this isn't the case for about 99% of them).
 
I personally can't live without this anymore. What really sets Adblock apart from all the other things i've seen is that it actually removes the blocked items from the layout of the page, so you get more room for the actual content. You only really appreciate it when, after a while, you're forced to use a PC with only IE and get reminded of what the internet used to be like ;)

**Plugins** 
Now, that takes care of speed optimisation and ad blocking; lets talk about plugins!
Now, there are plenty of topics that talk about integrating Mplayer with firefox so I won't go into that; just take look around ;)
The easiest plugins to get going are Acrobat Reader, Flash Player, Java and Realplayer. Check out [this page](https://pfs.mozilla.org/plugins/) for the list and some URL's.
To get Java going you'll want to take a look at [the excellent Ubuntu Wiki Java Howto](http://www.ubuntulinux.org/wiki/AddingJavaSupport/view?searchterm=java).
Now, you'll notice there is no support for Quicktime and Shockwave, but i'm using them anyway, with [Crossover Office](http://www.codeweavers.com/)! This nice little application gives you basically an improved version of WinE with a nice GUI. I personally use it to run Studio MX, Photoshop 7, Office 97, Borland Delhpi 7, and also Quicktime and Shockwave player. Sadly, Crossover Office isn't free but you can at least take a look at the trial version and *buy it if you like it*(tm)!

**RSS**
I also highly recommend the use of [RSS](http://en.wikipedia.org/wiki/RSS_%28file_format%29) (thanks poofyhairguy) feeds. Most major news outlets offer some kind of RSS feed, and you can take advantage of that using firefox! Personally I have my entire Bookmarks Toolbar filled with 'live bookmarks' (RSS feeds). A good example is [SlashDot](http://slashdot.org). Notice the orange icon in the lower right portion of the screen. Click on it. Don't be shy! An option will pop up for you to subscribe to the feed, and there you have it!
However, the nice orange icon will only show up if the RSS feed is sort of advertised in the html of the page itself. There are sites that do offer RSS, but don't advertise them like that. No problem though! Just figure out where they hid it, and go to Bookmarks -> Bookmark manager. There, look under 'File' and click on 'New live bookmark' and enter a name and the location of the feed you just found. Just thought mentioning this might be useful since they kind of hid this function in there. 

**Other** 
Next are not really tweaks, but some handy things to know if you use Firefox a lot; keyboard shortcuts!

- Ctrl+N                                : Open a new window
- Ctrl+T                                : Open a new Tab
- F6                                      : Jump to the address bar
- Middle mouse button on link: Open link in new tab
--{list incomplete, post suggestions to complete it!}--

**Outro**
Well, there you have my little howto! Let me know how you liked it, and feel free to offer suggestions so we make it (even more ;)) complete!
I'd also like to take the opportunity to thank the Mozilla team for such a great product. Thanks guys, you're the best!


(note to the mods: sorry for cross-posting this but I really wanted this in the 5.04 howto forum  ;-) )

---

### Post by lao_V on 2005-04-11
Great post heliode!! I like to also change the following line to true to make sure all my links open in new tab in the foreground. 

browser.tabs.loadInBackground = false

---

### Post by poofyhairguy on 2005-04-11
Great Howto, I really notice a difference. Very good job. I browse for hours everyday, so this is great.

You stimulated my interest in RSSes. This article helped me a lot:

[http://en.wikipedia.org/wiki/RSS_%28file_format%29](http://en.wikipedia.org/wiki/RSS_%28file_format%29)

EDIT: You should add a link to this from the stater's guide.

---

### Post by orvalax on 2005-04-11
Excellent post Heliode. I'm at school right now and then I have work later so I won't be able to try in out till i get back home. But like i said, this is an excellent HowTo. Thank you and Long Live Ubuntu.

---

### Post by mrbass on 2005-04-11
Excellent write up.  Only thing I missed from mozilla is ability to easily disable image animations.  Easy way to do it in firefox is install Web Developer extension [http://www.chrispederick.com/work/firefox/webdeveloper/](http://www.chrispederick.com/work/firefox/webdeveloper/)

---

### Post by link on 2005-04-11
Nice post, though your heavy usage of the exclamation point makes it read a bit like a user car salesman speech. ;)

---

### Post by beeldings on 2005-04-11
A wonderful post, you're an asset to the Community. My web browsing is almost ad-free. If there was a tool to block those annoying "Sponsored Links" from displaying in Google, then I'd be completely ad-free.

---

### Post by poofyhairguy on 2005-04-12
I just did it on my girlfriend's computer and again it worked good. One of the top ten howtos IMHO.

---

### Post by wmcbrine on 2005-04-13
[QUOTE=mrbass]Only thing I missed from mozilla is ability to easily disable image animations.[/QUOTE]
about:config
image.animation_mode

Set it to "once" for a single loop through, or "none" to disable GIF animation completely.

Once you've done that, you may want to add the "Replay Animation" extension for those rare cases where it's actually worth viewing:

[http://www.extensionsmirror.nl/index.php?showtopic=2315](http://www.extensionsmirror.nl/index.php?showtopic=2315)

---

### Post by kuleali on 2005-04-13
nice howto  :smile:

---

### Post by localzuk on 2005-04-13
In order to stop most of the annoying pop-unders that are appearing now:

[http://safercomputing.co.uk/site/content/view/23/](http://safercomputing.co.uk/site/content/view/23/) - the site is currently under heavy construction... Works though.

---

### Post by Heliode on 2005-04-15
Recently a couple of ways have been found to get past firefox's pop-up blocker.
If you really, REALLY hate pop-ups, you might want to try the [Pop-ups must die](http://weblogs.mozillazine.org/asa/archives/007860.html)  extention. The link goes to the blog of a Mozilla developer. The technology used in the extension might make it to the next version of firefox, but right now I think its a little bit TOO powerful, since it also blocks things I actually WANT to see. Firefox notifies you of course, and you can ajust the settings to display them anyway, but it can be annoying.
Just thought i'd mention it for those of you that are really allergic to pop-ups ;)

---

### Post by Triton on 2005-04-15
Here are a few more settings to add:

user_pref("network.http.keep-alive.timeout", 30);
user_pref("network.http.request.max-start-delay", 5);
user_pref("network.http.connect.timeout", 30);
user_pref("network.dnsCacheExpiration", 86400);
user_pref("network.dnsCacheEntries", 1024);
user_pref("network.ftp.idleConnectionTimeout", 60);
user_pref("content.maxtextrun", 8191);

Edit:

Here's the filterset I use for Adblock [Filterset.g](http://www.geocities.com/pierceive/adblock/2005-04-12a.txt) this filterset is updated, so check it often.

---

### Post by Sionide on 2005-05-24
What do those settings do?

---

### Post by rooster on 2005-05-31
Hi lao_V,

this is something I searched for days after I switched to a new computer - thank you very much for the hint!

Oliver

[QUOTE=lao_V]Great post heliode!! I like to also change the following line to true to make sure all my links open in new tab in the foreground. 

browser.tabs.loadInBackground = false[/QUOTE]

---

### Post by veritas366 on 2005-05-31
Not to sound too stupid, but I found no documentation on chromedit...so how do you access it?  I installed the extension.

---

### Post by Mez on 2005-06-01
[SIZE=4]_**Basic Streamlining**_[/SIZE]

1.Type "about:config" into the address bar and hit return. Scroll down and look for the following entries:

network.http.pipelining network.http.proxy.pipelining network.http.pipelining.maxrequests

Normally the browser will make one request to a web page at a time. When you enable pipelining it will make several at once, which really speeds up page loading.

2. Alter the entries as follows:

Set "network.http.pipelining" to "true"

Set "network.http.proxy.pipelining" to "true"

Set "network.http.pipelining.maxrequests" to some number like 10. This means it will make 10 requests at once, rather than one

3. Lastly right-click anywhere and select New-> Integer. Name it "nglayout.initialpaint.delay" and set its value to "0". This value is the amount of time the browser waits before it acts on information it receives

[SIZE=4]_**Advanced Streamlining**_[/SIZE]

By now you should be used to chnaging the settings, so I'll list only the basics

The below are advanced streamlining techniques

_**All Computers**_

network.http.pipelining = true
network.http.pipelining.firstrequest = true
network.http.pipelining.maxrequests = 10
nglayout.initialpaint.delay =  0
network.http.proxy.pipelining = true
content.notify.backoffcount = 5
plugin.expose_full_path = true
ui.submenuDelay = 0

_**Fast Computer, Fast connection**_

content.interrupt.parsing = true
content.max.tokenizing.time = 2250000
content.notify.interval = 750000
content.notify.ontimer = true
content.switch.threshold = 750000
nglayout.initialpaint.delay = 0
network.http.max-connections = 48
network.http.max-connections-per-server = 16
network.http.max-persistent-connections-per-proxy = 16
network.http.max-persistent-connections-per-server = 8
browser.cache.memory.capacity = 65536

A couple settings of note - Firefox is allocated 4096 KB of memory by default and in this configuration we give it roughly 65MB as denoted by the last line. This can be changed according to what is used.

_**Fast Computer, Slower Connection**_

This configuration is more suited to people without ultra fast connections. We are not talking about dial up connections but slower DSL / Cable connections.

 content.max.tokenizing.time = 2250000 
 content.notify.interval = 750000 
 content.notify.ontimer = true 
 content.switch.threshold = 750000 
 network.http.max-connections = 48 
 network.http.max-connections-per-server = 16 
 network.http.max-persistent-connections-per-proxy = 16 
 network.http.max-persistent-connections-per-server = 8 
 nglayout.initialpaint.delay = 0 
 browser.cache.memory.capacity = 65536 

_**Fast Computer, Slow Connection**_

 browser.xul.error_pages.enabled = true 
 content.interrupt.parsing = true 
 content.max.tokenizing.time = 3000000 
 content.maxtextrun = 8191 
 content.notify.interval = 750000 
 content.notify.ontimer = true 
 content.switch.threshold = 750000 
 network.http.max-connections = 32 
 network.http.max-connections-per-server = 8 
 network.http.max-persistent-connections-per-proxy = 8 
 network.http.max-persistent-connections-per-server = 4 
 nglayout.initialpaint.delay = 0 
 browser.cache.memory.capacity = 65536 

_**Slow Computer, Fast Connection**_
 content.max.tokenizing.time = 3000000 
 content.notify.backoffcount = 5 
 content.notify.interval = 1000000 
 content.notify.ontimer = true 
 content.switch.threshold = 1000000 
 content.maxtextrun = 4095 
 nglayout.initialpaint.delay = 1000 
 network.http.max-connections = 48 
 network.http.max-connections-per-server = 16 
 network.http.max-persistent-connections-per-proxy = 16 
 network.http.max-persistent-connections-per-server = 8 
 dom.disable_window_status_change = true 

One of the changes made for this particular configuration is the final line where the status bar is disabled for changing web pages to save processor time.
[U]
**Slow Computer, Slow Connection**[/U]

We have entered the doldrums of the dial-up user

 content.max.tokenizing.time = 2250000 
 content.notify.interval = 750000 
 content.notify.ontimer = true 
 content.switch.threshold = 750000 
 nglayout.initialpaint.delay = 750 
 network.http.max-connections = 32 
 network.http.max-connections-per-server = 8 
 network.http.max-persistent-connections-per-proxy = 8 
 network.http.max-persistent-connections-per-server = 4 
 dom.disable_window_status_change = true

Let me know how these affect you!

---

### Post by byen on 2005-06-01
whoa... is it just me or is it my version...for some reason im able to find about 25% of the ones listed....

---

### Post by shakin on 2005-06-01
Let's just remember *why* these options default to slower settings: compatibility.

'nglayout.initialpaint.delay = 0' will cause the page to load with more jerkeyness since rendering begins before much of the HTML is downloaded. Note that this setting often actually slows down the time it takes to render the whole page, but may appear to be faster since you start seeing things on screen sooner. It may not slow down high-end computers, but it will definitely not speed up anybody's page rendering time. Though I haven't tested it, I'd bet that setting this number higher than the default .5 seconds might actually be a better performance boost on sites with a large amount of html.

Pipelining is the biggest performance improvement and probably the only one most people will notice a speed gain from, but the speed comes at the cost of some pages not rendering properly. People who have this enabled and have noticed some broken pages should probably disable this feature and try those pages again. Decide on your own if it's worth the broken pages.

---

### Post by bored2k on 2005-06-01
[QUOTE=byen]whoa... is it just me or is it my version...for some reason im able to find about 25% of the ones listed....[/QUOTE]
 Well I have nothing with the name "content" in it.
But the pipeline+ipv6 off trick work :)

I suppose we have to make some of them.

---

### Post by Chuck Adams on 2005-06-01
There is no point in setting max pipeline requests above 8.  Anything higher than 8 will become 8. 

Pipelining does not send multiple requests at once.  It sends them in sequence, on the same connection, so there isn't any extra overhead of establishing the connection.  Pipelining is broken on a lot of servers, so if you start having to reload to refresh images that are mysteriously broken, you might need to set this back down.

Setting the initial paint delay to 0 is nice if you like seeing lots of reflows, but it will *always* make it load slower in actual time -- you're just doing more paints for the same amount of data.  For short pages or really fast connections, the browser always forces a paint when it receives all the data -- it doesn't wait for the paint delay.  It might look faster though, which I suppose counts for some people.

Changing the UI submenu delay will result in annoying "flicker" as cascading menus pop up when you just pass the mouse over them.  If you have one cascading menu right below another, you'll probably end up popping the wrong menu out when you move the mouse on a diagonal path to reach a menu item.  In short, it makes cascading menus even more annoying than they were already.

If you turn on XUL error pages, grab the "show failed URL" extension, which makes firefox's fail page approach the usefulness of IE's.  I can't believe they still use modal popups by default, and that the XUL pages are still so incomplete.

---

### Post by gyjanos on 2005-06-01
My favourite Firefox keyboard shortcuts
[HTML]'		find as you type link
/		find as you type text
C-h		history
C-g		find again
C-S-g		find again backwards
C-TAB		next tab
C-PGDN		next tab
C-PGUP		prev tab
A-Enter		open address in new tab
C-0		restore text size
A-d		select location bar
C-l		select location bar
C-1		select tab 1 (to 9)
[/HTML]
The full list of keyboard shortcuts is here:
[http://www.mozilla.org/support/firefox/keyboard](http://www.mozilla.org/support/firefox/keyboard)

---

### Post by Mez on 2005-06-01
[QUOTE=byen]whoa... is it just me or is it my version...for some reason im able to find about 25% of the ones listed....[/QUOTE]
 If they don't exist, create them

---

### Post by krusbjorn on 2005-06-01
[QUOTE=byen]whoa... is it just me or is it my version...for some reason im able to find about 25% of the ones listed....[/QUOTE]


easiest way is just to open ~/.mozilla/firefox/*your default firefox profile*/user.js with a text editor,  and paste the lines into that file.

---

### Post by FLeiXiuS on 2005-06-20
****RECOMMENDED FOR BROADBAND USERS ONLY****

Ok so I'm sure a vast majority of you have had problems with firefox running slowly.  Not only is it the IPv6/4 strings but a enormous amounts of others.

So whats the catch?  ABSOLUTELY NOTHING!  It's all about tweaking and this is how I did it.  

(Credits to google/memphis users for explaing a majority)

Open firefox and in the address bar enter:
```

     $ about:config 

```
For the following below you can enter a portion of the string as a quicker way of finding it :-).
```


     $ browser.tabs.showSingleWindowModePrefs = true

     $ browser.xul.error_pages.enabled = true

     $ network.dns.disableIPv6 = true

     $ network.http.max-connections = 48

     $ network.http.max-connections-per-server = 24

     $ network.http.max-persistent-connections-per-proxy = 12

     $ network.http.max-persistent-connections-per-server = 6

     $ network.http.pipelining = true

     $ network.http.pipelining.maxrequests = 8

```
After this, restart firefox and voila.  Light-speed at the palm of your hands.

Other firefox customization guides, thankyou notos.
[http://ubuntuforums.org/showthread.php?p=218169](http://ubuntuforums.org/showthread.php?p=218169)

---

### Post by JimmyJazz on 2005-06-20
seems to work, thanks.

---

### Post by poofyhairguy on 2005-06-20
Can you please take away the $ signs so I can cut and paste into the filter flexi?

---

### Post by moment on 2005-06-20
Can you please explain what these parameters are? Why they are not the default then?

---

### Post by luca_linux on 2005-06-20
Great job!

---

### Post by Toddy on 2005-06-20
There is a "Tweak Network" firefox extension ([http://www.bitstorm.org/extensions/tweak/](http://www.bitstorm.org/extensions/tweak/)) that does many of these changes.

---

### Post by XDevHald on 2005-06-20
VERY impressive :)

---

### Post by Sionide on 2005-06-20
Are the differences really very noticeable?

---

### Post by jdong on 2005-06-20
Let's discuss this:

     $ browser.tabs.showSingleWindowModePrefs = true

Not speed related. In Advanced Settings and Tabbed Browsing, you'll see the "open new windows in tabs" option, which clones Opera's MDI browsing.

     $ browser.xul.error_pages.enabled = true
try [http://abcd.efg.nonexistent/](http://abcd.efg.nonexistent/) . New-style XUL error pages instead of alert boxes. More of a cosmetic tweak than a performance one.

     $ network.dns.disableIPv6 = true
Alright, now we're talking performance. Skips a IPv6 DNS query for every address. Speeds up DNS lookup when you use IPv4 internet (umm, basically everyone) with IPv6 enabled. If you've disabled IPv6 at the OS-level via modprobe.conf's "alias net-pf-10 off" option, you won't see much of a performance gain. For everyone else, enjoy :)

     $ network.http.max-connections = 48

Allows 48 simultaneous connections IN TOTAL for Firefox, no matter how many tabs/windows you have. Great for browsing a lot of pages with auto-refresh or are otherwise constantly connecting back to the server.

     $ network.http.max-connections-per-server = 24

Like the last option, but allows 24 connections to every web server. Usually, this is pretty pointless and won't get you much performance.

     $ network.http.max-persistent-connections-per-proxy = 12

Self explanatory. Doesn't affect you if you're not using a proxy. It may boost your performance quite a bit if you're behind a proxy. Try setting this equal to http.max-connections if you use a proxy; it only makes sense! LOL

     $ network.http.max-persistent-connections-per-server = 6

Allows 6 keep-alive HTTP active connections to every web server. For servers that are stressed and slow-to-connect, this could help out. For everyone else, a nightmare for the server admins at the other side to deal with!

     $ network.http.pipelining = true

Allows multiple connections to download pieces of the same web page. For rate-throttled servers or large webpages, this will help out with load time. The downside: Some wacky web servers don't respond properly to pipelining, so you may see weirdly rendered webpages. Usually, this doesn't happen.

     $ network.http.pipelining.maxrequests = 32

Allows for a maximum of 32 connections to download each web page. Overkill. Please don't set this option higher than 8. Actually, usually anything greater than 4 is overkill. Your system has to handle multiple TCP/IP connections which slows down your end, and you put 32 times the stress on the server at the other end. Please be a good netizen and don't do it.

---

### Post by bored2k on 2005-06-20
[QUOTE=jdong]network.http.pipelining.maxrequests = 32

Allows for a maximum of 32 connections to download each web page. Overkill. Please don't set this option higher than 8. Actually, usually anything greater than 4 is overkill. Your system has to handle multiple TCP/IP connections which slows down your end, and you put 32 times the stress on the server at the other end. Please be a good netizen and don't do it.[/QUOTE]
So we shouldn't use 8 ? Iven using 8 for quite some time now..

---

### Post by jdong on 2005-06-20
8's borderline. That's about the fastest you'll get. Any more than that won't cause a difference in speed.

Try [http://scragz.com/tech/mozilla/test-rendering-time.php](http://scragz.com/tech/mozilla/test-rendering-time.php) and see for yourself.

---

### Post by Sionide on 2005-06-20
I am noticing the difference, but I use a proxy so... that'd be why :)

---

### Post by FLeiXiuS on 2005-06-20
[QUOTE=jdong]Let's discuss this:
....................

     $ browser.tabs.showSingleWindowModePrefs = true

Not speed related. In Advanced Settings and Tabbed Browsing, you'll see the "open new windows in tabs" option, which clones Opera's MDI browsing.

....................[/QUOTE]

Very nice walkthrough of what each of them do.  I just woke up and read a lot of the posts, getting ready to do the same until I seen this one.  Thank you!  Also, the SingleWIndowModePrefs was something I was browsing around on.  I've read multiple issues in firefox 1.0.3-4 where it had stumped your CPU.  Not sure if this is still the case I'll be sure to test it out.

[QUOTE=bored2k]So we shouldn't use 8 ? Iven using 8 for quite some time now..[/QUOTE]
Hmm I'll have to re-test this.  Just to make sure.

---

### Post by FLeiXiuS on 2005-06-20
[QUOTE=bored2k]So we shouldn't use 8 ? Iven using 8 for quite some time now..[/QUOTE]
_**Just use 8 to save you and the other guy loads of convenience.**_

Ok I have some benchmarks...
[http://scragz.com/tech/mozilla/test-rendering-time.php](http://scragz.com/tech/mozilla/test-rendering-time.php) 
[Provided by Jdodson]

All of the following have received 60-80% cpu usage.  Load Avg 0%.

network.http.pipelining.maxrequests = 8
**LOAD TIME: 5.369** 

network.http.pipelining.maxrequests = 12
**LOAD TIME: 4.839** 

network.http.pipelining.maxrequests = 24
**LOAD TIME: 4.667** 

network.http.pipelining.maxrequests = 32
**LOAD TIME: 4.423**

So a speed increase is little, but not enough to make a difference.  I will tone it down in the main section of the HOWTO, your correct too many will destroy the other end.

---

### Post by meldroc on 2005-06-20
I've been told that using more than eight connections per server is a Bad Thing - it hogs a lot of resources on the server.

Boosting Firefox performance is good and all, but we do have to be considerate as well... [-X

---

### Post by FLeiXiuS on 2005-06-20
[QUOTE=meldroc]I've been told that using more than eight connections per server is a Bad Thing - it hogs a lot of resources on the server.

Boosting Firefox performance is good and all, but we do have to be considerate as well... [-X[/QUOTE]

Fixed :-P

---

### Post by i3dmaster on 2005-06-20
Thanks! This is helpful to understand how to tweaking firefox... and I do feel the difference.

---

### Post by dissident on 2005-06-20
FYI, it doesn't matter how high you set it. It will always be limited to 8.
> network.http.pipelining.maxrequests


    * Description: maximum number of consecutive requests in one pipeline.
    * Type: integer
    * Limit: 8
    * Default: 4
    * Additional Info: nsHTTP.h. Optimal value depends on connection bandwidth/latency.
    * Recommendation: 8. While it doesn't hurt to set it to 100 like in other tweak examples, it will have no effect whatsoever because of the mentioned limit.
[http://forums.mozillazine.org/viewtopic.php?t=53650](http://forums.mozillazine.org/viewtopic.php?t=53650)

---

### Post by CAE on 2005-06-21
[QUOTE=FLeiXiuS]
```

     $ network.http.max-connections-per-server = 24

     $ network.http.max-persistent-connections-per-proxy = 12

     $ network.http.max-persistent-connections-per-server = 6

```[/QUOTE]

For the love of god, remove these "tweaks", please. They violate the HTTP spec and can cause massive problems on the server end.

---

### Post by somuchfortheafter on 2005-06-21
hmm on basic dsl 20 is great and for cable and beyond i range from 30-85 ...

---

### Post by Sionide on 2005-06-21
I don't know whether or not I do see the difference now, a LOT of images drop when loading a page and their ALT text shows up instead - I'm tempted to put the settings back on default (except for the IPv6 one)

---

### Post by jdong on 2005-06-21
[QUOTE=CAE]For the love of god, remove these "tweaks", please. They violate the HTTP spec and can cause massive problems on the server end.[/QUOTE]
Actually, those aren't too bad (unless they're Windows servers.. then that's a different story, LOL)

It's the too-many-pipelines tweaks that are awful on the remote end. Especially when the page is dynamic and expensively generated... **shudders**

---

### Post by CAE on 2005-06-21
[QUOTE=jdong]Actually, those aren't too bad (unless they're Windows servers.. then that's a different story, LOL)

It's the too-many-pipelines tweaks that are awful on the remote end. Especially when the page is dynamic and expensively generated... **shudders**[/QUOTE]

I'm going to call you on this one, buddy. ;)

Pipelining is only dangerous if it's some god-awful old webserver software. Simultaneous requests followed by simultaneous responses can actually help improve performance as it cuts out some latency, as the server has to deal with fewer requests.

When it comes to the max-connections, Apache has to fork a whole lot of children in order to deal with the shitload of new connections coming in, and this is a pretty CPU intensive task. What's more, the persistent connections are kept alive, which causes a whole lot of other problems.

---

### Post by FLeiXiuS on 2005-06-22
I've fixed all dangerour or potential threats.  Things should be fine :-)

---

### Post by notos on 2005-06-22
i ve made a post about FireFox and there is a section about tweaking :))
[http://ubuntuforums.org/showthread.php?p=218169](http://ubuntuforums.org/showthread.php?p=218169)

---

### Post by FLeiXiuS on 2005-06-22
[QUOTE=notos]i ve made a post about FireFox and there is a section about tweaking :))
[http://ubuntuforums.org/showthread.php?p=218169](http://ubuntuforums.org/showthread.php?p=218169)[/QUOTE]
Thank you I'll include a note about it in the main post.

---

### Post by Sionide on 2005-06-26
I've had to tone this down a bit on my Firefox, I do connect via proxy so I've set the values back to default, but made the proxy ones the same as the normal ones - when I had the values all set higher, I was getting a LOT of pages with images not downloading... Now that I've changed the values as above, the pages load perfectly. I left the top 3 alone, because I don't think they affect the actual download of data...

There is a program for Firefox on Windows, called FireTune which "Tunes" Firefox, it probably makes similar changes. [http://www.totalidea.com/freestuff4.htm](http://www.totalidea.com/freestuff4.htm)

---

### Post by picpak on 2005-06-26
[QUOTE=jdong]Try [http://scragz.com/tech/mozilla/test-rendering-time.php](http://scragz.com/tech/mozilla/test-rendering-time.php) and see for yourself.[/QUOTE]

With the tweaks: around 30 seconds

Without the tweaks: 28 seconds

That's just stupid. Only once have I ever found tweaks like these that work. And I lost it.

---

### Post by ah.heng on 2005-06-26
another one would be

```
nglayout.initialpaint.delay = 0
``` 

this value is the amount of time the browser waits before it acts on information it receives. it's non-existent, so you'll have to create it as a new integer.

---

### Post by Sionide on 2005-06-27
Isn't it not existing the same as it being 0 ?

---

### Post by michellembrodeur on 2005-06-28
[QUOTE=FLeiXiuS]****RECOMMENDED FOR BROADBAND USERS ONLY****

Ok so I'm sure a vast majority of you have had problems with firefox running slowly.  Not only is it the IPv6/4 strings but a enormous amounts of others.

So whats the catch?  ABSOLUTELY NOTHING!  It's all about tweaking and this is how I did it.  

(Credits to google/memphis users for explaing a majority)

Open firefox and in the address bar enter:
```

     $ about:config 

```
For the following below you can enter a portion of the string as a quicker way of finding it :-).
```


     $ browser.tabs.showSingleWindowModePrefs = true

     $ browser.xul.error_pages.enabled = true

     $ network.dns.disableIPv6 = true

     $ network.http.max-connections = 48

     $ network.http.max-connections-per-server = 24

     $ network.http.max-persistent-connections-per-proxy = 12

     $ network.http.max-persistent-connections-per-server = 6

     $ network.http.pipelining = true

     $ network.http.pipelining.maxrequests = 8

```
After this, restart firefox and voila.  Light-speed at the palm of your hands.

Other firefox customization guides, thankyou notos.
[http://ubuntuforums.org/showthread.php?p=218169](http://ubuntuforums.org/showthread.php?p=218169)[/QUOTE]



Didn't help with me or roommate.

And also do apt-get update and others its also slow. its everything that connects the net is slow. Something in ubuntu/kubuntu needs to be changed.

It always takes like 15 secs for it to hook up to anything. including Synaptic to download stuff.

So what is it?

---

### Post by michellembrodeur on 2005-07-26
Acutally this is how I spend up my enternet.
I put the DNS and Secondary DNS numbers in my router.
Instantly access on almost all sites.
If you don't have a router put it in your network configurations.

All the stuff to speed it up with firefox does not work. At least not for me, friends or anyone else I put on Kubuntu.

---

### Post by earther on 2005-08-30
[QUOTE=wmcbrine]about:config
image.animation_mode

Set it to "once" for a single loop through, or "none" to disable GIF animation completely.

Once you've done that, you may want to add the "Replay Animation" extension for those rare cases where it's actually worth viewing:

[http://www.extensionsmirror.nl/index.php?showtopic=2315](http://www.extensionsmirror.nl/index.php?showtopic=2315)[/QUOTE]
 Thanks for that tip.  I've been looking all over trying to find out how to shut animations off.

---

### Post by bored2k on 2005-09-08
All this tricks work on Epiphany. JUst wanted to point that out.

---

### Post by humanity_to_others on 2005-10-14
In Address Bar write about:config 
```
network.dns.disableIPv6: true
network.http.pipelining: true
network.http.proxy.pipelining: true
browser.turbo.enabled: true
nglayout.initialpaint.delay: 200 (right click, new -> integer)
network.http.max-connections 48
network.http.max-connections-per-server 24
network.http.max-persistent-connections-per-proxy 12
network.http.max-persistent-connections-per-server 6
network.http.pipelining.maxrequests 8
``` restart firefox.

---

### Post by bored2k on 2005-10-14
This works better IMO: [http://fasterfox.mozdev.org/](http://fasterfox.mozdev.org/) (you still have to manually disable IPv6).

---

### Post by majikstreet on 2005-10-14
[QUOTE=bored2k]This works better IMO: [http://fasterfox.mozdev.org/](http://fasterfox.mozdev.org/) (you still have to manually disable IPv6).[/QUOTE]
Yes, that works WAAAAY better. You can define your own settings in it too.. Prettier.

---

### Post by humanity_to_others on 2005-10-14
[QUOTE=bored2k]This works better IMO: [http://fasterfox.mozdev.org/](http://fasterfox.mozdev.org/) (you still have to manually disable IPv6).[/QUOTE]
thank you **bored**

---

### Post by erikpiper on 2005-10-14
Fasterfox- SWEET! I love how it looks to be platform independent!

But why and how would I disable IPv6?

---

### Post by majikstreet on 2005-10-14
[QUOTE=erikpiper]Fasterfox- SWEET! I love how it looks to be platform independent!

But why and how would I disable IPv6?[/QUOTE]
Why? If you don't have ipv6 it just makes it faster if you disable it.
How? about:config and search for ipv6 and click it to disable it.

---

### Post by karthik085 on 2005-11-08
1.Type about:config into the address bar and hit return. Scroll down and look for the following entries:

network.http.pipelining
network.http.proxy.pipelining
network.http.pipelining.maxrequests

Normally the browser will make one request to a web page at a time. When you enable pipelining it will make several at once, which really speeds up page loading.

2. Alter the entries as follows:

Set network.http.pipelining to true

Set network.http.proxy.pipelining to true

Set network.http.pipelining.maxrequests to some number like 30. This means it will make 30 requests at once.

3. Lastly right-click anywhere and select New-> Integer. Name it nglayout.initialpaint.delay and set its value to 0 (zero). This value is the amount of time the browser waits before it acts on information it recieves.

If you're using a broadband connection you'll load pages MUCH faster now!

You have to close your browser after you make the changes. When you start it back up they will be in effect.

---

### Post by benplaut on 2005-11-08
[QUOTE=karthik085]1.Type about:config into the address bar and hit return. Scroll down and look for the following entries:

network.http.pipelining
network.http.proxy.pipelining
network.http.pipelining.maxrequests

Normally the browser will make one request to a web page at a time. When you enable pipelining it will make several at once, which really speeds up page loading.

2. Alter the entries as follows:

Set network.http.pipelining to true

Set network.http.proxy.pipelining to true

Set network.http.pipelining.maxrequests to some number like 30. This means it will make 30 requests at once.

3. Lastly right-click anywhere and select New-> Integer. Name it nglayout.initialpaint.delay and set its value to 0 (zero). This value is the amount of time the browser waits before it acts on information it recieves.

If you're using a broadband connection you'll load pages MUCH faster now!

You have to close your browser after you make the changes. When you start it back up they will be in effect.[/QUOTE]

there's alot mpre than that, it's simpler to use FasterFox...
[http://fasterfox.mozdev.org/](http://fasterfox.mozdev.org/)

---

### Post by kingsidy on 2005-11-08
benplaut is right. just use the fasterfox extension. There is also another extension called "tweak network settings". it also does the same thing.

---

### Post by JogerNaut on 2005-11-08
[QUOTE=karthik085]
Set network.http.pipelining.maxrequests to some number like 30. This means it will make 30 requests at once. [/QUOTE]
Firefox limits network.http.pipelining to 8. Setting it to anything over 8 is just the same as setting it to 8.

[QUOTE=karthik085]
3. Lastly right-click anywhere and select New-> Integer. Name it nglayout.initialpaint.delay and set its value to 0 (zero). This value is the amount of time the browser waits before it acts on information it recieves.
[/QUOTE]
This will make the first part of the page appear quicker but the overall time for the page to load may take longer. This is because Firefox will start rendering the page before it has finished transfering tables, frames, etc. So Firefox will have to re-render the page several times. Setting it to a very low number will also mean higher CPU load for Firefox.

---

### Post by eyebrowman92 on 2005-11-08
way to steal the idea from someone who posted it on a hack website. i came across it once using stimbleupon, just like you probably did.

---

### Post by fakie_flip on 2005-11-08
A better way to fix things without the trouble is to install Opera. Opera has a nice user interface with the same tabbed browsing. One nice thing about it is that the pages you closed Opera with are there next time you open Opera again. The main reason for using Opera is it is fast as hell. It also has some cool skins.

---

### Post by etc on 2005-11-08
[QUOTE=eyebrowman92]way to steal the idea from someone who posted it on a hack website. i came across it once using stimbleupon, just like you probably did.[/QUOTE]
Those "tricks" are all over the place, and the ones which speed up pipelining are really bad for the servers firefox is trying to view.

---

### Post by ephman on 2005-11-08
[QUOTE=etc]Those "tricks" are all over the place, and the ones which speed up pipelining are really bad for the servers firefox is trying to view.[/QUOTE]

hi,

why is it bad for the servers firefox is trying to view?

thanks,
ephman

---

### Post by majikstreet on 2005-11-09
[QUOTE=ephman]hi,

why is it bad for the servers firefox is trying to view?

thanks,
ephman[/QUOTE]
from my information, it puts more stress on the server. if all of slashdot's readers used those high settings, slashdotting would be worse.

---

### Post by trinaryouroboros on 2005-11-09
[QUOTE=majikstreet]from my information, it puts more stress on the server. if all of slashdot's readers used those high settings, slashdotting would be worse.[/QUOTE]

I guess...but if one does pay out the nose for high connection speeds, one does wish to get the most of of that connection.

Perhaps in leiu of the recent flames against adding good running shoes to firefox, there should be a tweak to allow certain sites the priviledge of not being bombarded. I've been seeing alot of people start anti-firefox chains so noobs will not put a load on peoples servers...which IMHO, places like myspace really don't need a team of propagandites to do this, they just need to stop drinking so much and get more servers going to support their faster-than-an-EMP-wave increasing user base.

---

