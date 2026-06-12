---
title: "Korn Command Substitution Variable"
date: 2011-06-16
forum: Programming Talk
---

### Post by metallica1973 on 2011-06-16
I am in the process of creating a korn shell script and am trying to assign command substitutions to a variable like:

```
$ date=$(date +%m%d%y)
$ echo $date
061611

```

But when I try and assign it to variable $file_changed it executes the variable without me invoking in it. It just automatically starts executing so my scripts screws up.

```
$ file_changed=$(find . -depth \( -wholename \./\.\* \) -prune -o -mtime -1 -print | cpio -oav)
./perl_test.pl
./nam_test.ksh
./sniff_test.p1
./korn_script_0105.pdf
./check_nodes.new
./zoneminder_install.sh
./nam_test.11_3_07
./rolo_exclude
./check_nodes.sh
./nam_sniffer.history
./check_nodes (1).sh
./backup_website
./dachit
./test_data1
.
5506 blocks

```

So how can I assign this as a variable that is only used when it is called like the $date variable above? I know it can be done. I can remember how to do it, help!!

---

### Post by metallica1973 on 2011-06-16
his post is associated with this:

[http://ubuntuforums.org/showthread.php?t=1784418](http://ubuntuforums.org/showthread.php?t=1784418)

I am in the process of writing my first backup script and am having some issues with the script. I started playing around with Korn a couple of years ago and it sparked my interest so, I need a little direction. The goal of this script is too have a choice of performing a full or incremental backup or else give you a syntax error if you type what you weren't supposed too  The script should work like this:

```

<home_dir>saint_home.ksh full
or
<home_dir>saint_home.ksh incremental
or
<home_dir>saint_home.ksh
Incorrect syntax usage. Use <saint.ksh> {full|incremental}
Or target directory does not exist. Please verify share exist!

```

This is what it looks like so far:

```
#!/bin/ksh
#Basic script to backup caca
#Home directories to the external 
#1T drive
#Author  The One and Only 
#############################################################
#############################################################

results=$1
backup_dir="/home/testuser/testbackup"
date=$(date +%m%d%y)
#file_changed=find . -mtime -1 | cpio -oa 2>/dev/null | ( cd $backup_dir && cpio -imd) 
file_changed=$(find . -depth \( -wholename \./\.\* \) -prune -o -mtime -1 -print | cpio -oav)
full_backup_dir=$(find . -depth \( -wholename \./\.\* \) -prune -o -print | cpio -oav)
#zipit=$(tar czXF)
#include=rolo_include
#exclude=rolo_exclude

#$cat $include|while read lines;
#do



if [[ -d $backup_dir &&  $results = "full" ]] ; then

cd /home

$full_backup_dir > /home/testuser/testbackup/full$date.cpio 2>&1 /home/testuser/testbackup/full_status$date.log

else
        print "Incorrect syntax usage. Use <saint_home.ksh> {full|incremental}"
        print "Or target directory does not exist. Please verify share exist!"
fi

if      [[ -d $backup_dir && $results ="incremental"]] ; then

cd /home

$file_changed > /home/testuser/testbackup/inc$date.cpio 2>&1 /home/testuser/testbackup/inc_status$date.log

else
        print "Incorrect syntax usage. Use <saint.ksh> {full|incremental}"
fi

case
        $results in

        full)
                echo full
                ;;
        incremental)
                echo incremental
                ;;
        quit)
                exit
                ;;
esac

```
when I run my script by itself just to see if it errors ok, it will automatically start running one of the variables and not do what I want. It is suppossed to give me "else" syntax messages from the begginning but it is ignoring it and just running past it. 

Here is the test run(trucated):

```

<home-dir>./saint_home.ksh

./Pictures/2008/01/05/img_3612.jpg
./Pictures/2008/01/05/img_3609-2.jpg
./Pictures/2008/01/05/img_3606-3.jpg
./Pictures/2008/01/05/img_3612-2.jpg
./Pictures/2008/01/05
./Pictures/2008/01
./Pictures/2008/08/08/img_2104.jpg
./Pictures/2008/08/08/mvi_3476-1.avi
./Pictures/2008/08/08/mvi_3476.avi
./Pictures/2008/08/08/mvi_1620.avi
./Pictures/2008/08/08/img_2113.jpg
./Pictures/2008/08/08/mvi_1621.avi
./Pictures/2008/08/08/img_2104-1.jpg
./Pictures/2008/08/08/img_2113-1.jpg
2305 block
Incorrect syntax usage. Use <saint.ksh> {full|incremental}
Or target directory does not exist. Please verify share exist!
./saint_home.ksh[33]: [[: not found [No such file or directory]
Incorrect syntax usage. Use <saint.ksh> {full|incremental}
./saint_home.ksh: line 40: syntax error at line 44: `newline' unexpected


```

A couple of questions that I have are:

1 - when creating variables with command substition, how can I specify many on one line. These do not work:

```

file_changed=$(find . -depth \( -wholename \./\.\* \) -prune -o -mtime -1 -print | cpio -oav)
```

2 - When creating condition constructs, do I need separte brackets or can I put everything inside of one, like:

```
if [[ -d $backup_dir &&  $results = "full" ]] ; then
```

or 

```
if [[ -d $backup_dir ]] && [[ $results = "full" ]] ; then

```

The case entry was added to be able to choose full and or incremental and assign it to results=$1 to be interpreted by my if/else conditions. So 

```
$ saint_home.ksh full
```

or 

```
$ saint_home.ksh incremental
```

else

```
Incorrect syntax usage. Use <saint.ksh> {full|incremental}
Or target directory does not exist. Please verify share exist!
```

Help

---

### Post by kaibob on 2011-06-17
Deleted post.

---

### Post by metallica1973 on 2011-06-17
thanks for the reply.

That is exact what is in my experimental script:

```
#!/bin/ksh
#Basic script to backup caca
#Home directories to the external 
#1T drive
#Author  The One and Only 
#############################################################
#############################################################

results=$1
backup_dir="/home/testuser/testbackup"
date=$(date +%m%d%y)
#file_changed=find . -mtime -1 | cpio -oa 2>/dev/null | ( cd $backup_dir && cpio -imd) 
file_changed=$(find . -depth \( -wholename \./\.\* \) -prune -o -mtime -1 -print | cpio -oav)
full_backup_dir=$(find . -depth \( -wholename \./\.\* \) -prune -o -print | cpio -oav)
#zipit=$(tar czXF)
#include=rolo_include
#exclude=rolo_exclude

#$cat $include|while read lines;
#do



if [[ -d $backup_dir &&  $results = "full" ]] ; then

cd /home

$full_backup_dir > /home/testuser/testbackup/full$date.cpio 2> /home/testuser/testbackup/full_status$date.log

else
        print "Incorrect syntax usage. Use <saint_home.ksh> {full|incremental}"
        print "Or target directory does not exist. Please verify share exist!"
fi

if      [[ -d $backup_dir && $results ="incremental"]] ; then

cd /home

$file_changed > /home/testuser/testbackup/inc$date.cpio 2>  /home/testuser/testbackup/inc_status$date.log

else
        print "Incorrect syntax usage. Use <saint.ksh> {full|incremental}"
fi

case
        $results in

        full)
                echo full
                ;;
        incremental)
                echo incremental
                ;;
        quit)
                exit
                ;;
