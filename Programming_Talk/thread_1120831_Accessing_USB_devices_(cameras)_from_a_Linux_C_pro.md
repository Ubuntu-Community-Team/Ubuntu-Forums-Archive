---
title: "Accessing USB devices (cameras) from a Linux C program"
date: 2009-04-09
forum: Programming Talk
---

### Post by bluedalmatian on 2009-04-09
Is there a standard library in Linux which allows a C/C++ program to access devices via USB.

Ive never really done any direct interaction with hardware before but Im looking to build something which can import photos off a USB camera 

Thanks

---

### Post by Firestom on 2009-04-09
You could try out [Video4Linux]("http://linux.bytesex.org/v4l2/") but it is no longer officially supported and could stagnate over time. There are a few other libraries that allows to use webcams but you'll have to find them yourself!

---

### Post by soltanis on 2009-04-09
V4L2 (video for linux 2) is the new camera standard, but not all drivers support it yet. Camera support in linux is generally pretty terrible, IMHO should really be the target of hardware support over the next few years for desktop-oriented linuxes.

EDIT. Sorry for skimming. Actually what you need is not V4L2 at all. To get pics of a USB camera, you just have to mount the camera as a filesystem, then copy the files you need out of the directory you mounted to.

---

### Post by Firestom on 2009-04-09
Sorry, I thought he meant USB webcam by USB cameras. Actually, not all cameras are supported by Linux, devices using the Microsoft Media Transfer Protocol (MTP) are not supported. For those, you need to get through LibMTP to transfer files over if you device is an MTP one. Else, like soltanis said, you can just mount the device. It's location should be in the /media directory.

---

### Post by bluedalmatian on 2009-04-12
Thats great.  Thanks. I take it the files coming off the camera will be in RAW format?

---

### Post by Zugzwang on 2009-04-13
Dear OP, have a look at the "gphoto2" program. It is in the repositories. It is a command line utility that can download (and delete) pictures from a lot of digital still cameras, including those with the PTP/MTP protocol. That may be far easier than the solution provided. The images are downloaded in the format in which they have been taken.

---

### Post by hessiess on 2009-04-13
> **bluedalmatian said:**
> Thats great.  Thanks. I take it the files coming off the camera will be in RAW format?

Depends on the camera, most of the cheaper ones only support jpg.

---

