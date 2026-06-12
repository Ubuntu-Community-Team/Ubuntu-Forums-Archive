---
title: "Nvidia Driver Problem"
date: 2008-05-05
forum: New to Ubuntu
---

### Post by ^^viktor^^ on 2008-05-05
So, I`ve just installed the new drivers for my 7600GT and after I restarted my computer the resolution dropped to 1024x768. There was a pop-up that sad I was using restricted drivers but in Restricted Driver Manager it says that I`m using the latest drivers. What`s the problem?

---

### Post by haiji on 2008-05-05
install nvidia settings manager

```
sudo apt-get install nvidia-settings
```

and try to change to change resolution and refresh rate. It will also give you more info about the driver and your actual settings.

---

### Post by ^^viktor^^ on 2008-05-06
Now things are even worse. The max resolution now is 800x600. WTF!?

btw This is the second time I`ve had this problem. The first time I had to format my Hadr Drive due to some problems, but this time i don`t want to do that again.

---

### Post by aktiwers on 2008-05-06
I have seen people say it works to dissable the driver, reboot and then enable them again.

But usually when I get these kind of problems, I just go for a manual install. Or use Envy, its in the repo's.

If you wanna try install them manually, here is a small guide I made:
[http://ubuntuforums.org/showthread.php?p=4105735&posted=1#post4105735](http://ubuntuforums.org/showthread.php?p=4105735&posted=1#post4105735)

---

