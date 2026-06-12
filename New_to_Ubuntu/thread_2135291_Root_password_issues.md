---
title: "Root password issues"
date: 2013-04-13
forum: New to Ubuntu
---

### Post by MarkShark on 2013-04-13
I still depend on Windows as my main OS, but Ubuntu became an important partner with my IDEs. I've recently upgraded from 11.10 to 12.04, running fine until I decided to make a stupid mistake  of messing with the Compiz settings and making the GUI disappear. I made  some research and I managed to get it working again, but I felt like it  was still partially broken, and Unity became slower than before.

  I didn't bother with this anymore, found out the Compiz/GTK/Unity  settings are separated for each user, so I logged in as guest, deleted  my main account and created a new one.

  There's one problem though. When I created the new administrator  account, it didn't ask me for a password, but when I tried to log in, it  asks for a password... and now I have no idea on how to set/change the  password for this account, since I can only login as guest without  superuser/root access...
  
I use this PC for development, although I'm a total noob with Linux. I  would appreciate if someone knows a way to change the password rather  than having to reinstall 12.04 and all my applications again

  Thanks in advance

---

### Post by steeldriver on 2013-04-13
Hello and welcome - please follow the instructions in the tutorial below

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by MarkShark on 2013-04-13
Wow, that simple! Thanks a lot for the quick answer, very appreciated!

---

### Post by lisati on 2013-04-13
Have a look here as well: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by MarkShark on 2013-04-14
I have conscious about the power of the root, but it's always good to learn more about Linux. I've found out I was using "sudo" in wrong situations where I should use "gksudo" instead. That was a very informative article, thank you.

---

