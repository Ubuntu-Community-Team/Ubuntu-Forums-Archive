---
title: "can't install software"
date: 2008-05-31
forum: New to Ubuntu
---

### Post by ercferret18 on 2008-05-31
i downloaded a game called "Unreal Tournament 2004 Demo" for linux. however, whenever i try to extract it using the archive manager, it says "unexpected end of file" and whenever i use "tar xzfm" on it i get the same result. any ideas? (the file name is UT2004-LNX-Demo3334.run.gz

---

### Post by unutbu on 2008-05-31
It sounds like the file was not completely downloaded.
Perhaps try downloading it again?

---

### Post by ercferret18 on 2008-05-31
actually, i've already downloaded the file three times and every time i get this result, i even tried downloading it on another computer and transferring.

---

### Post by EXCiD3 on 2008-05-31
anything .gz means that it is a compressed archive. You probably have a partial download (firefox does this to me all the time if it drops the connection during a download or something and **never** thinks to warn me about a failed transfer) like unutbu said, just try downloading it again.

GREAT GAME btw!!! :D I've whipped up a little montage of me playing that game during last summer if you want to check it out -> [http://excid3.pcriot.com/UT2K4_Instagib__Rock_.wmv](http://excid3.pcriot.com/UT2K4_Instagib__Rock_.wmv)

**EDIT: **Just saw you said u downloaded it 3 times. So that means you probably have the same thing. Can you right click the file and choose "Extract Here"? You may also be using the wrong command to extract try using "**gunzip"** on the file instead.

---

### Post by unutbu on 2008-05-31
Try

```
gunzip UT2004-LNX-Demo3334.run.gz
```

This is not a tarball, so you should not use the tar command.

Also, I think if you just double click on these archived/compressed files in nautilus they are unpacked automatically.

---

### Post by ercferret18 on 2008-05-31
firefox does do this to me a lot, however i have used firefox and even the wget command in terminal, every time i download this, same result.

---

### Post by ercferret18 on 2008-05-31
> **unutbu said:**
> Try

```
gunzip UT2004-LNX-Demo3334.run.gz
```

This is not a tarball, so you should not use the tar command.

I tried this, but i get the same stupid message, "unexpected end of file"

btw in archive manager i noticed that the size of the .run file was 1.8 GB, i thought that this was a little strange...

---

### Post by EXCiD3 on 2008-05-31
Where are you downloading the file from? There is the possibility the host you are downloading it from is corrupted. Try the link below (for your version) And yes...the file could be about that size extracted...the game is quite large, ive had my UT2004 folder up to 20gb with mods before ;)

32 bit: [http://www.beyondunreal.com/dl.php/official/ut2004/ut2004-lnx-demo-3120.run.bz2](http://www.beyondunreal.com/dl.php/official/ut2004/ut2004-lnx-demo-3120.run.bz2)
64 bit: [http://www.beyondunreal.com/dl.php/official/ut2004/ut2004-lnx64-demo-3120.run.bz2](http://www.beyondunreal.com/dl.php/official/ut2004/ut2004-lnx64-demo-3120.run.bz2)

---

### Post by ercferret18 on 2008-05-31
i downloaded it from [www.unrealtournament2004.com](www.unrealtournament2004.com), however now i am currently downloading it from a different source (its a large file)... ill tell you if it works.

---

### Post by unutbu on 2008-05-31
Please post

```
ls -l UT2004-LNX-Demo3334*
file UT2004-LNX-Demo3334.run.gz
```

Also show the command you are using which is returning "unexpected end of file".

---

### Post by EXCiD3 on 2008-05-31
Well the file surely shouldnt extract to 1.8gb if the download size is less than 300mb (77 on the official site). Something is definitely wrong there.

Man...ut2k4's site hasnt been updated since 2005...that hurts me inside...what a great game and i still play it all the time! :)

---

### Post by ercferret18 on 2008-05-31
> **unutbu said:**
> Please post

```
ls -l UT2004-LNX-Demo3334*
file UT2004-LNX-Demo3334.run.gz
```

Also show the command you are using which is returning "unexpected end of file".

ercferret18@raut-pc:~$ ls -l UT2004-LNX-Demo3334*
-rw-r--r-- 1 ercferret18 ercferret18 81049007 2006-08-29 12:47 UT2004-LNX-Demo3334.run.gz
ercferret18@raut-pc:~$ 

ercferret18@raut-pc:~$ file UT2004-LNX-Demo3334.run.gz[/CODE]
UT2004-LNX-Demo3334.run.gz[/CODE]: ERROR: cannot open `UT2004-LNX-Demo3334.run.gz[/CODE]' (No such file or directory)
ercferret18@raut-pc:~$ 

i used tar xzfm and gunzip, both returning the same message

---

### Post by ercferret18 on 2008-05-31
> **EXCiD3 said:**
> Man...ut2k4's site hasnt been updated since 2005...that hurts me inside...what a great game and i still play it all the time! :)

i know its a great game i play it all the time on windows thats why i want it on linux too lol

---

### Post by EXCiD3 on 2008-06-01
> **ercferret18 said:**
> i know its a great game i play it all the time on windows thats why i want it on linux too lol

Oh! Since you said you were downloading the demo i thought you were new to the game! lol

If thats the case then you should download the linux client patch instead: [http://download.beyondunreal.com/fileworks.php/official/ut2004/ut2004-lnxpatch3369.tar.bz2](http://download.beyondunreal.com/fileworks.php/official/ut2004/ut2004-lnxpatch3369.tar.bz2)

Do you by chance have the linux installer on your disc? My copy (editors choice) doesnt have it as i think only the original ones do...but the linux patch might work installing. The same worked with Quake 3...install the patch and then copy the game textures etc over because the patch contained all the executable files anyways.

---

### Post by ercferret18 on 2008-06-01
lol i didnt read your message till now, but i will try this. thanks

btw i'm downloading the demo because im poor (why do you think i like ubuntu) lol

---

### Post by ercferret18 on 2008-06-01
ok i assumed that i was supposed to merge the patch with the real ubuntu installation, but when i try running the game i get this error message:

Failed to enter NvidiaLogo.ut2: Can't find file for package 'BenTex01'

what does this mean?

---

### Post by EXCiD3 on 2008-06-01
Well the patch needs the textures and everything in the folder where it installs to. Did you copy them over? If you have a full install on windows you could possibly just copy over everything but the /bin folder which is just a folder of the executable code and the rest should be the textures, maps, etc that are missing. That error just means that it cant find the file for the texture its trying to load, which makes sense if you only installed the patch.

If you want to just use the demo, download it from [http://beyondunreal.com](http://beyondunreal.com) im not sure that the download from [http://www.unrealtournament2004.com](http://www.unrealtournament2004.com) is corrupted or what.

---

