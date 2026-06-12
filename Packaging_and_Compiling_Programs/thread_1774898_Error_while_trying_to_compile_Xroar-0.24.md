---
title: "Error while trying to compile Xroar-0.24"
date: 2011-06-03
forum: Packaging and Compiling Programs
---

### Post by castiglione on 2011-06-03
Hi - I've been trying to compile Xroar-0.24 and ran into the following error.

./configure worked fine but when I did make, I ran into the following:

In file included from vo_sdl.c:63:0:
vo_generic_ops.c: In function ‘render_sg4’:
vo_generic_ops.c:224:10: error: ‘vdg_alpha’ undeclared (first use in this function)
vo_generic_ops.c:224:10: note: each undeclared identifier is reported only once for each function it appears in
make: *** [vo_sdl.o] Error 1

I don't know quite what to make of this.  Has anyone run into a similar problem?  Were you able to solve it?  If so, how?

Thanks in advance!

c

---

### Post by SevenMachines on 2011-06-04
The Makefile should contain a line like
```
vdg_bitmaps.h: tools/font2c $(SRCROOT)/vdgfont.png
    tools/font2c --header --array vdg_alpha --type "unsigned int" --vdg $(SRCROOT)/vdgfont.png > $@

```so when you run make, something like
```
 tools/font2c --header --array vdg_alpha --type "unsigned int" --vdg ./vdgfont.png > vdg_bitmaps.h
```happens, giving you a file

vdg_bitmaps.h:
```
/* This file was automatically generated
 * by tools/font2c from ./vdgfont.png */

extern const unsigned int vdg_alpha[768];
```You could generate this file manually maybe if the makefile command is missing but it would depend which of the above things is missing really to see where the automatic stuff is going wrong.

---

### Post by castiglione on 2011-06-04
I've poked around in the make file and found the line of code you described.
 
Poking around in my xroar-0.24 folder, I can see that vdg_bitmaps.h does exist so it got made but it has the little lock icon on the file (read only?).

---

### Post by SevenMachines on 2011-06-04
Shouldnt have a lock icon, try removing it ( using sudo if necessary ). its auto generated on make so thats fine. mine is 644 permissioned to user,
```
 -rw-r--r-- 1 seven seven 550 2010-09-08 08:15 vdgfont.png
```

or 
> $ chown <my_username>.<my_group_name> vdgfon.png
$ chmod 644 vdgfont.png

---

### Post by castiglione on 2011-06-04
I changed ownership and permissions on vdg_bitmaps.h and I'm still getting the same 'vdg_alpha' undeclared in vo_generic_ops.c error message.

---

### Post by SevenMachines on 2011-06-04
Have you tried deleting the directory and running 
```
$ ./configure
$ make
```
from a fresh unpack of the source?
I'm a little worried that the permissions of files were wrong. doing the above will at least rule out an accidental use of sudo or something.

---

### Post by castiglione on 2011-06-04
I went ahead and erased the xroar directly and unpacked the tar.zip file and went through ./configure and make again.
 
I got an error again but it was different from what I've described above:
 
tools/font2c --array vdg_alpha --type "unsigned int" --vdg ./vdgfont.png > vdg_bitmaps.c
 
tools/font2c: ./vdgfont.png: Unsupported image format
make: *** [vdg_bitmaps.c] Error 1
 
 
I checked the xroar directory and the vdg_bitmaps.h file doesn't seem to have been created at all.
 
I suppose I could try download the tar.zip again in case the copy I have is bad...

---

### Post by SevenMachines on 2011-06-04
> **castiglione said:**
> I suppose I could try download the tar.zip again in case the copy I have is bad...
might be worth a try. you could also check sdl image is installed, its used for the thing thats failing
```
$ sudo apt-get install libsdl-image1.2-dev
```

---

### Post by castiglione on 2011-06-04
I installed the sdl-image file (which is odd because I could have sworn that I had already installed it but according to synaptic, I didn't) and I got the very first error message I described.

Re-downloaded the tarball, unzipped, etc. and got the second error message I described.

This is most strange.

---

### Post by castiglione on 2011-06-04
Just tried again:

After the first make attempt - got the 2nd error message I described.
I attempted a 2nd make attempt without changing anything - got the 1st error message I described.

After the 1st make, there was no vdg_bitmaps.h file.  After the 2nd, there was.

On the positive side, it wasn't locked, i.e. it wasn't "root-root".

Frankly, I'm very puzzled by all this.  It almost makes me long for my old Apple IIe.

:D

---

### Post by SevenMachines on 2011-06-04
Running out of ideas myself, can you post config.log and the full output of make, either in the CODE tags (so its not 7 pages long:) ) or as an attachment, maybe something will stand out

