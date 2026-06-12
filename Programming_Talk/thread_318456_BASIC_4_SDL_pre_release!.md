---
title: "BASIC 4 SDL pre release!"
date: 2006-12-14
forum: Programming Talk
---

### Post by Wybiral on 2006-12-14
Ok, this is a derived work from Tom Mulgrews Basic4GL. A number of the commands are different to allow for an easier integration for linux. SDL is used for most of the windows functions so it should be pretty portable. Credit goes to Tom Mulgrew for writing the most of the original source code, and to Jon Snape for his working getting it to compile in linux. This project isn't complete, but the source and executable included in this package are fully functional. If you have any feature requests please send them my way!

Here is a link: [http://p13.wikispaces.com/space/showimage/b4sdl.tar.gz](http://p13.wikispaces.com/space/showimage/b4sdl.tar.gz)

The BASIC source files have the extension ".gb" and I threw in a few examples plus some of the textures that came with the original Basic4GL.

You execute the source files from the command line using "./b4sdl program.gb"

You will need OpenGL installed!

As I said, feature request and bug reports will be very welcome. Thanks!

-Davy

Screenshots:
[http://p13.wikispaces.com/space/showimage/b4sdl001.png](http://p13.wikispaces.com/space/showimage/b4sdl001.png)
[http://p13.wikispaces.com/space/showimage/b4sdl002.png](http://p13.wikispaces.com/space/showimage/b4sdl002.png)

Temporary home page:
[http://p13.wikispaces.com/B4SDL](http://p13.wikispaces.com/B4SDL)

---

### Post by Wybiral on 2006-12-14
Well, it seems the file in/out isn't working but I'll have it up in the next release.

---

### Post by Mickeysofine1972 on 2006-12-14
thats excellent!

Mike

---

### Post by Wybiral on 2006-12-16
Ok, Basic4SDL's file in/out has been fixed. I've also added another example program (it loads a terrain from a data file and a texture and lets you walk/drive around on it). To run it, simply unpack the archive, open the folder in the terminal and type "./b4sdl terrain.gb"

I will soon start work on embedding the VM and the compiled opcodes into an executable so that Basic4SDL can produce stand-alone executable files instead of having to run from the interpreter.

The source is also included with the package and has a makefile setup to help anyone who wants to work on it themselves.

Enjoy!

Download and screenshots here:
[http://p13.wikispaces.com/B4SDL](http://p13.wikispaces.com/B4SDL)

---

