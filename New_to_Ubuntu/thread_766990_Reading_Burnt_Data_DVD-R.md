---
title: "Reading Burnt Data DVD-R"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by ChompTheMan on 2008-04-25
Hi all.  I installed Hardy Heron yesterday.  I started with the alternative cd and installed the base system.  I then installed x-window-system-core, kde-core and kdm.  Now here's the problems I am having:

1. When I put a burnt data DVD-R into my rom it doesn't show up on my desktop like with a normal install.  Am I missing something that doesn't come with the core installs that will show an icon on the desktop everytime I put something in my rom?

2. My rom won't read the burnt data DVD-R 9 times out of 10.  I've tried *sudo mount /dev/scd0 /media/cdrom0* to no avail.  I'm not sure if this is because of the core install or if it's a bug of some sort.  The rom was bought just last year so I don't think it's defective.  Any ideas?

---

### Post by OriginalOG on 2008-07-07
What format is the movie in? Try installing the codecs.
Go To Applications> Accessories> Terminal
Type in between "   " 
"apt-get update
"apt-get upgrade
"apt-get install gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-  plugins-bad-multiverse 
gstreamer0.10-plugins-bad gstreamer0.10-plugins-ugly gstreamer0.10-ffmpeg libxine1-ffmpeg libdvdread3
sudo apt-get install xine-ui"

Let me know if it works.

---

### Post by alienexplorers on 2008-07-07
Is it a movie or data disk?

---

