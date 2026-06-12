---
title: "Classical Greek (and Hebrew) in Ubuntu without drawbacks"
date: 2009-04-30
forum: Outdated Tutorials &amp; Tips
---

### Post by VCoolio on 2009-04-30
There are several solutions to writing classical Greek and Hebrew, but all with drawbacks:
1. input by unicode or from character map: ok for single characters but takes far too much time when you're writing texts.
2. using plugin for Openoffice.org [Thessalonica]("http://www.thessalonica.org.ru/en/"), but it requires Java and works only with openoffice.
3. Use [this howto]("http://www.frame-poythress.org/poythress_articles/2007KeyboardGreekHebrew.htm") by V.S. Poythress. But when I followed it completely in Intrepid it broke my usual input of complex characters and support for unicode input. I think it had to do with changing to xim-input, but I'm not sure.

The last option seemed the most promising nevertheless, so with my fresh Jaunty install I tried parts of it and now I have it running without the drawbacks. :) Here follows how to do the classical Greek / ancient Greek part, but for classical / ancient Hebrew goes the same. All credits to V.S. Poythress and A. Pater though for the files. 

This works on Ubuntu Desktop i386 9.04 Jaunty. Please report if this works on Kubuntu etc, or what change is needed to make it work.

0. The howto I linked to requires your system to be in locale en_US.UTF-8. Don't know how necessary that is, but if you have it different you might have to change the location you use in step 2 to your locale. Type 'locale' in your terminal and check the output. 
The link I gave also tells howto change locale if you want. You can also change your locale just for one session with the EXPORT command you can find there, so you are back to default when you login again. Just follow steps below, then run 'export LANG=en_US.UTF-8'.

1. From the link I gave, download [evdev.xml]("http://www.frame-poythress.org/poythress_articles/evdev.xml"), [Compose.new]("http://www.frame-poythress.org/poythress_articles/Compose.new") and [gr.hal]("http://www.frame-poythress.org/poythress_articles/gr.hal") (not gr.new) (and the [Hebrew file]("http://www.frame-poythress.org/poythress_articles/il.hal") if you need).

For the following you need root rights, so use sudo cp / mv in terminal or use nautilus with root rights (run 'gksudo nautilus' in terminal or Alt-F2 window).

2. put Compose.new in
/usr/share/X11/locale/en_US.UTF-8/
Backup the existing Compose (e.g. rename to Compose.old) and rename new one to Compose

3. after backup of existing evdev.xml put downloaded evdev.xml in:
/usr/share/X11/xkb/rules/

4. after backup of existing gr put downloaded gr.hal in
/usr/share/X11/xkb/symbols
and rename to gr

5. Logout, login, go to system > preferences > keyboard > layouts and add greek polytonic. I did not choose the Poythress one as it refused to compose complex characters with spiritus in it. With the button "layout options" > layout switching you can add a keybinding to switching layout easily. Also you can add a layout switcher to your panel (right click > add to panel > keyboard indicator).

6. I recommend the font Palatino Linotype for writing Greek, but check for yourself.

7. Learn the dead keys for writing Greek. I've attached a textfile which shows what key does what. In short: [];':" are the dead keys to use. That is on my qwerty-keyboard the four buttons right of 'p' and 'l'.

Now you can write classical polytonic Greek in any application you want by changing your layout with the keybinding you chose or clicking the switcher on your panel. And you can still use the default compose to input ß å ç ñ etcetera. And you can still use ctrl-shift-u + unicode. If nevertheless something broke, then undo steps 2, 3 and 4 and login again.

Additional remarks on this howto are most welcome.

---

### Post by simosx on 2009-05-05
In Ubuntu 9.04, you can type Greek Polytonic simply by adding the Greek keyboard layout in addition to your current layout. Also, you can set a shortcut in order to switch between English and Greek.
There has been an addition in the default Greek layout so that users can type Greek Polytonic in addition to Modern Greek.

Specifically,

AltGr + [ + &#945; = &#8118;
AltGr + { + &#945; = &#8113;
AltGr + @ + &#945; = &#7937;
...

The dead keys are under ; : AltGr+; AltGr+ AltGr+' AltGr+@ AltGr+[{]} (4 keys).

Some instructions are available at 
[https://docs.google.com/Doc?id=dccdrjqk_1g6g6ncgw](https://docs.google.com/Doc?id=dccdrjqk_1g6g6ncgw)
Feel free to translate.

---

### Post by VCoolio on 2009-05-09
Didn't know that. But can you combine the accents and spiritus (and iota subscriptum) like so:[SIZE="3"] &#8102; &#7940; &#8080; [/SIZE]etc?

---

### Post by simosx on 2009-05-10
> **VCoolio said:**
> Didn't know that. But can you combine the accents and spiritus (and iota subscriptum) like so:[SIZE="3"] &#8102; &#7940; &#8080; [/SIZE]etc?

Yep,

type AltGr+[  AltGr+]  AltGr+:  &#969;  and you get &#8102;
type AltGr+:  AltGr+'  &#945;           and you get &#7938;

and so on.
Other samples are &#8069;&#8183;&#8119;&#8114;&#993;&#951;&#991;&#955;&#919;&#992;&#1022;&#976;&#946;&#982;&#969;&#891;&#1021;&#893;&#1023;«»&#962;&#987;&#986;&#1013;&#977;&#952;&#1012;&#1016;&#1015;&#993;&#992;

---

### Post by VCoolio on 2009-05-10
Specify your problem. Are you trying simosx's method or my first post here? If you're trying to add a keyboard map you can look at step 5 of my howto. And is right-alt your compose key? You can check your compose key at the same place and use that to activate the dead keys.

---

### Post by simosx on 2009-05-10
I have added a guide on how to add the Greek keyboard layout and how to type Greek Polytonic,
[http://simos.info/blog/archives/888](http://simos.info/blog/archives/888)

---