esac
```

you can see that is exact what I am trying to accomplish in the middle of the script but when I open up terminal to test that variable, the variable doesnt store just store the command until the script requests its. It simply just executes so I am trying to figure out what I need to do to not make it do that. I have tried:

```
full_backup_dir="$(find . -depth \( -wholename \./\.\* \) -prune -o -print | cpio -oav)"
```
```
$full_backup_dir=`$(find . -depth \( -wholename \./\.\* \) -prune -o -print | cpio -oav)`
```
```
$full_backup_dir=$((find . -depth \( -wholename \./\.\* \) -prune -o -print | cpio -oav))
```

???????????????????/

---

### Post by metallica1973 on 2011-06-17
I made progress:

```
$>$full_backup_dir=$(find . -depth \( -wholename \./\.\* \) -prune -o -mtime -1 -print)
$>full_backup | cpio -oav > /home/testuser/caca$date.cpio

```

I will update you when I am done. It has something to do with the "|" pipe symbol that the variable doesnt like.

---

### Post by gmargo on 2011-06-17
It's not the pipe, it's using the "$()" form - which executes the command immediately.

I think you need something of the form:
```

full_backup_dir="find . -depth -print0"
cpio_out="cpio -o0av"

$full_backup_dir | $cpio_out > "$backup_dir/full${date}.cpio" 2> "$backup_dir/full_status${date}.log"

