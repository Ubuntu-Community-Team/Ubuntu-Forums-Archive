---
title: "Xubuntu Precise Pangolin doesn't have as many theme choices!"
date: 2012-06-09
forum: New to Ubuntu
---

### Post by hamstermoon on 2012-06-09
Help!

I am setting up my replacement MSI 230 (the old one has motherboard issues) and putting Xubuntu Precise Pangolin on to it. I have noticed that although I can still set my style to Thin Ice in apperances, I can't find Agua as a theme in the Window Manager. There seem to be a lot less themes in there than there have been before. I am upset about that!

 I am going for a sort of mac-like appearance (I have Docky as well instead of my bottom panel) as I find it easier to use, and would like the gem-like buttons to manage my windows.

Any suggestions??

---

### Post by CrocoDuck on 2012-06-09
Hi. When I tweak xfce themes and other DE stuff I'm usually download cool things from here [http://xfce-look.org/?PHPSESSID=e462b1b14ca2fdcdf114bfa530c7d847](http://xfce-look.org/?PHPSESSID=e462b1b14ca2fdcdf114bfa530c7d847) and act like exposed here: [http://wiki.xfce.org/howto/install_new_themes](http://wiki.xfce.org/howto/install_new_themes) . You can also find instructions for installing the stuff you need at their download page. Have a look at these pages, they looks suit your needings: [http://xfce-look.org/content/show.php/MacOS-X+Aqua+Theme?content=13548](http://xfce-look.org/content/show.php/MacOS-X+Aqua+Theme?content=13548) ,  [http://xfce-look.org/content/show.php/meopard?content=147309](http://xfce-look.org/content/show.php/meopard?content=147309) , [http://xfce-look.org/content/show.php/Arbeit+Aurora+Xfce?content=127363](http://xfce-look.org/content/show.php/Arbeit+Aurora+Xfce?content=127363).

---

### Post by hamstermoon on 2012-06-10
I am going to have to have a step by step explanation of how to install once I have downloaded the files. I can't seem to find where to put them (or even how to put them there_.

---

### Post by Peripheral Visionary on 2012-06-10
I added some themes and fonts just using Synaptic! 

One of the best things about Xubu is that it's one of the *few* remaining full-service desktop distros that [COLOR=DarkOrange]**still fits on a CD**[/COLOR] (instead of needed a DVD). One of the reasons for that is because they don't fill it up with a bunch of extra themes and screensavers and other stuff that is so easily added after installation.

---

### Post by hamstermoon on 2012-06-10
I did that but it still doesn't allow me to change the buttons on the window edge. I am still stuck with that! All I am asking for is something called agua, or something similar to that.

---

### Post by Dennis N on 2012-06-10
> **hamstermoon said:**
> ... All I am asking for is something called agua, or something similar to that.

Assuming this is what you are talking about, you can download it and see if it still works:

[http://xfce-look.org/content/show.php/MacOS-X+Aqua+Theme?content=13548](http://xfce-look.org/content/show.php/MacOS-X+Aqua+Theme?content=13548)

It dates from 2004.

---

### Post by black veils on 2012-06-10
this is my collection of window manager themes and one extra general style:

[https://skydrive.live.com/redir?resid=5B4D1DDB5344FCB0!127&authkey=!AAJT_2DvBrbGgJY]("https://skydrive.live.com/redir?resid=5B4D1DDB5344FCB0%21127&authkey=%21AAJT_2DvBrbGgJY")

(i added to their titles, so it wont overwrite any you already have)


you may also be interested in some panel themes:

[http://gnome-look.org/content/show.php/Panel+Background+pack+7?content=151112](http://gnome-look.org/content/show.php/Panel+Background+pack+7?content=151112)

bottom panel only:
[http://xfce-look.org/content/show.php/Bottom+Panel+Backgrounds+Pack?content=150311](http://xfce-look.org/content/show.php/Bottom+Panel+Backgrounds+Pack?content=150311)

---

### Post by Toz on 2012-06-10
> **hamstermoon said:**
> I did that but it still doesn't allow me to change the buttons on the window edge. I am still stuck with that! All I am asking for is something called agua, or something similar to that.

The agua and agualemon themes are part of the xfwm4-themes package which doesn't appear to be installed by default in 12.04 (can't remember if it was default in previous versions). Look for it the software centre or from a terminal window prompt:
```
sudo apt-get install xfwm4-themes
```

---

### Post by hamstermoon on 2012-06-12
Oh, thank you! That worked. I now have it looking the way I want it!

---

