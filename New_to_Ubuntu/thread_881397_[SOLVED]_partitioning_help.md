---
title: "[SOLVED] partitioning help?"
date: 2008-08-05
forum: New to Ubuntu
---

### Post by ercferret18 on 2008-08-05
Okay, so my current partitioning setup looks like what's in the screenshot.

What I want to do is... delete the last partition, and increase the space of the first partition using the space left by the last partition. But... it lets me delete the last partition, but it won't let me make the first partition any bigger... only smaller. any ideas?

---

### Post by SunnyRabbiera on 2008-08-05
Its because its a NTFS partition, it probably wont co operate unless you re format everything.

---

### Post by ercferret18 on 2008-08-06
is there any way to do it without reformatting?

---

### Post by castor_troy on 2008-08-06
It wont allow because the last three partitions (recovery included) are an extended partition. Even i am stuck because of the same problem. I tried doing it using diff softs but then gparted showed by HDD to be blank. 

It has got nothing to do with it being ntfs.

---

### Post by SunnyRabbiera on 2008-08-06
> **ercferret18 said:**
> is there any way to do it without reformatting?

Sadly no I dont think, you should back up what you can and if you have a windows disc I suggest you use it.

---

### Post by Liakath on 2008-08-06
Dear castor-troy

> **castor_troy said:**
> It wont allow because the last three partitions (recovery included) are an extended partition. Even i am stuck because of the same problem. I tried doing it using diff softs but then gparted showed by HDD to be blank. 

It has got nothing to do with it being ntfs.

I think this is what the reason. Please note that the last partition sda3 is a primary partition and not part of the extended partition sda2 (viz. sda5 & sda6)

It is not allowing it to be merged with sda1 because they are not adjacent with the extended partition in between the two.

Liakath

---

### Post by SunnyRabbiera on 2008-08-06
> **castor_troy said:**
> It wont allow because the last three partitions (recovery included) are an extended partition. Even i am stuck because of the same problem. I tried doing it using diff softs but then gparted showed by HDD to be blank. 

It has got nothing to do with it being ntfs.

Actually I had a similar issue myself during my dual boot days, I wanted to change the size of my windows partition but it would not resize.

---

### Post by Liakath on 2008-08-06
Dear ercferret,

> **ercferret18 said:**
> Okay, so my current partitioning setup looks like what's in the screenshot.

What I want to do is... delete the last partition, and increase the space of the first partition using the space left by the last partition. But... it lets me delete the last partition, but it won't let me make the first partition any bigger... only smaller. any ideas?

I think this is what the reason. Please note that the last partition sda3 is a primary partition and not part of the extended partition sda2 (viz. sda5 & sda6)

It is not allowing it to be merged with sda1 because they are not adjacent with the extended partition in between the two.

Liakath

---

### Post by ercferret18 on 2008-08-06
ok... I guess i'll just make the linux partition bigger lol... thanks for all the help

---

### Post by SlalomMan on 2008-08-06
Can't you just delete the last partition and move all the other partitions over to the free space, and then resize the first one? 

Maybe I'm missing the issue, but it seems like it owuld work.

---

### Post by ercferret18 on 2008-08-06
I tried... It won't let me move the extended linux partition, just resize it to fill the free space.

---

### Post by Thingymebob on 2008-08-06
Wouldn't this work
Delete sda3,
Resize sda2 (extended) to fill free space
move swap up
move sda5 up
resize sda2 to regain free space
resize sda1

May be a long process
Defrag sda1 (NTFS) before starting will speed things up a bit

---

### Post by ercferret18 on 2008-08-06
Okay, next time I boot from the live cd, I'll try it. Thanks.

---

### Post by ercferret18 on 2008-08-06
> **Thingymebob said:**
> Wouldn't this work
Delete sda3,
Resize sda2 (extended) to fill free space
move swap up
move sda5 up
resize sda2 to regain free space
resize sda1

May be a long process
Defrag sda1 (NTFS) before starting will speed things up a bit
Thingymebob's solution (nice name lol) worked. thanks

---

