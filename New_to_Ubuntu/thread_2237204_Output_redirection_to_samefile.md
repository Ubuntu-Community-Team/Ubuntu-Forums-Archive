---
title: "Output redirection to samefile"
date: 2014-07-31
forum: New to Ubuntu
---

### Post by ric_Poirier on 2014-07-31
Hi,

I am currently studying the "**>**" and "**>>**" tools for output redirection. I have a file, **eleves.txt**, in which some lines a repeated. My goal is to sort them out. For this, I want to use the **sort** command. In a terminal, I have written:
```
sort eleves.txt > eleves.txt
```
Now I know that, using the "**>**" tool for output redirection, if the file already exists, it will be overwritten. My problem is that when I type
```
cat eleves.txt
```
in the terminal (after having sorted the file a redirected the output to the same file), all data from **eleves.txt** seems to have disapeared. I was expecting the files to have all its lines sorted instead. Please help me understand this behaviour...

---

### Post by Impavidus on 2014-07-31
>> will append the sorted file, so **sort eleves.txt >>eleves.txt** leads to a sorted list of (pupils?).
> will truncate the file to zero and then write the output. It appears that the shell first truncates the file to make it ready for writing and only then starts the sort command, which therefore encounters an empty file, which after sorting still is an empty file. You could try first storing it as a temporary file under a different name.

If you want to delete repeated lines, have a look at the uniq command. See **man uniq**.```
sort input | uniq >output
```

---

### Post by ric_Poirier on 2014-07-31
Okay, thanks for the reply!

---

