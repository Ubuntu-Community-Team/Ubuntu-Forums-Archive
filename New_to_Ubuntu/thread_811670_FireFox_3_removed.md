---
title: "FireFox 3 removed?"
date: 2008-05-29
forum: New to Ubuntu
---

### Post by noland on 2008-05-29
Hi there... am i the only one? synaptic told me there was a dist-upgrade ready, uuuuu the new firefox!!! but when i ran it... no firefox... then i re-install it and it re-installs the beta 5...  is that normal or what did i do wrong?


my-box@my-box-laptop:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be REMOVED:
  firefox firefox-3.0 ubuntu-desktop yelp
The following packages will be upgraded:
  xulrunner-1.9
1 upgraded, 0 newly installed, 4 to remove and 0 not upgraded.
Need to get 7741kB of archives.
After this operation, 7586kB disk space will be freed.
Do you want to continue [Y/n]? n
Abort.

Thanks in advance!

Phil

---

### Post by Soundtrack Black on 2008-05-29
same here

---

### Post by noland on 2008-05-29
oh well at least im not the only one... ill look more for some threads, there must be something on that...

---

### Post by Dragonslicer on 2008-05-29
I noticed it this morning too. Looks like they updated xulrunner to 1.9rc1, but didn't update the firefox-3.0 package yet (firefox-3.0 b5 naturally requires xulrunner 1.9b5). Hopefully it will be fixed sometime today.

---

### Post by noland on 2008-05-29
all right, broken dependencies i guess... BTW there is a similar thread with the title  '[ubuntu]   Partial Upgrade Request'  and people have the same problem thread... 

might as well follow both or cancel this one...

---

### Post by Riffer on 2008-05-29
Just had an update and it removed FF3.  I know theres been a lot of trouble with FF3 but is it so much that they needed to remove it?

---

### Post by PmDematagoda on 2008-05-29
> **Riffer said:**
> Just had an update and it removed FF3.  I know theres been a lot of trouble with FF3 but is it so much that they needed to remove it?

There is no such thing as removing it, Firefox3 is still being built which is why there are dependency errors. But Firefox3 has now reached the Sri Lankan server, so just update the sources list, that should allow you to reinstall/update Firefox3 properly.

---

### Post by Joeb454 on 2008-05-29
Firefox 3 RC1 is in the repo's now?

If so the Main Server hasn't got it yet :(

---

### Post by PmDematagoda on 2008-05-29
> **Joeb454 said:**
> Firefox 3 RC1 is in the repo's now?

If so the Main Server hasn't got it yet :(

It's reached the Sri Lankan server, so it must be on it's way.

---

### Post by Joeb454 on 2008-05-29
*Considers using sri-lankan server until then* ;)

---

### Post by Inxsible on 2008-05-29
> **Joeb454 said:**
> *Considers using sri-lankan server until then* ;)

You may wanna hold off until they get the dependency issues resolved :)

---

### Post by PmDematagoda on 2008-05-29
> **Inxsible said:**
> You may wanna hold off until they get the dependency issues resolved :)

Since the dependency issues are due to the late Firefox3 package, you should be able to resolve them simply by using a server which has the updated package, or by being patient:).

---

### Post by Joeb454 on 2008-05-29
I'll be patient - Beta 5 works perfectly fine for me, so I'm happy to wait...I just like updates ;)

---

### Post by Inxsible on 2008-05-29
> **PmDematagoda said:**
> Since the dependency issues are due to the late Firefox3 package, you should be able to resolve them simply by using a server which has the updated package, or by being patient:).

I think I'll be patient. Patience after all is a virtue ;-)  BTW....My work computer(XP) updated to FF3 RC1 from b5 and it borked my speed dial add on(I use that add on the most apart from noscript and adblock). It still works, but my shortcuts for speed dial dont work. And I have tried resetting them and even re-installing Speed Dial. Still no go.  Will I see the same with the Linux version of FF3 RC1 ? I sure hope not !!

---

### Post by Joeb454 on 2008-05-29
You could try removing the plugin first?

