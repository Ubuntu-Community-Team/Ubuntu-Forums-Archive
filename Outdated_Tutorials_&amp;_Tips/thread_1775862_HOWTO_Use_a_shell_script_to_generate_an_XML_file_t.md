---
title: "HOWTO: Use a shell script to generate an XML file to cycle your background picture"
date: 2011-06-05
forum: Outdated Tutorials &amp; Tips
---

### Post by detrix42 on 2011-06-05
Hello everyone. This is my first attmpt at posting a tutorial/how to. So here is some background:

Awhile back, I played around with finding a way to have my desktop background picture to change, to not be so static. I like the picture I have there, but I have lots of other I would like to see. 

I did managed to write a python program to change the background on bootup, but this program had some bugs. Then one day while is was going through the background images included when Ubuntu is installed, I noticed, some where setup with mulitple pictures, and would cycle through them about every half hour or hour. So with a little digging, I found out that Nautilus the file managing program that handles the desktop, uses an XML file to indicate the list of pictures to be cycled through. 

I whipped up a simple shell script that would create this XML file. 

Here is what I cam up with:

```

#!/bin/bash
# Written by Jeret Lendman
# detrix42@gmail.com

wpath="/usr/share/backgrounds/"

echo "enter path to the directory of the pictures for the wallpaper slide show"
echo "default is $wpath"
read sspath

len=${#sspath}
# testing first char of sspath
if [[ ${sspath:0:1} == '/' ]]
then 
	 wpath="${sspath%/}/"
else
	# test for ending '/'
	[[ $sspath == */ ]] || wpath=$wpath$sspath/
fi

echo workng path is $wpath

if [ ! -d $wpath ] 
then
	echo "Problem with the path you entered: $wpath"
	exit 1
fi

exec 3>wallpaper.xml

pics=( $wpath*.jpg )

echo '<background>' >&3
echo '  <starttime>' >&3
echo '    <year>2009</year>' >&3
echo '    <month>08</month>' >&3
echo '    <day>04</day>' >&3
echo '    <hour>00</hour>' >&3
echo '    <minute>00</minute>' >&3
echo '    <second>00</second>' >&3
echo '  </starttime>' >&3
echo '<!-- This animation will start at midnight. -->'  >&3

for (( i=0;i<${#pics[@]}-1;i++ ))
do
  echo '  <static>' >&3
  echo '    <duration>1795.0</duration>' >&3
  echo "    <file>${pics[$i]}</file>" >&3
  echo '  </static>' >&3
  echo '  <transition>' >&3
  echo '    <duration>5.0</duration>' >&3
  echo "    <from>${pics[$i]}</from>" >&3
  echo "    <to>${pics[$i+1]}</to>" >&3
  echo '  </transition>' >&3
done

l=$((${#pics[@]}-1))
echo "l = $l"
  echo '  <static>' >&3
  echo '    <duration>1795.0</duration>' >&3
  echo "    <file>${pics[$l]}</file>" >&3
  echo '  </static>' >&3
  echo '  <transition>' >&3
  echo '    <duration>5.0</duration>' >&3
  echo "    <from>${pics[$l]}</from>" >&3
  echo "    <to>${pics[0]}</to>" >&3
  echo '  </transition>' >&3

echo '</background>' >&3

echo "copying XML file to ${wpath}background-1.xml"
cp ./wallpaper.xml ${wpath}background-1.xml
echo "removing tempary XML file"
rm ./wallpaper.xml

```

Change the lines that say "<duration>1795.0</duration>" to change the amount of time between cycles. (1795 is just under 30 minutes. There is a 5 second transition time, which can be changed as well).

copy and paste this into your favorite text editor, and save it to where ever you like (recommend your home directory, or /usr/local/bin if you have sudo power ;)  )

---

