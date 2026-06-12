---
title: "x dosnt start (fluxubuntu)"
date: 2008-05-30
forum: New to Ubuntu
---

### Post by ozarkman on 2008-05-30
Sorry if this is the wrong place to post this. I just installed fluxubuntu on an old HP laptop and x wont start.I guessing it hangs on x starting. I can use recovery mode and do a startx and everything runs fine. is their anything I can do so x will start on bootup.

---

### Post by sayakb on 2008-05-30
Try:
```
sudo cp /etc/gdm/gdmprefetchlist /etc/gdm/gdmprefetchlist.backup
sudo gedit /etc/gdm/gdmprefetchlist
```

And add this line at the end:
```
/usr/bin/startx
```

---

### Post by ozarkman on 2008-05-30
sudo cp /etc/gdm/gdmprefetchlist /etc/gdm/gdmprefetchlist.backup

returns cp: cannot stat /etc/gdm/gdmprefetchlist': No such file or directory

I'm thinking I might have more luck installing ubuntu and then sudo install fluxbox instead of using the fluxubuntu .iso

---

