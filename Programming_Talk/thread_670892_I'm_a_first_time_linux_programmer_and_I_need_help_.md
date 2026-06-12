---
title: "I'm a first time linux programmer and I need help getting an IDE/allegro"
date: 2008-01-17
forum: Programming Talk
---

### Post by jkreef on 2008-01-17
Does anyone know what a good c++ IDE is and how to get the allegro libraries working for it? I am working on a project in windows and I want to port it to linux, Thanks for any help you can offer.

---

### Post by LaRoza on 2008-01-18
> **jkreef said:**
> Does anyone know what a good c++ IDE is and how to get the allegro libraries working for it? I am working on a project in windows and I want to port it to linux, Thanks for any help you can offer.

[http://www.talula.demon.co.uk/allegro/index.html](http://www.talula.demon.co.uk/allegro/index.html)

The IDE question can only be answered by yourself, if you are new to programming in Linux see the sticky for it.

---

### Post by EXCiD3 on 2008-01-18
Id recommend using Eclipse as a C++ IDE, however its all your personal preferences as LaRoze pointed out. I have used many Windows and Linux IDE's and have concluded the Eclipse is my favorite overall.

---

### Post by LaRoza on 2008-01-18
> **EXCiD3 said:**
> Id recommend using Eclipse as a C++ IDE, however its all your personal preferences as LaRoze pointed out. I have used many Windows and Linux IDE's and have concluded the Eclipse is my favorite overall.

I haven't used any IDE's for any length of time, but I found Geany to be very nice. Not heavy, but with nice features. I only used it out of curiousity for a short while on Windows though.

---

### Post by jkreef on 2008-01-18
Thanks for all the help! Eclipse is great but does anyone know how to get allegro working with it? I have read the readme that came with allegro and done some searching on the site but I cannot figure it out. Thanks!

---

### Post by vexorian on 2008-01-18
I vote for geany.

You don't get libraries working with IDEs , that's the compiling process' job.

I've found liballegro4.2 and liballegro4.2-dev in the normal ubuntu repos, once you install the -dev package you can use #include to allegro and make gcc link to it. I think there's more help about compiling an allegro project with gcc in their home page, I for one barely have experience with SDL and wasn't that hard.

---

### Post by jkreef on 2008-01-18
So in Linux all you have to do is put the include? Nothing else? If that's true yet another way that Ubuntu>windows,

---

### Post by LaRoza on 2008-01-18
> **jkreef said:**
> So in Linux all you have to do is put the include? Nothing else? If that's true yet another way that Ubuntu>windows,

If you have to link files, you have to link them. It depends on what you are doing.

I compile through the commend line, so I never had to configure an IDE for anything.

---

### Post by Acglaphotis on 2008-01-18
Try vim too, it's very nice and you can uber-customize it to you.

---

### Post by vexorian on 2008-01-18
> **LaRoza said:**
> If you have to link files, you have to link them. It depends on what you are doing.

I compile through the commend line, so I never had to configure an IDE for anything.

As a matter of fact , this whole linking thing can be really hard, so you should really get into some gcc documentation, and ( I recommend) Makefile tutorials and I am sure allegro has some instructions about this on their website as well.

---

### Post by jkreef on 2008-01-18
I feel like an uber-newb but how would I compile through the command line with allegro?

---

### Post by slavik on 2008-01-19
> **jkreef said:**
> I feel like an uber-newb but how would I compile through the command line with allegro?
something along the lines of (the command is most likely wrong):
```

g++ -o myprogram -l allegro myallegrocode.cpp

```

---

### Post by Acglaphotis on 2008-01-19
[PHP]g++ myprogram.cpp -o myoutput[/PHP]

---

### Post by jkreef on 2008-01-19
So all I need to do is g++ and then to where the .cpp file is?

---

### Post by slavik on 2008-01-20
> **jkreef said:**
> So all I need to do is g++ and then to where the .cpp file is?
that's the bare minimum :)

---

### Post by jkreef on 2008-01-20
Thanks for the help! I'll get out of your hair now and start experimenting. Thanks again!

---

