---
title: "Left over files"
date: 2008-10-05
forum: New to Ubuntu
---

### Post by toasty_ghosty on 2008-10-05
Hello

Just a quick question. When installing something, such as a package, or downloading something off line and stopping it before it is done, where does it go? Meaning are the partial files automatically deleted, or what? I have done that numerous times and I wonder how much space I have wasted.

Thanks.

---

### Post by ibuclaw on 2008-10-05
```
/var/cache/apt/archives
```

To clean up unused install packages.
```
sudo apt-get autoclean
```

To remove all install packages
```
sudo apt-get clean
```

Regards
Iain

---

### Post by wolfen69 on 2008-10-05
```
sudo apt-get autoremove
``` is good for getting rid of unused dependencies also. good to do after you uninstall something.

---

### Post by toasty_ghosty on 2008-10-05
After doing sudo apt-get autoremove I still have files in /var/cache/apt/archives. So I tried following tinivole's advice and tried his way. Still the files are there. I did not however use sudo apt-get clean as I do not want to remove install packages, or does that just remove the packages and not the programs themselves? I would think that is the case but I do not want to try without some input.

Thanks.

---

