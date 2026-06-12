---
title: "Vsftpd installed cant view ftp files"
date: 2012-12-16
forum: New to Ubuntu
---

### Post by Yurirev01 on 2012-12-16
Alrighty i am 100% new to linux ive used guides to install the ftp but i think i may have done something wrong because i cannot access the ftp directory.  I want to be able to upload files to the ftp through filezilla. The only thing this server is being used for is a web based rcon program for a gameserver and nothing else.  Any help would be greatly appreciated.  Any other information needed please ask.

Thank you

---

### Post by Merrattic on 2012-12-16
Which guide did you follow and please report back with the contents of your vsftpd.conf file which you can find in /etc on the server.

Mine looks like this:

> #custom vsftpd.conf
# Run standalone?  vsftpd can run either from an inetd or as a standalone
# daemon started from an initscript.
listen=YES
#
# Allow anonymous FTP? (Beware - allowed by default if you comment this out).
anonymous_enable=NO
#
# Uncomment this to allow local users to log in.
local_enable=YES
#
# Uncomment this to enable any form of FTP write command.
write_enable=YES
#
# Default umask for local users is 077. You may wish to change this to 022,
# if your users expect that (022 is used by most other ftpd's)
local_umask=022
#
# Activate directory messages - messages given to remote users when they
# go into a certain directory.
dirmessage_enable=YES
#
# If enabled, vsftpd will display directory listings with the time
# in  your  local  time  zone.  The default is to display GMT. The
# times returned by the MDTM FTP command are also affected by this
# option.
use_localtime=YES
#
# Activate logging of uploads/downloads.
xferlog_enable=YES
#
# Make sure PORT transfer connections originate from port 20 (ftp-data).
connect_from_port_20=YES
#
# You may fully customise the login banner string:
ftpd_banner=Welcome to Server FTP service.
#
# This option should be the name of a directory which is empty.  Also, the
# directory should not be writable by the ftp user. This directory is used
# as a secure chroot() jail at times vsftpd does not require filesystem
# access.
secure_chroot_dir=/var/run/vsftpd/empty
#
# This string is the name of the PAM service vsftpd will use.
pam_service_name=vsftpd
#
# This option specifies the location of the RSA certificate to use for SSL
# encrypted connections.
rsa_cert_file=/etc/ssl/private/vsftpd.pem

Also let's check it is running:
```
pidof vsftpd
``` should return a number (or use a program like Task Manager or htop ans search for vsftpd

---

### Post by Yurirev01 on 2012-12-16
i used [https://help.ubuntu.com/10.04/serverguide/ftp-server.html](https://help.ubuntu.com/10.04/serverguide/ftp-server.html)
And how do i go about editing a file?  i guess i need to know some basic commands to start off.

---

### Post by Merrattic on 2012-12-16
You are on Ubuntu so you can use gedit, but you will need root permissions.

Open a terminal and type:
```
gksudo gedit /etc/vsftpd.conf
``` (if gksudo borks, try gksu or just plain sudo)

If you want to stay in a terminal you can use nano:
```
sudo nano /etc/vsftpd.conf
```

You can 
```
man nano
``` to find out how it works

---

### Post by Yurirev01 on 2012-12-16
# Example config file /etc/vsftpd.conf
#
# The default compiled in settings are fairly paranoid. This sample file
# loosens things up a bit, to make the ftp daemon more usable.
# Please see vsftpd.conf.5 for all compiled in defaults.
#
# READ THIS: This example file is NOT an exhaustive list of vsftpd options.
# Please read the vsftpd.conf.5 manual page to get a full idea of vsftpd's
# capabilities.
#
#
# Run standalone?  vsftpd can run either from an inetd or as a standalone
# daemon started from an initscript.
listen=YES
#
# Run standalone with IPv6?
# Like the listen parameter, except vsftpd will listen on an IPv6 socket
# instead of an IPv4 one. This parameter and the listen parameter are mutually
# exclusive.
#listen_ipv6=YES
#
# Allow anonymous FTP? (Beware - allowed by default if you comment this out).
anonymous_enable=NO
#
# Uncomment this to allow local users to log in.
local_enable=YES
#
# Uncomment this to enable any form of FTP write command.
write_enable=YES
#
# Default umask for local users is 077. You may wish to change this to 022,
# if your users expect that (022 is used by most other ftpd's)
local_umask=022
#
# Uncomment this to allow the anonymous FTP user to upload files. This only
# has an effect if the above global write enable is activated. Also, you will
# obviously need to create a directory writable by the FTP user.
#anon_upload_enable=YES
#
# Uncomment this if you want the anonymous FTP user to be able to create
# new directories.
#anon_mkdir_write_enable=YES
#
# Activate directory messages - messages given to remote users when they
# go into a certain directory.
dirmessage_enable=YES
#
# If enabled, vsftpd will display directory listings with the time
# in  your  local  time  zone.  The default is to display GMT. The
# times returned by the MDTM FTP command are also affected by this
# option.
use_localtime=YES
#
# Activate logging of uploads/downloads.
xferlog_enable=YES
#
# Make sure PORT transfer connections originate from port 20 (ftp-data).
connect_from_port_20=YES
#
# If you want, you can arrange for uploaded anonymous files to be owned by
# a different user. Note! Using "root" for uploaded files is not
# recommended!
#chown_uploads=YES
#chown_username=whoever
#
# You may override where the log file goes if you like. The default is shown
# below.
#xferlog_file=/var/log/vsftpd.log
#
# If you want, you can have your log file in standard ftpd xferlog format.
# Note that the default log file location is /var/log/xferlog in this case.
#xferlog_std_format=YES
#

---

### Post by Yurirev01 on 2012-12-16
ok so i can login local with my 192 ip the router assigns but can not create new directories.  is there a teamspeak or ventrilo i could talk with you on?

---

### Post by Merrattic on 2012-12-17
So, are you logging in using a user created on the server? If so, which directory and location is default? If it is outside of /home/user then you will need to provide permissions to that user in order to create directories.

For example, in my setup (the ftp is only really for me to access some files on the server), my main user is bob, with password tail.

Using filezilla I set up a connection with hostname or IP address, normal login and connect with the above login details. By default I am taken to /home/bob. I can create directories, add and delete files etc. I can't see any other parts of the system (this is how it should be).

What is different for you?

---

