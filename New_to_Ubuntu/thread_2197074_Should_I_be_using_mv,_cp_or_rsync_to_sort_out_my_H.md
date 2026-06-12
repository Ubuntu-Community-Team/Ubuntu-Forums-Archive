---
title: "Should I be using mv, cp or rsync to sort out my /Home directory?"
date: 2014-01-02
forum: New to Ubuntu
---

### Post by RayArdia on 2014-01-02
I have  72467 recovered .jpeg files and 9 empty dirs in my /home dir.
I want to move all the .jpeg files into a newly formed dir 'recovered_jpegs' so that I can then sort them into 2 categories:-
1. Files which contain exif data, which will subsequently be moved into dir Pictures, and
2. Files with no exif data, which will need further sorting.

I have read man cp, man mv and man rsync remain baffled by all three. My apologies for being so thick but I'd appreciate a little help to make sure I use the correct commands and don't compound my problem. 
Thanks in advance.

---

### Post by tea for one on 2014-01-02
Good morning

The syntax for rsync can be baffling so I would suggest that you use Grsync (available via the Software Centre).

It is a GUI for rsync and it simplifies the process a bit.

---

### Post by RayArdia on 2014-01-02
> **tea for one said:**
> Good morning

The syntax for rsync can be baffling so I would suggest that you use Grsync (available via the Software Centre).

It is a GUI for rsync and it simplifies the process a bit.

Thank you tea for one, I'll try Grsync and see how I get on!

---

### Post by RayArdia on 2014-01-02
Grsync installed, looks to be understandable but first problem is that the files I want to transfer are all 'greyed out' so I can't select them.

---

### Post by RayArdia on 2014-01-02
Can I use Graphical Sudo to access greyed-out files?

---

### Post by ajgreeny on 2014-01-02
As far as I'm aware you can choose only folders in the browse window of grsync; you can not go right down to file level, though I am sure you can do it in rsync in terminal and it may be possible using the Advanced or Extra options tabs.
```
rsync -t Pictures/*.jpg recovered_jpegs
``` This assumes all your jpg files have the same suffix .jpg using the same letter case and are in the root of your Pictures folder.  If not you will need to use the path to the source files and then either need to rename all to .jpg or repeat the rsync for each suffix, eg JPG, jpeg, JPEG, etc etc.

I believe it may also be possible to use the **find** command to find all of the jpgs in the source folder, and then use the -exec option to rsync them to recovered_jpegs folder, but that is a bit beyond my immediate skills.

---

### Post by buzzingrobot on 2014-01-02
Are all those files on the same machine?  If so, rsync is overkill. The cp command copies and mv moves, i.e., mv removes the files from the current location and puts them in the new location.

Say the files are now in /oldfolder, and you want them in /newfolder.  A "cp -R /oldfolder /newfolder" will put all the files in /newfolder/oldfolder. Generically, "cp -R destination_folder target_folder" recurses through everything in target_folder and recreates target_folder inside destination_folder. The original target_folder is unchanged.

---

### Post by RayArdia on 2014-01-02
> **ajgreeny said:**
> As far as I'm aware you can choose only folders in the browse window of grsync; you can not go right down to file level, though I am sure you can do it in rsync in terminal and it may be possible using the Advanced or Extra options tabs.
```
rsync -t Pictures/*.jpg recovered_jpegs
``` This assumes all your jpg files have the same suffix .jpg using the same letter case and are in the root of your Pictures folder.  If not you will need to use the path to the source files and then either need to rename all to .jpg or repeat the rsync for each suffix, eg JPG, jpeg, JPEG, etc etc.

I believe it may also be possible to use the **find** command to find all of the jpgs in the source folder, and then use the -exec option to rsync them to recovered_jpegs folder, but that is a bit beyond my immediate skills.

Thank you.
My .jpeg files are 'loose' within folder /home/ray so would this work:-

```
rsync -t ray/*.jpg recovered_jpegs
``` 

ie, to sweep all the loose files into folder recovered_jpegs?

---

### Post by RayArdia on 2014-01-02
> **buzzingrobot said:**
> Are all those files on the same machine?  If so, rsync is overkill. The cp command copies and mv moves, i.e., mv removes the files from the current location and puts them in the new location.

Say the files are now in /oldfolder, and you want them in /newfolder.  A "cp -R /oldfolder /newfolder" will put all the files in /newfolder/oldfolder. Generically, "cp -R destination_folder target_folder" recurses through everything in target_folder and recreates target_folder inside destination_folder. The original target_folder is unchanged.

I must agree that rsync does seem to be overkil - and anyway I couldn't follow man rsync at all.
Grsync seems very simple to operete BUT I can't select the 'loose' files, only directories; see my 'bleats' above.

---

### Post by ajgreeny on 2014-01-02
Having given this more thought, the simpler **cp** or **mv** commands ```
cp *.jpg recovered_jpegs/
``` or ```
mv *.jpg recovered_jpegs/
```will do it for you if all the files are as you call it "loose" in your home, and again this depends on all the files being .jpg, not JPG or jpeg etc etc.
The trailing / on **recovered_jpegs/** is important if using rsync but does not matter with cp or mv.

cp will copy them and leave them also in your home folder, mv will move them out of home to the new folder.

I have just noticed (never used it though) that there is a "browse files" selection box in the "Extra options" tab of grsync that may help you with that if you want to look further into using it; I use grsync and rsync only for backing up my home, so have never bothered with the individual file options.

---

### Post by buzzingrobot on 2014-01-02
Per ajgreeny, if the filenames have a consistent extension, say, '.jpg', then using '*.jpg' will collect them all. If different extensions exist, just repeat the command using the different extensions.

The '*' in '*.jpg' will match any and all filenames that end with '.jpg'.

---

### Post by RayArdia on 2014-01-02
Thanks, I think I'll try the cp one then if it goes pear-shaped I'll still have files to move!
As regards the "browse files" section in Grsync, I even found a tick-box to turn you into a 'Superuser', but since I still couldn't select the files because they were greyed out, neither helped.

---

