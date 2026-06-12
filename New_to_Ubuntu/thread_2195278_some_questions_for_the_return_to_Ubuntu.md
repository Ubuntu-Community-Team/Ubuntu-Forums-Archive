---
title: "some questions for the return to Ubuntu"
date: 2013-12-23
forum: New to Ubuntu
---

### Post by g-vincentip on 2013-12-23
Hi all,

After a long while I decided to go back to Ubuntu (last time I checked gnome was were all the cool kids were hanging around - ok, maybe it has not been *such *a long time ago... anyway I digress)
so getting back up and running,...

First of all, I noticed my calendar says "Montag 23 December" and my *back *and *continue* buttons are labeled as zuruck and weiter (while the rest in in English).
Does anyone know where I can change this so my system is fully English (my guess is when I installed my system, I said I am based in Germany)

second question, how is this new funky "dock" called? it's quite hard to google something if you don't know how it is called :)
+ is there an (easy) way to thinker with this?
 

Thanks!

---

### Post by craig10x on 2013-12-23
The "funky dock" is called UNITY....it's actually called the Unity Launcher (but as you said, it is a dock...lol) and the search button on the top is called the DASH... :D

---

### Post by monkeybrain20122 on 2013-12-23
Hi

[http://askubuntu.com/questions/132347/gnome-classic-language-turned-into-chinese-how-do-i-change-it-back-to-english](http://askubuntu.com/questions/132347/gnome-classic-language-turned-into-chinese-how-do-i-change-it-back-to-english)

Hope this helps.

---

### Post by g-vincentip on 2013-12-23
> **craig10x said:**
> The "funky dock" is called UNITY....it's actually called the Unity Launcher (but as you said, it is a dock...lol) and the search button on the top is called the DASH... :D
Thanks, that'll make my life 20% easier



> **monkeybrain20122 said:**
> Hi

[http://askubuntu.com/questions/132347/gnome-classic-language-turned-into-chinese-how-do-i-change-it-back-to-english](http://askubuntu.com/questions/132347/gnome-classic-language-turned-into-chinese-how-do-i-change-it-back-to-english)

Hope this helps.
Unfortunately if I go to user accounts, only english is displayed

---

### Post by ibjsb4 on 2013-12-23
[The Unity Desktop]("http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=unity&sa=Search&cof=FORID:9")

 If you prefer the old desktop look, it can be installed to your current install.  [In terminal:]("https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal")

 ```
sudo apt-get install gnome-panel
```

And choose your desktop at login by clicking on the login-window-icon.

---

### Post by g-vincentip on 2013-12-23
> **ibjsb4 said:**
> [The Unity Desktop]("http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=unity&sa=Search&cof=FORID:9")

 If you prefer the old desktop look, it can be installed to your current install.  [In terminal:]("https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal")

 ```
sudo apt-get install gnome-panel
```

And choose your desktop at login by clicking on the login-window-icon.

Thanks but I guess I will give Unity a chance.
The only thing I am trying to figure out is how to customize it a bit (eg the icons in the top right corner can't be moved as far as I can figure out?)

and well also the language issue which is bugging the crap out of me :-S

---

### Post by craig10x on 2013-12-23
Well, there are some basic customizations you can make on unity in the "system settings" under appearance....you can shrink the size of the icons (pixel size) on my 17" desktop/laptop i shrink them to 38 pixels cause i think it looks nicer that way...you can add workspaces...and you can auto hide the dock of course and set the sensitivity of the "auto hide" when you push your mouse over there...you can delete icons (right click on it) and add new ones (after opening a program, when the icon appears on there just right click and lock it in)...you can move the icons around on the unity dock using "drag and drop"....

And you can install Unity Tweaks program from software center for some other customizations if you wish...you can't move the dock though...
I don't think you can move the icons around on the top panel, though as far as i know...

---

### Post by monkeybrain20122 on 2013-12-23
> **craig10x said:**
> Well, there are some basic customizations you can make on unity in the "system settings" under appearance....you can shrink the size of the icons (pixel size) on my 17" desktop/laptop i shrink them to 38 pixels cause i think it looks nicer that way...you can add workspaces...and you can auto hide the dock of course and set the sensitivity of the "auto hide" when you push your mouse over there...you can delete icons (right click on it) and add new ones (after opening a program, when the icon appears on there just right click and lock it in)...you can move the icons around on the unity dock using "drag and drop"....
.

There are more customization options in ccsm (more in terms of functionalities than look) The default single desktop is pretty dumb IMO.

---

### Post by grahammechanical on 2013-12-23
Has anybody given advice on the language issue?

Go to System Settings. You will find it by clicking the power/cog icon. And then load Language Support. Oh, by the way, if you are using Ubuntu 13.10, and you want something like the old look then I suggest that you install Gnome Session Flashback through the Software Centre. And then you can at login select either Ubuntu; Gnome Flashback (with Compiz); Gnome Flashback (with Metacity).

Regards.

---

### Post by vasple on 2013-12-23
I had to change back my system from half-English/half-Greek to fully English. I did it by simply going into settings-->Language Support and change both Language format to English. Log-out and log back in and you're done.

If it doesn't work make sure you have the correct language pack installed and regenerate the locales.

**sudo apt-get install --reinstall language-pack-en-base **
**sudo dpkg-reconfigure locales**

or in some cases: **sudo apt-get install --reinstall locales** instead of the second command.

---

### Post by g-vincentip on 2013-12-24
Great the language thing was solved (although I had to change to South African English to have a decent formatting :-S )

Anyway, talking about Desktop Environements... what by *whatever you believe in *are they smoking? Anyone any suggestions for a post Gnome 2 DE?
- before anyone mentions it, Gnome Flashback, close but no cigar... what happened to the possibility to move things around ?

---

