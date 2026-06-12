---
title: "Please explain this Python script"
date: 2014-07-28
forum: Programming Talk
---

### Post by vasa1 on 2014-07-28
I found the following script in a [blog post]("http://dontsurfinthenude.blogspot.dk/2013/02/check-gmail-script-for-conky-on.html") in turn attributed to [an Arch Linux forum post]("https://bbs.archlinux.org/viewtopic.php?pid=1019254#p1019254"):```
#!/usr/bin/env python
# -*- coding: UTF-8 -*-

import sys, imaplib

port = 993
server = 'imap.gmail.com'

username = 'name@gmail.com'
passwd = 'password'

imap_server = imaplib.IMAP4_SSL(server, port)
try:
    imap_server.login(username, passwd)
except:
    print('?? new')
    sys.exit( 1 )

typ, data = imap_server.select ('Inbox', True)
if typ == 'OK':
    total = int(data[0])
    typ, data = imap_server.search (None, 'SEEN')
    if typ == 'OK':
        seen = len(data[0].split())
        print('{} new'.format(total - seen))

if typ != 'OK':
    print('?? new')

imap_server.logout()

```
It works for me but I don't understand why there are three "*print*" lines. Could someone please explain what each print line does?

---

### Post by ian-weisser on 2014-07-28
> **vasa1 said:**
> ```
try:
    imap_server.login(username, passwd)
except:
    print('?? new')
    sys.exit( 1 )
```

If the login fails, print "?? new" and exit instead of throwing an error.


> **vasa1 said:**
> ```
typ, data = imap_server.select ('Inbox', True)
if typ == 'OK':
    total = int(data[0])
        typ, data = imap_server.search (None, 'SEEN')
    if typ == 'OK':
        seen = len(data[0].split())
        print('{} new'.format(total - seen))
```

total is an int, the first entry in 'data', which is the response to  imap_server.select('Inbox', True).
seen is an int, the first entry in a different 'data', which is the first response to imap_server.search(None, 'SEEN')
(total - seen) will be another int. It's not named, but let's call it 'unseen'. Yeah, you can do math in a print line.

The print line prints "$UNSEEN new"
The {} if a print formatter. It refers to the .format suffix on the same line, and whatever is in that suffix gets inserted within the brackets.
You can do the same thing by saying **print( str(total - seen) + ' new')**... but learning to use print statements properly (which this script does) is important.

> **vasa1 said:**
> ```
if typ != 'OK':
    print('?? new')
```

Print another '?? new' line. From the location in the script, this seems intended to indicate unsuccesful completion.

---

### Post by vasa1 on 2014-07-28
Thank you for the detailed explanation!

So it seems the second print line that is the one involved if all goes well.

I think the third print```
if typ != 'OK':
    print('?? new')
``` won't be involved because of "**!=**"; is that correct?

My reason for asking is that I want to have something compact so that checking three gmail accounts won't take up much horizontal space.

My conky script looks like this:```
${time %a, %d %b} ${color B3492B}${time %H:%M}$color ${utime (%H:%M)} ${acpitemp}${iconv_start UTF-8 ISO_8859-1}°${iconv_stop}C RAM: $memperc% ${execpi 300 python ~/bin/gmail1.py}/${execpi 3600 python ~/bin/gmail2.py}/${execpi 240 python ~/bin/gmail3.py}

```

And I modified the gmail.py scripts to remove each occurrence of the word "new" and the preceding space because I didn't know the significance of each print line.

Here's what my Conky looks like with 1 new email in the third gmail account.

---

### Post by ian-weisser on 2014-07-28
> **vasa1 said:**
> I think the third print```
if typ != 'OK':
    print('?? new')
``` won't be involved because of "**!=**"; is that correct?

Oops; you're right. Edited my answer above.

---

