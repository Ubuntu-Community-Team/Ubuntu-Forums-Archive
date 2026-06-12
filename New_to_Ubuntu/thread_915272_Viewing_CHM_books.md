---
title: "Viewing CHM books"
date: 2008-09-09
forum: New to Ubuntu
---

### Post by TadeoDiaz on 2008-09-09
Anyone know how to be able to see CHM book files in Ubuntu (Hardy). I tried the CHM viewer but it didn't work

---

### Post by whitethorn on 2008-09-09
Hi, do you have xchm installed ?

```
sudo apt-get update && sudo apt-get install xchm
```

It's not exactly pretty, there's also another program for KDE which is supposed to look better

```
sudo apt-get install kchmviewer
```

---

### Post by TadeoDiaz on 2008-09-09
I tried it but whenever I open a CHM file in the program it comes up blank. I tried it with several CHM files and I get the same results

---

### Post by whitethorn on 2008-09-10
Have you tried starting it from the terminal?

```
xchm /path/to/the/file.chm
```

What does it give you back?

---

### Post by acidsolution on 2008-09-10
use gnochm

```
 sudo apt-get install gnochm 
```

this might help u

---

### Post by TadeoDiaz on 2008-09-10
> **whitethorn said:**
> Have you tried starting it from the terminal?

```
xchm /path/to/the/file.chm
```

What does it give you back?

When I try this it comes up blank again and gives me this in terminal:

```

** (xchm:22789): WARNING **: Can't create printer "PDF" because the id "PDF" is already used

(xchm:22789): GnomePrintCupsPlugin-WARNING **: The CUPS printer PDF could not be created


(xchm:22789): GnomePrintCupsPlugin-WARNING **: The data for the CUPS printer PDF could not be loaded.
```
> **acidsolution said:**
> use gnochm

```
 sudo apt-get install gnochm 
```

this might help u

I tried it for both the files I have and it gave me a blank. It says at the bottom that it has "opened" a URL but nothing is showing. I tried clicking on the home link on the left but nothing comes up

---

### Post by whitethorn on 2008-09-11
That's wierd. You got the same output that I get, with the printers and stuff. Have you tried the files in windows or on another computer?  Are you sure they work?

Go to this webpage and download a chm file.  And try opening it.  

[http://www.php.net/download-docs.php](http://www.php.net/download-docs.php)

Can you read it?

---

### Post by t0p on 2008-09-11
Have you tried **evince**?  I think I've viewed chm files with it.

---

### Post by TadeoDiaz on 2008-09-11
> **whitethorn said:**
> That's wierd. You got the same output that I get, with the printers and stuff. Have you tried the files in windows or on another computer?  Are you sure they work?

Go to this webpage and download a chm file.  And try opening it.  

[http://www.php.net/download-docs.php](http://www.php.net/download-docs.php)

Can you read it?

I checked the files on a PC and it opens up just fine. I downloaded a file from that link and it opens just fine in xCHM and CHMviewer

---

### Post by TadeoDiaz on 2008-09-11
> **t0p said:**
> Have you tried **evince**?  I think I've viewed chm files with it.

Is it already included as the document viewer on Hardy?

---

### Post by whitethorn on 2008-09-13
Yes evince is installed.  You could just try running evince from the terminal, good way to check if it's installed.  I tried it out and it didn't open any .chm for me.  I have no idea why those .chm files work on a different PC and not on the other (right?), but xchm does open other .chm files.  I have no idea why it's not working. Maybe someone else does.

---

### Post by TadeoDiaz on 2008-09-13
The PC opens the CHM files just fine but xCHM can't open them. I ended up converting the CHM files to HTML and just viewing them on firefox but it's still kind of a pain (lots and lots of files)

---

### Post by namaku0 on 2008-09-13
archmage, chmsee, gnochm, kchmviewer, xchm...

..or you can use this Firefox plugin like me:
[https://addons.mozilla.org/en-US/firefox/addon/3235](https://addons.mozilla.org/en-US/firefox/addon/3235)

---

### Post by Kellemora on 2008-09-13
Hi TD

This may or may not help at all, but it's worth giving it a try anyhow.

I've had several files that would appear BLANK, even if I was in Root Terminal, IF I didn't do this first.

After opening Root Terminal and logging in if need be.
Type cd .. then hit enter, type cd .. again then hit enter, then do an 'ls' to make sure are finally in the root.  

Then try to read the file you want to read, however you read it.

For some reason, on my computer, I can't look at most configuration files unless I do this first, else the pages just come up as blank pages.

I'm a NOOB, so don't know why yet, just know I have to back up using cd .. twice before it will work.

TTUL
Gary

---

### Post by TadeoDiaz on 2008-10-19
Sorry for not responding earlier fellas

Initially I had converted the chm files to html but it was just a pain to work with (a lot of the links don't work properly and if you want to look at a picture you have to hunt for it)

The firefox extension works initially but upon clicking on any link to change pages it changes to an error message or some weird code line

I tried both gchm and xchm and they did not work, I just installed chmsee and it seems to be working just fine (only reasonably slow to open the file and I get a message that It cannot find a file in the .chmsee library but it does eventually open the file)

kchmviewer works a hell of a lot faster with both files, even though the visual integration isn't as great with the current theme I am running (anyone know how to change the theme for it? :) ) 

Thanks for all your help fellas!

---

