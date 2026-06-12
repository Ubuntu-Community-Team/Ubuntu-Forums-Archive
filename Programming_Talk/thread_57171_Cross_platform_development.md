---
title: "Cross platform development"
date: 2005-08-15
forum: Programming Talk
---

### Post by ~J~ on 2005-08-15
Hiya Linux experts...

Quick question that hopefully has a simple answer...

If I develop a graphical demo (similar to the ones you saw in the 80's 90's on Amigas), and I develop this in Visual Studio on Windows, and providing I don't use DirectX but OpenGL, could I then take the code and compile it under Linux and it still work?

Likewise, if I develop the demo in Linux, could I take the source, compile it in Windows, and run it?

TIA

---

### Post by PeP on 2005-08-15
Depending on what widget you use it might be easier or more difficult, if not impossible.
If you use no graphic widgets, it will be easier to port if you do not use VC, because VC creates projects without makefiles and you will have to make one.


If you just want a 80's like demo, why not use java ?

---

### Post by LordHunter317 on 2005-08-15
It depends on how many Windows platform SDK calls you make.  

OpenGL itself is portable, most of the stuff you'll use around it won't be.

---

### Post by ~J~ on 2005-08-15
Hi PeP, thanks for the reply.

First answer is the Java.  I don't know Java (not a great deal anyway), and the Demo is for a band's promo video so it needs to be fast which I don't think Java has.  Likewise the demo will probably appear on a CD and I know there are still a fair few people that don't want to download the VM just to run Java.

As for the second part, I'll admit, I'm totally lost about the "Widgets" part.

I'd have thought (and my ignorance on this maybe showing) that if I code it in C++ using OpenGL (all industry standards), then I 'should' be ok.  If I were to do something machine or OS specific, then obviously I'd hit problems, but C++ calls to create, say, a square on the machine and twist it this way and that, I'd have thought should be universally standard.

I could avoid using VS2003 altogether and use an alternative (I do like the IDE of VS though ;))

Like I said, this is totally new to me (the cross-platform, not the coding) and I really appreciate the comments.

---

### Post by LordHunter317 on 2005-08-15
[QUOTE=~J~] and the Demo is for a band's promo video so it needs to be fast which I don't think Java has.[/quote]You could make it fast.

A better solution sounds like to get Macromedia Flash or Shockwave, and use that.  That gives you Mac and Windows anyway, though doesn't work for Linux.

Otherwise, I'd just record an .AVI in some sort of common codec, and set it to autoplay.  That'd work pretty much anywhere.

> I'd have thought (and my ignorance on this maybe showing) that if I code it in C++ using OpenGL (all industry standards), then I 'should' be ok. The problem is, your application will need stuff that goes beyond what OpenGL provides, and what C++ provides as standard.

---

### Post by PeP on 2005-08-15
hum...
To be exact flash player does work for linux while there is no flash IDE from macromedia.

The widgets are buttons/checkboxes/frames/... lots of graphic stuffs.

For VS2003 it is intuitive and comes with a good debugging environment, I am also pretty sure it is possible to make an app for linux with it but that it would be a hell to configure it accordingly.

