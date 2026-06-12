---
title: "Postfix problem"
date: 2013-08-27
forum: New to Ubuntu
---

### Post by paul31 on 2013-08-27
Hi
I'm very new to linux so would be greatful if someone could help me resolve this Postfix problem.

I'm trying to configure Postfix to just send externally (not receive). I'm able to send the messages to postfix however they are stuck in the deferred mail queue.

When checking with pfqueue, the status of each mail is either "No route to host" or "Connection timed out" 
I've not included a relay host as was trying to send direct, however when I input a relay host, the problem is still the same as being "No route to host" or "Connection timed out".

I have spoken with my ISP who told me they don't block any ports at all.

```

traceroute -p 25 mail.google.com
traceroute to mail.google.com (173.194.34.118), 30 hops max, 60 byte packets
 1  lns1.uan.the.uk.murphx.net (94.30.127.72)  32.387 ms  33.085 ms  34.085 ms
 2  er1.uan.the.uk.murphx.net (94.30.127.65)  35.758 ms  36.695 ms  37.419 ms
 3  ge2-6-1.crs1.core.the.uk.murphx.net (94.30.127.225)  38.426 ms  40.109 ms  40.552 ms
 4  * * *
 5  * * *
 6  * * *
 7  * * *
 8  * * *
 9  * * *
10  * * *
11  * * *
12  * * *
13  * * *
14  * * *
15  * * *
16  * * *
17  * * *
18  * * *
19  * * *
20  * * *
21  * * *
22  * * *
23  * * *
24  * * *
25  * * *
26  * * *
27  * * *
28  * * *
29  * * *
30  * * *
root@NCserver:~# 
```
```

telnet localhost 25
Trying ::1...
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
220 test.newworldenergy.co.uk ESMTP Postfix

```
```
netstat -alnp | grep :25
tcp        0      0 0.0.0.0:25              0.0.0.0:*               LISTEN      32421/master    

```

