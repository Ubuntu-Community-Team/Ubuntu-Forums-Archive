---
title: "HowTo:  Intel 537EP Chipset MODEM driver install on Ubuntu Dapper."
date: 2006-07-06
forum: Outdated Tutorials &amp; Tips
---

### Post by chuckman78 on 2006-07-06
**[SIZE="4"]HowTo:  Intel 537EP Chipset MODEM driver install on Ubuntu Dapper.[/SIZE]**

First of all: I am a new Linux, and subsequently Ubuntu, user. The following information is a blend of steps from various sources with the purpose of installing the driver for a dial up MODEM with Intel 537EP Chipset. 

The principal sources of info for this little guide are:

[<http://www.ubuntu-es.org/comment/reply/5503/40456>]("http://www.ubuntu-es.org/comment/reply/5503/40456")

<[https://help.ubuntu.com/community/DialupModemHowto]("https://help.ubuntu.com/community/DialupModemHowto")>

I have got also lots of help from the guys at <[http://linmodems.org/]("http://linmodems.org/")> and their discussion list, specially Marv and Jaques. Last, but not least, the people at <[http://www.ubuntuforums.org/]("http://www.ubuntuforums.org/")> , with special acknowledgement to zxee, azz and Matchless.

Now, let’s get to business.

0.- I did this on a fresh new install, but I think It could work even after some kernel updates. More on this later.

You will need to use a computer with internet connection to get these files:

<[http://downloadfinder.intel.com/scripts-df-external/Detail_Desc.aspx?agr=Y&ProductID=1230&DwnldID=9284&strOSs=39&OSFullName=Linux*&lang=eng]("http://downloadfinder.intel.com/scripts-df-external/Detail_Desc.aspx?agr=Y&ProductID=1230&DwnldID=9284&strOSs=39&OSFullName=Linux*&lang=eng")>

This is the driver from Intel. Don’t worry if it says “suse” in its name.

Also, let’s get these:
<[http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-3.4/gcc-3.4-base_3.4.4-6ubuntu8_i386.deb]("http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-3.4/gcc-3.4-base_3.4.4-6ubuntu8_i386.deb")>
<[http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-3.4/cpp-3.4_3.4.4-6ubuntu8_i386.deb]("http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-3.4/cpp-3.4_3.4.4-6ubuntu8_i386.deb")> 
<[http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-3.4/gcc-3.4_3.4.4-6ubuntu8_i386.deb]("http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-3.4/gcc-3.4_3.4.4-6ubuntu8_i386.deb")> 

These are the files for the C compiler needed to create the driver.

1.- We need to install some things first, the linux-headers and the build-essential packages. They are in the Dapper installation CD, so pop it in and type at the terminal:


```
sudo apt-get install linux-headers-386 build-essential
```

(I am assuming that you are using the same architecture as I am, x86. If not, change 386 with yours).

It is a good idea to put all the downloaded files in the previous step in your Desktop, just to keep then handy.

On the terminal lets cd to Desktop and execute the following three commands (The order is important):

```
sudo dpkg -i gcc-3.4-base_3.4.4-6ubuntu8_i386.deb
sudo dpkg -i cpp-3.4_3.4.4-6ubuntu8_i386.deb
sudo dpkg -i gcc-3.4_3.4.4-6ubuntu8_i386.deb
```

This installs the gcc packages, needed for the compilation of the driver. 

Now lets unpack the MODEM driver:

```
tar xzf Intel-537EP-2.70.95.0-suse9.3.tgz
```

This will create a folder called Intel-537. We will need to rename it with the result of doing:

```
uname –r
```

In my case I got “***2.6.15-23-386***” so I renamed the directory **Intel-537** to…. yes, you got it ***2.6.15-23-386***. This step will be addressed and explained later.  For simplicity in this tutorial I will call this directory “**modem_source**”. 

2.- Let’s cd to modem_source. Now, we will need root privileges so:

```
sudo su
```

And, now let’s compile:


```
make clean
make 537
make install
```

At this point, hopefully, we got the driver compiled.

3.- To make things easier lets open nautilus (I assume you are using Gnome) from the terminal still having root privileges:

```
nautilus
```

Now, from nautilus copy the **modem_source** folder to **/etc/init.d.** 

4.- At the **/etc/init.d** directory you will also find the **537_boot **shell script. Double click on it to open it in your text editor. We will replace the content of the script with the following:

[COLOR="Blue"]#!/bin/sh
kernel=`uname -r`
serial="/etc/init.d/$kernel/Intel537.ko"
device="537"
registry="hamregistry"
group="root"
mode="664"
if [ -a /etc/SuSE-release ]; then
{
group="dialout"
}
fi
case "$1" in
start | b)
if ! ( modprobe -f $serial 1>/dev/null 2>/dev/null ); then
{
if ! ( insmod -f $serial 1>/dev/null 2>/dev/null ); then
{
echo error loading $serial
rmmod $serial
exit 1
}
fi
}
fi
major=`cat /proc/devices | awk "\\$2==\"Intel537\" {print \\$1}"`
echo major="($major)"
rm -f /dev/$device
mknod /dev/$device c $major 1 2> /dev/null 1> /dev/null
chgrp $group /dev/$device
chmod $mode /dev/$device
ln -sf /dev/Intel5370 /dev/modem 1> /dev/null 2> /dev/null
if ! ps -C $registry 1> /dev/null 2> /dev/null; then
{
if ! ( /usr/sbin/$registry 2> /dev/null 1> /dev/null & ); then
{
echo "Modem registry ($registry) could not start."
echo "Please see international users secion in readme.txt for more info."
}
fi
}
fi
exit 0
;;
stop)
rmmod 537 1> /dev/null 2> /dev/null
rmmod 537_core 1> /dev/null 2> /dev/null
rmmod $serial 1> /dev/null 2> /dev/null
;;
restart | reload)
/bin/bash "$0" stop
/bin/bash "$0" start
exit 0
;;
status)
if lsmod | grep "$serial " >/dev/null; then
{
lsmod | grep "$serial " > /dev/null
}
else
{
echo "$serial NOT loaded"
}
fi
if ps -C $registry 1> /dev/null 2> /dev/null; then
{
ps -C $registry
}
else
{
echo "$registry NOT running"
}
fi
exit 0
;;
*)
echo unknown $serial script parameter
exit 1
esac
exit 0[/COLOR]
################# End of script ##################

This script is executed on boot, looks for the directory with the same name as the kernel version (that’s why we renamed the directory on step 1), installs the module for the modem and creates the link to /dev/modem from /dev/537. If you update your kernel you should repeat steps 0 to 3 (it worked for me when I updated to 2.6.15-25-386).

5.- Configure your favorite dial up utility (I use gnome-ppp). In my case I had to uncheck the “Abort if busy”, “Abort if no dial tone” and “Carrier check” check boxes.

6.- Restart or type:

```
sudo bash /etc/init.d/537_boot start
```


And that's pretty much it.  

Right now I've been having trouble to use gnome-ppp when I restart the machine so I have to type in terminal before using the modem (but just once per session), this:

```
sudo /etc/init.d/537_boot restart
```

Enjoy!

Regards,

Carlos Marcano.

P.S: Please, I would like to read your suggestions and improvement to this little guide. We all most try to make this as painless as possible for all the dialup users out there using winmodems. I still have a faboulus USrobotics external modem lying on the top of my desk with out use with Ubuntu, thats my next goal. Meanwhile, I have my 537 to help me! :D

---

