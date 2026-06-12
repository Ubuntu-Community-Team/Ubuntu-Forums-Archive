---
title: "Need some help writing a shell script for archiving jobs"
date: 2012-11-19
forum: Programming Talk
---

### Post by uno_the_great on 2012-11-19
Hey everybody, 

Before I get into my request for help, let me give you a little background about my company, and what I do...

I recently started a Visual Effects and Digital Media company. We work with some MASSIVE amounts of data. Anywhere from 10GB, to upwards of a TB per job. 

I use backupPC to keep rolling nightly backups of the fileserver, so that we don't lose anything. This works great for up to date backups. It does not, however, provide, in my opinion, and adequate method for archiving jobs to offline media once we're finished with them. 

This is where my fellow ubuntu users can help me. 

I'm looking for some help to write a script that will allow me to pass it an input folder which contains the ENTIRE job (we use a very specific folder structure for storing all of our data), build a series of tarballs, each no larger than can fit on a dvd (4.65GB, to account for size variance in manufacturing), and store it in a pre-specified archive folder (in my case, that folder would be located in '/media/backups/archives/jobs'. 

When I pass the folder to the script via a terminal, I would like it to automatically create a sub-folder withing the archives/jobs folder that matches the name of the job. 

I'm sure for somebody with a decent amount of shell scripting knowledge could do this in no time at all, but unfortunately, I'm an artist, and not a programmer, so I have no idea where to start. 

Any help you guys could provide would be MOST appreciated!!

---

