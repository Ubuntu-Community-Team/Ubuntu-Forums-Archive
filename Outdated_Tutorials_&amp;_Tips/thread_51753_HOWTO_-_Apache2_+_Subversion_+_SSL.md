---
title: "HOWTO - Apache2 + Subversion + SSL"
date: 2005-07-25
forum: Outdated Tutorials &amp; Tips
---

### Post by Sniper PT on 2005-07-25
I needed install Apache2 + Subversion and i have searching for info, etc. and now i'm decide to create this tutorial, i hope you like!

Here we go:

INSTALL APACHE2

To install apache2 run that command:
```
sudo apt-get install apache2
```

(if you want also install php and mysql just follow this [Link](http://ubuntuguide.org/#apachehttpserver))

After you will install subversion:
```
sudo apt-get install subversion
```

(in that moment doens't exist the pre-buil binary of the last version (1.2.1), but when it's out you can simple upgrade  ;-) )

To use svn with apache you need install libapache2-svn:
```
sudo apt-get install libapache2-svn
```

Now is better restart apache  ;-) :
```
sudo /etc/init.d/apache2 restart
```

If you don't want SSL go to the last instructions (dav_svn.conf configurations, and users accounts).

Run:
```
a2enmod ssl
``` 

Add "Listen 443" to /etc/apache2/ports.conf:
```
sudo gedit /etc/apache2/ports.conf
```

Run:
```
apache2-ssl-certificate
```

Create a new SSL configuration file:
```
sudo cp /etc/apache2/sites-available/default /etc/apache2/sites-available/myown-ssl
```

Edit myown-ssl file:
```
sudo gedit /etc/apache2/sites-available/myown-ssl
```
Change:
```
NameVirtualHost *
``` to ```
NameVirtualHost *:443
```
and
```
<VirtualHost *>
``` to ```
<VirtualHost *:443>
```

Add before </VirtualHost>:
```
SSLEngine on
SSLCertificateFile /etc/apache2/ssl/apache.pem
SSLProtocol all
SSLCipherSuite HIGH:MEDIUM
```

Run:
```
a2ensite myown-ssl
```

Restart Apache:
```
sudo /etc/init.d/apache2 restart
```

**Last instruction:**

Edit dav_svn configuration file and follow the instructions:
```
sudo gedit /etc/apache2/mods-available/dav_svn.conf
```

Restart apache:
```
 sudo /etc/init.d/apache2 restart
```

Create SVN folder:
```
sudo svnadmin create /srv/svn
sudo chown -R www-data:www-data /srv/svn
sudo chmod -R g+ws /srv/svn
```

Create the users account file:
```
sudo htpasswd2 -c /etc/apache2/dav_svn.passwd svnuser
```
(after asks for a password)

Test SVN:
```
svn import .bashrc https://localhost/svn/testfile -mlogentry
```

That is all!!!


