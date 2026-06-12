---
title: "conky slideshow script"
date: 2009-07-29
forum: Outdated Tutorials &amp; Tips
---

### Post by k3ttc4r on 2009-07-29
so.. i created a script that let's you have a slideshow with conky. right on your desktop!

of course this is on my site, too, for all you german speaking folks out there: [http://linuxian.net/artikel/conky-teil-3-slideshow-script.html](http://linuxian.net/artikel/conky-teil-3-slideshow-script.html)

just configure this under "settings", save it, chmod +x it, change in the directory with the images you want to use (in a terminal, of course), and execute the script. it takes care of all the rest, you just have to call it in conky with

```
${execi 600 ***DIRECTORY YOU USED IN THE SCRIPT***/slideshow}
${image ***DIRECTORY YOU USED IN THE SCRIPT***/current.png}
```
```
#!/bin/sh
 
##########################################################################
##               conky slideshow by Christian Brassat                   ##
##		                 a.k.a.					##
##    __         __    __    __           __ __                         ##
##   /\ \      /'__`\ /\ \__/\ \__       /\ \\ \                        ##
##   \ \ \/'\ /\_\L\ \\ \ ,_\ \ ,_\   ___\ \ \\ \    _ __               ##
##    \ \ , < \/_/_\_<_\ \ \/\ \ \/  /'___\ \ \\ \_ /\`'__\             ##
##     \ \ \\`\ /\ \L\ \\ \ \_\ \ \_/\ \__/\ \__ ,__\ \ \/              ##
##      \ \_\ \_\ \____/ \ \__\\ \__\ \____\\/_/\_\_/\ \_\              ##
##       \/_/\/_/\/___/   \/__/ \/__/\/____/   \/_/   \/_/              ##
##                                                                      ##
##                               v 0.0.2                                ##
##                          GNU GPLv3 2009                              ##
##########################################################################
 
##########################################################################
# Settings
##########################################################################
 
directory="***DIRECTORY***"    # Directory containing the script and the pictures
geometry="400x300"             # Max Geometry of the pictures in the slideshow
 
##########################################################################
# Script (do not change unless you know what you're doing)
##########################################################################
 
# Generates the specified directories
mkdir -p -v $directory/pics 
 
# Converts the image files for conky to use
cp -v * $directory/pics
mogrify -format png -resize $geometry $directory/*
rm -v -f $directory/*.jpg
 
# Creates an array from all pictures
files=($directory/pics/*.*)           	# create an array of the files.
N=${#files[@]}                     	# Number of members in the array
((N=RANDOM%N))
randomfile=${files[$N]}
 
# Sets picture from random file
cp -v $randomfile $directory/current.png
 
# Generates the Script itself
touch $directory/slideshow
echo "#!/bin/sh
 
##########################################################################
##               conky slideshow by Christian Brassat                   ##
##				v 0.0.2					##
##                           aka. k3ttc4r                               ##
##                          GNU GPLv3 2009                              ##
##########################################################################
 
##########################################################################
# Settings
##########################################################################
 
directory='$directory'		    	# Directory containing the script and the pictures
 
##########################################################################
# Script (do not change unless you know what you're doing)
##########################################################################
 
# Creates an array from all pictures
files=(\$directory/pics/*.*)        # create an array of the files.
N=\${#files[@]}                     	# Number of members in the array
((N=RANDOM%N))
randomfile=\${files[\$N]}
 
# Sets picture from random file
cp \$randomfile \$directory/current.png
" > $directory/slideshow
chmod -v +x $directory/slideshow
 
exit
```
let me know what you think, if you have any improvements, suggestions, request..

and have fun with it!

**changelog:**
v 0.0.2 - removed unnecessary cd call

---

### Post by loomsen on 2009-07-29
Nice code, I don't use conky anymore but maybe I will reuse some of your code somewhen somewhere :D

btw, wenne magst und jabber hast loomsen <at> lethyro.net, oder 123 866 981 für i seek you

*edit*
I'd rather use 

```

# Converts the image files for conky to use
cp -v * $directory/pics
mogrify -format png -resize $geometry $directory/*
rm -v -f $directory/*.jpg

```

than 

```

# Converts the image files for conky to use
cp -v * $directory/pics
cd $directory/
mogrify -format png -resize $geometry *
rm -v -f *.jpg

```

If you need to change a directory pushd and popd will handle this very well inside your script instead of cd

---

### Post by bedbug on 2009-08-23
TRY THIS and make your comments
Note: yo need to have images(either jpg OR png) in ~/Pictures Folder
      and convert from imagemagick

~/.conkyrc

alignment		   tr
own_window                 yes
own_window_transparent     yes
own_window_type		   override
gap_x			   10
gap_y 			   120
minimum_size               160 0
maximum_width              160
update_interval	           5.0

TEXT
${exec cd ~/Pictures; /usr/bin/convert -format png -resize 160x120 "`/bin/ls *.png *.jpg 2>/dev/null | /usr/bin/shuf -n1`" /dev/shm/current.png}${image /dev/shm/current.png -p 0,0 -n}${voffset 100}

---

### Post by Gregoroff on 2010-07-11
Hi there, I just would like to contribute to this forum by adding the following code  which is shorter and works well. The bash file (slideshow.sh) is in the folder /slideshow and within the same folder (/slideshow) I created the sub folder /pictures (/slideshow/pictures) which contains all the relevant pictures.
Here are quick explanations of the code:

ls -1 $dir/pictures -> list one picture  per line, the picture in my case has a jpg extension.

sort --random-sort -> randomly sort the pictures. The first picture of the list is randomly chosen
 
head -1 ->only keep the first randomly listed picture

mogrify -frame 100 -format png -resize $geometry -write $dir/model.png  $dir/pictures/$file -> resize picture and save it in the folder /slideshow next to the bash file (slideshow.sh)

Conky calls the script (slideshow.sh) and creates/updates a picture called model.png in the folder /slideshow which further appears in the conky side bar on the desktop. Be aware that the -p is for the position of the picture and the -n is very important for the update of the picture.


----------------------------
/.conkyrc
${execi 50 /home/user/scripts/slideshow/slideshow.sh}
${image /home/user/scripts/slideshow/model.png -p 70,790 -n}

----------------------------
#!/bin/sh
# conky slideshow by G. 2010
dir="/home/user/scripts/slideshow"    # Directory
geometry="200x200"                        # Max Geometry of the pictures in the slideshow
file=`ls -1 $dir/pictures | sort --random-sort | head -1`
mogrify -frame 100 -format png -resize $geometry -write $dir/model.png $dir/pictures/$file
#echo "The randomly-selected file is: $file"
exit

---------------------------

If you want to add new pictures just drag it in the folder /pictures at any time. Any kind of pictures should do the job. If you have any comment or questions, feel free to ask.

---

