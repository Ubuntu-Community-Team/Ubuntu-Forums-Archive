---
title: "Does this online video work on your machine?"
date: 2008-10-12
forum: New to Ubuntu
---

### Post by stoogiebuncho on 2008-10-12
I have a friend who's dad just switched to Ubuntu and is a huge Nebraska Husker's fan.  He wants to watch the video off their site but it's not working for him.

I went and checked it out on my machine and it tells me that I need to install the latest version of WMP to view the video.

I use the vlc firefox plugins and they work great for every other site I've been to.  Is there another plugin I need, or is the site just refusing to send me the video because I'm not using Window$?

There's a sample video at the bottom of this page:
[http://www.huskers.com/ViewArticle.dbml?DB_OEM_ID=100&ATCLID=1265088&KEY=&DB_OEM_ID=100&DB_LANG=&IN_SUBSCRIBER_CONTENT=](http://www.huskers.com/ViewArticle.dbml?DB_OEM_ID=100&ATCLID=1265088&KEY=&DB_OEM_ID=100&DB_LANG=&IN_SUBSCRIBER_CONTENT=)

Does that work on anyone else's Ubuntu box?

I've tried using the agent-switcher to make it look like I"m using Vista, but then it tells me I need to install Flash.

Or, if there are other Husker's fans out there, is there an alternate site you could recommend for this poor fan?

Thanks.

---

### Post by jamesrl on 2008-10-12
I usually don't have problems playing video (e.g., mlb.tv, etc) but this one didn't work by default.  Does work within windows XP running virtualbox.

---

### Post by patrickballeux on 2008-10-12
They're are using the Flash player to use the Window Media Player?  They should use Flash directly since it is able to play streaming video.

Anyway, I did a small test, and they do not recognized the Flash 10 player in Firefox.  In Epiphany, they told me to download the wmpsomething.exe software...  

I think that the guy who made that site did not know how to create such a website...

You should complain to the owner of the site.

---

### Post by jpangamarca on 2008-10-13
> **stoogiebuncho said:**
> I have a friend who's dad just switched to Ubuntu and is a huge Nebraska Husker's fan.  He wants to watch the video off their site but it's not working for him.

I went and checked it out on my machine and it tells me that I need to install the latest version of WMP to view the video.

I use the vlc firefox plugins and they work great for every other site I've been to.  Is there another plugin I need, or is the site just refusing to send me the video because I'm not using Window$?

There's a sample video at the bottom of this page:
[http://www.huskers.com/ViewArticle.dbml?DB_OEM_ID=100&ATCLID=1265088&KEY=&DB_OEM_ID=100&DB_LANG=&IN_SUBSCRIBER_CONTENT=](http://www.huskers.com/ViewArticle.dbml?DB_OEM_ID=100&ATCLID=1265088&KEY=&DB_OEM_ID=100&DB_LANG=&IN_SUBSCRIBER_CONTENT=)

Does that work on anyone else's Ubuntu box?

I've tried using the agent-switcher to make it look like I"m using Vista, but then it tells me I need to install Flash.

Or, if there are other Husker's fans out there, is there an alternate site you could recommend for this poor fan?

Thanks.

Try installing totem-mozilla and totem-gstreamer:

```
$ sudo apt-get install totem totem-mozilla totem-gstreamer 
```

and restart Firefox.

---

### Post by stalkingwolf on 2008-10-13
I get the same " your version of wmv is old you need the new one" also.

Im using UbuntuEEE 8.04.1

---

### Post by t0p on 2008-10-13
> **stalkingwolf said:**
> I get the same " your version of wmv is old you need the new one" also.

Im using UbuntuEEE 8.04.1

I also get the "old wmv" stuff.  I'm running ubuntu 8.04.1 with the RiceeeyTweak/Niceee modifications detailed on the [eeeuser wiki]("http://wiki.eeeuser.com").

---

### Post by HellNoire on 2008-10-13
If you have to run WMP, sometimes (and I hate to say this because I hate it with a passion) you need to use it. 

[http://www.getdeb.net/app/Wine-Doors](http://www.getdeb.net/app/Wine-Doors)

That link has Wine-Doors to download, and once that is installed, you can install WMP9.

Or if you'd like to stay more open source, you could always look for the VLC plug-in for Firefox. I think that would work too.

---

### Post by stoogiebuncho on 2008-10-13
Thanks for all the responses - it's looking to me like the problem must be in the way the website was coded, not in my video plugins, seeing as no one else has been able to get it working off of Ubuntu either.

The Wine-Doors idea is an interesting one.  I might try it out myself, but I'm guessing it would be too complicated for our Husker's fan.  I doubt he would feel brave enough to try it himself.

So I'm going to write a polite letter to the Husker's website manager, and start looking around for other places for my friend to tune into the game.  Thanks again for your help.

---

