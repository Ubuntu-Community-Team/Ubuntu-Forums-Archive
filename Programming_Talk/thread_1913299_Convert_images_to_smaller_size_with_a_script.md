---
title: "Convert images to smaller size with a script"
date: 2012-01-22
forum: Programming Talk
---

### Post by Sigma1 on 2012-01-22
Hello,
I'm trying to put together a script for my daughter to be able to convert batches of image files, rather than doing them one by one.
Now, in the console, I use:
```
convert -quality 20% * newfile.jpg
```
or something similar, but I'd like to do a script with something like:
```
for FILE in * ; do convert -quality 20% * newfile.jpg ; done
```
Problem is, when I have, say, two images P1020298.JPG, P1020299.JPG the above command gives me not two but four reduced versions as follows:
```
~/Desktop/testfolder$ ls
P1020298.JPG  P1020299.JPG
~/Desktop/testfolder$ for FILE in * ; do convert -quality 20% * newfile.jpg ; done
~/Desktop/testfolder$ ls
newfile-0.jpg  newfile-2.jpg  P1020298.JPG
newfile-1.jpg  newfile-3.jpg  P1020299.JPG
```
There's something about "for" which appears to lead to the script doing more than I want it to. If I make the script more precise with:
```
for FILE in *.JPG ; do convert -quality 20% * newfile.jpg ; done
```
Then I get what I want: one copy of each, only, but I'm not quite sure why, and the solution is not that satisfying, since it limits me to one, named, filetype.
If anyone can help me understand what's going on, I'd appreciate it! Thanks.

---

### Post by coldraven on 2012-01-22
I just use Phatch, it's in the Software Centre.

---

### Post by Sigma1 on 2012-01-22
Thanks for your quick answer. I've given Phatch a look and it certainly looks an attractive and easy to use option: I'll recommend my daughter uses that, for simplicity's sake. Nonetheless, I would still like to be able to understand what was wrong in my script!

---

### Post by ajgreeny on 2012-01-22
There is also a plugin for nautilus, if that's what you're using for doing that, nautilus-image-converter.  Just select, then right click on all the images you want to convert, and choose resize (or rotate) and you will get a dialog box like the attachment.

Dead easy and very quick.

---

### Post by dargaud on 2012-01-22
You shouldn't use the * within the loop, but the FILE variable you defined as loop index. Also watch for spaces in filenames (add quotes). Also you need a different destination filename for each source file. Here:
```
mkdir -p Small; for FILE in * ; do convert -quality 20% "$FILE" "Small/$FILE"; done
```

---

### Post by Sigma1 on 2012-01-22
Thanks to ajgreeny for the Nautilus script: I didn't know about that and it certainly looks worth investigating. Thanks too to dargaud, for helping me out with the $FILE variable: that, apparently, was the sticky bit.
(I didn't realise it would be so complicated, once I'd got the script there, to make a clickable launcher for it, in 11.10... I got there in the end, however!)

For what it's worth, here's what the script looks like:
```
#!/bin/bash
cd ~/Desktop/testfolder;
# change to the folder you've put your photos in
mkdir -p Small;
# make a subfolder called "Small" to hold the reduced versions
for FILE in * ;
do convert -quality 20% "$FILE" "Small/$FILE";
# for all files in current folder, run the convert command with the options and write to the subfolder with the same filename; put reduced-$FILE etc if you want to change the filename to avoid possible confusion
# you could add another line, rm * if you want the original, larger files, removed after reduction
done
```
Then I created a launcher in the "Other" category with alacarte pointing to the script in question, i.e. "sh myscript.sh" in the Command box (I'm using GNOME 3). The filepath above, after cd, has to be absolute.

---

