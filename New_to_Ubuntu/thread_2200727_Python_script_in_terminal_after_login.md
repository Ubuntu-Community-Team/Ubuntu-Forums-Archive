---
title: "Python script in terminal after login"
date: 2014-01-20
forum: New to Ubuntu
---

### Post by swat-leader on 2014-01-20
Hi all,
        I have a python script that i would like to run once the desktop has loaded. the terminal window it runs in needs to remain open so i can see the output.

here is the code i use to run python script
```

 python -m pagerprinter.pagerprinter -c pagerprinter.ini
```

so i have made an .sh script to run and have tried the following

```
#!/bin/bash
gnome-terminal -e "python -m pagerprinter.pagerprinter -c pagerprinter.ini"

```
```
#!/bin/bash
python -m pagerprinter.pagerprinter -c pagerprinter.ini
```


the .sh script runs fine when i click on it but when i put it in startup applications nothing shows on my desktop

i have also tried adding it to rc.local and cron -e but nothing


could someone point me in the right direction

cheers Shaggy


P.S newish to Ubuntu

---

### Post by sanderj on 2014-01-20
what if you put the full path before the two file names?

---

### Post by fosterD on 2014-01-20
Hi, assuming the name of your script is "my-script.sh".

First, you need to make it excutable
```
sudo chmod u+x ./my-script.sh
```

To make it run at startup
1- Copy the script to /etc/init.d/
2- then, make a symbolic link in /etc/rcX.d/
```
ln -s /etc/init.d/my-script.sh /etc/rc2.d/S20my-script.sh
```
where:
X is your run level (you can check it with 'runlevel' command)
S means Start
20 is run priority

Hope this could help

---

