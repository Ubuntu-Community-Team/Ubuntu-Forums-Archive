---
title: "anybody managed to compile insight3d ?"
date: 2010-10-30
forum: Packaging and Compiling Programs
---

### Post by drBouvierLeduc on 2010-10-30
Hi, 

I'm unsuccessfully trying to compile insight3d -> [http://insight3d.sourceforge.net](http://insight3d.sourceforge.net) , a software able to construct a 3d model out of photographs. 
I installed all the required dependencies, but when I launch **"make"** to compile, I get this error message :

```
 
g++ -O3 -c `pkg-config --cflags opencv libxml-2.0 sdl gtk+-2.0` -I./ann_1.1.1/include/ actions.cpp
In file included from geometry_structures.h:38,
                 from actions.h:28,
                 from actions.cpp:25:
./sift/include/utils.h:159: error: new declaration ‘char* basename(const char*)’
/usr/include/string.h:603: error: ambiguates old declaration ‘const char* basename(const char*)’
actions.cpp: In function ‘bool action_camera_resection(size_t, bool, bool)’:
actions.cpp:108: warning: format ‘%d’ expects type ‘int’, but argument 4 has type ‘size_t’
make: *** [actions.o] Erreur 1

```Any idea where the error could come from ?
I would really like to give this software a try (I have all the pictures ready !)

Running ubuntu 10.10 x64

---

### Post by MadCow108 on 2010-10-30
the problem is that the library seems to define a function "basename" in utils.h which conflicts with the basename function in libc (string.h, see man 3 basename)

check what the basname function in insight does.
If it has the same behavior as the libc the fix would be to just remove the library version (for linux builds).

Else you'll have to rename it.

Also informing upstream about this is always a good idea.

---

### Post by drBouvierLeduc on 2010-10-30
> **MadCow108 said:**
> 
Also informing upstream about this is always a good idea.

Thanks very much for your hints.
By the way, by upstream you mean I should inform the author himself, or via sourceforge's bug tracker ?

---

### Post by MadCow108 on 2010-10-30
upstream usually refers to the original authors or maintainers of the source code.

If they have a bug tracker this is the place to report it.

---

### Post by drBouvierLeduc on 2010-10-30
I managed to fix/hack the first two compilations error, but i'm bumping into yet another one.

