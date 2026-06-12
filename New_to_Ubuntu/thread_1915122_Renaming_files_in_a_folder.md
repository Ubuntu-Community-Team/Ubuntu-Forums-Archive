---
title: "Renaming files in a folder"
date: 2012-01-25
forum: New to Ubuntu
---

### Post by RayArdia on 2012-01-25
I know this is a recurring subject, but it is one which I simply can't 'get my head round'!

---

### Post by Krytarik on 2012-01-25
Simply use "pyRenamer", a GUI tool for mass renaming files, it's in the official repos, and my favorite for that. :D

Regards.

---

### Post by mwd5650 on 2012-01-25
Are you trying to do this from a terminal? if so ```
mv <oldfile> <newfile>
```
 
If you are talking in the GUI then right click is your friend.
 
Matt

---

### Post by RayArdia on 2012-01-25
So Sorry, finger trouble - I meant to go on:-
I have thousands of photos which I am gradually scanning and adding to Shotwell. My problem is that the names of the scanned images are all mixed up because as I scan and then add files to a folder containing files scanned at an earlier date I am forced to rename (eg) Scanned Document -1.jpg to something else because of a clash of names. For example,in dir ~/Dec89-Jan90 I end up with this:-

ray@ray-Aspire-5735:~/Dec89-Jan90$ ls
Scanned Document-1.jpg    Scanned Documenta-15.jpg  Scanned Documenta-26.jpg
Scanned Document-2.jpg    Scanned Documenta-16.jpg  Scanned Documenta-27.jpg
Scanned Document-3.jpg    Scanned Documenta-17.jpg  Scanned Documenta-2.jpg
Scanned Document-4.jpg    Scanned Documenta-18.jpg  Scanned Documenta-3.jpg
Scanned Document-5.jpg    Scanned Documenta-19.jpg  Scanned Documenta-4.jpg
Scanned Document-6.jpg    Scanned Documenta-1.jpg   Scanned Documenta-5.jpg
Scanned Document-7.jpg    Scanned Documenta-20.jpg  Scanned Documenta-6.jpg
Scanned Documenta-10.jpg  Scanned Documenta-21.jpg  Scanned Documenta-7.jpg
Scanned Documenta-11.jpg  Scanned Documenta-22.jpg  Scanned Documenta-8.jpg
Scanned Documentain dir -12.jpg  Scanned Documenta-23.jpg  Scanned Documenta-9.jpg
Scanned Documenta-13.jpg  Scanned Documenta-24.jpg  Scanned Documenta.jpg
Scanned Documenta-14.jpg  Scanned Documenta-25.jpg  Scanned Document.jpg
ray@ray-Aspire-5735:~/Dec89-Jan90$ rename *.jpg Christmas1989.jpg
Bareword found where operator expected at (eval 1) line 1, near "1.jpg"
	(Missing operator before jpg?)
syntax error at (eval 1) line 2, near "1.jpg
"

