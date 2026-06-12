---
title: "firefox 7.0.1 bookmarks"
date: 2012-01-14
forum: New to Ubuntu
---

### Post by shadow120 on 2012-01-14
i just updated from 10.04 to 11,10 and i have the .json bookmark backup for firefox but in the new firefox it dose not have the import backup thing under show all bookmarks anyone know how to restore them? thanks

---

### Post by carl4926 on 2012-01-14
It is there, promise

---

### Post by carl4926 on 2012-01-14
Here you see
[http://paste.opensuse.org/23398848](http://paste.opensuse.org/23398848)

---

### Post by shadow120 on 2012-01-14
definitely not there

---

### Post by carl4926 on 2012-01-14
So this is a clean .mozilla
And you are trying to add to it your .json ?

---

### Post by shadow120 on 2012-01-14
ya i just installed ubuntu 11.10 and i have a .json backup file that i want to restore but the thing isnt there

---

### Post by carl4926 on 2012-01-14
Did you update the system?

Try deleting .mozilla and try again

---

### Post by shadow120 on 2012-01-14
all updates are done tried deleting the .mozilla also tired deleting the everything in /bookmarkbackups and copying my .json in there and that didnt work

---

### Post by lovinglinux on 2012-01-20
> **carl4926 said:**
> Did you update the system?

Try deleting .mozilla and try again

Please avoid recommending deleting the mozilla folder. Although it usually solves many problems, I only recommend that as last resort. Also be sure to make clear to the user that he/she will lose all passwords, bookmarks and settings if he do so. Usually I recommed creating a new profile first for testing, instead of deleting the default one. You can do that with the profile manager:

```
firefox -P
```

If the user report back saying that it works, then recommend copying the profile files he needs and delete the old profile.

---

### Post by lovinglinux on 2012-01-20
> **shadow120 said:**
> all updates are done tried deleting the .mozilla also tired deleting the everything in /bookmarkbackups and copying my .json in there and that didnt work

First of all, you need to update your system, because you should have Firefox 9 and not 7.

Please attach the firefox-report.txt file generated in your desktop after running the commands below:

```

echo 'Ubuntu Architecture' > ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
uname -a >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Ubuntu Version' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
cat /etc/lsb-release >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Firefox Packages' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
dpkg --get-selections | grep 'firefox*' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Firefox binaries' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
which firefox >> ~/Desktop/firefox-report.txt
file /usr/bin/firefox >> ~/Desktop/firefox-report.txt
file /usr/local/bin/firefox >> ~/Desktop/firefox-report.txt
file /opt/firefox/firefox >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Firefox divertion' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
file /usr/bin/firefox.ubuntu >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Sources' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
ls /etc/apt/sources.list.d >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
firefox ~/Desktop/firefox-report.txt
```

Also, try starting Firefox from a terminal using the commend below:

```
firefox -safe-mode
```

This is just a test, not a definitive solution. Report back if the problem persists or not.

---

### Post by carl4926 on 2012-01-20
> Please avoid recommending deleting the mozilla folder.I agree
But I already established the user profile was new and so not populated with settings that the user might prefer to keep. In fact he was trying to import the .json file from a backup.

Normally I recommend a 
```
mv .mozilla .mozilla-old
```

---

### Post by lovinglinux on 2012-01-20
> **carl4926 said:**
> I agree
But I already established the user profile was new and so not populated with settings that the user might prefer to keep. In fact he was trying to import the .json file from a backup.

Normally I recommend a 
```
mv .mozilla .mozilla-old
```

Fair enough. But the main reason why I gave you such suggestion, is because I saw another post of yours suggesting the same thing to solve a cookie issue. So whenever I see that deleting the profile is a trend, I usually give such advice.

---

### Post by carl4926 on 2012-01-20
> **lovinglinux said:**
> Fair enough. But the main reason why I gave you such suggestion, is because I saw another post of yours suggesting the same thing to solve a cookie issue. So whenever I see that deleting the profile is a trend, I usually give such advice.

You may mean this
[http://ubuntuforums.org/showpost.php?p=11613396&postcount=2](http://ubuntuforums.org/showpost.php?p=11613396&postcount=2)

---

### Post by lovinglinux on 2012-01-20
> **carl4926 said:**
> You may mean this
[http://ubuntuforums.org/showpost.php?p=11613396&postcount=2](http://ubuntuforums.org/showpost.php?p=11613396&postcount=2)

Yes. I know, you actually told the user to rename it. I am just making sure you are not one of those users who like to delete the profile to solve any Firefox problem. Point made. Case closed. Lets move on.

---

