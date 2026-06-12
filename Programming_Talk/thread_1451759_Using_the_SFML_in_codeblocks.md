---
title: "Using the SFML in codeblocks"
date: 2010-04-10
forum: Programming Talk
---

### Post by DiegoTc on 2010-04-10
Hi 
I am playing around with the SFML library.
I could compile and run a program writing the code in gedit and compiling it on the terminal.
I used this guide for doing this -> [http://www.sfml-dev.org/tutorials/1.6/start-linux.php](http://www.sfml-dev.org/tutorials/1.6/start-linux.php)

There is a guide for using codeblocks in windows. So I used it but edit some parts -> [http://www.sfml-dev.org/tutorials/1.6/start-cb.php](http://www.sfml-dev.org/tutorials/1.6/start-cb.php)

The first part where I have to add in the Search Directory Compiler I add this
> 
"/usr/include/SFML"

[http://img233.imageshack.us/img233/1333/pantallazoge.png](http://img233.imageshack.us/img233/1333/pantallazoge.png)
Thats the picture

And in Search Directories Linker I add this
> 
/usr/lib

Here is the picture -> [http://img233.yfrog.com/img233/8660/pantallazo7.png](http://img233.yfrog.com/img233/8660/pantallazo7.png)

And I have this error when I try to compile
[http://img297.imageshack.us/img297/3918/pantallazo1x.png](http://img297.imageshack.us/img297/3918/pantallazo1x.png)

---

### Post by yabbadabbadont on 2010-04-11
Since you are specifying /usr/include/SFML, do you need to use <SFML/...> in your include?  What happens if you just set /usr/include as an include directory option instead of /usr/include/SFML?

---

### Post by Compyx on 2010-04-11
Did you set the linker flags? The linker complains because it can't find the libraries it needs. According to the website, you might need these: -lsfml-graphics -lsfml-window -lsfml-system.

---

### Post by DiegoTc on 2010-04-11
Thanks problem solved :D:lolflag:

---

### Post by Compyx on 2010-04-11
I see you posted your findings on Planet Ubuntu. ;)

---

