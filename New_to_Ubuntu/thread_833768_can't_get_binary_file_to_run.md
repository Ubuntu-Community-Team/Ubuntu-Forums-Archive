---
title: "can't get binary file to run"
date: 2008-06-18
forum: New to Ubuntu
---

### Post by Cholera on 2008-06-18
i just put heron on this computer, and everything went smoothly untill i tried to put yamipod on. the program runs perfectly on my other ubuntu machine, but i can't even get the executable file to open at all on this computer.

i've re-downloaded it, re-extracted it, and it doesn't change anything.

anyone have any ideas? thanks.

---

### Post by sdowney717 on 2008-06-18
right click it check properties and see if it can execute as a program.
then open a terminal, cd over to it and type ./filename.bin or whatever and see if you get an error

---

### Post by Cholera on 2008-06-18
it says it will execute as a program. and um..i don't really know how to do anything at all in the terminal.

---

### Post by iaculallad on 2008-06-18
Use the chmod terminal command to create an executable file:

To make it executable:

```
sudo chmod a+x Filename.bin
```

To execute it:

```
sudo ./Filename.bin
```

---

### Post by Cholera on 2008-06-18
it just says no file/directory found.. :(

---

### Post by iaculallad on 2008-06-18
Ok. Assuming you downloaded this tarball file named **yam-linux.tar.gz**. Right-click on it on your desktop and choose "Extract Here" to extract its content to the folder named "**yam-linux**". Get in your terminal and issue the command:

```
 cd ~/Desktop/yam-linux
```

And execute the file:

```
./YamiPod
```

---

### Post by fenian on 2008-06-18
Heres what I did...

1-Downloaded [yamipod]("http://www.yamipod.com/download/click.php?action=go&to=yam-linux") to Desktop.

2-Extracted archive to Desktop (right click>extract here)

3-Moved the libfmodex.so.4.02.05 to /usr/ lib with the command...

>  sudo mv ~/Desktop/yam-linux/libfmodex.so.4.02.05 /usr/lib

4-Run YamiPod by right clicking on it and choosing open or with the command...
> 
~/Desktop/yam-linux/YamiPod

---

### Post by Cholera on 2008-06-18
aaaahh! i just keep getting:

```
/home/meara/Desktop/yam-linux/YamiPod: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

```

this is so stupid- the same program works perfectly on my other ubuntu machine!

---

### Post by jordanmthomas on 2008-06-19
```
sudo apt-get install Package libstdc++5
```
It should be installed already to be honest, but it may help.

Failing that, you can make a symbolic link to a libstdc++.so.*whateveryouDOhave*

---

### Post by Cholera on 2008-06-19
YES! great success! thanks jordan, that worked!

---

### Post by joseph! on 2010-04-30
Hi guys.. i did everything it says here still not working. iam running ubuntu 9.10

and when trying to run YamiPod by ./YamiPod it says 

./YamiPod: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: no such file or directory.

when i try to do a sudo aptitude search libstdc++ it only gives me the libstdc++6 and many other libstdc++6*** options, when i try to do a sudo aptitude install libstdc++6 it installs 0 files, meaning its already installed right?

dont know what to do i really want to use my ipod on ubuntu.

regards
PD: yeah i moved the libfmodex.so.4.02.05 to /usr/lib by sudo mv libfmodex.so.4.02.05 /usr/lib

thx for the time

---

### Post by gansvv on 2010-07-10
Use the download link from 
[http://packages.debian.org/lenny/i386/libstdc++5/download](http://packages.debian.org/lenny/i386/libstdc++5/download) and install.

E.g.:
```

wget http://ftp.us.debian.org/debian/pool/main/g/gcc-3.3/libstdc++5_3.3.6-18_i386.deb

sudo dpkg -i libstdc++5_3.3.6-18_i386.deb 

```

For 62bit: [http://packages.debian.org/stable/base/libstdc++5](http://packages.debian.org/stable/base/libstdc++5)

---

