---
title: "Avi to dvd script"
date: 2010-08-09
forum: Programming Talk
---

### Post by stars on 2010-08-09
Could someone make this into a bash script if you have time. I want to be able to run ./script.sh some.avi, allowing the avi to convert and burn to dvd. I tried to do this but received errors. I plan to learn bash but my free time is limited at the moment.

ffmpeg -i some.avi -target ntsc-dvd some.mpg && dvdauthor -o DVD/ -t tb.mpg && dvdauthor -o DVD/ -T && mkisofs -dvd-video -v -o DVD.iso DVD && growisofs -dvd-compat -Z /dev/dvdrw=/home/june/temp/DVD.iso

Any help will be greatly appreciated.

Figured it out by googling, probably not the greatest but works.

#!/bin/bash

output=$1

ffmpeg -i $1 -target ntsc-dvd output.mpg

mkdir DVD

dvdauthor -o DVD/ -t output.mpg 

dvdauthor -o DVD/ -T

mkisofs -dvd-video -v -o DVD.iso DVD

growisofs -dvd-compat -Z /dev/dvdrw=/home/june/temp/DVD.iso

exit

---

