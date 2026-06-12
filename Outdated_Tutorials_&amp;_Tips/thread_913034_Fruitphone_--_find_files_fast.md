---
title: "Fruitphone -- find files fast"
date: 2008-09-07
forum: Outdated Tutorials &amp; Tips
---

### Post by NightCrawler03X on 2008-09-07
[i]*****Please note, that you do not need to run as root in order to install fruitphone
*****Also, please note that this isn't a "program"; it's just a script. It should work on any unix system, such as linux, BSD (OpenBSD, FreeBSD, etc), Solaris, etc, etc, etc. It shouldn't matter what architecture you're on either, be it x86, AMD64, Sparc, PPC, etc, etc. It might also work on Microsoft Windows, through the use of [cygwin](http://www.cygwin.com/), though I haven't personally tested this myself.[/i]


I don't use Xorg most of the time, so I'm stuck browsing through files on the command line. I made a script that when run, lists every file on the disc, and automatically sorts the findings into alphabetical order, and tells you how many files it finds. After running the script, you then open up a text file that the script generates, and there will be a full list of every file found, upon which you can use that text editors search function to find the location of the file you are looking for.

To download fruitphone, click the link:
[http://ubuntuforums.org/attachment.php?attachmentid=84479&d=1220823664](http://ubuntuforums.org/attachment.php?attachmentid=84479&d=1220823664)

When you download the tarball, extract it and cd to the directory it creates, and you'll see the following files:
dfind
fchount
fcrount
fhome
froot
install_fruitphone

Run the install_fruitphone script:
```

./install_fruitphone

```
Then restart your terminal

The install_fruitphone script will copy all the other files to $HOME/fruitphone/ (after creating the fruitphone directory). The install_fruitphone script will also put the following aliases in your $HOME/.bashrc script:
```

alias dfind='~/fruitphone/dfind'
alias fhome='~/fruitphone/fhome'
alias froot='~/fruitphone/froot'
alias fchount='~/fruitphone/fchount'
alias fcrount='~/fruitphone/fcrount'
For easy running of each script.

```

Let me explain what each thing does:
```

fhome - looks for all files and directories in your $HOME, and makes a list in a text file ( ~/fruitphone/home.log ), before sorting that list into alphabetical order. After finishing this search, it reports how many files and directories it found too. It also makes a log in ~/fruitphone/hhistory of the time this search was run at, and how many files were found; this is so that at a later date you can refer back to see how many files you had on different dates

froot - same as fhome, except it searches everything in / -- lists the files in ~/fruitphone/root.log instead of ~/fruitphone/home.log and logs the date and number of files found in ~/fruitphone/rhistory instead of ~/fruitphone/hhistory

*Note: each time you run fhome, it will delete ~/fruitphone/home.log file from the previous search, and create a new one; that way information won't be repeated (and no-longer-existing files will not be listed). The same thing applies to froot and ~/fruitphone/root.log

fchount - same as fhome, except it only tells you the number of files and directories in your $HOME (it doesn't write any lists into a text file though).

fcrount - same as fchount, but lists the amount of files found on your entire disc ( / ) instead.

dfind - deletes fruitphone; however, it will not delete the aliases used to run the scripts; edit out the following lines:
alias dfind='~/fruitphone/dfind'
alias fhome='~/fruitphone/fhome'
alias froot='~/fruitphone/froot'
alias fchount='~/fruitphone/fchount'
alias fcrount='~/fruitphone/fcrount'
in ~/.bashrc with a text editor

```


fhome and froot are useful if you want to find the location of a file; just open up the text files they generate and use that text editors search function, so e.g. if you wanted to know where a file called hello.jpg was, you'd search for hello.jpg, and it if was in /usr/local, the text editor's search function would bring to to a line of text that says /usr/local/hello.jpg
You could also do the following command, e.g.
```

grep hello.jpg $HOME/fruitphone/root.log or
grep hello.jpg $HOME/fruitphone/home.log

```
this will list every line with "hello.jpg" on it; every line details a single file and it's location. To extend this even further, you could record the results of this into the fruitphone directory, e.g:
```

grep hello.jpg $HOME/fruitphone/home.log >> $HOME/fruitphone/home_hello-search.log
and view $HOME/fruitphone/home_hello-search.log with a text editor, or cat it:
cat $HOME/fruitphone/home_hello-search.log | less

```

You may be thinking, why do I need this if I can already do, e.g:
find $HOME | grep hello.jpg >> $HOME/whatever.txt && cat $HOME/whatever.txt | less

In fact, this is more or less what fruitphone (in this example fhome) does:
```

rm $HOME/fruitphone/home.log
touch $HOME/fruitphone/home.log
find $HOME | grep '' >> $HOME/fruitphone/home.log
grep -c '' $HOME/fruitphone/home.log *#counts the number of lines in home.log, in other words the number of files and directories in your $HOME*
sort $HOME/fruitphone/home.log -o $HOME/fruitphone/home_sorted.log
rm $HOME/fruitphone/home.log
mv $HOME/fruitphone/home_sorted.log $HOME/fruitphone/home.log
Imagine if you often need to find the location of certain files, and having to type lots and lots of commands like that all the time.
It even does this for you:
date >> $HOME/fruitphone/hhistory
echo 'home.log lists the following number of items:' >> $HOME/fruitphone/hhistory
grep -c '' $HOME/fruitphone/home.log >> $HOME/fruitphone/hhistory
(it's the part that makes a log of fhome's findings in the ~/fruitphone/hhistory text file)

```

If you don't often need to search for a file, and only have to do something like
```

find /whatever/location | grep whatever >> /whatever/files.txt && cat /whatever/files.txt | less

```
every now and then, then you probably won't need fruitphone, but if you often find yourself needing to find files (and make a record, including order everything alphabetically for better readability, etc) then fruitphone makes it extremely easy for you.
Well, this will simplify that; you type much less. Also, greping from the text file fruitphone generates is better because the listings in there will be in alphabetical order.

A computer is meant to make things easier; fruitphone makes file searching easier. The amount of things this script does will save you minutes (you'll take seconds instead of minutes), and because of this, you can spend those gained minutes to do even more ( or better yet, improve the script and post your modified version here for us all to use ;-) )

It's a bit like the search function you'd find on Windows, some linux distros, etc. It's not as easy to use as other ones, but it's faster and more convenient if you know how to use it properly.

Go to the bottom of this post, and you'll see something that says "attached files"; click on the attachment to download fruitphone.

Here is the source for each script (some people are wary about scripts that others write, so they want to check to see if it is secure; to make it easy for you, I provide the source right here, so you can take a look at it right away):
fhome:
```

##!/bin/sh

# fhome - lists all files in the users ~ directory
echo 'searching all files in home...'
rm $HOME/fruitphone/home.log
touch $HOME/fruitphone/home.log
find $HOME | grep '' >> $HOME/fruitphone/home.log
echo ''
echo 'number of files found; this includes directories:'
grep -c '' $HOME/fruitphone/home.log
echo ''
echo 'sorting file listing into alphabetical order...'
sort $HOME/fruitphone/home.log -o $HOME/fruitphone/home_sorted.log
rm $HOME/fruitphone/home.log
mv $HOME/fruitphone/home_sorted.log $HOME/fruitphone/home.log
echo '...done'
date >> $HOME/fruitphone/hhistory
echo 'home.log lists the following number of items:' >> $HOME/fruitphone/hhistory
grep -c '' $HOME/fruitphone/home.log >> $HOME/fruitphone/hhistory
echo '' >> $HOME/fruitphone/hhistory
echo ''
echo 'Fruit-Phone has finished searching your disc'
echo 'to see a list of all files in your home directory, just look in $HOME/fruitphone/home.log with a text editor'
echo ''
echo 'fhome has also made a log in $HOME/fruitphone/hhistory containing the following information:'
echo 'date, and number of files found; this is so that at a later date'
echo 'you can refer to the log and see how many files were found at this time'
echo 'the most recent recording will be at the bottom of the file'


```
froot:
```

#!/bin/sh

# froot - lists all files on the disc - needs root privileges
echo 'searching all files in root...'
rm $HOME/fruitphone/root.log
touch $HOME/fruitphone/root.log
find / | grep '' >> $HOME/fruitphone/root.log
echo ''
echo 'number of files found; this includes directories:'
grep -c '' $HOME/fruitphone/root.log
echo ''
echo 'sorting file listing into alphabetical order...'
sort $HOME/fruitphone/root.log -o $HOME/fruitphone/root_sorted.log
rm $HOME/fruitphone/root.log
mv $HOME/fruitphone/root_sorted.log $HOME/fruitphone/root.log
echo '...done'
date >> $HOME/fruitphone/rhistory
echo 'root.log lists the following number of items:' >> $HOME/fruitphone/rhistory
grep -c '' $HOME/fruitphone/root.log >> $HOME/fruitphone/rhistory
echo '' >> $HOME/fruitphone/rhistory
echo ''
echo 'Fruit-Phone has finished searching your disc'
echo 'to see a list of all files in your root directory, just look in $HOME/fruitphone/root.log with a text editor'
echo ''
echo 'froot has also made a log in $HOME/fruitphone/rhistory containing the following information:'
echo 'date, and number of files found; this is so that at a later date'
echo 'you can refer to the log and see how many files were found at this time'


```
fcrount:
```

#!/bin/sh

# fchount - reports how many files+directories there are on the disc
find / | grep '' >> $HOME/fruitphone/fc.log
echo 'there are:'
grep -c '' $HOME/fruitphone/fc.log
echo 'files on your disc'
rm $HOME/fruitphone/fc.log


```
fchount:
```

#!/bin/sh

# fchount - reports how many files+directories there are in the users home directory
find $HOME | grep '' >> $HOME/fruitphone/fc.log
echo 'there are:'
grep -c '' $HOME/fruitphone/fc.log
echo 'files in your home directory'
rm $HOME/fruitphone/fc.log


```
dfind:
```

#!/bin/sh

# dfind - deletes fruitphone
echo 'uninstalling fruitphone...'
rm $HOME/fruitphone/froot
echo '...removed froot'
rm $HOME/fruitphone/fhome
echo '...removed fhome'
rm $HOME/fruitphone/dfind
echo '...removed dfind'
rm $HOME/fruitphone/fchount
echo '...removed fchount'
rm $HOME/fruitphone/fcrount
echo '...removed fcrount'
rm $HOME/fruitphone/home.log
echo '...removed $HOME/fruitphone/home.log'
rm $HOME/fruitphone/root.log
echo '...removed $HOME/fruitphone/root.log'
rm -Rf $HOME/fruitphone
echo '...removed directory $HOME/fruitphone'
echo 'NOTE:'
echo 'fruitphone has not been completely uninstalled'
echo 'open the file ~/.bashrc with a text editor'
echo 'and delete the following lines:'
echo 'alias froot=~/fruitphone/froot'
echo 'alias fhome=~/fruitphone/fhome'
echo 'alias dfind=~/fruitphone/dfind'
echo 'after doing this, restart your terminal'
echo 'or log off and log back in again'
echo 'if you are not running X, but are on an actual shell'


```
install_fruitphone:
```

#!/bin/sh

# Fruit-Phone will list all files in either your entire disc, or your home directory
# Think of it like the search function you might see on Windows, Mac, certain
# linux distros, etc, except it doesn't let you search for a specific file...
# ...instead it lists all files on your harddrive, and lists all of these
# files and their location in a seperate text file somewhere...
# ...after which, you can view this text file in a text editor,
# and use the 'find text' function in that text editor, to find
# a file. So for example, if fruitphone
# found a file named cooker.mp3, and it was located in /usr/local,
# and you searched for a string of text called 'cooker' in a 
# text editor, the text editor would find a line of text that says
# '/usr/local/cooker.mp3'
# and if you wanted to listen to that mp3 audio file, you know
# where it is.
# It's not as easy to use as some of the more 'sophisticated'
# file searching programs out there (and it's just a simple script anyway),
# but it's certainly much faster and uses way less system resources, 
# so it's cool

# Written by NightCrawler03X (aka me),
# other names I use on the internet:
# LordMister
# Haneda
# Chain Hustler
# Sans-Sherrif

# install fruit phone
echo 'installing fruitphone...'
mkdir $HOME/fruitphone
touch $HOME/fruitphone/home.log
touch $HOME/fruitphone/root.log
cp ./fhome $HOME/fruitphone/
echo '...installing fhome'
cp ./froot $HOME/fruitphone/
echo '...installing froot'
cp ./dfind $HOME/fruitphone/
echo '...installing dfind'
cp ./fchount $HOME/fruitphone/
echo '...installing fchount'
cp ./fcrount $HOME/fruitphone/
echo '...installing fcrount'
echo ''
echo "alias froot='~/fruitphone/froot'" >> ~/.bashrc
echo "alias fhome='~/fruitphone/fhome'" >> ~/.bashrc
echo "alias dfind='~/fruitphone/dfind'" >> ~/.bashrc
echo "alias fchount='~/fruitphone/fchount'" >> ~/.bashrc
echo "alias fcrount='~/fruitphone/fcrount'" >> ~/.bashrc
echo 'Fruit-Phone is installed. Use froot to list all files on the disc, and fhome to list all files in your ~ directory'
echo 'to properly use froot, you will need root privileges'
echo 'froot will list all files in the text file ~/fruitphone/root.log'
echo 'fhome will list all files in the text file ~/fruitphone/home.log'
echo 'to uninstall fruitphone, just issue a dfind command'
echo ''
echo 'If you only want to know how many files there are on your disc, and how much space'
echo 'is being used on the disc, or in your home area:'
echo 'use fchount to count the files in your home directory'
echo 'and fcrount to count the files in your root directory'
echo ''
echo 'NOTE:'
echo 'if this is your first time installing fruitphone, you will need to restart your terminal program'
echo 'just close it, then open it again'
echo 'if you are not running Xorg, and are viewing this from an actual shell, you will'
echo 'need to completely log out, then log back in again'
echo 'this is because the fruitphone installer does not put a shell script'
echo 'in any place, e.g. /usr/bin, to run from, instead adding several'
echo 'aliases to ~/.bashrc, which means you need to restart your'
echo 'bash shell so it can register any commands it finds in ~/.bashrc'
echo 'if you are not using bash, instead something like zsh'
echo 'I am not sure how to help, but I am sure if you just modify'
echo 'the install_fruitphone file to instead create'
echo 'aliases in whatever file zsh reads from I am sure you will be fine'


```

---

### Post by swegner on 2008-09-08
Does this offer similar functionality to the *locate commands?  For quickly finding a file on the system by name, I generally use:

```
mlocate myfile
```

mlocate also supports regular expressions for more complicate searches.  The search database is automatically maintained through a cron job, but can be manually updated with the command:

```
sudo updatedb
```

---

### Post by NightCrawler03X on 2008-09-08
Well, "mlocate myfile" does the exact same thing as "find / | grep myfile"
but as far as I'm aware, it doesn't tell you exactly how many files it found based on your search, nor does it make a log of the date and how many files it found, nor does it record information about the files it found into a seperate text file. It does, however, automatically arrange what it finds into alphabetical order.

Well, if you wanted to do "mlocate myfile" and everything else that my script does, you'd do:
mlocate myfile >> ~/file_search
grep -c '' ~/file_search
date >> ~/file_search_log
grep -c '' ~/file_search >> ~/file_search_log

Though, please note that my script doesn't let you search for an individual file. You run the script and it lists every file on your disc, in a seperate text file. After that, you can do a 
grep myfile ~/fruitphone/root.log

> Does this offer similar functionality to the *locate commands?
Yes, my script does offer similar functionality to mlocate. It does other useful things automatically too though, as I've explained above.
(such as not just display the results, also save the record the results in a seperate file, and make a log in another file of what time it did the scan, and how many files were found during that scan).

I'm not as skilled with the command line as I'd like to think I am; my script is pretty simple. I'm trying to learn more, so I can make much more complex scripts. The *locate commands offer much more functionality than my script, however for most searches my script makes things much easier (you type much less).

---

