---
title: "Installing a Tar.GZ file"
date: 2013-11-06
forum: New to Ubuntu
---

### Post by blake4 on 2013-11-06
How do I install this file?: ultimate_control_v1.2_linux_64bit.tar.gz

Readme file says 

```
******************
* ULTIMATE CONTROL
******************


This is the agent application of "Ultimate Control". Along with the mobile application, it allows you to take control of your mouse and keyboard through Wifi (local netowrk) and Bluetooth.


PRECONDITIONS:
*************


In order to run the application, the Java Virtual Machine must be installed. It is posible to use the OpenJDK, which lots of linux distributions come with. If yours doesn't, you can use a package manager to get "openjdk-6-jre" package, or you can run the following command:


sudo apt-get install openjdk-6-jre


In order to use the bluetooth capabilities, you will need the "libbluetooth-dev" package. Again, you can get it through a package manager or with the following command:


sudo apt-get install libbluetooth-dev




INSTALLATION:
************


In the terminal, you will have to run the "install" script. Superuser permissions are required so you can run it with the following command:


sudo sh install


If everything went ok, you can now open the program with the following command (no matter in what directory you are):


ucontrol


You can also use the launcher available to open the program: "Ultimate Control". It is also possible to copy it anywhere.


UNINSTALL:
*********



```

---

### Post by oldos2er on 2013-11-06
Moved to Absolute Beginners.

---

### Post by jerome1232 on 2013-11-06
Basically do as the readme says.

Open your file browser, browse so that you are in the same folder as that installer. press ctrl+L and highlight the location that appears in the location bar and press ctrl+c to copy it. press ctrl+alt+t to open a terminal.

```
sudo -i
apt-get install openjdk-6-jre libbluetooth-dev
cd [press ctrl+shift+v to paste that location]
sh install
exit
exit

```

Now you should be able to run that program by opening a terminal (ctrl+alt+t) and typing

```
ucontrol
```

Maybe pressing alt+f2 to bring up the run dialog from HUD will work too.

---

### Post by Impavidus on 2013-11-06
Seems quite straight-forward to me. Unpack the archive (the .tar.gz file) and use the terminal to enter the directory where it puts the files. If necessary, run one or both of the **sudo apt-get install ...** commands. Before doing so you may have to run **sudo apt-get update**. Then run **sudo sh install**.

What is the part you have a problem with?

---

