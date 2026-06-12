---
title: "Making the Most out of gedit for C/C++"
date: 2008-11-02
forum: Programming Talk
---

### Post by Arukas on 2008-11-02
I've tried many IDEs.  I've tried KDevelope and Anjuta, and look at various others.  I couldn't find anything close to bloodshed.  Right now I just don't have time sit down and get used the IDEs. 

I'm using gedit and the terminal to write and run my programs.  I've notice gedit is pretty nice to use.  I've notice there's external tools plugins and what not.  

So my question is:
Is there a way I can get gedit to just compile my program using the gcc compiler? and run it?  

Also this scripting?  Where can I learn it?

---

### Post by LaRoza on 2008-11-02
You should use the terminal plugin for running and compiling in Gedit.

The file browser is also very useful, and I couldn't do without it.

---

### Post by jimi_hendrix on 2008-11-02
> **Arukas said:**
> So my question is:
Is there a way I can get gedit to just compile my program using the gcc compiler? and run it?

use the terminal plugin for gedit, make sure build-essentials is installed, compile c with ```
gcc filename.c -o the_program_name_you_want
```

c++ would be the same but with g++ instead of gcc and a .cpp file...
> 
Also this scripting?  Where can I learn it?

what type of scripting...bash?

---

### Post by Arukas on 2008-11-02
What terminal plugin?  Do you mean the external tool plug in that open terminal here? or is there another one that open the terminal in gedit?

---

### Post by jimi_hendrix on 2008-11-02
since im not on an ubuntu computer i cant tell you exactly...but look at the plugins for gedit...there should be an embeded terminal one that is like an extra shell stuck at the bottom of gedit (but you need botom panals enabled in options somewhere too)

and after you compile the program run it with ./the name you put after -o

---

### Post by Arukas on 2008-11-02
As far as what type of scripting, I don't know the name of it, but whatever scripting that you can do in the external tool plugin.  It seems like it would come in handy.  

Just to make sure we are on the same page.  I have been writing my programs in gedit and then compiling them in the terminal. (and they work too!)  I'm trying to do as much from one window as possible to keep things simple.  At least until I figure out how to make the IDE do what I want them too.  (after look at IDEs, I see why lots of people use gedit)

---

### Post by jimi_hendrix on 2008-11-02
the embeded terminal plugin will let you do this all from one window...imagine a 4 line terminal stuck on the bottom of your gedit window

---

### Post by Arukas on 2008-11-02
I found it, I was thinking it was an external tool.  I downloaded more plugins and got the terminal one.  So that is a big help.  Thanks

---

