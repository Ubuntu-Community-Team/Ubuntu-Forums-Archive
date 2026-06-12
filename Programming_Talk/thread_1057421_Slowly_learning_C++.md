---
title: "Slowly learning C++"
date: 2009-02-01
forum: Programming Talk
---

### Post by S0m3th1ngw13rd on 2009-02-01
Started to learn how to program using C++. My keyboard(actually a ZBOARD, without the software), it never worked in windows either!!  Anyways the keyboard has hotkeys at the top for the volume, play, stop, mute, next song, previous song. What I would like to do is write a program to make these keys work again for Linux.  I'm still a begginer, so I know it will time time and effort.  Is this idea feasible or am I jumping in the deep end of the pool without knowing how to swim.

---

### Post by monkeyking on 2009-02-01
I think you are in to deep.

What you basicly want to do is making a driver for your keyboard.
Without proper documentation, this is quite timeconsuming or even impossible.

But even if you figure out how this works, then you need to hook up your program to the linux sound api, or more precisiely the program that you want to use.

I've never tried it, but my guess is that it's close to hell.

Have you tried if your linux can catch your specialized buttons?
try with xev.

---

### Post by S0m3th1ngw13rd on 2009-02-01
thanks for the reply. I didn't realize it would involve creating a driver for keyboard.  Ok so on to next idea.  A program that tracks time spent in a game or other program and keeps a running total of time spent in game or program.

---

### Post by slavik on 2009-02-01
here's what you should try:

open a terminal window and run "xev" that program can capture X EVents. What you can do now is press the hot keys and see if they produce output in the terminal, if they do, you can probably just go to system -> prefs -> keyboard shortcuts and set them up there :)

---

### Post by S0m3th1ngw13rd on 2009-02-01
Nothing on any of the hotkeys at all. Not that important I was just trying to throw some ideas around for a programming project.

---

### Post by slavik on 2009-02-01
well, there is also the evdev driver if you want to mess with it. evdev will just pass on any keypress straight from kernel to X.

once you are competent in C (and can implement data structures using pointers and structs) then you can definately learn driver development.

AFAIK, a keyboard/mouse is not as complex as a video card, because in this case, you almost never send any information back, most of the time, you just interpret the information from the device.

---

