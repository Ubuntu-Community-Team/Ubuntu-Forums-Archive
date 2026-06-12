---
title: "getmail stopped downloading emails..."
date: 2013-06-01
forum: New to Ubuntu
---

### Post by Guruprasad on 2013-06-01
I was using getmail for past 2years to download emails from gmail.com using POP3. But now it is not downloaing it.
Recently I changed my internet connection from direct wired to wireless router.

Here is the output 
```
$ sudo -u mail getmail --trace --getmaildir=/media/Disk1/.bhoomijamail/.getmail --rcfile=info@bhoomija.com

parsed options:  dump_config="False",ensure_value="<bound method Values.ensure_value of <Values at 0x2609830: {'trace': True, 'override_delete': None, 'getmaildir': '/media/Disk1/.bhoomijamail/.getmail', 'override_read_all': None, 'override_verbose': None, 'dump_config': False, 'rcfile': ['info@bhoomija.com']}>>",getmaildir="'/media/Disk1/.bhoomijamail/.getmail'",override_delete="None",override_read_all="None",override_verbose="None",rcfile="['info@bhoomija.com']",read_file="<bound method Values.read_file of <Values at 0x2609830: {'trace': True, 'override_delete': None, 'getmaildir': '/media/Disk1/.bhoomijamail/.getmail', 'override_read_all': None, 'override_verbose': None, 'dump_config': False, 'rcfile': ['info@bhoomija.com']}>>",read_module="<bound method Values.read_module of <Values at 0x2609830: {'trace': True, 'override_delete': None, 'getmaildir': '/media/Disk1/.bhoomijamail/.getmail', 'override_read_all': None, 'override_verbose': None, 'dump_config': False, 'rcfile': ['info@bhoomija.com']}>>",trace="True"
processing rcfile /media/Disk1/.bhoomijamail/.getmail/info@bhoomija.com
  looking for option read_all ... 
got "false"
-> False

  looking for option delete ... 
got "false"
-> False

  looking for option delivered_to ... 
got "True"
-> True

  looking for option received ... 
got "True"
-> True

  looking for option message_log_verbose ... 
got "False"
-> False

  looking for option message_log_syslog ... 
got "False"
-> False

  looking for option delete_after ... 
got "0"
-> 0

  looking for option max_message_size ... 
got "0"
-> 0

  looking for option max_messages_per_session ... 
got "0"
-> 0

  looking for option max_bytes_per_session ... 
got "0"
-> 0

  looking for option verbose ... 
got "1"
-> 1

  looking for option message_log ... 
got "None"
-> None

  getting retriever
    type="SimplePOP3SSLRetriever"
    parameter username="info@bhoomija.com"
    parameter password=*
    parameter port="995"
    parameter server="pop.gmail.com"
    instantiating retriever SimplePOP3SSLRetriever with args configparser="<ConfigParser.RawConfigParser instance at 0x2609c68>",getmaildir="/media/Disk1/.bhoomijamail/.getmail",password=*,port="995",server="pop.gmail.com",username="info@bhoomija.com"
__init__() [baseclasses.py:249] trace
__init__() [baseclasses.py:261] setting username to "info@bhoomija.com" (<type 'str'>)
__init__() [baseclasses.py:261] setting getmaildir to "/media/Disk1/.bhoomijamail/.getmail" (<type 'str'>)
__init__() [baseclasses.py:261] setting server to "pop.gmail.com" (<type 'str'>)
__init__() [baseclasses.py:258] setting password to * (<type 'str'>)
__init__() [baseclasses.py:261] setting port to "995" (<type 'str'>)
__init__() [baseclasses.py:261] setting configparser to "<ConfigParser.RawConfigParser instance at 0x2609c68>" (<type 'instance'>)
checkconf() [baseclasses.py:267] trace
checkconf() [baseclasses.py:272] checking configparser
checkconf() [baseclasses.py:272] checking getmaildir
checkconf() [baseclasses.py:272] checking timeout
checkconf() [baseclasses.py:272] checking server
checkconf() [baseclasses.py:272] checking port
converting port (995) to type <type 'int'>
checkconf() [baseclasses.py:272] checking username
checkconf() [baseclasses.py:272] checking password
checkconf() [baseclasses.py:272] checking use_apop
checkconf() [baseclasses.py:272] checking delete_dup_msgids
checkconf() [baseclasses.py:272] checking keyfile
checkconf() [baseclasses.py:272] checking certfile
checkconf() [baseclasses.py:281] done
__init__() [_retrieverbases.py:459] trace
__str__() [retrievers.py:107] trace
    checking retriever configuration for SimplePOP3SSLRetriever:info@bhoomija.com@pop.gmail.com:995
checkconf() [baseclasses.py:267] trace
  getting destination
    type="Maildir"
    parameter path="/media/Disk1/.bhoomijamail/info@bhoomija.com/Maildir/"
    instantiating destination Maildir with args configparser="<ConfigParser.RawConfigParser instance at 0x2609c68>",path="/media/Disk1/.bhoomijamail/info@bhoomija.com/Maildir/"
__init__() [baseclasses.py:249] trace
__init__() [baseclasses.py:261] setting path to "/media/Disk1/.bhoomijamail/info@bhoomija.com/Maildir/" (<type 'str'>)
__init__() [baseclasses.py:261] setting configparser to "<ConfigParser.RawConfigParser instance at 0x2609c68>" (<type 'instance'>)
checkconf() [baseclasses.py:267] trace
checkconf() [baseclasses.py:272] checking configparser
checkconf() [baseclasses.py:272] checking path
checkconf() [baseclasses.py:272] checking user
checkconf() [baseclasses.py:272] checking filemode
checkconf() [baseclasses.py:281] done
initialize() [destinations.py:115] trace
__init__() [destinations.py:83] done
  getting filters
getmail version 4.17.0
Copyright (C) 1998-2009 Charles Cazabon.  Licensed under the GNU GPL version 2.
__str__() [retrievers.py:107] trace
SimplePOP3SSLRetriever:info@bhoomija.com@pop.gmail.com:995:
__str__() [retrievers.py:107] trace
initialize() [_retrieverbases.py:550] trace
initialize() [_retrieverbases.py:404] trace
checkconf() [baseclasses.py:267] trace
_read_oldmailfile() [_retrieverbases.py:350] trace
__str__() [retrievers.py:107] trace
read 0 uids for SimplePOP3SSLRetriever:info@bhoomija.com@pop.gmail.com:995
_connect() [_retrieverbases.py:113] trace
_connect() [_retrieverbases.py:134] establishing POP3 SSL connection to pop.gmail.com:995
_connect() [_retrieverbases.py:149] POP3 connection <poplib.POP3_SSL instance at 0x2684098> established
_getmsglist() [_retrieverbases.py:471] trace
UIDL response "+OK", 383 octets
Message IDs: ['GmailId13ec17afeadfd1c7', 'GmailId13ec17f399d63003', 'GmailId13ec6fb5f814ca61', 'GmailId13ed1379bad8b685', 'GmailId13ed65e4be9643ad', 'GmailId13ed66416ab9ff4d', 'GmailId13ed67e20b839617', 'GmailId13ee5df4b1be5af8', 'GmailId13eedc08d93d8546', 'GmailId13efa6b7c5763bd3', 'GmailId13efa6b7cc46c1a4', 'GmailId13efa718d54d9ac2', 'GmailId13efa8b1c085981f', 'GmailId13efb9e93433eb85']
msgids: ['GmailId13ec17afeadfd1c7', 'GmailId13ec17f399d63003', 'GmailId13ec6fb5f814ca61', 'GmailId13ed1379bad8b685', 'GmailId13ed65e4be9643ad', 'GmailId13ed66416ab9ff4d', 'GmailId13ed67e20b839617', 'GmailId13ee5df4b1be5af8', 'GmailId13eedc08d93d8546', 'GmailId13efa6b7c5763bd3', 'GmailId13efa6b7cc46c1a4', 'GmailId13efa718d54d9ac2', 'GmailId13efa8b1c085981f', 'GmailId13efb9e93433eb85']
msgsizes: {'GmailId13eedc08d93d8546': 6268, 'GmailId13ed1379bad8b685': 665644, 'GmailId13efa8b1c085981f': 22966, 'GmailId13efa6b7cc46c1a4': 9587, 'GmailId13ee5df4b1be5af8': 3568900, 'GmailId13ec17afeadfd1c7': 5309109, 'GmailId13efa718d54d9ac2': 10670, 'GmailId13ec6fb5f814ca61': 3568900, 'GmailId13ed65e4be9643ad': 10665, 'GmailId13efa6b7c5763bd3': 9552, 'GmailId13ed67e20b839617': 11615, 'GmailId13ed66416ab9ff4d': 9531, 'GmailId13ec17f399d63003': 2460501, 'GmailId13efb9e93433eb85': 17902}
retriever_info() [destinations.py:86] trace
__len__() [_retrieverbases.py:339] trace
__getitem__() [_retrieverbases.py:343] i == 0
  message GmailId13ec17afeadfd1c7 ...
msgid GmailId13ec17afeadfd1c7
_getmsgnumbyid() [_retrieverbases.py:465] trace
msgnum 1
```

---

### Post by Guruprasad on 2013-06-01
By mistake I selected solved... I dont know how to make it unsolved...

The post is not solved...

---

### Post by wildmanne39 on 2013-06-01
Thread closed. Please do not post duplicates, it dilutes community effort.

---

