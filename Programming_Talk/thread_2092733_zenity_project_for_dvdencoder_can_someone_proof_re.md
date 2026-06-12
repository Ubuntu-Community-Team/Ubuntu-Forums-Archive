---
title: "zenity project for dvdencoder can someone proof read my workneed help with argument"
date: 2012-12-08
forum: Programming Talk
---

### Post by 3drender on 2012-12-08
#!/bin/bash

[SIZE=3]# Won't run after my original sanity  checks - there aren't any #arguments at all (or if I #have to enter them  on the command line #then it isn't using zenity properly).[/SIZE][SIZE=3] #Don't pester the user wtih excessive dialogs (when it  creates all the #temp dirs and such)
[/SIZE]



dvdencoder=$( zenity --file-selection --title="dvd-it-encode.sh" --directory --filename=$HOME/)

if [ $# -lt 3 ]
then
echo \ 
echo zenity --error --text="Insufficient arguments." $#
echo Usage: $0 movies_to_process final_iso_image temp_workspace
echo \ 
echo zenity --info --title="Note that the movies_to_process can either be a list of movie files given by a path with a wildcard or regular expression, or it can be a directory.  If a directory is given the script will process all files in that directory - hope they are movies\!"
echo \ 
sleep 4
fi

if [ ! -d $3 ]
then
  echo \ 
  echo zenity --error --text="temp workspace $3 is not a directory"
  echo Usage: $0 dir_of_movies_to_process final_iso_image temp_workspace
  echo \ 
  exit 0
fi

if [ ! -w $3 ]
then
  echo \ 
  echo zenity --error --text="temp workspace $3 is not writeable"
  echo Usage: $0 dir_of_movies_to_process final_iso_image temp_workspace
  echo \ 
  exit 0
fi

if [ -f $2 ]
then
  echo \ 
  echo zenity --error --text="$2 exists - please rename or use a different name or path for your final iso image"
  echo Usage: $0 dir_of_movies_to_process final_iso_image temp_workspace
  echo \ 
  exit 0
fi
if [ ! -w `dirname $2` ]
then
  echo \ 
  echo zenity --error --text="$2 is unwriteable please use a different path for your final iso image"
  echo Usage: $0 dir_of_movies_to_process final_iso_image temp_workspace
  echo \ 
  exit 0
fi

if [ ! -x $dvdencoder ]
then
echo \ 
echo zenity --error --text="encoding script not available"
echo \
exit 0
fi

cd $3
tmpdir=$( zenity --file-selection --title="/dvdit-`whoami`" --directory --filename=$`pwd`/)
bn=$( zenity --file-selection --title="`whoami`" --directory --filename=$dvdit-)
cd -
mkdir -p $tmpdir || exit 0
mkdir $tmpdir/dvd || exit 0 
mkdir $tmpdir/iso || exit 0 
mkdir $tmpdir/mpg || exit 0 
mkdir $tmpdir/sources || exit 0 

isodir=$( zenity --file-selection --title="iso" --directory --filename=$tmpdir/)
mpgdir=$( zenity --file-selection --title="mpg" --directory --filename=$tmpdir/)
sources=$( zenity --file-selection --title="sources" --directory --filename=$tmpdir/) 
dvddir=$( zenity --file-selection --title="dvd" --directory --filename=$tmpdir/) 
xmlfile=$( zenity --file-selection --title="/mpg/xmlfile.xml" --directory --filename=$tmpdir/)
moviedir=$1

if [ -d "$moviedir" ]
then
  src=`cd $moviedir && pwd`
  moviedir="$src"
  echo zenity --info --title="Movie Directory Scan" --text="processing all files in $moviedir hope they are movies ..."
else 
  echo zenity --info --title="Movie Directory Scan" --text="processing anything that matches $moviedir  ..."
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

echo zenity --info --title="Notification" --text="creating XML file ..."

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
echo "    <vob file=\"$i\" />" >> $xmlfile
done

echo "
     </pgc>
   </titles>
 </titleset>
</dvdauthor>
" >> $xmlfile

echo zenity --info --title="Notification" --text="XML file done ...")
dvdauthor -o ../dvd -x xmlfile.xml
cd -
mkisofs -dvd-video -o $isodir/dvdit.iso -V DVD $dvddir
mv $isodir/dvdit.iso $2

if [ -f $2 ]
then
  rm -rf $tmpdir
fi

---

### Post by Vaphell on 2012-12-08
put your code in ```
[/c****ode]

comment out or delete the whole 'intro' where you perform checks on $1 $2 $3. You don't use any parameters yet still test for existence of dirs and call **exit 0**. No wonder script does nothing, it exits pretty much right off the bat.



[code][COLOR="Red"]for i in `ls -1 *mpg`[/COLOR] # WRONG!
[COLOR="Blue"]for i in *mpg[/COLOR]
```

this one is bad too
```
ls -1 $moviedir | while read m
do
c=`expr $c + 1`
ln -s "$moviedir/$m" $sources/$c
$dvdencoder "$mpgdir/$c.mpg" "$sources/$c" || exit
done
```

```
for m in "$moviedir"/*
do
  (( c++ ))
  ln -s "$m" "$sources"/$c
  $dvdencoder "$mpgdir/$c.mpg" "$sources/$c" || exit
done
```
always quote variables unless you are absolutely sure you won't have any whitespace in them. Currently your script is rather spotty in this aspect.

---

