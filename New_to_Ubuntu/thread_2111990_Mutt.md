---
title: "Mutt"
date: 2013-02-03
forum: New to Ubuntu
---

### Post by GrouchyGaijin on 2013-02-03
Hi Folks,

I have been struggling with mutt for several days and finally *kind of* have it working.

Below please find a copy of my ~/.muttrc file:

```
set from = "me@mydomain.com"
set use_from = "yes"
set envelope_from ="yes"
set smtp_url="smtp://me@mydomain.com@mail.mydomain.com:587/"
mailboxes imap://mail.mydomain.com:993
set folder="imap://mail.mydomain.com/INBOX"  
set imap_user="me@mydomain.com" #your IMAP user name or login
set imap_pass="mypassword" #your IMAP password


# If not set in ~/.bashrc:
set spoolfile = imap://mail.mydomain.com/INBOX
```

Question 1:  I found that I can have my real name show up in the email next to the address by using the set real name command.  However, there seems to be a problem with mutt seeing a last name as an unknown variable.  I have been using an underscore between my first and last names.  Is there a work around or fix for this?

Question 2:  How can I see other mailboxes in the side panel? Now I see a side panel, with mail.myserver,com at the top and nothing underneath.  I can navigate to other mailboxes (IMAP folders, I've always called them) by using the C? command or typing =mailbox name.  My panel, though is empty :-(

I really appreciate the help!!

---

### Post by Sector11 on 2013-02-03
**@ GrouchyGaijin**

I don't see where you set your "realname" in the config file:
```
set realname="Grouchy Gaijin"
```

Found that [here]("http://dev.mutt.org/trac/wiki/MuttFaq/Header")

Sidebar ... patch ... [Oops!]("http://thomer.com/mutt/") and the real [Mutt sidebar]("http://www.lunar-linux.org/mutt-sidebar/").

Hope you get some better help.

---

### Post by GrouchyGaijin on 2013-02-04
This works for anyone using SiteGround as their host:

```
You can use the following settings in your .muttrc file, I can confirm they are working on SiteGround's servers:

set imap_user = 'user@domain.com'
set imap_pass = '<password for user@domain.com>'
set smtp_pass = '<password for user@domain.com>'
set smtp_url = "smtps://user@domain.com@secureXXX.sgcpanel.com:465/"
set from = "user@domain.com"
set realname="My User"
set spoolfile = imaps://secureXXX.sgcpanel.com:993/INBOX
set folder = imaps://secureXXX.sgcpanel.com:993
set record = "imaps://secureXXX.sgcpanel.com/INBOX.Sent"
set postponed = "imaps://secureXXX.sgcpanel.com/INBOX.Drafts"
set header_cache = "~/.mutt/cache/headers"
set message_cachedir = "~/.mutt/cache/bodies"
set certificate_file = ~/.mutt/certificates

All settings are for SSL/TLS connections (IMAPs and SMTPs).

```

---

