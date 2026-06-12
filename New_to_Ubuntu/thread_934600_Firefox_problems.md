---
title: "Firefox problems"
date: 2008-09-30
forum: New to Ubuntu
---

### Post by Alchemists_Kitten on 2008-09-30
When I'm surfing the web, Firefox sometimes closes on its own. Anyone else having the same problem? Anyone know how to fix it?

Thanks, 
Alchemists_Kitten

---

### Post by Crafty Kisses on 2008-09-30
While Firefox is open, run the following command:
```
top
```
Post the results here.

---

### Post by Alchemists_Kitten on 2008-10-03
I ran the code you told me in the terminal but the results keep scrolling and changing.

---

### Post by Kellemora on 2008-10-03
Hi AK

I've been having that trouble at certain web sites for the last month!
I think it has to do with some Mickey$oft proprietary code they started using recently in banner ads.

It not only affects Firefox on all platforms, but Safari, Netscape, Mozilla and others.

With Safari on the DOZE, if I scroll down below the banner fast enough, it don't crash.  But all the rest won't let you scroll down until the page loads, then crashes and by then it's too late.

A lot of web sites are starting to use Shockwave for some ads too and we have nothing in Linux that they will recognize.  This sometimes causes a lock-up.

And I've yet to get Java jre-6 running on Firefox.

TTUL
Gary

---

### Post by eternalnewbee on 2008-10-03
Same problem here. I've actually had this thing for a while now. I get the feeling that it happens with certain web pages that won't load correctly...
Then Firefox disappears, and when I restart it, luckily get the restore session option, after which (most of the time) I can open the web page with no trouble. They call this a BUG. I'm not technical, but know that they handle these bugs at a website called launchpad something...
I guess we'll just have to be patient until a better version of firefox is released...

---

### Post by eternalnewbee on 2008-10-03
Kellemora is more knowledgeable about this. Thanks for the info Kellemora

---

### Post by Alchemists_Kitten on 2008-10-03
Thank you both. I knew it was a bug, but was wondering if there was a way to fix it. I'll just be patient like you said and wait for a better Firefox version.
Thanks, 
Alchemists_Kitten

---

### Post by oldsoundguy on 2008-10-03
An FYI, I run Script Blocker and have little issues with that banner crap. Also run Ad Block Plus.  At least I can get on the sites that are loaded with that junk.  You DO have to enable a script now and then, but usually only the primary script.  Others can be ignored.

---

### Post by fooman on 2008-10-03
what versions of flash and firefox are you using?

i was getting a crash on certain websites a version or 2 ago.

since firefox 3.0.3 and flash 10....i have had no such problems.

---

### Post by jmszr on 2008-10-03
Go to Tools>add-ons>search add-ons>and install Adblock Plus, Adblock Filterset.G Updater and NoScript. That should take care of the ads. You also might want to consider Swiftweasel (a Linux optimized version of Firefox). As noted above by oldsoundguy you will sometimes need to enable a primary javascript-not difficult-you'll see.

---

### Post by Alchemists_Kitten on 2008-10-04
> **fooman said:**
> what versions of flash and firefox are you using?

i was getting a crash on certain websites a version or 2 ago.

since firefox 3.0.3 and flash 10....i have had no such problems.

I'm using Firefox 8.04 LTS, and as for the flash, I have no clue.

---

### Post by crashcoredump on 2008-10-04
Me 2,
I would say it has been the past month on sites such as Orkut and Myspace where firefox is overwhelmed with embedded videos and banners.
I will try disabling some of this scripting and see what happens.

It has been quite a pain in the ***. I hope the FF developers find a work-around fairly soon.

-J

The error syntax seems to be something like this:

> Warning: Error in parsing value for property 'filter'.  Declaration dropped.
Source File: [http://img3.orkut.com/css/gen/base033.css](http://img3.orkut.com/css/gen/base033.css)
Line: 580

---

### Post by Alchemists_Kitten on 2008-10-05
> **crashcoredump said:**
> Me 2,
I would say it has been the past month on sites such as Orkut and Myspace where firefox is overwhelmed with embedded videos and banners.
I will try disabling some of this scripting and see what happens.

It has been quite a pain in the ***. I hope the FF developers find a work-around fairly soon.

-J

The error syntax seems to be something like this:

Sorry, I'm not very good with the technical side of computers. How do I disable scripting?

---

### Post by ddixonr on 2008-10-12
Try this: [http://ubuntuforums.org/showthread.php?t=904719]("http://ubuntuforums.org/showthread.php?t=904719")

---

### Post by kansasnoob on 2008-10-12
Since you're using 8.04 here's a link for the Flash 10 release candidate:

[http://launchpadlibrarian.net/16766494/flashplugin-nonfree_10.0.1.218%2B10.0.0.569ubuntu1%7Eppa2_i386.deb](http://launchpadlibrarian.net/16766494/flashplugin-nonfree_10.0.1.218%2B10.0.0.569ubuntu1%7Eppa2_i386.deb)

It's a .deb so it's easy to install, but first remove the old flash:

```
sudo apt-get remove --purge flashplugin-nonfree
```

Or, if you've installed flash via tar.gz:

```
cd ~/.mozilla
rm flashplayer.xpt libflashplayer.so
```

Don't worry if it says "not found" or something like that, if it's not there then it's just not there.

I also like to install all "sun-java6-***" except "-doc" and "-source". The easiest way to do that is just open synaptic and click on search - then type in sun-java6 and you'll see 9 packages that start with sun-java6. Just tick them all for installation - except sun-java6-doc and sun-java6-source.

Then while your in synaptic I'd also install "flashblock" and "adblock-plus". then just click on apply.

You'll have to restart Firefox (or possibly the whole desktop) to get all changes to apply.

---

