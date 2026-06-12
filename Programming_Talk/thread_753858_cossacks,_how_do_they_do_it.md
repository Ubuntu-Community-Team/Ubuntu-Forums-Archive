---
title: "cossacks, how do they do it?"
date: 2008-04-13
forum: Programming Talk
---

### Post by A_B on 2008-04-13
Hi,

I have always been a fan of the Cossacks series, unfortunately, I can't get it to run on ubuntu :(

But that's not what I want to talk about right now, I'm here to talk about code :D

Cossacks uses 2d units, buildings, objects, ... But a 3D terrain. I just wonder how this is done.

here is how I think it is done (the red line, option A)
Assuming that Direct X works similar to openGL.


The point of view here is assumed to be top view (in the code, ofcourse the game gives the impression of a 45° view)

The 3d terrain would be placed at an angle to create the 45° view)

Sprites are rendered on quads which move over the 3D terrain, I assume in "path A" on my beautiful diagram.

Does anyone have a different view on this?

Thanks
Alex

PS: I don't have any intention of starting the development of a cossacks like game at all, please don't come with "you'll never be able to make such a program" because I know I can't.

** This is the right place to post such a question right?**

---

### Post by angustia on 2008-04-13
i've never seen that game but:

1- if the camera move around the map, but it always looks in the same direction (it never turns around some axis), i supose it's pretty simple to make the ground using a heightmap and rendering using tiles.

2- if the camera does turns around, the ground can be rendered using voxels ([http://en.wikipedia.org/wiki/Voxel]("http://en.wikipedia.org/wiki/Voxel")), the thing becomes more complicated for the sprites because animations will have to take account for many angles of views. You can see an example of this in the past century game Magic Carpet: [http://www.mobygames.com/game/dos/magic-carpet/screenshots/gameShotId,2292/]("http://www.mobygames.com/game/dos/magic-carpet/screenshots/gameShotId,2292/").


excuse my english

---

### Post by Can+~ on 2008-04-13
The terrain is really 3d? or is it isometric?

-If it is 3d, then you use opengl to render a 3d environment (probably a height map) and then put sprites over it as you said.

-If it is isometric, then any 2d library can do it, have a lot of tiles saved, and associated to a certain number (0...n) and go over an array and paste the corresponding tile on the corresponding place.

---

### Post by A_B on 2008-04-14
The terrain in cossacks is actually 3d, not an isometric image and the camera can not move around.

Well.. let his be the end of this short question. No need to waste your time with such an unnecessary  question.

Got an art exam to work on too.

Alex

---

### Post by P_Hansson on 2008-04-14
Units are sprites for sure.

As for how to render them, I assume it's just some fancy 3D into 2D projection thing which determines which angle should be displayed and perhaps scale them if camera projection is true perspective instead of orthogonal.

I can't go into the maths though, not my kind of cake.

---

### Post by Wybiral on 2008-04-14
If the camera cannot rotate, what's to stop it from being 2d? Do you remember sim-city, where you could raise and lower the terrain? But it was all isometric and technically 2d, it just looked 3d.

If you can move the camera around, then it could just be a heightmap with some billboarded sprites. But from the screenshots I've seen (having never played the game) it looks isometric to me.

---

### Post by P_Hansson on 2008-04-14
The view in Cossacks is isometric. But that's 3D terrain and 2D sprites working together. I know, I've used the level editor.

Sidenote: Most modern isometric view games are implemented with 3D terrain. The reason is it's easier to do hardware effects on 3D geometry than on an isometric bitmap.

---

### Post by Wybiral on 2008-04-17
> **P_Hansson said:**
> The view in Cossacks is isometric. But that's 3D terrain and 2D sprites working together. I know, I've used the level editor.

Sidenote: Most modern isometric view games are implemented with 3D terrain. The reason is it's easier to do hardware effects on 3D geometry than on an isometric bitmap.

Interesting... The last isometric game I played was Sim-City, so I'm probably not one to speak.

But in this case, using [billboarded]("http://www.lighthouse3d.com/opengl/billboarding/") sprites on a simple terrain seems to be the easiest way to go.

---

### Post by slavik on 2008-04-17
the terrain is 2D, I asked a person who works for the company (he made models in STALKER).

---

### Post by A_B on 2008-04-17
> **slavik said:**
> the terrain is 2D, I asked a person who works for the company (he made models in STALKER).

????  [http://www.cdv.de/editor/produkt_seiten/templates/cossacks.php?s=cossacks&l=e&gpp=1.%2BGeneral%2BQuestions&g=faq]("http://www.cdv.de/editor/produkt_seiten/templates/cossacks.php?s=cossacks&l=e&gpp=1.%2BGeneral%2BQuestions&g=faq")  ????

check out 2nd paragraph.

And if Cossacks EW isn't 3D, I bet Napoleonic wars is...

Alex

---

### Post by slavik on 2008-04-17
they might mean 3D in that there are bridges and such.

---

### Post by Wybiral on 2008-04-17
Without playing the game it's hard to say, but I will say that there are plenty of ways to make 2d "appear" to be 3d. Have you ever played the original [Resident Evil]("http://www.thejadedgamer.net/images/screens/psx/resident_evil_dc.jpg")? It may not strike you at first, but the backgrounds are actually just still shots and all of the moving elements are rendered over that picture. Using proper perspective tricks and collision detection, they can make it feel like it's 3d.

Some isometric games create the 3d effect using sloped tiles that can be applied in various layers ([sim city]("http://www.linuxjournal.com/files/linuxjournal.com/linuxjournal/articles/086/8630/8630f2.resized.png"), as I mentioned, is a good example... Not quite as impressive, but it is an old game).

---

### Post by {HWK}Michael on 2010-08-10
I am a modder of the GSC games. ( Cossacks 1 and 2, and the american conquest series) the units in these games are 2d images compiled in a program to cover 180 degrees of the 3d model. all the units start out as a 3d model in 3d max. there rendered at 9 angels ( 16 for cannon and the cannons in Cossacks 2 Napoleonic wars are 3d, becuase C2 uses a different engion then the original 3 cossacks) and compiled in a way the engine can read them. for more info on how the game runs or how to mod the game. theres a lovely website that im a Moderator on.
[http://cossacksworld.ucoz.co.uk/](http://cossacksworld.ucoz.co.uk/)

---

