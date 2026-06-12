---
title: "Please enlight me... about some graphics.."
date: 2006-12-23
forum: Programming Talk
---

### Post by Jango on 2006-12-23
The question may saound really silly, so please forgive me :p I never programmed in linux but have experience programming for windows. So I decided to learn the linux programming too, part by part. So when it comes to simple calculation problems, arrays, memory - it is pretty straight forward and similar to usual windows programming.

Now I get really stuck with graphics. You know how DOS had video modes? And you initialize it in the programe and your console programs can do drawing and everything else? Is it anyhow possible in linux? For example, is it possible to draw a factorial on a screen of a console program? Or is it differnt here?

May've sounded really clumpsy, but I am really stuck. All suggestions/comments/links are appreciated! Thank you!! :-k

---

### Post by red_Marvin on 2006-12-23
Depending on what programming language you choose there are libraries available to let you use graphic commands...
Some libraries available for c/c++
Xlib - core linux graphics functions, very basic.
SDL - generic graphics and input handling, gaming oriented.
OpenGL - 3D graphics and polygons etc.
gtk / qt - used to create gui's (like winAPI)
Other languages have built in graphics functions (Like FreeBASIC) but can also use external libraries...

---

### Post by Wybiral on 2006-12-23
For simple 2d stuff, you may want to try libsvga, it allows for direct pixel manipulation to the hardware (you can also use it with assembly is you get too bored). Also, I highly advocate OpenGL which is capable of both 2d AND 3d graphics and also very fast. Combining SDL and OpenGL is probably the easiest way to use OpenGL and you should be able to find some good documentation.

There's a couple of introductory tutorials here: [http://ubuntu-gamedev.wikispaces.com/](http://ubuntu-gamedev.wikispaces.com/)

Good luck! Definitely post any problems you run into around here.

---

### Post by Biased turkey on 2006-12-23
[SIZE="3"]First AFAIK, no one using windows programs graphics in DOS anymore. DirectX is the way to go.
In Linux, with a C or C++ compiler,  SDL graphics libraries are very popular , and guess what, those SDL libraries have a Windows version.
So, you'll need a few things:
1) a C or C++ compiler ( included in Ubuntu )
2) some graphics API ( application programming interface ) such as SDL, ClanLib, Plib 
3) Some integrated development application , Anjuta or Kdevelop[/SIZE]

---

### Post by Wybiral on 2006-12-23
> DirectX is the way to go.

Actually... OpenGL is just as popular in Windows (thats where I started programming in OpenGL) if not MORE popular and is also very portable. DirectX may have more tools than OpenGL (because OpenGL is a Graphics Library) but using OpenGL with SDL will give you alot of the functionality you would get from DirectX... Without limiting yourself to windows.

---

### Post by Jango on 2006-12-24
Thanks! Assuming that I am using C++ is there something that is better documented/standarized than others? :D

---

### Post by Wybiral on 2006-12-24
It depends... I haven't done much 2d programming lately, but as for 3d... Without a doubt, OpenGL has the most documentation. SDL makes OpenGL incredibly easy to initialize and offers extra abilities like texture loading and mouse/keyboard/sound interfacing. 2d programs are also pretty easy to work with in OpenGL, it's just more meant for 3d.

For a ton of examples (including linux compatible ones) NeHe is great: [http://nehe.gamedev.net/](http://nehe.gamedev.net/)

If you understand BASIC there is a lot of good code using OpenGL that could be ported to C++ here: [http://basic4gl.proboards20.com/](http://basic4gl.proboards20.com/) (there is also a new linux version of that language in my sig)

And some more stuff here: [http://www.gamedev.net/reference/list.asp?categoryid=31](http://www.gamedev.net/reference/list.asp?categoryid=31)

---

### Post by Biased turkey on 2006-12-24
[SIZE="3"]The SDL doc itself is not bad, but it is just some piece of programs as example for each SDL "instruction".
If you need a basic reference book about 2D programming using SDL, I would suggest the book "Programming Linux Games " written by John R. Hall    and published by No Starch Press ([/SIZE]

---

### Post by std on 2006-12-25
You could also try Allegro ([http://www.talula.demon.co.uk/allegro/](http://www.talula.demon.co.uk/allegro/) ) although it's not intended as a graphics library but more for game programming. It's quite easy to use, but I don't know how widely used it is today. It used to be one of the bigger players some years ago.

From my experience, libsvga will get you closest to the old DOS programming, but it does have a number of limitations. I'd go for SDL with OpenGL.

---

### Post by Jango on 2006-12-26
Thanks a lot guys! At least i know where to start now :)

---

