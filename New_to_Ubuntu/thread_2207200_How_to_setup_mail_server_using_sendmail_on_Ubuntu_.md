---
title: "How to setup mail server using sendmail on Ubuntu 13.04?"
date: 2014-02-22
forum: New to Ubuntu
---

### Post by raj7 on 2014-02-22
All,

I am new to Ubuntu. I am trying to setup mail server using sendmail. 
Can someone send me steps how to configure sendmail on Ubuntu 13.04?

Thanks in advance.

See attached logs.


Here are some of information from my server: 

[EMAIL="root@server:/etc/bind"]root@server:/etc/bind[/EMAIL]# hostname
server
[EMAIL="root@server:/etc/bind"]root@server:/etc/bind[/EMAIL]#



[EMAIL="root@server"]root@server[/EMAIL]:~# cat /etc/hosts
fe00::0         ip6-localnet
ff00::0         ip6-mcastprefix
ff02::1         ip6-allnodes
ff02::2         ip6-allrouters
127.0.0.1 localhost.localdomain localhost
# Auto-generated hostname. Please do not remove this comment.
162.212.130.164 server.eptent.com eptent.com  server [www.eptent.com]("http://www.eptent.com")
::1             localhost ip6-localhost ip6-loopback
[EMAIL="root@server"]root@server[/EMAIL]:~#

[EMAIL="root@server"]root@server[/EMAIL]:~# cat /etc/resolv.conf
search server.eptent.com eptent.com [www.eptent.com]("http://www.eptent.com")
nameserver 162.212.130.164
nameserver 75.98.161.224
nameserver 69.39.86.5
[EMAIL="root@server"]root@server[/EMAIL]:~#


[EMAIL="root@server:/etc/bind"]root@server:/etc/bind[/EMAIL]# host [www.eptent.com]("http://www.eptent.com")
[www.eptent.com]("http://www.eptent.com") has address 162.212.130.164
[EMAIL="root@server:/etc/bind"]root@server:/etc/bind[/EMAIL]#

[EMAIL="root@server:/etc/bind"]root@server:/etc/bind[/EMAIL]# host 162.212.130.164
164.130.212.162.in-addr.arpa domain name pointer 162.212.130.164.static.a2webhosting.com.
[EMAIL="root@server:/etc/bind"]root@server:/etc/bind[/EMAIL]#


[EMAIL="root@server:/etc/bind"]root@server:/etc/bind[/EMAIL]# dig [www.eptent.com]("http://www.eptent.com")
; <<>> DiG 9.9.2-P1 <<>> [www.eptent.com]("http://www.eptent.com")
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 32618
;; flags: qr aa rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 1, ADDITIONAL: 2
;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 4096
;; QUESTION SECTION:
;[www.eptent.com](www.eptent.com).                        IN      A
;; ANSWER SECTION:
[www.eptent.com]("http://www.eptent.com").         259200  IN      A       162.212.130.164
;; AUTHORITY SECTION:
eptent.com.             259200  IN      NS      server.eptent.com.
;; ADDITIONAL SECTION:
server.eptent.com.      259200  IN      A       162.212.130.164
;; Query time: 3 msec
;; SERVER: 162.212.130.164#53(162.212.130.164)
;; WHEN: Sat Feb 22 12:20:54 2014
;; MSG SIZE  rcvd: 96
[EMAIL="root@server:/etc/bind"]root@server:/etc/bind[/EMAIL]#


[EMAIL="root@server:/etc/bind"]root@server:/etc/bind[/EMAIL]# dig 162.212.130.164
; <<>> DiG 9.9.2-P1 <<>> 162.212.130.164
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NXDOMAIN, id: 42187
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 1, ADDITIONAL: 0
;; QUESTION SECTION:
;162.212.130.164.               IN      A
;; AUTHORITY SECTION:
.                       3600    IN      SOA     a.root-servers.net. nstld.verisign-grs.com. 2014022201 1800 900 604800 86400
;; Query time: 11 msec
;; SERVER: 75.98.161.224#53(75.98.161.224)
;; WHEN: Sat Feb 22 12:21:33 2014
;; MSG SIZE  rcvd: 108
[EMAIL="root@server:/etc/bind"]root@server:/etc/bind[/EMAIL]#

[EMAIL="root@server:/etc/bind"]root@server:/etc/bind[/EMAIL]# cat named.conf.local
//
// Do any local configuration here
//
// Consider adding the 1918 zones here, if they are not used in your
// organization
//include "/etc/bind/zones.rfc1918";
zone "eptent.com" {
        type master;
        file "/etc/bind/db.eptent.com";
};
zone "130.212.162.in-addr.arpa" {
   type master;
   file "/etc/bind/db.162-212-130.zone";
};

