---
title: "[fluxbuntu] wrong keybord settings"
date: 2008-05-26
forum: New to Ubuntu
---

### Post by mic5zz on 2008-05-26
Hello,

I've just installed fluxbuntu.

During the installation, i didn't get question about keyboard.
The only question i get was about languages. So as french speacker i selected french and and now symbols like ! $ ... are at the wrong places.

In /etc/X11/xorg.conf i have changed "fr" by "be" for the line "XkbLayout" and saved. But I solved nothing.

How should i do to redefine my keyboard?

---

### Post by mic5zz on 2008-05-28
Hello,

I did the following ..

edit **/etc/X11/xorg.conf** and add a language shortcut for the keyboard line:
**Option      "XkbLayout"   "fr,[COLOR="Red"]be[/COLOR]**"

And to have keyboard switch:
Edit **/home/<myusername>/.fluxbox/menu**
And adding following lines:
[B][submenu] (Keyboards)
      [exec]   (fr) {setxkbmap fr}
      [exec]   (be) {setxkbmap be}[
[end][/B]

_Conclusion:_ 
I not happy of the result because i have to switch manually the keyboard to 'be' at each restart.
**How can i do to redefine my keyboard settings ?**

---

