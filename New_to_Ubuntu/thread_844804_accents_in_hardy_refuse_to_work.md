---
title: "accents in hardy refuse to work"
date: 2008-06-29
forum: New to Ubuntu
---

### Post by clickypens on 2008-06-29
I just installed Hardy in English, however I live in Mexico (I know more about computers in english than spanish, hence). After installing all my favorite programs and files and setting it up just like I like it, I decided to get the accents working. First, I tried changing the keyboard layout. That at least gave me Ñ. But, the accents don't do right. I changed the xorg.conf file to allow for the international variant of the US keyboard, I even made a compose key.
However, it still comes out seperate: ´a

Is there any way I can get accents to work without reinstalling Hardy in Spanish. And saying I do that, can I keep my files?

---

### Post by clickypens on 2008-06-29
I realize it's probably too quick to be replying to my own thread, and that this is completely unrelated, but also on the login splash screen, the fonts are huge. Like, where it says Options or Name and Password are all fine. But when I enter my name, it's in (at least) 72 font. Or when I click options, I can't even really read what it says.
Anyway I can change this?

---

### Post by Matthewslf on 2008-06-29
I forget the details, but if you use XIM instead of gnome keyboard input, you can set custom keybindings. I used it to make typing in French more convenient. However you will have to change a lot of settings. Before that, check the bindings tables at [https://help.ubuntu.com/community/GtkComposeTable]("https://help.ubuntu.com/community/GtkComposeTable") and read [https://help.ubuntu.com/community/ComposeKey]("https://help.ubuntu.com/community/ComposeKey"). You should also be able to install a spanish locale

check system>one of the two>login manager for settings
otherwise /etc/gdm.conf (not sure it has settings for that)

---

### Post by clickypens on 2008-06-29
and how do I change to XIM?

also, I looked for a boot screen changer and couldn't find it, but found Language Support. Excited, I changed it to Spanish...and accented characters are still unsupported.

---

### Post by agave on 2008-08-07
I am having the same problem with a spanish laptop keyboard. Instalation was Spanish, so I do not think it has anything to do with the instalation language. ´a´e´i´o´u is what I get. Changing layout has absolutly no effect.

I have found several post with the same problem, but no direct solution. Is this not a bug?

---

