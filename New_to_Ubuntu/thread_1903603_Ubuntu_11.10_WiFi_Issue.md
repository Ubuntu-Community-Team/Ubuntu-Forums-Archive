---
title: "Ubuntu 11.10 WiFi Issue"
date: 2012-01-02
forum: New to Ubuntu
---

### Post by gerard90 on 2012-01-02
:)
Hello, 
I recently received a Lenovo B575 for Christmas
I decided to Install Ubuntu 11.10 alongside windows 7
Everything is running perfectly (I think)
The only problem is my internet connection
When running on windows 7, my internet works fine.
When using ubuntu, I cannot even turn on the Wifi option
When i do, it immediately switches back off
From reading some of the forums here, I understand that some wireless cards or adapters (Mine being a "Ralink  RT3090 wifi adapter")are not always compatible with Linux.
I cannot even look for any wireless connection.
This is my first time using a Linux operating system. 
I never played with my command prompt with windows.
If someone can please help me using baby steps, i would really appreciate it.

Thanks! =:)

---

### Post by chipbuster on 2012-01-02
EDIT: Try [COLOR=Black]sadaruwan12's solution first (in the post below me)[/COLOR]. CTRL+ALT+T to open the terminal, CTRL+ALT+C to copy from terminal, CTRL+ALT+V to paste into terminal.






huh, well that's funny. A lot of threads say that the 3090 has been supported since 10.10 (over a year ago at this point).

Let's start by seeing if your computer can actually see the wireless card. Open up a terminal with CTRL+ALT+T and paste the following commands. You can copy from the terminal with CTRL+SHIFT+C and paste things into terminal with CTRL+SHIFT+V.

> 
lspci -nn

lsmod | grep -e rt2 -e rt3
The vertical bar (pipe) is SHIFT + \, backslash is right above the enter key.

Put those two commands into the terminal and post the results here. If the second command doesn't return anything, post the results of "lsmod" and note that the first command didn't return anything.

Oh, and welcome to the forums and the wonderful world of Linux :)

---

### Post by sadaruwan12 on 2012-01-02
First of all welcome to the forum and to Ubuntu.

I had the same issue with my laenovo B560 but got it solved. The problem is a wifi driver from acer which disables the wifi switching from the system. So here is my solution.


There are two way of doing this first do the temporary one.

```
sudo rmmod -f acer-wmi
sudo rfkill unblock all
rfkill list all
```

After the above steps your wireless starts to work then make it permanent by doing this,

```
gksudo gedit /etc/modprobe.d/blacklist.conf
```

Add the below line to the end of the file

```
blacklist acer-wmi
```

Proof read this before saving and if everything is ok then save it.

Now do this

```
gksudo gedit /etc/rc.local
```

Just before the word end put this

```
rfkill unblock all
```

Proof read it twice if ok save it.

Now reboot your system, once you log in your wireless should work with out any problem 'cos this solved my issue.

Hope this helps and cheers.

---

### Post by gerard90 on 2012-01-03
> **sadaruwan12 said:**
> First of all welcome to the forum and to Ubuntu.

I had the same issue with my laenovo B560 but got it solved. The problem is a wifi driver from acer which disables the wifi switching from the system. So here is my solution.


There are two way of doing this first do the temporary one.

```
sudo rmmod -f acer-wmi
sudo rfkill unblock all
rfkill list all
```After the above steps your wireless starts to work then make it permanent by doing this,

```
gksudo gedit /etc/modprobe.d/blacklist.conf
```Add the below line to the end of the file

```
blacklist acer-wmi
```Proof read this before saving and if everything is ok then save it.

Now do this

```
gksudo gedit /etc/rc.local
```Just before the word end put this

```
rfkill unblock all
```Proof read it twice if ok save it.

Now reboot your system, once you log in your wireless should work with out any problem 'cos this solved my issue.

Hope this helps and cheers.


OMG, Thanks! I am connected =D
just one more question, on your last step, you say to put 
[FONT=monospace]rfkill unblock all "just before the word end"

where do I put "rfkill unblock all" on this 

"#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.


exit 0 "

Thanks! =D
[/FONT]

---

### Post by sadaruwan12 on 2012-01-03
> **gerard90 said:**
> OMG, Thanks! I am connected =D
just one more question, on your last step, you say to put 
[FONT=monospace]rfkill unblock all "just before the word end"

where do I put "rfkill unblock all" on this 

"#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.


exit 0 "

Thanks! =D
[/FONT]

Sorry for that put it just before the "exit 0" and save it.

After that reboot thats it.

After this your "fn+WiFi key" will work as well. Also mark the thread if your issue get solved.

---

### Post by gerard90 on 2012-01-03
> **sadaruwan12 said:**
> Sorry for that put it just before the "exit 0" and save it.

After that reboot thats it.

After this your "fn+WiFi key" will work as well. Also mark the thread if your issue get solved.

OMG!
Thank you so much guys!
It works Wonderfully now =D
:):):):)

---

