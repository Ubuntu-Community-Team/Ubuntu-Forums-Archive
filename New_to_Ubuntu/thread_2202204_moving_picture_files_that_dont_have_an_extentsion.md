---
title: "moving picture files that dont have an extentsion ?"
date: 2014-01-27
forum: New to Ubuntu
---

### Post by bm143 on 2014-01-27
Hi I was wondering how in CLI I would move multiple image files or any other file of a certail type that have no extension in their name such as    myself.jpeg  ocean.jpeg  These are easy to move because i could go mv *.jpeg to /diectory. How would i move these if they were just called    myself    ocean      I cant use the mv *.jpeg because there is no .jpeg in the name. please help thank you

---

### Post by steeldriver on 2014-01-28
Hello and welcome to the forums

You could use the 'file' command to examine the files' contents and try to determine their type (or mime-type), and then move them if the answer matches 'image'. I'm not sure exactly the best way to write that but something like

```

for f in ~/Desktop/*; do [[ $(file --brief --mime-type "$f") =~ ^image ]] && echo mv -t /path/to/dest/ "$f"; done

```

(the above won't actually do anything - it just 'echoes' what you might want to do)

See the manual page for more info - also I'm pretty sure this has been asked before so if you search for 'mime-type' you will likely find a better answer from someone else

```

man file

```

---

### Post by okanagansage on 2014-01-28
You could add an extension to all the files with a command like:
```
rename -n 's/$/.mp4/' *
```

...and then move them. 

Here's a post from [https://www.linuxquestions.org/questions/showthread.php?p=4135091#post4135091](https://www.linuxquestions.org/questions/showthread.php?p=4135091#post4135091) that explains the command:

> I understand that -n tells rename to show what would be done but not to do it.
- and that s means to substitute the second expression *.mp4* for the first.
- and the * means to match any file - that is to process all flies in the directory

However, the $ as me stumped. I understand that $ in a regular  expression matches the (right hand) end of a string.  In the example at  hand I wish to concatenate .mp4 to the end of the file name, not replace  the last character or characters with .mp4.  

Well wait a minute. I reread the description of $.  Since it matches the **position**  at the end of the string - now that makes sense. The command is  replacing the nothingness following the file name with .mp4 - exactly  what I wished to do.


---