Or check out [http://portableapps.com](http://portableapps.com) and get RC1 from there - it should install just fine alongside b5 and use separate profiles (from what I've read anyway :))

---

### Post by Inxsible on 2008-05-29
> **Joeb454 said:**
> You could try removing the plugin first?



I did try removing -- when I said re-installing, i meant i removed it and then restarted FF and then re-installed. Still no go :(  

Anyway..i think it will get fixed in the next update.

---

### Post by JohanSwe on 2008-05-29
After the upgrade was finished and Firefox 3 was gone I updated the upgrading window, and more updates were shown. I upgraded everything and then installed the package *firefox* in synaptic without problem and I now got Firefox 3 back..

---

### Post by Joeb454 on 2008-05-29
I should note that you (currently) need the "hardy-proposed" repo enabled to get Firefox 3 RC1 - my guess is that they are going to test it for a day or 2 before pushing it through properly

---

### Post by philinux on 2008-05-29
Dang forgot to tick proposed thought I had.

Just got 69 updates.

Had hardy going since alpha 3

Testing..Testing..Testing...:wink:

---

### Post by peakshysteria on 2008-05-29
Checked Hardy-proposed. Got 128 updates all in all. Now running:

Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9) Gecko/2008052909 Firefox/3.0 :)

Greasemonkey disabled :(
Last.Fm code disabled :(

Edit:
Seems faster. Uses less memory.

---

### Post by Joeb454 on 2008-05-29
For most users I'd recommend waiting that little while longer, some of the proposed updates may not be ready for general release.

Though I guess the repo name should sort of suggest it ;)

---

### Post by philinux on 2008-05-29
Yep gvfs keeps crashing. They must be getting inundated with crash reports.

---

### Post by peakshysteria on 2008-05-29
I agree. Looks could be deceiving. But then again what's the fun in waiting. FF runs smooth in my end. And no apparent signs of other bugs at all. I guess each one must decide for them self if it's worth it.

My Firefox Information

Last updated: Thu, 29 May 2008 22:20:38 GMT
User Agent: Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9) Gecko/2008052909 Firefox/3.0

