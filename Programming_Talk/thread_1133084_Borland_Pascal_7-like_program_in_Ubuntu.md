---
title: "Borland Pascal 7-like program in Ubuntu?"
date: 2009-04-22
forum: Programming Talk
---

### Post by rickyroger0907 on 2009-04-22
Hi, I've just used Ubuntu for a couple weeks now. And I've read some posts about programming software in Ubuntu. They mention Lazarus, Dosbox, etc. I just wonder is there software for beginner programmer (stuff like just start-declare variables-do sth like if, while, for, array, etc -stop), but probably it's too basic though. Anyway, BPascal is a nice software to practice. I have fpc-source installed, but I don't think it does any good, does it? It needs some other packages to work with right? So should I lazarus-ide (+lazarus-src) or what? Also, I'll be learning C,C# and C++. Is there any packages for practicing those languages? 
And last, for all the packages mentioned above, how can i start the software, the program? does it appear under Applications-Programming? or i have to access to it via terminal?
Thanks for any reply

---

### Post by cmay on 2009-04-22
read the stickies first on these subjects as most answers is there.
just in case you miss it then in order to use c/c++ you have to sudo apt-get instal build-essential 

as for the fpc compiler you need to sudo apt get install fp-ide and this will drag along the runtime and compiler and all you need to use free pascal from the commanline. 

the src package is just the sources and wont do any good if you just want to compile somthing .

the homepage is a good place to lok for tutorials. [http://www.freepascal.org/](http://www.freepascal.org/)

---

### Post by rickyroger0907 on 2009-04-23
I'll try to give it a shot and let you know later, appreciate it.

---

### Post by Kilon on 2009-04-23
> **rickyroger0907 said:**
> I'll try to give it a shot and let you know later, appreciate it.

lazarus will make your life easier. It is a good idea to use it.

---

### Post by rickyroger0907 on 2009-04-23
What do i need for Lazarus? -ide, -src and -doc? After I install, how can i get it to work? thanks

---

### Post by Kilon on 2009-04-23
> **rickyroger0907 said:**
> What do i need for Lazarus? -ide, -src and -doc? After I install, how can i get it to work? thanks

lazarus can be found here

[http://www.lazarus.freepascal.org/](http://www.lazarus.freepascal.org/)

it also need freepascal in order to work which can be found here 

[http://www.freepascal.org/](http://www.freepascal.org/)

they are both free, very much cross platform and almost entirely compatible with delphi. 

have fun!

---

### Post by rickyroger0907 on 2009-04-24
I have a little problem, it says: "Free Pascal Sources not found"
"Some code functions will not work ..."
Is it the fpc-src? or something else?

---

### Post by rickyroger0907 on 2009-04-24
I've got it fixed. I read it carefully and got it fixed, lol. Thanks for yo' help. I'll try it. Again, appreciate it guys

---

### Post by Kilon on 2009-04-24
> **rickyroger0907 said:**
> I've got it fixed. I read it carefully and got it fixed, lol. Thanks for yo' help. I'll try it. Again, appreciate it guys

Glad to be of help. Have fun.

---

### Post by lisati on 2009-04-24
If you don't mind command-line stuff, the Free Pascal compiler can be installed with the following: ```
sudo apt-get install fp-compiler
```
You'll need to get a suitable editor or IDE, something like gedit or nano will be fine for occasional use. 
Information on the command to compile a PASCAL file can be browsed by entering the following at the CLI prompt:
```
man fpc
```

---

### Post by Kilon on 2009-04-24
> If you don't mind command-line stuff, the Free Pascal compiler can be installed with the following: ```
sudo apt-get install fp-compiler
```

bash commands are all good and nice , but the synaptic might not donwload the latest version . That is why I advice download from the website itself.
 
> You'll need to get a suitable editor or IDE, something like gedit or nano will be fine for occasional use. 



Lazarus is the IDE for freepascal and if it is the clone of DELPHI as it claims to be , then it is probably the most amazing free open source ide out there. 

[IMG]http://wiki.lazarus.freepascal.org/images/c/c3/Lazarus_IDE_GTK2.png[/IMG]

Ahhh if python had only a similar IDE. Python ides do suck.

---

