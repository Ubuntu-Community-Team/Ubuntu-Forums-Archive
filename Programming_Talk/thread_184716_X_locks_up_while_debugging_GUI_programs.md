---
title: "X locks up while debugging GUI programs"
date: 2006-05-30
forum: Programming Talk
---

### Post by mdh on 2006-05-30
Hi,

I am debugging a GUI application written in a C++ based GUI toolkit called fox. The problem that I am facing is when ever I set a breakpoint (using gdb) in a part of code that gets called when the user interacts with a particular GUI item, the mouse and keyboard gets locked and I cannot do anything but to restart X. When I use ddd for debugging, in this scenario ddd pops-up a dialog, which says "Mouse Pointer Froze Continuing execution in 10 seconds" and after ten seconds my program continues to run but I cannot interact with the user interface as my mouse and keyboard remains locked and the only way out of it for me is to use ctrl+alt+backspace to restart x :(

Any thoughts on this rather weird problem ?

---

### Post by rydow on 2006-05-30
Hi,
I have come across a similar problem under redhat with QT. I was not able to pin down what caused the problem but exactly as your experience it occured only when debugging. My "solution" was to log in to the computer whose process was being debugged over ssh from another computer on the network and kill the debuggee. When the process was killed, X got on its feet and I could start over again without a reboot.

So if you are on a network the above might ease the pain a little.

Regards
Jonas

---

### Post by mdh on 2006-05-30
Hi Jonas,

I came to know that the reason for X locking up was because, my GUI toolkit (fox) would grab the mouse/keyboard on some gui events and release them later when the events are processed. If I place a breakpoint in a segment of the code that is between this grab and release then I  am left with only two options 1) ctrl+alt+backspage 2) ](*,) 

So the only way out of this is to be more judicious about where to put the breakpoints.

Thanks for your suggestion,

---

### Post by Arndt on 2006-05-31
[QUOTE=mdh]Hi Jonas,

I came to know that the reason for X locking up was because, my GUI toolkit (fox) would grab the mouse/keyboard on some gui events and release them later when the events are processed. If I place a breakpoint in a segment of the code that is between this grab and release then I  am left with only two options 1) ctrl+alt+backspage 2) ](*,) 

So the only way out of this is to be more judicious about where to put the breakpoints.

Thanks for your suggestion,[/QUOTE]

If you have enough control over the program, you may be able to disable the grabbing, maybe something as simple as commenting out the call to XGrabMouse or XGrabDisplay.

---

### Post by rydow on 2006-05-31
Hi Murali,

Thank you for enlighten me on the subject. I had a feeling it was something like that but I never had time to go to the bottom with it at the time.
/J

---

