---
title: "Gcc"
date: 2008-05-08
forum: New to Ubuntu
---

### Post by Aarookie on 2008-05-08
I am relatively new to ubuntu, I worked with mandrake years ago for a short amount of time.  I installed the gcc package to fiddle around, very limited experience with coding and just wanted to play around and learn and such.  Gcc appears to be installed, but I have absolutely no idea how to start it.

It's not on any menus in applications or others, I found it in the /usr/lib/gcc directory but.. well... I'm just confused.  Do you type your code into like a regular text editor or do you load up some kind of program included with it to input/compile your code?

Thanks in advance.

---

### Post by quelx on 2008-05-08
You edit it in any text editor, then I -think- what you do is ```
gcc <filename>
```

this creates an a.out binary file which you can execute by running ```
./a.out
``` in a terminal window

---

### Post by glennric on 2008-05-08
Yes, you type your code and save it in a text file.  Then you compile it with gcc assuming the code you are using is C.  gcc is a command line tool.  It doesn't have a gui.  You could install an IDE to edit your code and it will do the compiling in the background for you.  I am sure someone will recommend one for you.

---

### Post by Monicker on 2008-05-08
gcc by itself is just a compiler, with no graphical interface.  Kdevelop is one IDE that you can use.  There are others, but that is the only one which comes to mind at the moment.  You can still use a text editor, and then compile it from gcc at the command line.


```

gcc -o foo foo.c
```


I know it gets a lot more complex than that, but when it comes to C/C++ I have mainly just glanced through the code of others.


*EDIT:  I'm late again!  :P*

---

### Post by Aarookie on 2008-05-08
I'll give it a try thank you all for your lightning fast answers.  I'm new like I said but I think I'm really gonna dig ubuntu and linux after I get going.  Expect a lot more head scratching from my direction though /gulp.:)[http://ubuntuforums.org/images/smilies/icon_smile.gif](http://ubuntuforums.org/images/smilies/icon_smile.gif)

---

### Post by Joeb454 on 2008-05-08
Usually when I use gcc I end up running something along the lines of ```
gcc prog1.c -o myprogram
``` Then I would run it with ```
./myprogram
```

You need to do this from a terminal by the way (Applications > Accessories > Terminal). And just to finish off - make sure you have the *build-essential* package installed. From that same terminal you can run ```
sudo aptitude install build-essential
```

---

