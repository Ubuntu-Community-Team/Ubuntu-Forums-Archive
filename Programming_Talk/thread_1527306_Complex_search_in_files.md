---
title: "Complex search in files"
date: 2010-07-09
forum: Programming Talk
---

### Post by Michlis on 2010-07-09
Hi,
Let me start by explaining the problem.
I have a very long list of files from one folder, where each line is a single file name e.g. 
- list.txt:
path/image1.gif
path/image2.jpg
path/doc.pd
...

I need to find out which files from the web server refer to those listed files (if any), so the output should be like this:
- results.txt
path/image1.gif www/home/index.php, www/products/template.php, ... (multiple references)
path/image2.jpg www/tools/select.php (single reference)
path/doc.pdf  (empty if no references)

Due to the length of the list and huge search scope (www/*) I need to find a fully automatic solution. I tried with grep, sed and some regular expressions, but I couldn't solve the problem completely.

Next, I tried to reduce the search scope by finding the files that contain the "path/[somefile]" expression using:

```
egrep -rl '/path/([A-Za-z0-9\_\-]+\.[A-Za-z]{3})' /www/ --exclude-dir=.svn

```

So I ended up with two long list of files to search for (A) and files to search in (B).

I was planning to write a shell script, which would loop through (A) and grep each single file name in all files listed in (B), but I am not good at scripting in bash. Especially when it comes to redirecting output to get the final result in the format explained above.

Perhaps someone could explain me how to start with such script?
Any suggestions are welcomed!

---

### Post by Trumpen on 2010-07-09
You may use the -f option of grep, which makes grep to read the patterns from a file, and awk to print the way you need:

```
grep -F -f list.txt /www/* | awk -F: '
    a[$2]{
        a[$2]=a[$2] ", " $1; 
        next
    } 
    
    {
        a[$2]=$1
    } 

    END{
        for (el in a) 
            print el,a[el];
    }'
```

---

### Post by Michlis on 2010-07-12
Hey,
I ended up with something similar:

```

#!/bin/bash
while read line;
do {
echo $line
lineresult=""
counter=0

	while read searchin;
	do {
		fpath=/resource/images/${line}
		result=`grep -sl $fpath $searchin`
		
		if [ ! -z "$result" ]; then #An results?
		   ((counter++))
		   if [ -z "$lineresult" ]; then #First result?
		  	lineresult=$result
		   else
			lineresult="${lineresult},${result}"
		   fi
		fi
	}
	done < <(cat searchinlist.txt)

echo "${line};${counter};${lineresult}" >> results.csv
}
done < <(cat searchforlist.txt)

```

---

