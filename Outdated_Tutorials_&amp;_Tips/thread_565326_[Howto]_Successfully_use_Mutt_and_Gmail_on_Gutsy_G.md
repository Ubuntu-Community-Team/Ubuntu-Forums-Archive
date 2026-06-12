---
title: "[Howto] Successfully use Mutt and Gmail on Gutsy Gibbon"
date: 2007-10-02
forum: Outdated Tutorials &amp; Tips
---

### Post by andrew.46 on 2007-10-02
***** This thread has been locked at the poster's request. The new version of this howto may be found [here](http://ubuntuforums.org/showthread.php?t=1021746) *****

================
**Introduction**
================

This page is a guide to using the email client Mutt to send, receive and read email under Ubuntu using a Gmail account as a relay. Despite the thread title, which speaks of Gutsy Gibbon, this guide should work under most versions of Ubuntu. I am using it myself under Intrepid Ibex with no problems.

There are a few steps involved but if followed carefully and in sequence you will soon be using Mutt successfully with your Gmail account.
 
In sequence we will:

[LIST=1]
[*]Set up an SSL and some certificates
[*]Set up the Mail Transport Agent msmtp
[*]Set up the Mail Transport Agent Fetchmail
[*]Set up the Mail Delivery Agent Procmail
[*]Set up our mail program Mutt
[/LIST]

Sections that require *your* details inserted are in bold and red to eliminate some confusion :-). Lets get started with SSL:

============
**SSL Tools**
============

Gmail uses the POP3-over-SSL protocol to protect the transmission of username and password over the Internet. You will need to install open ssl and a certificate pack:

```
$ sudo apt-get install openssl ca-certificates
```

Later you will need to add the necessary SSL instructions to Fetchmail, but the next step is to install the software to send mail from your computer to the server: ssmtp.

=========
**msmtp**
=========

msmtp is a great and wonderfully reliable way to move mail from your computer. Download it from the repository as follows:

```
$ sudo apt-get install msmtp
```

There is a single configuration file to be altered: $HOME/.msmtprc. It can be created and permissions set as follows:

```
$ touch $HOME/.msmtprc
$ touch $HOME/.msmtp.log
$ chmod 0600 $HOME/.msmtprc
```

Below is the required configuration for a Gmail server:

```
account default              
host smtp.gmail.com          
port 587                     
from **[COLOR="Red"]full.gmail.address@gmail.com[/COLOR]**   
tls on                       
tls_starttls on              
tls_trust_file /etc/ssl/certs/ca-certificates.crt
auth on                     
user **[COLOR="Red"]gmail.username [/COLOR]**       
password **[COLOR="Red"]mypassword [/COLOR]**       
logfile ~/.msmtp.log
```

Now to the MTA Fetchmail:

============
**Fetchmail**
============

Next to download fetchmail from the Ubuntu repository:

```
$ sudo apt-get install fetchmail
```

Once again a single configuration file is required and so you will need to create ~/.fetchmailrc as follows:

```
 $ vim ~/.fetchmailrc 
```

The following configuration allow Fetchmail to access and fetch email from Gmail, leave a copy of the mail on the Gmail server and pass the mail to Procmail on your local machine. The SSL configuration is included here as well:

```
poll pop.gmail.com                   # Tell fetchmail about server
with proto POP3                      # Use the POP-protocol       
user '**[COLOR="Red"]Gmail Username[/COLOR]** '               # Your Gmail Username            
there with password '**[COLOR="Red"]Gmail Password[/COLOR]**' # Your Gmail Password  
is '**[COLOR="Red"]username[/COLOR]**' here                   # Local Username                    
mda "/usr/bin/procmail -d %T"        # Tell fetchmail which MDA to use   
options                              # Options duh                                      
keep                                 # Keep the mail on server = safe
ssl                                  # Use ssl
sslcertck                            # Check the certificates
sslcertpath /etc/ssl/certs           # Path to the certificates
```

All done except as a final touch, since the username and password are openly in this file,you will need to make the file readable only by the file owner. If this is not done Fetchmail will not even run:

```
 $ chmod 600 ~/.fetchmailrc
```

Now would be a good to time to make sure you have [POP forwarding enabled]("http://gmail.google.com/support/bin/answer.py?answer=13273") in your Gmail account. You will find this in: Settings - Forwarding and POP.  Note also that Gmail has a little oddity in regard to the "keep" and "nokeep" command of Fetchmail. You cannot remove mail from Gmail servers via POP3 but you can choose to have your messages archived, kept or deleted once they have been downloaded via POP3. This is a Gmail setting hidden in Settings - Forwarding and POP: "When messages are accessed with POP...".

Now for the mail delivery program Procmail:

===========
**Procmail**
===========

Procmail can be easily downloaded from the repository:

```
$ sudo apt-get install procmail
```

So where will Procmail deliver to? Traditionally all mail goes to the location specified in the $MAIL environment variable, but in a default Ubuntu system this is often not set. Set the MAIL variable by opening ~/.bashrc as follows:

```
 $ vim ~/.bashrc 
```

and adding the following, using your *own* username:

```
# Sets the Mail Environment Variable
MAIL=/var/spool/mail/**[COLOR="Red"]username[/COLOR]** && export MAIL
```

A very simple configuration file must be created for procmail as follows:

```
$ vim ~/.procmailrc 
```

and below is a very simple start to what can be quite a complex file:

```
# Environment variable assignments
PATH=/bin:/usr/bin:/usr/local/bin 
VERBOSE=off                   # Turn on for verbose log
MAILDIR=$HOME/Mail            # Where Procmail recipes deliver
LOGFILE=$HOME/.procmaillog    # Keep a log for troubleshooting.
# Recipes
:0:
* ^TOmutt-user
mutt
```

