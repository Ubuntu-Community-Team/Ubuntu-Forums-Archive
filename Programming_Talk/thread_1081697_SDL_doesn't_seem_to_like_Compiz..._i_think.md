---
title: "SDL doesn't seem to like Compiz... i think"
date: 2009-02-26
forum: Programming Talk
---

### Post by MarcusCarabas on 2009-02-26
I've been using GNU/Linux (Ubuntu: Gutsy Gibbon) for just about a year now. These days I am teaching myself how to use SDL, and I 've run into the following problem:

I've this really simple program that loads a bitmap image into a SDL_Surface structure and draws it on the screen using SDL_BlitSurface and SDL_UpdateRect. 

When Compiz is NOT enabled. That is, " System | Preferences | Appearance -> "Visual Effects" is set to "None" ", my program works as expected. It throws up a little rectangular window with a black background and displays the bmp image inside the window. 

However, with Compiz enabled, that is "Visual Effects" is set to "Custom" ("Trail Focus" and translucent menus are some of the effects that become enabled) my program does not run as expected. There is no crash and no errors are displayed, but instead of showing the bmp image like it did before it simply throws up a white rectangular window with nothing in it. The size of the window is the same as before.

I've searched for this problem (and solutions to it) on-line but haven't found anything suitable. I did come across posts describing similar problems but no real solutions were given.

So, does anyone here have any idea what could be going on? Is this an issue with Compiz or SDL or me or just my particular hardware/software combination? Is there any way to get around this? Ideally I would like my SDL code to work the same regardless of the " System | Preferences | Appearance -> Visual Effects" settings.

Any help would be greatly appreciated :)

merci
marcus carabas

---

### Post by Can+~ on 2009-02-26
Could you upload the file to see if I get the same results? (Running with ATI's fglrx)

Oh, and as a temporary solution, you can add two icons to your desktop:

To turn off compiz fusion:
```
metacity --replace
```

To turn it on:
```
compiz --replace
```

---

### Post by MarcusCarabas on 2009-02-28
Hey thanks for responding ... I tried out your suggestion and yes when Compiz is turned off the program behaves as it should. However, the problem remains that with Compiz turned on my program does not display what it is supposed to. 

For the time being I have found a temprary solution. Turns out that if I pass SDL_FULLSCREEN to SDL_SetVideoMode then the program displays everything as expected. This is not the best solution because ideally I would like to be able to work with whatever video mode (and screen size) I want. Still, for the purpose of teaching myself how to use SDL the existing solution is enough.

Anyway, if you are curious and would like to try playing around with the code I have attached it as a text file. Mind this is very very basic and simple code... nothing fancy or breath-taking or creative ...


Thanks again :)
MarcusCarabas

---

### Post by hessiess on 2009-02-28
> This is not the best solution because ideally I would like to be able to work with whatever video mode (and screen size) I want.

Sorry about the shameless plug, but this is essentially why I wrote Quad-Ren, to enable easy development of 2D applications which will run regardless of screen size. Though as it uses SDL as a back-end, so may be effected by the issue you are describing.

---

