---
title: "Help with one more BASH Script"
date: 2007-06-12
forum: Programming Talk
---

### Post by brennydoogles on 2007-06-12
So this BASH script I have been working on is designed to aid in Data recovery via PhotoRec. When PhotoRec recovers files, it creates several hundred directories called recup_dir.*, each with several hundred files inside. Here is the script:
```
#!/bin/bash

#This is a script to move files recovered by PhotoRec into one folder, and should be run from your home

# Folder by typing sudo sh prorganize.sh into your terminal. If you have any questions, please write to #wishingforayer@gmail.com

set -o verbose
#sudo chmod -v 777 recup_dir.*
#for i in recup_dir.*/*; do sudo chmod -v 777 $i; done
mkdir -v prsaves

cd prsaves

mkdir -v images

mkdir -v video

mkdir -v text

mkdir -v docs

mkdir -v music

mkdir -v html

mkdir -v everythingelse

cd ..
sudo chmod 777 prsaves

echo "Now moving images"

#This command will scan all of your recup_dir.* folders for image files, and move them to your

# prsaves/images/ folder. To add a filetype just add *.filetype after *.psd

for i in recup_dir.*/*.jpg *.jpeg *.gif *.png *.psd; do mv -vf $i prsaves/images/; done

echo "Now moving video"

for i in recup_dir.*/*.mpeg *.avi *.mov *.mpg *.xvid; do mv -vf $i prsaves/video/; done

echo "now moving text files"

for i in recup_dir.*/*.txt; do mv -vf $i prsaves/text/; done

echo "Now moving documents"

for i in recup_dir.*/*.doc *.odt *.ods *.odp *.odg *.odf *.ppt; do mv -vf $i prsaves/docs/; done

echo "Now moving music"

for i in recup_dir.*/*.mp3 *.ogg *.wav; do mv -vf $i prsaves/music/; done

echo "Now movint HTML files"

for i in recup_dir.*/*.html; do mv -vf $i prsaves/html/; done

echo "Now moving whatever is left"

for i in recup_dir.*/*; do mv -vf $i prsaves/everythingelse/; done

rmdir recup_dir.*

echo "Have a great day!"
exit 0

```

and here is the error:

```
brendon@desktop:~$ sudo sh prorganize.sh
Password:
#sudo chmod -v 777 recup_dir.*
#for i in recup_dir.*/*; do sudo chmod -v 777 $i; done
mkdir -v prsaves
mkdir: cannot create directory `prsaves\r': File exists
cd prsaves
mkdir -v images
mkdir: cannot create directory `images\r': File exists
mkdir -v video
mkdir: cannot create directory `video\r': File exists
mkdir -v text
mkdir: cannot create directory `text\r': File exists
mkdir -v docs
mkdir: cannot create directory `docs\r': File exists
mkdir -v music
mkdir: cannot create directory `music\r': File exists
mkdir -v html
mkdir: cannot create directory `html\r': File exists
mkdir -v everythingelse
mkdir: cannot create directory `everythingelse\r': File exists
cd ..
sudo chmod 777 prsaves
echo "Now moving images"
Now moving images
#This command will scan all of your recup_dir.* folders for image files, and move them to your
# prsaves/images/ folder. To add a filetype just add *.filetype after *.psd
for i in recup_dir.*/*.jpg *.jpeg *.gif *.png *.psd; do mv -vf $i prsaves/images/; done
echo "Now moving video"
for i in recup_dir.*/*.mpeg *.avi *.mov *.mpg *.xvid; do mv -vf $i prsaves/video/; done
echo "now moving text files"
for i in recup_dir.*/*.txt; do mv -vf $i prsaves/text/; done
echo "Now moving documents"
for i in recup_dir.*/*.doc *.odt *.ods *.odp *.odg *.odf *.ppt; do mv -vf $i prsaves/docs/; done
echo "Now moving music"
for i in recup_dir.*/*.mp3 *.ogg *.wav; do mv -vf $i prsaves/music/; done
echo "Now movint HTML files"
for i in recup_dir.*/*.html; do mv -vf $i prsaves/html/; done
echo "Now moving whatever is left"
for i in recup_dir.*/*; do mv -vf $i prsaves/everythingelse/; done
rmdir recup_dir.*
echo "Have a great day!"
exit 0
prorganize.sh: 37: Syntax error: end of file unexpected (expecting "done")

```

Is this a DASH issue, or a scripting issue??

---

### Post by HackingYodel on 2007-06-12
I think the problem is with the > for i in recup_dir.*/*.mpeg *.avi *.mov *.mpg *.xvid; do mv -vf $i prsaves/video/; done
I don't think **for** loops will work like that.
[B]
You could try something like:

*images*=(jpg jpeg gif png psd)
*video*=(mpeg avi mov mpg xvid)
*text*=(txt)
*docs*=(doc odt ods odp odg odf ppt)
*music*=(mp3 ogg wav)
*html*=(htm html)

for i in ${*images*[*]}; do find /recup_dir/ -type f -name '*.'$i -exec mv {} ~/prsaves/*images*/ \;; done;[/B]

