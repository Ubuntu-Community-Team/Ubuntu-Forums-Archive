---
title: "zenity --file-selection"
date: 2011-01-16
forum: Programming Talk
---

### Post by frrobert on 2011-01-16
I am using Ubuntu 10.04 and zenity 2.30.0.

I don't know if I found a bug or not.

If I use zenity --file-selection the exit code is 0 no matter if I hit ok or cancel rather then 0 for ok and 1 for cancel.  

I was able to work around it since cancel returns an empty string for file selection.

Anyone else seen the same behavior?

---

### Post by geirha on 2011-01-17
I'm unable to reproduce it
```

$ zenity --file-selection; echo $? # Hit Cancel
1
$ zenity --file-selection; echo $? # Selected file and hit OK
/tmp/testfile.txt
0

```

How exactly are you using it in your script?

---

### Post by frrobert on 2011-01-17
My own stupid mistake

My code was out of order
```
step2=$(zenity  --file-selection --title="Select Directory that contains JPEGS" --directory --filename=$HOME/)
echo "$step2"
step2ret=$?
```

Instead of 

```
step2=$(zenity  --file-selection --title="Select Directory that contains JPEGS" --directory --filename=$HOME/)
step2ret=$?
echo "$Step2
```"

So the variable was storing the exit code of the echo rather then the dialog box.

---

### Post by geirha on 2011-01-17
Yeah, that explains it. Though, why aren't you just testing the exit status right away?

---

### Post by frrobert on 2011-01-17
I will in real life.  

I haven't used zenity before and I was just playing around with it yesterday.  I decided to take some of my shell scripts and put gui front ends on them and was looking at how zenity worked.

---

