---
title: "HOW TO: Postfix with SMTP-AUTH and TLS"
date: 2005-09-26
forum: Outdated Tutorials &amp; Tips
---

### Post by KingBahamut on 2005-09-26
In order to install Postfix with SMTP-AUTH and TLS do the following steps:

apt-get install postfix postfix-tls libsasl2 sasl2-bin libsasl2-modules libdb3-util procmail (1 line!)
dpkg-reconfigure postfix


<- Internet Site
<- NONE
<- server1.example.com
<- server1.example.com, localhost.example.com, localhost
<- No
<- 127.0.0.0/8
<- 0
<- +

postconf -e 'smtpd_sasl_local_domain ='
postconf -e 'smtpd_sasl_auth_enable = yes'
postconf -e 'smtpd_sasl_security_options = noanonymous'
postconf -e 'broken_sasl_auth_clients = yes'
postconf -e 'smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination'
postconf -e 'inet_interfaces = all'
echo 'pwcheck_method: saslauthd' >> /etc/postfix/sasl/smtpd.conf
echo 'mech_list: plain login' >> /etc/postfix/sasl/smtpd.conf

mkdir /etc/postfix/ssl
cd /etc/postfix/ssl/
openssl genrsa -des3 -rand /etc/hosts -out smtpd.key 1024
chmod 600 smtpd.key
openssl req -new -key smtpd.key -out smtpd.csr
openssl x509 -req -days 3650 -in smtpd.csr -signkey smtpd.key -out smtpd.crt
openssl rsa -in smtpd.key -out smtpd.key.unencrypted
mv -f smtpd.key.unencrypted smtpd.key
openssl req -new -x509 -extensions v3_ca -keyout cakey.pem -out cacert.pem -days 3650

postconf -e 'smtpd_tls_auth_only = no'
postconf -e 'smtp_use_tls = yes'
postconf -e 'smtpd_use_tls = yes'
postconf -e 'smtp_tls_note_starttls_offer = yes'
postconf -e 'smtpd_tls_key_file = /etc/postfix/ssl/smtpd.key'
postconf -e 'smtpd_tls_cert_file = /etc/postfix/ssl/smtpd.crt'
postconf -e 'smtpd_tls_CAfile = /etc/postfix/ssl/cacert.pem'
postconf -e 'smtpd_tls_loglevel = 1'
postconf -e 'smtpd_tls_received_header = yes'
postconf -e 'smtpd_tls_session_cache_timeout = 3600s'
postconf -e 'tls_random_source = dev:/dev/urandom'
postconf -e 'myhostname = server1.example.com'

The file /etc/postfix/main.cf should now look like this:

> # See /usr/share/postfix/main.cf.dist for a commented, more complete version

smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

myhostname = server1.example.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = server1.example.com, localhost.example.com, localhost
relayhost =
mynetworks = 127.0.0.0/8
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
smtpd_sasl_local_domain =
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination
smtpd_tls_auth_only = no
smtp_use_tls = yes
smtpd_use_tls = yes
smtp_tls_note_starttls_offer = yes
smtpd_tls_key_file = /etc/postfix/ssl/smtpd.key
smtpd_tls_cert_file = /etc/postfix/ssl/smtpd.crt
smtpd_tls_CAfile = /etc/postfix/ssl/cacert.pem
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom


/etc/init.d/postfix restart

Authentication will be done by saslauthd. We have to change a few things to make it work properly. Because Postfix runs chrooted in /var/spool/postfix we have to do the following:

mkdir -p /var/spool/postfix/var/run/saslauthd
rm -fr /var/run/saslauthd

Now we have to edit /etc/default/saslauthd in order to activate saslauthd. Remove # in front of START=yes and add the line PARAMS="-m /var/spool/postfix/var/run/saslauthd":

> # This needs to be uncommented before saslauthd will be run automatically
START=yes

PARAMS="-m /var/spool/postfix/var/run/saslauthd"

