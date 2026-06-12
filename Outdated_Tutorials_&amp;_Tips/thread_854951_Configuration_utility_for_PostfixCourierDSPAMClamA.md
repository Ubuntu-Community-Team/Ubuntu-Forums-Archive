---
title: "Configuration utility for Postfix/Courier/DSPAM/ClamAV with MySQL on Ubuntu Hardy"
date: 2008-07-10
forum: Outdated Tutorials &amp; Tips
---

### Post by undesigned on 2008-07-10
[SIZE="5"]If you'd like to know what this does before installing...[/SIZE]

This package simply modifies configuration files with some [shell scripts]("http://code.google.com/p/vmailconfig/source/browse/trunk/DEBIAN/postinst") - existing configuration directories will be backed up.  This package has been tested on Ubuntu Hardy 32bit and 64bit.


[SIZE="5"]Installation[/SIZE]

[SIZE="3"]**NB: This package is for a fresh installation of required packages. **
It is recommended that you purge and reinstall all apps that will be reconfigured:[/SIZE]

```
sudo apt-get remove postfix postfix-mysql \
dspam libdspam7 libdspam7-drv-mysql clamav \
clamav-base clamav-daemon --purge
```

[SIZE="3"]Install the required packages with apt-get:[/SIZE]

```
sudo apt-get install \
mailx postfix postfix-mysql postfix-pcre \
python-policyd-spf postfix-policyd-spf-python python-spf \
libsasl2-2 libsasl2-modules libsasl2-modules-sql \
dspam libdspam7 libdspam7-drv-mysql \
clamav clamav-base clamav-daemon clamav-freshclam libclamav6 \
mysql-server-5.0 mysql-client-5.0 \
courier-authdaemon courier-base courier-maildrop \
courier-pop courier-ssl courier-pop-ssl \
courier-authlib courier-authlib-userdb courier-authlib-mysql
```

[SIZE="3"]Download and install the package (you will be prompted with a few configuration options - when prompted to configure the DSPAM databases, you can select "NO"):[/SIZE]

[SIZE="3"]For Ubuntu Jaunty:[/SIZE]
```

wget http://vmailconfig.googlecode.com/files/vmailconfig_0.1.5.deb
sudo dpkg -i vmailconfig_0.1.5.deb

```

[SIZE="3"]For Ubuntu Hardy:[/SIZE]
```

wget http://vmailconfig.googlecode.com/files/vmailconfig_0.1.4.deb
sudo dpkg -i vmailconfig_0.1.4.deb

```

If the MySQL DB import fails the file will still exist @ /tmp/vmail.sql


[SIZE="5"]Adding domains and users to your MySQL database[/SIZE]

Every mail domain must be configured on the system:

```
insert into domains (domain) values ('testhost');
```

[SIZE="5"]Adding a new mail user:[/SIZE]

```
insert into mailusers (email, password, maildir) 
values ('user@testhost', 'password', 'testhost/user@testhost/');

insert into dspam_preferences (uid, preference, value)
values (LAST_INSERT_ID(), 'localStore', LAST_INSERT_ID());
```


[SIZE="5"]Testing[/SIZE]

To test mail (requires you to add 'testhost' to domains and 'user@testhost' to mailusers):

```
echo "this is a test" | mail "user@testhost"
```

To see the test mailbox (requires mutt, sudo apt-get install mutt):

```
sudo mutt -f /home/vmail/testhost/user@testhost/
```

You can also see what postfix/dspam has to say with:

```
sudo tail -f /var/log/mail.log /var/log/mail.err
```


[SIZE="5"]DSPAM Retraining[/SIZE]

Spam email can be forwarded to user@**spam.**testhost for retraining with the dspam_retrain script.


[SIZE="5"]That's that![/SIZE]

Hope somebody finds this useful :)

---

