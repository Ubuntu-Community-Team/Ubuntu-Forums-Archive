---
title: "CHanging the IP address of a Linux device from a webpage using CGI scripts"
date: 2012-01-20
forum: New to Ubuntu
---

### Post by 213Wayne on 2012-01-20
Hi.

I have a device that has a Linux OS on-board. The device supports web interface. I want to be able to configure the device from the web interface (e.g. change the IP address of the device) using CGI scripts.

Please assist.

---

### Post by 213Wayne on 2012-01-23
Hi.
 
Can any one give me CGI code to change the IP address of a server?

---

### Post by 213Wayne on 2012-01-24
Hi.
 
Is it possible to change the IP address using the command:** ifconfig eth0 inet "IP" netmask "netmask"** in a CGI bash script?

---

### Post by denver on 2012-01-24
Short answer: Yes


Changing the IP address however is an administrative task, and requires root access. That means that your web server has to be run as root, or that you must use sudo (or other privilege escalating apps) in order to be able to use ifconfig, or the ip command.

CAUTION:
Running a web server as root is never a good idea! Use sudo in your CGI if you must, and be sure to restrict it only to the ifconfig command. Also, be sure you secure access to the CGI script, as it is a huge potential security risk.

My personal recommendation is that you use ssh instead for any administrative task.

---

### Post by 213Wayne on 2012-01-24
Thank you for your response.
Can you give me an example of sudo (or ssh) commands as well as the ifconfig command and how you would intergrate these into bash CGI?

---

### Post by denver on 2012-01-24
I would not recommend CGI scripts for changing IP's. This operation may cut you off from your device and should be used with caution. If you must change the IP, I sugest you do it manually via ssh.

For more information on SSH, you can start here:

[https://help.ubuntu.com/community/SSH](https://help.ubuntu.com/community/SSH)

For information on sudo and how to configure it, please check:

[https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)

---

### Post by 213Wayne on 2012-01-24
This is the device that I'm attempting to change the IP address using a CGI bash script.
 
I ultimately want to design a web page (front-end) that will allow user's to configure the IP address and so on.
 
[http://www.moxa.com/doc/man/Moxa_C_Programmable_RTU_Controllers_User's_Manual.pdf](http://www.moxa.com/doc/man/Moxa_C_Programmable_RTU_Controllers_User's_Manual.pdf)

---

### Post by denver on 2012-01-24
Ahh! I see!

So its not supposed to be a multi-user system. According to the manual apache seems to run under the "nobody" user by default. That user is unprivileged.

In order for your CGI to work, you will need to run the web server as root, or use sudo, if available. If sudo is not available, you will have to find a way to run apache using the root user.

The manual mentions that you can cross compile applications for your device. It might be worth compiling sudo. Unfortunatly i dont have access to such a device, I cannot give you any advice regarding how you could do that.

if you do have sudo, add this to /etc/sudoers:

```

Cmnd_Alias PRIV_CMD = /sbin/ifconfig
nobody        ALL= NOPASSWD: PRIV_CMD

```

after that, you may use:

```

/usr/bin/sudo /sbin/ifconfig ethX $IP netmask $NETMASK

```

to run ifconfig as root, using a CGI.

---

### Post by 213Wayne on 2012-01-25
This device does have sudo, I cannot find the "sudoers" file in etc. What else can it be named as/ where else could it be stored?
 
I cannot find the "sudo" file in the "usr/bin" directory, I can only find "su" in the "bin" directory. Can this be the "sudo"?

---

### Post by 213Wayne on 2012-01-25
Will this code work?
 
#!/bin/bash
# Example for setting an IP Address and Subnet mask and restarting the network interface
 
$FILENAME="/etc/network/interfaces"
# Write new setting for eth0
readwriteconfig -w $FILENAME IPADDR=192.168.127.253
readwriteconfig -w $FILENAME NETMASK=255.255.255.0
readwriteconfig -w $FILENAME GATEWAY=192.168.127.50
readwriteconfig -w $FILENAME ONBOOT=yes
# Restart the interface with new values
ifdown eth0
ifup eth0

---

### Post by denver on 2012-01-25
If the command

```
sudo 
```

Does not give you "command not found" message, then you do have sudo. If sudo is present on the system, the default path for the sudoers file is:

```
/etc/sudoers
```

If it does not exist, try to create it:

```
vi /etc/sudoers
```

make sure its owned by root:root and permissions set to 440.

```
chown root:root /etc/sudoers && chmod 440 /etc/sudoers
```

Some machines may have a non standard path for this file, and it may already be created. Try to locate it via find or locate. If you have strace installed, you could try:

```
strace sudo 2>&1|grep sudoers
```

To see where sudo is looking for the sudoers file. The "su" binary is for switching users, or running commands as a different user, but it will ask you for that user's password. If you have sudo, use that.

---

### Post by 213Wayne on 2012-01-25
Will this code work?
 
#!/bin/bash
# Example for setting an IP Address and Subnet mask and restarting the network interface

$FILENAME="/etc/network/interfaces"
# Write new setting for eth0
readwriteconfig -w $FILENAME IPADDR=192.168.127.253
readwriteconfig -w $FILENAME NETMASK=255.255.255.0
readwriteconfig -w $FILENAME GATEWAY=192.168.127.50
readwriteconfig -w $FILENAME ONBOOT=yes
# Restart the interface with new values
ifdown eth0
ifup eth0

---

### Post by 213Wayne on 2012-01-27
I cannot find the sudoers file.
 
I'm going to create one (vi sudoers).
What should I put in the file?

---