# You must specify the authentication mechanisms you wish to use.
# This defaults to "pam" for PAM support, but may also include
# "shadow" or "sasldb", like this:
# MECHANISMS="pam shadow"

MECHANISMS="pam"

Finally we have to edit /etc/init.d/saslauthd. Change the line

> dir=`dpkg-statoverride --list $PWDIR`

to

> #dir=`dpkg-statoverride --list $PWDIR`

Then change the variables PWDIR and PIDFILE  and add the variable dir  at the beginning of the file:

> PWDIR="/var/spool/postfix/var/run/${NAME}"
PIDFILE="${PWDIR}/saslauthd.pid"
dir="root sasl 755 ${PWDIR}"

/etc/init.d/saslauthd  should now look like this:

> #!/bin/sh -e

NAME=saslauthd
DAEMON="/usr/sbin/${NAME}"
DESC="SASL Authentication Daemon"
DEFAULTS=/etc/default/saslauthd
PWDIR="/var/spool/postfix/var/run/${NAME}"
PIDFILE="${PWDIR}/saslauthd.pid"
dir="root sasl 755 ${PWDIR}"

createdir() {
# $1 = user
# $2 = group
# $3 = permissions (octal)
# $4 = path to directory
        [ -d "$4" ] || mkdir -p "$4"
        chown -c -h "$1:$2" "$4"
        chmod -c "$3" "$4"
}

test -f "${DAEMON}" || exit 0

# Source defaults file; edit that file to configure this script.
if [ -e "${DEFAULTS}" ]; then
    . "${DEFAULTS}"
fi

# If we're not to start the daemon, simply exit
if [ "${START}" != "yes" ]; then
    exit 0
fi

# If we have no mechanisms defined
if [ "x${MECHANISMS}" = "x" ]; then
    echo "You need to configure ${DEFAULTS} with mechanisms to be used"
    exit 0
fi

# Add our mechanimsms with the necessary flag
PARAMS="${PARAMS} -a ${MECHANISMS}"

START="--start --quiet --pidfile ${PIDFILE} --startas ${DAEMON} --name ${NAME} -- ${PARAMS}"

# Consider our options
case "${1}" in
  start)
        echo -n "Starting ${DESC}: "
        #dir=`dpkg-statoverride --list $PWDIR`
        test -z "$dir" || createdir $dir
        if start-stop-daemon ${START} >/dev/null 2>&1 ; then
                echo "${NAME}."
        else
                if start-stop-daemon --test ${START} >/dev/null 2>&1; then
                        echo "(failed)."
                        exit 1
                else
                        echo "${DAEMON} already running."
                        exit 0
                fi
        fi
        ;;
  stop)
        echo -n "Stopping ${DESC}: "
        if start-stop-daemon --stop --quiet --pidfile "${PIDFILE}" \
                --startas ${DAEMON} --retry 10 --name ${NAME} \
                >/dev/null 2>&1 ; then
                        echo "${NAME}."
        else
                if start-stop-daemon --test ${START} >/dev/null 2>&1; then
                        echo "(not running)."
                        exit 0
                else
                        echo "(failed)."
                        exit 1
                fi
        fi
        ;;
  restart|force-reload)
          $0 stop
        exec $0 start
        ;;
  *)
        echo "Usage: /etc/init.d/${NAME} {start|stop|restart|force-reload}" >&2
        exit 1
        ;;
esac

exit 0

Now start saslauthd:

/etc/init.d/saslauthd start

To see if SMTP-AUTH and TLS work properly now run the following command:

telnet localhost 25

After you have established the connection to your postfix mail server type

ehlo localhost

If you see the lines

250-STARTTLS

and

250-AUTH

everything is fine.

[IMG]http://www.howtoforge.com/images/perfect_setup_ubuntu_5.04/31.gif[/IMG]

Type

quit

to return to the system's shell.

---

### Post by majikstreet on 2005-09-26
KB,
This tutorial doesn't really make sense to me...

