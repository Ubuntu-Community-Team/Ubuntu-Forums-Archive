---
title: "Admin password no longer works"
date: 2014-01-03
forum: New to Ubuntu
---

### Post by haroldtheferret on 2014-01-03
I've been using Ubuntu for a few weeks and everything was working fine, only a few days ago I tried to install new software from the Software Centre- Steam, I think it was- and when I was prompted to put in my admin password to authorise the installation, the password didn't work. Wondering if it was just the Software Centre that was messing up, I tried using the same password to unlock my user accounts but the password didn't work there either. I haven't changed the password since I started using Ubuntu and the password I tried to put in has worked plenty of times before. (It even worked on the same day as the issue started. Does anyone know what's causing this or if anyone has experienced this before? I repeat that I definitely haven't forgotten my password nor changed it. 
(Sorry if this has been solved in another thread)

---

### Post by hoopia on 2014-01-03
Can you please post /var/log/syslog and authlog?

Are you able to login with root or any other password? Does sudo work?

---

### Post by deadflowr on 2014-01-03
It has happened to user before, though I don't think exactly the same as you have experience.(maybe someone has had this happen as you have)
The simple thing to do is to reset the password
Try the solution found here
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

of note, when you run the mount command, the -o is the letter and not a zero.
You need to do this command because recovery mode loads it as read-only and that command remounts it as read-write.
Otherwise it won't make any changes.

---

### Post by whitesmith on 2014-01-03
Sometimes it's the simple, stupid things we all do that lead us to the most grief. Caps lock ... case of characters in PW ... Num Lock if you're using the keypad. Are all those OK? Cheers!

---

