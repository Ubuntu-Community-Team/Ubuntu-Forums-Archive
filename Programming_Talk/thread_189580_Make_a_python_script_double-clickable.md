---
title: "Make a python script double-clickable"
date: 2006-06-05
forum: Programming Talk
---

### Post by 3rdalbum on 2006-06-05
I would like to set up my Python script so it opens by double-clicking in Gnome. Right now, when you double-click it, it opens in gedit. I've got Nautilus set to "Ask each time" for executable text files.

I've tried putting #!/usr/python at the top of my script, but to no avail.

If someone could please tell me how to achieve this, or point me to a URL about it, I would be most appreciative.

---

### Post by dabear on 2006-06-05
ehm, you could compile the file to a .pyc? look at modules such as compileall

---

### Post by Engnome on 2006-06-05
Havent tried python but in perl adding the line #!/usr/bin/perl and then adding execute permissions to the file will make the "Run in terminal Display Cancel Run" dialog pop up if you double click it. Maybe there is something similar in python?

---

### Post by simplyw00x on 2006-06-05
Definitely the way to go is "chmod +x" the file (or use the GUI in nautilus to add execute permissions).

---

### Post by Engnome on 2006-06-05
Did you change your first post to include:
[QUOTE=3rdalbum]
I've tried putting #!/usr/python at the top of my script, but to no avail.
[/QUOTE]

?

If so dont do that in the future. People wont notice the new info and thread continuity will be disrupted.

If not sorry I bothered you.

Anyway its should be #!/usr/bin/python (atleast on my system) Then right click the file and select properties. Under the permissons tab mark the Execute boxes.

---

### Post by Ingenue on 2008-08-17
I know this post is old as hell, but...how do you make the terminal hang around after it is run after being clicked. I know other ways to run the script. Maybe I am not asking this right?

---

### Post by Steveway on 2008-08-17
You should put:
#!/usr/bin/env python
at the top of your program.

---

### Post by Ingenue on 2008-08-17
> **Steveway said:**
> You should put:
#!/usr/bin/env python
at the top of your program.

bless you!

---

### Post by unutbu on 2008-08-17
@Ingenue, perhaps you could swap computers with OzzyFrank: [http://ubuntuforums.org/showpost.php?p=5604819&postcount=1](http://ubuntuforums.org/showpost.php?p=5604819&postcount=1)

If the shipping cost is prohibitive, then hm...
how about this:

```
#!/usr/bin/env python
print "Hello"
raw_input()

```
ending the script with "raw_input()" seems to preserve the terminal until you press a key.

---

### Post by LaRoza on 2008-08-17
> **unutbu said:**
> 
ending the script with "input()" seems to preserve the terminal until you press a key.

Use "raw_input()", input() will evaluate the input, and you don't want that.

Also, the actions of double clicking is up to the file manager. In Windows, double clicking does weird things (like if you change the exenstion of of something and double click it, it will automatically run it!)

Most Linux file managers usually give a dialog (like run, edit and such), but can be configured to do others things.

---

### Post by pmasiar on 2008-08-17
> **LaRoza said:**
> Also, the actions of double clicking is up to the file manager. 

... and you don't need it.

Preferably run your program from IDLE. If not, open terminal, cd to directory where your program lives (assuming it is called myprogram.py), and type "python mypr" <TAB>. Shell is smart, it checks which files match "mypr" and adds the rest of the filename if can be resolved uniquely.

And running your program again from shell is even simpler: hit up-arrow and previous line from shell history will pop up, edit parameters or just hit enter to run it.

And you can switch between editor and shell by alt-tab, like in windows, but you knew that?

Keyboard is much faster than fiddling around with the mouse - Linux gurus have zillions such timesaving tips for you, free for taking.

Enjoy!

---

### Post by Ingenue on 2008-08-17
> **pmasiar said:**
> ... and you don't need it.

Preferably run your program from IDLE. If not, open terminal, cd to directory where your program lives (assuming it is called myprogram.py), and type "python mypr" <TAB>. Shell is smart, it checks which files match "mypr" and adds the rest of the filename if can be resolved uniquely.

And running your program again from shell is even simpler: hit up-arrow and previous line from shell history will pop up, edit parameters or just hit enter to run it.

And you can switch between editor and shell by alt-tab, like in windows, but you knew that?

Keyboard is much faster than fiddling around with the mouse - Linux gurus have zillions such timesaving tips for you, free for taking.

Enjoy!

I see what you are saying, and I do that as well. I just wanted to know because I want to know...

Thanks again!

---

