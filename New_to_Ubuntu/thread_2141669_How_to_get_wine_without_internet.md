---
title: "How to get wine without internet?"
date: 2013-05-03
forum: New to Ubuntu
---

### Post by Dayyan on 2013-05-03
[COLOR=#000000]I've recently installed Ubuntu 12.10 on a computer and don't have access to the internet on that computer. All the instructions that I've seen on how to install wine involve being connected to the internet, which I am not. So is there a way that I could just download the needed files on the computer which I am using now (which runs Xp) and just use my flash drive to send the files to the computer running Ubuntu?

Please tell me.[/COLOR]

---

### Post by ibjsb4 on 2013-05-03
If you haven't updated since you installed 12.10, then you are lacking many packages.

[https://help.ubuntu.com/community/InstallingSoftware#Installing_packages_without_an_Internet_connection](https://help.ubuntu.com/community/InstallingSoftware#Installing_packages_without_an_Internet_connection)

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=update+without+internet&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=update+without+internet&sa=Search&cof=FORID:9)

---

### Post by Jason Kuzhively on 2013-05-03
If you had used the "Search" Function, you would have already go the answer...

> Installing all of the dependencies is not needed. You can just download these to install wine:
cabextract : [http://packages.ubuntu.com/natty/cabextract](http://packages.ubuntu.com/natty/cabextract)
gettext : [http://packages.ubuntu.com/natty/gettext](http://packages.ubuntu.com/natty/gettext)
libmpg123-0 : [http://packages.ubuntu.com/natty/libmpg123-0](http://packages.ubuntu.com/natty/libmpg123-0)
libopenal1 : [http://packages.ubuntu.com/natty/libopenal1](http://packages.ubuntu.com/natty/libopenal1)
wine1.3 : [http://packages.ubuntu.com/natty/wine1.3]("http://packages.ubuntu.com/natty/wine")

Transfer these packages to your home folder, and type in a terminal:
 	Code:
 	
cd ~ sudo dpkg -i cabextract*.deb gettext*.deb libmpg123-0*.deb libopenal1*.deb wine1.3*.deb 
And wine will be installed 				

If you have any problems, then go to the [Original Thread](http://ubuntuforums.org/showthread.php?t=1762889) and ask for help there.

---

### Post by ibjsb4 on 2013-05-03
Install Natty (reached end of life two years ago) on 12.10?

Sometimes old threads are left buried for a reason :)

---

### Post by AndyOpie150 on 2013-05-03
Do you have a wireless card that is functioning? I use my phones HotSpot function to connect to the internet and upgrade, install pkgs, etc.

Just another option to look into.

---

