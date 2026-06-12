---
title: "Installing Atmail mail-server under Ubuntu - Webmail, SMTP/POP3/IMAP, Calendar + More"
date: 2009-01-05
forum: Outdated Tutorials &amp; Tips
---

### Post by lukeyduke on 2009-01-05
The following is a guide to setting up Atmail server in an Ubuntu environment.

First you must become root and install dependencies:
```

# sudo /bin/bash
(enter sudo password and press enter)
# apt-get update
# apt-get install apache2 php5 libapache2-mod-php5 php5-cli mysql-server mysql-client
```

Download Atmail php5 server from the atmail website [http://www.atmail.com](http://www.atmail.com) (this will need to be purchased, but an evaluation version can be acquired from here).

Move the downloaded file into /usr/local/
```
# mv atmailphp5server.tgz /usr/local/
```

Navigate to /usr/local/
```
# cd /usr/local

```
Extract the tarball
```
# tar xzvf atmailphp5server.tgz
```

As the tarball extracts, a list of files being extracted will scroll down the screen, wait until you are presented with a prompt, and run the following commands.
```

# cd atmail
# chmod +x ./server-install.php
# php ./server-install.php
```

[IMG]http://atmail.com/kb/attach/Picture%202.png[/IMG]

From here, the install is very simple, following the prompts and using default values should lead to a successful installation.
Note that the value inside [ ] square brackets is the default value, you don’t need to re-enter it, you can just press enter/return.

When asked if you wish to install all missing dependencies automatically, choose YES.

If you get a message as below:

[IMG]http://atmail.com/kb/attach/Picture%205.png[/IMG]

Simply re-run the server installation with the following command:
```

# php ./server-install.php
```

You will need to enter the mysql root password when prompted.

When asked:
“Select the database to use or enter the name of a new database to create:”, Enter the name “atmail” as your new database and press enter.

You should get a message that says “Atmail tables successfully created. MySQL setup complete!”

Enable the Groupware Module if you wish, this will enable calendar, address-book and task data sharing.

When Asked:
“Specify the binary location of your Webserver:”
Use default value (/usr/sbin/apache2)

Allow the atmail install to configure your httpd.conf file automatically and restart httpd.

You are now at the point in your Atmail installation where you need to specify a domain name for which you wish to host email accounts. You can also specify multiple domains separated by a comma, for this demonstration I will be setting up domain.com

I entered domain.com as the domain and [email]admin@domain.com[/email] as the admin email address, but you should enter your domain and real administrator email address in your install.

Use default values to allow atmail to automatically setup SMTP.

Use default values to allow atmail to automatically setup POP3/IMAP server.
(This will take about 5 minutes, please be patient)

Ensure that you get a message saying:

"@Mail POP3/IMAP Server Installation: Successful
Compile & installation complete"

Use default settings to allow Atmail to install Spamassassin from source.
Ensure you get a message saying:
SpamAssassin Installation: SUCCESSFUL

Now use default settings to install the anti-virus engine from source,
Ensure you get a message saying:
@Mail AV Installation: SUCCESSFUL
Compile & Installation complete

Allow the Atmail installation script to run diagnostic tests, this is a good way to troubleshoot if your Atmail installation did not go as planned.

Should you have any other trouble with this installation, contact Atmail support.

Your Atmail installation should now be complete.

[IMG]http://atmail.com/kb/attach/Picture%206.png[/IMG]

Navigate to [http://localhost/mail](http://localhost/mail) to view your new @mail messaging platform login screen,

[IMG]http://atmail.com/kb/attach/Picture%207.png[/IMG]

and [http://localhost/mail/webadmin](http://localhost/mail/webadmin) to view and modify your configuration settings.

[IMG]http://atmail.com/kb/attach/Picture%208.png[/IMG]

NOTE: You should read the red text and secure webadmin immediately with a password.
[B]
Congratulations on your new, fully functional Atmail server![/B]

---

