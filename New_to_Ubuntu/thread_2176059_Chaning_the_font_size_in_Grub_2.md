---
title: "Chaning the font size in Grub 2"
date: 2013-09-22
forum: New to Ubuntu
---

### Post by ImTroyMiller on 2013-09-22
I'm not sure if this is the correct section of the forum, but I couldn't find a section for Grub.

Anyways, I'd like to make the font in Grub 2 a little bit bigger.  I have a large screen and the font size is really small.  I don't want to change the font style, or the color of the font, just the size of the font.  I also don't want to change my screen resolution because I've already set that.

---

### Post by oldfred on 2013-09-22
I thought you had to change screen resolution, but this also shows how to change font.

[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
> 
[h=3]Editing /etc/default/grub[/h] Now change the default line number, the timeout, the resolution of the GRUB2 screen and add the font. 
First, In terminal enter this command to generate the font: 
 
****
[B]sudo grub-mkfont --output=/boot/grub/DejaVuSansMono.pf2 \
 --size=24 /usr/share/fonts/truetype/ttf-dejavu/DejaVuSansMono.ttf[/B]

---

### Post by ImTroyMiller on 2013-09-22
I didn't see anything for just changing the size of the font.  It looks like that's all for changing the style of the font, and then changing the size.  I want to keep the same font that's comes stock with Grub 2.

---

### Post by Dennis N on 2013-09-22
> **ImTroyMiller said:**
> I didn't see anything for just changing the size of the font.  It looks like that's all for changing the style of the font, and then changing the size.  I want to keep the same font that's comes stock with Grub 2.

Edit the file **/etc/default/grub** in a text editor (requires use of sudo):

Uncomment the line (delete the # in front) 

[B]#GRUB_GFXMODE=640x480
[/B]
I then change the value to 800x600 for my HD monitor (1920x1080).

After editing and saving, you need to issue the command: **sudo update-grub** in the terminal. Next boot, your changes will take effect.

---

