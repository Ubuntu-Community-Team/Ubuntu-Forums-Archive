---
title: "[SOLVED] 8.04 Firefox running too slow"
date: 2008-07-26
forum: New to Ubuntu
---

### Post by m_ad on 2008-07-26
I've researched this and I've read a lot of people disappointed all together with Firefox on Ubuntu. I've never had this problem until recently, and I don't know why. It works fine on my laptop (with compiz enabled also).

Basically it's only the scrolling on webpages with black backgrounds. Using the scroll button on the mouse is unbearable and even grabbing the scroll bar is lagged. Like I said, scrolling on ubuntuforums is fine, it's only with black backgrounds.

Is there any solution?

EDIT: I have an nVidia video card with the drivers installed and compiz enabled, I turned the Animations down a lot (but I hated doing it :lolflag:) and that didn't fix it.

---

### Post by PHATSPEED7x on 2008-07-26
I'm running it on two computers and I havn't had problems.

---

### Post by UbuntuNerd on 2008-07-26
have you tried disabling IPv6 read in this link it may help !!!


[https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4](https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4)

---

### Post by m_ad on 2008-07-26
Will disabling IPv6 affect anything else?

---

### Post by UbuntuNerd on 2008-07-26
I don't think is  standard right now..will be sometime in the future but someone please correct me if I'm wrong

---

### Post by UbuntuNerd on 2008-07-26
you can also look in here  