logging {
    channel query.log {
        file "/var/log/query.log";
        severity debug 3;
    };
    category queries { query.log; };
};
[EMAIL="root@server:/etc/bind"]root@server:/etc/bind[/EMAIL]#

[EMAIL="root@server:/etc/bind"]root@server:/etc/bind[/EMAIL]# cat named.conf.options
options {
        directory "/var/cache/bind";
        // If there is a firewall between you and nameservers you want
        // to talk to, you may need to fix the firewall to allow multiple
        // ports to talk.  See [http://www.kb.cert.org/vuls/id/800113](http://www.kb.cert.org/vuls/id/800113)
        // If your ISP provided one or more IP addresses for stable
        // nameservers, you probably want to use them as forwarders.
        // Uncomment the following block, and insert the addresses replacing
        // the all-0's placeholder.
         forwarders {
                162.212.130.164;
         };
        //========================================================================
        // If BIND logs error messages about the root key being expired,
        // you will need to update your keys.  See [https://www.isc.org/bind-keys](https://www.isc.org/bind-keys)
        //========================================================================
        dnssec-validation auto;
        auth-nxdomain no;    # conform to RFC1035
        listen-on-v6 { any; };
};
[EMAIL="root@server:/etc/bind"]root@server:/etc/bind[/EMAIL]#





[EMAIL="root@server:/etc/bind"]root@server:/etc/bind[/EMAIL]# cat db.eptent.com
;
; BIND data file for eptent.com
;
; The full zone file
;
$TTL 3D
eptent.com.       IN      SOA     server.eptent.com. root.eptent.com. (
                       200211152       ; serial#
                       3600            ; refresh, seconds
                       3600            ; retry, seconds
                       3600            ; expire, seconds
                       3600 )          ; minimum, seconds
eptent.com. IN      NS      server.eptent.com.
eptent.com. IN      MX     10 mta.eptent.com.
www           IN      A       162.212.130.164
mta              IN      A       162.212.130.164
server               IN       A        162.212.130.164
[EMAIL="root@server:/etc/bind"]root@server:/etc/bind[/EMAIL]#

[EMAIL="root@server:/etc/bind"]root@server:/etc/bind[/EMAIL]# cat db.162-212-130.zone
;
; BIND data file for eptent.com
;
; Filename: 162-212-130.zone
;
; Zone file for 162.212.130.x
;
$TTL 3D
@       IN        SOA        server.eptent.com.  root.eptent.com. (
                            200303301          ; serial number
                            8H                 ; refresh, seconds
                            2H                 ; retry, seconds
                            4W                 ; expire, seconds
                            1D )               ; minimum, seconds
        IN            NS      server.eptent.com   ; Nameserver Address
164     IN           PTR      eptent.com.
[EMAIL="root@server:/etc/bind"]root@server:/etc/bind[/EMAIL]#


Here are logs:

[U][B]From mail.info

