---
title: "installing from tar file"
date: 2013-04-12
forum: New to Ubuntu
---

### Post by gabmuks on 2013-04-12
Greetings to all.

I recently downloaded a Warzone 2100 game.
It is a tar.xz file. I have extracted the files but
do not know how to install. Need help.
Thank you for your time.

---

### Post by PhantomTurtle on 2013-04-12
The tar file downloaded from the warzone website requires you to compile it. You might find it easier to install it from the Ubuntu repositories, rather than compiling. To install from the repositories, Open up the software Center, search "warzone" in the search box at the top, then click on "Warzone 2100", then click install.

However if you still want to install it from the tar file you received(harder way), then you can do the following. First, extract the tar file into your desktop. Next open up terminal and type the following commands

```
cd Desktop/warzone2100-3.1.0
[COLOR=#000000]
sudo apt-get install build-essential automake flex bison libpng12-dev libsdl1.2-dev libopenal-dev libphysfs-dev libvorbis-dev libtheora-dev libglc-dev libglew1.5-dev libxrandr-dev zip unzip libqt4-opengl-dev libqt4-network libqjson-dev[/COLOR]
```

Wait for all of that to install.

Now we can compile

```
[COLOR=#000000]./autogen.sh && ./configure && make[/COLOR]
```

Once that is finished, you should be able to run Warzone using the following command,

```
[COLOR=#000000]./src/warzone2100[/COLOR]
```
(Source for compile instructions: [http://developer.wz2100.net/wiki/CompileGuideLinux](http://developer.wz2100.net/wiki/CompileGuideLinux))

I recommend the first method of installing through the Software Center, over compiling it yourself.

-Phantom

---

### Post by gabmuks on 2013-04-12
Thank you much!
I already had the Software Center Version so I was looking for the latest version.
But maybe I already had the latest. I don't know.
Anyways I opened the terminal and did the manual install according to your instructions.
Thank you Phantom for your kind reply and helping with this.
I truly admire all you people who know how to do these Linux commands.

---

