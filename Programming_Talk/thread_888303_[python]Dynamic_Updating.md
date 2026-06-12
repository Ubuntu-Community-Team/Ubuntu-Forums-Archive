---
title: "[python]Dynamic Updating"
date: 2008-08-13
forum: Programming Talk
---

### Post by Pyro.699 on 2008-08-13
Hello,

Is it possible to dynamically update a line of text in a unix based terminal/command prompt?

An example would be something like the application wget, where the progres bar updates without a new line appearing on the screen.

[quote=Example]
 wget [http://ubuntuforums.org/newthread.php?](http://ubuntuforums.org/newthread.php?)
--01:53:08--  [http://ubuntuforums.org/newthread.php?](http://ubuntuforums.org/newthread.php?)
           => `newthread.php'
Resolving ubuntuforums.org... 91.189.94.12
Connecting to ubuntuforums.org|91.189.94.12|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]

    [====>                               ] 37,245        50.99K/s             

01:53:09 (50.90 KB/s) - `newthread.php' saved [37245]
[/quote]

The progress bar updates without a new line appearing (i know wget is not written in python), but is it possible to do this in python?

If its not possible in python, how about the languages; Perl or Java

[EDIT]
Also, what would this type of functionality be called? Im starting to get the impression that "dynamically updating" is incorrect.
[/EDIT]

Thanks
~Cody Woolaver

---

### Post by samjh on 2008-08-13
> **Pyro.699 said:**
> Is it possible to dynamically update a line of text in a unix based terminal/command prompt?

An example would be something like the application wget, where the progres bar updates without a new line appearing on the screen.

The progress bar updates without a new line appearing (i know wget is not written in python), but is it possible to do this in python?

If its not possible in python, how about the languages; Perl or Java

Also, what would this type of functionality be called? Im starting to get the impression that "dynamically updating" is incorrect.

Have a look at the [FONT="Courier New"]curses[/FONT] module:

Howto: [http://docs.python.org/dev/howto/curses.html](http://docs.python.org/dev/howto/curses.html)

Library doc: [http://docs.python.org/lib/module-curses.html](http://docs.python.org/lib/module-curses.html)

---

### Post by Bachstelze on 2008-08-13
Here's a quick example without the curses library. It won't be very useful, as it can't "update" a line if another has been written (actually, the line isn't updated, but it is deleted and the new one is written instead), but it might give you a better understanding of how things work

```
#!/usr/bin/env python

import sys
import time

count = 0
while count <= 10 :
    sys.stdout.write("\r[" + count*"=" + ">" + (10-count) * " " + "]")

    # Python normally just buffers the lines written to stdout and writes
    #them when a new line character is written. That's not what we want,
    #so we use flush() to force immediate writing.
    sys.stdout.flush()

    count += 1
    time.sleep(1)

sys.stdout.write("\n")

```

---

### Post by Pyro.699 on 2008-08-14
Thankyou HymnToLife,

Do you know how to configure this in Eclipse, because currently it adds a new line but when i run it in the command prompt it works fine.

I did try to do this in curses but i got an error (Running Windows XP)
[quote=test.py]
import curses
stdscr = curses.initscr()
[/quote]
[quote=Eclipse]
Traceback (most recent call last):
  File "C:\Users\Cody\workspace\quickie\src\test.py", line 1, in <module>
    import curses
  File "C:\Python25\lib\curses\__init__.py", line 15, in <module>
    from _curses import *
ImportError: No module named _curses
[/quote]

I do like the way that HymnToLife suggested i do this though

How exactly does "\r" work? because im having multipule lines that i need to print out and change.

Line 1: This is Line one's counter - 000
Line 2: Next Counter - 021
Line 3: Some Random Counter - 054

Each line has a counter that needs to go up... Each line is stored in a variable so everytime "Line 1: This is Line one's counter -001" is printed out, so is all the text along with it.

Thanks
~Cody Woolaver

---

### Post by Pyro.699 on 2008-08-15
Sorry for the bump but i still have some questions. After looking around it turns out that curses is for a linux system only. I also still dont understand how the \r works... should i use \b with this aswell?

Thanks
~Cody Woolaver

---

### Post by pmasiar on 2008-08-15
> **Pyro.699 said:**
> After looking around it turns out that curses is for a linux system only.

not sure where you got that info: [http://docs.python.org/lib/module-curses.html](http://docs.python.org/lib/module-curses.html) says "While curses is most widely used in the Unix environment, versions are available for DOS, OS/2, and possibly other systems as well."


> I also still dont understand how the \r works... 

read up [http://docs.python.org/lib/module-re.html](http://docs.python.org/lib/module-re.html)

---

### Post by Pyro.699 on 2008-08-15
Thats where i got it from. Also, when i tried it in python i got this error:

[quote=cur.py]
import curses
[/quote]
[quote=output]
Traceback (most recent call last):
  File "C:\Users\Cody\workspace\quickie\src\cur.py", line 1, in <module>
    import curses
  File "C:\Python25\lib\curses\__init__.py", line 15, in <module>
    from _curses import *
ImportError: No module named _curses
[/quote]

That was all that was in the file "import curses"

Thanks
~Cody Woolaver

---

### Post by days_of_ruin on 2008-08-15
> **Pyro.699 said:**
> Thats where i got it from. Also, when i tried it in python i got this error:




That was all that was in the file "import curses"

Thanks
~Cody Woolaver

Did you install it on windows?I am sure it doesn't come included.

---

### Post by Pyro.699 on 2008-08-15
No i didnt install it on windows... but after looking through the module im alittle intimidated with using it. I would personally prefer to use the "\r" method thats already used. Im still unsure how to use it to controll multipule lines.

Thanks
~Cody Woolaver

---

### Post by Pyro.699 on 2008-08-15
I went to [http://adamv.com/dev/python/curses/](http://adamv.com/dev/python/curses/) and downloaded the curses module and also downloaded the demos. When i tried to run one of the demos it still said that module was none existant so i renamed "_WCurses.pyd" to "curses.pyd" and then that error went away but if you look at the attachment it shows that another more complex error arose.

Thanks
~Cody Woolaver

---

### Post by Pyro.699 on 2008-08-16
I truly am sorry for the recursive posts but i am still struggling as hard that i try to figure out this task on my own. I have tried several things. I am still unable to get curses to work properly on windows because i keep getting several errors that i find unexplainable. I have read a lot about return carriages **"\r" **understanding that it takes the cursor location and places it at the beginning of the line. A symbol I'm still unable to grasp is the backspace **"\b" **because from my understanding **"Line1\n\bLine2"** should equal **"Line1Line2" **which it is not. I have tried several combinations of **"Line1\nLine2" => "\r\b\rFix1\r\nFix2" **would ultimatly print out **"Fix1\nFix2"** but again that is not the case. I have taken a serious atempt at learnig how to use the regular expressions and escape characters but after 3 days am still running into obsticles from the verry beggining.

The error i recieved from the curses module was one that made python.exe crash and from my understanding that means an internal program failure so there would be something else wrong. The system that this is taking place on is a Windows XP Home, Service Pack 2, x86 Intel. If there is any information that could help me achieve my goal would be greatly appreachiated.

Thanks again for your help
~Cody Woolaver

---

### Post by Bachstelze on 2008-08-16
> **Pyro.699 said:**
> A symbol I'm still unable to grasp is the backspace **"\b" **because from my understanding **"Line1\n\bLine2"** should equal **"Line1Line2" **which it is not.

\b is like \r, except that it just goes one character backwards. However, it can not "delete" new lines when printing to stdout. If a line has been printed, then it has been printed and there's nothing you can do about it. That's why my example code didn't print a \n until the very end of the script: as long as a newline has not been printed, you can edit your line as you wish.

In other words, if at the beginning of a line, \b and \r do the same thing: nothing.

---

### Post by Pyro.699 on 2008-08-16
After doing quite a bit of research and talking amongst my friends im now learning that the most effective way to go about doing this would be to use the curses module. Does anyone know what i can do to get it working properly, there doesnt seem to be much online documentation explaining such errors.

Thanks again
~Cody Woolaver

---

