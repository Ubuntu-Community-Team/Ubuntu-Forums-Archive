---
title: "Having trouble with fonts..."
date: 2008-05-25
forum: New to Ubuntu
---

### Post by arcarsenal on 2008-05-25
Just installed Ubuntu today and I've been kind of navigating my way through it. I've figured out most of what I've needed to in order to get this thing setup to my liking but some of the pages I'm viewing on FireFox have some hideous looking sans serif type fonts. I installed the mscorefonts package and it changed some portions of sites, but I know the general appearance isn't what it should be. 

Am I doing something wrong? I read through as many other posts related to this topic as I could, but the stuff I've tried has not made much of a difference. I'm also having trouble with commands in the "Run" prompt. Either nothing happens or if I go to the terminal, it doesn't let me type my password when I'm prompted to. The only key on the board that works there is "Enter".. which results in an error for incorrect password (obviously, because I can't type it!). 

Any help would be GREATLY appreciated. I basically just want the websites to be displayed with the correct fonts. I know what I'm looking at right now is not the way it should be. I'm completely new to this so my apologies in advance if any of this is redundant. 

Thanks!

---

### Post by sayakb on 2008-05-25
At the terminal, when you type your password, no text is displayed. So just type the correct password (ie. dont expect * to come) and press Enter. Also, if you want extra fonts, copy Windows fonts to a flash drive or something. Copy the fonts to /usr/share/fonts/truetype/MyFonts (create the folder MyFonts)

---

### Post by arcarsenal on 2008-05-25
> **LinuxIsInnovation said:**
> At the terminal, when you type your password, no text is displayed. So just type the correct password (ie. dont expect * to come) and press Enter. Also, if you want extra fonts, copy Windows fonts to a flash drive or something. Copy the fonts to /usr/share/fonts/truetype/MyFonts (create the folder MyFonts)

Ah, thanks! That helped. 

My font sizes still look a bit funky, though. I dropped that .txt file into the home directory and re-named it .font.conf to get the smoother fonts and I also went back to FireFox 2.0. It made a difference but things still seem to be a little out of whack. 

For example... where I'm typing right now, the font is a small grey-ish Times New Roman and everything else (FireFox tabs, Web Addresses, Toolbar text) seems to be a boldish looking Tahoma. It just kind of looks strange or unnatural. Anyone know if I'm missing something?

---

