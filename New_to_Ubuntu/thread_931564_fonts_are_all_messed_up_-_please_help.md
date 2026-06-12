---
title: "fonts are all messed up - please help"
date: 2008-09-27
forum: New to Ubuntu
---

### Post by HarmonicaGoldfish on 2008-09-27
For the past little while I have been having problems when opening documents in Open Office. The documents would open with the font 'Jungle' even if I had another font set as default - mainly with documents I downloaded from the net or an email.

I tried to reset the defaults - no change.

Arial seemed to be somehow linked to Jungle, so I (perhaps too hastily...) logged in as root and deleted arial from the truetype folder.

Now, this weird jungle font is being used in my browser as well (Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.3) Gecko/2008092510 Ubuntu/8.04 (hardy) Firefox/3.0.3)! It's horrible.

[ATTACH]86579[/ATTACH]

How can I fix this?

---

### Post by mihaiv on 2008-09-27
For firefox please check the implicit font setting In Edit\Preferences\Content. For your entire system you can change the default font setting in System\Preferences\Appearance\Fonts. In Open Office you can go at Tools\Options\OpenOffice.org Writer\Basic Fonts.

---

### Post by HarmonicaGoldfish on 2008-09-27
The first two were the ways I tried to reset the defaults but they did not work.

I never did try the firefox one, so I will go try it now. However, the wonky font only started after I changed my computer settings. I never touched the ff settings. And I don't think that will help with the open office issue...but will try!

---

### Post by barlaventoexpert on 2008-10-04
I have also encountered this problem since I upgraded to Ubuntu Hardy 64bit and Oo 2.4. 

I have checked the basic system fonts, the Oo fonts and the Firefox fonts and none are set to Jungle.

There appears to be a bug here but where?

---

### Post by the8thstar on 2008-10-13
I second that. Same problem here.

---

### Post by HarmonicaGoldfish on 2008-10-14
Finally I uninstalled then reinstalled msttcorefonts (found in usr/share/fonts/truetype) with synaptic. This seems to have fixed things!

---

### Post by the8thstar on 2008-10-15
> **HarmonicaGoldfish said:**
> Finally I uninstalled then reinstalled msttcorefonts (found in usr/share/fonts/truetype) with synaptic. This seems to have fixed things!

Tried that. Didn't work though.

---

### Post by Kellemora on 2008-10-15
Hi HG

I've seen some mention here in the past for folks to put new fonts they download into a hidden folder in their home directory, eg: /home/George/.fonts

If you access a font from the hidden folder in your home directory, on occasion some file somewhere redirects font requests to that hidden folder.  Therefore, if THAT is where you put Jungle, and if that's the only font there, that's the only font that is usable to the system until it is redirected back to the /usr/fonts folder.

I've not heard of this happening to folks who put their ttf fonts in /usr/fonts/truetype, but heard it from those who did the hidden .font folder in their home directory.

How to fix it, I don't know, sorry.  But perhaps deleting the hidden folder might help and then rebooting.

TTUL
Gary

---

