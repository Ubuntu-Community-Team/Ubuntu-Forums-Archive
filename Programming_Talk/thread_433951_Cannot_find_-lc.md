---
title: "Cannot find -lc"
date: 2007-05-05
forum: Programming Talk
---

### Post by gm__ on 2007-05-05
Hello!

I'm trying to learn some assembly and in the book where i learn it from it uses the "C++ printf " function 
to print the program on the terminal using this command to link it:
ld -dynamic-linker /lib/ld-linux.so.2 -lc -o myprog myprog.o

When i execute this command i get this "cannot find -lc" error message.
I tried to google it but apparently nobody had this problem yet.

Thanks for any help!

---

### Post by bashologist on 2007-05-05
It looks to me like it's looking for "-lc" as a filename. Try changing the order of your parameters/options.

---

### Post by gm__ on 2007-05-05
Thanks for the suggestion ,what youre saying sounds logical, cause it isnt complaining after an operand
or such its true.
I tried to put -lc anywhere else but no joy...

---

### Post by hod139 on 2007-05-05
What if you use gcc to do the linking instead of ld
```

gcc  -dynamic-linker /lib/ld-linux.so.2 -lc -o myprog myprog.o

```

---

### Post by gm__ on 2007-05-05
No go either.Thanks though.

He says it actually in the book that i can use gcc instead ld like this: gcc -o myprog myprog.s
provided that i change "_start" to "main" which i did but it didnt work either...

---

### Post by hod139 on 2007-05-05
Silly question, but you have installed the package build-essential right?

---

### Post by gm__ on 2007-05-06
Well its good that you say that cause i did install a few "gcc" stuff but apparently something's
missing, cause when i try to compile a simple "Hello world!" program i get :
stdio.h: no such file or directrory.

So i should find out what i need exactly to compile with "c".

---

### Post by lloyd_b on 2007-05-06
> Well its good that you say that cause i did install a few "gcc" stuff but apparently something's
missing, cause when i try to compile a simple "Hello world!" program i get :
stdio.h: no such file or directrory.

Install the package "build-essential"
```
sudo apt-get install build-essential
```
in a terminal window, or use Synaptic/Adept if you're more comfortable with a GUI.

This should clear up that particular problem, and may (or may not) help with your assembly code problem.

Lloyd B.

---

### Post by gm__ on 2007-05-06
Cool :)  That was it! the build-essential and now everything works fine.

I didnt know the build-essential was something to do with programming , now i know ,
and i thought i already installed it. It goes to show that the most of the time its just a stupid mistake you made.  
Plus i upgraded to Feisty last night, that went well too.
I did it  online cause from the CD install  i was getting an error message, its because of my laptop's hardware i guess, the earlier distros  i had to install with nolapic noapic etc. and that just didnt work with Feisty but thats another topic...

Anyway im very happy, you made my day guys :)
Thaks a lot

---

