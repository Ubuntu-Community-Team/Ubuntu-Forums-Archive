---
title: "Python script question"
date: 2014-12-10
forum: Programming Talk
---

### Post by CantankRus on 2014-12-10
I have a perl script to check my email....
```
#!/usr/bin/perl

## Origin of script## http://ubuntuforums.org/showthread.php?t=680265

#########################################################
##### WARNING: Change name and password if posting!! ####
#########################################################

use Switch;
use Text::Wrap;

my $what=$ARGV[0];

$user="[COLOR="#808080"]XXXXX[/COLOR]"; #username for gmail account
[COLOR="#FF0000"]$pass[/COLOR]=`/home/glen/scripts/gkeyring.py --id 3 -1`; #password for gmail account
$file="/tmp/gmail2.html"; #temporary file to store gmail
```
For the variable [COLOR="#FF0000"]$pass[/COLOR] it uses gkeyring.py to retrieve my password from gnome-keyring
so as not to have my password in a plain text file.

How can I do the same in the **gmail-count.py** python script below.
```
#!/usr/bin/env python
# -*- coding: UTF-8 -*-

import sys, imaplib

port = 993
server = 'imap.gmail.com'

username = '[COLOR="#808080"]XXXXX[/COLOR]'
passwd = '*******'
```
I have the gkeyring.py in my ~/scripts folder but I also installed using **sudo easy_install -U gkeyring**
so I can run with just...
```
gkeyring --id 3 -1
```

---

### Post by schragge on 2014-12-11
Obviously, you can do
```

from subprocess import check_output
passwd = check_output(['gkeyring', '--id', '3', '-1'])

```
But gkeyring is a python script using python-gnomekeyring. I guess you can directly incorporate its functionality into your script. Probably, something like
```

import sys, gnomekeyring as gk

if not gk.is_available():
    print >>sys.stderr, 'GNOME keyring is not available'
else:
    keyring = gk.get_default_keyring_sync()
    passwd = gk.item_get_info_sync(keyring, 3).get_secret()

```

---

### Post by CantankRus on 2014-12-11
Ok thanks.
I don't know any code.
This is the script I picked up to use with conky.
Can you incorporate it into the script?
_gmail-count.py_
```
#!/usr/bin/env python
# -*- coding: UTF-8 -*-

import sys, imaplib

port = 993
server = 'imap.gmail.com'

username = 'XXXXX'
passwd = 'xxxxx'

imap_server = imaplib.IMAP4_SSL(server, port)
try:
    imap_server.login(username, passwd)
except:
    print('??')
    sys.exit( 1 )

typ, data = imap_server.select ('Inbox', True)
if typ == 'OK':
    total = int(data[0])
    typ, data = imap_server.search (None, 'SEEN')
    if typ == 'OK':
        seen = len(data[0].split())
        print('{}'.format(total - seen))

if typ != 'OK':
    print('??')

imap_server.logout()

# from [http://dontsurfinthenude.blogspot.dk/2013/02/check-gmail-script-for-conky-on.html](http://dontsurfinthenude.blogspot.dk/2013/02/check-gmail-script-for-conky-on.html)
```

---

### Post by schragge on 2014-12-11
Ok, try this
```

#!/usr/bin/env python
# -*- coding: UTF-8 -*-

import sys, imaplib, gnomekeyring as gk

port = 993
server = 'imap.gmail.com'

username = 'XXXXX'
id = 3

if not gk.is_available():
    print('GNOME keyring is not available')
    sys.exit(1)

keyring = gk.get_default_keyring_sync()
passwd = gk.item_get_info_sync(keyring, id).get_secret()

imap_server = imaplib.IMAP4_SSL(server, port)
try:
    imap_server.login(username, passwd)
except:
    print('??')
    sys.exit( 1 )

typ, data = imap_server.select ('Inbox', True)
if typ == 'OK':
    total = int(data[0])
    typ, data = imap_server.search (None, 'SEEN')
    if typ == 'OK':
        seen = len(data[0].split())
        print('{}'.format(total - seen))

if typ != 'OK':
    print('??')

imap_server.logout()

# from [http://dontsurfinthenude.blogspot.dk/2013/02/check-gmail-script-for-conky-on.html](http://dontsurfinthenude.blogspot.dk/2013/02/check-gmail-script-for-conky-on.html)

```

---

### Post by CantankRus on 2014-12-11
Yep that works.
I originally was using gkeyring in a bash script for a keyboard shortcut to autotype
my password when admin privileges were needed because I can fudge a bit of bash.
eg
```
xdotool key --delay 50 $(gkeyring --id 1 -1 | sed 's/./& /g') Return
```

So when using python, you don't need gkeyring and just access using python-gnomekeyring???

---

### Post by schragge on 2014-12-11
Yep.

---

### Post by ofnuts on 2014-12-11
> **CantankRus said:**
> 
So when using python, you don't need gkeyring and just access using python-gnomekeyring???

Actually gkeyring is mostly meant for bash scripts. There are bindings for other languages, including Perl: [https://bitbucket.org/Mekk/perl-keyring-gnome](https://bitbucket.org/Mekk/perl-keyring-gnome)

---

### Post by CantankRus on 2014-12-11
Ok, thanks for the help.

---

