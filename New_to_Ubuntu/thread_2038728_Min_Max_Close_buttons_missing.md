---
title: "Min Max Close buttons missing"
date: 2012-08-07
forum: New to Ubuntu
---

### Post by Primus1 on 2012-08-07
This still seems to be a problem. My Windows are not showing 'min, max, close' buttons. Firefox has none of these either. I installed Chromium and that has got 'min max close' buttons, but only when maximised. Does anyone know what is causing this or have a solution? This is a horrible problem. I am using Lucid 10.04. Thanks

---

### Post by jtarin on 2012-08-07
Are you running Compiz? If so try disabling it. Have you got any window managers other than Meta-city running?

---

### Post by Kalanac on 2012-08-07
Hi there,

If you're running a Unity desktop (the standard in the recent versions of ubuntu) the window buttons hide until you mouse over them.  Just run your mouse up to the top of the screen and if things are working properly they should appear at the left hand corner along with the menu options and such :)

---

### Post by Frogs Hair on 2012-08-07
> **Kalanac said:**
> Hi there,

If you're running a Unity desktop (the standard in the recent versions of ubuntu) the window buttons hide until you mouse over them.  Just run your mouse up to the top of the screen and if things are working properly they should appear at the left hand corner along with the menu options and such :)

Strange , for me it depends if the theme has that feature other wise the window button always appear.

---

### Post by uRock on 2012-08-07
Can you take a screenshot of this issue to help us? Thanks.

---

### Post by Frogs Hair on 2012-08-07
Primus1 , if you are using Compiz and the title bar is missing try the following. ```
compiz --replace
``` 
If Not
```
metacity --replace
```

---

### Post by Primus1 on 2012-08-07
Hi jtarin, I have compitz but checking all running processes ( ps aux | less ) I can't see it listed. Not sure what a windows manager is, I have Nautilus?  Don't think I have 'Metacity'. Kalanac, yes that works with Firefox, as I said my OS is Lucid 10.04, is that Unity? ( I have not been able to install 12.04 but that's another story/can of worms/mystery ). The buttons don't show when using Gedit, not with or without F11. I can't max or min my 'software centre' nor drag to resize it. All was well yesterday, now this strange window behaviour. Hi uRock I will try to attach a screen cap with this message.

---

### Post by jtarin on 2012-08-07
10.04 is not Unity. More than likely your Window Manager is Meta-City.....if you don't know what a window manager is....then  it's Meta-City. :) Try another theme if you've been theme swapping.

---

### Post by Primus1 on 2012-08-07
> **jtarin said:**
> 10.04 is not Unity. More than likely your Window Manager is Meta-City.....if you don't know what a window manager is....then  it's Meta-City. :) Try another theme if you've been theme swapping.

I checked software centre and I have Metacity installed. I can't see a GUI button for it so I assume I would have to get to it in a Terminal. Ok I know this is wrong but I keyed 'metacity' and it produced this:


dave@dave-storm:~$ metacity
Window manager warning: Screen 0 on display ":0.0" already has a window manager; try using the --replace option to replace the current window manager.
dave@dave-storm:~$ 

AH! Like a good Linux soldier I just checked the Metacity Ubuntu Documentation. I must have turned M off after 'looking'  #-oat Compiz. Restarted Metacity - all the open Windows flashed for a second and then all the Max/Min/Close buttons reappeared. Wonderful :)

Thanks to all and thanks Jtarin for pointing me in the direction of Metacity.

---

### Post by jtarin on 2012-08-07
Your welcome.

---

