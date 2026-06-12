---
title: "Making an aimbot for fps games with OpenCV, possible?"
date: 2008-11-16
forum: Programming Talk
---

### Post by crazyfuturamanoob on 2008-11-16
I just got an insane idea, aimbot which works like this:
[list]
[*]1. Start a first person shooter game
[*]2. Have a screencapture software taking screenshots while playing
[*]3. Let OpenCV analyze the screenshots, and locate targets
[*]4. Send mouse move / aiming commands to the game, to aim the targets.
[/list]
That would probably use a lot cpu time and wouldn't work as well as usual aimbots, not for serious cheating. 
But idea just sounds so funny I had to post this. Don't get me wrong, I'm not into cheating.

So OpenCV (Open Computer Vision) is a library, which can analyze pictures/video
and recognize shapes, background, gestures, motion.

---

### Post by Quikee on 2008-11-16
> **crazyfuturamanoob said:**
> I just got an insane idea, aimbot which works like this:
[list]
[*]1. Start a first person shooter game
[*]2. Have a screencapture software taking screenshots while playing
[*]3. Let OpenCV analyze the screenshots, and locate targets
[*]4. Send mouse move / aiming commands to the game, to aim the targets.
[/list]
That would probably use a lot cpu time and wouldn't work as well as usual aimbots, not for serious cheating. 
But idea just sounds so funny I had to post this. Don't get me wrong, I'm not into cheating.

Next step.. exchange the game with a web camera and mouse with a camera mounted paint ball gun with motor functions. :)

---

### Post by jimi_hendrix on 2008-11-16
probably easier just to get the player coords from the game and tell the aim bot to aim and shoot

---

### Post by crazyfuturamanoob on 2008-11-16
> **jimi_hendrix said:**
> probably easier just to get the player coords from the game and tell the aim bot to aim and shoot

That would be boring & lame. Probably all cheaters do that.

---

### Post by Phenax on 2008-11-16
> **crazyfuturamanoob said:**
> That would be boring & lame. Probably all cheaters do that.

Justifiably, it would take a whole lot less code and is a whole lot more accurate.

---

### Post by skullmunky on 2008-11-22
Sure, probably possible.

If you used a game w/o a moving camera (like duck hunt instead of doom) then just basic blob tracking does it, because anything that moves is a target.

That's not a useful cheat but it could be a good new media artwork.

If it could work as well with a video camera that might be better. 

For the installation maybe put the CPU on a stool in front of the table with the game on it.

Let me know if you make this, I'll pass on some festivals and media art mailing lists to watch for opportunities to submit it to.

i know that sounds like a joke, so check out [URL="http://www.eddostern.com/fort_paladin.html"]Eddo Stern's "Fort Paladin"
[/URL] which is a computer sculpture that plays "America's Army".

---

### Post by slavik on 2008-11-22
> **crazyfuturamanoob said:**
> I just got an insane idea, aimbot which works like this:
[list]
[*]1. Start a first person shooter game
[*]2. Have a screencapture software taking screenshots while playing
[*]3. Let OpenCV analyze the screenshots, and locate targets
[*]4. Send mouse move / aiming commands to the game, to aim the targets.
[/list]
That would probably use a lot cpu time and wouldn't work as well as usual aimbots, not for serious cheating. 
But idea just sounds so funny I had to post this. Don't get me wrong, I'm not into cheating.

So OpenCV (Open Computer Vision) is a library, which can analyze pictures/video
and recognize shapes, background, gestures, motion.
actually, this wouldn't be cheating. this would actually be an interesting research project.

I would recommend making the system that plays the game a completely different system than the one which actually runs the game client.

This way, you could build a robot that pwns everyone in Counter-Strike (or your choice of FPS).

---

### Post by Tpsycrit on 2009-04-26
> **slavik said:**
> actually, this wouldn't be cheating. this would actually be an interesting research project.
 
I would recommend making the system that plays the game a completely different system than the one which actually runs the game client.
 
This way, you could build a robot that pwns everyone in Counter-Strike (or your choice of FPS).
 
so basicly ur just throwin in a computer

---

### Post by Sprut1 on 2009-04-27
I made a pixelbot for 2d games in visual basic.net - it captured output of an firefox window (web game) and scanned for different colors and such, worked pretty well.

What you are trying is probably a bit harder to make, I don't think this will be any effective in 3d games at all.

---

### Post by Kilon on 2009-04-27
> **crazyfuturamanoob said:**
> 
[list]

[*]2. Have a screencapture software taking screenshots while playing


you should avoid this as this alone could eat up your CPU. What you could do instead is develop an algorithm for searching for picture (like color of armor , etc) patterns for identifying the targets/enemies while the game is playing .  


Of course that would require that you look at the enemy, which mean that you will have not only control the shooting and walking but also the looking / turning mechanics of the game.

---

