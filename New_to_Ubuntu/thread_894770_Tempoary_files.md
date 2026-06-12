---
title: "Tempoary files"
date: 2008-08-19
forum: New to Ubuntu
---

### Post by keefy777 on 2008-08-19
Does ubuntu store temp files like windows and if so how do i 
A.  find them
B.   delete them
C.  Is there a code that will erase them after a while

Your help is greatly appreciated

---

### Post by anotherdisciple on 2008-08-19
I'm pretty sure they are in the /tmp folder.... They should delete after some period of time.

---

### Post by anotherdisciple on 2008-08-19
I looked into it...

apparently there is on option in /etc/default/rcS

it is "TMPTIME=?" fill in the question mark with the number of days that you want.

---

### Post by silkstone on 2008-08-19
There is a /tmp folder, but mine never seems to contain much of any size, so is not really worth worrying about.

What *is* worth worrying about is the hidden .thumbnails folder under your Home folder. Every image you view (almost) generates a thumbnail which is saved to to either .thumbnails/normal or .thumbnails/large, and over time this can mount up to thousands of files and a lot of disk space.

You can safely delete the .png files (not the folders themselves), but it's not so easy to do that from the command line, because there's a limit to how many files can be included in the rm command. The best way is either with Nautilus or - my preference - install gnome-commander with Synaptic. You can sort the thumbnail files by date and delete just the older ones if you like.

---

### Post by LowSky on 2008-08-19
sudo apt-get autoremove

sudo apt-get clean

sudo apt-get autoclean

---

### Post by insane_alien on 2008-08-19
lowsky, that is deleting package cache not temporary files.

---

