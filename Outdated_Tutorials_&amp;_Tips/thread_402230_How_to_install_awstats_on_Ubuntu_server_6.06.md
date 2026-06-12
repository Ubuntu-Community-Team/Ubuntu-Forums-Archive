---
title: "How to install awstats on Ubuntu server 6.06"
date: 2007-04-05
forum: Outdated Tutorials &amp; Tips
---

### Post by pjbgravely on 2007-04-05
I got awstats running on my server with the use of 3 different howto's. I thought it would be good to document them here as each one has wrong or missing information. There is an existing Howto here but it is old and breaks the debian Apache model. Any suggestions on how to make this howto better is welcome. This configuration is for monitoring Apache2 only.

For this Howto  your_domain should be substituted with your site domain name. Actually any name but awstats will work as long as it is the same throughout. Easiest to use you root domain name for example domain.com

I am assuming the server is headless and administered thought ssh. Log into your sudo user. then :

$sudo -i

This makes a root session without enabling the root account.

$apt-get install awstats libnet-ip-perl

When installed:

$pico /etc/awstats/awstats.conf

Change line 52: LogFile="/var/log/apache/access.log"

To: LogFile="/var/log/apache2/access.log"

Change line 122: LogFormat=4 to LogFormat=1

Save and exit editor.

Now:

$cp -a /etc/awstats/awstats.conf /etc/awstats/awstats.your_domain.conf

If you are doing this for many virtual domains, repeat for each one.

Now:

$pico /etc/awstats/awstats.your_domain.conf

Change the line 153: SiteDomain="" to SiteDomain="your_domain"

and change line 168 if you want to use this config for all your domains. Each one added will be picked up using this config.

Line 319 to 349 deal with security, if you want to use awstats to limit certain users. I have found publicly accessible awstats on the web. I have also seen that on my 500 MHz server awstats will use 100% of the processor when serving a page. This could be used as a DoS so it should be locked down in some way.

There are many other options to work with, but the above are the most important.

Save and exit.

Add this to apache2.conf, to fix the lost icon problem, it will work with all domains when put here.

$pico /etc/apache2/apache2.conf

```
Alias /awstats-icon/ /usr/share/awstats/icon/

<Directory /usr/share/awstats/icon>
  Options None
  AllowOverride None
  Order allow,deny
  Allow from all
</Directory>
```

If you want to lock down /var/lib/cgi-bin/awstats/ using apache2 now is the time to do it. The changes would be made in your virtual host. You only need to have access to awstats through one domain to see any number of different ones.

Now reload apache:

$/etc/init.d/apache2 reload

Now to make awstats automatically update.

$pico /etc/cron.d/awstats

You will see the following:
```
0,10,20,30,40,50 * * * * www-data [ -x /usr/lib/cgi-bin/awstats.pl -a -f /etc/awstats/awstats.conf -a -r /var/log/apache/access.log ] && /usr/lib/cgi-bin/awstats.pl -config=awstats -update >/dev/null
```

You will need to change it to look like this, of course adding you domain. Also make a line for each domain you have if you went that way.

```
3,33 * * * * www-data [ -x /usr/lib/cgi-bin/awstats.pl -a -f /etc/awstats/awstats.conf -a -r /var/log/apache2/access.log ] && /usr/lib/cgi-bin/awstats.pl -config=your_domain  -update >/dev/null
```

This is set to run for every 30 min. I changed mine to run every day at 4 :03 AM with 3 4 * * *

The default setup won't let www-data see the logs so we need to change them

$chmod 755 /var/log/apache2
$chmod 644 /var/log/apache2/access.log

Now to keep from losing data during log rolls and to keep the logs readable:

$ pico /etc/logrotate.d/apache2

Change: create 640 root adm 

To: create 644 root adm

Add to line after sharedscripts:

```
 prerotate
                su www-data -c '/usr/lib/cgi-bin/awstats.pl -config=your_domain -update'
        endscript

```

Don't forget to change your_domain.

Now to run for the first time.

$su www-data -c '/usr/lib/cgi-bin/awstats.pl  -config=your_domain  -update'

Now to see if it worked, open your browser to:

