---
title: "New to Ubuntu, need to do programming"
date: 2008-11-29
forum: New to Ubuntu
---

### Post by Rugger4Ever on 2008-11-29
Hey. I had to switch over from Windows rather suddenly and I have a project to do that I used to do in Visual Basic C#. Now I have no idea what to do. Most everything on Ubuntu runs just fine and I've figured out most of what I need. This however I have no clue what to do. I downloaded some stuff for Mono but I can't seem to find it or run it. I'm a noob and need some fairly watered down simple guidance if someone could help me out I'd be really grateful, otherwise my odds of passing this college course are slim to none. Thanks!

---

### Post by mikewhatever on 2008-11-29
I suggest reposting the question in the [Programming Talk Section]("http://ubuntuforums.org/showthread.php?t=996863"). Might get faster and more practical responses.

---

### Post by linux_tech on 2008-11-29
Applications>Accessories>Terminal
The first step is to uncompress the files-

```
tar xvfz nameoffile.tar.gz
```

or another way to do this-

when you download the file, in the downloads window, double-click on the file. (This will bring up another window), then click the extract button to extract, (this will bring up another window) to browse to where you would like to extract then to. For this example select Desktop and click extract.

The 2nd step is to compile-
For this enter the terminal Application>Accessories>Terminal

```
cd Desktop
```

```
cd nameoffolder
```

(that was extracted to desktop) there will usually be a readme.txt in it that give the install instructions

then from inside the folder type (3 seperate commands)

```
./configure
```

```
make
```

```
sudo make install
```

```
https://help.ubuntu.com/community/CompilingEasyHowTo
```

---

### Post by directhex on 2008-11-29
"monodevelop" is the package containing the most popular IDE for C# development. Install the "mono-2.0-devel" package for the compiler itself.

It'll appear in the Applications/Programming menu.

---

