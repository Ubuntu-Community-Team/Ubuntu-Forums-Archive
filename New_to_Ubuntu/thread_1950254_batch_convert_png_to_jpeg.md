---
title: "batch convert png to jpeg"
date: 2012-03-31
forum: New to Ubuntu
---

### Post by gandalf3 on 2012-03-31
I'm new to linux of all types, and installed ubuntu 11.10 
I'm not very familiar with the terminal, and I want to convert a large number of png format pictures to jpeg. i tried Phatch, but it wanted to know extra stuff about image quality and things.. all i want to do is convert them.
does any one know how to do a batch "convert" command? i can do them separately, but thats no good with about 100 pictures..

---

### Post by gandalf3 on 2012-03-31
never mind.. i got it :redface:
if anyone wants to know, i did an ls of all the files i wanted to convert, pasted all the file names in gedit, did a find and replace to replace all the spaces with \n (copy and paste, don't type, a space from gedit into the "find" box.. took me half an hour to figure that out..) then I copied the whole thing into a new document and replaced "png" with "jpg"
then to get it to paste back into gedit right i had to use librecalc and put everything from both files into columns, then paste everything back into gedit and finally replace tabs with spaces.
now every file name looked like "convert IMG_blahblah.png IMG_blahblah.jpg"
(no quotes) then typed the directory of the saved .txt file in the terminal and it worked easy!:-) hope this helps.. (i don't know if that was very clear)

---

### Post by idoitprone on 2012-04-01
> **gandalf3 said:**
> never mind.. i got it :redface:
if anyone wants to know, i did an ls of all the files i wanted to convert, pasted all the file names in gedit, did a find and replace to replace all the spaces with \n (copy and paste, don't type, a space from gedit into the "find" box.. took me half an hour to figure that out..) then I copied the whole thing into a new document and replaced "png" with "jpg"
then to get it to paste back into gedit right i had to use librecalc and put everything from both files into columns, then paste everything back into gedit and finally replace tabs with spaces.
now every file name looked like "convert IMG_blahblah.png IMG_blahblah.jpg"
(no quotes) then typed the directory of the saved .txt file in the terminal and it worked easy!:-) hope this helps.. (i don't know if that was very clear)

woah, wat you did there is difficult and long. were linux geeks, we like simple and fast ways

Altough, you may be gone...there is an easier solution

```
#!/bin/bash
for img in *.png
 do 
  convert "$img" "$img.jpg"
 done

```save this in a script and run it. and it should convert all your png files to jpg

---

### Post by HiImTye on 2012-04-01
```
sudo apt-get install imagemagick
convert *.png *.jpg
```
done

---

### Post by kevdog on 2012-04-01
Good script but you might need to tweak the script if you want to set quality level.

---

### Post by gandalf3 on 2012-04-01
> sudo apt-get install imagemagick convert *.png *.jpg
hmm I tried that.. my CPU and RAM hit the roof (I happened to have system monitor open) and I didn't see any jpgs appearing in the file manager, so decided to kill it before anything really bad happened.. no idea what went wrong.. maybe i mistyped it? :/

---

### Post by idoitprone on 2012-04-01
> **gandalf3 said:**
> hmm I tried that.. my CPU and RAM hit the roof (I happened to have system monitor open) and I didn't see any jpgs appearing in the file manager, so decided to kill it before anything really bad happened.. no idea what went wrong.. maybe i mistyped it? :/

they are two commands

srry, I do not understand enough about the inner details star of bash to say what happened.

my method should work

[http://ubuntuforums.org/showthread.php?t=1617470](http://ubuntuforums.org/showthread.php?t=1617470)

here another link than show another method

```
mogrify -format jpg *.png
```

---

### Post by gandalf3 on 2012-04-01
if your talking about ```
sudo apt-get install imagemagik
``` and ```
convert *.png *.jpg
``` being to different commands, i got that right.. at least, i installed imagemagik, then did convert.. oh well.. 

as a matter of fact, i read that thread earlier and thats when i tried convert, but i didn't try mogrify because i wanted to keep the pngs.

---