==== Main.cf ====
```

smtpd_banner = $myhostname ESMTP $mail_name      
biff = no                             
mailbox_size_limit = 0                
recipient_delimiter = +               
append_dot_mydomain = no             
mail_spool_directory = /var/mail     
relayhost =
mynetworks = 127.0.0.1/32 192.168.1.1 #This is the machine i'm sending the mail to the server from
inet_interfaces = all
myhostname = test.newworldenergy.co.uk
mydomain = newworldenergy.co.uk
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
mydestination = $mydomain $myhostname localhost.localdomain localhost
default_process_limit = 100
smtpd_client_connection_count_limit = 10
smtpd_client_connection_rate_limit = 30
header_size_limit = 51200
smtp_recipient_limit = 100

```
==== Master.cf====
```

#
# Postfix master process configuration file.  For details on the format
# of the file, see the master(5) manual page (command: "man 5 master").
#
# Do not forget to execute "postfix reload" after editing this file.
#
# ==========================================================================
# service type  private unpriv  chroot  wakeup  maxproc command + args
#               (yes)   (yes)   (yes)   (never) (100)
# ==========================================================================
smtp      inet  n       -       -       -       -       smtpd
#submission inet n       -       -       -       -       smtpd
#  -o smtpd_tls_security_level=encrypt
#  -o smtpd_sasl_auth_enable=yes
#  -o smtpd_client_restrictions=permit_sasl_authenticated,reject
#  -o milter_macro_daemon_name=ORIGINATING
#smtps     inet  n       -       -       -       -       smtpd
#  -o smtpd_tls_wrappermode=yes
#  -o smtpd_sasl_auth_enable=yes
#  -o smtpd_client_restrictions=permit_sasl_authenticated,reject
#  -o milter_macro_daemon_name=ORIGINATING
#628       inet  n       -       -       -       -       qmqpd
pickup    fifo  n       -       -       60      1       pickup
cleanup   unix  n       -       -       -       0       cleanup
qmgr      fifo  n       -       n       300     1       qmgr
#qmgr     fifo  n       -       -       300     1       oqmgr
tlsmgr    unix  -       -       -       1000?   1       tlsmgr
rewrite   unix  -       -       -       -       -       trivial-rewrite
bounce    unix  -       -       -       -       0       bounce
defer     unix  -       -       -       -       0       bounce
trace     unix  -       -       -       -       0       bounce
verify    unix  -       -       -       -       1       verify
flush     unix  n       -       -       1000?   0       flush
proxymap  unix  -       -       n       -       -       proxymap
proxywrite unix -       -       n       -       1       proxymap
smtp      unix  -       -       -       -       -       smtp
# When relaying mail as backup MX, disable fallback_relay to avoid MX loops
relay     unix  -       -       -       -       -       smtp
    -o smtp_fallback_relay=
#       -o smtp_helo_timeout=5 -o smtp_connect_timeout=5
showq     unix  n       -       -       -       -       showq
error     unix  -       -       -       -       -       error
retry     unix  -       -       -       -       -       error
discard   unix  -       -       -       -       -       discard
local     unix  -       n       n       -       -       local
virtual   unix  -       n       n       -       -       virtual
lmtp      unix  -       -       -       -       -       lmtp
anvil     unix  -       -       -       -       1       anvil
scache    unix  -       -       -       -       1       scache
#
# ====================================================================
# Interfaces to non-Postfix software. Be sure to examine the manual
# pages of the non-Postfix software to find out what options it wants.
#
# Many of the following services use the Postfix pipe(8) delivery
# agent.  See the pipe(8) man page for information about ${recipient}
# and other message envelope options.
# ====================================================================
#
# maildrop. See the Postfix MAILDROP_README file for details.
# Also specify in main.cf: maildrop_destination_recipient_limit=1
#
maildrop  unix  -       n       n       -       -       pipe
  flags=DRhu user=vmail argv=/usr/bin/maildrop -d ${recipient}
#
# ====================================================================
#
# Recent Cyrus versions can use the existing "lmtp" master.cf entry.
#
# Specify in cyrus.conf:
#   lmtp    cmd="lmtpd -a" listen="localhost:lmtp" proto=tcp4
#
# Specify in main.cf one or more of the following:
#  mailbox_transport = lmtp:inet:localhost
#  virtual_transport = lmtp:inet:localhost
#
# ====================================================================
#
# Cyrus 2.1.5 (Amos Gouaux)
# Also specify in main.cf: cyrus_destination_recipient_limit=1
#
#cyrus     unix  -       n       n       -       -       pipe
#  user=cyrus argv=/cyrus/bin/deliver -e -r ${sender} -m ${extension} ${user}
#
# ====================================================================
# Old example of delivery via Cyrus.
#
#old-cyrus unix  -       n       n       -       -       pipe
#  flags=R user=cyrus argv=/cyrus/bin/deliver -e -m ${extension} ${user}
#
# ====================================================================
#
# See the Postfix UUCP_README file for configuration details.
#
uucp      unix  -       n       n       -       -       pipe
  flags=Fqhu user=uucp argv=uux -r -n -z -a$sender - $nexthop!rmail ($recipient)
#
# Other external delivery methods.
#
ifmail    unix  -       n       n       -       -       pipe
  flags=F user=ftn argv=/usr/lib/ifmail/ifmail -r $nexthop ($recipient)
bsmtp     unix  -       n       n       -       -       pipe
  flags=Fq. user=bsmtp argv=/usr/lib/bsmtp/bsmtp -t$nexthop -f$sender $recipient
scalemail-backend unix    -    n    n    -    2    pipe
  flags=R user=scalemail argv=/usr/lib/scalemail/bin/scalemail-store ${nexthop} ${user} ${extension}
mailman   unix  -       n       n       -       -       pipe
  flags=FR user=list argv=/usr/lib/mailman/bin/postfix-to-mailman.py
  ${nexthop} ${user}

```


Thanks

Paul

---

### Post by vishal_agarwal2 on 2013-08-27
Post some Log details from /var/log/mail.log

---

### Post by paul31 on 2013-08-27
Hi
The mail.log file is empty
Showing as 0 bytes

Edit: Is this correct or will logging be turned off for some reason?

---

### Post by vishal_agarwal2 on 2013-08-27
what are the ip address of postfix server.

