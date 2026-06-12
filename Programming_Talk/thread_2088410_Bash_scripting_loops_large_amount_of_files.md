---
title: "Bash scripting loops: large amount of files"
date: 2012-11-26
forum: Programming Talk
---

### Post by sbergman on 2012-11-26
Hi,

I'm trying to write out a sorting algorithm to move png's that were created from some weather data. In my bash script I've got a for-loop that starts with 
```
for file in $src_dir/*.png; do
```
and then it moves the $file into a folder that I created dynamically. Once 60 files gets moved, it increments to the next folder, etc etc.

I can open 60 pngs in Nautilus and scan through the thumbnails by eye, picking out the ones I need (but I cant do that with large amounts of files cos it takes forever to make all the thumbnails in one go.)

The script has been debugged and works with a small number of pngs, but my problem is that the number of files is so large (I think its in millions) that I run out of memory when I start the for-loop. So I'm looking for a workaround.

I thought that if I could somehow change the for-loop to a
do-while loop, and then pass some condition which says list only a single file in the folder and keep doing this-that-and-the-other while that condition is true... it wont run out of memory and will keep sorting the png's into subfolders until the original folder is empty, and the condition fails.

Any suggestions if this is possible?

---

### Post by Vaphell on 2012-11-26
general approach with while loop would look like this

```
while IFS= read -rd $'\0' file
do
  something with "$file"
done < <( find "$src_dir" -iname '*.png' -print0 )

```
find produces null delimited list (null is forbidden by filesystems so it's safe to be used as a separator between elements), while read processes it with null delimiter

care to give more accurate description of what you are dealing with? It would allow to figure out solution more suited for the task at hand.

---

### Post by sbergman on 2012-11-26
The problem I think is that I'm dealing with a large amount of files. I get a "Cannot allocate memory error"

I've kind of found a workaround, though not very elegant if I do
```
for file in $src_dir/*[0-5]0.png; do
```

and then manually change my bash script and run it twenty times. It basically chunks the job up.

Question about 'find' is it possible to invoke find so that it returns the first result and then immediately quits? (Ie stops using memory?)

---

### Post by steeldriver on 2012-11-26
I think Vaphell's solution won't suffer from that problem - effectively the while/read loop buffers the output from find

However you could also try xargs if you prefer

```
echo "$src_dir"/*.png | xargs mv -t /path/to/target_dir/
```[http://en.wikipedia.org/wiki/Xargs](http://en.wikipedia.org/wiki/Xargs)

---

### Post by ofnuts on 2012-11-26
> **sbergman said:**
> Hi,

I'm trying to write out a sorting algorithm to move png's that were created from some weather data. In my bash script I've got a for-loop that starts with 
```
for file in $src_dir/*.png; do
```and then it moves the $file into a folder that I created dynamically. Once 60 files gets moved, it increments to the next folder, etc etc.

I can open 60 pngs in Nautilus and scan through the thumbnails by eye, picking out the ones I need (but I cant do that with large amounts of files cos it takes forever to make all the thumbnails in one go.)

The script has been debugged and works with a small number of pngs, but my problem is that the number of files is so large (I think its in millions) that I run out of memory when I start the for-loop. So I'm looking for a workaround.

I thought that if I could somehow change the for-loop to a
do-while loop, and then pass some condition which says list only a single file in the folder and keep doing this-that-and-the-other while that condition is true... it wont run out of memory and will keep sorting the png's into subfolders until the original folder is empty, and the condition fails.

Any suggestions if this is possible?
To move 60 files in the folder to somewhere else that would be:

```

find $sourcedir -name "*.png" | head -60 | xargs mv -t $targetdir

```This way you never subject the bash interpreter to your million files. For a smaller number of files 

```

ls $sourcedir/*.png | head -60 | xargs mv -t $targetdir

```would work just as well.

---

### Post by Vaphell on 2012-11-26
> ```
for file in $src_dir/*[0-5]0.png; do
```
and then manually change my bash script and run it twenty times. It basically chunks the job up.

if the file names lend themselves to programmatic solution, you could run 2 loops to split the work automatically
eg
```
for x in {000..999}
do
  for f in "$src_dir"/$x*.png
  do
    something with "$f"
  done
done
```

we don't know if there is some common filename format though and what is the sorting algorithm.

---

### Post by sbergman on 2012-11-30
Thanks all. I ended up solving the problem by just copying the block 20X (yes, I know its an ugly solution but "any port in a storm" as the saying goes)

Strangely enough Vaphell's suggestion actually looks promising enough to sort out a totally different problem I had.

---

