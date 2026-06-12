---
title: "simple interactive script- how do i?"
date: 2015-01-16
forum: Programming Talk
---

### Post by cris7 on 2015-01-16
I need some help figuring out how to write a little renaming script that others can interact with.

********************************************************************************************************************
After clicking a file to open it, I need it to open a terminal and ask the following prompt:
[INDENT]**Enter the portion of the file name to be changed:**
[/INDENT]

I need it to **echo** that answer back.  

Then that answer will need to replace [COLOR=#ff0000]AAA[/COLOR] in the command (in red below) at the end of this script.

Then I need it to ask the following prompt:

[INDENT]**Enter what you would like to change that portion of the name to:**
[/INDENT]

I need it to **echo** that answer back.  

Then that answer will need to replace [COLOR=#ff0000]BBB[/COLOR] in the command (in red below) at the end of this script.

Then I need it to ask the following prompt:[INDENT][B]
Confirm that you would like to replace (insert [COLOR=#ff0000]AAA[/COLOR] here) with (insert [COLOR=#ff0000]BBB[/COLOR] here) [y/n]: [/B]
[/INDENT]

Ideally it would take y, Y, yes, YES, as well as n, N, no NO for answers, but that isn't necessary.

If they answer yes, do the following:[INDENT][COLOR=#ff0000]
rename 's/AAA/BBB/g' *[/COLOR]            ##need to modify this command so AAA=1st answer and BBB=2nd answer
[/INDENT]

If they answer no, end the script and close the terminal window.
********************************************************************************************************************

Any help would be appreciated.

Thanks!

---

### Post by TheFu on 2015-01-17
[http://www.tldp.org/LDP/abs/html/](http://www.tldp.org/LDP/abs/html/)  there are thousands of examples of this type of thing on the internet.
What have you tried?
Can you post the current code?
Really, that link above has examples for almost anything people want to accomplish in bash.
*I won't hand you a fish, but I'm very willing to help you learn to fish for yourself.*

---

### Post by Bucky Ball on 2015-01-17
*Thread moved to **Programming Talk**.*

Just curious, is this an assignment you've been set for study?

---

### Post by whitesmith on 2015-01-17
Another homework assignment, eh? How can you possibly learn Linux by asking others to do your work for you?

---

### Post by Node_Star on 2015-01-18
What language do you want to use?

---

### Post by Bucky Ball on 2015-01-18
> **Node_Star said:**
> What language do you want to use?

Before going much further with this, please wait until the OP answers the question I posed in my last post:

[QUOTE=Bucky Ball]Just curious, is this an assignment you've been set for study? [/QUOTE]

Please be aware of this, from the forum [guide]("http://ubuntuforums.org/showthread.php?t=2158945"):

> While we are happy to serve as a resource for hints and for asking questions when you get stuck and need a little help, **the Ubuntu Forums is not a homework service**. Please do not post your homework assignments expecting someone else to do it for you. Any such threads will either be jailed or closed, and warnings or infractions may be issued.

Thanks.

---

### Post by cris7 on 2015-01-19
This is something I do manually on a weekly basis, just trying to save some time.  I've tried researching this, but as I'm still somewhat of a novice I don't know what the best way to go about this is.  I'm using Xubuntu 12.04, I believe bash is the language I need.

I'm not trying to be lazy here at all, I've spent a few hours over the last year trying to understand how to get an interactive prompt, but it's been time that's broken up and I don't know the best way to go about looking the information up.  A lot of the answers I've found on how to do things have been by searching these forums and looking at the answers others have given, occasionally asking questions.  If that time spent is not good enough for you to respond then that's ok, but I'm hoping someone will see this and have no problem passing along some information to a guy who's kinda stuck.  Not everyone who needs to use code has the time to study all of it.

If you can't post here to ask for help, I guess I misunderstood what these forums are for.  Is this just a place to tell folks to figure things out themselves, or is it a place to help folks out?

---

### Post by TheFu on 2015-01-19
I want to help you learn to help yourself.  I prefer to see the prior effort (i.e. the code) to see where you are stuck.

The way you asked seemed exactly like what a college Linux 101 class student would have asked, as they get this type of homework all the time.

To read a value from a shell script, use "read".  That should be a built-in command to bash.  BTW, that is covered in that link I previously provided. [http://www.tldp.org/LDP/abs/html/internal.html#EX36](http://www.tldp.org/LDP/abs/html/internal.html#EX36)  ... took 10 sec (literally) to find a simple example, but my google-fu is strong.

Again, there are thousands, if not millions of examples for this stuff.  If you want to see more examples, any package that you've ever installed on Ubuntu that had interactive questions/answers is an example and the code is on your box today, already.  todo.sh (from Gina T.) and winetricks are two popular scripts you can easily find via search engines that are examples of this as well.

BTW, I applaud trying to save a few seconds with a script like this.

I would write the script NOT to require interactive input - instead just pass the 2 variables on the command prompt as $1 and $2. You can show the rename command, pause, <enter> does it.  cntl-c breaks out.

So - it is best to post some code to get more help.

---

### Post by sudodus on 2015-01-19
Will this help?

```
[COLOR=#0000cd]$ read -p "enter string to be replaced: " old[/COLOR]
enter string to be replaced: [COLOR=#ff0000]aaa[/COLOR]
$ [COLOR=#0000cd]read -p "enter string replacement: " new[/COLOR]
enter string replacement: [COLOR=#ff0000]bbb[/COLOR]
$ [COLOR=#0000cd]echo "$old $new"[/COLOR]
[COLOR=#800080]aaa bbb[/COLOR]
$
```

So use [COLOR=#0000cd]"$old" and "$new[/COLOR]" in your rename command :-)

And there are several good ***tutorials about bash***, that you find easily via the internet. Or you can start with the following links

[https://help.ubuntu.com/community/Beginners/BashScripting](https://help.ubuntu.com/community/Beginners/BashScripting)

[https://help.ubuntu.com/community/CategoryCommandLine](https://help.ubuntu.com/community/CategoryCommandLine)

---

### Post by Pinoy Tux on 2015-01-21
> **cris7 said:**
> ...renaming script that others can interact with.  After clicking a file to open it, I need it to open a terminal and...

Your script may have to include the snippet of code found in [this thread]("http://forums.linuxmint.com/viewtopic.php?f=213&t=80823") that makes sure a terminal window gets opened when you run your renaming script directly from the GUI.  Without the additional code, your script will run headless and you won't be able to interact with it.

HTH.

---

### Post by cris7 on 2015-01-26
Thanks for all the responses.  I was able to follow the given advice, do  a bit of searching and playing, and come up with an almost complete  solution.  Now I just have to research more on the replies that share  how to get it to open in a terminal when clicking the script from the  file browser.

Here's the end code I have:
[INDENT]
#!/bin/bash
#interactive replacement of portions of file names, full directory non-recursive
#created by cris7 on 1/26/15, with help from Ubuntu Forums
#see the following link for further credit: [http://ubuntuforums.org/showthread.php?t=2261147](http://ubuntuforums.org/showthread.php?t=2261147)
read -p "enter string to be replaced: " old
read -p "enter string replacement: " new
echo "..."
echo "..."
echo "replacing: $old"
echo "with: $new"
echo "..."
echo "..."
read -p "This script will make the following changes... (hit enter preview changes)"
echo ""
rename -v -n s/$old/$new/ *
echo ""
echo ""
read -p "Do you want to continue [y/n]" quit
        case $quit in
          n|N) exit;;
        esac
rename s/$old/$new/ *
[/INDENT]

I really appreciate the help from everyone.  Once I'm able to get the "open in terminal" part figured out I'll post the final code, in case someone else needs it later on.

By the way, what are the proper ways to credit folks when doing scripts (see lines 3&4 of script above)?

Thanks again!

---

### Post by TheFu on 2015-01-26
> **cris7 said:**
> By the way, what are the proper ways to credit folks when doing scripts (see lines 3&4 of script above)?

Thanks again!

Depends on how the help was provide (freely or commercial) or whether you "borrowed" code from nontrivial examples and what the license, if any, for the examples is.

I don't care about any credit for something like this.  Every Sunday, I help Linux people at our LUG for 3-5 hrs. Can't keep up with all the people being helped or scripts I've helped them create.

For scripts of any significance, people have a separate file with that information. Often at the end of a README or THANKS file. Look around on github for examples. There must be over a million there. ;)

Here's how I've documented code: [http://blog.jdpfu.com/files/kernel-cleanup.sh](http://blog.jdpfu.com/files/kernel-cleanup.sh)
Having a license is important for anyone coming later. I've been screwed over by someone giving his code to a different company without any license. No license means "all rights reserved", if you ask a lawyer.  If you want other people to build off it - be clear on the license.

---

### Post by Pinoy Tux on 2015-01-26
> **cris7 said:**
> Once I'm able to get the "open in terminal" part figured out...

Somewhere in the link I posted in an earlier reply explains the logic of the code fragment. A refined version is found at the end of that thread.

---

### Post by cris7 on 2015-01-29
> **Pinoy Tux said:**
> Somewhere in the link I posted in an earlier reply explains the logic of the code fragment. A refined version is found at the end of that thread.

Yes, that link had exactly what I needed.  Here's what I have after adding that information:[INDENT]

#!/bin/bash
#fixes filenames for shapefile processing
#created by Cris Jesse on 12/17/14
# if this script was not launched from a terminal, restart it from a terminal
if [[ ! -t 0 && -x /usr/bin/x-terminal-emulator ]]; then
   /usr/bin/x-terminal-emulator -e "bash -c \"$0 $*; read -s -p 'Press enter to continue...'\""
   exit
fi
##rename code below
read -p "enter string to be replaced: " old
read -p "enter string replacement: " new
echo "..."
echo "..."
echo "replacing: $old"
echo "with: $new"
echo "..."
echo "..."
read -p "This script will make the following changes... (hit enter preview changes)"
echo ""
rename -v -n s/$old/$new/ *
echo ""
echo ""
read -p "Do you want to continue [y/n]" quit
        case $quit in
          y|Y)  rename s/$old/$new/ *
n|N) exit;;
        esac
echo "Done"
[/INDENT]

---

### Post by cris7 on 2015-01-29
After reworking this script a little bit:

#!/bin/bash
#fixes filenames for shapefile processing
#created by Cris Jesse on 12/17/14
# if this script was not launched from a terminal, restart it from a terminal
if [[ ! -t 0 && -x /usr/bin/x-terminal-emulator ]]; then
/usr/bin/x-terminal-emulator -e "bash -c \"$0 $*; read -s -p 'Press enter to continue...'\""
exit
fi
##rename code below
          echo "..."
            echo "..."
            read -p "enter string to be replaced: " old
            read -p "enter string replacement: " new
            echo "..."
            echo "..."
            echo "replacing: $old"
            echo "with: $new"
            echo "..."
            echo "..."
            read -p "This script will make the following changes... (hit enter preview changes)"
            echo ""
            echo ""
            rename -v -n s/$old/$new/ *
            echo ""
            echo ""
            read -p "Do you want to continue [y/n]" doRename
            echo "..."
            echo "..."
                case $doRename in
                  y|Y) rename s/$old/$new/ *
                      echo "Done updating file names";;
                  n|N) echo "Discarding changes";;
                  *) echo invalid option, discarding changes;;
                esac

---

### Post by cris7 on 2015-01-29
Thanks again to everyone for your help!

---

### Post by TheFu on 2015-01-29
You know, you don't have to have a separate echo for each line. Multi-line is ok.

---

### Post by cris7 on 2015-01-29
Like this TheFu?:

echo "


"

---

### Post by CantankRus on 2015-01-29
You can also make use of the echo [COLOR="#FF0000"]**-e**[/COLOR] option.
From **man echo**...
> If -e is in effect, the following sequences are recognized:

\\
backslash
\a
alert (BEL)
\b
backspace
\c
produce no further output
\e
escape
\f
form feed
\n
new line
\r
carriage return
\t
horizontal tab
\v
vertical tab

eg
```
echo -e "\n"
echo -e "\v"
echo -e "   replacing: $old \n\twith: $new"
```

---

### Post by cris7 on 2015-01-30
Thanks!

---

