---
title: "xna on linux"
date: 2008-11-27
forum: Programming Talk
---

### Post by TheUnreasonable on 2008-11-27
Hello,

I have had a bit of experience in programming and currently I have been working on a game project in xna on my windows machine (which I dislike).  My goal is to eventually bring the game over to the xbox 360 through the live arcade (which is why I am using xna).

Currently, xna is keeping me tied to windows and I would really like to start using only ubuntu.  I have heard things about mono and in the past I have tried wine to bring windows programs over to linux, but I was wondering how best to work on my xna project in ubuntu.

It would be great if I could somehow run the full visual studio .net but I suppose that is asking a bit much.  I am actually dual booting right now, but I'd rather just stay on ubuntu all the time.  If you guys could just let me know what kind of solutions are out there, that would be greatly appreciated.

Thanks.

---

### Post by jimi_hendrix on 2008-11-27
i dont think you can but dont quote me on that

<OT>

how is XNA...after i finish my C++ game i will write one in XNA to see which is easier (i dont have a lot of time on my hands normally)

</OT>

---

### Post by TheUnreasonable on 2008-11-27
xna is nice.  As I said, I have only done a bit of programming and this is my first attempt at a game, so I don't know how it compares to c++, but i haven't really run into any big trouble yet.  Things are progressing a bit slowly, but that is just because of my lack of experience i think...

It isn't too hard to deal with and it is neat that the games can be ported over to the 360.

---

### Post by jimi_hendrix on 2008-11-27
C# is a nice language...pretty simple...you will get it quickly

when i wrote my first game it was in C#...pong (with pictureboxes...not even something like XNA) it took a long time...now i could probably write it in an hour...

best way to learn is to write

---

### Post by directhex on 2008-11-28
Someone started on an XNA implementation on Mono, but a lack of contributors means it's pretty much dead

---

### Post by wrtpeeps on 2008-11-28
Use windows, c# on linux (mono) is crap.

---

### Post by directhex on 2008-11-28
> **wrtpeeps said:**
> Use windows, c# on linux (mono) is crap.

On what basis?

---

### Post by Kilon on 2008-11-28
here we go again :guitar:

---

### Post by TheUnreasonable on 2008-11-28
yeah, I thought that was the case.

I was pretty much just checking to see if there were any other solutions out there... I guess there aren't.

Well, I will be continuing to dual-boot i suppose.

Thanks for all your help guys!  Please post here if you come across any good way to run c# on linux.

thanks!

---

### Post by directhex on 2008-11-28
> **TheUnreasonable said:**
> yeah, I thought that was the case.

I was pretty much just checking to see if there were any other solutions out there... I guess there aren't.

Well, I will be continuing to dual-boot i suppose.

Thanks for all your help guys!  Please post here if you come across any good way to run c# on linux.

thanks!

Oh, C# is no problem. You have two C# apps on your default install

The XNA assemblies are a problem, as someone needs to re-implement them - and with no spec, that's hard work.

---

### Post by holomorph on 2008-12-28
For reference the mono XNA implimentation is at [http://code.google.com/p/monoxna/](http://code.google.com/p/monoxna/) but as mentioned above, it seems pretty stalled.

An alternative to dual booting is to run windows in a virtual machine.  I've found Virtualbox to be very easy to set up and get running; unfortunately the open source edition probably will not suffice for xna work because it doesn't include USB passthrough.

---

### Post by paul079 on 2010-01-27
The MonoXna project is back in development, but not complete.  The repository is
[http://monoxna.googlecode.com/svn/trunk/]("http://monoxna.googlecode.com/svn/trunk/")

---

