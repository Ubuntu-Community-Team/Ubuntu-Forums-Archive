---
title: "[C++] Console game, keypress, clear screen"
date: 2011-08-29
forum: Programming Talk
---

### Post by LukaK on 2011-08-29
Hi all!

I'm a advanced beginner in programming. Basically what I want to do is a simple C++ console game, something like a dude in a maze, controlled by WASD or Arrow keys.

But how to detect keypresses?

Also how could I prevent from printing a new copy of the maze after each move? So that after 10 moves I don't see 9 leftover mazes in the console. So basically how to refresh the output in the console?

Best,
Luka

---

### Post by gnometorule on 2011-08-29
Have a look at allegro in the software center/google it. It provides you with graphics library support and is reasonably easy to use, providing also key stroke detection and such.

---

### Post by LukaK on 2011-08-29
Thank you for the answer. If anyone else is trying to get Allegro working with C++, you need to go into Software Center search for liballegro and install the package that says "development files for the Allegro Library".

So I won't be able to stick with console and get key press recognition?

---

### Post by lumore22 on 2011-08-29
Look up a text by Deitel & Deitel on C++ programming. It's  a pretty good book.Ihink that they actually address this. 

Patience & lots of luck.

Regards

---

### Post by gnometorule on 2011-08-29
It certainly is possible, but I have not done this. Allegro is, from memory, using OpenGL. If you intend to get really serious and do this from scratch, this is probably what you want to look at. However, when I was looking at it, it appears to need a  significant time investment, and I then didn't have the necessary time.

---

### Post by nvteighen on 2011-08-30
Wait, if this is meant to be an ASCII text-based UI, then Allegro is not what you're looking for. Allegro allows you to create simple 2D graphics, more or less like Pygame does in Python.

For ASCII text-based UIs, the best and simplest is ncurses. It's a C library, but you can use it in C++. (There's a binding called ndk-xx, but I haven't used it).

---

### Post by LukaK on 2011-08-30
Thank you all. I'll give ncurses and C a shot, I want to keep it in the console if possible.

---

### Post by nvteighen on 2011-08-30
> **LukaK said:**
> Thank you all. I'll give ncurses and C a shot, I want to keep it in the console if possible.

You can use ncurses on C++; it's explicitly supported, according to the API docs (the general rule is that C libraries work on C++ directly, though sometimes some tweaking might be needed from the library's developers). The only issue is that you might have to wrap its structures into classes in order to make it easier or more C++-ish, if you like.

---

