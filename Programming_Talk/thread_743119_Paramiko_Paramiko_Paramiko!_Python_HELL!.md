---
title: "Paramiko Paramiko Paramiko! Python HELL!"
date: 2008-04-02
forum: Programming Talk
---

### Post by Mickeysofine1972 on 2008-04-02
Hey guys

I'm trying to incorporate a sftp connection feature to a python program i wrote and was wondering is anyone has or knows a basic tutorial on how to connect to a sftp server using paramiko?

All i need is a basic idea of what has to be done to setup for password authentication and then opening the connection

Thanks In advance!

Mike

---

### Post by Martin Witte on 2008-04-02
Did you already study the demos? If you downloaded the package from the repositories the examples are in /usr/share/doc/python-paramiko/examples.

---

### Post by pmasiar on 2008-04-02
Are you always this easily excited?

I opened the post intrigued what Python problems you have (and maybe I can help to solve), but it seems more like a case of google-fu deficiency, unrelated to Python at all.

Consider reading "how to ask questions" in sticky FAQ, you may get better response next time.

---

### Post by Mickeysofine1972 on 2008-04-03
> **pmasiar said:**
> Are you always this easily excited?

I opened the post intrigued what Python problems you have (and maybe I can help to solve), but it seems more like a case of google-fu deficiency, unrelated to Python at all.

Consider reading "how to ask questions" in sticky FAQ, you may get better response next time.

---- RANT STARTED ------

Are always such a wet blanket? Honestly, I ask for help and get you with you usual sarcasm and lack of actual answers to genuine questions. This is not the first time you have come in guns blazing and its not the first time you have violated the spirit of this forum, Inkeeping with the unix development way for things "If a program has nothing interesting to say, it should say nothing", please be a good program and shut up.

--- RANT OVER ------

In response to the post before that, yes I have looked at the demos and even they generate a 'SSHException: Channel closed.' which seems to to imply that I have to keep the connection open somehow.

Any Idea, (and genuine help), would be a great help and inline with the idea of 'Ubuntu'

Mike

---

### Post by ghostdog74 on 2008-04-03
which demo example are you using? you might also want to ask paramiko creator himself, using Paramiko mailing list.

---

### Post by Mickeysofine1972 on 2008-04-03
> **ghostdog74 said:**
> which demo example are you using? you might also want to ask paramiko creator himself, using Paramiko mailing list.

its the demo_sftp.py from the latest 1.7.2 release of the paramiko website, but I also tried the ubuntu version out of the repos too.

I'm sure that its not the server I'm connecting to as well, becuase I can connect to it with FileZilla out of the repos.

The whole point really is that i want to connect using the program I wrote in python so that I can get it to carry out some admin functions for me you see, so using filezilla is fine but I want to automate a few jobs all at the same time.

And thank for you help so far BTW, Its good to see there are others who arent looking to massage thier egos, but are looking to help others to use a truly great OS like Ubuntu

Mike

---

### Post by ghostdog74 on 2008-04-03
show your modified demo_sftp.py then. also, error messages , other information to help troubleshooting if any.

---

### Post by Mickeysofine1972 on 2008-04-03
ok here goes:


the outout :
```

Using host key of type ssh-rsa
*** Caught exception: <class 'paramiko.SSHException'>: Channel closed.
Traceback (most recent call last):
  File "./demo_sftp.py", line 84, in <module>
    sftp = paramiko.SFTPClient.from_transport(t)
  File "/home/mike/kd site deployer/paramiko/sftp_client.py", line 105, in from_transport
    chan.invoke_subsystem('sftp')
  File "/home/mike/kd site deployer/paramiko/channel.py", line 238, in invoke_subsystem
    self._wait_for_event()
  File "/home/mike/kd site deployer/paramiko/channel.py", line 1062, in _wait_for_event
    raise e
SSHException: Channel closed.

```

