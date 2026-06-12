---
title: "YUV  (YUY2/YUYV) colorspaces, mixing and matching Y and UV's"
date: 2009-07-27
forum: Programming Talk
---

### Post by iochinome on 2009-07-27
Hey guys, so i have a pretty specialized problem, all is forgiven if nobody knows whats up. in the program i am writing, i am working with YUV colorspaces, right now in the format YUYV, a.k.a. YUY2. here is a look at it from the v4l2 API:

[http://v4l2spec.bytesex.org/spec-single/v4l2.html#V4L2-PIX-FMT-YUYV](http://v4l2spec.bytesex.org/spec-single/v4l2.html#V4L2-PIX-FMT-YUYV)

basically, at one point, i need to be able to copy a single pixel repeatedly into a memory location from the YUYV colorspace. as one can see, though, pixels share the color coordinates U and V between them, so in order to take the information that represents one pixel, one must go like this:
Y1 U1 Y1 V1 Y1 U1 Y1 V1 (how it should be to rep. one pixel 4 times)
Y1 U1 Y2 V1 Y3 U2 Y4 V2 (how 4 pixels are rep.d in the actual colorspace)

for some reason, however, this method is not working for me. check out this code:
(read = location i am reading from, contains a YUV frame, write = location i am writing to, both unsigned char *)
```

for (i=1;i<=16;i++) {   //need to copy the first pixel 16 times...
     if (i%2 == 1) {
          memcpy(write, read, 2); // gets (Y1, U1)
     }
     else {
          memcpy(write, read, 1); 
          memcpy(write, read+3, 1);  //gets (Y1, V1)
     }
     write = write + 2; //advances the location of the buffer
}


```


when i do that, things get majorly messed up, and the colorspace goes awry, giving me green and yellow streaks all down the image. whats the deal? that seems perfectly reasonable to me... thanks, much appreciated!

---

### Post by iochinome on 2009-07-28
allow me to rephrase the question: for the YUYV colorspace, four pixels would be represented like this, going left to right, wouldnt they?

Y1 U1 Y2 V1 Y3 U2 Y4 V2

so why is it when you try to rearrange like this

Y1 U1 Y1 V1 Y3 U2 Y3 V2 (keeping one Y across two pixels that share the color coordinates)

the image comes out all screwy?

thanks!

---

### Post by iochinome on 2009-08-10
hmm... does nobody have experience with YUYV? this is a pretty obscure problem, i bet...

---

