---
title: "HOWTO: IPplan and LDAP Authentication"
date: 2011-02-25
forum: Outdated Tutorials &amp; Tips
---

### Post by shaferwr on 2011-02-25
[FONT=Calibri][SIZE=3]One of the things that I can't stand in the IT field is failure to share information with other IT engineers. There are a plethora of strong IT engineers out there that spend countless hours working on projects and the information that they learn can be shared, but isn't. Sometimes an engineer will take the time to type up a snippet of a tutorial and assume that everyone reading it has the same knowledge as he does. This is where the problems come in. If tutorials are written with the assumption that the reader has NO experience, then you can truly help another engineer instead of frustrating him. [/SIZE][/FONT]
 
[FONT=Calibri][SIZE=3]I&#8217;m just as guilty about not sharing information. So I decided to take a few minutes and write up a tutorial on setting up LDAP (Lightweight Directory Access Protocol) within the IPplan website.[/SIZE][/FONT]
 
[FONT=Calibri][SIZE=3]We all know that single sign-on is a must in enterprise networking due to multiple reasons. If an employee leaves the company, removing just one account instead of spending the time to search all resources and tools for inactive or expired accounts is the preferred method. With LDAP, you can keep one account active and use it for multiple resources and tools. [/SIZE][/FONT]
 
[FONT=Calibri][SIZE=3]IPplan is no different. By utilizing LDAP, you can authenticate your IPplan users and administrators with your Active Directory Domain Controller and not have to worry about unauthorized access once an employee leaves the company.[/SIZE][/FONT]
 
