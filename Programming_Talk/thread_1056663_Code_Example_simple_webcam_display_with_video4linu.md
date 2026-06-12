---
title: "Code Example: simple webcam display with video4linux and SDL"
date: 2009-02-01
forum: Programming Talk
---

### Post by skullmunky on 2009-02-01
It's hard to find good example code to use when starting out with video4linux; perhaps because API's have changed so much over the years, a lot of the examples out there are outdated and don't seem to work right anymore, or won't even compile.  There's a great capture example in the video4linux documentation, but all it does is capture - it doesn't actually display the images.

I took that and crudely hacked some SDL display code onto it in order to get just a basic example of how to get images from a webcam and display them on the screen.  After doing this I still don't understand anything at all about how video4linux works, so I'm afraid I can't explain or comment this any more than it is :)  

You'll also notice improper mixing of C and C++ as well as a host of other shortcuts and bad coding practices.  The code is lengthy, so I'm attaching it plus a binary compiled on ubuntu 8.04 i386.

---

### Post by SIGTERMer on 2009-02-01
i think this is just what I'm looking for. thanks :)

---

### Post by vector.kerr on 2009-04-20
Champion! Downloading as we speak... Thanks for putting it up! :KS

---

### Post by szuthsi on 2011-09-08
I downloaded this but im getting an error when i run it that /dev/video0 is no capture device. 

Im using Logitech HD PRO 1080p C910  and a Logitech Webcam C905 and neither works with this.

Same error for both :-( any idea?

---

### Post by toccata015 on 2011-10-02
Also have the same problem...

/dev/video0 is no video capture device

---

### Post by skullmunky on 2011-10-10
Hi, sorry I didn't see your questions before - if you look in /dev, do you have anything else that looks promising? 

Also, does cheese work?  

by the way, in the time since I wrote this sample I've become a big fan of gstreamer for doing video capture; they seem to have done a great job of wrapping up a lot of the annoying details about finding and starting devices.

---

### Post by narsi1986 on 2012-02-28
Hi,

I somehow managed to remove 
"/dev/video0 is no video capture device" error

I introduced the below code in init_device()

<SNIP>

    if (-1 == xioctl (fd, VIDIOC_QUERYCAP, &cap)) {
        if (EINVAL == errno) {
            fprintf (stderr, "%s is no V4L2 device\n",dev_name);
            exit (EXIT_FAILURE);
        } else {
            errno_exit ("VIDIOC_QUERYCAP");
        }
    }

    if (!(cap.capabilities & V4L2_CAP_VIDEO_CAPTURE)) {
        fprintf (stderr, "%s is no video capture device\n",dev_name);
        exit (EXIT_FAILURE);
    }

</SNIP>

But I am not able to see any video output on the ""Video4Linux + SDL" viewer, its giving some junk video.

I observed that my web camera is getting detected.(Only after calling start_capture() method in the main).

Please help me out over here.

---

### Post by narsi1986 on 2012-03-06
Hi,

I am getting a new error while trying to debug the code.(As I was getting a junk video).:confused:

When I try to print the data inside campixdata (which is process_image function), I get an unusual print 

"Address 0xb7fe8c40 out of bounds"

Has anyone encountered it? I am not able to proceed because of this. As this is the value which is passed as Y U and V.

Please help me!!!!

---

### Post by mennowo on 2012-05-09
Hello,

here I am able to compile and run the code when replacing part of the init_device() method from the source with the original code from the V4L2 example. Here is the relevant code:

```
static void init_device (void)
{
    struct v4l2_capability cap;
    struct v4l2_cropcap cropcap;
    struct v4l2_crop crop;
    struct v4l2_format fmt;
    unsigned int min;

    if (-1 == xioctl (fd, VIDIOC_QUERYCAP, &cap))
    {
        if (EINVAL == errno)
        {
            fprintf (stderr, "%s is no V4L2 device\n", dev_name);
            exit (EXIT_FAILURE);
        }
        else
        {
            errno_exit ("VIDIOC_QUERYCAP");
        }
    }

    if (!(cap.capabilities & V4L2_CAP_VIDEO_CAPTURE))
    {
        fprintf (stderr, "%s is no video capture device\n", dev_name);
        exit (EXIT_FAILURE);
    }

        switch (io)
    {
        case IO_METHOD_READ:
            if (!(cap.capabilities & V4L2_CAP_READWRITE))
            {
                fprintf (stderr, "%s does not support read i/o\n", dev_name);
                exit (EXIT_FAILURE);
            }
            break;

        case IO_METHOD_MMAP:
        case IO_METHOD_USERPTR:
            if (!(cap.capabilities & V4L2_CAP_STREAMING))
            {
                fprintf (stderr, "%s does not support streaming i/o\n", dev_name);
                exit (EXIT_FAILURE);
            }
            break;
    }

    /* Select video input, video standard and tune here. */

    CLEAR (cropcap); etc...
```

However, the video looks really strange, blurry, grainy and greenish, like the captured data is misinterpreted.

My goal is to have a proper V4L2 implementation in C/C++, for eventual use inside Openframeworks. The Openframeworks libraries actually provide for Gstreamer support, but this does not give me good results with multiple cameras (ps3 eye cams).

Using Guvcview I have good results, which is why I am thinking a direct V4L2 implementation would be better. At least, I am presuming Guvcview uses V4L2 for usb webcams...

Is the V4L2 example found [here]("http://v4l2spec.bytesex.org/spec/capture-example.html") still relevant and up to date? Since it is a few years old, whereas the V4L2 source has been updated in 2012... Or is it really better to focus on Gstreamer?

---

### Post by lhkeong on 2012-05-22
i'm facing this problem too.

"/dev/video0 is no video capture device"

anyone can know how to solve this?

---