[/B][/U][FONT=Courier New][SIZE=3][COLOR=#000000]Feb 17 03:36:08 server sendmail[24801]: s1H8Z5ul024801: to=bdahiya2007@gmail.com, ctladdr=root (0/0), delay=00:01:03, xdelay=00:00:48, mailer=relay, pri=30020, relay=[127.0.0.1] [127.0.0.1], dsn=2.0.0, stat=Sent (s1H8ZKsI024804 Message accepted for delivery)
Feb 17 03:42:52 server sm-mta[24870]: STARTTLS=client, relay=gmail-smtp-in.l.google.com., version=TLSv1/SSLv3, verify=FAIL, cipher=ECDHE-RSA-RC4-SHA, bits=128/128
Feb 17 03:43:03 server sm-mta[24870]: STARTTLS=client, relay=alt1.gmail-smtp-in.l.google.com., version=TLSv1/SSLv3, verify=FAIL, cipher=ECDHE-RSA-RC4-SHA, bits=128/128
Feb 17 03:43:14 server sm-mta[24870]: STARTTLS=client, relay=alt2.gmail-smtp-in.l.google.com., version=TLSv1/SSLv3, verify=FAIL, cipher=ECDHE-RSA-RC4-SHA, bits=128/128
Feb 17 03:43:25 server sm-mta[24870]: STARTTLS=client, relay=alt3.gmail-smtp-in.l.google.com., version=TLSv1/SSLv3, verify=FAIL, cipher=ECDHE-RSA-RC4-SHA, bits=128/128
Feb 17 03:43:37 server sm-mta[24870]: STARTTLS=client, relay=alt4.gmail-smtp-in.l.google.com., version=TLSv1/SSLv3, verify=FAIL, cipher=ECDHE-RSA-RC4-SHA, bits=128/128
Feb 17 03:43:38 server sm-mta[24870]: s1H8ZKsI024804: to=<bdahiya2007@gmail.com>, ctladdr=<root@server.eptent.com> (0/0), delay=00:08:18, xdelay=00:00:56, mailer=esmtp, pri=120310, relay=alt4.gmail-smtp-in.l.google.com. [173.194.65.27], dsn=4.0.0, stat=Deferred: 421-4.7.0 [162.212.130.164      10] Our system has detected an unusual rate of
Feb 17 03:50:52 server sendmail[24921]: s1H8olxa024921: from=root, size=83, class=0, nrcpts=1, msgid=<201402170850.s1H8olxa024921@server.eptent.com>, relay=root@localhost
Feb 17 03:50:57 server sm-mta[24923]: s1H8oqnm024923: from=<root@server.eptent.com>, size=372, class=0, nrcpts=1, msgid=<201402170850.s1H8olxa024921@server.eptent.com>, proto=ESMTP, daemon=MTA, relay=localhost.localdomain [127.0.0.1]
Feb 17 03:50:57 server sendmail[24921]: s1H8olxa024921: to=bdahiya2007@gmail.com, ctladdr=root (0/0), delay=00:00:10, xdelay=00:00:05, mailer=relay, pri=30083, relay=[127.0.0.1] [127.0.0.1], dsn=2.0.0, stat=Sent (s1H8oqnm024923 Message accepted for delivery)
Feb 17 03:51:08 server sm-mta[24925]: STARTTLS=client, relay=gmail-smtp-in.l.google.com., version=TLSv1/SSLv3, verify=FAIL, cipher=ECDHE-RSA-RC4-SHA, bits=128/128
Feb 17 03:51:12 server sm-mta[24925]: s1H8oqnm024923: to=<bdahiya2007@gmail.com>, ctladdr=<root@server.eptent.com> (0/0), delay=00:00:15, xdelay=00:00:15, mailer=esmtp, pri=120372, relay=gmail-smtp-in.l.google.com. [74.125.142.27], dsn=2.0.0, stat=Sent (OK 1392627072 m1si12300006igt.16 - gsmtp)
Feb 17 03:52:38 server sm-mta[24936]: STARTTLS=client, relay=gmail-smtp-in.l.google.com., version=TLSv1/SSLv3, verify=FAIL, cipher=ECDHE-RSA-RC4-SHA, bits=128/128
Feb 17 03:52:45 server sm-mta[24936]: STARTTLS=client, relay=alt1.gmail-smtp-in.l.google.com., version=TLSv1/SSLv3, verify=FAIL, cipher=ECDHE-RSA-RC4-SHA, bits=128/128
Feb 17 03:52:46 server sm-mta[24936]: s1H8ZKsI024804: to=<bdahiya2007@gmail.com>, ctladdr=<root@server.eptent.com> (0/0), delay=00:17:26, xdelay=00:00:09, mailer=esmtp, pri=210310, relay=alt1.gmail-smtp-in.l.google.com. [173.194.65.26], dsn=2.0.0, stat=Sent (OK 1392627166 s6si30542531eel.77 - gsmtp)
Feb 17 04:18:53 server sm-mta[24641]: restarting /usr/sbin/sendmail-mta due to signal
Feb 17 04:18:54 server sm-mta[24641]: gethostbyaddr(127.0.0.2) failed: 1
Feb 17 04:18:55 server sm-mta[25204]: starting daemon (8.14.4): SMTP+queueing@00:10:00
Feb 17 11:41:53 server sm-mta[28198]: s1HGfphK028198: 107-194-33-105.lightspeed.rlghnc.sbcglobal.net [107.194.33.105] did not issue MAIL/EXPN/VRFY/ETRN during connection to MTA
Feb 17 14:54:01 server sm-mta[29431]: s1HJs0E7029431: [58.26.37.252] did not issue MAIL/EXPN/VRFY/ETRN during connection to MTA
Feb 18 02:50:26 server sendmail[1693]: gethostbyaddr(127.0.0.2) failed: 1
Feb 18 02:50:27 server sendmail[1694]: starting daemon (8.14.4): SMTP+queueing@01:00:00
Feb 18 02:50:27 server sendmail[1694]: NOQUEUE: SYSERR(root): opendaemonsocket: daemon MTA: cannot bind: Address already in use
Feb 18 02:50:27 server sendmail[1694]: daemon MTA: problem creating SMTP socket
Feb 18 02:50:27 server sendmail[1694]: NOQUEUE: SYSERR(root): opendaemonsocket: daemon MTA: cannot bind: Address already in use
Feb 18 02:50:27 server sendmail[1694]: daemon MTA: problem creating SMTP socket
Feb 18 02:50:32 server sendmail[1694]: NOQUEUE: SYSERR(root): opendaemonsocket: daemon MTA: cannot bind: Address already in use
Feb 18 02:50:32 server sendmail[1694]: daemon MTA: problem creating SMTP socket
Feb 18 02:50:37 server sendmail[1694]: NOQUEUE: SYSERR(root): opendaemonsocket: daemon MTA: cannot bind: Address already in use
Feb 18 02:50:37 server sendmail[1694]: daemon MTA: problem creating SMTP socket
Feb 18 02:50:42 server sendmail[1694]: NOQUEUE: SYSERR(root): opendaemonsocket: daemon MTA: cannot bind: Address already in use
Feb 18 02:50:42 server sendmail[1694]: daemon MTA: problem creating SMTP socket
Feb 18 02:50:47 server sendmail[1694]: NOQUEUE: SYSERR(root): opendaemonsocket: daemon MTA: cannot bind: Address already in use
Feb 18 02:50:47 server sendmail[1694]: daemon MTA: problem creating SMTP socket
Feb 18 02:50:52 server sendmail[1694]: NOQUEUE: SYSERR(root): opendaemonsocket: daemon MTA: cannot bind: Address already in use
Feb 18 02:50:52 server sendmail[1694]: daemon MTA: problem creating SMTP socket
Feb 18 02:50:57 server sendmail[1694]: NOQUEUE: SYSERR(root): opendaemonsocket: daemon MTA: cannot bind: Address already in use
Feb 18 02:50:57 server sendmail[1694]: daemon MTA: problem creating SMTP socket
Feb 18 02:51:02 server sendmail[1694]: NOQUEUE: SYSERR(root): opendaemonsocket: daemon MTA: cannot bind: Address already in use
Feb 18 02:51:02 server sendmail[1694]: daemon MTA: problem creating SMTP socket
Feb 18 02:51:07 server sendmail[1694]: NOQUEUE: SYSERR(root): opendaemonsocket: daemon MTA: cannot bind: Address already in use
Feb 18 02:51:07 server sendmail[1694]: daemon MTA: problem creating SMTP socket
Feb 18 02:51:12 server sendmail[1694]: NOQUEUE: SYSERR(root): opendaemonsocket: daemon MTA: cannot bind: Address already in use
Feb 18 02:51:12 server sendmail[1694]: daemon MTA: problem creating SMTP socket
Feb 18 02:51:12 server sendmail[1694]: NOQUEUE: SYSERR(root): opendaemonsocket: daemon MTA: server SMTP socket wedged: exiting
Feb 18 02:58:51 server sendmail[1779]: starting daemon (8.14.4): queueing@01:00:00
Feb 18 10:24:06 server sm-mta[4749]: s1IFO4le004749: lx5.life813x5.com [199.168.138.137] (may be forged) did not issue MAIL/EXPN/VRFY/ETRN during connection to MTA
Feb 18 12:34:44 server sm-mta[5589]: s1IHYWxQ005589: ruleset=check_rcpt, arg1=<support@microsoft.com>, relay=[199.87.239.74], reject=550 5.7.1 <support@microsoft.com>... Relaying denied. IP name lookup failed [199.87.239.74]
Feb 18 12:34:44 server sm-mta[5589]: s1IHYWxQ005589: lost input channel from [199.87.239.74] to MTA after rcpt
Feb 18 12:34:44 server sm-mta[5589]: s1IHYWxQ005589: from=<support@microsoft.com>, size=0, class=0, nrcpts=0, proto=SMTP, daemon=MTA, relay=[199.87.239.74]
Feb 19 01:37:31 server sm-mta[10677]: s1J6bTAA010677: [210.21.110.58] did not issue MAIL/EXPN/VRFY/ETRN during connection to MTA
Feb 19 01:42:38 server sm-mta[10726]: s1J6gOBJ010726: [210.21.110.58] did not issue MAIL/EXPN/VRFY/ETRN during connection to MTA
Feb 19 11:21:05 server sm-mta[14548]: s1JGL4Qo014548: [212.7.218.142] did not issue MAIL/EXPN/VRFY/ETRN during connection to MTA
 
Thanks,
Raj[/COLOR][/SIZE][/FONT]

---

### Post by TheFu on 2014-02-23
Welcome to the forums.

TL;DR  - however, sendmail is one of the most hacked programs in UNIX systems, mainly because of the incredible capabilities to handle almost any complex situation related to email.  With that extra flexibility comes added risk of misconfiguration.

Might want to check into other, easier to configure MTAs, like postfix and qmail.  I've been using postfix for over 15 yrs. Many ISPs use postfix.

Ubuntu has lots of how-to guides at help.ubuntu.com for things like this. Also, howtoforge.com has step-by-step guides for things like this as well.

To get better help, please wrap all the commands in your first post in code tags so we can more easily read it. My signature has a link for how-to do that. Help us help you please.

---

