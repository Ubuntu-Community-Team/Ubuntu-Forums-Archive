---
title: "Redirecting multiple outputs in bash script"
date: 2007-11-12
forum: Programming Talk
---

### Post by cknight on 2007-11-12
I think this should be easy but I'm rather a bash novice.  I have two commands 'date' and 'cal-3' which I want to pipe to a third command, 'gmessage -file -'. The ideal output would look something like

line1: Mon Nov 12 21:54:05 GMT 2007
line2: blank
line3...etc. 'cal -3' output

I know the syntax of all the commands, but how do I add the output of one command to another and pass that along the pipe to gmessage?  E.g.
```
cal -3|gmessage -file -
```
does some of what I want, but now I want to add the date and blank line to the start of this.  Any ideas?

Or alternatively, does anyone know how to preserve the highlighted day in gmessage?  E.g. on the command line, cal -3 highlights the current day, but this is lost on gmessage.

Thanks!

---

### Post by finer recliner on 2007-11-12
try making a bash file (filename.sh) that looks like this:

```

#!/bin/sh
touch tmp.txt #create an empty temporary text file
date >> tmp.txt #append date command to temp file
cal -3 >> tmp.txt #append cal -3 command to temp file
gmessage -file tmp.txt #run gmessage using your temp file as an argument
rm tmp.txt #delete the temp file

```


i havent run this to make sure it works as expected, but i think its close to what you want.
tweak as necessary.

---

### Post by scorp123 on 2007-11-12
> **cknight said:**
>  but how do I add the output of one command to another and pass that along the pipe to gmessage?  You mean like this? **command2 `execute command1` | command3** ...

Example: ```
ls -al /lib/modules/`uname -r` | more 
``` See how it works? First the command1 inside the ` ` backtick signs (those "backticks" should not be mistaken for ' ' apostrophe signs) is executed. The result is handed over to command2 two which takes the result as argument and then passes the new result over to command3. You can create quite a lot of "chains of commands" that way.

Hope this helped?

---

### Post by scorp123 on 2007-11-12
> **finer recliner said:**
>  try making a bash file (filename.sh) that looks like this: ```

#!/bin/sh
touch tmp.txt #create an empty temporary text file
date >> tmp.txt #append date command to temp file
cal -3 >> tmp.txt #append cal -3 command to temp file
gmessage -file tmp.txt #run gmessage using your temp file as an argument
rm tmp.txt #delete the temp file 
```  Why so complicated? Why not e.g. ```
gmessage -wrap `date; cal -3`
```

EDIT .... ah, I see. With my method I run into ugly formatting problems. I am trying to find a way around this but for the moment I'd have to agree that your method produces the better-looking result :)

---

### Post by geirha on 2007-11-12
You can group the output together like this: 
```
(date;echo;cal -3) | gmessage -file -
```

Edit: Still a bit ugly though, perhaps -font "courier" as well?

---

### Post by cknight on 2007-11-13
> **geirha said:**
> You can group the output together like this: 
```
(date;echo;cal -3) | gmessage -file -
```

Edit: Still a bit ugly though, perhaps -font "courier" as well?

Fantastic.  This is just what I was looking for.  To put the finishing touches on this, we change the font to monospace:
```
 (date;echo;cal -3) | gmessage -file - -font "monospace 8"
```
Thanks again for everyone's replies!

---

### Post by geirha on 2007-11-13
Btw, why not use zenity? ```
zenity --calendar
```

---

### Post by cknight on 2007-11-15
> **geirha said:**
> Btw, why not use zenity? ```
zenity --calendar
```

lol, that's too easy :)  Where's the challenge?  In all seriousness, thanks, I had forgotten that zenity had a calendar option.  It also highlights the current day nicely which is something I wanted.

Too bad you can't configure it more to show multiple months or a year view.  But for a quick and dirty command-line calendar script, not so bad!

---

