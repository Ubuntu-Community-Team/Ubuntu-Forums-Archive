---
title: "Postfix"
date: 2019-06-02
forum: New to Ubuntu
---

### Post by rjphares on 2019-06-02
I am trying to send an email to myself and it says I have no mail. I am using Bash on Ubuntu on Windows 10.  What should I do?
[IMG]https://ubuntuforums.org/editpost.php?do=updatepost&p=13863539[/IMG][IMG]https://ubuntuforums.org/editpost.php?do=updatepost&p=13863539[/IMG]


[ATTACH=CONFIG]283363[/ATTACH]

---

### Post by LwIh%*7 on 2019-06-03
Could you have a look at: 

[https://askubuntu.com/questions/996906/ubuntu-16-04-postfix-cant-receive-emails](https://askubuntu.com/questions/996906/ubuntu-16-04-postfix-cant-receive-emails)

And see if this helps? It may do the same for the Ubuntu version you're using.

---

### Post by rjphares on 2019-06-03
[LEFT][COLOR=#222222][FONT=Verdana]Says sendmail is not installed: [/FONT][/COLOR][/LEFT]
[IMG]https://ubuntuforums.org/ajax.php[/IMG][URL="https://imgur.com/a/eCMnhjK"][FONT=Verdana][LEFT][COLOR=#222222][FONT=Verdana]https://imgur.com/a/eCMnhjK[/FONT][/COLOR][/LEFT]
[/FONT][/URL][FONT=Verdana][LEFT][/LEFT]
[/FONT]

---

### Post by LwIh%*7 on 2019-06-04
> **rjphares said:**
> [LEFT][COLOR=#222222][FONT=Verdana]Says sendmail is not installed: [/FONT][/COLOR][/LEFT]
[IMG]https://ubuntuforums.org/ajax.php[/IMG][URL="https://imgur.com/a/eCMnhjK"][FONT=Verdana][LEFT][COLOR=#222222][FONT=Verdana]https://imgur.com/a/eCMnhjK[/FONT][/COLOR][/LEFT]
[/FONT][/URL]

If that's the only missing bit then issue the following command:

```

sudo apt-get install sendmail

```

See if that'll solve the problem. Also see [https://gist.github.com/adamstac/7462202](https://gist.github.com/adamstac/7462202)

---

### Post by rjphares on 2019-06-08
Do I need Sendmail for Postfix?

---

### Post by TheFu on 2019-06-08
> **rjphares said:**
> Do I need Sendmail for Postfix?

No.  Sendmail and postfix fulfil the same requirement. Postfix is much easier to configure and less likely to be hacked. Only 1 MTA should be installed on any Unix system.

I don't know anything about win10, so don't feel comfortable helping with the base issue, but to send email from a Unix system, you need a number of things.

* MTA - postfix
* Mail client - Mail, mail, mailx, elm, something that will convert what you type/enter/script into the MTA
* An address TO send the mail that will accept it from your machine.

None of those things are installed automatically. You must install them all and configure the MTA.  **If you expect to send to internet email addresses, there are more requirements to get passed the anti-spam checks that most email servers have.** There are other threads here about what is needed to send email using Ubuntu with postfix that cover those requirements.

---

### Post by SeijiSensei on 2019-06-09
I don't think Postfix is any easier to install than sendmail, especially for a simple task like delivering locally.  

If you install sendmail, try using

```
echo 'test message' | sendmail yourusername
```

It should show up in your mailbox on the machine.

---

### Post by TheFu on 2019-06-09
It has been a long time since I touched sendmail (1995-ish?).

I know that postfix installs a "sendmail" program that is supposed to be 100% compatible with the expected sendmail interface. Is is there: 
```
$ ll /usr/sbin/sendmail
-rwxr-xr-x 1 root root 26648 Jan 17  2018 /usr/sbin/sendmail*

```
and I can confirm that 
```
echo 'test message' | sendmail yourusername
```
behaved exactly as expected.  Nice.
On my systems, it also works to send external emails without a formal FROM/SUBJECT or other expected X-Headers.

Regardless, can't believe I've forgotten about that shell interface.

---

### Post by kevdog on 2019-06-11
Postfix is really easy to send through however are you sending the mail locally or out to the internet? You said to yourself however is that just locally or are you trying to make this go out to the internet and back?

---

### Post by rjphares on 2019-06-12
[LEFT]Since I was unable to send an email out to the internet, I tried sending locally. And then I couldn't do that either, so now I am just trying to send an email to myself locally.

I tried sending myself an email using sendmail and got the same result.[/LEFT]

[https://imgur.com/a/QnMgB7t](https://imgur.com/a/QnMgB7t)

---

### Post by lisati on 2019-06-12
Are you seeing anything helpful in the mail logs?

---

### Post by rjphares on 2019-06-12
I don't have or cannot find a mail.log file. But I found this:

```
Return-Path: <>
X-Original-To: [email]rjphares@mail.gmail.com[/email]
Delivered-To: [email]rjphares@mail.gmail.com[/email]
Received: by mail.gmail.com (Postfix)
 id 004887000000041689; Wed, 22 May 2019 18:27:14 -0400 (DST)
Date: Wed, 22 May 2019 18:27:14 -0400 (DST)
From: [email]MAILER-DAEMON@mail.gmail.com[/email] (Mail Delivery System)
Subject: Undelivered Mail Returned to Sender
To: [email]rjphares@mail.gmail.com[/email]
Auto-Submitted: auto-replied
MIME-Version: 1.0
Content-Type: multipart/report; report-type=delivery-status;
 boundary="E84219000000041688.1558564033/mail.gmail.com"
Content-Transfer-Encoding: 8bit
Message-Id: <20190522222714.004887000000041689@mail.gmail.com>
This is a MIME-encapsulated message.
--E84219000000041688.1558564033/mail.gmail.com
Content-Description: Notification
Content-Type: text/plain; charset=utf-8
Content-Transfer-Encoding: 8bit
This is the mail system at host mail.gmail.com.
I'm sorry to have to inform you that your message could not
be delivered to one or more recipients. It's attached below.
For further assistance, please send mail to postmaster.
If you do so, please include this problem report. You can
delete your own text from the attached returned message.
                   The mail system
<rjphares914@gmail.com>: unknown user: "rjphares914"
<test@mail.gmail.com> (expanded from <test>): unknown user: "test"
--E84219000000041688.1558564033/mail.gmail.com
Content-Description: Delivery report
Content-Type: message/delivery-status
Reporting-MTA: dns; mail.gmail.com
X-Postfix-Queue-ID: E84219000000041688
X-Postfix-Sender: rfc822; [email]rjphares@mail.gmail.com[/email]
Arrival-Date: Wed, 22 May 2019 18:27:10 -0400 (DST)
Final-Recipient: rfc822; [email]rjphares914@gmail.com[/email]
Original-Recipient: rfc822;rjphares914@gmail.com
Action: failed
Status: 5.1.1
Diagnostic-Code: X-Postfix; unknown user: "rjphares914"
Final-Recipient: rfc822; [email]test@mail.gmail.com[/email]
Original-Recipient: rfc822;test@mail.gmail.com
Action: failed
Status: 5.1.1
Diagnostic-Code: X-Postfix; unknown user: "test"
--E84219000000041688.1558564033/mail.gmail.com
Content-Description: Undelivered Message
Content-Type: message/rfc822
Content-Transfer-Encoding: 8bit
Return-Path: <rjphares@mail.gmail.com>
Received: by mail.gmail.com (Postfix, from userid 1000)
 id E84219000000041688; Wed, 22 May 2019 18:27:13 -0400 (DST)
Message-Id: <20190522222713.E84219000000041688@mail.gmail.com>
Date: Wed, 22 May 2019 18:27:10 -0400 (DST)
From: DESKTOP-K50P15B <rjphares@mail.gmail.com>
--E84219000000041688.1558564033/mail.gmail.com--
```

---

### Post by kevdog on 2019-06-13
So your error logs would suggest your trying to email through google?  Have you setup postfix properly to be able to send through google's smtp service?  You need to create a one time password to bypass the 2FA on Google to do this and configure postfix to read this one time password within a hashed file.

---

### Post by SeijiSensei on 2019-06-13
> **rjphares said:**
> I tried sending myself an email using sendmail and got the same result.
If the message is stored in /var/spool/mail/username, or /var/mail/username, then it was properly delivered, and the mail command you are using is not looking in the right location for messages.

---

### Post by rjphares on 2019-06-13
I already configured postfix for gmail's two step auth. I followed this site's instructions: [https://opensource.com/article/18/8/postfix-open-source-mail-transfer-agent](https://opensource.com/article/18/8/postfix-open-source-mail-transfer-agent)

---

### Post by kevdog on 2019-06-14
So what happens when you try to send mail at command line as discussed in the article?

---

### Post by kevdog on 2019-06-14
Just a couple of things, since I walked through this exact same process on my freebsd server like a few months back.  Basically encrypted email can be sent over port 587 or port 465.  There is a lot of controversy about what port to send encryption over however I'll make a very broad general statement -- both are supported -- [465 was, then it wasn't, and now it is again]("https://www.fastmail.com/help/technical/ssltlsstarttls.html").  Anyway in my experience with gmail -- although I've done it both ways, I've found port 465 to be much more user friendly and prone to less errors.

I configured my postfix main.cf file a little different than in the source you referenced.  I put these lines at the bottom of the main.cf file:  (please note that I found this line:
smtp_tls_CAfile = /etc/ssl/certs/ca-certificates.crt
totally unnecessary. I don't own this file and I didn't include it.

```

## SASL Options
smtp_sasl_auth_enable = yes
smtp_sasl_security_options = noanonymous
smtp_sasl_password_maps = hash:/usr/local/etc/postfix/sasl_passwd

## TLS Options
smtp_use_tls = yes
smtp_tls_security_level = encrypt
##Following line required for port 465
smtp_tls_wrappermode = yes
tls_random_source = dev:/dev/urandom

## Relay host
relayhost = [smtp.gmail.com]:465

```


My sasl_password file simply is the following:

```

smtp.gmail.com  <username>:<two_factor_password>      <------None are in brackets replace the contents including the brackets with the appropriate paramters

```

Hopefully that will help.  Make sure port 465 is being blocked somewhere.

---

### Post by rjphares on 2019-06-14
I got the same result, so the output said "no mail for rjphares". Here is my main.cf file:

```

[FONT=Verdana]# Global Postfix configuration file. This file lists only a subset
# of all parameters. For the syntax, and for a complete parameter
# list, see the postconf(5) manual page (command: "man 5 postconf").
#
# For common configuration examples, see BASIC_CONFIGURATION_README
# and STANDARD_CONFIGURATION_README. To find these documents, use
# the command "postconf html_directory readme_directory", or go to
# http://www.postfix.org/BASIC_CONFIGURATION_README.html etc.
#
# For best results, change no more than 2-3 parameters at a time,
# and test if Postfix still works after every change.
# COMPATIBILITY
#
# The compatibility_level determines what default settings Postfix
# will use for main.cf and master.cf settings. These defaults will
# change over time.
#
# To avoid breaking things, Postfix will use backwards-compatible
# default settings and log where it uses those old backwards-compatible
# default settings, until the system administrator has determined
# if any backwards-compatible default settings need to be made
# permanent in main.cf or master.cf.
#
# When this review is complete, update the compatibility_level setting
# below as recommended in the RELEASE_NOTES file.
#
# The level below is what should be used with new (not upgrade) installs.
#
compatibility_level = 2
# SOFT BOUNCE
#
# The soft_bounce parameter provides a limited safety net for
# testing.  When soft_bounce is enabled, mail will remain queued that
# would otherwise bounce. This parameter disables locally-generated
# bounces, and prevents the SMTP server from rejecting mail permanently
# (by changing 5xx replies into 4xx replies). However, soft_bounce
# is no cure for address rewriting mistakes or mail routing mistakes.
#
#soft_bounce = no
# LOCAL PATHNAME INFORMATION
#
# The queue_directory specifies the location of the Postfix queue.
# This is also the root directory of Postfix daemons that run chrooted.
# See the files in examples/chroot-setup for setting up Postfix chroot
# environments on different UNIX systems.
#
#queue_directory = /var/spool/postfix
# The command_directory parameter specifies the location of all
# postXXX commands.
#
command_directory = /usr/sbin
# The daemon_directory parameter specifies the location of all Postfix
# daemon programs (i.e. programs listed in the master.cf file). This
# directory must be owned by root.
#
daemon_directory = /usr/lib/postfix/sbin
# The data_directory parameter specifies the location of Postfix-writable
# data files (caches, random numbers). This directory must be owned
# by the mail_owner account (see below).
#
data_directory = /var/lib/postfix
# QUEUE AND PROCESS OWNERSHIP
#
# The mail_owner parameter specifies the owner of the Postfix queue
# and of most Postfix daemon processes.  Specify the name of a user
# account THAT DOES NOT SHARE ITS USER OR GROUP ID WITH OTHER ACCOUNTS
# AND THAT OWNS NO OTHER FILES OR PROCESSES ON THE SYSTEM.  In
# particular, don't specify nobody or daemon. PLEASE USE A DEDICATED
# USER.
#
mail_owner = postfix
# The default_privs parameter specifies the default rights used by
# the local delivery agent for delivery to external file or command.
# These rights are used in the absence of a recipient user context.
# DO NOT SPECIFY A PRIVILEGED USER OR THE POSTFIX OWNER.
#
#default_privs = nobody
# INTERNET HOST AND DOMAIN NAMES
# 
# The myhostname parameter specifies the internet hostname of this
# mail system. The default is to use the fully-qualified domain name
# from gethostname(). $myhostname is used as a default value for many
# other configuration parameters.
#
myhostname = rjphares.localdomain
#myhostname = virtual.domain.tld
# The mydomain parameter specifies the local internet domain name.
# The default is to use $myhostname minus the first component.
# $mydomain is used as a default value for many other configuration
# parameters.
#
mydomain = gmail.com
# SENDING MAIL
# 
# The myorigin parameter specifies the domain that locally-posted
# mail appears to come from. The default is to append $myhostname,
# which is fine for small sites.  If you run a domain with multiple
# machines, you should (1) change this to $mydomain and (2) set up
# a domain-wide alias database that aliases each user to
# user@that.users.mailhost.
#
# For the sake of consistency between sender and recipient addresses,
# myorigin also specifies the default domain name that is appended
# to recipient addresses that have no @domain part.
#
# Debian GNU/Linux specific:  Specifying a file name will cause the
# first line of that file to be used as the name.  The Debian default
# is /etc/mailname.
#
#myorigin = /etc/mailname
#myorigin = $myhostname
#myorigin = $mydomain
# RECEIVING MAIL
# The inet_interfaces parameter specifies the network interface
# addresses that this mail system receives mail on.  By default,
# the software claims all active interfaces on the machine. The
# parameter also controls delivery of mail to user@[ip.address].
#
# See also the proxy_interfaces parameter, for network addresses that
# are forwarded to us via a proxy or network address translator.
#
# Note: you need to stop/start Postfix when this parameter changes.
#
inet_interfaces = loopback-only
#inet_interfaces = $myhostname
#inet_interfaces = $myhostname, localhost
# The proxy_interfaces parameter specifies the network interface
# addresses that this mail system receives mail on by way of a
# proxy or network address translation unit. This setting extends
# the address list specified with the inet_interfaces parameter.
#
# You must specify your proxy/NAT addresses when your system is a
# backup MX host for other domains, otherwise mail delivery loops
# will happen when the primary MX host is down.
#
#proxy_interfaces =
#proxy_interfaces = 1.2.3.4
# The mydestination parameter specifies the list of domains that this
# machine considers itself the final destination for.
#
# These domains are routed to the delivery agent specified with the
# local_transport parameter setting. By default, that is the UNIX
# compatible delivery agent that lookups all recipients in /etc/passwd
# and /etc/aliases or their equivalent.
#
# The default is $myhostname + localhost.$mydomain + localhost.  On
# a mail domain gateway, you should also include $mydomain.
#
# Do not specify the names of virtual domains - those domains are
# specified elsewhere (see VIRTUAL_README).
#
# Do not specify the names of domains that this machine is backup MX
# host for. Specify those names via the relay_domains settings for
# the SMTP server, or use permit_mx_backup if you are lazy (see
# STANDARD_CONFIGURATION_README).
#
# The local machine is always the final destination for mail addressed
# to user@[the.net.work.address] of an interface that the mail system
# receives mail on (see the inet_interfaces parameter).
#
# Specify a list of host or domain names, /file/name or type:table
# patterns, separated by commas and/or whitespace. A /file/name
# pattern is replaced by its contents; a type:table is matched when
# a name matches a lookup key (the right-hand side is ignored).
# Continue long lines by starting the next line with whitespace.
#
# See also below, section "REJECTING MAIL FOR UNKNOWN LOCAL USERS".
#
#mydestination = $myhostname, localhost.$mydomain, localhost
mydestination = mail.gmail.com, localhost.gmail.com, localhost, gmail.com
#mydestination = $myhostname, localhost.$mydomain, localhost, $mydomain,
# mail.$mydomain, www.$mydomain, ftp.$mydomain
# REJECTING MAIL FOR UNKNOWN LOCAL USERS
#
# The local_recipient_maps parameter specifies optional lookup tables
# with all names or addresses of users that are local with respect
# to $mydestination, $inet_interfaces or $proxy_interfaces.
#
# If this parameter is defined, then the SMTP server will reject
# mail for unknown local users. This parameter is defined by default.
#
# To turn off local recipient checking in the SMTP server, specify
# local_recipient_maps = (i.e. empty).
#
# The default setting assumes that you use the default Postfix local
# delivery agent for local delivery. You need to update the
# local_recipient_maps setting if:
#
# - You define $mydestination domain recipients in files other than
#   /etc/passwd, /etc/aliases, or the $virtual_alias_maps files.
#   For example, you define $mydestination domain recipients in    
#   the $virtual_mailbox_maps files.
#
# - You redefine the local delivery agent in master.cf.
#
# - You redefine the "local_transport" setting in main.cf.
#
# - You use the "luser_relay", "mailbox_transport", or "fallback_transport"
#   feature of the Postfix local delivery agent (see local(8)).
#
# Details are described in the LOCAL_RECIPIENT_README file.
#
# Beware: if the Postfix SMTP server runs chrooted, you probably have
# to access the passwd file via the proxymap service, in order to
# overcome chroot restrictions. The alternative, having a copy of
# the system passwd file in the chroot jail is just not practical.
#
# The right-hand side of the lookup tables is conveniently ignored.
# In the left-hand side, specify a bare username, an @domain.tld
# wild-card, or specify a user@domain.tld address.
# 
local_recipient_maps = unix:passwd.byname $alias_maps
#local_recipient_maps = proxy:unix:passwd.byname $alias_maps
#local_recipient_maps =
# The unknown_local_recipient_reject_code specifies the SMTP server
# response code when a recipient domain matches $mydestination or
# ${proxy,inet}_interfaces, while $local_recipient_maps is non-empty
# and the recipient address or address local-part is not found.
#
# The default setting is 550 (reject mail) but it is safer to start
# with 450 (try again later) until you are certain that your
# local_recipient_maps settings are OK.
#
unknown_local_recipient_reject_code = 550
# TRUST AND RELAY CONTROL
# The mynetworks parameter specifies the list of "trusted" SMTP
# clients that have more privileges than "strangers".
#
# In particular, "trusted" SMTP clients are allowed to relay mail
# through Postfix.  See the smtpd_recipient_restrictions parameter
# in postconf(5).
#
# You can specify the list of "trusted" network addresses by hand
# or you can let Postfix do it for you (which is the default).
#
# By default (mynetworks_style = subnet), Postfix "trusts" SMTP
# clients in the same IP subnetworks as the local machine.
# On Linux, this does works correctly only with interfaces specified
# with the "ifconfig" command.
# 
# Specify "mynetworks_style = class" when Postfix should "trust" SMTP
# clients in the same IP class A/B/C networks as the local machine.
# Don't do this with a dialup site - it would cause Postfix to "trust"
# your entire provider's network.  Instead, specify an explicit
# mynetworks list by hand, as described below.
#  
# Specify "mynetworks_style = host" when Postfix should "trust"
# only the local machine.
# 
#mynetworks_style = class
#mynetworks_style = subnet
mynetworks_style = host
# Alternatively, you can specify the mynetworks list by hand, in
# which case Postfix ignores the mynetworks_style setting.
#
# Specify an explicit list of network/netmask patterns, where the
# mask specifies the number of bits in the network part of a host
# address.
#
# You can also specify the absolute pathname of a pattern file instead
# of listing the patterns here. Specify type:table for table-based lookups
# (the value on the table right-hand side is not used).
#
#mynetworks = 168.100.189.0/28, 127.0.0.0/8
#mynetworks = $config_directory/mynetworks
#mynetworks = hash:/etc/postfix/network_table
#mynetworks = 127.0.0.0/8, 10.0.0.0/24
# The relay_domains parameter restricts what destinations this system will
# relay mail to.  See the smtpd_recipient_restrictions description in
# postconf(5) for detailed information.
#
# By default, Postfix relays mail
# - from "trusted" clients (IP address matches $mynetworks) to any destination,
# - from "untrusted" clients to destinations that match $relay_domains or
#   subdomains thereof, except addresses with sender-specified routing.
# The default relay_domains value is $mydestination.
# 
# In addition to the above, the Postfix SMTP server by default accepts mail
# that Postfix is final destination for:
# - destinations that match $inet_interfaces or $proxy_interfaces,
# - destinations that match $mydestination
# - destinations that match $virtual_alias_domains,
# - destinations that match $virtual_mailbox_domains.
# These destinations do not need to be listed in $relay_domains.
# 
# Specify a list of hosts or domains, /file/name patterns or type:name
# lookup tables, separated by commas and/or whitespace.  Continue
# long lines by starting the next line with whitespace. A file name
# is replaced by its contents; a type:name table is matched when a
# (parent) domain appears as lookup key.
#
# NOTE: Postfix will not automatically forward mail for domains that
# list this system as their primary or backup MX host. See the
# permit_mx_backup restriction description in postconf(5).
#
#relay_domains = $mydestination
# INTERNET OR INTRANET
# The relayhost parameter specifies the default host to send mail to
# when no entry is matched in the optional transport(5) table. When
# no relayhost is given, mail is routed directly to the destination.
#
# On an intranet, specify the organizational domain name. If your
# internal DNS uses no MX records, specify the name of the intranet
# gateway host instead.
#
# In the case of SMTP, specify a domain, host, host:port, [host]:port,
# [address] or [address]:port; the form [host] turns off MX lookups.
#
# If you're connected via UUCP, see also the default_transport parameter.
#
#relayhost = $mydomain
#relayhost = [gateway.my.domain]
#relayhost = [mailserver.isp.tld]
#relayhost = uucphost
#relayhost = [an.ip.add.ress]
# REJECTING UNKNOWN RELAY USERS
#
# The relay_recipient_maps parameter specifies optional lookup tables
# with all addresses in the domains that match $relay_domains.
#
# If this parameter is defined, then the SMTP server will reject
# mail for unknown relay users. This feature is off by default.
#
# The right-hand side of the lookup tables is conveniently ignored.
# In the left-hand side, specify an @domain.tld wild-card, or specify
# a user@domain.tld address.
# 
#relay_recipient_maps = hash:/etc/postfix/relay_recipients
# INPUT RATE CONTROL
#
# The in_flow_delay configuration parameter implements mail input
# flow control. This feature is turned on by default, although it
# still needs further development (it's disabled on SCO UNIX due
# to an SCO bug).
# 
# A Postfix process will pause for $in_flow_delay seconds before
# accepting a new message, when the message arrival rate exceeds the
# message delivery rate. With the default 100 SMTP server process
# limit, this limits the mail inflow to 100 messages a second more
# than the number of messages delivered per second.
# 
# Specify 0 to disable the feature. Valid delays are 0..10.
# 
#in_flow_delay = 1s
# ADDRESS REWRITING
#
# The ADDRESS_REWRITING_README document gives information about
# address masquerading or other forms of address rewriting including
# username->Firstname.Lastname mapping.
# ADDRESS REDIRECTION (VIRTUAL DOMAIN)
#
# The VIRTUAL_README document gives information about the many forms
# of domain hosting that Postfix supports.
# "USER HAS MOVED" BOUNCE MESSAGES
#
# See the discussion in the ADDRESS_REWRITING_README document.
# TRANSPORT MAP
#
# See the discussion in the ADDRESS_REWRITING_README document.
# ALIAS DATABASE
#
# The alias_maps parameter specifies the list of alias databases used
# by the local delivery agent. The default list is system dependent.
#
# On systems with NIS, the default is to search the local alias
# database, then the NIS alias database. See aliases(5) for syntax
# details.
# 
# If you change the alias database, run "postalias /etc/aliases" (or
# wherever your system stores the mail alias file), or simply run
# "newaliases" to build the necessary DBM or DB file.
#
# It will take a minute or so before changes become visible.  Use
# "postfix reload" to eliminate the delay.
#
#alias_maps = dbm:/etc/aliases
alias_maps = hash:/etc/aliases
#alias_maps = hash:/etc/aliases, nis:mail.aliases
#alias_maps = netinfo:/aliases
# The alias_database parameter specifies the alias database(s) that
# are built with "newaliases" or "sendmail -bi".  This is a separate
# configuration parameter, because alias_maps (see above) may specify
# tables that are not necessarily all under control by Postfix.
#
#alias_database = dbm:/etc/aliases
#alias_database = dbm:/etc/mail/aliases
alias_database = hash:/etc/aliases
#alias_database = hash:/etc/aliases, hash:/opt/majordomo/aliases
# ADDRESS EXTENSIONS (e.g., user+foo)
#
# The recipient_delimiter parameter specifies the separator between
# user names and address extensions (user+foo). See canonical(5),
# local(8), relocated(5) and virtual(5) for the effects this has on
# aliases, canonical, virtual, relocated and .forward file lookups.
# Basically, the software tries user+foo and .forward+foo before
# trying user and .forward.
#
#recipient_delimiter = +
# DELIVERY TO MAILBOX
#
# The home_mailbox parameter specifies the optional pathname of a
# mailbox file relative to a user's home directory. The default
# mailbox file is /var/spool/mail/user or /var/mail/user.  Specify
# "Maildir/" for qmail-style delivery (the / is required).
#
#home_mailbox = Mailbox
home_mailbox = Maildir/
 
# The mail_spool_directory parameter specifies the directory where
# UNIX-style mailboxes are kept. The default setting depends on the
# system type.
#
#mail_spool_directory = /var/mail
#mail_spool_directory = /var/spool/mail
# The mailbox_command parameter specifies the optional external
# command to use instead of mailbox delivery. The command is run as
# the recipient with proper HOME, SHELL and LOGNAME environment settings.
# Exception:  delivery for root is done as $default_user.
#
# Other environment variables of interest: USER (recipient username),
# EXTENSION (address extension), DOMAIN (domain part of address),
# and LOCAL (the address localpart).
#
# Unlike other Postfix configuration parameters, the mailbox_command
# parameter is not subjected to $parameter substitutions. This is to
# make it easier to specify shell syntax (see example below).
#
# Avoid shell meta characters because they will force Postfix to run
# an expensive shell process. Procmail alone is expensive enough.
#
# IF YOU USE THIS TO DELIVER MAIL SYSTEM-WIDE, YOU MUST SET UP AN
# ALIAS THAT FORWARDS MAIL FOR ROOT TO A REAL USER.
#
#mailbox_command = /usr/bin/procmail
#mailbox_command = /usr/bin/procmail -a "$EXTENSION"
# The mailbox_transport specifies the optional transport in master.cf
# to use after processing aliases and .forward files. This parameter
# has precedence over the mailbox_command, fallback_transport and
# luser_relay parameters.
#
# Specify a string of the form transport:nexthop, where transport is
# the name of a mail delivery transport defined in master.cf.  The
# :nexthop part is optional. For more details see the sample transport
# configuration file.
#
# NOTE: if you use this feature for accounts not in the UNIX password
# file, then you must update the "local_recipient_maps" setting in
# the main.cf file, otherwise the SMTP server will reject mail for    
# non-UNIX accounts with "User unknown in local recipient table".
#
# Cyrus IMAP over LMTP. Specify ``lmtpunix      cmd="lmtpd"
# listen="/var/imap/socket/lmtp" prefork=0'' in cyrus.conf.
#mailbox_transport = lmtp:unix:/var/imap/socket/lmtp
#
# Cyrus IMAP via command line. Uncomment the "cyrus...pipe" and
# subsequent line in master.cf.
#mailbox_transport = cyrus
# The fallback_transport specifies the optional transport in master.cf
# to use for recipients that are not found in the UNIX passwd database.
# This parameter has precedence over the luser_relay parameter.
#
# Specify a string of the form transport:nexthop, where transport is
# the name of a mail delivery transport defined in master.cf.  The
# :nexthop part is optional. For more details see the sample transport
# configuration file.
#
# NOTE: if you use this feature for accounts not in the UNIX password
# file, then you must update the "local_recipient_maps" setting in
# the main.cf file, otherwise the SMTP server will reject mail for    
# non-UNIX accounts with "User unknown in local recipient table".
#
#fallback_transport = lmtp:unix:/file/name
#fallback_transport = cyrus
#fallback_transport =
# The luser_relay parameter specifies an optional destination address
# for unknown recipients.  By default, mail for unknown@$mydestination,
# unknown@[$inet_interfaces] or unknown@[$proxy_interfaces] is returned
# as undeliverable.
#
# The following expansions are done on luser_relay: $user (recipient
# username), $shell (recipient shell), $home (recipient home directory),
# $recipient (full recipient address), $extension (recipient address
# extension), $domain (recipient domain), $local (entire recipient
# localpart), $recipient_delimiter. Specify ${name?value} or
# ${name:value} to expand value only when $name does (does not) exist.
#
# luser_relay works only for the default Postfix local delivery agent.
#
# NOTE: if you use this feature for accounts not in the UNIX password
# file, then you must specify "local_recipient_maps =" (i.e. empty) in
# the main.cf file, otherwise the SMTP server will reject mail for    
# non-UNIX accounts with "User unknown in local recipient table".
#
#luser_relay = $user@other.host
#luser_relay = $local@other.host
#luser_relay = admin+$local
  
# JUNK MAIL CONTROLS
# 
# The controls listed here are only a very small subset. The file
# SMTPD_ACCESS_README provides an overview.
# The header_checks parameter specifies an optional table with patterns
# that each logical message header is matched against, including
# headers that span multiple physical lines.
#
# By default, these patterns also apply to MIME headers and to the
# headers of attached messages. With older Postfix versions, MIME and
# attached message headers were treated as body text.
#
# For details, see "man header_checks".
#
#header_checks = regexp:/etc/postfix/header_checks
# FAST ETRN SERVICE
#
# Postfix maintains per-destination logfiles with information about
# deferred mail, so that mail can be flushed quickly with the SMTP
# "ETRN domain.tld" command, or by executing "sendmail -qRdomain.tld".
# See the ETRN_README document for a detailed description.
# 
# The fast_flush_domains parameter controls what destinations are
# eligible for this service. By default, they are all domains that
# this server is willing to relay mail to.
# 
#fast_flush_domains = $relay_domains
# SHOW SOFTWARE VERSION OR NOT
#
# The smtpd_banner parameter specifies the text that follows the 220
# code in the SMTP server's greeting banner. Some people like to see
# the mail version advertised. By default, Postfix shows no version.
#
# You MUST specify $myhostname at the start of the text. That is an
# RFC requirement. Postfix itself does not care.
#
#smtpd_banner = $myhostname ESMTP $mail_name
#smtpd_banner = $myhostname ESMTP $mail_name ($mail_version)
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)

# PARALLEL DELIVERY TO THE SAME DESTINATION
#
# How many parallel deliveries to the same user or domain? With local
# delivery, it does not make sense to do massively parallel delivery
# to the same user, because mailbox updates must happen sequentially,
# and expensive pipelines in .forward files can cause disasters when
# too many are run at the same time. With SMTP deliveries, 10
# simultaneous connections to the same domain could be sufficient to
# raise eyebrows.
# 
# Each message delivery transport has its XXX_destination_concurrency_limit
# parameter.  The default is $default_destination_concurrency_limit for
# most delivery transports. For the local delivery agent the default is 2.
#local_destination_concurrency_limit = 2
#default_destination_concurrency_limit = 20
# DEBUGGING CONTROL
#
# The debug_peer_level parameter specifies the increment in verbose
# logging level when an SMTP client or server host name or address
# matches a pattern in the debug_peer_list parameter.
#
#debug_peer_level = 2
# The debug_peer_list parameter specifies an optional list of domain
# or network patterns, /file/name patterns or type:name tables. When
# an SMTP client or server host name or address matches a pattern,
# increase the verbose logging level by the amount specified in the
# debug_peer_level parameter.
#
#debug_peer_list = 127.0.0.1
#debug_peer_list = some.domain
# The debugger_command specifies the external command that is executed
# when a Postfix daemon program is run with the -D option.
#
# Use "command .. & sleep 5" so that the debugger can attach before
# the process marches on. If you use an X-based debugger, be sure to
# set up your XAUTHORITY environment variable before starting Postfix.
#
debugger_command =
  PATH=/bin:/usr/bin:/usr/local/bin:/usr/X11R6/bin
  ddd $daemon_directory/$process_name $process_id & sleep 5
# If you can't use X, use this to capture the call stack when a
# daemon crashes. The result is in a file in the configuration
# directory, and is named after the process name and the process ID.
#
# debugger_command =
# PATH=/bin:/usr/bin:/usr/local/bin; export PATH; (echo cont;
# echo where) | gdb $daemon_directory/$process_name $process_id 2>&1
# >$config_directory/$process_name.$process_id.log & sleep 5
#
# Another possibility is to run gdb under a detached screen session.
# To attach to the screen session, su root and run "screen -r
# <id_string>" where <id_string> uniquely matches one of the detached
# sessions (from "screen -list").
#
# debugger_command =
# PATH=/bin:/usr/bin:/sbin:/usr/sbin; export PATH; screen
# -dmS $process_name gdb $daemon_directory/$process_name
# $process_id & sleep 1
# INSTALL-TIME CONFIGURATION INFORMATION
#
# The following parameters are used when installing a new Postfix version.
# 
# sendmail_path: The full pathname of the Postfix sendmail command.
# This is the Sendmail-compatible mail posting interface.
# 
sendmail_path = /usr/sbin/postfix
# newaliases_path: The full pathname of the Postfix newaliases command.
# This is the Sendmail-compatible command to build alias databases.
#
newaliases_path = /usr/bin/newaliases
# mailq_path: The full pathname of the Postfix mailq command.  This
# is the Sendmail-compatible mail queue listing command.
# 
mailq_path = /user/bin/mailq
# setgid_group: The group for mail submission and queue management
# commands.  This must be a group name with a numerical group ID that
# is not shared with other accounts, not even with the Postfix account.
#
setgid_group = postdrop
# html_directory: The location of the Postfix HTML documentation.
#
#html_directory =
# manpage_directory: The location of the Postfix on-line manual pages.
#
#manpage_directory =
# sample_directory: The location of the Postfix sample configuration files.
# This parameter is obsolete as of Postfix 2.1.
#
#sample_directory =
# readme_directory: The location of the Postfix README files.
#
#readme_directory =
inet_protocols = ipv4
#add to end of file: limit an email size to 10M
message_size_limit = 10485760
#limit mailbox size to 1G
mailbox_size_limit = 51200000
myorigin = /etc/mailname
#mydestination = $myhostname, localhost.$mydomain, localhost
mynetwork = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
relayhost = 
recipient_delimiter = 
default_transport = error
relay_transport = error
mynetworks = 127.0.0.1/32
## SASL Options
smtp_sasl_auth_enable = yes
smtp_sasl_security_options = noanonymous
smtp_sasl_password_maps = hash:/usr/local/etc/postfix/sasl_passwd
## TLS Options
smtp_use_tls = yes
smtp_tls_security_level = encrypt
##Following line required for port 465
smtp_tls_wrappermode = yes
tls_random_source = dev:/dev/urandom
## Relay host
relayhost = [smtp.gmail.com]:465
[/FONT][FONT=Verdana]
[/FONT]

```

---

### Post by kevdog on 2019-06-14
I don't understand your main.cf file -- I read it -- Where are all the SASL options as I mentioned above?

---

### Post by rjphares on 2019-06-14
I made the changes to main.cf and sasl_passwd. Still says "no mail for rjphares"

---

### Post by kevdog on 2019-06-15
rjphares

It makes it impossible for anyone to truly help you without posting out, log files, or configurations to give us something to go on to help you.

---

### Post by rjphares on 2019-06-15
I am doing my best to solve this issue and am very thankful for the help.  I posted a log file and my configuration file.  I do want to solve this issue but I do not have a specific file called "mail.log" that appears in most of my google searches.

---

### Post by lisati on 2019-06-15
The information you posted in [post 12]("https://ubuntuforums.org/showthread.php?t=2420291&p=13865949&viewfull=1#post13865949") of this thread isn't actually a log entry, but appears to be a non-delivery report ("bounce"), informing you/me that gmail didn't accept a message for delivery.

It has been several years since I've run a mail server at home, but if memory serves correctly, there should be a log file  in /var/log/mail.log

---

### Post by rjphares on 2019-06-15
```
[FONT=Verdana,Arial,Tahoma,Calibri,Geneva,sans-serif]May 31 12:15:05 DESKTOP-K50P15B postfix/local[743]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 12:16:06 DESKTOP-K50P15B postfix/local[776]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 12:17:07 DESKTOP-K50P15B postfix/local[809]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 12:18:08 DESKTOP-K50P15B postfix/local[810]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 12:19:09 DESKTOP-K50P15B postfix/local[811]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 12:20:10 DESKTOP-K50P15B postfix/local[812]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 12:21:11 DESKTOP-K50P15B postfix/local[813]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 12:22:12 DESKTOP-K50P15B postfix/local[814]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 12:23:13 DESKTOP-K50P15B postfix/local[815]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 12:24:14 DESKTOP-K50P15B postfix/local[816]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 12:25:15 DESKTOP-K50P15B postfix/local[817]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 12:26:16 DESKTOP-K50P15B postfix/local[818]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 12:27:17 DESKTOP-K50P15B postfix/local[819]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 12:28:18 DESKTOP-K50P15B postfix/local[820]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 12:29:19 DESKTOP-K50P15B postfix/local[821]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 12:30:20 DESKTOP-K50P15B postfix/local[822]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 12:31:21 DESKTOP-K50P15B postfix/local[823]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 12:32:22 DESKTOP-K50P15B postfix/local[824]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 12:33:23 DESKTOP-K50P15B postfix/local[825]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 12:34:24 DESKTOP-K50P15B postfix/local[826]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 12:35:25 DESKTOP-K50P15B postfix/local[827]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 12:36:26 DESKTOP-K50P15B postfix/local[828]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 12:37:28 DESKTOP-K50P15B postfix/local[829]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 12:38:29 DESKTOP-K50P15B postfix/local[830]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 12:39:30 DESKTOP-K50P15B postfix/local[831]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 12:40:31 DESKTOP-K50P15B postfix/local[832]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 12:41:32 DESKTOP-K50P15B postfix/local[833]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 12:42:33 DESKTOP-K50P15B postfix/local[834]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 12:43:34 DESKTOP-K50P15B postfix/local[835]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 12:44:35 DESKTOP-K50P15B postfix/local[836]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 12:45:36 DESKTOP-K50P15B postfix/local[837]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 12:46:37 DESKTOP-K50P15B postfix/local[838]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 12:47:38 DESKTOP-K50P15B postfix/local[839]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 12:48:39 DESKTOP-K50P15B postfix/local[840]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 12:49:40 DESKTOP-K50P15B postfix/local[841]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 12:50:41 DESKTOP-K50P15B postfix/local[842]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 12:51:43 DESKTOP-K50P15B postfix/local[843]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 12:52:44 DESKTOP-K50P15B postfix/local[844]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 12:53:45 DESKTOP-K50P15B postfix/local[845]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 12:54:46 DESKTOP-K50P15B postfix/local[846]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 12:55:47 DESKTOP-K50P15B postfix/local[847]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 12:56:48 DESKTOP-K50P15B postfix/local[848]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 12:57:49 DESKTOP-K50P15B postfix/local[849]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 12:58:50 DESKTOP-K50P15B postfix/local[850]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 12:59:51 DESKTOP-K50P15B postfix/local[851]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 13:00:52 DESKTOP-K50P15B postfix/local[852]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 13:01:53 DESKTOP-K50P15B postfix/local[853]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 13:02:54 DESKTOP-K50P15B postfix/local[854]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 13:03:55 DESKTOP-K50P15B postfix/local[855]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 13:04:56 DESKTOP-K50P15B postfix/local[856]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 13:05:58 DESKTOP-K50P15B postfix/local[857]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 13:06:59 DESKTOP-K50P15B postfix/local[858]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 13:08:00 DESKTOP-K50P15B postfix/local[859]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 13:09:01 DESKTOP-K50P15B postfix/local[860]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 13:10:02 DESKTOP-K50P15B postfix/local[861]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 13:11:03 DESKTOP-K50P15B postfix/local[862]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 13:12:04 DESKTOP-K50P15B postfix/local[863]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 13:13:05 DESKTOP-K50P15B postfix/local[864]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 13:14:06 DESKTOP-K50P15B postfix/local[865]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 13:15:07 DESKTOP-K50P15B postfix/local[866]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 13:16:08 DESKTOP-K50P15B postfix/local[867]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 13:17:09 DESKTOP-K50P15B postfix/local[868]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 13:18:10 DESKTOP-K50P15B postfix/local[869]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 13:19:11 DESKTOP-K50P15B postfix/local[870]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 13:20:12 DESKTOP-K50P15B postfix/local[871]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 13:21:14 DESKTOP-K50P15B postfix/local[872]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 13:22:15 DESKTOP-K50P15B postfix/local[873]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 13:23:16 DESKTOP-K50P15B postfix/local[874]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 13:24:17 DESKTOP-K50P15B postfix/local[875]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 13:25:18 DESKTOP-K50P15B postfix/local[876]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 13:26:19 DESKTOP-K50P15B postfix/local[877]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 13:27:20 DESKTOP-K50P15B postfix/local[878]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 13:28:21 DESKTOP-K50P15B postfix/local[879]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 13:29:22 DESKTOP-K50P15B postfix/local[880]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 13:30:23 DESKTOP-K50P15B postfix/local[881]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 13:31:24 DESKTOP-K50P15B postfix/local[882]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 13:32:25 DESKTOP-K50P15B postfix/local[883]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 13:33:26 DESKTOP-K50P15B postfix/local[884]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 13:34:27 DESKTOP-K50P15B postfix/local[885]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 13:35:28 DESKTOP-K50P15B postfix/local[886]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 13:36:30 DESKTOP-K50P15B postfix/local[887]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 13:37:31 DESKTOP-K50P15B postfix/local[888]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 13:38:32 DESKTOP-K50P15B postfix/local[889]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 13:39:33 DESKTOP-K50P15B postfix/local[890]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 13:40:34 DESKTOP-K50P15B postfix/local[891]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 13:41:35 DESKTOP-K50P15B postfix/local[892]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 13:42:36 DESKTOP-K50P15B postfix/local[893]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 13:43:37 DESKTOP-K50P15B postfix/local[894]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 13:44:38 DESKTOP-K50P15B postfix/local[895]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 13:45:39 DESKTOP-K50P15B postfix/local[896]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 13:46:40 DESKTOP-K50P15B postfix/local[897]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 13:47:41 DESKTOP-K50P15B postfix/local[898]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 13:48:42 DESKTOP-K50P15B postfix/local[899]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 13:49:43 DESKTOP-K50P15B postfix/local[900]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 13:50:44 DESKTOP-K50P15B postfix/local[901]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 13:51:46 DESKTOP-K50P15B postfix/local[903]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 13:52:47 DESKTOP-K50P15B postfix/local[904]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 13:53:48 DESKTOP-K50P15B postfix/local[905]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 13:57:34 DESKTOP-K50P15B postfix/local[906]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 13:58:35 DESKTOP-K50P15B postfix/local[908]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 13:59:36 DESKTOP-K50P15B postfix/local[909]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 14:00:37 DESKTOP-K50P15B postfix/local[910]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 14:01:38 DESKTOP-K50P15B postfix/local[911]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 14:02:39 DESKTOP-K50P15B postfix/local[912]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 14:03:40 DESKTOP-K50P15B postfix/local[913]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 14:07:40 DESKTOP-K50P15B postfix/local[914]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 14:08:41 DESKTOP-K50P15B postfix/local[916]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 14:09:42 DESKTOP-K50P15B postfix/local[917]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 14:10:43 DESKTOP-K50P15B postfix/local[918]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 14:11:44 DESKTOP-K50P15B postfix/local[919]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 14:12:45 DESKTOP-K50P15B postfix/local[920]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 14:13:46 DESKTOP-K50P15B postfix/local[921]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 14:14:48 DESKTOP-K50P15B postfix/local[937]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 14:15:49 DESKTOP-K50P15B postfix/local[938]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 14:16:50 DESKTOP-K50P15B postfix/local[939]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 14:17:51 DESKTOP-K50P15B postfix/local[940]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 14:18:52 DESKTOP-K50P15B postfix/local[942]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 14:19:53 DESKTOP-K50P15B postfix/local[943]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 14:20:54 DESKTOP-K50P15B postfix/local[944]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 14:21:55 DESKTOP-K50P15B postfix/local[945]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 14:22:56 DESKTOP-K50P15B postfix/local[946]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 14:23:57 DESKTOP-K50P15B postfix/local[947]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 14:26:39 DESKTOP-K50P15B postfix/local[948]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 14:27:41 DESKTOP-K50P15B postfix/local[950]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 14:28:42 DESKTOP-K50P15B postfix/local[951]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 14:29:43 DESKTOP-K50P15B postfix/local[952]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 14:30:44 DESKTOP-K50P15B postfix/local[953]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 14:31:45 DESKTOP-K50P15B postfix/local[954]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 14:32:46 DESKTOP-K50P15B postfix/local[955]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 14:33:47 DESKTOP-K50P15B postfix/local[956]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 14:34:48 DESKTOP-K50P15B postfix/local[957]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 14:35:49 DESKTOP-K50P15B postfix/local[958]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 14:36:50 DESKTOP-K50P15B postfix/local[959]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 14:37:51 DESKTOP-K50P15B postfix/local[960]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 14:38:52 DESKTOP-K50P15B postfix/local[961]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 14:39:53 DESKTOP-K50P15B postfix/local[962]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 14:40:54 DESKTOP-K50P15B postfix/local[963]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 14:41:56 DESKTOP-K50P15B postfix/local[964]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 14:42:57 DESKTOP-K50P15B postfix/local[965]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 14:43:58 DESKTOP-K50P15B postfix/local[966]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 14:44:59 DESKTOP-K50P15B postfix/local[967]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 14:46:00 DESKTOP-K50P15B postfix/local[968]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 14:47:01 DESKTOP-K50P15B postfix/local[969]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 14:48:02 DESKTOP-K50P15B postfix/local[970]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 14:49:03 DESKTOP-K50P15B postfix/local[971]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 18:57:53 DESKTOP-K50P15B postfix/qmgr[741]: fatal: timeout connecting to transport: local
May 31 18:57:53 DESKTOP-K50P15B postfix/local[972]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 20:20:50 DESKTOP-K50P15B postfix/local[976]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 20:21:51 DESKTOP-K50P15B postfix/local[978]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 20:22:52 DESKTOP-K50P15B postfix/local[979]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 20:23:53 DESKTOP-K50P15B postfix/local[980]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 20:24:54 DESKTOP-K50P15B postfix/local[981]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 20:25:55 DESKTOP-K50P15B postfix/local[982]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 20:43:55 DESKTOP-K50P15B postfix/local[983]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 20:44:56 DESKTOP-K50P15B postfix/local[1001]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 20:45:57 DESKTOP-K50P15B postfix/local[1256]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 20:46:58 DESKTOP-K50P15B postfix/local[1257]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 20:47:59 DESKTOP-K50P15B postfix/local[1286]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 20:49:00 DESKTOP-K50P15B postfix/local[1287]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 20:50:01 DESKTOP-K50P15B postfix/local[1288]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 20:51:02 DESKTOP-K50P15B postfix/local[1289]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 20:52:03 DESKTOP-K50P15B postfix/local[1290]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 20:53:05 DESKTOP-K50P15B postfix/local[1291]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 20:54:06 DESKTOP-K50P15B postfix/local[1305]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 20:55:07 DESKTOP-K50P15B postfix/local[1306]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 20:56:08 DESKTOP-K50P15B postfix/local[1307]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 20:57:09 DESKTOP-K50P15B postfix/local[1308]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 20:58:10 DESKTOP-K50P15B postfix/local[1309]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 20:59:11 DESKTOP-K50P15B postfix/local[1310]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 21:00:12 DESKTOP-K50P15B postfix/local[1311]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 21:01:13 DESKTOP-K50P15B postfix/local[1312]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 21:02:14 DESKTOP-K50P15B postfix/local[1313]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 21:03:15 DESKTOP-K50P15B postfix/local[1314]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 21:04:16 DESKTOP-K50P15B postfix/local[1315]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 21:05:17 DESKTOP-K50P15B postfix/local[1316]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 21:06:18 DESKTOP-K50P15B postfix/local[1317]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 21:07:19 DESKTOP-K50P15B postfix/local[1318]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 21:08:20 DESKTOP-K50P15B postfix/local[1319]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 21:09:21 DESKTOP-K50P15B postfix/local[1320]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 21:10:22 DESKTOP-K50P15B postfix/local[1336]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 21:11:23 DESKTOP-K50P15B postfix/local[1354]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 21:12:24 DESKTOP-K50P15B postfix/local[1371]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 21:13:25 DESKTOP-K50P15B postfix/local[1419]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 21:13:33 DESKTOP-K50P15B postfix/local[1597]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 21:14:34 DESKTOP-K50P15B postfix/local[1605]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 21:15:35 DESKTOP-K50P15B postfix/local[1606]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 21:16:36 DESKTOP-K50P15B postfix/local[1607]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 21:17:37 DESKTOP-K50P15B postfix/local[1608]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 21:18:39 DESKTOP-K50P15B postfix/local[1609]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 21:19:40 DESKTOP-K50P15B postfix/local[1610]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 21:20:41 DESKTOP-K50P15B postfix/local[1611]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 21:21:42 DESKTOP-K50P15B postfix/local[1612]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 21:22:43 DESKTOP-K50P15B postfix/local[1613]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 21:23:44 DESKTOP-K50P15B postfix/local[1614]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 21:24:45 DESKTOP-K50P15B postfix/local[1615]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 21:25:46 DESKTOP-K50P15B postfix/local[1616]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 21:26:47 DESKTOP-K50P15B postfix/local[1617]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 21:27:48 DESKTOP-K50P15B postfix/local[1618]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 21:28:49 DESKTOP-K50P15B postfix/local[1619]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 21:29:50 DESKTOP-K50P15B postfix/local[1620]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 21:30:51 DESKTOP-K50P15B postfix/local[1621]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 21:31:52 DESKTOP-K50P15B postfix/local[1622]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 21:32:53 DESKTOP-K50P15B postfix/local[1623]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 21:33:54 DESKTOP-K50P15B postfix/local[1624]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 21:35:01 DESKTOP-K50P15B postfix/local[1625]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 21:36:21 DESKTOP-K50P15B postfix/local[1626]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 21:37:36 DESKTOP-K50P15B postfix/local[1627]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 21:38:56 DESKTOP-K50P15B postfix/local[1628]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 21:40:06 DESKTOP-K50P15B postfix/local[1629]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 21:41:11 DESKTOP-K50P15B postfix/local[1630]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 21:42:23 DESKTOP-K50P15B postfix/local[1631]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 21:43:25 DESKTOP-K50P15B postfix/local[1632]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 21:44:26 DESKTOP-K50P15B postfix/local[1633]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 21:45:27 DESKTOP-K50P15B postfix/local[1634]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 21:46:28 DESKTOP-K50P15B postfix/local[1635]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 21:47:29 DESKTOP-K50P15B postfix/local[1636]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 21:48:30 DESKTOP-K50P15B postfix/local[1637]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 21:49:31 DESKTOP-K50P15B postfix/local[1638]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 21:50:33 DESKTOP-K50P15B postfix/local[1639]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 21:51:34 DESKTOP-K50P15B postfix/local[1640]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 21:52:35 DESKTOP-K50P15B postfix/local[1641]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 21:53:36 DESKTOP-K50P15B postfix/local[1642]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 21:54:37 DESKTOP-K50P15B postfix/local[1643]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 21:55:38 DESKTOP-K50P15B postfix/local[1644]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 21:56:39 DESKTOP-K50P15B postfix/local[1645]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 21:57:40 DESKTOP-K50P15B postfix/local[1646]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 21:58:42 DESKTOP-K50P15B postfix/local[1647]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 21:59:43 DESKTOP-K50P15B postfix/local[1648]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 22:00:44 DESKTOP-K50P15B postfix/local[1649]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 22:01:45 DESKTOP-K50P15B postfix/local[1650]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 22:02:46 DESKTOP-K50P15B postfix/local[1651]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 22:03:47 DESKTOP-K50P15B postfix/local[1652]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 22:04:48 DESKTOP-K50P15B postfix/local[1653]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 22:05:49 DESKTOP-K50P15B postfix/local[1654]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 22:06:50 DESKTOP-K50P15B postfix/local[1655]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 22:07:51 DESKTOP-K50P15B postfix/local[1656]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 22:08:52 DESKTOP-K50P15B postfix/local[1657]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 22:09:54 DESKTOP-K50P15B postfix/local[1658]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 22:10:55 DESKTOP-K50P15B postfix/local[1659]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 22:11:56 DESKTOP-K50P15B postfix/local[1660]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 22:12:57 DESKTOP-K50P15B postfix/local[1661]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 22:13:58 DESKTOP-K50P15B postfix/local[1662]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 22:14:59 DESKTOP-K50P15B postfix/local[1663]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 22:16:00 DESKTOP-K50P15B postfix/local[1664]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 22:17:01 DESKTOP-K50P15B postfix/local[1665]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 22:18:02 DESKTOP-K50P15B postfix/local[1666]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 22:19:03 DESKTOP-K50P15B postfix/local[1667]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 22:20:04 DESKTOP-K50P15B postfix/local[1668]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 22:21:05 DESKTOP-K50P15B postfix/local[1669]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 22:22:07 DESKTOP-K50P15B postfix/local[1670]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 22:23:08 DESKTOP-K50P15B postfix/local[1671]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 22:24:09 DESKTOP-K50P15B postfix/local[1672]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 22:25:10 DESKTOP-K50P15B postfix/local[1673]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 22:26:11 DESKTOP-K50P15B postfix/local[1674]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 22:27:12 DESKTOP-K50P15B postfix/local[1675]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 22:28:13 DESKTOP-K50P15B postfix/local[1676]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 22:29:14 DESKTOP-K50P15B postfix/local[1677]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 22:30:15 DESKTOP-K50P15B postfix/local[1678]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 22:31:16 DESKTOP-K50P15B postfix/local[1679]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 22:32:17 DESKTOP-K50P15B postfix/local[1680]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 22:33:18 DESKTOP-K50P15B postfix/local[1681]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 23:26:52 DESKTOP-K50P15B postfix/local[1682]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 23:27:53 DESKTOP-K50P15B postfix/local[1684]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 23:28:55 DESKTOP-K50P15B postfix/local[1685]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 23:29:56 DESKTOP-K50P15B postfix/local[1686]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 23:30:57 DESKTOP-K50P15B postfix/local[1687]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 23:31:58 DESKTOP-K50P15B postfix/local[1688]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 23:32:59 DESKTOP-K50P15B postfix/local[1689]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 23:34:00 DESKTOP-K50P15B postfix/local[1690]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 23:35:01 DESKTOP-K50P15B postfix/local[1691]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 23:36:02 DESKTOP-K50P15B postfix/local[1692]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 23:37:03 DESKTOP-K50P15B postfix/local[1693]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 23:38:04 DESKTOP-K50P15B postfix/local[1694]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 23:39:05 DESKTOP-K50P15B postfix/local[1695]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 23:40:07 DESKTOP-K50P15B postfix/local[1696]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 23:41:08 DESKTOP-K50P15B postfix/local[1697]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 23:42:09 DESKTOP-K50P15B postfix/local[1698]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 23:43:10 DESKTOP-K50P15B postfix/local[1699]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 23:44:11 DESKTOP-K50P15B postfix/local[1700]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 23:45:13 DESKTOP-K50P15B postfix/local[1701]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 23:46:14 DESKTOP-K50P15B postfix/local[1702]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 23:47:15 DESKTOP-K50P15B postfix/local[1703]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 23:48:16 DESKTOP-K50P15B postfix/local[1704]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 23:49:17 DESKTOP-K50P15B postfix/local[1705]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 23:50:18 DESKTOP-K50P15B postfix/local[1706]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 23:51:19 DESKTOP-K50P15B postfix/local[1707]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 23:52:20 DESKTOP-K50P15B postfix/local[1708]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 23:53:21 DESKTOP-K50P15B postfix/local[1709]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 23:54:22 DESKTOP-K50P15B postfix/local[1710]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 23:55:23 DESKTOP-K50P15B postfix/local[1711]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 23:56:24 DESKTOP-K50P15B postfix/local[1712]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 23:57:25 DESKTOP-K50P15B postfix/local[1713]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 23:58:27 DESKTOP-K50P15B postfix/local[1714]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 23:59:28 DESKTOP-K50P15B postfix/local[1715]: fatal: bad numerical configuration: mailbox_size_limit = 
Jun  1 00:00:29 DESKTOP-K50P15B postfix/local[1716]: fatal: bad numerical configuration: mailbox_size_limit = 
Jun  1 00:01:30 DESKTOP-K50P15B postfix/local[1717]: fatal: bad numerical configuration: mailbox_size_limit = 
[/FONT]
```

---

### Post by rjphares on 2019-06-15
```
[FONT=Verdana]May 31 12:15:02 DESKTOP-K50P15B postfix/master[196]: terminating on signal 15
May 31 12:15:05 DESKTOP-K50P15B postfix/master[737]: daemon started -- version 3.3.0, configuration /etc/postfix
May 31 12:15:05 DESKTOP-K50P15B postfix/qmgr[741]: BA25BA000000036029: from=<rjphares@DESKTOP-K50P15B.localdomain>, size=436, nrcpt=1 (queue active)
May 31 12:15:05 DESKTOP-K50P15B postfix/local[743]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 12:15:06 DESKTOP-K50P15B postfix/master[737]: warning: process /usr/lib/postfix/sbin/local pid 743 exit status 1
May 31 12:15:06 DESKTOP-K50P15B postfix/master[737]: warning: /usr/lib/postfix/sbin/local: bad command startup -- throttling
May 31 12:15:24 DESKTOP-K50P15B postfix/pickup[740]: A1B067000000033AC3: uid=1000 from=<rjphares@DESKTOP-K50P15B.localdomain>
May 31 12:15:24 DESKTOP-K50P15B postfix/cleanup[747]: A1B067000000033AC3: message-id=<20190531161524.A1B067000000033AC3@rjphares.localdomain>
May 31 12:15:24 DESKTOP-K50P15B postfix/qmgr[741]: A1B067000000033AC3: from=<rjphares@DESKTOP-K50P15B.localdomain>, size=422, nrcpt=2 (queue active)
May 31 12:15:24 DESKTOP-K50P15B postfix/error[748]: A1B067000000033AC3: to=<d@DESKTOP-K50P15B.localdomain>, relay=none, delay=0.16, delays=0.06/0.04/0/0.06, dsn=5.0.0, status=bounced (DESKTOP-K50P15B.localdomain)
May 31 12:15:44 DESKTOP-K50P15B postfix/pickup[740]: 757166000000033AC8: uid=1000 from=<rjphares@DESKTOP-K50P15B.localdomain>
May 31 12:15:44 DESKTOP-K50P15B postfix/cleanup[747]: 757166000000033AC8: message-id=<20190531161544.757166000000033AC8@rjphares.localdomain>
May 31 12:15:44 DESKTOP-K50P15B postfix/qmgr[741]: 757166000000033AC8: from=<rjphares@DESKTOP-K50P15B.localdomain>, size=424, nrcpt=2 (queue active)
May 31 12:15:44 DESKTOP-K50P15B postfix/error[748]: 757166000000033AC8: to=<root@DESKTOP-K50P15B>, relay=none, delay=0.04, delays=0.03/0/0/0.01, dsn=5.0.0, status=bounced (DESKTOP-K50P15B)
May 31 12:15:44 DESKTOP-K50P15B postfix/error[748]: 757166000000033AC8: to=<D@DESKTOP-K50P15B.localdomain>, relay=none, delay=0.06, delays=0.03/0.02/0/0.01, dsn=5.0.0, status=bounced (DESKTOP-K50P15B.localdomain)
May 31 12:15:44 DESKTOP-K50P15B postfix/cleanup[747]: 814057000000033AC6: message-id=<20190531161544.814057000000033AC6@rjphares.localdomain>
May 31 12:15:44 DESKTOP-K50P15B postfix/bounce[749]: 757166000000033AC8: sender non-delivery notification: 814057000000033AC6
May 31 12:15:44 DESKTOP-K50P15B postfix/qmgr[741]: 814057000000033AC6: from=<>, size=2698, nrcpt=1 (queue active)
May 31 12:15:44 DESKTOP-K50P15B postfix/qmgr[741]: 757166000000033AC8: removed
[/FONT][FONT=Verdana,Arial,Tahoma,Calibri,Geneva,sans-serif]May 31 12:15:59 DESKTOP-K50P15B postfix/pickup[740]: D380B7000000033AC8: uid=1000 from=<rjphares@DESKTOP-K50P15B.localdomain>
May 31 12:15:59 DESKTOP-K50P15B postfix/cleanup[747]: D380B7000000033AC8: message-id=<20190531161559.D380B7000000033AC8@rjphares.localdomain>
May 31 12:15:59 DESKTOP-K50P15B postfix/qmgr[741]: D380B7000000033AC8: from=<rjphares@DESKTOP-K50P15B.localdomain>, size=445, nrcpt=2 (queue active)
May 31 12:15:59 DESKTOP-K50P15B postfix/error[754]: D380B7000000033AC8: to=<ROOT@DESKTOP-K50P15B.localdomain>, relay=none, delay=0.04, delays=0.03/0/0/0.01, dsn=5.0.0, status=bounced (DESKTOP-K50P15B.localdomain)
May 31 12:15:59 DESKTOP-K50P15B postfix/error[754]: D380B7000000033AC8: to=<mail@DESKTOP-K50P15B.localdomain>, relay=none, delay=0.05, delays=0.03/0/0/0.02, dsn=5.0.0, status=bounced (DESKTOP-K50P15B.localdomain)
May 31 12:15:59 DESKTOP-K50P15B postfix/cleanup[747]: DDAF19000000033AC6: message-id=<20190531161559.DDAF19000000033AC6@rjphares.localdomain>
May 31 12:15:59 DESKTOP-K50P15B postfix/bounce[749]: D380B7000000033AC8: sender non-delivery notification: DDAF19000000033AC6
May 31 12:15:59 DESKTOP-K50P15B postfix/qmgr[741]: DDAF19000000033AC6: from=<>, size=2788, nrcpt=1 (queue active)
May 31 12:15:59 DESKTOP-K50P15B postfix/qmgr[741]: D380B7000000033AC8: removed
May 31 12:15:59 DESKTOP-K50P15B postfix/error[748]: DDAF19000000033AC6: to=<rjphares@DESKTOP-K50P15B.localdomain>, relay=none, delay=0.03, delays=0.02/0/0/0.01, dsn=5.0.0, status=bounced (DESKTOP-K50P15B.localdomain)
May 31 12:15:59 DESKTOP-K50P15B postfix/qmgr[741]: DDAF19000000033AC6: removed
May 31 12:16:06 DESKTOP-K50P15B postfix/local[776]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 12:16:07 DESKTOP-K50P15B postfix/master[737]: warning: process /usr/lib/postfix/sbin/local pid 776 exit status 1
May 31 12:16:07 DESKTOP-K50P15B postfix/master[737]: warning: /usr/lib/postfix/sbin/local: bad command startup -- throttling
May 31 12:16:16 DESKTOP-K50P15B postfix/pickup[740]: 6B8138000000033AC8: uid=0 from=<root@DESKTOP-K50P15B.localdomain>
May 31 12:16:16 DESKTOP-K50P15B postfix/cleanup[747]: 6B8138000000033AC8: message-id=<20190531161616.6B8138000000033AC8@rjphares.localdomain>
May 31 12:16:16 DESKTOP-K50P15B postfix/qmgr[741]: 6B8138000000033AC8: from=<root@DESKTOP-K50P15B.localdomain>, size=422, nrcpt=2 (queue active)
May 31 12:16:16 DESKTOP-K50P15B postfix/error[754]: 6B8138000000033AC8: to=<d@DESKTOP-K50P15B.localdomain>, relay=none, delay=0.04, delays=0.03/0/0/0.01, dsn=5.0.0, status=bounced (DESKTOP-K50P15B.localdomain)
May 31 12:16:16 DESKTOP-K50P15B postfix/error[754]: 6B8138000000033AC8: to=<rjphares@DESKTOP-K50P15B.localdomain>, relay=none, delay=0.05, delays=0.03/0/0/0.02, dsn=5.0.0, status=bounced (DESKTOP-K50P15B.localdomain)
May 31 12:16:16 DESKTOP-K50P15B postfix/cleanup[747]: 75C48B000000033AC6: message-id=<20190531161616.75C48B000000033AC6@rjphares.localdomain>
May 31 12:16:16 DESKTOP-K50P15B postfix/bounce[749]: 6B8138000000033AC8: sender non-delivery notification: 75C48B000000033AC6
May 31 12:16:16 DESKTOP-K50P15B postfix/qmgr[741]: 75C48B000000033AC6: from=<>, size=2756, nrcpt=1 (queue active)
May 31 12:16:16 DESKTOP-K50P15B postfix/qmgr[741]: 6B8138000000033AC8: removed
May 31 12:16:16 DESKTOP-K50P15B postfix/error[748]: 75C48B000000033AC6: to=<root@DESKTOP-K50P15B.localdomain>, relay=none, delay=0.03, delays=0.02/0/0/0.01, dsn=5.0.0, status=bounced (DESKTOP-K50P15B.localdomain)
May 31 12:16:16 DESKTOP-K50P15B postfix/qmgr[741]: 75C48B000000033AC6: removed
May 31 12:17:07 DESKTOP-K50P15B postfix/local[809]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 12:17:08 DESKTOP-K50P15B postfix/master[737]: warning: process /usr/lib/postfix/sbin/local pid 809 exit status 1
May 31 12:17:08 DESKTOP-K50P15B postfix/master[737]: warning: /usr/lib/postfix/sbin/local: bad command startup -- throttling
May 31 12:18:08 DESKTOP-K50P15B postfix/local[810]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 12:18:09 DESKTOP-K50P15B postfix/master[737]: warning: process /usr/lib/postfix/sbin/local pid 810 exit status 1
May 31 12:18:09 DESKTOP-K50P15B postfix/master[737]: warning: /usr/lib/postfix/sbin/local: bad command startup -- throttling
May 31 12:19:09 DESKTOP-K50P15B postfix/local[811]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 12:19:10 DESKTOP-K50P15B postfix/master[737]: warning: process /usr/lib/postfix/sbin/local pid 811 exit status 1
May 31 12:19:10 DESKTOP-K50P15B postfix/master[737]: warning: /usr/lib/postfix/sbin/local: bad command startup -- throttling
May 31 12:20:10 DESKTOP-K50P15B postfix/local[812]: fatal: bad numerical configuration: mailbox_size_limit = 
May 31 12:20:11 DESKTOP-K50P15B postfix/master[737]: warning: process /usr/lib/postfix/sbin/local pid 812 exit status 1
May 31 12:20:11 DESKTOP-K50P15B postfix/master[737]: warning: /usr/lib/postfix/sbin/local: bad command startup -- throttling[/FONT]
```

---

### Post by SeijiSensei on 2019-06-16
First you need to fix this.

```
May 31 12:17:07 DESKTOP-K50P15B postfix/local[809]: fatal: bad numerical configuration: mailbox_size_limit = 
```

I presume it expects a number, not a blank entry.

When the error begins with "fatal" it means exactly what it says.

---

### Post by rjphares on 2019-06-16
I'm not sure what I typed into the terminal to produce that output. But I am unable to recreate the message. I also changed the mail size and still got "no mail for rjphares"

---

### Post by kevdog on 2019-06-16
Can you post the postfix conf file again please

---

### Post by rjphares on 2019-06-16
```

[FONT=Verdana,Arial,Tahoma,Calibri,Geneva,sans-serif]# Global Postfix configuration file. This file lists only a subset
# of all parameters. For the syntax, and for a complete parameter
# list, see the postconf(5) manual page (command: "man 5 postconf").
#
# For common configuration examples, see BASIC_CONFIGURATION_README
# and STANDARD_CONFIGURATION_README. To find these documents, use
# the command "postconf html_directory readme_directory", or go to
# http://www.postfix.org/BASIC_CONFIGURATION_README.html etc.
#
# For best results, change no more than 2-3 parameters at a time,
# and test if Postfix still works after every change.[/FONT]
[FONT=Verdana,Arial,Tahoma,Calibri,Geneva,sans-serif]# COMPATIBILITY
#
# The compatibility_level determines what default settings Postfix
# will use for main.cf and master.cf settings. These defaults will
# change over time.
#
# To avoid breaking things, Postfix will use backwards-compatible
# default settings and log where it uses those old backwards-compatible
# default settings, until the system administrator has determined
# if any backwards-compatible default settings need to be made
# permanent in main.cf or master.cf.
#
# When this review is complete, update the compatibility_level setting
# below as recommended in the RELEASE_NOTES file.
#
# The level below is what should be used with new (not upgrade) installs.
#
compatibility_level = 2[/FONT]
[FONT=Verdana,Arial,Tahoma,Calibri,Geneva,sans-serif]# SOFT BOUNCE
#
# The soft_bounce parameter provides a limited safety net for
# testing.  When soft_bounce is enabled, mail will remain queued that
# would otherwise bounce. This parameter disables locally-generated
# bounces, and prevents the SMTP server from rejecting mail permanently
# (by changing 5xx replies into 4xx replies). However, soft_bounce
# is no cure for address rewriting mistakes or mail routing mistakes.
#
#soft_bounce = no[/FONT]
[FONT=Verdana,Arial,Tahoma,Calibri,Geneva,sans-serif]# LOCAL PATHNAME INFORMATION
#
# The queue_directory specifies the location of the Postfix queue.
# This is also the root directory of Postfix daemons that run chrooted.
# See the files in examples/chroot-setup for setting up Postfix chroot
# environments on different UNIX systems.
#
#queue_directory = /var/spool/postfix[/FONT]
[FONT=Verdana,Arial,Tahoma,Calibri,Geneva,sans-serif]# The command_directory parameter specifies the location of all
# postXXX commands.
#
command_directory = /usr/sbin[/FONT]
[FONT=Verdana,Arial,Tahoma,Calibri,Geneva,sans-serif]# The daemon_directory parameter specifies the location of all Postfix
# daemon programs (i.e. programs listed in the master.cf file). This
# directory must be owned by root.
#
daemon_directory = /usr/lib/postfix/sbin[/FONT]
[FONT=Verdana,Arial,Tahoma,Calibri,Geneva,sans-serif]# The data_directory parameter specifies the location of Postfix-writable
# data files (caches, random numbers). This directory must be owned
# by the mail_owner account (see below).
#
data_directory = /var/lib/postfix[/FONT]
[FONT=Verdana,Arial,Tahoma,Calibri,Geneva,sans-serif]# QUEUE AND PROCESS OWNERSHIP
#
# The mail_owner parameter specifies the owner of the Postfix queue
# and of most Postfix daemon processes.  Specify the name of a user
# account THAT DOES NOT SHARE ITS USER OR GROUP ID WITH OTHER ACCOUNTS
# AND THAT OWNS NO OTHER FILES OR PROCESSES ON THE SYSTEM.  In
# particular, don't specify nobody or daemon. PLEASE USE A DEDICATED
# USER.
#
mail_owner = postfix[/FONT]
[FONT=Verdana,Arial,Tahoma,Calibri,Geneva,sans-serif]# The default_privs parameter specifies the default rights used by
# the local delivery agent for delivery to external file or command.
# These rights are used in the absence of a recipient user context.
# DO NOT SPECIFY A PRIVILEGED USER OR THE POSTFIX OWNER.
#
#default_privs = nobody[/FONT]
[FONT=Verdana,Arial,Tahoma,Calibri,Geneva,sans-serif]# INTERNET HOST AND DOMAIN NAMES
# 
# The myhostname parameter specifies the internet hostname of this
# mail system. The default is to use the fully-qualified domain name
# from gethostname(). $myhostname is used as a default value for many
# other configuration parameters.
#
myhostname = rjphares.localdomain
#myhostname = virtual.domain.tld[/FONT]
[FONT=Verdana,Arial,Tahoma,Calibri,Geneva,sans-serif]# The mydomain parameter specifies the local internet domain name.
# The default is to use $myhostname minus the first component.
# $mydomain is used as a default value for many other configuration
# parameters.
#
mydomain = gmail.com[/FONT]
[FONT=Verdana,Arial,Tahoma,Calibri,Geneva,sans-serif]# SENDING MAIL
# 
# The myorigin parameter specifies the domain that locally-posted
# mail appears to come from. The default is to append $myhostname,
# which is fine for small sites.  If you run a domain with multiple
# machines, you should (1) change this to $mydomain and (2) set up
# a domain-wide alias database that aliases each user to
# user@that.users.mailhost.
#
# For the sake of consistency between sender and recipient addresses,
# myorigin also specifies the default domain name that is appended
# to recipient addresses that have no @domain part.
#
# Debian GNU/Linux specific:  Specifying a file name will cause the
# first line of that file to be used as the name.  The Debian default
# is /etc/mailname.
#
#myorigin = /etc/mailname
#myorigin = $myhostname
#myorigin = $mydomain[/FONT]
[FONT=Verdana,Arial,Tahoma,Calibri,Geneva,sans-serif]# RECEIVING MAIL[/FONT]
[FONT=Verdana,Arial,Tahoma,Calibri,Geneva,sans-serif]# The inet_interfaces parameter specifies the network interface
# addresses that this mail system receives mail on.  By default,
# the software claims all active interfaces on the machine. The
# parameter also controls delivery of mail to user@[ip.address].
#
# See also the proxy_interfaces parameter, for network addresses that
# are forwarded to us via a proxy or network address translator.
#
# Note: you need to stop/start Postfix when this parameter changes.
#
inet_interfaces = loopback-only
#inet_interfaces = $myhostname
#inet_interfaces = $myhostname, localhost[/FONT]
[FONT=Verdana,Arial,Tahoma,Calibri,Geneva,sans-serif]# The proxy_interfaces parameter specifies the network interface
# addresses that this mail system receives mail on by way of a
# proxy or network address translation unit. This setting extends
# the address list specified with the inet_interfaces parameter.
#
# You must specify your proxy/NAT addresses when your system is a
# backup MX host for other domains, otherwise mail delivery loops
# will happen when the primary MX host is down.
#
#proxy_interfaces =
#proxy_interfaces = 1.2.3.4[/FONT]
[FONT=Verdana,Arial,Tahoma,Calibri,Geneva,sans-serif]# The mydestination parameter specifies the list of domains that this
# machine considers itself the final destination for.
#
# These domains are routed to the delivery agent specified with the
# local_transport parameter setting. By default, that is the UNIX
# compatible delivery agent that lookups all recipients in /etc/passwd
# and /etc/aliases or their equivalent.
#
# The default is $myhostname + localhost.$mydomain + localhost.  On
# a mail domain gateway, you should also include $mydomain.
#
# Do not specify the names of virtual domains - those domains are
# specified elsewhere (see VIRTUAL_README).
#
# Do not specify the names of domains that this machine is backup MX
# host for. Specify those names via the relay_domains settings for
# the SMTP server, or use permit_mx_backup if you are lazy (see
# STANDARD_CONFIGURATION_README).
#
# The local machine is always the final destination for mail addressed
# to user@[the.net.work.address] of an interface that the mail system
# receives mail on (see the inet_interfaces parameter).
#
# Specify a list of host or domain names, /file/name or type:table
# patterns, separated by commas and/or whitespace. A /file/name
# pattern is replaced by its contents; a type:table is matched when
# a name matches a lookup key (the right-hand side is ignored).
# Continue long lines by starting the next line with whitespace.
#
# See also below, section "REJECTING MAIL FOR UNKNOWN LOCAL USERS".
#
#mydestination = $myhostname, localhost.$mydomain, localhost
mydestination = mail.gmail.com, localhost.gmail.com, localhost, gmail.com
#mydestination = $myhostname, localhost.$mydomain, localhost, $mydomain,
# mail.$mydomain, www.$mydomain, ftp.$mydomain[/FONT]
[FONT=Verdana,Arial,Tahoma,Calibri,Geneva,sans-serif]# REJECTING MAIL FOR UNKNOWN LOCAL USERS
#
# The local_recipient_maps parameter specifies optional lookup tables
# with all names or addresses of users that are local with respect
# to $mydestination, $inet_interfaces or $proxy_interfaces.
#
# If this parameter is defined, then the SMTP server will reject
# mail for unknown local users. This parameter is defined by default.
#
# To turn off local recipient checking in the SMTP server, specify
# local_recipient_maps = (i.e. empty).
#
# The default setting assumes that you use the default Postfix local
# delivery agent for local delivery. You need to update the
# local_recipient_maps setting if:
#
# - You define $mydestination domain recipients in files other than
#   /etc/passwd, /etc/aliases, or the $virtual_alias_maps files.
#   For example, you define $mydestination domain recipients in    
#   the $virtual_mailbox_maps files.
#
# - You redefine the local delivery agent in master.cf.
#
# - You redefine the "local_transport" setting in main.cf.
#
# - You use the "luser_relay", "mailbox_transport", or "fallback_transport"
#   feature of the Postfix local delivery agent (see local(8)).
#
# Details are described in the LOCAL_RECIPIENT_README file.
#
# Beware: if the Postfix SMTP server runs chrooted, you probably have
# to access the passwd file via the proxymap service, in order to
# overcome chroot restrictions. The alternative, having a copy of
# the system passwd file in the chroot jail is just not practical.
#
# The right-hand side of the lookup tables is conveniently ignored.
# In the left-hand side, specify a bare username, an @domain.tld
# wild-card, or specify a user@domain.tld address.
# 
local_recipient_maps = unix:passwd.byname $alias_maps
#local_recipient_maps = proxy:unix:passwd.byname $alias_maps
#local_recipient_maps =[/FONT]
[FONT=Verdana,Arial,Tahoma,Calibri,Geneva,sans-serif]# The unknown_local_recipient_reject_code specifies the SMTP server
# response code when a recipient domain matches $mydestination or
# ${proxy,inet}_interfaces, while $local_recipient_maps is non-empty
# and the recipient address or address local-part is not found.
#
# The default setting is 550 (reject mail) but it is safer to start
# with 450 (try again later) until you are certain that your
# local_recipient_maps settings are OK.
#
unknown_local_recipient_reject_code = 550[/FONT]
[FONT=Verdana,Arial,Tahoma,Calibri,Geneva,sans-serif]# TRUST AND RELAY CONTROL[/FONT]
[FONT=Verdana,Arial,Tahoma,Calibri,Geneva,sans-serif]# The mynetworks parameter specifies the list of "trusted" SMTP
# clients that have more privileges than "strangers".
#
# In particular, "trusted" SMTP clients are allowed to relay mail
# through Postfix.  See the smtpd_recipient_restrictions parameter
# in postconf(5).
#
# You can specify the list of "trusted" network addresses by hand
# or you can let Postfix do it for you (which is the default).
#
# By default (mynetworks_style = subnet), Postfix "trusts" SMTP
# clients in the same IP subnetworks as the local machine.
# On Linux, this does works correctly only with interfaces specified
# with the "ifconfig" command.
# 
# Specify "mynetworks_style = class" when Postfix should "trust" SMTP
# clients in the same IP class A/B/C networks as the local machine.
# Don't do this with a dialup site - it would cause Postfix to "trust"
# your entire provider's network.  Instead, specify an explicit
# mynetworks list by hand, as described below.
#  
# Specify "mynetworks_style = host" when Postfix should "trust"
# only the local machine.
# 
#mynetworks_style = class
#mynetworks_style = subnet
mynetworks_style = host[/FONT]
[FONT=Verdana,Arial,Tahoma,Calibri,Geneva,sans-serif]# Alternatively, you can specify the mynetworks list by hand, in
# which case Postfix ignores the mynetworks_style setting.
#
# Specify an explicit list of network/netmask patterns, where the
# mask specifies the number of bits in the network part of a host
# address.
#
# You can also specify the absolute pathname of a pattern file instead
# of listing the patterns here. Specify type:table for table-based lookups
# (the value on the table right-hand side is not used).
#
#mynetworks = 168.100.189.0/28, 127.0.0.0/8
#mynetworks = $config_directory/mynetworks
#mynetworks = hash:/etc/postfix/network_table
#mynetworks = 127.0.0.0/8, 10.0.0.0/24[/FONT]
[FONT=Verdana,Arial,Tahoma,Calibri,Geneva,sans-serif]# The relay_domains parameter restricts what destinations this system will
# relay mail to.  See the smtpd_recipient_restrictions description in
# postconf(5) for detailed information.
#
# By default, Postfix relays mail
# - from "trusted" clients (IP address matches $mynetworks) to any destination,
# - from "untrusted" clients to destinations that match $relay_domains or
#   subdomains thereof, except addresses with sender-specified routing.
# The default relay_domains value is $mydestination.
# 
# In addition to the above, the Postfix SMTP server by default accepts mail
# that Postfix is final destination for:
# - destinations that match $inet_interfaces or $proxy_interfaces,
# - destinations that match $mydestination
# - destinations that match $virtual_alias_domains,
# - destinations that match $virtual_mailbox_domains.
# These destinations do not need to be listed in $relay_domains.
# 
# Specify a list of hosts or domains, /file/name patterns or type:name
# lookup tables, separated by commas and/or whitespace.  Continue
# long lines by starting the next line with whitespace. A file name
# is replaced by its contents; a type:name table is matched when a
# (parent) domain appears as lookup key.
#
# NOTE: Postfix will not automatically forward mail for domains that
# list this system as their primary or backup MX host. See the
# permit_mx_backup restriction description in postconf(5).
#
#relay_domains = $mydestination[/FONT]
[FONT=Verdana,Arial,Tahoma,Calibri,Geneva,sans-serif]# INTERNET OR INTRANET[/FONT]
[FONT=Verdana,Arial,Tahoma,Calibri,Geneva,sans-serif]# The relayhost parameter specifies the default host to send mail to
# when no entry is matched in the optional transport(5) table. When
# no relayhost is given, mail is routed directly to the destination.
#
# On an intranet, specify the organizational domain name. If your
# internal DNS uses no MX records, specify the name of the intranet
# gateway host instead.
#
# In the case of SMTP, specify a domain, host, host:port, [host]:port,
# [address] or [address]:port; the form [host] turns off MX lookups.
#
# If you're connected via UUCP, see also the default_transport parameter.
#
#relayhost = $mydomain
#relayhost = [gateway.my.domain]
#relayhost = [mailserver.isp.tld]
#relayhost = uucphost
#relayhost = [an.ip.add.ress][/FONT]
[FONT=Verdana,Arial,Tahoma,Calibri,Geneva,sans-serif]# REJECTING UNKNOWN RELAY USERS
#
# The relay_recipient_maps parameter specifies optional lookup tables
# with all addresses in the domains that match $relay_domains.
#
# If this parameter is defined, then the SMTP server will reject
# mail for unknown relay users. This feature is off by default.
#
# The right-hand side of the lookup tables is conveniently ignored.
# In the left-hand side, specify an @domain.tld wild-card, or specify
# a user@domain.tld address.
# 
#relay_recipient_maps = hash:/etc/postfix/relay_recipients[/FONT]
[FONT=Verdana,Arial,Tahoma,Calibri,Geneva,sans-serif]# INPUT RATE CONTROL
#
# The in_flow_delay configuration parameter implements mail input
# flow control. This feature is turned on by default, although it
# still needs further development (it's disabled on SCO UNIX due
# to an SCO bug).
# 
# A Postfix process will pause for $in_flow_delay seconds before
# accepting a new message, when the message arrival rate exceeds the
# message delivery rate. With the default 100 SMTP server process
# limit, this limits the mail inflow to 100 messages a second more
# than the number of messages delivered per second.
# 
# Specify 0 to disable the feature. Valid delays are 0..10.
# 
#in_flow_delay = 1s[/FONT]
[FONT=Verdana,Arial,Tahoma,Calibri,Geneva,sans-serif]# ADDRESS REWRITING
#
# The ADDRESS_REWRITING_README document gives information about
# address masquerading or other forms of address rewriting including
# username->Firstname.Lastname mapping.[/FONT]
[FONT=Verdana,Arial,Tahoma,Calibri,Geneva,sans-serif]# ADDRESS REDIRECTION (VIRTUAL DOMAIN)
#
# The VIRTUAL_README document gives information about the many forms
# of domain hosting that Postfix supports.[/FONT]
[FONT=Verdana,Arial,Tahoma,Calibri,Geneva,sans-serif]# "USER HAS MOVED" BOUNCE MESSAGES
#
# See the discussion in the ADDRESS_REWRITING_README document.[/FONT]
[FONT=Verdana,Arial,Tahoma,Calibri,Geneva,sans-serif]# TRANSPORT MAP
#
# See the discussion in the ADDRESS_REWRITING_README document.[/FONT]
[FONT=Verdana,Arial,Tahoma,Calibri,Geneva,sans-serif]# ALIAS DATABASE
#
# The alias_maps parameter specifies the list of alias databases used
# by the local delivery agent. The default list is system dependent.
#
# On systems with NIS, the default is to search the local alias
# database, then the NIS alias database. See aliases(5) for syntax
# details.
# 
# If you change the alias database, run "postalias /etc/aliases" (or
# wherever your system stores the mail alias file), or simply run
# "newaliases" to build the necessary DBM or DB file.
#
# It will take a minute or so before changes become visible.  Use
# "postfix reload" to eliminate the delay.
#
#alias_maps = dbm:/etc/aliases
alias_maps = hash:/etc/aliases
#alias_maps = hash:/etc/aliases, nis:mail.aliases
#alias_maps = netinfo:/aliases[/FONT]
[FONT=Verdana,Arial,Tahoma,Calibri,Geneva,sans-serif]# The alias_database parameter specifies the alias database(s) that
# are built with "newaliases" or "sendmail -bi".  This is a separate
# configuration parameter, because alias_maps (see above) may specify
# tables that are not necessarily all under control by Postfix.
#
#alias_database = dbm:/etc/aliases
#alias_database = dbm:/etc/mail/aliases
alias_database = hash:/etc/aliases
#alias_database = hash:/etc/aliases, hash:/opt/majordomo/aliases[/FONT]
[FONT=Verdana,Arial,Tahoma,Calibri,Geneva,sans-serif]# ADDRESS EXTENSIONS (e.g., user+foo)
#
# The recipient_delimiter parameter specifies the separator between
# user names and address extensions (user+foo). See canonical(5),
# local(8), relocated(5) and virtual(5) for the effects this has on
# aliases, canonical, virtual, relocated and .forward file lookups.
# Basically, the software tries user+foo and .forward+foo before
# trying user and .forward.
#
#recipient_delimiter = +[/FONT]
[FONT=Verdana,Arial,Tahoma,Calibri,Geneva,sans-serif]# DELIVERY TO MAILBOX
#
# The home_mailbox parameter specifies the optional pathname of a
# mailbox file relative to a user's home directory. The default
# mailbox file is /var/spool/mail/user or /var/mail/user.  Specify
# "Maildir/" for qmail-style delivery (the / is required).
#
#home_mailbox = Mailbox
home_mailbox = Maildir/
 
# The mail_spool_directory parameter specifies the directory where
# UNIX-style mailboxes are kept. The default setting depends on the
# system type.
#
#mail_spool_directory = /var/mail
#mail_spool_directory = /var/spool/mail[/FONT]
[FONT=Verdana,Arial,Tahoma,Calibri,Geneva,sans-serif]# The mailbox_command parameter specifies the optional external
# command to use instead of mailbox delivery. The command is run as
# the recipient with proper HOME, SHELL and LOGNAME environment settings.
# Exception:  delivery for root is done as $default_user.
#
# Other environment variables of interest: USER (recipient username),
# EXTENSION (address extension), DOMAIN (domain part of address),
# and LOCAL (the address localpart).
#
# Unlike other Postfix configuration parameters, the mailbox_command
# parameter is not subjected to $parameter substitutions. This is to
# make it easier to specify shell syntax (see example below).
#
# Avoid shell meta characters because they will force Postfix to run
# an expensive shell process. Procmail alone is expensive enough.
#
# IF YOU USE THIS TO DELIVER MAIL SYSTEM-WIDE, YOU MUST SET UP AN
# ALIAS THAT FORWARDS MAIL FOR ROOT TO A REAL USER.
#
#mailbox_command = /usr/bin/procmail
#mailbox_command = /usr/bin/procmail -a "$EXTENSION"[/FONT]
[FONT=Verdana,Arial,Tahoma,Calibri,Geneva,sans-serif]# The mailbox_transport specifies the optional transport in master.cf
# to use after processing aliases and .forward files. This parameter
# has precedence over the mailbox_command, fallback_transport and
# luser_relay parameters.
#
# Specify a string of the form transport:nexthop, where transport is
# the name of a mail delivery transport defined in master.cf.  The
# :nexthop part is optional. For more details see the sample transport
# configuration file.
#
# NOTE: if you use this feature for accounts not in the UNIX password
# file, then you must update the "local_recipient_maps" setting in
# the main.cf file, otherwise the SMTP server will reject mail for    
# non-UNIX accounts with "User unknown in local recipient table".
#
# Cyrus IMAP over LMTP. Specify ``lmtpunix      cmd="lmtpd"
# listen="/var/imap/socket/lmtp" prefork=0'' in cyrus.conf.
#mailbox_transport = lmtp:unix:/var/imap/socket/lmtp
#
# Cyrus IMAP via command line. Uncomment the "cyrus...pipe" and
# subsequent line in master.cf.
#mailbox_transport = cyrus[/FONT]
[FONT=Verdana,Arial,Tahoma,Calibri,Geneva,sans-serif]# The fallback_transport specifies the optional transport in master.cf
# to use for recipients that are not found in the UNIX passwd database.
# This parameter has precedence over the luser_relay parameter.
#
# Specify a string of the form transport:nexthop, where transport is
# the name of a mail delivery transport defined in master.cf.  The
# :nexthop part is optional. For more details see the sample transport
# configuration file.
#
# NOTE: if you use this feature for accounts not in the UNIX password
# file, then you must update the "local_recipient_maps" setting in
# the main.cf file, otherwise the SMTP server will reject mail for    
# non-UNIX accounts with "User unknown in local recipient table".
#
#fallback_transport = lmtp:unix:/file/name
#fallback_transport = cyrus
#fallback_transport =[/FONT]
[FONT=Verdana,Arial,Tahoma,Calibri,Geneva,sans-serif]# The luser_relay parameter specifies an optional destination address
# for unknown recipients.  By default, mail for unknown@$mydestination,
# unknown@[$inet_interfaces] or unknown@[$proxy_interfaces] is returned
# as undeliverable.
#
# The following expansions are done on luser_relay: $user (recipient
# username), $shell (recipient shell), $home (recipient home directory),
# $recipient (full recipient address), $extension (recipient address
# extension), $domain (recipient domain), $local (entire recipient
# localpart), $recipient_delimiter. Specify ${name?value} or
# ${name:value} to expand value only when $name does (does not) exist.
#
# luser_relay works only for the default Postfix local delivery agent.
#
# NOTE: if you use this feature for accounts not in the UNIX password
# file, then you must specify "local_recipient_maps =" (i.e. empty) in
# the main.cf file, otherwise the SMTP server will reject mail for    
# non-UNIX accounts with "User unknown in local recipient table".
#
#luser_relay = $user@other.host
#luser_relay = $local@other.host
#luser_relay = admin+$local
  
# JUNK MAIL CONTROLS
# 
# The controls listed here are only a very small subset. The file
# SMTPD_ACCESS_README provides an overview.[/FONT]
[FONT=Verdana,Arial,Tahoma,Calibri,Geneva,sans-serif]# The header_checks parameter specifies an optional table with patterns
# that each logical message header is matched against, including
# headers that span multiple physical lines.
#
# By default, these patterns also apply to MIME headers and to the
# headers of attached messages. With older Postfix versions, MIME and
# attached message headers were treated as body text.
#
# For details, see "man header_checks".
#
#header_checks = regexp:/etc/postfix/header_checks[/FONT]
[FONT=Verdana,Arial,Tahoma,Calibri,Geneva,sans-serif]# FAST ETRN SERVICE
#
# Postfix maintains per-destination logfiles with information about
# deferred mail, so that mail can be flushed quickly with the SMTP
# "ETRN domain.tld" command, or by executing "sendmail -qRdomain.tld".
# See the ETRN_README document for a detailed description.
# 
# The fast_flush_domains parameter controls what destinations are
# eligible for this service. By default, they are all domains that
# this server is willing to relay mail to.
# 
#fast_flush_domains = $relay_domains[/FONT]
[FONT=Verdana,Arial,Tahoma,Calibri,Geneva,sans-serif]# SHOW SOFTWARE VERSION OR NOT
#
# The smtpd_banner parameter specifies the text that follows the 220
# code in the SMTP server's greeting banner. Some people like to see
# the mail version advertised. By default, Postfix shows no version.
#
# You MUST specify $myhostname at the start of the text. That is an
# RFC requirement. Postfix itself does not care.
#
#smtpd_banner = $myhostname ESMTP $mail_name
#smtpd_banner = $myhostname ESMTP $mail_name ($mail_version)
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)[/FONT]
[FONT=Verdana,Arial,Tahoma,Calibri,Geneva,sans-serif]
# PARALLEL DELIVERY TO THE SAME DESTINATION
#
# How many parallel deliveries to the same user or domain? With local
# delivery, it does not make sense to do massively parallel delivery
# to the same user, because mailbox updates must happen sequentially,
# and expensive pipelines in .forward files can cause disasters when
# too many are run at the same time. With SMTP deliveries, 10
# simultaneous connections to the same domain could be sufficient to
# raise eyebrows.
# 
# Each message delivery transport has its XXX_destination_concurrency_limit
# parameter.  The default is $default_destination_concurrency_limit for
# most delivery transports. For the local delivery agent the default is 2.[/FONT]
[FONT=Verdana,Arial,Tahoma,Calibri,Geneva,sans-serif]#local_destination_concurrency_limit = 2
#default_destination_concurrency_limit = 20[/FONT]
[FONT=Verdana,Arial,Tahoma,Calibri,Geneva,sans-serif]# DEBUGGING CONTROL
#
# The debug_peer_level parameter specifies the increment in verbose
# logging level when an SMTP client or server host name or address
# matches a pattern in the debug_peer_list parameter.
#
#debug_peer_level = 2[/FONT]
[FONT=Verdana,Arial,Tahoma,Calibri,Geneva,sans-serif]# The debug_peer_list parameter specifies an optional list of domain
# or network patterns, /file/name patterns or type:name tables. When
# an SMTP client or server host name or address matches a pattern,
# increase the verbose logging level by the amount specified in the
# debug_peer_level parameter.
#
#debug_peer_list = 127.0.0.1
#debug_peer_list = some.domain[/FONT]
[FONT=Verdana,Arial,Tahoma,Calibri,Geneva,sans-serif]# The debugger_command specifies the external command that is executed
# when a Postfix daemon program is run with the -D option.
#
# Use "command .. & sleep 5" so that the debugger can attach before
# the process marches on. If you use an X-based debugger, be sure to
# set up your XAUTHORITY environment variable before starting Postfix.
#
debugger_command =
  PATH=/bin:/usr/bin:/usr/local/bin:/usr/X11R6/bin
  ddd $daemon_directory/$process_name $process_id & sleep 5[/FONT]
[FONT=Verdana,Arial,Tahoma,Calibri,Geneva,sans-serif]# If you can't use X, use this to capture the call stack when a
# daemon crashes. The result is in a file in the configuration
# directory, and is named after the process name and the process ID.
#
# debugger_command =
# PATH=/bin:/usr/bin:/usr/local/bin; export PATH; (echo cont;
# echo where) | gdb $daemon_directory/$process_name $process_id 2>&1
# >$config_directory/$process_name.$process_id.log & sleep 5
#
# Another possibility is to run gdb under a detached screen session.
# To attach to the screen session, su root and run "screen -r
# <id_string>" where <id_string> uniquely matches one of the detached
# sessions (from "screen -list").
#
# debugger_command =
# PATH=/bin:/usr/bin:/sbin:/usr/sbin; export PATH; screen
# -dmS $process_name gdb $daemon_directory/$process_name
# $process_id & sleep 1[/FONT]
[FONT=Verdana,Arial,Tahoma,Calibri,Geneva,sans-serif]# INSTALL-TIME CONFIGURATION INFORMATION
#
# The following parameters are used when installing a new Postfix version.
# 
# sendmail_path: The full pathname of the Postfix sendmail command.
# This is the Sendmail-compatible mail posting interface.
# 
sendmail_path = /usr/sbin/postfix[/FONT]
[FONT=Verdana,Arial,Tahoma,Calibri,Geneva,sans-serif]# newaliases_path: The full pathname of the Postfix newaliases command.
# This is the Sendmail-compatible command to build alias databases.
#
newaliases_path = /usr/bin/newaliases[/FONT]
[FONT=Verdana,Arial,Tahoma,Calibri,Geneva,sans-serif]# mailq_path: The full pathname of the Postfix mailq command.  This
# is the Sendmail-compatible mail queue listing command.
# 
mailq_path = /user/bin/mailq[/FONT]
[FONT=Verdana,Arial,Tahoma,Calibri,Geneva,sans-serif]# setgid_group: The group for mail submission and queue management
# commands.  This must be a group name with a numerical group ID that
# is not shared with other accounts, not even with the Postfix account.
#
setgid_group = postdrop[/FONT]
[FONT=Verdana,Arial,Tahoma,Calibri,Geneva,sans-serif]# html_directory: The location of the Postfix HTML documentation.
#
#html_directory =[/FONT]
[FONT=Verdana,Arial,Tahoma,Calibri,Geneva,sans-serif]# manpage_directory: The location of the Postfix on-line manual pages.
#
#manpage_directory =[/FONT]
[FONT=Verdana,Arial,Tahoma,Calibri,Geneva,sans-serif]# sample_directory: The location of the Postfix sample configuration files.
# This parameter is obsolete as of Postfix 2.1.
#
#sample_directory =[/FONT]
[FONT=Verdana,Arial,Tahoma,Calibri,Geneva,sans-serif]# readme_directory: The location of the Postfix README files.
#
#readme_directory =
inet_protocols = ipv4[/FONT]
[FONT=Verdana,Arial,Tahoma,Calibri,Geneva,sans-serif]#limit mailbox size to 1G
mailbox_size_limit = 1073741824
myorigin = /etc/mailname
#mydestination = $myhostname, localhost.$mydomain, localhost
mynetwork = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
relayhost = 
recipient_delimiter = 
default_transport = error
relay_transport = error
mynetworks = 127.0.0.1/32[/FONT]
[FONT=Verdana,Arial,Tahoma,Calibri,Geneva,sans-serif]## SASL Options
smtp_sasl_auth_enable = yes
smtp_sasl_security_options = noanonymous
smtp_sasl_password_maps = hash:/usr/local/etc/postfix/sasl_passwd[/FONT]
[FONT=Verdana,Arial,Tahoma,Calibri,Geneva,sans-serif]## TLS Options
smtp_use_tls = yes
smtp_tls_security_level = encrypt
##Following line required for port 465
smtp_tls_wrappermode = yes
tls_random_source = dev:/dev/urandom[/FONT]
[FONT=Verdana,Arial,Tahoma,Calibri,Geneva,sans-serif]## Relay host
relayhost = [smtp.gmail.com]:465[/FONT]

```

---

### Post by lisati on 2019-06-16
I don't understand why you have the following:
```

mydestination = mail.gmail.com, localhost.gmail.com, localhost, gmail.com

```
This is likely to get postfix to try to deliver mail for a gmail address locally instead of delivering it through gmail's servers.

More information on "mydestination" can be found [here]("http://www.postfix.org/BASIC_CONFIGURATION_README.html#mydestination").

---

### Post by kevdog on 2019-06-17
Hey just a tip, when posting the main.cf file -- it might be easier for readability purposes to cut out all the commented lines:  I usually do something like
cat main.cf | grep -v ^# | grep -v ^$

smtp_sasl_password_maps = hash:/usr/local/etc/postfix/sasl_passwd

You sure you have a file located in this directory?

---

### Post by rjphares on 2019-06-17
I purged postfix and then reinstalled postfix. I then chose "No Configuration". When I try to send an email now I get this message: [https://imgur.com/a/ipDls1B](https://imgur.com/a/ipDls1B)


Here is what the main.cf.proto file looks like: [https://imgur.com/a/wNYXpkI](https://imgur.com/a/wNYXpkI)

---

### Post by kevdog on 2019-06-17
Ok I just set this up on a new Ubuntu Server and can confirm it will work -- or it did for me at least. 
I followed the instructions here:
[https://www.linode.com/docs/email/postfix/configure-postfix-to-send-mail-using-gmail-and-google-apps-on-debian-or-ubuntu/](https://www.linode.com/docs/email/postfix/configure-postfix-to-send-mail-using-gmail-and-google-apps-on-debian-or-ubuntu/)

I wanted port 465 and not 587 as I've stated earlier so I made the following modifications
/etc/postfix/sasl/sasl_passwd

```
smtp.gmail.com <your_gmail_username>:<your gmail app specific password>
```

I put the following at the bottom of my main.cf file:

```
# Manual Configuation for Gmail
## SASL Options
smtp_sasl_auth_enable = yes
smtp_sasl_security_options = noanonymous
smtp_sasl_password_maps = hash:/etc/postfix/sasl/sasl_passwd

## TLS Options
smtp_use_tls = yes
smtp_tls_security_level = encrypt
##Following line required for port 465
smtp_tls_wrappermode = yes
tls_random_source = dev:/dev/urandom

## Relay host
relayhost = [smtp.gmail.com]:465

disable_vrfy_command = yes
```


Hopefully that helps -- Admittedly I've set this up before, however this process took me all of 5 minutes.  It took me longer to construct this post than setup the mail server.

---

### Post by rjphares on 2019-06-17
I am unable to send an email. I still get this message: [https://imgur.com/a/ipDls1B](https://imgur.com/a/ipDls1B)

---

### Post by lisati on 2019-06-17
I refer you back to [post 12]("https://ubuntuforums.org/showthread.php?t=2420291&p=13865949&viewfull=1#post13865949") in this thread again - your test emails could be bouncing. 

The log entries in [post25]("https://ubuntuforums.org/showthread.php?t=2420291&p=13866620&viewfull=1#post13866620") tell me that at least some of your test messages are not getting to where they should:
```
May 31 12:16:16 DESKTOP-K50P15B postfix/cleanup[747]: 6B8138000000033AC8: message-id=<20190531161616.6B8138000000033AC8@rjphares.localdomain>
May 31 12:16:16 DESKTOP-K50P15B postfix/qmgr[741]: 6B8138000000033AC8: from=<root@DESKTOP-K50P15B.localdomain>, size=422, nrcpt=2 (queue active)
May 31 12:16:16 DESKTOP-K50P15B postfix/error[754]: 6B8138000000033AC8: to=<d@DESKTOP-K50P15B.localdomain>, relay=none, delay=0.04, delays=0.03/0/0/0.01, dsn=5.0.0, status=bounced (DESKTOP-K50P15B.localdomain)
May 31 12:16:16 DESKTOP-K50P15B postfix/error[754]: 6B8138000000033AC8: to=<rjphares@DESKTOP-K50P15B.localdomain>, relay=none, delay=0.05, delays=0.03/0/0/0.02, dsn=5.0.0, status=bounced (DESKTOP-K50P15B.localdomain)
May 31 12:16:16 DESKTOP-K50P15B postfix/cleanup[747]: 75C48B000000033AC6: message-id=<20190531161616.75C48B000000033AC6@rjphares.localdomain>
May 31 12:16:16 DESKTOP-K50P15B postfix/bounce[749]: 6B8138000000033AC8: sender non-delivery notification: 75C48B000000033AC6
May 31 12:16:16 DESKTOP-K50P15B postfix/qmgr[741]: 75C48B000000033AC6: from=<>, size=2756, nrcpt=1 (queue active)
May 31 12:16:16 DESKTOP-K50P15B postfix/qmgr[741]: 6B8138000000033AC8: removed
May 31 12:16:16 DESKTOP-K50P15B postfix/error[748]: 75C48B000000033AC6: to=<root@DESKTOP-K50P15B.localdomain>, relay=none, delay=0.03, delays=0.02/0/0/0.01, dsn=5.0.0, status=bounced (DESKTOP-K50P15B.localdomain)

```

---

### Post by rjphares on 2019-06-17
Do you know what I typed that could have produced those error message? Since I deleted postfix and reinstalled with "No Configuration" I have been unable to find a mail.log file.

---

### Post by kevdog on 2019-06-18
I think you need to install with internet configuration.  See this post about log files for mail/postfix: [https://askubuntu.com/questions/394724/where-are-the-postfix-log-files](https://askubuntu.com/questions/394724/where-are-the-postfix-log-files)

---

### Post by rjphares on 2019-06-18
I am not sure the configuration is correct but this is the output : [https://imgur.com/a/g5s5fJB](https://imgur.com/a/g5s5fJB)

---

### Post by kevdog on 2019-06-19
Yikes - the postfix daemon isn't even running -- I'm not sure why. Something is screwed up with your postfix installation.

---

### Post by rjphares on 2019-06-19
Success. I changed my hostname to DESKTOP-K50P15B. Really excited to have solved this issue and couldn't have done it with out all the advice.

[https://imgur.com/a/ZGhbSnU](https://imgur.com/a/ZGhbSnU)

---

### Post by rjphares on 2019-06-19
[LEFT][COLOR=#222222][FONT=Verdana]Success. I changed myhostname to "DESKTOP-K50P15B" in main.cf. Really excited to have solved this issue and couldn't have done it with out all the advice.[/FONT][/COLOR]

[/LEFT]
[https://imgur.com/a/ZGhbSnU](https://imgur.com/a/ZGhbSnU)

[LEFT]```

[COLOR=#222222][FONT=Verdana][FONT=Verdana]# See /usr/share/postfix/main.cf.dist for a commented, more complete version[/FONT][/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana][FONT=Verdana]
# Debian specific:  Specifying a file name will cause the first
# line of that file to be used as the name.  The Debian default
# is /etc/mailname.
#myorigin = /etc/mailname[/FONT][/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana][FONT=Verdana]smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no[/FONT][/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana][FONT=Verdana]# appending .domain is the MUA's job.
append_dot_mydomain = no[/FONT][/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana][FONT=Verdana]# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h[/FONT][/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana][FONT=Verdana]readme_directory = no[/FONT][/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana][FONT=Verdana]# See http://www.postfix.org/COMPATIBILITY_README.html -- default to 2 on
# fresh installs.
compatibility_level = 2[/FONT][/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana][FONT=Verdana]# TLS parameters
smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache[/FONT][/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana][FONT=Verdana]# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.[/FONT][/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana][FONT=Verdana]smtpd_relay_restrictions = permit_mynetworks permit_sasl_authenticated defer_unauth_destination
myhostname = DESKTOP-K50P15B
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = DESKTOP-K50P15B, smtp.gmail.com, DESKTOP-K50P15B.localdomain, localhost.localdomain, localhost
relayhost = 
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_size_limit = 51200000
recipient_delimiter = +
inet_interfaces = loopback-only
inet_protocols = ipv4
default_transport = error
relay_transport = error
[/FONT][/FONT][/COLOR]

```[/LEFT]

---

### Post by kevdog on 2019-06-20
Ok so postfix looks like its up and running, however I don't see any gmail going through.  What are you terming Success?

---

