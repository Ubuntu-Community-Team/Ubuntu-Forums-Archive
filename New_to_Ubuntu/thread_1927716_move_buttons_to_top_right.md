---
title: "move buttons to top right"
date: 2012-02-18
forum: New to Ubuntu
---

### Post by benjie1 on 2012-02-18
HI  Newbie here. When any page pen like Firefox, Thunderbird, Libre Office, etc. the minimize, maximize, and close buttons are at the top left. Can I get them to be at the top right? Thanks.

Bob

---

### Post by Lisiano on 2012-02-18
Good news: Yes
Bad news: Almost yes.

The easiest way to move the buttons the right is to use [Ubuntu Tweak]("http://ubuntu-tweak.com/"), download it and install

Now go to Tweak -> Window Manager Settings -> Window Titlebar Button Layout -> Place

From there you can tick "Right" and the buttons will instantly move to the right.

Mess around with Ubuntu Tweak as it can do some nifty tweaks.

You might be wondering why I said "bad news" and "almost yes", well, when you maximize the window, the buttons will be on the left and as far as I know, there is no way to move them from there.

---

### Post by Paco009 on 2012-02-18
You have to edit the configuration file for your window manager. This is actually pretty easy. There's a good guide to help you out **_[HERE]("http://www.howtogeek.com/howto/13535/move-window-buttons-back-to-the-right-in-ubuntu-10.04/")_**. Hope that helps.

---

### Post by benjie1 on 2012-02-20
the box popped up but no run command was there so I can't follow the rest of the instructions  sorry any other ideas?

---

### Post by raja.genupula on 2012-02-20
Follow this , dont worry about the Dist version . it works fine . 

[http://www.howtogeek.com/howto/13535/move-window-buttons-back-to-the-right-in-ubuntu-10.04/](http://www.howtogeek.com/howto/13535/move-window-buttons-back-to-the-right-in-ubuntu-10.04/)

---

### Post by benjie1 on 2012-02-20
> **Lisiano said:**
> Good news: Yes
Bad news: Almost yes.

The easiest way to move the buttons the right is to use [Ubuntu Tweak]("http://ubuntu-tweak.com/"), download it and install

Now go to Tweak -> Window Manager Settings -> Window Titlebar Button Layout -> Place

From there you can tick "Right" and the buttons will instantly move to the right.

Mess around with Ubuntu Tweak as it can do some nifty tweaks.

You might be wondering why I said "bad news" and "almost yes", well, when you maximize the window, the buttons will be on the left and as far as I know, there is no way to move them from there.

did this and buttons in the tweak box went to the right but not anywhere elsee like in firefox, thunderbird and other apps as well. They are still on the left.

---

### Post by benjie1 on 2012-02-20
> **raja.genupula said:**
> Follow this , dont worry about the Dist version . it works fine . 

[http://www.howtogeek.com/howto/13535/move-window-buttons-back-to-the-right-in-ubuntu-10.04/](http://www.howtogeek.com/howto/13535/move-window-buttons-back-to-the-right-in-ubuntu-10.04/)


Pressing alt + F2 does not bring up the run application box as shown on the page above. can't do anything further. any other ideas?

---

### Post by raja.genupula on 2012-02-20
> **benjie1 said:**
> Pressing alt + F2 does not bring up the run application box as shown on the page above. can't do anything further. any other ideas?

Do this one by one
*open software center and type gconf editor , it will give you a out list in that select "configuration editor " and install it . 

*After installing that one go to Unity dash and in the launcher bar type as gconf it will give you what you have installed from the software center .then open it .

And follow the instructions which  are given at the link of my above post . 

All the best , if anything comes up , let us know .

---

### Post by u2nTu on 2012-10-23
Posting here because this thread comes up high in the search rank.

There is no need to install new packages or struggle through howto pages.

For 12.04, simply paste the following into a terminal.:
```
gconftool -s /apps/metacity/general/button_layout -t string menu:minimize,spacer,maximize,spacer,close
```The above ("menu:minimize,spacer,maximize,spacer,close") adds a space between buttons to make it harder to accidentally hit the wrong one. Just remove the two "spacer," items if you prefer your buttons crammed tightly together, which is the default.

**EDIT:**
Apparently gconf is deprecated from 12.10 Quantal onward. The schema to control button placement, however, remains valid: *org.gnome.desktop.wm.preferences button-layout*. So while the above works for 12.04 and earlier, the following works for current ( and **hopefully** future) releases:
```
gsettings set org.gnome.desktop.wm.preferences button-layout menu:minimize,spacer,maximize,spacer,close
```Of course, there's easier access to many more settings using dconf-editor (sudo apt-get install dconf-tools); this just puts the window controls back where they belong. :)
</EDIT>

As Lisiano pointed out, button arrangement reverts to the default when windows are maximized. (No problem for me since I hardly ever maximize.) Hopefully this will be fixed in future releases.

Anyways, found this after much searching and checking. Wanted to save others the trouble.

---

