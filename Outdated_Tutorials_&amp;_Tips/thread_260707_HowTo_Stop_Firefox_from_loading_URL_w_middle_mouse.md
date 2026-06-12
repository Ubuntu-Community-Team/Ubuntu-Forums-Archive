---
title: "HowTo: Stop Firefox from loading URL w/ middle mouse button"
date: 2006-09-19
forum: Outdated Tutorials &amp; Tips
---

### Post by tturrisi on 2006-09-19
Scene:
You have a 3 button mouse or a wheel mouse & occasionally when using the middle mouse button to scroll a Web page you push too fast or too hard & you are surprised to see some Web page load that you did not intend to load.

Cause:
Firefox default setting for midle mouse button will load a Web page when pressed if cursor happens to be over hypertext.  (a nuisance when using the mouse wheel to rapidly scroll a Web page)

Solution:
1. open Firefox
2. in address bar type:  [COLOR="Red"]about:config[/COLOR]
3. locate line:  [COLOR="Red"]middlemouse.contentLoadURL[/COLOR]
4. double click the line to change from [COLOR="Red"]true[/COLOR] to [COLOR="Red"]false[/COLOR]

---

### Post by Kingsley on 2006-09-21
thanks. your guide helped me figure out how to fix the annoyance in my opera browser.

---

### Post by tzulberti on 2006-09-21
Thanks, that solved that annoyiance in firefox... :D

---

### Post by enopepsoo on 2006-09-21
This is far from an annoyance to me.  Middle clicking is great in firefox.  I am in the habit of opening links in new tabs.  You can also close a tab by middle clicking it! :D 

I know this middle click works well in Windows as well, but I love Linux' use of middle clicking for copy / paste.  that is very handy (although it is not 100% consistent.

:KS

---

### Post by dmizer on 2006-09-21
i love you man.  can't count how many forum posts i've lost as a result of that little middle click "feature".

---

### Post by tht00 on 2006-09-22
Yeah, I also use the middle-click a ton.  I used to use mouse gestures to open new tabs (and closing tabs) until I found the middle-click gem.

In any case, does anyone know what causes the very strange behavior in firefox in other environments?  I've noticed it on some of the school's Solaris machines -- a middle click on a tab won't close it, but rather, open some (sometime completely random) website. (Does anyone know what I mean?)

I've also noticed this in the KDE environment under Mepis... why is it not consistant?

---

### Post by kotti on 2006-09-22
Why not just check "Use autoscrolling" from options/advanced/general? That's the first thing I change when I install Firefox.

---

### Post by george_apan on 2006-09-22
Thank you, thank you, thank you! I use a laptop touchpad and the middle click is mapped to the right-top edge which I accidentally pressed all the time. This was a major annoyance for me.

---

### Post by Antipodean on 2006-09-22
Thank you very much, this also fixes the annoyance in non-standard installations of Firefox (Swiftfox etc.) and Seamonkey where middle clicking on a tab button causes the browser to try to load the contents of the clipboard rather than closing the tab.

For those who may be interested here is the user.js entry for this.

```
user_pref("middlemouse.contentLoadURL", false);
```

---

### Post by respyre on 2006-09-29
> **tht00 said:**
> In any case, does anyone know what causes the very strange behavior in firefox in other environments?  I've noticed it on some of the school's Solaris machines -- a middle click on a tab won't close it, but rather, open some (sometime completely random) website. (Does anyone know what I mean?)I just noticed this myself--middle clicking seems to do a Google "feeling lucky" search for the currently selected, or most recently selected text.  Now that I see a pattern to the seemingly random URLs that were loaded, I can see how it'd be a useful feature.

---

### Post by Uber_Nick on 2006-11-30
> **respyre said:**
> I just noticed this myself--middle clicking seems to do a Google "feeling lucky" search for the currently selected, or most recently selected text.  Now that I see a pattern to the seemingly random URLs that were loaded, I can see how it'd be a useful feature.

I might be wrong on some of the details, but here's my best explanation of why this is occuring:

In KDE, middle-clicking will paste the last piece of text to be selected.  So if you have "hello" selected and middle click in a kwrite window, it'll paste "hello".

Now there's a behavior setting in firefox that tries to visit a URL of what's pasted in with middle click.  So if you middle click inside firefox with "hello" selected, it'll try to visit "http://hello".  

There's also a behavior where if firefox can't resolve a domain (like "http://hello"), it does a google search for "hello" and goes to whatever come out of "I'm feeling lucky".  

So in effect, you were right about what middle clicking does.  As noted above, you can open a new firefox window and type "about:config" in the address bar.  You need to set false the middleMouse.contentLoadURL preference.  This won't screw with opening links in tabs or anything like that.  Good luck.

---

### Post by Dmitri on 2007-10-20
Thanks! :popcorn:

This is what caused my frustration when using my laptop without a mouse (you sometimes press too hard and it counts as middle click)...

My daily frustration level decreased by at least 30% ;)

---

### Post by r3ll3k on 2008-05-11
God  I hated this feature!!!! It might be great with a mouse but when your on a touchpad ... It will bring you nothing but frustration. Daily frustration also down 30% .LOL

---

### Post by FrooziE on 2008-08-14
Thanks! This was driving me crazy. Now to find out how to get my horizontal scrollbar back :(

---

### Post by e633 on 2010-01-29
Thanks for the workaround but i was wondering if i can get the middle mouse button to engage that sort of "scroll mode" i get on windows XP if you know what i mean. (Karmic, FF 3.6).

EDIT: i figured it out myself, just go to about:config, look for "general.autoScroll" and set it to true! Don't know if you need to disable URL loading first though.

---

### Post by Izkata on 2010-07-28
Finally, an answer... sorta, at least.

Lucid apparently configured the upper-right corner of my touchpad as a middle-click, and I haven't found a way to change it.  It's especially frustrating when the side of my thumb brushes it and suddenly I get a Comcast error page saying saying "random words" website cannot be found.  Took me a week to even figure out what caused it.

---

