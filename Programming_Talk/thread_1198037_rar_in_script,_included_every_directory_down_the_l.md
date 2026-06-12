---
title: "rar in script, included every directory down the list!"
date: 2009-06-26
forum: Programming Talk
---

### Post by talz13 on 2009-06-26
Ok, so I finally got around to writing a python script to rar my image folders for easy archiving / backup.  However, when I opened one of the rar files, it had like 7 levels of folders before I got to the images that I added!  The contents of any given rar file looks like:```
/home/username/folder/folder2/folder3/folder4/folder5/
``` with all my images inside that bottom folder.

How can I make rar just insert the actual image files without all the crazy folders on the way there?

python script below:
```
import os
import subprocess
# Get last folder downloaded:
mbDir = "/home/my/pictures/are/here"
mbScript = "/home/my/script/is/here"
# Get list of folders in mbDir (should correspond to dates):
dirList = [name for name in os.listdir(mbDir) if os.path.isdir(os.path.join(mbDir, name))]
for dir in dirList:
        # Get list of folders in each dated dir:
        mbDir2 = os.path.join(mbDir, dir)
        dirList2 = [name for name in os.listdir(mbDir2) if os.path.isdir(os.path.join(mbDir2, name))]
        #print dirList2
        for dir2 in dirList2:
                #print 'rar a "' + os.path.join(mbDir2, dir2 + '.rar') + '" "' + os.path.join(os.path.join(mbDir2, dir2), '*') + '"'
                subprocess.call('rar a "' + os.path.join(mbDir2, dir2 + '.rar') + '" "' + os.path.join(os.path.join(mbDir2, dir2), '*') + '"', shell=True)
                #print 'rm -rf "' + os.path.join(mbDir2, dir2) + '"'
                subprocess.call('rm -rf "' + os.path.join(mbDir2, dir2) + '"', shell=True)
```

I can either re-archive them if I fix the script, or I could rejigger the rar files to get rid of the upper directories in them, either one would work at the moment.

---

### Post by .Maleficus. on 2009-06-27
If I understand what you're trying to do, you're just trying to create separate .RARs for each folder?  Something like date1.rar, date2.rar, etc?


Edit:  I would recommend choosing better variable names than 'dir', 'dir2', 'mbDir' and 'mbDir2'.

---

### Post by philcamlin on 2009-06-27
just rar the 1 file ? right click on the file not the whole directory :D

---

### Post by talz13 on 2009-06-27
for the most part, yes.  I have my main pictures folder in my home directory, then that folder is broken up into folders by date.  these date folders are then broken up by album, and I want to make rar's out of each of the albums.

The script works, but the directory structure of the rar file looks like:```
album1.rar:
	/home
		/username
			/pics folder
				/date folder
					/album folder
						(images are under here)
```and that results in me having to drill down through like 5 directories inside the rar file just to get to the images that I added.

---

### Post by philcamlin on 2009-06-27
yeah so rar the 1 filder you need :popcorn:

---

### Post by .Maleficus. on 2009-06-27
So what you want to do is something like
```
/home/name/pics/date/album/pictures.rar
```
?  With all of the pictures in one .RAR?

---

### Post by talz13 on 2009-06-27
> **philcamlin said:**
> yeah so rar the 1 filder you need :popcorn:

that's what I'm doing, but it is in a python script and I am passing the directory that needs rar'ed from python to rar, and rar is adding the 5 levels above the folder I am rar'ing

---

### Post by .Maleficus. on 2009-06-27
Try using os.chdir() to "cd" into your working directory, rather than working from the script directory and dealing with all of the the folder nonsense.