then use *video*, *text*, etc.. instead of images.  This assumes that all the recup_dir.* directories are under one master recup_dir directory.

Hope this helps!

---

### Post by brennydoogles on 2007-06-12
> **HackingYodel said:**
> I think the problem is with the 
I don't think **for** loops will work like that.
[B]
You could try something like:

*images*=(jpg jpeg gif png psd)
*video*=(mpeg avi mov mpg xvid)
*text*=(txt)
*docs*=(doc odt ods odp odg odf ppt)
*music*=(mp3 ogg wav)
*html*=(htm html)

for i in ${*images*[*]}; do find /recup_dir/ -type f -name '*.'$i -exec mv {} ~/prsaves/*images*/ \;; done;[/B]

then use *video*, *text*, etc.. instead of images.  This assumes that all the recup_dir.* directories are under one master recup_dir directory.

Hope this helps!

all of those commands work wonderfully when typed directly into terminal, but when put into a script for easy execution, it spits out the error message. And the way the recup_directories works is in your home folder you have recup_dir.1 recup_dir.2 all the way to recup_dir.150 up to recup_dir.999999999999..... I think you get the picture. It simply makes enough directories to store all of the files from one hard drive with about 500 files per directory. I know it's confusing, but thanks for the help!!!

---

### Post by HackingYodel on 2007-06-12
I think this could work, if I understand what you need.


```
#!/bin/bash

#This is a script to move files recovered by PhotoRec into one folder, and should be run from your home

# Folder by typing sudo sh prorganize.sh into your terminal. If you have any questions, please write to #wishingforayer@gmail.com

#sudo chmod -v 777 recup_dir.*
#for i in recup_dir.*/*; do sudo chmod -v 777 $i; done

safemk () {
if [ ! -d $1 ]; 
  then mkdir $1; 
  chmod 777 $1; 
fi
}

safemk prsaves

safemk prsaves/images

safemk prsaves/video

safemk prsaves/text

safemk prsaves/docs

safemk prsaves/music

safemk prsaves/html

safemk prsaves/everythingelse

echo "Now moving images"

#This command will scan all of your recup_dir.* folders for image files, and move them to your

# prsaves/images/ folder. To add a filetype just add filetype to array list

images=(jpg jpeg gif png psd)
for i in ${images[*]}; do find ~/recup_dir.*/ -type f -name '*.'$i -exec mv {} ~/prsaves/images \;; done;


echo "Now moving video"

video=(mpeg avi mov mpg xvid)
for i in ${video[*]}; do find ~/recup_dir.*/ -type f -name '*.'$i -exec mv {} ~/prsaves/video \;; done;


echo "now moving text files"

text=(txt)
for i in ${text[*]}; do find ~/recup_dir.*/ -type f -name '*.'$i -exec mv {} ~/prsaves/text \;; done;


echo "Now moving documents"

docs=(doc odt ods odp odg odf ppt)
for i in ${docs[*]}; do find ~/recup_dir.*/ -type f -name '*.'$i -exec mv {} ~/prsaves/docs \;; done;


echo "Now moving music"

music=(mp3 ogg wav)
for i in ${music[*]}; do find ~/recup_dir.*/ -type f -name '*.'$i -exec mv {} ~/prsaves/music \;; done;



echo "Now movint HTML files"

html=(htm html)
for i in ${html[*]}; do find ~/recup_dir.*/ -type f -name '*.'$i -exec mv {} ~/prsaves/html \;; done;


echo "Now moving whatever is left"

 find ~/recup_dir.*/ -type f -exec mv {} ~/prsaves/everythingelse \; 

#rmdir recup_dir.* commented out to be safe, remove when happy with script

echo "Have a great day!"
exit 0
```

If you are happy with the code remove the # before your rmdir command.

I attempted to follow the spirit of your script, I hope I did not vary more than your comfort level.


Hope this help!

---

### Post by brennydoogles on 2007-06-12
> **HackingYodel said:**
> I think this could work, if I understand what you need.


