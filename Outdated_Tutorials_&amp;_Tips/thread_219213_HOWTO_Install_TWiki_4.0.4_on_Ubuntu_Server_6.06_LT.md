---
title: "HOWTO: Install TWiki 4.0.4 on Ubuntu Server 6.06 LTS"
date: 2006-07-19
forum: Outdated Tutorials &amp; Tips
---

### Post by tjb4u on 2006-07-19
**TWiki.org Links**
[LIST]
[*][Installation Guide]("http://http://twiki.org/cgi-bin/view/TWiki04/TWikiInstallationGuide")
[*][System Requirements]("http://twiki.org/cgi-bin/view/TWiki04/TWikiSystemRequirements") 
[/LIST]

**Instructions**

Complete a Server Install of Ubuntu 6.06 LTS

Enable Universe Repository and update packages:
[LIST]
[*]Open the file for editing:
```
sudo nano /etc/apt/sources.list
```

[*]Remove the hashes from the following lines and save the file
```
# deb [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) dapper universe
# deb-src [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) dapper universe
```

[*]Update packages:
```
sudo apt-get update
sudo apt-get upgrade
```
[/LIST]

Install required packages:
(Some of these packages may already be installed with the default Ubuntu installation but running the commands as shown will not hurt.)
```

sudo apt-get install apache2 perl
sudo apt-get install cron grep  
sudo apt-get install rcs

```

Install required perl modules (modules not included with the perl install above):
```

sudo apt-get install libcgi-session-perl
sudo apt-get install libdigest-sha1-perl
sudo apt-get install libhtml-parser-perl
sudo apt-get install patch

```

Unpack TWiki .tgz file:
```
sudo mkdir -p /home/httpd/twiki/
cd /home/httpd/twiki/
sudo tar -xvzf <full path to TWiki-4.0.4.tgz>
sudo chown -R www-data /home/httpd/twiki
sudo chgrp -R www-data /home/httpd/twiki
```

Prepare the example .conf file included with TWiki
```
sudo cp /home/httpd/twiki/twiki_httpd_conf.txt /home/httpd/twiki/twiki_httpd.conf

```

Append this line to the end of /etc/apache2/httpd.conf
include "/home/httpd/twiki/twiki_httpd.conf"
```
sudo nano /etc/apache2/httpd.conf
```

Restart the Apache server:
```
sudo /etc/init.d/apache2 restart
```

Run the configuration script from a web-browser on another networked computer. The ip-address of the server can be determined using 'sudo ifconfig':
```
http://<ipaddress>/twiki/bin/configure
```

Start TWiki-ing:
```
http://<ipaddress>/twiki/bin/view
```

---

### Post by Robbrad on 2006-07-31
sudo apt-get install php4

Had to do the above to get it working :p

---

### Post by tjb4u on 2006-07-31
> **Robbrad said:**
> sudo apt-get install php4

Had to do the above to get it working :p

That's interesting. As far as I know TWiki does not use PHP at all, however I did use a LAMP server install for the example above so PHP was installed on my system by default. I still maintain that you should not need it though.