I include a very simple sorting recipe with the file: this one intercepts everything addressed to "mutt-user" and directs it to $HOME/Mail/mutt. This is the mutt-user mailing list which I would advise all new mutt users to join. And lets not forget to create the Mail folder:

```
$ mkdir $HOME/Mail 
```

Now finally to the MUA: Mutt.

=======
**Mutt**
=======

The following command downloads mutt from the Ubuntu repository:

```
$ sudo apt-get install mutt
```

Mutt is driven by a configuration file that can be created as follows:

```
$ vim ~/.muttrc 
```

I have spent some time building this file from scratch but for you, Gentle Reader, I include here a more basic version, similar to the one I started from:

```
#======================================================#
# Boring details
set realname = "**[COLOR="Red"]Your realname[/COLOR]**"
set from = "**[COLOR="Red"]Email address[/COLOR]**"
set use_from = yes
set envelope_from ="yes"
set sendmail="/usr/bin/msmtp"

# If not set in environment variables:
set spoolfile = /var/spool/mail/**[COLOR="Red"]user-name[/COLOR]**

#======================================================#
# Folders
set folder="~/Mail"                # Mailboxes in here
set record="+sent"                 # where to store sent messages
set postponed="+postponed"         # where to store draft messages
set move=no                        # Don't move mail from the spool.

#======================================================#
# Watch these mailboxes for new mail:
mailboxes ! +Fetchmail +slrn +mutt
set sort_browser=alpha    # Sort mailboxes by alpha(bet)

#======================================================#
# Order of headers and what to show
hdr_order Date: From: User-Agent: X-Mailer \
          To: Cc: Reply-To: Subject:
ignore *
unignore Date: From: User-Agent: X-Mailer  \
         To: Cc: Reply-To: Subject:
               
#======================================================#
# which editor do you want to use? 
# vim of course!
set editor="vim -c 'set tw=70 et' '+/^$' " 
set edit_headers          # See the headers when editing

#======================================================#
# Aliases

set sort_alias=alias     # sort aliases in alpha order by alias name

#======================================================#
# Colours: This scheme is fairly basic and only
# really works if your Terminal background is white

color hdrdefault black        default   
color quoted     red          default   
color signature  brightblack  default   
color indicator  brightwhite  red
color attachment black        green
color error      red          default   
color message    blue         default   
color search     brightwhite  magenta
color status     brightyellow blue
color tree       red          default   
color normal     blue         default   
color tilde      green        default   
color bold       brightyellow default   
color markers    red          default  

#======================================================#
# Odds and ends
set markers          # mark wrapped lines of text in the pager with a +
set smart_wrap       # Don't wrap mid-word
set pager_context=5  # Retain 5 lines of previous page when scrolling.
set status_on_top    # Status bar on top.
push <show-version>  # Shows mutt version at startup
```

**Note: ** Procmail will create your mailbox in the spool, and set the appropriate permissions, when it first receives mail from fetchmail so don't worry that mutt cannot *initially* find this mailbox. If you wish to create the mailbox yourself the following permissions and ownership are required (taken from my own system):

```
-rw-rw---- 1 andrew mail 0 2008-10-23 10:12 /var/spool/mail/andrew
```


And finally it is reward time as you open Mutt, type ! to open a shell prompt, type fetchmail -v and start reading your mail! My parting gift is a little macro that was written for me by a generous person on the mutt-user mailing list that will actually do this for you when you simply press the key "I". Place the following in your ~/.muttrc file:

```
macro index,pager I '<shell-escape> fetchmail -v<enter>'
```

And welcome to the world of mutt!

October 23rd, 2008
Andrew Strong

---

### Post by wounded on 2007-10-04
I'd like to report one success.

I had tried to set mutt up a long while ago and always ran into some sort of issue with something, which I imagine is easy when you need to configure three to four programs to set one up correctly, but I went through and followed your post and only had one error (Which was due to me not realizing I had left a space at the end of my gmail username - easily fixed!). 

Also, I think you also have to turn on POP forwarding in the settings of your gmail account. Not a big deal, unless you don't know about the gmail setting.


I have some questions that maybe you can help me with (Or at least point in the right direction :o )

In my gmail account I have filters that sort through and apply labels to different emails I receive. Is there a way for mutt to use these labels to sort through? Or maybe that would be procmail that would do that?

Thanks for the post, it helped at least one poor soul :]

---

### Post by andrew.46 on 2007-10-04
Hi,

 Glad you had success with the walkthrough:

> **wounded said:**
> I'd like to report one success.
[...]
Also, I think you also have to turn on POP forwarding in the settings of your gmail account. Not a big deal, unless you don't know about the gmail setting.

I have some questions that maybe you can help me with (Or at least point in the right direction :o )

In my gmail account I have filters that sort through and apply labels to different emails I receive. Is there a way for mutt to use these labels to sort through? Or maybe that would be procmail that would do that?
Thanks for the post, it helped at least one poor soul :]

 Good point about the Gmail POP forwarding, I have added it in. As for filtering and labelling mutt will not use gmail filters. You will have to set procmail up for that and trust me that syntax is *not* easy!

 All the very best,

      Andrew

---

### Post by wounded on 2007-10-04
> **andrew.46 said:**
> Hi,

 Glad you had success with the walkthrough:



 Good point about the Gmail POP forwarding, I have added it in. As for filtering and labelling mutt will not use gmail filters. You will have to set procmail up for that and trust me that syntax is *not* easy!

 All the very best,

      Andrew

