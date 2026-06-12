---
title: "Installing HP2400 drivers in Ubuntu 10.10"
date: 2011-04-23
forum: Outdated Tutorials &amp; Tips
---

### Post by pepperspray038 on 2011-04-23
----


Source

```
http://www.elcot.in/linuxdrivers_download.php#Scan2400
```

Download Mirrors

```
https://rapidshare.com/files/458794280/linux_hp2400_drivers.zip
http://www.megaupload.com/?d=NS14G09G
```


----



Beginner's Guide to installing HP2400 scanner drivers
Last updated: 4-23-2011
Uploader: pepperspray038



Just a short introduction. I literally spent an entire day getting my HP2400 to work with XSane and Gimp. The purpose of this guide is to spare that ordeal. 

I took the liberty of updating the guide included in the source for Ubuntu 10.10 users. For the original documentation on the drivers, please see "original_readme.txt" and the "EULA.txt"

Advance Linux users need not use this guide as it is aimed for total beginners such as myself. Feel free to correct any instructions you find here that are wrong. 

* Driver source - [http://www.elcot.in/linuxdrivers_download.php#Scan2400](http://www.elcot.in/linuxdrivers_download.php#Scan2400)

** Tested on a machine running on Ubuntu 10.10 (maverick), Kernel Linux 2.6.35-28-generic, GNOME 2.32.0

*** I do not take credit for the drivers found in this file nor do I take any responsibility for damages done to your computer if something goes wrong. The steps provided below are what I took to get the drivers to work on my machine.



---Guide---


1. On your desktop, create a folder called "scanner".


2. Extract the contents of "linux_hp2400_drivers.zip" inside "scanner".


3. Open Nautilus File Manager (folder browser).


4. To the left side of Nautilus, there is Places by default. Click on your desktop to navigate to it. 


5. We need the directory of your desktop. On your keyboard, hold down CTRL + L. A location bar will appear on top portion. Take note of it. It will follow this format.

```
home/example/Desktop
usr/example/Desktop
```



6. Open GNOME Terminal. There are 2 ways to do this.

```
a. Hold down CTRL + ALT + T.
b. Main Menu > Accessories > Terminal.
```


7. Login as root user. To do this enter "sudo bash" without the " ". It will prompt you for your administrator password. Enter your password, and then press enter. If you have followed this step correctly, you will see this.

```
root@example:~$
root@example2:~$
```

8. Type the command "cd /"


9. I suggest using the text editor for the following steps. Insert your desktop directory BEFORE the following lines. 


```
(insert your Desktop directory here)/scanner/hp2400.tgz
(insert your Desktop directory here)/scanner/libsane.tgz
```


If done correctly this is what it should look like.


```
home/example/Desktop/scanner/hp2400.tgz
home/example/Desktop/scanner/libsane.tgz
```


10. Copy and paste the two commands in the terminal. To paste the command on the terminal, hold down CTRL + SHIFT + V. Press enter to extract the drivers.


11. Copy and paste this other command to the terminal. 


```
nano /etc/sane.d/dll.conf
```


Nano is a text editor we can run from the terminal. We will be listing our HP2400 to the list of scanners onto the dll.conf.



12. Use the arrow keys on your keyboard. Look for "HP5400". Once you have located it, insert a line break by pressing enter. Type "hp2400" w/o the " ".



13. We're done. To exit the text editor and save the changes, Hold down CTRL + X. You will be prompted with "Save modified buffer (ANSWERING "No" WILL DESTROY CHANGES) ?". Press "Y" to confirm. The next prompt is "File Name to Write: /etc/sane.d/dll.conf". Disregard the rest of the commands there. Press enter to finish editing the text. You'll be back on the terminal still logged in as root.

To check if you've saved the changes on the dll.conf, you may repeat Step 11.


14. To check if the drivers were installed successfully, enter this code. 


```
scanimage -L
```


Mine said this...

```
device `hp2400:libusb:003:003' is a Hewlett-Packard hp2400 flatbed scanner
device `genesys:libusb:003:003' is a Hewlett Packard ScanJet 2400c flatbed scanner
```


Your HP2400 should now work with XSane or SimpleScan.



---End of Guide---

---

