---
title: "Music cover script"
date: 2008-01-23
forum: Programming Talk
---

### Post by bkanuka on 2008-01-23
If anyone knows how to do this, I would be really grateful:
I need a script that will go through my music folders, find the largest picture file in each folder (by file size is fine), convert it to .png if it isn't already, rename it cover.png, and remove all other picture files in that directory.
All picture files are .jpg or .png; my directory structure is [artist]/[album]/[music and covers], in other words, */*/*.png or */*/*.jpg

Am I asking too much? Step by step it doesn't seem too complicated, I just don't know how to do such things as find the largest image file and pipe that into imagemagick.

Again, any help is appreciated.

-bkanuka

---

### Post by bkanuka on 2008-01-24
So I've been working on this for a while and so far I have this,
```
ls -S --hide=*.mp3 . | head -1 
```
That returns the image file that I need to work with (granted I'm in an album directory).  I just don't know what to do with this now :confused:

---

### Post by bkanuka on 2008-01-24
Alright, I'm doing pretty well on my own. This almost does what I want
```
#!/bin/bash

FILE=$(ls -S --hide=*.mp3 . | head -1)
echo $FILE

convert $FILE cover.png

OTHERS=$(ls -1 | grep -v '\.mp3$' | grep -v '\cover.png$' | xargs)

rm -i $OTHERS
```
It's probably pretty choppy; it is my first bash script ever.  The 'rm -i' is there so that it doest remove the script itself.  I need to find a way for this to run on every directory ./*/*
Anybody is welcome to chime in! :)

---

### Post by nick_h on 2008-01-24
Use *find* to call your script with something like:
```
find . -type d -exec script.sh '{}' \;
```
Put your script in your ~/bin directory or somewhere else in your path.
The variable $1 will contain the directory name which you use in the script.

---

### Post by bkanuka on 2008-01-24
Thanks for the help, but I must not understand what I must do with $1.  If I put my coverpic.sh in /usr/bin and run your command, I get:
```
~/Documents/Music$ find . -type d -exec coverpic.sh '{}' \;
.
Top 500 Rock
convert: unable to open image `Rock': No such file or directory.
xargs: unmatched single quote; by default quotes are special to xargs unless you use the -0 option
rm: cannot lstat `10': No such file or directory
rm: cannot lstat `Years': No such file or directory
rm: cannot lstat `1200': No such file or directory
rm: cannot lstat `Micrograms': No such file or directory
rm: cannot remove directory `2Pac': Is a directory
rm: cannot lstat `30': No such file or directory
rm: cannot lstat `Seconds': No such file or directory
rm: cannot lstat `To': No such file or directory
rm: cannot lstat `Mars': No such file or directory
rm: cannot lstat `3': No such file or directory
rm: cannot lstat `Doors': No such file or directory
rm: cannot lstat `Down': No such file or directory

```
So obviously there is a problem with spacing in the directory names.

---

### Post by nick_h on 2008-01-24
It looks like you need quotes around the variables.

$1 will contain the directory name for each directory visited.  This will be available to you in $1 so you can add it to the front of your filenames.  -exec runs in the starting directory so this will be helpful.

You could also consdier rusing -execdir which runs in each directory rather than the starting directory.

---

### Post by bkanuka on 2008-01-24
nah, I figured that much out. The problem is a little bigger than that. See the ls | xargs is listing a bunch of folder names (most of which have spaces) in one long string like> 10 Years 1200 Micrograms 2Pac 30 Seconds To Mars 3 Doors Down +44 50 Cent Abba and than that gets fed to rm, causing a bunch of errors.
Even if ls listed only pictures, some will have spaces and rm will not like.
Any suggestions for purging a folder of everything but *.mp3 and cover.png?

---

### Post by nick_h on 2008-01-24
Maybe with something like:
```
for f in *; do
	if [ "${f: -4}" != ".mp3" ] && [ "$f" != "cover.png" ]; then
		rm "$f"
	fi
done
```

---

### Post by bkanuka on 2008-01-24
I think I got it.  Its a shame it couldn't all be in one script tho.  The script is this:```
#!/bin/bash

cd "$1"
FILE=$(ls -S --hide=*.mp3 . | head -1)
echo $FILE

convert "$FILE" cover.png
``` put that in /usr/bin/ than cd to my Music directory and run this, ```
find -mindepth 2 -type d -execdir /usr/bin/coverpic.sh '{}' \;
```which creates all the cover.png's, and than I cleaned up the folders with this command, ```
find . \( \! -name "*\.mp3" \! -name "*\cover.png" -type f \) -print0 | xargs -0 /bin/rm -fv
```

This turned out to be a lot more complicated than I would have liked it.  The above worked on a test folder, but now that I'm running it on a massive folder ~70Gb it's not echoing anything.  Maybe 'find' needs to index everything before it gets to work?
Assuming this works, could someone help fit it all into one script? because it is something I would like to use here and there.

Thanks for the help.

---

### Post by nick_h on 2008-01-24
I don't see why a *find* like that shouldn't work.  You could put it in your script.

Make sure you quote the -name "*.mp3" : see the section on non-bugs in the *find* manual page.

---

### Post by bkanuka on 2008-01-24
Turns out that that last command I had in my previous post was pretty dangerous.  It started deleting everything out of my music folder.  I killed it before too much damage and edited the post to a LITTLE safer command.  It still deleted everything that I had in .ogg .flac and whatnot :s
This latest command will work in my script a little better, so I'm going to try to consolidate it.  Probably not now though becasue I accomplished what I wanted to, and have other work to do.
Thanks.

And for anyone who's reading this later, this will work ONLY on mp3 files, and probably very specifically to my situation.  Don't go running commands that have "rm" in them without knowing EXACTLY what you're doing.

---

