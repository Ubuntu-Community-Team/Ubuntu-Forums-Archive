---
title: "linking with libavformat / libavcodec"
date: 2009-05-03
forum: Programming Talk
---

### Post by skullmunky on 2009-05-03
I've always wanted to learn how to use ffmpeg in my own code.  I found this wonderful tutorial([http://www.dranger.com/ffmpeg/tutorial01.html]("http://www.dranger.com/ffmpeg/tutorial01.html"), but I can't get any of the linking to work.  I get a spew of errors such as
```

undefined reference to `av_freep'
undefined reference to `av_mallocz'
undefined reference to `av_log'

```

etc. which obviously means it's not linking correctly.

the compile command looks like this:

```

gcc -o tutorial05 tutorial05.c -lavformat -lavcodec -lavutil   -lm -lswscale -lz `sdl-config --cflags --libs`

```

whenever anyone has this problem, the advice is always to link to libavformat first.   So something must be wrong with that step, I imagine.  

I'm on 8.04 with an ffmpeg built from SVN, following the excellent guide on the forums here on building ffmpeg with H.264.

I went hunting for libavformat, here's what locate found for me:

```

/usr/lib/libavformat.so.1d
/usr/lib/libavformat.so.1d.51.10.0
/usr/local/lib/libavformat.a

```

as well as many others scattered amongst various src folders for different things, but I these should be the only ones in my path.

---

