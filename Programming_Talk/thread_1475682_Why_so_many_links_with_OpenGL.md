---
title: "Why so many links with OpenGL?"
date: 2010-05-07
forum: Programming Talk
---

### Post by &amp;)ky#)^ on 2010-05-07
So, I'm fooling around writing some OpenGL stuff for fun and using SDL along with it.  I'm kind of new to this, so bear with me.

I'm using the -lSDL and -lGL linking options for dynamic linking.  Those are the only ones I'm using.  Being curious, I used the ldd command on my program and found a ton of links.

```
	linux-gate.so.1 =>  (0x008b1000)
	libSDL-1.2.so.0 => /usr/lib/libSDL-1.2.so.0 (0x0022b000)
	libGL.so.1 => /usr/lib/libGL.so.1 (0x00c8b000)
	libstdc++.so.6 => /usr/lib/libstdc++.so.6 (0x005c2000)
	libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0x009fe000)
	libgcc_s.so.1 => /lib/libgcc_s.so.1 (0x004fc000)
	libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0x00315000)
	libasound.so.2 => /usr/lib/libasound.so.2 (0x00110000)
	libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0x00e30000)
	libdirectfb-1.2.so.0 => /usr/lib/libdirectfb-1.2.so.0 (0x0045a000)
	libfusion-1.2.so.0 => /usr/lib/libfusion-1.2.so.0 (0x001d7000)
	libdirect-1.2.so.0 => /usr/lib/libdirect-1.2.so.0 (0x00868000)
	libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0x001e1000)
	libX11.so.6 => /usr/lib/libX11.so.6 (0x006b4000)
	libXext.so.6 => /usr/lib/libXext.so.6 (0x001fa000)
	libXxf86vm.so.1 => /usr/lib/libXxf86vm.so.1 (0x00c2b000)
	libXdamage.so.1 => /usr/lib/libXdamage.so.1 (0x0020a000)
	libXfixes.so.3 => /usr/lib/libXfixes.so.3 (0x00886000)
	libdrm.so.2 => /usr/lib/libdrm.so.2 (0x00f78000)
	/lib/ld-linux.so.2 (0x00e46000)
	librt.so.1 => /lib/tls/i686/cmov/librt.so.1 (0x00b3e000)
	libxcb.so.1 => /usr/lib/libxcb.so.1 (0x00fa4000)
	libXau.so.6 => /usr/lib/libXau.so.6 (0x00f94000)
	libXdmcp.so.6 => /usr/lib/libXdmcp.so.6 (0x00e98000)
```

I did the same on another program I had lying about, Lugaru, which also uses SDL and OpenGL. Here's what I found:

```
	linux-gate.so.1 =>  (0x0033b000)
	libSDL-1.2.so.0 => /home/jsherby/lugaru/libSDL-1.2.so.0 (0x006d7000)
	libopenal.so.1 => /home/jsherby/lugaru/libopenal.so.1 (0x00386000)
	libstdc++.so.6 => /home/jsherby/lugaru/libstdc++.so.6 (0x00950000)
	libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0x00110000)
	libgcc_s.so.1 => /home/jsherby/lugaru/libgcc_s.so.1 (0x00f18000)
	libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0x00d30000)
	libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0x00b95000)
	libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0x002d9000)
	/lib/ld-linux.so.2 (0x00ca5000)
```

As you can see, far fewer links.  How might I change how I compile to reduce the number of libraries I'm linking with?

---

### Post by nvteighen on 2010-05-07
The second one seems to be using OpenAL not OpenGL and therefore, the only thing needed from SDL is the audio bits I guess...

---

### Post by &amp;)ky#)^ on 2010-05-07
Hmm... you're right.  Upon closer inspection, Lugaru doesn't list libGL as a dependency.  However, I know for a fact that it uses OpenGL.  I wonder how it gets away with that.

---

### Post by slavik on 2010-05-08
grep -cr "glBegin" *

if you get 0, you aren't using OpenGL :)

---

### Post by nvteighen on 2010-05-08
There are two other possibilities: 

1) that OpenGL was linked statically. If that's true, then it won't appear in ldd's output. The executable would be really big.
2) that OpenGL is loaded dynamically. The program is linked to libdl (the dynamic loader), so it may be true.

---

### Post by &amp;)ky#)^ on 2010-05-08
It must be dynamically loading opengl as I don't believe the executable is large enough to have linked it statically.  It's about 1.7 MB.

Although, I wonder what icculus was thinking when porting it to linux as opengl isn't exactly optional for that game.

---

### Post by splicerr on 2010-05-08
Statically linking against libGL wouldn't make any sense. If you could then against which libGL would you link: libGL from NVidia, ATI or Mesa?  Pick any of them and your app would only run on a specific subset of video cards .

---

### Post by nvteighen on 2010-05-09
> **bluej774 said:**
> It must be dynamically loading opengl as I don't believe the executable is large enough to have linked it statically.  It's about 1.7 MB.


Ok, it seems that's the most reasonable hypothesis.

> 
Although, I wonder what icculus was thinking when porting it to linux as opengl isn't exactly optional for that game.

That's a good question...

---

