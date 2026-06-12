---
title: "HOWTO: Install Firefox 2 RC1 + Widgets"
date: 2006-09-27
forum: Outdated Tutorials &amp; Tips
---

### Post by Karail on 2006-09-27
Forgive me if this article is not too detailed but i am new to linux myself. All credit for the attached scripts goes to the following two articles:

[ HOWTO Install new Firefox 2.0 Beta]("http://ubuntuforums.org/showthread.php?t=248158")
[ A polished Firefox for Dapper]("http://ubuntuforums.org/showthread.php?t=175394")

Following these instructions will install the latest firefox II release plus add widgets which imporve the appearance of forms. Simply extract the attached file to your desktop then open a terminal and do the following:

```

cd ~/Desktop
chmod +x installnewfirefox.sh installfirefoxwidgets.sh
./installnewfirefox.sh
./installfirefoxwidgets.sh

```

---

### Post by termite on 2006-09-27
You beat me to to it.  Oh well...

Anyway, if you followed the instructions in my post about installing Beta 2, you don't need to do all this.  All you need to do is download the .tar.gz from http://ftp.mozilla.org/pub/firefox/releases/<insert locale here>/http://ftp.mozilla.org/pub/mozilla.org/firefox/releases/2.0rc1/linux-i686/en-US/firefox-2.0rc1.tar.gz

and extract to /opt/firefox.  You may want to move your old installation with  ```
sudo mv /opt/firefox /opt/firefox.old
``` first.

Script to do all this for you attached.

---

### Post by ThrobbingBrain66 on 2006-10-10
great howto...

however there's an issue with the alignment of the search button at the top of yahoo.com.  anyway to address this issue?

thanks again!

---

