---
title: "mod_perl2 / apache2 / ISP Config Vhosts / RT3.6"
date: 2008-07-15
forum: New to Ubuntu
---

### Post by brokenshadows on 2008-07-15
I am trying to get Resource Tracker 3.6 running and I'm running into a problem with mod_perl2...

I'm not sure where to begin to describe my issue, or what information will be needed to troubleshoot it, but here goes:

I have Ubuntu 8.04 LAMP, mySQL 5, phpMyAdmin, and ISP Config installed.  
In '/usr/lib/apache2/modules' I see "mod_perl.so"
In '/etc/apache2/mods-available' and '/etc/apache2/mods-enabled' I see "perl.load"  
When I run "httpd -l" from '/etc/apache2' I do not see anything with the word "perl" under "Compiled in modules:"

/etc/apache2/vhosts/Vhosts_ipsconfig.conf has the following added by me (everything else was configured by the ISP Config install):

Alias /rt /opt/rt3/share/html/
<Directory /opt/rt3/share/html/>
     Order allow,deny
     Allow from all
</Directory>
#PerlRequire /opt/rt3/bin/webmux.pl
#<Location /rt/>
#     AddDefaultCharset UTF-8
#     SetHandler perl-script
#     PerlHandler RT::Mason
#</Location>

I added that in per RT's installation instructions...

When I un-comment the portion regarding perl I can no longer restart apache2

I have no idea what I'm doing wrong as I know about ((==this much ==)) about linux and ubuntu and [SIZE="1"]((this much))[/SIZE] about perl and mod_perl

when I look at the bottom of my apache2 error.log I find the following...if anybody has any experience with Request Tracker, I'd appreciate the help...

RT_SiteConfig.pm:  Array found where operator expected at /opt/rt3/etc/RT_SiteConfig.pm line 412, at end of line
RT_SiteConfig.pm:  (Missing operator before?)
[error] Couldn't load RT config file RT_SiteConfig.pm:\n\nsyntax error at /opt/rt3/etc/RT_SiteConfig.pm line 412, near "helpdesk@owasa"\nCompilation failed in require at /opt/rt3/bin/ ../lib/RT/Config.pm line 402.\nBegin failed--compilation aborted at /opt/rt3/bin/webmux.pl line 101.\nCompilation failed at (eval 119) line 1.\n

---

### Post by jfluhmann on 2008-07-16
Change "helpdesk@owasa" in your RT_SiteConfig.pm to either:
'helpdesk@owasa'  (single quotes)
OR
"helpdesk\@owasa"  (double quotes, escaping the @)

HTH,
Jeremy

---

### Post by brokenshadows on 2008-07-16
thanks!  that kinda worked...

the difference being that in the RT_SiteConfig file, *helpdesk@owasa.local* wasn't in any kind of quotes, so I put it in double-quotes and tried to start the server again and it started up with no errors :)

don't know why I didn't notice it wasn't quoted...oh well

thanks again :D

---

