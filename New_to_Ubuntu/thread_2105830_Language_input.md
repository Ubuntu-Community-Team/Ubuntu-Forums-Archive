---
title: "Language input"
date: 2013-01-17
forum: New to Ubuntu
---

### Post by kkira13 on 2013-01-17
I need to be able to write in 3 languages on my PC (Armenian, russian and english). So when I check Lxkeymap, I can find all of those and even activate from there. But I need a better switching method so I activated iBus, however, when I try to edit input methods in iBus preferences, in "select an active input" drop down menu, there is nothing. How can I solve this problem ? Or if it is iBus related, what other input method switcher can I use ?

Edit: installing iBus-m17n partially solved the problem, now I can select input methods, but the problem is m17n library does not contain a good input method for armenian. I really like the ones that I see in Lxkeymap, how can I make them appear there ?

---

### Post by Locus Kiesselbachi on 2013-02-10
Hello!

Im also using LXKeyMap between three languages. 
I even made shortcut of LXKeyMap to desktop. LOL

I remember once I had some feature in window-panel, but it got lost because had to reinstall whole Lubuntu.

---

### Post by GrouchyGaijin on 2013-02-10
> **kkira13 said:**
> I need to be able to write in 3 languages on my PC (Armenian, russian and english). So when I check Lxkeymap, I can find all of those and even activate from there. But I need a better switching method so I activated iBus, however, when I try to edit input methods in iBus preferences, in "select an active input" drop down menu, there is nothing. How can I solve this problem ? Or if it is iBus related, what other input method switcher can I use ?

Edit: installing iBus-m17n partially solved the problem, now I can select input methods, but the problem is m17n library does not contain a good input method for armenian. I really like the ones that I see in Lxkeymap, how can I make them appear there ?

I don't know if there is something in Lbuntu (is that what you are running?) that makes ibus work differently than in regular Ubuntu, but when I set my system for Japanese/English, installing iBus was not enough.

I also needed to install the files for Japanese.  In my case, that is Anthy and the anthy related files including anthy-ibus.
Only after installing the required language input files did the input method Anthy appear in the iBus language input drop down menu.

---

### Post by Locus Kiesselbachi on 2013-02-11
ok I think I got this somewhat.
Right-click on startbar, select "Add/Remove Panel Items", select "Panel Applets", select +Add, *...a list pops up*, select "Keyboard Layout Switcher".
Now you have keyboard layout seen on windowbar (near clock).
I dont know how to do further the nice way, so...

kkira13 should enter to LXtermial:

setxkbmap -layout "us,am" -variant ",,std" -option "grp:alt_shift_toggle"

With this command you get to switch between english and armenian - ALT+SHIFT. I can not get russian by adding ,ru to "us,am", like that  "us,am,ru". By some reason it does not work, it gives:

Error loading new keyboard description

This solution is not permanent and needed to add every time after restart. 

[I]edit
[/I]It still would be nice if you have enabled "Keyboard Layout Switcher" as mentioned.
**kkira13**, run this command through LXTerminal:[B]

@setxkbmap -option grp:ctrl_shift_toggle "am,ru,us"' | sudo tee -a /etc/xdg/lxsession/Lubuntu/autostart[/B]

This command makes keyboard layout switching with CTRL+SHIFT between armenian/russian/english and its permanent after restart.

For example I needed estonian, english, and russian keymap:
I manually entered at the end of "autostart" fail:
@setxkbmap -option grp:ctrl_shift_toggle "ee,us,ru"

eesti keeles on palju täppidega tähti
english
&#1088;&#1091;&#1089;&#1089;&#1082;&#1080;&#1080;&#1081; &#1103;&#1079;&#1099;&#1082;

I chose these with Ctrl+Shift easily.
:guitar:

---

