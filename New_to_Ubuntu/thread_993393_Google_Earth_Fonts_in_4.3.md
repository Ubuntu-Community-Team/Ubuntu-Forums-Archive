---
title: "Google Earth Fonts in 4.3"
date: 2008-11-25
forum: New to Ubuntu
---

### Post by RedRat on 2008-11-25
I have Google earth installed in Ubunto 8.04. However when the toolbar displays, the font size appears to be something like a font size of 3 or 4 pts. In the Google Earth Toobar (File, Edit, View, Tools, Add, Help) this small font size is barely readable. Is there any way to increase this font size?? Other parts of the program are OK, just this toolbar.

---

### Post by bhadotia on 2008-11-25
Right click on the desktop and select "change desktop background" the switch to the fonts tab and try using bigger fonts and see if this works. This will also effect other apps as it sets fonts system wide.

---

### Post by RedRat on 2008-11-25
> **bhadotia said:**
> Right click on the desktop and select "change desktop background" the switch to the fonts tab and try using bigger fonts and see if this works. This will also effect other apps as it sets fonts system wide.

Thanks. But no, the fonts in all of the native Linux apps that I use are just fine, right where I want them; it is only in Google Earth were the toolbar font is oddly very tiny. Even when I run Wine and Windows apps I could set the fonts larger by configuring Wine. I suspect that it has something to do with Google Earth being ported over to Linux. I wish I could fix it though because trying to read such small fonts is hard on my old eyes.

---

### Post by bhadotia on 2008-11-25
> **RedRat said:**
> Thanks. But no, the fonts in all of the native Linux apps that I use are just fine, right where I want them; it is only in Google Earth were the toolbar font is oddly very tiny. Even when I run Wine and Windows apps I could set the fonts larger by configuring Wine. I suspect that it has something to do with Google Earth being ported over to Linux. I wish I could fix it though because trying to read such small fonts is hard on my old eyes.

There might be some option in google earth preferences regarding the font size etc. Have a look around to find it. I cannot check as I am on windows at present.
Also, if that does not work, look at the .googleearth directory (after pressing ctrl+h) in your home folder and see if you can find some configuration file wit the fonts settings in it and edit that manualy.

---

### Post by RedRat on 2008-11-25
> **bhadotia said:**
> There might be some option in google earth preferences regarding the font size etc. Have a look around to find it. I cannot check as I am on windows at present.
Also, if that does not work, look at the .googleearth directory (after pressing ctrl+h) in your home folder and see if you can find some configuration file wit the fonts settings in it and edit that manualy.

Looked in .googleearth and did not see anything that resembled a config file. there is nothing in the toolbar, nothing! Checked each section. Nothing that governs the appearance of the Window toolbar.

---

### Post by bhadotia on 2008-11-25
> **RedRat said:**
> Looked in .googleearth and did not see anything that resembled a config file. there is nothing in the toolbar, nothing! Checked each section. Nothing that governs the appearance of the Window toolbar.

Then I have no idea.
I will try to find out something (If I can) when I log into ubuntu (after an hour or so)and install googleearth (I also wanted it).

---

### Post by dandart on 2008-12-16
Edit ~/.config/Google/GoogleEarthPlus.conf


In [Render]

Change the line:

GuiFontSize=8

To:

GuiFontSize=14

Cheers!

---

### Post by philinux on 2008-12-16
As dandart says. I use this setting.

GuiFontFamily=Arial Black
GuiFontSize=12

---

### Post by RedRat on 2008-12-16
Thanks to dandart and philinux for your help. That has solved my problem. I would suggest the following (at least it works for me):
SecondaryFontVersion2Family=Bitstream Vera Sans
SecondaryFontVersion2Size=12
SecondaryFontVersion2Style=0
SecondaryFontVersion2Weight=75

For reasons known only to Google, the Arial font face does not render quite as well as the Bitstream font. Also changing the font weight from 50 to 75 very definitely improved the appearance of the tool bar.

Many thanks for the help.

---

### Post by ad5os on 2009-01-08
Make sure you run the program before you try to edit the settings.. was wondering why the gui preferences weren't there till after I ran 4.3 from the install.

---

### Post by yogreece on 2009-01-23
hi all
sorry, I want to ask us for the same problem that happens with me with GoogleEarth and with Open Office 
can any body to emplane to me exactly, how  can I solve this problem?
thanks again

---

### Post by RedRat on 2009-01-23
> **yogreece said:**
> hi all
sorry, I want to ask us for the same problem that happens with me with GoogleEarth and with Open Office 
can any body to emplane to me exactly, how  can I solve this problem?
thanks again

Take a look at responses #7 thru 10, they tell you what you must edit. I am running Open Office 3 and I don't have this problem. I would suggest one of the previous replies here about the Desktop settings. However, at least in OO 3, go to 'Tools' and then 'Options', there are a myriad of ways to configure just about anything in all of the OO apps.

---

### Post by freeediver on 2009-02-05
I have the same problem, the font size for the sidebar information,
search ets is just to small.
I attempted the fix in reply #7 and could not access the commands.
I even tried to copy/paste the edit command into my terminal box
and when finally copied the correct number of spaces I was told I did not have permission to access the file.

What now?
Thanks

---