[http://your_domain/cgi-bin/awstats.pl?config=your_domain](http://your_domain/cgi-bin/awstats.pl?config=your_domain)

Hopefully if everything I have here is correct and it will work the first time.


Paul

---

### Post by tommytomato on 2007-07-01
Hi all

any one else getting an error straight away

I seem to be installing ok, 
```
apt-get install awstats
Reading package lists... Done
Building dependency tree... Done
Suggested packages:
  apache httpd libnet-dns-perl libnet-ip-perl libgeo-ipfree-perl
Recommended packages:
  libnet-xwhois-perl
The following NEW packages will be installed:
  awstats
0 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
Need to get 853kB of archives.
After unpacking 4747kB of additional disk space will be used.
Get:1 http://security.ubuntu.com dapper-security/main awstats 6.5-1ubuntu1.2 [853kB]
Fetched 853kB in 1m13s (11.5kB/s)                                                                                          
Selecting previously deselected package awstats.
(Reading database ... 23781 files and directories currently installed.)
Unpacking awstats (from .../awstats_6.5-1ubuntu1.2_all.deb) ...
Setting up awstats (6.5-1ubuntu1.2) ...
```

but when looking for awstats.conf to edit the directory /etc/awstats seems to be empty :confused:

Im running ubuntu 6.06.1.


TT

---

### Post by pjbgravely on 2007-07-01
You can try reinstalling awstats with 

aptitude reinstall awstats

If that doesn't help then just use the attached config file. Remember to rename it to awstats.conf and  make it owned by root with 644 permissions.

mv ./awstats.conf.txt ./awstats.conf
chown root. ./awstats.conf
chmod 644 ./awstats.conf

Paul

---

### Post by tommytomato on 2007-07-01
Thank you

I found this link worked straight away
[http://ubuntuforums.org/showthread.php?t=8410](http://ubuntuforums.org/showthread.php?t=8410)
```
Awesome tutorial. It got me going pretty quickly. Here's a quick and dirty update -- I think some packages have changed since the original tutorial. I did this as root, and am just listing the commands since the descriptions above were so good! (March 25, 2005).

# apt-get install awstats
# cp /usr/share/doc/awstats/examples /usr/local/awstats
# cd usr/local/awstats
# mkdir wwwroot
# mkdir wwwroot/cgi-bin
# gunzip awstats.model.conf.gz
# mv awstats.model.conf wwwroot/cgi-bin
# ./awstats_configure.pl
/etc/apache2/apache2.conf
y
foo.com
{ENTER}
{ENTER}
{ENTER}
# ln -s /usr/local/awstats/css/ wwwroot/
# ln -s /usr/share/awstats/* wwwroot/
# ln -s /usr/lib/cgi-bin/awstats.pl wwwroot/cgi-bin/
# chown -R --dereference www-data:www-data wwwroot
# chown -R --dereference www-data:www-data /var/lib/awstats
# chown root:www-data /var/log/apache2/access.log

In /etc/apache2/apache2.conf, find the section starting with
<Directory "/usr/loacl/awstats/wwwroot">, and put a # in front of the line "Options None" it should look like:
<Directory "/usr/local/awstats/wwwroot">
# Options None
AllowOverride None
Order allow,deny
Allow from all
</Directory>

# /etc/init.d/apache2 reload

visit:
http://foo.com/awstats/awstats.pl?config=foo.com
```

I had to change a few commands to suit my system like the cp command

```
cp -a /usr/share/doc/awstats/examples /usr/local/awstats
```

besides that it all worked out well.

TT

---

### Post by tommytomato on 2007-07-01
Got any idea on to why this keeps coming up ?

Never updated (See 'Build/Update' on awstats_setup.html page)


TT

---

### Post by pjbgravely on 2007-07-05
> **tommytomato said:**
> Got any idea on to why this keeps coming up ?

Never updated (See 'Build/Update' on awstats_setup.html page)


TT

Sounds like you haven't updated it yet. How are you doing it? With a web browser, which I didn't include because I consider it insecure, or the way I did in my Howto with automatic updating. Either way you have to change permissions on /var/log/apache2/access.log because it can't be read by default. The Howto you followed breaks the Debian apache2 model so finding a problem with the awstats script might be hard if that is the real problem.

Paul

---

### Post by tommytomato on 2007-07-06
Edit, never mind I got it

TT

---

### Post by tommytomato on 2007-07-06
Did you happen to create a mail config using awstats ?

any idea on what the Format log would be for /var/log/mail.log

TT

---

### Post by twistedtwig on 2007-07-06
Hi,

Firstly I would like to say thank you for the Howto!

I am having an issue though.  I have got to the following line and I get this error:

[php]su www-data -c '/usr/lib/cgi-bin/awstats.pl -config=your_domain -update'[/php]

[php]root@UbuntuWiggly:/etc# su www-data -c '/usr/lib/cgi-bin/awstats.pl -config=houseofhawkins.com -update'
Update for config "/etc/awstats/awstats.houseofhawkins.com.conf"
With data in log file "/var/log/apache/access.log"...
Error: Couldn't open server log file "/var/log/apache/access.log" : No such file or directory
Setup ('/etc/awstats/awstats.houseofhawkins.com.conf' file, web server or permissions) may be wrong.
Check config file, permissions and AWStats documentation (in 'docs' directory).
root@UbuntuWiggly:/etc# 
[/php]

I have used houseofhawkins.com as "my_domain" all the way though.  I am not sure why it is trying to look at /var/log/apache/access.log when I have apache2 installed.

EDIT: stupid me!!!! have edited Line 52.. will re read EVERY line to ensure I didn't miss anything else.  sorry /blush

not sure what permissions issues I may have also.

Thank you for your help :)

P.S... testing the link (if it had worked).. I don't (as far as I know and understand) have a cgi-bin "thingy"... I have only ever used PHP and static pages before so don't know if I have missed something there.



SECOND EDIT: I made sure the conf files were ok and setup correctly and removed a bad dup (Friday night coding and not doing too well)... but anyway... it now get:

[php] root@UbuntuWiggly:/etc# su www-data -c '/usr/lib/cgi-bin/awstats.pl -config=houseofhawkins.com -update'
Update for config "/etc/awstats/awstats.houseofhawkins.com.conf"
With data in log file "/var/log/apache2/access.log"...
Phase 1 : First bypass old records, searching new record...
Searching new records from beginning of log file...
Phase 2 : Now process new records (Flush history on disk after 20000 hosts)...
Jumped lines in file: 0
Parsed lines in file: 8
 Found 0 dropped records,
 Found 0 corrupted records,
 Found 0 old records,
 Found 8 new qualified records.
[/php]

Which (i assume :p) is great :)