So first, as MadCow108 spotted, there was a problem with the function "basename" in the **../sift/include/utils.h** file (conflicting with unix's basename command as I understand)
I had to rename that function and its occurences to something else (eg. newbasename) to make it work.

There was another error a few seconds later, I found the solution in this webpage : [http://www.lewin.nu/~erl/blogs/erls/labels/3d.html](http://www.lewin.nu/~erl/blogs/erls/labels/3d.html)
I had to edit the file **../cv_extensions.ccp**, and change every occurence of **__BEGIN__** to **__CV_BEGIN__** , then **__END__** to **__CV_END__**

Then everything is going fine, but when the program attemps to compile sift, I run into another error (sorry for the long output) :

```
make -C ./sift
make[1]: entrant dans le répertoire « /home/charles/Téléchargements/programmes/insight3d/insight3d/sift »
make -C ./src siftfeat
make[2]: entrant dans le répertoire « /home/charles/Téléchargements/programmes/insight3d/insight3d/sift/src »
gcc -O3 -I../include `pkg-config --cflags opencv` `pkg-config --cflags gtk+-2.0` `pkg-config --cflags gsl` -c utils.c -o utils.o
ar rc ../lib/libfeat.a imgfeatures.o utils.o sift.o kdtree.o minpq.o xform.o
ranlib  ../lib/libfeat.a
gcc -O3 -I../include `pkg-config --cflags opencv` `pkg-config --cflags gtk+-2.0` `pkg-config --cflags gsl` siftfeat.c -o ../bin/siftfeat -L../lib -lfeat `pkg-config --libs opencv` `pkg-config --libs gtk+-2.0` `pkg-config --libs gsl`
siftfeat.c: In function ‘main’:
siftfeat.c:78: error: too few arguments to function ‘cvSaveImage’
siftfeat.c: In function ‘arg_parse’:
siftfeat.c:129: warning: assignment makes pointer from integer without a cast
make[2]: *** [siftfeat] Erreur 1
make[2]: quittant le répertoire « /home/charles/Téléchargements/programmes/insight3d/insight3d/sift/src »
make[1]: *** [siftfeat] Erreur 2
make[1]: quittant le répertoire « /home/charles/Téléchargements/programmes/insight3d/insight3d/sift »
make: *** [sift_detector] Erreur 2
```

I will try to investigate a little, but my knowledge in programation is close to zero !

---

### Post by drBouvierLeduc on 2010-10-30
Ok, the solution to that last problem was simple : 
edit the file **../sift/src/siftfeat.c** and change [FONT=monospace]**cvSaveImage( out_img_name, img);** to [B]cvSaveImage( out_img_name, img, 0);
  [/B]
But then, I have yet another compilation problem ! 
  
  [/FONT]```
siftfeat.c: In function &#8216;arg_parse&#8217;:
siftfeat.c:129: warning: assignment makes pointer from integer without a cast
/usr/bin/ld: skipping incompatible ../lib/libfeat.a when searching for -lfeat
/usr/bin/ld: cannot find -lfeat
/usr/bin/ld: cannot find -lcvaux
collect2: ld returned 1 exit status
```

EDIT : I just realized the problem didn't change from my previous post, as the error message is the same as before minus the "cvSaveImage missing argument" warning.

---

### Post by MadCow108 on 2010-10-30
the cvaux library can be found in libcvaux-dev

the libfeat problem is more interesting, it seems to be compiled by the program itself but then turns out to e incompatible o_O
maybe it got built for 32 bit and the rest for 64 bit?

edit (see edit2 first):
just had a look at this.
the "source" package includes precompiled binaries which aren't recompiled with make.
These binaries are 32 bit binaries, so they are incompatible with the ones you compile yourself (on 64 bit)
So you either have to see if one can recompile the precompiled stuff (as the source seem to be there) or compile in 32 bit mode.
For the former remove all precompiled stuff (find . -name "*.o" | xargs /bin/rm (!!in the insight folder!!)) and compile again.
But you there are more problems ahead (if the library works under 64 bit at all!) :/

To do the latter you have to add the -m32 flag to all the compilation/linking commands in all the Makefiles
And you need g++-multilib package and 32 bit versions of all libraries which it links with and aren't included in the ia32-libs package (opencv, gsl, highgui ...)


Also I'm not sure about adding NULL to cvSaveImage, it seems to expect an array and may not handle the NULL case:
[http://stackoverflow.com/questions/801054/opencv-cvsaveimage-jpeg-compression-factor](http://stackoverflow.com/questions/801054/opencv-cvsaveimage-jpeg-compression-factor)

edit2:
good news, I got it to compile and start :)
remove all precompiled stuff (e.g. find . -name "*.o" | xargs /bin/rm (!!in the insight folder!!)) and just build again

you still need to fix a problem with cvEigenVV (needs 2 more parameters, I think -1, -1 but better check it!)
It will then compile and start, but I did no testing if it actually works.
It may very well fail due to 64 bit. There were quite a few warnings during compile I did not like.

---

### Post by drBouvierLeduc on 2010-10-30
You're right, the problem comes from the Sift library, more precisely from the **libfeat.a** file wich seems to be built for 32 bit, while I'm on 64 bit.
I assume I have to compile this for my architecture myself.
Unfortunately, **make libfeat.a** (as indicated in the doc) returns even more error messages (I post the error only, not the warnings) :

```
imgfeatures.c: In function &#8216;draw_oxfd_feature&#8217;:
imgfeatures.c:369: error: too few arguments to function &#8216;cvEigenVV&#8217;
```

I had a look at the corresponding file, but it seems way more complicated to fix than the previous error... way beyond my knowledge !
This is a bit frustrating as I have the feeling it's the last show-stopper...

---

### Post by MadCow108 on 2010-10-30
adding -1, -1 as arguments should be fine
Unless opencv seriously broke their api this should give the same behavior as was intended by the insight3d author.
I also checked cvSaveImage, the 0 should be ok there too.

Also this was the last error on my system :)

---

### Post by drBouvierLeduc on 2010-10-30
> **MadCow108 said:**
> 
Also this was the last error on my system :)

So I understand you managed to compile this software on your system ?
You're lucky, I still fail miserabily !

First, thanks for your indication, adding -1,-1 as argument worked perfectly.
So, after this fix, the compilation continues a bit, then stop with a very long error output.
I spotted a dozen lines like this :

