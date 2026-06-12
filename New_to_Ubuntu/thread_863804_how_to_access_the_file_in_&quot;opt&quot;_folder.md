---
title: "how to access the file in &quot;opt&quot; folder"
date: 2008-07-18
forum: New to Ubuntu
---

### Post by Unewbeginner on 2008-07-18
Hi all,

I have one program installed under "opt" directory. 
Now I need to unistall it. I saw the .uninstall file is there but I don't know how to change my directory over there.

Thanks,

---

### Post by SunnyRabbiera on 2008-07-18
use superuser mode in a terminal by typing in sudo nautilus.

---

### Post by Unewbeginner on 2008-07-18
> **SunnyRabbiera said:**
> use superuser mode in a terminal by typing in sudo nautilus.

Thanks a lot

---

### Post by nhandler on 2008-07-18
You shouldn't use sudo when running a graphical application ([http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)). So if you decide to run nautilus as root, you should run 'gksudo nautilus'. You can also go with a terminal approach and type 'sudo rm -r /opt/NameOfFolder' to remove it.

---

### Post by werries on 2008-07-18
> **Cheater said:**
> You shouldn't use sudo when running a graphical application ([http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)). So if you decide to run nautilus as root, you should run 'gksudo nautilus'. You can also go with a terminal approach and type 'sudo rm -r /opt/NameOfFolder' to remove it.
Is gksudo the same function as gksu? or is there a subtle difference?

---

### Post by ad_267 on 2008-07-18
> **werries said:**
> Is gksudo the same function as gksu? or is there a subtle difference?

```
adam@adam-desktop:~$ which gksudo
/usr/bin/gksudo
adam@adam-desktop:~$ file /usr/bin/gksudo
/usr/bin/gksudo: symbolic link to `gksu'

```

---

