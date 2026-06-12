---
title: "Height Mapping"
date: 2007-12-30
forum: Programming Talk
---

### Post by Lster on 2007-12-30
Hi again everyone :)

Well, I have been noticing that when I walk over terrain in my game engine it is a little bit bumpy. The code I have at the moment to compute the height at any given point is probably incorrect. I have searched and found many other people seem to have had similar issues but I still can't fix mine.

Edit: See Wybirals and Klips post on how to do it!

Can anyone give me a hint about what is wrong with that? I imagine it must be very simple. :)

Thanks,
Lster

---

### Post by Wybiral on 2007-12-30
It looks like your function is interpolating it between three points, am I correct? If that's the case, then that would explain it.

What you need to do is interpolate between two sides, then interpolate between those values.

Here's the current "cell" (the four surrounding height point samples)
```

A--B
|..|
|..|
C--D

```

For instance:
i1 = interpolate between A and B using x offset
i2 = interpolate between C and D using x offset
height = interpolate between i1 and i2 using y offset

I don't think I articulated this very well, so let me know if this makes sense.

EDIT:

It should basically look like this:
```

i1 = A * (1.0-dx) + B * dx
i2 = C * (1.0-dx) + D * dx
height = i1 * (1.0 - dy) + i2 * dy

```

---

### Post by Lster on 2007-12-30
Thanks for your quick reply! :)

I think I get what your saying. Unfortunately, that is even jerkier while walking.

---

### Post by Wybiral on 2007-12-30
Hmm, that should work. You might want to replace the cast to "int" with "floor" (from math.h) to ensure that no funny business goes on when dropping the decimals. If you post tit or send it to me I can play with it a bit and see if I can figure it out. But the above is what I usually use and it should interpolate nice and smooth ([here]("http://ubuntuforums.org/showpost.php?p=3048198&postcount=15")'s an example, look in "terrainlib.c" at the bottom).

---

### Post by Klipt on 2007-12-30
Try replacing

```
    float Top = DX * Terrain3 + ( 1.0F - DX ) * Terrain4;
    float Bottom = DX * Terrain1 + ( 1.0F - DX ) * Terrain2;
```
with
```
    float Top = DX * Terrain4 + ( 1.0F - DX ) * Terrain3;
    float Bottom = DX * Terrain2 + ( 1.0F - DX ) * Terrain1;
```

---

### Post by Lster on 2007-12-30
I changed the method to use floor instead but the problem still persists. Is there a possibility that this is something to do with my height map?

Very nice firework show by the way. :)

As for posting my project, I can but it is rather large! Also that function is the only relative part...

---

### Post by DavidBell on 2007-12-30
I think Wybiral is correct suggesting the four points. But apart from the error marked by Klipt, there is also a problem of your terrain being facetted. So the four point interpolation will be smooth beteen points but as you cross the line into the next indexed area in either direction there will be a sudden change of direction.

One way around it is to do similar interpolation but with first order bezier curves, done in two dimensions makes a bezier surface. If your calculate bezier surfaces using the central points of four ajoining facets plus the contained vertex as the peak, then the beziers will fit together for perfectly smooth terraine.

Sorry you have google bezier, I don't feel like doing it right now. But they are not hard and don't take much more calculation than interpolation.

HTH DB

**EDIT** You can also calculate a Terrain_Midpoints array to save a bit of calculation **END**

---

### Post by Lster on 2007-12-30
[QUOTE=Klipt]Try replacing


```
    float Top = DX * Terrain3 + ( 1.0F - DX ) * Terrain4;
    float Bottom = DX * Terrain1 + ( 1.0F - DX ) * Terrain2;
```

with

```
    float Top = DX * Terrain4 + ( 1.0F - DX ) * Terrain3;
    float Bottom = DX * Terrain2 + ( 1.0F - DX ) * Terrain1;
```

[/QUOTE]

Good call! That works perfectly now! Can you explain why?

---

### Post by Lster on 2007-12-30
As for Beizers, I will research them tomorrow!

---

### Post by Klipt on 2007-12-30
It's easier to check these things if you draw it out, but basically as dx increased (moving right) you gave more weight to the point with lower floor(x) (the left point), making your interpolated lines mirror images of what they should've been. E.g. 

```
/
 /
  /
```instead of```
\
 \
  \
```
Hence the bumpiness. ;)

As DavidBell points out, linear interpolation can still have sudden changes in slope, but it shouldn't have sudden changes in height.

---

### Post by Lster on 2007-12-30
[QUOTE=Klipt]As DavidBell points out, linear interpolation can still have sudden changes in slope, but it shouldn't have sudden changes in height.[/QUOTE]

They aren't really noticeable on my height map. If I look hard I can see slight ups and downs.

---

### Post by Wybiral on 2007-12-30
I'm curious to see what it's like now. If you ever have the time, you should post it somewhere!

---

### Post by Lster on 2007-12-30
The code or a screenshot? I'd be happy to either way...

---

### Post by Wybiral on 2007-12-30
You're writing a game engine right? What all do you have done for it? I'm definitely interested in giving it a test run.

---

### Post by Lster on 2007-12-31
I am planning on showing it in a month or two - it is very far from finished. Here's it's current feature list if your interested:

[LIST]
[*]Truly huge levels (by using a polygon reduction algorithm for my height map)
[*]Full network support for 2 players (more later, possibly) over internet or LAN
[*]Ambient, diffusive and speculare lighting and transparency
[*]Full multithreaded support for any number of CPUs (although there isn't much benefit with more than 2)
[*]3D sound using OpenAL supporting spatialized sound, Doppler effects etc...
[*]Fast dynamic shadows
[*]Supports both 32 and 64 bit machines and is very easily ported (just recompile)
[*]Font system
[*]Up to 4x Antialising
[/LIST]

Still to do:
[LIST]
[*]Object loading from different formats
[*]Largely destructible environments
[*]Game modes (such as "capture the flag" or "one shot, one kill")
[*]Reflections and possibly per pixel lighting
[*]Optimization - a lot of it (when I started using my terrain vertex reduction algorithm I increased the idle time between each frame from 250 to 750ms!)
[*]So much more work needs doing
[*]Testing!
[/LIST]

What that looks live right now is rather boring however:

---

### Post by Lster on 2007-12-31
Forgot some others!

[LIST]
[*]Motion blurring (and tinting)
[*]Distance fog (non volumetric)
[/LIST]

And some others to implement:

[LIST]
[*]Volumetric fog ;)
[*]Particle system (half done already)
[/LIST]

---

### Post by Lster on 2007-12-31
[QUOTE=Wybiral]I'm definitely interested in giving it a test run.[/QUOTE]

You'd be welcome to beta test it sometime (not quite ready for that stage yet but it shouldn't be too long). When I have got it reasonably stable I can post it - perhaps you would review the code for me then?

---

