---
title: "Howto: [Edgy] Fix crashes with Xgl+fglrx on r200 cards (e.g., Mobility Radeon 9000)"
date: 2006-10-13
forum: Outdated Tutorials &amp; Tips
---

### Post by misha680 on 2006-10-13
**Open-GL Crashes**

To fix OpenGL crashes change 
```
-accel glx:pbuffer
``` 
to 
```
-accel glx:fbo
``` 
in the Xgl command line. The OpenGL crashes are due to a known bug in fglrx [http://ati.cchtml.com/show_bug.cgi?id=232](http://ati.cchtml.com/show_bug.cgi?id=232). Basically glXCreatePbuffer fails and takes Xgl with it. The solution thus is, as shown above, not to use pbuffer's for glx.

**Non-OpenGL Crashes (e.g., Xgl crashes when moving a window due to wobbly windows crashing Xgl)**

The non-openGL crashes are due to another known fglrx bug where the glDrawArrays function crashes the fglrx driver if a vertex array of greater than 4000 elements is passed to it (see [http://www.gamedev.net/community/forums/topic.asp?topic_id=269117&whichpage=1&](http://www.gamedev.net/community/forums/topic.asp?topic_id=269117&whichpage=1&) this is quite an old bug).

I have made a patch to workaround this bug (attached to this post) and have recompiled an Edgy deb with this patch, which can be found here:

[http://misha680.googlepages.com/xgl-edgy.zip](http://misha680.googlepages.com/xgl-edgy.zip)

Open it with Archive Manager from firefox and then install it.

Misha

p.s. yes this video card is supported by the open source r200 driver with AIGLX, but unfortunately that driver is nowhere as speedy as Xgl + fglrx. 

p.p.s. I made a (very) detailed bug report 
[https://launchpad.net/distros/ubuntu/+source/xserver-xgl/+bug/63830](https://launchpad.net/distros/ubuntu/+source/xserver-xgl/+bug/63830).

---

### Post by misha680 on 2006-10-14
Deleted

---

### Post by misha680 on 2006-10-14
Deleted

---

### Post by tecteun on 2006-10-20
I installed the deb... but still getting crashes, am I doing something wrong?'
by the way: excellent job fixing the fglrx/xgl for my trusty laptop :KS

edit: i'm sorry, complaining too soon, after a reboot all works a lot better than before!  it still crashes though :confused:

---

### Post by misha680 on 2006-10-20
Hmm... so are these crashes like with wobbly windows and openoffice (non-OpenGL applications) or with OpenGL applications (glxgears or google earth, etc). If it's the first, then I need to look into it further (how much video RAM do you have? It might be that the number of OpenGL arrays that fglrx can draw is not really fixed as <4000 but depends on your specific machine, so for me <4000 works great, but maybe for you it has to be <3000 or something). If it is only with OpenGL apps, then it is a different bug that I don't think is related. Anyway, waiting for your reply.

Also the next thing you could do is to start a regular X session, then
type:
```
gdb Xgl 
run :1 -fullscreen -ac -accel glx:pbuffer -accel xv:pbuffer
```

Then open another terminal or a tab in a new terminal (XGl is running but so is your regular X session, so you can use Alt-TAB to switch back and forth between Xgl and the regular X server apps, only trick is that when you switch back to Xgl with Alt-TAB it still thinks you are holding down the Alt key so you need to hit it before you type anything else, otherwise it will act as if the Alt key is pressed). Run emerald & beryl like this:

```

export DISPLAY=:1
emerald &
beryl-xgl &

```

Now run some other apps in the Xgl session, for example:

```

gnome-terminal &

```

Do some stuff until it crashes. Then you can go back to the terminal/tab where gdb is running and type:

```
bt
```

and that will give you a backtrace. Of course it would be more helpful with a version of Xgl compiled with debugging support, which unfortunately is about 10 times as big, but it might be helpful (specifically if the lines aren't __R200TCLDrawArrays than chances are you are having a different bug). 
Misha

---

### Post by tecteun on 2006-10-21
Beryl/XGL crashes back to login when trying to run OpenGL based apps, non-OpenGL apps are fine...

I saw the wobbly windows working, but i cant recreate the same settings, so i only saw it working like twice...
Now moving windows is very slow. Things like rotating the cube and "expose" are really fast..

lspci | grep ati gives 
VGA compatible controller: ATI Technologies Inc Radeon R250 Lf [FireGL 9000] (rev 02)
it has 64 Mb ram.

---

### Post by misha680 on 2006-10-21
Yeah, the opengl crashes aren't supposed to be fixed, just the other ones (I was having a lot of non-opengl crashes on my computer, and I can reproduce one consistently but this fixes it, as well as some other non-opengl crashes I was having). 

Misha

p.s. so, e.g., if you were having any problems with wobbly windows crashes they should be gone.

---

### Post by tecteun on 2006-10-22
> **misha680 said:**
> Yeah, the opengl crashes aren't supposed to be fixed, just the other ones (I was having a lot of non-opengl crashes on my computer, and I can reproduce one consistently but this fixes it, as well as some other non-opengl crashes I was having). 

Misha

Okay, all is clear to me now...

---

### Post by Paerez on 2006-11-03
Hey I wrote a guide for xgl/fglrx with beryl, so I am interested in this fix. However I have no experience in patching source files. I am assuming I have to get xserver-xgl-dev and then compile it somehow?

Also, I am unable to get 3d acceleration in any applications once xgl/beryl is working. For example, I can't run fgl_glxgears or "mplayer -vo gl2" (mplayer using opengl). Do you think this will help or do I have a different bug?

Thanks.

---

### Post by misha680 on 2006-11-03
Yeah, unfortunately this won't fix the GL bug. You could still run 3D apps on the main X server by prefacing the command with DISPLAY=:0 but there won't be any window borders or anything like that.

Basically, to patch a package you'd have to do:

```
sudo apt-get build-dep xserver-xgl
```

This would get dependencies needed to compile it. Then, to get the code:

```
apt-get source xserver-xgl
```

Now it will create a directory with the sources. In that directory, put the patch you want in the debian/patches subdirectory and also edit the list file (I think its something like 00list) and add the filename to the end. Now, you need to increment the verison of the package:

```
dch -i
```

Put in your comments and save the file. Now to compile:

```
dpkg-buildpackage -rfakeroot -us -uc
```

And you will have your debs. Unfortunately, I'm not 100% sure of the package names where you can get some of the d* commands so you will need to play around looking for debian in synaptic (debhelper or something like that is one, also you need build-depend).

Misha

> **Paerez said:**
> Hey I wrote a guide for xgl/fglrx with beryl, so I am interested in this fix. However I have no experience in patching source files. I am assuming I have to get xserver-xgl-dev and then compile it somehow?

Also, I am unable to get 3d acceleration in any applications once xgl/beryl is working. For example, I can't run fgl_glxgears or "mplayer -vo gl2" (mplayer using opengl). Do you think this will help or do I have a different bug?

Thanks.

---

### Post by akshaymodi on 2006-11-10
I am a new user to linux, and I have finally installed beryl. I have logged in under Xgl Session, and it has already crashed once.
I don't understand how I can check if I even have beryl, and how I can check if my Xgl is working properly, and lastly how can I install the patch that you have written.

Thanks in advance

---

### Post by misha680 on 2006-11-10
* Check whether you have beryl - press and hold down Ctrl and Alt keys and press left. Does you see the "desktop cube" rotate? If so, you have beryl installed properly and running.
* Check if your Xgl is working properly? Well, if beryl works and you are using the proprietary ATI drivers (fglrx) then your Xgl must be working as beryl does not work with fglrx without Xgl.
* How to install my patch? I need some more info, are you using dapper or edgy? If you are using edgy, all you have to do is download the modified deb I made using the link I provided in a (much earlier I think) post. Firefox should open it in Archive Manager, and from there you should be able to double click on the "deb" file and it will open GDebi which will let you install it by click on an install button and entering your password.

Btw, what were you doing when it crashed?

Misha

> **akshaymodi said:**
> I am a new user to linux, and I have finally installed beryl. I have logged in under Xgl Session, and it has already crashed once.
I don't understand how I can check if I even have beryl, and how I can check if my Xgl is working properly, and lastly how can I install the patch that you have written.

Thanks in advance

---

### Post by docanime on 2006-11-12
Does the .deb package listed in the first post here contain the most updated patch/fix?

DA

---

### Post by misha680 on 2006-11-12
Yes

Misha

> **docanime said:**
> Does the .deb package listed in the first post here contain the most updated patch/fix?

DA

---

### Post by St3althcAt on 2006-11-12
I can't download the patch! *cry*
It says Geocitie's site unavailable!

Btw, how do I install dpatch file?

---

### Post by misha680 on 2006-11-12
As I mentioned near the URL I think, it's just the way geocities is working. You have to right click, Copy Link Location, then paste it in the address field to go to that address. I think that's how geocities stops people from hosting files on their site. Sorry. But it will work.

Misha

> **St3althcAt said:**
> I can't download the patch! *cry*
It says Geocitie's site unavailable!

Btw, how do I install dpatch file?

---

### Post by blakken on 2006-11-14
> **misha680 said:**
> 

Anyhow, the deb is in a zip file at the following URL (too big to attach):

[http://www.geocities.com/misha680/xgl-edgy.zip](http://www.geocities.com/misha680/xgl-edgy.zip)


:confused: 
your link is no more pointing to any archive ,could you post it somewhere else ?please?
.............sorry It worked like you said with copy/pasting the link ,besides I tried glxinfo in the shell and surprise ........it didn't change a damned thing the x server still crashes!

---

### Post by misha680 on 2006-11-14
I am sorry it did not work for you. Are you experiencing crashes with OpenGL apps (which this is not designed to fix) or otherwise?

THanks
Misha

> **blakken said:**
> :confused: 
your link is no more pointing to any archive ,could you post it somewhere else ?please?
.............sorry It worked like you said with copy/pasting the link ,besides I tried glxinfo in the shell and surprise ........it didn't change a damned thing the x server still crashes!

---

### Post by fsalum on 2006-11-15
Hi Misha!

Do you have any idea how to fix the crash for OpenGL apps?

Here to reproduce the crash I run 'mplayer -vo gl2 file.avi'

and my Xgl crashes coming back to the login screen.

My laptop is a Dell D600 with 32Mb video card below:
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon R250 Lf [FireGL 9000] (rev 02)

Thanks for any help!!!

Felipe

---

### Post by misha680 on 2006-11-15
Hi, unfortunately I currently do not know how to fix this. However, if I have some time, I could look into it, as it would be fairly easy to debug now that I have lots of experience debugging the other crashes. Mplayer with xv actually works great with Xgl, except Edgy uses Xorg 7.1 and Xv does not work at all with the latest version of fglrx drivers for r200 chipsets on Xorg 7.1. As for other opengl apps, you can run them on display :0, i.e.,

```
DISPLAY=:0 google-earth
```

for example, although then you lose the advantage of having a window manager for these apps.

Anyhow, that's all for now. If I have time I will look into it later althoguh I suspect it is yet another fglrx bug that might be "wrapped-arounable" in Xgl but probably cannot really be "fixed."

Misha

> **fsalum said:**
> Hi Misha!

Do you have any idea how to fix the crash for OpenGL apps?

Here to reproduce the crash I run 'mplayer -vo gl2 file.avi'

and my Xgl crashes coming back to the login screen.

My laptop is a Dell D600 with 32Mb video card below:
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon R250 Lf [FireGL 9000] (rev 02)

Thanks for any help!!!

Felipe

---

### Post by fsalum on 2006-11-16
Misha,

I'm using your patch and I followed your howto to use gdb with Xgl, here is the output for the bt command in gdb:

Program received signal SIGSEGV, Segmentation fault.
[Switching to Thread -1212475728 (LWP 10086)]
0xb7f0c520 in glitz_context_make_current () from /usr/lib/libglitz.so.1
(gdb) bt
#0  0xb7f0c520 in glitz_context_make_current () from /usr/lib/libglitz.so.1
#1  0xb7915e03 in xglxUseXorgMsg () from /usr/lib/xorg/modules/xgl/libxglx.so
#2  0xb791b7a9 in xglxUseXorgMsg () from /usr/lib/xorg/modules/xgl/libxglx.so
#3  0xb796e06d in __glXForceCurrent () from /usr/lib/xorg/modules/xgl/libglxext.so
#4  0xb798d403 in DoGetString () from /usr/lib/xorg/modules/xgl/libglxext.so
#5  0xb798d65c in DoGetString () from /usr/lib/xorg/modules/xgl/libglxext.so
#6  0xb796e5d0 in __glXFreeContext () from /usr/lib/xorg/modules/xgl/libglxext.so
#7  0x08089aea in Dispatch ()
#8  0x0809ac89 in main ()

Could this help?

Thanks,
Felipe

---

### Post by shizeon on 2006-11-16
Hello Misha,
  I've noticed that ATI dropped support for the 9000 a couple releases ago.  Are you using the last supported driver for the 9000, 8.28.8 or are you still able to use the newer versions (8.31.5) even without official support? 

Thanks!

---

### Post by misha680 on 2006-11-16
I am using 8.28.8. Haven't tried 8.31.5, I would believe it wouldn't work anymore, but I haven't tried either so I can't be sure.

Misha

p.s. as for the openGL bug I will try to look into it this weekend. The debugging output is helpful fsalum, but unfortunately I will have to recompile the package with debugging symbols (it's actually pretty easy you just have to comment out dh_strip in debian/rules) as that way it gives the actual line numbers in the code and not just the functions.

> **shizeon said:**
> Hello Misha,
  I've noticed that ATI dropped support for the 9000 a couple releases ago.  Are you using the last supported driver for the 9000, 8.28.8 or are you still able to use the newer versions (8.31.5) even without official support? 

Thanks!

---

### Post by fsalum on 2006-11-16
Thanks Misha!!

It will be great to run it without crashing!! :)

---

### Post by DarkWizzard on 2006-11-21
I have the latest beryl and it keeps crashing and crashing no matter what I do.
Your patch made it work better but it still crashes.I hate ati.I'm using the fglrx driver with a radeon card.

Does anyone have any ideea ?

---

### Post by andre_txk on 2006-11-25
Hi! I'm running Dapper right now, but I have the same problem with my video card. I have an ATI Mobility Radeon 9000 of 32 mb and in addition I have 1 Gb of RAM. When I try to start the XGL session the error that gives me is: No display found. Any ideas? Do you know if the patch that you used can be applied to Dapper??

---

### Post by misha680 on 2006-11-28
Hi I think you are having a different error although this patch may be useful later if you get it working and Xgl still crashes. You need to ensure that Xgl is running (you will notice things redraw slower, and also if you do 
```
env | grep DISPLAY
``` in Terminal it should tell you you are running on Display :1). Do you see that?

Misha

> **andre_txk said:**
> Hi! I'm running Dapper right now, but I have the same problem with my video card. I have an ATI Mobility Radeon 9000 of 32 mb and in addition I have 1 Gb of RAM. When I try to start the XGL session the error that gives me is: No display found. Any ideas? Do you know if the patch that you used can be applied to Dapper??

---

### Post by plush on 2006-12-01
Hey Misha, thanks for the patch.  Having some random issues compiling that .deb package (patched).  I think I'm missing some random build tools though I can't identify which.

Can you post a link again to the deb package you made??

---

### Post by plush on 2006-12-01
> **plush said:**
> Hey Misha, thanks for the patch.  Having some random issues compiling that .deb package (patched).  I think I'm missing some random build tools though I can't identify which.

Can you post a link again to the deb package you made??

NEEEEEEEEEEEEEEEEEVERMIND.  It worked.  Great patch!  So far works great.  For wobbly windows set resolution to be like 1 for a super-smooth window.

---

### Post by plush on 2006-12-01
Any way to get rid of that SLOOOOOOOW 2D window open from opening a panel applet?  It looks like how it does on gnome GDM.

---

### Post by plush on 2006-12-01
NEEEEEEEEEEEEEEEEVERMIND.  All I had to do was go in gconf-editor, go into /apps/panel/global _AND_ general
and uncheck "enable animations".  Duh!

---

### Post by misha680 on 2006-12-02
plush, I am glad it is working for you.

Misha

> **plush said:**
> NEEEEEEEEEEEEEEEEVERMIND.  All I had to do was go in gconf-editor, go into /apps/panel/global _AND_ general
and uncheck "enable animations".  Duh!

---

### Post by lid on 2006-12-02
Hi Misha, I'm suffering the same problem. Thank you for your patch that solved the non-OpenGL problem, and I'm eagerly waiting for your solution for the OpenGL bug.

p.s. my graphic card is ATI R9000 pro

Regards.

> **misha680 said:**
> I am using 8.28.8. Haven't tried 8.31.5, I would believe it wouldn't work anymore, but I haven't tried either so I can't be sure.

Misha

p.s. as for the openGL bug I will try to look into it this weekend. The debugging output is helpful fsalum, but unfortunately I will have to recompile the package with debugging symbols (it's actually pretty easy you just have to comment out dh_strip in debian/rules) as that way it gives the actual line numbers in the code and not just the functions.

---

### Post by misha680 on 2006-12-03
Well fyi I did look into the OpenGL crashes for a bit and it seems like it is going to be harder to solve than the non-OpenGL crashes (at least for me, as until I spent a week fixing the non-OpenGL crashes I had never looked at Xgl code). Plus, it seems like this is a less intrusive (though still major bug) as at least there is an easy way to avoid it (don't run OpenGL apps). So I might find a solution, but it will probably be a while as I also have some things in my life going on right now.

Misha

> **lid said:**
> Hi Misha, I'm suffering the same problem. Thank you for your patch that solved the non-OpenGL problem, and I'm eagerly waiting for your solution for the OpenGL bug.

p.s. my graphic card is ATI R9000 pro

Regards.

---

### Post by javaJake on 2006-12-03
I, and others, await this patch as well. Think of us. *sniff* :)

---

### Post by misha680 on 2006-12-04
Alright, so I did a litte more research and for some reason the fglrx driver seems to have errors creating pbuffers (glXCreatePbuffer fails). However, I tried a simple change and it seemed to work at least for glxgears, others maybe can try it with other OpenGL apps and see if it no longer crashes. Simply, when you start Xgl, instead of the option:
```
-accel glx:pbuffer
```
put
```
-accel glx:fbo
```

That's it. Glxgears no longer crashes. Let me know if this works or doesn't work for you.

Misha

UPDATE: Works for mplayer -vo gl2 too.

> **javaJake said:**
> I, and others, await this patch as well. Think of us. *sniff* :)

---

### Post by rogosh55 on 2006-12-06
Hi,
been searching the forum high and low for a fix. I think you might be the person that can help me. 

I am running dapper with xgl and beryl. I also use cedega to play w3 in opengl. I have it working and it looks fantastic but i get random crashes which really sucks when playing team games. Is there anyway the last thing you mentioned can fix my problem? Also, if so how would i be able to start cedega using that? like to start a program with cedega i can just "cedega File.exe -opengl " would I be able to use this at the beginning every time I want to open it?

I would be so grateful for any help as i have posted a couple places with no luck. I am also like 2 months into my Ubuntu only life and I am not very capable of fixing these problems myself. I know you are running edgy but i cant as it kill my framerates in games when using cedega. Anyhow any help would be hugely appreciated.

Dan

---

### Post by misha680 on 2006-12-06
Dan, I am not really that familiar with cedega (other than knowing it is a commercial wine-like program for games), and I was wondering are you running it within Xgl or separately (e.g., on DISPLAY :0 or a non-Xgl session)? If you are running it in Xgl, I am assuming Xgl is crashing, or is it just cedega? I am also assuming you are using an r200-chipset based ATI card?

Misha

> **rogosh55 said:**
> Hi,
been searching the forum high and low for a fix. I think you might be the person that can help me. 

I am running dapper with xgl and beryl. I also use cedega to play w3 in opengl. I have it working and it looks fantastic but i get random crashes which really sucks when playing team games. Is there anyway the last thing you mentioned can fix my problem? Also, if so how would i be able to start cedega using that? like to start a program with cedega i can just "cedega File.exe -opengl " would I be able to use this at the beginning every time I want to open it?

I would be so grateful for any help as i have posted a couple places with no luck. I am also like 2 months into my Ubuntu only life and I am not very capable of fixing these problems myself. I know you are running edgy but i cant as it kill my framerates in games when using cedega. Anyhow any help would be hugely appreciated.

Dan

---

### Post by rogosh55 on 2006-12-06
Sorry i didnt notice this was directed at people with r200 cards. i have an ATI x1400 and im using ATI driver 8.26.18 as newer versions fail the cedega opengl tests(even though opengl is working). 

I am not entirely sure how to get a program running on display:0 and the only guide i found said it crashed ati cards. Therefore i would assume i am running it within xgl. I just installed it and run it during my xgl session. however everything else continues to work fine.

beryl works fine still after warcraft 3 crashes(being run by cedega) so i am assuming that xgl is not crashing. If there is anything else i can tell you to help or some way i can make a log of what is happening when it crashes im willing to do anything.

All i know is beryl functionality is truely the best thing i have seen on a computer in years. 

here is a screenshot of it with me in w3 and spinning

---

### Post by misha680 on 2006-12-07
I agree with you about beryl/compiz, I think it is really awesome and revolutionary (well some parts more than others certainly, but the overall concept). The first thing I would try is running w3 on display :0.

I think for ATI cards running _XGL_ on display :0 may or may not work. However, I am pretty sure running _other programs_ on display :0 should not crash anything. Here's why, basically a little about how XGL works when it is set up the way it normally is for XGL cards:

1. First, the normal Xorg server is started on display :0.
2. Then, XGL is started, and XGl runs as a window on display :0. Any windows that are run on display :1 show up in  the XGl window on display :0. Actually, you can easily see this yourself if you just start a regular (non-XGl) X session (if you still have that capability with your setup) and then you can just run Xgl on the command-line in the terminal, you will see an Xgl window pop up (I think this is actually really neat and did not appreciate the full "power" of Xgl until I had to play around with it like this).

Since Xgl runs as a window on the main X server which runs on display :0 (in the case of an "XGl session" this window is fullscreen, and also there is no window manager which is why you don't see window borders around the Xgl window), it's almost a given that you can run other programs on display :0 (and in the past, before I fixed the OpenGL bug, that is what I did to run OpenGL programs since it would crash Xgl otherwise). To run a program in Display :0, simply open terminal and, instead of typing programname or whatever you type to normally run the program, type:

```
DISPLAY=:0 programname
```

The big disadvantage of this is that basically it will take over the whole screen (Beryl & your cube will be "behind" w3) so you will not be able to use Beryl while you are playing w3. However, if w3 no longer crashes like this, then this points to an issue that has to do with Xgl, and likely one that in theory at least we could deal with because Xgl is open source. However, if w3 still crashes running on DISPLAY :0 (or, for example, if you just ran it in a non-Xgl session, which is the same thing you would be doing here), then the problem likely has to do with the interaction between cedega and the fglrx drivers. This would be harder to fix, as, from what I understand, the source code to cedega is not available.

The other alternative, depending on the problem, could be to create a "wrapper" to the fglrx driver which would basically do the same thing that I did with my Xgl code but would replace not the specific application that crashes but the driver itself, and would basically "correct" the binary fglrx driver. This would actually be a good idea, except I think this might still quite an undertaking for me at this point, as I am just learning (forcibly) about the intricacies of OpenGL thanks to the Xgl bugs that I have experienced.

Anyhow, sorry for the long response. I would first test cedega with w3 running on DISPLAY :0 or a non-Xgl session to see if it is still crashing, and let me know the results.

Misha

> **rogosh55 said:**
> Sorry i didnt notice this was directed at people with r200 cards. i have an ATI x1400 and im using ATI driver 8.26.18 as newer versions fail the cedega opengl tests(even though opengl is working). 

I am not entirely sure how to get a program running on display:0 and the only guide i found said it crashed ati cards. Therefore i would assume i am running it within xgl. I just installed it and run it during my xgl session. however everything else continues to work fine.

beryl works fine still after warcraft 3 crashes(being run by cedega) so i am assuming that xgl is not crashing. If there is anything else i can tell you to help or some way i can make a log of what is happening when it crashes im willing to do anything.

All i know is beryl functionality is truely the best thing i have seen on a computer in years. 

here is a screenshot of it with me in w3 and spinning

---

### Post by rogosh55 on 2006-12-07
hey, just checking this quickly before school, but I warcraft 3 runs fine in cedega under my GNOME session. I will try Display=:0 tonight though but i gotta run right now. thanks a lot!

---

### Post by rogosh55 on 2006-12-07
Okay i have done some testing and i cant get the DISPLAY=:0 to work because i cant open warcraft through cedega from the terminal or cedega crashes my computer ( whole different problem ). So i tested and i get a crash when running in XGL and with beryl and window manager and when using metacity as window manager in XGL. So it seems the problem is clearly related to Xgl in some way as it is fine in GNOME.

Anything else that might help?
Dan

---

### Post by misha680 on 2006-12-07
Well in all honesty if you can't run it from teh command line you are going to have bigger problems, because the next step would be to run it using gdb as follows:
```
gdb cedega
```
and then
```
run everythingyouwouldnormallyputonthecommandline
```
this way, when it crashes, you will be able to type:
```
bt
```
and it will give you a backtrace you can post here which may or may not help figure out what is going on.

Also, have you tried using Wine? I heard people run this game using Wine?

Misha

> **rogosh55 said:**
> Okay i have done some testing and i cant get the DISPLAY=:0 to work because i cant open warcraft through cedega from the terminal or cedega crashes my computer ( whole different problem ). So i tested and i get a crash when running in XGL and with beryl and window manager and when using metacity as window manager in XGL. So it seems the problem is clearly related to Xgl in some way as it is fine in GNOME.

Anything else that might help?
Dan

---

### Post by rogosh55 on 2006-12-07
yeah a couple reasons i dont like wine however. one of the problems i had with wine is it appeared on all my desktops. which is less that ideal because i have to exit w3 to see my desktop again. and loading it isnt exactly a quick option compared to changing workspaces.

yeah when i type for example "cedega Frozen\ Throne.exe -opengl" warcraft 3 starts to load but then it crashes my computer completely. I think it is because i have to have certain settings turned on and off to get it to work properly even using the interface. However, I was getting some help from cedega support but they didnt email me after my last response so im kinda not feeling so good about them getting back to me again. Maybe I will try wine again I dont know. I have had a very frustrating time getting this all working. 

I will try wine again actually and let you know how that goes.

Dan

---

### Post by rogosh55 on 2006-12-07
Okay, i remember now why I didnt use wine. It says it cant initialize OpenGL when im running under Xgl.

I guess ill just have to stick with GNOME for now. Switching workspaces when my game and desktop are the same resolution is still a billino times faster and mroe convenient than it was in windows and I am starting to get very comfortable using multiple desktops. So I will just wait untill I can get cedega working properly or maybe untill I can get cedega running in Edgy at all. 

Thanks for the help though and the ideas. I just wish it didnt tease me by running for 5-10 minutes before crashing.

Dan

---

### Post by jenesuispasbavard on 2006-12-10
I think I got it.
I was messing around with the settings in Beryl Settings Manager, and this is the configuration I'm currently using (see attachment). Unzip the .profile file, then start Beryl Settings Manager and choose Import... at the bottom.
I can now move windows just like I did in Ubuntu 6.06 with Compiz.
Thanks to Misha for the patch (install the patch first, then use these settings),
Chirag

P.S. I'm not sure if this has been done before, so I'm sorry if I'm doing something that's already been done.

P.P.S. Does the Mobility Radeon 9000 support full-screen anti-aliasing with Beryl and OpenGL? I'd like to see smooth edges when I move my windows.

---

### Post by lid on 2006-12-11
Hi, Misha

After apllying the patch, it hasn't crashed. But when I run 'glxinfo', there seems some problems, the biggest one is, the direct rendering doesn't work. When I turned back to the gnome session without xgl, it goes all fine. The attachment is the glxinfo outputs under the two sessions, can you give me a suggestion of the problem?

Thanks

---

### Post by misha680 on 2006-12-11
Hi lid,

I am glad the patch stopped your crashes. As for the glxinfo direct rendering, this is the correct behavior. If you'd like to see that the Xgl output itself is actually being direct rendered just look at the output of:
```
DISPLAY=:0 glxinfo
```
Basically, everything that Xgl draws on DISPLAY :0 _is_ direct rendered. However, what is drawn by programs _on_ the Xgl display (DISPLAY :1) cannot be direct rendered (well, it could, I guess, but that is not the way Xgl is implemeneted). Basically, the way I understand it when OpenGL output is drawn to DISLAY :1 it is drawn on offscreen buffers which then are sent to be shown on DISPLAY :0 along with other screen info. Anyway, that's kind of a bad explanation, but the bottom line is what you are seeing on glxinfo is correct.

Misha

> **lid said:**
> Hi, Misha

After apllying the patch, it hasn't crashed. But when I run 'glxinfo', there seems some problems, the biggest one is, the direct rendering doesn't work. When I turned back to the gnome session without xgl, it goes all fine. The attachment is the glxinfo outputs under the two sessions, can you give me a suggestion of the problem?

Thanks

---

### Post by BOBSONATOR on 2006-12-30
Misha, let me tell you once again, you rock.

The wobbly windows work fine, but its not 100% all the time. Soemtimes when i log in the windows wobble, but they are very stuttery, do you have  a fix for that?


Thanks a bunch!

---

### Post by misha680 on 2006-12-30
> **BOBSONATOR said:**
> Misha, let me tell you once again, you rock.

The wobbly windows work fine, but its not 100% all the time. Soemtimes when i log in the windows wobble, but they are very stuttery, do you have  a fix for that?


Thanks a bunch!

I believe this may be pretty much a consequence of the way I am working around the bug
of drawing vertex arrays with > 4000 vertices. The way I am getting around this is by
drawing ~4000 vertices at a time, and thus I would assume it would be stuttery all the
time (don't use wobbly windows myself, but had crashes doing other stuff before I 
implemented this). In any case, I will think of any other possible solutions, but I think
for now your best bet might be to play with Beryl settings with regards to wobblyness.

Misha

---

