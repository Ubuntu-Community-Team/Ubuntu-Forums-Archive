---
title: "[Python] Building a proxy"
date: 2011-06-01
forum: Programming Talk
---

### Post by ki4jgt on 2011-06-01
How do I build a local proxy with Python?
Situation:
I want to run the browser through the proxy at 127.0.0.1:XXXX and when the browser asks for a file protocol XXX:// I want the proxy to download the file from a certain website/predefined location and feed it to the browser. How would I get the proxy to interact with the browser? (Basically how are the protocols setup) How would I configure a start page to adjust settings when the user went to [http://127.0.0.1:XXXX](http://127.0.0.1:XXXX)
All help appreciated.

---

### Post by Petrolea on 2011-06-01
You want to make a proxy with Python? I mean, code it yourself? Or are you just looking for a script that would set this up for you?

---

### Post by ki4jgt on 2011-06-02
I want to code it myself, I have a script I just wrote, but need to find out how to read only one line of the rec data (A multilined string) so I can seperate the GET url from the rest of the data. BTW: If anyone has any suggestions to this script, please let me know.

```

#!/usr/bin/env python

def rl(str):
    list = []
    while str <> "":
        end = str.find(chr(13))
        if end == -1:
            end = str.find(chr(10))
            if end == -1:
                end = str.find("\n")
        phrase = str[:end]
        str.replace(phrase, "", 1)
        list.append(phrase)
        return list

import socket
import urllib2
import readline

getend = 1
backlog = 5
s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
s.bind(("",7890))
s.listen(backlog)
while 1:
    client, address = s.accept()
    data = client.recv(500000)
    print data
    url = rl(data)
    urls = url[0]
    if urls.find(" ") == 0:
        getend = urls.find(" ")
    if getend <> 0:
        urls = urls[4:getend]
    if getend == 0:
        urls = urls[4:]
    rechtml = urllib2.urlopen(urls)
    html = rechtml.read()
    if data:
        client.send(html)
    client.close()

```

---

### Post by Petrolea on 2011-06-02
> **ki4jgt said:**
> I want to code it myself, I have a script I just wrote, but need to find out how to read only one line of the rec data (A multilined string) so I can seperate the GET url from the rest of the data. BTW: If anyone has any suggestions to this script, please let me know.

```

#!/usr/bin/env python

def rl(str):
    list = []
    while str <> "":
        end = str.find(chr(13))
        if end == -1:
            end = str.find(chr(10))
            if end == -1:
                end = str.find("\n")
        phrase = str[:end]
        str.replace(phrase, "", 1)
        list.append(phrase)
        return list

import socket
import urllib2
import readline

getend = 1
backlog = 5
s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
s.bind(("",7890))
s.listen(backlog)
while 1:
    client, address = s.accept()
    data = client.recv(500000)
    print data
    url = rl(data)
    urls = url[0]
    if urls.find(" ") == 0:
        getend = urls.find(" ")
    if getend <> 0:
        urls = urls[4:getend]
    if getend == 0:
        urls = urls[4:]
    rechtml = urllib2.urlopen(urls)
    html = rechtml.read()
    if data:
        client.send(html)
    client.close()

```

Read the string till you encounter a new line.

---

### Post by ki4jgt on 2011-06-03
```

#!/usr/bin/env python

import socket
import urllib2

backlog = 5
s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
s.bind(("",7890))
s.listen(backlog)
while 1:
    client, address = s.accept()
    data = client.recv(500000)
    print data
    datas = data.split()
    print datas
    if datas[0] == "GET":
        page = urllib2.urlopen(datas[1])
        data = page.read()
    if data:
        client.send(data)
    client.close()

```

New code. Shorter and simpler ;-)

---

