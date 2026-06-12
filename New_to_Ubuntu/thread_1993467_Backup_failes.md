---
title: "Backup failes"
date: 2012-06-02
forum: New to Ubuntu
---

### Post by Houmie on 2012-06-02
Hi,

When I try to run the Backup to backup my home directory into Ubuntu one it shows an error:

Backup location is too small.  Try using one with more space.

What does that mean? My home directory is only 20 MB or so.

---

### Post by Ms. Daisy on 2012-06-04
Well, the error tells you the problem.  Your 20 MB exceeds the size of what you have available in Ubuntu One.

According to [this]("https://one.ubuntu.com/"), you have 5 MB of free storage space available in Ubuntu One.  You can purchase additional space if you want.

---

### Post by critin on 2012-06-04
@ Ms Daisy:  Did you make a typo?  Ubuntu One gives 5GB free space, not 5mb.  

[B]
 [/B]


[B]
 [/B]

---

### Post by critin on 2012-06-04
> 
Backup location is too small.  Try using one with more space.

What does that mean? My home directory is only 20 MB or so.
[I]
Houmie;[/I]  Have you used Ubuntu One before now or is this your first visit?

It could be that your home is too small for the backup tool to work properly.  20MB is very tiny and if it's full, well...

---

### Post by NikTh on 2012-06-04
> **critin said:**
> [I]
Houmie;[/I]  Have you used Ubuntu One before now or is this your first visit?

It could be that your home is too small for the backup tool to work properly.  20MB is very tiny and if it's full, well...

@Houmie yes , maybe thats the problem.. too tiny for backup tool to work properly . 

Try to use **[Tar]("http://ubuntuforums.org/showthread.php?t=35087")** instead . 
Then you can upload your compressed file to Ubuntu One.

---

### Post by Ms. Daisy on 2012-06-04
> **critin said:**
> @ Ms Daisy:  Did you make a typo?  Ubuntu One gives 5GB free space, not 5mb.  

Whoops, indeed. Sorry about that!

---

### Post by critin on 2012-06-05
@ Ms Daisy:  Don't be sorry--all of those Bee's look alike after a long day, but they're sure not the same.   lol!

---

### Post by Houmie on 2012-06-05
> **NikTh said:**
> @Houmie yes , maybe thats the problem.. too tiny for backup tool to work properly . 

Try to use **[Tar]("http://ubuntuforums.org/showthread.php?t=35087")** instead . 
Then you can upload your compressed file to Ubuntu One.


Hey everyone,

thank you very much for the help.  It is my first time using Ubuntu one and its empty. The size is meant to be 5GB, so plenty available.

The problem might be as you already mentioned the size of my backup files.  How weird.  It is a bit incovient doing a TAR each time though. Kills the whole aspect of backup.

I think I will try to put more stuff in my home directory until it accepts it. haha  :lolflag:

---

### Post by gordintoronto on 2012-06-05
If you right-click on your home folder and select Properties, I think you will find it is quite a lot bigger than 20 MB. On a very lightly used installation, the hidden folders contain about 200 MB of files.

---

### Post by deadflowr on 2012-06-05
> **gordintoronto said:**
> If you right-click on your home folder and select Properties, I think you will find it is quite a lot bigger than 20 MB. On a very lightly used installation, the hidden folders contain about 200 MB of files.

Very true, the OP should run disk usage analyzer and scan home to get an easy to read look at the size of the home directory, or use a command line command.

---

