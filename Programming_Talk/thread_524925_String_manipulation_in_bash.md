---
title: "String manipulation in bash"
date: 2007-08-13
forum: Programming Talk
---

### Post by lsutiger on 2007-08-13
Hi There! New to bash, old to programming. 
What I need to do is take the date and do some string manipulation. Can someone point me in the right direction?
There is nill to none info on this forum about this subject.
Thanx!

---

### Post by Gagle on 2007-08-13
Well, to start off, I would recommend to take a look at this website.  I guarantee  you it's not a waste of time :  [http://linuxcommand.org](http://linuxcommand.org)

Now, issuing the command : ```
/sbin/hwclock
```
or ```
date
```
in the terminal will print the complete date on the screen. 
You could use its output but maybe there is a more clever way.  

HIH,

Gagle

---

### Post by ghostdog74 on 2007-08-13
check your man page of the date command. it has various options that you can use to format the output of the date to your needs..

---

### Post by Mr. C. on 2007-08-14
How about more specifics on what you are trying to accomplish?

MrC

---

### Post by lsutiger on 2007-08-14
I am switching over my office computer to ubuntu. I have quite a few dos batch programs that run while I am away from the desk. One of these batch files calls a TAS (very old database/scripting software) program. In the program, it gets the date, subtracts one day ( this is processing the company's reports from the previous day) and creates a text string that is passed to zip.
IE - todays zip file would be named Aug1307.zip
I've got all of the other processing ( printing the reports, zipping up each individual location's reports, dumping the correct reports to the correct servers, etc). All now that is left, on that project, is creating a zip file that is tagged with a date name.

But I have plenty, plenty to do :D

PS - I have O'Reilly's "Learning the bash Shell" and Apress' "From Bash to Z Shell" and "Shell Scriptind Recipes", so I am learning. I also spent a few hours over at linuxcommand.org.

Thanx in advance for any input

---

### Post by batrick on 2007-08-14
```
date --date=yesterday +%b%d%y
```

Use that command when naming the file.

EDIT: Fixed it so it shows yesterday's date.

---

### Post by winch on 2007-08-14
Note that date replaces the sequences it recognises in the format string with the correct values then outputs the string. You can get the zip filename in one shot.

```

date --date=yesterday +"%b%d%y.zip"

```

I mention that as it isn't obvious after reading the man page and can result in cleaner code.

---

### Post by lsutiger on 2007-08-14
I appreciate all of the help so far! But I am having hell with assignment and filenaming.

When I try something like:```
tempdate= date --date=yesterday +"%b%d%y.zip"
```
it returns (prints) the correct filename
When I try to echo $tempdate I get nothing
When I try to pass it to zip, it looks like it is doing something, but does not create a new file (adding filename (storing 0%))


Sorry for the newbish stuff...

---

### Post by Mr. C. on 2007-08-14
```
tempdate=$(date --date=yesterday +"%b%d%y.zip")
```

MrC

---

### Post by lsutiger on 2007-08-14
Ahhh...thank you very much...it's always semantics !

---

### Post by batrick on 2007-08-14
```
tempdate=$(date --date=yesterday +"%b%d%y.zip")
```

Can be this as well:

```
tempdate=$(date --date=yesterday +%b%d%y).zip
```

The quotations in the earlier command were not necessary. Note that there can be no whitespace surrounding the equals sign. The space in your first try caused tempdate to be initialized to nothing, and then date was executed (which is why you didn't see any errors but *did* see the output of date on your screen). Also note that you can have .zip outside $(date ...), bash automatically concatenates the strings.

$(...) and `...` (notice these are backticks, not single quotes) both cause ... to be executed and the output of these commands to be substituted.

HTH

---

