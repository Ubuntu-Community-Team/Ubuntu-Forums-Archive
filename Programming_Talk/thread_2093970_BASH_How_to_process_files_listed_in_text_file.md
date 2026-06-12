---
title: "BASH: How to process files listed in text file?"
date: 2012-12-12
forum: Programming Talk
---

### Post by Valpskott on 2012-12-12
I have 2 directories with png files. One directory is called "OLD" and the other one is called "NEW". Some of the files in these directory need to be processed, but only the ones that have been updated. For this I tried "diff --brief -r" combined with cat, grep and sed, this way I managed to get a list (outputed to a txt file) of the files that needs to be processed.

I also have successfully written the processing chain (this by entering the file-names manually).

How ever, I want this to be automated, so I need help so that the script processes the files that are mentioned in the TXT file.

---

### Post by Vaphell on 2012-12-12
```
while read -r f
do
  something with "$f"
done < file

```
or skipping the file stage entirely

```
while read -r f
do
  something with "$f"
done < <( cmd1 | cmd2 | cmd3 )
```

---

### Post by Valpskott on 2012-12-12
Thank you for the quick reply. I'm not quite sure how to implement this though.

Where in the code do I input the text file?
I guess the "proccessing code" should be where you wrote "something with "$f"" where the variable f is the information of each file mentioned in the txt file, correct?

Not sure what the "< file" or "< <( cmd1 | cmd2 | cmd3 )" is for after done. Does it suggest I do the diff grep sed thingie there, like after the loop? Then how will the loop know what files should be processed?

Please elaborate some on what this does so I get a better chance of understanding. :)

---

### Post by SeijiSensei on 2012-12-12
If the list is in a text file with one entry per line, I use this:

```

FILES=$(cat /path/to/the/file)

for f in $FILES
do
    stuff
done

```

Now for some caveats.

First, do the files in the list contain complete paths or just filenames?  If the latter then you need to run the script from the directory in which the files are located, or have the script set the directory itself.  

[Critics - please don't bother to complain about using "cat".]

---

### Post by Valpskott on 2012-12-12
after testing Vaphell's suggestion and inserting the text file after the "done <" stage, that part of the script seemed to work.

How ever, It seemed to have created a new problem with the processing code(which worked before) that I hope someone can help me with.

```
composite NEW/$f -blend 50x50 OLD/$f TEMP/$f.01.png
convert TEMP/$f.01.png -background "#808080" -flatten +matte \
-channel rgba -alpha set -fuzz 1% -fill none -opaque "#7f7f7f" \
-channel rgba -alpha set -fuzz 60% -fill black -opaque "#808080" \
-background "#ffffff" -flatten +matte \
-channel rgba -alpha set -fuzz 1% -fill none -opaque "#000000" TEMP/$f.02.png
composite -compose dst-out TEMP/$f.02.png NEW/$f -matte DIFF/$f

```

Which results in a bunch of errors.

```
convert: unable to open image `TEMP/armor/cloth_1.png.01.png':  @ error/blob.c/OpenBlob/2587.
convert: unable to open file `TEMP/armor/cloth_1.png.01.png' @ error/png.c/ReadPNGImage/3238.
convert: missing an image filename `TEMP/armor/cloth_1.png.02.png' @ error/convert.c/ConvertImageCommand/3011.
composite: unable to open image `TEMP/armor/cloth_1.png.02.png':  @ error/blob.c/OpenBlob/2587.
composite: unable to open file `TEMP/armor/cloth_1.png.02.png' @ error/png.c/ReadPNGImage/3238.
composite: missing an image filename `DIFF/armor/cloth_1.png' @ error/composite.c/CompositeImageCommand/1616.

```

I'm fairly confident it has something to do with the pathways, My guess is that imagemagick does not create the directories for me.

---

### Post by SeijiSensei on 2012-12-12
> **Valpskott said:**
> I'm fairly confident it has something to do with the pathways, My guess is that imagemagick does not create the directories for me.

No, it doesn't.  You need to create them all in advance, or add lines to the script to do it for you before converting the files.

---

### Post by Vaphell on 2012-12-12
> ```
FILES=$(cat /path/to/the/file)

for f in $FILES
do
    stuff
done
```
ok, i'll bite ;-)
this will fail so hard with spaces... you need IFS= which suxx

then there is that cat... ;-) *var=$( < file )*

---

### Post by SeijiSensei on 2012-12-12
> **Vaphell said:**
> ok, i'll bite ;-)
this will fail so hard with spaces... you need IFS= which suxx

Yup, been there, done that.

Perhaps you can explain to me why

```
$(< filename)
```

is so much better than

```
$(cat filename)
```

other than what seems simple prejudice against using the cat command.  In what circumstances would one alternative work and the other not?

---

### Post by Valpskott on 2012-12-12
After alot of tinkering I managed to make the script duplicate the directory structure. By cd:ing into the NEW directory, copying the files (cp --parents -r $f ../DIFF/$f) then removed the files (rm ../DIFF/$f).

I'm marking this thread as solved.

Thanks to both of you for helping me.

---

### Post by Vaphell on 2012-12-12
*<* is better because it is a standard functionality of shell and doesn't require spawning yet another process.
similar case is with *touch* - people create empty files with *touch* because they don't know they can use builtin *> file* for that (with nothing before >).

besides, while it doesn't make much difference here, there is plenty of difference between standard functionality that is intended for its purpose and pretty much foolproof, and handmade fugly hacks full of caveats, eg widespread use of *for f in `ls`* instead of *for f in **

---

### Post by drmrgd on 2012-12-12
> **Vaphell said:**
> *<* is better because it is a standard functionality of shell and doesn't require spawning yet another process.
similar case is with *touch* - people create empty files with *touch* because they don't know they can use builtin *> file* for that (with nothing before >).

</snip>

People means me.  I had no idea that was possible (and more proper - if you want to say that).  Thanks for the tip!

---

### Post by JKyleOKC on 2012-12-12
> **Vaphell said:**
> *<* is better because it is a standard functionality of shell and doesn't require spawning yet another process.
similar case is with *touch* - people create empty files with *touch* because they don't know they can use builtin *> file* for that (with nothing before >).

Besides, while it doesn't make much difference here, there is plenty of difference between standard functionality that is intended for its purpose and pretty much foolproof, and handmade fugly hacks full of caveats, eg widespread use of *for f in `ls`* instead of *for f in **Great points. In addition, for the specific situation at hand, using input redirection will route the data through a FIFO behind the scenes while using "cat" will copy the entire file into RAM thus using much more in the way of resources. If the file in question is only a few K bytes that's no big deal, but if it's a couple of hundred GB then it makes the difference between running at all or crashing spectacularly...

---

