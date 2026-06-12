---
title: "C++ Help!"
date: 2009-01-21
forum: Programming Talk
---

### Post by InSaN3 GoDLiK3 on 2009-01-21
im using ubuntu and i need some help im writing a tetris program in c++ and i have 2 files main.cpp and bitmap.h how would i make it into a tetris game? aka make them into tetris?

---

### Post by s|fr on 2009-01-21
Hi Insane GodLike,

I think you are basically saying write my program for me. I think you need to ask specific questions like how do I load a bitmap in c++ or how do I add music etc. Otherwise people will not be able to help you much.

Have you coded before in C++? Have you done any graphics in C++ before?
Answers to these questions will help others to help you.

---

### Post by InSaN3 GoDLiK3 on 2009-01-21
well first off i don't need anyone to write my code for me (no fun in that now is there?) and yes i have codded in c+ before graphics well i think you mean photoshop, flash, lua programming thats about all the graphics i know

---

### Post by curvedinfinity on 2009-01-21
Heya,
As s|fr points out, some more details would be helpful. In C++, you can use a variety of libraries to help create the visuals for the game. There are probably a hundred different options. If you're looking for the most simple option, and you are a beginner programmer, there are even other languages that will probably better suited to a small game such as tetris. :)

---

### Post by curvedinfinity on 2009-01-21
> **InSaN3 GoDLiK3 said:**
> well first off i don't need anyone to write my code for me (no fun in that now is there?) and yes i have codded in c+ before graphics well i think you mean photoshop, flash, lua programming thats about all the graphics i know

In this case, I'd strongly recommend trying to do some even simpler games/programs than tetris to start out. SDL is a good library to use for C++ ([http://www.libsdl.org](http://www.libsdl.org)).

If you aren't set on C++, I'd also strongly recommend using another language for your first games.

Try...
[http://www.processing.org](http://www.processing.org)
[http://www.pygame.org](http://www.pygame.org)
Or even the project I run...
[http://www.mirthkit.com](http://www.mirthkit.com)

---

### Post by CptPicard on 2009-01-21
Try Python, it's a much more suitable language for a noob.

Do you have some general idea as to how a Tetris game would be laid out, in a program logic sense?

---

### Post by slavik on 2009-01-21
> **CptPicard said:**
> Try Python, it's a much more suitable language for a noob.

Do you have some general idea as to how a Tetris game would be laid out, in a program logic sense?
How does switching to Python help OP?

InSaN3 GoDLiK3, please be a little more specific with what issue you are having and rephrase your question.

---

### Post by Wybiral on 2009-01-21
> **slavik said:**
> How does switching to Python help OP?

InSaN3 GoDLiK3, please be a little more specific with what issue you are having and rephrase your question.

Because it appears that they need to start with something a bit simpler...

---

### Post by InSaN3 GoDLiK3 on 2009-01-21
i figured it out thanks for the help guys i just used g++ compiler watching a movie now peace:popcorn:

---

### Post by curvedinfinity on 2009-01-21
> **slavik said:**
> How does switching to Python help OP?

InSaN3 GoDLiK3, please be a little more specific with what issue you are having and rephrase your question.

In all fairness, Python libraries generally have more automation and simpler usage. I was recommending Processing (Java based) in particular because all of the OpenGL setup is done before Processing even enters your code. The entirety of the code for drawing an image to the screen looks like this:

```

a = loadImage("image.jpg");
image(a, 0, 0, 100, 100);

```

... that's the code for the entire application (no setup or destruction). A similar SDL C++ app would take probably 200 lines with all the image processing, setup, exiting, blah blah blah. It uses jogl or alternatively a built-in software renderer.

---

