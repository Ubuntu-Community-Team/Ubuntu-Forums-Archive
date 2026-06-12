---
title: "Help understanding instructions"
date: 2008-07-12
forum: New to Ubuntu
---

### Post by SeriousTom on 2008-07-12
I'm trying to understand the install instructions of this file _gstreamer-ossv4-amd64.tar.gz_
I have unpacked it to the Desktop by right clicking and extract here. 
```
INSTALLATION
------------

To install as root:
gzip /usr/lib/gstreamer-0.10/libgstossaudio.so
mv libgstossaudio.so /usr/lib/gstreamer-0.10/

Applet may restart automatically or display a window asking if you want to
reload it (select reload). If neither happens and applet does not work, right
click on it and select "remove From Panel" from displayed menu. It can be
reloaded by right clicking on an empty area of the panel and selecting "Add to
Panel" then double clicking on Volume control in "Add to Panel" window.

```

---

### Post by fahadsadah on 2008-07-12
Open a terminal (Applications->Accessories->Terminal) and type the following commands, in order: ```
cd folder_you_unpacked_into
sudo -s
gzip /usr/lib/gstreamer-0.10/libgstossaudio.so
mv libgstossaudio.so /usr/lib/gstreamer-0.10/

```
The sudo -s is to make yourself root as per the instructions, and then we do what the instructions say. Close the terminal, or type 'exit' when you are done, to unmake yourself root

---

### Post by dracayr on 2008-07-12
In a terminal, execute the commands:

sudo gzip /usr/lib/gstreamer-0.10/libgstossaudio.so
sudo mv libgstossaudio.so /usr/lib/gstreamer-0.10/


dracayr

---

### Post by SeriousTom on 2008-07-14
Well, I think I've made a mess of it now. I tried to install both ways and it said both times the directory doesn't exist. 
So I thought I would be clever and make the file named /usr/lib/gstreamer-0.10/libgstossaudio.so and let it get over-written.
So now I get this ```
serioustom@serioustom-desktop:~/Desktop/gstreamer-ossv4$ sudo -s
root@serioustom-desktop:~/Desktop/gstreamer-ossv4# gzip /usr/lib/gstreamer-0.10/libgstossaudio.so
gzip: /usr/lib/gstreamer-0.10/libgstossaudio.so is a directory -- ignored
root@serioustom-desktop:~/Desktop/gstreamer-ossv4# mv libgstossaudio.so /usr/lib/gstreamer-0.10/

``` So now it thinks it's a directory and I can't seem to get rid of it. I tried this
```
serioustom@serioustom-desktop:~$ sudo rm /usr/lib/gstreamer-0.10/libgstossaudio.so
[sudo] password for serioustom: 
rm: cannot remove `/usr/lib/gstreamer-0.10/libgstossaudio.so': Is a directory

``` 
There were 3 files that were unpacked, 
The Read Me that had the instructions
The gstreamer-0.10/libgstossaudio.so file
Also a file called gst-plugins-good-0.10.6_v0.1.patch
I've tried to get this to run in the terminal and thiis is the outcome
```
root@serioustom-desktop:~/Desktop/gstreamer-ossv4# gst-plugins-good-0.10.6_v0.1.patch
bash: gst-plugins-good-0.10.6_v0.1.patch: command not found
root@serioustom-desktop:~/Desktop/gstreamer-ossv4# install gst-plugins-good-0.10.6_v0.1.patch
install: missing destination file operand after `gst-plugins-good-0.10.6_v0.1.patch'
Try `install --help' for more information.

```
So you can see, I'll try anything :confused:

---

