---
title: "Chromium Questions"
date: 2011-11-01
forum: New to Ubuntu
---

### Post by d4m1r on 2011-11-01
Hi, I didn't want to install another browser other than Firefox v7.0.1 because it does a good job but it isn't compatible with 2-3 sites, even in my Windows 7 partition (opening PDFs from a javascript).

Anyway, I use IE to access them in Windows 7 but that is obviously not an option in Ubuntu...I wasn't sure if Chromium would do it but I tried it because it's the 2nd most popular browser and it does work :P

1)I heard Chromium isn't the same as Chrome? Is the Ubuntu version not developed by Google?

2)Does it use the same/similar engine as IE?

3)How do I get it to delete EVERYTHING when I close it? Search results, cookies, passwords, history, etc

[IMG]http://i.imgur.com/5JggN.png[/IMG]

^That is what I have set in the settings, but if I close Chromium and re-open it, I can go to history and still see sites visited earlier....

Keep in mind, the sites I visit require cookies to be enabled to login.

---

### Post by nickleboyblue on 2011-11-01
Chromium, technically, is not Chrome, but it is so similar (hence the nearly identical branding and ui) that the differences don't amount to all that much.  Chromium and Chrome are both webkit based, while firefox is not.

Many browsers allow you to do what is called "private" browsing; this would allow you to avoid cookie buildup and heaps of cache.  Otherwise, I don't know how to get chromium to delete everything every time it turns off.  Best practice?  Don't click on "remember me" options in websites.

---

### Post by d4m1r on 2011-11-01
> **nickleboyblue said:**
> Chromium, technically, is not Chrome, but it is so similar (hence the nearly identical branding and ui) that the differences don't amount to all that much.  Chromium and Chrome are both webkit based, while firefox is not.

Many browsers allow you to do what is called "private" browsing; this would allow you to avoid cookie buildup and heaps of cache.  Otherwise, I don't know how to get chromium to delete everything every time it turns off.  Best practice?  Don't click on "remember me" options in websites.

Is Chromium developed by Google or a linux group?

Also, I specified to never save passwords, and it doesn't remember them, and it **does** delete cookies but it does **not** erase the history upon logout ](*,)

---

### Post by dniMretsaM on 2011-11-01
(1) [Chromium]("http://www.chromium.org/") is not developed by Google. It is a separate project which Google Chrome is based off of.

(2) I really have no idea. Chromium/Chrome uses WebKit (as does Apple's Safari and a bunch of other browsers. FF uses Gecko.), but I don't know what IE uses. Probably something proprietary.

(3) One of the many things Chromium/Chrome lacks is good private browsing, but I /think/ there is a way to delete history when the session ends. Look in the browser's history settings, not the cookie settings.[URL="http://www.chromium.org/"]
[/URL]

---

### Post by d4m1r on 2011-11-01
UPDATE: Chromium has a built in "incognito" mode that is similar to Firefox's Private Session Browser. Anyway, it is able to accept cookies, etc, but specifically erases all history when the browser is closed.

I have figured out a way to get it to launch in incognito mode automatically off my Unity launcher and it does erase everything 8-)

Step #1:

```
sudo gedit /usr/share/applications/chromium-browser.desktop
```Step #2

```
search for exec and replace the line with: Exec=/usr/bin/chromium-browser --incognito %U
```Step #3

Not sure if necessary, but minimize everything, hover over the Unity launcher and press F5.

Step #4

