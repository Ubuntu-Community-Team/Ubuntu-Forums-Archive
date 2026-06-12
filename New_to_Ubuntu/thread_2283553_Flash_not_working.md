---
title: "Flash not working"
date: 2015-06-22
forum: New to Ubuntu
---

### Post by anbu-s on 2015-06-22
Adobe flash is not wirking in firefox or chrome browser in my new Gnome install 15.04

I've done all the installs mentioned in this thread (ironically it was my thread during my first Ubuntu install!!)

[http://ubuntuforums.org/showthread.php?t=2261869](http://ubuntuforums.org/showthread.php?t=2261869)

But still its not working - browser says adobe flash not installed.

How do i fix this?

---

### Post by branau on 2015-06-23
I'm not sure if you're using Firefox or Chromium, but as of May this year, the current way to install Flash player is to go to your Software settings and allow software from Canonical partners, and then download the adobe-flashplugin from either the software center or the terminal. You can find detailed instructions on how to do that [here](https://wiki.ubuntu.com/Chromium/Getting-Partner-Flash).

---

### Post by anbu-s on 2015-06-23
Thanks for your reply. I did allow canonical software and then downloaded the flash plugin. It installed without any issues - but firefox is still having the same issue. No adobe flash player message is displayed on the websites.

---

### Post by VMC on 2015-06-23
From Firefox, does "Open menu > Add-ons > Plugins" show  "Shockwave Flash" ?

---

### Post by Geoffrey_Arndt on 2015-06-23
When you do what VMC says (in menu:  "Tools>Add ons>Plug ins" . . . ) what version of Flash is installed in your Firefox (by the way  -  did you use the Ubuntu Software Center to install "restricted-extras" package)?

Since a few websites don't like the older versions of Flash, you can always install the "Chromium" browser , and then install "pepperflash" plugin from Ubuntu Software Center.   Chromium runs the lastest Flash for sites requiring it.

---

### Post by anbu-s on 2015-06-23
> **Geoffrey_Arndt said:**
> When you do what VMC says (in menu:  "Tools>Add ons>Plug ins" . . . ) what version of Flash is installed in your Firefox (by the way  -  did you use the Ubuntu Software Center to install "restricted-extras" package)?

Since a few websites don't like the older versions of Flash, you can always install the "Chromium" browser , and then install "pepperflash" plugin from Ubuntu Software Center.   Chromium runs the lastest Flash for sites requiring it.

Yes firefox add on displays shockwave flash 11.2.r202

I also installed chrome and pepperflash plugin. Now it doesn't display flash missing message - but still doesn't play the video content.

---

### Post by flaymond on 2015-06-23
You will need some 'restricted-extras' to play non HTML5-flash videos.

---

### Post by kostkon on 2015-06-23
> **InterProg said:**
> You will need some 'restricted-extras' to play non HTML5-flash videos.
Actually, that should be: You will need some 'restricted-extras' to play HTML5 non-flash videos.

---

### Post by anbu-s on 2015-06-23
> **kostkon said:**
> Actually, that should be: You will need some 'restricted-extras' to play HTML5 non-flash videos.

I've installed the restricted-extras as well via software centre. Still the same issue - firefox says no adobe flash. In chrome, it plays the advertisement of the live tv website but still nothing after that. The website i'm trying is tsn.ca/tv

I've installed the pipelight also for chrome which is supposed to work.

So its really puzzling why the flash player doesn't work in both the browsers/

---

### Post by kostkon on 2015-06-23
> **anbu-s said:**
> I've installed the restricted-extras as well via software centre. Still the same issue - firefox says no adobe flash. In chrome, it plays the advertisement of the live tv website but still nothing after that. The website i'm trying is tsn.ca/tv

I've installed the pipelight also for chrome which is supposed to work.

So its really puzzling why the flash player doesn't work in both the browsers/
In Chrome you don't need to install anything, it comes with its own Flash and video codecs. Is it really Chrome you are using or Chromium?

In Chromium, you need to install the package pepperflashplugin-nonfree to get Flash and the restricted extras for HTML5 videos.

Again, in Firefox, you need to install the package flashplugin-installer to get Flash and the restricted extras for the playback of HTML5 videos.

Hope that helps.

---

### Post by anbu-s on 2015-06-23
> **kostkon said:**
> In Chrome you don't need to install anything, it comes with its own Flash and video codecs. Is it really Chrome you are using or Chromium?

In Chromium, you need to install the package pepperflashplugin-nonfree to get Flash and the restricted extras for HTML5 videos.

Again, in Firefox, you need to install the package flashplugin-installer to get Flash and the restricted extras for the playback of HTML5 videos.

Hope that helps.

I'm using both chrome (not chormium) and firefox.
In google chrome, it plays the advertisement  but no live tv. In firefox (after installing flashplugin-installer and ubuntu restricted extras) it still says no adobe flash and nothing plays.

Just to try it out, i downloaded chromium browser also - same result as google chrome.

I'm on Gnome ubuntu 15.04

---

### Post by monkeybrain20122 on 2015-06-24
Which website is that? Maybe the flash stream is drm protected.

---

### Post by flaymond on 2015-06-24
* Thanks for help kostkon! About my previous reply! ;)

Anyway, I'm kinda curious about this - [http://www.zdnet.com/article/why-flash-and-html5-need-each-other/](http://www.zdnet.com/article/why-flash-and-html5-need-each-other/)

I think HTML5 videos does really need Flash to run, and till today I never find any plugin to run HTML5 videos without Flash. If not, I think I just need to explore more.

# exceptional to video withOut Flash firefox plugin.

---

### Post by anbu-s on 2015-06-24
> **monkeybrain20122 said:**
> Which website is that? Maybe the flash stream is drm protected.

May be it is drm protected. But it worked with my previous install of Gnome 14.04.02 LTS

tsn.ca/tv

---

### Post by Geoffrey_Arndt on 2015-06-24
OK,  does video work on other sites?  Youtube, LiveLeak, etc?    On my system, yes, but this site is heavily encumbered with DRM and authentication for content provider network (ISP) . . . the label about needing Flash is not accurate.   So, perhaps a few days ago it did work??? . . . but these sites are always adding restrictions on a progressive basis.   What they want is for you to login and provide verification that you're a customer of a particular provider (Bell, Charter, Cox, etc.).

On these site, Linux supported media codecs are a "NON_STARTER"  . . . .

---

### Post by monkeybrain20122 on 2015-06-24
> **InterProg said:**
> * Thanks for help kostkon! About my previous reply! ;)