**Extensions** (enabled: 10, disabled: 3; total: 13)
[list]
[*][Flashblock](http://flashblock.mozdev.org/) 1.5.6 [disabled]
[*][Forecastfox](http://forecastfox.mozdev.org/) 0.9.6 
[*][Greasemonkey](http://www.greasespot.net/) 0.7.20080121.0 [disabled]
[*][InfoLister](http://mozilla.doslash.org/infolister) 0.10 
[*][last.fmCode](http://mll02.free.fr/?p=42) 0.7 [disabled]
[*][Linkification](http://yellow5.us/firefox/linkification/) 1.3.3 
[*][Norsk Bokmål ordliste]() 2.0.10.0 
[*][Norsk Nynorsk ordliste]() 2.0.10.0 
[*][Tab Mix Plus](http://tmp.garyr.net) 0.3.6.1.080416 
[*][Text Link](http://piro.sakura.ne.jp/xul/_textlink.html.en) 2.0.2008052801 
[*][Ubuntu Firefox Modifications]() 0.5 
[*][Update Channel Selector](http://www.oxymoronical.com/web/firefox/updatechannel) 1.0.3 
[*][User Agent Switcher](http://chrispederick.com/work/user-agent-switcher/) 0.6.11 
[/list]

**Themes** (1)
[list]
[*]Default [selected]
[/list]

**Plugins**
[list]
[*]Default Plugin
[*]Demo Print Plugin for unix/linux
[*]DivX® Web Player
[*]GCJ Web Browser Plugin (using IcedTea) 1.0
[*]Helix DNA Plugin: RealPlayer G2 Plug-In Compatible (compatible; Totem)
[*]iTunes Application Detector
[*]QuickTime Plug-in 7.2.0
[*]Shockwave Flash
[*]Totem Web Browser Plugin 2.22.1
[*]VLC Multimedia Plugin (compatible Totem 2.22.1)
[*]Windows Media Player Plug-in 10 (compatible; Totem)
[/list]


Anyway, my tip for the point of the thread is in my post above...

---

### Post by Joeb454 on 2008-05-29
I have to agree with you - Firefox 3 may as well be a final build for me, works great, always has done (some may say I've been lucky in that respect)

---

### Post by markbuntu on 2008-05-29
Firefox 3b5 was nothing but a horror show for me. So much so that I switched to Opera.
I've been using rc1 for a few days now and it is a huge huge improvement.

---

### Post by philinux on 2008-05-29
> **markbuntu said:**
> Firefox 3b5 was nothing but a horror show for me. So much so that I switched to Opera.
I've been using rc1 for a few days now and it is a huge huge improvement.

In what way. I've had zero problems. Must be hardware related.

---

### Post by peakshysteria on 2008-05-29
> **markbuntu said:**
> Firefox 3b5 was nothing but a horror show for me. So much so that I switched to Opera.
I've been using rc1 for a few days now and it is a huge huge improvement.

Switched to Opera and using FF RC1? Or doing fine and using only FF RC1?

---

### Post by Primefalcon on 2008-05-29
> **philinux said:**
> In what way. I've had zero problems. Must be hardware related.

Have to agree I've had zero problems with beta 5, so personally I'm gonna wait. It'll prob only be a matter of days if that much anyhow

---

### Post by eric_m_allen on 2008-05-30
I'm using standard sources, and it wouldn't let me install FF3 at all. This is troubling-it should be set up to remove 3 and install 2.
I went into Synaptic and FF2 seems to run OK. (FF3 ran fine too) Both would run dead slow when I had a lot of tabs open, a problem I never had with the Windows version...
I'll wait until this gets into the main source stream. Let the bleeding edge guys feel the pain...That's why the removal without a downgrade troubles me. C'mon guys-I'm a developer, and I'd get spanked by my users for doing that...

---

### Post by peakshysteria on 2008-05-30
dead slow indicates an addon issue/incompatibility, flash trouble or graphics driver issue. Check my first post if you want to solve it and run cutting edge :)

---

### Post by gn2 on 2008-05-30
Foxmarks working in FF3 yet?

---

### Post by Lowcountry on 2008-05-30
> **gn2 said:**
> Foxmarks working in FF3 yet?

Yep:)

---

### Post by CameO73 on 2008-05-30
> **philinux said:**
> In what way. I've had zero problems. Must be hardware related.
Ehrm. No. FF3b5 in combination with Flash 9 and libflashsupport (to prevent Flash from having exclusive audio) will crash FF3 quite frequently (see [bugreport](https://bugs.launchpad.net/bugs/192888)). The good news is that this seems to be solved with FF3RC1 and Flash 10 (currently beta). But there are definitely problems with FF3b5 ... but that's why it was a beta in the first place. 

In retrospect, I still think putting FF3b5 in this LTS release is a good thing. This way Ubuntu has to support FF3 the next couple of years, instead of FF2. The only problem is that not everyone realised it was a beta (and wrongfully blaming FF3 for poor stability). Hopefully this will soon be over, now that RC1 is on its way!

---

### Post by CameO73 on 2008-05-30
> **gn2 said:**
> Foxmarks working in FF3 yet?
Yes! But you have to get it as a beta (from [http://beta.foxmarks.com/](http://beta.foxmarks.com/)). But as far as I can tell it's pretty stable (have not lost any bookmarks yet ;))__

---

### Post by gn2 on 2008-05-30
> **CameO73 said:**
> Yes! But you have to get it as a beta (from [http://beta.foxmarks.com/](http://beta.foxmarks.com/)). But as far as I can tell it's pretty stable (have not lost any bookmarks yet ;))__

Yep, Foxmarks is working fine with FF3 in openSUSE 11 RC1 which I am currently expirementing with.

---

### Post by Bubba64 on 2008-05-30
I downloaded the overwrite of rc1 a week ago from launchpad, runs even faster than the Hardy version, but I have older computers with no need for  custom drivers. If any body wants the launch pad link all you have to do is post. I am not sure if overwriting with the launchpad download will bork future updates in Ubuntu though.

---

