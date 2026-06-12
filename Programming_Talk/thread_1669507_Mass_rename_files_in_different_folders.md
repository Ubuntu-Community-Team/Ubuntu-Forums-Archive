---
title: "Mass rename files in different folders"
date: 2011-01-17
forum: Programming Talk
---

### Post by bcooperizcool on 2011-01-17
I am trying to rename multiple files that all have the same name, but are in different folders, to the same name, but changed (eg. icon1.png to icon.png)

I am using the mv command with variables set for the locations.
(The script searches for these files, adds them to a text file, then sets that text file as a variable for the location and name)

My problem is it moves the file to where the script is located...

Thanks!

---

### Post by sisco311 on 2011-01-17
Please post the script you are using and an exemple of input files and what output you are expecting. 

I guess, you could use find. Something like:
```
find path/to/dir -name 'file.name' -type f -execdir mv -b -- '{}' 'new.file.name' \;
```

---

### Post by kaspar_silas on 2011-01-17
So is it just a temporary moving issue or am I missing something. If it is can't you just add something like:

$ mv output [somedir]
$ cd [somedir]

With
$ cd -

At the very end

---

### Post by bcooperizcool on 2011-01-17
I'm sorry :(  I should have posted my script.


I'm just getting down the basic functions, so it is not the best yet, and still messy.

I would use it on my iphone to change images out. (just to give you an idea of how it would work)

```

#!/bin/bash


# if [ `id -u` != 0 ]; then echo "Please Run this as SU"; exit 0; fi

base=/home/ubuntu

theme_base=/home/ubuntu/Themes


clean_theme()
{


updatedb && locate icon1.odg > $theme_base/.iconlist.txt
cat $theme_base/.iconlist.txt | while read file; do basename "$file" ; done > $theme_base/.iconname.txt

sed 's/1.odg/.odg/' < $theme_base/.iconlist.txt >$theme_base/.iconlocation.txt 
cat $theme_base/.iconlocation.txt | while read file; do basename "$location"; done


cat $theme_base/.iconlocation.txt | while read file; do
rm -rf "$location" ; done

}


check_folder_theme()
{
if [ ! -d $theme_base ];
then mkdir $theme_base;
else echo "Theme folder exists already...  moving on";
fi
}





theme_list=`dir $theme_base`


chose_theme()
{
echo "Please choose a theme.  It is case sensitive, so please type it out exactly"
echo "-----------------"
echo "$theme_list"
echo "normal"
echo "-----------------"
read -p "Theme to apply = " theme
echo 
echo "$theme"
}



check_folder_theme
chose_theme
clean_theme



```

---

### Post by sisco311 on 2011-01-18
First of all, use some indentation in your code to make it more readable.
```

if something; then
  echo something
then
  echo something else :)
fi
```

Instead of updatedb && locate use find. locate is very fast if the database is up-to-date, but it's much slower than find if you have to update the database each time.

```

cd path/to/dir
find ./ -name '*.odg' -type f
```

File names can contain any characters other than slash or the null character. I'm not sure why you save the file names in a file, but if you do so, separate the names with a null character:
```
find ./ -name '*.odg' -type f -print0 > files
```

Instead of:
```
cat files | while read file; do
...
done

```
use:
```
while read file; do
...
done < files
```

Of course, if the file names are separated by a null character, you have to specify that:
```
while IFS= read -r -d '' file; do
...
done < files
```

Anyway, your code is overcomplicated. I'm not sure if I understand it correctly, but in Ubuntu, I would use find and the perl based rename command:
```
find ./ -name '*.odg' -type f -execdir -n rename 's/1.odg/.odg/' '{}' +
```

or 
```

while IFS= read -r -d '' file; do
  mv -b -- "$file" "${file%1.odg}.odg"
done < <(find ./ -name '*.odg' -type f -print0)
```

For more information, check out:
```
man find
```
and a bash guide:
[http://mywiki.wooledge.org/BashGuide](http://mywiki.wooledge.org/BashGuide)

---

### Post by bcooperizcool on 2011-01-18
Thank you!  Find is just what I wanted :D


I actually worked a way around this though, using a different approach.  I will need the find though for the next stage.

This themes the system icons on an iPhone without winterboard (google it if you don't know what it is :P)
I don't think I can run perl on an iphone, so I will stick with this.

Here is my code now.  (still not done)

```

#!/bin/bash

#Brian Cooper (bcooperizcool)
#theme.sh (need to think of a better name >:( )
#I don't care if you take it, just don't claim you made it. 
#My messy code :D   It actually works for theming the system icons!   This #took me what, 5 hours?   Sigh...  At least I learnt some things along the #way.  There is probaly a way more efficient way to do this, but I am not in #a position to do that right now.   I might try to theme the non-system #icons in the future, but not right now.


#checks if user is root
if [ `id -u` != 0 ]; then echo "Needs to be run as root! (silly person)"; exit 0; fi

#changable for me, so I can test on different machines
base=/private/var/stash/

theme_base=/private/var/stash/Themes


check_folder_theme()
{
#checks to see if /Themes is a directory.  If not, then it makes it.
if [ ! -d $theme_base ];
then mkdir $theme_base;
else echo "Theme folder exists already...  moving on";
fi
}




#Will list the the themes for choosing when called upon
theme_list=`dir $theme_base`




#This does the final install
install_theme()
{
#gets a list of the icons, hoping they are the same as the actual folder names
ls "$theme_base/$theme/Icons" > "$theme_base/.icons.txt"
cat "$theme_base/.icons.txt" > "$theme_base/.name.txt"
#removing the .png so it can be universal :P
sed 's/.png//' < "$theme_base/.name.txt" > "$theme_base/.second.txt"
#removing the space so it is more compatible.
sed 's/ //' < "$theme_base/.second.txt" > "$theme_base/.final.txt"


#renames the original icon so as not to lose it :P
while read icons
do mv "/Applications/$icons.app/icon.png" "/Applications/$icons.app/icon1.png" 
done < "$theme_base/.final.txt"

#copies the themed icon into its respective folder
while read name
do cp "$theme_base/$theme/Icons/$name.png" "/Applications/$name.app/icon.png"
done < "$theme_base/.final.txt"
}

#want to un-apply the theme?
clean_theme()
{
#laaaallaaaaaallama o.O   renaming the original icons over the themed ones
while read clean
do mv "/Applications/$clean.app/icon1.png" "/Applications/$clean.app/icon.png"
done < "$theme_base/.final.txt"
}


chose_theme()
{
#Time to set the folder it all works out of!  :D

echo "Please choose a theme.  It is case sensitive, so please type it out exactly" #saves me a lot of coding, as this can now be used as part of the path :3

#echoing the choices, with the variable we used above.
echo "-----------------"
echo "$theme_list"
echo "normal"
echo "-----------------"
read -p "Theme to apply = " theme 
echo 

if [[ "$theme" == normal ]]
then clean_theme;
else check_folder_theme; install_theme;
fi

}

#calling the functions off!

#check_folder_theme
chose_theme
#clean_theme
#install_theme
#just a reminder
echo "$theme_base/$theme"




```

---

