---
title: "Get raw screen pixels, move mouse and send keys."
date: 2007-12-22
forum: Programming Talk
---

### Post by solarwind on 2007-12-22
I'm making a program that will need to:

* Read raw pixels on the screen. For example, get the colour of the pixel (239, 512).

* Move the mouse to anywhere on the screen. For example, move the mouse to (731, 612).

* Simulate key press and be able to send keys as if the keyboard was typing.

Is there an API to do this, or how would I go about doing this?

---

### Post by revanthedarth on 2007-12-22
Hmm... GLUT has a function for getting color of the pixel the mouse points, but that's not what you need, it seems.

Win32 API has functions to move the mouse.

And, to simulate key press, all is so simple. Use any API you wish, and when a key is pressed, add to the string that's displayed. When backspace is pressed, delete the last element of string (make it NULL).

---

### Post by solarwind on 2007-12-22
> **revanthedarth said:**
> Hmm... GLUT has a function for getting color of the pixel the mouse points, but that's not what you need, it seems.

Win32 API has functions to move the mouse.

And, to simulate key press, all is so simple. Use any API you wish, and when a key is pressed, add to the string that's displayed. When backspace is pressed, delete the last element of string (make it NULL).

I know winbloze has an api that lets you do all of this (part of the reason why it's so insecure), however I do not know of a way to do this in Linux.

---

