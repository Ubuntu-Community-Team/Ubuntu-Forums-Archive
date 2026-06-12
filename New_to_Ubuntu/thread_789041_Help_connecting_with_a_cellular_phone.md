---
title: "Help connecting with a cellular phone"
date: 2008-05-10
forum: New to Ubuntu
---

### Post by mickeygood on 2008-05-10
I am new with linux as os I've got an sony vaio lapto pmodel pcg-k15 
pentium 4 2.80 ghz ,512dr sdram . Beacause i live in a rural area , i use my V3 rzor celular as a modem SeArch in motorola site but there is no divers for linus available, i would appreciate any help

mickeygood

---

### Post by K.Mandla on 2008-05-10
Post split from sticky thread.

---

### Post by niteshifter on 2008-05-10
Hi,

> Beacause i live in a rural area , i use my V3 rzor celular as a modem SeArch in motorola site but there is no divers for linus available, i would appreciate any help

No "driver" needed, one treats the V3 like a modem and uses dial-up networking. Here's how I use mine, I connect via USB or Bluetooth:

You need - if you don't already have it - a program from the repositories called wvdial.

I'll give the two scripts in full at the end of this post. You'll copy and paste each into two files. Open a terminal and type:

```
cd /etc
sudo cp wvdial.conf wvdial.conf.backup
gksudo gedit wvdial.conf
```

Delete all the text from the opened file wvdial.conf
Select all the text in the code block below titled WVDIAL CONFIGURATION SCRIPT
Paste that into the editor (gedit).
Save the file and quit the editor.

After saving and quitting you should still be in the terminal. Type
```
cd ~
gedit v3du

```

Select all the text in the code block below titled SHELL SCRIPT.
Paste that into the editor.
Save the file and quit the editor.
Exit the terminal session

Just one more thing to do, make the shell script runnable:
Open your Home Folder via the GUI (click Places -> Home Folder)
Look for the file v3du
Right click on that file
Click on Properties.
Click on Permissions
Click on the box labled Execute.
Click the Close button.

To use:

Open a terminal and type:
```
./v3du
```

Select which way you wish to connect: Bluetooth or USB. It will ask for your system password (since we're using sudo), this can be "fixed", search on these forums about editing sudoers.


---



**WVDIAL CONFIGURATION SCRIPT**
```
[Dialer V3USB]
Baud = 921600
Modem = /dev/ttyACM0
Dial Command = ATDT
Init2 = AT+CGDCONT=1,"IP","isp.cingular"
Phone = *99***1#
Username = ISP@CINGULARGPRS.COM
Password = CINGULAR1
New PPPD = yes
Stupid mode = 1

[Dialer V3BT]
Baud = 230400
Modem = /dev/rfcomm0
Dial Command = ATDT
Init2 = AT+CGDCONT=1,"IP","isp.cingular"
Phone = *99***1#
Username = ISP@CINGULARGPRS.COM
Password = CINGULAR1
New PPPD = yes
Stupid mode = 1

```
Notes about the wvdial configuration: What is shown works with ATT (Cingular). Your wireless provider, if different is going to need different values for Init2, Phone, Username and Password. The easiest way to find out what those values need to be is to borrow a Win machine and use the wireless provider's software to set up a connection. Verify the connection works and get the properties from the DUN (Dial Up Networking) object it created. Alternatively, you can call their customer service and ask - but that's a lot like playing roulette, maybe they know, maybe they don't. They will be utterly clueless the moment Linux gets mentioned.



**SHELL SCRIPT**
```
#!/bin/bash
# v3du - Dialup method chooser script for Mototola V3 phones
# Date: Mar 19, 2007
#  You must:
#   A) Have already configured bluetooth to work with the phone.
#   B) Have wvdial installed and edited wvdial.conf with your required settings
#  This script's purpose is to save a bit of remembering and typing ;)
#
echo Motorola V3 dialup connection by:
OPTIONS="Bluetooth USB Quit"
select opt in $OPTIONS; do
    if [ "$opt" = "Quit" ]; then
        echo Done
        exit
    elif [ "$opt" = "Bluetooth" ]; then
        echo Dialing out with Bluetooth...
        sudo wvdial V3BT
        exit
    elif [ "$opt" = "USB" ]; then
        echo Dialing out with USB...
        sudo wvdial V3USB
        exit
    else
        echo Bad choice!
    fi
done

```

---

