---
title: "How to write a USB keyboard simulator?"
date: 2009-03-13
forum: Programming Talk
---

### Post by houbysoft.xf.cz on 2009-03-13
Hi, I have been bothering with this thing and still don't have any answer...

So this is my question:

Let's say we have 2 computers connected with each other via USB. How to make a program that could be run on one of the computers and send keystrokes to the another? In other words the computer with the program would appear as a keyboard to the other computer?

Thanks for all the answers :)

---

### Post by crazyfuturamanoob on 2009-03-14
How to make a key press (compile with -lXtst):
```

#include <stdio.h>

#include <X11/Xlib.h>
#include <X11/extensions/XTest.h>

#define KEY_DOWN True
#define KEY_UP   False

/* key codes */
#define KEYCODE_ESC 9
#define KEYCODE_A 38
#define KEYCODE_K 45
#define KEYCODE_B 56
#define KEYCODE_L 46
#define KEYCODE_O 32
#define KEYCODE_ENTER 36

Display *dpy;

/* generate a key press */
void keypress( int keycode )
{
    XTestFakeKeyEvent(dpy, keycode, KEY_DOWN, CurrentTime);
    XTestFakeKeyEvent(dpy, keycode, KEY_UP, CurrentTime);
}


int main() 
{
    /* init */
    dpy = XOpenDisplay(NULL);
    if (!dpy) return 1;
    
    /* press A key */
    keypress( KEYCODE_A );
    
    /* cleanup */
    XCloseDisplay(dpy);
    return 0;
}

```
And to get keycodes, use **xev**:
> 
KeyPress event, serial 33, synthetic NO, window 0x4800001,
    root 0x13b, subw 0x0, time 3022336, (549,249), root:(559,346),
    state 0x0, **keycode 38** (keysym 0x61, a), same_screen YES,
    XLookupString gives 1 bytes: (61) "a"
    XmbLookupString gives 1 bytes: (61) "a"
    XFilterEvent returns: False

You could also include some X headers to get all keycodes without xev. No idea if this was helpful at all.

---

### Post by houbysoft.xf.cz on 2009-03-14
Thanks for the reply, but this won't help me... I need it done in hardware, so that one of the computers acts as a simulated keyboard, and the second recognizes the other just as a normal keyboard...

Thanks anyway

---

### Post by Zugzwang on 2009-03-14
> **houbysoft.xf.cz said:**
> Thanks for the reply, but this won't help me... I need it done in hardware, so that one of the computers acts as a simulated keyboard, and the second recognizes the other just as a normal keyboard...


That's quite hard to do. I assume that you are connecting the computers using some USB link "cable" (containing some controller) in contrast to just connecting the two computers using a USB cable and an adapter, as here you would have two USB hosts connected, which AFAIK isn't allowed. However, if you have that link "cable" in between, it will report itself to the second computer as being a link cable and not a keyboard. You best bet is probably to get some USB development kit and start twiggling around.

---

### Post by crazyfuturamanoob on 2009-03-14
Maybe just split your keyboard's USB cable in two?

---

### Post by winch on 2009-03-14
You could possibly use the parallel port on the source computer to emulate a ps/2 keyboard plugged into the target computer.

I doubt usb is possible without a microcontroller.

---

### Post by houbysoft.xf.cz on 2009-03-14
Thanks all for replies, I now also realized that USB would be hard because using a simple cable, the voltage would probably be too high.

> **winch said:**
> You could possibly use the parallel port on the source computer to emulate a ps/2 keyboard plugged into the target computer.

I doubt usb is possible without a microcontroller.
This looks promising, could you please give more details about how to do this? Today evening I will try googling a little bit to figure out how to do this, thanks.

---

### Post by NathanB on 2009-03-14
I can't help but think that the wrong terminology is being used here.  Is it possible that instead of "keyboard simulator", your goal is to create a "thin client" or "dumb terminal" or something of that fair?

There exist various approaches:

