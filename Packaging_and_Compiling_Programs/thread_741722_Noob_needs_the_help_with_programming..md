---
title: "Noob needs the help with programming."
date: 2008-04-01
forum: Packaging and Compiling Programs
---

### Post by kashmirxincx on 2008-04-01
I was looking around on the forums for help with programming, and I found this 

[http://ubuntuforums.org/showthread.php?t=740604](http://ubuntuforums.org/showthread.php?t=740604)

(See first post)

i would like to know how to compile that, I have downloaded the everything as directed. I would like to mess around with a bit. Get an idea for the feel of coding. That simple script/what ever it is seemed like an ok place to start.

---

### Post by kashmirxincx on 2008-04-01
Keep in mind complete noob.

---

### Post by Aztek on 2008-04-01
I realize that you said "complete noob", but do you just mean that you don't have C++ experience, game programming experience, or no experience AT ALL with programming?

---

### Post by kashmirxincx on 2008-04-01
NONE at all. Sorry I should have made that clear.

---

### Post by Aztek on 2008-04-01
Based on the first couple of posts, in order to compile the pong exampe in the first post try this:

1) Run this command:
```

sudo apt-get install build-essential libsdl-ttf2.0-dev libsdl-mixer1.2-dev libsdl-image1.2-dev libsdl1.2-dev

```

2) In Nautilus (or whatever file manager you use), navigate to some folder, let's say /home/USERNAME/Desktop (where USERNAME is whatever your username is) . Right click and create a new document. Name it "main.cpp"

3) Open the main.cpp file with gedit (default) or another text editor. Copy the code from the first post into the file and save it.

4) Now open a Terminal and change directory to /home/USERNAME/Desktop (or wherever you put the new file).

5) Run this command:
```

g++ main.cpp -lSDL -lSDL_image -lSDL_mixer -lSDL_ttf

```

6) The above command will create an executable file. This was named a.out on my machine. Double click on this in Nautilus.


Let me know if this works for you. Everything worked for me except actually running it. A black window comes up for a second then disappears without doing anything. I'm running Hardy Heron 8.04 beta.

---

### Post by Aztek on 2008-04-01
> **kashmirxincx said:**
> NONE at all. Sorry I should have made that clear.

Ok well if you want to learn C++ I would definitely recommend doing some google searches for "beginning C++" and starting to do some reading. Game progamming is a great goal but I wouldn't recommend it for starting out! I wouldn't even start with GUI programming. What you want to do is start with simple CLI (command line interface) applications, similar to those that come with Linux but much simpler. I can recommend some C++ books if you'd like. In my opinion that's really the way to go.

---

### Post by kashmirxincx on 2008-04-01
It worked, The person that posted it purposely started with non c++ code. There are some other places it was done I think. How do I get that exe to use the sounds and images he also provided in that archive?

---

### Post by Aztek on 2008-04-01
I'm not sure I know what you mean. Could you clarify a little?

---

### Post by Zugzwang on 2008-04-01
> **kashmirxincx said:**
> It worked, The person that posted it purposely started with non c++ code. There are some other places it was done I think. How do I get that exe to use the sounds and images he also provided in that archive?

There are no exe files in Linux. To use the sounds & images, extract the archive with the media stuff into a directory and start your program from there. If your compilation process generates a file called "main" (without extension) then you just type "./main" in the terminal to run the executable.

---

### Post by stair314 on 2008-04-06
C and C++ are both relatively hard languages to learn. If you've never programmed at all, you might want to start off with Java or Python or something like that instead. It will be a lot easier to learn C/C++ once you already know how to program.

---

### Post by SteveNorman on 2008-04-14
> **Aztek said:**
> Ok well if you want to learn C++ I would definitely recommend doing some google searches for "beginning C++" and starting to do some reading. Game progamming is a great goal but I wouldn't recommend it for starting out! I wouldn't even start with GUI programming. What you want to do is start with simple CLI (command line interface) applications, similar to those that come with Linux but much simpler. I can recommend some C++ books if you'd like. In my opinion that's really the way to go.



I would love some book recommendations,,all the ones I come across are dated, and the code wont work.

---

### Post by Delever on 2008-04-15
Since I don't want to start a new thread, and this is quite similar topic, i will ask for some help too.

I am not the one who asks for help very often, so this time it seems I face some huge wall...

Ok, I am windows programmer (heh), I used to program all kinds of things with different programming languages, like, network bussiness applications with delphi, mutators for unreal engine, map scripts with python for civ4, visual basic 6, php, currently C#, and little bit of simple C and C++ long time ago. That's just to give some background.

So, I want to learn C++ now, and do that with Ubuntu. It's great os, I already modified some screenlets for my needs and that just does not compare to windows :D

The problem is, learning C++ is not that hard, it's harder to understand the way ubuntu libraries are linked, used, and shared. For example, I just KNOW that there already exists HUGE code base, and I have hard time grasping how to make best use of it for beginner like me. I will try to break that down to simple questions:

- Where to look for latest libraries (or code which is comonly used)
- How to use them
- How those libraries are linked, how much manual work involved, and how it is done
- How to create my own libraries
- How to create code compatible with all ubuntu architectures

The most usefull thing would be practical examples of doing such things. Like some small programs which use different things to get job done.

Any help on these things would be much appreciated. I am determined to learn it, but right now this part is already taking too long :D

---

### Post by noerrorsfound on 2008-04-16
> **SteveNorman said:**
> I would love some book recommendations,,all the ones I come across are dated, and the code wont work.
[Beginning C++ Through Game Programming, 2nd Edition](http://www.amazon.com/Beginning-Through-Game-Programming-Second/dp/1598633600)
I've had the most success with this book while learning C++.

---

### Post by Delever on 2008-04-17
> **SteveNorman said:**
> I would love some book recommendations,,all the ones I come across are dated, and the code wont work.

I have found this one to be quite usefull, and the code definatelly works:

[http://www.isotton.com/devel/docs/lcpp/unpacked/node2.html](http://www.isotton.com/devel/docs/lcpp/unpacked/node2.html)

---

