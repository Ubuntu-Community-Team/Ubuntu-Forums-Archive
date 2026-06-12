---
title: "Internet Explorer under wine - How to install?"
date: 2008-06-02
forum: New to Ubuntu
---

### Post by niceguy123 on 2008-06-02
I saw some mention on anther thread that this is possible with wine-doors. I tried installing but couldn't find the deb for fiesty. 

Can I run IE with wine? If so how do I go about installing it? 

(Why? - Because I need it to access certain sites that just don't work in other browsers).

---

### Post by billgoldberg on 2008-06-02
> **niceguy123 said:**
> I saw some mention on anther thread that this is possible with wine-doors. I tried installing but couldn't find the deb for fiesty. 

Can I run IE with wine? If so how do I go about installing it? 

(Why? - Because I need it to access certain sites that just don't work in other browsers).

Take a look here:

[http://www.tatanka.com.br/ies4linux/page/Main_Page](http://www.tatanka.com.br/ies4linux/page/Main_Page)

for IE7:

[http://webexpose.org/2007/01/07/internet-explorer-7-on-linux/](http://webexpose.org/2007/01/07/internet-explorer-7-on-linux/)

---

### Post by niceguy123 on 2008-06-02
> **billgoldberg said:**
> Take a look here:

[http://www.tatanka.com.br/ies4linux/page/Main_Page](http://www.tatanka.com.br/ies4linux/page/Main_Page)

for IE7:

[http://webexpose.org/2007/01/07/internet-explorer-7-on-linux/](http://webexpose.org/2007/01/07/internet-explorer-7-on-linux/)

I've tried ies4linux and it gets stuck all of the time.

---

### Post by Joeb454 on 2008-06-02
I think that's actually the only way of getting IE installed under Wine. How do you mean it "gets stuck all of the time"?

---

### Post by cheesypoof on 2008-06-02
If you have wine installed, you should already have a simple iexplore available.

> wine iexplore URL
Make sure when you type the URL, you include the full link. I have experienced loading problems if I don't do this.
Ex. [http://www.msn.com/](http://www.msn.com/)

---

### Post by niceguy123 on 2008-06-03
> I think that's actually the only way of getting IE installed under Wine. How do you mean it "gets stuck all of the time"?

It just friezes. 

> **cheesypoof said:**
> If you have wine installed, you should already have a simple iexplore available.


Make sure when you type the URL, you include the full link. I have experienced loading problems if I don't do this.
Ex. [http://www.msn.com/](http://www.msn.com/)

That's a neat tool. But its not solving my problem, the sites that don't work in regular Mozilla don't work in this one ether.

---

### Post by sicofante on 2008-07-16
Use wine-doors.

[http://www.wine-doors.org/wordpress/?page_id=3](http://www.wine-doors.org/wordpress/?page_id=3)

It makes it really easy to install not just Explorer, but a lot of Wine apps.

---

### Post by elmoosecapitan on 2008-07-16
Honestly, just get firefox and add the 'ie tab' plugin/add-on. IE can then be opened inside of ff. Thats how you get netflix to work on firefox.

---

### Post by krsmit0 on 2008-07-16
IE Tab is not available for Linux.

---

### Post by james_vanb on 2008-07-16
Have you looked at this?

[http://www.psychocats.net/ubuntu/ies4linux](http://www.psychocats.net/ubuntu/ies4linux)

---

### Post by sicofante on 2008-07-16
> **sicofante said:**
> Use wine-doors.

[http://www.wine-doors.org/wordpress/?page_id=3](http://www.wine-doors.org/wordpress/?page_id=3)

It makes it really easy to install not just Explorer, but a lot of Wine apps.
BEWARE: There's an issue with the current version of Wine Doors. I've used it in the past and has been working well, but apparently there's a bug in the latest version (I'm not sure how it affects older versions). Check it out here:

[http://www.wine-doors.org/wordpress/?p=57](http://www.wine-doors.org/wordpress/?p=57)

---

### Post by YaroMan86 on 2008-07-16
Personally, I don't see why anyone would put something as insecure as Internet Explorer on something as secure as Linux. But that's just me.

---

### Post by sicofante on 2008-07-16
> **YaroMan86 said:**
> Personally, I don't see why anyone would put something as insecure as Internet Explorer on something as secure as Linux. But that's just me.
LOL. Explorer is "insecure" in a Windows Environment. It's harmless in a Linux environment and there are lots of reasons to install it.

Web developers' needs make it obvious, but just many websites that don't work with Firefox make it a must. It depends obviously on the kind of websites you visit. Spain's Administration websites are not very Linux-friendly and many times don't work well except with IE. I have a Dlink router whose web-based administration tool doesn't work properly under Firefox.

---

### Post by Thelasko on 2008-07-16
Have you tried faking Firefox's [user agent?]("https://addons.mozilla.org/en-US/firefox/addon/59") It makes the website think your using IE.

---

### Post by Canis familiaris on 2008-07-16
If you only need IE temporarily, you can download Crossover Trial, install IE and run it; if there is indeed no other way.

---

### Post by Thelasko on 2008-07-16
If you are indeed trying to use Netflix's play now, good luck.  It appears you practically need Windows Genuine Advantage to get that to work.  Although, I did hear a rumor of someone getting WGA to work in Wine.

---

### Post by rhenium3 on 2008-07-27
Hi, I'm getting this message when I try to install ies4linux:

IEs4Linux 2 is developed to be used with recent Wine versions (0.9ost .x). It seems that you are using an old version. It's recommended that you update your wine to the latest version (Go to: winehq.com).


Except I have the most recent version of wine, so I don't know what it is talking about. Is there any way to install wine 0.9 so I can use ie. I need it for my work website, I can't access email otherwise.  I tried to run ie in wine and it just comes up blank :(

Please let me know, thanks!

---

### Post by rhenium3 on 2008-07-27
I wrote too quickly... the ie in program files on c drive that you get to via wine does not work. However I did install the ies4linux and it seems that I lost a window and did not finish installing it all the way.  Found the window, installed it, and now it works... :popcorn:

---

### Post by Thelasko on 2008-07-28
Sounds like you had this problem:
> Emulate Virtual Desktop - using this option makes installations run so much smoother. I found instances where attempting to run an installation without this option checked caused some dialog boxes, such as CD key entry or disk swap confirmation, to not come to the front when activated. This led me to believe that the install had become "stuck" and I would end up killing the process. This can also help when troubleshooting a problem game as it won't lock up your desktop or alter your screen resolution to an unusable state when the game fails.
[From this page.]("http://ubuntuforums.org/showthread.php?t=497332")

To make the IE in Program Files work I believe you have to install the gecko engine.
> Install the Wine Gecko IE engine - Some programs require Internet Explorer to be installed in order to run. However, installing Internet Explorer can severely break Wine. Instead, you should install the Wine Gecko IE engine. To install the Geko engine, do this:

   1. Run the following in the terminal:
     ```
 wine iexplore [http://www.winehq.org](http://www.winehq.org)
```

   2. Answer yes to the install prompt
   3. Go to the Useful Registry Keys page and scroll down to the HKEY_LOCAL_MACHINE section.
   4. Add all of the Internet Explorer keys by using regedit.
From the same page I linked above.

The Internet Explorer installed with ies4linux is "sandboxed" in your wine install to keep it from damaging wine.  Unfortunately, because of this, other programs can't use that install of IE.

---

### Post by gjoellee on 2008-07-28
running IE in WINE is simple, just follow my instructions if you are running ubuntu 7.04 or greater:

got to terminal and add this sentence....
```
sudo apt-get install wine cabextract
```and install....now:
```
cd ~
``````
wget http://www.tatanka.com.br/ies4linux/downloads/ies4linux-latest.tar.gz
``````
tar zxvf ies4linux-latest.tar.gz
``````
cd ies4linux-*
``````
./ies4linux  
```and make sure to install icon to desktop so you can use IE with a click of a button (you can move this later on)

tell me if you get any problems...

---

### Post by dew5 on 2008-07-28
worked for me thanks.
How ever when I try to open the short cut it nothing happens.  I reinstalled it and it worked, how ever when I close iexplore and try to boot from the short cut nothing happens again.

help?

dew

---

### Post by dew5 on 2008-07-28
never mind its solved

dew

---

