---
title: "FTP Scritp needs improovment please help!"
date: 2011-05-24
forum: Programming Talk
---

### Post by conradin on 2011-05-24
Hi all, I have an Expect script (I dont mind converting to bash)
which takes an image from my web cam then sends it to my FTP server.
That part seems fine, but what I need to do is make the script modify the 
file name with a date (date & time) when it is loading it to the server. 
Currently, my file persistently overwrites it self.

I'm trying to set up a real simple security camera type script so I can see
if my roommates are going in my room when I'm not around.

```

#!/usr/bin/expect

spawn streamer -f jpeg -o /home/j/image.jpeg
expect "16"
sleep 10


spawn ftp ftp.server.edu
expect ":"
send "UserName\r"
expect "Password:"
send "PassWord\r"
expect "ftp>"
send "put /home/j/image.jpeg  /webCamImage.jpeg\r" 
expect "ftp>"
send "bye\r"

```

---

### Post by aeiah on 2011-05-25
how about replacing ```
send "put /home/j/image.jpeg  /webCamImage.jpeg\r" 
```
with
```
send "put /home/j/image.jpeg  /webcam-`date`.jpeg\r" 
```

date has many formatting options, and you could save as, say 'webcam-2011-05-25_14.40.jpeg' or something.

incidentally, is this your own server? do you have ssh access? if so it may be simpler to set up ssh keys for automatic login and just scp your image over in a cron job.

---

### Post by conradin on 2011-06-06
1. aeiah, Thank you, your idea gave me an idea, and both work.
2. OMG, Look man!: webcamd And: webcam! right in the ubuntu software center! All is well!

---

