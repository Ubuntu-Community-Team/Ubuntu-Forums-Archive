---
title: "HOWTO: Easily find the IP of networked computers (script)"
date: 2006-08-24
forum: Outdated Tutorials &amp; Tips
---

### Post by Greeface on 2006-08-24
I have written this tiny script that allows you to type in the hostname of a computer that is on your network, and get it's internal IP.  This isn't exactly a big howto, but I find it useful.

It depends on only Samba and Zenity



Paste the following code into your favorite editor
```
#!/bin/bash
#Basic script to retreive the IP of a networked computer
#Created by Greeface
#Requires Zenity and Samba

GETIP=$(command net lookup `zenity --entry --title='IP Finder' --text='Please Enter the Hostname'`)
command zenity --info --text=$GETIP'    ' --title='IP Finder'

```and save it temporarily to your desktop as 'ipfinder'

Open a terminal and navigate to your desktop
```
cd ~/Desktop
```
...and make it executable
```
chmod +x ipfinder
```

You are done!  You can double click it and hit 'Run,' put it into your Nautilus Scripts folder, make a launcher, or put it in /usr/bin so you can run it from the terminal (I prefer the second).

Thanks for reading, I hope you enjoy!

---

