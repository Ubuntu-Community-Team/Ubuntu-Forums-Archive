---
title: "GDB + Allegro + C++ == blue screen of death"
date: 2010-04-06
forum: Programming Talk
---

### Post by gnometorule on 2010-04-06
Here is a problem I have so far unsuccessfully posted on the (otherwise good) allegro forum. Maybe someone here has any ideas. I am told that gdb should work with the allegro library, but so far, I could not get it to work - see below. If I need to compile differently, kindly write how to in a completely idiot-proof way. :) Many thanks in advance for feedback. 

Here are the precise specs of what I do:

- Ubuntu 9.10
- using gcc/gdb as provided by package 'build-essential' 11.4 (which should be the most recent one distributed using synaptic)
- gcc and gdb are default configured, except (of course) I increased space allocable to core dumps (which defaults to 0kb). debugs normal C++ code fine.
- using allegro under 'liballegro4.2-dev', plus whatever was dependency installed with it (again, most current under synaptic)
- example program used is the following from a tutorial at this address:
[http://www.cppgameprogramming.com/cgi/nav.cgi?page=pong](http://www.cppgameprogramming.com/cgi/nav.cgi?page=pong) 
(only change: program forgets to set 'install_timer();' which I added in main)

I compile with 
g++ -g pong.cpp `allegro-config --static` -o pong

Result:
- no compilation errors
- program runs fine

I enter

gdb -q pong

gdb starts normally. I then use these gdb commands (as I normally do):
li
break 150 (random line in 'main()'))
run

Result: linux version of the blue screen of death (which I had never seen prior to this). Same when I compile any C++ code using allegro library writing to screen.

Ideas? Do i need to compile differently? Change anything in any config file? (if yes, which one and where would it usually be)

---

### Post by gnometorule on 2010-04-06
Well I did get a reply there saying (quoting):

"
If you compile allegro (instead) with
 '$./configure --enable-debug'

then use

`allegro-config --debug`
"
(the you should be fine).

I understand (?) the second part (use option 'allegro-config - debug' instead of 'allegro-config --static' (??)), but what would 'compile allegro with ...' mean? Allegro is installed already. Very confused here, and kind helper did not elaborate after I asked him to. Maybe someone can just make sense of this for me, and that solves the issue.

---

### Post by GeoMX on 2010-04-07
It means you have to download Allegro source code and compile yourself, creating the debug version of the code.

I worked with Allegro some time ago but under Windows, I used to work with dynamic libraries and had  both: debug and no debug versions of the DLLs. I think the Ubuntu repositories do not include the debugging version of the library, but you'll have to confirm it.

If you can't find the debugging version in the repositories or as a prebuild package on another place, you'll have to compile it. So, download Allegro source code, uncompress it and run

./configure --enable-debug
make
make install

I'm not really sure it will solve your problems as I haven't done any gdb debugging with Allegro programs (haven't done any Allegro programming for a while), but sounds like the way to go.

---

### Post by gnometorule on 2010-04-07
Thank you very much. You are right, the standard synaptic dev package does not install the debug version of allegro and one would have to do what you say if one wanted the debug version

However, I've been playing with this many hours yesterday and the day before, and now probably resolved my issues. For anyone in the future googling/forum searching this, here are some comments on what worked for me.

(1) My main issues went away upon changing in my programs

set_gfx_mode(GFX_AUTODETECT, ..., ..., ..., ...) into
set_gfx_mode(GFX_AUTODETECT_WINDOWED, ..., ..., ..., ...)

The apparent blue screen of death goes away, for the (now) obvious reason. This may be clear for experienced allegro coders and that's why no one mentioned it; but it's very confusing when you start out. Or at least it confused me.

(2) Even w/o linking to a debug library, and after using (1), allegro and gdb seem to coexist happily. Compile as usual

g++ -g (name).cpp -o (name) `allegro-config --static` (or --dynamic)

This implicitly compiles using the release (as opposed to debug) library version. However, even this release library allowed gdb to backtrace into the allegro library functions, not only my own. 

What I couldn't get to work was to have allegro execute one line, then see this line produced on the separate window called in set_gfx_mode. The separate window updates later (not yet totally clear if always only at program end). But that's secondary. Will close this thread now. Thanks again.

---

