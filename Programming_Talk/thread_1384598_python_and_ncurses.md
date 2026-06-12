---
title: "python and ncurses"
date: 2010-01-18
forum: Programming Talk
---

### Post by duanedesign on 2010-01-18
I am working on a python program that uses ncurses. I have not found a whole lot of material online so I decided to post here and see if i could get some input.

[The program]("http://pastebin.com/m3da0bb32") runs fine the first time through. After completing one of the commands it goes back to the menu. Then when you execute another command is when it gets buggy. Usually requiring you to close the Terminal.

If anyone has any insight as to what is going wrong here it would be greatly appreciated.

[pastebin of program]("http://pastebin.com/m3da0bb32")

---

### Post by wmcbrine on 2010-01-18
Theoretically, you should call initscr() only once.

I couldn't really see a problem when I ran it, though.

---

### Post by lavinog on 2010-01-18
> **duanedesign said:**
> Then when you execute another command is when it gets buggy. Usually requiring you to close the Terminal.


I am just learning curses, but I noticed that there is a wrapper function that restores the terminal if an exception is raised.

[http://docs.python.org/library/curses.html](http://docs.python.org/library/curses.html):
> Module curses.wrapper
    Convenience function to ensure proper terminal setup and resetting on application entry and exit.

---

### Post by lavinog on 2010-01-18
moving the following outside the while loop seems to fix the error:
```

screen = curses.initscr()

```

You just need to echo output when accepting user input

---

### Post by lavinog on 2010-01-18
also, if you break out of python and don't have your terminal back try typing reset and press enter. It should restore your terminal back to normal.

these lines are reversed:
```

          package = get_param("Enter the package name")
          curses.nocbreak(); screen.keypad(0); curses.echo()

```
you want to turn on echo before the prompt.

---

### Post by lavinog on 2010-01-19
I spent some time modifying your script with some things I just figured out.
I used the wrapper so the terminal returns to normal if things go badly
I used a pad to create a scrollable window for large output
Use q to return to the menu and again to exit
I used subprocess instead of system.
I did not add any window resize events, so resizing the terminal will force it to exit.
[php]
#!/usr/bin/env python

from os import system
import curses

'''
def get_param(screen, prompt_string):
     screen.clear()
     screen.border(0)
     screen.addstr(2, 2, prompt_string)
     screen.refresh()
     input = screen.getstr(10, 10, 60)
     return input
'''

def get_param_new(screen,y,x, prompt_string):
     screen.addstr(y, x, prompt_string)
     screen.refresh()
     curses.echo(); curses.nocbreak(); screen.keypad(0)
     
     input = screen.getstr()
     
     curses.noecho(); curses.cbreak(); screen.keypad(1)
     
     return input

'''
def execute_cmd(cmd_string):
     system("clear")
     a = system(cmd_string)
     print ""
     if a == 0:
          print "Command executed correctly"
     else:
          print "Command terminated with error"
     raw_input("Press enter")
     print ""
     
'''

def execute_cmd_new(screen,args):
    import subprocess
    p = subprocess.Popen(args,
                        stdout=subprocess.PIPE,
                        stderr=subprocess.PIPE )
    
    output,errors = p.communicate()
    output = output.split('\n')

    showdata(screen,output)
    
    
def showdata(screen,data):
    wy,wx=screen.getmaxyx()
    wy-=2
    wx-=2
    if type(data)==str:
        data = data.split('\n')

    padx = max(getmax(data),wx)
    pady = max(len(data)+1,wy)
    max_x = padx-wx
    max_y = pady-wy
    
        
    pad = curses.newpad(pady,padx)
        
    for i,line in enumerate(data):
        pad.addstr(i,0,str(line))
    
    x=0
    y=0
    
    inkey=0
    
    while inkey != 'q':
        pad.refresh(y,x,1,1,wy,wx)
        inkey = screen.getkey()
        
                
        if inkey=='KEY_UP':y=max(y-1,0)
        elif inkey=='KEY_DOWN':y=min(y+1,max_y)
        elif inkey=='KEY_LEFT':x=max(x-1,0)
        elif inkey=='KEY_RIGHT':x=min(x+1,max_x)
        elif inkey=='KEY_NPAGE':y=min(y+wy,max_y)
        elif inkey=='KEY_PPAGE':y=max(y-wy,0)
        elif inkey=='KEY_HOME':y=0
        elif inkey=='KEY_END':y=max_y
        
        
    

def getmax(lines): return max([len(str(l)) for l in lines])


def menu(screen):
  x = 0

  while x != ord('q'):
       curses.cbreak()
       curses.noecho()
       screen.keypad(1)

       screen.clear()
       screen.border(0)
       screen.addstr(2, 2, "Please enter a number...")
       screen.addstr(4, 4, "1 - Find version of a package")
       screen.addstr(5, 4, "2 - List installed packages")
       screen.addstr(6, 4, "3 - Show disk space")
       screen.addstr(7, 4, "q - Exit")
       screen.refresh()

       x = screen.getch()

       if x == ord('1'):
            package = get_param_new(screen,10,4, "Enter the package name: ")
            execute_cmd_new(screen,["dpkg", "-s", package])

       elif x == ord('2'):
            execute_cmd_new(screen,["dpkg", "-l"])

       elif x == ord('3'):
            execute_cmd_new(screen,["df", "-h"])

       elif x == ord('s'):
            curses.nocbreak(); screen.keypad(0); curses.echo()
            wy,wx=screen.getmaxyx()

            screen.addstr(10,4,'Y:'+str(wy))
            screen.addstr(11,4,'X:'+str(wx))

            screen.refresh()
            curses.napms(1000)

       elif x == ord('t'):
            data = range(101)
            showdata(screen,data)

curses.wrapper(menu)
[/php]

---

### Post by duanedesign on 2010-01-23
Thank you everyone who responded. You guys are awesome.

moving
```
screen = curses.initscr()
```
out of the loop did fix the problem. From what i have been able to gather this code works fine in Hardy. Newer versions of Ubuntu not so well.

The wrapper function does seem to be the way to go. Really helps keep from getting a borked terminal.

@lavinog Thank you for your work on this. I have been playing with that wrapper function and was getting stuck. Your code helped a lot. 

I will post my final results.

---

