---
title: "CGI help"
date: 2012-08-14
forum: Programming Talk
---

### Post by terminal27 on 2012-08-14
I need a webpage that show the actual device hostname and password (masked) and then allow web user to change the device hostname and password (similar to any router) and then a button to reboot the device. Can anyone help me where to start with? I am a bit blank.

---

### Post by trent.josephsen on 2012-08-14
Sounds like a security nightmare. I hope this machine isn't to be connected to the Internet.

---

### Post by terminal27 on 2012-08-14
> **trent.josephsen said:**
> Sounds like a security nightmare. I hope this machine isn't to be connected to the Internet.
Why? it is not far from a router's GUI. Of course access to the page is via admin login type.

---

### Post by trent.josephsen on 2012-08-14
And you plan to implement this yourself?

---

### Post by spjackson on 2012-08-14
Don't answer this now, but you need to consider what are the security requirements? e.g. only accept requests from certain IP addresses.

What sort of device, o/s, webserver is this to run on? Note for example that by default apache on Ubuntu runs as the unprivileged user www-data. In normal circumstances, this user cannot change the hostname or reboot the server. Are there similar restrictions on your device? The strategies for doing this on Ubuntu may not be appropriate for your device.

What facility is to be used to store the password and authenticate?

What tools are available for programming the webpage? PHP? Perl? Ruby? Python? Are you at liberty to install anything you want on the device? Depending on the environment, it may be possible to find something that does something similar as a starting point.

What relevant skills do you have?

---

### Post by terminal27 on 2012-08-16
> **trent.josephsen said:**
> And you plan to implement this yourself?
 Yes, I'll try.

---

### Post by terminal27 on 2012-08-16
> **spjackson said:**
> Don't answer this now, but you need to consider what are the security requirements? e.g. only accept requests from certain IP addresses.
 
What sort of device, o/s, webserver is this to run on? Note for example that by default apache on Ubuntu runs as the unprivileged user www-data. In normal circumstances, this user cannot change the hostname or reboot the server. Are there similar restrictions on your device? The strategies for doing this on Ubuntu may not be appropriate for your device.
 
What facility is to be used to store the password and authenticate?
 
What tools are available for programming the webpage? PHP? Perl? Ruby? Python? Are you at liberty to install anything you want on the device? Depending on the environment, it may be possible to find something that does something similar as a starting point.
 
What relevant skills do you have?
 I can install anything, total freedom. I can set/remove the restrictions as I please. I was expecting to use Apache & Ubuntu but I can use any other option.

---

### Post by spjackson on 2012-08-16
[Webmin]("http://webmin.com/") seems to have the facilities you describe, with a bucket load of other stuff as well. Could you use this or are you particularly wanting to write something yourself?

---

### Post by terminal27 on 2012-08-19
OK, at this point I managed to do a couple of things.
I found the answer for finding the device's hostname, changing it and reboot all through the webpage:
 
create a webpage with login access (let's say admin.cgi)
#!/usr/bin/perl -w
print "Content-type: text/html\r\n\r\n";
$myhost = `hostname`;
print "<html><body>";
print "Hostname : $myhost";
print "<FORM method=post action=reboot.cgi>";
print "New hostname : <INPUT TYPE=text NAME=newhostname SIZE=20>";
print "</FORM>";
print "</body></html>";
 
 
create a script (reboot.cgi)
#!/bin/sh
echo "Content-Length: 100"
echo ""
echo "<BR>"
echo "<BODY><H2>
myQry="$QUERY_STRING";
myNewHostname=$myQry | sed 's/newhostname=/ /g';
myOldHostname='hostname';
 
#I need help with the following two lines:
# sudo sed -i 's/myOldHostname/myNewHostname/g' /etc/hostname &
# sudo sed -i 's/myOldHostname/myNewHostname/g' /etc/host &
sudo reboot &
 
"..Rebooting the system...., please wait a couple of minutes before logging back.</H2></BODY>"
 
And it works to find the hostname and reboot the device but I can't make it chnage the hostname as I mentioned commented out. Any help?
Thank you in advance,
 
Forgot to mention that you need to go to /etc/sudoers and add a line:
ALL ALL=(root) NOPASSWD /sbin/reboot

---

### Post by spjackson on 2012-08-19
> **terminal27 said:**
> 
create a webpage with login access (let's say admin.cgi)
```

#!/usr/bin/perl -w
print "Content-type: text/html\r\n\r\n";
$myhost = `hostname`;
print "<html><body>";
print "Hostname : $myhost";
print "<FORM method=post action=reboot.cgi>";
print "New hostname : <INPUT TYPE=text NAME=newhostname SIZE=20>";
print "</FORM>";
print "</body></html>";
 
```
 If you are doing CGI programming from Perl, then the CGI module is meant to make this a bit easier. e.g.
```

use CGI;

$html = CGI->new( );
print $html->header;
print $html->start_html( -title=>"My Webpage",-bgcolor=>"#FFE599");

```but you don't have to use it.

> 
Forgot to mention that you need to go to /etc/sudoers and add a line:
ALL ALL=(root) NOPASSWD /sbin/rebootIf you are doing it that way, I guess you should create a script that does the privileged operations and add that script to /etc/sudoers, similar to the above. I haven't tested that this works, but I think it would.

```

#!/bin/bash

$myOldHostname="$1"
$myNewHostname="$2"

# TODO validate parameters

#I need help with the following two lines:
sed -i "s/${myOldHostname}/${myNewHostname}/g" /etc/hostname
sed -i "s/${myOldHostname}/${myNewHostname}/g" /etc/host
reboot

```

---

### Post by terminal27 on 2012-08-19
It doesn't work, can't read from /etc/hosts and hostname. But for a last try I did:
 
sudo gedit /etc/apache2/sites-available/default
 
and add:
<Directory /etc/>
       Order allow,deny
       Allow from all
</Directory>
 
then restart apache (sudo /etc/init.d/apache2 restart)
and from now I can read the etc files from the apache server
 
#if I add to my reboot.cgi
cat /etc/hosts | sed 's/$myOldHostname/$myNewHostname/g' > /tmp/newhosts;
 
#and now I need just to copy from tmp to etc such as 
sudo mv /tmp/newhosts /etc/hosts;
 
and do the same for /etc/hostname file, then finally reboot to make things right.
At this point I am not worry about security holes if any. I will investigate it later.

---

### Post by terminal27 on 2012-08-26
[QUOTE=spjackson;12181357]If you are doing CGI programming from Perl, then the CGI module is meant to make this a bit easier. e.g.
```

use CGI;
 
$html = CGI->new( );
print $html->header;
print $html->start_html( -title=>"My Webpage",-bgcolor=>"#FFE599");

```but you don't have to use it.
 
QUOTE]
 Sorry spjackson, I forgot to thank you for your help. :-)

---

