---
title: "Just wrote my favorite sh script!"
date: 2010-09-28
forum: Programming Talk
---

### Post by ironic.demise on 2010-09-28
I'm just looking for where I can improve, where I can go to from here to improve myself and general advice.
 oh and as a side-note, is there any advice on security when using Apache?

This is used for maintaining a straight-forward html page
but I can imagine it would work with php or mysql as well.

This is mainly because when my girlfriend writes a new blog entry on her hand-written website she always copy+pastes a lot of generic things from one page to the newer one... things like div locations, side-bars, menus and things.

So I wrote a website compiler script based on seperating the universal aspects of a website and those that are updated, such as a blog would maintain icons, links and other such things but the content in the entry would change.

Is BASH a programming language?

This asks about:
Changing the default locations of files
Changing previously written pages
makes a backup
adds new changes
and compiles every page, ensuring that each page is consistent with things such as the header.
```

#! /bin/bash
#
# Set-up
backupdir=/home/samuel/Documents/backups/website
sourcedir=/home/samuel/Documents/Source
serverdir=/var/www/unacquainted
script=/home/samuel/.scripts/compile.sh
#
#
echo Throughout each yes or no question
echo asked by this program
echo you must explicitly answer "yes" or "no"
echo y, n, YES, NO or any other abbreviation or derivation will NOT be accepted
#
# Make changes
#
echo Do you wish to change the backup, source, server and script directories \(non-permanent\)
read changesettings
if [[ "$changesettings" == "yes" ]]
then
#
# Change backup directory
echo name backup directory
echo current: /home/samuel/Documents/backups/website
echo press ctrl+c to cancel
read backupdir
mkdir -p $backupdir
echo changed temporarily from /home/samuel/Documents/backups/website to $backupdir
#
# Change source directory
echo name source directory
echo current: /home/samuel/Documents/Source
echo press ctrl+c to cancel
read sourcedir
mkdir -p $sourcedir
echo changed temporarily from /home/samuel/Documents/Source to $sourcedir
#
# Change script location
echo name script location
echo current: /home/samuel/.scipts/compile.sh
echo press ctrl+c to cancel
read script
mkdir -p $script
echo changed temporarily from /home/samuel/.scripts/compile.sh to $script
else
echo Not changing any defaults
fi
#
# Changing old files
#
echo would you like to make changes to any already existing pages? yes or no, if yes you will then be asked which page.
read changepage
if [[ "$changepage" == "yes" ]]
then
echo Which page? 
echo \(You will need to input the name of the page in full without any errors\)
echo This will change the SOURCE file, not the server file
echo do NOT ammend file extension to page name
read pagename
gedit $sourcedir/$pagename.txt
else
echo not making any changes at the moment.
fi
#
# Backups
#
echo This is a compulsory section
echo \for security reasons you must define a location to backup files
echo the location \for backup will be $backupdir followed by
echo the directory that you define now.
echo name the new backup directory name followed by enter.
read backup
mkdir -p $backupdir/$backup/Server
mkdir -p $backupdir/$backup/Source
cp -R $sourcedir $backupdir/$backup/Source
cp -R $serverdir $backupdir/$backup/Server
cp -R $script $backupdir/$backup
#
# Add a new page
#
echo Do you want to \make a new page? enter yes or no followed by enter
read newpage
if [[ "$newpage" == "yes" ]]
then
echo name the homepage currently written in index.html
read oldname
echo moving $oldname
cp $sourcedir/index.txt $sourcedir/$oldname.txt
echo \# Compiling $oldname.html >>  $script  
echo cat \$sourcedir/html.txt \> \$serverdir/$oldname.html  >> $script  
echo cat \$sourcedir/head.txt \>\> \$serverdir/$oldname.html  >> $script  
echo cat \$sourcedir/body.txt \>\> \$serverdir/$oldname.html  >> $script  
echo cat \$sourcedir/universal.txt \>\> \$serverdir/$oldname.html  >> $script  
echo cat \$sourcedir/$oldname.txt \>\> \$serverdir/$oldname.html  >> $script  
echo cat \$sourcedir/end.txt \>\> \$serverdir/$oldname.html  >> $script  
echo you will now be required to edit the old homepage.
echo remember to save your work, Otherwise you will have two identical pages.
echo the old homepage was backed up and is restorable.
gedit $sourcedir/index.txt
else
echo not making new page. continuing
fi
#
# Begin compilation
#
# Compiling index.html 
cat $sourcedir/html.txt > $serverdir/index.html  
cat $sourcedir/head.txt >> $serverdir/index.html  
cat $sourcedir/body.txt >> $serverdir/index.html  
cat $sourcedir/universal.txt >> $serverdir/index.html  
cat $sourcedir/index.txt >> $serverdir/index.html  
cat $sourcedir/end.txt >> $serverdir/index.html  

```

Crit requested.

---

### Post by mobilediesel on 2010-09-28
> **ironic.demise said:**
> I'm just looking for where I can improve, where I can go to from here to improve myself and general advice.
 oh and as a side-note, is there any advice on security when using Apache?

This is used for maintaining a straight-forward html page
but I can imagine it would work with php or mysql as well.

This is mainly because when my girlfriend writes a new blog entry on her hand-written website she always copy+pastes a lot of generic things from one page to the newer one... things like div locations, side-bars, menus and things.

So I wrote a website compiler script based on seperating the universal aspects of a website and those that are updated, such as a blog would maintain icons, links and other such things but the content in the entry would change.

Is BASH a programming language?

This asks about:
Changing the default locations of files
Changing previously written pages
makes a backup
adds new changes
and compiles every page, ensuring that each page is consistent with things such as the header.


Crit requested.

You can make it less picky about the yes/no answers using the case...esac statements:
```
echo "Do you want to do that thing?"
read answer
case "${answer:0:1}" in
[yY])
echo "Doing that thing you want..."
echo "Doing the thing"
;;
*) echo "Okay, not doing that thing." ;;
esac
```
Using **${answer:0:1}** means it's only looking at the first character of the answer. The **[yY]** means it looks for a **Y** in upper or lowercase. The ***)** means anything that doesn't start with a **Y** is treated as **no**.

That improves the ease-of-use a bit. Doing it that way, it'll even take "Yo!" as a **yes** answer.

Then something like this:
```
# Compiling index.html 
cat ~/Documents/Source/html.txt > ~/Public/Web_server/unacquainted/index.html  
cat ~/Documents/Source/head.txt >> ~/Public/Web_server/unacquainted/index.html  
cat ~/Documents/Source/body.txt >> ~/Public/Web_server/unacquainted/index.html  
cat ~/Documents/Source/universal.txt >> ~/Public/Web_server/unacquainted/index.html  
cat ~/Documents/Source/index.txt >> ~/Public/Web_server/unacquainted/index.html  
cat ~/Documents/Source/end.txt >> ~/Public/Web_server/unacquainted/index.html
```
Can be simplified like this:
```
# Compiling index.html 
cat ${SOURCE}/{html,head,body,universal,index,end}.txt > ${Target}/unacquainted/index.html
```
The brackets {...} will go through each comma-separated item. Using the brackets around the variable names does something different entirely, it helps keep the actual variable name separate from the rest of the line. Easier for later debugging.

And as for whether or not Bash is a programming language: *almost*
A bash script is just a list of commands that can be typed at a terminal. Having actual flow control brings it *close* to being a full programming language but not quite.

That being said, I do most of my "programming" in Bash.

---

### Post by ironic.demise on 2010-09-29
I appreciate the advice, I think I'll use those and it'll probably come in usefull from here on in.
If there was a recommend or thumbs up on this site, i'd give you ten

---

