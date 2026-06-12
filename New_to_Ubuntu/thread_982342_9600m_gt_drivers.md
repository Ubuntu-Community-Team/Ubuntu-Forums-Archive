---
title: "9600m gt drivers?"
date: 2008-11-14
forum: New to Ubuntu
---

### Post by UberMouse on 2008-11-14
OK so i just got Ubunto 8.10 yesterday since my vista partition crapped out
for some reason it just crashes every time it starts loading all the dlls.
but anyway i have a few problems with screen resolutions my screen can handle 1280x800 but i can only set it to 1024x768 and thats just to small for me. does anyone know how i can change it to 1280x800? im also not sure if i have my graphics card drivers intalled when i upgraded to 8.10 it came up with the drivers and i installed 177 but i have no way to test them since i cant get WINE working. any help there as well would be appreciated

Thanks

---

### Post by Bölvaður on 2008-11-14
> **UberMouse said:**
> OK so i just got Ubunto 8.10 yesterday since my vista partition crapped out
for some reason it just crashes every time it starts loading all the dlls.
but anyway i have a few problems with screen resolutions my screen can handle 1280x800 but i can only set it to 1024x768 and thats just to small for me. does anyone know how i can change it to 1280x800? im also not sure if i have my graphics card drivers intalled when i upgraded to 8.10 it came up with the drivers and i installed 177 but i have no way to test them since i cant get WINE working. any help there as well would be appreciated

Thanks

test it with type this into terminal: glxgears

```

bölvaður@Gorgeous:~$ glxgears
60319 frames in 5.0 seconds = 12063.747 FPS
62247 frames in 5.0 seconds = 12449.400 FPS
61200 frames in 5.0 seconds = 12239.946 FPS
61148 frames in 5.0 seconds = 12229.517 FPS
```

you should get fps more in tune with mine than 100.

---

### Post by UberMouse on 2008-11-15
> **Bölvaður said:**
> test it with type this into terminal: glxgears

```

bölvaður@Gorgeous:~$ glxgears
60319 frames in 5.0 seconds = 12063.747 FPS
62247 frames in 5.0 seconds = 12449.400 FPS
61200 frames in 5.0 seconds = 12239.946 FPS
61148 frames in 5.0 seconds = 12229.517 FPS
```

you should get fps more in tune with mine than 100.

ok so these are the results

12205 frames in 5.0 seconds = 2440.924 FPS
12473 frames in 5.0 seconds = 2494.505 FPS
12692 frames in 5.0 seconds = 2538.311 FPS
12772 frames in 5.0 seconds = 2554.352 FPS
12790 frames in 5.0 seconds = 2557.949 FPS

yours are a LOT better what graphics card do you have?
and im running the nvidia-glx-177-dev drivers from the synaptics package manager

---