Well, that's not a very big deal. Would you happen to have any particularly good procmail/mutt links you could share?

---

### Post by andrew.46 on 2007-10-04
Hi,

 Had a quick dig in my bookmarks:

> **wounded said:**
> Well, that's not a very big deal. Would you happen to have any particularly good procmail/mutt links you could share?

 For procmail:

[http://lipas.uwasa.fi/~ts/info/proctips.html](http://lipas.uwasa.fi/~ts/info/proctips.html)
[http://partmaps.org/era/procmail/mini-faq.html](http://partmaps.org/era/procmail/mini-faq.html)

 For mutt:

[http://therandymon.com/content/view/42/79/](http://therandymon.com/content/view/42/79/)
(This is the Woodnots: highly reccomended!)

[http://mutt.blackfish.org.uk/](http://mutt.blackfish.org.uk/)

 Should get you off to a start :-)

           Andrew

---

### Post by wounded on 2007-11-15
And now... imap howto? :D

---

### Post by andrew.46 on 2007-11-15
Hi,

 Thanks for the suggestion:

> **wounded said:**
> And now... imap howto? :D

 and it strikes me that this could be a project that you might rmbrace yourself :-) I do not actually use Ubuntu any more and simply hang around the forums supporting a few of the walkthroughs that I have put together.

 I guess a starting point would be to compile mutt with the appropriate option: --enable-imap ?

                Andrew

---

### Post by hugmenot on 2007-11-17
IMAP with Gmail is real easy, and a lot shorter than what you put up.
Just put a few lines into your muttrc and it works. No compilation or installs neccesary.

```
set imap_user = 'hug@gmail.com'
set spoolfile = imaps://imap.gmail.com:993/INBOX
set folder = imaps://imap.gmail.com:993
set record="" #gmail does recording on its own
set postponed="imaps://imap.gmail.com/[Gmail]/Drafts"
set trash="imaps://imap.gmail.com/[Gmail]/Trash"
set realname="Hug M. Not"
set from="hug@gmail.com"

#maybe these too
set imap_check_subscribed="yes"
set imap_list_subscribed="yes"

set smtp_url="smtp://hug@smtp.gmail.com:587/"

set header_cache=~/.mutt/hcache
set message_cachedir="~/.mutt/msgcache/"
set certificate_file=~/.mutt/certs

#and maybe some useful bindings
macro index,pager y "<save-message>=[Gmail]/All Mail<enter><enter>" "Archive"
macro index,pager d "<save-message>=[Gmail]/Trash<enter><enter>" "Trash"
macro index,pager s "<save-message>=[Gmail]/Spam<enter><enter>" "Spam"
macro index gi "<change-folder>=INBOX<enter>" "Go to inbox"
macro index ga "<change-folder>=[Gmail]/All Mail<enter>" "Go to all mail"
macro index gs "<change-folder>=[Gmail]/Starred<enter>" "Go to starred messages"
macro index gd "<change-folder>=[Gmail]/Drafts<enter>" "Go to drafts"
macro index go "<change-folder>=[Gmail]/Sent Mail<enter>" "Go to sent Mail"
macro index gp "<change-folder>=[Gmail]/Spam<enter>" "Go to Spam"


```

---

### Post by boob11 on 2007-11-19
thnx :lolflag:

---

### Post by andrew.46 on 2007-11-20
Hi,

 Read your reply to my mutt walkthrough:

> **hugmenot said:**
> IMAP with Gmail is real easy, and a lot shorter than what you put up.
Just put a few lines into your muttrc and it works. No compilation or installs neccesary.

 You are being a little harsh there :-) As far as I know Gmail only started rolling out imap to its accounts in the end of October 2007. Certainly this walkthrough will start to be a little dated now but I think it is still a valid approach while Gmail imap support matures.

 Once this support has matured certainly this walkthrough will be ready for the archives, although it can easily be modified for standard POP3 accounts.

                      Andrew

---

### Post by hugmenot on 2007-11-20
No harshness intended. You sounded like IMAP support would be even more complicated including re-compiling of stuff. It isn't so I posted the config.

---

### Post by blackvnu on 2007-11-20
hi!
how can send mail using mutt, i tried but system error: authenticate fails

plz help
thanks

---

### Post by andrew.46 on 2007-11-20
Hi:
> **blackvnu said:**
> hi!
how can send mail using mutt, i tried but system error: authenticate fails

plz help
thanks

Mutt itself does not send the mail, that is done by ssmtp in this example. Have a close look at the following in ssmtp:

```
AuthUser=Gmail Username       # Your Gmail Username
AuthPass=Gmail Password       # Your Gmail Password
```

and see if there is a problem. If you cannot correct the problem here could you post the exact error message as well as the contents of your /etc/ssmtp/ssmtp.conf file?

   Andrew

---

### Post by blackvnu on 2007-11-20
hi 
at terminal run command: mutt ->compose mail when i sending , and had system error message
```
sendmail: Authorization failed (454 4.7.0 Cannot authenticate due to temporary
```

it's my **ssmtp.conf** 

```
root=datleduy@gmail.com            # Your email address
mailhub=smtp.gmail.com:587    # Gmail details
UseSTARTTLS=YES               # Send SSL/TLS messages to Gmail
AuthUser=datleduy       # Your Gmail Username
AuthPass=*********       # Your Gmail Password
rewriteDomain=gmail.com       # So the message appears to come from Gmail
FromLineOverride=YES          # So the message appears to come from Gmail
hostname=blackvnu-laptop             # Hostname: use hostname -f in a Terminal
```

---

### Post by andrew.46 on 2007-11-21
Hi,

 Might not be so bad:

> **blackvnu said:**
> hi 
at terminal run command: mutt ->compose mail when i sending , and had system error message
```
sendmail: Authorization failed (454 4.7.0 Cannot authenticate due to temporary
```

 I suspect the full message is:

> AUTH FAIL Backend offline: 454 4.7.0 Cannot authenticate due to temporary system problem. Try again later.

 Could very well be a Gmail problem. In this case wait 24 hours and try again. Can you access by the web interface?

               Andrew

---

### Post by blackvnu on 2007-11-21
> Could very well be a Gmail problem. In this case wait 24 hours and try again. Can you access by the web interface?

yes, i used both web interface and thunderbird, it's ok!

---

### Post by andrew.46 on 2007-11-21
Hi:

> **blackvnu said:**
> yes, i used both web interface and thunderbird, it's ok!

 Well in that case it is not a Gmail problem. Can you run the following 2 commands and post the results:

```
$ sudo updatedb
$ slocate ssmtp
```

 The updatedb command may take a while.

               Andrew

---

### Post by andrew.46 on 2007-11-21
Hi:

> **hugmenot said:**
> No harshness intended. You sounded like IMAP support would be even more complicated including re-compiling of stuff. It isn't so I posted the config.

 In fact courtesy of your .muttrc I have tried IMAP with Gmail and of course you are perfectly correct: it is fairly straightforward to setup. Mind you I did have to recompile my copy of mutt with:

```
./configure --enable-imap --with-ssl
```

 But then the whole process was easy. So now I am not entirely clear where this leaves guides such as mine? This particular walkthrough is the Ubuntu version of my own walkthrough, which was written and tested with Slackware and aimed at *all* distros:

[http://people.aapt.net.au/~adjlstrong/mutt.html](http://people.aapt.net.au/~adjlstrong/mutt.html)

which delves into SSl / TLS authentication a little more and substitutes the much better msmtp for ssmtp. In fact what I might do is include advice at the head of this walkthrough that IMAP is here and the following is out of date etc etc. My own personal guide I will continue to maintain as I think there is still a need for this sort of access to Gmail and also POP3 mailboxes plus I put many hours into the ssl / tls info!!

 Thanks you very much for pointing me towards IMAP / Gmail and furnishing the relevant ~/.muttrc sections.

               Andrew

---

### Post by andrew.46 on 2007-11-21
Hi,

 A final question:

> **hugmenot said:**
> 
```
set trash="imaps://imap.gmail.com/[Gmail]/Trash"
```


 I can see nothing in Mutt 1.5.17  to cover the use of a trash folder. Is this a macro or something discontinued in the developer version?

                 Andrew

---

### Post by hugmenot on 2007-11-21
man muttrc
```

      trash
              Type: path
              Default: &#8220;&#8221;

              If  set,  this  variable specifies the path of the trash folder where the mails marked for
              deletion will be moved, instead of being irremediably purged.

              NOTE: When you delete a message in the trash folder, it is really  deleted,  so  that  you
              have a way to clean the trash.
```

my macro is this:
```
macro index,pager d "<save-message>=[Gmail]/Trash<enter><enter>" "Trash"
```

---

### Post by hugmenot on 2007-11-21
> **andrew.46 said:**
> you I did have to recompile my copy of mutt with:

```
./configure --enable-imap --with-ssl
```

 But then the whole process was easy.

I see, but this is not needed in Ubuntu. It&#8217;s all compiled in.

$ mutt -v
```

Mutt 1.5.15+20070412 (2007-04-11)
Copyright (C) 1996-2007 Michael R. Elkins and others.
Mutt comes with ABSOLUTELY NO WARRANTY; for details type `mutt -vv'.
Mutt is free software, and you are welcome to redistribute it
under certain conditions; type `mutt -vv' for details.

System: Linux 2.6.22-14-generic (i686)
ncurses: ncurses 5.6.20070716 (compiled with 5.6)
libidn: 1.0 (compiled with 1.0)
Compile options:
-DOMAIN
+DEBUG
-HOMESPOOL  +USE_SETGID  +USE_DOTLOCK  +DL_STANDALONE  
+USE_FCNTL  -USE_FLOCK   +USE_INODESORT   
+USE_POP  +USE_IMAP  +USE_SMTP  -USE_GSS  -USE_SSL_OPENSSL  +USE_SSL_GNUTLS  +USE_SASL  +HAVE_GETADDRINFO  
+HAVE_REGCOMP  -USE_GNU_REGEX  
+HAVE_COLOR  +HAVE_START_COLOR  +HAVE_TYPEAHEAD  +HAVE_BKGDSET  
+HAVE_CURS_SET  +HAVE_META  +HAVE_RESIZETERM  
+CRYPT_BACKEND_CLASSIC_PGP  +CRYPT_BACKEND_CLASSIC_SMIME  +CRYPT_BACKEND_GPGME  
-EXACT_ADDRESS  -SUN_ATTACHMENT  
+ENABLE_NLS  -LOCALES_HACK  +COMPRESSED  +HAVE_WC_FUNCS  +HAVE_LANGINFO_CODESET  +HAVE_LANGINFO_YESEXPR  
+HAVE_ICONV  -ICONV_NONTRANS  +HAVE_LIBIDN  +HAVE_GETSID  +USE_HCACHE  
-ISPELL
SENDMAIL="/usr/sbin/sendmail"
MAILPATH="/var/mail"
PKGDATADIR="/usr/share/mutt"
SYSCONFDIR="/etc"
EXECSHELL="/bin/sh"
MIXMASTER="mixmaster"
To contact the developers, please mail to <mutt-dev@mutt.org>.
To report a bug, please visit http://bugs.mutt.org/.

patch-1.5.13.cd.ifdef.2
patch-1.5.13.cd.purge_message.3.4
patch-1.5.13.cd.trash_folder.3.4
patch-1.5.13.nt+ab.xtitles.4
patch-1.5.14.rr.compressed.1
patch-1.5.4.vk.pgp_verbose_mime
patch-1.5.6.dw.maildir-mtime.1

```

---

### Post by andrew.46 on 2007-11-21
Hi,

 Thanks for that:

> **hugmenot said:**
> I see, but this is not needed in Ubuntu. It’s all compiled in [...].

 I think you have just demonstrated to me why I should really *not* be trying to support my walkthrough when I no longer run Ubuntu. Using Slackware I have downloaded the source and made my own compile-time options and I have not used any patches. I have actually added a few more configure options:

```
./configure --enable-imap --with-ssl --with-sasl --enable-smtp --enable-hcache
```

and ended up with:

> Mutt 1.5.17 (2007-11-01)
Copyright (C) 1996-2007 Michael R. Elkins and others.
Mutt comes with ABSOLUTELY NO WARRANTY; for details type `mutt -vv'.
Mutt is free software, and you are welcome to redistribute it
under certain conditions; type `mutt -vv' for details.

System: Linux 2.6.21.5-smp (i686)
ncurses: ncurses 5.6.20070217 (compiled with 5.6)
libidn: 0.6.10 (compiled with 0.6.10)
hcache backend: GDBM version 1.8.3. 10/15/2002 (built Feb 15 2007 17:04:52)
Compile options:
-DOMAIN
-DEBUG
-HOMESPOOL  -USE_SETGID  +USE_DOTLOCK  -DL_STANDALONE  
+USE_FCNTL  -USE_FLOCK   -USE_INODESORT   
-USE_POP  +USE_IMAP  +USE_SMTP  -USE_GSS  +USE_SSL_OPENSSL  -USE_SSL_GNUTLS  +USE_SASL  +HAVE_GETADDRINFO  
+HAVE_REGCOMP  -USE_GNU_REGEX  
+HAVE_COLOR  +HAVE_START_COLOR  +HAVE_TYPEAHEAD  +HAVE_BKGDSET  
+HAVE_CURS_SET  +HAVE_META  +HAVE_RESIZETERM  
+CRYPT_BACKEND_CLASSIC_PGP  +CRYPT_BACKEND_CLASSIC_SMIME  -CRYPT_BACKEND_GPGME  
-EXACT_ADDRESS  -SUN_ATTACHMENT  
+ENABLE_NLS  -LOCALES_HACK  +HAVE_WC_FUNCS  +HAVE_LANGINFO_CODESET  +HAVE_LANGINFO_YESEXPR  
+HAVE_ICONV  -ICONV_NONTRANS  +HAVE_LIBIDN  +HAVE_GETSID  +USE_HCACHE  
ISPELL="/usr/bin/ispell"
SENDMAIL="/usr/bin/sendmail"
MAILPATH="/var/mail"
PKGDATADIR="/usr/local/share/mutt"
SYSCONFDIR="/usr/local/etc"
EXECSHELL="/bin/sh"
-MIXMASTER
To contact the developers, please mail to <mutt-dev@mutt.org>.
To report a bug, please visit [http://bugs.mutt.org/](http://bugs.mutt.org/).

 An absolutely fascinating comparison and certainly demonstrates the work that the Ubuntu people put into their product. 

                Andrew

---

### Post by hugmenot on 2007-11-22
> **andrew.46 said:**
> 
 An absolutely fascinating comparison and certainly demonstrates the work that the Ubuntu people put into their product. 

Or, in fact, the Debian people. Well maintained packages like this are usually merged verbatim. And the difference in philosophies between Slackware and Debian is well known, isn't it?

---

### Post by ctyc on 2007-12-13
ok using the default mutt from the 7.10 repositories and Andrews fine tutorial I not have mutt working fine for Gmails new imap.

Thanks Andrew and keep up the great work.

---

### Post by andrew.46 on 2007-12-13
Hi,

 Thanks for your message:

> **ctyc said:**
> ok using the default mutt from the 7.10 repositories and Andrews fine tutorial I not have mutt working fine for Gmails new imap.

Thanks Andrew and keep up the great work.

Glad you found some use with this posting of mine. Unfortunately I am not writing too much more for these forums as I no longer use Ubuntu. I drift through the forums like an old ghost sometimes, just checking up on some of these walkthroughs that I wrote ...

Anyway all the best with mutt, it is a fantastic program and still under very active development.

              Andrew

---

### Post by kvk on 2008-03-23
Hi Folks~

Andrew, I hope I catch you in one of your ghostly drift-throughs. :)

First off, I am unable to find Mutt in the 7.10 repositories, even though I've enabled universal selections. Anyone have any idea why?

Given that, however, I've installed Mutt directly from Berlios, which means that I need to follow Andrew's original walk-through to set everything straight. I did notice, however, that even after recompiling Mutt with IMAP enabled, as per Andrew's post above, the Mutt -v output still reads that neither IMAP not SSL are functioning. I imagine that I've left a step out from the walk-through.

My biggest question is whether it is possible to add multiple sections to the Muttrc file to enable multiple email accounts to be directed into Mutt, even if Gmail is IMAP-enabled and others are older POP3 functions. 

Thanks so much! These forums are completely invaluable. :)

KVK

---

### Post by andrew.46 on 2008-03-24
Hi,

 Here I am, drifting through :-)

