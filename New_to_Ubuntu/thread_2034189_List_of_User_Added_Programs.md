---
title: "List of User Added Programs?"
date: 2012-07-28
forum: New to Ubuntu
---

### Post by arsenic_creed on 2012-07-28
Hello, I'm going to be getting a new computer in a month or so and I started wondering if there is any way to make my current computer show me all of the programs I've added to it since I installed it fresh so I can decide what I want on the new on quicker? I hope that made sense, I can clarify if it didn't.  Thank you for your time and any assistance anyone can offer!

---

### Post by kyphi on 2012-07-28
You can use ```
dpkg --get-selections > apps.txt
```
That will list ALL programs that have been installed and you can easily sift out the ones you want to install again.  Please note that the file "app.txt" will appear in your Home directory and, yes, you may give it any name you want.

---

### Post by nothingspecial on 2012-07-28
Everything you have installed yourself will be recorded in /var/log/apt
```

grep "install" /var/log/apt/history.log
```

if you have lots of archived logs also you can

```
zcat /var/log/apt/history.log* | grep "install"
```

---

### Post by arsenic_creed on 2012-07-30
Thank you both. I'll make sure to write down both of your suggestions so I have them again if I need them later during the switch.

---

