---
title: "Installing Atmail Open Webmail Client on Ubuntu"
date: 2008-12-23
forum: Outdated Tutorials &amp; Tips
---

### Post by lukeyduke on 2008-12-23
I have come across many forums of people who are trying to install squirrelmail/horde, using OWA,  fed up with gmail/hotmail, or are looking for a decent free webmail client that they can easily install on their own servers.
This is exactly how I felt, until I discovered the Atmail Open Webmail client.
It can be easily configured as a Webmail alternative to Gmail, and any other mail that supports IMAP or POP.
It has a fantastic looking, simple interface which can be customised to your own needs/wants and best of all, it is entirely free!

Here is a guide on installing the software to your Ubuntu system, the original document is located [here]("http://atmail.com/kb/2008/installing-atmail-open-webmail-client-on-ubuntu/").

[FONT="Arial Black"]
How to Install Atmail Open Webmail Client on Ubuntu[/FONT]

Open your favourite web-browser and navigate to [www.atmail.org/download.php]("http://www.atmail.org/download.php") to get a copy of the Atmail Open tarball.
Run the following command to become root:

```
# sudo /bin/bash
```

If apache, PHP and MySQL are not already installed, run the following commands:
```

# apt-get update
# apt-get install apache2 php5 libapache2-mod-php5 mysql-server mysql-client php5-mysql libapache2-mod-auth-mysql
```

Move the Atmail Open tarball into your webservers root public directory.

```
# mv ./atmailopen.tgz /var/www/
```

Extract the tarball with the following commands:

```
# cd /var/www
# tar xzvf ./atmailopen.tgz
```

Now navigate to [http://localhost/atmailopen](http://localhost/atmailopen) in your favourite web browser and there should be a page there, most likely displaying an Installation Error, do not panic!  This is absolutely normal.

Go back to the command line and run the following command,

```
# chown -R www-data /var/www/atmailopen
```
(where www-data is the user running apache)
You will also need to turn magic quotes off in your php.ini file (most likely at /etc/php5/apache2/php.ini)
Find the line that says:
```

magic_quotes_gpc = On
```

and change it to:
```

magic_quotes_gpc = Off
```

Save and quit the text editor that you used, then restart apache with the following command:
```
# /etc/init.d/apache2 restart
```
Now navigate to [http://localhost/atmailopen](http://localhost/atmailopen) in your favourite web browser and make sure there is no errors in the @mail Pre-installation check, then click “continue” at the bottom of the page.
Select the default language that you wish to use in your Atmail installation, read the license agreement, and if you agree to them, select “Yes I agree to the above license”, and click “Continue >>”.

You have now reached Step 2 of the Atmail client installation.
Enter your MySQL details in the form presented to you:
SQL Server Type = MySQL
SQL Server Hostname or IP = localhost
SQL Username = root
SQL Password = whatever you set it to when you installed MySQL
Database Name = atmail
Create Database = Checked

Create Database Tables = Checked
[IMG]http://atmail.com/kb/attach/SQL_setup.gif[/IMG]
Select “Continue >>”

You have now reached Step 3 of the Atmail client installation.
Enter your SMTP and Admin Email information:
You can use an external SMTP server or install an SMTP server on localhost, as long as the value in this field is changed to suit.
[IMG]http://atmail.com/kb/attach/SMTP_config.gif[/IMG]
In this case, I have installed exim on the host machine, this can be achieved with the following command:

```
# sudo apt-get install exim4
```

Click “Continue >>”

The next page will ask you about migrating from another webmail system, if you wish to migrate from Horde, Roundcube, or Squirrelmail, Atmail supports this, and you should select the appropriate webmail system to migrate from, however I will not be migrating from any previous webmail system in this tutorial, so I will just select “Continue >>” which concludes the Atmail client installation.
<p>The final page of your installation should look like the following:
[IMG]http://atmail.com/kb/attach/install_complete.gif[/IMG]
Congratulations, you have successfully installed your new webmail client, select “Login to Webmail” to start using it!

---

### Post by saanjac on 2009-06-06
hi 

i installed atmail open webmail to my qmail server and working fine 
with sending and receivig mails in locally.I have doubt in 
 atmail open database table Log_RecvMail.What's the use of this table. Is it for logging received mails.But in my server Log_RecvMail is not updating and Log_SendMail is updating every mail sending..any idea........


Thanks 
jacob

---

