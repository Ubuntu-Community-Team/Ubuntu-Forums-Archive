---
title: "[SOLVED] Snort/Base Setup Issue"
date: 2008-11-24
forum: New to Ubuntu
---

### Post by scribbles on 2008-11-24
Following bodhi.zazen's [Intrusion Detection Guide]("http://ubuntuforums.org/showthread.php?t=919472"), I'm on the second code snippet of post #4. I'm using snort-2.8.3.1 while the guide has snort-2.8.3. The guide says to run ```
cp -R /usr/src/snort-2.8.3/doc/signatures .
``` but that dir doesn't exist in this version and I cannot seem to find where they might've moved it or the files that command was supposed to move.

Can anyone shed some light on this issue? :-k

---

### Post by Elfy on 2008-11-24
It looks to me like the command is there to files into the directory you can't find. It should be created by the command. You could change the name to suit snort-2.8.3.1 but I've not followed the whole thing to see what else might need to be done.

---

### Post by scribbles on 2008-11-24
yea I've changed it to snort-2.8.3.1 but that signatures dir is not there. It's supposed to copy those files to /var/www/base. Think its safe to move on without them? :)

---

### Post by Elfy on 2008-11-24
Absolutely no idea I'm afraid - I can ask the man himself though. No idea when though.

But if the files not there I would have thought not.

---

### Post by scribbles on 2008-11-24
That'd be great! So I was browsing the FAQ over at the BASE homepage and ran across this quote > The Snort database plug-in only logs packet information into the database when an alert is triggered by a rule (signature). If you look further up in the guide you're shown to copy a set of rules to ../rules. If a rule is a signature, did bodhi.zazen mean /rules or am I just making a longshot here?

---

### Post by bodhi.zazen on 2008-11-24
There are two things, the names are similar ... but they are separate.

First, snort captures all packets coming to your box. It checks the packet against a set of rules. If there is a concerning packet it logs it to mysql and is displayed in base.

for this you need a set of rules from snort

[http://www.snort.org/pub-bin/downloads.cgi](http://www.snort.org/pub-bin/downloads.cgi)

If you followed my how-to, your rules are in /usr/etc/snort-2.8.3/rules

Copy those rules to /etc/snort/rules

This is all you *need* to do.

Second, within the rule set there is documentation. Documentation is also available on line, so there is no *need* to install anything further locally.

The documentation should also be in the snort rules and is in 

/usr/src/snort-2.8.3/doc/signatures/

These are a whole bunch of *.txt files .... These are not rules and do not affect snort, they are explanations of the alerts. If you go to base and log in -> then go to an alert.

Within base you will see a number of links to an explanation of the alert. The number of links varies with each rule.

[[IMG]http://bodhizazen.net/img/IDS/base_2_sm.JPG[/IMG]]("http://bodhizazen.net/img/IDS/base_2.JPG")
<click for a larger image>


Look on the left , on the line with "robots.txt", you will see "nessus" "local" "snort"

Click on a link, and you will see an explanation. 

Here is the link for "nessus" for "robots.txt

[http://www.nessus.org/plugins/index.php?view=single&id=10302](http://www.nessus.org/plugins/index.php?view=single&id=10302)

If you do nothing, there will be an error if you select "local" (as you have not installed any local explanations of the alerts). If, however, you copy /usr/src/snort-2.8.3/doc/signatures to /var/www/base/signatures , you will have explanations for alerts on your local web server (and will not need to go to the nessus or snort web site).

If you do not have the signatures, download the "current" snort rule set.

---

### Post by scribbles on 2008-11-24
Thanks bodhi.zazen! Your guides have helped me a lot thus far and I really appreciate all of your efforts. So the issue stems from me using the bleeding rules and not extracting the snort current rules which I imagine has the /doc/signature in it.... 

Is there any harm to me going ahead and extracting snort current rules with bleeding.rules in the directory already?

---

### Post by bodhi.zazen on 2008-11-24
> **scribbles said:**
> Thanks bodhi.zazen! Your guides have helped me a lot thus far and I really appreciate all of your efforts. So the issue stems from me using the bleeding rules and not extracting the snort current rules which I imagine has the /doc/signature in it.... 

Is there any harm to me going ahead and extracting snort current rules with bleeding.rules in the directory already?

Not at all. You can have multiple rule sets, and if you really get into it you can try out the oinkmaster.

---

### Post by scribbles on 2008-11-24
I just extracted the rules into /etc/snort/ and there's quite a bit of /precompiled/ dirs, do I have to recompile to integrate this?

---

### Post by bodhi.zazen on 2008-11-24
LOL

I just move the rules over, perhaps I am doing something wrong, I do not know.

---

### Post by scribbles on 2008-11-24
BASE is up and running! I did notice a message during the setup stating: > In order to support Alert purging (the selective ability to permanently delete alerts from the database) and DNS/whois lookup caching, the DB user "snort" must have the DELETE and UPDATE privilege on the database "snort@localhost"  Is this something I should be concerned with?

SSL was also mentioned as a possibility but that blog has 404'd, is there a guide available for logging into BASE securely?

BASE still doesn't show any data in it (Sensors/Total: 0 / 0). I thought maybe snort needed to be restarted and ran ```
/etc/init.d/snort restart
``` and got this ```
root@localhost:/etc/init.d# /etc/init.d/snort restart
/etc/init.d/snort: line 129: /usr/local/bin/snort: No such file or directory
root@localhost:/etc/init.d# No protocol specified

(zenity:27058): Gtk-WARNING **: cannot open display: :0.0

