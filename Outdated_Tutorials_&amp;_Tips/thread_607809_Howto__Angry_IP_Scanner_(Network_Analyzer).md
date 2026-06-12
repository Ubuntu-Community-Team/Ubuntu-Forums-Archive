---
title: "Howto:  Angry IP Scanner (Network Analyzer)"
date: 2007-11-09
forum: Outdated Tutorials &amp; Tips
---

### Post by handband2 on 2007-11-09
Angry IP Scanner is a utility to help analyze networks.  It is available for all platforms.  If you want to learn more about the program go here:  [http://www.angryziber.com/ipscan/](http://www.angryziber.com/ipscan/)

**Here is a howto guide to install it on Ubuntu:**

**1.** Make sure you are running java since the Linux version is a .jar file.
[LIST]
[*]Check which version of java:
[/LIST]
```
$ java --version
```
[LIST]
[*]If you need to change and/or upgrade to a different version of java do the following:
[/LIST]
```

$ sudo apt-get update
$ sudo apt-get install sun-java5-bin
$ sudo update-alternatives --config java

```
[LIST]
[*]Then check again:
[/LIST]
```
$ java --version
```
[LIST]
[*]If you have more question on this go here:  [https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)
[/LIST]


**2.** Download Angry IP Scanner.
[LIST]
[*]You can go to the webpage which will direct you to download the file:  [http://www.angryziber.com/ipscan/download.php](http://www.angryziber.com/ipscan/download.php)
[/LIST]
**[INDENT]or[/INDENT]**
[LIST]
[*]Here is a direct link:
[/LIST]
```

$ wget http://superb-west.dl.sourceforge.net/sourceforge/ipscan/ipscan-linux-3.0-alpha2.jar

```


**3.** The jar file can be placed anywhere but to make it easy we will user the /opt directory
[LIST]
[*]Make directory and move file:
[/LIST]
```

$ sudo mkdir /opt/angry-ip-scanner
$ sudo mv ipscan/ipscan-linux-3.0-alpha2.jar /opt/angry-ip-scanner
$ sudo chown -R <username>:<username> /opt/angry-ip-scanner
$ chmod +rx /opt/angry-ip-scanner/ipscan-linux-3.0-alpha2.jar

```


**4.** Make an application file
[LIST]
[*]Use the terminal and gedit to create the file:
[/LIST]
```

$ sudo gedit /usr/share/applications/angry-ip-scanner.desktop

```
[LIST]
[*]Insert the following in gedit:
[/LIST]
```

[Desktop Entry]
Encoding=UTF-8
Name=Angry IP Scanner
Exec=java -jar /opt/angry-ip-scanner/ipscan-linux-3.0-alpha2.jar %U
Icon=/usr/share/pixmaps/gnome-netstatus-tx.png
Type=Application
Categories=Application;Network;
Comment=A Program for Analyzing Networks

```


**Notes:**
If the location of the .jar file is different, don't forget to change the **Exec** in the **[Desktop Entry]**.

---

