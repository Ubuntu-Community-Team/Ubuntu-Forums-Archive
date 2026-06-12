---
title: "help with basic uinput example"
date: 2009-11-17
forum: Programming Talk
---

### Post by oedipuss on 2009-11-17
Hello

I'd like to try and write a program to capture keyboard events, modify them in some way and generate new events, to emulate a simple chorded keyboard. 
I've tried with xlib and the xtest extension, which kind of works, but it's not as nice as I'd like (tends to capture its own artificial events), and not all programs respond to it nicely. 
I'd like to try using the uinput device for generating keyboard events, and something like evdev to capture them, so it would be like creating a second fake keyboard, but I can't understand it very well .. 

Using this example [http://lkcl.net/software/uinput/](http://lkcl.net/software/uinput/) , and loading the uinput module, basically does nothing under X . It works  only in a virtual terminal (types 'a').. 
Isn't it supposed to create a device, that X will automatically detect and accept events from it?

Could someone offer some clues, or point me in the right direction ?


Nevermind, it worked itself out after a reboot..

---

