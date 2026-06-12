---
title: "Problem Using Mutagen Module in Python"
date: 2009-06-14
forum: Programming Talk
---

### Post by StunnerAlpha on 2009-06-14
Ey guys, I don't know if any of you have used mutagen for music tag editing, but I am currently having a problem and am not sure if it is my code, or the module, or the files that are the problem. Here is the error message I am receiving:
```

[u'50 Cent'] [u"If I Can't"] [u"Get Rich or Die Tryin'"]
Traceback (most recent call last):
  File "C:\Documents and Settings\tjubbal\My Documents\Aaron\testarea\winDecipher.py", line 16, in <module>
    album = audio["album"]
  File "C:\Python26\lib\site-packages\mutagen\easyid3.py", line 93, in __getitem__
    return getter(self, self.__id3[frame])
  File "C:\Python26\lib\site-packages\mutagen\_util.py", line 106, in __getitem__
    return self.__dict[key]
KeyError: 'TALB'

```
And here is my code:
```

from mutagen.easyid3 import EasyID3
import os

count = 0
for fname in os.listdir(os.getcwd()):
	split = os.path.splitext(fname)
	if split[1] == ".mp3":	
		if count == 0:
			if not os.path.isdir("Artists"):
				os.makedirs("Artists")
		audio = EasyID3(fname)
		artist = audio["artist"]
		title = audio["title"]
		album = audio["album"]
		print artist, title, album
		
	count += 1

```
So it only happens to print out the tag information for the first file... and no others.

I know it is not a problem with my files since they are all tagged and I made a similar program with the eyeD3 module and it worked flawlessly with all files.

Anyone know what is going on? Thanks in advance!

---

### Post by StunnerAlpha on 2009-06-15
Bump... anyone?

---

### Post by Can+~ on 2009-06-15
Just catch the exception, I'm guessing one of your files doesn't have the "album" tag defined.

(PD: 1000th post)

---