Link: [http://docs.python.org/library/os.html](http://docs.python.org/library/os.html)

---

### Post by talz13 on 2009-06-27
> **.Maleficus. said:**
> So what you want to do is something like
```
/home/name/pics/date/album/pictures.rar
```
?  With all of the pictures in one .RAR?

Correct, and when I rar with the command:```
subprocess.call('rar a "' + os.path.join(mbDir2, dir2 + '.rar') + '" "' + os.path.join(os.path.join(mbDir2, dir2), '*') + '"', shell=True)
```it is adding the directory levels as seen below, from one of my actual rar files it created:

```
jeff@server:~/Pictures/level1/level2/level3/dateFolder$ unrar v album.rar 

UNRAR 3.80 freeware      Copyright (c) 1993-2008 Alexander Roshal

Archive album.rar

Pathname/Comment
                  Size   Packed Ratio  Date   Time     Attr      CRC   Meth Ver
-------------------------------------------------------------------------------
 home/jeff/Pictures/level1/level2/level3/dateFolder/album/021.jpg
                582077   572422  98% 09-10-08 16:07 -rw-r--r-- 60597974 m3e 2.9
 home/jeff/Pictures/level1/level2/level3/dateFolder/album/023.jpg
                319220   296429  92% 09-10-08 16:08 -rw-r--r-- FE9F3AA7 m3e 2.9
 home/jeff/Pictures/level1/level2/level3/dateFolder/album/017.jpg
                696011   687469  98% 09-10-08 16:06 -rw-r--r-- 0AC4B1F4 m3e 2.9
 home/jeff/Pictures/level1/level2/level3/dateFolder/album/009.jpg
                654888   649510  99% 09-10-08 16:05 -rw-r--r-- 95652830 m3e 2.9
 home/jeff/Pictures/level1/level2/level3/dateFolder/album/026.jpg
                629356   620307  98% 09-10-08 16:08 -rw-r--r-- 396284C3 m3e 2.9
 home/jeff/Pictures/level1/level2/level3/dateFolder/album/004.jpg
                589880   579281  98% 09-10-08 16:03 -rw-r--r-- 4DBC9A23 m3e 2.9
 home/jeff/Pictures/level1/level2/level3/dateFolder/album/005.jpg
                528810   520521  98% 09-10-08 16:04 -rw-r--r-- 5225003A m3e 2.9
 home/jeff/Pictures/level1/level2/level3/dateFolder/album/010.jpg
                703683   695501  98% 09-10-08 16:05 -rw-r--r-- 2C1EEC1B m3e 2.9
 home/jeff/Pictures/level1/level2/level3/dateFolder/album/024.jpg
                256403   251839  98% 09-10-08 16:08 -rw-r--r-- C8FED747 m3e 2.9
 home/jeff/Pictures/level1/level2/level3/dateFolder/album/013.jpg
                578146   563456  97% 09-10-08 16:05 -rw-r--r-- BF40F2E1 m3e 2.9
 home/jeff/Pictures/level1/level2/level3/dateFolder/album/003.jpg
                583051   574099  98% 09-10-08 16:03 -rw-r--r-- F4F89ABE m3e 2.9
 home/jeff/Pictures/level1/level2/level3/dateFolder/album/022.jpg
                107482    92228  85% 09-10-08 16:08 -rw-r--r-- CF0DAB02 m3e 2.9
 home/jeff/Pictures/level1/level2/level3/dateFolder/album/014.jpg
                603057   593832  98% 09-10-08 16:06 -rw-r--r-- 03A5CC14 m3e 2.9
 home/jeff/Pictures/level1/level2/level3/dateFolder/album/012.jpg
                594806   583282  98% 09-10-08 16:05 -rw-r--r-- 8AC02D56 m3e 2.9
 home/jeff/Pictures/level1/level2/level3/dateFolder/album/001.jpg
                687456   684585  99% 09-10-08 16:03 -rw-r--r-- 58926442 m3e 2.9
 home/jeff/Pictures/level1/level2/level3/dateFolder/album/018.jpg
                687689   680302  98% 09-10-08 16:07 -rw-r--r-- A8099370 m3e 2.9
 home/jeff/Pictures/level1/level2/level3/dateFolder/album/020.jpg
                610464   597467  97% 09-10-08 16:07 -rw-r--r-- E5A3CEA8 m3e 2.9
 home/jeff/Pictures/level1/level2/level3/dateFolder/album/006.jpg
                564212   555216  98% 09-10-08 16:04 -rw-r--r-- AA77FAC7 m3e 2.9
 home/jeff/Pictures/level1/level2/level3/dateFolder/album/008.jpg
                623807   610049  97% 09-10-08 16:04 -rw-r--r-- 938A5A82 m3e 2.9
 home/jeff/Pictures/level1/level2/level3/dateFolder/album/002.jpg
                582414   575219  98% 09-10-08 16:03 -rw-r--r-- 9CB29C44 m3e 2.9
 home/jeff/Pictures/level1/level2/level3/dateFolder/album/011.jpg
                607484   595644  98% 09-10-08 16:05 -rw-r--r-- 2D0817C0 m3e 2.9
 home/jeff/Pictures/level1/level2/level3/dateFolder/album/019.jpg
                694908   687327  98% 09-10-08 16:07 -rw-r--r-- A6A23D41 m3e 2.9
 home/jeff/Pictures/level1/level2/level3/dateFolder/album/007.jpg
                598497   589665  98% 09-10-08 16:04 -rw-r--r-- 63AC5F73 m3e 2.9
 home/jeff/Pictures/level1/level2/level3/dateFolder/album/016.jpg
                675084   669453  99% 09-10-08 16:06 -rw-r--r-- 576A8A41 m3e 2.9
 home/jeff/Pictures/level1/level2/level3/dateFolder/album/025.jpg
                141759   129231  91% 09-10-08 16:08 -rw-r--r-- 326BB912 m3e 2.9
 home/jeff/Pictures/level1/level2/level3/dateFolder/album/015.jpg
                699640   692874  99% 09-10-08 16:06 -rw-r--r-- 2DFDA5BF m3e 2.9
-------------------------------------------------------------------------------
   26         14600284 14347208  98%
```

---

### Post by talz13 on 2009-06-27
> **.Maleficus. said:**
> Try using os.chdir() to "cd" into your working directory, rather than working from the script directory and dealing with all of the the folder nonsense.

Link: [http://docs.python.org/library/os.html](http://docs.python.org/library/os.html)

I will give that a try and see how it goes :)

---

### Post by talz13 on 2009-06-27
Awesome, that worked great!  Here's the relevant part of the updated script:```
# Get list of folders in mbDir (should correspond to dates):
dirList = [name for name in os.listdir(mbDir) if os.path.isdir(os.path.join(mbDir, name))]
for dir in dirList:
	# Get list of folders in each dated dir:
	mbDir2 = os.path.join(mbDir, dir)
	dirList2 = [name for name in os.listdir(mbDir2) if os.path.isdir(os.path.join(mbDir2, name))]
	for dir2 in dirList2:
		os.chdir(os.path.join(mbDir2, dir2))
		subprocess.call('rar a "' + os.path.join(mbDir2, dir2 + '.rar') + '" "*"', shell=True)
		os.chdir(mbDir)
		subprocess.call('rm -rf "' + os.path.join(mbDir2, dir2) + '"', shell=True)
```

---

### Post by .Maleficus. on 2009-06-27
Cool, glad you got it figured out.  Now all you have to do is make a cron entry for it and have it run automatically :).

---

### Post by talz13 on 2009-06-27
> **.Maleficus. said:**
> Cool, glad you got it figured out.  Now all you have to do is make a cron entry for it and have it run automatically :).

as soon as my test run of it finishes, I will have an all-in-one script to:

1. Check if I have the latest albums from the site
2. If I don't have them, get them
3. Rar the directories after downloading

It was getting to be a pain backing up the files, since everything is slow with huge numbers of files (before I rar'ed everything there were almost 40k files, now there are barely more than 1k)

---

