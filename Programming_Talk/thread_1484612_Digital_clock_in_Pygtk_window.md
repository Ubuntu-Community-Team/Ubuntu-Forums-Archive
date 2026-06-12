---
title: "Digital clock in Pygtk window"
date: 2010-05-15
forum: Programming Talk
---

### Post by Patagon on 2010-05-15
I need to show the updated time in a window (or label).

I was looking a example with Tkinter but I do not know how to integrate in a pygtk window

This is the code 
[PHP]# use Tkinter to show a digital clock
# tested with Python24    vegaseat    10sep2006

from Tkinter import *
import time

root = Tk()
time1 = ''
clock = Label(root, font=('times', 20, 'bold'), bg='white')
clock.pack(fill=BOTH, expand=1)

def tick():
    global time1
    # get the current local time from the PC
    time2 = time.strftime('%H:%M:%S')
    # if time string has changed, update it
    if time2 != time1:
        time1 = time2
        clock.config(text=time2)
    # calls itself every 200 milliseconds
    # to update the time display as needed
    # could use >200 ms, but display gets jerky
    clock.after(200, tick)

tick()
root.mainloop(  )[/PHP]

Bye

---

