---
title: "Need help adding zenity to a script"
date: 2012-11-25
forum: New to Ubuntu
---

### Post by linuxuser2012 on 2012-11-25
Hey guys, I was wondering if any linux gurus could help add zenity to a script. If anyone could show me what the script below would look like with zenity added to it would be greatly appreciated.


#!/bin/bash
dvdencoder=./dvd-it-encode.sh

if [ $# -lt 3 ]
then
echo \ 
echo Insufficient arguments. $#
echo Usage: $0 movies_to_process final_iso_image temp_workspace
echo \ 
echo Note that the movies_to_process can either be a list of movie files
echo given by a path with a wildcard or regular expression, or it can be 
echo a directory.  If a directory is given the script will process all
echo files in that directory - hope they are movies\!
echo \ 
sleep 4
fi

if [ ! -d $3 ]
then
  echo \ 
  echo Error:  temp workspace $3 is not a directory
  echo Usage: $0 dir_of_movies_to_process final_iso_image temp_workspace
  echo \ 
  exit 0
fi

if [ ! -w $3 ]
then
  echo \ 
  echo Error:  temp workspace $3 is not writeable
  echo Usage: $0 dir_of_movies_to_process final_iso_image temp_workspace
  echo \ 
  exit 0
fi

if [ -f $2 ]
then
  echo \ 
  echo Error:  $2 exists - please rename or use a different name or path 
  echo for your final iso image
  echo Usage: $0 dir_of_movies_to_process final_iso_image temp_workspace
  echo \ 
  exit 0
fi
if [ ! -w `dirname $2` ]
then
  echo \ 
  echo Error:  $2 is unwriteable please use a different path 
  echo for your final iso image
  echo Usage: $0 dir_of_movies_to_process final_iso_image temp_workspace
  echo \ 
  exit 0
fi

if [ ! -x $dvdencoder ]
then
echo \ 
echo Error: encoding script not available
echo \
exit 0
fi

cd $3
tmpdir=`pwd`/dvdit-`whoami`
bn=dvdit-`whoami`
cd -
mkdir -p $tmpdir || exit 0
mkdir $tmpdir/dvd || exit 0 
mkdir $tmpdir/iso || exit 0 
mkdir $tmpdir/mpg || exit 0 
mkdir $tmpdir/sources || exit 0 

isodir=$tmpdir/iso
mpgdir=$tmpdir/mpg
sources=$tmpdir/sources
dvddir=$tmpdir/dvd 
xmlfile=$tmpdir/mpg/xmlfile.xml
moviedir=$1

if [ -d "$moviedir" ]
then
  src=`cd $moviedir && pwd`
  moviedir="$src"
  echo processing all files in $moviedir hope they are movies ...
else 
  echo processing anything that matches $moviedir  ...
fi
echo pausing 5 seconds....
sleep 5
c=0
ls -1 $moviedir | while read m
do 
  c=`expr $c + 1`
  ln -s "$moviedir/$m" $sources/$c
  $dvdencoder "$mpgdir/$c.mpg" "$sources/$c"  || exit
done

echo "creating XML file ..."

echo "<dvdauthor>
 <vmgm>
 </vmgm>
 <titleset>
   <titles>
     <pgc>
" > $xmlfile
cd $mpgdir
for i in `ls -1 *mpg`
do
echo "	<vob file=\"$i\" />" >> $xmlfile
done

echo "
     </pgc>
   </titles>
 </titleset>
</dvdauthor>
" >> $xmlfile

echo "XML file done ..."
dvdauthor -o ../dvd -x xmlfile.xml
cd -
mkisofs -dvd-video -o $isodir/dvdit.iso -V DVD $dvddir
mv $isodir/dvdit.iso $2

if [ -f $2 ]
then
  rm -rf $tmpdir
fi

---

### Post by Vaphell on 2012-11-25
wrap it in ```
[/co****de] tags to make your code easier on the eyes
what is zenity supposed to do in this script?



- use $() instead of ``

- there are readily available variables that can do that
[code]cd $3
tmpdir=`pwd`/dvdit-`whoami`
bn=dvdit-`whoami`
```
```
cd $3
tmpdir="$PWD"/dvdit-$USER
bn=dvdit-$USER
```


- don't use ls for that
```
[COLOR="Red"]ls -1 $moviedir[/COLOR] | while read m
do
  ln -s "$moviedir/$m" $sources/$c

```
```
for m in "$moviedir"/*
do
  ln -s "$m" $sources/$c
```

- bash can do integer arithmetic just fine
```
c=`expr $c + 1`
```
```
((c++))
```

- again, ls is bad
```
for i in [COLOR="Red"]`ls -1 *mpg`[/COLOR]
do
```
```
for i in *mpg
do
```

---

### Post by linuxuser2012 on 2012-11-26
I was asked to make it graphical using zenity I just have no idea where to add it in the script.

---

### Post by Vaphell on 2012-11-26
read
```
zenity --help
zenity --help-file-selection
```

eg
```
some_dir=$( zenity --file-selection --directory )
```
will allow you to select single dir

---

### Post by linuxuser2012 on 2012-11-26
Do you find that in the terminal sorry im a total noob this has just been impossible for me i was wondering if anyone could show me what the first section of the script would look like with zenity added to it.

---

### Post by linuxuser2012 on 2012-11-26
will echo still be in the script with zenity added or will echo be removed?

---

### Post by Vaphell on 2012-11-26
script using zenity works the same, the only difference is that instead of using command line parameter or *read* to feed data to it you get a shiny window that closes itself as soon as its job is done

try this example
```
#!/bin/bash

# select files
IFS='|' read -ra **files** < <( zenity --file-selection --multiple --title="Select files" --file-filter="all files|*.*" --file-filter="MPG files|*.mpg *.mpeg" --file-filter="AVI files|*.avi" )

# iso name
**iso**=$( zenity --entry --text "enter name" --title "Iso name" )

# workspace
**workspace**=$( zenity --file-selection --directory --title "Workspace" )

# print out entered values
echo "FILES:"
for **f** in **"${files[@]}"**; do echo **"$f"**; done
echo "ISO NAME: **$iso**"
echo "WORKSPACE: **$workspace"**

```

---

### Post by linuxuser2012 on 2012-11-27
Am i adding the file name from my script to this example?

---

### Post by linuxuser2012 on 2012-11-27
Im sorry im just really really confused ive read alot of tutorials and everything Im just really lost.

---

### Post by Vaphell on 2012-11-29
chill out and read about bash. It's not rocket science.


that example code is pretty much equivalent to passing parameters to script
workspace in your code is $3
instead of workspace=$3 you can do workspace=$( zenity .... ) - effect is the same, $workspace holds the proper value and can be used in later parts of the script.

---

