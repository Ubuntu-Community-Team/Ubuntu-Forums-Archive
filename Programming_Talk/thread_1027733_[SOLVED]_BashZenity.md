---
title: "[SOLVED] Bash/Zenity"
date: 2009-01-01
forum: Programming Talk
---

### Post by Dale Sexton on 2009-01-01
I'm using this as a test, but the answer is always 'Yes 127'. I thought $? was supposed to equal 0, 1 or -1.

I've tried several different ways to do the if statement, but $? always equals 127. Where am I wrong?

```

#!/bin/bash 
 
zenity --question
if [[ $? == 0 ]] ; then 
   zenity --info --text="Yes $?";
else
   zenity --info --text="No $?";
fi

```

---

### Post by kaibob on 2009-01-01
The script works fine on my computer. Something else is involved.

---

### Post by Gwasanaethau on 2009-01-01
I think the '$?' in the '--text="Yes $?"' is catching the exit status of the 'if […]' block rather than 'zenity' command prior to it. I could be wrong…does this give you a different result?
```
#!/bin/bash 
 
zenity --question
ZENEXIT=$?
if [[ $ZENEXIT == 0 ]] ; then 
   zenity --info --text="Yes $ZENEXIT";
else
   zenity --info --text="No $ZENEXIT";
fi
```

---

### Post by Dale Sexton on 2009-01-01
Thanks,
that's what did it.

---

### Post by Dale Sexton on 2009-01-01
Hmmm... on closer examination, when I click OK, I get 'No 0' and when I click Cancel, I get 'No 1'.

---

### Post by Gwasanaethau on 2009-01-01
Hmm, intriguing…

It works OK here - did you do any cutting-and-pasting, out of interest? If so, you might have forgotten to change a 'No' to a 'Yes'. Other than that I have no idea why that's happening…sorry!

---

### Post by Dale Sexton on 2009-01-01
I've cut and pasted exactly as you have it and also have several variations. They all do the same. I've copied it a couple of times to make sure I got everything. ???

---

### Post by kaibob on 2009-01-01
I'm new to shell scripts, but I don't believe either of those lines of your script should return an exit status 127, which is explained as follows:

Exit Code Number: 127
Meaning: "command not found"
Comments: possible problem with $PATH or a typo

[http://www.museum.state.il.us/ismdepts/library/linuxguides/abs-guide/exitcodes.html](http://www.museum.state.il.us/ismdepts/library/linuxguides/abs-guide/exitcodes.html)

> If a command is not found, the child process created to execute it returns a status of 127. If a command is found but is not executable, the return status is 126.

[http://theory.uwinnipeg.ca/localfiles/infofiles/bash/bashref_43.html](http://theory.uwinnipeg.ca/localfiles/infofiles/bash/bashref_43.html)

Perhaps one of the more knowledgeable members of this forum will have an answer.

---

### Post by Dale Sexton on 2009-01-01
I'm really starting to think I've got a fragged computer.

---

### Post by Dale Sexton on 2009-01-02
After alot of play, here's what worked:

```

#!/bin/bash 
 
zenity --question
# zenity --info --text="$?"
tTest=$?
if [ "$tTest" -eq "0" ] ; then
   zenity --info --text="Yes $tTest";
else
   zenity --info --text="No $tTest";
fi

```

(I still think my computer is fragged if the other codes worked on other computers.)

---

### Post by Dale Sexton on 2009-01-02
127 was the code if $? was put directly into the if statement. Once I used a variable other than $? it gave me the correct code. Not sure why I had to encase the variable in quotations or why I had to use -eq instead of ==.

---

### Post by Dale Sexton on 2009-01-03
I'm wondering if it might be my version of Ubuntu? I'm using 8.04. You guys?

---

### Post by kaibob on 2009-01-03
> **Dale Sexton said:**
> I'm wondering if it might be my version of Ubuntu? I'm using 8.04. You guys?

I'm also running Ubuntu 8.04 and your original script still works fine (see thumbnails).

---

### Post by Dale Sexton on 2009-01-04
[RIGHT][LEFT]Seems I may be limited in programming with this computer.:(



[/LEFT]
[/RIGHT]

---

