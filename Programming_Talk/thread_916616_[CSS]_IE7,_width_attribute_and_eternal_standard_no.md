---
title: "[CSS] IE7, width attribute and eternal standard non-compliance"
date: 2008-09-11
forum: Programming Talk
---

### Post by nvteighen on 2008-09-11
Just a question. I'm developing a website for someone with a div that contains the webpage's "real body" (in other words, where text and images will be displayed). The website uses CSS-based frames and, of course, using **width: 100%** for the content div caused it to overflow horizontally, as percentages are calculated from the browser's window size. So, I decided to use **width: auto**... it worked with FF3, Epiphany, Google Chrome, Konqueror and I suppose it would probably also work in Safari and Opera.

But, guess in which browser it didn't work... :)

IE7 produced a dissastrous layout that overflowed horizontally and (surprisingly) also vertically, images where at full size... in one word: crap. To fix it, I had to set **width: 65%** or similar... of course, the layout now looks a very little bit different, but it's OK and of course, all decent browser accept it with no complains... and the W3C validator congratulates me.

Another quirk was that IE7 didn't recognize the encoding (UTF-8, not even a weird one!) attribute at the **<?xml ...?>** line... so, to make it happy, I have to redundantly include the **<meta http-equiv="Content-Type" .../>** line even if it's absolutely unnecessary for all the rest of browsers there are...

What I'd like to ask is this: Ok, this time I could fix the page to fit IE7 without introducing nasty hacks and keep my page standard compliant. But, what if, to satisfy the 80%-market-share-browser, I have to break standards or introduce non-standard extensions or code Javascript to detect browser and "selectively break standards" depending on the user's browser? What would you do?

As this is not my personal webpage, I have to do this visible for IE7 users. If it was mine, I really wouldn't care to support such a piece of crap... I'd tell people to get a decent browser: I want my webpages to have tidy, normal, senseful and standard XHTML 1.1+CSS 2.1 code... yeah, that way I'm thinking more like a programmer than a marketing staff and sadly, here I have to deal with a marketing website...

(By the way, I haven't even tested the webpage with IE6... it would probably break because of the **<?xml ...?>** tag... but there I really don't care at all)

P.S.: It's funny/crazy that I also use the "auto" value in other places in the very same CSS and IE7 does render those correctly... The only one that failed was the div's.

---

### Post by CptPicard on 2008-09-11
Yes, the IE box model is totally borked and has been so for all eternity... :( they really are holding back "doing things right" as far as CSS goes.

---

### Post by nvteighen on 2008-09-11
**Update**: Even Lynx and Elinks render the webpage correctly using width: auto!

EDIT: Wait, do they support CSS?

---

### Post by Reiger on 2008-09-11
Wait until you move into tables, you padawan. Also: <?xml ... ?> declarations cause IE7 to jump into quirks-mode. Well, that's what you get. ;)

---

### Post by Flimm on 2008-09-11
I'd recommend [A List Apart](http://alistapart.com) for stuff like this. They have some excellent articles on good HTML that actually work cross-browser.
Also, I'm pretty sure starting your XHTML document with <?xml drives IE to do strange things.

---

### Post by pmasiar on 2008-09-11
I hope there is special ring in hell for managers in MSFT who force developers to release product with deliberately different quirks mode in each version, instead just following standards (which were developed with input from MSFT).

I heard about CSS framework Blueprint which is supposed to handle whose differences.

Solution we use is to design for standards-compliant browsers, place text "this site is best viewed in Firefox" and forget about it 8-)

---

### Post by nvteighen on 2008-09-11
> **Flimm said:**
> I'd recommend [A List Apart](http://alistapart.com) for stuff like this. They have some excellent articles on good HTML that actually work cross-browser.
Also, I'm pretty sure starting your XHTML document with <?xml drives IE to do strange things.

Yeah, I know it and even looked at it when trying to understand what was happening. 

> **pmasiar said:**
> I hope there is special ring in hell for managers in MSFT who force developers to release product with deliberately different quirks mode in each version, instead just following standards (which were developed with input from MSFT).

+1

> Solution we use is to design for standards-compliant browsers, place text "this site is best viewed in Firefox" and forget about it 8-)

Which is what I would have done if it was my website and not someone else's... :(

---

### Post by Merk42 on 2008-09-13
The majority of people will not download a new browser if you tell them your site is beter viewed with {insert Browser here}. They'll just think that you, the webmaster, aren't doing your job properly.

Unfortuantely, you really should test things in IE6 as well.  An easy way to test in 6, 7, and 8(beta 2).  Is to get the [preconfiguerd VHDs from Microsoft](http://www.microsoft.com/downloads/details.aspx?FamilyID=21eabb90-958f-4b64-b5f1-73d0a413c8ef&displaylang=en).  You can either convert them into VDMK or VDI for VMWare and Virtualbox respectively, or as of Virtualbox 2.0, open it directly.

---

### Post by Reiger on 2008-09-13
<letOffSteam>Unfortunately the Majority of these notices is about Microsoft Internet Explorer and the sites we're talking about are sites you absolutely 'need' to visit because they contain, say, your grades as a student, the online course material ... And that is the sole reason, why IE7 still has a place on my box. Gah, how I loathe that WebCT Vista thing of my Uni already for it (apart from the fact it ain't up to date as usual...) </letOffSteam>

But yes, I suppose I am in the minority in that I do keep up ~5 different browsers (Firefox 3 on Vista which is totally borked for it's no longer 2.x though the app itself got broken in the upgrade process...; Opera 9.5x on both Ubuntu & Vista; Microsoft IE 7 on Vista; Safari on Vista; and Konqueror on Ubuntu.)

---

### Post by slavik on 2008-09-13
> **pmasiar said:**
> I hope there is special ring in hell for managers in MSFT who force developers to release product with deliberately different quirks mode in each version, instead just following standards (which were developed with input from MSFT).

I heard about CSS framework Blueprint which is supposed to handle whose differences.

Solution we use is to design for standards-compliant browsers, place text "this site is best viewed in Firefox" and forget about it 8-)
I agree.

---

