---
title: "Asking for help once again with BASH"
date: 2007-07-16
forum: Programming Talk
---

### Post by brennydoogles on 2007-07-16
ok, so here is what I am trying to do. I am writing a bash script to help keep an infinite number of folders synchronized using symbolic links. I tossed the idea around, and could not come up with a way to make one script able to keep up with multiple folders at the same time, so I decided to have my script create a hidden folder in the user's home directory, into which it could create multiple scripts to synchronize the multiple folders (each of these scripts could be called at startup by calling a single script containing ```
sudo sh .foldersync/*
``` in the terminal) I think i have the basic idea down, but I am getting some strange errors.

Here is the script so far: ```
#!/bin/bash
# Program to create syncronized folders
#########################################################################################################################################################################################################################	Variable Declaration	####################################################################################################################################################################################################################################

safemk () {
if [ ! -d $1 ]; 
  then mkdir $1; 
  chmod +rw $1; 
fi
}

SYNC=/home/$USER/.foldersync

FILE=$SYNC/$PROJECT.sh


#########################################################################################################################################################################################################################	Scripted Action		####################################################################################################################################################################################################################################

safemk $SYNC

echo "What would you like to call this project?
read PROJECT
echo "Please input the source folder."
read SRCDIR
echo "Please input the destination directory"
read DEST


echo "#!/bin/bash" >> $FILE
echo "#Script to Update symbolic links on system startup" >> $FILE
echo "if [ !  " $DEST "/$1 ];" >> $FILE
echo "  then sudo ln -s /" $SRC "/* /" $DEST "/;" >>$FILE
echo "fi" >> $FILE
echo "exit 0" >> $FILE

sudo chmod +x $SYNC/$PROJECT.sh

exit 0
```

and here are my errors: ```
brendon@brendon-linux:~/devbin$ ./foldersync 
./foldersync: line 34: unexpected EOF while looking for matching `"'
./foldersync: line 39: syntax error: unexpected end of file
brendon@brendon-linux:~/devbin$ 

```

Where have I gone astray??

---

### Post by yabbadabbadont on 2007-07-16
```
echo "What would you like to call this project?
```
First error is here.  Add the missing ".

---

### Post by brennydoogles on 2007-07-16
> **yabbadabbadont said:**
> ```
echo "What would you like to call this project?
```
First error is here.  Add the missing ".

*SLAPS SELF ON FOREHEAD* 





I feel like an idiot lol. Thanks!!

---

### Post by Mr. C. on 2007-07-16
brennydoogles,

If you care to describe your goal a bit more, perhaps we can give you some guidance.

The solution you are creating seems more complicated than necessary.

MrC

---

### Post by brennydoogles on 2007-07-16
ok, so I have edited the script, and everything works mostly right except for one thing. Every file that it creates is called ```
.sh
``` without having a name. What did i do wrong?? Here is the updated script: ```
#!/bin/bash
# Program to create syncronized folders
#########################################################################################################################################################################################################################	Variable Declaration	####################################################################################################################################################################################################################################

safemk () {
if [ ! -d $1 ]; 
  then mkdir $1; 
  chmod +rw $1; 
fi
}

SYNC=/home/$USER/.foldersync

FILE=$SYNC/"$PROJECT".sh


#########################################################################################################################################################################################################################	Scripted Action		####################################################################################################################################################################################################################################

safemk $SYNC

echo "What would you like to call this project?"
read PROJECT
echo "Please input the source folder."
read SRCDIR
echo "Please input the destination directory"
read DEST


echo "#!/bin/bash" >> $FILE
echo "#Script to Update symbolic links on system startup" >> $FILE
echo "if [ !  "$DEST"/$1 ];" >> $FILE
echo "  then sudo ln -s "$SRCDIR"/* "$DEST"/;" >>$FILE
echo "fi" >> $FILE
echo "exit 0" >> $FILE

sudo chmod +x $FILE
exit 0
```

---

### Post by jyba on 2007-07-16
You're using $PROJECT as part of the $FILE variable while it's still got a value of "". If you move... 
```
echo "What would you like to call this project?"
read PROJECT
```
...up above the line...
```
FILE=$SYNC/"$PROJECT".sh
```
...it should work.

---

### Post by Mr. C. on 2007-07-16
There are a number of things that need to be addressed with your script.

[LIST]
[*]Place some diagnostic output so that you can debug !

[*]Check your input before blindly processing it.

[*]Examine the values of your variables, and understand how they are being set.

[*]Protect your variable expansion when values contain unexpected characters (such as whitespace).
[/LIST]

The solution you are creating is a bit convoluted.

Best of luck,
MrC

---

### Post by brennydoogles on 2007-07-16
> **Mr. C. said:**
> There are a number of things that need to be addressed with your script.

[LIST]
[*]Place some diagnostic output so that you can debug !

[*]Check your input before blindly processing it.

[*]Examine the values of your variables, and understand how they are being set.

[*]Protect your variable expansion when values contain unexpected characters (such as whitespace).
[/LIST]

The solution you are creating is a bit convoluted.

Best of luck,
MrC

ok, so to describe my goal a little bit more, let me give some examples of what I am working with. The first thing is a bin folder in my home directory. In this directory I store any scripts/programs that I have either written for myself, or found in some other way, and that I would like to be able to change or update at any time should I choose. For ease of use however, it is best to have these scripts in my /usr/bin/ folder so that I may call upon them at any time in terminal. This is most easily and efficiently done with symbolic links. The problem however, is that I find myself adding and removing programs from my bin folder often, leaving me with no idea whether or not a given program is linked or not. The purpose of this script (eventually) is to allow me to have a live updating link between my bin folder in my home, and the /usr/bin/ folder. The other use for the script for me is in my photo organization. My wife and I are both photographers, so in a short time we may amass a large quantity of photos. Right now we organize them by year, then month, then event, but if you are browsing for a particular photo and don't know when you took it, you can have a tough time finding it. However, by using symbolic links, you can more easily organize your photos by different types (weddings, photos at a certain place, birthdays, etc..) without having to take up the space of storing the photos in two places (plus we get to keep our current system which is very good in many ways).

The way that I have proposed doing this would be to have a folder full of scripts which would be called at boot time (or after a specified period of time during the day) to check each of these folders to see if they are all linked the way I would like, and if anything is not linked, to create links. The script that I have been working on today, is simply the script to create these new connections ( to make the scripts which will be periodically executed in the home/.foldersync/ folder), and also give me a way to manage these connections in the future. Does this make any sense?? I have updated the script, and will post it here. If anyone has the time to test it out and help me figure out exactly what I need to change to get it working well, I would greatly appreciate the input!!!

Most recent version of the script:```
#!/bin/bash
# Program to create syncronized folders
#########################################################################################################################################################################################################################	Variable Declaration	####################################################################################################################################################################################################################################

safemk () {
if [ ! -d $1 ]; 
  then mkdir $1; 
  chmod +rw $1; 
fi
}

SYNC=/home/$USER/.foldersync




#########################################################################################################################################################################################################################	Scripted Action		####################################################################################################################################################################################################################################

safemk $SYNC

echo "What would you like to call this project?"
read PROJECT
echo "Please input the source folder."
read SRCDIR
echo "Please input the destination directory"
read DEST
FILE=$SYNC/"$PROJECT".sh

echo "#!/bin/bash" >> $FILE
echo "#Script to Update symbolic links on system startup" >> $FILE
echo "" >> $FILE
echo "sym () {" >> $FILE
echo "if [ !  "$DEST"/$1 ];" >> $FILE
echo "  then sudo ln -s "$SRCDIR"/* "$DEST"/;" >> $FILE
echo "fi" >> $FILE
echo "}" >> $FILE
echo "for i in "$SRCDIR"/* ; do sym $i ; done" >> $FILE
echo "exit 0" >> $FILE

sudo chmod +x $FILE
exit 0
```

---

### Post by Mr. C. on 2007-07-17
Ok, I understand more what you want.

For the first goal, of having your bin utils available, why not just set your PATH, as in:

```
PATH=$HOME/bin:$PATH
```

This will allow you to run your scripts without creating all those needless symbolic lnks in /usr/bin.  You can place your programs anywhere you like, and tell the shell where to find them.  No need to create these links.

For your second goal, you're creating a poor man's database of assets using symlinks.  Have you considered:

[http://www.photovault.org/cgi-bin/trac.cgi](http://www.photovault.org/cgi-bin/trac.cgi)
[http://snap-photo.sourceforge.net/](http://snap-photo.sourceforge.net/)

or any of the other open source projects here:

[http://sourceforge.net/search/?type_of_search=soft&words=photo+organization](http://sourceforge.net/search/?type_of_search=soft&words=photo+organization)

MrC

---

### Post by brennydoogles on 2007-07-17
> **Mr. C. said:**
> Ok, I understand more what you want.

For the first goal, of having your bin utils available, why not just set your PATH, as in:

```
PATH=$HOME/bin:$PATH
```

This will allow you to run your scripts without creating all those needless symbolic lnks in /usr/bin.  You can place your programs anywhere you like, and tell the shell where to find them.  No need to create these links.

For your second goal, you're creating a poor man's database of assets using symlinks.  Have you considered:

[http://www.photovault.org/cgi-bin/trac.cgi](http://www.photovault.org/cgi-bin/trac.cgi)
[http://snap-photo.sourceforge.net/](http://snap-photo.sourceforge.net/)

or any of the other open source projects here:

[http://sourceforge.net/search/?type_of_search=soft&words=photo+organization](http://sourceforge.net/search/?type_of_search=soft&words=photo+organization)

MrC

Unfortunately as someone who is still somewhat new to linux/bash I have no idea what you are talking about. To be honest, most of the reason I decided to write a script for it was to learn more. I would love more detailed input about what you were talking about before though....

---

### Post by Mr. C. on 2007-07-17
Let's start with this.

To configure the shell to search your $HOME/bin, edit your your .bashrc file in your home directory.  Find an existing location where PATH is being set.  If there is one, place the following line after the existing setting, or add to that setting.  If there is not one, just add the following:

```
PATH=~/bin:$PATH
```

exactly as typed.  Then logout, and log back in.  Your home directory bin will now first be searched for your programs, before other program locations.

For more info on PATH and how the shell finds programs, start with slide 35, Week 5 Shells in the Coursework section here: [http://cis68a.mikecappella.com/](http://cis68a.mikecappella.com/)  (click the Get Notes).

MrC

---

### Post by brennydoogles on 2007-07-17
> **Mr. C. said:**
> Let's start with this.

To configure the shell to search your $HOME/bin, edit your your .bashrc file in your home directory.  Find an existing location where PATH is being set.  If there is one, place the following line after the existing setting, or add to that setting.  If there is not one, just add the following:

```
PATH=~/bin:$PATH
```

exactly as typed.  Then logout, and log back in.  Your home directory bin will now first be searched for your programs, before other program locations.

For more info on PATH and how the shell finds programs, start with slide 35, Week 5 Shells in the Coursework section here: [http://cis68a.mikecappella.com/](http://cis68a.mikecappella.com/)  (click the Get Notes).

MrC

Okay, I think I understand the idea now for the path variable, but now for learning purposes, how would i get my script working?? (I hate to leave a project unfinished... even if i ditch the completed work lol)

---

### Post by Mr. C. on 2007-07-17
For the links to your binaries?

I would just create a file containing source and destination lines, such as:

/home/me/bin/myprog /usr/bin/myprog

and then use a quick shell script to create the links, reading and looping on that file as input.  You can alternatively use the output of **ls** to give you the values, but that would imply a static destination directory (eg. /usr/bin).

To make this solution more generic...

I would create a script which asks for user input such as you project name, source directory, and destination directory.  This script would then examine the contents of the source directory, and it would create a datafile above (not the links).  The data file, name $project (the value you received from your input above) would be placed in your $HOME/projects directory perhaps, and would consist of lines such as:

sourcefile1 destfile1
sourcefile2 destfile2

So you'll end up with multiple project files: project1, gardening, family, etc.

I would then create the script above which loops through the contents of a data file, and creates the links for each line.  The script would do that for each project file.

Thus, you have only two scripts, centrally managed, which do distinct things: create the projects and create the links.  This separation makes it easier to manage.

MrC

---

