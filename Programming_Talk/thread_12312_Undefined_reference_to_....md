---
title: "Undefined reference to ..."
date: 2005-01-23
forum: Programming Talk
---

### Post by AcidTripp on 2005-01-23
Seeing as how the FCE Ultra project seems to be officially [dead](http://fceultra.sf.net), I've decided to make a code fork.
One of the goals of my fork is to try to slowly move over to a more object orientated approach to the code, which requires a port to C++.
I've gotten the port to compile all of the source files to objects, but during the linking process, I get a series of ": undefined reference to X" messages.

```
g++ -o nextra src/boards/8237.o src/boards/h2288.o src/boards/malee.o src/boards/novel.o src/boards/sachen.o src/boards/simple.o src/boards/super24.o src/boards/supervision.o src/input/arkanoid.o src/input/bworld.o src/input/cursor.o src/input/fkb.o src/input/ftrainer.o src/input/hypershot.o src/input/mahjong.o src/input/oekakids.o src/input/powerpad.o src/input/quiz.o src/input/shadow.o src/input/toprider.o src/input/zapper.o src/mappers/112.o src/mappers/113.o src/mappers/114.o src/mappers/117.o src/mappers/151.o src/mappers/15.o src/mappers/16.o src/mappers/17.o src/mappers/180.o src/mappers/182.o src/mappers/184.o src/mappers/187.o src/mappers/189.o src/mappers/18.o src/mappers/193.o src/mappers/200.o src/mappers/201.o src/mappers/202.o src/mappers/203.o src/mappers/208.o src/mappers/21.o src/mappers/225.o src/mappers/226.o src/mappers/227.o src/mappers/228.o src/mappers/229.o src/mappers/22.o src/mappers/230.o src/mappers/231.o src/mappers/232.o src/mappers/234.o src/mappers/235.o src/mappers/23.o src/mappers/240.o src/mappers/241.o src/mappers/242.o src/mappers/244.o src/mappers/246.o src/mappers/248.o src/mappers/24and26.o src/mappers/255.o src/mappers/25.o src/mappers/32.o src/mappers/33.o src/mappers/40.o src/mappers/41.o src/mappers/42.o src/mappers/43.o src/mappers/46.o src/mappers/50.o src/mappers/51.o src/mappers/57.o src/mappers/58.o src/mappers/59.o src/mappers/60.o src/mappers/61.o src/mappers/62.o src/mappers/65.o src/mappers/67.o src/mappers/68.o src/mappers/69.o src/mappers/6.o src/mappers/71.o src/mappers/72.o src/mappers/73.o src/mappers/75.o src/mappers/76.o src/mappers/77.o src/mappers/79.o src/mappers/80.o src/mappers/82.o src/mappers/83.o src/mappers/85.o src/mappers/86.o src/mappers/88.o src/mappers/89.o src/mappers/8.o src/mappers/91.o src/mappers/92.o src/mappers/95.o src/mappers/97.o src/mappers/99.o src/mappers/emu2413.o src/mappers/mmc2and4.o src/mappers/simple.o src/mbshare/164.o src/mbshare/90.o src/mbshare/deirom.o src/mbshare/mmc1.o src/mbshare/mmc3.o src/mbshare/mmc5.o src/mbshare/n106.o src/mbshare/tengen.o src/drivers/common/args.o src/drivers/common/cheat.o src/drivers/common/config.o src/drivers/common/hq2x.o src/drivers/common/hq3x.o src/drivers/common/scale2x.o src/drivers/common/scale3x.o src/drivers/common/scalebit.o src/drivers/common/vidblit.o src/drivers/pc/input.o src/drivers/pc/main.o src/drivers/pc/sdl.o src/drivers/pc/sdl-joystick.o src/drivers/pc/sdl-sound.o src/drivers/pc/sdl-throttle.o src/drivers/pc/sdl-video.o src/drivers/pc/unix-netplay.o src/cart.o src/cheat.o src/crc32.o src/debug.o src/endian.o src/fceu.o src/fceustr.o src/fds.o src/file.o src/filter.o src/general.o src/ines.o src/input.o src/md5.o src/memory.o src/movie.o src/netplay.o src/nsf.o src/palette.o src/ppu.o src/sound.o src/state.o src/unif.o src/unzip.o src/video.o src/vsuni.o src/wave.o src/x6502.o -L/usr/lib -lSDL -lpthread -lz
src/drivers/pc/main.o(.text+0x11e): In function `SaveConfig()':
: undefined reference to `SaveFCEUConfig'
src/drivers/pc/main.o(.text+0x17e): In function `LoadConfig()':
: undefined reference to `LoadFCEUConfig'
src/drivers/pc/main.o(.text+0x183): In function `LoadConfig()':
: undefined reference to `InputUserActiveFix()'
src/drivers/pc/main.o(.text+0x34d): In function `DoArgs(int, char**)':
: undefined reference to `ParseArguments'
src/drivers/pc/main.o(.text+0x569): In function `CloseGame':
: undefined reference to `InputUserActiveFix()'
src/drivers/pc/main.o(.text+0x74d): In function `DriverInitialize(FCEUGI*)':
: undefined reference to `InitOtherInput()'
src/drivers/pc/main.o(.text+0x5): In function `ParseGI(FCEUGI*)':
: undefined reference to `ParseGIInput(FCEUGI*)'
src/drivers/pc/main.o(.text+0x842): In function `FCEUD_Update(unsigned char*, int*, int)':
: undefined reference to `FCEUD_UpdateInput()'
collect2: ld returned 1 exit status

```

The weird thing is that these functions ARE defined in all of the files.
```
$ grep "SaveFCEUConfig" src/ -r
src/drivers/pc/main.cpp:        SaveFCEUConfig(tdir,fceuconfig);
Binary file src/drivers/pc/main.o matches <-- Object file looking for the function
src/drivers/common/config.cpp:void SaveFCEUConfig(char *filename, CFGSTRUCT *cfgst)
src/drivers/common/config.h:void SaveFCEUConfig(char *filename, CFGSTRUCT *cfgst);
Binary file src/drivers/common/config.o matches <-- Object file with the function
```
(repeat for every other undefined reference).
The code links fine as C code, but refuses to link with C++.
Anybody have experience in something like this?

---

### Post by AcidTripp on 2005-01-23
Ok, I know that I just posted this, but I already fixed it!
If anyone else has these problems, just include
```
extern "C" { 
         // FUNCTION
}
```
around the function definitions of the complaining functions.

Its funny how you can pull your hair out for hours, and then as soon as you ask for help, the solution falls into your hands.

---

### Post by anis152003 on 2011-11-29
hi. im having the same problem.. but how to include the code.. i don't get what u mean.. please explain to me.. tq

---

