---
title: "Simple bash script problem"
date: 2010-04-13
forum: Programming Talk
---

### Post by stereomuffin on 2010-04-13
**_EDIT: nevermind, i fixed it using sed (pasted my fix in the bottom)...this thread can be closed._**

I am just starting out so be gentle ;)[http://g-scripts.sourceforge.net/](http://g-scripts.sourceforge.net/)

I have this simple script that i have placed in my home directory under:
.gnome/nautilus-scripts

It resizes images to a user specified size (using Zenity and Imagemagick) and if necessary (in case filesize is still to large change the quality)

> [PHP]
#!/bin/bash
# resize pictures and if necessary change quality
# you need Zenity and Imagemagick installed
  which convert > /dev/null
if [ $? -eq 1 ]; then
  echo "Geen Imagemagick gevonden!"
  exit 1
fi
  which zenity > /dev/null
if [ $? -eq 1 ]; then
  echo "Geen Zenity gevonden!"
  exit 1
fi
while [ $# -gt 0 ]; do
  picture="$1"
  SIZE=`zenity --list --title="Resize "$picture"?" --radiolist --column="Check" --column="Size" "" "80x60" "" "320x240" "" "640x480" "" "800x600" "" "1024x768"`
if [ $? -eq 1 ]; then
  exit 1
fi
convert -resize $SIZE "$picture" "resized-$picture"
  jpg_size=`du -h "resized-$picture" | cut -f 1`
  QUALITY=`(zenity --scale --text "Is $jpg_size small enough?If not: change quality:" --min-value=2 --max-value=100 --value=40 --step 2)`
/usr/bin/convert -quality $QUALITY "resized-$picture" "kleiner-$picture"
  shift
done
[/PHP]

Whenever i right click a jpg in nautilus now and run my script everything works as expected (the filename ends up how i intended it) however when i run it from the terminal it doesn't work. 

It goes wrong here: >  convert -resize $SIZE "$picture" "resized-$picture" 
Now bash outputs: > 
convert: unable to open image `resized-./foto1.JPG': No such file or directory @ blob.c/OpenBlob/2439.
du: cannot access `resized-./foto1.JPG': No such file or directory 

I see what the problem is, but i don't know how to fix it (placing -resized after my variable inverts the problem so to speak...lol - now it goes correctly in bash terminal but the resulting filename places "resized" AFTER the extension) its very simple i'm sure...hope to learn something. Thanks for your help :)

FIXED:

>  [PHP]
#!/bin/bash
# resize pictures and if necessary change quality
# you need Zenity and Imagemagick installed
  which convert > /dev/null
if [ $? -eq 1 ]; then
  echo "Geen Imagemagick gevonden!"
  exit 1
fi
  which zenity > /dev/null
if [ $? -eq 1 ]; then
  echo "Geen Zenity gevonden!"
  exit 1
fi
while [ $# -gt 0 ]; do
  picture=$1
  SIZE=`zenity --list --title="Resize $picture?" --radiolist --column="Check" --column="Size" "" "80x60" "" "320x240" "" "640x480" "" "800x600" "" "1024x768"`
if [ $? -eq 1 ]; then
  exit 1
fi
  resized_file=`echo $picture | sed 's/\.\w*$/-resized.jpg/'`
  reduced_quality_file=`echo $picture | sed 's/\.\w*$/smaller.jpg/'`
convert -resize $SIZE $picture $resized_file
jpg_size=`du -h $resized_file | cut -f 1`
  QUALITY=`(zenity --scale --text "Is $jpg_size klein genoeg? Zoniet: pas de kwaliteit aan:" --min-value=2 --max-value=100 --value=40 --step 2)`
/usr/bin/convert -quality $QUALITY $resized_file $reduced_quality_file
  shift
done [/PHP]

---

### Post by geirha on 2010-04-13
Since you did post your script, I thought I'd give you some comments on that script, because you are doing a few odd things there.

1.
```
  which convert > /dev/null
if [ $? -eq 1 ]; then
  echo "Geen Imagemagick gevonden!"
  exit 1
fi

```
«which» is an external command, and bash can do that check itself with the built-ins «command» and «type». Also, checking the value of $? is pointless when you only need to know if it's true or false.
```

if ! command -v convert >/dev/null; then
  echo "no imagemagick..."
  exit 1
fi

```
[http://mywiki.wooledge.org/BashFAQ/081](http://mywiki.wooledge.org/BashFAQ/081)

2.
```

while [ $# -gt 0 ]; do
  picture=$1
  «...snipp...»
  shift
done

```
Just iterate "$@" with a for-loop «for picture in "$@"; do...», though actually, you can omit the «in "$@"» part because that's the default. (see «help for»)
```

for picture; do
  ...
done

```

3.
```

  resized_file=`echo $picture | sed 's/\.\w*$/-resized.jpg/'`
  reduced_quality_file=`echo $picture | sed 's/\.\w*$/smaller.jpg/'`

```
Another thing bash can do without the use of external commands
```

  resized_file=${picture%.*}-resized.jpg
  reduced_quality_file=${picture%.*}smaller.jpg

```
[http://mywiki.wooledge.org/BashFAQ/073](http://mywiki.wooledge.org/BashFAQ/073)

4.
```
convert -resize $SIZE $picture $resized_file
```
In your initial script you had $picture and $resized_file properly quoted. Why did you remove them? Without those quotes, it will break on filenames with whitespace and other special characters.

5.
```

  QUALITY=`(zenity --scale --text "Is $jpg_size klein genoeg? Zoniet: pas de kwaliteit aan:" --min-value=2 --max-value=100 --value=40 --step 2)`

```

Those parenthesis are generating another subshell in the subshell created by ``. That's pointless overhead.

Also, in general it's better to use $() rather than ``.
[http://mywiki.wooledge.org/CommandSubstitution](http://mywiki.wooledge.org/CommandSubstitution)

---

### Post by MadBillyGoat on 2010-09-27
[http://ubuntuforums.org/showthread.php?t=976945](http://ubuntuforums.org/showthread.php?t=976945)

There is a plugin for this.

I know it is solved but a different option never hurts.

Thanks
Madbillygoat

---

### Post by MadBillyGoat on 2010-09-27
> **MadBillyGoat said:**
> [http://ubuntuforums.org/showthread.php?t=976945](http://ubuntuforums.org/showthread.php?t=976945)

There is a plugin for this.

I know it is solved but a different option never hurts.

Thanks
Madbillygoat


sudo apt-get install nautilus-image-converter


 :)

---

