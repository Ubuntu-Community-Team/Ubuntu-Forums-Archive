---
title: "Python and mouse buttons - possible?"
date: 2008-10-25
forum: Programming Talk
---

### Post by MaxVK on 2008-10-25
Hi, please forgive me if this is a 'daft' question - I'm very new to Python (and quite new to Linux), so I'm testing the waters, so to speak.

What I want to do:
I would like to be able to run a script/program and while this program is running I want to be able to hold a specific key on the keyboard, for example the Windows or Super Key, or Alt etc, and while that key is being held down, all click & hold actions with the left mouse button will be translated a continuous stream of single clicks.

I'm kind of hoping that Python will be able to do this, but I'm open to other suggestions if this is not possible. Please remember that I am an absolute beginner with Python.

Regards

Max

---

### Post by sheto on 2008-10-25
I haven't tried this, but I think Pygame ([http://pygame.org/](http://pygame.org/)) should be able to do this. I'm so sorry I can't help you further. I am no expert on Pygame.

---

### Post by MaxVK on 2008-10-25
Ah thats an excellent link in its own right, thanks, but I cant see how it will help me. I don't want to program a game, although I can see the allusion to the old 'auto-fire' that some joysticks had.

Now that I come to think of it, there are some web based games that would be well served with a repeating left mouse click (:lolflag:).

Anyway, onward.

Can anyone help, either with Pygame (and how to utilize it in this instance) or some other method?

cheers

Max

---

### Post by days_of_ruin on 2008-10-25
Maybe [xlib]("http://python-xlib.sourceforge.net/")

---

### Post by MaxVK on 2008-10-25
Hmm, thanks.

The problem you see, is that, as I mentioned, I'm *very* new to Python, and pointing me at a library is of no use at all I'm afraid. For a start, even if I managed to install the thing, I would still have no idea what to do with it.

I understand the basis of making a script, but I have no idea how to access a library, and I was hoping to find some pointers to example scripts that may or may not do the *kind* of thing that I'm looking for, so that I can at least browse code that is going to be similar, or a part of, any script that I need to write myself.

Many thanks for your help so far, it is appreciated, and I don't want to come across with the wrong attitude, but to say that I am a beginner here is a bit of an understatement!

Regards

Max

---

### Post by crazyfuturamanoob on 2008-10-25
Well, pygame has functions for detecting key/mouse presses, but actually it needs a window to work. And cursor must be inside that window. So I'd say pygame can't do that task.

---

### Post by reacocard on 2008-10-25
xlib is probably the only way to go. I've looked into setting global keybindings for an app I develop and I have yet to find anything other than xlib that even sounds like it could do it. However the last time I checked the python xlib bindings were out of date, so you might have to look into using ctypes to access the library directly.

In short, doing what you want to do is probably a lot more complicated than you'd hoped, but it'd probably be doable with some time and effort.

---

### Post by MaxVK on 2008-10-26
> doing what you want to do is probably a lot more complicated than you'd hoped

Hmm, I see that now. I have no idea what 'ctypes' might be, but Ill do a search for that anyway and see where it lands me.

In any case, many thanks for your input. Ill not give up, but I might change direction a bit. If I ever do come up with a way to do this Ill will endevour to remember to come back and post here so that others might benefit.

Thanks all

Max

---

