---
title: "logs for snort and base dont show"
date: 2012-09-30
forum: New to Ubuntu
---

### Post by isa.dsouza on 2012-09-30
At the outset I would like to state that as recommended I did try starting this thread in the Security forum. But was restricted, but anyway that is not the point.

I tried setting up the IDS via bodhi zazen post, then did my own R&D.  It turns out I am facing a problem with the log file for snort. 

When I installed snort it was snort pgsl that was installed as per the post by bodhi.

I installed it this way.

sudo apt-get install postgresql
sudo apt-get install -y apache2 php5 php-pear php5-gd php5-adodb php5-pgsql libphp-adodb snort-pgsql

2 separate commands.

Now then the error I see is:

ERROR: log_tcpdump: Failed to open log file "/var/log/snort/tcpdump.log.1348993619": No such file or directory
Fatal Error, Quitting..

when I type sudo snort -c /etc/snort/snort.conf

But...

When I try sudo snort -c /etc/snort/snort.conf  -T
as per bodhis' post things are alright.

My question is why does the command not work without the -T at the end?

Also I edited "ipvar HOME_NET any" as when I used the search function it did not show "var HOME_NET any" I even looked everywhere in snort.conf and it is not there.  This means the snort config file is pre-configured for ipv6?

I must admit that I have not set up the Snort Rules and Oinkmaster yet. But this should not be linked to getting a log file from snort with present rules.

Another thing is that there is a pgsl folder under /var/log/pgsl but the folder rquired for snort log  /var/log/snort is not there.

That is what the error ideally states.  Should I make the folder and in the first place isnt it already supposed to be there or is snort supposed to log to /var/log/pgsl.

I am also checking the snort manual. But any directions and guidance will surely help.

---

### Post by isa.dsouza on 2012-10-30
I have removed snort, postgresql, php and apache. I can still see some folders i /etc folder for postgresql. How can I get rid of it?

I have removed the applications from synaptic and selected mark for complete removal.

---

### Post by isa.dsouza on 2012-11-11
Seems to me that the tutorial I followed did not help much. There is some intrusion as firefox really does not work like it should.

I posted in this thread as well about problems with logging in to my ISP on their login page.

[http://ubuntuforums.org/showthread.php?t=1711500](http://ubuntuforums.org/showthread.php?t=1711500)

Firefox doesnt open the last session on reload inspite of selecting it. Freezes a lot as well. Clam AV doesnt pick up any intrusion except for cache.

---

