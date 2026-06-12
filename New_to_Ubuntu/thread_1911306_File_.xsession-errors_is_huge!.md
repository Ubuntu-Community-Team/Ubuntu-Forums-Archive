---
title: "File .xsession-errors is huge!"
date: 2012-01-18
forum: New to Ubuntu
---

### Post by Judodan on 2012-01-18
I have a fit PC running Ubuntu 10.04 LTS.  I use it primarily as a subversion server and to test web based stuff.  It's a headless box that I usually access (when I need to) by VNC.

Suddenly the subversion server was reporting no disk space.  I checked to find that the .xsession-errors file was 110GB large!

I used head and tail to get the first and last 100k lines.  After about 13000 lines of other stuff, the log started filling up with this:


08/01/2012 12:27:21 PM Authentication deferred - ignoring client message
08/01/2012 12:27:21 PM Authentication deferred - ignoring client message
08/01/2012 12:27:21 PM Authentication deferred - ignoring client message
08/01/2012 12:27:21 PM Authentication deferred - ignoring client message
08/01/2012 12:27:21 PM Authentication deferred - ignoring client message
08/01/2012 12:27:21 PM Authentication deferred - ignoring client message

this apparently kept running until the disk was full... the last lines are:

11/01/2012 07:38:23 AM Authentication deferred - ignoring client message
11/01/2012 07:38:23 AM Authentication deferred - ignoring client message
11/01/2012 07:38:23 AM Authentication deferred - ignoring client message
11/01/2012 07:38:23 AM Authentication deferred - ignoring client message
11/01/2012 07:38:23 AM Authentication deferred - ignoring client message
11/01/2012 07:38:23 AM Authentication deferred - ignoring client message
11/01/2012 07:38:23 AM Authentication deferred - ignoring client message
11/01/2012 07:38:23 AM Authentication deferred - ignoring client message
11/01/2012 07:38:23 AM Authentic

