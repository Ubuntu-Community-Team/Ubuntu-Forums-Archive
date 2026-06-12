---
title: "scanner only works as root"
date: 2008-08-27
forum: New to Ubuntu
---

### Post by Daedal on 2008-08-27
i had to install sane cvs because my scanner wasn't supported yet by the normal version. it's in a canon pixma mp470.

so i got the thing to work but it only works as root even though i've added scanner privileges to my normal username.  so i have no idea what the deal is.
anytime i try scanimage -T or xsane without sudo it just says "open of device pixma:04A91723 failed: Access to resource has been denied"

any help or attempt at help would be great.

---

### Post by iaculallad on 2008-08-27
Try adding your username to the scanner group:

```
sudo useradd -G scanner username
```

---

### Post by Daedal on 2008-08-27
it said "user daedal exists" but it still doesn't let me scan without using sudo.

could it have anything to do with the XX-libsane.rules file missing in /etc/udev/rules.d ? 
the stuff i was reading about how to install sane cvs said that older versions of ubuntu needed to have the file swapped out with a new one but you didn't have to do that in hardy.  i looked there and there's a libsane-extras.rules but not just a normal libsane.rules file. 
 
many thanks for replying.

---

