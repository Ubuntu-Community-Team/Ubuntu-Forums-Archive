---
title: "Snortd missing LBS information"
date: 2013-04-18
forum: New to Ubuntu
---

### Post by lewandowskid on 2013-04-18
Following this guide to install Snort on Ubuntu 12.04
[http://wiki.aanval.com/wiki/Community:Snort_2.9.2.3_Installation_Guide_for_Ubuntu_12.04,_with_Barnyard2,_Pulledpork,_and_Aanval](http://wiki.aanval.com/wiki/Community:Snort_2.9.2.3_Installation_Guide_for_Ubuntu_12.04,_with_Barnyard2,_Pulledpork,_and_Aanval)

When I get to #41

update-rc.d snortd defaults

I get the following message-

update-rc.d: warning: /etc/init.d/snortd missing LSB information
update-rc.d: see <http://wiki.debian.org/LSBInitScripts>


so when i try to restart the service I get the error:

Stopping snort: snort: no process found


If anyone can help me me with this it would be greatly appreciated.

---

### Post by dan.borchert on 2014-01-23
[**[COLOR=#000000]lewandowskid[/COLOR]**]("http://ubuntuforums.org/member.php?u=1812304"), I know it has been a while, but were you ever able to get past this? I'm at this exact spot and when I run "service snortd restart" I get "env: /etc/init.d/snortd: No such file or directory".

 I have yet to find one snort how-to where something breaks along the way and there's actually a resolution. If you know of a how-to that works with a specific build of linux please share. I can't tell you how many times I've reinstalled Ubuntu and snort in the last couple weeks. 

Thank you!

---

