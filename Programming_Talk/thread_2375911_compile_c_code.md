---
title: "compile c code"
date: 2017-10-28
forum: Programming Talk
---

### Post by mikekush on 2017-10-28
hi
i have some knowledge in hardware  if someone have trouble maybe i can help
but in software  totally noob  thats why i am here , to ask for some guidance. 
 
i want to compile some code. 
i have the code on pdf but no idea whow to do-it. 
its c
obviously i  have been on Internet searching for help but no luck
since Ubuntu have an great community i tink thats an great  start

---

### Post by spjackson on 2017-10-28
Welcome to the forums.

1. Install the compiler and associated tools with
```

sudo apt-get install build-essential

```
2. Put the source code in a text file e.g. example.c. You can use any text editor to do this.
3. Compile and link with:
```

make example

```
4. Run the program
```

./example

```
See also this 'getting started' page [https://ubuntuforums.org/showthread.php?t=333867](https://ubuntuforums.org/showthread.php?t=333867)

---

### Post by Impavidus on 2017-10-28
Source code in a pdf file isn't very useful. Get your source code saved as a plain text file, like you make in text editors as gedit, mousepad or vim.

Install a compiler (gcc is the standard on Ubuntu, the **gcc** package will install the default version of gcc for your version of Ubuntu), some header files and you probably want **make** too. The package **build-essential** is a easy package that installs aforementioned packages automatically (although it wasn't really meant for that and includes some stuff that you don't need), but depending on what exactly you want to compile you may have to install additional header files. Those can be found in packages typically named **libfoo-dev**.

If you use make, you may have to write a makefile first, containing instructions how to run gcc. You can also run gcc directly from the terminal. You may need some command line options to set output file name, link libraries etc.

---

### Post by mikekush on 2017-10-28
tanks  i ill try later .

---

### Post by oldos2er on 2017-10-28
Thread moved to *Programming Talk*

---

### Post by mikekush on 2017-10-30
hi after some trial and error and a lot of Google  i tink that im closer. 
but
 fatal error: sndfile.h: No such file or directory
 #include <sndfile.h>

need to install repository?
how i do that?
appreciated

---

### Post by lisati on 2017-10-30
Some context might be useful. Are you trying to process sound files using the [libsndfile API]("http://www.mega-nerd.com/libsndfile/api.html") by any chance?

---

### Post by spjackson on 2017-10-31
Does the program you are trying to build come with any documentation? There may be other dependencies besides libsndfile. Nevertheless, I'll fly blind and suggest a possible solution to this immediate problem:

1. Install the dependency
```

sudo apt-get install libsndfile1-dev

```
2. Use it
```

gcc -o example example.c -llibsndfile

```

---

