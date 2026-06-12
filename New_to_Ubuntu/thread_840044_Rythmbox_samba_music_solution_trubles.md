---
title: "Rythmbox samba music solution trubles"
date: 2008-06-25
forum: New to Ubuntu
---

### Post by &lt;&lt;joe&gt;&gt; on 2008-06-25
I have a samba server set up with a music share, and I have Rythmbox, on my laptop, pointing to this share as its music library. 
The trouble is when I am playing songs they cut out early. Half way through 1/3 the way stuff like that. 
Even though I know there whole songs on there and the don't cut out in the same spot each time so I don't think that it is the files them selfs.
I think that Rythmbox must just stop playing if there is some lag. So I figure there must be a network bottle neck or server bottle neck that make this happen. Really thinking server but don't know what to do to speed this up....
I am going to double check and see that its nothing on my laptop thats doing by playing stuff thats on my hard drive.
Any tips on how to make this work better and fix my problem of the songs only playing 1/3 the way through.

---

### Post by &lt;&lt;joe&gt;&gt; on 2008-06-26
so i did some more playing around 
i used totem to play music that resides on the server and it played it fine 
it would some times stop for a sec but it would resume playing the song insted of just stoping all togethere.
and it didn't do it nearly as much as rhythembox did

---

### Post by Nepherte on 2008-06-26
Sometimes music players can't cope with the smb protocol. Maybe you should just mount the samba share somewhere in /media for example and point Rhythmbox to the mounted directory.

---

