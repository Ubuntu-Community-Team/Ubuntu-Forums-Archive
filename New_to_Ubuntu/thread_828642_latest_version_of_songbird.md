---
title: "latest version of songbird?"
date: 2008-06-13
forum: New to Ubuntu
---

### Post by northwestuntu on 2008-06-13
how to install latest version of songbird 0.6?

---

### Post by wolfen69 on 2008-06-14
[Here's]("http://www.cyberciti.biz/faq/install-tarballs/") how. if you dont mind using .5, [here]("http://www.getdeb.net/search.php?keywords=songbird") is the link for it. just click to install.

---

### Post by northwestuntu on 2008-06-14
yeah i am using .5 right now. but wanting to check out the new version

---

### Post by aysiu on 2008-06-14
Try [this](https://help.ubuntu.com/community/Songbird#head-25861b3066dba454799a78e77edbe7ccfe8978e1).

---

### Post by mjwhitfield on 2008-06-14
I just grabbed the tar.gz from [http://getsongbird.com/](http://getsongbird.com/) then did the following:
```
cd /opt
sudo mkdir Songbird/
sudo chown -R MYUSERNAME:MYUSERNAME Songbird/
sudo chmod -R g+w Songbird/
mv ~/Songbird_0.6_linux-i686.tar.gz .
tar zxvf Songbird_0.6_linux-i686.tar.gz
cd Songbird
./songbird
```

I always favour shoving apps like this in /opt/.  Ubuntu never use it for anything, so it's just personal preference on my part to use it. You can untar it anywhere you like.

As it's an alpha, it's quite handy being able to see the errors in the terminal, though I've not had any show stopping issues yet. You can make a launcher in the usual way if you wish too. fyi the songbird icon for the launcher is in: ```
/opt/Songbird/chrome/icons/default.xpm
```

It makes a folder in ~/.songbird2 which contains all your local settings, I've not started hacking around in there yet though.

---

### Post by aysiu on 2008-06-14
That's what the script I linked to does.

---

