---
title: "changing themes and icons is complicated!"
date: 2014-07-19
forum: New to Ubuntu
---

### Post by Ghune on 2014-07-19
I'm pleased with xubuntu and normally don't really try to modify my OS, but I saw a theme that I found interesting I wanted to try it. Well, everything seems to be complicated!

So I created a folder in /usr/share/icons named treepana in order to copy paste the files. Of course (and you're probably already laughing) I couldn't do anything because I don't have the permission. I perfectly understand that for security reasons, I should stay away from being getting the root privilege (and I'm fine with that, actually), but I finally found a way to create a directory with: sudo mkdir /usr/share/icons/treepana
Now, I'd like to remove it because I found a way to copy paste a directory by using 
sudo cp -r /home/Username/Desktop/myNewTheme /usr/share/....How do I do remove this directory because I couldn't remove it without the privilege!

Finally, is there an easier way to install a theme or icons?

---

### Post by Frogs Hair on 2014-07-19
Try the following command which I have used in XFCE and enter your password when prompted. ```
gksudo thunar
```

---

### Post by Ghune on 2014-07-19
I typed sudo thunar and it worked! Thanks a lot!

Edit: gk sudo thunar asked to download something, but sudo worked fine. I guess it's because I use xubuntu...

---

### Post by Frogs Hair on 2014-07-20
The gksu package is no longer installed by default in 14.04.

---

