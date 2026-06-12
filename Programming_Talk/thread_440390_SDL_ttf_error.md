---
title: "SDL_ttf error"
date: 2007-05-11
forum: Programming Talk
---

### Post by Corlyn on 2007-05-11
Almost finished writing a small tic-tac-toe game for a school-project. Writing it in C++ using the SDL- and SDL_ttf-libraries. I'm trying to output some text on the middle of the screen, but when I try to use the RenderText-function it just crashes. I'm new to Linux in general and I ain't quite sure what the problem is since I've never seen it windows. Tried to find a solution but the only thing I could find was to update my libraries, but they are up to date.

```

SDL_Surface *message=NULL;
if(!(message=TTF_RenderText_Solid(font,"Cross is the winner!",textColor)))
{
	cout<<TTF_GetError()<<endl;
}

```
returns:
```

Failed loading DPMSDisable: /usr/lib/libX11.so.6: undefined symbol: DPMSDisable

```

---

### Post by Classic_gamer on 2007-05-29
I'm getting the same error. Please someone help.

---

### Post by moma on 2007-05-30
A hint seen on the web:
That error is probably related to freetype ( [http://freetype.org](http://freetype.org) ) package. 
Download freetype-2.3.4.tar.gz from  [http://download.savannah.gnu.org/releases/freetype/](http://download.savannah.gnu.org/releases/freetype/)
./configure;  make;  sudo make install 
it.

Of course, it's not ideal to mix tar.gz source and .deb packages !

One possibility is to borrow a newer package from Gutsy Gibbon, but unfortunately it seems to have an old package as well.  See: [http://packages.ubuntu.com/gutsy/libdevel/libfreetype6-dev](http://packages.ubuntu.com/gutsy/libdevel/libfreetype6-dev)
Someone should report this to Gutsy's developers. They must update it.  Maybe it is a GNOME issue?

Motivation: [http://zonaforo.meristation.com/foros/viewtopic.php?p=8209047&sid=0646d6a9bc78f7a0391e6ff254bbb819&m=1](http://zonaforo.meristation.com/foros/viewtopic.php?p=8209047&sid=0646d6a9bc78f7a0391e6ff254bbb819&m=1)
I can compile und run the example code (on the above link) without errors on Feisty 7.04. It ran ok before I updated to freetype-2.3.4.  Requires packages: libsdl1.2-dev,  libsdl-ttf2.0-dev.

---

### Post by the_darkside_986 on 2007-06-06
I am having the same trouble on Ubuntu 7.04 trying to use SDL_ttf libraries. The function TTF_RenderText_Blended works but not *_Solid. It gives that error. I tried installing the freetype234 tar ball source package but it still does it.

---

### Post by the_darkside_986 on 2007-07-05
Any news on the status of this bug? Will it be fixed in 7.10 because I cannot figure out how to fix it in Ubuntu 7.04. If i try to install an alternate libfreetype deb package it will cause an error with synaptic. And building and installing freetype tar ball packages doesn't help at all.

---

### Post by leibowitz on 2007-07-05
Please try with the attached example.

Download, extract, cd to the SDLTTF directory.


```
make
./sdltext
```

Press any key to exit.


Note: you need both libsdl1.2-dev and libsdl-ttf2.0-dev package to compile this little example.

---

### Post by the_darkside_986 on 2007-07-05
It simply terminates without printing an error after quickly showing a small black screen, but if I change the TTF_RenderText_Solid to *Blended it stays open and prints a white text message.

I've tried installing different tar balls of freetype but none of them help. I found an older deb package of libfreetype but if I install it, the software index gets broken and I get the update notification from synaptic.

---

### Post by leibowitz on 2007-07-06
Seems to be a bug in the package provided in Feisty.

You should check the bugs.launchpad.net

Here's a related one:
[https://bugs.launchpad.net/ubuntu/+source/sdl-ttf2.0/+bug/93445](https://bugs.launchpad.net/ubuntu/+source/sdl-ttf2.0/+bug/93445)

I found this from the bug report:
[http://lists.libsdl.org/pipermail/sdl-libsdl.org/2006-November/058787.html](http://lists.libsdl.org/pipermail/sdl-libsdl.org/2006-November/058787.html)

So, like everyone said earlier here it seems to be related to freetype, not SDL.

Can you try to edit the main.c file in the package and replace "Hello World" with "Hello" and see if it crashs again.

---

### Post by the_darkside_986 on 2007-07-07
I've called that function without spaces in the strings and it doesn't crash.  I hope they fix it by the next Ubuntu release. I plan on upgrading directly from Feisty to G. via net instead of discs.

---

### Post by leibowitz on 2007-07-07
It's already fixed upstream.

What you have to do basicly is update the freetype package by hand.

It shouldn't be that hard.

---

### Post by the_darkside_986 on 2007-07-07
> 
It's already fixed upstream.

What you have to do basicly is update the freetype package by hand.

It shouldn't be that hard.


What exactly is the command for that? The synaptic notification icon isn't showing up after I did sudo apt-get update. And sudo apt-get install libfreetype6 simply prints a message saying that the package is already the newest one. I've tried building source packages of freetype but it is obviously not the exact same thing as libfreetype and has no effect when I install it.

---

### Post by AlexThomson_NZ on 2007-07-08
I just found this bug yesterday too (having spaces in the text causes *_solid to fail).

You can write a wrapper around the function to handle spaces as a work around until it's fixed.

---

### Post by the_darkside_986 on 2007-07-08
That's ok. I'll just use *_Blended until I try to compile it on a non-broken platform such as my g/f's PC, which runs PC-BSD. I'm still trying to get openGL installed on it. It is a real challenge to install stuff on that system without having an internet connection in her house.

---

### Post by leibowitz on 2007-07-10
By downloading this file (freetype2.2.1)

[http://sourceforge.net/project/downloading.php?group_id=3157&use_mirror=mesh&filename=freetype-2.2.1.tar.bz2&31144193](http://sourceforge.net/project/downloading.php?group_id=3157&use_mirror=mesh&filename=freetype-2.2.1.tar.bz2&31144193)

Applying this patch:
[http://cvs.savannah.gnu.org/viewvc/freetype/freetype2/src/base/ftutil.c?r1=1.22&r2=1.23](http://cvs.savannah.gnu.org/viewvc/freetype/freetype2/src/base/ftutil.c?r1=1.22&r2=1.23)

Then compiling the software (./configure, make, make install)

Then call any program with LD_LIBRARY_PATH=/usr/local/lib 

You can see it's working fine.


Note that if you download a newer version of freetype it would be already fixed (no patch needed).

I think the best way for you to update this is to inform the freetype ubuntu package maintainer of the situation, and point to him the way to fix this issue.

Then he would probably throw an update to the servers so any user could update their freetype package to the fixed version without compiling anything.

---

### Post by vexorian on 2007-07-10
I think this is pretty strange, the other day I wanted to implement SDL_ttf to my program and I simply installed the dev package for SDL_ttf and everything compiled through SDL_config, I am using feisty 7.04 anyone knows how frequent this bug is ?

---