```I saw no point in  the -wholename argument, which does not seem to do anything except create a shell-escaping headache.

---

### Post by metallica1973 on 2011-06-17
thanks gmargo,

I change the tag from [PHP] to ```
. now look at the variable:

[code]$full_backup_dir=$(find . -depth \( -wholename \./\.\* \) -prune -o -mtime -1 -print) 
```


I corrected my posted script. I am excluding my hidden directories and that is why I have -wholename and -prune. Since then I ran a test run and am now getting a permission error.

```
~$ $full_backup_dir | cpio -aov > /media/caca/extract/full$date.cpio 
bash: ./examples.desktop: Permission denied
1 block

```

but if I run it without it being a variable it runs fine:

```
~$ find . -depth \( -wholename \./\.\* \) -prune -o -print|  cpio -aov > /media/caca/extract/full$date.cpio 
./examples.desktop
./Desktop/saint.desktop
./Desktop
./Downloads/fitzpatrick/status_file
^Z
[3]+  Stopped                 find . -depth \( -wholename \./\.\* \) -prune -o -print | cpio -aov > /media/caca/extract/full$date.cpio

```

```
~$ $full_backup_dir | cpio -aov > /home/testuser/full$date.cpio 
bash: ./examples.desktop: Permission denied
1 block

```

I also ran it with ksh debug

```

