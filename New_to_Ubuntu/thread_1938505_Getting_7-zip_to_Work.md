---
title: "Getting 7-zip to Work"
date: 2012-03-09
forum: New to Ubuntu
---

### Post by ubunt10 on 2012-03-09
Before I installed Ubuntu, I backed files up (on Windows) by burning them to DVDs. To do this, I encrypted the files with 7-zip and then transferred them to DVD. While I still had Windows installed, I opened the encrypted zip files to verify that they were not corrupted. That is when I noticed that WinRAR was limited in what it could do with the archive. For example, I could not just open the zip archive in WinRAR and delete a single file that was highlighted. But if I opened it in 7-zip, I could delete a single file. So, to conclude this first paragraph: Even on Windows, an archive created by 7-zip works better with 7-zip than WinRAR. The same may be true for other programs, including those on Linux. 

Okay. Let's go to Ubuntu 11.10. My goal is to extract a file from an encrypted zip archive (that was encrypted by 7-zip) on Ubuntu. Using Ubuntu, I tried to extract it. It prompted me for a password. After entering the correct password, a box popped up that said this. 
>    skipping: prog/a.EXE              need PK compat. v5.1 (can do v4.6)
I am not sure exactly what that message meant (feel free to elaborate if you know), but it seemed wise that my next step is to use 7-zip and try to extract it. On Windows, I just downloaded and EXE file and clicked "Next" to install. I am not sure how to install it on Ubuntu. 

I visited the 7-zip download page here. 
[http://www.7-zip.org/download.html](http://www.7-zip.org/download.html)

I do not know what links to click and how to install it. I thought maybe this page leads to the answer.
[http://packages.debian.org/sid/p7zip-full](http://packages.debian.org/sid/p7zip-full)

But I do not know which file to click and how to install. Thanks.

---

### Post by synaptix on 2012-03-09
Open terminal and type:

```
sudo apt-get install p7zip-full
```

Then try extracting again and it should work for you this time.

---

### Post by rattskjelke on 2012-03-09
I never figure out why they renamed it p7zip in Linux but synaptix's instruction will install it from the Ubuntu repo.

---

### Post by ubunt10 on 2012-03-09
It worked! Sweet. Why did it work? How could one command install it? Did Ubuntu come with the p7zip package? Did that command both download it from the internet and install it?

---

### Post by restorator on 2012-03-09
> Did that command both download it from the internet and install it? 

yes.

---

### Post by _0R10N on 2012-03-09
Plase, ubunt10, mark the thread as SOLVED. Thank you!

---