and my copy of the demo:
```

#!/usr/bin/env python

# Copyright (C) 2003-2007  Robey Pointer <robey@lag.net>
#
# This file is part of paramiko.
#
# Paramiko is free software; you can redistribute it and/or modify it under the
# terms of the GNU Lesser General Public License as published by the Free
# Software Foundation; either version 2.1 of the License, or (at your option)
# any later version.
#
# Paramiko is distrubuted in the hope that it will be useful, but WITHOUT ANY
# WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS FOR
# A PARTICULAR PURPOSE.  See the GNU Lesser General Public License for more
# details.
#
# You should have received a copy of the GNU Lesser General Public License
# along with Paramiko; if not, write to the Free Software Foundation, Inc.,
# 59 Temple Place, Suite 330, Boston, MA  02111-1307  USA.

# based on code provided by raymond mosteller (thanks!)

import base64
import getpass
import os
import socket
import sys
import traceback

import paramiko


# setup logging
paramiko.util.log_to_file('demo_sftp.log')

# get hostname
username = ''
if len(sys.argv) > 1:
    hostname = sys.argv[1]
    if hostname.find('@') >= 0:
        username, hostname = hostname.split('@')
else:
    hostname = raw_input('Hostname: ')
if len(hostname) == 0:
    print '*** Hostname required.'
    sys.exit(1)
port = 22
if hostname.find(':') >= 0:
    hostname, portstr = hostname.split(':')
    port = int(portstr)


# get username
if username == '':
    default_username = getpass.getuser()
    username = raw_input('Username [%s]: ' % default_username)
    if len(username) == 0:
        username = default_username
password = getpass.getpass('Password for %s@%s: ' % (username, hostname))


# get host key, if we know one
hostkeytype = None
hostkey = None
try:
    host_keys = paramiko.util.load_host_keys(os.path.expanduser('~/.ssh/known_hosts'))
except IOError:
    try:
        host_keys = paramiko.util.load_host_keys(os.path.expanduser('~/ssh/known_hosts'))
    except IOError:
        print '*** Unable to open host keys file'
        host_keys = {}

if host_keys.has_key(hostname):
    hostkeytype = host_keys[hostname].keys()[0]
    hostkey = host_keys[hostname][hostkeytype]
    print 'Using host key of type %s' % hostkeytype


# now, connect and use paramiko Transport to negotiate SSH2 across the connection
try:
    t = paramiko.Transport((hostname, port))
    t.connect(username=username, password=password, hostkey=hostkey)
    sftp = paramiko.SFTPClient.from_transport(t)

    # dirlist on remote host
    dirlist = sftp.listdir('.')
    print "Dirlist:", dirlist

    # copy this demo onto the server
    try:
        sftp.mkdir("demo_sftp_folder")
    except IOError:
        print '(assuming demo_sftp_folder/ already exists)'
    sftp.open('demo_sftp_folder/README', 'w').write('This was created by demo_sftp.py.\n')
    data = open('demo_sftp.py', 'r').read()
    sftp.open('demo_sftp_folder/demo_sftp.py', 'w').write(data)
    print 'created demo_sftp_folder/ on the server'
    
    # copy the README back here
    data = sftp.open('demo_sftp_folder/README', 'r').read()
    open('README_demo_sftp', 'w').write(data)
    print 'copied README back here'
    
    # BETTER: use the get() and put() methods
    sftp.put('demo_sftp.py', 'demo_sftp_folder/demo_sftp.py')
    sftp.get('demo_sftp_folder/README', 'README_demo_sftp')

    t.close()

except Exception, e:
    print '*** Caught exception: %s: %s' % (e.__class__, e)
    traceback.print_exc()
    try:
        t.close()
    except:
        pass
    sys.exit(1)

```

