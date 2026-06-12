---
title: "Debugging Problem in Gdb"
date: 2008-12-29
forum: Programming Talk
---

### Post by akm3 on 2008-12-29
Dear All,

I have written a program with FFMPEG API(This a library for video/audio manipulation)
I have tried to debug the executable file using DDD(which uses 'gdb' itself)

To make it simple, I am trying to see where in the ffmpeg source code, a function (namely "avcodec_decode_video()")referes to.
I put a breakpoint on the function name, and use "step" to debug.
But, when it reaches the line containing the function, I get the following message:
[IMG]http://i43.tinypic.com/6ej436.jpg[/IMG]

I wanted to know which of these is the source of this error;

1) I have done some mistakes installing ffmpeg (i.e. wrong ./configure options [I think this is not the case, since I've disabled all optimization options])

2) I have problem with "root" privileges (since the libraries are at "use/local/lib")(note I tried "sudo ddd executable_filename" instead of "ddd executable_filename", and i get an error in the beginnig of debugging which says :
[IMG]http://i39.tinypic.com/311ozyq.png[/IMG]
)

3) I am using gcc(in compiling the file)wrongly
(I compile it like:
```
gcc -o executable_filename myCCode.c -g -lavutil -lavformat -lavcodec -lz
```
where I have used the names of the required libraries and -g for being debuggable
)(Note that the program compiles correctly, and works when I'm not debugging)

I appreciate your help on this, cuz it has made me stuck in working on a project.
Though, this is not an ffmpeg forum, I am attaching the source code, in case anybody with knowledge of ffmpeg wants to take a look.

---

