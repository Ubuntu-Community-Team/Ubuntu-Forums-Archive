---
title: "Equivalent to Win API for Ubuntu?"
date: 2007-09-06
forum: Programming Talk
---

### Post by Fixman on 2007-09-06
I before programmed games for windows using the windows API. Now, Im new to Linux programming and I don't know where to start. Could someone at least name a solution for my programs?

---

### Post by SomethingUniqueHere on 2007-09-06
Check out SDL: [http://www.libsdl.org/](http://www.libsdl.org/)
If you code with Python check out pygame: [http://www.pygame.org/news.html](http://www.pygame.org/news.html)

---

### Post by ryno519 on 2007-09-06
> **Fixman said:**
> I before programmed games for windows using the windows API. Now, Im new to Linux programming and I don't know where to start. Could someone at least name a solution for my programs?

Are you referring to DirectX and Win32 in C++? I assume that because you said game development.

In GNU/Linux you have OpenGL for the 3D graphics library, which has a bit of a learning curve, but if you have used DirectX before you should have a good understanding of 3D development already.

As far as the Win32 goes you will be using GNU/Linux system libraries and your graphics toolkits library to perform equivalent tasks. I like to use gtkmm to code gtk apps in C++.

As for sound, the FMOD Sound System will compile in GNU/Linux. There's probably a GPL'd sound system that will do, but I've never used a different one. Not sure that gstreamer or phonon would be up to the task.

---

### Post by pmasiar on 2007-09-06
> **Fixman said:**
> I before programmed games for windows using the windows API. Now, Im new to Linux programming and I don't know where to start. 

You also may just pick a Linux game you want to enhance, and learn whatever that project uses. Most open source projects are eager to train "fresh blood" developers (who are willing and able to learn) and have even simple bugs set aside to get you involved. WorldForge is one of such communities. Depends on your interests, skill level, and dedication.

---

### Post by fct on 2007-09-07
In [http://happypenguin.org](http://happypenguin.org) there is a huge list of open source games you can use to learn from. If you are learning SDL, for example, there are tons of simple games using that library there.

---

### Post by gnusci on 2007-09-07
Give a look to Allegro:

[http://www.talula.demon.co.uk/allegro/](http://www.talula.demon.co.uk/allegro/)

It is a library for game development.

---

