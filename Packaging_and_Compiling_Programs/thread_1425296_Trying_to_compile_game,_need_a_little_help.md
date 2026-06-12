---
title: "Trying to compile game, need a little help"
date: 2010-03-08
forum: Packaging and Compiling Programs
---

### Post by aviedw on 2010-03-08
Hi i got this program from one of the editors at [www.linuxformat.com](www.linuxformat.com). He has a small write up in search of beta testers. I decided to become one. I also wanted to sharpen my skills with compiling code. Here is the link if you want to try it out. [www.tuxradar.com/files/brainparty/brainparty003.tar.gz](www.tuxradar.com/files/brainparty/brainparty003.tar.gz) 

> 

I've ported my iPhone game, Brain Party, to Linux. It's now stable enough that I'm looking for a handful of testers able to give it a whirl and help find bugs. So, if you a) know what SDL/OpenGL are, b) are happy compiling stuff from source, and c) have 30 minutes to spare, please drop me a line at [email]paul.hudson@futurenet.com[/email] and I'll set you up.


I tried to compile the program but i didn't work for me. I cd to the folder and typed make and it went through this process

> avied@avied-desktop:~/Downloads/brainparty$ make
g++ -g -c -Wno-deprecated `sdl-config --cflags` -I/usr/X11R6/include -o balloonblaster.o balloonblaster.cpp
g++ -g -c -Wno-deprecated `sdl-config --cflags` -I/usr/X11R6/include -o BGObject.o BGObject.cpp
g++ -g -c -Wno-deprecated `sdl-config --cflags` -I/usr/X11R6/include -o bombhunt.o bombhunt.cpp
g++ -g -c -Wno-deprecated `sdl-config --cflags` -I/usr/X11R6/include -o BPGame.o BPGame.cpp
g++ -g -c -Wno-deprecated `sdl-config --cflags` -I/usr/X11R6/include -o BPPoint.o BPPoint.cpp
g++ -g -c -Wno-deprecated `sdl-config --cflags` -I/usr/X11R6/include -o bpsays.o bpsays.cpp
g++ -g -c -Wno-deprecated `sdl-config --cflags` -I/usr/X11R6/include -o bubbletrouble.o bubbletrouble.cpp
g++ -g -c -Wno-deprecated `sdl-config --cflags` -I/usr/X11R6/include -o cardmatch.o cardmatch.cpp
g++ -g -c -Wno-deprecated `sdl-config --cflags` -I/usr/X11R6/include -o Colour.o Colour.cpp
g++ -g -c -Wno-deprecated `sdl-config --cflags` -I/usr/X11R6/include -o connex.o connex.cpp
g++ -g -c -Wno-deprecated `sdl-config --cflags` -I/usr/X11R6/include -o cupsnballs.o cupsnballs.cpp
g++ -g -c -Wno-deprecated `sdl-config --cflags` -I/usr/X11R6/include -o diceoff.o diceoff.cpp
g++ -g -c -Wno-deprecated `sdl-config --cflags` -I/usr/X11R6/include -o flashcounting.o flashcounting.cpp
g++ -g -c -Wno-deprecated `sdl-config --cflags` -I/usr/X11R6/include -o flashlight.o flashlight.cpp
g++ -g -c -Wno-deprecated `sdl-config --cflags` -I/usr/X11R6/include -o iqtest.o iqtest.cpp
g++ -g -c -Wno-deprecated `sdl-config --cflags` -I/usr/X11R6/include -o jewelflip.o jewelflip.cpp
g++ -g -c -Wno-deprecated `sdl-config --cflags` -I/usr/X11R6/include -o jeweljam.o jeweljam.cpp
g++ -g -c -Wno-deprecated `sdl-config --cflags` -I/usr/X11R6/include -o main.o main.cpp
g++ -g -c -Wno-deprecated `sdl-config --cflags` -I/usr/X11R6/include -o marbledrop.o marbledrop.cpp
g++ -g -c -Wno-deprecated `sdl-config --cflags` -I/usr/X11R6/include -o memoryblox.o memoryblox.cpp
g++ -g -c -Wno-deprecated `sdl-config --cflags` -I/usr/X11R6/include -o memorybox.o memorybox.cpp
g++ -g -c -Wno-deprecated `sdl-config --cflags` -I/usr/X11R6/include -o memorymaths.o memorymaths.cpp
g++ -g -c -Wno-deprecated `sdl-config --cflags` -I/usr/X11R6/include -o MessageBox.o MessageBox.cpp
g++ -g -c -Wno-deprecated `sdl-config --cflags` -I/usr/X11R6/include -o minesweep.o minesweep.cpp
g++ -g -c -Wno-deprecated `sdl-config --cflags` -I/usr/X11R6/include -o Minigame.o Minigame.cpp
g++ -g -c -Wno-deprecated `sdl-config --cflags` -I/usr/X11R6/include -o moonjump.o moonjump.cpp
g++ -g -c -Wno-deprecated `sdl-config --cflags` -I/usr/X11R6/include -o nextinline.o nextinline.cpp
g++ -g -c -Wno-deprecated `sdl-config --cflags` -I/usr/X11R6/include -o numbersnake.o numbersnake.cpp
g++ -g -c -Wno-deprecated `sdl-config --cflags` -I/usr/X11R6/include -o oddoneout.o oddoneout.cpp
g++ -g -c -Wno-deprecated `sdl-config --cflags` -I/usr/X11R6/include -o patchmatch.o patchmatch.cpp
g++ -g -c -Wno-deprecated `sdl-config --cflags` -I/usr/X11R6/include -o perfectpaths.o perfectpaths.cpp
g++ -g -c -Wno-deprecated `sdl-config --cflags` -I/usr/X11R6/include -o Rectangle.o Rectangle.cpp
g++ -g -c -Wno-deprecated `sdl-config --cflags` -I/usr/X11R6/include -o routefinder.o routefinder.cpp
g++ -g -c -Wno-deprecated `sdl-config --cflags` -I/usr/X11R6/include -o rps.o rps.cpp
g++ -g -c -Wno-deprecated `sdl-config --cflags` -I/usr/X11R6/include -o scrambled.o scrambled.cpp
g++ -g -c -Wno-deprecated `sdl-config --cflags` -I/usr/X11R6/include -o setfinder.o setfinder.cpp
g++ -g -c -Wno-deprecated `sdl-config --cflags` -I/usr/X11R6/include -o sharpshooter.o sharpshooter.cpp
g++ -g -c -Wno-deprecated `sdl-config --cflags` -I/usr/X11R6/include -o shortcircuitsudoku.o shortcircuitsudoku.cpp
g++ -g -c -Wno-deprecated `sdl-config --cflags` -I/usr/X11R6/include -o shufflepuzzler.o shufflepuzzler.cpp
g++ -g -c -Wno-deprecated `sdl-config --cflags` -I/usr/X11R6/include -o SpriteFont.o SpriteFont.cpp
g++ -g -c -Wno-deprecated `sdl-config --cflags` -I/usr/X11R6/include -o strangerdanger.o strangerdanger.cpp
g++ -g -c -Wno-deprecated `sdl-config --cflags` -I/usr/X11R6/include -o symboliclogic.o symboliclogic.cpp
g++ -g -c -Wno-deprecated `sdl-config --cflags` -I/usr/X11R6/include -o Texture.o Texture.cpp
g++ -g -c -Wno-deprecated `sdl-config --cflags` -I/usr/X11R6/include -o underthehat.o underthehat.cpp
g++ -g -c -Wno-deprecated `sdl-config --cflags` -I/usr/X11R6/include -o untangler.o untangler.cpp
g++ -g -c -Wno-deprecated `sdl-config --cflags` -I/usr/X11R6/include -o wordsmash.o wordsmash.cpp
g++ -o brainparty `sdl-config --cflags` -I/usr/X11R6/include `sdl-config --libs` -lGL -lGLU -lSDL_mixer -lSDL_ttf -lSDL_gfx -lSDL_image   balloonblaster.o BGObject.o bombhunt.o BPGame.o BPPoint.o bpsays.o bubbletrouble.o cardmatch.o Colour.o connex.o cupsnballs.o diceoff.o flashcounting.o flashlight.o iqtest.o jewelflip.o jeweljam.o main.o marbledrop.o memoryblox.o memorybox.o memorymaths.o MessageBox.o minesweep.o Minigame.o moonjump.o nextinline.o numbersnake.o oddoneout.o patchmatch.o perfectpaths.o Rectangle.o routefinder.o rps.o scrambled.o setfinder.o sharpshooter.o shortcircuitsudoku.o shufflepuzzler.o SpriteFont.o strangerdanger.o symboliclogic.o Texture.o underthehat.o untangler.o wordsmash.o


If anybody can help me understand this i would really help it thanks.

---

### Post by mc4man on 2010-03-08
At your source dir. prompt run
```
./brainparty
```

---

### Post by alienjon on 2010-03-08
Looks like it compiled fine.  Should just need to run the binary now (or ./brainparty, as mc4man points out)

---

### Post by aviedw on 2010-03-08
Is there anyway to create an icon for it so i can prompt it from the desktop

---

