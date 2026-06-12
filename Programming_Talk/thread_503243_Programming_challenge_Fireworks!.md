---
title: "Programming challenge: Fireworks!"
date: 2007-07-17
forum: Programming Talk
---

### Post by AlexThomson_NZ on 2007-07-17
Hi all!

This is the official thread for the "Fireworks Programming Challenge"!

The rules:
 * Can use any programming language you like
 * Can reuse any existing code you may already have
 * Must be OpenGL
 * Theme is "Fireworks"- (interpret this any way you like)

I have attached a skeleton OpenGL C++ program for those who haven't used OpenGL before to start with and have a look at.  It's pretty simple, but covers the basics.  Hope the code's ok, was very rushed (but does compile).  I doesn't have anything tricky at all code-wise, so even programming n00bs should be pretty comfortable with it.

There is no deadline (we will stop when everyone who's interested is done), and no physical prizes (it's a "challenge" rather than a "competition").  The goal of this is for people to maybe try something they haven't done before, so feel free to make it as simple or as complex as you like, and just ask if you need help :)

Good luck!

// EDIT: I posted a long openGL beginners lesson, but seemed to have got lot somewhere, and I can't be bothered writing it all out again.  Let me know if you have any specific OpenGL questions or need help
// EDIT: [http://nehe.gamedev.net/](http://nehe.gamedev.net/) (this is a great OpenGL tutorial site)
// EDIT: Added attachment.  You need build-essential,  libsdl1.2-dev and freeglut3-dev installed to be able to compile it.

---

### Post by Note360 on 2007-07-17
so we need to make fireworks?

---

### Post by AlexThomson_NZ on 2007-07-17
Yep, sorry if I didn't make it clear- the theme is "Fireworks" (hope that's ok- had to make an executive decision...)

---

### Post by Note360 on 2007-07-17
np. nwo to figure out hwo to make this.

---

### Post by Technophobia on 2007-07-17
Oouu i'm up for this. I have been in need of motivation for getting into Linux OpenGL programming for the longest time. An actual competition would be nice too, but a challenge is close enough.

---

### Post by AlexThomson_NZ on 2007-07-17
Maybe we could have a "virtual" prize for the most technically impressive! :)

Something along the lines of the title- "Current Coding Challenge Champion!"

---

### Post by po0f on 2007-07-17
Wybiral has been kind enough to post some OpenGL links in the "How to start programming..." thread.

[Linkage](http://ubuntuforums.org/showthread.php?t=333867#8).

---

### Post by Wybiral on 2007-07-18
I've already started mine, I'm excited to see some other peoples submissions! This should be an entertaining challenge.

---

### Post by Note360 on 2007-07-18
guh does this mean I have to write a particle engine to?

---

### Post by Wybiral on 2007-07-18
> **Note360 said:**
> guh does this mean I have to write a particle engine to?

lol, it's pretty easy... Just make something really simple if you haven't done something like this. Some kind of structure that stores the positon/color/velocity/lifespan and then update it each frame.

---

### Post by bobbocanfly on 2007-07-18
What are the dependencies to compile that demo app? I made some changes but i get a pile of errors when i try and compile it.

---

### Post by AlexThomson_NZ on 2007-07-18
Yep you need:
 * build-essential
 * libsdl1.2-dev
 * freeglut3-dev

To be able to build it.  Sorry I didn't mention earlier, was posting from a different box and couldn't check.

---

### Post by Note360 on 2007-07-18
why is it in cpp. It looks like C to me? (ps I would prefer to try to do this in C)

---

### Post by AlexThomson_NZ on 2007-07-18
The code posted is a bit of a  mash, I started it in C and added some OO bits later, then very quickly stripped everything back and posted the skeleton code.  I should be fully C compatible (I think).  Regardless it's a starting point, and hopefully understandable to everyone whether familiar with C or C++

I tend to implement helper bits and peices as classes to handle things like 3dObjs, lights, special fx, etc. and I was indending to develop this as a series of tutorials heading in this direction.

Certainly don't feel you have to use my skeleton code, you're free to do things anyway you like, whether in C/C+/Python/Java/whatever

---

### Post by Wybiral on 2007-07-19
OK, looks like I'm the first one (ironic because it's in C)... It's not done yet, but it's presentable.

This uses OpenGL, SDL, and SDL_Image.

I took the textures for the skybox and the texture for the terrain from the Cube 2 package... They are temporary (I might try to make my own later on), but all of the code is my own.

Be sure to watch the firework show all the way through before walking around! I wrote it to be viewed from the starting position.

I wrote a simple scripting language for the fireworks that uses this format:
X Y Z XV YV ZV R G B (ms till exposion) (ms till next firework)
You can view the script in "data/script.fw" (negative colors create the spinner things... no explosion)
The script executes from the bottom to the top BTW (It's a stack of commands)

After you watch the show, it will repeat, then you can go explore the terrain... It's small, but it's still pretty fun.

"f" toggles fullscreen
Arrow keys steer the camera
"w", "a", "s", "d" move the camera
Space jumps
Enter/Return fires your own "firework"

Anyway... Enjoy the show!

Notes:
I didn't implement any LOD on the terrain, so this isn't exactly meant for older computers. If anyone is good at terrain LOD or ROAM and would like to teach me a thing or two, please contact me, I would be very interested in learning!

---

### Post by leibowitz on 2007-07-19
Excellent ! The personnal-firework (triggered by hitting 'Enter' key) is ..[I will not divulge anything].

All this lack is some sounds. It would be damn funny. Anyone could improve this one and add sounds ? I know it's huge for so little changes, that's why maybe someone else could do it. It's kind of another challenge too.

I'm so sorry not have any time to learn OpenGL ! And don't have any sound programmation knowledge (OpenAL nor SDL_mixer) otherwise I would have taken this task myself.

---

### Post by Wybiral on 2007-07-19
Come to think of it... You're right, it's certainly in need of some loud booms.

Anyone interested in adding sound would probably want to do so in the function "void firework_boom(particle **p, particle *i)" in the file "fireworklib.c". That's the callback used for the main firework particles (the ones that emit the smaller sparks and eventually blow up) that initiates their explosion (called right before it's death).

EDIT:

OK, I now have a working version with sound if anyone wants to see it, but I'll give others a chance to implement it as well for an extra challenge.

---

### Post by ankursethi on 2007-07-20
A suggestion : Please include the binaries in the package so that we non-openGL guys can run it without having to pull the dev packages off the Interweb.

---

### Post by Note360 on 2007-07-20
Wow, that was fun. I jsut played the animal Animal COllective song Fireworks while runnign aorund in circles wiht fireworks. Hehe kinda fun actually.

---

### Post by dave091 on 2007-07-20
> **Wybiral said:**
> OK, looks like I'm the first one (ironic because it's in C)... It's not done yet, but it's presentable.

That is awesome and way above my opengl knowledge at the moment. I am still plugging away at the NeHe tutorials as well as one of my old textbooks.

---

### Post by AlexThomson_NZ on 2007-07-25
How is everyone going with this?

I was hoping to have something done by now, but am having trouble finding the time- hopefully I can spend some time over the weekend doing this.  Won't be anything like Wybiral's great offering though...

---

