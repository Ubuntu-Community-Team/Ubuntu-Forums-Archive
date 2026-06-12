---
title: "Is it possible to download files offline?"
date: 2012-02-28
forum: New to Ubuntu
---

### Post by skyjuice88 on 2012-02-28
Hi ubuntu users. I just started venturing to Ubuntu from Windows. So I  have a few newbie question to ask regarding software/application  installations.

1) What are the difference between installing a  software from Ubuntu Software Center (Appstore for Ubuntu?) and by  typing sudo apt-get install from the terminal? Which one is preferred?

2)  Can I download a particular app/software from another pc and transfer  it to my ubuntu system? (My ubuntu is using broadband so there is a  quota). If yes, what should I do?

Thank you.

---

### Post by surfer on 2012-02-28
1) Software center is using apt-get in the background. you are free to choose to use apt-get or any frontend (Software Center, Synaptic, aptitude...). the result is the same.

2) maybe. if the package you are interested in has recently been downloaded it will still be in [FONT="Courier New"]/var/cache/apt/archives/[/FONT] . you can copy it from there and install it with[FONT="Courier New"] $ dpkg -i package.deb[/FONT] . in case the package has a lot of dependencies, this will be difficult.

you could install an apt-cacher (i suggest apt-cacher-ng) on one of the machines. if you install a package on both machines, it will only be downloaded once (if both machines use the apt-cacher machine as apt proxy).

---

### Post by drmrgd on 2012-02-28
Yes, it is possible to install packages offline by using either a CD or a USB drive.  From the official documentation (scroll down to the "Installing Packages without an Internet Connection" section):

[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

Hope that helps

---

### Post by cortman on 2012-02-28
Hi, welcome to Ubuntu!

Regarding offline installation, I have VB.Net program for that (download [[URL="http://ubuntuforums.org/showthread.php?t=1915489"]here]("https://sourceforge.net/projects/wassail/")[/URL] and instructions here, but you may want to look into [Keryx]("https://launchpad.net/keryx") as well- Keryx looks like the real do-all, terrific program for it, but I haven't successfully installed or run it yet.

---

### Post by skyjuice88 on 2012-03-09
Can those methods be used if I'm using Windows XP (with internet connection) and transfer to Ubuntu (without internet connection)? I tried using Keryx but I cant find the project package for Ubuntu 11.10

---

### Post by mastablasta on 2012-03-09
> **skyjuice88 said:**
> Can those methods be used if I'm using Windows XP (with internet connection) and transfer to Ubuntu (without internet connection)? I tried using Keryx but I cant find the project package for Ubuntu 11.10

Try usign cortman's program. it was made for just that.



Additionally you can use .deb files (kind of like .exe files for Ubuntu/debian). usually double click, give the passwrod and it iwll install them. note that debian debs are not always compatible with Ubuntu.

Or you can download and sue a source file (usually tar.gz.) which you then need to compile yourself. instructions on compiling are suually found within the file and those commands can be then copied into terminal to install.

---

