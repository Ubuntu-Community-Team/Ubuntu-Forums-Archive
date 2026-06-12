---
title: "c++ compile error"
date: 2006-10-19
forum: Programming Talk
---

### Post by Jason_Hampson on 2006-10-19
Hi,
   This is my first Linux applicaion. I normally use an IDE, so I'm a bit of a stranger to the command line.

I've installed g++/gcc. I'm trying to compile some sample source code I found on a website ([http://www.inb.uni-luebeck.de/~boehme/avcodec_sample.cpp](http://www.inb.uni-luebeck.de/~boehme/avcodec_sample.cpp)) to interface to libavcode.   

I used the suggesed command line argument: 

   g++ -o avcodec_sample avcodec_sample.cpp -lavformat -lavcodec -lz

but I get compilation errors:

avcodec_sample.cpp:20:21: error: avcodec.h: No such file or directory
avcodec_sample.cpp:21:22: error: avformat.h: No such file or directory
avcodec_sample.cpp:25: error: ‘AVFormatContext’ was not declared in this scope
avcodec_sample.cpp:25: error: ‘pFormatCtx’ was not declared in this scope
avcodec_sample.cpp:25: error: ‘AVCodecContext’ was not declared in this scope 
...

I'm assuming the header files aren't on the path and there not relative to the source code file I'm trying to compile.

I tried coping the header files to they were in the same directory as the cpp file, but got the same result. 

I then tried putting the full path to the headers:

   g++ -o avcodec_sample avcodec_sample.cpp -l/usr/include/ffmpeg/avcodec.h -l/usr/include/ffmpeg/avformat.h -lz

and

   g++ -o avcodec_sample avcodec_sample.cpp -l/usr/include/ffmpeg/avcodec -l/usr/include/ffmpeg/avformat -lz

but still had the same problem.

Any advice?

Thanks

---

### Post by engineer on 2006-10-19
you need the -I option for additional include directories

```

-I /usr/include/ffmpeg

```

---

### Post by Jason_Hampson on 2006-10-19
I still get the same set of errors with:

g++ -o avcodec_sample avcodec_sample.cpp -l /usr/include/ffmpeg

:-?

---

### Post by engineer on 2006-10-19
you have to use a big i. this stands for include i guess. not a small L

---

### Post by Jason_Hampson on 2006-10-19
](*,) 

Thanks! 

I've got some compilation errors now. Do you think I'm referencing the wrong header files:

avcodec_sample.cpp: In function ‘int main(int, char**)’:
avcodec_sample.cpp:149: error: request for member ‘codec_type’ in ‘pFormatCtx->AVFormatContext::streams[i]->AVStream::codec’, which is of non-class type ‘AVCodecContext*’
avcodec_sample.cpp:158: error: cannot convert ‘AVCodecContext**’ to ‘AVCodecContext*’ in assignment
avcodec_sample.cpp:176: error: ‘struct AVCodecContext’ has no member named ‘frame_rate’
avcodec_sample.cpp:176: error: ‘struct AVCodecContext’ has no member named ‘frame_rate_base’
avcodec_sample.cpp:177: error: ‘struct AVCodecContext’ has no member named ‘frame_rate_base’

---

### Post by engineer on 2006-10-19
you could post the code and i try to find your error. but i can't guarantee anything because i never worked with this lib

---

### Post by Jason_Hampson on 2006-10-19
thanks for your help!

---

### Post by engineer on 2006-10-19
can't compile it here because i don't want to install all those dev libs.
but one error is: you try to access a member called codec_type.
but in the header file it's defined as type. so replace codec_type with type and it should be 1 error less.

---

