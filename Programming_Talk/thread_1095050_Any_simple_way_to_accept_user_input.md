---
title: "Any simple way to accept user input?"
date: 2009-03-13
forum: Programming Talk
---

### Post by benjorino on 2009-03-13
Hi, I'm creating a program that has a (Very simple) GUI and needs to take some very basic user input. The GUI was written using the CImg library which is designed for image processing, but for the simple point-and-click interface I need it's easy enough to adapt (Note: CImg is crucial to the rest of the program, I didn't choose it specifically to write a GUI, I just used it because I'm already using it and I'm familiar with it).

The problem is that I need to be able to accept simple numerical input from the user, and while CImg can check the state of individual keys, it can't really be easily adapted for this purpose (at least I can't work out how to...).

So my question is this:
What is the simplest way that I can / library that I can use to create a pop-up box that the user can enter a number into, that will then be stored as a variable in my code?

I don't have time (deadline very soon!) to learn anything too complicated, I'm just looking for a simple solution.

---

### Post by listener on 2009-03-13
If you are using Ubuntu, there is a package provided called Zenity.  Try checking it out.  It does pretty much exactly what you're asking for.

Good Luck

---

### Post by tneva82 on 2009-03-13
> **benjorino said:**
>  and while CImg can check the state of individual keys, it can't really be easily adapted for this purpose (at least I can't work out how to...).

Check which key is pressed and add it to string containing text? That's essentially where I went with my own openGL driven GUI-wannabe textfields. Roughly it works like this:

There's variable containing pointer to class extending GUIObject. This has function to handle keyboard input.

When specific thing happen(in my case press enter) I create textfield. I put it to above pointer thus giving focus to it(when I click something else said variable is changed to point elsewhere. When textfield is clicked again pointer points there as well). When textfield has focus keyboard keys(provided by SDL) are sent to the textfield(initial focus is btw on main program itself and if anything but textfield is clicked with mouse focus goes to main program).

in keyboard handler function I then add character to the text line(assuming it doesn't exceed maximum length I have defined).

Then when I need the information I can pull it(in my case enter is pressed again).

If you don't find suitable 3rd party library then something like above could work. Shouldn't be too hard if you can draw your GUI and find out which was clicked. I got this working today + bunch more so hardly impossible.

Assuming of course you don't need multi-line text editing. That's where I'm ATM struggling. One line textfield easy. Multi-line which is split when line exceeds X characters and which you can edit. Much harder :(

And next somebody comes along and shows much better way to do it without 3rd party libraries :lol:

---

