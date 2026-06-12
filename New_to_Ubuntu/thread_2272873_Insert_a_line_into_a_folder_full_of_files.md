---
title: "Insert a line into a folder full of files"
date: 2015-04-09
forum: New to Ubuntu
---

### Post by Ubu1son on 2015-04-09
Ive got a folder that has 15 files.

These files dont automatiucally open with a text editor, butI can just choose "open with" and choose text editor, and they open ready to edit.

I want to insert some text into each of the files, say "insertedtext", at the end of each file, and save, leaving the files as is, ie. not changing their type, extension, etc.


Can this be done with a command in terminal, so I dont have to manually open each file with a text editor, paste text, save, close, then repeat 15 times?


Thanks

---

### Post by coldraven on 2015-04-09
The command line append utility is >> so to append "sometext" to the file test.txt you would do this
```
echo "sometext" >> test.txt
```
I'm not sure how you would automate that but you could experiment by copying the files to a different folder. Make sure that you are in the correct folder before running it or you may append the text to the wrong files.

---

### Post by matt_symes on 2015-04-09
Hi

There are a number of ways to accomplish this. This is a method using the bash shell.

First change into the directory

```
cd /path/to/dir/with/files
```

then loop over each file in that directory, appending text.

```
for f in *; do echo "Test to append" >> "$f"; done
```

If you need to insert multiple lines of text..

```
for f in *; do echo -e "Line 1\nLine2\nLine ..." >> "$f"; done
```

You can also use find with echo, printf, herestrings and other tools such as sed..... 

Like i said, there are a number of ways of doing this.

Kind regards

---

### Post by Ubu1son on 2015-04-09
> **matt_symes said:**
> Hi

There are a number of ways to accomplish this. This is a method using the bash shell.

First change into the directory

```
cd /path/to/dir/with/files
```

then loop over each file in that directory, appending text.

```
for f in *; do echo "Test to append" >> "$f"; done
```

If you need to insert multiple lines of text..

```
for f in *; do echo -e "Line 1\nLine2\nLine ..." >> "$f"; done
```

You can also use find with echo, printf, herestrings and other tools such as sed..... 

Like i said, there are a number of ways of doing this.

Kind regards



Thanks, 

Would you be able to just briefly explain those commands by breaking them down, so I can get my head around what they roughly do?

Where do I exactly put in the line I want to insert (  the answer seems obvious, but just want to make sure ), and does it insert it automatically at the end of each file?

---

### Post by Holger_Gehrke on 2015-04-09
> **Ubu1son said:**
> Would you be able to just briefly explain those commands by breaking them down, so I can get my head around what they roughly do?

```

for f in *; do echo "Text to append" >> "$f"; done

```
The 'for f in *; do' and 'done' is a loop. It takes all the files in the current directory (that's what the '*' means, you could give any valid file globbing pattern here or a list of files or a list of patterns) and in each iteration of the loop assigns one filename to the variable f and executes the command(s) between 'do' and 'done'. The 'echo "Text to append"' outputs the text to standard output and the '>> "$f"' redirects the output to the file given by the value of the variable f and appends to that file. **Important:** if you mistype the redirection as '>' you will **overwrite** your file.

---

### Post by Ubu1son on 2015-04-09
Thanks, still a little confusing, but I gave it a test anyway.

After pressing enter, there was no mention of anything happening, it just returned to the prompt.

I checked the folder, there were no extra files, or duplicates etc..  but the original files were appended with the text.

So it did work, not sure if it was supposed to append the original files, or make copies?

---

### Post by Holger_Gehrke on 2015-04-09
> **Ubu1son said:**
> Thanks, still a little confusing, but I gave it a test anyway.
After pressing enter, there was no mention of anything happening, it just returned to the prompt.

Standard Unix behaviour: No News is Good News. If nothing is shown, you can assume everything went well.
> **Ubu1son said:**
> 
I checked the folder, there were no extra files, or duplicates etc..  but the original files were appended with the text.
So it did work, not sure if it was supposed to append the original files, or make copies?
It appended to the original files, just as the code told it to. If you wanted backup copies made, you would have to tell your machine to do so, perhaps like this:
```

for f in *; do cp "$f" "${f%%.*}.bak" ; echo "Text to append" >> "$f"; done

```
The additional 'cp' command copies the original file to a file with the original extension of the filename removed (that's what "${f%%.*} means: take the content of variable f and remove everything after the last period) and replaced with '.bak'.

---

### Post by Ubu1son on 2015-04-10
Thanks all, success :cool:

---

