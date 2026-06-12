---
title: "Limiting memory usage of a specific process?"
date: 2009-01-21
forum: Programming Talk
---

### Post by skullmunky on 2009-01-21
I did some google searching, but can't seem to find a clear answer on this.  How do you limit the amount of memory a process uses - like nice, but for memory limit?  

Here's the specific use case: I'm converting many batches of jpg's to PDF's using ImageMagick, and it's totally killing my machine.  top says convert is using only about 2% CPU but 50% mem, (if I have 2GB, that's 1GB, right?) Everything else gets really slow and unresponsive, which I'm theorizing is because once convert devours all the physical memory there's a lot of page swaps going on. 

so anyway is there a way to limit just that one process?  if i understand this right, ulimit sets the limit for all subsequent processes from that shell?

---

### Post by loell on 2009-01-21
i think you can limit it by

```
convert -limit memory <mem allocation by MB> file1.png file2.pdf
```

still unsure though..

---

### Post by slavik on 2009-01-21
unless the program supports it, how do imagine limiting a process to the amount of memory it can use? say it needs that 1GB, how do you imagine it would react if it didn't have that much available?

---

### Post by loell on 2009-01-21
have just checked, it does have **-limit memory** parameter, but once it hits the ceiling, it'll spike some cpu usage which you also want to avoid. and so maybe you could use nice alongside that parameter.

---

### Post by Quikee on 2009-01-22
> **slavik said:**
> unless the program supports it, how do imagine limiting a process to the amount of memory it can use? say it needs that 1GB, how do you imagine it would react if it didn't have that much available?

React the same way when you run out of memory - kill it ;)

---

### Post by lavinog on 2009-02-09
> **skullmunky said:**
> I did some google searching, but can't seem to find a clear answer on this.  How do you limit the amount of memory a process uses - like nice, but for memory limit?  

Here's the specific use case: I'm converting many batches of jpg's to PDF's using ImageMagick, and it's totally killing my machine.  top says convert is using only about 2% CPU but 50% mem, (if I have 2GB, that's 1GB, right?) Everything else gets really slow and unresponsive, which I'm theorizing is because once convert devours all the physical memory there's a lot of page swaps going on. 

so anyway is there a way to limit just that one process?  if i understand this right, ulimit sets the limit for all subsequent processes from that shell?

I find that it is much easier and more reliable to convert one file at a time with imageMagick:
```

for file in *.jpg;do echo "converting $file";convert "$file" "${file%.jpg}.pdf";done

```

for those that don't understand for loops:
```

for {variable} in {list}
do
{code involving variable}
done

```
The list in the convert example is a list of files in the current directory that match the pattern *.jpg.  
The list can also be made by reading a text file:
```
for x in $(cat mytext.txt)
```
or if you need a sequence of numbers:
```
for x in {1..99}

for x in $(seq 1 99)

for x in $(seq 1 2 99 )
# the 2 tells it to skip every other num

for x in $(seq -w 1 99)
# the -w will add leading zeros to make all numbers equal width

```

filenames with spaces can mess up a for loop. The for loop will breakup a list by the spaces and newlines. To fix this we can set IFS to only equal a new line:
```

IFS='
'
for file in *.jpg;do echo "converting $file";convert "$file" "${file%.jpg}.pdf";done
unset IFS

```
note that there is only a newline between the single quotes...no space.
unset IFS restores the IFS back to default...although many scripts will make use of setting a OldIFS=IFS before changing IFS then changing IFS=OldIFS...I prefer unsetting it.

The ${file%.jpg}.pdf uses the % to remove .jpg from the end of the string so that .pdf can be appended to the string.  ${file#IMG} would remove the IMG from the beginning of a filename.

If you are not working with files in the current directory, you can use basename $file and dirname $file to split the string up.

If you find yourself using a loop repeatedly, you can make a script:
```
#!/bin/bash
# imgconv - Converts image files type to another
# Usage:  imgconv {old extension} {new extension}
# ex: imgconv jpg pdf

#take care of whitespace
IFS='
'

for file in *.$1
do

# remove old extension
filebase=$(basename $file $1)

echo "Converting $file to ${filebase}$2"

# convert the file
convert "$file" "${filebase}$2"||{
echo "THERE WAS AN ERROR, BREAKING LOOP"
break
}

done

#restore IFS
unset IFS

```
the above code should convert all files in the current folder
to execute it you can chmod it, or just run it with bash:
```
bash imgconv jpg pdf

```

If you find you use it really frequently, you may want to consider making an alias for it.

---

