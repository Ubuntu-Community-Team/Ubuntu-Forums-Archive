---
title: "making a password file out of multiple files"
date: 2011-06-15
forum: Programming Talk
---

### Post by Mia_tech on 2011-06-15
I'm trying to compile multiple password files into a single one, and the script I've created does just that, but I would like to hear other opinion, especially when it comes to the "sort" portion of the script. sorting in can take time specially when sorting millions of words....here's the script

```
files=$(ls -1)
script=$(basename $0)

for file in $files
do
	#skipping this file else read file
	if [ "$file" == "$script" ]; then
		continue
	else
		while read line
		do
			#adding words only greater than 8 char
			if [ ${#line} -ge 3 ]; then
				echo "$line" >> tmpfile
			fi
		done < $file
	fi
done

#sorting alphabeticaly and deleting duplicates
sort -u tmpfile > superwpa 2>/dev/null
if [ $? != 0 ]; then
	echo "script encounter an error..."
	exit 1
fi

#cleaning up
rm tmpfile > /dev/null 2>&1
if [ $? != 0 ]; then
	echo "script encounter an error..."
	exit 1
fi
```

---

### Post by amauk on 2011-06-15
What's the purpose of this script?
What are the passwords being used for?

There's proper ways of generating secure passwords
Eg. makepasswd

---

### Post by geirha on 2011-06-15
Seems like it's doing the equivalent of
```

grep -h ... * | sort -u > /some/dir/superwpa
# or
awk 'length >= 3 && !seen[$0]++' * > /some/dir/superwpa

```

The latter doesn't sort it, but it does filter out duplicates.

---

### Post by Mia_tech on 2011-06-15
> **geirha said:**
> Seems like it's doing the equivalent of
```

grep -h ... * | sort -u > /some/dir/superwpa
# or
awk 'length >= 3 && !seen[$0]++' * > /some/dir/superwpa

```

The latter doesn't sort it, but it does filter out duplicates.

lol... I would like to think my script is more sophisticated, but, yeah, they are doing the same thing.... you gotta love linux commands.

---

### Post by geirha on 2011-06-15
> **Mia_tech said:**
> lol... I would like to think my script is more sophisticated, but, yeah, they are doing the same thing.... you gotta love linux commands.

They don't do exactly the same things though. Your bash script has a possible bug in that a left-over tmpfile or destination file might exist from a previous run, and those will be processed along with the other input files.

Another difference is that your bash-script will trim off leading and trailing whitespace, and also remove backslashes, before testing the length of the line.

And lastly, your script won't handle filenames containing whitespace or glob characters correctly. This is because of your use of ls, which should never really be used in a script. The shell can iterate filenames containing any characters you can think of, and quite safely, without using any external commands like ls.
```
for file in *; do ...
```

---

### Post by Mia_tech on 2011-06-15
> **geirha said:**
> They don't do exactly the same things though. Your bash script has a possible bug in that a left-over tmpfile or destination file might exist from a previous run, and those will be processed along with the other input files.


take a look at 
```

#cleaning up
rm tmpfile > /dev/null 2>&1
if [ $? != 0 ]; then
	echo "script encounter an error..."
	exit 1
fi

```

thanks for all your input; however, the main problem with this script is optimizing the times it takes to sort the output file, especially when dealing with millions of words. I was wondering if inserting the sort command inside the for loop and sorting the output file after a new file has been added will somehow reduce the time it takes to sort the file.

---

### Post by amauk on 2011-06-15
> **Mia_tech said:**
> take a look at 
```

#cleaning up
rm tmpfile > /dev/null 2>&1
if [ $? != 0 ]; then
	echo "script encounter an error..."
	exit 1
fi

```Just FYI, your script can exit before the cleanup takes place (If the sort doesn't return 0 exit status, then exit 1)

---

### Post by Mia_tech on 2011-06-15
> **amauk said:**
> Just FYI, your script can exit before the cleanup takes place (If the sort doesn't return 0 exit status, then exit 1)

well, in that case is irrelevant whether the tmpfile gets remove or not. It is obvious that script exited with error... now, it will be better to make a more descriptive error. For example, I would have to specify where exited and why. That's very simple to do. But we're deviating from the point of this thread which is to optimize the sorting part of script... is there a way to make it faster?

---

### Post by geirha on 2011-06-15
> **Mia_tech said:**
> take a look at 
```

#cleaning up
rm tmpfile > /dev/null 2>&1
if [ $? != 0 ]; then
	echo "script encounter an error..."
	exit 1
fi

```


Yes, as amauk said, if the script reaches that part of the script, the file will be deleted. If you kill or interrupt the script before that, it will not be deleted.

> **Mia_tech said:**
> 
thanks for all your input; however, the main problem with this script is optimizing the times it takes to sort the output file, especially when dealing with millions of words. I was wondering if inserting the sort command inside the for loop and sorting the output file after a new file has been added will somehow reduce the time it takes to sort the file.

No, you'd still have to sort the whole thing to discover all duplicates. Also, bash is not the best tool to use for parsing large files. grep, awk or sed will be much more efficient as they are designed for that task.

Compare the awk I showed previously with your while read loop:

```
$ wc -l /usr/share/dict/words
98569 /usr/share/dict/words
$ time awk 'length >= 3 && !seen[$0]++' /usr/share/dict/words >/dev/null

real	0m0.200s
user	0m0.188s
sys	0m0.012s
$ time while read line; do if [ ${#line} -ge 3 ]; then echo "$line" >> /dev/null; fi; done </usr/share/dict/words

real	0m4.663s
user	0m4.108s
sys	0m0.548s

```

And that's even without trying to remove duplicates in the bash-version.

Your bash code reopens the output file every time it writes a line btw. That's very inefficient, so you can lower the runtime a bit by redirecting the output of the whole loop instead of each echo command.
```

$ time while read line; do if [ ${#line} -ge 3 ]; then echo "$line"; fi; done </usr/share/dict/words >>/dev/null

real	0m3.307s
user	0m3.144s
sys	0m0.156s

```

---

