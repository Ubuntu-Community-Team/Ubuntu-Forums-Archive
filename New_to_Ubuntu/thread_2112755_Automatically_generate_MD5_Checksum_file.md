---
title: "Automatically generate MD5 Checksum file"
date: 2013-02-05
forum: New to Ubuntu
---

### Post by jerden on 2013-02-05
Is it possible to create a MD5 file automatically any time a file is added or changed on a PC?

I posted earlier about enabling MD5 Checking on pureftpd but it doesn't seem that will get done. So I was thinking if a MD5 file could be created every time a file is added or changed that file could be downloaded and checked. 

Best case scenario would be I upload a file say test.txt and in turn it creates a file with the MD5 number as the name of the file so M8fhfngE9LFNG.txt I could have a script record the name, take in everything before the .txt and use it as a comparison to the MD5 Sum of the file on the local computer.

That way I can get an exact copy of the MD5. Would anyone have a clue if that is possible or a better way of going about it?

It is for an automated service to prevent a client downloading old files from the server or allow them to download updated ones.

---

