---
title: "Spam Control For Postfix"
date: 2011-03-01
forum: Outdated Tutorials &amp; Tips
---

### Post by linuxbasiccommand on 2011-03-01
**[Spam]("http://linuxbasiccommand.blogspot.com/2010/10/spam-control-for-postfix_29.html") is a major problem for anyone with a mail server. Many times,  spam goes to[ email]("http://linuxbasiccommand.blogspot.com/search/label/Mail") addresses that don't exist. But, it still is hitting  your server even if it isn't delivered. Other times, a users inbox will  be overflowing with annoying messages about ******, hookers, free  software, and whatever else.**

**Below is a solution. It's an ongoing accumulation of my efforts to  stop spam to the best of my abilities. So far, it has a 97% success rate  with over 20,000 emails (spam and ham, alike) processed.**

**Follow the instructions. I will update/modify as necessary if things seem unclear. Feel free to ask.**

**1) Install Postgrey, RRD, a log parser, and Graphing tools.**
apt-get install postgrey rrdtool mailgraph pflogsumm

Postgrey will have a delay of 5 minutes by default on email going to  your mailbox. If this is too long, edit the /etc/default/postgrey file  by adding --delay=120 where 120 is seconds.

**2) Restart the Postgrey server.**
/etc/init.d/postgrey restart

**3) Edit the Postfix main.cf.**
We will be adding several things including the Postgrey configuration.

# See /usr/share/postfix/main.cf.dist for a commented, more complete version


# Debian specific:  Specifying a file name will cause the first
# line of that file to be used as the name.  The Debian default
# is /etc/mailname.
#myorigin = /etc/mailname

smtpd_banner = $myhostname ESMTP $mail_name (Debian/GNU)
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

readme_directory = /usr/share/doc/postfix

# TLS parameters
smtpd_tls_cert_file = /etc/postfix/smtpd.cert
smtpd_tls_key_file = /etc/postfix/smtpd.key
smtpd_use_tls = yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = my.derekgordon.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = my.derekgordon.com, localhost, localhost.localdomain
relayhost =
mynetworks = 127.0.0.0/8 [::1]/128 66.118.142.78
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
html_directory = /usr/share/doc/postfix/html
virtual_alias_domains =
virtual_alias_maps = proxy:mysql:/etc/postfix/mysql-virtual_forwardings.cf, mysql:/etc/postfix/mysql-virtual_email2email.cf
virtual_mailbox_domains = proxy:mysql:/etc/postfix/mysql-virtual_domains.cf
virtual_mailbox_maps = proxy:mysql:/etc/postfix/mysql-virtual_mailboxes.cf
virtual_mailbox_base = /var/vmail
virtual_uid_maps = static:5000
virtual_gid_maps = static:5000
smtpd_sasl_auth_enable = yes
broken_sasl_auth_clients = yes
smtpd_sasl_authenticated_header = yes
smtpd_recipient_restrictions = permit_mynetworks,  permit_sasl_authenticated, check_recipient_access  mysql:/etc/postfix/mysql-virtual_recipient.cf,  reject_unauth_destination, check_policy_service inet:127.0.0.1:60000,  reject_rbl_client zen.spamhaus.org, reject_rbl_client  smtp.dnsbl.sorbs.net, reject_rbl_client bl.spamcop.net,  reject_rbl_client combined.rbl.msrbl.net, reject_rbl_client  multihop.dsbl.org, check_recipient_access regexp:/etc/postfix/spamtrap,  permit
smtpd_tls_security_level = may
transport_maps = proxy:mysql:/etc/postfix/mysql-virtual_transports.cf
relay_domains = mysql:/etc/postfix/mysql-virtual_relaydomains.cf
relay_recipient_maps = mysql:/etc/postfix/mysql-virtual_relayrecipientmaps.cf
virtual_create_maildirsize = yes
virtual_maildir_extended = yes
virtual_mailbox_limit_maps = proxy:mysql:/etc/postfix/mysql-virtual_mailbox_limit_maps.cf
virtual_mailbox_limit_override = yes
virtual_maildir_limit_message = "The user you are trying to reach is over quota."
virtual_overquota_bounce = yes
proxy_read_maps = $local_recipient_maps $mydestination  $virtual_alias_maps $virtual_alias_domains $virtual_mailbox_maps  $virtual_mailbox_domains $relay_recipient_maps $relay_domains  $canonical_maps $sender_canonical_maps $recipient_canonical_maps  $relocated_maps $transport_maps $mynetworks $virtual_mailbox_limit_maps
smtpd_sender_restrictions = check_sender_access mysql:/etc/postfix/mysql-virtual_sender.cf
smtpd_client_restrictions = check_client_access mysql:/etc/postfix/mysql-virtual_client.cf
maildrop_destination_concurrency_limit = 1
maildrop_destination_recipient_limit = 1
virtual_transport = maildrop
header_checks = regexp:/etc/postfix/header_checks
mime_header_checks = regexp:/etc/postfix/mime_header_checks
nested_header_checks = regexp:/etc/postfix/nested_header_checks
body_checks = regexp:/etc/postfix/body_checks
content_filter = amavis:[127.0.0.1]:10024
receive_override_options = no_address_mappings
message_size_limit = 0

disable_vrfy_command = yes
smtpd_helo_required = yes


From a generic main.cf found in the Debian Lenny installation, I added/modified the BOLD areas.

**4) Create a file named "spamtrap" in the /etc/postfix/ directory.**
This serves as a filter. If spam is emailed to this address and other  addresses on your machine, it will drop that email so that it doesn't  get to any other mailboxes.

