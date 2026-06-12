---
title: "Bash -  batch renaming"
date: 2009-01-14
forum: Programming Talk
---

### Post by ThorX89 on 2009-01-14
Hi there. 
I have done some renaming of files in bash before. I usually needed to do something like change a part of it for another, so I generally did something like:

$ ls *| while read n; do mv "$n" ......; done

Now I'd like to do something similar but different.
I have a list of files containing movie episodes. Their naming is really messy, but the names always contain the number of the episode.
I also have downloaded a list of the episodes from the internet (tidy names, also contain the number of the episodes). Now what I'd like to do is to rename the messy file names to the tidy ones, based on the fact that the number part of both the tidy and messy file names are identical for the corresponding file names.

Any idea how to do that in bash?

---

### Post by azzamite on 2009-01-14
Unless its a 200 episode anime, you may have finished the
renaming by hand...

If the name of the file desn't include the episode's name,
you could try using something like this.
ls * | **sort |**
And include somewhere within the while a variable **$i=$i+1**
mv "$n" "episode - **$i**"; done

Or you could try using regexes.

---

### Post by slavik on 2009-01-14
man rename. :)

---

### Post by swiftarrow on 2009-03-14
> **slavik said:**
> man rename. :)

I tried using rename with a pearl regex but it just renamed everything to gggggggggggggggggggg and variations thereof.  What I used was:

```
rename -v -n 'y/\([A-Z]\).\([0-9]*\)\([a-zA-Z0-9 ]*\).jpg/$1_$2.jpg/' *.jpg

```

to select files of the form A.1 some name.jpg and rename to A_1.jpg

It ran the rename, skipped a bunch of files for no apparent reason, and renamed most of them to gggggggg$ggggggggg or ggggggggggggggggg or variants.  Any help?

EDIT: this happened in xubuntu Ibex, all up to date, using xfce-terminal.

---

### Post by ghostdog74 on 2009-03-14
why do you need to make it so complicated. Do it step by step
```

# filename="A.1 some name.jpg"
# echo ${filename/./_} #change the "." into "_"
A_1 some name.jpg 
# filename=${filename/./_}  #store the changes
# echo ${filename/ *./.}
A_1.jpg
# filename=${filename/ *./.} #substitute from first space to the first occurence of dot "."
# echo $filename
A_1.jpg


```

---

### Post by geirha on 2009-03-14
> **swiftarrow said:**
> 
```
rename -v -n 'y/\([A-Z]\).\([0-9]*\)\([a-zA-Z0-9 ]*\).jpg/$1_$2.jpg/' *.jpg

```


y// transliterates, you want to use s//:
```
rename -n 's/^([A-Z])\.(\d+).*/$1_$2.jpg/' *.jpg
```

---

### Post by oygle on 2009-03-17
I need to change the case of all the JPG files, to lowercase, and thought this might work

```

for old in *
do
new=`echo $old | sed 's/A-Z/a-z/g'`
mv $old $new
done

```

but get msgs like .

> 
mv: `IMG_0978.JPG' and `IMG_0978.JPG' are the same file


Obviously $new hasn't been evaluated properly >

Oygle

---

### Post by geirha on 2009-03-17
That's when you want to use y//.
```
rename -n 'y/A-Z/a-z/' *.JPG
```
Replace -n with -v to have it actually rename instead of just telling you what it would've done.

---

### Post by oygle on 2009-03-17
Thanks very much, that worked perfectly.

---

### Post by a_hippie on 2009-07-20
> **geirha said:**
> That's when you want to use y//.
```
rename -n 'y/A-Z/a-z/' *.JPG
```
Replace -n with -v to have it actually rename instead of just telling you what it would've done.


That was just the trick I needed.  Guess photobucket doesn't get uppercase filenames--lame yes, but the code just saved me a TON of time.  Thank you thank you thank you!  :)


regards,

---

