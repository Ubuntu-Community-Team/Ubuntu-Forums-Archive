---
title: "Bash and file lists"
date: 2010-03-06
forum: Programming Talk
---

### Post by Fibonacci on 2010-03-06
Hello.

I have a list of files on which I want to perform certain operations (say, moving them somewhere else). This list is stored on a plain-text file, one filename per line, along with some other files which I don't want to touch. So my script would go somewhat like this:
```
for i in $(grep 'jpg' file_list.txt); do mv $i /some/other/dir; done
```
This works fine, except if some of the filenames on file_list.txt contain spaces - in that case, each of the whitespace-delimited tokens is taken as a possible value for $i. So for example, if file_list.txt contains the following:
```
Photo 1.jpg
Photo 2.jpg
```
then i takes the values "Photo", "1.jpg", and "2.jpg", which is NOT what I want.

How can I modify the script so that each line is taken as a single argument?

---

### Post by kaibob on 2010-03-06
There are a number of methods that will work. For example, 

```
grep 'jpg' file_list.txt | while read file ; do mv "$file" /target/directory ; done
```

Your command can be modified to work by changing the Internal Field Separator to a newline:

```
IFS=$'\n' ; for i in $(grep 'jpg' file_list.txt) ; do mv $i /target/directory ; done
```

---

### Post by Fibonacci on 2010-03-06
> **kaibob said:**
> Your command can be modified to work by changing the Internal Field Separator to a newline:

```
IFS=$'\n' ; for i in $(grep 'jpg' file_list.txt) ; do mv $i /target/directory ; done
```

That was EXACTLY what I was looking for. Thank you very much!

---

