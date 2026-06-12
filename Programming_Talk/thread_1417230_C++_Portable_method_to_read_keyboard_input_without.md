---
title: "C++ Portable method to read keyboard input without carriage return."
date: 2010-02-27
forum: Programming Talk
---

### Post by Jonas thomas on 2010-02-27
I have spent the last few hours googling trying to figure out if there was a simple portable method to read a single character from the keyboard without a carriage return in C++

I've looked a couple of mega-threads spanning over multiple years.

I've come to conclusion that there isn't.

This seems most strange to me that something so simple should be so complex.

I know that anything is possible within any OS, but it seems to me that it would be logical to a simple "standard" portable function across all OS to do this. What am I not considering here?

Could one of you uber gurus.. confirm this is still the case in 2010.

If this is the case, my question would be why isn't there a standard library call that could perform this task across all os?

I"m a bit tired at the moment.  Hopefully what I just wrote makes sense.

---

### Post by Simon17 on 2010-02-27
To answer your first question, the *most* portable way is with a curses library (ncurses for Linux, pdcurses for Windows).

As for why there isn't a standard way to do it, it's because the C standard library doesn't have any concept of a "keyboard". C is as minimal as possible and runs on many devices that don't have keyboards.

---

### Post by Jonas thomas on 2010-02-27
> **Simon17 said:**
> To answer your first question, the *most* portable way is with a curses library (ncurses for Linux, pdcurses for Windows).

As for why there isn't a standard way to do it, it's because the C standard library doesn't have any concept of a "keyboard". C is as minimal as possible and runs on many devices that don't have keyboards.

Thanks,
I need a spot to park some book marks.
[http://en.wikipedia.org/wiki/Ncurses]("http://en.wikipedia.org/wiki/Ncurses")
[http://en.wikipedia.org/wiki/PDCurses]("http://en.wikipedia.org/wiki/PDCurses")

[http://en.wikipedia.org/wiki/Curses_%28programming_library%29]("http://en.wikipedia.org/wiki/Curses_%28programming_library%29")

Ok.. So I'm taking a beginners C++. Class is taught in windows. My preference is to use Linux at home.  This is good because it forces me to address portability issues which is on of the reasons I was drawn to C++ in the first place.

The instructor placed a compiled example for window of the project on the school server which we are to use a minimum basis for our project.
Basically there is a main menu with choices 1-5.
His example uses  choice + return.
Therefore... I don't have to do this unless I want to.

I went down the pdcursers(windows)/ncurses(Linux) route it sound like I would need to download the pdcursers library to the school computer to run.  Eeeeh.... project is due next week.  Last home work assignments that I created portable features for "fun", sucked up a bunch of time that got the wife and daughter ticked at me that made it not so fun :(

The little voice inside of me is that I should just grin and bear the carriage return on the menu selection(which is driving me nuts) and just move along finish the project and have some Q time with the family.

---

### Post by Simon17 on 2010-02-27
Yes, if you wanted to run the pdcurses program on the school's machine, you would have to include the library with the rest of your files.

I agree that you should just deal with the return for now. Just stick to the assignment. Adding extras might even annoy your instructor along with your family. If you want to add extra features, do it afterwards when you have time.

---

### Post by Jonas thomas on 2010-02-27
> 
I agree that you should just deal with the return for now. Just stick to the assignment. Adding extras might even annoy your instructor along with your family. If you want to add extra features, do it afterwards when you have time.
The teach said it was ok to use stuff not covered yet.  He may wind up regretting telling me that. Sort like putting gasoline on a fire.

An extra carriage return I can live with. Lack of bullet proof basic input I can't. I have another thread running on that.

Anyway.. Thanks for the help. I have a good starting point when the need/want/time arises...

---

