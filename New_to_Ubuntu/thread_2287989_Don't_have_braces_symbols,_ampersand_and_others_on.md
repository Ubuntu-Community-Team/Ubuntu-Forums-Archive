---
title: "Don't have braces symbols, ampersand and others on keyboard"
date: 2015-07-23
forum: New to Ubuntu
---

### Post by kapi on 2015-07-23
Hi, just installed 14.0.4.2 and all looks fantastic

Just noticed that when i try to use the keyboard for ampersand using  --   shift+7    -- nothing happens.

Other characters are missing too SHIFT+1, SHIFT+2,SHIFT+3, SHIFT+0,SHIFT+9,SHIFT+8,

Any help would be really appreciated

Thanks

---

### Post by toxx on 2015-07-23
Run both of these commands, then paste us the output

```

locale -a
cat /etc/default/keyboard

```

Also, try ```
 [COLOR=#000000]dpkg-reconfigure keyboard-configuration 
```[/COLOR]

---

### Post by grahammechanical on 2015-07-23
A lot depends on the language we choose for the installation & the keyboard type that we choose. Ubuntu defaults to installing English (US) and puts a keyboard layout app indocator in the top panel. That app indicator has a menu that includes Keyboard Layout Chart. Click on that and see if the keyboard layout matches the layout of the actual keys on the keyboard.

We can also add and remove keyboard layouts by selecting Text Entry Settings and in the dialog that appears click the + button and select a keyboard layout form the list. We can also access these utilities from System Settings.

Regards.

---

### Post by kapi on 2015-07-23
Hi Daniel

Thanks for the reply, much appreciated. The output from the locale is: 

C.UTF-8
en_AG
en_AG.utf8
en_AU.utf8
en_BW.utf8
en_CA.utf8
en_DK.utf8
en_GB.utf8
en_HK.utf8
en_IE.utf8
en_IN
en_IN.utf8
en_NG
en_NG.utf8
en_NZ.utf8
en_PH.utf8
en_SG.utf8
en_US.utf8
en_ZA.utf8
en_ZM
en_ZM.utf8
en_ZW.utf8
POSIX


I also ran the dpkg-reconfig as suggested and rebooted the system but the problem still remains.

Thanks

---

### Post by kapi on 2015-07-23
Just noticed that if I type shift quickly then type 2 straight after the the correct symbol appears. So there appears to be a problem somewhere and it's not even responding to certain letters using left shift but works for certain characters using right shift.

Any ideas please

---

### Post by kapi on 2015-07-23
Update - -  The only way I can get around this for now is to turn on sticky keys in settings-> accessbility

Is there anyone from Ubuntu who has a more ideal solution? I have no problem on my other laptop (Toshiba) using the 32bit version of 14.04.2 but only on my HP laptop using the 64bit version

Many thanks again

---

### Post by gordintoronto on 2015-07-24
Did you run: cat /etc/default/keyboard

---

### Post by zendejaskids on 2015-07-24
From the logs it looks like you don't have the US locale installed. Look in Settings > Keyboard > Click on "Text Entry" > then add the English (US) keyboard layout.

---

### Post by Vladlenin5000 on 2015-07-24
> **zendejaskids said:**
> From the logs it looks like you don't have the US locale installed. Look in Settings > Keyboard > Click on "Text Entry" > then add the English (US) keyboard layout.

Exactly! At last someone understood the problem...

General rule: Unless you're a typist and quite used to a certain layout, you should always choose the keyboard layout for the system that matches the one of your physical keyboard (there are hundreds to choose from but only one matches what you have). In case of a US International variant being used for any language requiring accentuated characters not (usually) present in the English language, one must choose the same US International but with the "dead keys" variant:

 - Apostrophe and double quotes, when typed before the character to be accentuated, will then produce an acute accent and umlaut, respectively. 
 - Grave accents, circumflexes and tildes have their own (dead) keys (with any other than "dead keys" variant this diacritic symbols will print as standalone characters).
 - The apostrophe and double quotes can also be used in this scenario provided SPACE is typed after the symbol.

---

### Post by kapi on 2015-07-25
Morning and thanks for the reply. I ran the cat /etc/default/keyboard and got the following output:

 The following variables describe your keyboard and can have the same
# values as the XkbModel, XkbLayout, XkbVariant and XkbOptions options
# in /etc/X11/xorg.conf.

XKBMODEL="pc105"
XKBLAYOUT="gb"
XKBVARIANT=""
XKBOPTIONS=""

My keyboard settings are set to (EN1) English UK and the keyboard chart layout confirms that when I check.

I also noticed that when I hold down the left shift key and press the letter 'm' that nothing happens. Instead I have to quickly tap the shift key followed by the 'm' key to make the capital m appear. The goes for the characters in keys 1,2,3,4,7,8,9,0

Many thanks

,,,

---

### Post by kapi on 2015-07-25
Thanks, ran that and got the following

 The following variables describe your keyboard and can have the same
# values as the XkbModel, XkbLayout, XkbVariant and XkbOptions options
# in /etc/X11/xorg.conf.

XKBMODEL="pc105"
XKBLAYOUT="gb"
XKBVARIANT=""
XKBOPTIONS=""

---

### Post by dino99 on 2015-07-25
Your usual shortcuts may have changed: ctrl+key, or ctrl+shift+key

[https://help.ubuntu.com/community/KeyboardShortcuts](https://help.ubuntu.com/community/KeyboardShortcuts)
[https://wiki.ubuntu.com/Hotkeys/Troubleshooting](https://wiki.ubuntu.com/Hotkeys/Troubleshooting)

---

### Post by zendejaskids on 2015-07-25
Your keyboard could also be broken...? Probably not though if it works after quickly pressing the shift and the m key. This could be a software problem most likely or something is wrong. Check all the the keyboard setting and make sure everything is all right. Also Chechen accessibility settings in the typing/mouse section.

---

### Post by zendejaskids on 2015-07-25
I don't think the shortcuts have been changed because he can quickly press the shift key then the key and the capital/symbol will appear.

---

### Post by kapi on 2015-07-26
Hi guys, no the shortcuts haven't changed, I checked. It's definitely a software problem. Just don't know where to turn next.

I've tried everything I can think of (even left feedback on Launchpad)

---