If you want an interactive demo for a band with movies and sound ... use flash it is a higher level language and the ime you'll  learn it is certainly worth the time you'll spend to get something similar from C++ (especially if you don't know about widgets)

Also, java is not so slow! 
If you are not so familiar with c++,you're likely to make faster java program:
 Since you won't be able to write a well optimised program which uses the full possibilities of c++ to beat the java equivalent the use of a higher level programation language will be worth the "alledged" slowdown.

---

### Post by johanvdw on 2005-08-15
You provide only very little information on the type of project you want to make and the time you want to spend on it. Nowadays, I think Flash would be the best choice for many projects if you are not a real programmer or want to concentrate on content rather than programming.

If you really want to use C++ you have to use a widgets library. One that also supports opengl is wxwidgets:
[http://www.wxwidgets.org/opengl.htm](http://www.wxwidgets.org/opengl.htm)
Some programming tools make it easy to compile on different platforms:
I myself use Chinook:
[http://www.degarrah.com/chinookfree.php](http://www.degarrah.com/chinookfree.php)
There are other applications as well, you can check at:
[http://www.wxwidgets.org/](http://www.wxwidgets.org/) (check under resources>applications, because the site is frame-based I cannot give a direct link).

---

### Post by ~J~ on 2005-08-15
OK, well it's certainly given me a bit more scope on things, many thanks for the help.

As for the project itself, well like I said, it's a band/groups promo for a 'gig' to be held in Manchester in September.

In short they have about 25 (5x5) screens which they want some kind of 'interactive' music demo.  Basically they'll be playing the music whilst some fancy eye candy goes off in the background.

The CD has a selection of tracks, and they'd like a collection of graphics demos, again similar to the old Amiga ones, whilst some music is playing in the background.  Ideally, and I doubt I'll have the time to do this seeing as the gig is only a month away, but they'd like the CD's to be "different", having both music and a small selection of demos/games/utilities.

The flash side of things I can probably handle, but I was hoping to go down the C++ route, coding something for both Windows and Linux users to have.  For example I'm in the middle of coding a scene that takes you through a labyrinth, twisting this way and that, and I just thought it would be nice if the Linux users could benefit seeing and hearing something different.

Thanks again for the help though, seriously, it's appreciated.

---

### Post by PeP on 2005-08-15
you're welcome:

Remember that flash _will_ play on a well configured linux.

If you have an interactive labyrinth in c++ that compiles with gcc, then it is easy to make the linux thing but:
will you make a .deb for debian, a .rpm for mandrake/redhat an ebuild for gentoo ?
If not you will have to make a beatifull tarball with all the configure scripts, but seriously, ask yourself if it is worth making it for the small percent of linux users in your public?

Another option would be to just check that it works with wine ...

Last but not least, if you can make an interactive labyrinth in c++, can't you make an eye candy interactive thing in flash?

---

### Post by LordHunter317 on 2005-08-15
[QUOTE=PeP]If you have an interactive labyrinth in c++ that compiles with gcc, then it is easy to make the linux thing but:
will you make a .deb for debian, a .rpm for mandrake/redhat an ebuild for gentoo ?
If not you will have to make a beatifull tarball with all the configure scripts, but seriously, ask yourself if it is worth making it for the small percent of linux users in your public?[/quote]He'll be distributing a binary, not source, so he won't have to do any of this.

---

### Post by PeP on 2005-08-15
that's what I am saying, you'll have to distribute a binary for each distribution (it's not compatible ... eg: are you sure that you'll just find the GL libs in the same place? If you use glut for it is cross platform, the libs for it might just not e installed ) ...

---

### Post by LordHunter317 on 2005-08-15
[QUOTE=PeP]that's what I am saying, you'll have to distribute a binary for each distribution[/quote]Not really no, though you may have to wrap some things.

The biggest issue would be C++ compatibility, and that'd be solved quite easily by using only GCC-3.3 and libstdc++5.

>  (it's not compatible ... eg: are you sure that you'll just find the GL libs in the same place?Won't have to worry, the path isn't encoded, and if libGL isn't on the library search path, it's not worth dealing with.

---

### Post by ~J~ on 2005-08-15
Well this is gathering pace - lol!

OK, here's a question then.

There are a lot of programs these days that are available in both platforms.  I say "available" rather than cross-platform as the literal sense of the word would mean the same program could be run on both OS's.

So taking Blender3d as an example, which I imagine is wrote in C++.  Does this mean that if this program had 3,000 lines of code for Windows, that some Linux developer would need to go through those 3,000 lines and change certain 'things' to make it run under Linux?

---

### Post by LordHunter317 on 2005-08-15
[QUOTE=~J~]So taking Blender3d as an example, which I imagine is wrote in C++.  Does this mean that if this program had 3,000 lines of code for Windows, that some Linux developer would need to go through those 3,000 lines and change certain 'things' to make it run under Linux?[/QUOTE]Yes, though one in C++ would generally abstract those details, and have different implementations of the same interfaces.

---

### Post by ~J~ on 2005-08-15
Right, think it's starting to make sense now.

Well, at least I know for the future.

I have to say, as yet I haven't seen any application (free or paid) that beats the IDE of VS, but I "AM" determined to do some development on Linux so at least I know where to come in the future...!

A CyberPint on it's way to you all...

---

### Post by jsimmons on 2005-08-15
[QUOTE=LordHunter317]He'll be distributing a binary, not source, so he won't have to do any of this.[/QUOTE]
 I just started a project to convert a 500,000+ line C++ project to be cross platform. I chose wxWidgets because it's fairly MFC-like, so I understand the basic structure of the framework.  It also includes opengl "widgets" (what C++ programmers call " classes").

For an IDE, I'm starting with CodeBlocks.

This whole process is new to me as I'm also moving from Visual Studio (6.0), and it's been quite a battle getting a simple wizard-generated app to even compile in CodeBlocks.  But it's finally working and I'm now off and running.

The resulting code conversion should allow us to run on any platform supported by wxWidgets (*nix, Windows, Mac OS/X, etc) with little/no changes.

---

### Post by jsimmons on 2005-08-15
[QUOTE=~J~]Well this is gathering pace - lol!

OK, here's a question then.

There are a lot of programs these days that are available in both platforms.  I say "available" rather than cross-platform as the literal sense of the word would mean the same program could be run on both OS's.

So taking Blender3d as an example, which I imagine is wrote in C++.  Does this mean that if this program had 3,000 lines of code for Windows, that some Linux developer would need to go through those 3,000 lines and change certain 'things' to make it run under Linux?[/QUOTE]

If the program was designed with cross-platform requirements in mind, then the impact would at least be minimized to include just the user interface portions.

---

### Post by LordHunter317 on 2005-08-15
No, it wouldn't.

The UI is generally the eaisest portion to workaround if you're planning with it mine: just use a cross-platform toolkit.

It's primitives like threads, IPC constructs, sockets, memory management that aren't the same and a PITA to deal with.

---

### Post by dcraven on 2005-08-15
If the demo is going to be 2D for the most part, have a look at the SDL. It's quite portable and handles everything from sound to video and user input. It's wrapped in many languages including some quick to develop ones like Python (pygame). If you still like C++, then perfect. SDL is still a good solution. There are many extensions available that add things like GUI widgets and so forth too.

I don't know if it is exactly what you're looking for, but I thought it was worth a mention.

~djc

---

