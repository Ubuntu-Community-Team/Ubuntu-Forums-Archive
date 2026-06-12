---
title: "HOWTO: Setup A Headless Ubunutu CUPS Print-Server"
date: 2006-12-01
forum: Outdated Tutorials &amp; Tips
---

### Post by metalhippyrich on 2006-12-01
This explains how to set up a headless Ubuntu CUPS print-server which allows printing, and can be administered, over a network (without having to install the gui).  This is for Ubuntu 6.06 or 6.10.

I found the following a useful reference:
[FONT=Lucida Console]/usr/share/doc/cupsys/README.Debian.gz[/FONT]    
(only available after installing cupsys)


[SIZE=4]**Set Up The Server**[/SIZE]

**Install Ubuntu Server**
Install from the "Alternative" CD and select Server Installation

**Perform an update**

                [FONT=Lucida Console]apt-get update
                apt-get upgrade[/FONT]


**Install cupsys 1.2 and openssh-server**
These are available from the CD, so no need to add any repositories.  Eg;    

[FONT=Lucida Console]apt-get install cupsys openssh-server[/FONT]

You can now ssh in and could do the rest remotely.


**Allow remote administration of CUPS**
By default the cups server only allows local access and administration.  Edit the cups config file to allow us to browse the print-sever remotely.

In Ubuntu 6.10 with cupsys 1.2.4 edit: [FONT=Lucida Console]/etc/cups/cupsd.conf[/FONT]

In Ubuntu 6.06 with cupsys 1.2.2 edit: [FONT=Lucida Console]/etc/cups/cups.d/browse.conf[/FONT]
(This file is then included in [FONT=Lucida Console]cupsd.conf[/FONT])


Change:[FONT=Lucida Console] BrowseAllow @LOCAL[/FONT]
to:             [FONT=Lucida Console]BrowseAllow all[/FONT]

Similarly, in the blocks:

    [FONT=Lucida Console]<Location /> , <Location /admin>[/FONT] and [FONT=Lucida Console]<Location /admin/conf>[/FONT]

Change from:  [FONT=Lucida Console]Allow localhost[/FONT]
to:                               [FONT=Lucida Console]Allow all[/FONT]


**Set it to listen for connections from other machines**
In the config file: 

change: [FONT=Lucida Console]Listen localhost:631[/FONT]
to:            [FONT=Lucida Console]Listen 631[/FONT]




**Set CUPS so it doesn't try to use SSL (the default setting)**
  In the config file:

        [FONT=Lucida Console]/etc/cups/cupsd.conf[/FONT]

Add the line:

            [FONT=Lucida Console]DefaultEncryption Never[/FONT]

This should avoid the error:    [FONT=Lucida Console]426 - Upgrade Required[/FONT] when using the CUPS web interface.


**Allow CUPS to read the password file**
To do admin tasks remotely using the web interface, it will ask you for a password.  In order to check this password CUPS needs to be able to read the password shadow file.  To do this 'cupsys' needs to be a member of the group 'shadow'.

                [FONT=Lucida Console]adduser cupsys shadow[/FONT]


**Check the print-server's name is correctly known on the network**
On our network we have a server with a list of host names, which needed updating. On our system this meant using the IPCop web interface and  going to:  Services > Edit Hosts, and checking that the name corresponding to the print-server's IP address was correct.


You should now be able administer CUPS through the web interface from any machine on the network(!).  Use the print-server's name or IP address and port 631.  Eg:

                [FONT=Lucida Console]http://print-server-name.networkname:631[/FONT] or: [FONT=Lucida Console]192.168.0.20:631[/FONT]

You can then view jobs, add and manage printers etc.


**Install some good drivers**
Gutenprint (formerly known as gimp-print) includes a lot of recomended drivers, including the ones that we required for our Epson printers.

                [FONT=Lucida Console]apt-get install cupsys-driver-gutenprint[/FONT]

Now, when you go through the Add Printer process there will be far more drivers available, hopefully including the recomended ones which actually work.


**Add the Printers**
Connect the printers to the print-server and use the web interface to add them.


