---
title: "Recursive copy and rename of *.jpg, *.avi etc"
date: 2012-12-26
forum: New to Ubuntu
---

### Post by bashwannabe on 2012-12-26
Hi,

I have a drive with a real messed up set of directories/folders with lots of *.jpg, *.avi.  The mess-up, unsurprisingly is the result of i-photo...

I need to search through the whole structure and pull out all the relevant files to one folder.  The problem is that a lot of the files (images from my camera) have the same name, such as DSC_0001.jpg - not a problem now because they're in different folders...

How can i recursively work through the folder system, copy all the pictures (including the hidden pictures, of which there seem to be many) in to a single new folder and rename them with a unique name?

Thank you -
:KS

---

### Post by acimi66 on 2012-12-26
I am just going through  "T[HE LINUX COMMAND LINE.pdf]("http://iweb.dl.sourceforge.net/project/linuxcommand/TLCL/09.12/TLCL-09.12.pdf")" and this would be a great project.

I hope this helps

---

### Post by papibe on 2012-12-26
Hi bashwannabe. Welcome to the forums ):P

You can accomplish that using the command 'find' and using the --backup option on the command mv to avoid overwriting your files.

Take a look at this [thread]("http://ubuntuforums.org/showthread.php?t=2086723&highlight=mv+backup+find") with a similar concern a several suggestions.

Let us know how it goes.
Regards.

---

### Post by bashwannabe on 2012-12-27
Thank you both for your help.  It looks like the thread you posted is exactly what i need!  :KS

---

### Post by bashwannabe on 2012-12-28
Thank you Papibe - i have been trying out the code and it works.  when i have several files with the same name (the files might be different) the back up command does not overwrite, making for example:

pic_001.jpg
pic_001.jpg.~2~
pic_001.jpg.~3~
pic_001.jpg.~4~

etc.

Is there some code i could use to take the back-up files (the ones ending in ~) and give them the jpg extension so that i can look at them and manipulate them as if they were normal jpg and see them in a normal finder or home-folder window?

The names don't matter so much as the ability to easily look at and deal with each file.

Thank you and regards,

:KS

---

### Post by steeldriver on 2012-12-28
you could do something like this - just moves the unique numeric part of the ~n~ suffix to the other side of the .jpg extension

```
$ rename -nv 's/([^.]*)[.]jpg[.]~([0-9]+)~/$1_$2.jpg/' *.jpg.*
pic_001.jpg.~2~ renamed as pic_001_2.jpg
pic_001.jpg.~3~ renamed as pic_001_3.jpg
pic_001.jpg.~4~ renamed as pic_001_4.jpg

```Have a play and decide how you want the names to look - then when you're ready, remove the 'n' option to make it run for real 

(you could use ($2) instead of _$2 or whatever)

---

### Post by Vaphell on 2012-12-28
```
rename -v 's/([^.]+)[.]([^.]+)[.]~(.+)~$/$1__$3.$2/' *~*~
```

it is probably more scary than it needs to be, but i thought it's good to make it more universal and it will work with any backed up file type. That expression will reuse the parts enclosed in parentheses:
(name).(extension).~(number)~ => name__number.extension

edit: steeldriver posted pretty much the same thing, but with fixed jpg part :)

---

### Post by bashwannabe on 2012-12-29
Hi thank you steeldriver and vaphell  - i have tried each of your expressions and in each case i get an error - 

Unknown option : 3
Unknown option : 8
Unknown option : .
Unknown option : j
Unknown option : p
Unknown option : g
Unknown option : .
Unknown option : ~
Unknown option : 1
Unknown option : ~
Usage: rename [-v] [-n] [-f] perlexpr [filenames]

I've double checked and i am using your code verbatim inside the folder with all the *.jpg files.

do i need to download/initiate perl?

---

### Post by steeldriver on 2012-12-29
are you maybe missing a space between the options ( -nv ) and the expression (the 's/.../.../ ' part)?

```
$ rename [COLOR=Red]-nv's/[/COLOR]([^.]*)[.]jpg[.]~([0-9]+)~/$1_$2.jpg/' *.jpg.*
Unknown option: s
Unknown option: /
Unknown option: (
Unknown option: [
Unknown option: ^
Unknown option: .
Unknown option: ]
Unknown option: *
Unknown option: )
Unknown option: [
Unknown option: .
Unknown option: ]
Unknown option: j
Unknown option: p
Unknown option: g
Unknown option: [
Unknown option: .
Unknown option: ]
Unknown option: ~
Unknown option: (
Unknown option: [
Unknown option: 0
Unknown option: 9]+)~/$1_$2.jpg/
Usage: rename [-v] [-n] [-f] perlexpr [filenames]
$
$ rename [COLOR=Red]-nv 's/[/COLOR]([^.]*)[.]jpg[.]~([0-9]+)~/$1_$2.jpg/' *.jpg.*
pic_001.jpg.~2~ renamed as pic_001_2.jpg

```

---

### Post by bashwannabe on 2012-12-29
Hi steeldriver - i've posted below the error i get - also checked perl version: it is perl 5 version 12

$ rename -nv 's/([^.]*)[.]jpg[.]~([0-9]+)~/$1_$2.jpg/' *.jpg.*
Unknown option: 3
Unknown option: 8
Unknown option: .
Unknown option: j
Unknown option: p
Unknown option: g
Unknown option: .
Unknown option: ~
Unknown option: 1
Unknown option: ~
Usage: rename [-v] [-n] [-f] perlexpr [filenames]
$

---

### Post by steeldriver on 2012-12-29
OK I think I know the problem - you have a file whose name starts with a '-' character and somehow that is getting interpreted as additional options:

