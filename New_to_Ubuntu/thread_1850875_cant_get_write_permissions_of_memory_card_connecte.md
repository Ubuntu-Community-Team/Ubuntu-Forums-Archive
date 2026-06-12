---
title: "cant get write permissions of memory card connected through mobile mass storage mode"
date: 2011-09-27
forum: New to Ubuntu
---

### Post by rrsk on 2011-09-27
i cannot write or delete in my memory card which is connected to my laptop(ubuntu 11.04).......
whatever command i use or whatever operations i do,,,,,
it just shows "Read-only file system"
please help me.....

---

### Post by rrsk on 2011-09-27
am using Dell laptop and samsung mobile.........

---

### Post by rrsk on 2011-09-29
hi guys,,,,,please any one help me............i hav no other idea about this problem

---

### Post by SlugSlug on 2011-09-29
open a terminal

df -h

note path of memory card (/media/CARD)

sudo chmod 777 /media/CARD

---

### Post by rrsk on 2011-09-29
shows
/dev/sdb1             1.9G  1.3G  568M  70% /media/3863-6265
if i put
 sudo chmod 777 /media/3863-6265
it shows
chmod: changing permissions of `/media/3863-6265': Read-only file system

please help me

---

### Post by roger_1960 on 2011-09-29
Hi

I had this once.

I think from memory that I did this:

Backup contents of memory card to PC.

Reformat memory card using the phone by unmounting and reformating in Android (or was it using Ubuntu? - not sure). Copy data back to memory card - and then it worked - not sure why...... I would have a spare memory card which is already writeable to hand before trying this so you can carry on anyway.  Memory cards do fail sometimes.

If you are copying media files, music etc, its probably easier to use dropbox (assuming you have wifi)

---

### Post by StevoSn on 2011-09-29
Hey!
may be there's just a stupid (mechanical) switch at the memory card that needs to be switched to "write"?

- but I guess you are able to use the memory card with you mobile?

..
stevo

---

### Post by rrsk on 2011-09-30
i think it is a kind of problem only in samsung mobiles with ubuntu..

nokia mobiles has no problem with ubuntu while reading memory card.......
any one having any idea about samsung in ubuntu????

thanks in advance,,,,help me pls

---

### Post by Phateless on 2011-09-30
> **rrsk said:**
> i think it is a kind of problem only in samsung mobiles with ubuntu..

nokia mobiles has no problem with ubuntu while reading memory card.......
any one having any idea about samsung in ubuntu????

thanks in advance,,,,help me pls

You may need special drivers. Download kies mini from the Samsung website (if they have a Linux version) and see if that helps.

---

### Post by rrsk on 2011-09-30
so sad.........there is no linux version of kies in samsung website.....can any one say where can i get linux version of kies?

---