[SIZE=4]On The Client Workstations[/SIZE]

**Allow network printing**

Goto:        System > Administration > Printing
then goto:    Global Settings > Detect LAN Printers, and make sure it is ticked.

[I]
Note:    Doing the above changes a line in the config file to:[/I]

[FONT=Lucida Console]Browsing On[/FONT]

[I]In Ubuntu 6.10 with cupsys 1.2.4 this line appears directly in [FONT=Lucida Console]/etc/cups/cupsd.conf[/FONT]
In Ubuntu 6.06 with cupsys 1.2.2 this line is in the file [FONT=Lucida Console]/etc/cups/cups.d/browse.conf[/FONT], which is then included in cupsd.conf.
[/I]

**Specify the CUPS server**
To make the workstation pick up the printers published by our print server we have to tell it the CUPS server.
If it does not already exist, make a file:

                [FONT=Lucida Console]/etc/cups/client.conf[/FONT]

and add the line:

        [FONT=Lucida Console]ServerName 192.168.0.20[/FONT]

substituting your printserver's IP address or name.

[I]Notes:  We shouldn't really have to do this.  If the printers are added using the Ubuntu GUI Printing Admin window they simply appear on all the other machines, without us specifying a print server.  
However, we wanted to run a headless print server without installing the gui, so we add them through the CUPS web interface.  When we do this we have to specify the CUPS server.
The file client.conf may exist as a complete config file on some older versions (cupsys 1.1 ?).
[/I]

[SIZE=4]Acknowledgement[/SIZE]

