---
title: "I Can't Script; but I Can Dance."
date: 2010-11-20
forum: Programming Talk
---

### Post by tg3793 on 2010-11-20
Good morning everyone (not that time matters on the Internet :-))

I've  searched several sites and have been able to pick up a great deal of  what I need to know on [tldp.org]("http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html")  and Youtube. I was surprised however that I didn't see more examples of  the way _Bruceydk_ was demonstrating it. I find his method 'very'  useful.

> **Brucevdk said:**
> 
PHP Code:
                            [COLOR=#000000] [COLOR=#ff8000]#!/bin/sh 

# nautilus passes every file selected as an argument to this script, what happens 
# here is that it loops through each of the arguments (filenames). 
[/COLOR][COLOR=#007700]for [/COLOR][COLOR=#0000bb]arg[/COLOR][COLOR=#007700]; do 
    [/COLOR][COLOR=#ff8000]# uses the file command to determine the type of file (uses the "magic numbers") 
    # and stores it in a variable called filetype 
    [/COLOR][COLOR=#0000bb]filetype[/COLOR][COLOR=#007700]=`[/COLOR][COLOR=#0000bb]file -i "$arg"[/COLOR][COLOR=#007700]`  

    [/COLOR][COLOR=#ff8000]# -n tests to see if the argument is non empty, if it doesn't match jpeg 
    # the echo would return nothing (i.e. it would be empty and so the condition 
    # would fail). 
    [/COLOR][COLOR=#007700]if [ -[/COLOR][COLOR=#0000bb]n [/COLOR][COLOR=#dd0000]"`echo $filetype | grep -i 'jpeg'`" [/COLOR][COLOR=#007700]]; [/COLOR][COLOR=#0000bb]then 
        [/COLOR][COLOR=#ff8000]# so if the filetype matches jpeg it'll use jpegtran to rotate it 
        [/COLOR][COLOR=#0000bb]jpegtran [/COLOR][COLOR=#007700]-[/COLOR][COLOR=#0000bb]rotate 90 [/COLOR][COLOR=#dd0000]"$arg" [/COLOR][COLOR=#007700]> [/COLOR][COLOR=#0000bb]temp[/COLOR][COLOR=#007700].[/COLOR][COLOR=#0000bb]jpg[/COLOR][COLOR=#007700]; 
        [/COLOR][COLOR=#0000bb]mv temp[/COLOR][COLOR=#007700].[/COLOR][COLOR=#0000bb]jpg [/COLOR][COLOR=#dd0000]"$arg" 
    [/COLOR][COLOR=#007700]else 
        [/COLOR][COLOR=#ff8000]# if it can't determine if the file is a jpeg it uses convert from 
        # imagemagick to manipulate it, which is a bit strange because it might 
        # aswell be a text file (ASCII text). 
        [/COLOR][COLOR=#0000bb]convert [/COLOR][COLOR=#007700]-[/COLOR][COLOR=#0000bb]rotate 90 [/COLOR][COLOR=#dd0000]"$arg" "$arg" 
    [/COLOR][COLOR=#0000bb]fi 
done  [/COLOR][/COLOR]


And with his example in mind I'd like to post a script that I've  been playing around and editing and ask a specific question or two about  it. Here is the script:

#!/bin/bash
while [[ -n "$1" ]]; do
    #if a file and not a dir
    if [[ -f "$1" ]]; then
        [COLOR=Blue]#the images that I copy from my cell phone don't have exif headers
        #so I am using the -mkexif switch first to match the exif information
        #to the "created date" in the .jpg file. 
        jhead -mkexif "$1"[/COLOR]

        #by default, jpegtran will only copy some
        # Exif data, so we'll specify "all"
        jpegtran -rotate 270 -copy all -outfile "$1" "$1"

        [COLOR=Blue]#Then the next line uses the -ft switch which will match the "modified date" 
        #using the exif date and time previously matched from the first line
        #of this script.
        jhead -ft "$1"[/COLOR]
        
        #clear rotation/orientation tag so that
                # some viewers (e.g. Eye of GNOME) 
                # won't be fooled
        jhead -norot "$1"
    fi
    shift
done

~  ~ ~ ~ ~ ~ ~ ~ ~ ~ ~ ~ ~ ~ ~ ~ ~ ~ ~ ~ ~ ~ ~ ~ ~ ~ ~ ~ ~ ~ ~ ~ ~ ~ ~ ~ 
Ok;  what I'm curios about is the **[COLOR=SeaGreen]"[COLOR=#000000][COLOR=#007700]for [/COLOR][COLOR=#0000bb]arg[/COLOR][COLOR=#007700]; do[/COLOR][/COLOR]"[/COLOR]**  in the first script compared to the "**[COLOR=SeaGreen]while [[  -n "$1" ]]; do[/COLOR]**" in the second script. I'm still quite new to  this but from what I can tell isn't this two ways of doing the same  thing? And 'if' I am correct could someone explain to me if there is a  benefit of one way versus the other.

I know that one is scripting for "sh" and the other for "BASH". But again which way would be better to do it (bring in files selected) and why.
~ ~ ~ ~ ~ ~ ~ ~ ~ ~ ~ ~ ~ ~ ~ ~ ~  ~ ~ ~ ~ ~ ~ ~ ~ ~ ~ ~ ~ ~ ~ ~ ~ ~ ~ ~

---

### Post by saulgoode on 2010-11-21
> **tg3793 said:**
> ... could someone explain to me if there is a  benefit of one way versus the other.
The 'while..shift..done' approach makes it easier to process switches that employ parameters (wherein you need to process more than one argument during each pass through the loop).

For example, consider how you might handle including a '--log filename' option amongst your list of files. Or a '--date month day year' option.

---

