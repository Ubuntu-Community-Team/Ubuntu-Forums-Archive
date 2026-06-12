---
title: "Sending fake keypress to X problem"
date: 2011-09-01
forum: Programming Talk
---

### Post by anonymousie on 2011-09-01
Hi guys. I'm a bit of a newbie to programming.

I'm using [this code here](http://www.doctort.org/adam/nerd-notes/x11-fake-keypress-event.html) to send fake keypresses to the currently in focus window, and it's working great... for basic keys.

When I attempt to send one of the Unicode characters, for example Pi or XK_Greek_PI or 0x07d0, it sends a p instead. Other Unicode characters seem to either do nothing or send the wrong character, so I'm a little confused.

Is there something special about using these? Any help would be appreciated.

---

### Post by cgroza on 2011-09-01
Could you tell us how do you get the result? I don't see anything in that code that outputs the keypress back to you.

My first guess is an encoding issue.

---

### Post by anonymousie on 2011-09-02
I'm using it as a virtual keyboard to a physical keypad, so when they keypad's button goes down, I'd like to output PI. It's mostly at the proof-of-concept stage right now, but I've been successful sending simple things like "A" and "B" just not the more complicated things.

What do you mean an encoding issue? In the receiving application?

Thanks for your reply.

---

