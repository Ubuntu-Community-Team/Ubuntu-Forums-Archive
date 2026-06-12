---
title: "problems with sudo command"
date: 2008-07-04
forum: New to Ubuntu
---

### Post by kr3ko on 2008-07-04
everytime i want to update or use sudo command,i receive "sudo: timestamp too far in the future: Jul  4 16:35:01 2008".. can anybody help me with this thing.i dont have any clue what i did after i install ubuntu hardy but i believe i didn't do anything wrong.please help...

---

### Post by qrwe on 2008-07-04
What do you get when you run "date"? Sounds like a simple time desync.

---

### Post by ModelM on 2008-07-04
Have a look at this...

[http://www.spiration.co.uk/post/1341/sudo:](http://www.spiration.co.uk/post/1341/sudo:) timestamp too far in the future - fixing sudo problem

---

### Post by kr3ko on 2008-07-04
to qrwe: i receive the correct info..

---

### Post by anubhavrocks on 2008-07-04
try this 
```
sudo -v
```

Also read the manpage if you are interested.

---

### Post by kr3ko on 2008-07-04
thanx man..it's all fine now after i run sudo -k..

---

