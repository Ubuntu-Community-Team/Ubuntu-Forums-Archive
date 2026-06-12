---
title: "Creating a script to zip specific filetypes in arbitrary subfolders"
date: 2011-12-02
forum: Programming Talk
---

### Post by saphil on 2011-12-02
In another thread, I got this neat structure from Vaphell"
> **Vaphell said:**
> code maybe something like this?
```
for f in */*
do
  if [ -f "$f" ]
  then
    echo $f is a file 
    echo mv -v "$f" "${f%/*}/${f%/*}_${f##*/}"
  else
    echo $f is a dir
  fi
done
``` now it prints out the mv command for testing purposes

```
$ ./mass_ren.sh 
111/a.txt is a file
mv -v 111/a.txt 111/111_a.txt
111/b.txt is a file
mv -v 111/b.txt 111/111_b.txt
222/a.txt is a file
mv -v 222/a.txt 222/222_a.txt
222/b.txt is a file

```
I want to use a similar structure to zip a bunch of files in separate subdirectories and I just don't seem to get the organization.  I tried this but the outputs gave me a hidden file called .zip in all the directories.
```
for i in *; do zip $i/$i_images.zip $i/*.jp2; echo "$i_images.zip is complete" >> ziplog.log ; done

```

I tried this but the output is still weird
```
echo "Enter the extension type you would like to zip"
echo " for instance jp2 waa ai or whatever."; read extt

for d in */*
do
  if [ -d "$d" ]
  then
    echo $d is a directory 
    echo zip "${d##*/*}/${d##*/*}_images.zip" *.$extt
  else
    echo $d is a file
  fi
done

``````
+ for d in '*/*'
+ '[' -d example2/pd.pdf ']'
+ echo example2/pd.pdf is a file
example2/pd.pdf is a file
+ for d in '*/*'
+ '[' -d example2/shoey ']'
+ echo example2/shoey is a directory
example2/shoey is a directory
+ echo zip /_images.zip '*.waa'
zip /_images.zip *.waa

```
I don't really want you to give me the fish, I want to understand fishing. 
Where would I go to understand this structure better.

---

### Post by saphil on 2011-12-05
Well now I have the answer to why the zip file was coming out named .zip
I had to put a lot more quote marks in.

```

for x in *; do if [ -d "$x" ]; then zip   "$x/$x.zip" *.txt; fi; done
# gives a zip file called arbitrary_directory/arbitrary_directory.zip
# however, 
for x in *; do if [ -d "$x" ]; then zip   ""$x/$x_textses.zip" *.txt; fi; done
# gives a file with no name (my starting point for this thread)
for x in *; do if [ -d "$x" ]; then zip   ""$x""/""$x""_textses.zip"" *.txt; fi; done
# quoting the variables and text additions separately worked perfectly - going only one level deep.
# since I only need to go one level deep, this is as far as I am going for now.
# note: if the wildcard filetype is quoted, the script fails because the literal string "*.txt" doesn't and probably can't exist.


```

---

