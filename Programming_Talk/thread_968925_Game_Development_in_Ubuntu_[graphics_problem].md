---
title: "Game Development in Ubuntu [graphics problem]"
date: 2008-11-03
forum: Programming Talk
---

### Post by signal_ on 2008-11-03
Hi first post here.  I just installed Ubuntu today and I have much to learn.

Prior to using Ubuntu I used and still use WindowsXP.  **I also am writing a game in C++ using Code::Blocks as an IDE.  I am using SDL with OpenGL as the API.**

However, I have a huge problem.  When I compile and build the game project everything works fine.  I then run the game and the screen in 800x640 windowed mode and it **flickers/flashes when scrolling.**

My graphics card is an ATI Mobility Radeon X300 on an old laptop.  I went to System > Administration > Hardware Drivers and updated the drivers.  Still didn't work.

I then tried running my Windows build under Wine.  Still didn't work.

I also tried enabling/disabling VSYNC.  No go.

So I am at a loss.  I would like for my game to be able to be used by Ubuntu users and I would also like to develop on Ubuntu as well.  **Why does my game scroll so smoothly in Windows, but on Ubuntu it flashes/flickers???**

It seems like its got to be a driver/graphics card issue, right?  All the code is exactly the same as it is on Windows -- the whole cross platform thing and all.  Please help if you can.

Thanks in advance!

---

### Post by Ferrat on 2008-11-03
Are you sure you have activated the ATi drivers 

enter this in a terminal 
```

glxinfo | grep "direct"

```

you should get the response 
**direct rendering: Yes**

---

### Post by hessiess on 2008-11-03
sounds like a driver bug to me.
Firstly if you use compiz, try turning it off. If that dosent work manually update the drivers from ATI's site.

---

### Post by signal_ on 2008-11-03
Thanks for the replies guys.

Ferrat, I typed what you posted into the terminal and I received the afirmative: "direct rendering: Yes".

And, hessiess I do not know if I use compiz; I do not know what compiz is, so I will look into it.

One thing though: I was using the SDL function: SDL_WM_SetCaption(), once per frame; I was writing the frames per second (fps) to the window caption every second or so.  I disabled this and it at least stopped flashing every second.  Now it only flashes when I scroll the screen.

I am using Ubuntu 8.10.... so maybe it is an issue with the new release.  I have no idea, but I will keep searching.  Thanks guys!

EDIT: So, hessiess, I turned visual effects off (compiz) and it worked.  Thanks dude.  So now I can develop & play my game in Ubuntu.  

The thing that pissed me off about Windows was the virus scanner constantly sucking all the cpu when I'm in the middle of typing out some complex code and freezing the comp when I'm trying to work.  Hopefully with Ubuntu I can remain more calm.  Thanks again.

---

