---
title: "Odd Behavior When Tarring Files in Python"
date: 2009-05-02
forum: Programming Talk
---

### Post by StunnerAlpha on 2009-05-02
Ey fellas I am having a problem tarring a particular file in python. I have been able to tar 3 files beforehand and they were placed in the archive just fine. This is what happens and what I have done to check out the issue:
```

----------------MENU-----------------
2.Delete .nfo .sfv .txt .m3u files
1.Search and remove empty folders
0.Exit script
-------------------------------------
Select option: 2
Do you want this script to make a backup of everything you delete within this function for insurance reasons?(Y/N)y
Enter the name of the backup: test.tar
Would you like to remove megaZORD.sfv?(Y/N)y
megaZORD.sfv  removed.
Would you like to remove meta.txt?(Y/N)y
meta.txt  removed.
Would you like to remove bombackaz.nfo?(Y/N)y
bombackaz.nfo  removed.
Would you like to remove test.nfo?(Y/N)y
Traceback (most recent call last):
  File "cleaner.py", line 110, in <module>
    del_nfo_sfv_txt_m3u_files()
  File "cleaner.py", line 49, in del_nfo_sfv_txt_m3u_files
    tarArchive(backupname,filename,insurance)
  File "cleaner.py", line 14, in tarArchive
    tar.add(filename)
  File "/usr/lib/python2.5/tarfile.py", line 1460, in add
    tarinfo = self.gettarinfo(name, arcname)
  File "/usr/lib/python2.5/tarfile.py", line 1333, in gettarinfo
    statres = os.lstat(name)
OSError: [Errno 2] No such file or directory: 'test.nfo'
aaron@T60:~/Documents/Programming/BashProjects/test$ ls
[1-5]          cleaner.py  empty1      megaZORD.sfv  rule3-2.sh   rule3py.sh  test.tar
bombackaz.nfo  cleaner.sh  hahaha      meta.txt      rule3.py     rule3.sh    Test.tar
chaat          emptry      makill.mp3  r             rule3py.py~  test.sh     touchy
aaron@T60:~/Documents/Programming/BashProjects/test$ tar tvf test.tar 
-rw-r--r-- aaron/aaron       0 2009-04-23 22:27 megaZORD.sfv
-rw-r--r-- aaron/aaron       0 2009-04-23 22:27 meta.txt
-rw-r--r-- aaron/aaron       0 2009-04-23 22:27 bombackaz.nfo
aaron@T60:~/Documents/Programming/BashProjects/test$ ls -aR
.:
.              chaat       empty1        meta.txt    rule3py.py~  test.tar
..             cleaner.py  hahaha        r           rule3py.sh   Test.tar
[1-5]          cleaner.sh  makill.mp3    rule3-2.sh  rule3.sh     touchy
bombackaz.nfo  emptry      megaZORD.sfv  rule3.py    test.sh

./[1-5]:
.  ..

./chaat:
.   chutney  heythere   mastaz.m3u   nole      the empty one
..  filez    killz.m3u  megamix.wma  test.nfo

./chaat/chutney:
.  ..  brazton.m3u  hellz  watermalon

./chaat/filez:
.  ..  brawls  makillaz  warsaw.m4p

./chaat/filez/brawls:
.  ..  anotherone

./chaat/filez/brawls/anotherone:
.  ..  flackcannon.flac  m.mp3  thewave.wav

./chaat/filez/makillaz:
.  ..  emptah  emptyounces  spiderman  thedebs.m4a

./chaat/filez/makillaz/emptah:
.  ..

./chaat/filez/makillaz/emptyounces:
.  ..  READMEH

./chaat/filez/makillaz/spiderman:
.  ..  ogre.ogg

./chaat/the empty one:
.  ..

./empty1:
.  ..

```
The file is clearly there and exists, yet it says otherwise... 

Here is my script's tar code:
```

def tarArchive(backupname,filename,insurance):
#	print insurance # PASSED
	if insurance == 1:
#		print "CHECKPOINT 1" #PASSED
		if os.path.exists(backupname):
			tar = tarfile.open(backupname, "a")
			tar.add(filename)
			tar.close()
		else:
			tar = tarfile.open(backupname, "w")
			tar.add(filename)
			tar.close()

```
I am pretty stumped on this, any help greatly appreciated!

---

### Post by StunnerAlpha on 2009-05-02
Bump.... Anyone?

---

