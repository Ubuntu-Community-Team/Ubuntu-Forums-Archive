---
title: "starting a Kdeveloper OpenGL application port"
date: 2008-06-13
forum: Programming Talk
---

### Post by Clive McCarthy on 2008-06-13
I have an OpenGL C application that is running on XP which I developed using and old Borland 6 compiler. I want to port the application to Ubuntu. I've installed build-essential, kdeveloper, automake etc. but things seem somewhat messy. There always seems to be just-one-more-package to add.

Whenever I ask Kdeveloper to build the project I get a dialog box that asks me if I want to run automake which seems redundant. Clearly I haven't got my set-up configured properly. I also get a warning that AM_PROG_LIBTOOL is not found in the library -- I'm thrashing and I don't have a clue.

I'd like to move ahead quickly, there is obviously a lot of _actual_ porting work to be done. I haven't even figured out how to add C files to the IDE's (make system's ?) list of files in the project.

:confused:

---

### Post by Vadi on 2008-06-15
Here's how things stand, as I think, in Linux. There's the old, confusing, but very reliable and still majorly used Makefile system. Making makefiles isn't exactly fun because it has very strict syntax rules and a huge manual you're supposed to read.

The new systems that have come out are cmake and scons. Both are cross-platform, with cmake being recently chosen by the kde project, and scons being used by id Software (or so scons's front page says). Look into both for your project needs.

I'm not sure if there's a GUI for configuring either, as I've never used either of them, so I can't help you much there unfortunately.

---

### Post by Clive McCarthy on 2008-06-16
I've started with Kdevelop and have, over a couple of days, gotten quite far. The current problem I'm having is figuring where Ubuntu has put the libtiff, libjpeg, and libglut stuff, and what the files are actually called! For all the electro-magic of Kdevelop and the library retrieval process, specifying the libraries is clunky with Kdevelop/GCC.

Some help with this would be good.:popcorn:

Of course I have to whine a bit too:

I was also bemused that GCC needed a -lm flag to use the math library. This is clearly an anachronism. I was at first very perplexed by errors from ceil(), floor(), sqrt() calls despite including math.h -- I thought it was a C99 issue. The payload of the math library can't be that heavy so I wonder why Kdevelop doesn't have the flag on by default?

Makefiles are fine, but they are simply a hangover from the days when a clean build of a large project took overnight. The speed of modern machines means that compiling a million lines is a snap (BTW, my project doesn't have a million lines).
:KS

---

### Post by Vadi on 2008-06-16
Well, installing libtiff4-dev, libjpeg62-dev, and libglut3-dev should do it. The installed files go into /usr/include I think, and that location is searched automatically.

If it's not a secret, what does your app do?

---

### Post by Clive McCarthy on 2008-06-16
Are you sure the libs go into usr/include and not usr/lib? I'm having a silly difficulty finding and identifying the lib files. I started using the browser tool but couldn't find my own nose with both hands... I began to wonder if it implicitly did recursive searches? Anyhow, I reverted to the command line console went to the root and did: 
ls -R libtiff* 
and still couldn't find stuff... user error, I'm sure. :(

I need to put the explicit directory path and library names on GCC's command line. Kdevelop isn't too helpful with this.

My application is a small program to display artwork. I'm an artist (though I had a long career working with software & hardware) and my program displays sequences of images (jpeg and tiff) on computers embedded behind LCDs. There is no user interface, just a power button! I'm using mini-itx format computers running XP and soon, with luck, Ubuntu...

I had been using Macromedia/Adobe's Director but it's an orphan product. So recently I built an OpenGL system running on XP. You can see the kind of work I do at:
[www.FourteenthStreetStudio.com](www.FourteenthStreetStudio.com)
The images usually start as photographs but I run them though my own filters and then assemble sequences using various transitions. The images slowly transition one into another. As artwork it lies somewhere between still photography and video/film.

The error code I get is "Exit with status 77" and when I look in the config log it says it can't find the lib file provided on the GCC command line.

---

### Post by Vadi on 2008-06-16
Try using -ltiff or something like that to link against a library, it should find it automatically.

I think for example for a program that required curl, I did gcc -lcurl.

---

### Post by Clive McCarthy on 2008-06-16
Yes, that worked -- Kdevelop now configures OK. So I now have:
gcc -O0 -g3 -lm -ltiff -ljpeg -lglut
whereas I had been trying to give the compiler the _exact_ filename.
It's a case of the interface being TOO helpful...

thanks!

On to the next problem...

---

### Post by Vadi on 2008-06-16
You're welcome.

---

### Post by Clive McCarthy on 2008-06-17
...and so the next problem:

My application runs! That's the good news. :KS However, I'm not happy with how Kdevelop works with OpenGL -- it seems that Kdevelop's own window clean-up/refresh isn't robust :(. It's windows, once corrupted, stay dirty until the target application exits. In my case my code switches an OpenGL window from full screen to normal and Kdevelop goes mega-UGLY. Further it seems that Kdevelop hijacks stdout rather that letting the application talk to it's own console window.

I'm new to Linux C development so I'm hesitant to drop the use of an IDE. My project has only a small number of source files and three libraries so I hardly care about automake. I could script a simpler build process myself -- a clean build takes only a few seconds and it's all ANSI C. I read a posting about Anjuta from February 2007 which doesn't encourage me in that direction. There is GTK+ and Eclipse to try. 

Does anyone have experience of these other IDEs with OpenGL & glut?

In Ubuntu/Linux does OpenGL/glut's **glutFullScreen()** really go full screen (no framing or title bar) as it does on XP? Is it Kdevelop that is "containing" the OpenGL window as a child? Conversely, when not full screen, my OpenGL window has no title bar so I can't see the results of calls to **glutSetWindowTitle()** -- is this Kdevelop at work too?

Should I be using **glutGameMode()** instead of **glutFullScreen()** ?

I realize these are VERY specific questions about the interactions of Ubuntu/Kdevelop/OpenGL/glut but not so obscure I hope? Maybe I should post this to the Ubuntu gamers?

---

### Post by Vadi on 2008-06-17
Try Geany for an IDE, I like it better.

I don't know about glut, but try reposting it in the Programming Talk ([click]("http://ubuntuforums.org/forumdisplay.php?f=39")) section. This thread isn't exactly in the proper place :/

---

### Post by Clive McCarthy on 2008-06-17
I've posted my glut questions as you suggested. I'll try geany (light brown hair?)

How do you get make to work in Geany or do you simply add the object file names to the build list?

I did just that. There are only eight source files and three libs so the gcc command line is fine. It's a MUCH cleaner tool than Kdevelop. Thank you for the recomendation. I get a separate OpenGL/glut window and a simple console window with my own diagnostics that go to stdout.

---

### Post by Vadi on 2008-06-17
Glad you got it working. And doing shift+f9 makes geany execute "make" in the folder, so I use that to compile things.

Then you can even double-click on an error and it'll take you to that line, a very useful thing I found. If you'll have any more geany questions, I recommend joining the #geany channel on IRC - it's very helpful.

---

### Post by Clive McCarthy on 2008-06-17
I like Geany it's simple and clean. When I run the OpenGL code it behaves properly: I get a graphics window and a console window.

I have eight source files and three libs and it's not difficult to put them all on the gcc command line. The only unfortunate habit Geany has, is that it names the executable after whichever source tab is open. Not a big deal.

For a project this size it is all I need. I'll get a gcc manual and study up on the flags I want. I like it too because it doesn't blend compiling with linking. Though there may be some advantages to such an approach, I find it easier (perhaps simply more familiar) to deal with syntax issues and only then to deal with linkage issues.

It does seem that glutFullScreen() under Linux does NOT fill the entire screen. At least with Geany I get a proper window with frame. I shall have to delve into using glutEnterGameMode() which is guaranteed to be full screen, whereas the definition of glutFullScreen() allows for some interpretation...

Your advice has been most helpful.
:popcorn:

---

### Post by 23meg on 2008-06-19
Moved to Programming Talk.

---

