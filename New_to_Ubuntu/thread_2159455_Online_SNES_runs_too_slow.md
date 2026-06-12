---
title: "Online SNES runs too slow"
date: 2013-07-03
forum: New to Ubuntu
---

### Post by art1ll3ry on 2013-07-03
I'm going to start by saying that I am PC (windows) competent, and that's about it. I switched to linux/ubuntu because I've always been interested in it and when I opened up the new windows on this laptop that I bought, I almost turned right around and returned it. So that's how I got here, and I'm stubborn, so I have no intention of running back to windows just because this is difficult for me.... on to the point

     I love Earthbound. If you haven't played it, then do so now; it's from the Super Nintendo. I use a site called snesbox.com. When I go to play it on here, for a brief instant before it starts to load, I see an error message, but it disappears before I can read it and the game loads. It runs slower than I can deal with. When I go to open a menu there is a delay first between the key press and the menu opening, and then between the menu opening and the sound of it opening. I don't know anywhere near enough to understand why. I've googled what I can guess that I need to google, and I think that it has something to do with flash. That's only a guess though because I have no idea what I'm doing. If there is already a post addressing this, please just direct me to it, and I'll try to figure it out from there. If not then any information, direction, or advice will be greatly appreciated. I also have no idea what kind of system information someone would need to help me, so please just tell me what info is needed to diagnose/troubleshoot, and I will gladly provide it.

     Thank you in advance for anything that anyone can do to help.

---

### Post by Dozy Van on 2013-07-03
As I am unsure on what excatly is the problem I would just download an [Snes Emulator]("http://linuxgamingtoday.wordpress.com/2008/01/26/how-to-install-emulators-on-ubuntu-snes-edition/") and work from there.



I would doubt it but it may be that your flash is outdated as you said

I would go to: [https://www.mozilla.org/en-US/plugincheck/](https://www.mozilla.org/en-US/plugincheck/)


and if your flashplayer is out dated click update now

---

### Post by art1ll3ry on 2013-07-03
Well, it does say that it's outdated. I click update, and from there I used to get the option to run, but now I only have the option to open or save. I've always had the install wizzard to take care of anything past that, so I don't actually know what to do with the file.

---

### Post by art1ll3ry on 2013-07-03
I also don't know which one I need. There are three options; tar.gz, YUM, and rpm.

---

### Post by art1ll3ry on 2013-07-03
Ok. So I found a thread on here about updating flash, and it said to put the .so file into usr/lib/mozilla/plugins but when I go to extract the file to it, it tells me that I don't have the right permissions...

---

### Post by art1ll3ry on 2013-07-03
Ok... So apparnetly, changing permissions isn't as easy as checking or unchecking read-only like on windows if that's even an accurate comparison. This looks like it might take me a while to figure out... again, any direction or advice is more than welcome.

---

### Post by Dozy Van on 2013-07-04
sorry not been online till now. If you can you need to move it via the terminal. 

**sudo mv /home/file location/**<name of file here> **/home/ where you need to move it to**

---

### Post by art1ll3ry on 2013-07-05
[FONT=georgia]    Well, I turned around and just installed ZSNES, but that froze after about a half hour. I've tried both copying and pasting the file as well as moving it by the terminal. Both ways tell me that I don't have permission to put it in the file that it needs to go to... I'm just gonna give it a rest for a while, try to learn some more about the system. Once I have some more knowledge, maybe I'll be able to figure it out. Thanks for all of the advice.[/FONT]

---