---

### Post by vishal_agarwal2 on 2013-08-27
Pl try changing the following :
relayhost =
mynetworks = 127.0.0.1/32 192.168.1.1/32, "[COLOR=#ff0000]IP address of your .newworldenergy.co.uk[/COLOR]"  #This is the machine i'm sending the mail to the server from
inet_interfaces = all
myhostname = test.newworldenergy.co.uk
mydomain = newworldenergy.co.uk
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
mydestination = $mydomain $myhostname localhost.localdomain localhost,[COLOR=#ff0000]newworldenergy.co.uk

[/COLOR][COLOR=#000080][/COLOR][COLOR=#000080]Pl check and revert back; if solved/not seoved.[/COLOR]

---

### Post by paul31 on 2013-08-27
Not Solved!

My understanding was that $mydomain in mydestination meant you didn't need to add [COLOR=#ff0000]newworldenergy.co.uk[/COLOR][COLOR=#000000]?
I've tried it as you said and still no joy.

[/COLOR]

---

### Post by SeijiSensei on 2013-08-27
Use the same telnet method you used before, but try connecting to gmail-smtp-in.l.google.com rather than localhost.  Can you connect?

---

### Post by paul31 on 2013-08-27
Thanks for the reply
No, output below.

root@NCserver:~# telnet gmail-smtp-in.l.google.com 25
Trying 173.194.66.27...
Trying 2a00:1450:400c:c03::1b...
telnet: Unable to connect to remote host: Network is unreachable

---

### Post by SeijiSensei on 2013-08-27
Somewhere along the line someone is blocking access to port 25 on remote hosts.  Your ISP claims they are not, but I'd bet that's wrong.  Otherwise the blocking has to be happening somewhere upstream from them.  Can you ping the Google SMTP server even if you cannot connect to its SMTP port?  The problem clearly is not DNS-related since your machine can obviously resolve the name for that server.

Just to make sure, you're not running iptables with limits on the OUTPUT chain are you?

---

### Post by paul31 on 2013-08-28
Yes can ping the SMTP server.



Output for iptables

root@NCserver:~# sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:smtp state NEW,ESTABLISHED 

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            tcp spt:smtp state ESTABLISHED

---

### Post by paul31 on 2013-08-28
Have changed master.cf to add following line:

587 inet n - - - - smtpd

Still no route to host

Am I missing something here?

---

### Post by paul31 on 2013-08-28
Is there any further information I can post to help resolve this?
I can't even get a relay to work if I try that way.

Could someone post their master.cf and main.cf so I can see the differences and try to understand what/where I'm going wrong.

As you've stated It looks like 25 is blocked SOMEWHERE, so the files setup to include 587. 
Does postfix interact with ANYTHING else which needs configuring which I may have missed?

Thanks

Paul

---

### Post by paul31 on 2013-08-28
Thank for you help so far.
I've just got off the phone to the ISP and they were blocking 25!!! I was told by the previous sys admin that it wasn't, so took him on his word.
They said 100,000+ emails were being sent, strange as we only send max 3000 per week.
I've to try again in a couple of hours, if it works I'll mark as solved.

---

### Post by SeijiSensei on 2013-08-28
If they told you 100,000 emails were sent from your IP address, you had probably misconfigured Postfix and were running an "open relay" that got exploited by spammers.  (Been there myself.)   Since you don't actually care about receiving mail, just sending it, you should revert to the default configuration where Postfix listens only on the localhost interface.  A send-only server does not need to listen on your Internet-facing port 25.  Back up your current Postfix configuration for reference then purge it and reinstall.

I also suggest you visit [mxtoolbox.com]("http://mxtoolbox.com/blacklists.aspx") and see if your IP pops up on any blacklists.  If you really were relaying spam, the chances are good that your address appears on at least one or two such lists.  Receiving servers who rely on these lists will reject your mail.  Usually if you fix the problem you'll be dropped from the lists in a few weeks.  Worst case scenario is that you would need to change your IP address.  I'd wait a while before asking your ISP to do that, though, so you can demonstrate that you've fixed the problem.

---

