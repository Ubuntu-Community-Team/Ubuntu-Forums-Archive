---
title: "Tip: For those looking to have specific [alt + code] (from windows) working on Ubuntu"
date: 2009-07-26
forum: Outdated Tutorials &amp; Tips
---

### Post by justldd on 2009-07-26
Step 1:
 Just follow the following tutorial and instead of choosing 'right win', choose 'right alt' for the [compose key]
 [http://www.ubuntugeek.com/special-characters-made-easier-in-ubuntu.html](http://www.ubuntugeek.com/special-characters-made-easier-in-ubuntu.html)
 

 Also, do follow 'solution2', but ignore the part where it says:
> Now you need to copy this file to your home directory
 cp /usr/share/X11/locale/en_US.UTF-8/Compose ~/.XCompose
 This will give you a more complete character set.For example that your keyboard doesn’t have a tilde (~). You can change the lines that require entering a tilde so that a simple “t” (or whatever you like) will work. Just don’t use a key combination that’s already in use.
 One thing that I noticed is that there are already [compose key] [number]  codes in  
 /usr/share/X11/locale/en_US.UTF-8/Compose
 so you can't still have the [alt + code] promised.
 

 So... let's just backup that file, and modify it (i.e: delete EVERY code)
```
sudo cp /usr/share/X11/locale/en_US.UTF-8/Compose /usr/share/X11/locale/en_US.UTF-8/ComposeBup
sudo gedit /usr/share/X11/locale/en_US.UTF-8/Compose

``` There, delete everything except for the first ~4lines (or the comment section that appears before the first “<” character)
 

 Mine looks like this:  
```
# UTF-8 (Unicode) compose sequence 
 # David.Monniaux@ens.fr 
 # 
 # $XFree86: xc/nls/Compose/en_US.UTF-8,v 1.11 2004/01/06 13:14:04 pascal Exp $  
 
```Close the file.  
 Go to character map (applications>Accesories>Character Map) and find the character(s) you need. For instance, let's suppose we want to have a code for "ñ".
 I looked for that character and found it. On the lower part of the screen, there is a TEXT IN CAPS. Read it. It will start with something like “U+XXXX” In the case of  "ñ", it is U+00F1. Write down that code.
 

 Now, create a file named .Xcompose in your home folder:
 gedit  ~/.XCompose
 

 Here is where you will need to write the new codes.
Write the line
```
include "%L"
 
```Then, add a line for each code to be added (here is an example, read the explanation that comes just after it)
```
<Multi_key> <1> <6><4>                  : "ñ"   U00F1 # LATIN SMALL LETTER N WITH TILDE
 <Multi_key> <KP_1> <KP_6><KP_4>                  : "ñ"   U00F1 # LATIN SMALL LETTER N WITH TILDE
 
```As you probably have guessed by now, the <1><6><4> is the number code used in windows, which you have to know/look up or remember. Remember the U+00F1? Just delete the “+” and put it the code there(replace the example's U00F1 by the code you need).
 Create as many code as you need, always following the pattern
 <Multi_key><1><x><x>     : “x” UXXXX
 

 Save, exit, log out and there you go!
 =)
 

 Oh, and by the way, KP_1 means “1”, just  from the numerical pad ( I think)

---

