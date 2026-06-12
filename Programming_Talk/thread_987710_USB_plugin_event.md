---
title: "USB plugin event?"
date: 2008-11-19
forum: Programming Talk
---

### Post by Masterofpsi on 2008-11-19
I'm trying to make a Bash script to sync a flash drive with my computer. Here is what I have:

#!/bin/bash

drive=CHARON
usr=nicholas

files=/media/$drive/sync/"*"
mkdir -p /home/$usr/sync/$drive
for f in $files
do
    cp -r $f /home/$usr/sync/$drive
done

Now, the script does what I want it to when I run it. My question is, where would I put it to make it execute whenever I plug in a flash drive? Ideally, this would entail detecting the drive's name. Thanks.

---

