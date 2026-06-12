---
title: "[SOLVED] Cannot extract  zip file"
date: 2008-11-15
forum: New to Ubuntu
---

### Post by islandstone on 2008-11-15
I have a downloaded .zip file from play.com , containing MP3's , it is 103mb. When I attempt to extract/open it I get the following errors.

If I click it in Dolphin I get "Could not open the file, probably due to an unsupported file format.
zip:/home/island/Desktop/PlayDigital_14-11-2008_2058.zip"

Archive Manger "An error occurred while loading the archive."
command line output "End-of-central-directory signature not found.  Either this file is not a zipfile, or it constitutes one disk of a multi-part archive.  In the latter case the central directory and zipfile comment will be found on the last disk(s) of this archive.
note:  /home/island/Desktop/PlayDigital_14-11-2008_2058.zip may be a plain executable, not an archive
zipinfo:  cannot find zipfile directory in one of /home/island/Desktop/PlayDigital_14-11-2008_2058.zip or/home/island/Desktop/PlayDigital_14-11-2008_2058.zip.zip, and cannot find /home/island/Desktop/PlayDigital_14-11-2008_2058.zip.ZIP, period.

Which is the same message I get from the command line using unzip "file" -d dir

Is the file corrupted maybe?

---

### Post by jimmy the saint on 2008-11-15
sounds like a good guess.  you may try installing a different utility and see if that works, but my guess would be corrupted

---

### Post by baruch60610 on 2008-11-15
I'm wondering whether this is, in fact, a Zip file.  Are you sure about this being one, or are you relying on the extension (the .zip part)?  The reason I ask is that some servers rename MP3 files.  I'm not sure why they do it, but it is apparently to defeat certain software or corporations that try to block such downloads based on the .MP3 extension.

You might consider renaming your file from .zip to .mp3, and see whether you are able now to play it.  This sounds nuts, but it has worked for me on occasion when I downloaded MP3 files from a Russian Website.

---

### Post by jimmy the saint on 2008-11-15
If that is the case I would probably think a little before running it on my system.  Sounds kind of shady to me.

---

### Post by islandstone on 2008-11-16
Decided it was corrupted , and downloaded album as individual files instead to be sure. AS I have had no other .zip file problems(yet) , I reckon that's it. But I hope that play.com isn't supplying dodgy files ?

---

