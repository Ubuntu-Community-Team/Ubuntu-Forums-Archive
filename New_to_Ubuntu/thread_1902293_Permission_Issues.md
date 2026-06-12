---
title: "Permission Issues"
date: 2011-12-30
forum: New to Ubuntu
---

### Post by gtrrockz84 on 2011-12-30
Hi everyone,
I just started using ubuntu a little over a week ago and loved it so much that im now using ubuntu as my server for the company i work in. 
Its 5 days and looks like all has been going good. there are 16 pcs and 1 ubuntu (desktop version) server. 
There is one particular drive that i made read/write/execute permission to everyone on the lan. 
But for some reason there is one pc that seems to act up every now and then. Sometimes the pc can read/write sometimes the pc can only read.. Im not sure why the pc keeps seeing permissions differently every now and then. this pc uses Windows 7. there are 2 other windows 7 and they have no problem. there are vista and xp computers and they have no problem. 
its just that one pc. please help! :) 
Also, windows 7 pc that has problem and the other windows 7 pc that has no problem both use the same anti-virus. 
I also tried creating a samba user for the windows pc that has problem but its not fully solved. he gets rights for a while and the next day it becomes read only again (and this happens only to certain folders in the drive) :( im really lost and confused. 
Thanks a lot for all your support in advance.

---

### Post by gtrrockz84 on 2011-12-30
Hi everyone,
I just started using ubuntu a little over a week ago and loved it so much that im now using ubuntu as my server for the company i work in. 
Its 5 days and looks like all has been going good. there are 16 pcs and 1 ubuntu (desktop version) server. 
There is one particular drive that i made read/write/execute permission to everyone on the lan. 
But for some reason there is one pc that seems to act up every now and then. Sometimes the pc can read/write sometimes the pc can only read.. Im not sure why the pc keeps seeing permissions differently every now and then. this pc uses Windows 7. there are 2 other windows 7 and they have no problem. there are vista and xp computers and they have no problem. 
its just that one pc. please help!  
Also, windows 7 pc that has problem and the other windows 7 pc that has no problem both use the same anti-virus. 
I also tried creating a samba user for the windows pc that has problem but its not fully solved. he gets rights for a while and the next day it becomes read only again (and this happens only to certain folders in the drive)  im really lost and confused. 
Thanks a lot for all your support in advance.

Need to add that other pcs are also now seeing the folder as read only. i check the box in sharing properties, everyone can read and write and after a while for some reason maybe after a day it automatically goes back to read only.. Please help!!!

---

### Post by gtrrockz84 on 2011-12-30
Hi everyone,
I posted this situation in "Network.." category and i got no response. Hopefully someone will help me here.

I have an ubuntu server and 12 pcs (some are windows 7, some vista). I have a hard drive in ubuntu (named as "X-drive" drive) and created a folder called "Projects" to be accessed by all pcs. 

so i changed the settings in samba to read/write so all pc users can access this folder and have full permission to read and write. I also right clicked the "Projects" folder in that drive and changed the settings in share. 

After these steps it all works fine for a while (sometimes even a day or so) and then suddenly the folder becomes read only. Im not sure why that happens. I check the folder sharing properties and the share is unchecked! But samba settings still say its writable and visible. So i check the boxes in share properties and works fine for about a day and becomes read only again!

Please help me with this. Why is the settings keep changing automatically? 

Any help is greatly appreciated. Thanks!

---

### Post by oldos2er on 2011-12-30
Threads merged. Please don't start more than one thread per issue.

---

### Post by coffeecat on 2011-12-31
And a third thread merged in. Please do not start multiple threads on the same issue. You may bump your thread not more than once every 24 hours if you receive no replies.

---

### Post by gtrrockz84 on 2011-12-31
Would be nice if anyone of you could give me some direction to fix this problem!

---

### Post by ilikelinuxitisthebest on 2011-12-31
hey. welcome to the fourms. does ubuntu tell you that it has read, write, and execute permissions. even when it isint working?

---

### Post by gtrrockz84 on 2012-01-03
Thanks for your reply! when some .doc files become read only in the folder i check the sharing property of the folder and the sharing options are unchecked. So i check them and after few hours or so they automatically become unchecked again. This happened about 3 times in 2 weeks. I also did chmod -R to the folder but some files like .doc files still remained as read only. Not sure why :(

---

### Post by gtrrockz84 on 2012-01-03
Hi i just wanted to update that this happens to only one person. He uses Windows 7. There are other people using windows 7 and vista but they have rwx permission. For some reason he keeps having rwx issues with some folders. 
Here's a folder of where he only has read only permission. But the terminal says this
```
kevin@Server:~$ sudo ls -l /media/P-drive/Projects/"EQPro Testing"/2010/Janice/LGSSQA44/EQPro/Data
total 6764
-rwxrwxrwx 1 nobody nogroup 2310144 2011-12-27 10:04 EQProData-429 - Blank.mdb
-rwxrwxrwx 1 kevin  kevin   2269184 2011-09-14 08:38 EQProData-429 - Empty.mdb
-rwxrwxrwx 1 nobody nogroup 2338816 2012-01-03 09:37 EQProData-429.mdb
-rwxrwxrwx 1 nobody nogroup       0 2010-12-28 10:46 Limerick Test Steve.txt
-rwxrwxrwx 1 kevin  kevin         0 2010-12-28 10:46 Limerick Test.txt
-rwxrwxrwx 1 nobody nogroup     178 2010-08-18 13:27 Locations.txt
-rwxrwxrwx 1 nobody nogroup     101 2011-02-07 15:14 Test of EQPro with Windows 7 and Access 2003.txt
```

This is true for all computers except his. I believe it has something to do with the settings of his computer maybe? all other windows 7 and vista can read and write but for some reason his windows 7 can only read. Everyone uses the same anti-virus software. Please help.

---