and finally the log file it makes:
```

DEB [20080403-09:09:12.304] thr=1   paramiko.transport: starting thread (client mode): 0xb7d718acL
INF [20080403-09:09:12.333] thr=1   paramiko.transport: Connected (version 2.0, client OpenSSH_4.2-chrootssh)
DEB [20080403-09:09:12.358] thr=1   paramiko.transport: kex algos:['diffie-hellman-group-exchange-sha1', 'diffie-hellman-group14-sha1', 'diffie-hellman-group1-sha1'] server key:['ssh-rsa', 'ssh-dss'] client encrypt:['aes128-cbc', '3des-cbc', 'blowfish-cbc', 'cast128-cbc', 'arcfour128', 'arcfour256', 'arcfour', 'aes192-cbc', 'aes256-cbc', 'rijndael-cbc@lysator.liu.se', 'aes128-ctr', 'aes192-ctr', 'aes256-ctr'] server encrypt:['aes128-cbc', '3des-cbc', 'blowfish-cbc', 'cast128-cbc', 'arcfour128', 'arcfour256', 'arcfour', 'aes192-cbc', 'aes256-cbc', 'rijndael-cbc@lysator.liu.se', 'aes128-ctr', 'aes192-ctr', 'aes256-ctr'] client mac:['hmac-md5', 'hmac-sha1', 'hmac-ripemd160', 'hmac-ripemd160@openssh.com', 'hmac-sha1-96', 'hmac-md5-96'] server mac:['hmac-md5', 'hmac-sha1', 'hmac-ripemd160', 'hmac-ripemd160@openssh.com', 'hmac-sha1-96', 'hmac-md5-96'] client compress:['none', 'zlib@openssh.com'] server compress:['none', 'zlib@openssh.com'] client lang:[''] server lang:[''] kex follows?False
DEB [20080403-09:09:12.358] thr=1   paramiko.transport: Ciphers agreed: local=aes128-cbc, remote=aes128-cbc
DEB [20080403-09:09:12.359] thr=1   paramiko.transport: using kex diffie-hellman-group1-sha1; server key type ssh-rsa; cipher: local aes128-cbc, remote aes128-cbc; mac: local hmac-sha1, remote hmac-sha1; compression: local none, remote none
DEB [20080403-09:09:12.571] thr=1   paramiko.transport: Switch to new keys ...
DEB [20080403-09:09:12.577] thr=2   paramiko.transport: Host key verified (ssh-rsa)
DEB [20080403-09:09:12.577] thr=2   paramiko.transport: Attempting password auth...
DEB [20080403-09:09:12.659] thr=1   paramiko.transport: userauth is OK
INF [20080403-09:09:12.708] thr=1   paramiko.transport: Authentication (password) successful!
DEB [20080403-09:09:12.717] thr=2   paramiko.transport.1: Max packet in: 34816 bytes
DEB [20080403-09:09:12.742] thr=1   paramiko.transport.1: Max packet out: 32768 bytes
INF [20080403-09:09:12.743] thr=1   paramiko.transport: Secsh channel 1 opened.
DEB [20080403-09:09:12.787] thr=1   paramiko.transport.1: EOF sent (1)
DEB [20080403-09:09:12.980] thr=1   paramiko.transport: EOF in transport thread

```

Mike

---

### Post by ghostdog74 on 2008-04-03
it works fine for me on Paramiko 1.6. You can try ver 1.6, if it still does not work, something is wrong with your ssh setup.

