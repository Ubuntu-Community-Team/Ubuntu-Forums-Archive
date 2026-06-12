---
title: "xmms and flac 1.1.4 plugin"
date: 2007-04-21
forum: Programming Talk
---

### Post by trak87 on 2007-04-21
(This is for feisty, but I would imagine the same applies to Edgy.)

The xmms flac plugin does play flac files, but it crashes xmms if you try to edit any of the plugin's settings. I was however able to compile the latest version of flac (1.1.4) and it works fine. I'll briefly mention how I did it.

As best as I can remember, install xmms, xmms-dev, libvorbis-dev, libogg-dev, nasm and of course build-essential. 

Download and unpack the flac 1.1.4 source code from here: [http://sourceforge.net/projects/flac/](http://sourceforge.net/projects/flac/). 

cd into the flac-1.1.4 directory.

Run ./configure. (Look through the output and see if I forgot any libraries (hehe). 

Run make.

If all went well, look in the flac-1.1.4/src/plugin_xmms/.libs directory and copy  libxmms-flac.so into your ~/.xmms/Plugins directory. Restart xmms. Xmms will choose this plugin over any flac plugin installed at /usr/lib/xmms/Input.

That's it.

I would still like to know the proper way to create Ubuntu style .deb files. I realize I can run checkinstall but I'm not sure if that's the same thing.

---

### Post by trak87 on 2007-06-01
The above doesn't work completely. I have problems playing files over the server so perhaps this is related to missing library files.

---

### Post by tturrisi on 2007-06-01
> I would still like to know the proper way to create Ubuntu style .deb files. I realize I can run checkinstall but I'm not sure if that's the same thing.
fyi, after you build a package from source, it put the .deb in /usr/src dir.

---

