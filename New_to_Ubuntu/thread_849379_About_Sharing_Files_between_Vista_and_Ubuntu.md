---
title: "About Sharing Files between Vista and Ubuntu"
date: 2008-07-04
forum: New to Ubuntu
---

### Post by litlchanman on 2008-07-04
on my new laptop im planning on dual booting vista and ubuntu 8.04, its comes with vista already

when installing im going to set up a fat32 partition for media files so i can play them in either OS, however, im still confused as to how this works.

say i put a song in vista's "my music" folder, where would it show up in ubuntu? 

or would it actually have a certain folder named like "fat32" that can be accessed from both OS's..

if someone could please explain the details for me i'd greatly appreciate it

---

### Post by sayakb on 2008-07-04
You can access and write onto NTFS partitions in Ubuntu without any problems. Ubuntu will mount the Vista partition each time you boot in and you can access it fairly easily -- From the desktop or from the **Computer** (Places-> Computer) 
Inside the **Computer**, you may see the Vista drive either by it's drive label or by the size (for example 50GB Media) Once you identify and open the vista drive (Which would be the drive having the Windows and Program Files folder in it), look into the following folders:

[LIST]
[*]My Documents = Users*/**username*/Documents
[*]My Pictures = Users*/**username*/Pictures
[*]My Music = Users*/**username*/Music
[*]My Videos = Users/*username*/Videos
[/LIST]
Where *username *is you Vista user-name.

---

### Post by litlchanman on 2008-07-04
thanks that really cleared things up

---