[http://en.wikipedia.org/wiki/Computer_terminal](http://en.wikipedia.org/wiki/Computer_terminal)

[http://en.wikipedia.org/wiki/Terminal_emulator](http://en.wikipedia.org/wiki/Terminal_emulator)

[http://en.wikipedia.org/wiki/Dumb_terminal#Dumb_terminal](http://en.wikipedia.org/wiki/Dumb_terminal#Dumb_terminal)

In the Unix/Linux world, SSH is popular for remote usage of computing resources:

[http://en.wikipedia.org/wiki/Secure_Shell](http://en.wikipedia.org/wiki/Secure_Shell)

---

### Post by houbysoft.xf.cz on 2009-03-14
> **NathanB said:**
> I can't help but think that the wrong terminology is being used here.  Is it possible that instead of "keyboard simulator", your goal is to create a "thin client" or "dumb terminal" or something of that fair?

There exist various approaches:

[http://en.wikipedia.org/wiki/Computer_terminal](http://en.wikipedia.org/wiki/Computer_terminal)

[http://en.wikipedia.org/wiki/Terminal_emulator](http://en.wikipedia.org/wiki/Terminal_emulator)

[http://en.wikipedia.org/wiki/Dumb_terminal#Dumb_terminal](http://en.wikipedia.org/wiki/Dumb_terminal#Dumb_terminal)

In the Unix/Linux world, SSH is popular for remote usage of computing resources:

[http://en.wikipedia.org/wiki/Secure_Shell](http://en.wikipedia.org/wiki/Secure_Shell)

Thanks for replying but I don't want a thin client or dumb terminal... my goal with this is to create something that will be able to for example brute force a BIOS password in case you'll forget it - that's why I need it done in hw because otherwise you can't connect to the computer (when it only is booted to BIOS).

---

### Post by NathanB on 2009-03-14
Rather than using a second computer, I am sure that a microcontroller can be made to "brute force" interrogate the BIOS password.  Here are some options:

BASIC Stamp  [http://www.parallax.com/tabid/295/Default.aspx](http://www.parallax.com/tabid/295/Default.aspx)

Javelin Stamp
[http://www.parallax.com/tabid/127/List/0/CategoryID/13/Level/a/SortField/0/Default.aspx](http://www.parallax.com/tabid/127/List/0/CategoryID/13/Level/a/SortField/0/Default.aspx)

You can then wire one of those to a USB interface:

[http://www.quickusb.com/store/index.php?main_page=index&cPath=1](http://www.quickusb.com/store/index.php?main_page=index&cPath=1)

[related info]
[http://www.beyondlogic.org/usb/usbhard2.htm](http://www.beyondlogic.org/usb/usbhard2.htm)

But I believe it would be much less expensive and easier to build if you go via the PS/2 plug (if your comp happens to have one):

[http://www.computer-engineering.org/ps2protocol/](http://www.computer-engineering.org/ps2protocol/)

[related info]
[http://wiki.osdev.org/Keyboard_Controller](http://wiki.osdev.org/Keyboard_Controller)

Hope that helps!

---

### Post by houbysoft.xf.cz on 2009-03-15
> **NathanB said:**
> Rather than using a second computer, I am sure that a microcontroller can be made to "brute force" interrogate the BIOS password.  Here are some options:

BASIC Stamp  [http://www.parallax.com/tabid/295/Default.aspx](http://www.parallax.com/tabid/295/Default.aspx)

Javelin Stamp
[http://www.parallax.com/tabid/127/List/0/CategoryID/13/Level/a/SortField/0/Default.aspx](http://www.parallax.com/tabid/127/List/0/CategoryID/13/Level/a/SortField/0/Default.aspx)

You can then wire one of those to a USB interface:

[http://www.quickusb.com/store/index.php?main_page=index&cPath=1](http://www.quickusb.com/store/index.php?main_page=index&cPath=1)

[related info]
[http://www.beyondlogic.org/usb/usbhard2.htm](http://www.beyondlogic.org/usb/usbhard2.htm)

But I believe it would be much less expensive and easier to build if you go via the PS/2 plug (if your comp happens to have one):

[http://www.computer-engineering.org/ps2protocol/](http://www.computer-engineering.org/ps2protocol/)

[related info]
[http://wiki.osdev.org/Keyboard_Controller](http://wiki.osdev.org/Keyboard_Controller)

Hope that helps!

Thanks a lot! I will study both the options and see what's better for me :) A microcontroller would be really cool but when I checked the links I saw that it's pretty expensive compared to the PS/2 plug.

Thanks again

---

