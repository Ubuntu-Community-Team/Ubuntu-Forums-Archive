---
title: "Completely reinstall apache2"
date: 2008-08-17
forum: New to Ubuntu
---

### Post by The Titan on 2008-08-17
I went through a tutorial on configuring apache2 and messed everything up, i dont even get error messages starting it it just fails.  But anyways, is there any way to completely reinstall apache 2 without losing my www folder(i know i can just copy these files)?  I am running ubuntu server 8.04

---

### Post by RealPSL on 2008-08-17
The files in your www folder were not a part of the original package so removing the apache2 related packages should not result in their removal. In short the task can be accomplished with ```
sudo apt-get remove apache2
```

I would still recommend that you take a copy of the directory just the same.

---

### Post by The Titan on 2008-08-18
> **RealPSL said:**
> The files in your www folder were not a part of the original package so removing the apache2 related packages should not result in their removal. In short the task can be accomplished with ```
sudo apt-get remove apache2
```I would still recommend that you take a copy of the directory just the same.
So if i do this and then
```

# apt-get install apache2

```Everything should be back to normal?


Edit:
It wasnt.  I did this and re-installed it and it didn't delete any of the files...   I also did purge with the same result.  So i uninstalled it deleted /etc/apache2 then reinstalled and it didn't replace the files.  I even tried dpkg reconfigure.....  Nothing.   I cuold really use some help, At this point i feel i need to just reinstall ubuntu server and i don't want to do that.  Anyone?

---

### Post by RealPSL on 2008-08-18
Which files did the purge not delete? Are you saying that after you deleted the files and reinstalled the /etc/apache2 directory was not put back in place?

---

### Post by The Titan on 2008-08-18
> **RealPSL said:**
> Which files did the purge not delete? Are you saying that after you deleted the files and reinstalled the /etc/apache2 directory was not put back in place?
exactly...   But i just reinstalled ubuntu server....

---

### Post by cdtech on 2008-08-18
You should always check your log files before deciding to reinstall. It could be easier to repair than reinstall.

[http://httpd.apache.org/docs/1.3/logs.html](http://httpd.apache.org/docs/1.3/logs.html)

Just my 2 pennies....

---

### Post by eightmillion on 2008-08-18
Next time you might try manually removing /var/www and /etc/apache2
```
sudo rm -rf /var/www/ /etc/apache2/
```
and then reinstalling apache2 with:
```
sudo apt-get remove --purge apache2 apache2-common
sudo apt-get install --reinstall apache2 apache2-common

```

---

### Post by sampath silva on 2010-05-31
> **The Titan said:**
> I went through a tutorial on configuring apache2 and messed everything up, i dont even get error messages starting it it just fails.  But anyways, is there any way to completely reinstall apache 2 without losing my www folder(i know i can just copy these files)?  I am running ubuntu server 8.04

i also face that kind of problem

---

### Post by SmaugDragon on 2012-02-03
This worked for me
[http://dancingpenguinsoflight.com/2009/02/how-to-completely-reset-an-apache-instance-in-ubuntu/]("http://dancingpenguinsoflight.com/2009/02/how-to-completely-reset-an-apache-instance-in-ubuntu/")

---

### Post by The Titan on 2012-02-03
Double thread resurrection.  Now that's impressive.  I don't believe I ever solved this problem, because I just reinstalled Ubuntu.

But removing the directories and then purging and reinstalling should do the trick, like somebody said like two and a half years ago.

---

