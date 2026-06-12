---
title: "Oh no! C++/SDL Error!!!"
date: 2007-05-04
forum: Programming Talk
---

### Post by kmslinux on 2007-05-04
I'm following [Lazyfoo's tutorial]("http://lazyfoo.net/SDL_tutorials/") on C++ and SDL. I do the first step (on the Kdevelop section) and think, "Here's my first roadblock. It's an RPM." So I use alien to convert it to a deb. Easy enough. I install it. Then, I use Kdevelop to generate the sample SDL file. I then do the next step. I download the zip, put the zipped folder in the same directory as my SDL folder, and compile the cpp file with g++. It starts spitting out all these errors at me! What do I do? :confused:

---

### Post by hod139 on 2007-05-04
Let me rewrite Lesson 1:

```

sudo apt-get install libsdl1.2-dev

```

I haven't looked at the other lessons to comment.

---

### Post by kmslinux on 2007-05-06
It keeps spitting the errors at me, no matter what I do. I'm on another computer, so I'll show you those errors later.

---

### Post by Wybiral on 2007-05-06
What are you using to link? And are your include paths correct?

---

### Post by hod139 on 2007-05-06
> **kmslinux said:**
> It keeps spitting the errors at me, no matter what I do. I'm on another computer, so I'll show you those errors later.

Is apt spitting out errors, or trying a different lesson?

---

### Post by kmslinux on 2007-05-06
The lesson is spitting the errors at me. I'm trying lesson 2, so when I "g++ lesson02.cpp" it shows the errors. Once it said something along the lines of "SDL.h: File Not Found", but I fixed that. So, the #include line is okay. And Wybiral, what do you mean by "what are you using to link"?

---

### Post by hod139 on 2007-05-06
Make sure you are using pkg-config to compile code that requires SDL.  For example, to compile Tutorial 2:
```

 g++ -Wall `sdl-config --cflags --libs` lesson02.cpp -o lesson02

```

The -Wall flag turns on all warnings
The `sdl-config --cflags --libs` properly sets up the include and linking paths for SDL.
The -o lesson02 names the resulting binary lesson02

---

### Post by kmslinux on 2007-05-07
THANK YOU SO MUCH! You rock.
Edit: I ran everything from another computer (scp from local to remote) and it worked flawlessly. I tried it from my computer, and I think I don't meet the requirements for SDL.
CPU: AMD Athlon XP 1600+, 1399.700 MHz, 256 KB cache
Memory: 512 MB
Hard Disk space: 310 GB (60 internal + 250 external)
Linux Version: 2.6.20-15-generic
Ubuntu version: 7.04 Feisty Fawn

Do I meet the requirements?

---

### Post by snoop on 2007-05-07
> **kmslinux said:**
> THANK YOU SO MUCH! You rock.
Edit: I ran everything from another computer (scp from local to remote) and it worked flawlessly. I tried it from my computer, and I think I don't meet the requirements for SDL.
CPU: AMD Athlon XP 1600+, 1399.700 MHz, 256 KB cache
Memory: 512 MB
Hard Disk space: 310 GB (60 internal + 250 external)
Linux Version: 2.6.20-15-generic
Ubuntu version: 7.04 Feisty Fawn

Do I meet the requirements?


More than enough for sdl.

---

### Post by kmslinux on 2007-05-07
Hmm... Then I don't know what's going on... I compiled the lesson (lesson 02) just as hod139 said, and "./lesson02"-ed. It doesn't do anything. I'm baffled. Does it have something to do with my X session? I've tried it on both GNOME and KDE, and the both come up with the same result. :( I don't know why it worked on the other computer, though... I even grepped the binary for the code (as in for each line of code I did "grep 'line' *") and it came up with "binary file lesson02 matches." I'm so frustrated. I want to pound my head against a brick wall. That's what I'll do.  ](*,)

---

### Post by kmslinux on 2007-05-11
Am I missing any libraries?

---

### Post by kmslinux on 2007-05-20
Ah! I found the problem. I did some Googling and found a little line of code that prints the error message.

SDL_Init Failed: No available video device

^^ That's my error. What's wrong?

---

### Post by slavik on 2007-05-20
you are using a remote connection without X running (and tunneled to your client)

---

### Post by kmslinux on 2007-05-20
> **slavik said:**
> you are using a remote connection without X running (and tunneled to your client)

Was that supposed to be a question? No, I'm not connected remotely; I'm doing it directly from my computer. X is running.

---

### Post by slavik on 2007-05-20
I guess I misread the thread. are you running the program from a terminal inside X?

also, make sure you have the proper X11-dev libraries. :)

---

### Post by Mickeysofine1972 on 2007-05-21
Why not try the Ubuntu Games Developer Wiki, its has a good section of SDL setup and beginners howtos like this one:

[http://ubuntu-gamedev.wikispaces.com/How-To+Setup+SDL+for+games+development](http://ubuntu-gamedev.wikispaces.com/How-To+Setup+SDL+for+games+development)

Mike

---

### Post by kmslinux on 2007-05-21
> **Mickeysofine1972 said:**
> Why not try the Ubuntu Games Developer Wiki, its has a good section of SDL setup and beginners howtos like this one:

[http://ubuntu-gamedev.wikispaces.com/How-To+Setup+SDL+for+games+development](http://ubuntu-gamedev.wikispaces.com/How-To+Setup+SDL+for+games+development)

Mike

I had all those packages installed (except libsdl1.2debian-alsa conflicted with libsdl1.2debian-oss). My problem is it won't start. It gives me a "no available video devices" error.

---

### Post by kmslinux on 2007-05-21
Solved! Before I installed libsdl1.2-dev, I compiled it from source without having xorg-dev installed. Now that I "make uninstall"ed and "make install"ed the SDL source code, everything works.

---

