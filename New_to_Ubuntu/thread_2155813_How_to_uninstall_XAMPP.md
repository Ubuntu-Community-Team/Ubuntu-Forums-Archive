---
title: "How to uninstall XAMPP"
date: 2013-06-19
forum: New to Ubuntu
---

### Post by kamrava on 2013-06-19
Hi there

I have installed XAMPP with [this article ]("http://andyhat.co.uk/2012/07/installing-xampp-32bit-ubuntu-11-10-12-04/")and i would like to uninstall it.

Any idea would be appreciated.

---

### Post by arpanaut on 2013-06-19
Aparently it is as easy as this:

[http://www.apachefriends.org/en/xampp-linux.html#388](http://www.apachefriends.org/en/xampp-linux.html#388)

If you have made further configuration outside of /opt then you may need to reverse those changes.

---

### Post by monkeybrain2012 on 2013-06-19
Just remove all the files 

```
sudo rm -r /opt/lampp
```

---

### Post by andyhat on 2013-06-20
If you followed the instructions on my website you will also need to open up the main menu application and delete the Launcher con that you created. I will write a full step by step tutorial on uninstalling XAMPP soon.

---

