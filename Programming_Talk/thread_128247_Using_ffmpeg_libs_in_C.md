---
title: "Using ffmpeg libs in C"
date: 2006-02-11
forum: Programming Talk
---

### Post by endersshadow on 2006-02-11
Well, first of all, I just want to say that I'm a total noob when it comes to this, but I'm giving it my best shot.

I've got two header files that I need from ffmpeg, avcodec and avformat.  I've done the include, but when I go to compile with gcc, I keep getting the following error:

```
eric@homesteadgrays:~/workspace/vive$ gcc -L/home/eric/workspace/vive/libavcodec/ -lavcodec -L/home/eric/workspace/vive/libavformat/ -lavformat -o vive vive.c
vive.c:10:21: error: avcodec.h: No such file or directory
vive.c:11:22: error: avformat.h: No such file or directory
```

Even though avcodec.h and avformat.h are in the specified folders.  If it's something stupid, just let me know...and/or please point me in the direction of good resources for delving into C...something a little beyond an introduction to the language and more into about how to use C to build a solid program.

Thank you!

---

### Post by toojays on 2006-02-12
The -L option is passed to the linker. For including the headers, you need to use the -I option, which is for the preprocessor.

---

### Post by endersshadow on 2006-02-12
You, sir, are bloody awesome.

---

