---
title: "How do I stop my screen dimming on battery"
date: 2012-10-11
forum: New to Ubuntu
---

### Post by ElaineJoyce on 2012-10-11
Hello,

I am really new to Ubuntu and am running 12.04 on a Dell Inspiron 1300 laptop.

As the title says I would like to stop this screen dimming, I use my laptop mostly on battery power

I have read lots of posts including this one....

[http://ubuntuforums.org/showthread.php?t=1967718&highlight=stop+screen+dim](http://ubuntuforums.org/showthread.php?t=1967718&highlight=stop+screen+dim)

some of the suggestions I just have no idea how to do !


Changing the settings has no effect.

Nor does most of the ideas I read on Google.

I even re=installed using a different CD to the first on but no luck


What's a girl supposed to do ??


Thanks

Ellie

---

### Post by ElaineJoyce on 2012-10-11
Hello,

Sorry I put the wrong URL for the post I meant to show you but I hope you know what I mean.

Ellie

---

### Post by newb85 on 2012-10-11
Welcome to Ubuntu and the forums!

Caffeine a great little applet you can use to prevent your screen from dimming or turning off.  It's not available in the main repositories, but it is available in a personal package archive (PPA), so the easiest way to install is to add that PPA to your sources list and then install the app.

```
sudo add-apt-repository ppa:caffeine-developers/ppa
sudo apt-get update
sudo apt-get install caffeine
```

Once it's installed, you can open it the first time through the Dash.  It will look like a little coffee cup in your system tray (upper-right part of your screen).

---

### Post by ElaineJoyce on 2012-10-12
Hello,

Thank you very much for the quick response.

I did as you said and installed Caffeine, I just don't see quite how you use it to stop the  scree dimming on battery.

Is there somewhere I can go to see a "Help" file ??

Thanks again 


Ellie

---

### Post by newb85 on 2012-10-12
If you click the icon and select "Disable Screensaver", it should prevent the screen from dimming.

---

### Post by mips on 2012-10-12
On some laptops (My old one from 1995) it's simply not possible, seems like a hardware function which not even the fn keys can override.

---

### Post by ElaineJoyce on 2012-10-13
Hello,

Thanks guys for the info but so far no luck, I did as you said with caffeine but the screen still dims.#

The laptop is several years old, would that be the problem



Ellie

---

### Post by salmanahmedtariq on 2012-10-14
ellie this will help u
[http://xubuntugeek.blogspot.com/2012_01_01_archive.html](http://xubuntugeek.blogspot.com/2012_01_01_archive.html)

---

### Post by Hadaka on 2012-10-14
Hi, On the Inspiron 1300 you can set the screeen brightness while on
battery in bios settings.

power down your laptop
power it back up
while its booting up press the F2 key
this puts you into bios setup
arrow down to VIDEO
press enter
arrow to BRIGHTNESS
press enter....this is for the battery brightness setting..default is 3
on the right hand side of the screen you can increase the brightness value
press enter
press ESC
choose SAVE/EXIT
thats all there is to it.

---

### Post by ElaineJoyce on 2012-10-15
Hello,

Hadaka, what a Saviour you turned out to be. You've improved my life no end.

Many. many thanks


Ellie

---

### Post by ElaineJoyce on 2012-10-15
Hello,

I would like to mark this as solved but can't make "Thread Tools" work but again thanks


Ellie

---

