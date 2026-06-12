---
title: "Can't run php script from root directory"
date: 2008-10-01
forum: New to Ubuntu
---

### Post by sab0tage on 2008-10-01
I have a php script called hellaVCR. Its in my /var/www/hellaVCR directory.

The only way I can get the script to run correctly is to be IN the directory. For example:

```
ryan@rkoffice:/$ php /var/www/hellaVCR/hellavcr.php 
[10/01/08 06:54:52] processing tv...
ryan@rkoffice:/$
```

It doesn't run correctly.

BUT if im IN the directory before I run the script, it works fine...
```

ryan@rkoffice:/$ cd /var/www/hellaVCR
ryan@rkoffice:/var/www/hellaVCR$ php /var/www/hellaVCR/hellavcr.php [10/01/08 06:55:44] processing tv...
[10/01/08 06:55:44] House (x264, English)
[10/01/08 06:55:44]   last episode: 5x03
[10/01/08 06:55:58] saving xml file | done
ryan@rkoffice:/var/www/hellaVCR$ 
```


I'm ultimately needing to setup as a cron, but I figure I need to get it working in terminal first.

---

### Post by Peter09 on 2008-10-01
Its worth checking that you have no statements in your script that are assuming a path to a file. When you change the point where you run the script from you may be changing the default path.

---

### Post by hyper_ch on 2008-10-01
```

sudo apt-get install php5-cli

```

---

