---
title: "Python - No such file or dictionary"
date: 2014-10-09
forum: Programming Talk
---

### Post by Yozuru on 2014-10-09
Hello ubuntu forums! It has been awhile, I have picked up Python again and I am practicing with files. I can't seem to make my function to work. So here is the goal I am trying to acheive:


 [B]Reading through a file, remove all extra white spaces between words, at the beginning of the line, and between paragraphs. This will

 output(written) into the file called essay_neb.txt.[/B]


*Here a pastebin of my code*: [http://pastebin.com/WWwmSy03](http://pastebin.com/WWwmSy03)

I keep getting "FileNotFoundError: [Errno 2] No such file or directory: 'infile'"

I was hoping to get some input on it if is not to much to ask. Many thanks for giving a browse!

---

### Post by nidzo732 on 2014-10-09
You told open() to look for a file called 'infile' (which doesn't exist).
Try removing the quotes arround 'infile' and 'outfile' in the open() calls. 
You need to pass the actual contents of variables called infile and outfile to open().
 Don't put quotes arround names of variables.

---

### Post by Yozuru on 2014-10-09
> **nidzo732 said:**
> You told open() to look for a file called 'infile' (which doesn't exist).
Try removing the quotes arround 'infile' and 'outfile' in the open() calls. 
You need to pass the actual contents of variables called infile and outfile to open().
 Don't put quotes arround names of variables.


Hello nidzo!

I have just taken in what you just said and change my program. (Helps out a lot! It alive eeek!)

This is a pastebin of my code so far: [http://pastebin.com/Mz8MfD4p]("http://pastebin.com/cQxLtenj") (Updated my pastebin code again)

I was able to make the outfile, however, it returns back just one character out of a whole txt file.

I believe I need to also remove blank lines and between paragraphs, I just have a bit of trouble figuring it out. Again, thank you thank you for the help.

---

### Post by ian-weisser on 2014-10-10
Is this some kind of homework assignment?

---

### Post by Vaphell on 2014-10-10
you write only the very last value of newline variable because the operation is outside the loop.

Also whitespace at the beginning/end of the string can be trivially removed with strip() function

to skip empty lines, look at *continue* or write an if

---

### Post by Yozuru on 2014-10-10
Ahh interesting, I'll give that a shot later and see if I can figure it out. As always, I appreciate it!

@Ian: Yes and no, its not mandatory since I am just trying to get better with the language, but it is homework from a python book I picked up. :) (People might call me ol' fashion for having a book since you can learn anything online nowadays!)

---

