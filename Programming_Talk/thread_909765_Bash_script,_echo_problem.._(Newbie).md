---
title: "Bash script, echo problem.. (Newbie)"
date: 2008-09-03
forum: Programming Talk
---

### Post by Spyros_Gre on 2008-09-03
Hello!!! 
I have a background in C/C++ programming and I started making my first bash scripts.
I have a simple problem!

I made a simple script that creates a file (does also some file checks) and then it tries to write in the file (after that it copies it elsewhere).  
I use echo in order to write into the file. I try to repetitively  write the number of loops of the program. If I don't redirect to the file, the output is OK with every loop echoing something distinctively. If I redirect to the file, the output seems to get overwritten and only the last loop leaves its mark. I hereby present you the "code"..

```
#!/bin/bash          
echo -n "Enter a filename:"

read filename
if [ -f "$filename" ]; then
	echo "File exists deleting..."
	echo "Creating file again..."
	rm $filename
fi

touch $filename
if [ ! -r "$filename" ]; then
	echo "File is not read-able"
	exit 1
fi 
i=1000
while [ $i -gt 10 ]; do
	((i--))
	echo $i $\n > $filename #HERE IS THE PROBLEM
done
#echo ok > $filename
#echo ok2 > $filename
cp $filename "ok"

``` 

Thank you!

---

### Post by ghostdog74 on 2008-09-03
use the "append" output redirection operator ">>" instead of ">".

---

### Post by Spyros_Gre on 2008-09-03
Thank you!!! That did the trick!
:)

---

