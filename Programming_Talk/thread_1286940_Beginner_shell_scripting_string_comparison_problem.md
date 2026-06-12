---
title: "Beginner shell scripting string comparison problem"
date: 2009-10-09
forum: Programming Talk
---

### Post by RolandFlagg on 2009-10-09
So I'm trying to write a script that involves in comparing file names in a directory, but for some reason my if statement does not seem to be doing anything at all:

for i in $( ls -A ); do
    for j in $( ls -A ); do
        echo i: $i j: $j
        if [ $i!=$j ]
        then echo they are not the same! file1: $i file2: $j
        fi
    done   
done

no matter what $i and $j are, the script echos that they are not the same. I tried checking if they were the same (ie. if [ $i==$j ]), and it echoed when they are not same as well. I also tried putting " around the $i and $j, but it didn't change anything. I cant figure out why the if statement is not doing anything.

Is there anything else the matter (ie the way im comparing the two)? Because the segment of code does the exact same thing whether I take out the if statement or leave it in.

Thanks so much, any help is greatly appreciated

---

### Post by NoaHall on 2009-10-09
Can you upload your whole script please? 
Try using "if [ $i != $j ]" with all the spaces as I did.

---

### Post by RolandFlagg on 2009-10-09
Thanks so much for responding!
here's the entire script

#! /bin/sh

dirD=$1
cd $dirD

for i in $( ls -A ); do
	for j in $( ls -A ); do
		echo i: $i j: $j
		if [ $i!=$j ] 
		then echo they are not the same! file1: $i file2: $j
		fi
	done	
done

I'll try out your suggestion.

---

### Post by RolandFlagg on 2009-10-09
O, your suggestion worked, lol thanks so much, looks like it was because of missing white spaces.

---

