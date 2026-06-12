---
title: "Turn off sounds"
date: 2013-03-07
forum: New to Ubuntu
---

### Post by heroquestelf on 2013-03-07
Okay, here's an absolute beginner's question. I'm currently running Ubuntu 12.04 LTS on my Acer Aspire 3613 Laptop. 

Every time it boots into Ubuntu, as it prompts me for my password it makes the most irritating sound, and for the life of me I can't figure out how to turn it off. 

I have tried going to Dash Home and opening the "Sound" tab. From there I made the assumption that the next step would be to open up the "sound effects" tab. I have tried changing the alert sound to one of the other sounds in the menu, but it doesn't work. 

It also has a volume control to turn down and possibly mute the alert sounds.

Mind you, it's not that I have a problem with my computer making an alert sound. I don't necessarily want to disable the alert sound... I'd just like to change it to something a little more pleasant.

---

### Post by katriel on 2013-03-08
Hey! Is this what you're looking for? [http://askubuntu.com/questions/138760/how-do-i-change-the-start-up-sound](http://askubuntu.com/questions/138760/how-do-i-change-the-start-up-sound)

---

### Post by siddharth007 on 2013-03-08
If you don't want to go the terminal way and want to do it in clicks go for **Ubuntu Tweaks **application.You can customoize the entire look and feel of your Ubuntu apart from want you want to do right now.You can download it [here]("http://ubuntu-tweak.com").Its a .deb package(912kb). For app review visit this link: [Ubuntu tweak review]("http://bluesteel007india.blogspot.com/2013/03/tweak-your-ubuntu-with-this-smart-tool.html")

---

### Post by heroquestelf on 2013-03-08
Okay, here's the problem I'm having. When I try to use the terminal commands to move the file (and actually my problem was not with the "desktop-login.ogg" file, it was the "system-ready.ogg" file) I was able to convert the old "system-ready.ogg" to "system-ready.ogg.old", but when I try and replace the file, I get "cp: missing destination file operand after '/home/Jonathan/Home/system-ready.ogg'. For the record, I used the command "sudo cp ~/Home/system-ready.ogg", as the *NEW* system-ready.ogg file I want to use is in my "Home" directory.

I have also tried just copying and pasting the file into the /usr/share/sounds/ubuntu/stereo directory, but it tells me that I do not have permission.

I also tried installing the  "Ubuntu tweaks" utility that you pointed me to, and I could not get it to help me either. I found the command area where I could turn the sounds OFF... but I don't want to do that. I want the sounds, I just want to **CHANGE** them.

Also, for the record, the minute I change "system-ready.ogg" to "system-ready.ogg.old", it almost IMMEDIATELY re-creates ANOTHER system-ready.ogg file and I'm back to square one.

**SOLVED!!**

I used the "gksu nautilus" command to open up the shell and cut and paste. Once I did that it gave me permission. File changed!!

---