> **kvk said:**
> Hi Folks~

Andrew, I hope I catch you in one of your ghostly drift-throughs. :)

First off, I am unable to find Mutt in the 7.10 repositories, even though I've enabled universal selections. Anyone have any idea why?

It is definitely there, although it is a slightly older version:

[http://packages.ubuntu.com/gutsy/mail/mutt](http://packages.ubuntu.com/gutsy/mail/mutt)

This should be fully kitted-out for IMAP.

> Given that, however, I've installed Mutt directly from Berlios, which means that I need to follow Andrew's original walk-through to set everything straight. I did notice, however, that even after recompiling Mutt with IMAP enabled, as per Andrew's post above, the Mutt -v output still reads that neither IMAP not SSL are functioning. I imagine that I've left a step out from the walk-through.

You mean this bit:

```
./configure --enable-imap --enable-smtp --enable-hcache --with-ssl --with-sasl
```

I no longer have ubuntu installed at all now so I cannot check but I suspect you are missing the dev files required by the compile process. For example to finde the required dev file for sasl you would search as follows:
```

$ apt-cache search sasl | grep dev
```

and then download the suggested file. Same for ssl, and then recompile.

> My biggest question is whether it is possible to add multiple sections to the Muttrc file to enable multiple email accounts to be directed into Mutt, even if Gmail is IMAP-enabled and others are older POP3 functions. 

I am afraid that for my own use I have abandoned IMAP with gmail and returned to the 'old' way of doing things: fetchmail / procmail / mutt / msmtp and I am a lot happier. There is a growing body of information online about mutt and IMAP which may be of some assistance though. A starter is:

[http://www.mutt.org/doc/manual/manual-4.html#ss4.11](http://www.mutt.org/doc/manual/manual-4.html#ss4.11)

My apologies for being less than helpful with your query, hopefully someone can assist with greater detail.

               Andrew

---

### Post by kvk on 2008-03-24
No worries! You've been a wealth of information!

I need to wade through the Mutt documentation, and I think I'll explore setting up multiple POP3 servers routed to Mutt- I'll bet there is information on that in the documentation.

Thank you!

KVK

---

### Post by mavi_yelkenler on 2008-04-17
thanks Andrew. I am now able to use mutt. Mutt is really great

---

### Post by andrew.46 on 2008-04-17
Hi:

> **mavi_yelkenler said:**
> thanks Andrew. I am now able to use mutt. Mutt is really great

It is my pleasure :-)

      Andrew

---

### Post by go_beep_yourself on 2008-07-13
Does anybody know how to apply Gmail labels from Mutt and archive mail from Mutt?

---

### Post by hugmenot on 2008-07-13
[http://mail.google.com/support/bin/answer.py?answer=77657](http://mail.google.com/support/bin/answer.py?answer=77657)

i.e., labels map to folders.

---

### Post by go_beep_yourself on 2008-07-13
a

---

### Post by go_beep_yourself on 2008-07-13
[QUOTE=andrew.46;3461402]

There is a single configuration file to be altered: /etc/ssmtp/ssmtp.conf. Below is the required configuration for a Gmail server:
```
root=Email Address            # Your email address
mailhub=smtp.gmail.com:587    # Gmail details
UseSTARTTLS=YES               # Send SSL/TLS messages to Gmail
AuthUser=Gmail Username       # Your Gmail Username
AuthPass=Gmail Password       # Your Gmail Password
rewriteDomain=gmail.com       # So the message appears to come from Gmail
FromLineOverride=YES          # So the message appears to come from Gmail
hostname=Hostname             # Hostname: use hostname -f in a Terminal 
```



I didn't need to install ssmtp or do any of the above. I have this in my ~/.muttrc.

[PHP] 99 set imap_user = 'myuser@gmail.com'
100 set imap_pass = 'mypass'
101 set from = "myuser@gmail.com"
102 set realname = "My Name"
103 set spoolfile = "imaps://imap.gmail.com:993/INBOX"
104 set folder = imaps://imap.gmail.com:993
105 set smtp_url = "smtp://myuser@smtp.gmail.com:587/"
106 set record = "imaps://imap.gmail.com/[Gmail]/Sent Mail"
107 set postponed = "imaps://imap.gmail.com/[Gmail]/Drafts"
108 set header_cache = "~/.mutt/cache/headers"
109 set message_cachedir = "~/.mutt/cache/bodies"
110 set certificate_file = "~/.mutt/certificates"
111 set imap_check_subscribed = yes # this allows me to see labelled email[/PHP]

So Mutt uses the smtp server of Gmail just like any other mail client without the need of my own additional smtp software. This has worked, but I would like to know how to do the following by using Mutt alone.

[PHP]UseSTARTTLS=YES               # Send SSL/TLS messages to Gmail
AuthUser=Gmail Username       # Your Gmail Username
AuthPass=Gmail Password       # Your Gmail Password[/PHP]

Also, it would be nice if you explained hooks and aliases on your website or this howto.:popcorn:

---

### Post by shortylonglegs on 2008-07-14
Is there a way I could set up a script to automatically send a message to an address when the script is run?  I would like to set it up as a sort of security system, so it emails me whenever the script is run [startup or something].  I looked at the man page and got it to attach the file and have the right address/subject, but it still makes me confirm everything by hitting enter several times.  Sorry if this is an unrelated issue that doesn't belong here.

---

### Post by go_beep_yourself on 2008-07-14
If you want a script that sends emails, Mutt is not best for that. Try sendemail.

```
sudo apt-get install sendemail
```

---

### Post by andrew.46 on 2008-07-14
Hi:

> **go_beep_yourself said:**
> 

[...] it would be nice if you explained hooks and aliases on your website or this howto.:popcorn:

I do not use Ubuntu any more so this guide will no longer be updated, although the website will receive more work. A few points that would really need to be addressed by anybody keen enough to write their own:

[LIST=1]
[*]I cordially loathe IMAP but I guess it needs to be addressed.
[*]ssmtp is abandoned software and not particularly feature-rich. MI believe msmtp would be a better choice.
[*]More complex features should be addressed like multiple identities etc
[/LIST]

This guide will work as it is, I would not leave it broken, but it simply needs a major update and rewrite.

    Andrew

---

### Post by Chriseverclear on 2008-07-26
I am having trouble running a minor issue with Mutt.

I have followed the entire instructions. Running mutt in terminal is fine, but it is not retrieving any messages. I was able to use fetchmail -v, and it looks like it is retrieving but when i access mutt, i don't see anything.

What do i have to look for? I have also enable gmail setting as instructed.

thanks
chriseverclear

---

### Post by andrew.46 on 2008-07-26
Hi Chriseverclear,

 Can I ask what you have set in your muttrc for:

```
set spoolfile = ??
```

   Andrew

---

### Post by Chriseverclear on 2008-07-27
> **andrew.46 said:**
> Hi Chriseverclear,

 Can I ask what you have set in your muttrc for:

```
set spoolfile = ??
```

   Andrew

I haven't set anything. I just use the same in your initial instruction.

I have tried using my gmail username but it is not fetching and emails.


set spoolfile = /var/spool/mail/user-name

---

### Post by Chriseverclear on 2008-07-27
Hi Andrew,

I finally solved the issue.

It is because i used my gmail username instead of my Ubuntu username.

# Sets the Mail Environment Variable
MAIL=/var/spool/mail/ubuntu_username && export MAIL

and set spoolfile.

thanks,
chris

---

### Post by andrew.46 on 2008-07-27
Hi:

> **Chriseverclear said:**
> I haven't set anything. I just use the same in your initial instruction:

set spoolfile = /var/spool/mail/user-name

My apologies for the confusion: it should not actually be 'user-name', it should actually be the username that you log on to your computer with. This can be seen at the console by typing in:

```
$ echo $USER
```

This is  something I clarified [on my website]("http://www.andrews-corner.org/mutt.html") but as I am not developing my Ubuntu guides any more it has remained a little confusing here.

  Andrew

---

### Post by TeknoPhil on 2008-08-04
Thanks for this great tutorial Andrew.

I have a n00b question : How does mail knows about ssmtp? (I just did step 1 and 2 to be able to send a mail through gmail's smtp and it's working... don't we need to map the command mail to ssmtp?)

did I miss something :)

Thanks

---

### Post by andrew.46 on 2008-08-04
Hi,

Thanks for your message:

> **TeknoPhil said:**
> Thanks for this great tutorial Andrew.

I have a n00b question : How does mail knows about ssmtp? (I just did step 1 and 2 to be able to send a mail through gmail's smtp and it's working... don't we need to map the command mail to ssmtp?)

did I miss something :)

Thanks

Not such a n00b question :-). I must confess that I no longer run Ubuntu so I can only give a general answer here but I think you will find that a default installation of ssmtp in Ubuntu includes a sendmail symlink. So any program that looks for sendmail will find ssmtp instead. To test this find the path to sendmail on your system:

```
andrew@ilium~$ which sendmail
/usr/bin/sendmail
```

and then run:

```
andrew@ilium~$ ls -l /usr/bin/sendmail
lrwxrwxrwx 1 root root 18 2008-02-18 11:11 /usr/bin/sendmail -> /usr/sbin/sendmail
```

On my current system you can see a symlink to /usr/sbin/sendmail, on your system I would bet that the link goes to ssmtp. Let me know how this goes as it would be nice to get this 'on the record' in the forums.

Sorry I cannot test this myself :(.

  Andrew

---

### Post by TeknoPhil on 2008-08-05
> **andrew.46 said:**
> Hi,

Thanks for your message:



Not such a n00b question :-). I must confess that I no longer run Ubuntu so I can only give a general answer here but I think you will find that a default installation of ssmtp in Ubuntu includes a sendmail symlink. So any program that looks for sendmail will find ssmtp instead. To test this find the path to sendmail on your system:

```
andrew@ilium~$ which sendmail
/usr/bin/sendmail
```

and then run:

```
andrew@ilium~$ ls -l /usr/bin/sendmail
lrwxrwxrwx 1 root root 18 2008-02-18 11:11 /usr/bin/sendmail -> /usr/sbin/sendmail
```

On my current system you can see a symlink to /usr/sbin/sendmail, on your system I would bet that the link goes to ssmtp. Let me know how this goes as it would be nice to get this 'on the record' in the forums.

Sorry I cannot test this myself :(.

  Andrew

Thanks a lot Andrew, that's exactly the case on my system!

---

### Post by TeknoPhil on 2008-08-05
Andrew,
I need to send email through a HTTP proxy server, do you happen to know how to set SSMTP to go through it?
Thanks again!

EDIT : Never mind ... my company is blocking most of the port on our router (like port 587), I'll figure this out first.

Thanks!

---

### Post by andrew.46 on 2008-08-11
Hi:


> **TeknoPhil said:**
> Andrew,
I need to send email through a HTTP proxy server, do you happen to know how to set SSMTP to go through it?
Thanks again!
EDIT : Never mind ... my company is blocking most of the port on our router (like port 587), I'll figure this out first.

If you ever feel the need for a bit more flexibility you could try msmtp which I personally use instead of ssmpt. Having said that when I used ssmtp it caused me absolutely no trouble whatsoever. I have an msmtp setup for gmail on my website:

[http://www.andrews-corner.org/mutt.html#sending](http://www.andrews-corner.org/mutt.html#sending)

  Andrew

---

### Post by lukanium on 2008-08-14
Thanks you very much, this works smoothly with google apps also.

---

### Post by Coastal Confessions on 2008-11-25
> **hugmenot said:**
> ```
macro index ga "<change-folder>=[Gmail]/All Mail<enter>" "Go to all mail"
macro index go "<change-folder>=[Gmail]/Sent Mail<enter>" "Go to sent Mail"

```

These two macros won't work due to Space being already bound to a key. See this thread: [http://marc.info/?t=120431869400001&r=1&w=2](http://marc.info/?t=120431869400001&r=1&w=2)

These macros work:
```

macro index ga "<change-folder>=[Gmail]/All<quote-char> Mail<enter>" "Go to all mail"
macro index gt "<change-folder>=[Gmail]/Sent<quote-char> Mail<enter>" "Go to sent Mail"

```

---

### Post by Chapatt on 2008-11-28
Is there any way that I can move my mailbox from "/var/spool/mail" to "/home/$home/Mail" and rename it "inbox"? Thanks!

EDIT: I resolved the problem on my own (surprisingly, seeing as I'm only semi-CLI literate)!

---

### Post by andrew.46 on 2008-11-29
Hi,

Finally cut ssmtp loose and replaced it with msmtp. I nicer program that is still under active development and *very* well documented. Hope everybody is as happy with it as I am :-).

  Andrew

---

### Post by jcr1 on 2008-12-12
Hi,

Nice HOWTO!

I am a little confused though... I found this howto after having a go with mutt... 

I simply created the .fetchmailrc very similar to yours. 

I then ran fetchmail -dk 600 to check and keep mail on server every 10 mins.

after that i did nothing else... 
I opened mutt it recieved emails and I could send them too (after adding a muttrc like yours)

But I have done none of the other instructions in your HOWTO. Why is mine working? Perhaps I am leaving myself open to attack by not following all the instructions?

Cheers.

---

### Post by andrew.46 on 2008-12-12
Hi jcr1,

Well, there are many ways ways to get mail using mutt. If your works well you should leave it as it is :-). Are you using gmail? This usually involves a few extra steps although IMAP has made this all a bit easier.

The method I show is the 'traditional' unix way which is falling out of favour with many these days.

 All the best,

  Andrew

---

### Post by enoughsaid05 on 2008-12-20
Hi

I have followed your directions in the very first post. I tried sending email to myself and checked the mail using fetchmail, but it says there is no email for me. When I checked the email on the server, the email is there. How do I solve this problem?

Thanks!

---

### Post by enoughsaid05 on 2008-12-20
Hi all

I just realise that whenever I type in the fetchmail command in my own terminal, I see that on the webmail (that is on the browser because I run browser and terminal simultaneously) it downloads the email from the server, but in the terminal it says that there are no mail on the server.

Help!! How am I going to use mutt??

---

### Post by andrew.46 on 2008-12-20
Hi enoughsaid,

> **enoughsaid05 said:**
> Hi

I have followed your directions in the very first post. I tried sending email to myself and checked the mail using fetchmail, but it says there is no email for me. When I checked the email on the server, the email is there. How do I solve this problem?

This is a 'feature' of Gmail and it is a right royal PITA that unfortunately cannot be bypassed. One possibility is to use another smtp server or simply create another gmail address for testing purposes.

If you like send me the address by PM, not openly in the forum, and I will send an email :-).

All the best,

  Andrew

---

### Post by enoughsaid05 on 2008-12-20
Thanks for the reply!!

What feature is this? What is PITA?

---

### Post by enoughsaid05 on 2008-12-20
Hi
I get what you mean. I get my friend to send me a mail and I can receive it. So this means that I wouldn't be able to send email to myself in gmail afterall, am I right to say that?

Thanks for the info!

---

### Post by andrew.46 on 2008-12-20
Hi again!

> **enoughsaid05 said:**
> Thanks for the reply!!

What feature is this? What is PITA?

Google has deliberately blocked the ability to download a copy of email that you have sent to yourself, they call it a 'feature' of the service they provide. PITA is an acronym for 'Pain in the <rear-end>' :-).

  Andrew

