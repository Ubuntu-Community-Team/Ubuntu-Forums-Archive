---
title: "How to cross-compile libgdiplus"
date: 2009-11-19
forum: Programming Talk
---

### Post by WitchCraft on 2009-11-19
Hi, I have an interesting question:

On my Linux server, I let .net apps run under mono.
So far so good, I haven't been able to get a single one of them running ;-))

Actually, my problem is with my captcha routine.
It makes several calls to GDI to generate a captcha.

Now, after it didn't work on my Linux server, I tested it on my Linux desktop, where it showed the captcha background, but not the foreground numbers.

I've looked in the desktop's server logfile, and found gdi-warp not implemented. 
After I removed the call of GDI, it worked on the desktop, just no distortion of the captcha image (because of the missing gdi-warp implementation)...

When I went on the server, it failed again. After spending some time changing the config, I was able to see the remote error message, which was: Error: libgdi.dll not found. 
True, for it is NOT installed, as I found out.

Now the problem is it's a tiny Synology server (64 MB ram, 260 MHz), and it has a PPC processor, and virtually no packages...
(It had mono, but I had to improvise by extracting the XSP server executables and dlls as well as the vb.net compiler from a debian package - that works because these are mono/.net dlls as I found out when I let the file utility run over the dll's and exe's on my computer.

Now, libgdiplus is native, so I have to cross-compile.

The sources are here:
[http://ftp.novell.com/pub/mono/sources-stable/](http://ftp.novell.com/pub/mono/sources-stable/)

and the process is a standard ./configure make make install process.

But now I have to tell it to use the cross-compiler, cross-compiler headers and build for PPC and not x86_64.

Anybody knows how to do that ?
I can improvize with the install process, doing it manually (because that certainly won't work, because all the programs are at the wrong location...).
But I have no idea where or how I could replace the compier and headers.

---

### Post by WitchCraft on 2009-11-20
bump.

---

### Post by directhex on 2009-11-20
Try [http://people.debian.org/~debacle/cross/](http://people.debian.org/~debacle/cross/) (substitute the ARM language for PPC)

---

### Post by WitchCraft on 2009-11-23
> **directhex said:**
> Try [http://people.debian.org/~debacle/cross/](http://people.debian.org/~debacle/cross/) (substitute the ARM language for PPC)

Oh, correct, I need an entire environment, with all the cross-compiled dependencies, not just some changes in the config file.
Thank you very much, excellent link. Now I just need one more weekend to make it work ;-))

---