```
#!/bin/bash

#This is a script to move files recovered by PhotoRec into one folder, and should be run from your home

# Folder by typing sudo sh prorganize.sh into your terminal. If you have any questions, please write to #wishingforayer@gmail.com

#sudo chmod -v 777 recup_dir.*
#for i in recup_dir.*/*; do sudo chmod -v 777 $i; done

safemk () {
if [ ! -d $1 ]; 
  then mkdir $1; 
  chmod 777 $1; 
fi
}

safemk prsaves

safemk prsaves/images

safemk prsaves/video

safemk prsaves/text

safemk prsaves/docs

safemk prsaves/music

safemk prsaves/html

safemk prsaves/everythingelse

echo "Now moving images"

#This command will scan all of your recup_dir.* folders for image files, and move them to your

# prsaves/images/ folder. To add a filetype just add filetype to array list

images=(jpg jpeg gif png psd)
for i in ${images[*]}; do find ~/recup_dir.*/ -type f -name '*.'$i -exec mv {} ~/prsaves/images \;; done;


echo "Now moving video"

video=(mpeg avi mov mpg xvid)
for i in ${video[*]}; do find ~/recup_dir.*/ -type f -name '*.'$i -exec mv {} ~/prsaves/video \;; done;


echo "now moving text files"

text=(txt)
for i in ${text[*]}; do find ~/recup_dir.*/ -type f -name '*.'$i -exec mv {} ~/prsaves/text \;; done;


echo "Now moving documents"

docs=(doc odt ods odp odg odf ppt)
for i in ${docs[*]}; do find ~/recup_dir.*/ -type f -name '*.'$i -exec mv {} ~/prsaves/docs \;; done;


echo "Now moving music"

music=(mp3 ogg wav)
for i in ${music[*]}; do find ~/recup_dir.*/ -type f -name '*.'$i -exec mv {} ~/prsaves/music \;; done;



echo "Now movint HTML files"

html=(htm html)
for i in ${html[*]}; do find ~/recup_dir.*/ -type f -name '*.'$i -exec mv {} ~/prsaves/html \;; done;


echo "Now moving whatever is left"

 find ~/recup_dir.*/ -type f -exec mv {} ~/prsaves/everythingelse \; 

#rmdir recup_dir.* commented out to be safe, remove when happy with script

echo "Have a great day!"
exit 0
```

If you are happy with the code remove the # before your rmdir command.

I attempted to follow the spirit of your script, I hope I did not vary more than your comfort level.


Hope this help!

As a very beginning scripter (this is my first script, eve though my second and third are already finished :tongue: ) I don't understand what the changes you made mean. What is safemk?? Is it a command I need to install before using the script?? Thanks so much for the help!!

---

### Post by brennydoogles on 2007-06-12
> **brennydoogles said:**
> As a very beginning scripter (this is my first script, eve though my second and third are already finished :tongue: ) I don't understand what the changes you made mean. What is safemk?? Is it a command I need to install before using the script?? Thanks so much for the help!!

ok, nevermind. I had an idiot moment, and now i understand what you did. The script works perfectly now!! I edited it up to a final version, so here it is if anyone needs to use it ever!!!

```
#!/bin/bash
############################################################################################################################################################
####################################################		Developer Comments		############################################################
############################################################################################################################################################
#This is a script to move files recovered by PhotoRec into one folder, and should be run from your home folder by typing sudo sh prorganize.sh into your #terminal.
#
# If you have any questions, please write to wishingforayer@gmail.com
#
############################################################################################################################################################
#####################################################		Thanks to		####################################################################
############################################################################################################################################################
#Thanks to Ubuntuforums users Hymntolife and Hackingyodel for the technical know-how and advice to get this script running properly!!
#
#
#
############################################################################################################################################################
#####################################################		Variable Declaration		############################################################
############################################################################################################################################################

safemk () {
if [ ! -d $1 ]; 
  then mkdir $1; 
  chmod 777 $1; 
fi
}
## If you would like to add another type of file to any category, you may add it here.
images=(jpg jpeg gif png psd)
video=(mpeg avi mov mpg xvid)
text=(txt)
docs=(doc odt ods odp odg odf ppt)
music=(mp3 ogg wav)
html=(htm html)
############################################################################################################################################################
#####################################################		Scripted Action			############################################################
############################################################################################################################################################
sudo chmod -v 777 recup_dir.*
for i in recup_dir.*/*; do sudo chmod -v 777 $i; done

safemk prsaves

safemk prsaves/images

safemk prsaves/video

safemk prsaves/text

safemk prsaves/docs

safemk prsaves/music

safemk prsaves/html

safemk prsaves/everythingelse

echo "Now moving images"

for i in ${images[*]}; do find ~/recup_dir.*/ -type f -name '*.'$i -exec mv {} ~/prsaves/images \;; done;


echo "Now moving video"

for i in ${video[*]}; do find ~/recup_dir.*/ -type f -name '*.'$i -exec mv {} ~/prsaves/video \;; done;


echo "Now moving text files"

for i in ${text[*]}; do find ~/recup_dir.*/ -type f -name '*.'$i -exec mv {} ~/prsaves/text \;; done;


echo "Now moving documents"

for i in ${docs[*]}; do find ~/recup_dir.*/ -type f -name '*.'$i -exec mv {} ~/prsaves/docs \;; done;


echo "Now moving music"

for i in ${music[*]}; do find ~/recup_dir.*/ -type f -name '*.'$i -exec mv {} ~/prsaves/music \;; done;



echo "Now moving HTML files"

for i in ${html[*]}; do find ~/recup_dir.*/ -type f -name '*.'$i -exec mv {} ~/prsaves/html \;; done;


echo "Now moving whatever is left"

 find ~/recup_dir.*/ -type f -exec mv {} ~/prsaves/everythingelse \; 

echo "Now deleting empty folders and unneccesary leftover files"

rmdir recup_dir.* 
rm photorec.ses

echo "Have a great day!"
exit 0
```

