---
title: "Games slow/don't work on Xubuntu"
date: 2008-08-18
forum: New to Ubuntu
---

### Post by huu on 2008-08-18
I had Win 2000 on that computer before I installed Xubuntu. This is my first time to use Linux. 

The only games that work perfectly are those Gnome games, which came with the OS. Downloaded Linux games show colourful flickering screen after opening and play sound, that's all. Windows games which worked perfectly under Win 2000 are now very slow and/or have some small graphical problems (blinking cursor, ...).
Also, the whole OS is a little bit slower than Windows 2000 used to be.
Yes, I have checked that Xubuntu has recognized my video card driver. I also looked that the command "glxinfo|grep direct" says "direct rendering: Yes".

Computer's technical information: 130 MB RAM; ca 30 GB HDD; Intel graphic card with 4 MB video RAM (=D); Pentium III.

I'd be very grateful if someone could help me with this problem.
And sorry about my English, it's not my native language.

---

### Post by huu on 2008-08-18
Anyone knows any solution? Sorry about double-post, I just want some attention.

---

### Post by Thelasko on 2008-08-18
Two questions:

[LIST=1]
[*]Where did you get the Linux games you downloaded?

[*]How are you running your Windows 2000 Games?
[/LIST]
If you are running Wine, [please read this.]("http://ubuntuforums.org/showthread.php?t=497332")

---

### Post by Glw8z on 2008-08-19
What if it's the old Intel card that's not working in Linux, as was the case w/ me. My glxinfo also showed *direct rendering: yes*, yet glxgears and screensavers w/ 3D failed to work. 

Solution: ditch the card, find another (even old w/o much RAM) that supports 3D etc. 

Sorry I can't provide any technical help or point out any thread w/ answers. Good luck.

---

### Post by Perfect Storm on 2008-08-19
> **Glw8z said:**
> What if it's the old Intel card that's not working in Linux, as was the case w/ me. My glxinfo also showed *direct rendering: yes*, yet glxgears and screensavers w/ 3D failed to work. 

Solution: ditch the card, find another (even old w/o much RAM) that supports 3D etc. 

Sorry I can't provide any technical help or point out any thread w/ answers. Good luck.

+1

If you're trying to game with an intel card = forget it.

---

### Post by alienexplorers on 2008-08-19
Go out and get a cheap nvidia graphics card such as the fx5200 or fx5500.  Both are real cheap and work good with all games.

---

### Post by Thelasko on 2008-08-19
> **Artificial Intelligence said:**
> +1

If you're trying to game with an intel card = forget it.

In what version?  Intel cards have come a long way.  Although I must admit, I'm not a gamer.

---

### Post by Perfect Storm on 2008-08-19
> **Thelasko said:**
> In what version?  Intel cards have come a long way.  Although I must admit, I'm not a gamer.

All versions. If you want to 2D gaming no problem. But if you want 3D gaming then it's a ney. Intel cards are not build for gaming. Even in Windows where the intel driver is better than linux.

---

### Post by snowpine on 2008-08-19
Xubuntu is a modern OS, and your computer just barely meets its minimum system requirements. Windows 2000 is 8 years old. It's not really fair to compare the performance; of course W2000 will be faster and lighter on system resources! 

You might have better performance with a distro like Puppy or DSL that is specifically designed for older hardware. Also, some of the other posters have good advice about your video card. Good luck!

---

### Post by linuxguymarshall on 2008-08-19
An intel card with 4 mb of memory. :lolflag:

I will reccomend a NVIDIA 6200 if you are on a budget.

---

### Post by huu on 2008-08-20
Thanks a lot for your answers! 
I can use three (or even four) newer computers than that old one, so i wouldn't like to waste money on better video card.

I think I should really try another distro. Which one do you recommend? Is DSL good idea or is it too difficult to handle for newbie like me? 

(I wondered what DSL could stand for - digital subscriber line? Lol, no. =D)

---

### Post by huu on 2008-08-20
Don't ignore me, please. =)

---

### Post by linuxguymarshall on 2008-08-20
DSL = Damn Small Linux and for gaming, no. If you are a basic Linux user you should use Ubuntu

---

### Post by huu on 2008-08-20
I don't need "gaming". I just want some basic 2-D games to run normally on my computer (Red Alert 2). But even the Linux 2-D games
like SuperTux or those breakout games won't work. 

Thanks for the help anyway.

---

### Post by Thelasko on 2008-08-20
> **huu said:**
> I don't need "gaming". I just want some basic 2-D games to run normally on my computer (Red Alert 2). But even the Linux 2-D games
like SuperTux or those breakout games won't work. 

Thanks for the help anyway.

What do they do?  If you go to the terminal and enter "supertux" or "LBreakout2" what is the output?

---

### Post by LowSky on 2008-08-20
> **huu said:**
> Computer's technical information: 130 MB RAM; ca 30 GB HDD; Intel graphic card with 4 MB video RAM (=D); Pentium III.
 
The best answer I can give is to go back to Win2000

And How are you guys telling him to get a new video card?
A new Video card probably wont do much on a system that old. Not to mention you need to find a AGP or a PCI card which few manufacturers even make anymore.

The amount of RAM is really the first issue to deal with, 130 (which makes no sence to me, I'm thinking its really 128) is too little. You really need at least 256MB to work with a Ubuntu based distro. And if you want to play games, you should double that. I know computer hardware isn't cheap, but you got to pay to play.

---

### Post by huu on 2008-08-21
Sorry, I even hadn't installed SuperTux. I had SuperTux2 and it showed me some weird colours and ****. I installed Supertux now and it works perfectly.

Back to Win2000? -.- No way. And I don't have the installation CD.

---

