---
title: "OpenGL Running at lightspeed - why ??"
date: 2006-01-05
forum: Programming Talk
---

### Post by kudu on 2006-01-05
I'm having trouble with OpenGL example programs running at lightspeed. My triangles are whizzing around at warp factor 8, should be sedately rotating at a nice leisurely pace showing off in all their glory.

I'd like to know why it's so damn fast and how I can fix it ? My card seems to be working correctly, games run fine etc.

Thanks!

---

### Post by Lord Illidan on 2006-01-05
You should be pleased that they run so fast... hehe
You are using glxgears, I presume.

Run it like this :
```
glxgears -printfps
```

---

### Post by kudu on 2006-01-05
I'm not referring to glxgears. Gears are running slowly at a cool 12225 fps!

I'm talking about compiling and running OpenGL apps, like the classic "Triangle" spinning sample app. The triangle should spin slowly around its axis, but it's not. It's zipping around in a blur about a million miles an hour.

I want to know if it's my hardware or software causing this anomoly ? How do you control spin rate ?

Never had it spinning so damn fast before. :)

kudu...out

---

### Post by Retrix on 2006-01-05
You can either sleep for a small period of time after drawing a frame, or decrease the delta - the amount you rotate the scene by.

---

### Post by Lord Illidan on 2006-01-05
If you have made the programs yourself, than it could be that you need to implement a wait function.

Interesting, that your glxgears is so high, though. What are your system specs?

---

### Post by fct on 2006-01-05
It's normal that programs using basic functions run that fast. That's why most game programmers put an FPS limit in their code so when played years later in much faster hardware it won't be unplayable.

Old games didn't do that and the result is that you had to use speed limitters in your 486 when playing games developed for 8086 processors.

---

### Post by kudu on 2006-01-05
[QUOTE=Lord Illidan]If you have made the programs yourself, than it could be that you need to implement a wait function.

Interesting, that your glxgears is so high, though. What are your system specs?[/QUOTE]

2.26 GHz CPU, 512MB RAM, GeForce 6800 GT video card. Nothing cutting edge.

When I run the same example code on the same machine in Windows it runs correctly.

Very interesting!

---

### Post by Lagiv on 2006-01-05
[QUOTE=kudu]When I run the same example code on the same machine in Windows it runs correctly.[/QUOTE]
Maybe you have Vsync activated in Windows, so it's synced to your monitor refresh rate.

---

### Post by fct on 2006-01-06
If that's the case, install nvidia-settings, run it, and check "Sync to VBlank" on the OpenGL Settings option.

---

### Post by kudu on 2006-01-07
[QUOTE=fct]If that's the case, install nvidia-settings, run it, and check "Sync to VBlank" on the OpenGL Settings option.[/QUOTE]


That did it, thanks very much to both you vsync fellows. Cool!

---

