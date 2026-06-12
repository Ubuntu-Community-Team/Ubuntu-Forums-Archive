---
title: "Ubuntu Restricted Extra"
date: 2012-06-27
forum: New to Ubuntu
---

### Post by czgirb on 2012-06-27
Installed **Ubuntu Restricted Extra** from **Ubuntu Software Center (USC)** and ended with:

```

**Package Operation Failed**
The Installation or Remover of the Software Package Failed
```
So, I re-open the **USC** with a purpose for looking a **Installation Repair** options ... with a click More Info options, it displayed **Flash Player Plugin** are not installed. So I check-mark the box and choose **Apply Changes** ... but ended with this:

```

**Package Operation Failed**
The Installation or Remover of the Software Package Failed

installArchives() failed: Preconfiguring packages ... 
Preconfiguring packages ... 
Preconfiguring packages ... 
Preconfiguring packages ... 
(Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 155016 files and directories currently installed.) 
Removing adobe-flash-properties-gtk ... 
Removing adobe-flashplugin ... 
Processing triggers for bamfdaemon ... 
Rebuilding /usr/share/applications/bamf.index... 
Processing triggers for desktop-file-utils ... 
Processing triggers for gnome-menus ... 
Processing triggers for hicolor-icon-theme ... 
Selecting previously unselected package libnss3-1d. 
(Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 154991 files and directories currently installed.) 
Unpacking libnss3-1d (from .../libnss3-1d_3.13.1.with.ckbi.1.88-1ubuntu6_i386.deb) ... 
Selecting previously unselected package libnspr4-0d. 
Unpacking libnspr4-0d (from .../libnspr4-0d_4.8.9-1ubuntu2_i386.deb) ... 
Selecting previously unselected package flashplugin-installer. 
Unpacking flashplugin-installer (from .../flashplugin-installer_11.2.202.236ubuntu0.12.04.1_i386.deb) ... 
Processing triggers for update-notifier-common ... 
flashplugin-installer: downloading [http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.2.202.236.orig.tar.gz](http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.2.202.236.orig.tar.gz) 
Installing from local file /tmp/tmphQJh_s.gz 
Flash Plugin installed. 
Setting up oracle-java7-installer (7u3-0~eugenesan~precise4) ... 
Downloading... 
--2012-06-27 18:48:57--  [http://download.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-i586.tar.gz](http://download.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-i586.tar.gz) 
Resolving download.oracle.com (download.oracle.com)... 118.98.42.107, 118.98.42.114 
Connecting to download.oracle.com (download.oracle.com)|118.98.42.107|:80... connected. 
HTTP request sent, awaiting response... 302 Moved Temporarily 
Location: [https://edelivery.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-i586.tar.gz](https://edelivery.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-i586.tar.gz) [following] 
--2012-06-27 18:48:57--  [https://edelivery.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-i586.tar.gz](https://edelivery.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-i586.tar.gz) 
Resolving edelivery.oracle.com (edelivery.oracle.com)... 173.223.18.174 
Connecting to edelivery.oracle.com (edelivery.oracle.com)|173.223.18.174|:443... connected. 
HTTP request sent, awaiting response... 302 Moved Temporarily 
Location: [http://download.oracle.com/errors/download-fail-1505220.html](http://download.oracle.com/errors/download-fail-1505220.html) [following] 
--2012-06-27 18:48:58--  [http://download.oracle.com/errors/download-fail-1505220.html](http://download.oracle.com/errors/download-fail-1505220.html) 
Connecting to download.oracle.com (download.oracle.com)|118.98.42.107|:80... connected. 
HTTP request sent, awaiting response... 200 OK 
Length: 5307 (5.2K) [text/html] 
Saving to: `./jdk-7u3-linux-i586.tar.gz' 
 
     0K .....                                                 100%  147K=0.04s 
 
2012-06-27 18:48:59 (147 KB/s) - `./jdk-7u3-linux-i586.tar.gz' saved [5307/5307] 
 
Download done. 
sha256sum mismatch jdk-7u3-linux-i586.tar.gz 
Oracle JDK 7 is NOT installed. 
dpkg: error processing oracle-java7-installer (--configure): 
 subprocess installed post-installation script returned error exit status 1 
No apport report written because MaxReports is reached already
Setting up libnss3-1d (3.13.1.with.ckbi.1.88-1ubuntu6) ... 
Setting up libnspr4-0d (4.8.9-1ubuntu2) ... 
Setting up flashplugin-installer (11.2.202.236ubuntu0.12.04.1) ... 
Errors were encountered while processing: 
 oracle-java7-installer 
Error in function:  
Setting up oracle-java7-installer (7u3-0~eugenesan~precise4) ... 
Downloading... 
--2012-06-27 18:49:01--  [http://download.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-i586.tar.gz](http://download.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-i586.tar.gz) 
Resolving download.oracle.com (download.oracle.com)... 118.98.42.107, 118.98.42.114 
Connecting to download.oracle.com (download.oracle.com)|118.98.42.107|:80... connected. 
HTTP request sent, awaiting response... 302 Moved Temporarily 
Location: [https://edelivery.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-i586.tar.gz](https://edelivery.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-i586.tar.gz) [following] 
--2012-06-27 18:49:01--  [https://edelivery.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-i586.tar.gz](https://edelivery.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-i586.tar.gz) 
Resolving edelivery.oracle.com (edelivery.oracle.com)... 173.223.18.174 
Connecting to edelivery.oracle.com (edelivery.oracle.com)|173.223.18.174|:443... connected. 
HTTP request sent, awaiting response... 302 Moved Temporarily 
Location: [http://download.oracle.com/errors/download-fail-1505220.html](http://download.oracle.com/errors/download-fail-1505220.html) [following] 
--2012-06-27 18:49:02--  [http://download.oracle.com/errors/download-fail-1505220.html](http://download.oracle.com/errors/download-fail-1505220.html) 
Connecting to download.oracle.com (download.oracle.com)|118.98.42.107|:80... connected. 
HTTP request sent, awaiting response... 200 OK 
Length: 5307 (5.2K) [text/html] 
Saving to: `./jdk-7u3-linux-i586.tar.gz' 
 
     0K .....                                                 100%  144K=0.04s 
 
2012-06-27 18:49:02 (144 KB/s) - `./jdk-7u3-linux-i586.tar.gz' saved [5307/5307] 
 
Download done. 
sha256sum mismatch jdk-7u3-linux-i586.tar.gz 
Oracle JDK 7 is NOT installed. 
dpkg: error processing oracle-java7-installer (--configure): 
 subprocess installed post-installation script returned error exit status 1 

```Any suggestion?

---

### Post by Curtis6767 on 2012-06-27
As in your thread about Java, you've got to get rid of that eugenesan PPA.

Try opening up the Software Center and then point your mouse to the upper left hand corner of your screen.  Under "Edit" select "Software Sources".  Go to the "Other Software" tab and scroll through there and see if eugenesan PPA is there. If so, remove it.

If you can remove that PPA that way, then reboot your computer start from there.

Also, don't install Flash from the Software Center. You'll want to go over to Firefox and look for Flash-Aid in the add-ons/extension area and install Flash-Aid from there.

But first try to get rid of that PPA.

---

