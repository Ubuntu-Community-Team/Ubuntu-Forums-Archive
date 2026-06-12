---
title: "User names and Passwords"
date: 2008-06-05
forum: New to Ubuntu
---

### Post by brez on 2008-06-05
Hi,

This is my first time to get engaged in a ubuntu forum. I loaded ubuntu on to my laptop a few weeks ago and did not come back to it again until yesterday. Yes you've guessed it I've forgotten my username and password. Am I looking at a reload of the software?????

---

### Post by lazyart on 2008-06-05
There is a way but if you just loaded it on and didn't do anything with it, it's easier to just reinstall.

---

### Post by spiderbatdad on 2008-06-05
Not at all, hopefully... Boot into recovery mode and run the command:```
passwd username
```That should prompt you to enter a new password for the username you enter.

If that fails, try:```
passwd -d username
passwd username
```

---

### Post by shifty_powers on 2008-06-05
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

will get you started.

---

### Post by forestpixie on 2008-06-05
[http://ubuntuforums.org/showpost.php?p=1774482&postcount=2](http://ubuntuforums.org/showpost.php?p=1774482&postcount=2)

[https://help.ubuntu.com/community/LostPassword](https://help.ubuntu.com/community/LostPassword)

If you don't remember your username and you used same for computer name it'll be at the bottom of the login screen > name-desktop

---

### Post by st33med on 2008-06-05
Not really. Try going into recovery mode at boot and type:
```
passwd <username>
```
It should walk you through the process.

---

