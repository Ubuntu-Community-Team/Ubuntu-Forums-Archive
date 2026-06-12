---
title: "Auto Mounting Storage Partition"
date: 2012-10-10
forum: New to Ubuntu
---

### Post by ratompkins on 2012-10-10
I have a seperate storage partition (which is also my Windows partition right now) that I would like to have automatically mount when I log in since it currently does not. Any suggestions?

---

### Post by sandyd on 2012-10-10
Can you go to the terminal ( Unity Dash -> Type in 'terminal' -> Click on 'terminal')

and run this
```

sudo apt-get install ntfs-config
gksudo ntfs-config

```

You should then recieve a dialog box, where you can enable NTFS write (if you want), and select where you want your partitions to be mounted to.

---

