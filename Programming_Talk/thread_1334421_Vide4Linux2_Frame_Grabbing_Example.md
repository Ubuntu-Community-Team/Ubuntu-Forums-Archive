---
title: "Vide4Linux2 Frame Grabbing Example"
date: 2009-11-22
forum: Programming Talk
---

### Post by rba1988 on 2009-11-22
Hello. 

I'm looking for a simple example for grabbing frames from a v4l2 device. I've successfully done it using Java and the v4l4j library ([http://code.google.com/p/v4l4j/](http://code.google.com/p/v4l4j/)). Although it gets the job done, I'm looking for an example in C/C++. 

Thanks.

---

### Post by grayrainbow on 2009-11-22
[http://v4l2spec.bytesex.org/]("http://v4l2spec.bytesex.org/")
Make sure you know what ioctl is, or go for some wrappers.

---

### Post by rba1988 on 2009-11-23
> **grayrainbow said:**
> [http://v4l2spec.bytesex.org/]("http://v4l2spec.bytesex.org/")
Make sure you know what ioctl is, or go for some wrappers.

I've been trying to study the capture.c source code for some time now. The documentation is too complex for my level. I believe the bytes of the frame get captured in this snippet:

```

switch (io) {
        case IO_METHOD_READ:
                if (-1 == read (fd, buffers[0].start, buffers[0].length)) {
                        switch (errno) {
                        case EAGAIN:
                                return 0;

                        case EIO:
                                /* Could ignore EIO, see spec. */

                                /* fall through */

                        default:
                                errno_exit ("read");
                        }
                }

                process_image (buffers[0].start);

                break;

```

The bytes get stored in the buffers array? Although I'm not so sure yet. Are there any simpler examples out there for beginners? In v4l4j, It captures frames from a loop and converts them to an Image object. It's quite simple and I'm looking for a counterpart in C/C++.

---

### Post by grayrainbow on 2009-11-23
If you want to learn something about how your camera is controlled, you'll go and use ioctl. Btw, ioctl is basiclly standard for device control, it's use in windows as well. Anyway as I sad if you don't care about this stuff go for some wrapper.

About the part of switch statement you post...basiclly it's true only if you can "cat /dev/video0" without error, on Jounty and Karmic it never worked on my laptop(and a lot of programs for accessing my cam didn't work as well). The other method is memmap. And in the example they don't do anything with the image, just showing access to the camera.

---

