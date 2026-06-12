---
title: "Microsoft Core Fonts abroad?"
date: 2008-11-15
forum: New to Ubuntu
---

### Post by Obero on 2008-11-15
I've installed the microsoft core fonts on this account, which is the administrator. However, when I go on other accounts which aren't administrator, the installation doesn't seem to be working on it. So how do I enable microsoft fonts for every user?

---

### Post by Kellemora on 2008-11-15
Hi Obero

If you obtained them through Synaptic or add/remove they should have installed in the proper location to be used by all.

If you look in /usr/share/fonts/truetype you should find the mstcorefonts folder there.

There is NOT supposed to be a hidden folder named .fonts in your user directory, but a lot if folks tell you to put the fonts in a hidden folder in your user directory by creating a hidden folder named .fonts.  This makes them only usable by the user.

Fonts do NOT need to be INSTALLED in Linux, they only need placed in the /usr/share/fonts/truetype folder if truetype.  In some cases, you need to reboot for some of the programs to be able to find them though.

TTUL
Gary

---

### Post by Obero on 2008-11-15
> **Kellemora said:**
> Hi Obero

If you obtained them through Synaptic or add/remove they should have installed in the proper location to be used by all.

If you look in /usr/share/fonts/truetype you should find the mstcorefonts folder there.

There is NOT supposed to be a hidden folder named .fonts in your user directory, but a lot if folks tell you to put the fonts in a hidden folder in your user directory by creating a hidden folder named .fonts.  This makes them only usable by the user.

Fonts do NOT need to be INSTALLED in Linux, they only need placed in the /usr/share/fonts/truetype folder if truetype.  In some cases, you need to reboot for some of the programs to be able to find them though.

TTUL
Gary

I uninstalled the fonts on the administrator, and then installed through *Add/Remove*, then I went to one of the normal users and it appeared that the fonts didn't work still. They're working on the administrator right now again, but they're not working for the other accounts. Any way to solve this?

---

### Post by Kellemora on 2008-11-15
Sorry Obera

Whatever is causing it is above my level of expertise, which isn't much!

I have 5 different users here in my office and all of the fonts are available to all of them, in programs like OOo and most others.

Now some programs DO  have their own font's and do not use external fonts at all.  Others, there is a setting in the program itself as to where to use the fonts from.
For example:  I can't change the fonts Firefox uses in it's titlebars, but I can change the fonts used in the display area to over-ride the html pages own fonts.

There are not a whole lot of fonts in the mstcorefonts package, perhaps you have a document that is using a font you don't have installed?????

Can you give me an idea of WHICH program is not seeing the fonts.
Also, did you try rebooting?

TTUL
Gary

---

### Post by metallicamike on 2008-11-15
u could just reinstall them on the other users, thats all i can really recommend :-k

---

### Post by Obero on 2008-11-15
> **Kellemora said:**
> Sorry Obera

Whatever is causing it is above my level of expertise, which isn't much!

I have 5 different users here in my office and all of the fonts are available to all of them, in programs like OOo and most others.

Now some programs DO  have their own font's and do not use external fonts at all.  Others, there is a setting in the program itself as to where to use the fonts from.
For example:  I can't change the fonts Firefox uses in it's titlebars, but I can change the fonts used in the display area to over-ride the html pages own fonts.

There are not a whole lot of fonts in the mstcorefonts package, perhaps you have a document that is using a font you don't have installed?????

Can you give me an idea of WHICH program is not seeing the fonts.
Also, did you try rebooting?

TTUL
Gary

Hmm, programs? Well, mainly websites or .html files. I'll try rebooting, but I'm not quite sure that's going to help.

---

### Post by Obero on 2008-11-15
> **Obero said:**
> Hmm, programs? Well, mainly websites or .html files. I'll try rebooting, but I'm not quite sure that's going to help.

Well, well, well. If that ain't so. Restarting the computer did the trick. Looks like you saved the day, buddy. Thanks.

This is wierd though. It only works in Firefox. In Opera, it ain't flinching.

---

