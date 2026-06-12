---
title: "HOWTO: custom gproftpd"
date: 2008-07-12
forum: Outdated Tutorials &amp; Tips
---

### Post by pavel989 on 2008-07-12
If you have installed lampp, then you probably know that the proftpd configuration is very confusing for people that haven't dealt with proftpd.

Gproftpd is a user interface to the config file, making it easy to set it up. However, installing it from synaptic makes u get a new proftpd install.

So after fiddling with it for a while, I figured out how to make a custom gproftpd install:

**[SIZE="3"]step 1[/SIZE]**: have this installed: (you can remove it after, its just so that the compiler thinks that you have gtk2.0 installed. if anyone finds a work around, plz post)

```
sudo apt-get install libgtk2.0-dev
```

**[SIZE="3"]step 2[/SIZE]**: get the gproftpd package and unpack it:
```
wget http://mange.dynalias.org/linux/gadmin-proftpd/gadmin-proftpd-0.2.8.tar.gz && tar -zxvf gadmin-proftpd-0.2.8.tar.gz
```

you can remove the tar.gz if you like
```
rm gadmin-proftpd-0.2.8.tar.gz
```

**[SIZE="3"]step 3[/SIZE]**: cd there and open autoinstall:
```
cd gadmin-proftpd-0.2.8 && gedit ./Autoinstall
```

**[SIZE="3"]step 4[/SIZE]**:  we have to change the directories for it use the lampp proftp.conf:

original:
```
### Default paths and settings ###
# export PROFTPD_CONF="/etc/proftpd.conf"
# export SECURE_LOG="/var/log/secure"
# export XFER_LOG="/var/log/xferlog"
# export PROC_PATH="/proc"
# export PROFTPD_BINARY="proftpd"
# export FTPWHO_BINARY="ftpwho"
# export SERVER_USER="nobody"
# export SERVER_GROUP="nobody"
# export WELCOME_MESSAGE="welcome.msg"
# export HTML_STATISTICS="/var/www/html/ftp.htm"
# export MIN_PASS_LEN=6

### Debian commands for starting the server at boot ###
# export SYSINIT_START_CMD="update-rc.d -f proftpd defaults"
# export SYSINIT_STOP_CMD="update-rc.d -f proftpd remove"

### RH/Fedora commands for starting the server at boot ###
### This is the defaults for the rpm specfile ###
export SYSINIT_START_CMD="chkconfig proftpd on"
export SYSINIT_STOP_CMD="chkconfig proftpd off"

./configure --prefix=/usr --sysconfdir=/etc \
--localstatedir=/var --sbindir=/usr/sbin &&
make &&
make install
```
 
(assuming you did a normal lampp install) new: 
```
### Default paths and settings ###
  export PROFTPD_CONF="/opt/lampp/etc/proftpd.conf"
# export SECURE_LOG="/var/log/secure"
# export XFER_LOG="/var/log/xferlog"
# export PROC_PATH="/proc"
  export PROFTPD_BINARY="/opt/lampp/sbin/proftpd"
  export FTPWHO_BINARY="/opt/lampp/bin/ftpwho"
# export SERVER_USER="nobody"
# export SERVER_GROUP="nobody"
# export WELCOME_MESSAGE="welcome.msg"
# export HTML_STATISTICS="/var/www/html/ftp.htm"
# export MIN_PASS_LEN=6

#############################################
############# feel free to change any of the  
############# above to your liking as long as 
############# you know what you're doing
#############################################

### Debian commands for starting the server at boot ###
# export SYSINIT_START_CMD="update-rc.d -f proftpd defaults"
# export SYSINIT_STOP_CMD="update-rc.d -f proftpd remove"

### RH/Fedora commands for starting the server at boot ###
### This is the defaults for the rpm specfile ###
export SYSINIT_START_CMD="chkconfig proftpd on"
export SYSINIT_STOP_CMD="chkconfig proftpd off"

./configure --prefix=/usr --sysconfdir=/etc \
--localstatedir=/var --sbindir=/usr/sbin &&
make &&
make install
```

[SIZE="3"]Save it![/SIZE]

**[SIZE="3"]step 5[/SIZE]**: last step
```
sudo ./Autoinstall
```

[SIZE="3"]NOTE:[/SIZE]
the binary isn't ```
gproftpd
``` its

```
gadmin-proftpd
```
and it has to be run as root

recommended steps:

This installs a binary into Applications-Internet-GADMIN-PROFTPD.
but it needs to run  as root. So, right click on applications, click edit menus, click internet, right click on gadmin-proftpd, click properties, and in the command box it'll say:
```
gadmin-proftpd
```
but we want it to be:
```
gksudo gadmin-proftpd
```
Save all that.

and that should be it!

---

