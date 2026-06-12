---
title: "Everything is Missing"
date: 2008-08-15
forum: New to Ubuntu
---

### Post by Obso1337 on 2008-08-15
Hey,
I sometimes let my parents and brothers use this laptop with Heron on it. I keep a guest account for them all to use. Yesterday my brother says he downloaded some music with Frostwire, tried to load it onto his mp3 player when suddenly everything was gone. Their bookmarks are gone, all files are gone, most programs and apps are gone. Oddly the only thing that seems to remain is their history in firefox. 
I have no idea how to find out what happened. :-(

---

### Post by croniksoft on 2008-08-15
Check the logs in your /var/log/messages and auth.log or paste them here so we can check it out

---

### Post by Obso1337 on 2008-08-15
Sorry, I should have mentioned. I am a recent convert from M$ and will need you to post the exact command I need to input for any output you need to see.

---

### Post by croniksoft on 2008-08-15
ok no problem,

run  "cat /var/log/messages > ~/Desktop/mes.txt" and "cat /var/log/auth.log > ~/Desktop/auth.txt"

now you should have 2 text file in your Desktop, i want you to copy the text in those files to this post or try to attach them to the forum.

---

### Post by Obso1337 on 2008-08-15
Ok, an abbreviated version of auth.txt should be attaches including only the logs from today and yesterday. (The file was to big otherwise) The other file "mes.txt" is to large by far even with just today and yesterday. I've broken it up into three files. Together they make up just from about 3-6pm yesterday, which is the closest I can get my brother to narrowing the time this occurred to.

Edit: Quick question. Just for my own learning purposes, will putting that > ~/Location/name on the end of any command save a file of the output?

---

### Post by anotherdisciple on 2008-08-15
Yes, putting > ~/Location/name will sent the output to a file... it will create the file if it doesn't exist, and it will write over the file if it does exist.

Putting >> ~/Location/name will append the output to the file if it exists and create the file if it doesn't.

---

### Post by anotherdisciple on 2008-08-15
PS- I learned a ton about the terminal from Kyral when I first started using Ubuntu... here is the guide he made >>> [http://ubuntuforums.org/showthread.php?t=73885]("http://ubuntuforums.org/showthread.php?t=73885")

---

### Post by Obso1337 on 2008-08-15
> **anotherdisciple said:**
> PS- I learned a ton about the terminal from Kyral when I first started using Ubuntu... here is the guide he made >>> [http://ubuntuforums.org/showthread.php?t=73885]("http://ubuntuforums.org/showthread.php?t=73885")
Thanks discile! I'll be sure to give that a read. :-)

---