I was trying in my dumb way to rename all the files with a sequential number eg 'Christmas1989-1.jpg, Christmas1989-2.jpg' etc.
How should I best go about this please? 
[http://ubuntuforums.org/images/smilies/confused.gif](http://ubuntuforums.org/images/smilies/confused.gif)

---

### Post by mwd5650 on 2012-01-25
pyRenamer will allow you to rename using patterns, which it looks like that's what you are trying to do.
 
You can find more info here:[http://www.infinicode.org/code/pyrenamer/](http://www.infinicode.org/code/pyrenamer/)
 
Matt

---

### Post by I2k4 on 2012-01-25
I'm pretty new to Ubuntu but agree about Pyrenamer.  The best is that if files are within a properly named folder, you can set it to simply adopt the name of the folder and attach a numerical sequence, in my own case, e.g.

Folder: 120125 - Walk in the Park
Files: 120125 - Walk in the Park 001 (etc.)

---

### Post by Miljet on 2012-01-25
The easiest way is to avoid the predicament you have is by renaming the files as you scan them. You should never end up with a lot of files named "scanned document-?.jpg". Just the fact that the filenames contain spaces is going to cause you additional headaches at some point.

---

### Post by Vaphell on 2012-01-26
try pasting this
```

name='Christmas1989'
digits=4
i=0; for f in *.jpg; do ((i++)); **echo** mv "$f" **"${name}"**-$( printf "%0**${digits}**d" $i ).jpg; done

```
in this form it prints out the mv commands with a filename-standarized name pair.
If it works you can remove echo to perform the operation (but have backup just in case)
$name defines the standarized name, $digits defines how many digits are to be used in autoindexing, depending on the total number of pictures (otherwise 10 will land after 1 not after 9 when sorted alphabetically)

example output from my junk folder (name='Pictures', digits=2):
```
mv 5960_planescape_torment-7.jpg Pictures-01.jpg
mv DarkArchon_SC1_Cncpt1.jpg Pictures-02.jpg
mv deusex_800x450.jpg Pictures-03.jpg
mv gallery-522877-500x500.jpg Pictures-04.jpg
```

---

### Post by Sigma1 on 2012-01-26
I'll note Vaphell's reply, for reference: it looks good. I hadn't found how to rename files numerically.
Here is a handy tutorial on command-line renaming which I have stored on my box and often refer to: [http://www.basicallytech.com/blog/?/archives/10-Shell-stuff-rename-multiple-files-on-the-command-line.html](http://www.basicallytech.com/blog/?/archives/10-Shell-stuff-rename-multiple-files-on-the-command-line.html) Good luck.

---

### Post by RayArdia on 2012-01-26
> **mwd5650 said:**
> pyRenamer will allow you to rename using patterns, which it looks like that's what you are trying to do.
 
You can find more info here:[http://www.infinicode.org/code/pyrenamer/](http://www.infinicode.org/code/pyrenamer/)
 
Matt

> **Krytarik said:**
> Simply use "pyRenamer", a GUI tool for mass renaming files, it's in the official repos, and my favorite for that. :D

Regards.

Many thanks for both the above.
Installed pyRenamer and am coming to terms with it. I can rename all the files to the same year from the metadata eg

Original                          Renamed to
Scanned Document-1.jpg            01Sep1962.jpg
Scanned Document-2.jpg            01Sep1962.jpg
Scanned Document.jpg              01Sep1962.jpg

What want to achieve is 01Sep1962-01.jpg,01Sep1962-2.jpg etc. Any ideas how to do this?

---

### Post by Sigma1 on 2012-01-26
I don't know about PyRenamer, but Vaphell's solution will work, won't it? You just need to change "name" to what you want, i.e.

```
name='01Sep1962'
digits=4
i=0; for f in *.jpg; do ((i++)); echo mv "$f" "${name}"-$( printf "%0${digits}d" $i ).jpg; done
```

cd into the folder containing the files, run the command with "echo" in it: this won't change anything, it'll just print what would happen, without "echo". If you're happy with the result, then remove "echo" and run it again. (Change digits to "2" if you've got less than 100 photos to rename.)

---

### Post by RayArdia on 2012-01-26
Thank you Sigma1, but have tried and failed miserably; I think my old brain hasn't got enough cells left to cope!
If anyone can help me to go a little further with pyRenamer I would be very grateful.
Ray

---

### Post by Sigma1 on 2012-01-26
OK. I'm happy to walk you through the process, if you like. If you prefer to go with pyRenamer, though, that's fine.

---

### Post by Vaphell on 2012-01-26
why bother with some magic tools when renaming the files manually requires as much brain power as figuring out how to force these magic tools to obey you?

these 3 lines are not rocket science
first two set up parameters
last one does "for each filename matching *.jpg do ( print out move filename $newname-$index.jpg )"
that's it, actual renaming requires removing print out part (echo)

you can highlight the lines here/middleclick-paste into terminal 1 by 1 (which eliminates typos and syntax errors caused by typing everything) and it should work

---

### Post by Krytarik on 2012-01-26
> **RayArdia said:**
> What want to achieve is 01Sep1962-01.jpg,01Sep1962-2.jpg etc. Any ideas how to do this?
In pyRenamer,

[LIST=1]
[*]select all files in the respective directory you want to rename,
[*]under the "Patterns" tab, set the first field, "Original...", to:
```
{X}.jpg
```
[*]and set the second field, "Renamed...", to:
```
{1}-{num}.jpg
```
[*]then choose "Preview", and if satisfied, "Rename", obviously.
[/LIST]
You get a list of possible keys and their meanings when you mouse over the respective fields.

---

### Post by RayArdia on 2012-01-26
> **Krytarik said:**
> In pyRenamer,

[LIST=1]
[*]select all files in the respective directory you want to rename,
[*]under the "Patterns" tab, set the first field, "Original...", to:
```
{X}.jpg
```
[*]and set the second field, "Renamed...", to:
```
{1}-{num}.jpg
```
[*]then choose "Preview", and if satisfied, "Rename", obviously.
[/LIST]
You get a list of possible keys and their meanings when you mouse over the respective fields.

Many thanks to Vaphel and Sigma1 for kind offers to help but I think I'd better stick to the 'system' I've had a little success with so far!

I tried Krytarik's suggestion but without success, renamed files still had the Scnned/Scanne/Scan and the original numbers but with a nice sequential number just before the .jpg.  Eg. Scanned Document -7 3.jpg etc.

Changed the 'Renamed' field to 1985 -{num}.jpg and BINGO!

Thanks again,
Ray

---

### Post by Krytarik on 2012-01-26
> **RayArdia said:**
> I tried Krytarik's suggestion but without success, renamed files still had the Scnned/Scanne/Scan and the original numbers but with a nice sequential number just before the .jpg.  Eg. Scanned Document -7 3.jpg etc.

Changed the 'Renamed' field to 1985 -{num}.jpg and BINGO!
Oh, yeah, I already forgot about the first part of your 'mission', and didn't take it into account for setting up the pattern. :P

---