---

### Post by castiglione on 2011-06-04
Ask and ye shall receive:

configure.log and the output of make are attached!

I had to chop make into two parts due to a slight problem of running into the maximum size limit for txt files.

Thank you for your patience and time.

Cheers,

c

---

### Post by SevenMachines on 2011-06-05
you seem to be using a local, custom build of SDL (/usr/local/include/SDL), i'm guessing the issue might lie there. Have you tried using the repository version libsdl1.2-dev? If you really need to use a custom sdl, you might want to look at the compilation options you used relating to png support.

---

### Post by castiglione on 2011-06-05
> **SevenMachines said:**
> you seem to be using a local, custom build of SDL (/usr/local/include/SDL), i'm guessing the issue might lie there. Have you tried using the repository version libsdl1.2-dev? If you really need to use a custom sdl, you might want to look at the compilation options you used relating to png support.
 
I actually have the repository version installed but the I guess the custom sdl is causing problems by "superceding" it.  I'll de-install the custom build and see if that helps.

---

### Post by castiglione on 2011-06-05
I erased the custom builds I had of sdl and sdl-image and that seems to have solved the problem of these version having precedence over the standard builds.
 
However, I'm back to getting the make error I first described.
 
:(

---

### Post by SevenMachines on 2011-06-05
Definitely running out of ideas here. Can you  post the make output of the first error, vdg_bitmaps.c and vdg_bitmaps.h. Also, what version of ubuntu are you on and if your i386 or amd64. The last thing i could try is to reproduce it on a virtual machine and hope it fails in the same way.

---

### Post by castiglione on 2011-06-05
I'm running on as ASUS 1005HA which I believe is an i686.
 
Both the vdg_bitmaps.c and vdg_bitmaps.h files are empty (0 bytes) after my most recent make attempts.

---

### Post by SevenMachines on 2011-06-07
Not really sure of what else to try. You could try running the vdg_bitmap.c/h generating commands by hand and see if that actually does create the right files
```
$ tools/font2c --array vdg_alpha --type "unsigned int" --vdg ./vdgfont.png > vdg_bitmaps.c
$tools/font2c --header --array vdg_alpha --type "unsigned int" --vdg ./vdgfont.png > vdg_bitmaps.h
```

I'll attach the files i get so you can see if you can use them instead, at least you'll know then that this is the problem, which it most probably is :)

---

### Post by castiglione on 2011-06-08
Thank you for looking into this:
I'll give it a go.
Cheers,
c

---

### Post by castiglione on 2011-06-08
Scotty, you're a miracle worker!
 
Mr. Sulu, warp factor six!
 
It worked!
 
:D
 
Thank you very much for your assistance!
 
c

---

### Post by castiglione on 2011-06-08
BTW - when I run xroar, it says:
 
Initialising OSS audio driver
ERROR: Failed to initialise OSS audio driver
Initialising SDL audio driver
     8-bit unsigned, mono, 44100 Hz
 
Should the error message be cause for concern or is everything fine?

---

### Post by castiglione on 2011-06-08
Welp, it installed but I still have problems.
 
LOL.
 
I just did a vanilla "make install"
 
and tried installing the appropriate ROMS in
 
.xroar/roms in my home directory and also in /usr/local/share/xroar/roms (xroar got installed in /usr/local/share/bin) and none of the ROMS have been detected.
 
Any idea of where the ROMS should go?
 
Cheers,
 
c

---

### Post by SevenMachines on 2011-06-09
Sorry, I know nothing about xroar, the manual
[http://www.6809.org.uk/dragon/xroar-manual.shtml#Firmware-ROM-image-names](http://www.6809.org.uk/dragon/xroar-manual.shtml#Firmware-ROM-image-names)
says you can specify this sort of thing with the XROAR_ROM_PATH environment variable but I dont know where it looks by default

---

### Post by castiglione on 2011-06-09
> **SevenMachines said:**
> Sorry, I know nothing about xroar, the manual
[http://www.6809.org.uk/dragon/xroar-manual.shtml#Firmware-ROM-image-names](http://www.6809.org.uk/dragon/xroar-manual.shtml#Firmware-ROM-image-names)
says you can specify this sort of thing with the XROAR_ROM_PATH environment variable but I dont know where it looks by default
 
Oops - sorry, I assumed you knew about xroar.  No worries.  Thank you again for your help!

---

