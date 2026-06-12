---
title: "firefox - right click strange behavior"
date: 2008-06-16
forum: New to Ubuntu
---

### Post by akkad on 2008-06-16
since 8.04 installed i have an issue with firefox 3 that when i right click a link in a page then one of the following actions happen:
- open the standard context menu for the selected link (this should be the expected behavior).
- open the link in a new window.
- open the bookmark dialog for the selected link.
- open a new compose message in evolution where the message body is the selected link.
- perform the "switch page direction" from right to left.

strange isn't it ?? any idea ???

---

### Post by ChameleonDave on 2008-06-16
Does this still happen if you disable all your add-ons?

---

### Post by alienexplorers on 2008-06-16
Mine does the same thing with or without extensions disabled.

---

### Post by PGScooter on 2008-11-09
Mine does the same. It is quite annoying and curiously strange..

any solutions?

Has anyone tried reinstalling firefox?

---

### Post by Kellemora on 2008-11-09
Hi akkad

I use Firefox nearly 8 hours a day, some days even longer.

Only ONE of the mouse features I've used for decades is available in Linux, any flavor.  The mouse works better in Ubuntu than most others, but does NOT have the support it should have, considering the keyboard and mouse are the two PRIMARY Human Interface Tools connected to a computer.

However, back to your issue.  Firefox on Linux is NOT the same Firefox as for Winders!  Images can be deceiving!  As far as the mouse goes, it depends WHERE you are on the page and exactly WHAT your pointer is on top of when you right click.  And WHAT the programmers of that web page WANT to happen if you right click.  They actually have a little more control in WinDOZE on what happens than they do in Linux due to the lack of mouse support in Linux.

Web sites I visit that have repetitive tasks will set a tab to work the same from a right click or a left click, these are usually Java or Shockwave controlled images, shockwave don't work in Linux either, or should I say rarely.

If I go to a white space on a web page the BACK option is on the top of the list.  But if I'm anywhere else, what comes up is nearly (not totally) dependent upon what the owners of that web page want to happen.

In WinDOZE you can override the web sites requests for action in your mouse set-up program.  Another feature not supported in Linux.

But look at it this way!  Everything works better in Ubuntu than things did in WinDOZE when it was at the same age or even 4 times as old!

And WinDOZE hardware was NEVER cheap back then!  A simple 9 pin dot matrix printer was over sixteen hundred dollars and slower than molasses in winter.  Today you can get a full color excellent graphics printer for 50 bucks, but they'll soak you on the ink cartridges at 40 bucks each.

Most printers (due to standardization) will run on Linux, but perhaps not with all the support they should have.

Maybe we should all get together and agree to buy only from manufacturers who offer full Linux support for their products.
There are too many manufacturers to expect all of them to fill the Linux niche, but if all Linux users chose a single manufacturer to make their hardware and accompanying software purchases, then the manufacturer would have the support they needed to develop the software and drivers.
Just food for thought is all!

TTUL
Gary

---

### Post by PGScooter on 2008-11-10
> **Kellemora said:**
> Hi akkad
Maybe we should all get together and agree to buy only from manufacturers who offer full Linux support for their products.
There are too many manufacturers to expect all of them to fill the Linux niche, but if all Linux users chose a single manufacturer to make their hardware and accompanying software purchases, then the manufacturer would have the support they needed to develop the software and drivers.
Just food for thought is all!

TTUL
Gary

I always wondered if there were movements such as you describe. I would think that this would be popular for the consumer and the company. Please let me know if you find/start anything.

---

### Post by waydownsouth on 2008-11-10
I've been experiencing the same issues and up till now was just thinking it was just me.

I understand what Kellemora is saying but this is happening on just a simple html hyperlink on pages that I'd been right clicking on for all my time browsing the site.

For example, right click on a link to bring up the context menu 'open in new tab' option, no menu appears, computer grinds away for a bit, pops up a new message window with the link in the message body (or any of the above that the OP mentioned).
Curse and swear a little, close the new message window, right click again on the link, and then the context menu appears, carry on as normal...

it just seems a little weird that at first it won't work as expected, then it will second time around.

---