---

### Post by andrew.46 on 2008-12-20
Hi!

> **enoughsaid05 said:**
> Hi
I get what you mean. I get my friend to send me a mail and I can receive it. So this means that I wouldn't be able to send email to myself in gmail afterall, am I right to say that?

Yes this is correct. There is a work-around which I have not tested which is where in your .msmtprc you specify a different server, for example the one provided by your ISP. It all starts to get a little silly though :-).

  Andrew

---

### Post by enoughsaid05 on 2008-12-20
I got it set up quite nicely, but then got a few minor problems

How do I get mutt to notify which mailboxes have new mails. I have set up certain parameters in procmail file and muttrc such that mails that satisfy certain criteria goes to specific mailboxes, but mutt doesn't notify me. Is there a workaround?

Thanks!

---

### Post by andrew.46 on 2008-12-21
Hi enoughsaid,

> **enoughsaid05 said:**
> How do I get mutt to notify which mailboxes have new mails. I have set up certain parameters in procmail file and muttrc such that mails that satisfy certain criteria goes to specific mailboxes, but mutt doesn't notify me. Is there a workaround?

In the sample ~/.muttrc I have given in the guide you will see the following:

```
# Watch these mailboxes for new mail:
mailboxes ! +Fetchmail +slrn +mutt
```

Simply add your mailboxes to this using similar syntax. When you press 'c' to change folders mutt will prompt you to change to the folders with new mail.

Hope that helps?

 Andrew

---