[FONT=Calibri][SIZE=3]The following tutorial is how I set up authentication on my server. There are different ways of doing it, but the quick and dirty way of getting it working is right here. The only assumption here is that you have already installed and have a working distribution of IPplan from [/SIZE][/FONT][[FONT=Calibri][SIZE=3]http://iptrack.sourceforge.net/[/SIZE][/FONT]]("http://iptrack.sourceforge.net/")
 
[FONT=Calibri][SIZE=3]**Software Versions:**[/SIZE][/FONT]

[LIST]
[*][FONT=Calibri][SIZE=3]Ubuntu &#8211; 10.04[/SIZE][/FONT]
[*][FONT=Calibri][SIZE=3]IPplan - v4.92a[/SIZE][/FONT]
[*][FONT=Calibri][SIZE=3]Windows Server 2008[/SIZE][/FONT]
[/LIST][FONT=Calibri][SIZE=3]**Required items:**[/SIZE][/FONT]

[LIST]
[*][FONT=Calibri][SIZE=3]A functioning IPplan Installation[/SIZE][/FONT]
[*][FONT=Calibri][SIZE=3]A functioning Active Directory Domain Controller.[/SIZE][/FONT]
[*][FONT=Calibri][SIZE=3]Access to the internet from your IPplan Server for module and package installations.[/SIZE][/FONT]
[/LIST][FONT=Calibri][SIZE=3]Files that you will have to either create or alter (*Don't create or alter them yet! Follow the instructions below!*) If you are so inclined, back up the originals by using this command: [/SIZE][/FONT]
 
```
 
sudo cp [filename.extension] [filename.extension.bak]

```

[LIST]
[*][FONT=Calibri][SIZE=3]Create .htaccess file in */var/www/ipplan/user* directory[/SIZE][/FONT]
[*][FONT=Calibri][SIZE=3]Alter your config.php file in */var/www/ipplan* directory[/SIZE][/FONT]
[*][FONT=Calibri][SIZE=3]Alter your httpd.conf file in */etc/apache2* directory[/SIZE][/FONT]
[*][FONT=Calibri][SIZE=3]Alter your apache2.conf file in */etc/apache2* directory[/SIZE][/FONT]
[/LIST][FONT=Calibri][SIZE=3]**INFO:** The following instructions are all done in either a terminal window or an SSH session to your IPplan server.[/SIZE][/FONT]
 
[FONT=Calibri][SIZE=3]Install the LDAP modules if they are not already installed:[/SIZE][/FONT]
 
```
 
sudo a2enmod authnz_ldap

```
 
[FONT=Calibri][SIZE=3]If they are not installed already, Ubuntu will pull them in from the internet. If they are, you will see that both modules are already enabled.[/SIZE][/FONT]
 
[FONT=Calibri][SIZE=3]Next, you have to alter your */etc/apache2/apache2.conf* file:[/SIZE][/FONT]
 
```
 
cd /etc/apache2
sudo nano apache2.conf 

```
 
[FONT=Calibri][SIZE=3]Scroll down to &#8220;AccessFileName .htaccess&#8221; and make sure that it is uncommented. This tells Apache to look into specific directories for authentication requirements instead of globally adding them to the httpd.conf file. This is the &#8220;quick and dirty&#8221; way of doing it. It taxes your webserver a bit more than it would if it was in the httpd.conf file, but if the server is internal, and all you are doing is hosting the IPplan website, it shouldn&#8217;t be that big of a deal.[/SIZE][/FONT]
 
[FONT=Calibri][SIZE=3]Then scroll down to &#8220;LogLevel&#8221; and change it to &#8220;debug&#8221;. This helps in troubleshooting any LDAP issues once everything is somewhat configured. When all is said and done, you can change his back to &#8220;info&#8221; if you want.[/SIZE][/FONT]
 
[FONT=Calibri][SIZE=3]Save the file &#8211; (^x to save, hit &#8220;y&#8221; to confirm, enter to overwrite the old one.)[/SIZE][/FONT]
 
[FONT=Calibri][SIZE=3]Now edit your httpd.conf file:[/SIZE][/FONT]
```
 
sudo nano httpd.conf

```
[FONT=Calibri][SIZE=3]Add this to your httpd.conf file:[/SIZE][/FONT]
```
 
<Directory /var/www/ipplan/user>
AllowOverride All
</Directory>

```
[FONT=Calibri][SIZE=3]Save the file &#8211; (^x to save, hit &#8220;y&#8221; to confirm, enter to overwrite the old one.)[/SIZE][/FONT]
 
[FONT=Calibri][SIZE=3]This tells Apache to use the .htaccess file that we are about to create for authentication of your IPplan users.[/SIZE][/FONT]
 
[FONT=Calibri][SIZE=3]Now go to your */var/www/ipplan* directory and modify your config.php file:[/SIZE][/FONT]
```
 
cd /var/www/ipplan
sudo nano config.php

```
[FONT=Calibri][SIZE=3]Scroll down to the bottom where it says &#8220;Start of Authentication&#8221;.[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]Change this line:[/SIZE][/FONT]
```
 
define("AUTH_VAR", PHP_AUTH_USER);

```
[FONT=Calibri][SIZE=3]to this:[/SIZE][/FONT]
```
 
define("AUTH_VAR", 'REMOTE_USER');

```
[FONT=Calibri][SIZE=3]Also, you need to change this line:[/SIZE][/FONT]
```
 
define("AUTH_INTERNAL", TRUE);

```
[FONT=Calibri][SIZE=3]to this:[/SIZE][/FONT]
```
 
define("AUTH_INTERNAL", FALSE);

```
[FONT=Calibri][SIZE=3]Save the file &#8211; (^x to save, hit &#8220;y&#8221; to confirm, enter to overwrite the old one.)[/SIZE][/FONT]
 
[FONT=Calibri][SIZE=3]Now go to your */var/www/ipplan/user* directory:[/SIZE][/FONT]
```
 
cd /var/www/ipplan/user

```
[FONT=Calibri][SIZE=3]Create your .htaccess file:[/SIZE][/FONT]
```
 
sudo nano .htaccess

```
[FONT=Times New Roman][SIZE=3]Add these lines to your newly created .htaccess file:[/SIZE][/FONT]
```
 
Order deny,allow
Deny from All
AuthType basic
AuthName "IPplan LDAP Authentication"
AuthBasicProvider ldap
AuthzLDAPAuthoritative off
require valid-user
AuthLDAPBindDN [EMAIL="ipplan@myADdomain.com"]ipplan@myADdomain.com[/EMAIL]
AuthLDAPBindPassword P@ssw0rd
AuthLDAPURL [ldap://xxx.xxx.xxx.xxx:389/ou=unique,ou=unique,dc=myADdomain,dc=com?samaccountname](ldap://xxx.xxx.xxx.xxx:389/ou=unique,ou=unique,dc=myADdomain,dc=com?samaccountname)
Satisfy any

```
[FONT=Calibri][SIZE=3]Ok, this is where I had the most trouble. First off, I had to create a user on the Windows server called &#8220;ipplan&#8221;. Give him a password of whatever you want. In this case, we will use &#8220;P@ssw0rd&#8221;. This is how the IPplan website will bind to the LDAP server.[/SIZE][/FONT]
 
[FONT=Calibri][SIZE=3]Secondly, the &#8220;AuthLDAPURL&#8221; is VERY important and will be unique to your AD structure. This tells IPplan a few things. First, it tells IPplan where your AD server is and what port to talk on (ldap://xxx.xxx.xxx.xxx:389). After that, it details out the structure of your AD objects. [COLOR=red]**THIS WILL BE UNIQUE TO YOUR DOMAIN CONTROLLER!!!**[/COLOR] Finally, &#8220;?samaccountname&#8221; is the query information necessary to search for the username you are trying to authenticate. **[COLOR=red]IMPORTANT:[/COLOR]** If you use what I&#8217;ve put here, you have a 99% chance of it not working. This example is from my AD server, so you'll have to use the query that is unique to your AD server![/SIZE][/FONT]
 
 
[FONT=Calibri][SIZE=3]While you are testing, use the &#8220;tail&#8221; command to watch your error log. Open your web browser and go to your IPplan main page. Log into your admin section and delete any users that you have already created for internal authentication. Make sure you recreate the users with the **[COLOR=red]EXACT[/COLOR]** username that is in Active Directory. [/SIZE][/FONT]
 
[FONT=Calibri][SIZE=3]This is where the error log comes in. [/SIZE][/FONT]
```
 
tail &#8211;f /var/log/apache2/error.log

```
[FONT=Calibri][SIZE=3]Now go to any other menu item and try to log in. If you&#8217;ve correctly identified your AD structure in the query line of your .htaccess file, you will be able to log in. If it is not working, watch your error.log file and try to decipher the problems. If you&#8217;ve followed this tutorial correctly, then 99% of all troubleshooting will have to be done with the query.[/SIZE][/FONT]
 
[FONT=Calibri][SIZE=3]Please let me know if you have any suggestions or additions to this tutorial. Also, please do not assume that I know your experience level, so take a few minutes out of your day and explain your issues or suggestions thoroughly![/SIZE][/FONT]
[FONT=Calibri][SIZE=3]Thanks![/SIZE][/FONT]
 
[FONT=Calibri][SIZE=3]-Will[/SIZE][/FONT]

---

