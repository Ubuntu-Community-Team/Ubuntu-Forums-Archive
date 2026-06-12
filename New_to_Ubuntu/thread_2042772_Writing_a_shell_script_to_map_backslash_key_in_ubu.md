---
title: "Writing a shell script to map backslash key in ubuntu12.04"
date: 2012-08-15
forum: New to Ubuntu
---

### Post by akira87 on 2012-08-15
Hi, 

I am new to linux. I just installed linux on my laptop and whenever I tried to type a backslash key, '>' appears instead. I once came across a post that guided me to write a shell script using xmodmap -e "keycode 94 = backslash bar". However, I am unable to make that script to run automatically when I start the OS. Can anyone please guide me how to do so? Thanks lot. 

This is the current script that I once saw online:
touch fix_keyboard.sh
chmod +x fix_keyboard.sh
nano fix_keyboard.sh
type in = xmodmap -e "keycode 94 = backslash bar"

---

### Post by spjackson on 2012-08-15
Although it should be possible to manually remap keys like this, I don't think it is the best way, unless you are doing it to learn how.

It sounds like you have the wrong keyboard mappings installed - e.g. US when you have, say, a UK keyboard. You get to select the keyboard in the installation process. The best thing to do is to install the right keyboard map.

From the Dash, select System Settings, then Keyboard, then click on the Layout Settings link. Click the + to add a new layout. Pick the right one, and make it the default.

---

### Post by akira87 on 2012-09-01
Thx for the quick reply. I have tried several US layouts but my laptop model was not found on the list. Is there a way to use the system settings or terminal? 

And yes, I am trying to learn how to use the shall script setup. Can you kindly quide me thru the steps? Thanks.

---