remove all the unecessary code for troubleshooting.
```

#!/usr/bin/env python
import base64
import getpass
import os
import socket
import sys
import traceback

import paramiko


# setup logging
paramiko.util.log_to_file('demo_sftp.log')

# get hostname
username = ''
if len(sys.argv) > 1:
    hostname = sys.argv[1]
    if hostname.find('@') >= 0:
        username, hostname = hostname.split('@')
else:
    hostname = raw_input('Hostname: ')
if len(hostname) == 0:
    print '*** Hostname required.'
    sys.exit(1)
port = 22
if hostname.find(':') >= 0:
    hostname, portstr = hostname.split(':')
    port = int(portstr)


# get username
if username == '':
    default_username = getpass.getuser()
    username = raw_input('Username [%s]: ' % default_username)
    if len(username) == 0:
        username = default_username
password = getpass.getpass('Password for %s@%s: ' % (username, hostname))


# get host key, if we know one
hostkeytype = None
hostkey = None
try:
    host_keys = paramiko.util.load_host_keys(os.path.expanduser('~/.ssh/known_hosts'))
except IOError:
    try:
        host_keys = paramiko.util.load_host_keys(os.path.expanduser('~/ssh/known_hosts'))
    except IOError:
        print '*** Unable to open host keys file'
        host_keys = {}

if host_keys.has_key(hostname):
    hostkeytype = host_keys[hostname].keys()[0]
    hostkey = host_keys[hostname][hostkeytype]
    print 'Using host key of type %s' % hostkeytype


# now, connect and use paramiko Transport to negotiate SSH2 across the connection
try:
    t = paramiko.Transport((hostname, port))
    t.connect(username=username, password=password, hostkey=hostkey)
    sftp = paramiko.SFTPClient.from_transport(t)

    # dirlist on remote host
    dirlist = sftp.listdir('.')
    print "Dirlist:", dirlist

    t.close()

except Exception, e:
    print '*** Caught exception: %s: %s' % (e.__class__, e)
    traceback.print_exc()
    try:
        t.close()
    except:
        pass
    sys.exit(1)

```

---

### Post by Mickeysofine1972 on 2008-04-03
Hmmm even version 1.6.2 from thier site crashes!

Ok it looks as though there may be something not right on my local machine or the server.

Whats really odd is that FileZilla lets me in and transfer using the same account!?!? I can even establish a ssh connection using the python command line and the paramiko library but as soon as I get the SFTPClient stuff to connect it dies.

Could there be something I need to allter on the server?

Mike

---

### Post by ghostdog74 on 2008-04-03
if you are quite sure that by using ssh or Filezilla and you can connect to the server, you might want to try posting to the mailing list.

---

### Post by Mickeysofine1972 on 2008-04-03
> **ghostdog74 said:**
> if you are quite sure that by using ssh or Filezilla and you can connect to the server, you might want to try posting to the mailing list.

I noticed that when you setup ssh you put 'PermitRootLogin no' in in the server config and this apears to be true of my remote host

This makes me think this might be an issue as I'm trying to login as root on the remote host, and, whilst FileZilla allows this the ssh allows it but sftp doesnt.

I tried this using the terminal sftp too and it gives:

```

Request for subsystem 'sftp' failed on channel 0
Couldn't read packet: Connection reset by peer

``` 

I even install a authorized_keys2 or the remote host and it seems to work on shh and asks for the pass phrase but sftp dies when I do the same and give the error above

Mike

---

### Post by Mickeysofine1972 on 2008-04-03
UPDATE:

Scratch that I tried with a non root account and that dies too :confused:

Mike

---

### Post by pmasiar on 2008-04-03
> **Mickeysofine1972 said:**
> Are always such a wet blanket? ... its not the first time you have violated the spirit of this forum, 

It you think that my suggestion for you to learn how to ask questions better violates CoC, you should report me instead of flaming.

> please be a good program and shut up.

It's very kind of you; definitely spirit of Ubuntu is with you! 

I will not waste my time on you anymore. I am turning you off. Bye.

---

### Post by tseliot on 2008-04-03
> **Mickeysofine1972 said:**
> ---- RANT STARTED ------

Are always such a wet blanket? Honestly, I ask for help and get you with you usual sarcasm and lack of actual answers to genuine questions. This is not the first time you have come in guns blazing and its not the first time you have violated the spirit of this forum, Inkeeping with the unix development way for things "If a program has nothing interesting to say, it should say nothing", please be a good program and shut up.

--- RANT OVER ------
Was this rant really necessary?

While pmasiar could have avoided being sarcastic, I agree with his suggestion. When I first read the title of this thread I thought that you were having (serious) problems with Python itself (e.g. some broken library).

Please, try to be a bit clearer next time, that's all.

---

