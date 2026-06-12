---
title: "Python and curses"
date: 2011-04-26
forum: Programming Talk
---

### Post by Mosabama on 2011-04-26
hey, I am new to curses Library.
I have python code that runs fine with no problems, but when I resize the window of the terminal emulator, the program exists automatically.

actually this program has something to do with size of the screen or the terminal emulator. 
maybe if I post the code you will understand what I need.

I want curses to adjust with the change of the size of the window without any problems.. is it possible?

take a look at the code:

 ```

import curses
import time
from math import floor



def makewin(row,col,y=0,x=0):
    win=curses.newwin(row,col,y,x)
    win.box()
    return win

def start_center(totaly,totalx,string):
    length=len(string)
    return floor(totalx/2)-floor(length/2)

#This function shows where the string should start in a window                                                                                             
#args: max Y and Max X of the window and the length of the string                                                                                                                                              

def main(stdscr):
                                                                                                                                        
    maxy,maxx=stdscr.getmaxyx()
    stdscr.box()
    stdscr.addstr(1,1,"max Y:" + str(maxy))
    stdscr.addstr(2,1,"max X:" + str(maxx))
    center=start_center(maxy,maxx,"This is the title")
    stdscr.addstr(0,center,"This is the title",curses.A_STANDOUT)


    stdscr.refresh()
    stdscr.getch()

curses.wrapper(main)






```

---

### Post by cgroza on 2011-04-26
Do you get any error messages?

---

### Post by juancarlospaco on 2011-04-26
You can try Urwid or python-Dialog

---

### Post by Mosabama on 2011-04-26
> **cgroza said:**
> Do you get any error messages?

Not at all

---

### Post by Mosabama on 2011-04-26
> **juancarlospaco said:**
> You can try Urwid or python-Dialog

how to use that?

---

### Post by Mosabama on 2011-04-26
I took a look at python-dialog .. but I think its very limited to simple applications.. am I right?

---

### Post by cgroza on 2011-04-26
Do you really need to program CLI applications? If not , I suggest you learning a GUI  toolkit, such as wxPython.

---

### Post by Mosabama on 2011-04-26
> **cgroza said:**
> Do you really need to program CLI applications? If not , I suggest you learning a GUI  toolkit, such as wxPython.

I have 2 reasons:
1- I am planning to make some administration programs that run on server, and most linux servers dont have GUI. so it runs with or without X server.
2. its really fun. I love old stuff 

can you really give up Htop for gnome system monitor?

---

### Post by cgroza on 2011-04-26
Try running your program with IDLE, the application will crash, but the interpreter will stay there, possibly with your error message.

---

### Post by juancarlospaco on 2011-04-27
> **Mosabama said:**
> I took a look at python-dialog .. but I think its very limited to simple applications.. am I right?

No.

Dialog is used to compile Linux Kernel from source code, 
i dont think that your app is more complex than that.

---

### Post by wmcbrine on 2011-04-27
Your program exits on a key event. A resize generates a key event. Thus, your program exits when you resize the terminal. There is no error here.

Yes, you can adjust to handle a resize. That's what the event is for.

Please ignore the previous posters; they are obviously unfamiliar with curses.

As an example, here's how you could modify your program to display the new size, while exiting on a press of 'q' -- move most of your main() to a separate function (so it can be called repeatedly), add a clear() call to that, and make a simple loop:

```
def draw(stdscr):
                                                                                                                                        
    stdscr.clear()
    maxy,maxx=stdscr.getmaxyx()
    stdscr.box()
    stdscr.addstr(1,1,"max Y:" + str(maxy))
    stdscr.addstr(2,1,"max X:" + str(maxx))
    center=start_center(maxy,maxx,"This is the title")
    stdscr.addstr(0,center,"This is the title",curses.A_STANDOUT)


    stdscr.refresh()

def main(stdscr):
    while True:
        draw(stdscr)
        key = stdscr.getch()
        if key == ord('q'):
            break
```

Or to make it closer to your original -- exiting on any key *except* the resize pseudo-key:

```
if key != curses.KEY_RESIZE:
    break
```

---

