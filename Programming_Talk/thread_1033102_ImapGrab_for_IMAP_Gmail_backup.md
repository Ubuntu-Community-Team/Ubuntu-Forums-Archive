---
title: "ImapGrab for IMAP Gmail backup"
date: 2009-01-07
forum: Programming Talk
---

### Post by diafygi on 2009-01-07
Howdy all,

I just wrote my first real python program, and I was wondering if y'all could provide input. I'm not a programmer, but I saw a lack of a good linux-based Gmail backup program, so I wrote this.

IMAP Grab (imapgrab) is a program that allows you to log into an IMAP server and download selected mailboxes (for Gmail they are labels) to .mbox files. You can also list the folders on that server. It is basically a wrapper for getmail (a mail downloading program). When done downloading selected mailboxes, you end up with one .mbox file per mailbox.

The current getmail in Ibex (i.e. 4.7.8 ) has a bug that causes it to lose track of previously downloaded messages, so you need 4.8.2 or higher for ImapGrab to work properly (4.8.4 should be in Jaunty).

Since this is my first program, please let me know if I'm doing something taboo in the programming world. I basically used this program to teach myself python. I want to eventually make a gui to go with this cli.

Usage:
```
# Usage:
#  imapgrab [-ldaSv] [-s] SERVER [-P] PORT [-u] USERNAME [-p] PASSWORD [-m] "BOX1,BOX2,..." [-f] DIRECTORY)
#    Possible arguments:
#    --list, -l        List the mailboxes available for download
#    --download, -d    Download mailboxes to separate mbox files
#    --all, -a         Force download all mail in a mailbox (optional)
#    --ssl, -S         Use SSL connection (optional)
#    --server, -s      IP or domain of server (required)
#    --port, -P        Port of server (optional)
#    --username, -u    Username for account (required)
#    --password, -p    Password for account (required)
#    --mailboxes, -m   Comma separated list of mailboxes to download 
#                       (i.e. "Box1, Box2, Box3")
#                       ("{,}" for non-separating commas)
#                       ("_ALL_" for all mailboxes)
#                       ("_ALL_, -Box1" to except Box1 from _ALL_)
#                       ("_ALL_, -_Gmail_" to except [Gmail]* folders)
#                       (required for -d)
#    --folder, -f      Path to folder
#                       (optional, creates imapgrab folder in current directory as default)
#    --quiet, -q       Don't display any output
#    --verbose, -v     Verbose output
#    --debug           Print debug output
#    --version         Print version
#    --about           Display detailed info
#    --help, -h        Print help with command options
```

Examples:
```
# Examples:
#  1) List available mailboxes
#       imapgrab -l -s imap.example.com -u username -p password
#  2) Download "box1" and "box2" from server imap.example.com (save "box1.mbox" and "box2.mbox")
#       imapgrab -d -s imap.example.com -u username -p password -m "box1, box2"
#  3) Download all mailboxes except "box3"
#       imapgrab -d -s imap.example.com -u username -p password -m "_ALL_, -box3"
#  4) Download all Gmail custom labels and INBOX (none of the [Gmail]* mailboxes)
#       imapgrab -d -S -s imap.gmail.com -u username -p password -m "_ALL_, -_Gmail_"
#  5) Download Gmail label "receipts"
#       imapgrab -d -S -s imap.gmail.com -u username -p password -m "receipts"
```

---

### Post by diafygi on 2009-01-14
UPDATE 2009-01-14: This program now has a [website]("http://daylightpirates.org/index.php/Programs/ImapGrab"), SourceForge.net [project page]("https://sourceforge.net/projects/imapgrab/"), and [mailing list]("http://groups.google.com/group/imapgrab").

---

