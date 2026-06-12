---
title: "Newbie Programmer Question"
date: 2007-01-10
forum: Programming Talk
---

### Post by bsalt on 2007-01-10
Hey, I am headed to be a Computer Science & Engineering major. However, I am only a sophomore and am strapped down with gen ed classes. 

I already own a computer science book called _Python Programming_ - it's an intro to programming book. 

I want to try my hand at writing an app that can customize the mouse buttons to do scrolling, back/forward, etc - with a GUI. I'm currently using xev and xmodmap to get my Marble Mouse to use the extra buttons as a scroll up/scroll down function. I feel that people with a 5 button mouse or so should have the option to customize their mouse quickly and easily as well.


How hard would this task be to learn basic programming?

---

### Post by pmasiar on 2007-01-10
> **bsalt said:**
> app that can customize the mouse buttons to do scrolling, back/forward, etc - with a GUI. (...) How hard would this task be to learn basic programming?

IMHO this task is not suited to help you *basics* of programming (for some values of "basics"). You will have loads of very deep technical problems which might frustrate you unless you know what you are doing. Simpler tasks, where is more obvious *what* to do, *how* to do it, and to confirm that *result makes sense*,  are better suites for beginners (for some values of "beginers"). YMMV

It's entirely possible that some required calls to mouse driver are missing from standard python libraries and you might need to create wrappers for C libraries to link them to python. Yes, if it looks scary or confusing, it worked as planned :-) If you are not afraid, or know how to do it - full speed ahead!

I maintain Learn Python wiki with links to good online books, articles about data structures, and tasks suitable for learners. Should give you couple of weeks worth of homeworks. :-)

---

### Post by Tomosaur on 2007-01-10
Python has a wealth of options when it comes to GUI programming. However, you should know that GUI programming in general is considered to be pretty complex, it's not 'basic' by any standards. It would do you well to be comfortable writing command line applications with interactivity and such before moving on to GUI programming. Granted, Python makes life a LOT easier when writing a GUI, but it still has its quirks and its complications. That said, I prefer GTK to most of ther other GUI libraries available, and it is, for the most part, well documented.

To allow wheel-scrolling, you need to have what is called an 'event listener' (sometimes, mouse-specific stuff is called a mouse-listener, but it's really just an event listener) applied to either the scroll bar or the app as a whole. You can see this in other apps already. There's no real standard to follow, but most apps have context-sensitive scrolling. That is, the area to be scrolled waits for the moust to hover above it. This is event 1. If the user begins to scroll the wheel, then another event listener fires and decides which way to scroll the pane/window. Some apps only wait for the scroll wheel. Apps with multiple windows need to listen for the mouse to hover above the different panes before waiting for the scroll wheel to move.

The problem, however, comes when (as you point out), mice do not have a scroll wheel, but instead have extra buttons. If you want the button mapping to work system-wide, you would need to play with the desktop environment of the user, possibly even X itself. You can quite easily re-map the buttons in your application, but as soon as your app is closed, or loses focus, the buttons revert back to their normal usage. This is basically how games work, the ones which allow you to change what different buttons do. It works by listening for the button, and then matching that with whatever you or the user wants it to do. One way to do this is apply your event listeners as normal, then poll the device (keyboard/mouse) for whichever key was pressed. You can then match this with what the user wanted that button to do. One way to do this is to use a single event listener and have a switch statement inside it (although Python doesn't have switch statements so you need to use multiple if statements, which is problematic) which matches different keys to different actions.

EDIT: While python is great for making life easy, some elements of it are illogical. I prefer Java for GUI stuff any day of the week, but many people think Java's GUIs look ugly. It does, however, make event listening and whatnot pretty easy compared to some other languages.

---