but I now come to the N.B.  I don't seem to have this cgi-bin "thingy"... as when that is put into my browser houseofhawkins.com/cgi-bin/awstats.pl it returns that can not be found.

Not sure where to go from here.... will do some research, but if anyone can offer some advice I would be VERY grateful.

Thanks

---

### Post by tommytomato on 2007-07-06
I want to be able to create a mail awstats page

any idea on what the Format log would be for /var/log/mail.log

I came across a site that had a awstats auto generator for IIS

I have some thing like this is my mail.rockinghamgateway.com.conf file

LogFormat= "%time2 %email %email_r %host %host_r %method %url %code %bytesd"

And when i run ./awstats_updateall.pl now i get

```
root@rockinghamgateway:/usr/local/awstats# ./awstats_updateall.pl now
Running '"/usr/local/awstats/wwwroot/cgi-bin/awstats.pl" -update -config=mail.rockinghamgateway.com -configdir="/etc/awstats"' to update config mail.rockinghamgateway.com
Update for config "/etc/awstats/awstats.mail.rockinghamgateway.com.conf"
With data in log file "/var/log/mail.log"...
Phase 1 : First bypass old records, searching new record...
Searching new records from beginning of log file...
AWStats did not find any valid log lines that match your LogFormat parameter, in the 50th first non commented lines read of your log.
Your log file /var/log/mail.log must have a bad format or LogFormat parameter setup does not match this format.
Your AWStats LogFormat parameter is:
%time2 %email %email_r %host %host_r %method %url %code %bytesd
This means each line in your web server log file need to have the following personalized log format:
%time2 %email %email_r %host %host_r %method %url %code %bytesd
And this is an example of records AWStats found in your log file (the record number 50 in your log):
Jul  3 07:54:04 rockinghamgateway postfix/qmgr[4011]: C13D45DC159: from=<user1@rockinghamgateway.com>, size=545, nrcpt=1 (queue active)
Setup ('/etc/awstats/awstats.mail.rockinghamgateway.com.conf' file, web server or permissions) may be wrong.
Check config file, permissions and AWStats documentation (in 'docs' directory).

```

