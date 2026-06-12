---
title: "My first game (bricker)"
date: 2008-10-26
forum: Programming Talk
---

### Post by Gulyan on 2008-10-26
Hello,
I've just finished my first game (bricker). If you have time to play it please tell me what do you think about it. :popcorn:
I hope I can make it the best that I can and maybe get it included in the Ubuntu repository. :lolflag:

The project page can be found at [https://launchpad.net/bricker]("https://launchpad.net/bricker")

A simple way to install it is to add the following lines to the repository
deb [http://ppa.launchpad.net/gulyan89/ubuntu](http://ppa.launchpad.net/gulyan89/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/gulyan89/ubuntu](http://ppa.launchpad.net/gulyan89/ubuntu) hardy main

then you can find it in synaptic or you can use:
```
 sudo apt-get install bricker
```

---

### Post by DrMelon on 2008-10-26
Sweet, it's like an offline version of Bloxors.

---

### Post by Gulyan on 2008-10-26
yes, similar but different
other levels (26 so far) and the rules are not identical at the "bridge"

---

### Post by Tony Flury on 2008-10-26
Excellent work - well done - now to get a walkthrough :-)

---

### Post by NovaAesa on 2008-10-26
I'm at uni right now, so I can't use apt-get. It's not compiling well for me either, using 'make' doesn't seem to be working. I might try it when I get home from uni tonight.

---

### Post by abeisgreat on 2008-10-26
Looks pretty sweet Ill have to try this.

EDIT: Fun game, pretty slick, menus could use some work. and a falling animation would be nice. Plus I dont reallt dig the concept of cloning anothers game, try to be original ;) otherwise its fun

---

### Post by Gulyan on 2008-10-27
Thx for all the suggestions :)

NovaAesa, the reason make is not working is probably because it depends on libsdl1.2-dev and libsdl-image1.2-dev for building.

I'll definitely work on the menus.
As for improvements, I plan to add a few sounds, 4 more levels (at least), some information text so you know on which level you are and how many moves you've made and I'll try to make the falling animation.

---

### Post by NovaAesa on 2008-10-27
Wow, very impressive (installed from the repo). I'm stuck though... you will have me here all night :P

---

### Post by sheto on 2008-10-27
Cool game. Could you teach me to program such stuff?

---

### Post by newbuntuxx on 2008-10-27
well done..the game is really nice. 

suggestions: at the moment, you can not resize the game platform (actual gui window) perhaps you should add that in future updates.

---

### Post by lukjad on 2008-10-27
I'm gonna have to try it!

---

### Post by jyaan on 2008-10-27
this is a great game, and a nice contribution to ubuntu. overall, the presentation is very good as well. there is only one thing i can think of for improvement; that would be another graphics mode (openGL; you probably know it's fairly easy to integrate with SDL anyways) with lots of flashy effects for better video cards. good work. i'm looking forward to see what you'll produce next. :)

jyaan

---

### Post by Gulyan on 2008-10-27
Thanks for the suggestion, I've heard that you can use open GL with SDL but I was to afraid to try it. :lolflag:
Originally I searched the net for open gl tutorials and that's how I got so SDL.
I'll definitely try to integrate it now because SDL lacks some features: rotation, alpha for transparent png etc.

This was my first attempt and I know there's room for improvements. :)

---

### Post by Tony Flury on 2008-10-27
a suggestion would be an system where by other users could easily build and submit new puzzles, and maybe a grading system for levels (Easy, Medium, Insomiac).

Also maybe a scoring system - moves taken vs minimum needed.

These though are minor points, for a first effort it is very very good.

---

### Post by Gulyan on 2008-10-27
The build your own level idea is great. Thx a lot.
Now you can build your own levels by editing the files in /usr/games/bricker/levels but the next version will have a level builder integrated with drag and drop features :KS
Thx again for this great idea

---

