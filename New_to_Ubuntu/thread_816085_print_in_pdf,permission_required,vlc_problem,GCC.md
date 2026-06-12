---
title: "print in pdf,permission required,vlc problem,GCC"
date: 2008-06-02
forum: New to Ubuntu
---

### Post by phanipalagummi on 2008-06-02
1.I m using ubuntu 7.10,how do i print a page(i.e from web) in pdf.I dont know where all the printed files go after i select to print in file(tool bar)

2. How should i get permission for pasting a source file from desktop to
/usr/local/src... or to any folder in file system.
when tried to do that using >cp filename path
i m getting these error cp: cannot stat `adobeflashplayer.tar.gz': No such file or directory

3.when i play any movie in vlc i m just getting sounds but no video.Is there any good player than vlc(i m really getting mad).

4.Can any one please provide me material for GCC.

---

### Post by spiderbatdad on 2008-06-02
You can run gksu nautilus for graphical admin file permissions, or use sudo before the cp command: sudo cp [option] [old location] [new location]

Check out medibuntu for playing dvd movies.

Don't understand #4. Not sure what the problem is on #1.

---

### Post by phanipalagummi on 2008-06-02
when some one said me to use sudo dpkg -r package-name for un installing i written this
.please give your suggestion 

i dont know the package name 
because i downloaded .tar.gz file and installed using running in terminal
and i later renamed the .tar.gz file

---

### Post by phanipalagummi on 2008-06-02
GCC gnu compiler collection ,i need material to see commands in compiling 
the c,c++ etc languages

---

### Post by pedro_orange on 2008-06-02
You can use the ls command to list a directories contents if you're unsure of names.
You can also use tab to finish off half typed words/filenames/dirs etc.

Do you mean the compiler GCC?

```
sudo apt-get install build-essential
```

For the DVDs...have you installed the codecs?

```
sudo apt-get install ubuntu-restricted-extras
```

Contains all the codecs and frills most computer users need. This will also install flash player for you.

To compile a simple hello world app, I make a file called hello.c and save it in Documents.
I then change directory (cd) to Documents.
Then do something along the lines of (for a C++ app):

```
g++ hello.c -o hello.o
```
Then to run it I go:
```
./hello.o
```

Magic 'eh

---

