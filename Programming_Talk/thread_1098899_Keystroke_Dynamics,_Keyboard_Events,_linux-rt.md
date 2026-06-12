---
title: "Keystroke Dynamics, Keyboard Events, linux-rt"
date: 2009-03-17
forum: Programming Talk
---

### Post by Shrikaant on 2009-03-17
To implement a keystroke dynamics program, i need to capture keyup & keydown events, and also the time elapsed between these events.

1. How to capture keyup and keydown events in C? Any specific functions or library i can make use of? Or any way to hook to keyboard interrupts?

2. How to ensure that the timing is accurate and consistent? Should i make use of Ubuntu's linux-rt realtime kernel? Doesn't the CONFIG_PREEMPT_PATCH yield to other processes is the realtime app is waiting for I/O (keyboard??) ?

Any help or suggestions are welcome. Thanks. :)

---

### Post by Ferrat on 2009-03-17
1. depends on what type of program you are doing but most windows handlers have some sort of keyboard and mouse handler/hook.

2. real time kernel isn't really needed unless you need something extremly exact, time.h takes time down to 1/1000000 of a second fairly accurate that should meet most of your needs?

---

### Post by Shrikaant on 2009-03-18
Hi. Thnx for the reply.

1. I am aware of the win32 keyboard hooks. I am interested in linux alternatives. Is it not possible to achieve the same thing in Linux??

2. Time.h has a very fine resolution but not very precise since the timing gets disrupted by background processes/interrupts etc. I may sound paranoiac but still... However can anyone confirm this : "if realtime app is waiting for I/O, cpu spends its time by processing other processes" <- this wud mean that there will be additional latencies while the scheduler returns back to process I/O.

---

### Post by rendon on 2009-03-18
I believe that the previous poster, Ferrat, wasn't referring to "Windows" but "window handlers", that is to say a type of API in a programming language that allows you to create windows, or frames, or widgets, depending on what language you're using.

For example, recently I've been using a game API built for python called pygame.  Pygame includes a set of methods which allows you to easily make windowed applications, and it can control keyboard input and time rates.  This type of thing is obviously important for a game, and I believe pygame has done a good job at making this job very easy.  Pygame, being a module for python, is also cross platform, so you can try it on any OS.

Have a look

[http://www.pygame.org]("http://www.pygame.org")


click on documentation on the left menu, then try click "key" at the top to see key control functions, then try clicking "time" at the top to see time control functions.

---

### Post by Shrikaant on 2009-03-18
Hi rendon. Thnx for correcting me. So foolish of me...

I will surely go through the link you sent. Thnks again :)

---

