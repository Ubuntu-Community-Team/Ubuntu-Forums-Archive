---
title: "Help with AWK/TAR/EMACS problem..."
date: 2013-05-03
forum: New to Ubuntu
---

### Post by poison310 on 2013-05-03
[COLOR=#333333][FONT=arial]Ok, so I need a little help on this.. I have gotten through steps 1 and 2 but am struggling with 3 and havent gotten to 4. Can someone help me with the Code involved here? I am using emacs for a text editor for making the myscript.scr file. [/FONT][/COLOR]
[COLOR=#333333][FONT=Arial]

1.  Under your home directory, create three new directories:  Dubuque, Davenport, and Madison[/FONT][/COLOR]

[COLOR=#333333][FONT=Arial]2.  In the Dubuque Directory, create a text file (called "myinfo.txt") containing your name, permanent address, email address, and phone number.  Use the following pattern:[/FONT][/COLOR]
[COLOR=#333333][FONT=Arial]name[/FONT][/COLOR]
[COLOR=#333333][FONT=Arial]street address[/FONT][/COLOR]
[COLOR=#333333][FONT=Arial]city, state, zip[/FONT][/COLOR]
[COLOR=#333333][FONT=Arial]email address[/FONT][/COLOR]
[COLOR=#333333][FONT=Arial]phone number[/FONT][/COLOR]

[COLOR=#333333][FONT=Arial]3.  In the Davenport directory, create a script (called "myscript.scr") that outputs the date, the contents of the USER environment variable, the contents of the HOSTNAME variable, and the contents of the file in step 2 to a file called "scriptout.txt" in the Madison directory.[/FONT][/COLOR]

[COLOR=#333333][FONT=Arial]4.  Using the "tar" command, archive the contents of the "myinfo.txt", "myscript.scr", and "scriptout.txt" files to a file in your home directory called "yourname_finaloutput.tgz"[/FONT][/COLOR]

---

### Post by poison310 on 2013-05-03
here is what i have so far.... i get wierd error messages too. idont think i am doin gsomethign right

#!/usr/bin/awk -f
{
    printf $0 >>"/myfile.txt"
    printf $0 >"/scriptout.txt"
}
{    
    print $0 > "myfile.txt"
    print $0 > "scriptout.txt"
}
TODAY=$(date)
HOST=$(hostname)
awk=$(awk)
echo "------------------------------"
echo "Date: $TODAY                    Host: $HOST"
echo "------------------------------"
awk '{print;} myfile.txt'

---

### Post by oldos2er on 2013-05-04
```
man tar
``` should point you in the right direction. Good luck.

From the Code of Conduct: While we are happy to serve as a resource for hints and for asking  questions when you get stuck and need a little help, the Ubuntu Forums  is not a homework service. Please do not post your homework assignments  expecting someone else to do it for you. Any such threads will be taken  offline and warnings or infractions may be issued.

---

