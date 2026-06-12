---
title: "Wireless Dual Boot"
date: 2013-01-23
forum: New to Ubuntu
---

### Post by Dyronne on 2013-01-23
I own a toshiba satellite L855-S5112 and windows is installed on it and when I boot into windows 8 the wireless connects to the network flawlessly but when I boot into ubuntu 12.1 it recognizes the network but it does not connect to the network.

Can somebody help me, I am fairly new to ubuntu?

---

### Post by squakie on 2013-01-23
e need to know a little information before we can tell you anything - like what driver you might need.  So, please open a terminal window and type (just copy and paste these one at a time):

lspci > ~/abs-network.txt

lsusb >> ~/abs-network.txt

ifconfig >> ~/abs-network.txt

iwconfig >> ~/abs-network.txt

Now post a reply here and attach (via the paperclip) the abs-network.txt file which will be in your home folder.

---

### Post by Dyronne on 2013-01-24
I think its attached here is the abs file from my computer...

---

### Post by squakie on 2013-01-24
The driver has been rather sketchy, but here's video on installing it:

[http://www.youtube.com/watch?v=QFh2EZhUKgs](http://www.youtube.com/watch?v=QFh2EZhUKgs)

---

### Post by Dyronne on 2013-01-24
i tried it but every time i did it with either one of the driver downloads it comes to an message that said there was two errors, one being that "make : *** lib/modules/3.5.0-22-generic/build: No such file directory. Stop" and "make: *** [all] Error 2"

---

### Post by windscape on 2013-01-24
Hi,

You need to install the linux-headers package. You can do that using the following command: ```
sudo apt-get install linux-headers
```

---

### Post by squakie on 2013-01-24
If you haven't already, you may also want to install the build-essential package.  While it says it's for just building debs, it's the dependencies it installs that you want.

---

### Post by Dyronne on 2013-01-25
Well i don't know how I can do this because it does not recognize when the ethernet is connected either. I am using another computer to work from while I work on getting the wireless working. That is how do I install the linux header package or the debs so I can transfer it to my laptop

---

### Post by squakie on 2013-01-25
I'm running 64-bit 12.10 an I uninstalled build-essential, then I went through synaptic package manager (I don't know if apt-get or some other tool installed by default can do this or not), checked build-essential for installation and went to "File" and clicked on the Generate package script option.  The result is:

#!/bin/sh
wget -c [http://us.archive.ubuntu.com/ubuntu/pool/main/b/build-essential/build-essential_11.5ubuntu3_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/b/build-essential/build-essential_11.5ubuntu3_amd64.deb) 

This is an actual shell script you could run on another Linux box.  With a browser I  you could also just do the  [http://us.archive.ubuntu.com/ubuntu/pool/main/b/build-essential/build-essential_11.5ubuntu3_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/b/build-essential/build-essential_11.5ubuntu3_amd64.deb) and press enter, then when it wants to know what you want to do with the package select save.  You can then use a removable media - such as a usb flash drive - to load that file to your Linux box, then click on it and I *think* it will just open the software center so you can install it.

---

