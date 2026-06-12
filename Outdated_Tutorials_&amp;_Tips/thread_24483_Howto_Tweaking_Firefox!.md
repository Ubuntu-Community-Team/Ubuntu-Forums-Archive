---
title: "Howto: Tweaking Firefox!"
date: 2005-04-07
forum: Outdated Tutorials &amp; Tips
---

### Post by Heliode on 2005-04-07
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
So, lets get the [Adblock extension](https://addons.update.mozilla.org/extensions/moreinfo.php?application=firefox&version=1.0&os=Windows&category=Miscellaneous&numpg=10&id=10)! Install this, and restart firefox to make it work. Now, this thing by itself won't do anything; you'll need filters. Of course you can make your own, but since someone else has already done so you can just use that and save yourself a lot of time. Go to [this regularly updated page](http://www.geocities.com/pierceive/adblock/), grab the latest filter and import it into adblock with Extra -> Adblock -> Preferences -> Adblock options -> Import filters.
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
I also highly recommend the use of RSS feeds. Most major news outlets offer some kind of RSS feed, and you can take advantage of that using firefox! Personally I have my entire Bookmarks Toolbar filled with 'live bookmarks' (RSS feeds). A good example is [SlashDot](http://slashdot.org). Notice the orange icon in the lower right portion of the screen. Click on it. Don't be shy! An option will pop up for you to subscribe to the feed, and there you have it!
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

---

### Post by Heliode on 2005-04-09
Request to the mods:

Can this thread be moved to Hoary howto subforum, so I don't have to cross-post it?
Thanks.

---

### Post by Tamacracker on 2006-11-12
ChromeEdit cannot install on the new version of FIrefox... this is basically useless for Edgy users with Firefox 2.0

---

### Post by dutchmega on 2006-11-12
Really? Maybe because the topic is like older then a year... I read it and most information is outdated by now...

---

### Post by esaym on 2006-11-12
mike's ad blocking hosts file works great for me: [http://everythingisnt.com/hosts.html](http://everythingisnt.com/hosts.html)

---

### Post by FRuMMaGe on 2007-06-12
Middle-mouse button on a tab = Close tab

---

### Post by itsjareds on 2008-08-10
Two keyboard shortcuts I use ALL THE TIME are Ctrl+L for the location bar, and Ctrl+K for the search bar.

So I can keep my hands on the keyboard and navigate without the mouse :)

---

### Post by tehwinrar on 2009-07-08
ctrl+tab switches between tabs

---

### Post by M0ndo on 2009-07-08
thanx for the tuorial

---

### Post by binbash on 2009-07-09
Ummm this tutorial is from history i guess :)

---

### Post by melhe on 2009-10-07
Ctrl-L is awesome...

Ctrl-L selects the text in the location bar, but is there some way to tweak firefox to also select the text when clicking in the location bar with the mouse? Yeah, I know, like in windows...

---

### Post by the_guv on 2009-10-12
firefox-3.6 is the best tweak in ages!  hope helps.

---

### Post by fooman on 2009-10-12
> **melhe said:**
> Ctrl-L is awesome...

Ctrl-L selects the text in the location bar, but is there some way to tweak firefox to also select the text when clicking in the location bar with the mouse? Yeah, I know, like in windows...


                                                                             open firefox,  type about:config in address bar

copy/paste the following into the filter bar:
```
browser.urlbar.clickSelectsAll
```change false to true....restart firefox.

hope that helps.

---

### Post by melhe on 2009-10-12
Thanks, case closed!!!

---

### Post by harpinder on 2010-08-01
> **fooman said:**
> open firefox,  type about:config in address bar

copy/paste the following into the filter bar:
```
browser.urlbar.clickSelectsAll
```change false to true....restart firefox.

hope that helps.

thanks very helpful

---

### Post by Sef on 2010-08-01
Closed. Original post is more than 5 years old.

---