~$ ksh -x $full_backup_dir | cpio -aov > /home/saint/full$date.cpio 
+ '[Desktop' 'Entry]'
./examples.desktop[1]: [Desktop: not found [No such file or directory]
+ Version=1.0
+ Type=Link
+ Name=Examples
+ content for Ubuntu
+ Comment=Example
./examples.desktop[5]: content: not found [No such file or directory]
+ URL=file:///usr/share/example-content/
+ Icon=folder
+ X-Ubuntu-Gettext-Domain=example-content
./examples.desktop: line 8: X-Ubuntu-Gettext-Domain=example-content: not found
1 block

```

It doesnt matter what directory. So why am I getting a permission error?

---

### Post by metallica1973 on 2011-06-17
gmargo,

you were right, keep it simple and move forward:

didnt work:

```

search=$(find)
move=$(cpio)
move=$(cpio -aov)
move=`cpio -aov`
full_backup_dir=$(find . -depth \( -wholename \./\.\* \) -prune -o -print)
full_backup_dir="find . -depth \( -wholename \./\.\* \) -prune -o -print"


worked:

[code]search=find
archive="cpio -oav"

```

```

$search . -depth \( -wholename \./\.\* \) -prune -o -print | $archive > /media/caca/extract/full$date.cpio

```

many thanks

---

### Post by metallica1973 on 2011-06-20
I have written a script that works fine except that one of my lines is not interpreting the regular expression within the script. This section of the script uses the find command to search for everything in the directory except for the hidden directories such as .gconf, .evolution, .ssh as an example. The command works fine outside of the script but when used in the script, it doesnt interpret a section of the statement. I know it is some type of syntax error but can figure out what it is.

Here is the line in the script that is not working correctly: 

```
 
$search . -depth \( -wholename \./\.\* \) -prune -o -print | $archive > $backup_dir/full$date.cpio 2> $backup_dir/full_status$date.log

```

This is what it is doing via debug:

```

~$ set -x
+ set -x
~$ archive="cpio -oavc"
+ archive='cpio -oav'
~$ search=find
+ search=find
~$ backup_dir=/home/davider/Downloads
+ backup_dir=/home/davider/Downloads
~$/Documents/scripts$ date=$(date +%m%d%y)
++ date +%m%d%y
+ date=061811
~$/Documents/scripts$ archive="cpio -oavc"
+ archive='cpio -oavc'
~$/Documents/scripts$ $search . -depth \( -wholename \./\.\* \) -prune -o -print | $archive > $backup_dir/full$date.cpio 2> $backup_dir/full_status$date.log
+ find . -depth '(' -wholename './.*' ')' -prune -o -print
+ cpio -oavc

```

This is what the code is not interpreting correctly:

```

\( -wholename \./\.\* \) -prune

```

This is what the korn shell is seeing:

```

+ find . -depth '(' -wholename './.*' ')' -prune -o -print

```

Here is the section of the script where it lives:

```

if [[ -d $backup_dir &&  $results = "full" ]] ; then

        cd /home

$search . -depth \( -wholename \./\.\* \) -prune -o -print | $archive > $backup_dir/full$date.cpio 2> $backup_dir/full_status$date.log

fi

```

Do I need quotes around it or something?

---

### Post by gmargo on 2011-06-20
Isn't this an extension of this thread:
[http://ubuntuforums.org/showthread.php?t=1784418](http://ubuntuforums.org/showthread.php?t=1784418)

Why do you need a -wholename option?
Why do you need parentheses?

If you're trying to exclude something from the find output, try using "grep -v" to remove the parts you don't want.

---

### Post by metallica1973 on 2011-06-20
Gmargo,

Thanks for the reply

yes you are correct. I didnt want to created a book from the other thread. You helped me solve my issue. By using the wholename and the way I was using it cause issues with interpretation of:

```
 
\( -wholename \./\.\* \) -prune

```

I instead switched to using -path which:

[php]
-path pattern
              File name matches shell pattern pattern.  The metacharacters do not treat `/' or `.' specially; so, for example,
                        find . -path "./sr*sc"
              will  print  an  entry  for a directory called `./src/misc' (if one exists).  To ignore a whole directory tree, use -prune rather than checking
              every file in the tree.  For example, to skip the directory `src/emacs' and all files and directories under it, and  print  the  names  of  the
              other files found, do something like this:
                        find . -path ./src/emacs -prune -o -print
              Note  that  the  pattern  match test applies to the whole file name, starting from one of the start points named on the command line.  It would
              only make sense to use an absolute path name here if the relevant start point is also an absolute path.  This  means  that  this  command  will
              never match anything:
[/php]

and with winning results I was able to get the script doing what I want to do.

```

~$ ksh -x Documents/scripts/saint.ksh full
+ results=full
+ backup_dir=/media/caca/extract
+ date +%m%d%y
+ date=062011
+ search=find
+ archive='cpio -oavc'
+ [[ -d /media/caca/extract ]]
+ [[ full == full ]]
+ cpio -oavc
+ 1> /media/caca/extract/full062011.cpio 2> /media/caca/extract/full_status062011.log
+ find . -depth -path './.*' -prune -o -print
+ [[ -d /media/caca/extract ]]
+ [[ full == incremental ]]
+ echo full
full

```

which produced the results I was looking for:

```

+ find . -depth -path './.*' -prune -o -print

```

So I finally added that to the script and ran it:

```

$search . -depth -path "./.*" -prune -o -print | $archive > /media/caca/extract/full$date.cpio 2> /media/caca/extract/full_status$date.log

```

on more thing I had to add:

```

! -path "./.*"

```

and take out:

```

-prune -o

```

to exclude my hidden directories in my home directory:

```

$search . -depth -mtime -1 ! -path "./.*"  -print | $archive > /media/caca/extract/inc$date.cpio 2> /media/caca/extract/inc$date.log

```


One more question:

Even though I have a 2> /media/caca/extract/full_status$date.log, it is reporting everything like 2>&1 (stderr and stdout). This should only report errors but it not, it reporting everything successfull as well. 

??

---

### Post by bapoumba on 2011-06-20
Threads merged.

---

