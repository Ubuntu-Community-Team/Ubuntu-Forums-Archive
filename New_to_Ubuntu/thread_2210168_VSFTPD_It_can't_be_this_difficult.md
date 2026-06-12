---
title: "VSFTPD It can't be this difficult?"
date: 2014-03-09
forum: New to Ubuntu
---

### Post by chris187 on 2014-03-09
I would seriously appreciate any help anyone has. I have tried to set up ftp so many different times, I'm almost ready to just say forget the whole thing. Help!
I followed the tutorial found at [http://ubuntuforums.org/showthread.php?t=518293](http://ubuntuforums.org/showthread.php?t=518293)
Port forwarding is enabled on port 80, 21, 22, 12000, and 12100, but the firewall on the router is at Max Protection.
ufw is disabled
I tried to use the ftp protpcal in a browser** [ftp://username:password@domain.com/](ftp://username:password@domain.com/)**, and **[ftp://username:password:21@domain.com/](ftp://username:password:21@domain.com/)**
I installed Filezilla client, not the server, host: showmemn.com, and [www.showmemn.com](www.showmemn.com), and 10.0.0.25, and localhost.
Finally even tried using DMZ on the router.

This is a copy of Vsftpd.conf.:

```
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
#write_enable=YES
#
# Default umask for local users is 077. You may wish to change this to 022,
# if your users expect that (022 is used by most other ftpd's)
#local_umask=022
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
# You may change the default value for timing out an idle session.
#idle_session_timeout=600
#
# You may change the default value for timing out a data connection.
#data_connection_timeout=120
#
# It is recommended that you define on your system a unique user which the
# ftp server can use as a totally isolated and unprivileged user.
#nopriv_user=ftpsecure
#
# Enable this and the server will recognise asynchronous ABOR requests. Not
# recommended for security (the code is non-trivial). Not enabling it,
# however, may confuse older FTP clients.
#async_abor_enable=YES
#
# By default the server will pretend to allow ASCII mode but in fact ignore
# the request. Turn on the below options to have the server actually do ASCII
# mangling on files when in ASCII mode.
# Beware that on some FTP servers, ASCII support allows a denial of service
# attack (DoS) via the command "SIZE /big/file" in ASCII mode. vsftpd
# predicted this attack and has always been safe, reporting the size of the
# raw file.
# ASCII mangling is a horrible feature of the protocol.
#ascii_upload_enable=YES
#ascii_download_enable=YES
#
# You may fully customise the login banner string:
#ftpd_banner=Welcome to blah FTP service.
#
# You may specify a file of disallowed anonymous e-mail addresses. Apparently
# useful for combatting certain DoS attacks.
#deny_email_enable=YES
# (default follows)
#banned_email_file=/etc/vsftpd.banned_emails
#
# You may restrict local users to their home directories.  See the FAQ for
# the possible risks in this before using chroot_local_user or
# chroot_list_enable below.
#chroot_local_user=YES
#
# You may specify an explicit list of local users to chroot() to their home
# directory. If chroot_local_user is YES, then this list becomes a list of
# users to NOT chroot().
# (Warning! chroot'ing can be very dangerous. If using chroot, make sure that
# the user does not have write access to the top level directory within the
# chroot)
#chroot_local_user=YES
#chroot_list_enable=YES
# (default follows)
#chroot_list_file=/etc/vsftpd.chroot_list
#
# You may activate the "-R" option to the builtin ls. This is disabled by
# default to avoid remote users being able to cause excessive I/O on large
# sites. However, some broken FTP clients such as "ncftp" and "mirror" assume
# the presence of the "-R" option, so there is a strong case for enabling it.
#ls_recurse_enable=YES
#
# Customization
#
# Some of vsftpd's settings don't fit the filesystem layout by
# default.
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
#
# No anonymous login
anonymous_enable=NO
# Let local users login
# If you connect from the internet with local users, you should enable TLS/SSL/FTPS
local_enable=YES
#
# Write permissions
write_enable=Y
#
# 3. Just some users are "free":
chroot_local_user=YES
chroot_list_enable=YES
# Create the file /etc/vsftpd.chroot_list with a list of the "free" users.
#
userlist_deny=NO
userlist_enable=YES
userlist_file=/etc/vsftpd.allowed_users
#
pasv_min_port=12000
pasv_max_port=12100
#
```

BTW, I restrated VSFTPD after reconfiguring.

---

### Post by Lars Noodén on 2014-03-09
In most situations, [you should not use FTP](http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp).  If you are looking to upload files to a host then you might as well do that securely and SFTP does that.  SFTP support is built into the package openssh-server, so install that and you are good to go with no additional configuration needed.  FileZilla and other tools like Nautilus and the other file managers have built-in SFTP capabilities.  To use SFTP you only need port 22 (SSH) open or forwarded .

---

### Post by chris187 on 2014-03-09
I want to install Bitnami LAMP satck, will there be a conflict, I know SSH uses port 443.

---

### Post by Lars Noodén on 2014-03-09
[SSH uses port 22](http://www.iana.org/assignments/service-names-port-numbers/service-names-port-numbers.xhtml) and SFTP operates over SSH.  It is HTTPS that uses port 443.  If file transfer is your goal, then SFTP is probably what you want.  I don't know why FTP persists.  Anonymous FTP, yes, but not user name and login. 

I don't know about Bitnami but a normal lamp stack is normally managed via SSH / SFTP.  You can install LAMP on Ubuntu like this:

```

sudo apt-get update
sudo apt-get install lamp-server^

```

Or you can install the pieces a la carte.  Perl and Python are a normal part of the distro and so do not need to be added.

---

### Post by chris187 on 2014-03-09
I performed sudo apt-get update
Then I performed sudo apt-get install tasksel
Then I selected OPENssh, LAMPserver
Do I also need to install additional libraries or connectors to have LAMP server and OPEnssh server work properly?
Or should I just redeploy the same command sudo apt-get install lamp-server^ after everything I have already done?
Conflict or no?
Thanks for your help.

---

### Post by Lars Noodén on 2014-03-09
openssh-server gives you SFTP.  So you should be able to connect via Nautilus or FileZilla now.  In Nautilus go to the location bar(press ctrl-L if necessary) and enter the URL for your server.

```

sftp://username@sftp.server.com

```

Unless you set it up otherwise, Apache2 on Ubuntu gives you one virtual host by default.  The configuration file for that default vhost is /etc/apache2/sites-enabled/000-default.conf and the default location for the web pages will be /var/www  You can get at that directory with SFTP but you'll need to set up write access for yourself.  If you are the only user on that machine then it is enough to take ownership of the directory for your account:

```

sudo chown -R chris187 /var/www

```

If you are working with one or more other people then you'll have to use groups instead.  It's easy, too.

---

### Post by chris187 on 2014-03-10
I tried 
sftp://username@sftp.server.com
but error reads "Server not found" (Firefox)
Localhost is good, and FQDN works, with and without www.

---

### Post by Lars Noodén on 2014-03-10
> **chris187 said:**
> 
but error reads "Server not found" (Firefox)

Firefox won't handle SFTP.  Try it in your file manager's location bar.  Nautilus is the default for Ubuntu and there is an icon for it over in the dock.  If the location bar is not visible, press ctrl-L to bring it up.

---

