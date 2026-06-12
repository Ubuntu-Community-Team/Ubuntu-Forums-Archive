---
title: "Building against libavformat"
date: 2010-06-10
forum: Programming Talk
---

### Post by soltanis on 2010-06-10
I'm trying to build some source code that depends on the avcodec, avutil, and avformat libraries. Because the Ubuntu packages are slow to keep pace with ffmpeg and haven't incorporated libvpx (VP8 support) yet, I downloaded and built FFmpeg from the subversion repositories. I used checkinstall to install the package.

EDIT:

This wasn't clear before; I'm **not** building FFmpeg, this is a C program which **depends** on the avformat library.

I've removed the libavcodec-dev (and associated) packages from my system, but when trying to build I get the following slew of errors:

```

gcc -o oggment oggment.c -lavcodec -lavutil -lavformat 2>&1| head

/usr/local/lib/libavformat.a(concat.o): In function `concat_open':
/home/soltanis/Documents/code/ffmpeg/ffmpeg/libavformat/concat.c:67: undefined reference to `av_strstart'
/home/soltanis/Documents/code/ffmpeg/ffmpeg/libavformat/concat.c:99: undefined reference to `av_strlcpy'
/usr/local/lib/libavformat.a(rl2.o): In function `rl2_read_seek':
/home/soltanis/Documents/code/ffmpeg/ffmpeg/libavformat/rl2.c:277: undefined reference to `av_rescale_q'
/usr/local/lib/libavformat.a(allformats.o): In function `av_register_all':
/home/soltanis/Documents/code/ffmpeg/ffmpeg/libavformat/allformats.c:47: undefined reference to `avcodec_register_all'
/usr/local/lib/libavformat.a(anm.o): In function `read_header':
/home/soltanis/Documents/code/ffmpeg/ffmpeg/libavformat/anm.c:88: undefined reference to `av_log_ask_for_sample'
/home/soltanis/Documents/code/ffmpeg/ffmpeg/libavformat/anm.c:168: undefined reference to `av_log_ask_for_sample'

```

(oggment.c is the file).

As you can see, the library build directory is being barfed into there. Any suggestions on how I could solve this without having to go back to the Ubuntu packages?

EDIT: Just noticed this too, but should I be trying to use shared libraries (I notice it's linking against static libraries)? Also, should I be compiling with these libraries in a certain order?

---

### Post by FakeOutdoorsman on 2010-06-11
See [HOWTO: Install and use the latest FFmpeg and x264](http://ubuntuforums.org/showthread.php?t=786095) for a complete guide that includes *libvpx* installation instructions.  The libvpx section has only been added to the Ubuntu Lucid Lynx 10.04 version of the guide but it should be easily adapted for older versions.

You probably don't need shared libraries if you only need FFmpeg, but I'm not totally sure of what you're trying to do.  You need to build external libraries first if you want them included in a compiled FFmpeg.

---

### Post by soltanis on 2010-06-11
I've got ffmpeg working fine with libvpx; that's not the issue. I was merely explaining why I uninstalled the stock ffmpeg packages and decided to compile it myself to preface the next question, which was why was it that after I did that (and removed the stock packages) that code which depended on the ffmpeg libraries wouldn't link properly.

---

### Post by soltanis on 2010-06-12
Still no apparent solution to this problem. Lucky for me I have other options then trying to compile/test this program, but I hope some other poor soul doesn't run into this issue.

---

