---
title: "[SOLVED] keyboad layout changing after reboot"
date: 2008-05-11
forum: New to Ubuntu
---

### Post by Irishpolyglot on 2008-05-11
Hello!

I've got a strange problem; every time I reboot Ubuntu my keyboard layout changes. I have a Spanish keyboard, but it keeps defaulting to American or some other similar layout (slash key etc. changes position and ñ and accents disappear). When I go to Keyboard in Preferences there's no mention of any other layouts, and yet if I click ANY option in all the keyboard tabs and unclick it (so I'm not changing anything), in OKing that box it somehow cancels whatever is causing the change and I suddenly get back to my Spanish layout.

This has been happening ever since I repartitioned my drive from the Live CD. But it may be related to updates. The only other thing I can remember doing that could be related is installing lots of new programs including the KDE control module keyboard layout, but once again that only has Spanish in it.
Thanks for any advice!! :)

---

### Post by Irishpolyglot on 2008-06-07
I still have this problem... any suggestions?

---

### Post by rrofes on 2008-06-10
I have exactly the same problem... I did not find any solution yet...

---

### Post by audunpoi on 2008-06-17
I also have this problem. I have a Norwegian keyboard that changes to US after reboot. The Norwegian is marked as default all the time, even when not active.

---

### Post by TeoBigusGeekus on 2008-06-17
[http://ubuntuforums.org/showthread.php?t=798555]("http://ubuntuforums.org/showthread.php?t=798555")

---

### Post by Irishpolyglot on 2008-06-17
That's solved the problem! To summarise the post linked (which actually tackles a couple of problems simultaneoulsy), it's a known bug in the Hardy installation. Just type ```
sudo gedit /etc/X11/xorg.conf
``` and somewhere (probably near the beginning) you will see a line ```
Option		"XkbLayout"	"us"
``` and just change *us* to your two letter language code (*es* in the case of Spanish for example). After saving the file and rebooting, the problem will be gone.
Thanks for the link! Also good to implement that handy shortcut outlined in the problem there if I want to quickly switch layouts for those unfamiliar with the Spanish keyboard.

---

