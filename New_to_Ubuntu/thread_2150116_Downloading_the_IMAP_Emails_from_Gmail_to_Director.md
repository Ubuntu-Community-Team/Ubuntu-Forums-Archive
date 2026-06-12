---
title: "Downloading the IMAP Emails from Gmail to Directory?"
date: 2013-05-31
forum: New to Ubuntu
---

### Post by honeybear on 2013-05-31
Hi,

It is maybe possible to use fetchmail, but I would like sthg 
easy, universal, that is capable to retrieve all directories
of the gmail (inbox, sent, ...)
onto the local harddisk somewhere. 

Which program (light-weight) would you recommend?

kind regards




----
Stop the fetchmail service
To stop fetchmail while configuring it, run

/etc/init.d/fetchmail stop
/etc/fetchmail.rc
The file /etc/fetchmailrc should look as follows:

set syslog

set daemon 240

poll pop.gmail.com
  with nodns,
  with protocol POP3
  user "jane.doe@gmail.com" there is jane here,
  with password doeadeer,
  with ssl, sslcertck;
A detailed explanation is given in the appendix, though fetchmail's configuration language hopefully makes it clear.

Since this file contains your Gmail password, you may wish to give it restrictive read permission:

chmod 600 /etc/fetchmailrc
Testing
To test your configuration, run fetchmail as below; this should be run as root, since it reads /etc/fetchmailrc.

fetchmail -v -d0 -f /etc/fetchmailrc
Take a look at /var/log/mail.log (e.g., using less /var/log/mail.log) to see that the connection was successful.

Restart fetchmail
Once your configuration is working, you can restart fetchmail with

/etc/init.d/fetchmail start

---

### Post by mennopieters on 2013-05-31
ImapSync: [http://imapsync.lamiral.info/](http://imapsync.lamiral.info/)
Or offlineimap or mbsync referred on that page.

-Menno

---

### Post by honeybear on 2013-05-31
thanks a lot

offlineimap sounds nice, but I dont like it that much.


Would you maybe know sthg very very light-weight? 


what is the lightest way?

Cannot it be done with curl or wget directly and simply?



$ apt-cache search imap sync
evolution - groupware suite with mail client and organizer
imapcopy - IMAP backup, copy and migration tool
isync - Synchronize a local maildir with a remote IMAP4 mailbox
libmail-imaptalk-perl - IMAP client interface with lots of features
mailsync - Synchronize IMAP mailboxes
mswatch - watch mailstores for changes and initiate mailbox syncs - client tools
watch-maildirs - watch mailstores for changes and initiate mailbox syncs - server tools
offlineimap - IMAP/Maildir synchronization and reader support
syncmaildir - Sync Mail Dir is a set of tools to synchronize Maildirs
texlive-latex-extra - TeX Live: LaTeX supplementary packages


Similar softwares

imap_tools: [http://www.athensfbc.com/imap_tools](http://www.athensfbc.com/imap_tools)
offlineimap: [https://github.com/nicolas33/offlineimap](https://github.com/nicolas33/offlineimap)
mbsync: [http://isync.sourceforge.net/](http://isync.sourceforge.net/)
mailsync: [http://mailsync.sourceforge.net/](http://mailsync.sourceforge.net/)
mailutil: [http://www.washington.edu/imap/](http://www.washington.edu/imap/) part of the UW IMAP tookit.
imaprepl: [http://www.bl0rg.net/software/](http://www.bl0rg.net/software/) [http://freecode.com/projects/imap-repl/](http://freecode.com/projects/imap-repl/)
imapcopy: [http://home.arcor.de/armin.diehl/imapcopy/imapcopy.html](http://home.arcor.de/armin.diehl/imapcopy/imapcopy.html)
migrationtool: [http://sourceforge.net/projects/migrationtool/](http://sourceforge.net/projects/migrationtool/)
imapmigrate: [http://sourceforge.net/projects/cyrus-utils/](http://sourceforge.net/projects/cyrus-utils/)
larch: [https://github.com/rgrove/larch](https://github.com/rgrove/larch) (derived from wonko_imapsync)
wonko_imapsync: [http://wonko.com/article/554](http://wonko.com/article/554)
pop2imap: [http://www.linux-france.org/prj/pop2imap/](http://www.linux-france.org/prj/pop2imap/)
exchange-away: [http://exchange-away.sourceforge.net/](http://exchange-away.sourceforge.net/)

---