A quick net search seems to indicate it might have something to do with something called vino.  So I was wondering if anybody knew what was causing this (and why it's outputting 13000+ lines per second to the log?) and how to resolve?

It doesn't seem to be doing it again (and the subversion server is working again) so I can check in a couple days to see if it happens again, but I'd like to know, if I can, what caused it.

Any help appreciated!  Thanks!

---

### Post by jerrrys on 2012-01-20
A bug?

[https://bugs.launchpad.net/ubuntu/+source/nspluginwrapper/+bug/498911](https://bugs.launchpad.net/ubuntu/+source/nspluginwrapper/+bug/498911)

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=limit+xsession-errors&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=limit+xsession-errors&sa=Search&cof=FORID:9)

---

### Post by Judodan on 2012-01-20
I'm sure it's a bug of some sort (and maybe I should do something to limit the size of the error file, I'm looking at that google search you linked and there's some info on that, thanks), but none of the reported bugs from your link (or my searches) detailed the repeating error message I'm seeing.

---

### Post by Mosome on 2012-01-26
I also have this problem and am looking to resolve.  It's over 100M in size, with a lot of warnings.  I don't mind the errors, but warnings are unsolvable.

I've tried toying around with /etc/rsyslog.d/50-default.conf and disabled the bottom part where it was commented that it could bog down the system.  Way too much logging going on for a fresh and first install however.

Even with this disabled though, it still records to this file.  Is there some conf somewhere where this could be turned from warnings to errors only?

---

### Post by heheman3000 on 2012-08-05
I had this problem on my Gentoo system, except it was writing to .gnomerc-errors. Since I had a raid array, 44G was blown away in a few minutes.

This seems to be a problem with the window or session manager allowing infinite log output from X apps gone awry. Googling it shows that many different apps can cause this problem.

Maybe the bug should be reported to the GNOME team?

---

### Post by happbd on 2012-08-18
have the same issue - 

it looks like the vnc server is under a DOS attack as the log is filled with invalid login attempts.  I'm changing the VNC port to something other than 5900 to see if this helps.  See the link below to change the default port

[http://davestechsupport.com/blog/2009/06/14/howto-change-vncs-listen-port-in-ubuntu/](http://davestechsupport.com/blog/2009/06/14/howto-change-vncs-listen-port-in-ubuntu/)

---

### Post by Judodan on 2012-10-14
I had deleted the file (and rebooted), which solved the problem.  However, it kept cropping up intermittently.  It's kind of annoying to have to SSH in, remove the file, then rebloot.

So I changed the xsession logger to write to /dev/null and that was no problem.  However, it's now filling a logfile in the .vnc directory with the SAME LINES!

It's a HUGE amount, over 13k lines per second.  Searching the net leaves NO CLUE to how this happens.

---

### Post by everlong on 2012-11-28
Happened to me too, using 12.10. The file **.xsession-errors.old** now clocks in at 851.4 GB!

---

### Post by keyneom on 2013-02-13
I was taking a look at things and it appears to me that this is the result of a brute force attack. Looking back in the logs you should be able to find quite a few failed and logged attempts to connect to and authenticate to the VNC server. For me I found the following Ip Addresses were the sources:

202.101.174.246
75-150-133-209-Philadelphia.hfc.comcastbusiness.net
177.212-55-8.static.clientes.euskaltel.es
vps-6217.united-hoster.de
tinsoda.com

The first one originates from in the middle of China somewhere. I assume the others are bots being used to carry out the attack. The attack first started 2 days ago for me. After a number of failed attempts to authenticate it looks like the VNC server started to block the attempts to authenticate outright. Only logging the message "Authentication deferred - ignoring client message". If you want to see where the original attempts were made from you can just run the following command and use ctrl+c as soon as you see the log get to the "Authentication deferred" message.

cat ~/.xsession-errors | grep -P "[0-9][0-9]/[0-9][0-9]/[0-9][0-9][0-9][0-9]"

This just catches any lines that begin with a date (which all the logged messages we are interested in do) and prints them out. Pipe them to a file if you would prefer for later analysis.

As an aside I don't really consider this to be a bug and don't think deleting and rebooting ought to be a wise workaround. Maybe set a rule in iptables to only allow VNC connections from local IP addresses, or something similar in the corporate firewall, etc.

Best of luck in keeping your servers from getting hacked! :)

p.s. It might be interesting to see what other logs show happening at the times the original attacks occurred.

---

### Post by Marksist on 2013-03-13
My attack was from 

    114.203.87.201
    222.234.0.100
    222.234.0.119
    59.15.58.187
    static.211-232-57-18.nexg.net

I am pretty sure that sending the file to null would be a bad choice as it will allow the attacks to go unabated. I was getting ~75k *Authentication deferred - ignoring client* messages messages per second. With a weak password, I imagine that the attacker could install another drone client to run in the background.

---

### Post by Peterlorre on 2013-05-27
Hi, I'm pretty new to ubuntu and am having the same problem as is described here. Could someone point me to a good resource for protecting myself from this sort of thing a little bit better? Also, I really need to figure out a solution to this problem- my HD is filling up really fast, even after piping .xsession-errors to /dev/null (the deleted files don't clear from disk unless I manually remove them). 

Sorry if this is obvious to everyone else- I guess I've never had to manage my internet security this directly before.

---

### Post by deadflowr on 2013-05-27
> **Peterlorre said:**
> Hi, I'm pretty new to ubuntu and am having the same problem as is described here. Could someone point me to a good resource for protecting myself from this sort of thing a little bit better? Also, I really need to figure out a solution to this problem- my HD is filling up really fast, even after piping .xsession-errors to /dev/null (the deleted files don't clear from disk unless I manually remove them). 

Sorry if this is obvious to everyone else- I guess I've never had to manage my internet security this directly before.

Post a snapshot of maybe ten lines of the file that are recurring over and over.

---

### Post by Peterlorre on 2013-05-28
Hmmm- altered the line that was redirecting .xsession-errors to dev/null and restarted, and now I'm not getting the error- so it could have been something about my last session, or maybe the attack has stopped (if that's what it was). If I see the problem again, I'll post error data as advised.

---

### Post by Peterlorre on 2013-05-29
Looking around a bit more, I think that changing the listening port away from the default setting in etc/ssh/sshd_config was what ultimately fixed this problem.

---

