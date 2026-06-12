---
title: "Compile external files into a binary (c++)"
date: 2010-12-19
forum: Programming Talk
---

### Post by sdlynx on 2010-12-19
Is this possible?

For example, I'm making something in OpenGL that uses textures and would like it if the texture images could be packed in with the compiled program binary.

Thanks,
SDLynx

P.S. Sorry if what I'm saying makes completely no sense, I'm new to anything aside from the standard compiling done by an IDE (usually I use Code::Blocks).

---

### Post by nvteighen on 2010-12-20
> **sdlynx said:**
> Is this possible?

For example, I'm making something in OpenGL that uses textures and would like it if the texture images could be packed in with the compiled program binary.

Thanks,
SDLynx

P.S. Sorry if what I'm saying makes completely no sense, I'm new to anything aside from the standard compiling done by an IDE (usually I use Code::Blocks).

It is perfectly possible and GIMP is very handy for this. The obstacle may be the OpenGL API itself.

Let's see. The normal procedure to load any kind of data is to grab it from a file and then create a data structure that holds all the data needed, so that usually the file is no longer accessed and everything is done from memory (which is faster than doing it from the disk).

Well, what you have to do is to skip the first step and code the file into a data structure right into your source code. But of course, doing this manually would be really hard, but there's GIMP.

In GIMP, save your image as a C header file (*.h). Yes, as a C header file. It will store your image as a bitmap data structure you can either copy or #include in the relevant source code. It also defines a pair of pixel accessors.

There may be several problems:
1) That you'll have to trick OpenGL to take this data structure as it was a file.
2) The size of your executable and compilation time may grow a lot...
3) I don't see any particular advantage of doing this... ok, yeah, that people don't fiddle with your images, but that could be solved by encrypting them somehow or using a custom format (But that if you plan to create a FOSS project, this is a bit... uh... counterproductive).

---

### Post by sdlynx on 2010-12-20
> **nvteighen said:**
> It is perfectly possible and GIMP is very handy for this. The obstacle may be the OpenGL API itself.

Let's see. The normal procedure to load any kind of data is to grab it from a file and then create a data structure that holds all the data needed, so that usually the file is no longer accessed and everything is done from memory (which is faster than doing it from the disk).

Well, what you have to do is to skip the first step and code the file into a data structure right into your source code. But of course, doing this manually would be really hard, but there's GIMP.

In GIMP, save your image as a C header file (*.h). Yes, as a C header file. It will store your image as a bitmap data structure you can either copy or #include in the relevant source code. It also defines a pair of pixel accessors.

There may be several problems:
1) That you'll have to trick OpenGL to take this data structure as it was a file.
2) The size of your executable and compilation time may grow a lot...
3) I don't see any particular advantage of doing this... ok, yeah, that people don't fiddle with your images, but that could be solved by encrypting them somehow or using a custom format (But that if you plan to create a FOSS project, this is a bit... uh... counterproductive).

Wow! That sounds like it will work.  For what I need, OpenGL need only access a char* that contains the image data, and that can be easily stored in a variable.  That sounds like a great idea, thanks!

---

### Post by nvteighen on 2010-12-21
> **sdlynx said:**
> Wow! That sounds like it will work.  For what I need, OpenGL need only access a char* that contains the image data, and that can be easily stored in a variable.  That sounds like a great idea, thanks!

Then your problem is solved, as the GIMP data structure contains the data in a char * :)

---