```
/usr/bin/ld: i386 architecture of input file `./sba/libsba.a(sba_levmar_wrap.o)' is incompatible with i386:x86-64 output
```So I guess it's another x64 incompatibility problem.
What I don't understand is that I can now compile successfully all the 3 libraries the program needs (sift, sba, ann), so they should be 64 bit.

Anyway, that's enough for me... I guess i will have to create my 3d models myself, like a real man !

---

### Post by MadCow108 on 2010-10-30
yes this is again the same 32 bit problem

removing all precompiled stuff should trigger a rebuild for 64 bit when doing a make in the main directory.
you could also touch all the source files to make sure make picks up that it should recompile.

---

### Post by drBouvierLeduc on 2010-10-30
Oh, wait, it's working !
All I had to do was **make clean** in the 3 affordmentioned folders.
As you pointed out, some precompiled stuff were remaining.

Thanks very much for your time, I would never have figured everything out by myself.
I guess I'll be writing some how-to later on so that poeple can try this open-source software on open-source system.

Anyway, I'm off to play with this new toy !

---

### Post by drBouvierLeduc on 2010-10-31
Well, the software is very unstable on linux at the moment, it seems. I couldn't do anything except import pictures.

---

### Post by Interruptor on 2011-01-07
Had the same problems compiling, but successfully running it under wine.

---

### Post by onlymee on 2011-02-15
I have it compiling and running in linux, but it crashes when I start matching.  I get the issue described here and just trying to patch opencv as suggested.  I'll report the result asap.
  
[https://bugs.launchpad.net/ubuntu/+source/opencv/+bug/684302](https://bugs.launchpad.net/ubuntu/+source/opencv/+bug/684302)

---

### Post by phillipude on 2011-02-22
Hi Ubuntu'es

Happy to hear one has got through the jungle of installing Insight3d :P

However, getting OpenCV in costed me 3 hours, as I first found the link now:
[http://opencv.willowgarage.com/wiki/InstallGuide](http://opencv.willowgarage.com/wiki/InstallGuide)
When I write "make" in the subdirectory of Insight3d, I get a gtk2 and a xml2 error as these are not installed (and is -like OpenCV- not part of the repositories). :confused:

Anybody with a safe and easier How-to install Insight for Ubuntu - or a reference to a .deb package, if any? 

Best Phillip

---

### Post by epajarre on 2011-02-25
> **phillipude said:**
> 

Happy to hear one has got through the jungle of installing Insight3d :P

However, getting OpenCV in costed me 3 hours, as I first found the link now:
[http://opencv.willowgarage.com/wiki/InstallGuide](http://opencv.willowgarage.com/wiki/InstallGuide)
When I write &quot;make&quot; in the subdirectory of Insight3d, I get a gtk2 and a xml2 error as these are not installed (and is -like OpenCV- not part of the repositories). :confused:



I started with Insight3dng fork from Sourceforge (notice the ng)

Standard Ubuntu repositories contain OpenCv, gtk2 and xml2, atleast for 32bit on 10.10 release.

The bad news is, it does not work too well, it goes through matching, but crashes on camera calibration, unless I run it under gdb.


   Eero

---

### Post by phillipude on 2011-02-25
Thanks for your reply, Eero !

I did also start with the "Insight3dng fork" and even tried with a .GIT installation without any clue how-to start the application.

> OpenCv, gtk2 and xml2, at least for 32bit on 10.10 release
Well, it is not obvious for me. xml2 is now directly available in 10.10. But as in 10.04 there is only a pyton-opencv and a gtk2-engines, and when trying to compile the Insight3D I keep getting the error that OpenCV is missing (unless I install it through the mentioned link procedure).

Finally, what is gdb?

Best,

Phillip

---

### Post by epajarre on 2011-02-25
> **phillipude said:**
> 

....
 when trying to compile the Insight3D I keep getting the error that OpenCV is missing (unless I install it through the mentioned link procedure).

Finally, what is gdb?




As mentioned I compiled Insight3dng, which - I think - has some Linux support added compared to the original Insight3d.


For Opencv I think I get the relevant libraries if I type "opencv" to the quick-search box in Synaptic package manager. I have installed packages like libcv-dev, libcv2.1, libcvaux-dev and libcvaux2.1.

I had experimented with Opencv before looking at Insight3D so it might have made this easier for me. (But I think I had not added any special package sources, my apologies if this is the case)


gdb is the debugger program by the GNU project. I used it hoping that it would make it easier to understand where the program crashed. It did not directly help....


  Eero

---

### Post by phillipude on 2011-02-26
Hi Eero and other Insight3d interested ):P

Yes, the Insight3dng fork has no file-extentions with connections to microsoft. 

I did get OpenCV to work using the mentioned hard way around - but the others: gtk2 and xml2 (for Ubuntu 10.04), I see no way to get working?

How did you get these inside?

You may try to get OpenCV inside the [http://opencv.willowgarage.com/wiki/InstallGuide](http://opencv.willowgarage.com/wiki/InstallGuide) way and with your gtk2 and xml2 inside, all may work for you?

Best, Phillip

---

