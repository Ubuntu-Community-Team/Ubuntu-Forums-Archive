---
title: "Problem with 7zip and volumes and update"
date: 2008-11-11
forum: New to Ubuntu
---

### Post by Hurter on 2008-11-11
Hi

Just a bit of background:
I have a few users data that I needs to compress and put on DVD. These user site use Win and still would like to access there backup  and compressed data. (They connect to the Linux server via Samba.)

I decided to use 7zip since the format of the compressed files can be access from Win. Yes I know about the permission issue and its not a problem in this case.

The command I use once:
7zr a -t7z -v4450m -mx=5 /mnt/data/Backup/All_tower35_zip/Tony.7z /mnt/data/Backup/Users/Tony/ >>/mnt/data/Backup/All_tower35_zip/Tony.txt

This works and creates files no bigger than 4450Meg. So that I can write it to DVD at a later stage.

Then I would like to use this command there after:
7zr u Tony.7z.001 -uq0r2y2z0w2!TonyChange.7z /mnt/data/Backup/Users/Tony/ >>TonyChange.txt -ms=off -t7z -mx=5

This command to get a update works only if there are one "Tony.7z.001" file. The moment there are more that one it boms out.

Is there a posibility to run 7zip and a update suffex there after on multiple volumes. I still want the windows access aswell.
To save time I would like to run the update suffex. The current zip process take about 40 hours. (One user has 4 DVD for all his data)

Thanx for the help so far.
H

---

### Post by bscbrit on 2008-11-11
I don't know enough about 7zip to say whether there is a built-in command to do what you want, but this sounds like a perfect job for a small script.  Have you considered this as an option and, if so, is there a specific reason why you cannot go down this path?

---

### Post by Hurter on 2008-11-12
Just to clear thing a bit.
This is running in a script.Each user's data is compressed.

After running:
7zr a -t7z -v4450m -mx=5 /mnt/data/Backup/All_tower35_zip/Tony.7z /mnt/data/Backup/Users/Tony/ >>/mnt/data/Backup/All_tower35_zip/Tony.txt

Tony's data is compress into 2 files
Tony.7z.001       (4,666,163,200 bytes)
Tony.7z.002       (1,615,733,360 bytes)

Running this
7zr u Tony.7z.001 -uq0r2y2z0w2!TonyChange.7z /mnt/data/Backup/Users/Tony/ >>TonyChange.txt -ms=off -t7z -mx=5

Fail because its on multiple vol.

Is there maybe a way around this or maybe another solution

---

### Post by bscbrit on 2008-11-12
OK, I have had to go the man 7zip page because it is not a utility that I am conversant with.  Google took me to this address [http://www.digipedia.pl/man/7zr.1.html](http://www.digipedia.pl/man/7zr.1.html).

What do you want the line :

```
7zr u Tony.7z.001 -uq0r2y2z0w2!TonyChange.7z /mnt/data/Backup/Users/Tony/ >>TonyChange.txt -ms=off -t7z -mx=5
```

to do?  You are trying to update the contents but you do not know in which part of your archive the previous data was saved. For example, when you first create the archive, item X is placed near the end of part .001.  However, as the data grows and the parts are updated, the parts will grow and thus exceed their limit.  Data at the end of part 001 should now really be at the beginning of part 002. Item X therefore might not even be in part 001 when you come to update it.

I suspect that, if you must maintain the archive structure that you have chosen, then you need to use a command more closely resembling the first one which imposes the size limit that you wish to set. But I stress that not knowing 7zip and with no comments in your code I am not certain of the exact command to use.  

However, do the users have to access the data from DVD or is DVD solely used by yourself for remote archiving purposes?  If it is the latter then the easier solution would be to leave the data in one archive per user but divide it later for storing on DVD - the split command seems to be ideal for this purpose.  This has the advantage that each user is accessing a single file and that the update command will always be using the same complete archive and so will not suffer from the error that I outlined above. The script to split and recombine the archive is trivial to write.

I hope that this has been useful - without knowing the command it is not easy to suggest how to use it.

---

### Post by Hurter on 2008-11-24
Ok, your explanation make sense and I decide to run 2 archive structures. One to create DVDs and there updates and one with one file per user.
(A bit costly in terms of HDD space but I can live with it for now.)

The implementation may be done in 2 ways:
One make both archives, the DVDs one and the one file one at the same time or,
make the one file archive and split it later into volumes.

I am not sure if the latter one is possible (not tested or tried yet)

On the update side I also see that the original file change date (not sure about size or content). I assume it could update the list of contents. If that's the case, the plan to save time on archiving will not work because no the original differ anyway...
I will have to confirm this. May be its a sitting on creating the update zip files.

Anyway thanks for your help
Hurter

---

