---
title: "How-to -- Nautilus Scripts"
date: 2008-04-26
forum: Outdated Tutorials &amp; Tips
---

### Post by Bodsda on 2008-04-26
Nautilus scripts allow you to preform many tasks just by right clicking and selecting to run a script, scripts can be very handy if you don't want to have to got to the terminal and type in all this obscure stuff to convert a file in ffmpeg, you could just write it once in a script then never have to write it again.

below i am going to show you how to write a script for use in nautilus.



Ok, so a script to chmod 777 any file/folder you run this script on
first we start by opening a text editor vi/emacs/gedit

Whenever writing a bash script (a script using bash (terminal) commands)
we start the file like
```
#!/bin/bash
```

this tells the computer what language your script is in.

now the main difficulty (well only real difficulty) in writing simple bash scripts is how do we tell the computer to act upon the file we are clicking on. 
$@  is the answer. or i believe $? can be used as well (but im not sure)

so if we were to chmod a file called blah in our home directory we would use
```
sudo chmod 777 /home/bod/blah
```

but now we have another problem -- if i upload my scripts they wont work for other people because they may not have a user called bod. so we need to find a way of getting the users name before the script does its buissness.
now we could use '~' but i prefer to use variables

the command 
```
whoami
```
will print the username if run in a terminal.
so we use this code to store the output of 'whoami' into avariable
```
userName=$(whoami)
```
now for those of you with little or no bash/programming knowledge 
that piece of code basically has added the output of 'whoami' into the variable $userName  so when we type $userName the script will substitute it for the contents of the variable.

so are script should now look like this 
```
#!bin/bash

userName=$whoami
```
now we can add the chmod stuff

```
#!bin/bash

userName=$(whoami)
gksudo chmod 777 ./$@

```

now this will work but with 1 problem, when you use it first time its fine but the second time wont work because sudo/gksudo has a 5/10/15 (cant remember which) timer on it so will not show up aainduring that period, so we needto reset the time before we run the gksudo
the command to reset the timer is sudo -k
so when we add this to the script it should look like
```
#!bin/bash

userName=$(whoami)
sudo -k
gksudo chmod 777 ./$@

```
Thats it thats your first nautilus script,now save it to
/home/user/.gnome2/nautilus-scripts/
then got to terminal and type
```
sudo chmod 777 /home/'user'/.gnome2/nautilus-scripts/*

```
then give your script a try

You can make a script do almost anything -- just remember the $@ and you will be overwhelmed in scripts in no time 

Hope this helped

---

### Post by Ron_ on 2011-01-08
This was very helpful.  I had to dig around a little to figure out how to write my first script.  The following works for me.  I named it "toggle RW", saved it in /home/xxx/.gnome2/nautilus-scripts and made it executable.

```
#!/bin/bash
# Change read/write permissions on selected files in Nautilus
#
# $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS is an automatic variable containing newline-delimited paths for selected files.
# IFS ensures that newlines are identified as file separators.
# FILENAME is defined by my "for" statement as each element in the selected files array.
# if [ -w ... tests whether I have write-access to each selected file.
# chmod -w ... removes write-access for all users.  Note the difference in the use of the minus sign from above.
# chmod +w ... adds write-access for all users.
#
IFS=$'\n'
for FILENAME in $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS
do
 if [ -w "$FILENAME" ]; then
   chmod -w "$FILENAME"
 else
   chmod +w "$FILENAME"
 fi
done
```

---

### Post by crf112 on 2011-03-06
I wrote a script that used zenity to display some formatted output.  Since zenity uses a proportional space font, my formatted output didn't display as expected.  I tried for several hours to make zenity use a fixed space font, but finally gave up.  I decided to see if I could use gnome-terminal instead.  

The following is a script I used to prove that it would work as I wanted.  I inserted some comments to, hopefully, make it useful as a sample script.  

The trick that makes it work is that the script gets called twice.  The first time it is called by nautilus.  During this execution it calls gnome-terminal and uses the --command option to call itself.  On the second execution it is running in a terminal session and does the real work.

```
#!/bin/bash
#
# Version: 0.1
#
# Install in your Nautilus scripts directory.
#
# This script shows you how to run a nautilus-script as a gnome-terminal command.
#
# Prior to using this script, you MUST create a gnome-terminal profile named "HoldOpen"
#  1) open a gnome-terminal sessions
#  2) click on Edit ... Profiles ... New
#  3) in "Profile name:" enter "HoldOpen"
#  4) click on the "Title and Command" tab
#  5) set "When command exits:" to "Hold the terminal open"
#  6) make other changes to the profile as desired
#         I turn off "Show menubar ..." on the "General" tab
#         and turn on "Unlimited" on the "Scrolling" tab
#

# You should not have to change the next six lines
if [[ ! $PassTwo ]]
then
    export PassTwo="TRUE"
    gnome-terminal --window-with-profile=HoldOpen --title=${0##*/} --execute "$0" "$@"
    exit
fi

# Replace the following with your code.

# This shows you the current working directory.
printf '%s\t%s\n\n' '$PWD' "$PWD"

# Use "for arg" to operate on the arguments one at a time.
printf 'Individual arguments:\n'
for arg
do
    printf '\t%s\n' "$arg"
done

# Use "$@" to pass all the arguments at one time.
printf '\nOutput from ls "$@"\n\n'
ls "$@"
```

---

