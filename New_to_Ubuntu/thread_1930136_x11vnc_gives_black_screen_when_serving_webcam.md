---
title: "x11vnc gives black screen when serving webcam"
date: 2012-02-23
forum: New to Ubuntu
---

### Post by znoob on 2012-02-23
When using x11vnc to serve my desktop everything works fine, but when I try to have it serve my webcam all I get in the vnc viewer is a black screen. x11vnc does not report any errors.

The webcam works (I use it often for video calling) on /dev/video0. I noticed that usually when I use the webcam a small led on it switches on. When I launch x11vnc that led stays off, but I don't know what that means in terms of linux.

The command I use to launch the server is
```
x11vnc -usepw -rawfb video0
```

Any help would be greatly appreciated.

---

### Post by krunge on 2012-03-02
Could you capture the output when you try to do run that command by adding "-o log.txt" and then reproduce the problem and then attach log.txt here or send it to me in a PM if you prefer?

---

