---
title: "Bash Script for 'simple' Photobooth process"
date: 2010-11-03
forum: Programming Talk
---

### Post by garuff on 2010-11-03
Hi folks,

Fairly new to scripting so bear with me, I've done a bit in the past (and dabble in a bit of VB/SQL now and then) but usually end up searching for something with similar functionality and cannibalising it to do what I'm after!

Anyway... I'm trying to write a fairly simple script using gphoto2, imagemagick and feh currently to automate a photobooth at a friends wedding, the aim being to have an input from a USB button (in the post currently!) to fire off a script that will:

1) Show a countdown onscreen

2) take four pictures

3) re-arrange the pictures vertically and stick a small border on

What I'd like is to fire up the script and have it displaying say picture1.JPG (fullscreen) until an input is registered (perhaps spacebar is pressed). Then display a countdown (fullscreen also) followed by a nice smiling face (fullscreen) at which point gphoto2 kicks in in the background and takes four shots at an interval of say 6 seconds a pop, these are re-arranged by imagemagick and sent off to a printer. The fullscreen image then changes to an hourglass for 30 seconds say (give the printer a chance!) and back to picture1.JPG that would have instructions to press the input again...


I've got as far as:
```

#!/bin/bash

SOURCE=/home/gruff/Pictures
WORKING=/home/gruff/Pictures/Outputs/Working
DEST=/home/gruff/Pictures/Outputs
RESOLUTION="640x480!"
COUNTDOWN=/home/gruff/photobooth/files/countdown
SMILE=/home/gruff/photobooth/files/smile

#Await USB input - when found do as below but ignore any further USB input until it's finished

#Instructions and countdown
feh -FZ -D 1 --cycle-once $COUNTDOWN
feh -FZ -D 10 --cycle-once $SMILE

#Capture images
cd $SOURCE
gphoto2 --interval=6 --frames=4 --capture-image-and-download

# Set last four pics as $pictures variable, count output images and  set $finalpic file name variable

cd $DEST
    pictures=`ls $SOURCE/*.JPG | tail -4` #last four .jpgs
    photocount=`ls $DEST/*.JPG -1 | wc -l`
    photonumber=`expr $photocount + 1`
    finalpic="photo${photonumber}.JPG"

# Resize pics to resolution variable and save in working directory
    /usr/bin/convert -resize $RESOLUTION -bordercolor black -border 10x6 $pictures $WORKING/resized.JPG

# Combine pics and save to destination with $finalpic filename
    /usr/bin/convert $WORKING/resized* -append $DEST/$finalpic
    
# Clear working directory?

# Send to printer

# End 'please wait' type image - cycle back to start image and await USB input again
```Some rudimentary notes in there (mainly for my benefit!) that can be ignored for now!

But I'm struggling to get feh to maintain a fullscreen image - I need an IF or something to create a loop once the fullscreen image issue is sorted I think.

gphoto and imagemagick I'm pretty happy with there (might be a bit cowboy though!)... I'd like to make it fairly clean overall in the end as it's something I'm sure people would be interested in, requiring only a camera gphoto plays nicely with and a screen to set up next to it - simples!

/essay

Any help greatly received! Gareth

---

### Post by punong_bisyonaryo on 2011-03-06
This is interesting, I would like to know what progress you've made so far.:)

---