spamtrap file looks like this:

/emailcontrol.*@derekgordon\.com/ DISCARD

This is regexp so the slashes have to be used. My filter email is  [email]emailcontrol@derekgordon.com[/email] so edit accordingly and place in the  spamtrap file!!!

Side note: Do not create this mailbox using ISPConfig. There is  absolutely no reason for it to exist on your mailserver. It's a fake  address meant to catch annoying spam.



**5) Open up local.cf for SpamAssassin and add the following bit.**
It will be an extra filter designed to work with SA more than it is with general Postfix.

nano /etc/spamassassin/local.cf

Add the following to the bottom:

urirhssub       URIBL_BLACK  multi.uribl.com.        A   2
body            URIBL_BLACK  eval:check_uridnsbl('URIBL_BLACK')
describe        URIBL_BLACK  Contains an URL listed in the URIBL blacklist
tflags          URIBL_BLACK  net
score           URIBL_BLACK  3.0

**6) Restart Postfix and Spamassassin**
/etc/init.d/postfix restart
/etc/init.d/spamassassin restart



**7) Copy the mailgraph CGI script to your websites CGI-BIN:**
cp -p /usr/lib/cgi-bin/mailgraph.cgi /var/www/www.example.com/cgi-bin



**8) Create and CHMOD the postfix_report.sh script:**
nano /usr/local/sbin/postfix_report.sh

Paste the following into the script:

#!/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin

pflogsumm /var/log/mail.log | formail -c -I"Subject: Mail Statistics"  -I"From: [email]maillog@example.com[/email]" -I"To: [email]youremail@yourdomain.com[/email]"  -I"Received: from [www.example.com](www.example.com) ([ 127.0.0.1])" | sendmail  [email]youremail@yourdomain.com[/email]

##gzip /var/log/mail.log.0
exit 0
chmod 755 /usr/local/sbin/postfix_report.sh



**9) Edit the RSYSLOG file so that your mail.log rotates daily and to set up an automatic email with postfix statistics:**
nano /etc/logrotate.d/rsyslog

Delete the line that says /var/log/mail.log and add this at the VERY bottom of the file:

/var/log/mail.log
{
        rotate 7
        daily
        missingok
        notifempty
        delaycompress
        compress
        prerotate
              /usr/local/sbin/postfix_report.sh > /dev/null
        endscript
        postrotate
                invoke-rc.d rsyslog reload > /dev/null
        endscript
}
With this, every time the mail.log rotates (usually around 6am by  default) you will get a detailed email about what Postfix has delivered,  not delivered, greylisted, and so on.

So now you're all done! What did you do? You installed blacklist  filters, greylisting, graphing for on-the-fly information about Postfix,  daily emails with detailed Postfix stats, created a spam trap, and  other minor things to make your mailserver a lot more secure and less  susceptible to spam.

IMPORTANT: Let me know what you all do. Please respond with your choice,  if you use it, and how well it worked. If there's much of a use, I will  keep building upon the instructions and make it even better  (hopefully). Responses are in the form of thread messages.

BONUS INSTRUCTIONS:
If you use the script I posted below, that gives you GREYLISTING SPECIFIC STATS, do the following:

1) DELETE it from having a CRONJOB if you added one originaly. Most likely, you did.

2) Open the RSYSLOG file again.

3) Modify the above entry so that it looks like this:

/var/log/mail.log
{
        rotate 7
        daily
        missingok
        notifempty
        delaycompress
        compress
        prerotate
          /path/to/the/greylist_script.sh > /dev/null
              /usr/local/sbin/postfix_report.sh > /dev/null
        endscript
        postrotate
                invoke-rc.d rsyslog reload > /dev/null
        endscript
}
Make sure that the /path/to/the/greylist_script.sh > /dev/null matches the exact path to the script you were using.

Here is the greylist_script.sh:

#!/bin/sh

LOGFILE=/tmp/greylist-statistics
YOURMAIL=youremail@yourdomain.com

echo "Total amount of GreyListed messages
" > $LOGFILE
cat /var/log/mail.log | /usr/bin/postgreyreport --delay=300 >> $LOGFILE
echo -ne  "-------------------------------------\n" >> $LOGFILE
echo -ne  "-------------------------------------\n" >> $LOGFILE
echo "Get only the top 20 sources getting greylisted out
" >> $LOGFILE
cat /var/log/mail.log | postgreyreport | awk '{print $1}' | sort | uniq -c | sort -nr | head -n20 >> $LOGFILE
echo -ne  "-------------------------------------\n" >> $LOGFILE
echo -ne  "-------------------------------------\n" >> $LOGFILE
echo "Get a list of the top 20 email address that the greylisted sources are sending email to
"  >> $LOGFILE
cat /var/log/mail.log | postgreyreport | awk '{print $4}'  | sort  | uniq -c | sort -nr | head -n20 >> $LOGFILE
echo -ne  "-------------------------------------\n" >> $LOGFILE
echo -ne  "-------------------------------------\n" >> $LOGFILE
cat $LOGFILE | mail -s "Greylisting Statistics of `hostname` for `date +%Y-%m-%d`" $YOURMAIL
Edit the following parts of the above script:

1) Change the YOUREMAIL = line so that it goes to your personal mail box. This will give you details on how its working.
2) Make sure that /var/log/mail.log is the correct path to your current mail.log file. Distros are different.

Set the script to chmod +700 so that it is executable:

chmod 700 /path/to/the/greylist_script.sh

Source (linuxbasiccommand.blogspot.com

---

