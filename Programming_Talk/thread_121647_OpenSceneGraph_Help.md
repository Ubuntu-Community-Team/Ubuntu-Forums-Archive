---
title: "OpenSceneGraph Help"
date: 2006-01-25
forum: Programming Talk
---

### Post by Grae on 2006-01-25
I'm trying to program in C++ with OpenSceneGraph but as yet haven't been able to get very far. It seems the Ubuntu package of OpenSceneGraph doesn't install things in the same place as installs on most other systems. 

so far I've added a few things to .bashrc

```
export PATH=${PATH}:/usr/include
export LD_LIBRARY_PATH=${LD_LIBRARY_PATH}/usr/lib
export OSG_FILE_PATH=/home/grae/OpenSceneGraph-Data:/home/grae/
OpenSceneGraph-Data/Images 
```

but when tring to compile this:

```
#include <iostream>
#include <osgProducer/Viewer>


int main (int argc, char* argv[]) {
	// Create a Producer-based viewer
	osgProducer::Viewer viewer;
}
```

I get these errors:

```
main.cpp:14:2: warning: no newline at end of file
/tmp/ccYRTWT2.o: In function `main':
main.cpp:(.text+0x2a): undefined reference to `osgProducer::Viewer::Viewer()'
main.cpp:(.text+0x3c): undefined reference to `osgProducer::Viewer::~Viewer()'
collect2: ld returned 1 exit status
```

please does anyone have any ideas?

---

### Post by Grae on 2006-01-26
Almost 24 hours and no reply? :-( 

Surely someone must have some idea?

---

### Post by Grae on 2006-01-27
Fixed it!

Needed to add libs to my make line:

g++ -losg -losgProducer -lProducer -lOpenThreads main.cpp

hope this helps someone in the future

---

### Post by tappad on 2006-02-07
Hi, i have never compiled a c++ projekt ever under Linux.
Maybe a complete noob question but, where is this .bashrc located?

---

### Post by hod139 on 2006-02-07
[quote=tappad]Hi, i have never compiled a c++ projekt ever under Linux.
Maybe a complete noob question but, where is this .bashrc located?[/quote]

The .bashrc file is a hidden file located in your home dir. you can type 
```
ls -a
```
to show all files, and you will see your .bachrc.  Although, you shouldn't have to edit this file to compile code in linux.  It is sometimes useful for setting PATHs, but you generally don't need to do this.  As Grae found out, the problem wasn't with the paths, but with not telling gcc to link the libraries.

---

### Post by tappad on 2006-02-21
Okay, unfortunatly i couldnt get it working doing what he did (Without the Path's).
However, i do belive that they are nessesary for OSG to compile. I have a couple of OSG projects behind me using Visual Studio C++. And i remember it was a complete hell to set up the system, had to dodge linker-errors every now and then.

Don't really have time to read all the manuals and faq's on how to get it working in linux :(
Allthough it would be nice to make my projects somewhat cross-platform..
So, as Grae seems to succesfully compile an OSG-project under ubuntu i was Hoping, maybe he could give me a short howto :)

In Visual Studio you had to compile the core first to get it working, plus setting som Path vars.. Don't know if i need to/how to do this in ubuntu, except using get-apt install openscengraph.

All the best to you!

ps.
What is the 'best' c++ editor & compiler?
Want it easy a'la Visual Studio, no kommander-line compliers (eg. editor takes care of that part)
ds.

---

### Post by sunfisher on 2007-01-02
I've been trying to use openscenegraph and had problems w/ the binaries as well as an error in compiling version 1.2 (listed below). The problem w/ the binaries is similar between my desktop, laptop and the machines at work. All problems with detecting vertical sync.

My compile error is as follows:
g++ -O2 -L/usr/X11R6/lib -L../../../lib/Linux32 OrientationConverter.o osgconv.o -lstdc++ -losgProducer -lProducer -losgText -losg -losgUtil -losgGA -losgDB -lGLU -lGL -lOpenThreads -o osgconv
../../../lib/Linux32/libosgProducer.so: undefined reference to `Producer::PipeTimer::_thePipeTimer'
../../../lib/Linux32/libosgProducer.so: undefined reference to `Producer::Camera::FrameTimeStampSet::~FrameTimeSt ampSet()'
../../../lib/Linux32/libosgProducer.so: undefined reference to `Producer::PipeTimer::setReturnType(Producer::Pipe Timer::ReturnType)'
../../../lib/Linux32/libosgProducer.so: undefined reference to `OpenThreads::GetNumberOfProcessors()'
collect2: ld returned 1 exit status

Can anyone run the demos w/ osgviewer from the installed binaries? Any suggestions?
Thanks,

---

