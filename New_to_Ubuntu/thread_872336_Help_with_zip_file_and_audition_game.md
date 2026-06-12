---
title: "Help with zip file and audition game"
date: 2008-07-27
forum: New to Ubuntu
---

### Post by JinJolly on 2008-07-27
Ok so I was able to download Audition north America (a game from nexon) alright. But when I do the patch it gets stuck and says this: The central dictionary was not found in the archive (or were you trying to open not the last disk of a multi-disk archive). I think its because theres problems unzipping AUDITION6038.zip I tried to do it with Ark but it didn't seem to work. Can someone please help me out? ^__^

---

### Post by Dr Small on 2008-07-27
To unzip it, try:
```
unzip AUDITION6038.zip
```

---

### Post by JinJolly on 2008-07-27
> **Dr Small said:**
> To unzip it, try:
```
unzip AUDITION6038.zip
```

Errr oh yea duh... lol (this is why this thread is inm absolute beginner talk). But anyway I get this...

jin@jin-desktop:~$ unzip AUDITION6038.zip
unzip:  cannot find or open AUDITION6038.zip, AUDITION6038.zip.zip or AUDITION6038.zip.ZIP.
jin@jin-desktop:~$ cd /home/jin/Documents/Downloads
jin@jin-desktop:~/Documents/Downloads$ unzip AUDITION6038.zip
unzip:  cannot find or open AUDITION6038.zip, AUDITION6038.zip.zip or AUDITION6038.zip.ZIP.
jin@jin-desktop:~/Documents/Downloads$ sudo unzip AUDITION6038.zip
[sudo] password for jin: 
unzip:  cannot find or open AUDITION6038.zip, AUDITION6038.zip.zip or AUDITION6038.zip.ZIP.
jin@jin-desktop:~/Documents/Downloads$ 


Like the location of the file is this /home/jin/Documents/Downloads
So I typed cd /home/jin/Documents/Downloads
Then I tried to unzip it and didn't work then tried sudo unzip didn't work... what am I missing plz? :confused:

---

### Post by ramjet_1953 on 2008-07-27
Just use the file manager to navigate to where you downloaded the zip file.

When you are there, just right-click on it and select extract here.

Depending upon whether the archive has one, or several files, it may create a separate sub-directory with the un-zipped files in it.

Regards,
Roger :cool:

---

### Post by JinJolly on 2008-07-27
> **ramjet_1953 said:**
> Just use the file manager to navigate to where you downloaded the zip file.

When you are there, just right-click on it and select extract here.

Depending upon whether the archive has one, or several files, it may create a separate sub-directory with the un-zipped files in it.

Regards,
Roger :cool:

Thanks, this is what Im doing now... I uninstalled it and then reinstalled it onto the C drive, then I used wine to go to the C drive, I was able to right click and then choose extract here but then theres an error and on the details it says....

 End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
unzip:  cannot find zipfile directory in one of /home/jin/.wine/drive_c/Nexon/Audition/AUDITION06038.zip or
        /home/jin/.wine/drive_c/Nexon/Audition/AUDITION06038.zip.zip, and cannot find /home/jin/.wine/drive_c/Nexon/Audition/AUDITION06038.zip.ZIP, period.

Also when I run the patcher for the game a new zip file shows up named AUDITION06039.zip. When I try to extract that it has an error and says pretty much the same thing.

---

### Post by JinJolly on 2008-07-30
I still need help...

---

### Post by JinJolly on 2008-07-31
I tried installing the Sea version but that didnt even work at all, plus I dont like it as much, the players there are too bad *** lol. Anyway right now I'm trying to remove the sea version but all it shows is some blank grey window.... anyway I still have the same problem with th ecentral dictionary, heres a picture... [IMG]http://i37.tinypic.com/2ext3mg.png[/IMG]

---