Launch Chromium and check if there is a cloacked guy in the top right corner (if there is, you're done).


Not sure if it will work with other distro's/gnome/etc but works for me on 11.04 Natty (32 bit w/Unity).

---

### Post by dniMretsaM on 2011-11-01
Note that all add-ons are disabled in Incognito mode.

---

### Post by d4m1r on 2011-11-01
> **dniMretsaM said:**
> Note that all add-ons are disabled in Incognito mode.

Didn't know that...I don't have any installed anyway, but why would they do that? :neutral:

---

### Post by beew on 2011-11-01
What are the sites that you cannot access with Firefox? Did you try the user agent switcher addon?
[https://addons.mozilla.org/en-US/firefox/addon/user-agent-switcher/](https://addons.mozilla.org/en-US/firefox/addon/user-agent-switcher/)

---

### Post by dniMretsaM on 2011-11-01
> **d4m1r said:**
> Didn't know that...I don't have any installed anyway, but why would they do that? :neutral:

Who knows. One more reason I use Firefox.

---

### Post by d4m1r on 2011-11-01
> **dniMretsaM said:**
> Who knows. One more reason I use Firefox.

Same, but in Chromiums defense:

[COLOR=#000000][FONT=Arial]"Because Chromium does not control how extensions handle your personal data, all extensions have been disabled for incognito windows. You can re-enable them individually in the extensions manager."[/FONT][/COLOR]


So you can re-enable them manually...

@beew, no I haven't tried that but I tried the more popular IE Tab plugin (loads the IE engine in a tab) but it said it was not compatible with linux (maybe needs access to the IE library locally?) and wouldn't install...

---

### Post by Jaybyrrd on 2011-11-01
Ok so the only substantial difference, as no one has brought this up, is that Chromium is generally ahead of the curve as it IS the original project, and by using Chromium instead of Google Chrome you are not forced to agree to Google's privacy policies, which in a nutshell and in prettier words say that can look at anything you submit or do whilst using Chrome, can record that data, and even sell it if they so wish, however they do try state that this they try to limit this to legal demands for information. However when you reserve the right to do more then just that, can one truly trust that is all that happens? 

Hope that sheds extra light. :)

---

### Post by vasa1 on 2011-11-02
> **d4m1r said:**
> ...
@beew, no I haven't tried that but I tried the more popular IE Tab plugin (loads the IE engine in a tab) but it said it was not compatible with linux (maybe needs access to the IE library locally?) and wouldn't install...

Yes, whether for Firefox or Chrome, IE Tab needs access to a functional Internet Explorer (the Trident engine)! Fortunately, IE-only sites are decreasing. And if I come across one, I complain loudly. That helps ... sometimes.

---

### Post by mijdrawoh on 2011-11-02
Check out [http://scroogle.org/](http://scroogle.org/)

---

### Post by I2k4 on 2011-11-02
I gave up on Chromium (default install in Lubuntu) when it didn't work on several sites I use, e.g. GrooveShark.  I also had trouble adding Flash for it.  

Chrome has always worked, and has the added advantage of including Flash in the installation.  I have had good experiences with the beta versions of Chrome - not so good with the "unstable" developer builds.  An excellent configurable cleanup tool for it is the "Click & Clean" extension.

---

### Post by matt_symes on 2011-11-02
Hi

> I gave up on Chromium (default install in Lubuntu) when it didn't work on several sites I use, e.g. GrooveShark.

That's odd. It works on my version in Lucid.

```
matthew@matthew-laptop:~$ chromium-browser --version
Chromium 15.0.874.106 Ubuntu 10.04
matthew@matthew-laptop:~$ 
```

Why does it not work on your PC ? What is failing ?

Kind regards

---

### Post by kaldor on 2011-11-02
I should just clarify the engine and licensing.

Chromium is an entirely free and open source project. It uses various open source licenses. According to Wikipedia...

> BSD license, MIT License, LGPL, MS-PL and MPL/GPL/LGPL tri-licensed code, plus unlicensed files.

Nothing is proprietary in Chromium. Google Chrome is based on Chromium and adds some proprietary components on top. Chromium is the FOSS alternative to Chrome.

The rendering engine is Apple's Webkit. Webkit is a very successful open source project, and is arguably the most powerful engine right now. It's entirely standards compliant and it is used by Safari, Chromium, Epiphany (GNOME's browser), Rekonq (Kubuntu's browser) and others. It is in no way related to IE. Webkit is actually a fork of KDE's KHTML engine from Konqueror years ago.

TL;DR: Chromium is 100% open source and is unrelated to IE in any way. If anything, it's more like Safari.

---

### Post by d4m1r on 2011-11-02
^lol @ TL;DR, thanks for the info :D

I got it configured how I wanted and now understand browser engines more than I ever thought I would :lol:

---

### Post by I2k4 on 2011-11-03
> **matt_symes said:**
> Hi



That's odd. It works on my version in Lucid.

```
matthew@matthew-laptop:~$ chromium-browser --version
Chromium 15.0.874.106 Ubuntu 10.04
matthew@matthew-laptop:~$ 
```

Why does it not work on your PC ? What is failing ?

Kind regards

Hi, Don't know - I'm just an end-user dummy.  I found Chromium default browser for Lubuntu 10.10 about a year ago - had never seen it before - it didn't properly render or permit login to Grooveshark and failed on other sites I've forgotten.  There was also some problem with Flash, which may be related to the Grooveshark, etc. problem. I should say the same was true on two different PCs, an Acer netbook and a Dell laptop that I use on desktop.  

I installed Firefox, which I normally use for default, and used it to install the .deb for Chrome, which I normally use for Google's own services like YouTube and Docs, and haven't looked back.  No idea if Chromium is better now than it was then, but no real interest in it, either.  Chrome works out of the box, and installs Flash automatically.

---