Thanks to ethridgt for the post:
Howto: configure cups on Ubuntu Server from command line
[http://www.ubuntuforums.org/showthread.php?t=240282](http://www.ubuntuforums.org/showthread.php?t=240282)

---

### Post by altonbr on 2006-12-15
I found this tutorial confusing. misleading, out-dated with current CUPS packages and conf files and the formatting was HARD to read. Please work on touching up this tutorial by using [ QUOTE] and [/ QUOTE] tags and using more seperated headers.

The client.conf, cups.d/browse.conf & cups.d/ports.conf are in seperate files from cupsd.conf and I'm using CUPS 1.2.2

---

### Post by christhemonkey on 2007-02-16
This howto worked fine for me.

(until my server decided to choke and need a new powersupply before it finished installing gutenprint drivers (tested using standard drivers first, so it did work fine))

---

### Post by metalhippyrich on 2007-02-21
Sorry you found it confusing, altonbr.  I have now made it as clear as I possibly can.  It is definitely upto date.  
In  Ubuntu 6.06 [FONT="Lucida Console"]browse.conf[/FONT] & [FONT="Lucida Console"]ports.conf[/FONT] are indeed in seperate files, but in 6.10 it's all just in [FONT="Lucida Console"]cupsd.conf[/FONT], as the notes in the howto explain.

---

### Post by mbradlcu on 2007-02-25
Well I guess everyone's entitled to their opinion,,, I actually loved the tutorial, it worked perfectly, was direct, informative and to the point. I hope you continue to contribute and I look forward to your future posts!!

---

### Post by gimper48 on 2007-03-03
This tutorial worked wonderfully.  Thanks...

---

### Post by dmizer on 2007-03-15
> **metalhippyrich said:**
> 
**Specify the CUPS server**
To make the workstation pick up the printers published by our print server we have to tell it the CUPS server.
If it does not already exist, make a file:

                [FONT=Lucida Console]/etc/cups/client.conf[/FONT]

and add the line:

        [FONT=Lucida Console]ServerName 192.168.0.20[/FONT]

substituting your printserver's IP address or name.

that was my missing link.  had everything figured out except that.  thank you so much.

---

### Post by sinaen on 2007-03-27
I have a real hard time to find the correct uri with my printer

I got an own kernel and somehow i think i disabled the printer-ports. and now i cannot find where its enabled again. and i cant find where the right uri is

Examples:

    [http://hostname:631/ipp/](http://hostname:631/ipp/)
    [http://hostname:631/ipp/port1](http://hostname:631/ipp/port1)

    ipp://hostname/ipp/
    ipp://hostname/ipp/port1

    lpd://hostname/queue

    socket://hostname
    socket://hostname:9100

---

### Post by keithblack on 2007-05-23
I registered on ubuntu forums just so I could say that this worked perfect for me on my headless ubuntu 6.06 server.  Thanks, metalhippyrich :p

---

### Post by ginestre on 2007-05-24
I'm having a real hard time setting up printing, and I stumbled in to this thread. I wonder whether it contains the answer to my problem, but as I'm a nervous type I wanted to consult before banging my head against it. 

Here is the problem: I have a small home 4 PC network (win for the kids to play, ubuntu for work) and a brother laser printer, model hl1230. The printer is attached to a generic 'print server' magic box that always worked fine under win, and is attached at IP 192.168.0.2 All machines on the network can see the admin interface, so it connects. Installing the printer via CUPS and following as best I can all of the other instructions I can find on the forum, I can get CUPS to tell me it sees the printer, and to accept print jobs- but which remain permanently in the queue. I think CUPS isn't telling me the truth when it says it's installed everything. 

Should I be treating my magic box as if it were a server, ie another PC, in the terms of this HOWTO? I'm running Feisty

---

### Post by theblakeus on 2007-08-13
I have been trying for days to be able to access the gui remotely, and this howto worked flawlessly and only took a few moments to complete. Thank you!

---

### Post by joeqlaw on 2007-09-22
Hey wanted to say thanks for posting this howto - I was able to set up my network print server and start printing from other network computers in <30 minutes.  Thanks a TON!

---

### Post by dsl on 2007-11-17
Me too. It works. Thanks.

---

### Post by sinaen on 2007-11-21
do you know what was wrong, the guy i had bought the motherboard from had turned off paralell ports on the motherboard,
and now i have reinstalled the computer from a crash it works faster and more efficient...


it is better to put in the /etc/cups/cupsd.conf

Browseadress 192.168.0.255 or 192.168.0.*

and Allow is to be set 192.168.0.* or 192.168.0.255

to restrict it to the home network ip-addresses but you might already have found this one out,

because, Allow All, the outside of your firewall/gateway can get access if they know how to do it.
especially if you host a website or such then your server is routed to the outside.


> **sinaen said:**
> I have a real hard time to find the correct uri with my printer

I got an own kernel and somehow i think i disabled the printer-ports. and now i cannot find where its enabled again. and i cant find where the right uri is

Examples:

    [http://hostname:631/ipp/](http://hostname:631/ipp/)
    [http://hostname:631/ipp/port1](http://hostname:631/ipp/port1)

    ipp://hostname/ipp/
    ipp://hostname/ipp/port1

    lpd://hostname/queue

    socket://hostname
    socket://hostname:9100

---

### Post by mowgliee on 2007-11-27
hi, i'll throw my ring into the "i registered to say this howto is fine" hat.

its not very secure, but it works.

here's the problem i have:  one user has a local printer via para port.  if i enter ServerName IP into client.conf, the LAN shared printers appear fine for user but local printer vanishes.  if i remove that line, then the reverse.

how do i let the user's PC use both groups of printers?  it worked on FC4 but i have no intention of going back (ubuntu has that effect on people ... intelligent people).  thanx.

---

### Post by helpdeskdan on 2007-12-16
I'll add another thank you, but I also have a question.

When you do this, the client machine can print only to the server.  I have a client machine that I want to be able to print to more than one printer.  More importantly, I want it to be able to print to a separate network printer when the print server is off.   As it is, this is not possible - when the print server is down, you don't print anywhere.  

Many thanks, 
-Dan

---

### Post by mowgliee on 2008-01-06
actually i think my problem (see above a few posts) and the previous post's issue(s) are one in the same.

none of the logs have any error msgs.  all clients have the exact same config.  clients need to print to a local printer and to network printers via print server.  all hosts (clients, servers, etc) are on feisty.  here are the symptoms:

if i add a ServerName declaration to my client.conf file on the clients, then:
1. clients can only print to the network printers.  they can no longer print to local printers.
2. running lpstat -t or trying to print on clients hangs for about 10 sec before returning results or opening print dialog window.
3. result of lpstat -t are expected entries (ie same as results on cups server which is:
device for KM2300DL_Low_Res_bw: socket://192.168.1.101
KM2300DL_Low_Res_bw accepting requests since Fri 14 Dec 2007 03:38:23 PM CST

if i leave the declaration out (ie client.conf is empty), then:
1. at first, the client sees local printer and sees 2 entries for each network printer (see output below).
2. the URI for each entry is wrong (says ipp instead of socket - see output below).
3. local printing does not function (just fails to print but gives no error mesage except for the one in lpstat -t - see output below).
4. as time passes, network printer URI changes from ipp to dev/null (see output below).
5. lpstat -t does not hang; results are immediate.

what the heck is going on!???!!!!!????

and if the cups server is FC, no issues (with clients on feisty).  so it has to be some config on the feisty cups server?

initial lpstat -t results:
device for KM2300DL_Low_Res_bw: ipp://192.168.1.45:631/printers/KM2300DL_Low_Res_bw
KM2300DL_Low_Res_bw accepting requests since Sun 06 Jan 2008 09:41:27 PM CST

later lpstat -t results:
device for KM2430DL_High_Res_bw: ///dev/null
KM2300DL_Low_Res_bw accepting requests since Sun 06 Jan 2008 09:41:27 PM CST

local printer says (initially and later on): open print channel failed; will retry in 30 seconds...

help!

---

### Post by thefunnyman on 2008-08-02
Thanks so much for this HOWTO.  I could not get configuration via the web interface to work.  I would select the driver and click Add printer and the installation would hang on that screen.  I had to ultimately disable ssl ecryption on the web interface in order to get it to work right.

Thanks again,

thefunnyman

---

### Post by pandaking on 2008-09-03
Will this allow my Windows PC's on the network to connect to the printer?

Also, can it then be easily configured as a file server as well as printer which windows PC's can access.

I am fed up of having a Windows XP as a file/print server and all the muggins that goes with it...

---

### Post by jamsaver on 2008-09-20
hi,
First: thank you for this great tutorial, although I had alot of problems during my installation I figured things out quite fast thanks to your tutorial...
Secondly: I have a Canon Pixma IX4000 printer and a ubuntu headless server configured exactly like in this tutorial.I added my printer to cups I get to print a test page and looks ok...But the only problem is I can't get to print from my clients (1 macbook and 1 powerbook running OSX 10.5).When I try to add the printer from control panel it adds my printer with a generic postscript driver and than when I try to print something it stays up for couple of seconds and pauses itself...
I've tried IPP or LPD nothing seems to work..
this is what I see on the accses log
localhost - - [20/Sep/2008:19:37:07 -0500] "POST / HTTP/1.1" 200 107 Get-Subscriptions client-error-not-found
I googled the error but couldn't find the right solution...
I'd definetly appriciate some help 
thanks

---

### Post by dmizer on 2008-09-21
Use "Connect to a printer on the internet" and enter this as the url:

[noparse]http://server.ip.address.here:631/printers/printername[/noparse]
(you'll have to replace "server.ip.address.here" with your actual server ip address, and "printername" with your actual printer name in CUPS)

You will need the Windows printer drivers handy.

---

### Post by QuimNuss on 2008-10-28
I've followed the HOWTO, everything went smooth and I have web access.

The problem is I can't get it to work, when I print anything it goes to the jobs list and after a while it says it has been completed, but nothing happened.

I've tried printing from a client and from the server host with 
```
$ sudo cat file.txt | lp 
request id is pixma1500-15 (1 file(s))
```

but the result is same as above.

What could I do to "debug" a little bit to see what's going on?
There wasn't the appropiate driver (Canon Pixma iP1500) so I chose first another Canon pixma and afterwards a BJC, could that be the problem?

I'm total newbie so... tell me any information that would be useful if you're to help me :)

thanks!

---

### Post by rasheid2kx on 2008-11-27
im using ubuntu server 8.04
My cups hangs when i try to install a printer. more specifically after i select my gunten driver... 

after reading here:
[http://www.cups.org/str.php?L2892+P0+S-2+C0+I0+E0+M20+Q](http://www.cups.org/str.php?L2892+P0+S-2+C0+I0+E0+M20+Q)

i downloaded a patch file str2892-1.3.patch 
from here:[http://www.cups.org/str.php?L2892](http://www.cups.org/str.php?L2892)

what is the proceedure to using the patch 
i cd to the downloaded dir and when i run patch < str2892-1.3.patch

i get 

```
can't find file to patch at input line 5
Perhaps you should have used the -p or --strip option?
The text leading up to this was:
--------------------------
|Index: scheduler/client.c
|===================================================================
|--- scheduler/client.c	(revision 7820)
|+++ scheduler/client.c	(working copy)
--------------------------
File to patch: 
```


what is the correct format for patching the cups file

help

---

### Post by rasheid2kx on 2008-12-04
!!!!!!!!!Bump!!!!!!!!!!!! !!!!!!!!!Bump!!!!!!!!!!!!

---

### Post by thefunnyman on 2008-12-04
I don't know much about installing the patch file, but I can tell you that I had VERY similar problems until I disabled encryption when using the web interface.  It's an option in the cups config file.  

Don't forget to execute 
```

sudo /etc/init.d/cupsys restart

```
after you're finished making changes.

After I disabled encryption, I could get to cups using 
```

http://server:631

```
instead of 
```

https://server:631

```
And all was good in my printer server world.

And to remind the poster above you, log files for cups reside in
```

/var/log/cups

```

Post some of your log output indicating an error and maybe someone can help you out with your problems.

Hope this helps,

thefunnyman

---

### Post by damas on 2008-12-17
Hi all!

This guide doesn´t work for me, I can print localy on the server but none of my clients (XP and Vista) can print proberly.

I can discover the printer in the network but windows printer que tells me "access denied, ..."

How can i configure my cupsd.conf to allow the access? (I guess its a authentication problem)

Is there any option, to disable all kind of security? I mean i don´t have to worry because i only have a Local network!

Here´s my cupsd.conf:

[HTML]#
#
#   Sample configuration file for the Common UNIX Printing System (CUPS)
#   scheduler.  See "man cupsd.conf" for a complete description of this
#   file.
#

# Log general information in error_log - change "info" to "debug" for
# troubleshooting...
LogLevel warning

# Administrator user group...
SystemGroup lpadmin


# Only listen for connections from the local machine.
Listen 631
Listen /var/run/cups/cups.sock

# Show shared printers on the local network.
Browsing On
BrowseOrder allow,deny
BrowseAllow all
BrowseAddress @LOCAL

# Default authentication type, when authentication is required...
DefaultAuthType none

# Restrict access to the server...
<Location />
  Order allow,deny
Allow all
</Location>

# Restrict access to the admin pages...
<Location /admin>
  Order allow,deny
Allow all
</Location>

# Restrict access to configuration files...
<Location /admin/conf>
  AuthType None
  Require user @SYSTEM
  Order allow,deny
Allow all
</Location>

# Set the default printer/job policies...
<Policy default>
  # Job-related operations must be done by the owner or an administrator...
  <Limit Send-Document Send-URI Hold-Job Release-Job Restart-Job Purge-Jobs Set-Job-Attributes Create-Job-Subscription Renew-Subscription Cancel-Subscription Get-Notifications Reprocess-Job Cancel-Current-Job Suspend-Current-Job Resume-Job CUPS-Move-Job>
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>

  # All administration operations require an administrator to authenticate...
  <Limit CUPS-Add-Modify-Printer CUPS-Delete-Printer CUPS-Add-Modify-Class CUPS-Delete-Class CUPS-Set-Default>
    AuthType None
    Require user @SYSTEM
    Order deny,allow
	Allow all
  </Limit>

  # All printer operations require a printer operator to authenticate...
  <Limit Pause-Printer Resume-Printer Enable-Printer Disable-Printer Pause-Printer-After-Current-Job Hold-New-Jobs Release-Held-New-Jobs Deactivate-Printer Activate-Printer Restart-Printer Shutdown-Printer Startup-Printer Promote-Job Schedule-Job-After CUPS-Accept-Jobs CUPS-Reject-Jobs>
    AuthType None
    Require user @SYSTEM
    Order deny,allow
  </Limit>

  # Only the owner or an administrator can cancel or authenticate a job...
  <Limit Cancel-Job CUPS-Authenticate-Job>
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>

  <Limit All>
    Order deny,allow
  </Limit>
</Policy>
DefaultEncryption Never
#
#[/HTML]

Thankfull for any kind of answer or hints!

/Damas

---

### Post by tazizhere on 2009-11-13
It's November 2009 and this worked for me.  Although, little change but if you've made it this far in your installation then you can figure it out.

---

### Post by ZizzerZuz on 2010-05-16
Now May 2010 and this is the best how to to configure a headless print server?

It's close, but it's not quit right any more.

I can't be the only noob trying to work this out.

Zizzer

---

### Post by Crick on 2010-08-12
> **ZizzerZuz said:**
> Now May 2010 and this is the best how to to configure a headless print server?

It's close, but it's not quit right any more.

I can't be the only noob trying to work this out.

Zizzer
Bump... This doesn't appear to work any more (Hardy) for me either.

---

### Post by rlecheese@hotmail.com on 2010-08-16
Bump... I cant get the web interface either but here are a few differences I have sorted. Perhaps there is someone who can finish it up for us?

the cups restart is now
```
sudo /etc/init.d/cups restart
```rather than cupsys

the lines:
```
Allow localhost
```no longer exist so I would presume you add the line
```
Allow All
```between the location quotes where appropriate eg
```
<Location />
  Order allow,deny
Allow All
</Location>

```Also ```
sudo apt-get install cupsys cupsys-client
``` doesnt seem to generate a cups user that can be added to the shadow group??? Or did I miss something

Certainly listing all the users with grep cup didnt turn anything up
(Neither did manually looking at every user in turn)

Perhaps it was something not obviously "cups"

Who knows?

And perhaps this isnt even the thing stopping me from remotely accessing the web gui, but how would you know unless you had a working version to test against.

I wish ```
man cupsd.conf
``` made these issues clear to me but a list of commands does not an instruction book make.

Is there someone who knows what else is missing from the application of this howto to the latest version?

---

### Post by rlecheese@hotmail.com on 2010-08-16
Ok editing the cupsd.conf file line
```
LogLevel warn
```to read
```
LogLevel debug
``` 
and then back at the terminal restarting cups and then
```
sudo nano/var/log/cups/error_log
```
Is a useful starting point.
I will return shortly with answers (or more questions)

---

### Post by rlecheese@hotmail.com on 2010-08-16
Yup: use of error logs solved my problem (I had too many listen to port 631 lines)

The instructions as writen should get you to the web interface when including all the ammendments above.

---

### Post by finite9 on 2010-11-15
according to the cups manual there is a very simple way to get this working on Maverick on local subnet...

```
sudo apt-get install cups
sudo cupsctl --share-printers
sudo cupsctl 'BrowseLocalProtocols="cups dnssd lpd smb"'
sudo useradd cupsys
sudo usermod -G shadow
```

Then edit the config file:

```
sudo vi /etc/cups/cupsd.conf
```

Add the "Allow @LOCAL" to the admin and admin/conf stanzas as below:

```
<Location /admin>
  Order allow,deny
  Allow @LOCAL
</Location>
<Location /admin/conf>
  AuthType Default
  Require user @SYSTEM
  Order allow,deny
  Allow @LOCAL
</Location>
```

And everywhere it says "Require user @SYSTEM" in the config file, change to "Require user @SYSTEM cupsys", otherwise you get 403 Forbidden errors.  When prompted for a login, you can then enter your cupsys user credentials.

Then restart CUPS:

```
sudo service cups restart
```

Then you can browse to server:631 and administer CUPS.

---

### Post by upstatelabs on 2011-03-17
> **damas said:**
> Hi all!

This guide doesn´t work for me, I can print localy on the server but none of my clients (XP and Vista) can print proberly.

I can discover the printer in the network but windows printer que tells me &quot;access denied, ...&quot;

How can i configure my cupsd.conf to allow the access? (I guess its a authentication problem)

Is there any option, to disable all kind of security? I mean i don´t have to worry because i only have a Local network!

.
.
.

Thankfull for any kind of answer or hints!

/Damas

IS there anyone who has any suggestions for this? I have the exact same problem.  I have access to the web interface, and my windows clients can see the printers.  But I can't make connections:
"Access denied, unable to connect"
So some permission is wrong, but how to find out which?

Thanks!

---

### Post by graphius on 2011-05-03
I can't even see the web interface. I am at a bit of a loss...:confused:

the last part of my error log
> D [03/May/2011:09:28:52 -0700] Report: printers-implicit=0
D [03/May/2011:09:28:52 -0700] Report: stringpool-string-count=124
D [03/May/2011:09:28:52 -0700] Report: stringpool-alloc-bytes=3984
D [03/May/2011:09:28:52 -0700] Report: stringpool-total-bytes=3024
I [03/May/2011:09:30:09 -0700] Scheduler shutting down normally.
D [03/May/2011:09:30:09 -0700] Discarding unused server-stopped event...
I [03/May/2011:09:30:09 -0700] Saving job cache file "/var/cache/cups/job.cache"...
I [03/May/2011:09:30:09 -0700] Listening to 0.0.0.0:631 (IPv4)
I [03/May/2011:09:30:09 -0700] Listening to :::631 (IPv6)
E [03/May/2011:09:30:10 -0700] Hostname lookup for "All" failed!
E [03/May/2011:09:30:10 -0700] Bad BrowseAddress All at line 28.
I [03/May/2011:09:30:10 -0700] Remote access is enabled.
D [03/May/2011:09:30:10 -0700] Added auto ServerAlias ubuntu-nas
I [03/May/2011:09:30:10 -0700] Loaded configuration file "/etc/cups/cupsd.conf"
I [03/May/2011:09:30:10 -0700] Using default TempDir of /var/spool/cups/tmp...
I [03/May/2011:09:30:10 -0700] Configured for up to 100 clients.
I [03/May/2011:09:30:10 -0700] Allowing up to 100 client connections per host.
I [03/May/2011:09:30:10 -0700] Using policy "default" as the default!
I [03/May/2011:09:30:10 -0700] Full reload is required.
I [03/May/2011:09:30:10 -0700] Loaded MIME database from "/usr/share/cups/mime" and "/etc/cups": 37 types, 73 filters...
I [03/May/2011:09:30:10 -0700] Loading job cache file "/var/cache/cups/job.cache"...
I [03/May/2011:09:30:10 -0700] Full reload complete.
I [03/May/2011:09:30:10 -0700] Cleaning out old temporary files in "/var/spool/cups/tmp"...
I [03/May/2011:09:30:10 -0700] Listening to 0.0.0.0:631 on fd 6...
I [03/May/2011:09:30:10 -0700] Listening to :::631 on fd 7...
I [03/May/2011:09:30:10 -0700] Resuming new connection processing...
D [03/May/2011:09:30:10 -0700] Discarding unused server-started event...
D [03/May/2011:09:30:11 -0700] Report: clients=0
D [03/May/2011:09:30:11 -0700] Report: jobs=0
D [03/May/2011:09:30:11 -0700] Report: jobs-active=0
D [03/May/2011:09:30:11 -0700] Report: printers=0
D [03/May/2011:09:30:11 -0700] Report: printers-implicit=0
D [03/May/2011:09:30:11 -0700] Report: stringpool-string-count=124
D [03/May/2011:09:30:11 -0700] Report: stringpool-alloc-bytes=3984
D [03/May/2011:09:30:11 -0700] Report: stringpool-total-bytes=3024


---

