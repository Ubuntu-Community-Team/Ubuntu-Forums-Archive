---
title: "[SOLVED] Is there a program that can combine many mp3 into 1?"
date: 2008-06-12
forum: New to Ubuntu
---

### Post by Bigtime_Scrub on 2008-06-12
I got an audio book downloaded and I wanted to combine all the mp3's into one huge file. Is there any Linux program that can do this or any command line trick that will work. Some people who use Mac tell me in their terminal they can cat the files into a single directory but I have never used the cat command in that way.

---

### Post by ad_267 on 2008-06-12
Aparently you can just use cat like this. See here: [http://ubuntuforums.org/showthread.php?t=193144](http://ubuntuforums.org/showthread.php?t=193144)

So you can use: 

```
cat file1.mp3 file2.mp3 file3.mp3 > bigfile.mp3
```

cat is the greatest program ever.

---

### Post by iaculallad on 2008-06-12
Install mp3wrap:

```
sudo apt-get install mp3wrap
```

---

### Post by Bigtime_Scrub on 2008-06-12
Thank you both. They both work but that cat command is sweet!

---

