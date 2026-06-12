---
title: "Error given w/ unace"
date: 2008-09-14
forum: New to Ubuntu
---

### Post by querulousennui on 2008-09-14
I'm trying to use unace and I keep getting an error message:


kristin@querulousennui:~/Desktop$ unace x FileName.ace
UNACE v1.2 public version

Processing archive: FileName.ace

FileName
     Could not create directory.

  Analyzing
File compressed with unknown method. Decompression not possible.

Error occurred. 



I'd really like to be able to get this file open, although the message is quite discouraging.
Help is appreciated.

Thanks.

---

### Post by Mornedhel on 2008-09-14
I'm assuming you are using the correct filename instead of FileName.ace here (really, you'd be surprised...)

Did you install the unace, or the unace-nonfree package ? Standard unace only works with ACE 1 (according to apt-cache show unace and apt-cache show unace-nonfree).

---

### Post by querulousennui on 2008-09-14
> **Mornedhel said:**
> I'm assuming you are using the correct filename instead of FileName.ace here (really, you'd be surprised...)

Did you install the unace, or the unace-nonfree package ? Standard unace only works with ACE 1 (according to apt-cache show unace and apt-cache show unace-nonfree).


Of course I'm using the actual file name and not the generic that I typed out.

To install unace, I used:
sudo apt-get install unace

The terminal went through the whole process and it seemed to be fine. 


I'll try the 'nonfree' package. I wasn't aware of it.
I unrared a file a moment ago, and that worked fine (same code but 'unrar' instead of 'unace').




UPDATE: I tried the 'non-free'. I think it worked, it's running. Thanks a bunch!

---

### Post by Mornedhel on 2008-09-14
> **querulousennui said:**
> Of course I'm using the actual file name and not the generic that I typed out.

As I said, you'd be surprised how often this sort of thing happens.

unrar has two different packages as well, but instead of unace and unace-nonfree, there's unrar-free and unrar (unrar-free can't handle some newer rar formats). Tricky.

---

