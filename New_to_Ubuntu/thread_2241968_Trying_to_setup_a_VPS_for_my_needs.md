---
title: "Trying to setup a VPS for my needs"
date: 2014-08-29
forum: New to Ubuntu
---

### Post by neoclis_drosos on 2014-08-29
Hello, new Ubuntu user here. I am trying to set up a VPS for my needs, currently has Ubuntu 14.04 on it.

My main goals are pretty simple - I am thinking it would be best to get a web panel for managing this installed, I need to host different domains on here for 2 different websites. Set up email for them. And they need to be setup for Prestashop eCommerce solution. 

Problem 1) I have been trying to install Virtualmin but been having trouble... I got the auto installer downloaded from their website, but every time it errors. I'm not sure the best way to read this error log, btu there are 2 parts that I think may be important:


..Errors were encountered while processing:
 postfix
 postfix-pcre
E: Sub-process /usr/bin/dpkg returned an error code (1)

... and



Setting up libapache2-mod-php5 (5.5.9+dfsg-1ubuntu4.3) ...
Module mpm_event disabled.
Enabling module mpm_prefork.
 * Restarting web server apache2
   ...done.
 * Restarting web server apache2
   ...done.
Processing triggers for libc-bin (2.19-0ubuntu6) ...


FATAL - Fatal Error Occurred: Something went wrong during installation: 0
FATAL - Cannot continue installation.
FATAL - Attempting to remove virtualmin repository configuration, so the installation can be
FATAL - re-attempted after any problems have been resolved.
FATAL - Removing temporary directory and files.
FATAL - If you are unsure of what went wrong, you may wish to review the log
FATAL - in /root/virtualmin-install.log
root@66:~# ..Errors were encountered while processing:
..Errors: command not found
root@66:~#  postfix


It is also saying something about bad host name... I am currently using the IP address as the host name. I am trying to get the site set up properly before I link the domain to it, and I don't know how to do this correctly.

2) I am not sure how to link separate domains to my site properly and keep the websites separate. Would this be easier through the panel once I get it working? I basically need to know the steps to make the 2 separate websites on the server & link the domains to them

3) For Prestashop I need the following:

[COLOR=#444444][FONT=Calibri]- A domain name[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]    - Web server Apache 1.3, Apache 2.x, Nginx, or Microsoft IIS[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]    - PHP 5.1 Installed & Enabled[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]    - MySQL 5.0+ installed with a database created[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]    - FTP Access[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]
[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]    Optional But Recommended:[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]    - PHP Configuration ask your provider to set memory_limit to "64M" and file_max_upload_size to "16M"[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]    - SSL Certificate if you plan to process payments[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]    - Optional PHP extensions: GD, cURL, SimpleXML, SOAP[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]    - To Improve Performance: MemCached, mcrypt PHP extension

With that said, in the past I have set up Prestashop withOUT a domain name, by editing my hosts file on the client end. So that should not be a problem. But other than that I'm not sure how to go about the rest of it...

Any guidance would be appreciated. Thansk![/FONT][/COLOR]

---

### Post by Habitual on 2014-08-29
try localhost as the hostname for the install.
You can "connect" domains to IPs later afterward.

What all is in /root/virtualmin-install.log or did you post all of it already?

---

### Post by neoclis_drosos on 2014-08-29
> **Habitual said:**
> try localhost as the hostname for the install.
You can "connect" domains to IPs later afterward.

What all is in /root/virtualmin-install.log or did you post all of it already?

I just tried it again, and the virtualmin installer doesn't like it when I give it localhost as a host name. So I decided to just put the entire domain name... Anyway so letting it try to install after that, it seemed to finish properly? It seems a host name may have been the entire problem after all...

So I guess it is on to #2 now. How to get this setup for both domain names? Right now going to my servers IP directly (xx.xx.xx.xx) or the domain name will take me right to the site. I am going to need 2 different sites on this host...

Would the best format for that be for example, xx.xx.xx.xx/site1/, and xx.xx.xx.xx/site2/, and have the domains point to each? Assuming that is the proper method I do not even know how to get separate installs for each, so I need some assistance with that now if possible please!

(Edit: Experimented with Virtualmin to try to figure this out, and it's not going well at all so far. Tried adding a virtual server for my domain. Now I can't access my domain, it tells me "[h=1]Forbidden[/h][COLOR=#000000][FONT=Times New Roman]You don't have permission to access / on this server."[/FONT][/COLOR] 

I tried connecting to [www.domain.com]("http://www.domain.com"), [www.domain.com/domain]("http://www.domain.com/domain"), and it lists it should be under home/domain, so i tried [www.domain.com/home/domain]("http://www.domain.com/home/domain").... no luck on either of them. But the virtualmin panel still works.... AND if I go to xx.xx.xx.xx (the IP) it works...? Not sure what's going on ... but it seems like making a server on VirtualMin broke the domain link somehow? 

How does it stop the domain from working when the IP works directly???)

---

