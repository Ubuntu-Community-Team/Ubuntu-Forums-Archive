---
title: "how to make other folders on a mailserver"
date: 2014-06-19
forum: New to Ubuntu
---

### Post by shad2 on 2014-06-19
[h=2]i have this setting in my dovecot.conf file;[/h][INDENT] namespace private {
    separator = .
    prefix = INBOX.
    inbox = yes
  mailbox Trash {
    auto = create #no
    special_use = \Trash
  }
  mailbox Drafts {
    auto = create #no
    special_use = \Drafts
  }
  mailbox Sent {
    auto = create #subscribe # autocreate and autosubscribe the Sent mailbox
    special_use = \Sent
  }
  mailbox Spam {
   auto = create #subscribe
   special_use = \Spam
  }
}
i get this error,
 * Restarting IMAP/POP3 mail server dovecot                                      Error: Error in configuration file /etc/dovecot/dovecot.conf  line 12: Unknown section type (section changed in  /etc/dovecot/dovecot.conf at line 8)
Fatal: Invalid configuration in /etc/dovecot/dovecot.conf
                                                                         [fail] 				

how can i clear this problem??
[/INDENT]

---

