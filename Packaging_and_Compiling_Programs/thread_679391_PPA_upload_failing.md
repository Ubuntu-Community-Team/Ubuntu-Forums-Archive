---
title: "PPA upload failing"
date: 2008-01-26
forum: Packaging and Compiling Programs
---

### Post by Shapierian on 2008-01-26
I'm having trouble uploading to my ppa. dput always seems to choke on my .orig.tar.gz

```
alex@lombax:/usr/src/ubuntu/pidgin$ dput ppa pidgin_2.3.1-2~bpo40+1~ajc2_source.changes 
Checking Signature on .changes
gpg: Signature made Sat 26 Jan 2008 08:23:30 PM EST using DSA key ID 88CB2069
gpg: Good signature from "Alex Converse <REDACTED>"
Good signature on /usr/src/ubuntu/pidgin/pidgin_2.3.1-2~bpo40+1~ajc2_source.changes.
Checking Signature on .dsc
gpg: Signature made Sat 26 Jan 2008 08:23:24 PM EST using DSA key ID 88CB2069
gpg: Good signature from "Alex Converse <REDACTED>"
Good signature on /usr/src/ubuntu/pidgin/pidgin_2.3.1-2~bpo40+1~ajc2.dsc.
Package includes an .orig.tar.gz file although the debian revision suggests
that it might not be required. Multiple uploads of the .orig.tar.gz may be
rejected by the upload queue management software.
Uploading to ppa (via ftp to ppa.launchpad.net):
  pidgin_2.3.1-2~bpo40+1~ajc2.dsc: done.
  pidgin_2.3.1.orig.tar.gz: 
```
Sits here forever. I have a fast connection and this sits here for hours.

```
alex@lombax:~$ cat .dput.cf
[ppa]
fqdn = ppa.launchpad.net
method = ftp
incoming = ~ajc30/ubuntu/
login = anonymous
progress-indicator = 2
allow_unsigned_uploads = 0

```

I am a ubuntero and have activated my PPA.

Any idea what I'm doing wrong?

---

### Post by dholbach on 2008-01-29
Where is the rejection message? From the log I don't see a reason why it should have failed. What does the email from LP say?

---

### Post by Shapierian on 2008-02-05
Sorry about the delay getting back to you. It doesn't actually fail, it just sits there forever, never completing. If I look at it with wireshark the FTP traffic to ppa.launchpad.net (91.189.90.217) just completely stops.

EDIT: Also I'm seeing no progress indicator and according to man dput.cf I should be seeing a KB counter as "progress-indicator = 2" and "method = ftp".

---

### Post by dholbach on 2008-02-06
Try asking on [email]launchpad-users@lists.canonical.com[/email] or in #launchpad on irc.freenode.net

---

