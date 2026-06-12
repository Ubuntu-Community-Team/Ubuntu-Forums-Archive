---
title: "Not so new user but..."
date: 2024-06-19
forum: New to Ubuntu
---

### Post by mifzt-4 on 2024-06-19
...still have no idea!

I've been using Ubuntu for a couple of years ago on a spare PC for web browsing etc. The PC runs way better than it did on Windows 10 and i an happy with it.
However I run into issues when trying to install stuff. I've downloaded a Linux driver and Iscan software bundle package for an Epson V200 scanner which I'd like to use on this PC. I've extracted the content of the compressed file to the desktop and in there is a file "Install.sh". I have dragged this into the terminal and pressed enter. This is the result:


:~$ '/home/john/Desktop/iscan-gt-f670-bundle-2.30.4.x64.deb/install.sh' 
[sudo] password for John: 
Hit:1 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) jammy InRelease
Hit:2 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) jammy-updates InRelease              
Hit:3 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) jammy-backports InRelease            
Get:4 [https://dl.winehq.org/wine-builds/ubuntu](https://dl.winehq.org/wine-builds/ubuntu) jammy InRelease [8,041 B]       
Hit:5 [https://ppa.launchpadcontent.net/tomtomtom/woeusb/ubuntu](https://ppa.launchpadcontent.net/tomtomtom/woeusb/ubuntu) jammy InRelease 
Hit:6 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jammy-security InRelease               
Hit:7 [https://deb.opera.com/opera-stable](https://deb.opera.com/opera-stable) stable InRelease
Err:4 [https://dl.winehq.org/wine-builds/ubuntu](https://dl.winehq.org/wine-builds/ubuntu) jammy InRelease
  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 76F1A20FF987672F
Reading package lists... Done
W: GPG error: [https://dl.winehq.org/wine-builds/ubuntu](https://dl.winehq.org/wine-builds/ubuntu) jammy InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 76F1A20FF987672F
E: The repository 'https://dl.winehq.org/wine-builds/ubuntu jammy InRelease' is not signed.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.

I have literally no idea what I need to do to get this to install.

Please go easy on me!

---

### Post by ActionParsnip on 2024-06-20
You need to add the Wine PPA GPG key

---

### Post by grahammechanical on 2024-06-21
Did you choose to install wine? Or did install.sh install it?

As yet we do not know what version of Ubuntu. You can open Software & Updates>Other Software tab and disable the dl.winehq.org repository. Then follow these instructions to install wine.

[https://wiki.winehq.org/Ubuntu](https://wiki.winehq.org/Ubuntu)

You might be able to solve this problem by only installing the dl.wine.org repository key. 

> Download and add the repository key: 

 sudo mkdir -pm755 /etc/apt/keyrings
sudo wget -O /etc/apt/keyrings/winehq-archive.key [https://dl.winehq.org/wine-builds/winehq.key](https://dl.winehq.org/wine-builds/winehq.key)


The /etc/apt/keyrings  directory may already exist. It is your choice. a) install the repository key and see if that fixes things. Or, b) disable the existing dlwine.org repository and start again following the wine instructions. And then run install.sh

Regards

---

### Post by grahammechanical on 2024-06-21
I am guessing that you have purchased some kind of scanner and the software to use it (including driver) is for the Windows operating system. So, you are hoping that things will work under wine. Is this correct?

Once you have install the wine repository key you might have better success if you run

```
wine explorer.exe
```

That will give you a Windows type file manager. You can then browse to where you have put install.sh and use explorer to run the file. You need to install the ISCAN software through wine. The ISCAN software may or may not put an icon on the desktop or in the dash which you can use to launch the ISCAN application and hope that it connects to the scanner.

This may help

[https://askubuntu.com/questions/1303419/installing-epson-iscan-for-linux](https://askubuntu.com/questions/1303419/installing-epson-iscan-for-linux)

Regards

---

### Post by him610 on 2024-06-22
@mifzt-4
You might want to review this post, [https://askubuntu.com/questions/389880/installation-of-epson-scanner-on-ubuntu]("https://askubuntu.com/questions/389880/installation-of-epson-scanner-on-ubuntu")
Looks like it was done from command line.

---

