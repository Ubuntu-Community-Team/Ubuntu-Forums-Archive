---
title: "How To: Ninan (Usenet Binary downloader)"
date: 2009-08-08
forum: Outdated Tutorials &amp; Tips
---

### Post by duffydack on 2009-08-08
Ninan is a server-side program to download from binary newsgroups.  It requires JAVA installed because its accessed/configured via a web browser (Firefox etc)
If you want a simpler application, look at [http://www.lottanzb.org/](http://www.lottanzb.org/)

[http://ninan.org](http://ninan.org) for more info.

Make sure Java is installed.

```
sudo apt-get update && sudo apt-get install sun-java6-jre sun-java6-plugin unrar par2
```

Open up a terminal

```
cd
wget http://ninanbetas.ninan.org/ninan-2.1.0.tar.gz
tar zxvf ninan-2.1.0.tar.gz

```

```
cd ~/ninan-2.1.0
chmod 755 ninancore.sh ninanstop.sh upgradeninan.sh createMYSQLDB.sh
```

Next edit ~/ninan-2.1.0/ninancore.sh

```
gedit ~/ninan-2.1.0/ninancore.sh
```

Next, enter this on a free line ***BETWEEN*** "fi" and "touch restart"

```
cd /home/your-username/ninan-2.1.0
```
[COLOR="Red"]**_CHANGE YOUR-USERNAME TO YOUR USERNAME OBVIOUSLY_**[/COLOR]
and save it.

Now we`ll make a launcher for it. Terminal again

```
gedit ~/Desktop/nohup.desktop
```

and copy/paste this whole block of text and save it. 
[COLOR="Red"]**_CHANGE YOUR-USERNAME TO YOUR USERNAME OBVIOUSLY_**[/COLOR]

```
#!/usr/bin/env xdg-open

[Desktop Entry]
Encoding=UTF-8
Version=1.0
Type=Application
Terminal=false
Icon[en_GB]=/home/your-username/ninan-2.1.0/images/ninan.ico
Exec=nohup /home/your-username/ninan-2.1.0/ninancore.sh > /home/your-username/ninan-2.1.0/nohup.out &
Name[en_GB]=Ninan
Name=Ninan
Icon=/home/your-username/ninan-2.1.0/images/ninan.ico
```

```
chmod +x ~/Desktop/nohup.desktop
```

You should now see a new launcher with ninan icon on your desktop.

Just run it (you wont see anything happening) and after a few seconds when its loaded, load up your web browser and point it to [http://localhost:9090/ninan](http://localhost:9090/ninan)
Username = admin
Password = password

You can now setup your news server and a lot of other stuff.

If you would like Ninan to be autostarted upon boot, got System/Preferences - Startup Applications and click ADD and use this info

[Name] Ninan
[Command] nohup /home/your-username/ninan-2.1.0/ninancore.sh > /home/your-username/ninan-2.1.0/nohup.out &

[COLOR="Red"]**_CHANGE YOUR-USERNAME TO YOUR USERNAME OBVIOUSLY_**[/COLOR]

---

