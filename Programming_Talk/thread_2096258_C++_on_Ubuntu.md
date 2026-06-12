---
title: "C++ on Ubuntu?"
date: 2012-12-19
forum: Programming Talk
---

### Post by JayWash124 on 2012-12-19
So, I'm thinking of switching to Ubuntu but one of my concerns is that I wont be able to program C++ (as I'm just starting to learn it).
 
I don't mean that I dont think it'll work completely, rather that specific lines of code may or may not work, because the book I have does everything under Windows.
 
Does the OS make a difference?

---

### Post by akvino on 2012-12-19
> **JayWash124 said:**
> So, I'm thinking of switching to Ubuntu but one of my concerns is that I wont be able to program C++ (as I'm just starting to learn it).
 
I don't mean that I dont think it'll work completely, rather that specific lines of code may or may not work, because the book I have does everything under Windows.
 
Does the OS make a difference?

The OS makes all the difference in the world. In essence you will learn how to REALLY use C/C++. 

Get the latest gcc / g++ compiler, learn vim, and throw that book out of the window (really keep it, it's good to know multi platform implementations).

---

### Post by patrick-epl15 on 2012-12-19
The OS will make a difference. But it also depends on the book you are using. Some teach you to use Microsoft Visual Studio and the MS way,  Some books let you use any editor/ide of your choice and keep the programming OS agnostic.

---

### Post by JayWash124 on 2012-12-19
> **akvino said:**
> The OS makes all the difference in the world. In essence you will learn how to REALLY use C/C++. 
 
Get the latest gcc / g++ compiler, learn vim, and throw that book out of the window (really keep it, it's good to know multi platform implementations).
 
Um well I plan on keeping the book XD as it was $50 and I JUST got it. I guess I'll learn it on windows first, then when I have an understanding of it (a few years) then I'll move on to different platforms.

---

### Post by GeneralZod on 2012-12-19
What book is it?

---

### Post by dwhitney67 on 2012-12-19
> **JayWash124 said:**
> Um well I plan on keeping the book XD as it was $50 and I JUST got it. I guess I'll learn it on windows first, then when I have an understanding of it (a few years) then I'll move on to different platforms.

It shouldn't make a difference as to whether you learn ISO C++ on Windows or Linux.

So whether you use M$ Visual C++ or GCC (GNU Compiler Collection), it should not matter.

PS.  ISO = International Organization for Standardization

---

### Post by DTSDeveloper on 2012-12-19
if your just starting out learning c++, then your probably fine. i could be wrong but usually its just high level c++ and nothing low level. the exes youve made wont import, but your code should. if youve used libraries like windows or conio, done any win32, written drivers or things like that, then the code wont work but you should be fine

---

### Post by mysteriousdarren on 2012-12-19
If your looking to use just one program vim, and the before mentioned programs work well. I have always used Dev-C++
[http://www.bloodshed.net/dev/devcpp.html](http://www.bloodshed.net/dev/devcpp.html) and never had any trouble. 
It works in Ubuntu with the use of Wine, and Windows. It's free and works great for just learning.

---

### Post by akvino on 2013-01-22
> **JayWash124 said:**
> Um well I plan on keeping the book XD as it was $50 and I JUST got it. I guess I'll learn it on windows first, then when I have an understanding of it (a few years) then I'll move on to different platforms.

Here is a good book for any platform:

[http://www.amazon.com/C-Primer-Plus-5th-Edition/dp/0672326973](http://www.amazon.com/C-Primer-Plus-5th-Edition/dp/0672326973)

---

### Post by xb12x on 2013-01-22
If your reasons for learning C++ are career based, then stick with Windows for now. You're much more likely to have opportunities to work in a Windows environment than a Linux environment.

But if your reasons are not career based, keep in mind that Microsoft wants money for _everything_ you'll need, all tools, etc. In the Linux world everything you'll need is open-source and easily and freely downloadable, and well supported.

---

### Post by dwhitney67 on 2013-01-22
> **xb12x said:**
> If your reasons for learning C++ are career based, then stick with Windows for now. You're much more likely to have opportunities to work in a Windows environment than a Linux environment.

That's baloney.

I've worked on Unix and Linux systems all my career (20+ years), and only for a 6 month stint on Windows.

It really all boils down to what area of software one pursues.

---

### Post by xb12x on 2013-01-22
> **dwhitney67 said:**
> I've worked on Unix and Linux systems all my career (20+ years), and only for a 6 month stint on Windows.

I'm sorry to hear that. You have my sympathies.

---

### Post by Herbon on 2013-01-26
...

---

### Post by Liukcairo on 2013-01-26
I've started C++ programming back on a WindowsXP machine and had taught myself quite literally everything using Irrlicht as my experimental playground. Albeit I'm still not really all that great, I hope I can still provide advise: 

[quote="JayWash124"]
So, I'm thinking of switching to Ubuntu but one of my concerns is that I wont be able to program C++ (as I'm just starting to learn it).
[/quote]

As noted by some of the other posters, unless you're working with OS specific implementations such as DirectX, the windows API, whatever API OSX uses, etc as these are nonexistent in a Linux environment then your C++ code as far as I can tell should work on mostly any OS with an update-to-date C++ compiler.

[quote="mysteriousdarren"]
If your looking to use just one program vim, and the before mentioned programs work well. I have always used Dev-C++
[http://www.bloodshed.net/dev/devcpp.html](http://www.bloodshed.net/dev/devcpp.html) and never had any trouble. 
It works in Ubuntu with the use of Wine, and Windows. It's free and works great for just learning.
[/quote]
My IDE of choice for simplicity was [Code::Blocks]("http://www.codeblocks.org/") as it has a native binary for OSX, Linux and Windows.

As a lone programmer I've found it easier to pick systems and libraries for my work that are pretty agnostic of the target system such as rendering engines that make use of software/OpenGL rendering or at least provide a method of using DirectX or OpenGL. Obviously they probably won't do too much for your own learning, but they how are I learned so I suppose you can get to using these once you sharpen your skills in C++ enough.

Some cross-platform libraries you may be interested in when you get to that point (please note my efforts are mainly in the gaming area and I do not really know what you're wanting to get into, so all of these suggestions here are what I've ran into myself):
[Irrlicht]("http://irrlicht.sourceforge.net/") - realtime rendering software, works on just about any system.
[OGRE]("http://www.ogre3d.org/") - this is also realtime rendering software but is considerably harder to use than Irrlicht but would be worth the time to learn how to use.
[irrKlang]("http://www.ambiera.com/irrklang/") - an audio playback system this is easy to use and cheap for commercial use.

If you're wanting to be extreme, you can try FreeGLUT:
[FreeGLUT]("http://freeglut.sourceforge.net/") - pretty much makes your windowing code agnostic of OS (only Linux and Windows if I recall properly?) so that you can focus on whatever OpenGL powered project.

Anyway, I've put my little bit in.

---

