---
title: "ddrescue for dummies"
date: 2012-12-24
forum: New to Ubuntu
---

### Post by Huzudra on 2012-12-24
[IMG]http://2.bp.blogspot.com/-PQexHJjFs3o/UFAPTVoxvXI/AAAAAAAABX8/0pXwyV2v3NA/s400/dummies_man.gif[/IMG]

So I'm trying to save some data from a failing drive for a friend. 

I'm attempting to image a partition using ddrescue, 710GB of stuff, to an empty 1TB drive. I feel like I'm doing something wrong as the 'destination' is empty despite an output stating that I've rescued 66GB data. I'm using:
sudo ddresuce -r 1 --force /dev/sdc2 (thats the bad drive) /dev/sda1 (that's the good drive)

Am I wrong to think that I should see 65GB of stuff on /dev/sda1? If it's not there, where is it? I thought I understood what I was doing, but the empty destination drive has me worried. It's taking a long time and reading very slowly, sometimes down to just bytes a second. Is there anything I can do to speed that up? I'm getting more bad sectors the longer it's trying to read. It's not looking good.

---

### Post by Huzudra on 2012-12-25
Ok, I've been splitting blocks for over 13 hours now. I've checked it from time to time and sometimes my iops is big, sometimes my iops is small, errsize and errors seem to remain the same. How long should it be slitting blocks for? How many passes does it make?

---

### Post by Huzudra on 2012-12-25
Still splitting blocks, my whole desktop has vanished, all I have is a black screen, terminal window, and mouse pointer. Screen savers aren't coming on, screen just goes to black. I've seen iops count up to 400something GB and when I check later, it's down to 100 something, then later 200 something, then later 50 something. It's like it's splitting the same data in a loop?

---

### Post by Huzudra on 2012-12-25
Well either it crashed or it finished, I came back past the commputer, turned on the screen and the terminal window was gone. Just a black desktop without even a mouse pointer. I had to do a hard shut down, started it back up, and I have a whole bunch of stuff on the good 1TB drive that used to be on the failed 1TB drive, however most of it is still unreadable. Atleast it's on a good drive and I can work with it now! 

I'm running foremost to try to extract documents to email to the guy to see if any of it is what he was trying to save. Once I've figured out that some of the data he wanted is still good, I'll move on to trying to pull pictures off it for him and if I can he had some adobe photoshop files he wanted to keep as well.

---

