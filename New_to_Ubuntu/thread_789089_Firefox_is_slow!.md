---
title: "Firefox is slow!"
date: 2008-05-10
forum: New to Ubuntu
---

### Post by abhiroopb on 2008-05-10
I have firefox 2, and I will not be upgrading to version 3 until the final update. This is not a negotiable factor, as I dislike using beta software as much as I can. Especially since some of my extensions will not work (I tried it and it looked really really weird, because of my stylish scripts not installing properly so it was half way between 3.0 and what I had previously!!)

My problem right now is that FF has been causing me A LOT of problems. It crashes, slows downm just hangs, its  a real pain.

Anyway for now here are the extensions I have and I would like to know if any of them have been known to cause problems:

Adblock PLus 0.7.5.4
FEBE 5.3.1
FireFTP 0.97.1
FoxClocks 2.3.4
Greasemonkey 0.7.20080121.0
    HTTP to HTTPS redirector
    Linkify Ting
    Textarea Backup
    Facebook to Google Calendar
    6 Digg mirror
    Lifehacker Quote in Reply

Linky 2.7.1
McAfee SiteAdvisor 26.5
NoScript 1.6.5
PDF DOwnload 1.0.1.1
Safe Cache 0.9
Searchbad Autosizer 1.3.7
Secure Login 0.9.1.1
Stylish 0.5.6
    Colorize Firefox 2 Active Tab
    flat statusbar
    Slim down Firefox GUI
    Slim Tabs
    WellRounded 2

Tab Mix Plus 0.3.6

Themes:
Classic Compact

I know this is a LOT, so please I'd rather not have any comments criticizing my setup, unless it is known that one of these extensions actually causes a problem. Its just that I have seen posts like this before where the first thing people say is that you have too many. Now I haven't read anywhere that having simply too many extensions can slow down a system. If it can please let me know, and I'll try and thin things down. I do know that certain extensions DO cause problems. Anyway I use all these extension quite regularly, so much so that I barely realise that they're being used!! Its almost become like a part of firefox. So, let me know what you think! Thanks

---

### Post by dtrot55 on 2008-05-10
Yeah i've been having issues with FF3 Beta so I installed Seamonkey...so far so good...will probably install Opera though because its the next best thing after FF.

---

### Post by joshsmith on 2008-05-10
having a lot of extensions CAN slow down firefox, as it has to do more things, and as extensions might not be amazingly coded

if you try disabling extensions you can work out what the problem ones are

ps try updating your computer, one cause of hangs has just been fixed.

---

### Post by TenPlus1 on 2008-05-10
Try this, it may help:

Open Terminal and type:

sudo gedit /etc/firefox/firefoxrc

Add this line to the end of the file:

export XLIB_SKIP_ARGB_VISUALS=1 

you may also add this line to disable pango text rendering which can be pretty slow, but this may make things 2-7 times faster:

export MOZ_DISABLE_PANGO=1

Save file and start firefox up again. No more flash freezes and faster rendering.

---

### Post by hyper_ch on 2008-05-10
> **abhiroopb said:**
> Especially since some of my extensions will not work (I tried it and it looked really really weird, because of my stylish scripts not installing properly so it was half way between 3.0 and what I had previously!!)
There's an easy solution...

---

### Post by abhiroopb on 2008-05-10
> **joshsmith said:**
> having a lot of extensions CAN slow down firefox, as it has to do more things, and as extensions might not be amazingly coded

if you try disabling extensions you can work out what the problem ones are

ps try updating your computer, one cause of hangs has just been fixed.

Zero Updates :(...

I've tried that, unfortunately its not always slow and it would take forever for me to individually try everything and see if it is slow or not.


> 
There's an easy solution...


which is?

---

### Post by tjwoosta on 2008-05-10
i have had many problems with the mccaffe site advisor plugin

i installed it in the first place just because this computer shares alot of files with my windows machine and i didnt not want to infect windows with some strange virus

the problem is that i causes firefox to randomly stall out (it will just stop responding for a wile, then kick back in after about 30 seconds to 1 minute)

this happened enough to make me uninstall and reinstall firefox


(but to be honest the new opera 9.50 beta 2 is far faster and smoother than firefox and there are way less bugs) 

the only thing i dont like is how opera doesnt really have as many usefull extensions as firefox did

---

### Post by hyper_ch on 2008-05-10
> **abhiroopb said:**
> which is?
Nightly Build Test Addon

---

### Post by exaviorn on 2008-05-10
> **joshsmith said:**
> having a lot of extensions CAN slow down firefox, as it has to do more things, and as extensions might not be amazingly coded

I agree with joshsmith,if I had that many extentions my browser would be slow,I presume the mcaffe site block and grease monkey will slow thing down! (depending on how many greasemonkey scripts are being used:))

---

### Post by joshsmith on 2008-05-10
oh btw, you can try to use extensions that the developer hasnt said will specifically work with firefox 3.0 by adding
extensions.checkCompatibility
as a boolean and to false
in about:config
this will then just ignore if it says compatible with ff2 only

most of my extensions worked perfectly after this (it was just the dev hadnt bothered to test their extension of ff3, and change the extension to say it worked)

---

### Post by abhiroopb on 2008-05-10
Ok So i decided to try out ff3 and see which ones would be incompatible. 

I also thinned down my list:

Adblock PLus 0.7.5.4
FEBE 5.3.1
FoxClocks 2.3.4
Greasemonkey 0.7.20080121.0
NoScript 1.6.5
Secure Login 0.9.1.1
Tab Mix Plus 0.3.6

Themes:
Classic Compact

Unfortunately FEBE and tab mix plus don't work, any way to get them to work? As they are quite important. Anyway otherwise it looks ok, runs well enough. So I may just use it now if I don't have any problems.

---

### Post by abhiroopb on 2008-05-10
OK so now for whatever reason ff 3.0beta4 (from the repo) is officially worse than ff2. I opened up the subscriptions page on ubuntu forums and clicked on the page for this thread, and everything stopped for a few seconds and then the page loaded. Then I was scrolling down the thread and everything stopped again.

Similar thing happened in digg.com.

Also the hard disk light on my laptop starts flashing. Not sure whats going on.

Any thoughts?

---

