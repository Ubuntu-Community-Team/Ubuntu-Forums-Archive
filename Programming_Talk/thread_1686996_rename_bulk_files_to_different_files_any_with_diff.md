---
title: "rename bulk files to different files any with different name"
date: 2011-02-13
forum: Programming Talk
---

### Post by gpgiuit on 2011-02-13
Hello I hope post in this category is correct.

I have many files to rename with other many files with different names for each one, so it is not sufficient to add or remove to all files a text.

I have 123456.jpg 456789.jpg 556442.jpg ...... (many of these files)
I want to rename all these files in 
mio-prodotto.jpg copertina-musicale.jpg prodotto-informatico.jpg.... (many of these with different names)

Is there a script via terminal that do this?
I also have original names and modified names on openoffice, so I need a command, a script that I will paste on terminal and rename these files.

Please...

---

### Post by xplode on 2011-02-13
several ways of doing this i guess, here's how i would do it. assuming you have a plaintext file with:

original-1.jpg modified-1.jpg
original-2.jpg modified-2.jpg

separated by space, a commandline loop wold work:

bash> cat file-with-filenames.txt | while read old new; do mv $old $new; done

this is assuming you have that file-with-filenames.txt as above and none of the files have spaces in the names. sorry if i misunderstood you situation and what you have available.

if you have a comma-separated csv file (saved from an office suite) you can transform it to space separated with:

cat file-with-filenames.csv | tr "," " " > file-with-filenames.txt

---

### Post by gpgiuit on 2011-02-13
so I have to write
cat 123456.jpg | ; mio-prodotto.jpg; do mv $old $new;
that string for one file?
Sorry I don't know bash ...
if you can say to me exact to write on terminal I can test.
yes my files are all without spaces.

---

### Post by xplode on 2011-02-13
i might have misunderstood you, i thought you had a document detailing original filename and modified filename, and you wanted to rename all your files from the original name to the modified name (or the other way around) in one go - without having to rename each file one by one (lots of typing). if you don't have that document my idea really doesn't save you any time.

the command i described would have handled renaming all your files in one go, but you need that document describing old and new name. in my example i called it file-with-filenames.txt. this should be a plain text file, with two names per line, the old name and the new name. if you have that file, put it in the directory where your files to rename are. then in your terminal - cd to this directory and run exactly the command line i had above:

cat file-with-filenames.txt | while read old new; do mv $old $new; done

this will loop through the lines in your input file (file-with-filenames.txt) and rename the first name to the second name, then go to the next line and rename the first name to the second name, etc.

so if your file-with-filenames.txt looks like this:

123456.jpg mio-prodotto.jpg
456789.jpg copertina-musicale.jpg
556442.jpg prodotto-informatico.jp

(as many lines as you have files) after running my command above, your 123456.jpg file will have been renamed mio-prodotto.jpg, your 456789.jpg will have been renamed copertina-musicale.jpg... etc.

i guess this requires some rudimentary knowledge of the terminal and bash, so if you feel uncomfortable about any of this, perhaps someone else has a better idea.

---

### Post by Vaphell on 2011-02-13
so you got open office spreadsheet with full old and new names?
save/export it as a CSV - it's a format where columns are separated with ,

then create a script where it's needed
```
#!/bin/bash

while **IFS=,** read old new
do
  echo "$old -> $new"
  # mv "$old" "$new"
done < **names.csv**

```

IFS part sets ',' as a separator of input data, so 1st column is read to old, 2nd to new. < names.csv part feeds the loop from given file. Echo inside the loop prints out these pairs, mv command renames (it's commented now with #, uncomment when you confirm the pairs are good)
set the script as executable and run it

---

### Post by gpgiuit on 2011-02-13
> **xplode said:**
> i might have misunderstood you, i thought you had a document detailing original filename and modified filename, and you wanted to rename all your files from the original name to the modified name (or the other way around) in one go - without having to rename each file one by one (lots of typing). if you don't have that document my idea really doesn't save you any time.

the command i described would have handled renaming all your files in one go, but you need that document describing old and new name. in my example i called it file-with-filenames.txt. this should be a plain text file, with two names per line, the old name and the new name. if you have that file, put it in the directory where your files to rename are. then in your terminal - cd to this directory and run exactly the command line i had above:

cat file-with-filenames.txt | while read old new; do mv $old $new; done

this will loop through the lines in your input file (file-with-filenames.txt) and rename the first name to the second name, then go to the next line and rename the first name to the second name, etc.

so if your file-with-filenames.txt looks like this:

123456.jpg mio-prodotto.jpg
456789.jpg copertina-musicale.jpg
556442.jpg prodotto-informatico.jp

(as many lines as you have files) after running my command above, your 123456.jpg file will have been renamed mio-prodotto.jpg, your 456789.jpg will have been renamed copertina-musicale.jpg... etc.

i guess this requires some rudimentary knowledge of the terminal and bash, so if you feel uncomfortable about any of this, perhaps someone else has a better idea.

You understood perfectly (I instead understand english not very well).
So I created under same directory in which I have images file file-with-filenames.txt
in which I write to test 2 rows
533067.jpg primo-product.jpg
533068.jpg secondo-p.jpg
ok then I run via terminal
under directory in which I have these 3 files
cat file-with-filenames.txt | while read old new; do mv $old $new; done
but system says to me
mv: impossibile eseguire stat di "533067.jpg": Nessun file o directory
mv: impossibile eseguire stat di "533068.jpg": Nessun file o directory
in english it says that no file or directory, but I have them on my directory

For second solution I am trying to see
thanks :(

---

### Post by gpgiuit on 2011-02-13
So sorry, I had to be anything wrong.
First solution WORKS!!!!!

Thanks to you very much, you did to me a great favour!!! :KS

thanks again.
:lolflag:

---

