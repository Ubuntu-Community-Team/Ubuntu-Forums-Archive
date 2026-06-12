---
title: "xml background generator"
date: 2010-03-02
forum: Programming Talk
---

### Post by DarkJimmy on 2010-03-02
Hi, I've started learning some bash scripting and made this little script to give some life to my desktop.
I'm not yet too familiar with the syntax and find it a little weird..

Rate my code!
> #!/bin/sh
#
# Background XML generator v0.2
# author: darkjimmy062
# Currently supports directories with images only

# alter the values to your need
duration='120.0'  #duration of wallpaper
transition='2.5'  #duration of transitions between wallpapers


# -- messy code that does the job --

NOFILE=64
[ -z $1 ] &&  echo "Background XML generator by darkjimmy062\nUsage: ./bgxmlgen.sh <directory>" && exit $NOFILE


directory=${1}

myfile=".temp"
ls $directory > $myfile

basefile="slides"

count=0

firstimage='first_image'
oldimage='old_image'

started=0

#Printing
{
printf "<background>\n\t<starttime>\n\t\t<year>2009</year>\n\t\t<month>08</month>\n\t\t<day>04</day>\n\t\t<hour>00</hour>\n\t\t<minute>00</minute>\n\t\t<second>00</second>\n\t</starttime>"
  while read image
     do
         count=`expr $count + 1`
         
        if [ $started -eq 0 ]
        then
            printf "\n\t<static>\n\t\t<duration>$duration</duration>\n\t\t<file>$directory$image</file>\n\t</static>"
            oldimage=$image
            firstimage=$image
            started=1
        else
            printf "\n\t<transition>\n\t\t<duration>$transition</duration>\n\t\t<from>$directory$oldimage</from>\n\t\t<to>$directory$image</to>\n\t</transition>\n\t<static>\n\t\t<duration>$duration</duration>\n\t\t<file>$directory$image</file>\n\t</static>"
            oldimage=$image
        fi
     done < "$myfile"
printf "\n\t<transition>\n\t\t<duration>$transition</duration>\n\t\t<from>$directory$oldimage</from>\n\t\t<to>$directory$firstimage</to>\n\t</transition>"
printf "\n</background>"

} > $basefile.xml

rm $myfile
echo "$count file(s) processed.\nOutput file is $basefile.xml"


---

