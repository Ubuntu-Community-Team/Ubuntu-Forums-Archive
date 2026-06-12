---
title: "Trying to use ./configure"
date: 2019-11-13
forum: New to Ubuntu
---

### Post by alex-bingham on 2019-11-13
Guys & Gals

Being a numpty as I am trying to compile a download using the ./configure, make, sudo make install method but when I type ./configure in the directory where the download is located, it gives me:

bash: ./configure: No such file or directory


Now I know I am being a numpty but can someone explain what I am doing wrong?

Many thanks

AB

---

### Post by Holger_Gehrke on 2019-11-13
'./configure' means 'execute the program named 'configure' that can be found in the current working directory. Either there is no configure script included with the program or you're not in the right directory. In the latter case judicious application of the 'cd'-command will get you where you want to be.

Holger

---

### Post by CatKiller on 2019-11-13
Holger explained the issue and the solution well.

However, from a wider perspective, since this is the *New to Ubuntu* section: you don't.

Ex-Windows users are used to going to a website, downloading some random thing, and then running it. Ubuntu (and Linux generally) is not like that. That is what your package manager is for. The files that software developers put on their websites are for **other software developers**, so that they can help out. Not for end users. If you're a software developer helping out, you don't need a lot of help compiling software, because it's something that you already know how to do.

Whatever the software is that you're trying to install, it's almost certainly already in the repositories, or perhaps a PPA if it's particularly new or particularly niche. Downloading random stuff off random websites is not the way to do it.

---

### Post by yancek on 2019-11-13
Specific information might help someone to help you.  What exactly did you download (link to the site, name of the software) and what form does it take?  If it's a tar file, you need to extract it first and if you have done that it should show all the files in the directory and you should see a configure file.  Does the site give install instructions?

---

### Post by SeijiSensei on 2019-11-13
You may also encounter missing "dependencies" if you're compiling from source. A program may rely on a number of other libraries and need to include code to link to those libraries. Apt has a wonderful utility that can help resolve this problem for programs that also exist in the Ubuntu repositories. 

```
sudo apt-get build-dep packagename
```

will identify the needed dependencies and download them.  Some programs like media players have dozens of dependencies. mpv is a good example. Running

```
sudo apt-get build-dep mpv
```

brings up a list of some 150 additional needed packages on my 19.10 system.

You'll also need the gcc compiler and other utilities. If you have not yet done so, run the command

```
sudo apt install build-essential
```

to add these to your system.

---

