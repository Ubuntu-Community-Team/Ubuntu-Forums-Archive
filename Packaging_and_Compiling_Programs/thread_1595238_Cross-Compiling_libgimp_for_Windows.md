---
title: "Cross-Compiling libgimp for Windows"
date: 2010-10-13
forum: Packaging and Compiling Programs
---

### Post by Conoktra on 2010-10-13
Hi!

I have developed a plug-in for Gimp.  I would like to compile this plug-in for 32-bit Windows, which requires a Windows build of libgimp.  I am looking to cross-compile gimp, including libgimp, for Windows so that I can compile my plug-in.

After finally getting my plug-in to the linking stage, which was quite the frustrating project, I noticed that I need a build of libgimp for Windows.  After some extensive research, it appears (near as I can see) that the Gimp project is devoid of providing pre-compiled dev-packages for libgimp.

I read about quote: "Most people like to cross-compile Gimp on Linux for Windows".  I would prefer to do this too, because the Linux build system is SO much nicer than anything provided on Windows.

I was unable to find a tutorial on how to cross-compile Gimp, and the configure script for Gimp doesn't seem to support setting host and architecture options.

**So, how would I cross-compile gimp for Windows?**  A quick set of commands, or a link to a tutorial to point me in the right direction would be appreciated.

Thanks beforehand!

**EDIT:**  If anyone knows of some pre-compiled dev-packages of libgimp for Windows, I would prefer to use those.

---

### Post by George Edison on 2011-06-18
This is a very good question and one that I ran into myself when I was trying to compile a Gimp plugin for Windows. What you really need are the *.a files for linking against the *.dll files that ship with the Gimp. These files will resolve the linker problems you're facing.

I tried to find these files myself, but it seemed like nobody had posted them anywhere. I certainly didn't want to go through all of the trouble of compiling the Gimp from scratch. So here's what I did:

First of all, I downloaded the source code for the Gimp. Then I grabbed the *.dll files from the /bin folder of a Gimp installation. So now I had the source, and the *.dll files. How does that help? Well, the source archive contains the *.def files which list all of the exports for the *.dll files. Using a tool from the Mingw32 compiler collection, I generated the *.a files myself using the following command template:

```

dlltool -d libgimp.def -D libgimp-2.0-0.dll -l libgimp.a

```

(You'll need to repeat that for each libgimp*.dll) The results? The *.a files that we need for the linker! If all of this is confusing, don't worry. You can grab a ZIP archive with the *.a files here:

[http://dl.dropbox.com/u/31080052/gimp_static_libs.zip]("http://dl.dropbox.com/u/31080052/gimp_static_libs.zip")

---

