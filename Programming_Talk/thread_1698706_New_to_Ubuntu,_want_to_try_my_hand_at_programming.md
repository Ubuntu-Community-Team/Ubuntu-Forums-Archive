---
title: "New to Ubuntu, want to try my hand at programming"
date: 2011-03-02
forum: Programming Talk
---

### Post by bfmetcalf on 2011-03-02
So I am new to Linux based systems (other than android, but I don't totally count that as Linux) and would like to try my hand at programing something simple.  A thought I had was this:
 
I use easytether a lot to connect to the internet, it gets a little old typing in the terminal commands everytime I get disconnected.  Is there a way to write a simple program that I can click on from the desk top and have it run the terminal commands needed?  
 
Just a thought.  If anybody has any insight it would be appreciated.

---

### Post by cgroza on 2011-03-02
How about a bash script?

```
#/bin/bash

Your commands here
```

---

### Post by bfmetcalf on 2011-03-02
Ok, I guess I'm newer than I thought, Can you elaborate a bit.  Is this something I will type into terminal or use a programing software?  I have seen the bash deal on here before, but I guess I never saw exactly what it was.  If you know of any guides on this it would be helpful as well.

---

### Post by Shpongle on 2011-03-02
bash is basically programming logic and flow control combined with terminal commands if I was to give a very basic definition.

you can put all your commands you have to type into a bash script and execute that all the time instead. 



see here 
[http://www.freeos.com/guides/lsst/ch02sec01.html](http://www.freeos.com/guides/lsst/ch02sec01.html)

---

### Post by dodle on 2011-03-02
Here is an example of a file that would launch a web browser: Create an empty text file on the desktop and name it whatever you want. Open it with a text editor and put in the following:

[php]#! /bin/bash

firefox[/php]

Now close it. Right-click on the file and go to "Properties". Under the permissions tab check the box that says something like "Make file executable".

Now every time that you double-click that file it will launch Firefox web browser.

---

### Post by bfmetcalf on 2011-03-03
Wow, That actually sounds pretty easy.  I will try that tonight.  Anybody do any basic apps that were a fun learning experience that they could share to give me some more ideas?

---

