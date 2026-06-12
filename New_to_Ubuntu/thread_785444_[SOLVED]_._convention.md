---
title: "[SOLVED] ./ convention?"
date: 2008-05-07
forum: New to Ubuntu
---

### Post by H.Callahan on 2008-05-07
I have noticed that in a number of suggestions given by folks that seem to be pretty Linux savvy, that they use the convention of sticking a ./ before a filespec for a file that is in their current working directory.  For example to move a file from your home directory to the desktop, one might be told to enter this in the terminal:
```
mv ./mysong.mp3 ~/Desktop
```
Other than 2 extra keystrokes, what is the difference between the above and:
```
mv mysong.mp3 ~/Desktop
```
(In both instances I am assuming that the current working directory is where the file *mysong.mp3* is located.)

---

### Post by tacutu on 2008-05-07
none, really!

---

### Post by Monicker on 2008-05-07
The only time you should need to use ./ for a file in your current directory is if you are trying to execute it.  By default your current directory is not part of your path of executable files, for security reasons.

---

### Post by H.Callahan on 2008-05-07
I guess the question changes from "what" to "why", then.

(Thanks)

---------EDIT--------
> **Monicker said:**
> The only time you should need to use ./ for a file in your current directory is if you are trying to execute it.  By default your current directory is not part of your path of executable files, for security reasons.

Then Linux differs from Windows in that it does not search the current directory first (or at all?) when trying to execute a file?

---

### Post by Monicker on 2008-05-07
> **H.Callahan said:**
> I guess the question changes from "what" to "why", then.

(Thanks)


Then Linux differs from Windows in that it does not search the current directory first (or at all?) when trying to execute a file?

Correct.  Below is an excerpt which sums up the reasoning for that.




[I]**Always specify the full path; don't place the current directory in the PATH**

Specifying the full path to commands, binaries or other scripts limits the risk that a Trojan object could be inserted somewhere higher in the path. You also risk Trojans by placing the current directory in the path, especially if that directory is a home directory containing other scripts and non-system binaries.

You should only execute programs you trust from standard system directories. The safest way is not to trust the current PATH variable but rather to specify your own explicit PATH in the script. [/I]

---

### Post by Joeb454 on 2008-05-07
If you are running from a terminal then yes.

However because I do a fair bit of programming, I ended up adding the current directory to my path anyway :) Even though I shouldn't...

---

### Post by H.Callahan on 2008-05-07
That is good information to know.  

From what you said, then, I imply that if I did add the current subdirectory to the path, that it will also search the parent directories of the current subdirectory as well?  That would also be different than Windows.

---

### Post by bingoUV on 2008-05-07
> **H.Callahan said:**
> That is good information to know.  

From what you said, then, I imply that if I did add the current subdirectory to the path, that it will also search the parent directories of the current subdirectory as well?  That would also be different than Windows.

If I understand you correctly, no. To illustrate , if only /a/b/c/d is in path, and you type in an executable file name that is in c, you get an error "command not found"

---

### Post by H.Callahan on 2008-05-07
> **Monicker said:**
> *Specifying the full path to commands, binaries or other scripts limits the risk that a Trojan object could be inserted somewhere higher in the path.*

Then why would a Trojan object "inserted somewhere higher in the path" be a problem (other than the obvious fact that one would not want a Trojan object anywhere in the entire file system, of course [-X)

---

### Post by bingoUV on 2008-05-07
> **H.Callahan said:**
> Then why would a Trojan object &quot;inserted somewhere higher in the path&quot; be a problem (other than the obvious fact that one would not want a Trojan object anywhere in the entire file system, of course [-X)

The PATH variable has many directories separated by :. The first directory is searched first, and if executable of the name is found, it is executed. Otherwise next directory in the PATH variable is inspected. And so on. 

Higher in the path means somewhere in the PATH before the intended directory. Which is why putting . in the beginning of PATH is very risky (if not because of maliciously placed trojans, our own scripts might harm us).

---

### Post by H.Callahan on 2008-05-07
Ok, that clears it up.

Thanks all!

---

