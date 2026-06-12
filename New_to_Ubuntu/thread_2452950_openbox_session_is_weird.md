---
title: "openbox session is weird"
date: 2020-10-30
forum: New to Ubuntu
---

### Post by wugubee on 2020-10-30
Im new to linux desktop, just recently move from windows 7 to latest lubuntu, openbox session is weird, it looks buggy and dont goto blank screen, new people will think something goes wrong, although/actually is not, and expected?

---

### Post by wildmanne39 on 2020-10-31
Moved to own thread.

---

### Post by ActionParsnip on 2020-10-31
Lubuntu should load the LXPanel or are you logging in to the Openbox session? Openox is just a blank desktop. It is very minimal. The Lubuntu session will load LXDE fully. Is this the issue?

---

### Post by wugubee on 2020-10-31
is not blank desktop, it does not clear the default background with that white bird, so people will think its hang, but i can right click, but every right click, the screen (the right click menu) does not clear, but still show previous graphical right click menu, and it goes on, if u click other area, it goes on and on,

---

### Post by ajgreeny on 2020-10-31
You can make an openbox session look as you want it to but it is up to you to add any utilities you want yourself; openbox by default gives you an empty  desktop with no wallpaper image or panel.

I run Debian 10 on an old netbook with LXDE installed but use only the openbox session but with my own wallpaper and the lxpanel added using obconf settings.

---

### Post by guiverc on 2020-10-31
It may help if your more specific with your issue.

What do you consider the *latest *release of Lubuntu.

To me that means Lubuntu 20.10, or the 2020-October release, but I know to many people (about half the people asking questions), it means Lubuntu 20.04 LTS or the earlier 2020-April release (as it's the latest LTS, ignoring any non-LTS release).  Latest isn't helpful unless we know what you mean.

Are you logging into a Lubuntu, LXQt or Openbox session?  A clean install has those three options which vary the session you're presented with.

**Lubuntu** - offers all Lubuntu customizations; the best experience.
[B]
LXQt desktop[/B] -  more upstream experience, less Lubuntu configuration options are offered, thus it won't match the Lubuntu manual perfectly.
[B]
[Openbox]("http://openbox.org/wiki/Main_Page")[/B] - highly configurable window manager, very basic, considered stable & bug-free (*by upstream*), but it's minimalistic and what many users consider lacking features are deemed to be user issues as are usually fixed by customization openbox allows but isn't done by default unless the user sets it up.

It sounds to me like you're in Openbox, which isn't a desktop. It's not a hang, just an empty session needing you to configure it (openbox is installed, but is **not**pre-configured by Lubuntu except the features we use in our Lubuntu session). If you login with the Openbox option, it's almost a blank slate as the few configuration options there are designed for use with LXQt which won't be running in Openbox session.

If you're used to DEsktops and not the leaner window managers, yes it can seem weird & lacking. It's more a building-block that you configure into what you want or need, where as desktops come pre-configured.

FYI:  There are many older WMs that can be fun to explore. They are also very light.

---

### Post by scorp123 on 2020-11-02
> **wugubee said:**
>  openbox session is weird

Why are you, a beginner, even trying OpenBox? OpenBox might look "empty" and "buggy" maybe because you didn't configure it properly. Yes, you need to do a little something with it before it looks pleasant to you. The authors can't know what you like or don't like so the defaults are absolutely basic and minimal. Where OpenBox shines is the lack of clutter and the absence of excessive animations, and the extreme speed you get even when accessing it remotely over a mobile phone connection.

A nicely configured OpenBox desktop can look like this:

[https://paste.pics/462380596019ad5e97c0d4aa08cee354]("https://paste.pics/462380596019ad5e97c0d4aa08cee354")

(yes, that's my actual desktop that I use when working remotely)

---

### Post by TheFu on 2020-11-02
I used openbox for a number of years because I found all the DEs bloated. They got in my way. I really disliked the popup notifications.

There is an XML config file under ~/.config/openbox/ which can be used to customize stuff.  For the most part, my customization was setting up accel keys to launch specific programs with specific options. Very little need for a mouse, since I'd place each program launched on a specific workspace with specific geometry so each window was placed where I liked it every time.  
Also use the focus-follows-mouse for active window selection, but didn't use bring-to-top. Sometimes it is convenient to have the active window behind other windows.

But openbox is kinda limiting and I wanted more control, most customization ... it is was back to fvwm for me. In the mid-1990s, I'd used fvwm daily for about 5 yrs on my Alpha workstation.  [https://www.box-look.org/browse/cat/143/order/latest/](https://www.box-look.org/browse/cat/143/order/latest/) shows some example desktops.  Pretty much everything can be customized under fvwm, but all the settings are made via text config files. There isn't any GUI config editor.

---

### Post by rsteinmetz70112 on 2020-11-04
If I were new to Linux I wouldn't use openbox at least until I get more comfortable with it. I definitely wouldn't use if for other users.

---