```
$ > '-38.jpg.~1~'
$ 
$ rename -nv 's/([^.]*)[.]jpg[.]~([0-9]+)~/$1_$2.jpg/' *.jpg.*
Unknown option: 3
Unknown option: 8
Unknown option: .
Unknown option: j
Unknown option: p
Unknown option: g
Unknown option: .
Unknown option: ~
Unknown option: 1
Unknown option: ~
Usage: rename [-v] [-n] [-f] perlexpr [filenames]

```Try adding '--' after the options so that the shell knows that everything beyond that is *not* part of the option list:

```
$ rename -nv **[COLOR=Red]--[/COLOR]** 's/([^.]*)[.]jpg[.]~([0-9]+)~/$1_$2.jpg/' *.jpg.*
-38.jpg.~1~ renamed as -38_1.jpg
pic_001.jpg.~2~ renamed as pic_001_2.jpg

```You can use Vaphell's nice expression instead of course

---

### Post by CaptainMark on 2012-12-29
If you install the program jhead found in the standard repos then it can rename the files as you move them based on the photos metadata, heres a nice few lines for you ```
mkdir photos
find ./ -iname *.jpg -exec mv {} ./photos/ \; |xargs find ./ -iname *.jpg |xargs jhead -n%d-%m-%Y\ %H:%M:%S
```This creates a folder named photos, then find any files ending in .jpg or .JPG and moves them to the new photos folder also it renames them to the format "date-month-year hour:minute:second.jpg" this works for all jpegs as long as two wern't taken at exactly the same second, you could then sort them into folders if you wanted using jhead again, I have a script which automates this which runs on login, heres the chunk you'd need if you'd like the make use of it, you could literaly paste this into a terminal so long as all the photos are in the $HOME/Pictures folder it should work fine```
IFS=$'\n'
# determine files for iteration
for photo in $(ls $HOME/Pictures/ | grep -i -e jpg -e jpeg); do
	# obtain photo timestamp
	timestamp=$(jhead $HOME/Pictures/$photo | grep Date/Time)
	# check for successful timestamp
	if [ -z $timestamp ]; then
		let errors=$errors+1
	fi
	# obtain year and month 
	year=${timestamp:15:4}
	month=${timestamp:20:2}
	# create directory, move and rename photo
	if [ $year ] && [ $month ]; then
		mkdir -p $HOME/Pictures/$year/$month; mv -n $HOME/Pictures/$photo $HOME/Pictures/$year/$month/ && let count=$count+1
		jhead -n%d-%m-%Y\ %H:%M:%S $HOME/Pictures/$year/$month/$photo
	fi
done
```As for the .avi I cant be as helpful I'm afraid

---

### Post by Vaphell on 2012-12-30
```
IFS=$'\n'
for photo in $(ls $HOME/Pictures/ | grep -i -e jpg -e jpeg); do
...
```
very very fugly - redefined IFS, ls used to fuel the loop...

straightforward globs
```
for photo in $HOME/Pictures/*.[jJ][pP][gG] $HOME/Pictures/*.[jJ][pP][eE][gG]; do
```

find+while read
```
while IFS= read -rd $'\0' photo
do
  ...
done < <( find $HOME/Pictures/ -iregex '.*jpe?g$' -type f -print0 )
```

---

### Post by bashwannabe on 2012-12-31
Steeldriver, your last post works, thank you!

So now i have three folders containing hundreds of thousands of *.jpg - many of which are copies, with different names, some as a result of the backup copy we did earlier, many because of the way the images were stored previously.  Here there may be copies of the pictures in different resolutions.

Based on what Captain Mark is saying, is it possible to write a script which will go through all three folders, and put all the pictures into one folder, ensuring that only one copy of the same *picture*, with its highest available resolution, is saved?

This sounds complicated to me.  Thank you all for your help so far - i never thought i would get this far in the first place!!

---

### Post by CaptainMark on 2012-12-31
> **Vaphell said:**
> very very fugly - redefined IFS, ls used to fuel the loop...I'm only a noob myself by most standards so be nice on the criticism, I'll take on board your code though,
Thanks

---

### Post by steeldriver on 2012-12-31
> **bashwannabe said:**
> Steeldriver, your last post works, thank you!

Glad it worked! sorry about the couple of false starts

> **bashwannabe said:**
> Based on what Captain Mark is saying, is it possible to write a script which will go through all three folders, and put all the pictures into one folder, ensuring that only one copy of the same *picture*, with its highest available resolution, is saved?

I think something like that might be possible - using the exif metadata in the jpg files - I leave it to one of the picture experts to answer though

---

### Post by Vaphell on 2012-12-31
> I'm only a noob myself by most standards so be nice on the criticism, I'll take on board your code though,
Thanks

sorry about that, but seeing ls output processing in scripts gets old really fast ;-) It's the very first error mentioned here:
[http://mywiki.wooledge.org/BashPitfalls](http://mywiki.wooledge.org/BashPitfalls)


is there any straightforward rule that says two images of different sizes are related? do they share the same name? exif data? because if not, then you'd have to use imagemagick tools to apply some fuzzy logic to determine the similarity (scale temp copies of images to common size and calculate correlation). While doable, it would be very very annoying.

---

### Post by CaptainMark on 2013-01-01
I don't think jhead would differeniate the two, I just tested and if you have two images with the same timestamp down to the second it will name them DD-MM-YY HH:MM.jpg and DD-MM-YY HH:MMa.jpg depending on which is first, I'm sure there would be a way to filter all conflicting images to a seperate folder for analysis but I don't know of a way to automate this to choose to keep the highest resolution

EDIT: Perhaps Vaphell could help, you seem to know bash well, could one rearrange the script to use jhead on all *jpg's starting with the largest file first working its way to the smallest file, this way a find ./ -name *a.jpg would find all the smaller versions of the duplicate files

---

