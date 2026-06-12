---
title: "[SOLVED] Faulty keyboard indicator - unable to switch from English to Arabic"
date: 2008-06-10
forum: New to Ubuntu
---

### Post by al.adab on 2008-06-10
hello

before switching from Gutsy to Hardy Heron 8.04 (fresh installation) I was able to type Latin and Arabic characters on any kind of format (OO.org writer, Stardict, Firefox, etc) by clicking on the keyboard indicator. To do this, I simply had to update the language support (without downloading the Arabic package), add Arabic to the keyboard's layout (system.preferences.keyboard>layout) as well as to OO.org writer (tools.options.language settings). 

On Hardy 8.04 this is not working. Wherever I need to write in Arabic (and click on the keyboard indicator)...all I get is Latin characters. All the settings are as they were in Gutsy. I tried to download the Arabic package from system>administration>language support, and found some SCIM program sitting on my deskbar. If I'm on an OO.org writer documents, it works like the keyboard indicator - so I can use it there to type Arabic. Anywhere else, though (internet browser, dictionaries, etc) it doesn't work. 

Can anyone please help. Thanks.

---

### Post by al.adab on 2008-06-10
Update: I had a closer look at what happens when I use SCIM to write in Arabic on an OO.org writer doc, and...it's a complete disaster. At least one third of the keys on the keyboard do not input an Arabic character at all - some strange symbols come up instead. In short: it can't be used to type Arabic. I then tried to the following things, to no avail: 

- uninstall the Arabic package from language support
- unclick "enable support to enter complex character" on language support
- a combination of these two + using keybord indicator instead of SCIM and the other way around for each combination. 

This is a serious issue, and I'd be extremely grateful if a solution is found. 

Many thanks for taking the time to go through this.

---

### Post by al.adab on 2008-06-10
Update II: it now works IF I do the following: 

1) remove Arabic package (System>Administration>Language Support)
2) unclick "enable support to enter complex characters" (as above)
3) go to System>Preferences>Keyboard>Layout and REMOVE Arabic
4) go to System>Preferences>Keyboard>Layout and ADD Arabic

Please notice that I need to go through steps 3) and 4) EVERY TIME I re-boot, otherwise I cannot type in Arabic. After removing from and adding Arabic to the keyboard layout, I don't have to reboot. 

It's a (giant) step forward, but still...can whatever prevents the keyboard layout from keeping my settings after re-booting be fixed? How?

Thanks.

---

### Post by cariboo on 2008-06-10
Maybe this will help you. It uses hindi as an example, but if you know the locale for arabic it should be easy enough to do.

[http://www.linux.com/base/ldp/howto/Indic-Fonts-HOWTO/locale.html](http://www.linux.com/base/ldp/howto/Indic-Fonts-HOWTO/locale.html)

Jim

---

### Post by al.adab on 2008-06-11
Thanks for the link cariboo907 but I don't understand what the documents says. Would you mind translating it into simple language for me?

---

### Post by fenian on 2008-06-11
When you  do step 4 (go to System>Preferences>Keyboard>Layout and ADD Arabic) did you click the circle next to it to make it default?

---

### Post by cariboo on 2008-06-11
I'm not exactly sure what the language code for arabic is, but maybe you can find some more help here:

[http://www.linux4arab.com/](http://www.linux4arab.com/)

Jim

---

### Post by al.adab on 2008-06-11
thanks for your message fenian

No, the default language at keyboard>layout is USA (English). It's ticked. 
Arabic is not ticked. The OS default language on my machine is USA English.

cariboo907, thanks for the link in Arabic, but the problem seems to be (I might be wrong) with the keyboard layout settings or something related rather than the system's ability to write in Arabic. All the characters are there and available. It's just having to set the keyboard layout each time I start up the machine that's slightly annoying.

---

### Post by al.adab on 2008-06-12
Bug reported at 
[https://bugs.launchpad.net/ubuntu/+source/scim/+bug/238849](https://bugs.launchpad.net/ubuntu/+source/scim/+bug/238849)
thanks everyone for trying to help.

---

### Post by jou770d on 2008-06-12
I also use Arabic on my computer but somehow I didn't have any problems getting it to work on 8.04.
I've only tried SCIM a long time ago on 7.10 but it didn't work properly (it was switching languages randomly and some characters were not showing properly).

This is all I had to do to make Arabic work on Hardy:
1) Installed the following packages from Synaptic:
* languade-support-ar (it's only a meta package, it'll download some other packages).
* language-support-extra-ar (another meta package)

2) I went to System -> Preferences -> Keyboard and added a new layout (Layout = Arabic and Variants = Default)

3) Opened 'Layout Options' -> 'Layout Switching' to choose a key combination for switching layouts (personally I use both shift keys).

That's all I had to do on both of my devices which are a Toshiba Satellite a30-303 laptop and a homebuilt desktop with a spacewalker keyboard.

---

### Post by al.adab on 2008-07-28
Have just received the solution to this: 

- Edit the file /etc/X11/xorg.conf in any editor as a super user (eg. sudo gedit /etc/X11/xorg.conf)
- Look for the keyboard section. 
- Add "ar" next to the keyboard automatically set by the system. Mine looks like this (I use a spanish layout by default):
Section "InputDevice"
    Identifier    "Generic Keyboard"
    Driver        "kbd"
    Option        "XkbRules"    "xorg"
    Option        "XkbModel"    "pc105"
    Option        "XkbLayout"    "es, ar"
EndSection
- Save and restart.

It works. Simpler than I thought - I must've missed this out somehow, I'm sure someone must've suggested it at some stage!

---

