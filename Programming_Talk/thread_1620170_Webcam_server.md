---
title: "Webcam server"
date: 2010-11-12
forum: Programming Talk
---

### Post by Cutler on 2010-11-12
Hello, I need help with my webcam. I would like to stream a video from it and access it through web from another computer. Is there any simple solution for this? I tried VLC, but no success here. The best solution for me would be to use v4l4j for record and then somehow stream it to internet with java. I would like to access it with my Vaadin powered website. Any help appreciated. Regards

---

### Post by pasc on 2010-11-23
Hi, 
v4l4j comes with a bunch of example applications to show how to use it.  This includes a webcam server app which streams the video over the network and you can view it in firefox, VLC or ffplay on a remote computer. It also gives you access to the video controls.
I have tried it briefly and it worked great.  I think it has been added just a few days ago and is not part of the tarball yet, so you have to download it using svn (not the tar.gz). 
once v4l4j is installed, run the server with ant test-server.
- for a web browser, go to [http://localhost:8080](http://localhost:8080)
- for VLC, choose connect to stream and enterr "http://localhost:8080/stream" as the address
- for ffplay, use "ffplay -f mjpeg http://loccalhost:8080/stream"
Hope this helps
Pascal

---

