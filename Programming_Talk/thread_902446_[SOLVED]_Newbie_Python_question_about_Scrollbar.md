---
title: "[SOLVED] Newbie Python question about Scrollbar"
date: 2008-08-27
forum: Programming Talk
---

### Post by aktiwers on 2008-08-27
I want to use the "moveto" command in my scrollbar show here:
[http://www.tcl.tk/man/tcl8.4/TkCmd/scrollbar.htm#M26](http://www.tcl.tk/man/tcl8.4/TkCmd/scrollbar.htm#M26)
and here
[http://effbot.org/tkinterbook/scrollbar.htm](http://effbot.org/tkinterbook/scrollbar.htm)

I want it to keep scrolling to the end , so I give the scrollbar command=callback("1.0", offset)

This is obviously completely wrong and it gives me thes error:
> Traceback (most recent call last):
  File "test.py", line 83, in <module>
    scrollBar.config(command=callback("1.0", offset))
NameError: name 'callback' is not defined

So my question is how do I use the information given by pages like the one above, or better, how do I use this "moveto" command?

Thanks a lot

Edit: Okay already figured out that it needs to be something like this.. 
scrollBar.config(command=("moveto", 0.0))

sorry for my noobness..  gonna play with it now :)

---

### Post by y-lee on 2008-08-27
It would help to see your code and not just one error message.

> I want it to keep scrolling to the end , so I give the scrollbar command=callback("1.0", offset)

callback should be a function or method name defined by you or one of the import modules. 

> command=
    A callback used to update the associated widget. This is typically the xview or yview method of the scrolled widget.
    If the user drags the scrollbar slider, the command is called as callback(“moveto”, offset), where offset 0.0 means that the slider is in its topmost (or leftmost) position, and offset 1.0 means that it is in its bottommost (or rightmost) position.
    If the user clicks the arrow buttons, or clicks in the trough, the command is called as callback(“scroll”, step, what). The second argument is either “-1” or “1” depending on the direction, and the third argument is “units” to scroll lines (or other unit relevant for the scrolled widget), or “pages” to scroll full pages. (command/Command)

---

### Post by aktiwers on 2008-08-27
Thanks for the reply.
I actually found out that I need the scrollbar.set(hi) from that page. I also cant get this to work :S

Okay first I have this function :
[php]
def skriv():
    
    f = open(dokument, "r") # Reads doc..

    
    for line in f:    
        time.sleep(tid)
        yield line

[/php]Then I have this other function:
[php]
def startskriv():
   
    for line in skriv():
        startT.insert(END, line)
        startT.pack()
        startT.update()
    
[/php]And lastly the gui part:
[php]
startframe = Frame(root)
startframe.pack()
scrollBar = Scrollbar(startframe)
scrollBar.pack(side=RIGHT, fill=Y)
startT = Text(startframe, bg="white",yscrollcommand=scrollBar.set, font=("verdana", 20))
scrollBar.config(command=startT.yview)
[/php]This takes some text from a txt file and print it linie for linie in the Text area. 
Now I want to add to it, so that when the txt file contains more linies than the text area has, it automatically scrolls down to the last line.

I was thinking about using the scrollBar.set(hi), but I guess I need to write a function that gets the current size of the scroller and then use set(to that point) ?

Sorry I am still a newbie..  I really want this to work :)

---

### Post by aktiwers on 2008-08-27
I changed the my startskriv() function to this:
[php]
def startskriv():
   
    for line in skriv():
        startT.insert(END, line)
        startT.pack()
        startT.update()
        pos = scrollBar.get()
        scrollBar.set(pos[0], pos[1])
        print pos[1]
[/php]It runs and prints the right stuff and all.. but the scrollbar does not move?

---

### Post by aktiwers on 2008-08-27
I solved it..  I was looking the wrong place..  I this setting is in the Text widget.. 
I added this to my startskriv() function and it does like I want.
startT.yview_moveto(1.0)

Cheers!

---

