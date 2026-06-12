---
title: "trouble with games"
date: 2008-10-15
forum: New to Ubuntu
---

### Post by Spekke on 2008-10-15
Hey

I'm a newbie at linux, and I have the following problem

I'm using ubuntu (I think 8.04)
I have an ATI asus A9550GE and installed the drivers for the card using the hardware drivers install program on ubuntu.
openGL is installed

So far, I have downloaded 2 games on my comp
-one is 'Counter-strike: Source' (wich I installed with wine, after I installed steam)
-the other one is a free game that can run on linux, 'Teeworld'

When I start CS:S I see the menu background for a second and then the screen turns black and starts to flicker.

When I start teeworld I am able to play the game but I have the same flickering

I looked at the flickering and it's not that it goes on/off but it's like alt+tab is pressed rapidly. The problem with CS:S with the screen turning black will propably be another error.

I tried solving by changing the refresh rate, I also tried playing windowed, none of both worked.

Anyone who has a solution or something that might help?
(could it be my ATI driver?)

greetings Spekke

---

### Post by pyromanic123boom on 2008-10-15
If you have any compiz-related cube effects etc., enabled, it can do this with you graphics card.

Happened to me in some fullscreen games and I just disabled compiz entirely.

---

### Post by TheLions on 2008-10-15
can you play videos without flickering?

if you cant then it is driver problem, try installing drivers over EnvyNG

---

### Post by Spekke on 2008-10-15
errm, what's compiz? :p

ps: I can watch movies (with VLC) without the flickering

---

### Post by pyromanic123boom on 2008-10-15
Compiz is that fancy cube related desktop candy with the fire and everything. If you go to youtube you can see videos of it...but I guess that's not your problem then.

If you can play videos with no flickering, it might be a screen resolutioin on your system or game. TRy going to System-->Preferences-->Screen Resolution and tinkering with that. Or try ediding the screen szie in your game smaller, and settings quality lower. If nothing works, just play the game in a large window mode? It all sounds like a graphics card issue.

---

### Post by Gutt on 2008-10-15
It's a common problem with ATI cards.

If turning compiz off doesn't work, sometimes changing Windows Manager does (did for me, when I was under Gnome all the games kept of flicker, when I changed session and logged under KDE, games worked fine.).

---

### Post by TheLions on 2008-10-15
> **Spekke said:**
> errm, what's compiz? :p

ps: I can watch movies (with VLC) without the flickering

to turn off compiz System-->Settings-->appearance-->visual effects

---

### Post by Spekke on 2008-10-15
thanks for all the quick answers, I'll try it all and then post if it worked

but still thanks alot! :D

**edit: just changed that compiz thing, and it worked!!! Now I'll try to fix the trouble with steam and CS:S (I'll install more steam games and see what they do) Thanks again for the help:D**

---

### Post by tjwoosta on 2008-10-15
i also get the same flickering when compiz is enabled
(it only happens when the application has opengl video output)

i have intel gm965 graphics

i have found a solution 

beofore starting the problematic application you should temporarily disable compiz

to do that press alt-f2 and enter this
```
metacity --replace
```
(its important to use alt-f2 rather then a terminal)

now you can play your game or whatever you were doing,

after playing the game, or using google earth, or whatever you can re-enable compiz like this

```
compiz --replace
```
(again its important to use alt-f2 instead of the terminal)

if you have troubles with videos flickering in your media players (like with mplayer) you can always edit the config file and change the default video output to X11

---

### Post by jerome1232 on 2008-10-15
A much better way of turning off compiz temporarily is to use fusion-icon

```
sudo apt-get install fusion-icon
```

It puts a little icon in your tray that allows you to switch between metacity and compiz. And more.

---

### Post by Spekke on 2008-10-15
I think I'll just stick with the "no visual effects" :P
but I might change my mind later, so thanks

---

