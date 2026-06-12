---
title: "Storing each item in a list"
date: 2011-07-11
forum: Programming Talk
---

### Post by msjones on 2011-07-11
Hi,

I am planning a script to automate a task I do quite often. I would like to know if what I want to do is possible, and if so how I can do it.

I will be running the script in specific directories. These directories will contain no more than 10 files, and from those 10 I will only be looking for one file extension.

What I want to do is then I run the ls command and pipe it to grep *.txt is take each item from that list and pass it to case like this:

```
case $FILES in
	1)	file1.txt ;;
	2)	file2.txt ;;
```

How would I get case to expand if there is more than 2 files? Am I going down the wrong path for this?

Thanks in advance for any help, its greatly appreciated.

---

### Post by PaulM1985 on 2011-07-11
I think you might want:

ls | grep .[FILETYPE]$

Paul

---

### Post by msjones on 2011-07-11
YES! that seems to give me the output I am after.

Thank you very much for that Paul!

---

