---
title: "Installing packages from source"
date: 2008-07-16
forum: New to Ubuntu
---

### Post by XxUn70ucHaBlExX on 2008-07-16
I'm having trouble compiling anything from a tar.gz.

:(

I'm really new to ubuntu but I would really like to learn how to do this. I have read 3+ tutorials on how to do this but it always looses me. So if anyone can please run me through a COMPLETE compile, what to type EXACTLY, and what to download (wanted to try conky-1.5.1.tar.gz).

So if anyone would like to help please do so. Thank you. :confused::confused:

---

### Post by Canis familiaris on 2008-07-16
I hope this may help
```
tar -xvzf conky-1.5.1.tar.gz
cd conky*
./configure
make
sudo make install
```

Check out checkinstall for better integration with the package manager
[https://help.ubuntu.com/community/CheckInstall](https://help.ubuntu.com/community/CheckInstall)

---

### Post by hyper_ch on 2008-07-16
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by Sef on 2008-07-16
Read [How to Install Anything in Ubuntu]("http://monkeyblog.org/ubuntu/installing/").

---

### Post by XxUn70ucHaBlExX on 2008-07-19
Thanks!!!

---