Anyway, I'm kinda curious about this - [http://www.zdnet.com/article/why-flash-and-html5-need-each-other/](http://www.zdnet.com/article/why-flash-and-html5-need-each-other/)

I think HTML5 videos does really need Flash to run, and till today I never find any plugin to run HTML5 videos without Flash. If not, I think I just need to explore more.

# exceptional to video withOut Flash firefox plugin.

Normal HTML5 doesn't need any plugin to run providing the system can decode x264 (install restricted extras) Some HTML5 streams for drmed material would require an extra module in the browser, e.g Netflix and that's why it only works on Chrome on Linux.

---

### Post by monkeybrain20122 on 2015-06-24
> **anbu-s said:**
> May be it is drm protected. But it worked with my previous install of Gnome 14.04.02 LTS

tsn.ca/tv

Can't test it, you have to log in to watch. May be they changed on their end and has nothing to do with your OS upgrade.

If it is drmed maybe you need hal [https://launchpad.net/~mjblenner/+archive/ubuntu/ppa-hal](https://launchpad.net/~mjblenner/+archive/ubuntu/ppa-hal)
Hal only works with system flash (11.2) and won't work for Chrome's pepper flash.

Alternatively use pipelight flash (again Firefox only), it is a hack to run Windows flash in wine.
[http://pipelight.net/cms/install/installation-ubuntu.html](http://pipelight.net/cms/install/installation-ubuntu.html) 
[http://pipelight.net/cms/installation.html#section_2](http://pipelight.net/cms/installation.html#section_2)

---

### Post by anbu-s on 2015-06-24
> **Geoffrey_Arndt said:**
> OK,  does video work on other sites?  Youtube, LiveLeak, etc?    On my system, yes, but this site is heavily encumbered with DRM and authentication for content provider network (ISP) . . . the label about needing Flash is not accurate.   So, perhaps a few days ago it did work??? . . . but these sites are always adding restrictions on a progressive basis.   What they want is for you to login and provide verification that you're a customer of a particular provider (Bell, Charter, Cox, etc.).

On these site, Linux supported media codecs are a "NON_STARTER"  . . . .

Other sites are playing..youtube etc

For the tsn.ca/tv website, i do have a login via my isp and put in the user name and password. Then only it starts playing the ad on chrome and then nothing. With firefox, nothing at all.

It was working fine till i installed Gnome 15.04 fresh. before i was on 14.04.02 LTS

So no solution for this? Same websites work on my windows and apple laptops (same user name and password)

---

### Post by monkeybrain20122 on 2015-06-24
> **anbu-s said:**
> 

So no solution for this? Same websites work on my windows and apple laptops (same user name and password)

I just told you how.

---

### Post by anbu-s on 2015-06-24
> **monkeybrain20122 said:**
> Can't test it, you have to log in to watch. May be they changed on their end and has nothing to do with your OS upgrade.

If it is drmed maybe you need hal [https://launchpad.net/~mjblenner/+archive/ubuntu/ppa-hal](https://launchpad.net/~mjblenner/+archive/ubuntu/ppa-hal)
Hal only works with system flash (11.2) and won't work for Chrome's pepper flash.

Alternatively use pipelight flash (again Firefox only), it is a hack to run Windows flash in wine.
[http://pipelight.net/cms/install/installation-ubuntu.html](http://pipelight.net/cms/install/installation-ubuntu.html) 
[http://pipelight.net/cms/installation.html#section_2](http://pipelight.net/cms/installation.html#section_2)

Thanks. it works now!!
Not sure what fixed it.

I've done the pipelight flash already and didnt work
Now i've installed hal and tried it - no luck

Then I redid the pipelight install again and enabled flash with pipe light

Now firefox works for this website (tsn.ca/tv). But nothing in chrome after the advertisement.

---

### Post by monkeybrain20122 on 2015-06-24
> **anbu-s said:**
> Thanks. it works now!!
Not sure what fixed it.

I've done the pipelight flash already and didnt work
Now i've installed hal and tried it - no luck

Then I redid the pipelight install again and enabled flash with pipe light

Now firefox works for this website (tsn.ca/tv). But nothing in chrome after the advertisement.

You can see which version of flash is working by right clicking the video. Besides reporting flash 18 (as oppose to 11.2) Pipelight flash's menus are kind of ugly like all wine applications'.

No it won't work in Chrome because pipelight is a NAAPI plugin. While Chrome has the latest pepperflash the Linux version doesn't work for some drmed streams. It is intentionally crippled for some software political reasons. There is a ways to make it work in Chromium by extracting pepperflash from Chrome on a Chromebook image instead but it is not easy to do and flash you get that way doesn't update.

---

### Post by anbu-s on 2015-06-24
> **monkeybrain20122 said:**
> You can see which version of flash is working by right clicking the video. Besides reporting flash 18 (as oppose to 11.2) Pipelight flash's menus are kind of ugly like all wine applications'.

No it won't work in Chrome because pipelight is a NAAPI plugin. While Chrome has the latest pepperflash the Linux version doesn't work for some drmed streams. It is intentionally crippled for some software political reasons. I heard there are ways to make it work in Chromium by extracting pepperflash from Chrome on a Chromebook image instead, but it relies on a wrapper (freshplayer plugin) and is not easy to do

OK. How does Google chrome plays the same video on windows and OSX? I guess its google intentionally crippled this on linux

Thanks for your help

---

### Post by monkeybrain20122 on 2015-06-24
> **anbu-s said:**
> OK. How does Google chrome plays the same video on windows and OSX? I guess its google intentionally crippled this on linux

Thanks for your help

Yeah pepperflash on Linux doesn't play certain drmed streams, but not because of any limitation of the platform because Chrome in Chromebooks does work.  As I said if you can make it works on Chromium by extracting pepperflash from a Chrome book image instead of using the non free package from the repo. I have done it but it was kind of tedious to get it out of the Chrome book image (but I have no access to drmed video sites to test, just tested with adobe's demo and it worked) Maybe eventually someone will put up a ppa for it then all outdated, non drme capable flash issues will be solved. :) (it can be use in Firefox with freshplayer plugin, and for Chromium/Opera I don't think it even needs that)

---

