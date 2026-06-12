---
title: "how do I join 2 mp3 files?"
date: 2012-07-25
forum: New to Ubuntu
---

### Post by Old Jimma on 2012-07-25
Hi Community:

I record streaming audio radio program using streamripper.

I use crontab to make streamripper start when the program starts and end when the program ends.

Once in a little while the stream gets "dropped" for just a fraction of a second... i.e., the transmission of the stream is interrupted.

What this does to yeild 2 mp3 files of the show: one before the interruption and one after... with very little missing.

How can I join those 2 mp3 files to sort of "put the program together in one mp3 file?"

Thanks!
Old Jimma

---

### Post by Toz on 2012-07-25
The following will work:
```
cat 1.mp3 2.mp3 > new.mp3
```

In fact, you can list multiple mp3 files after cat. Just remember to terminate it with a redirection to a new mp3 file.

---

### Post by open.source on 2012-07-25
Or you can try Audacity from the software center and edit the files there.:)

---

### Post by PhilGil on 2012-07-26
mp3wrap is another option

To Install:
```
sudo apt-get install mp3wrap
```To use (will join all files in a directory - can also list individual files):
```
mp3wrap DestinationFile.mp3 *.mp3
```

---

### Post by alphacrucis2 on 2012-07-26
> **Toz said:**
> The following will work:
```
cat 1.mp3 2.mp3 > new.mp3
```

In fact, you can list multiple mp3 files after cat. Just remember to terminate it with a redirection to a new mp3 file.

Mp3 files have a header don't they? This would create erroneous data in the middle of the concatenated file.

---

### Post by coffeecat on 2012-07-26
> **alphacrucis2 said:**
> Mp3 files have a header don't they? This would create erroneous data in the middle of the concatenated file.

Indeed, and some mp3 players will simply stop when they get to the duration of the end of the first original fragment because of the data in the vbr header. And mp3wrap introduces its own problems by not correcting the duration field and by putting its own id3 tags into the metadata.

@Old Jimma, this post might have some useful information for you:

[http://ubuntuforums.org/showpost.php?p=10868154&postcount=4](http://ubuntuforums.org/showpost.php?p=10868154&postcount=4)

The first bit is irrelevant to your situation, but from "Here are a couple of links" the 4 listed steps *should* give you a way of concatenating the files into one and avoiding bad id3 tags and false vbr header. It is a rather large sledgehammer for one modest sized nut though, I must admit.

---

### Post by yuvraj23 on 2012-07-26
Use Audacity to join it.. If you use cat method then u may probably end up with a corrupted file

---

### Post by Old Jimma on 2012-07-26
My sincere thanks to all who responded to my query about joining 2 mp3 files.

I used the mp3wrap method and it seems to have worked perfectly!

Many thanks to all of my friends in the Ubuntu Community!

You can count on me upgrading to 12.04.1 from 10.04 on August 24! I'm really looking forward to it!!!

:P

Sincerely,
Old Jimma
Jimmastan, GA

---

