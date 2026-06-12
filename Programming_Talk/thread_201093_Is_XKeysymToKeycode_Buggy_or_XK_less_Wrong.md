---
title: "Is XKeysymToKeycode Buggy? or XK_less Wrong?"
date: 2006-06-21
forum: Programming Talk
---

### Post by SNX on 2006-06-21
Hi

I'm coding a platform independent Keyboard class for my engine, and at the moment I'm having a very annoying problem. I'm currently storing the strings internally in an array, of the key's I wish to have available to my engine. These strings are in the form of "KP_0", "greater", etc, and they can all be found in the "keysymdef.h" header file. So I know they are correct (or you would hope ...). Then I convert them into KeySym's by using the XStringToKeysym("string"); However I need the keycode of the various keys, not the "virtual keys", so I then use XKeysymToKeycode(Display*,KeySym) to get the required keycode. This is shown below:

[B]
       KeySym tempKey = XStringToKeysyn("less");
       KeyCode tempCode = XKeysymToKeycode(display, tempKey);[/B]

This works for every single key on the keyboard, except "less" (<) key. For example the keycode 46 would be assigned to both "l" and "L", and the keycode 14, would be assigned to both "5" and "%", and this is true because "l" and "L" are the same key, and "5" and "%" are the same key.

This is how it works for the intire keyboard, except for keycode 59, which should correspond to both "<" and ",". It assigns 59 to "," but not to "<", which is instead assigned 94. However they share the same physical key and for that matter should have the same keycode.

I've debugged it for ages, and I know that everything is correct up to the point where its calling XKeysymToKeycode. How do I know? Because I directly substituted the KeySym, which is XK_less into the function and still ontained the incorrect result. 

I also moved the software to a diffirent machine, just to make sure it wasnt my laptops keyboard that was just funky. Still exactly the same problem. The only commonality between the two boxes are that their both pentiums and one has Ubunutu 6.2.12-10 and the other Ubuntu 2.6.10-5. Which leads me to think that the function is buggy, because I cant find any other KeySym which represent this key.

If anyone knows about this problem, or has any advice please let me know, because this is driving me insane! Its just the "<" key on the intire keyboard with the wrong keycode!](*,) 

(PS, I have search for similar problems but didnt find any soluitions. I aplogise if it has been solved before and I used the wrong search string. I'm also fairly new to Linux)

Cheers
-SNX

---

