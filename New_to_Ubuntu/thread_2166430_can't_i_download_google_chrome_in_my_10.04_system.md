---
title: "can't i download google chrome in my 10.04 system?"
date: 2013-08-09
forum: New to Ubuntu
---

### Post by tojonukokhadush on 2013-08-09
gee! i recently replaced google chrome by chromium! what i greatly miss is the pdf viewer within the google chrome which i could not get in chromium. 

so coming to the point, is there any chance i can reinstall google chrome in my system again without needing to upgrade to 12.04?

---

### Post by lego11 on 2013-08-09
Hi,
does downloading Chrome from here 
[https://www.google.com/intl/en/chrome/browser/](https://www.google.com/intl/en/chrome/browser/)
works?
You have to select 32 or 64bit based on your system arch.
If it doesn't work, please post the error message so that I can help you further.
Thanks

---

### Post by Ninja&gt;Master on 2013-08-09
***Option 1:***
Open up terminal and type in:
```

sudo apt-get install google-chrome-stable

```

Though, you might not get the *latest* version, but you will get a version 20+ I guess.

[B][I]Option 2:
[/I][/B]
Visit: [https://www.google.com/intl/en/chrome/browser/](https://www.google.com/intl/en/chrome/browser/)
Click the blue button "Download Chrome", select the 32bit/64bit (depending on your system) Ubuntu/Debian package. Then install with the downloaded .deb file.

---

### Post by slickymaster on 2013-08-09
Google has dropped support for Ubuntu 10.04 as of Chrome 26, which was released last March.

---

### Post by Boab1993 on 2013-08-09
Hello tojonukokhadush,

As i was informed on your previous post that the repositries were closed for 10.04 after LTS was stopped, i had a look around to see if you can get packages else where.

Came across this: [http://www.ubuntuupdates.org/](http://www.ubuntuupdates.org/)

It has a packages section which has previous versions of google chrome, and the updates that proceed the older package.

Hope this helps

---

### Post by deadflowr on 2013-08-09
What did you do with the old deb?

---

### Post by tojonukokhadush on 2013-08-09
Hi everyone! thank you for your help & i deleted it deadflowr!:lolflag:

tried via terminal and it says- "E: Couldn't find package google-chrome-stable"

recently i am downloading .deb file; i'll let you know what happens further, need to wait a bit coz net is a bit slow!

---

### Post by deadflowr on 2013-08-09
Looking beyond the lack of your old lack of the old deb, I realized you pretty much just want the pdf reader, right?
If by chance you can find an older version of chrome try following these methods to move the pdf stuffs into your chromium stuff.
Thus, hopefully, eliminating your need to use Google-Chrome at all.

[http://www.omgubuntu.co.uk/2010/07/use-google-chrome%E2%80%99s-native-pdf-reader-in-chromium](http://www.omgubuntu.co.uk/2010/07/use-google-chrome%E2%80%99s-native-pdf-reader-in-chromium)

---

### Post by tojonukokhadush on 2013-08-09
neither the .deb file got installed! what shows up is- (see image posted). 

nor any of the methods explained here- [http://www.omgubuntu.co.uk/2010/07/u...er-in-chromium]("http://www.omgubuntu.co.uk/2010/07/use-google-chrome%E2%80%99s-native-pdf-reader-in-chromium") worked! 
i also ended up showing "missing plugin/ couldn't load plugin" error message!


so far i guess, it should be working! the only problem seems that i couldn't figure out hidden technicality! please some experts do help me! i desperately need that pdf viewer!!

---

### Post by Ninja&gt;Master on 2013-08-09
You might want to read this: [http://www.omgchrome.com/google-chrome-drops-support-for-ubuntu-10-04/](http://www.omgchrome.com/google-chrome-drops-support-for-ubuntu-10-04/).

***EDIT:***
Well, after some digging on the interwebs, I've found a gconf package for Ubuntu 10.04. You need to compile it from source though. Here it is:
[https://launchpad.net/ubuntu/lucid/+source/gconf/2.28.1-0ubuntu1/+files/gconf_2.28.1.orig.tar.gz](https://launchpad.net/ubuntu/lucid/+source/gconf/2.28.1-0ubuntu1/+files/gconf_2.28.1.orig.tar.gz)

I found it here: [https://launchpad.net/ubuntu/lucid/+source/gconf/2.28.1-0ubuntu1](https://launchpad.net/ubuntu/lucid/+source/gconf/2.28.1-0ubuntu1)

Try installing Google Chrome after installing that.
Good luck :).

---

### Post by Boab1993 on 2013-08-09
I found a stable, downloadable, compatible with 10.04 version of chromium(the open source google chrome) here:

[http://www.ubuntuupdates.org/package/chromium_stable_channel/lucid/main/base/chromium-browser](http://www.ubuntuupdates.org/package/chromium_stable_channel/lucid/main/base/chromium-browser)

try the .deb package download.

---

### Post by monkeybrain20122 on 2013-08-09
Why do you stick with a dead release? You should install 12.04 to save yourself further troubles.

---

### Post by Ninja&gt;Master on 2013-08-09
> **Boab1993 said:**
> I found a stable, downloadable, compatible with 10.04 version of chromium(the open source google chrome) here:

[http://www.ubuntuupdates.org/package/chromium_stable_channel/lucid/main/base/chromium-browser](http://www.ubuntuupdates.org/package/chromium_stable_channel/lucid/main/base/chromium-browser)

try the .deb package download.

He wants the "Google Chrome", by Google. Not the open-source "Chromium". ;)

---

### Post by Boab1993 on 2013-08-09
> **Ninja>Master said:**
> He wants the "Google Chrome", by Google. Not the open-source "Chromium". ;)

Yes but as they are essentially the same thing i.e. the functionality, and he is having trouble obtaining anything that will work atall, im making a suggestion as this is a stable download.

---

### Post by tojonukokhadush on 2013-08-09
okay **[COLOR=#000000][monkeybrain20122]("http://ubuntuforums.org/member.php?u=1843403")[/COLOR]**

10.04 was the so far the most stable version for me, i got stuck with it! :-D 

also since i have quite old configuration of my laptop(ref. the image attached), i am wondering i may not end up making the system more slow 

which i do not expect! and also to mention i have power problems in my country! but seems that i need to upgrade it sooner! the thing so far i 
don't like about 12.04 is there are no panels and tabs :-(




& **[COLOR=#000000][Boab1993]("http://ubuntuforums.org/member.php?u=1602050") [/COLOR]**

that's so kind of you but i am already using chromium and what let me sought google chrome back is the default pdf viewer of google chrome not being available in chromium! 

anyway thank you all for the help! :-D

---

### Post by VMC on 2013-08-09
you can install the classic gnome-panel ([COLOR=#333333][FONT=UbuntuMono]sudo apt-get install gnome-panel[/FONT][/COLOR][COLOR=#333333][FONT=UbuntuMono] ), [/FONT][/COLOR]and feel right at home using Precise 12.04.
Have a look see on how to do just that:
[PreciseGnomeClassic]("https://help.ubuntu.com/community/PreciseGnomeClassicTweaks")

---

### Post by monkeybrain20122 on 2013-08-09
> **VMC said:**
> you can install the classic gnome-panel ([COLOR=#333333][FONT=UbuntuMono]sudo apt-get install gnome-panel[/FONT][/COLOR][COLOR=#333333][FONT=UbuntuMono] ), [/FONT][/COLOR]and feel right at home using Precise 14.04.
Have a look see on how to do just that:
[PreciseGnomeClassic]("https://help.ubuntu.com/community/PreciseGnomeClassicTweaks")

You mean Precise 12.04

@OP,

If you haven't used 12.04 how do you know it is not stable? I mean, you sound as though it is sheer luck that you have a stable Ubuntu so that you have to cling on to it even if it is long dead, that doesn't sound like having a lot of confidence in Ubuntu. : )  I would not keep a dead OS around just for "stability", you already run into problems and there will be more as times go on. Also, if you machine is weak use a light DE like LXDE (e.g Lubtuntu 12.04) it would be much faster than gnome-2. You can also try Debian stable (or oldstable if you want something really old, which will get security updates for another year)

---

### Post by tojonukokhadush on 2013-08-10
yeah! it was "so far stable" ;-) i did not say 12.04 is unstable! i am only afraid that my hardware would not be quite enough! but i will soon upgrade 

to 12.04, download gnome panel and enjoy a lot; PROBLEM'S SOLVED, ONCE & FOR ALL! :-D :-D

THANK YOU ALL FOR THE HELP!!

---

