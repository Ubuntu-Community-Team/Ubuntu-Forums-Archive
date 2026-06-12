---
title: "WebDAV with encrypted authentication"
date: 2011-04-01
forum: Outdated Tutorials &amp; Tips
---

### Post by brucehohl on 2011-04-01
[FONT="Courier New"]
The following is how I set-up WebDAV on 10.04 LTS. It would be nice to see the Nautilus WebDAV support polished up a bit.

--------------------------------------------------------------------------
WebDAV with encrypted authentication:
--------------------------------------------------------------------------
1-  Install apache
    # aptitude install apache2 (apache 2.2)

    Enable webdav modules:
    # a2enmod dav
    # a2enmod dav_fs
    # /etc/init.d/apache2 restart

    Enable auth_digest module
    # a2enmod auth_digest
    # /etc/init.d/apache2 restart

--------------------------------------------------------------------------
2-  Add following davdir1 config to: /etc/apache2/httpd.conf

    <Directory "/var/www/davdir1">
    Dav On
    Order Allow,Deny
    Allow from all
    AuthType Digest
    AuthName webdav
    AuthUserFile  /etc/apache2/auth/htdigest
    AuthGroupFile /etc/apache2/auth/htgroup
    Require group davdir1
    </Directory>

    # /etc/init.d/apache2 restart

--------------------------------------------------------------------------
3-  Create directory:
    # mkdir /var/www/davdir1
    # chown www-data:www-data /var/www/davdir1

--------------------------------------------------------------------------
4-  Apache password file:
    To create:         # touch /etc/apache2/auth/htdigest
    To add a user:     # htdigest /etc/apache2/auth/htdigest realm user
    To delete a user:  # open file and delete related line

    Note: realm = "webdav" to match AuthName in httpd.conf.

--------------------------------------------------------------------------
5-  Apache group file:
    To create:         # touch /etc/apache2/auth/htgroup
    To add a user:     # nano  /etc/apache2/auth/htgroup
                         add  "davdir1: user1"

--------------------------------------------------------------------------
6-  Site access:
    Each defined <Directory> in /etc/apache2/httpd.conf is limited
    to valid users matching the specified realm and group.
    +++
    Users are added to a realm when created with the htdigest command.
    Users are added to one or more groups at /etc/apache2/auth/htgroup.

--------------------------------------------------------------------------
7- Connection methods: 

   (1) Cadaver CLI (like FTP):
       $ sudo aptitude install cadaver
       $ cadaver [http://localhost:80/davdir1/](http://localhost:80/davdir1/)


   (2) Gnome Nautilus:
       dav://user1@localhost/davdir1

   (a) 'Remember password until you logout' fails.
       'Remember forever' fails.
       'Forget password immediately' succeeds.

   (b) File rename succeeds but results in error message and file
       list must be updated manually via F5.
       Launchpad bug 512496.

   (c) Unable to save or open OpenOffice files from WebDAV mount.
       Work around: copy file to local computer, edit, copy back.

   (d) No apparent way to lock files.


   (3) Firefox extension: Web Folder 1.2
       Available from: [http://webfolder.mozdev.org/index.html](http://webfolder.mozdev.org/index.html)

       To use:
       File > Open Web Folder
       Enter [http://localhost/davdir1](http://localhost/davdir1)

       Directory contents will be listed and
       a 'Webfolder' menu will be added.

       Webfolder menu includes: 
       Change server, New directory, Delete file
       Download, Upload
       Lock, Unlock
       Cut file, Copy file, Paste file[/FONT]

---