BTW, I found an article in Linux Journal that describes a TWiki Install. I have not read it in full but I think it might be useful for those struggling to get TWiki up and going as I was: [LIST]
[*][Using Wikis and Blogs to Ease Administration]("http://www.linuxjournal.com/article/8779")
[*][Linux Journal Contents #144, April 2006]("http://www.linuxjournal.com/issue/144")
[/LIST]
Thank you **twas** for the lead  [(See Post)]("http://ubuntuforums.org/showthread.php?p=1250656#post1250656").

---

### Post by dwieringa on 2006-08-18
> **Robbrad said:**
> sudo apt-get install php4

Had to do the above to get it working :p

I had to run this command as well.  Before I did, I got an error when I tried to restart apache (sudo /etc/init.d/apache2 restart).  I was going to paste the error here, but I lost it from the clipboard.  As I recall, it complained about an error in /etc/apache2/httpd.conf -- which only had the include.  The included file mentioned PHP so I tried this suggestion -- the problem went away and I'm up and running.

---

### Post by bandoba on 2006-09-13
You don't really need PHP installed to run TWiki. But as mentioned before, if you see error while starting Apache server, just disable PHP from TWiki's configuration as memtioned in the error message and you are good to go.

Thanks for the simple guide!

---

### Post by dan_kent on 2006-10-05
i followed this guide, as well as several other, and I've got apache running nicely and twiki installed. However when I go to [http://ip/twiki](http://ip/twiki) and click on configure I just get a load of text - looks like a perl script. I've checked that the script is able to read and execute.
Any ideas on what i'm doing wrong?

Dan

---

### Post by tjb4u on 2006-10-06
> **dan_kent said:**
> i followed this guide, as well as several other, and I've got apache running nicely and twiki installed. However when I go to [http://ip/twiki](http://ip/twiki) and click on configure I just get a load of text - looks like a perl script. I've checked that the script is able to read and execute.
Any ideas on what i'm doing wrong?

Dan
First: 
If configured how I described above you won't be able to "click" on the configure script as the directory is not visible by exploring directories with an Internet browser.

Second:
The configure script should be at the following URL
**http://<ipaddress>/twiki/bin/configure**
Not
**http://<ipaddress>/twiki/configure**

I realize that may not be very helpful but maybe it will point you to a clue in the difference in our configurations.

---

### Post by steelec5 on 2006-10-24
I also needed to install sendmail.  Found this out when I tried to register myself as a user.

```
sudo apt-get install sendmail
```

---

### Post by maphew on 2006-11-14
there is a .deb package maintained at [http://members.iinet.net.au/~spos/](http://members.iinet.net.au/~spos/) which is generally only a few days behind the current twiki.org release, if that.

---

### Post by ryharv on 2006-12-07
Hi all,

I could use some help.  I've followed all the directions listed above, installed PHP4 via apt, and restarted apache.  

When I restart apache, I get this:

> ryan@rybuntu:~$ sudo /etc/init.d/apache2 restart
Password:
 * Forcing reload of apache 2.0 web server...
[Wed Dec 06 23:12:30 2006] [warn] The Alias directive in /etc/apache2/conf.d/twiki.conf at line 2 will probably never match because it overlaps an earlier Alias.
[Wed Dec 06 23:12:30 2006] [warn] The Alias directive in /etc/apache2/conf.d/twiki.conf at line 3 will probably never match because it overlaps an earlier Alias.
apache2: Could not determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Wed Dec 06 23:12:30 2006] [warn] The Alias directive in /etc/apache2/conf.d/twiki.conf at line 2 will probably never match because it overlaps an earlier Alias.
[Wed Dec 06 23:12:30 2006] [warn] The Alias directive in /etc/apache2/conf.d/twiki.conf at line 3 will probably never match because it overlaps an earlier Alias.
apache2: Could not determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
   ...done.


My twiki.conf file looks like this:

> # Added for twiki
Alias /twiki/pub /var/www/twiki/pub
Alias /twiki/data /var/lib/twiki/data
Redirect /twiki/index.html [http://localhost//cgi-bin/twiki/view](http://localhost//cgi-bin/twiki/view)
#Redirect /twiki/ [http://localhost//cgi-bin/twiki/view](http://localhost//cgi-bin/twiki/view)

# make sure this is even needed, and ref the doc section needing it 
<Directory /usr/lib/cgi-bin/twiki/> 
    Options +ExecCGI
    SetHandler cgi-script
    AllowOverride all
    Allow from all
</Directory>

# End twiki Configuration Block

And when I go to

[http://myip/twiki/bin/configure](http://myip/twiki/bin/configure)

all I get is a blank page (no error).

Any suggestions?  I appreciate the help.

---

### Post by jrftx on 2006-12-07
I was getting a screwy "oops" page with %20s in the URL when running Configure.  I had to edit
/home/httpd/twiki/twiki_httpd.conf and add the IP address of the machine from which I was running the TWiki configuration page.  About 1/2 way down is a section about limiting access.  Just add the IP address of your browser machine (with a comma) after the 192 address listed.  Since I'm running LTS server with no GUI I'm not accessing from 127.0.0.1

BTW, the PHP issue is fixed without installing PHP by commenting out the line php_admin_flag engine off
in twiki_httpd.conf

---

### Post by ryharv on 2006-12-19
Thanks, all, for your help.  In the end, I found that the easiest way to install twiki was through apt-get.  After doing it that way, it worked, almost magically. 

Now, though, my problem is that I've got it all configured and displaying properly, but in order to do anything I must first register myself.

But I can't register myself as a user.  I go to TwikiRegistration and fill in all the appropriate fields, but then the server thinks about it for a while and returns a 500 error.  

My apache log is telling me this:

[Mon Dec 18 23:05:40 2006] [error] [client 24.21.201.6] Premature end of script headers: register, referer: [http://myip/twiki/bin/view/TWiki/TWikiRegistration](http://myip/twiki/bin/view/TWiki/TWikiRegistration)

I'm sure I'm making a simple rookie mistake.  Any thoughts?  I greatly appreciate your help.  I would ask this over at the twiki forum, but it has blacklisted me because it thinks I'm a spammer (when I first posted this, I had my actual DynDNS hostname rather than "myip" above).

---++ Environment

%EDITTABLE{format="|label,1|text,70|" changerows="off"}%
|  TWiki version: | Codev.TWikiRelease04x00x05   |
|  TWiki plugins: | only the defaults    |
|      Server OS: | Ubuntu 6.04   |
|     Web server: | Apache 2.055   |
|   Perl version: | 5.87   |
|      Client OS: | OS X 10.4   |
|    Web Browser: | Camino   |
|     Categories: | Registration %SUPPORTCATEGORIES% |

---

### Post by GOwin on 2006-12-28
> **maphew said:**
> there is a .deb package maintained at [http://members.iinet.net.au/~spos/](http://members.iinet.net.au/~spos/) which is generally only a few days behind the current twiki.org release, if that.

this is the option i chose in installing my twiki site.

I still can't what the TwikiAdmin password is or how to reset it. anyone?

---

### Post by forg3@mac.com on 2007-01-07
Thanks for the detailed instruction.

Do have an issue with the install. When started twikking and went to either view or config the server messaged back:

can’t open the page “[http://192.168.25.55not%20set/oops/TWiki/TWikiRegistration?template=oopsaccessdenied;def=no_such_web;param1=view”](http://192.168.25.55not%20set/oops/TWiki/TWikiRegistration?template=oopsaccessdenied;def=no_such_web;param1=view”) because it can’t find the server “192.168.25.55not%20set”


Where would the variable be set for “192.168.25.55not%20set”?  twiki or apache confs?

Thoughts what might create this?

Thanks in advance!

forg3

---

### Post by forg3 on 2007-01-07
Oops, missed the post above but solved the problem differently.  Simply commented out this section

# Limit access to configure to specific IP addresses and or users.
# Make sure configure is not open to the general public.
# The configure script is designed for administrators only.
# The script itself and the information it reveals can be abused by
# attackers if not properly protected against public access.
# Replace JohnDoe with the login name of the administrator
# commented out  1/06/2007
#  <FilesMatch "^configure.*">
#       SetHandler cgi-script
#       Order Deny,Allow
#       Deny from all
#       Allow from 127.0.0.1, 192.168.1.10
#       Require user JohnDoe
#       Satisfy Any
# </FilesMatch>
# ------------------------

---

### Post by GOwin on 2007-01-25
If there are no email servers in the local network, and we have no interest for this feature, how do you suggest twiki handle user registration?

---

### Post by Cato2 on 2007-05-28
There's a pretty detailed [installation guide for TWiki on Ubuntu]("http://twiki.org/cgi-bin/view/Codev/TWikiOnUbuntu")  on the TWiki.org site - actually it's a supplement to the [installation guide for TWiki on Kubuntu]("http://twiki.org/cgi-bin/view/Codev/TWikiOnKubuntu"), but the two procedures are virtually identical.

If you have problems installing TWiki on Ubuntu, or general setup problems with TWiki, there is also a useful [support Web]("http://twiki.org/cgi-bin/view/Support/WebHome") on TWiki.org.  You won't always get such a quick answer as on Ubuntuforums, as we don't have such a large user base, but there is a lot of TWiki expertise there (I'm one of the developers btw).

Re GOWin's question about email server setup, here's a rather late reply...  the simplest approach is to simply point TWiki directly to your ISP's SMTP server, using Net::SMTP rather than sendmail.  See [this part of the TWiki docs]("http://twiki.org/cgi-bin/view/TWiki/TWikiSiteTools#E_mail").  Using TWiki without a local sendmail/postfix setup is quite common, but using it without any email access means you lose some useful features like notification of changes, ability to reset passwords automatically, and so on.

---

### Post by jambo-ap on 2007-08-23
Maybe it's unrelated to Twiki but when I go to [http://ipaddress/twiki/bin/configure](http://ipaddress/twiki/bin/configure)  I'm prompted to enter a user name and password.  I do so and get

Authorization Required

This server could not verify that you are authorized to access the document requested. Either you supplied the wrong credentials (e.g., bad password), or your browser doesn't understand how to supply the credentials required.

Additionally, a 500 Internal Server Error error was encountered while trying to use an ErrorDocument to handle the request.

Apache/2.0.55 (Ubuntu) PHP/5.1.6 Server at <ip address>Port 80

I've read through the install and followed to the letter.  I'm thinking it is somewhere in Apache but don't know where to look.

Thanks

---

### Post by christophniemann on 2007-09-18
You have to edit the /etc/apache2/conf.d/twiki.conf.
You have to replace the testusername with the name of the user with wich you would like to configure twiki. Afterwards you may have to restart apache and it works (It did in my case).

:guitar:

---

### Post by Cato2 on 2007-10-02
I didn't need to edit the twiki.conf file at all (tested on Feisty).  I just did 

   sudo apt-get install apache2 twiki

and that was it, could then log on as TWikiGuest to edit pages or run 'configure' within TWiki.

I've written a [TWiki on Ubuntu HOWTO]("http://twiki.org/cgi-bin/view/Codev/TWikiOnUbuntu") page at TWiki.org - I'd welcome comments on this, ideally on that page, and of course updates/fixes are very welcome!  This HOWTO is a greatly improved and simplified version of the original HOWTO, which is still available on the TWikiOnKubuntu page if you need or want to install TWiki manually.

---

### Post by Cato2 on 2007-10-21
Now that Ubuntu Gutsy 7.10 is released, TWiki 4.1.2 is available, which has some significant new features.  If TWiki was already installed on Feisty or earlier via the 'twiki' package, it will be upgraded automatically.

See the [TWiki on Ubuntu HOWTO]("http://twiki.org/cgi-bin/view/Codev/TWikiOnUbuntu") page at TWiki.org for details.  

If you can't be bothered reading the HOWTO, it is mostly just typing this: ```
sudo apt-get install apache2 twiki
```

But read the HOWTO for some other details too!

---

### Post by dhanushkodi.raja on 2008-07-28
root@dhanush-laptop:/# sudo /etc/init.d/apache2 restart
 * Restarting web server apache2                                                 * We failed to correctly shutdown apache, so we're now killing all running apache processes. This is almost certainly suboptimal, so please make sure your system is working as you'd expect now!
apache2: Syntax error on line 188 of /etc/apache2/apache2.conf: Syntax error on line 1 of /etc/apache2/httpd.conf: Could not open configuration file /home/httpd/twiki/twiki_httpd.conf: No such file or directory
 

Please help some one .After completing all those things , i am getting error like above. Please suggest any one . i am fighting with this last 7 days.

---

### Post by GOwin on 2008-07-28
Please post your
  /etc/apache2/apache2.conf
  /etc/apache2/httpd.conf

did you verify if /home/httpd/twiki/twiki_httpd.conf exists?

---

### Post by dhanushkodi.raja on 2008-07-29
> **GOwin said:**
> Please post your
  /etc/apache2/apache2.conf
  /etc/apache2/httpd.conf

did you verify if /home/httpd/twiki/twiki_httpd.conf exists?
now i am able to see the pages through Twiki guest user. But now i want to create the user. While i tried to registered as new user ,i am getting error like below.
******************************************************************************
Attention
Error registering new user
Internal error when sending email to [email]dhanush_akilan@sify.com[/email].
Please contact 0.
*****************************************************************************
Please help me to short out this issue

You have not been registered.

---

### Post by Cato2 on 2008-07-30
Do you have a mail system installed e.g. postfix or sendmail?  If not, and all you need is to have email sent to your ISP's SMTP server, try: ```
apt-get install ssmtp
``` - I haven't used this myself but it does just this.  It will need some configuration in both TWiki to point to its executable and in ssmtp to give it the SMTP server details.

It may be simpler to use TWiki's built-in SMTP support.  It requires the Net::SMTP package from CPAN, which should already be installed as part of the 'perl-modules' Ubuntu package.  So, just see the TWiki documentation on your system for how to set this up.

You didn't say which TWiki version you are using - assuming it's TWiki 4.1.2 as packaged in Ubuntu 7.10 and 8.04, have a look at step 9 of [http://twiki.org/cgi-bin/view/TWiki/TWikiInstallationGuide#Basic_Installation](http://twiki.org/cgi-bin/view/TWiki/TWikiInstallationGuide#Basic_Installation) where it talks about how to configure TWiki's SMTP support.  It's best to find the TWiki docs on your system as they will be correct for your system.  Something like the TWiki.TWikiInstallationGuide topic should be the right place.

---

### Post by dhanushkodi.raja on 2008-07-30
> **Cato2 said:**
> Do you have a mail system installed e.g. postfix or sendmail?  If not, and all you need is to have email sent to your ISP's SMTP server, try: ```
apt-get install ssmtp
``` - I haven't used this myself but it does just this.  It will need some configuration in both TWiki to point to its executable and in ssmtp to give it the SMTP server details.

It may be simpler to use TWiki's built-in SMTP support.  It requires the Net::SMTP package from CPAN, which should already be installed as part of the 'perl-modules' Ubuntu package.  So, just see the TWiki documentation on your system for how to set this up.

You didn't say which TWiki version you are using - assuming it's TWiki 4.1.2 as packaged in Ubuntu 7.10 and 8.04, have a look at step 9 of [http://twiki.org/cgi-bin/view/TWiki/TWikiInstallationGuide#Basic_Installation](http://twiki.org/cgi-bin/view/TWiki/TWikiInstallationGuide#Basic_Installation) where it talks about how to configure TWiki's SMTP support.  It's best to find the TWiki docs on your system as they will be correct for your system.  Something like the TWiki.TWikiInstallationGuide topic should be the right place.


I tried the same. but no luck . I want to create new user in twiki (localhost machine). Please help me plz.

---

### Post by jdqc69 on 2009-06-15
Anybody have a Graphics::Magick problem?
Graphics Magick is required for Twiki Image Plugin 

I am having trouble installing Graphics::Magick
Even if it installed, when I reupdate Image plug in it was saying Graphics Magick is not installed.

---

### Post by mzainal on 2010-03-09
Hi,

When i point to http://<ip address>/twiki/bin/configure, got page start with:
```
#!/usr/bin/perl -w
#
# TWiki Enterprise Collaboration Platform, http://TWiki.org/
#
# Copyright (C) 2000-2007 TWiki Contributors.
#
# This program is free software; you can redistribute it and/or
# modify it under the terms of the GNU General Public License
# as published by the Free Software Foundation; either version 2
# of the License, or (at your option) any later version. For
# more details read LICENSE in the root of this distribution.

```

Any idea why?

Thank you.

---

### Post by jdqc69 on 2010-03-09
You should follow the twiki steps carefully. I think you missed a step on your config
[http://twiki.org/cgi-bin/view/TWiki04x03/TWikiInstallationGuide#Customize_Your_TWiki](http://twiki.org/cgi-bin/view/TWiki04x03/TWikiInstallationGuide#Customize_Your_TWiki)

---

### Post by mzainal on 2010-03-10
All step i already follow but still got that page. Seems it's not execute that page using Perl.

---

### Post by jdqc69 on 2010-03-10
Did you install Perl?

Learn how to open perl... google it ;)

---

### Post by Cato2 on 2010-03-11
> **mzainal said:**
> Hi,

When i point to http://<ip address>/twiki/bin/configure, got page start with ...


What you are seeing is the result of the Perl (CGI) configure script for TWiki being returned as text to you, rather than being executed.

The problem is with your Apache2 setup (/etc/apache2/conf.d).

What I'd recommend is using Foswiki instead - it's completely upward compatible with TWiki and very well supported by the developers.  The Apache2 CGI setup for Foswiki is automatic and doesn't need any tweaking at all.

On Ubuntu, installing Foswiki is very simple, just did it recently on Ubuntu Hardy but will work on any version I believe:

1. Go to [http://foswiki.org/Extensions/DebianPackage](http://foswiki.org/Extensions/DebianPackage) and read the first bit - this package works fine on Ubuntu.

2. Go to [http://fosiki.com/Foswiki_debian/](http://fosiki.com/Foswiki_debian/) (linked from that page) and follow instructions to edit /etc/apt/sources.list

3. Run this command to install (this does the Apache setup for you):
```
apt-get install foswiki
```

4. Answer a few questions, e.g. setting a password

5. Foswiki should now be working - go to [http://yourhost/foswiki/bin/view](http://yourhost/foswiki/bin/view) to see if it works, and into the Sandbox to test it.

---

### Post by Zoanie on 2011-06-09
Hi Cato2,

    I'm vacillating on the decision to install twiki or foswiki.  I am starting with the latest Ubuntu 11.04 Server distro.  Would you still recommend foswiki over twiki?  Is the install procedure the same?

          Thanks,

---

### Post by Cato2 on 2011-06-10
I would recommend Foswiki - almost all the TWiki developers switched to Foswiki in 2008 and it is actively developed.  It's easy to install on any supported Ubuntu version, just follow the guide at [http://foswiki.org/Extensions/DebianPackage](http://foswiki.org/Extensions/DebianPackage) - essentially you add a repository at fosiki.com to APT, then do ```
aptitude install apache2 foswiki
``` and you have a working installation.

The fosiki.com repository also has 200+ Foswiki extensions packaged.

---

