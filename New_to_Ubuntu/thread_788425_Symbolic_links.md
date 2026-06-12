---
title: "Symbolic links"
date: 2008-05-09
forum: New to Ubuntu
---

### Post by dominik_ap on 2008-05-09
Hello,
I'd like to have content of one directory linked in other directory.

Let's say that I have /home/data/images/wallpapers/ and there i have directories: art, unsorted, linux...

I d like to have images from these directories in /usr/share/wallpapers/ as links.

I tried 
```

sudo ln -s /home/data/images/wallpapers/art /usr/share/wallpapers

```
but it created symlink /usr/share/wallpapers/art -> /home/data/images/wallpapers/art
I wanted to have the content of /home/.../art in /usr/share/wallpapers/


Or help me in other way:
I am using Kubuntu and when user wants different wallpaper, they are listed from /usr/share/wallpapers and from /home/user's_home/.kde/share/wallpapers/ , I want to show him wallpapers from /home/data/images/wallpapers/art linux unsorted and others..
How to do it? Don't you know?


Thank you very much
Dominik Franek

---

### Post by mlentink on 2008-05-09
> **dominik_ap said:**
> 
I tried 
```

sudo ln -s /home/data/images/wallpapers/art /usr/share/wallpapers

```
but it created symlink /usr/share/wallpapers/art -> /home/data/images/wallpapers/art
I wanted to have the content of /home/.../art in /usr/share/wallpapers/


What would happen if your turned the command around?
Like in:
```
sudo ln -s /usr/share/wallpapers /home/data/images/wallpapers/art
```

---

### Post by arvevans on 2008-05-09
Instructions for the "ln" command can be seen by going to a Terminal screen and typing

[INDENT]man ln[/INDENT]

Use your keyboard arrow keys to scroll up and down and hit "q" when ready to exit the man page.

_._

---

### Post by KIAaze on 2008-05-09
```
ln [TARGET] [LINKNAME]
```
And if LINKNAME is a directory, it creates the link inside it with the basename of TARGET.

The correct command would be:
```
sudo ln -s /home/data/images/wallpapers/art /usr/share/wallpapers/art
```
if you want to create a symlink called /usr/share/wallpapers/art to /home/data/images/wallpapers/art.
This means you'll end up with an art directory in /usr/share/wallpapers.

If you want to have the files from the art directory in wallpapers, it's a bit more complex.
Please stand by while I prepare a little shellscript or complex command-line. ;)

edit:
```
ls -1 /home/data/images/wallpapers/art/* | xargs -n1 -I{} sudo ln -s {} /usr/share/wallpapers/ 
```

This should do the trick. :)

_Explanation:_
ls -1 /home/data/images/wallpapers/art/*:
-1: one filename per line

"|": pipe output from one command to another

xargs -n1 -I{} sudo ln -s {} /usr/share/wallpapers/:
-sudo: Well, you want to put stuff in /usr...
-n1: handle input line by line
-I{}: replace {} with input
xargs - build and execute command lines from standard input

---

### Post by dominik_ap on 2008-05-10
> **arvevans said:**
> Re: Symbolic links
Instructions for the "ln" command can be seen by going to a Terminal screen and typing
man ln
Use your keyboard arrow keys to scroll up and down and hit "q" when ready to exit the man page.

Sorry but I was finding a lot in man page of ln, but there wasn't anything what would show the content of direactory in already existing one.

> **KIAaze said:**
> ```
ln [TARGET] [LINKNAME]
```
If you want to have the files from the art directory in wallpapers, it's a bit more complex.
Please stand by while I prepare a little shellscript or complex command-line. ;)

edit:
```
ls -1 /home/data/images/wallpapers/art/* | xargs -n1 -I{} sudo ln -s {} /usr/share/wallpapers/ 
```

This should do the trick. :)


Hey thanks KIAaze it was exactly what I needed. It works, perfect trick.

And now if something changes in directory /home/data/images/wallpapers/art then I have to run this small script again, right?
Do you have any idea how to make any "deamon" or something what will monitor few folders and if something will change will run this script?
do you think cron would do it?


PS: I will use this piece of code in: [http://www.franek.name/index.php/Editing How to list content of few directories in one directory](http://www.franek.name/index.php/Editing How to list content of few directories in one directory) and of course I will add the links to here. Is it ok?

---

### Post by KIAaze on 2008-05-11
> PS: I will use this piece of code in: [http://www.franek.name/index.php/Edi](http://www.franek.name/index.php/Edi)... one directory and of course I will add the links to here. Is it ok? 
No problem.


> And now if something changes in directory /home/data/images/wallpapers/art then I have to run this small script again, right?
Do you have any idea how to make any "deamon" or something what will monitor few folders and if something will change will run this script?
do you think cron would do it?

First of all: It's not a script. It's just a single command line. ;)
Second: If you made a link to a directory, it is not necessary to update the link. However since here you linked to the contents of "art" instead of to "art" itself, yes, it is necessary to add new links.to the new files and therefore run the command again.
(If you just change the files in the art folder (i.e: draw a line on an image for example), this is not necessary.)

Yes, cron would work.
However, since you need root permissions, you would have to do it in the root cronjobs.

_Solution 1: Run script/command regularly at a specific time:_
You seem to know cron, but while I'm at it, I'll give full info here. Might help others. ;)
Command:
```
sudo crontab -e
```
(by default the editor is vi, so use "i" to get into insert mode and then "esc", ":wq" to quit and save)
Write this into the file to have the script run every day at 00:00:
> # m h  dom mon dow   command
0 0 * * * ls -1 /home/data/images/wallpapers/art/* | xargs -n1 -I{} ln -s {} /usr/share/wallpapers/

Note: Since this will make the script run with root permissions, you may remove the "sudo" from the command.

_Solution 2: Run script/command at boot:_
But there is also another interesting solution: Run it at every boot:
All you need to do is add the command to **/etc/rc.local**:

```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

ls -1 /home/data/images/wallpapers/art/* | xargs -n1 -I{} ln -s {} /usr/share/wallpapers/

exit 0

```
The same applies here: It's run with root permissions, so no need to use "sudo".

Using /etc/rc.local allows having random wallpapers at every startup for example. I remember seeing a script doing this somewhere.

If you want to run something at every logon that doesn't need root permissions, it's easiest to add it through:
**System->Preferences->Sessions**

_Other info:_
And if you ever want to write a script looping through files (that was my first idea to solve your problem), here's an example:
```
#! /bin/bash
#example of looping through output of the find command
files=`find . -name "*.sh"`

for f in $files;
do
	echo $f
done

#example of looping through specific stuff
files="file1 file2 foo bar nice_image"

for f in $files;
do
	echo $f
done

```
One useful script I created:
```
#! /bin/bash
ext=.png
pics=`find . -name *$ext`
#echo $pics
for p in $pics;
do
        dir=`dirname $p`
        base=`basename $p $ext`
        echo "$p->$dir/$base.eps"
        convert $p $dir/$base.eps
done

```
It converts .png to .eps images.

---

