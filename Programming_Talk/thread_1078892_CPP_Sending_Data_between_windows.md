---
title: "CPP Sending Data between windows"
date: 2009-02-23
forum: Programming Talk
---

### Post by amainejr on 2009-02-23
How would I send data directly to another terminal window?  Keeping it simple, say I have something similar to the following:

```

#include <iostream>

void sendData(int, hWnd);

void main()
{
    int someNumber = 100;
    sendData(someNumber, terminal2);
}

void sendData(int number, hWnd theWindow)
{
    //theWindow.isOpen() = true;
    //setFocus(theWindow);
    std::cout << number << std::endl;
}

```


I'm wondering how to define the other window without using hWnd programming.  Something along the lines of the Window's getWindowHandle() function, without using window's programming.  Any ideas on how to get another window's id, set the focus to that window, and enter data into that window, assuming it is a textbox or other input area, such as a terminal?  std::cin gets data from the standard input, the keyboard.  I know I could make 2 structs or classes and pass the data internally, but I'm working on making a prototype for a wireless transceiver, so the data would have to traverse an unconnected medium to the other transceiver, which I'll figure out later.  Any ideas?

---

### Post by movieman on 2009-02-24
Is this the kind of thing you're looking for?

[http://www.doctort.org/adam/nerd-notes/x11-fake-keypress-event.html](http://www.doctort.org/adam/nerd-notes/x11-fake-keypress-event.html)

---

### Post by amainejr on 2009-02-24
I think that will just about work.  At least it does give the means for doing it under the X11 system.  I'll have to go load up my laptop and see what that bad boy will do.  Just looking at it, I think it is actually going to simulate a keypress, which is fine.  I can create a module to loop through the data one character at a time and send it that way.  Thanks.  Going to go try it now.

---

