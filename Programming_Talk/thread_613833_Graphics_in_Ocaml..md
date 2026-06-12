---
title: "Graphics in Ocaml."
date: 2007-11-15
forum: Programming Talk
---

### Post by Kadrus on 2007-11-15
Hello,
This code is supposed to draw a triangle with OCaml..but I am having a trouble compiling it..

I think it's not the same as compiling a regular .ml file..
Anyway here is the code
```
let _ =
   ignore( Glut.init Sys.argv );
   Glut.initDisplayMode ~double_buffer:true ();
   ignore (Glut.createWindow ~title:"OpenGL Demo");
   let angle t = 10. *. t *. t in
   let render () =
     GlClear.clear [ `color ];
     GlMat.load_identity ();
     GlMat.rotate ~angle: (angle (Sys.time ())) ~z:1. ();
     GlDraw.begins `triangles;
     List.iter GlDraw.vertex2 [-1., -1.; 0., 1.; 1., -1.];
     GlDraw.ends ();
     Glut.swapBuffers () in
   GlMat.mode `modelview;
   Glut.displayFunc ~cb:render;
   Glut.idleFunc ~cb:(Some Glut.postRedisplay);
   Glut.mainLoop ()

```
Any help will be appreciated :)

---

### Post by Jessehk on 2007-11-15
```

sudo aptitude update
sudo aptitude install liblablgl-ocaml-dev ocaml-findlib

```

```

ocamfind opt graphics_test.ml -package lablgl.glut -linkpkg -o graphics_test

```

In this case, I've named the file graphics_test.ml . :)

---

### Post by Kadrus on 2007-11-16
Thanks it worked perfectly :)
I owe you one:p

---

### Post by unprinted on 2012-06-24
I recognise that code :) and thanks for a way of getting it to compile without "Unbound module Glut" error. It's not exactly intuitive though, is it?

I had installed the liblablgl-ocaml package.. I was expecting it to be somewhere the linker could find it already, without having to install a separate program to help the compilation.

Is there a tutorial for starting OCaml in Ubuntu / Debian? If I stick the obvious words into Google, I get an awfully long list of repositories and not much useful (to me) content.

---

