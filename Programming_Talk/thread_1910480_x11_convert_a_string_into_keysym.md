---
title: "x11 convert a string into keysym"
date: 2012-01-17
forum: Programming Talk
---

### Post by fargalaxy1 on 2012-01-17
Dear all,
i need to send fake key events to my application, where the keysym to send is readen from a config file and saved to a vector<string>. 
I use:
```
 
[...]
#include <X11/Xlib.h>  
#include <X11/Intrinsic.h>  
#include <X11/extensions/XTest.h>  
#include <unistd.h>  

//the below function from [http://bharathi.posterous.com/x11-fake-key-event-generation-using-xtest-ext](http://bharathi.posterous.com/x11-fake-key-event-generation-using-xtest-ext)

static void **sendKBEvent** (Display * display, KeySym keysym, KeySym modsym)
{
  KeyCode keycode = 0, modcode = 0;
  
  keycode = XKeysymToKeycode (display, keysym);
  
  if (keycode == 0) return;

  XTestGrabControl (display, True);

  /* Generate modkey press */
  if (modsym != 0)
  {
     modcode = XKeysymToKeycode(display, modsym);
     XTestFakeKeyEvent (display, modcode, True, 0);
  }

  /* Generate regular key press and release */
  XTestFakeKeyEvent (display, keycode, True, 0);
  XTestFakeKeyEvent (display, keycode, False, 0);

  /* Generate modkey release */
  if (modsym != 0)
    XTestFakeKeyEvent (display, modcode, False, 0);

  XSync (display, False);
  XTestGrabControl (display, False);
}


int **main**(int argc, char** argv)
{
   [...]
   vector<string> kbdEventsVect;

   ConfigFile configFile;
    
   kbdEventsVect = configFile.parseFile("file.txt");
   
   /*kbdEventsVect[] contains XK_Up, XK_Down, XK_Escape, XK_Right*/

   [...]
   sendKBEvent(display, kbdEventsVect[0], 0);
  [...]
 }


```the problem is that the compiler does not like me passing a string ( kbdEventsVect[0]) to 
sendKBEvent(), which instread needs a Keysym var as 2 argument.

```
error: cannot convert ‘std::basic_string<char,  std::char_traits<char>, std::allocator<char> >’ to  ‘KeySym’ for argument ‘2’ to ‘void sendKBEvent(Display*, KeySym,  KeySym)’
```The wired thing is that if I pass directly the string, everything works fine

```
   sendKBEvent(display, XK_F11, 0); 
```but If I use &kbdEventsVect[0] == XK_F11

```
sendKBEvent(display, kbdEventsVect[0], 0); 
```I guess i'm missing something...

Thank you for any help you would give me.

Martina

---

### Post by dwhitney67 on 2012-01-17
A KeySym is a typedef for a long unsigned int.

It would seem from the error that you posted, that you are attempting to pass an STL string (which you retrieved from a vector), not a character within that string for the KeySym parameter.

Try something like:
```

sendKBEvent(display, kbdEventsVect[0][0], 0);

```

---

### Post by fargalaxy1 on 2012-01-17
Thank you for your help!

I tried your code and now it finally compiles! The only problem is that i need to send the whole string , say: **XK_F11**, but with the below code I just send **X** to sendKBEvent() which instead needs the whole **XK_F11** to know what to do next.

sendKBEvent(display, kbdEventsVect[0][0], 0);
 Maybe i can loop through the kbdEventsVect[0], save to a char array and then convert it to a long unsigned int. What do you think?

Martina

---

### Post by dwhitney67 on 2012-01-17
> **fargalaxy1 said:**
> Thank you for your help!

I tried your code and now it finally compiles! The only problem is that i need to send the whole string , say: **XK_F11**, but with the below code I just send **X** to sendKBEvent() which instead needs the whole **XK_F11** to know what to do next.

sendKBEvent(display, kbdEventsVect[0][0], 0);
 Maybe i can loop through the kbdEventsVect[0], save to a char array and then convert it to a long unsigned int. What do you think?

Martina

My $0.02...

I recommend that you setup an STL map, where you can have a relationship between a string and a KeySym value.  For example:
```

typedef std::map<std::string, KeySym>  KeySymMap;
...
KeySymMap myKeySymMapping;
...
myKeySymMapping["XK_F11"] = XK_F11;

```
Later, when you want to process a key-sym strings, look up the appropriate KeySym value from the map.
```

KeySymMap::iterator it = myKeySymMapping.find(keysymstr);
KeySym sym;

if (it != myKeySymMapping.end())
{
   sym = it->second;
}
else
{
   //error
}

```

---

### Post by fargalaxy1 on 2012-01-17
Thank you!
I'll try your suggestion.

Cheers,

Martina

---

