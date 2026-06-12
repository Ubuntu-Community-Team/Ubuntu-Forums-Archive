---
title: "Filter color codes from LOG File redirect"
date: 2014-06-23
forum: Programming Talk
---

### Post by octius4u on 2014-06-23
I have a script output in color going to a terminal emulators StdOUT. 
However that standard output is copied into a Log File. Now when I
read that File it contains the color codes that are distracting and confusing.

I would like to know if I could prevent(filter) the color codes from being written
into the Log File.

I have found a similar question that doesn't help me, and I also don't understand.
[https://stackoverflow.com/questions/8720508/bash-tee-remove-color](https://stackoverflow.com/questions/8720508/bash-tee-remove-color)

For a normal redirect to a text file such as "bash myscript.sh > ~/textfile.txt"
I have applied this solution [http://ubuntuforums.org/showthread.php?t=2221789](http://ubuntuforums.org/showthread.php?t=2221789)

```

#!/bin/bash
if [ -t 1 ]; then 
ColRESET="\e[0m"
CommentColor="$ColLiGRAY"
NoticeColor="$ColGREEN"
TitleColor="$ColYELLOW"
WarningColor="$ColRED"
fi
```
Which works very well. Thank you.

I am however still redirecting output to a LogFile, that does still contain all the color codes.

```
    exec >  >(tee -a $LogPath/$LogFileStdOUT)
    exec 2> >(tee -a $LogPath/$LogFileStdERR >&2)
```

Is there a way to combine the above solution here or may apply a solution such as ```
sed 's/\x1b\[[0-9;]*m//g'
```
from [https://superuser.com/questions/380772/removing-ansi-color-codes-from-text-stream](https://superuser.com/questions/380772/removing-ansi-color-codes-from-text-stream) in a similar manner?

Thanks for the help.

---

### Post by ofnuts on 2014-06-23
Normally this is done at the source (see how the ls command works). The script should check if its output goes to a terminal, in which case control characters for color or else are OK, or to something else (file, or pipe to some other process) it which case it should only output plain text. This check is done using [**-t**](http://www.gnu.org/software/bash/manual/bashref.html#Bash-Conditional-Expressions). Create a file with:

```

#! /bin/bash

[[ -t 1 ]] && echo "Outputting control characters"
[[ -t 1 ]] || echo "Not outputting control characters" 

```

And run it with
```

showoutput

```
```

showoutput | more

```

And compare the outputs...

---

### Post by octius4u on 2014-06-23
I have used the **-t** option to control the contents of the color variables that would otherwise remain empty. I do understand the condition being used, but the error logging is a continues output ongoing until the script finishes or error happens. If i understand your advice correctly, it would mean that i have to duplicate all echo or print output in the TRUE or FALSE condition. I would have hoped for modified version of
```
exec 2> >(tee -a $LogPath/$LogFileStdERR >&2)
``` in oder to prevent or filter color codes passing through. Maybe i just don't understand or I need to think outside the box, but I don't see it at the moment.

Could you please explain how you envisioned that implementation.

---

### Post by ofnuts on 2014-06-23
Normally you just conditionally set a bunch of strings variables at the beginning of the script, so that they contain the control characters when printing to console and nothing otherwise. You then insert them in your output string:

```

#! /bin/bash

if [[ -t 1 ]]
then #otherwise left undefined and so defaulting to empty strings
    none="\e[0m"
    red="\e[31m"
    green="\e[32m"
fi

echo -e "Outputting ${red}red${none} and ${green}green${none} text"

```

You can check that when you pipe the output of this to more, the colors disappear.

---

### Post by octius4u on 2014-06-23
ofnuts thanks for the advice, but doesn't work.

My original color code:
```

if [ -t 1 ]; then                                                              ## if stdout is a terminal then COLORS
ColBLACK="\e[1;30m"                                                             ##
ColRED="\e[1;31m"                                                               ##
ColGREEN="\e[1;32m"                                                             ##
ColYELLOW="\e[1;33m"                                                            ##
ColBLUE="\e[1;34m"                                                              ##
ColMAGENTA="\e[1;35m"                                                           ##
ColCYAN="\e[1;36m"                                                              ##
ColLiGRAY="\e[1;37m"                                                            ##
ColDkGRAY="\e[1;90m"                                                            ##
ColLiRED="\e[1;91m"                                                             ##
ColLiGREEN="\e[1;92m"                                                           ##
ColLiYELLOW="\e[1;93m"                                                          ##
ColLiBLUE="\e[1;94m"                                                            ##
ColLiMAGENTA="\e[1;95m"                                                         ##
ColLiCYAN="\e[1;96m"                                                            ##
ColWHITE="\e[1;97m"                                                             ##
# -----------------------------------------                                     ##
ColRESET="\e[0m"                                                                ##
CommentColor="$ColLiGRAY"                                                       ## Color of comments in LIGHT GRAY
NoticeColor="$ColGREEN"                                                         ## Color of important notices in GREEN
TitleColor="$ColYELLOW"                                                         ## Color of Titles and Greetings in YELLOW
WarningColor="$ColRED"                                                          ## Color of Warning or ERRORs in RED
fi                                                                              ##

# StdOUT and StdERR LOG
exec >  >(tee -a $LogPath/$LogFileStdOUT)
exec 2> >(tee -a $LogPath/$LogFileStdERR >&2)

SpecHdd=`parted -l | grep Model --after-context=1`
echo -e $CommentColor"---$NoticeColor HardDrives$CommentColor ----------------------------------------------------------------------"$ColRESET
echo -e "$SpecHdd \n"

```
This code results in color in a terminal eviroment but plain without color when redirected "bash myscript.sh > ~/Desktop/spec.txt",
but LOG File $LogPath/$LogFileStdOUT still contains the color code. I'm guessing it's because it ran in a terminal without a redirection.

Now after your suggestion the code looks like the this:
```

if [[ -t 1 ]]; then
## if [ -t 1 ]; then                                                               ## if stdout is a terminal then COLORS
ColBLACK="\e[1;30m"                                                             ##
ColRED="\e[1;31m"                                                               ##
ColGREEN="\e[1;32m"                                                             ##
ColYELLOW="\e[1;33m"                                                            ##
ColBLUE="\e[1;34m"                                                              ##
ColMAGENTA="\e[1;35m"                                                           ##
ColCYAN="\e[1;36m"                                                              ##
ColLiGRAY="\e[1;37m"                                                            ##
ColDkGRAY="\e[1;90m"                                                            ##
ColLiRED="\e[1;91m"                                                             ##
ColLiGREEN="\e[1;92m"                                                           ##
ColLiYELLOW="\e[1;93m"                                                          ##
ColLiBLUE="\e[1;94m"                                                            ##
ColLiMAGENTA="\e[1;95m"                                                         ##
ColLiCYAN="\e[1;96m"                                                            ##
ColWHITE="\e[1;97m"                                                             ##
# -----------------------------------------                                     ##
ColRESET="\e[0m"                                                                ##
CommentColor="$ColLiGRAY"                                                       ## Color of comments in LIGHT GRAY
NoticeColor="$ColGREEN"                                                         ## Color of important notices in GREEN
TitleColor="$ColYELLOW"                                                         ## Color of Titles and Greetings in YELLOW
WarningColor="$ColRED"                                                          ## Color of Warning or ERRORs in RED
fi                                                                              ##

# StdOUT and StdERR LOG
exec >  >(tee -a $LogPath/$LogFileStdOUT)
exec 2> >(tee -a $LogPath/$LogFileStdERR >&2)

SpecHdd=`parted -l | grep Model --after-context=1`
echo -e ${CommentColor}"---${NoticeColor} HardDrives${CommentColor}  ----------------------------------------------------------------------"${ColRESET}
echo -e "$SpecHdd \n"

```

I don't know why or how it would be different then the original code, but it behaves just the same. Color on the screen. No color in the Spec.txt. Color in the LogFile.txt
What am i doing wrong?

---

### Post by octius4u on 2014-06-23
Maybe it's important to know that the variable definitions such as the color codes are in a function and the Logging is called up its own function. Could the different function separations be responsible?

---

### Post by ofnuts on 2014-06-23
When you do the test at the beginning your output is still to terminal, but later (the "exec" statements) you change that to be a pipe. Then, it looks like you want to have your cake and eat it too, because a single output stream of your script (that goes to "tee") ends up both on the TTY and in the log file (and "tee" is doing the copy). There is no way these two outputs can be different.

IMHO you should replace your use of "exec" by  a "log" function, that produces both a conditionally colored output and a plain output that is directly written to file. That would also allows a bit more functionality in the file output (like time stamps, often useful in logs).

---

### Post by octius4u on 2014-06-24
I'm sorry that I don't understand the "cake" metaphor/reference. After a bit of searching and reading I understand that a log function would write only the specific output that is echoed or printed by the script instead of writing all stdOUT output to script. I NOT am versed enough with sed or awk to know how to do this but I have small understanding of grep and I'd image one could pipe the exec through sed or awk before piping it through tee. Using grep it would be something like this:

```

# This is just an example of how i'd imaging this. I know that this does not work.
exec >  >(grep -v $WarningColor | tee -a $LogPath/$LogFileStdOUT)

```

If grep could print all non-matches like with -v but even in the same line, that would be great, I think. Because it can't i thing sed or awk may be able to do this, I just don't know them well enough.
Tell me please, if I'm totally wrong about this.

```
 
# Imaginary grep filter example
grep '$Red\|$Blue\|$Green' 
```

---

### Post by Vaphell on 2014-06-24
```
#!/bin/bash

exec > >( tee >( sed 's/\x1B\[[0-9;]*[JKmsu]//g' >> stdout.txt ) )

ls --color=always
echo a | grep --color=always .
```

```
$ ./pipes.bash 
[COLOR="#00FF00"]**pipes.bash**[/COLOR]
stdout.txt
**[COLOR="#FF0000"]a[/COLOR]**
$ cat stdout.txt
pipes.bash
stdout.txt
a
```

---

### Post by octius4u on 2014-06-24
Great! Thanks. I'll test it right away.

---

### Post by octius4u on 2014-06-24
:guitar:  [COLOR=#ff0000][SIZE=6][FONT=book antiqua]Awesome![/FONT][/SIZE][/COLOR] :guitar: It works great. Goal achieved! Thanks a whole lot!

---

