---
title: "HOWTO: Counter Strike Source on Ubuntu"
date: 2004-11-16
forum: Outdated Tutorials &amp; Tips
---

### Post by cardador on 2004-11-16
Its pretty simple to play CS:Source on Ubuntu.

Assuming you have cedega and a fully updated css:

1- Go to css folder and do: chmod 777 * -R

2- Edit ~/.transgaming/config and add at the bottom
[AppDefaults\\hl2.exe\\Version]
"Windows" = "win2k"

3- Run css with:
cedega hl2.exe -steam -game cstrike -console

The game runs very smoothly, although some objects and the menus fonts are messed up.

Hope it helps!

Ubuntu Hoary
kernel 2.6.8
61.11 Nvidia drivers
P4 2.4
1024 ram
gforce4 ti4200 128

---

### Post by Crisp on 2004-11-16
[QUOTE=cardador]Its pretty simple to play CS:Source on Ubuntu.

Assuming you have cedega and a fully updated css:

1- Go to css folder and do: chmod 777 * -R

2- Edit ~/.transgaming/config and add at the bottom
[AppDefaults\\hl2.exe\\Version]
"Windows" = "win2k"

3- Run css with:
cedega hl2.exe -steam -game cstrike -console

The game runs very smoothly, although some objects and the menus fonts are messed up.

Hope it helps!

Ubuntu Hoary
kernel 2.6.8
61.11 Nvidia drivers
P4 2.4
1024 ram
gforce4 ti4200 128[/QUOTE]
 Nice.  Can you do the same with regular CS 1.6?

-Crisp

---

### Post by nehalem on 2004-11-16
Wow, I'm surprised.

If the source engine works for this, what about HL2?

---

### Post by cardador on 2004-11-16
[QUOTE=Crisp]Nice.  Can you do the same with regular CS 1.6?

-Crisp[/QUOTE]


I've read that 1.6 also works quite well on Linux.

---

### Post by cardador on 2004-11-16
[QUOTE=nehalem]Wow, I'm surprised.

If the source engine works for this, what about HL2?[/QUOTE]

I guess that if this works, and counter strike is a mod of HL2,  then HL2 should also work.

---

### Post by #Greg on 2004-11-16
HL2 has the same engine, so it should work.

I've also heard that some people have got CS 1 up and running, I managed to get HL working a bit, but it was far too unstable to play in reality.

Whats the fps like with this, I'm guessing it's not going to be the equivalent to windows, and CS:S isn't going to run at CS speeds, what specs are you running it with?

Also, could we get a couple shots of this?

---

### Post by cardador on 2004-11-16
[QUOTE=#Greg]HL2 has the same engine, so it should work.

I've also heard that some people have got CS 1 up and running, I managed to get HL working a bit, but it was far too unstable to play in reality.

Whats the fps like with this, I'm guessing it's not going to be the equivalent to windows, and CS:S isn't going to run at CS speeds, what specs are you running it with?

Also, could we get a couple shots of this?[/QUOTE]

I am getting around 40-50 fps, you can see my specs at my first post.

I have attached two screenshots (notice the strange fonts...).

---

### Post by plasmo on 2004-11-17
ive managed to get tfc and cs 1.6 up and running pretty smooth.
80-99 fps :D running on a gf4 mx420

---

### Post by HungSquirrel on 2004-11-18
> Assuming you have cedega and a fully updated css:
That's the kicker.  I used cedega to install Steam, and all went well until the Steam update reached 99%.  Then it crashed unexpectedly.  :(

---

### Post by FX on 2004-11-23
Ok here is some stupid questions after my statement. :)

One: I have steam working on here. Its a Toshiba Satellite Laptop with a 5100 Go 32 meg card. Is it worth to even try with the card I have?

Two: From what I understand you have to download both CS:Source and HL2 with Steam exactly how would I go about doing this?

Three: After downloading and installing (how do I install) how do I start the game? Do i have to start Steam with cedega first and then start the game with that or do I just start the game with the command that was given in the first post?

Sorry, but I've never really played any Steam/Valve games, much less in Linux.  :D

Thanks,

FX

---

### Post by FX on 2004-11-23
I keep getting this error....

WineDbg terminated on pid 1f

Any ideas?

FX

---

### Post by Beire on 2004-11-25
too bad cedega isn't free :'(

---

### Post by mdr on 2004-11-26
ahh but it is......CVS

---

### Post by Beire on 2005-03-03
[QUOTE=mdr]ahh but it is......CVS[/QUOTE]
 yeah but cedega cvs keeps giving me make errors

---

### Post by vassalle on 2005-03-06
hi guys.. just installed cs on my hoary.. played a bit but wasnt satisfied with the FPS im getting.. im getting like only 60fps where in windows im getting a solid 99 fps in CS 1.6.. one more thing though, theres no sound.. do i need to disable the server sound inorder to get sound under Cedega? Or should i change the config file..  Hope u gurus out there could help me.. ;)

---

### Post by r41d3r on 2008-07-25
I am using CrossOver and Counter Strike 1.6 working in my ubuntu HH 99,99%. :)

---

### Post by Coded.Symphony on 2009-01-05
[FONT="Century Gothic"]There are possibilities for Cedega to be free but only at times.. i think they do handouts in competitions.. etc[/FONT]

---

### Post by Johnkozz on 2009-05-14
Never do something for free, that you can get paid for...

---

