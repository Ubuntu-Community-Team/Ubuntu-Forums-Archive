---
title: "XAMPP Installation issues"
date: 2010-11-14
forum: Programming Talk
---

### Post by KevzJD on 2010-11-14
Hi guys, i following the easy to setup [xampp guide]("http://ubuntuforums.org/showthread.php?t=223410") and it seemed to install ok but when it came to starting it up i ran into a couple of issues, i done /opt/lampp/lampp panel and it brought up the xampp control panel and it says "Apache STOPPED" and when i try to click on execute it says "A new MainWindow has been created
Apache execute button clicked
/opt/lampp/lampp: line 195: echo: write error: Broken pipe
"

Not sure what to do here? Also when going to [http://localhost](http://localhost) it doesnt work, please help!

---

### Post by Mmmbopdowedop on 2010-11-14
```
sudo /etc/init.d/apache2 start
```

If that fails;

```
apt-get install apache2 php5 mysql-server phpmyadmin
```

That's probably all you need from a LAMP install anyhow. :)

---

### Post by KevzJD on 2010-11-16
Thanks a lot mate, works like a charm now :)

---

