---
title: "Bash scripting help"
date: 2012-05-18
forum: Programming Talk
---

### Post by Tclarkie on 2012-05-18
Hi all
I am trying to write a simple script to make it easy download the Triple J feature album, incorporating rtmpdump and pacpl.
 ```
#!/bin/bash
echo "Directory: "
read directory
cd $directory 
echo "xml:"
read xml 
grep "rtmp" $xml | tr "[ ]" "[\n]" | grep "rtmp" | sed "s/url=//g" >> .rtmp

for line in `cat .rtmp`; do
echo $line | tr -d '"'
echo "name of track: "
read  "name"
rtmpdump -r "$line" -o "$name.flv"
pacpl ."$name".flv -t mp3
rm ."$name".flv
play -q /usr/share/chirp.wav 
done
rm .rtmp
```
RTMPDUMP always returns "RTMPDump v2.4
(c) 2010 Andrej Stepanchuk, Howard Chu, The Flvstreamer Team; license: GPL
WARNING: Unknown protocol!" but when i substitute the variable $line with the string it contains, it works
what is the problem here?
Thanks

---

