---
title: "xlib keyboard encoding"
date: 2013-02-16
forum: Programming Talk
---

### Post by thedardanius on 2013-02-16
hey,

Im trying to get the keyboard input in this way:
if one key is pressed, check the keycode. Put this in an array of bools (bool[256]), to check and store which keycodes are on/off with keypressmaks and keyrelease.
However, what next?? I know keycodes are the "raw" data returned from some processing though drivers and hardware and kernel, but what then? Do I need to do sth with keysym? I know that keycodes do not have determined actual keys, so e.g. code 2 isnt always key "A" or "enter". How can I decode this chaos into actual physical keys, so I can create my game? Isnt there sth like virtual key codes in windows, which does have determined physical keys connected to each code?
BTW, when I press a key, I never get focus. So my app is in front, (assume it has focus) and I press eg.g a. Keypress event doesnt return a to be true (at least the translated keysym isnt there). nstead, other programs get the input. How come? How can I get full autonomous focus of one keyboard?

Finally, does anyone know a decent rather complete beginner's tutorial on xlib and preferable glx? I really need some decent material to learn it....

And another thing, why is my glx xlib app so laggy? Is this due to the fact that the client has to wait for the server, or simply because of me (actually you cant really know cause you havent seen the code. However, I would appreciate it if you would give me some potential factors contributing to lagginess in an glx program).

Im new to linux. I like it, I like the new xlib system/glx, but its so hard for a beginner. I alsodislike that fact that there so many independant window managers, all having different things and casuing xlib not to have full control of the window system, altough xlib wasnt designed for that i thought...

---

### Post by xytron on 2013-02-18
> **thedardanius said:**
> hey,

Im trying to get the keyboard input in this way:
if one key is pressed, check the keycode. Put this in an array of bools (bool[256]), to check and store which keycodes are on/off with keypressmaks and keyrelease.
However, what next?? I know keycodes are the "raw" data returned from some processing though drivers and hardware and kernel, but what then? Do I need to do sth with keysym? I know that keycodes do not have determined actual keys, so e.g. code 2 isnt always key "A" or "enter". How can I decode this chaos into actual physical keys, so I can create my game? Isnt there sth like virtual key codes in windows, which does have determined physical keys connected to each code?
BTW, when I press a key, I never get focus. So my app is in front, (assume it has focus) and I press eg.g a. Keypress event doesnt return a to be true (at least the translated keysym isnt there). nstead, other programs get the input. How come? How can I get full autonomous focus of one keyboard?

Finally, does anyone know a decent rather complete beginner's tutorial on xlib and preferable glx? I really need some decent material to learn it....

And another thing, why is my glx xlib app so laggy? Is this due to the fact that the client has to wait for the server, or simply because of me (actually you cant really know cause you havent seen the code. However, I would appreciate it if you would give me some potential factors contributing to lagginess in an glx program).

Im new to linux. I like it, I like the new xlib system/glx, but its so hard for a beginner. I alsodislike that fact that there so many independant window managers, all having different things and casuing xlib not to have full control of the window system, altough xlib wasnt designed for that i thought...



I think you are making this more difficult than it actually is.

Use the function XLookupString to map a KeyPress event to a keysym (from including the file keysym.h).


Then just use an if statement to compare what the function computed on the KeyPress event to the keysym codes.

For example something such as;

if ((keysym == XK_Return) then .....(whatever)


The variable keysym is of type KeySym.

In this example you take an action whenever the return key is pressed.

That's mostly all there is to it.

Here's a link for an example I found from Googling;

[http://sidvind.com/wiki/Xlib_and_GLX:_Part_2]("http://sidvind.com/wiki/Xlib_and_GLX:_Part_2")

---

### Post by thedardanius on 2013-02-19
> **xytron said:**
> I think you are making this more difficult than it actually is.
 
Use the function XLookupString to map a KeyPress event to a keysym (from including the file keysym.h).
 
 
Then just use an if statement to compare what the function computed on the KeyPress event to the keysym codes.
 
For example something such as;
 
if ((keysym == XK_Return) then .....(whatever)
 
 
The variable keysym is of type KeySym.
 
In this example you take an action whenever the return key is pressed.
 
That's mostly all there is to it.
 
Here's a link for an example I found from Googling;
 
[http://sidvind.com/wiki/Xlib_and_GLX:_Part_2](http://sidvind.com/wiki/Xlib_and_GLX:_Part_2)
 
very clear. I didnt expect it to be that easy. So basically, it should work, but its not compatible with my engine im writing. I watn arrays of 256 bools, each representing a key code. I want to know, if one key code is pressed, which key that is. Currently, im trying to translate keysyms to keycode, and they check which arrays of kecodes are true. Im cross platform programming, on windows it works in this way, and I would like to do it on xlib as well.

---