### Post by Benic on 2008-11-10
I've been plagued by the same problem for a while. As far as I know, there's no solution yet for [_bug #206295_]("https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/206295"). It seems to be caused by the random position of the pointer in the right-click menu when you open it.

---

### Post by waydownsouth on 2008-11-10
Thanks for the link,

a bit of reading through that bug and one linked upstream suggested a workaround of installing the mouse gestures plugin:
[https://addons.mozilla.org/en-US/firefox/addon/39]("https://addons.mozilla.org/en-US/firefox/addon/39"). 
This supposedly makes the context menu appear after the right click release

I have installed it and will see how it goes.

---

### Post by benerivo on 2008-11-10
It is definitely annoying. I didn't realise it was a bug. I always thought it was me moving the mouse whilst right clicking and therefore picking one of the context menu options accidentally. I now tend to hold the button down and drag and release to make sure i get the right option, or just take my palm off the mouse so  i can guarantee i don't move it.

The problem seems to happen to me for maybe one in every five right clicks.

---

### Post by Benic on 2008-11-11
> **waydownsouth said:**
> Thanks for the link,

a bit of reading through that bug and one linked upstream suggested a workaround of installing the mouse gestures plugin:
[https://addons.mozilla.org/en-US/firefox/addon/39]("https://addons.mozilla.org/en-US/firefox/addon/39"). 
This supposedly makes the context menu appear after the right click release

I have installed it and will see how it goes.

I've been trying it since you posted the link: so far, so good! No more right-click bug. We'll see after few days if it goes well, but I'm pretty optimistic.

---

### Post by waydownsouth on 2008-11-11
Its also looking good for me too...

---

### Post by Capa Pinbacker on 2008-12-07
Not only is the mouse gestures plug-in a cool utility, it has also solved the random context menu behavior I've also had with Firefox (currently at Firefox 3.04/Ubuntu 8.10)!  Thanks for this!

---

### Post by GNU/Greenman on 2008-12-07
I have been using Firefox 3.0.4 both in windowz and ubuntu machines.

The strange right-clicking problem only occurs in my ubuntu machine (Intrepid 8.10), with or without extensions enabled.

I have also tried the mouse gestures plug-in and it did solve the problem. I use no features of the plug-in other than installing it to avoid the right-clicking bug.

If someone disables the plug-in, bug behavior comes back again so there may be something usefull for the developers to look in the code of that plug-in so as to overall fix the bug.

Thanks for the workaround!! ):P

---

### Post by catchytune on 2008-12-07
I had exactly the same problems with the context menu in Firefox for some months and thought it happens only to me... the mouse-gestures add-on solved it. (FF 3.0.4 on Hardy) - Thanks for the hint! :biggrin:

---

### Post by zoniq on 2008-12-08
I had the same problem. The mouse gesture add-on solved that, but caused another problem. Instead of a right click, now when I do a left click it occasionally triggers the 'BACK_IN_HISTORY'-function of the tab/browser.

That behavior appears totally randomly. I figured, that if I do a single click on the top Window-bar of Firefox (where the icon, the minimize and close buttons are) it turns back to normal.

But after a few clicks it could be weird again.

Anyone else the same behavior?

---

### Post by Farmer of Bricks on 2008-12-08
How about just holding the right-clicker mouse button down for a fraction of a second longer?

---

### Post by solitaire on 2008-12-08
this happens to me all the time!

Only way to stop the "Random-Right-Click" is to every so often right click on a part of the screen that has no clickable objects, then Left click to get rid of the menu then the right click should work for a few more clicks.

I've noticed it that it happens to me when i'm doing many clicks on a single page (i.e. right clicking and selecting "open in a new tab").

It get's very annoying very quickly

---

### Post by GlennW on 2009-01-05
Here's something to throw into the mix. I have a laptop that runs Vista (I have no choice in the matter, it's a company machine) but I use Firefox exclusively on it. The issue is that inside the frame of Firefox (on a website only) there is no right click available. On the the tab bar I can right click to open a new tab so I know that the mouse isn't defective. 

I spent a couple of hours googling this issue and found nothing except a bunch of goofy web site owners who thought using Java script to disable the right click would protect their copyrighted material. Duh! 

There was a reference to an extension for firefox to allow right click but it's out of date. 

Now what?

Any ideas..........

---

### Post by GlennW on 2009-01-06
Will uninstalling firefox and reinstalling it solve my right click problem?

I can, in the meantime, use google chrome.

---

### Post by zoniq on 2009-01-07
> **GlennW said:**
> Will uninstalling firefox and reinstalling it solve my right click problem?

Why don't you try? ;-)

---

### Post by smokey_58au on 2009-03-14
> **waydownsouth said:**
> Thanks for the link,

a bit of reading through that bug and one linked upstream suggested a workaround of installing the mouse gestures plugin:
[https://addons.mozilla.org/en-US/firefox/addon/39](https://addons.mozilla.org/en-US/firefox/addon/39). 
This supposedly makes the context menu appear after the right click release

I have installed it and will see how it goes.

From the bottom of my heart, thank you.  This little add-on just removed the single biggest niggle I have had with Ubuntu/Firefox - the infamous right "what will happen this time" click.

---

### Post by Dojobuntu on 2009-03-30
> **waydownsouth said:**
> Thanks for the link,

a bit of reading through that bug and one linked upstream suggested a workaround of installing the mouse gestures plugin:
[https://addons.mozilla.org/en-US/firefox/addon/39]("https://addons.mozilla.org/en-US/firefox/addon/39"). 
This supposedly makes the context menu appear after the right click release

I have installed it and will see how it goes.

Thanks for the workaround. It worked like a charm, plus I'm getting used to those mouse gestures. Wonder if there's a bug report submitted for this issue...

---

### Post by thodpol on 2009-10-02
> **waydownsouth said:**
> Thanks for the link,

a bit of reading through that bug and one linked upstream suggested a workaround of installing the mouse gestures plugin:
[https://addons.mozilla.org/en-US/firefox/addon/39]("https://addons.mozilla.org/en-US/firefox/addon/39"). 
This supposedly makes the context menu appear after the right click release

I have installed it and will see how it goes.


Thanks a lot! it just solved my problem!

---

