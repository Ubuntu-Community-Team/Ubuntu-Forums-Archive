---
title: "HOWTO- Dapper: Azureus with Sun Java"
date: 2006-04-27
forum: Outdated Tutorials &amp; Tips
---

### Post by angrykeyboarder on 2006-04-27
1. Download Sun Java Runtime Environment (JRE).[INDENT]     a) Open Firefox (or your graphical browser of choice) and enter [http://java.sun.com/j2se/1.5.0/download.jsp]("http://java.sun.com/j2se/1.5.0/download.jsp")

    b) Click on “Download JRE 5.0 Update 6”.

    c) Click the "Accept license agreement" radio button (I always seem to forget this one).

    d) Scroll down to "Linux Platform - J2SE(TM) Runtime Environment 5.0 Update 6" (Be sure it's not the SDK right above it).

    e) Click on "Linux self-extracting file" (DO ***not*** download the "Linux RPM in self-extracting file").
[/INDENT]2. Open a Terminal.

3. CD to the directory where you just downloaded jre-1_5_0_06-linux-i586.bin (unless of course it was your home directory, in which case you are already there. ;->).

4. Make sure the Ubuntu Multiverse repository is enabled in your sources.list file (howto).

5*. Enter ```
wget [http://archive.ubuntu.com/ubuntu/pool/universe/s/swt-gtk/libswt-gtk-3.1-java_3.1-2ubuntu1_all.deb]("http://archive.ubuntu.com/ubuntu/pool/universe/s/swt-gtk/libswt-gtk-3.1-java_3.1-2ubuntu1_all.deb")
 
``` 6. Enter ```
sudo dpkg -i libswt-gtk-3.1-java_3.1-2ubuntu1_all.deb

``` 7. Enter ```
sudo apt-get update && sudo apt-get install fakeroot java-package libcommons-cli-java liblog4j1.2-java libseda-java

``` 
8. Enter ```
 fakeroot make-jpkg jre-1_5_0_04-linux-i586.bin 
``` 8. You will be presented with another very long license agreement. Scroll to the bottom of it and enter.

9. Enter
```
dpkg -i sun-j2re1.5_1.5.0+update06_i386.deb
``` 
10.Enter
```

wget [http://ftp.debian.org/debian/pool/contrib/a/azureus/azureus_2.4.0.2-1_all.deb]("http://ftp.debian.org/debian/pool/contrib/a/azureus/azureus_2.4.0.2-1_all.deb")

``` 11.And last but not least, enter ```
sudo dpkg -i azureus_2.4.0.2-1_all.deb
``` 

That's it. You're done! Now enjoy the most sophisticated Bittorrent (albeit somewhat slow) client out there !



*As of this writing libswt-gtk-3.1-java_3.1-2ubuntu1_all.deb was not in the Dapper repository, so this download is from Breezy.

---

