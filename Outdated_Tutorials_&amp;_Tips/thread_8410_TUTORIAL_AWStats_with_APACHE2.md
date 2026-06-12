---
title: "TUTORIAL: AWStats with APACHE2"
date: 2004-12-17
forum: Outdated Tutorials &amp; Tips
---

### Post by Hellsteeth on 2004-12-17
I have installed AWStats on my web server and posted the following guide to help others. 

A mini Howto tutorial  - Getting AWSTATS working with APACHE2 in UBUNTU Linux.

Proud of my little ADSL connected web server built on an old Gateway P200 was I, that I felt the need to add some stats pages. After under a minute of detailed research I decided to go for AWSTATS because it just looked better.

Diving right in I did a $ sudo apt-get install awstats and was happy to find a package available and watched it install without any fuss.

Now what? I suppose I’ll have to read some documentation so went to [www.awstats.org](http://www.awstats.org)  to find some interesting background reading and very little detail that matched my install. Where were wwwroot and the tools directory all the documententation kept referring to?

After 30 minutes of googling and forum searching I found a number of documents that just confused me so decided then if I got this thing going, I would write it up.

Well it works just fine now so true to my word here is what I had to do. I wish I had bookmarked some of the sites I got useful information from, just in a hurry I suppose but I didn’t other than one which was very useful, posted by anniec and gave me more than 90% of what I needed. [LINK](http://ibao.hopto.org/blog/debian/archives/2004/10/awstats_web_log.html) 

Before running the ./configure.pl  script you needs to get your directories in shape and make a backup of your Apache2 config file as it is modified during this process.

$sudo cp /etc/apache2/apache2.conf /etc/apache2/apache2.conf.orig

AWSTATS in ubunto seems to dump all the files into /usr/share/doc/awstats/examples so step one was to copy them all over to the documented directory /usr/local/awstats.

$ sudo cp /usr/share/doc/awstats/examples

You can use mv (move) as well, I just wasn’t sure what I was doing so wanted to keep a virgin copy at hand and maybe Ubuntu may yet need it.

In this directory you will find a compressed copy of the main config file called awstats.model.conf.gz. You need to uncompress this with

$ sudo gunzip awstats.model.conf.gz  which will give you a copy of awstats.model.conf.

I made a backup $ sudo cp awstats.model.conf awstats.model.conf.orig then copied it to /usr/local/awstats.

I then followed anniec’s instructions more or less, but modifying them for Apache2 rather than Apache.

$ sudo mkdir wwwroot

$ sudo mkdir wwwroot/cgi-bin

Now we need to run the perl script, which immediately failed because it cannot find httpd.conf.

This is because Apache2 in Ubunto’s default configuration is called apache2.conf.

You just need to enter this location after the script complains about not finding httpd.conf.

$ cd /usr/local/awstats/

$ sudo ./configure.pl

Enter /etc/apache2/apache2.conf  when prompted for httpd.conf location and give the configuration file a unique name such as your domain name. If your unique name given was foo  then you will end up with a file called awstats.foo.conf.  

Once run successfully the perl script will add some lines to apache2.conf. The final part of this file will have these lines added to it. Don’t bother restarting Apache just yet.

#
# Directives to allow use of AWStats as a CGI
#
Alias /awstatsclasses "/usr/local/awstats/wwwroot/classes/"
Alias /awstatscss "/usr/local/awstats/wwwroot/css/"
Alias /awstatsicons "/usr/local/awstats/wwwroot/icon/"
ScriptAlias /awstats/ "/usr/local/awstats/wwwroot/cgi-bin/"
#
# This is to permit URL access to scripts/files in AWStats directory.
#
<Directory "/usr/local/awstats/wwwroot">
    Options FollowSymLinks
    AllowOverride None
    Order allow,deny
    Allow from all
</Directory>

These lines added to apache2.conf do not match the directory structure so I added the recommended links to the real ones modifying again for the Apache2 structure.

$ sudo mv awstats.model.conf wwwroot/cgi-bin
$ sudo ln -s /usr/local/awstats/css/ wwwroot/
$ sudo ln -s /usr/share/awstats/* wwwroot/
$ sudo ln -s /usr/lib/cgi-bin/awstats.pl wwwroot/cgi-bin/
$ sudo chown -R --dereference www-data:www-data wwwroot
$ sudo chown -R www-data:www-data /var/lib/awstats/
$ sudo chown root:www-data /var/log/apache2/access.log

Now is the time to restart Apache2. The method I used was to issue the command

$ sudo /etc/init.d/apache2 restart

If all is well you will get a little [ok] in the right hand side. So far so good we need to now modify the awstats configuration file.

You now need to edit this with an editor. I used vi. If you have not used vi before or have been scared by the stories do not fear and follow these instructions.

$sudo vi /etc/awstats/awstats.foo.conf

If all is well you will see the configuration file come up – if you see a blank page you have made an error and need to replace foo above with you unique name! To exit press :q! in sequence and try again.

You need to scroll down and find the line that begins LogFile="…. and replace it

Vi has a FIND function which is to just press the / key and enter your search string i.e. LogFile=  and press [ENTER]. This will take you to the first entry that has this line. To FIND AGAIN just press / followed by [ENTER] again. When you have found your line you need to INSERT. This is done by pressing the I on the keyboard. You will see the work INSERT comes up at the bottom. Use the keyboard arrows to move where you want to go and then modify the line to read.

[Did you know that / can be used in the FireFox browser for FIND also?]

LogFile="/var/log/apache2/access.log"

To get out of INSERT mode press the [Esc] key. If you make a complete hash of it you can exit without saving with the three key sequence after pressing [Esc] :q!  and try again.

Ensure the following other lines read as follows

LogType=W
LogFormat=1
SiteDomain="foo"          
# Substitute foo above with your unique name that you gave your awstats configuration file and don’t bother to add this line.
DNSLookup=1
DirData="/var/lib/awstats/"
AllowToUpdateStatsFromBrowser=1

To save the configuration file we must now use the save command w (for Write) so press [Esc] followed by :wq!

Now go to your site with a browser and type this lot in

[http://www.foo.com/awstats/awstats.pl?config=foo](http://www.foo.com/awstats/awstats.pl?config=foo) 
changing foo for your appropriate settings as required. 

You should see the webpage come up but with blank stats. You will see an update Update now link at the top of the page which will then manually go and collect the stats. This bit can be automated with the use of the system cron command. This is well documented on the [www.awstats.org](www.awstats.org) site so you should get that bit from there.

As always with these tutorials, use at your own risk, make a backup first, subject to change without notice and probably will cause you some wasted hours. Your cat may also leave home.

---

### Post by ming0 on 2005-03-04
I keep getting permissions errors :( I followed the directions as closely as possible...

how should my directories be owned and set up? 

I've got /var/log/apache2/ owned root:www-data and all files are chmodded 640

```
dean@server /usr/local/awstats $ ls -la
total 149
drwxr-sr-x    5 root     www-data      496 Mar  4 12:14 .
drwxrwsr-x   10 root     staff         264 Mar  4 12:12 ..
-rwxr-xr-x    1 root     www-data      289 Mar  4 12:13 awstats-update
-rw-r--r--    1 root     www-data     1179 Mar  4 12:13 awstats-update.8
-rwxr-xr-x    1 root     www-data    18472 Mar  4 12:13 awstats_buildstaticpages.pl
-rwxr-xr-x    1 root     www-data    12767 Mar  4 12:13 awstats_exportlib.pl
-rwxr-xr-x    1 root     www-data     4576 Mar  4 12:13 awstats_updateall.pl
-rwxr-xr-x    1 root     www-data    22212 Mar  4 12:13 configure.pl
drwxr-sr-x    2 root     www-data      120 Mar  4 12:13 css
-rw-r--r--    1 root     www-data     1341 Mar  4 12:13 example.pm.gz
drwxr-sr-x    2 root     www-data       96 Mar  4 12:13 js
-rwxr-xr-x    1 root     www-data    27513 Mar  4 12:13 logresolvemerge.pl
-rwxr-xr-x    1 root     www-data    25133 Mar  4 12:13 maillogconvert.pl
-rwxr-xr-x    1 root     www-data    10535 Mar  4 12:13 urlaliasbuilder.pl
drwxr-sr-x    3 root     www-data      192 Mar  4 12:18 wwwroot

```

Whenever I visit [http://192.168.0.102/awstats/awstats.pl?config=gallery](http://192.168.0.102/awstats/awstats.pl?config=gallery), I get the following:
Forbidden

You don't have permission to access /awstats/awstats.pl on this server.

Additionally, a 403 Forbidden error was encountered while trying to use an ErrorDocument to handle the request.

Uggg, I hate permissions problems!!!!  ](*,)

---

### Post by Hellsteeth on 2005-03-04
Hi ming0,
At first glance, this may have nothing to do with awstats.
I suggest you look to see if apache is pointing to the right directory that awstats are in. Put an ordinary test web page (test.htm) in the same place, then see if you can access that at [http://192.168.0.102/awstats/test.htm](http://192.168.0.102/awstats/test.htm). If you can't it then Apache isn't getting that far and it is an Apache issue.

For the record my directory listing is like this. I see one symbolic link in my listing and not in yours?



```
root@server:/usr/local/awstats # ls -la
total 184
drwxr-xr-x    5 root     root         4096 2004-12-16 14:44 .
drwxrwsr-x   10 root     staff        4096 2004-12-16 14:41 ..
-rwxr-xr-x    1 root     root        18472 2004-01-25 16:19 awstats_buildstaticpages.pl
-rwxr-xr-x    1 root     root        12767 2003-12-06 00:53 awstats_exportlib.pl
-rw-r--r--    1 root     root        15671 2004-12-12 21:17 awstats.model.conf.orig.gz
-rwxr-xr-x    1 root     root          289 2004-07-27 23:36 awstats-update
-rw-r--r--    1 root     root         1179 2004-07-27 23:36 awstats-update.8
-rwxr-xr-x    1 root     root         4576 2004-01-05 08:01 awstats_updateall.pl
-rwxr-xr-x    1 root     root        22212 2004-01-13 14:14 configure.pl
drwxr-xr-x    2 www-data www-data     4096 2004-12-16 13:57 css
-rw-r--r--    1 root     root         1341 2003-11-15 20:39 example.pm.gz
drwxr-xr-x    2 root     root         4096 2004-12-16 13:57 js
-rwxr-xr-x    1 root     root        27513 2004-01-07 07:13 logresolvemerge.pl
-rwxr-xr-x    1 root     root        25133 2004-01-25 16:15 maillogconvert.pl
-rwxr-xr-x    1 root     root        10535 2003-11-08 17:56 urlaliasbuilder.pl
drwxr-xr-x    3 www-data www-data     4096 2004-12-16 15:28 wwwroot

```

---

### Post by ming0 on 2005-03-08
I think it is an apache problem--because I can't get to the test page.

Here's the bottom of my apache2.conf:

```
#
# Directives to allow use of AWStats as a CGI
#
Alias /awstatsclasses "/usr/local/awstats/wwwroot/classes/"
Alias /awstatscss "/usr/local/awstats/wwwroot/css/"
Alias /awstatsicons "/usr/local/awstats/wwwroot/icon/"
ScriptAlias /awstats/ "/usr/local/awstats/wwwroot/cgi-bin/"

#
# This is to permit URL access to scripts/files in AWStats directory.
#
<Directory "/usr/local/awstats/wwwroot">
    Options FollowSymLinks
    Options None
    AllowOverride None
    Order allow,deny
    Allow from all
</Directory>

```

I am really bad at weeding out permissions problems, and I'm sure that's what this is... do you have any tips or ideas?

Thanks :)

BTW, which file do you see missing? I can only see the awstats.model.conf.orig.gz file, but I don't think that is a necessary file to get apache access into the wwwroot folder.

---

### Post by Hellsteeth on 2005-03-11
Hi
My apache2.conf enclosed, some difference in the last part.
I have also included the line before that enables the virtual host configurations. You should check this one as well.



```
# Include the virtual host configurations:
Include /etc/apache2/sites-enabled/[^.#]*

#
# Directives to allow use of AWStats as a CGI
#
Alias /awstatsclasses "/usr/local/awstats/wwwroot/classes/"
Alias /awstatscss "/usr/local/awstats/wwwroot/css/"
Alias /awstatsicons "/usr/local/awstats/wwwroot/icon/"
ScriptAlias /awstats/ "/usr/local/awstats/wwwroot/cgi-bin/"

#
# This is to permit URL access to scripts/files in AWStats directory.
#
<Directory "/usr/local/awstats/wwwroot">
    Options FollowSymLinks
    AllowOverride None
    Order allow,deny
    Allow from all
</Directory>

```

---

### Post by ming0 on 2005-03-11
[QUOTE=ming0]```

<Directory "/usr/local/awstats/wwwroot">
    Options FollowSymLinks
    **Options None**
    AllowOverride None
    Order allow,deny
    Allow from all
</Directory>

```[/QUOTE]

The part that says "Options None" was the problem... I took that out, reset the server, and now awstats works like a charm!!! Thanks a lot for the help :)

---

### Post by stuporglue on 2005-03-25
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
<Directory "/usr/loacl/awstats/wwwroot">, and put a # in front of the line "Options None" it should     look like: 
<Directory "/usr/local/awstats/wwwroot">
#    Options None
    AllowOverride None
    Order allow,deny
    Allow from all
</Directory>

# /etc/init.d/apache2 reload

visit:
[http://foo.com/awstats/awstats.pl?config=foo.com](http://foo.com/awstats/awstats.pl?config=foo.com)

---

### Post by udha on 2005-04-09
Thankyou so much!
Thankyou Hellsteeth and thankyou stuporglue!

I am so glade to finally have this working! almost straight after installing ubuntu I used apt-get to install apache2, mysql, php4, awstats and then installed phpmyadmin, phpbb and a few other things to muck around with, I'm also experimenting with virtual hosts, and I just hosted a file for another forum board and was using iptraf to watch it flying along, and that got me motivated to figure out how to get AWstats working.

I didn't have much luck and decided to search the 'other software' thread in here for awstats and hit gold straight away, it's taken me 10 minutes now to get it working, and days of previous wondering, as I could see it mentioned in the syslog file which was just annoying me more!

---

### Post by kuleali on 2005-04-12
thank you. This worked!

---

### Post by istoyanov on 2005-05-26
Thanks to this tutorial I have a working AWstats installation, but I wonder how to tweak it further in order to:

1) allow the statistics page to be accessible only to a range of local addresses (for example 192.168.1.10 through 192.1168.1.125)

2) hide the contents of the /awstats/wwwroot/ directory and its subdirectories (which are now visible when accessing [http://my.site.example/awstats)](http://my.site.example/awstats)), allowing access only to the awstats.pl script.

3) to rotate the logs without losing information [1]

[1] According to the AWstats FAQ one should insert ```
prerotate
/usr/local/awstats/wwwroot/cgi-bin/awstats.pl -update -config=mydomainconfig
endscript
``` in /etc/logrotate.d/apache2. Is this OK for a default warty apache2 install?

I would be very grateful to receive tips/hints/help in this direction :)

Cheers!

---

### Post by VidJa on 2005-08-11
Thanks, this works for straight Debian as well. I wonder why the original debian package changed the file locations in the first place without modifying the installer to match the changes.

---

### Post by Chef666 on 2005-11-04
I installed awstats without a problem, BUT when I view my stats pages ([http://url/awstats/awstats.pl?config=bla](http://url/awstats/awstats.pl?config=bla)) I don't see any stats....

All the fields stay zero. So I see the page perfectly, but everythings stay 0....
And my access.log IS filled.
( -rw-r-----  1 root www-data 512048 2005-11-04 20:24 access.log )

What happened??? :confused:

---

### Post by shubjero on 2006-03-05
I'm having the same problem with Ubuntu 5.10.


These website statistic programs seem to be such a pain in the ***.. I wish they made something simplier.. or at least made an official ubuntu howto.

Please help!

---

### Post by kmi on 2006-03-29
For the - numerous :mrgreen: - 0 0 0 0 0 etc. in Awstats : are you sure you have updated stats with :
```
sudo /usr/local/awstats/wwwroot/cgi-bin/awstats.pl -update -config=yoursite.org
```
[QUOTE=shubjero]These website statistic programs seem to be such a pain in the ***.. I wish they made something simplier.. or at least made an official ubuntu howto.[/QUOTE]
[-(  Awstats really ain't that...
But if you want something really (really really...) simple to cope with, I think Webalizer could fit. You will find info [here]("http://j4cques.blogspot.com/2005/12/install-and-configure-webalizer-on.html") for example...;)

---

### Post by stupidbastard on 2006-06-17
I seem to be having a similar problem, although now it has morphed. I couldn't update awstats, I got "couldn't open access.log" error but managedto get that to work. However, my access.log is not working right now. Before I installed (mangled) awstats, it worked perfectly and I watched it with tail -f command. Now it does not update accurately, any idea what I should start looking for?

I can sit on the log with tail -f /var/log/apache2/access.log and today I only see this (from yesterday) but I had friends hit site and it didn't record them.

192.168.x.x - - [16/Jun/2006:22:49:35 -0700] "GET /favicon.ico HTTP/1.1" 404 287 "-" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.7.13) Gecko/20060418 Firefox/1.0.8 (Ubuntu package 1.0.8)"
212.95.x.x - - [17/Jun/2006:00:31:55 -0700] "HEAD /icons/apache_pb.gif HTTP/1.0" 200 - "-" "Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1)"

---

### Post by hogman23 on 2006-07-28
Awesome Tutorial...Thanks

---

### Post by Wasca on 2006-09-05
For those that are following these instructions and are using Breezy, I noticed that the install forgot to add this to my apache config

Options FollowSymLinks

make sure your config includes this (see below)

<Directory "/usr/local/awstats/wwwroot">
    Options FollowSymLinks
    #Options None
    AllowOverride None
    Order allow,deny
    Allow from all
</Directory>

---

### Post by Catty on 2006-11-08
> **stupidbastard said:**
> I can sit on the log with tail -f /var/log/apache2/access.log and today I only see this (from yesterday) but I had friends hit site and it didn't record them.

192.168.x.x - - [16/Jun/2006:22:49:35 -0700] "GET /favicon.ico HTTP/1.1" 404 287 "-" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.7.13) Gecko/20060418 Firefox/1.0.8 (Ubuntu package 1.0.8)"
212.95.x.x - - [17/Jun/2006:00:31:55 -0700] "HEAD /icons/apache_pb.gif HTTP/1.0" 200 - "-" "Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1)"

Yeah, I got the same problem as you.. Apache doesn't seem to write to access.log anymore after I followed this tutorial..
Anyone who have got a solution to this?


I hope someone can help me, I re-installed my server today because of the problem that it didn't write to access.log. And now that I've read these posts I know the source of it.. too late though, I followed the tutorial again without reading all posts. Damn.

Anyone who can give me a hand? I would be very thankful!

---

### Post by nucrebain on 2007-01-06
I have spent several hours trying to get apache2 to work with my ubuntu 6.10 box. I can get the Apache test page but I still get a 403 forbidden access denied error. I tried all the things every one said to try. I have my user permissions set for [www.....I](www.....I) think?

Could some one explain more simplified how _permissions_ work? I think this is where I am stuck but all the information I find is very vague.
-Patrick Kelly

---

### Post by Sherman.Boyd on 2007-03-09
Doesn't this whole tutorial defeat the purpose of using apt-get to install in the first place?  With all this copying and symlinking; what happens when it's time to update the software?  It's just as well to install from tarball.  :mad: 

Instead of modifying the apache config file with a perl script there should be an example conf file to drop into conf.d ...

Am I the only one who thinks the awstats package needs a little attention?

---

### Post by pcman01 on 2007-03-09
I saw a very similar question yesterday, on this site: [http://counting.xf.cz/id2964.html]("http://counting.xf.cz/id2964.html")

---

### Post by tr333 on 2007-03-10
for those who are interested, i found the following guide useful for setting up awstats on ubuntu edgy 6.10: [http://www.debuntu.org/2006/04/21/33-how-to-setting-up-awstats-with-apache-2-on-debianubuntu]("http://www.debuntu.org/2006/04/21/33-how-to-setting-up-awstats-with-apache-2-on-debianubuntu").

---

### Post by jackrobinson on 2007-03-25
never mind.

---

### Post by tommytomato on 2007-07-01
> **stuporglue said:**
> Awesome tutorial. It got me going pretty quickly. Here's a quick and dirty update -- I think some packages have changed since the original tutorial. I did this as root, and am just listing the commands since the descriptions above were so good! (March 25, 2005).

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
<Directory "/usr/loacl/awstats/wwwroot">, and put a # in front of the line "Options None" it should     look like: 
<Directory "/usr/local/awstats/wwwroot">
#    Options None
    AllowOverride None
    Order allow,deny
    Allow from all
</Directory>

# /etc/init.d/apache2 reload

visit:
[http://foo.com/awstats/awstats.pl?config=foo.com](http://foo.com/awstats/awstats.pl?config=foo.com)

is it normal for this message after running the command cp /usr/share/doc/awstats/examples /usr/local/awstats

```
root@rockinghamgateway:~# cp /usr/share/doc/awstats/examples /usr/local/awstats
cp: omitting directory `/usr/share/doc/awstats/examples'
```

TT

---

### Post by tommytomato on 2007-07-06
Ok got the cp thingy worked out

any one worked out what the log format is for mail ?

I had one for a tinysofa system

```
LogFormat= "%time2 %email %email_r %host %host_r %method %url %code %bytesd"
```

TT

---

### Post by ack.inc on 2010-02-14
Hi! I'm trying to set awstats up to read VSFTPD's logs. I've done every step mentioned here : [http://awstats.sourceforge.net/docs/...s_faq.html#FTP]("http://awstats.sourceforge.net/docs/awstats_faq.html#FTP"), except for the last statement that reads "Now you can use AWStats as usual (run the update process and read statistics)."

Now I'm flabbergasted...How do I "run the update process"? I don't have any directories that read "wwwroot" or "cgi-bin". In fact, I don't even have an "awstats.pl" script anywhere...

Please help!

---

### Post by Wingthor on 2010-03-25
Hi, 

Perhaps this is a bit OT, but has anyone manage to get the GeoIp plugin to work with Ubuntu 9.10? I just get "country unknown" an city unknown aswell.

Regards

---

### Post by pela020 on 2010-12-10
Does anybody know if it's possible to reset just the stats for Operating Systems and Browsers. I had the Logformat (4) wrong so I have a lot of unknown in thoose sections.

---

### Post by pot_roast on 2010-12-25
People also need to be aware that the awstats package for Ubuntu is now TWO YEARS out of date. 

from the awstats website: 

AWStats 6.9 released (Sun, 28 Dec 2008 

most current entry in the changelog:


awstats (6.7.dfsg-1ubuntu0.1) hardy-security; urgency=low

  * SECURITY UPDATE: XSS via quotes in the "config" parameter (CVE-2008-3714).
    - 1006_quote_xss.patch: upstream fixes, thanks to Florian Weimer.

 -- Kees Cook <kees@ubuntu.com>  Wed, 03 Dec 2008 11:22:38 -0800

---

you can still install it and then replace the awstats.pl file from the source package. this usually works ok. but just be aware that the ubuntu package is two years outdated....

actually it's worse than I thought... 
"Last stable version is 7.0 - 2010-12-05 23:54
Your Perl version must be at least 5.00503 (or higher) to use AWStats 6.x or higher. See ChangeLog to know what's new and for information on compatibility with previous versions.
See Features for current features."

---