Can you explain whats going on and where to do all this? The things with < in front of them don't really make any sense..


Does this provide mail retrival like IMAP or POP3? Or only SMTP?

What does this do for you?

---

### Post by KingBahamut on 2005-09-26
Just the SMTP. 

IMAP POP Below 

Install Courier-IMAP/Courier-IMAP-SSL (for IMAPs on port 993) and Courier-POP3/Courier-POP3-SSL (for POP3s on port 995).

apt-get install courier-authdaemon courier-base courier-imap courier-imap-ssl courier-pop courier-pop-ssl courier-ssl gamin libgamin0 libglib2.0-0 (one line!)

<- No
<- OK

Then configure Postfix to deliver emails to a user's Maildir:

postconf -e 'home_mailbox = Maildir/'
postconf -e 'mailbox_command ='
/etc/init.d/postfix restart

---

### Post by majikstreet on 2005-09-26
When I try to run the telnet command I get this:
root@ripleyhost:/etc/postfix/ssl # telnet localhost 25
Trying 127.0.0.1...
telnet: Unable to connect to remote host: Connection refused
root@ripleyhost:/etc/postfix/ssl #

---

### Post by John.Michael.Kane on 2005-09-27
Not to highjack the thread .. is post fix needed on say a laptop...

---

### Post by majikstreet on 2005-09-29
I fixed my telnet issue... I'm going to use flurdy's thread because it fits me more... But here is the solution:
[QUOTE=snaga]I managed to figure it out.

I edited the master.cf file in /etc/postfix/. I changed:
```
::1:smtp       inet n   -       -       -       -       smtpd
```
to 
```
smtp       inet n   -       -       -       -       smtpd
```
and commented out this line:
```
127.0.0.1:smtp inet n   -       -       -       -       smtpd
```
It worked right away after I did that (& restarted).

dm[/QUOTE]

---

### Post by gstrock on 2005-10-01
dude your instructions are f*cking excellent!
I've been all over the net trying to figure out
how to set this up on a Debian machine.  If you
go out and google you'll see there are a lot of
people hung up how to deal with the chroot aspect
of setting this up.  Your explanation is the first I've
seen that tells exactly what to do.  If I had found
your tutorial first I wouldn't have had to buy the
Book of Postfix. 
I can't thank you enough.
- greg s.

---

### Post by Zensunni on 2005-10-07
I keep getting an error in the last few steps of the setup.....When I type the "/etc/init.d/saslauthd start" command, it says Permission denied.

What does that mean? I've logged in on my login, sudo, and root....though, I think it's something to do with the key configuration.

I also don't have a clue what to do after that. How do I make new email accounts? what do I type in as incoming and outgoing when I set up an email client?

Any help?

---

### Post by snarkout on 2005-10-10
Thanks a lot for a ~*very*~ useful how-to.  You saved me hours of google fu.

---

### Post by willg on 2005-12-09
Dude, I just wanted to say thanks for instructions that actually get smtp-auth working under Debian. I have been trying to get this working for a long time. There is not one site out there that documents this properly as far as I know. I have tried them all. Sir, you are my hero.

---

### Post by caraboy on 2005-12-23
Ok, here are my problems: 

-when I connect with thunderbird using secure connection (pop3, 995) and when I log in a get a Maildir: No such file or directory error. 

-second thing, can I still use no secure connection to get my mails? It seems it is not working.... :(

---

### Post by psyncho on 2006-08-23
I've followed the directions exactly to find that I don't have a file at 

/etc/postfix/sasl/smtpd.conf

thus this command:

echo 'pwcheck_method: saslauthd' >> /etc/postfix/sasl/smtpd.conf

get a permission denied response.  Can anyone tell me what's going on with this, please? 

thanks, 
John

---

### Post by caraboy on 2006-09-02
You need to have root privileges to edit and create that file. So you should type sudo bash and enter your root passward before creating the file. This way you will enable the root shell.

---

