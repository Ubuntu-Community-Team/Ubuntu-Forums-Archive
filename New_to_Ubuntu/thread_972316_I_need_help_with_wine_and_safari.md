---
title: "I need help with wine and safari"
date: 2008-11-05
forum: New to Ubuntu
---

### Post by rspk12 on 2008-11-05
i got ubuntu yesterday so i am still learning how to do things....

i need help with this :( im following a guide ( tutorial )
------------------------------------------------------------------------
First lets install Microshit's Core Fonts and wine within the Terminal Applications->Accessories->Terminal
sudo apt-get install msttcorefonts wine
------------------------------------------------------------------------
Second Make sure wine is set to use the windows version Xp, just click Applications/Wine/Configure Wine
or type "winecfg" in the terminal
------------------------------------------------------------------------
Third lets copy Microshits Core Fonts to the wine font directory!
cp /usr/share/fonts/truetype/msttcorefonts/Arial*.ttf ~/.wine/drive_c/windows/fonts/
cp /usr/share/fonts/truetype/msttcorefonts/Times_New_Roman*.ttf ~/.wine/drive_c/windows/fonts/


( how do i copy the microshits core fonts to there idk?????))))

---

### Post by brandoncolorado on 2008-11-05
That command you see 'cp' is the copy command.  Just enter that whole command into the terminal.  Have you tried the easier method for the core fonts?  I believe this works.

Installing Microsoft Truetype fonts on Ubuntu

You can install the MS core fonts by installing the msttcorefonts package. To do this, enable the &#8220;Universe&#8221; component of the repositories. This is done by default in Feisty. After you do that, use the following command from the command line:

In terminal  type this -->       sudo apt-get install msttcorefonts

This will give you the core fonts, but if there are other TrueType fonts that you want installed, it is as easy as copying the font files to the ~/.fonts/ directory.

---