---

### Post by HackingYodel on 2007-06-12
```
safemk () {
if [ ! -d $1 ]; 
  then mkdir $1; 
  chmod 777 $1; 
fi
}
```

Bash allows us to use functions.  A function is constructed like this:

[B]name () {
     function body's code goes here
}[/B]

Our function *safemk* breaks down like this:

**if [ ! -d $1 ];**  <--**$1** is the first argument we pass to *safemk*, here we check if there is NOT (the** !**) a directory (** -d** ) by the name passed to *safemk* ( $1)

if the name passed to *safemk* is not a directory then **mkdir $1** creates it.
We then **chmod 777** the directory ( **$1**)

and close the if with a corresponding **fi **and finish our function with a closing** }**

Enter this at the command line:

[B]myecho () { 
  echo "You passed" $# "arguments to me"; 
  echo "The first was" $1 "and the current process number is" $$; 
}[/B]

then if you enter:

**myecho testing one two three**

you'll get:

[B]You passed 4 arguments to me
The first was testing and the current process number is 9009 [/B]  <-- of course your process number will be different.

I hope I didn't just confuse you more.
Does this help?

---

### Post by brennydoogles on 2007-06-12
> **HackingYodel said:**
> ```
safemk () {
if [ ! -d $1 ]; 
  then mkdir $1; 
  chmod 777 $1; 
fi
}
```

Bash allows us to use functions.  A function is constructed like this:

[B]name () {
     function body's code goes here
}[/B]

Our function *safemk* breaks down like this:

**if [ ! -d $1 ];**  <--**$1** is the first argument we pass to *safemk*, here we check if there is NOT (the** !**) a directory (** -d** ) by the name passed to *safemk* ( $1)

if the name passed to *safemk* is not a directory then **mkdir $1** creates it.
We then **chmod 777** the directory ( **$1**)

and close the if with a corresponding **fi **and finish our function with a closing** }**

Enter this at the command line:

[B]myecho () { 
  echo "You passed" $# "arguments to me"; 
  echo "The first was" $1 "and the current process number is" $$; 
}[/B]

then if you enter:

**myecho testing one two three**

you'll get:

[B]You passed 4 arguments to me
The first was testing and the current process number is 9009 [/B]  <-- of course your process number will be different.

I hope I didn't just confuse you more.
Does this help?

lol I basically understood what you were saying. Where do you learn the specifics of BASH scripting?? I would love to sit down for a week and pick your brain about random scripting ideas. Thank you so much for all of your help!!

---

### Post by HackingYodel on 2007-06-12
> **brennydoogles said:**
> lol I basically understood what you were saying. Where do you learn the specifics of BASH scripting?? I would love to sit down for a week and pick your brain about random scripting ideas. Thank you so much for all of your help!!

I'm just happy I can be of some help.  I'm really just learning the ins and outs of Bash myself and think I learn the most when I try to help other beginners. 

Some of the material I have found most useful includes:

***Shell Scripting Recipes A Problem-Solutions Approach* by Chris F.A. Johnson.**  This book is awesome, and Chris posts a lot on comp.unix.shell also.  I've learned the most from Chris, but all the kludge and mistakes are mine.

***Wicked Cool Shell Scripts* by Dave Taylor.**  I just picked this book up a couple of weeks ago, but love it already.  I was able to hack a script from this book to scrape my IP address from my wireless router and update my dynamic DNS when my IP changes.  Love it, love it.

I have a printout of the ***O'Reilly bash Quick Reference* by Arnold Robbins** PDF.  This is super handy for the basics without overloading you with details.  I'd guess 90% of my bash questions can be answered within its 64 pages.

Then there is my 5th edition ***Linux In A Nutshell*** that I could NOT live without.

I'm a big time reader.  BSD, Unix, Linux, programming, and pretty much anything to do with computers.  I can, and do often, find good information on the web, but really like having some printed material at hand.  Anything I know, I'm happy to share and look forward to learning together with everybody here at the Ubuntu forums.

---

### Post by Mr. C. on 2007-06-13
This might help walk you through scripting:

[http://cis68b1.mikecappella.com](http://cis68b1.mikecappella.com)

MrC

---