And i've tried this as well, which doesn't seem to work

LogFile= "perl /usr/local/awstats/maillogconvert.pl standard</var/log/mail.log|"

Any ideas please

TT

---

### Post by twistedtwig on 2007-07-09
to fix the *.pl fie downloading instead of running I found that the follow seemed to work:

within apache2.conf

I have uncommented:

AddHandler cgi-scrpt .cgi

But i was told to add .pl:

AddHandler cgi-scrpt .cgi .pl

also to do:

<Directory />
Options followsymLinks
AllowOverride None
</Directory>

change to:

Options followSymLibks +ExecCGI

the only place I could find this was in /etc/apach2/conf/vhosts/vhosts.conf in the root file path.

When I did the test.pl with the correct permissions it all worked :)

I now have it working :)  YAY

Thanks

---

### Post by pjbgravely on 2007-07-11
> **tommytomato said:**
> I want to be able to create a mail awstats page

any idea on what the Format log would be for /var/log/mail.log

I came across a site that had a awstats auto generator for IIS

I have some thing like this is my mail.rockinghamgateway.com.conf file

LogFormat= "%time2 %email %email_r %host %host_r %method %url %code %bytesd"

And when i run ./awstats_updateall.pl now i get



And i've tried this as well, which doesn't seem to work

LogFile= "perl /usr/local/awstats/maillogconvert.pl standard</var/log/mail.log|"

Any ideas please

TT

Sorry, I don't have a clue how to make that work. I checked for documentation and all I can find are docs on analyzing apache. If I find something I will let you know.

Paul

---

### Post by pjbgravely on 2007-07-11
> **twistedtwig said:**
> to fix the *.pl fie downloading instead of running I found that the follow seemed to work:

within apache2.conf

I have uncommented:

AddHandler cgi-scrpt .cgi

But i was told to add .pl:

AddHandler cgi-scrpt .cgi .pl

also to do:

<Directory />
Options followsymLinks
AllowOverride None
</Directory>

change to:

Options followSymLibks +ExecCGI

the only place I could find this was in /etc/apach2/conf/vhosts/vhosts.conf in the root file path.

When I did the test.pl with the correct permissions it all worked :)

I now have it working :)  YAY

Thanks

Sorry replying so late. I didn't think of people not having cgi-bin enabled by default on Apache. Was this installed on a later version of Ubuntu server, a desktop install,  or did awstats install somewhere other than /usr/lib/cgi-bin? Anyway I am glad you got it working despite my lateness.

Paul

---

### Post by twistedtwig on 2007-07-11
No problem at all.. I learnt some stuff so all good! :)

---

### Post by pjbgravely on 2007-07-11
> **twistedtwig said:**
> No problem at all.. I learnt some stuff so all good! :)

Please re-read my answer, as I changed it right after you posted. It seems I am  really slow this week.


Paul

---

### Post by twistedtwig on 2007-07-12
I can't remember where it installed (will check tonight if I get time, Dads Birthday so have to go see him).

My server had 5.10 installed first (I think) when it had all its web stuff setup.  It has been upgraded to edgy a while ago.

One mroe thing I had to go to get Awstats to fully work was create a symbolic link from /usr/lib/cgi-bin/ from "awstats-icons" to err... where ever it had installed it all.  Again will check that and edit the post accordingly.

I had never tried to use any perl or cgi-bin stuff before hand so was a bit of a confusing one for me.  Not sure if it was because of an old install or just not there.

---

### Post by ack.inc on 2010-02-14
Hi! I'm trying to set awstats up to read VSFTPD's logs. I've done every step mentioned here : [http://awstats.sourceforge.net/docs/awstats_faq.html#FTP](http://awstats.sourceforge.net/docs/awstats_faq.html#FTP), except for the last statement that reads "Now you can use AWStats as usual (run the update process and read statistics)."

Now I'm flabbergasted...How do I "run the update process"? I don't have any directories that read "wwwroot" or "cgi-bin". In fact, I don't even have an "awstats.pl" script anywhere...

Please help!

---

