---
title: "Help me to compile Movino Video Server in Ubuntu . Please ...."
date: 2010-02-08
forum: Packaging and Compiling Programs
---

### Post by vijaysoft on 2010-02-08
I am a beginner in Linux . I want some help from experts , please help me to compile **Movino Video Server **in Ubuntu . **Movino Video Server is open source video streaming server written for Linux** . I read the instructions in the 'COMPILING' file in the Movino-suite , that didn't helped me in anyway . So please help me . The document saying it requires the packages like libjpeg , ffmpeg , libcurl , libexpat, libogg, lame . How to install this packages , please i am just a beginner in Ubuntu . Please...any one help me .... there is no other forum for helping in this ..........please ...


for any more reference please go to  

[http://movino.org]("http://movino.org/")
[http://www.movino.org/faq](http://www.movino.org/faq)
[http://www.movino.org/documentation](http://www.movino.org/documentation)
[http://sourceforge.net/projects/movino/forums/forum/664494](http://sourceforge.net/projects/movino/forums/forum/664494)

---

### Post by SevenMachines on 2010-02-10
hi there. you should follow the instructions at
[http://www.movino.org/faq](http://www.movino.org/faq), the '[SIZE=1]How do I set up the Movino server on a Linux box?' section[/SIZE]
note you'll need to have at least the packages below installed, if you are missing any more (see the COMPILING file in the source) you can find them by searching for the missing program with the extension -dev in synaptic (dev for development files :) ). for example, if you try to follow the instructions in the faq and it fails due to something like 'missing lame', then you can search for 'lame dev' in synaptic and install that package

$ sudo apt-get install build-essential libogg-dev libvorbis-dev libtheora-dev libmp3lame-dev

note though that movino is 2 years old and may not compile on more recent linux, in particular, some source code header files would need to be changed to compile on gcc 4.4

---

