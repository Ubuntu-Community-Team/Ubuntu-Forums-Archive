---
title: "shell shell script to iterate a file line-by-line and delete current line"
date: 2014-10-12
forum: Programming Talk
---

### Post by IAMTubby on 2014-10-12
Hello,
 Is it possible to write a shell script to iterate through a file line-by-line and delete the current line?

I have seen examples using sed to delete a particular line number(say line no.3 using sed '3d' filename.txt), but was unable to find a character for matching the current line.
Please note that the same line might be present at multiple places in the file, so matching for a pattern and deleting the line will not help. 

I was looking for something like this,
```

 while read line
 do
  echo $line
  #delete current line before going to the next line
 done < filename.txt

```

Thanks.

---

### Post by ofnuts on 2014-10-12
What would be the difference with just 

```

cat file
echo "" >file 

```

Because in the end, you'll have displayed the whole file, and deleted all lines in it...

---

### Post by Vaphell on 2014-10-12
you shouldn't really try to read and write to the exact same file at once. Nothing good will come out of it.

---

### Post by IAMTubby on 2014-10-12
> **ofnuts said:**
> Because in the end, you'll have displayed the whole file, and deleted all lines in it...
Hello ofnuts,
Nope, before deleting I plan to copy certain line numbers to a buffer etc and then delete the line from the file.

---

### Post by IAMTubby on 2014-10-12
> **Vaphell said:**
> you shouldn't really try to read and write to the exact same file at once. Nothing good will come out of it.
Vaphell, I thought about it.
Say, I want to have only certain lines of a file based on a condition(presence of a substring, say), so would you advise me to 1.Read the file, .2.copy all the lines matching the condition to a buffer and then 3.Write to the file ?
(Assume we are not using grep,awk,sed here and we're using just shell scripting.)

I was thinking that I could just read the file, and replace the lines that do not match the condition with blank space(or delete the line if there is such an option, so that even empty lines aren't seen)

Please let me know your thoughts.
Thanks.

---

### Post by Vaphell on 2014-10-12
in pure bash you need some temporary structure, a string, an array or a file, to either store input or output. Reads and writes have to be performed on separate things. Iirc > inilitializes a 0-size file right off the bat in effect zeroing out inputs. Even sed -i does tempfile behind the curtains.

i'd probably use something like this
```
while read ln; do [[ $ln =~ pattern ]] && echo "$ln"; done < file1.txt > file2.txt
mv file2.txt file1.txt
```

if the output is small i might go for an array with *arr+=( "$ln" )* inside the loop and then *printf -- '%s\n' "${arr[@]}" > file1.txt* after the loop.

---

### Post by ofnuts on 2014-10-13
> **IAMTubby said:**
> Hello ofnuts,
Nope, before deleting I plan to copy certain line numbers to a buffer etc and then delete the line from the file.

I still think that the display of the full file and the removal/selection of the lines do not need to be done together. What are you trying to achieve exactly?

---

### Post by IAMTubby on 2014-10-14
> **ofnuts said:**
> What are you trying to achieve exactly?
Sorry for the late reply, ofnuts.

Okay, I had this client-server program in which the server is logging all transactions to a file, with a special bit for success/failure. Every time a request comes from the client, it first checks if there are any (pending)'failure' transaction(*that's where our file comes in*) and if yes, it deletes that line from the file and then proceeds with the request. I was thinking if there was an alternate method to reading all the file contents to a buffer and rewriting them sans the failure request.

---

### Post by ofnuts on 2014-10-15
No,  on Linux filesystems, to remove a line in the middle of a file, you always end up reading the whole file and rewriting it, whether it is done explicitly or not. Not much of a problem usually as long as the size is reasonable. 

But for this kind of use you should really be looking at using a database. 

If you want to keep the file, you can do things differently: 

[LIST]
[*]grep the whole file for all records about the client
[*]check if the last one is a failure.
[*]when things turn out OK, append a "success" line.
[/LIST]
this way you never need to rewrite the whole file (appending at the end is trivial). You still read the whole file but you are already doing that. And you keep a complete history of the failures.

---

### Post by IAMTubby on 2014-10-15
> **ofnuts said:**
> 
But for this kind of use you should really be looking at using a database. 

:) Thanks ofnuts, I went ahead with a database.

> 
If you want to keep the file, you can do things differently: 

[LIST]
[*]grep the whole file for all records about the client
[*]check if the last one is a failure.
[*]when things turn out OK, append a "success" line.
[/LIST]
this way you never need to rewrite the whole file (appending at the end is trivial). You still read the whole file but you are already doing that. And you keep a complete history of the failures.
Thanks.

---