### Post by Mickeysofine1972 on 2008-04-03
> **tseliot said:**
> Was this rant really necessary?

While pmasiar could have avoided being sarcastic, I agree with his suggestion. When I first read the title of this thread I thought that you were having (serious) problems with Python itself (e.g. some broken library).

Please, try to be a bit clearer next time, that's all.

Ok I admit that the title is a little sensational, but I only did it to get my post noticed and to get help of the Python gurus, not to get the contempt I recieved for being a lesser mortal.

Anyway, I respect your post tseliot as I have known you to be nothing but helpful, so if that offended you I apologize.

As thing turn out, all the help I received from all the other guys seems to have lead me to examining firewall issues when using ssh/sftp and whilst I know there are no port issues with my local side I know that my remote host does have firewalling but dont know if it has ports blocked.

If FileZilla can connect it might be that it is doing something more than paramiko doesnt by default, (like port forwarding, which I dont have the first clue how to do).

My situaltion is that I am in a office with a gateway between me and  the remote machine and so I dont really know how to get my ip to forward to back from the remote server.

Any ideas are most welcome.

Mike

BTW: this is serious as it for my job not for fun, but I wont go on anymore about that.

---

### Post by Mickeysofine1972 on 2008-04-03
Well i just used putty-tools and it connects no problem which implies that it does port forwarding.

I checked the C code and it does indeed!

How can I set that up in paramiko?

Mike

---

### Post by Wybiral on 2008-04-03
I've never even heard of paramiko, but my advice would be (since this seems like a very specific problem you're having) to try the [mailing list]("http://www.lag.net/mailman/listinfo/paramiko"). And, even easier than that, go to the [launchpad page]("https://launchpad.net/paramiko") and click the ["Ask a Question"]("https://answers.launchpad.net/paramiko/+addquestion") button. Chances are they will know better than we will.

---

### Post by ghostdog74 on 2008-04-03
look for the forward.py demo script.

---

### Post by slavik on 2008-04-03
nmap is good for port scanning :)

---

### Post by Mickeysofine1972 on 2008-04-04
Thanks for the advice, I promise to share the answer if I find one

Mike

---

### Post by hufengzhuo@yahoo.com on 2008-09-19
Hi Folks, 

I am a beginner for Paramiko Python programming. I am frustrated on how to read command returns in Paramiko? In Telnet, there is a function read_until, does anybody know which function in Paramiko can do the same functionality as read_until in Telnet?

Thanks a lot in advance

Lucy

---

### Post by ghostdog74 on 2008-09-19
> **hufengzhuo@yahoo.com said:**
> Hi Folks, 

I am a beginner for Paramiko Python programming. I am frustrated on how to read command returns in Paramiko? In Telnet, there is a function read_until, does anybody know which function in Paramiko can do the same functionality as read_until in Telnet?

Thanks a lot in advance

Lucy

you can post this to the paramiko mailing list. Let the author answer you.

---

### Post by hufengzhuo@yahoo.com on 2008-09-19
> **ghostdog74 said:**
> you can post this to the paramiko mailing list. Let the author answer you.

Thank you very much for your replies. I wonder how can I get the paramiko mailing list? I really appreciate your help.

---

### Post by Reiger on 2008-09-19
Though in the spirit of "Google knows ALL": try googling "paramiko mailing list", or alternatively follow this link [http://www.lag.net/mailman/listinfo/paramiko](http://www.lag.net/mailman/listinfo/paramiko) (note that this is hit #1 of the google results).

---

### Post by Reiger on 2008-09-19
ALSO: If the library really refuses to work you may be able to work around that by using an external (commandline) tool to do the job? For instance it turns out that typing ssh in my Konsole brings up a nice list of commands I may issue to it. Surely Python (its main interpreter being written in C after all) will offer some kind of Python wrapper/exec equivalent around an underlying C exec() procedure?

You would just have to perform top level redirecting of I/O streams to/from your app. In Java, at least this is really fairly straightforward using a Process object.

---

