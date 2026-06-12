---
title: "Bash characters"
date: 2008-10-21
forum: New to Ubuntu
---

### Post by cosmocrazy on 2008-10-21
I recently wanted to create a tar archive from a few images (from a book) on my desktop. But when I tried, it didn't work.

```
$ ls | grep -E 4[1-9]
432-433.jpg
434-435.jpg
436-437.jpg
438-439.jpg

$ tar -cvf pages.tar | ls | grep -E 4[1-9] 
tar: Cowardly refusing to create an empty archive
432-433.jpg
434-435.jpg
436-437.jpg
438-439.jpg

$ ls | grep -E 4[1-9] | tar -cvf pages.tar
tar: Cowardly refusing to create an empty archive
```

I searched on Google a few times and found that this worked:

```
$ tar -cvf pages.tar `ls | grep -E 4[1-9]`
432-433.jpg
434-435.jpg
436-437.jpg
438-439.jpg

$ tar -tvf pages.tar
-rwx------ Administrators/None 3872024 2008-10-11 18:07 432-433.jpg
-rwx------ Administrators/None 3638726 2008-10-11 18:07 434-435.jpg
-rwx------ Administrators/None 4154847 2008-10-11 18:12 436-437.jpg
-rwx------ Administrators/None 4126488 2008-10-11 18:12 438-439.jpg

```

"Ok..." I thought. "What does the ` character do?" 

I've never had to use that character before...so I'm not sure what it does. Could someone enlighten me?

---

### Post by Dr Small on 2008-10-21
The "`" character is executing a command. In order for tar to collect the files that you are trying to name, it has to be executed as a command.

In your first example, you were attempting to pipe tar into ls and pipe that result into grep. That's why tar was exiting with an error.

---

### Post by Dr Small on 2008-10-21
Also, a simple way to do it, would have been using variables like this:
```
FILES=`ls | grep -E 4[1-9]`
tar -cvf pages.tar $FILES
```

---

### Post by cosmocrazy on 2008-10-21
Oh, cool, I learned how to use variables and the ` character in one post!

But I still think the ` character is weird. Is there another real world example where you would use it?

---

### Post by drubin on 2008-10-21
` this is called the backtick.

Might help you if you ever need to search for it.

---

### Post by billgoldberg on 2008-10-21
> **drubin said:**
> ` this is called the backtick.

Might help you if you ever need to search for it.

Actually, it's called the grave accent.

*(ubiquity is great for stuff like this)*

---

### Post by drubin on 2008-10-21
> **billgoldberg said:**
> Actually, it's called the grave accent.

*(ubiquity is great for stuff like this)*

I would love to know where you can look this stuff up I just have this in my head it is a backtick or backtic. But tried to google it  cant seem to find it. [http://en.wikipedia.org/wiki/Grave_accent](http://en.wikipedia.org/wiki/Grave_accent) I assumed that was when inconjunction with A E I O U :) but on its own was backtick

---

### Post by Sarmacid on 2008-10-21
I use this character for assigning command results to variables in bash scritps.

```
SNORT=`which snort`
```

You can play around with it on the console doing

```
echo `ls`
```

Or with any command you want.

---

### Post by cosmocrazy on 2008-10-21
Interesting! I'll play around with it.

---