[http://en.opensuse.org/Disable_IPv6_for_Firefox]("http://en.opensuse.org/Disable_IPv6_for_Firefox")

---

### Post by northern lights on 2008-07-26
> **jperez78 said:**
> I don't think is  standard right now..will be sometime in the future but someone please correct me if I'm wrong

Nope, no corrections required. That's pretty much true.

Quick info:
The old/current standard is IPv4, with a theoretical range of IP addresses from 0.0.0.0 to 255.255.255.255, that's 256^4=4.29x10^9 or 4 billion possible combinations. Today, around 85% of those are already spoken for / in use. Thus, to ensure further growth of the web, a new standard is necessary. Most ISPs have not switched to IPv6 however...

---

### Post by m_ad on 2008-07-26
This didn't help the unbearably slow scrolling on black backgrounds :(

---

### Post by UbuntuNerd on 2008-07-26
I just did a little research and there seems to be a problem with Firefox lagging on the scrolling speed I would check Firefox FAQ or forums for an answer

---

### Post by m_ad on 2008-07-26
> **jperez78 said:**
> I just did a little research and there seems to be a problem with Firefox lagging on the scrolling speed I would check Firefox FAQ or forums for an answer

Unfortunately I can't find a solution to this problem.

---

### Post by BGFG on 2008-07-26
What version are you using ? there's 3.0 and 3.0.1 I initially had lots of problems with firefox's default install from the live cd but when i completely purged and re-installed it as well as the Ubuntu compatibility extras it's performance drastically improved.

---

### Post by gjoellee on 2008-07-26
1.Type &#8220;about:config&#8221; into the address bar and hit return. Scroll down and look for the following entries:
> network.http.pipelining network.http.proxy.pipelining
network.http.pipelining.maxrequests
Normally the browser will make one request to a web page at a time. When you enable pipelining it will make several at once, which really speeds up page loading.

2. Alter the entries as follows:
> Set &#8220;network.http.pipelining&#8221; to &#8220;true&#8221;
Set &#8220;network.http.proxy.pipelining&#8221; to &#8220;true&#8221;
Set &#8220;network.http.pipelining.maxrequests&#8221; to some number like 30. This means it will make 30 requests at once.
3. Lastly right-click anywhere and select New-> Integer. Name it 
> nglayout.initialpaint.delayand set its value to &#8220;0&#8243;. This value is the amount of time the browser waits before it acts on information it receives.

If you&#8217;re using a broadband connection you&#8217;ll load pages MUCH faster now!

This should work with Firefox 2.0 or better

---

### Post by m_ad on 2008-07-26
> **BGFG said:**
> What version are you using ? there's 3.0 and 3.0.1 I initially had lots of problems with firefox's default install from the live cd but when i completely purged and re-installed it as well as the Ubuntu compatibility extras it's performance drastically improved.

I'm using 3.0.1 which explains why I can't load ANY themes because it says I'm using a newer version than the theme is compatible with.

EDIT: It looks like the only version available through Synaptic is 3.0.1 or 2.0. Maybe I'll try 2.0 :lolflag:

to gjoellee: those changes don't increase the scroll speed :(

---

### Post by Joeb454 on 2008-07-26
It could also be a compiz issue. Firefox (and Opera) lag horribly for me when I'm scrolling...IF compiz is enabled. Works fine when the metacity compositor is enabled though :)

---

### Post by m_ad on 2008-07-26
> **Joeb454 said:**
> It could also be a compiz issue. Firefox (and Opera) lag horribly for me when I'm scrolling...IF compiz is enabled. Works fine when the metacity compositor is enabled though :)

So we just have to deal with this laggy scroll? It's VERY annoying.

Well, my laptop has compiz enabled with the same release of Ubuntu (8.04) and it works fine. It must be my geforce card..?

---

### Post by Joeb454 on 2008-07-26
It could be.

Hit Alt+F2 and enter ```
metacity --replace
``` and then try again and see if the issue persists

---

### Post by m_ad on 2008-07-26
I actually was trying that before you gave the suggestion. I tried changing the window manager, and I disabled compiz all together.

Still the scrolling is to the point where I don't want to use Firefox. The weird thing is, it only happens with black backgrounds.

---

### Post by gjoellee on 2008-07-26
does this happen when different applications are running flash or java at the same time?

---

### Post by m_ad on 2008-07-26
Nothing running but Firefox with this forum in one tab and another (with the black background) in another.

---

### Post by crjackson on 2008-07-26
How about installing a different browser and see if it has that problem.

How about launching firefox from the terminal with sudo and see if it also has that problem.

---

### Post by gjoellee on 2008-07-26
what you can do is either see if disabling compiz fusion makes firefox work better, or you can try to do what is posted i little earlier (whic helped for me), or try use an other web browser, (i would recommend Opera or Flock then), if nothing of this work i don't know what to do...

---

### Post by m_ad on 2008-07-26
> **crjackson said:**
> How about installing a different browser and see if it has that problem.

How about launching firefox from the terminal with sudo and see if it also has that problem.

First suggestion. I installed Epiphany and it scrolled without a problem.

Second suggestion. sudo firefox didn't improve :(

SO, the problem lies within Firefox..

---

### Post by gjoellee on 2008-07-26
the support team on PolishUbuntu  ([http://www.polishubuntu.co.nr/](http://www.polishubuntu.co.nr/)) know more about the technical stuff, maybe they can help you

---

### Post by m_ad on 2008-07-27
What version of Firefox does Ubuntu 8.04 install as default? All I see in Synaptic is 3.0.1, which doesn't allow me to install any themes (says I'm using a newer version). I would like to try an older version, either 3.0 or 2.0.x.

I'm assuming that installing 2.0.x would be a security risk? I would like some feedback on older versions of Firefox, as I think they would solve my problem.

---

### Post by gjoellee on 2008-07-27
i think Firefox 3 BETA5 comes default in Hardy  (it runs quit slow)

---

### Post by m_ad on 2008-07-27
Is it not advised to use 2.0 instead of 3.0 beta 5?

---

### Post by gjoellee on 2008-07-27
well 2.0 is more stable then the BETA, but i would recommend to use firefox 3.0.1, add some addons that may help firefox run better and look better etc... [https://addons.mozilla.org/en-US/firefox/](https://addons.mozilla.org/en-US/firefox/)

and use this tweak: 

1.Type &#8220;about:config&#8221; into the address bar and hit return. Scroll down and look for the following entries:
     Quote:
                                                 network.http.pipelining network.http.proxy.pipelining
network.http.pipelining.maxrequests                                 
Normally the browser will make one request to a web page at a time. When you enable pipelining it will make several at once, which really speeds up page loading.

2. Alter the entries as follows:
     Quote:
                                                 Set &#8220;network.http.pipelining&#8221; to &#8220;true&#8221;
Set &#8220;network.http.proxy.pipelining&#8221; to &#8220;true&#8221;                                 
Set &#8220;network.http.pipelining.maxrequests&#8221; to some number like 30. This means it will make 30 requests at once.
3. Lastly right-click anywhere and select New-> Integer. Name it 
     Quote:
                                                 nglayout.initialpaint.delay                                 
and set its value to &#8220;0&#8243;. This value is the amount of time the browser waits before it acts on information it receives.

If you&#8217;re using a broadband connection you&#8217;ll load pages MUCH faster now!

This should work with Firefox 2.0 or better

As well as getting flash 10: [http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_install_linux_070208.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_install_linux_070208.tar.gz)

To get firefox 3.0.1 > sudo apt-get install firefox

---

### Post by m_ad on 2008-07-27
I've done those tweaks and the scrolling is still unbearable.

I realized it's really only slow on a bboard with a background image.

---

### Post by gjoellee on 2008-07-27
well I have the same problem (if I think the same as you), you should add send this bug report to the Firefox team...:KS i will add a post with a link to a page that is slow for me....

---

### Post by gjoellee on 2008-07-27
this page lags when scrolling right? [http://www.polishubuntu.piczo.com/slowpage/](http://www.polishubuntu.piczo.com/slowpage/)

---

### Post by halitech on 2008-07-27
scrolls fine for me, Gutsy 7.10, FF3.0

---

### Post by m_ad on 2008-07-27
> **gjoellee said:**
> this page lags when scrolling right? [http://www.polishubuntu.piczo.com/slowpage/](http://www.polishubuntu.piczo.com/slowpage/)

That page actually scrolls fine :confused:

---

### Post by m_ad on 2008-07-27
AAAH! I figured it out!!!

I set the page text (Ctrl+Mouse scroll btn) smaller than it really is. This caused the scrolling to be slow. I made it bigger (default) and it scrolls fine.

This had to be a bug..?

---

