---
title: "Mednafen/OpenGL compilation problems"
date: 2006-09-17
forum: Programming Talk
---

### Post by nightmareci on 2006-09-17
I'm trying to compile the latest version of Mednafen ([http://www.mednafen.com/)](http://www.mednafen.com/)), a great multi-system emulator mainly intended for Unix operating systems, but I'm getting errors about not having the OpenGL headers. I've tried looking around the OpenGL-related packages with Synaptic and the Ubuntu Package Search, but the OpenGL headers aren't there, although OpenGL related libraries' headers are such as GLUT. When I ./configure, it ends (and fails) and says it needs gl.h, likely supposed to be located at /usr/include/GL/gl.h I would think. So, where the heck can I get the header I need? The package repositories certainly don't have it.

---

### Post by DoktorSeven on 2006-09-17
$ apt-file search /usr/include/GL/gl.h
mesa-common-dev: usr/include/GL/gl.h

So mesa-common-dev, apparently. (Not that you could have found that if you don't have it installed, since apt-file searches through installed packages.  But that's how I found it, so there ya go.)

---

### Post by hod139 on 2006-09-17
Another way to search is to go to [http://packages.ubuntu.com/](http://packages.ubuntu.com/), scroll down to the second search "[SIZE=4]Search the contents of packages[/SIZE]", and select "packages that contain files or directories named like this".  Then enter GL/gl.h for the search terms, and arrive at [URL="http://packages.ubuntu.com/cgi-bin/search_contents.pl?word=GL%2Fgl.h&searchmode=searchfilesanddirs&case=insensitive&version=dapper&arch=i386"]here.
[/URL]That lists shows all packages that provide GL/gl.h.

mesa-common-dev is in the list, and is most likely the package you want.  The mingw32-runtime is if you want to compile windows code in linux, and the nvidia packages contain Nvidia specific OpenGL extensions.  You can use these if you want to develop openGL using specific Nvidia extensions, but it won't be able to run on all video cards.

---

### Post by nightmareci on 2006-09-23
Sorry for not replying about my issue for a while, but I have been busy with other things.

Anyways, I found the problem. I actually had mesa-common-dev installed, but for some mysterious reason /usr/include/GL/gl.h and the other needed OpenGL headers weren't there. But the headers should be there, so I just completely removed the package and reinstalled, and the headers are there now. Why the files weren't there before I do not understand, but all is well now.

Mednafen compiled successfully, so thanks for the help!

---