``` I moved your init script and doublechecked that /etc/init.d/snort was indeed the script and followed the chmod commands but it doesn't seem to work. Hopefully fixing this is all thats needed to get data showing in BASE. 

I apologize for the profuse questioning, I'm excited to get this up and running... THANKS!

---

### Post by scribbles on 2008-11-24
```
SNORT='/usr/local/bin/snort -c /etc/snort/snort.conf -u snort -g snort -D'

``` That's line 129 I believe in the script. I checked /usr/local/bin/snort and there's nothing there but another program I installed a few weeks ago!

Woops. Line 129 is ```
  $SNORT -i "$IFACE" &
``` Looks like this links back to the /usr/local/bin/snort line which needs to be corrected. Where should it be pointed?

---

### Post by bodhi.zazen on 2008-11-25
Where did you install snort ???

---

### Post by scribbles on 2008-11-25
I followed the steps word for word. If I just run snort via konsole it says command not found, so I'm not even convinced it compiled correctly... There were some recursive directory errors at the tail end of compiling but didn't think it was anything major...

---

### Post by scribbles on 2008-11-26
I deleted the /usr/src snort files and downloaded 2.8.3 the exact version the guide uses and got the same errors during make and make install for both versions: ```
In function &#8216;open&#8217;,
    inlined from &#8216;server_stats_save&#8217; at server_stats.c:349:
/usr/include/bits/fcntl2.h:51: error: call to &#8216;__open_missing_mode&#8217; declared wi$
make[5]: *** [server_stats.o] Error 1
make[5]: Leaving directory `/usr/src/snort-2.8.3.1/src/preprocessors/flow/ports$
make[4]: *** [all-recursive] Error 1
make[4]: Leaving directory `/usr/src/snort-2.8.3.1/src/preprocessors/flow'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/usr/src/snort-2.8.3.1/src/preprocessors'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/usr/src/snort-2.8.3.1/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/usr/src/snort-2.8.3.1'
make: *** [all] Error 2

In function &#8216;open&#8217;,
    inlined from &#8216;server_stats_save&#8217; at server_stats.c:349:
/usr/include/bits/fcntl2.h:51: error: call to &#8216;__open_missing_mode&#8217; declared wi$
make[5]: *** [server_stats.o] Error 1
make[5]: Leaving directory `/usr/src/snort-2.8.3/src/preprocessors/flow/portsca$
make[4]: *** [all-recursive] Error 1
make[4]: Leaving directory `/usr/src/snort-2.8.3/src/preprocessors/flow'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/usr/src/snort-2.8.3/src/preprocessors'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/usr/src/snort-2.8.3/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/usr/src/snort-2.8.3'
make: *** [all] Error 2

``` I figured I've tried everything and snort still seems to not want to work. Big deal, delete and I'll follow the snort-mysql repo's package guide and see if I can get that to work. I'd installed it before only to delete it and come back to bodhi's guide to try again. During the install of that pkg and its dep's when the configuration screen comes up it immediately says there's been an error and I have to run some command to setup snort again. This is the blue/red screen that comes up and normally asks you what its looking for and runs you through the basic config questions. I can't get the screen back up as now apt-get says snort-mysql is the latest version. I'm at my wits end with why snort refuses to run in any way shape or form and just don't understand it. Did I not clearly remove previous attempts? I've followed guides perfectly.... any ideas from anyone?

---

### Post by scribbles on 2008-11-26
So after deleting the snort files in /usr/src from another failed compile attempt, I installed snort-mysql like the post above says. I sat down today and adept was showing it needed to do some updates so  ran it and at the end of configuring it errored showing snort-mysql and some errors about rc.d and its init script. After it errored a window popped up from Bodhi's init script saying snort is not running which is the first time I've seen anything from that script pop up. So I ran ```
apt-get remove snort-mysql
``` and got this ```
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up snort-mysql (2.7.0-19ubuntu1) ...
update-rc.d: /etc/init.d/snort: file does not exist
dpkg: error processing snort-mysql (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 snort-mysql
E: Sub-process /usr/bin/dpkg returned an error code (1)

``` 
I'm at a total loss. I really just would like all of this removed so I can start over with the snort-mysql pkg and move on. I already have mysql and base working together, I just need snort to work...

---

### Post by bodhi.zazen on 2008-11-26
hard to know exactly wher you are and what you have done, but it sounds as if you are starting to mix versions of snort, both from source and from the repos :(

I think you can resolve that latest error with :

```
sudo touch /etc/init.d/snort
```

then re-run your apt-get.

I would then remove everything snort related and start anew.

---

### Post by scribbles on 2008-11-26
I ran the touch command and got everything removed. I then followed the guide and followed Etlaesium's instructions on post #25 in the guide and everything seems to have gone without any errors. When I use the script to restart snort I get ```
root@stephen-desktop:/usr/src/snort-2.8.3.1# /etc/init.d/snort restart
root@stephen-desktop:/usr/src/snort-2.8.3.1# No protocol specified

(zenity:22928): Gtk-WARNING **: cannot open display: :0.0


```But if I ps -A | grep snort its now running which it wasn't before! Btw, zenity is installed and is the latest. 

I logged into BASE and I see > Sensors/Total: 0 / 1  which before had said 0 / 0. After about 15 mins theres still no traffic data in BASE which I'm concerned about, I didn't have any issues setting up the mysql db...

---

### Post by scribbles on 2008-11-26
Success!

3 of the Alerts are sourced from my desktop. Should the home_net be set at my desktop IP instead of 192.168.0.0/16?

---

### Post by bodhi.zazen on 2008-11-26
W00t !! :guitar:

---