For the SSL instructions i have follow [this](http://wiki.debian.net/?SubversionApache2SSLHowto) Tutorial.
About how using SVN see the official SVN book [here](svnbook.red-bean.com/) or visit the official website ([Link](http://subversion.tigris.org)).

Any error, please report! (and not only in the istructions but also in the english...)

---

### Post by Caboto on 2005-07-25
Nice. Finally got SVN with Apache to work...
But there're some mistakes. The dav_svn.passwd file should be in /etc/apache2/mods-available, right? At least, that's where I put it.
And I needed to run the following commands as root:
a2enmod ssl
apache2-ssl-certificate
a2ensite myown-ssl

---

### Post by Sniper PT on 2005-07-25
I said to create dav_svn.passwd file in /etc/apache2/ folder

```
sudo htpasswd2 -c /etc/apache2/dav_svn.passwd svnuser
```

if you have create that file in that place you can remove and create a new file but in the correct location.

Observation: I think isn't there problem if you create there...
If you look at file /etc/apache2/mods-available/dav_svn.conf, you will see that "AuthUserFile /etc/apache2/dav_svn.passwd", so if you change and want use Authentication you must change that.

---

### Post by Raenac on 2005-08-04
Hey all, great tutorial but I've come across a small problem and not sure where the error lies.  Followed the everything and seemed fine until I tried to test it.
```
svn import .bashrc https://localhost/svn/testfile -mlogentry
``` 
I tried this and come up with this error.
```
svn: PROPFIND request failed on '/svn/testfile'
svn: PROPFIND of '/svn/testfile': 403 Forbidden (https://localhost)
```

I'm guessing its a permissions problem but not sure if its apache or svn.  Any help?

---

### Post by mariuz on 2005-08-10
where is libapache2-svn ?

```
sudo apt-get install libapache2-svn
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package libapache2-svn
```

---

### Post by mariuz on 2005-08-10
[QUOTE=mariuz]where is libapache2-svn ?

```
sudo apt-get install libapache2-svn
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package libapache2-svn
```[/QUOTE]

fixed is in universe ;)
after i added in "/etc/apt/sources.list"
```
deb http://ro.archive.ubuntu.com/ubuntu hoary universe
deb-src http://ro.archive.ubuntu.com/ubuntu hoary universe
```  it worked

---

### Post by stwog on 2005-10-17
Thanks for the great howto. It worked perfectly!

I have a question though... I want to have my svn repository as a Virtual Host with no connection to my other sites. Basically I want the URL [http://svn.mydomain.com](http://svn.mydomain.com) go directly to the svn repository, while [http://mydomain.com](http://mydomain.com) goes to a normal website. My problem is, I have attempted to set it up, but no matter what I do, when I try and go to the normal website it goes the the repository. Could you give me an example of the setup that I need?

Also as a note, I don't want to have the /svn directory at the end of the URL as it seems messy and redundant and I don't want [http://mydomain.com/svn](http://mydomain.com/svn) to reference the repo either. 

Thanks
Simon

---

### Post by REBELinBLUE on 2005-11-29
<edit>oops wrong topic, mod please delete

Cheers

---

### Post by Vegettex on 2006-01-31
<moved>

---

### Post by hdpc on 2006-06-28
> **Sniper PT]I needed install Apache2 + Subversion and i have searching for info, etc. and now i'm decide to create this tutorial, i hope you like!

Here we go:

INSTALL APACHE2

To install apache2 run that command:
```
sudo apt-get install apache2
```

(if you want also install php and mysql just follow this [Link](http://ubuntuguide.org/#apachehttpserver))

After you will install subversion:
```
sudo apt-get install subversion
```

(in that moment doens't exist the pre-buil binary of the last version (1.2.1), but when it's out you can simple upgrade   said:**
> this[/URL] Tutorial.
About how using SVN see the official SVN book [here](svnbook.red-bean.com/) or visit the official website ([Link](http://subversion.tigris.org)).

Any error, please report! (and not only in the istructions but also in the english...)

Hi, I follow your steps above.  But everythime I try to access my repository I am getting the following error:
svn: PROPFIND request failed on '/svn/testfile'
svn: Could not open the requested SVN filesystem

Thanks.

---

### Post by djcronos on 2006-07-07
When I pull up [http://localhost/svn](http://localhost/svn) I can see that it looks like the install went fine, but when I try to run this command:

```

svn import .bashrc https://localhost/svn/testfile -mlogentry

```

I get the following:

```

root@alibaba:~# svn import .bashrc http://localhost/svn/testfile -mlogentry
svn: PROPFIND request failed on '/svn'
svn: PROPFIND of '/svn': 301 Moved Permanently (http://localhost)

```

Any ideas?

---

### Post by t800t8 on 2006-08-01
I'm trying to follow this HOWTO but when I try to add port to ports.conf in Dapper Drake 6.06 by using

```
sudo echo "Listen 443" >> /etc/apache2/ports.conf
```

I've got a "Permission denied" message. How can I fix it? Thanks a lot

---

### Post by t800t8 on 2006-08-01
Fixed it myself: Stop Apache first

---

### Post by Machtyn on 2006-09-13
I am having the same problem as someone earlier posted:
```
~# svn import .bashrc http://localhost/svn/testfile -mlogentry
svn: PROPFIND request failed on '/svn/testfile'
svn: PROPFIND of '/svn/testfile': 403 Forbidden (http://localhost)
# svn import .bashrc https://localhost/svn/testfile -mlogentry
svn: PROPFIND request failed on '/svn/testfile'
svn: PROPFIND of '/svn/testfile': 403 Forbidden (https://localhost)

```

I've even verified I have libapache2-svn installed ```

# apt-get install libapache2-svn
Reading package lists... Done
Building dependency tree... Done
libapache2-svn is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

I've verified my steps in the how-to.
Any other ideas?

---

### Post by Machtyn on 2006-09-13
I found my mistake.  It was in the dav_svn.conf file.
I had enabled the following:
```
  # AuthzSVNAccessFile /etc/apache2/dav_svn.authz

```

As you can see I disabled and restarted apache2.  everything is fine.

---

### Post by airtonix on 2006-10-31
try this...

check out the empty-only-just-now-created-repository : 
```

/var/www/projects:$ svn co svn+ssh://localhost/svn-repos/project-name ./project-name 

```

then create your-test-file-for-inclusion : 
```

/var/www/projects:$ echo 'text for inclusion' >> test.txt 

```

then  add it 
```

/var/www/projects:$ svn import ./ 

```

then import it
```

/var/www/projects:$ svn commit  svn+ssh://localhost/svn-repos/project-name ./project-name 

```

does that work or am i confused too?

---

### Post by jessecollins on 2006-11-02
I just created a script that will automate the installation and setup of Subversion and Apache2.  At this point SSL is not implemented but I am planning on getting to that in the future.

It can be found [here]("http://jessejcollins.com/blog/2006/11/02/script-for-installing-subversion-on-ubuntu").  Hopefully it will be useful for someone. :D

---

### Post by n8v on 2006-12-04
> **Sniper PT said:**
> Any error, please report! (and not only in the istructions but also in the english...)

Thanks for your documentation, Sniper PT!

Here is an update with corrected English and a little fancier markup.  I also added in some other users' notes, and 'a2enmod dav_svn', which I had to do with Edgy Eft; I'm not sure if it was necessary before?

[SIZE="6"][B]HOWTO Install Subversion + Apache2 + SSL 
[/B][/SIZE]

**References:**
[LIST]
[*][SSL Tutorial]("http://wiki.debian.net/?SubversionApache2SSLHowto")
[*][the official SVN book]("http://svnbook.red-bean.com/") 
[*][Subversion website]("http://subversion.tigris.org")
[/LIST]

This example configures a web-accessible Subversion repository on Ubuntu using Basic Authentication and SSL. 

[LIST=1]
[*] Install apache2:
```
sudo apt-get install apache2
``` (if you want php and mysql too, follow [this guide]("http://ubuntuguide.org/#apachehttpserver"))

[*] Install subversion and mod_dav_svn:

First, you need to have the 'universe' Ubuntu software repository enabled, if you haven't already enabled it.  To enable it, uncomment the following lines in "/etc/apt/sources.list"-- the release name in your file should match your Ubuntu release:
```
deb http://ro.archive.ubuntu.com/ubuntu *hoary* universe 
deb-src http://ro.archive.ubuntu.com/ubuntu *hoary* universe
```

Install Subversion:
```
sudo apt-get install subversion
```

You'll also need to install libapache2-svn:
```
sudo apt-get install libapache2-svn
```

If you don't want SSL, skip to the "Edit your Apache configuration for Subversion" step below. (dav_svn.conf configurations, and users accounts).

[*] Enable SSL
[LIST=a]
[*]Enable the SSL Apache module
```
sudo a2enmod ssl
```
[*]Add "Listen 443" to /etc/apache2/ports.conf:
```
sudo gedit /etc/apache2/ports.conf
```
[*]Generate a new self-signed certificate:
```
apache2-ssl-certificate
```
[*]Create a new Apache configuration file for an SSL virtual host named 'myown-ssl':
```
sudo cp /etc/apache2/sites-available/default /etc/apache2/sites-available/myown-ssl
```

[*]Edit your  myown-ssl file:
```
sudo gedit /etc/apache2/sites-available/myown-ssl
```Change:

```
NameVirtualHost *
``` to ```
NameVirtualHost *:443
```and
```
<VirtualHost *>
``` to ```
<VirtualHost *:443>
```
Add before </VirtualHost>:
```
SSLEngine on
SSLCertificateFile /etc/apache2/ssl/apache.pem
SSLProtocol all
SSLCipherSuite HIGH:MEDIUM
```

[*]Activate your new virtual host and restart Apache:
```
sudo a2ensite myown-ssl
sudo /etc/init.d/apache2 restart
```

[/LIST]

[*]Edit your Apache configuration for Subversion

Edit the dav_svn configuration file and follow the instructions in the comments:
```
sudo gedit /etc/apache2/mods-available/dav_svn.conf
```

It will look something like this:

```

# dav_svn.conf - Example Subversion/Apache configuration
#
# For details and further options see the Apache user manual and
# the Subversion book.

# <Location URL> ... </Location>
# URL controls how the repository appears to the outside world.
# In this example clients access the repository as http://hostname/svn/
<Location /svn>

  # Uncomment this to enable the repository,
  DAV svn

  # Set this to the path to your repository
  SVNPath /srv/svn

  # The following allows for basic http authentication.  Basic authentication
  # should not be considered secure for any particularly rigorous definition of
  # secure.

  # to create a passwd file
  # # rm -f /etc/apache2/dav_svn.passwd
  # # htpasswd2 -c /etc/apache2/dav_svn.passwd dwhedon
  # New password:
  # Re-type new password:
  # Adding password for user dwhedon
  # #

  # Uncomment the following 3 lines to enable Basic Authentication
  AuthType Basic
  AuthName "Subversion Repository"
  AuthUserFile /etc/apache2/dav_svn.passwd

  # Uncomment the following line to enable Authz Authentication
  # AuthzSVNAccessFile /etc/apache2/dav_svn.authz

  # The following three lines allow anonymous read, but make
  # committers authenticate themselves.

  <LimitExcept GET PROPFIND OPTIONS REPORT>
    Require valid-user
  </LimitExcept>

</Location>



```

[*]Create a new Subversion repository owned by the user who runs Apache:
```
sudo svnadmin create /srv/svn
sudo chown -R www-data:www-data /srv/svn
sudo chmod -R g+ws /srv/svn
```

[*]Create the htpasswd (user account) file for Basic Authentication:
```
sudo htpasswd2 -c /etc/apache2/dav_svn.passwd svnuser
```
(it will prompt for svnuser's new password)

[*]Enable mod_dav and mod_dav_svn:
```
sudo a2enmod dav
sudo a2enmod dav_svn
/etc/init.d/apache2 force-reload

```

[*]Check that you can browse your empty repository at this URL:
[https://localhost/svn/](https://localhost/svn/)

You should see a page titled "Revision 0: /".


[*]Test adding a file to your repository using the command-line Subversion client:
```
svn import .bashrc https://localhost/svn/testfile -m "change log entry"
```

[/LIST]

---

### Post by wuhaa on 2007-01-09
Hi,

How do I generate multiple ssl cert. for virtual host setup.  For example, i want to make a ssl cert for 2 different virtual hosts  **site1.com**  and   **site2.com**

Thanks,

---

### Post by n8v on 2007-01-15
wuhaa, there might be more specific tips on the SSL tutorial or the Apache docs, but I'll offer one tip off the top of my head-- you need a separate IP address for each SSL virtual host.  You can't do name-based virtual hosting with SSL because the web server needs to send the SSL cert to the client before it can read the hostname from the encrypted HTTP headers.

---

### Post by mike.thorton on 2007-04-23
for generating the ssl certificate under feisty works:```


/usr/sbin/make-ssl-cert /usr/share/ssl-cert/ssleay.cnf /etc/apache2/ssl/apache.pem 
```

if there's no /usr/sbin/make-ssl-cert, just do:

```
sudo apt-get install ssl-cert
```

---

### Post by Ozbboy on 2007-05-01
Hi All,

Having a small problem.

Fiesty is telling me that htpasswd2 cannot be found.

Anyone have any insight into this at all?

---

### Post by jessecollins on 2007-05-15
> **Ozbboy said:**
> Hi All,

Having a small problem.

Fiesty is telling me that htpasswd2 cannot be found.

Anyone have any insight into this at all?


Ozbboy:

Just use htpasswd if you don't have htpasswd2.  The package "apache2-utils" has htpasswd.  I am not sure but it seems like htpasswd2 has been renamed back to htpasswd.

---

### Post by MikeBenza on 2007-05-17
How do I go about creating my own CA for this?

---

### Post by antrophos on 2007-06-10
> apache2-ssl-certificate

> 
Generieren des SSL-Zertifikats
Anmerkung: Zur Generierung des SSl-Zertifikat nutzen wir OpenSSL. Dieses Paket wird alle notwendigen Fragen zur Erstellung eines Zertifikats automatisch stellen.

Debian Tutorial : ~# openssl req $@ -new -x509 -days 365 -nodes -out /etc/apache2/ssl/apache.pem -keyout /etc/apache2/apache.pem (alles eine Zeile)

Anmerkungen:
'-days' gibt die Gültigkeitsdauer an; Sie können auch weit mehr nehmen.
Unter Sarge konnte "apache2-ssl-certificate" genutzt werden. Unter ETCH ist dies nicht mehr möglich.

Quelle: [http://www.tim-bormann.de/?section=145#mod_1290](http://www.tim-bormann.de/?section=145#mod_1290)

sorry for not translating it but the howto owner should update it because there is no instruction quoted in the first box

---

### Post by satimis on 2007-11-27
> **mike.thorton said:**
> for generating the ssl certificate under feisty works:```


/usr/sbin/make-ssl-cert /usr/share/ssl-cert/ssleay.cnf /etc/apache2/ssl/apache.pem 
```

if there's no /usr/sbin/make-ssl-cert, just do:

```
sudo apt-get install ssl-cert
```
Hi mike.thorton,


Ubuntu 7.04 server amd64
Apache2


I followed this Howto and was stuck on;

$  apache2-ssl-certificate
bash: apache2-ssl-certificate: command not found

$ sudo apache2-myown-ssl-certificate
sudo: apache2-myown-ssl-certificate: command not found


Then I did;
$ sudo mkdir /etc/apache2/ssl
$ sudo /usr/sbin/make-ssl-cert /usr/share/ssl-cert/ssleay.cnf /etc/apache2/ssl/apache.pem


$  apache2-ssl-certificate
bash: apache2-ssl-certificate: command not found

$ sudo apache2-myown-ssl-certificate
Password:
sudo: apache2-myown-ssl-certificate: command not found


Still the same.


$ cat /etc/apache2/ssl/apache.pem
No printout

It is an empty file.


$ ls /etc/apache2/sites-available/
default  myown-ssl

$ ls /etc/apache2/sites-enabled/
000-default  myown-ssl

ssl is not there.


Any advice?  TIA


B.R.
satimis

---

### Post by satimis on 2007-11-27
> **n8v said:**
> 


[*]Check that you can browse your empty repository at this URL:
[https://localhost/svn/](https://localhost/svn/)

You should see a page titled "Revision 0: /".


Thanks for your update


I was stuck on;

[https://localhost/svn/](https://localhost/svn/)
Problem on loading page.  Where shall I check?  TIA


satimis

---

### Post by Lapeth on 2007-12-28
Same problem here:

svn: PROPFIND request failed on '/svn/testfile'
svn: Could not open the requested SVN filesystem

Other sources ([here]("http://svn.haxx.se/users/archive-2004-03/0463.shtml") and [here]("http://subversion.tigris.org/servlets/ReadMsg?list=dev&msgNo=94562")) suggest it's a problem with permissions, so I checked the permissions of /srv/svn and which user the apache server was running as. Both of them www-data, so that looks like it should work. But it doesn't.

---

### Post by Tha1 on 2007-12-28
Hey. i decided to take the chance and ask in this thread for my question to not open another thread with the same subject, but with slight differences.

I'm setting up a remote server, in which I use Apache sand tomcat installed on the latest release of Ubuntu. But, when I try to set up SVN for use with WEBDav(_*without SSL*_), using this guide:
[https://help.ubuntu.com/community/Subversion](https://help.ubuntu.com/community/Subversion)
after configuring it all, he doesn't let me in. gives me this error:
Code:

$ svn co [http://193.137.47.17/home/svn/projecto](http://193.137.47.17/home/svn/projecto) projecto --username 5805
[B]svn: PROPFIND request failed on '/home/svn/projecto'
svn: PROPFIND of '/home/svn/projecto': 501 Method PROPFIND is not defined in RFC 2068 and is not supported by the Servlet API  ([http://193.137.47.17](http://193.137.47.17))
[/B]

 When I try to access w/ browser it says me:
**The requested resource (/svn/projecto/) is not available.**

What's wrong in here?

---

### Post by duncs on 2008-03-11
From: /etc/apache2/mods-available/dav_svn.conf

```

# NOTE: for a setup with multiple vhosts, you will want to do this
# configuration in /etc/apache2/sites-available/*, not here.

```

I have multiple vhosts and I was getting the PROPFIND error until i moved the contents of the dav_svn.conf into the site ssl file.

  Duncs

---

### Post by duncs on 2008-03-12
[QUOTE]
$ svn co [http://193.137.47.17/home/svn/projecto](http://193.137.47.17/home/svn/projecto) projecto --username 5805
svn: PROPFIND request failed on '/home/svn/projecto'
svn: PROPFIND of '/home/svn/projecto': 501 Method PROPFIND is not defined in RFC 2068 and is not supported by the Servlet API ([http://193.137.47.17](http://193.137.47.17))
[QUOTE]

And also, don't forget its

svn co http**s**://193.137.47.17/home/svn/projecto projecto --username 5805

  Duncs

---

### Post by beercoder on 2010-04-12
Thanks dude... This is what I call ready-to-eat ;)

Cheers !!!
- BeerCoder

---

### Post by antwort42 on 2011-04-25
Sorry for resurrecting this old post, however since I just setted up a svn repository and intended to secure it via ssl I found this post.

First I followed these instructions:
[http://wiki.ubuntuusers.de/Subversion#Aufsetzen-eines-Repositories](http://wiki.ubuntuusers.de/Subversion#Aufsetzen-eines-Repositories)
[http://wiki.ubuntuusers.de/Apache/SSL?highlight=Pw%20Tbaustell%20Zapach%20Zhttps](http://wiki.ubuntuusers.de/Apache/SSL?highlight=Pw%20Tbaustell%20Zapach%20Zhttps)

Which is pretty much the same as suggested in this post, but afterwards subversion was accessible via http and https. Since I use multiple sites on my server and I wanted to restrict subversion to usage with https but allow http for anything else I additionally used a rewrite rule to get this accomplished:
[http://wiki.ubuntuusers.de/Apache/modrewrite](http://wiki.ubuntuusers.de/Apache/modrewrite)

I guess this could be done by restricting apaches VirtualHost to different directories also, but this would have ment more effort for me... Since I am not a security expert hopefully both solutions are equal...

---

### Post by NixNinja on 2011-08-12
After installing subversion apache no longer displays web pages now all i get is a file listing how do I fix this?

---

