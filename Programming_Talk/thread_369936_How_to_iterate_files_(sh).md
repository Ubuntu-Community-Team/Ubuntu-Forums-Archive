---
title: "How to iterate files (sh)"
date: 2007-02-25
forum: Programming Talk
---

### Post by iraiscoming223 on 2007-02-25
Hello there! I made a simple script to copy files to my mobile. Everything works fine: I just run the script on a file and it will be sent to my phone. Now I'm looking forward to "extend" the script in order to select multiple files.
This is the script for one file:
```
#!/bin/bash
#created by iraiscoming223
foo=`gksudo -u root -k -m "Hi Marco. Enter your password to access your Nokia N70" /bin/echo "Do you have root access?"`
if sudo obexftp -u 1 -c 'E:' -p "$*"
	then zenity --info --title "Fatto" --text "Files copied succesfully!"
	exit 0;
else
	zenity --error --title "Sorry Marco" --text "Error occured"
	exit 1;
fi
```
Of course if I want to move more then one file I need to select them one by one... How can I repeat ' -p "$*" ' for all the files? Or even all the command... Thank you in advance!

---

### Post by po0f on 2007-02-25
iraiscoming223,

```
[font="Courier New"]#!/bin/bash

# root user ID is 0, test for it
if [[ $UID -ne 0 ]]; then
    echo -E "Root access required, quitting."
    exit 1
fi

# loop through files
for file in "$@"; do
    # test to see if it's a regular file
    if [[ ! -f $file ]]; then
        echo "File \"$file\" is not a regular file, skipping"
        continue
    # it appears to be a regular file, process it
    else
        echo "File \"$file\" appears valid, copying"
        # add any other commands here
    fi
done[/font]
```

This is a command-line only script; if you want the fancy-shmancy Zenity dialogs, you'll have to add them.  ;)

---

### Post by iraiscoming223 on 2007-02-25
Wow! Thank you!! Ok, I'm going to add zenity, if necessary...
By the way... Do you know how to use zenity with the percentual bar in an application such as an ftp? I mean monitoring the moving of a file second after second... Is so difficult?!

---

### Post by iraiscoming223 on 2007-02-25
As long as I'm here, which is the way to assign a value to a var? For example, want to save a string (filename) into a var.. 
this is the way?```
foo = "$@"
```
And what about an array?```
foo[0] = "&@"
```

Is there any good guide about bash programming so I won't ask those useless questions around the forum?! :mrgreen: 
Thank you so much! ;)

---

### Post by po0f on 2007-02-25
iraiscoming223,

I've never had to use an array so far in my scripting so I couldn't tell you how to use it.  And I've never used Zenity before, so I don't know if it has a progress bar or not.

I will tell you about the [Advanced Bash Scripting](http://tldp.org/LDP/abs/html/) guide though.  This is *the* most informative guide I've read on Bash.  I haven't bought a book on the subject; but then again, with this guide, I haven't had to.  ;)  All of my Bash questions have been answered with this guide.  It's also available in the repos for offline browsing if you want to install it.

[quote=iraiscoming223]... so I won't ask those useless questions around the forum?! ...[/quote]

You're questions aren't useless; if you want to know something, ask!

And just as a side note, the $@ variable is "special" in Bash; it refers to all of the arguments passed to the script.  It's why I threw the file test in the script I posted above.

If you have any more questions, just ask away.  If I know the answer I'll post back.

---

