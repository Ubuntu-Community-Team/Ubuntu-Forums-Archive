---
title: "flv (flash video) to dvd iso"
date: 2008-09-29
forum: Outdated Tutorials &amp; Tips
---

### Post by rfrayer on 2008-09-29
first we need the dependancies

```
sudo aptitude install mencoder ffmpeg dvdauthor lame lame-extras libtwolame0 genisoimage
```sudo gedit /usr/bin/flv2dvd

paist in the fallowing code


```
#!/bin/bash

output=$1
####################
# flv     Function #
####################

function flv {
    ffmpeg -i "$output" -target ntsc-dvd -aspect 4:3 output.mpg
}

####################
# rmflv Function #
####################

function rmflv {
    rm *.flv
}
####################
# convert Function #
####################

function convert {
    dvdauthor -o dvd -t output.mpg
}

####################
# rmpg     Function #
####################

function rmpg {
    rm output.mpg
}

###################
# Rename Function #
###################

function finalize {

dvdauthor -o dvd -T

}

#####################
# ISO Function      #
#####################

function image {

mkisofs -dvd-video -o dvd.iso dvd/

}

#####################
# rm2 Function      #
#####################

function rm2 {

rm -rf dvd/

}


###############
# Main Script #
###############

flv ;
rmflv ;
convert ;
rmpg ;
finalize ;
image ;
rm2 ;

exit
```save 

sudo chmod 755 /usr/bin/flv2dvd


cd the directory where the (single) flv file is at 

run this comand 

```
flv2dvd *
```the end result is a dvd iso image ready to be burned to dvd

---

### Post by regor210 on 2008-11-03
Thanks works grate!

---

### Post by nirudha on 2008-12-05
I seem to be missing some apt sources as I can't find mpeg2video and lame-extras. Could you tell me what sources you have added? Also are you using Hardy or Intrepid?

---

### Post by BoomSchtick on 2009-06-07
Awesome... thanks so much...

This was EXACTLY what I needed and the script made it easy as could be!

---

### Post by filfish on 2010-06-18
Awesome, I came across a how2 with the same steps as your script in it, but this is a beautiful example of script writing, quick, clean and no fuss, I use many tools day in, day out but rarely put them into scripts such as this, time to take another look at my dailies and start scripting!

Might be worth pointing out the 'Aspect options' such as not adding an aspect leaves the video in its original aspect etc, and also the video format, you use ntsc-dvd whereas UK use pal-dvd, pointing out options would really help others that haven't much of an idea about formats etc.

All meant as constructive comments, this is a fantastic how to, and I'm really glad to have stumbled across it.

---

### Post by wboyd53tx on 2011-07-16
Wow. That is what I was looking for, all in a nutshell. Thank you very much. Now using Katya via Linux Mint 11 (Ubuntu 11.04 base), but already had all the necessary programs installed.

---

### Post by Cope57 on 2011-07-17
devede

---

