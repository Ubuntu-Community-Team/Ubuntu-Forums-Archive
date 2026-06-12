---
title: "python-virtkey"
date: 2007-11-11
forum: Programming Talk
---

### Post by JustAboutRealJAR on 2007-11-11
Hey, I'm trying to write a very basic macro (15 lines of code at most) which may grow to new tasks in the future.

After ~1 hour of google searches I concluded that there is no documentation for python-virtkey. I *did* find the source code, but I don't know C so it wasn't very helpful, can anyone tell me how to get the virtkey module to emulate a keypress? I need it to do spacebar, return, and the letters/numbers

here's the code for the virtkey module: [http://codebrowse.launchpad.net/~onboard/virtkey/main/annotate/tortoise%40tortuga-20070809174257-3cho3enck0zg4iq9?file_id=pythonvirtkey.c-20060911161653-c3owb3gyq5x17b53-3]("http://codebrowse.launchpad.net/~onboard/virtkey/main/annotate/tortoise%40tortuga-20070809174257-3cho3enck0zg4iq9?file_id=pythonvirtkey.c-20060911161653-c3owb3gyq5x17b53-3")

Here's the python I've written so far:
```
import virtkey
import time

keypress=virtkey.virtkey

time.sleep(2)

for i in range (1,100,1):
	print "loop " + str(i)
	time.sleep(1)
	keypress(" ")     # <-- doesn't work, but doesn't return an error either
	

```

Thanks in advance for your help!

---

### Post by pmasiar on 2007-11-11
It always help to mention **what** you want to accomplish, not to assume that the (dead-end) road you picked is the best way to accomplish it.

Looks like you want to send keystokes to your app?

[PyGUIUnittest](http://www.pyzine.com/Issue007/Section_Articles/article_PyGUIUnittest.html) or (on Win) [SendKeys](http://aspn.activestate.com/ASPN/Cookbook/Python/Recipe/65107) might be better way (and it is package [with docs](http://pypi.python.org/pypi/SendKeys/0.3).

Or do you need something different?

---

### Post by JustAboutRealJAR on 2007-11-11
> Looks like you want to send keystokes to your app?

Nah, I was basically trying to send keystrokes to someone else's app. But wanted to be able to use it to control any app. I send the author of virtkey an email to which he replied very quickly. Here's the email I sent, as well as his reply:

My email: 
> Dear Chris,

I found your module (virtkey) via a google search, and it appears to be exactly what I need. Unfortunately I have been unable to get it to actually emulate any key presses.

is there any documentation? if not, could you explain to me what the virtkey function expects as arguments? 

Chris' (the author of python-virtkey) Response:
> Sorry, this library has bit-rotted a bit since I wrote it two summers
ago.  I was part way through re-writing it but got distracted.  It is
used by onboard so you could look at that for examples.

v = virtkey.virtkey()

#where c is the char you want to type.
v.press_unicode(ord("c"))

#where 123 is the x keysym of the key you want to press.
v.press_keysym(123)

#Where mask is an or-ed combination of the modifiers you want to lock
or latch.  Order is the same as in the xkb api.
v.latch_mod(mask)
v.lock_mod(mask)

The other functions are all to do with getting keyboard layouts.

One more thing, Chris mentions how to send the keydown event, but not the keyup. Here's an example that uses the 'press' and 'release' functions of virtkey
```
import virtkey
import time

# This Example Presses the spacebar once every second for a minute

def press(keyname):
        # 'press_unicode()' emulates the key being pressed down
        # ord() converts the character to it's unicode value
	KeyEmulator.press_unicode(ord(keyname))

        # The key stays pressed down until you tell virtkey to release
        # it with the 'release_unicode()' function. note: you have to specify
        # which key to release with the unicode value again
	KeyEmulator.release_unicode(ord(keyname))

KeyEmulator=virtkey.virtkey()
	
for i in range(60):
	# Presses the key
        press(" ")

        # Wait 1 second
	time.sleep(1)

```

---

### Post by holihue on 2007-12-27
Thank you JustAboutRealJAR :):):):)

This helped me too.

It was exactly what I needed.:):)

---

### Post by fred.reichbier on 2008-03-02
Hello,

