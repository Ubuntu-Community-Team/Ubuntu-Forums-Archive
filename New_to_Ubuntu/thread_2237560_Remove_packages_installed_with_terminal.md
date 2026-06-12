---
title: "Remove packages installed with terminal"
date: 2014-08-02
forum: New to Ubuntu
---

### Post by ray9 on 2014-08-02
So I was trying to get "Sound Converter" to convert some wma files to wav and  it complained about the wrong plugins.  So I went through synaptic looking for the plugin and downloaded some other stuff.  I wasn't able to get it to work so I would like to remove the files I downloaded that day.  I was able to find them by >
cat /var/log/dpkg.log | cat /var/log/dpkg.log.1 | grep " install "

There's 10 or more files.  Is there a command where I can delete them all at once or do I have to write them all down and look each up  in synaptic and delete one at time?

Thanks

---

### Post by veddox on 2014-08-02
You can remove packages with 
```
sudo apt-get purge package1 [package2 package3 ...]
```
This will completely remove all listed packages and their configuration files. If you want to keep the configuration files for some reason, replace "purge" with "remove".

---

### Post by ray9 on 2014-08-02
So I can't remove all packages at once  that were installed on a given day?

---

### Post by veddox on 2014-08-02
You can remove them all at once when you append the package name to the above command, but I am not aware of any way to delete them based on the date of their installation. Sorry!

---

### Post by ray9 on 2014-08-02
ray@ray-ET1161-07:~$ cat /var/log/dpkg.log | cat /var/log/dpkg.log.1 | grep " install "
2014-07-14 11:51:30 install libjpeg-turbo-progs:i386 <none> 1.3.0-0ubuntu2
2014-07-14 11:51:31 install libjpeg-progs:i386 <none> 8c-2ubuntu8
2014-07-14 11:51:31 install xscreensaver-data:i386 <none> 5.15-3ubuntu1
2014-07-14 11:51:32 install xscreensaver:i386 <none> 5.15-3ubuntu1
2014-07-14 12:04:40 install libgle3:i386 <none> 3.1.0-7ubuntu2
2014-07-14 12:04:41 install xscreensaver-gl:i386 <none> 5.15-3ubuntu1
2014-07-14 12:04:42 install xscreensaver-gl-extra:i386 <none> 5.15-3ubuntu1
2014-07-17 16:40:32 install libfluidsynth1:i386 <none> 1.1.6-2
2014-07-17 16:40:33 install libtbb2:i386 <none> 4.2~20130725-1.1ubuntu1
2014-07-17 16:40:33 install libopencv-core2.4:i386 <none> 2.4.8+dfsg1-2ubuntu1
2014-07-17 16:40:34 install libopencv-flann2.4:i386 <none> 2.4.8+dfsg1-2ubuntu1
2014-07-17 16:40:35 install libopencv-imgproc2.4:i386 <none> 2.4.8+dfsg1-2ubuntu1
2014-07-17 16:40:35 install libopencv-features2d2.4:i386 <none> 2.4.8+dfsg1-2ubuntu1
2014-07-17 16:40:36 install libopencv-calib3d2.4:i386 <none> 2.4.8+dfsg1-2ubuntu1
2014-07-17 16:40:37 install libgtkglext1:i386 <none> 1.2.0-3.1fakesync3
2014-07-17 16:40:37 install libopencv-highgui2.4:i386 <none> 2.4.8+dfsg1-2ubuntu1
2014-07-17 16:40:38 install libopencv-ml2.4:i386 <none> 2.4.8+dfsg1-2ubuntu1
2014-07-17 16:40:38 install libopencv-objdetect2.4:i386 <none> 2.4.8+dfsg1-2ubuntu1
2014-07-17 16:40:39 install libopencv-video2.4:i386 <none> 2.4.8+dfsg1-2ubuntu1
2014-07-17 16:40:40 install libopencv-contrib2.4:i386 <none> 2.4.8+dfsg1-2ubuntu1
2014-07-17 16:40:40 install libopencv-legacy2.4:i386 <none> 2.4.8+dfsg1-2ubuntu1
2014-07-17 16:40:41 install libgstreamer-plugins-bad1.0-0:i386 <none> 1.2.4-1~ubuntu1
2014-07-17 16:40:41 install libsrtp0:i386 <none> 1.4.5~20130609~dfsg-1
2014-07-17 16:40:42 install gstreamer1.0-plugins-bad-videoparsers:i386 <none> 1.2.4-1~ubuntu1
2014-07-17 16:40:42 install gstreamer1.0-plugins-bad-faad:i386 <none> 1.2.4-1~ubuntu1
2014-07-17 16:40:43 install gstreamer1.0-plugins-bad:i386 <none> 1.2.4-1~ubuntu1
2014-07-17 16:42:26 install libopencore-amrnb0:i386 <none> 0.1.3-2ubuntu1
2014-07-17 16:42:27 install libopencore-amrwb0:i386 <none> 0.1.3-2ubuntu1
2014-07-17 16:42:27 install gstreamer1.0-libav:i386 <none> 1.2.4-1~ubuntu1
2014-07-17 16:42:28 install libsidplay1:i386 <none> 1.36.59-5ubuntu1
2014-07-17 16:42:28 install gstreamer1.0-plugins-ugly:i386 <none> 1.2.3-2build1
2014-07-19 11:50:49 install linux-image-3.13.0-32-generic:i386 <none> 3.13.0-32.57
2014-07-19 11:50:56 install linux-image-extra-3.13.0-32-generic:i386 <none> 3.13.0-32.57
2014-07-19 11:51:12 install linux-headers-3.13.0-32:all <none> 3.13.0-32.57
2014-07-19 11:51:23 install linux-headers-3.13.0-32-generic:i386 <none> 3.13.0-32.57

These are ones I want to remove.   How do I do it?

---

### Post by ray9 on 2014-08-02
apt-get autoremove" removed them.  Thanks for the replies.

---