sorry for the thread-digging, but I want to add something ;)
Here's a working example how to use modifiers for simulating shortcuts:

```

# simulate CTRL+T
import virtkey
v = virtkey.virtkey()

v.lock_mod(1<<2)

v.press_keycode(28)
v.release_keycode(28)

v.unlock_mod(1<<2)

```

The Modifier values (e.g. 1<<2) are defined in X11/X.h:
```
#define ShiftMask               (1<<0)
#define LockMask                (1<<1)
#define ControlMask             (1<<2)
#define Mod1Mask                (1<<3)
#define Mod2Mask                (1<<4)
#define Mod3Mask                (1<<5)
#define Mod4Mask                (1<<6)
#define Mod5Mask                (1<<7)
```

You can get the keycodes with the tool *xev*:
> KeyPress event, serial 27, synthetic NO, window 0x4800001,
    root 0x8a, subw 0x0, time 1895304872, (715,323), root: (720,371),
    state 0x0, [color=red]**keycode 28**[/color] (keysym 0x74, t), same_screen YES,
    XLookupString gives 1 bytes: (74) "t"
    XmbLookupString gives 1 bytes: (74) "t"
    XFilterEvent returns: False

I hope that's a help for somebody :)

Fred

---

### Post by holihue on 2008-03-06
Thanks Fred, this is very useful. :):):)

---

### Post by JustAboutRealJAR on 2008-03-06
very! I'll be using that info :)

---

### Post by fred.reichbier on 2008-04-03
Hello,

another update:

```
def simulate_keys(keys):
    """ simulate the keys using python-virtkey
        :param keys: (modifiers, keysym); returned by keystroke_to_x11
    """
    modifiers, key = keys

    v = virtkey.virtkey()
    if modifiers:
        v.lock_mod(modifiers)
    try:
        v.press_keysym(key)
        v.release_keysym(key)
    finally:
        if modifiers:
            v.unlock_mod(modifiers)

def keystroke_to_x11(keystroke):
    """ convert "CTRL+Shift+T" to (1<<2 | 1<<0, 28)
        :param keystroke: The keystroke string.
                         - can handle at least one 'real' key
                         - only ctrl, shift and alt supported yet (case-insensitive)
        :returns: tuple: (modifiers, keysym)
    """
    modifiers = 0
    key = ""
    splitted = keystroke.split("+")
    for stroke in splitted:
        lstroke = stroke.lower()
        if lstroke == "ctrl" or lstroke == "control":
            modifiers |= (1 << 2)
        elif lstroke == "shift":
            modifiers |= (1 << 0)
        elif lstroke == "alt":
            modifiers |= (1 << 3) # TODO: right?
        else: # is a ordinary key (Only one)
            key = gtk.gdk.keyval_from_name(stroke)
    return (modifiers, key)
``` (from [gestikk ](https://launchpad.net/gestikk) ;))

Just use simulate_keys(keystroke_to_x11('CTRL+ALT+A')) - it will simulate it ;) It uses gtk at the moment, because I couldn't find a function similar to gtk.gdk.keyval_from_name - maybe you have an idea? :)

Greetings,
Fred

---

### Post by adam35413 on 2008-05-14
I looked through the virtkey C code, but I couldn't tell if there is any way to dictate which tty the key presses go to.  Does anyone know if there is a way?  I want to be able to send key presses to certain virtual terminals.  I need to send it directly to the terminal, so switching to the terminal with something like chvt first won't work.

---

### Post by fred.reichbier on 2008-05-23
Hello,

as far i know, python-virtkey uses the Xtest Extension of the X-Server. I don't think that Xtest is able to send keystrokes to a tty, but I'm not sure.

Cheers,

Fred

---

### Post by adam35413 on 2008-05-23
I had to write a simple kernel module to send the keystrokes to tty.  This allowed me to successfully switch VMWare terminals.

---

### Post by werru on 2009-11-15
fred.reichbier, thank you!
> **JustAboutRealJAR said:**
> 
After ~1 hour of google searches I concluded that there is no documentation for python-virtkey.
I don't find anything  useful too, except you tread. But I do it in 2009 :( 
May be i'm wrong

---

