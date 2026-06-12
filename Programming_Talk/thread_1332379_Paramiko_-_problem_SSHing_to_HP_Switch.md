---
title: "Paramiko - problem SSHing to HP Switch"
date: 2009-11-20
forum: Programming Talk
---

### Post by phoenix__ on 2009-11-20
Hi all,

I am just getting started with paramiko, and using the latest 1.7.6. I've
got a very basic test program which I'm running interactively in python.
This works fine when I connect to a regular linux machine (I'm using ssh
keys so no need for passwords etc).

[php]
import paramiko
paramiko.util.log_to_file('/tmp/paramiko.log')
ssh = paramiko.SSHClient()
ssh.set_missing_host_key_policy(paramiko.AutoAddPolicy())
ssh.connect('<linux machine>')
stdin, stdout, stderr = ssh.exec_command('ls')
print stdout.read()
<output as expected>
ssh.close()
[/php]If I replace <linux machine> with one of our HP Procurve Switches, and try
and execute 'sh uptime' (or any other command), I get the output:

[COLOR=#800000]>>> stdin, stdout, stderr = ssh.exec_command('sh uptime')[/COLOR]
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  File "/home/jefff/paramiko-1.7.6/paramiko/client.py", line 355, in
exec_command
    chan.exec_command(command)
  File "/home/jefff/paramiko-1.7.6/paramiko/channel.py", line 213, in
exec_command
    self._wait_for_event()
  File "/home/jefff/paramiko-1.7.6/paramiko/channel.py", line 1084, in
_wait_for_event
    raise e
paramiko.SSHException: Channel closed.

The log file shows:
----
DEB [20091120-11:25:14.116] thr=4   paramiko.transport: starting thread
(client mode): 0xc9d78d90L
INF [20091120-11:25:14.484] thr=4   paramiko.transport: Connected (version
2.0, client OpenSSH_3.7.1p2)
DEB [20091120-11:25:14.488] thr=4   paramiko.transport: kex
algos:['diffie-hellman-group-exchange-sha1', 'diffie-hellman-group1-sha1']
server key:[
'ssh-rsa'] client encrypt:['des', '3des-cbc'] server encrypt:['des',
'3des-cbc'] client mac:['hmac-md5', 'hmac-sha1', 'hmac-ripemd160',
'hmac-ripem
[d160@openssh.com]("https://mail.fcse.co.uk/src/compose.php?send_to=d160%40openssh.com")', 'hmac-sha1-96', 'hmac-md5-96'] server mac:['hmac-md5',
'hmac-sha1', 'hmac-ripemd160', '[hmac-ripemd160@openssh.com]("https://mail.fcse.co.uk/src/compose.php?send_to=hmac-ripemd160%40openssh.com")', 'hmac-sha1-9
6', 'hmac-md5-96'] client compress:['none'] server compress:['none']
client lang:[''] server lang:[''] kex follows?False
DEB [20091120-11:25:14.488] thr=4   paramiko.transport: Ciphers agreed:
local=3des-cbc, remote=3des-cbc
DEB [20091120-11:25:14.488] thr=4   paramiko.transport: using kex
diffie-hellman-group1-sha1; server key type ssh-rsa; cipher: local
3des-cbc, remo
te 3des-cbc; mac: local hmac-sha1, remote hmac-sha1; compression: local
none, remote none
DEB [20091120-11:25:14.808] thr=4   paramiko.transport: Switch to new keys
...
DEB [20091120-11:25:14.819] thr=2   paramiko.transport: Adding ssh-rsa
host key for queens-core-sw1: dab836871bd7520b1088bb9653b741f4
DEB [20091120-11:25:14.822] thr=2   paramiko.transport: Trying SSH agent
key bf2ea5e7aad8da1030767bcddd640c41
DEB [20091120-11:25:14.853] thr=4   paramiko.transport: userauth is OK
INF [20091120-11:25:14.884] thr=4   paramiko.transport: Authentication
(publickey) successful!
DEB [20091120-11:25:19.341] thr=2   paramiko.transport: [chan 1] Max
packet in: 34816 bytes
DEB [20091120-11:25:19.343] thr=4   paramiko.transport: [chan 1] Max
packet out: 32768 bytes
INF [20091120-11:25:19.343] thr=4   paramiko.transport: Secsh channel 1
opened.
DEB [20091120-11:25:19.348] thr=4   paramiko.transport: [chan 1] EOF sent (1)
DEB [20091120-11:25:19.353] thr=4   paramiko.transport: EOF in transport
thread
----

When I SSH to the switch manually, after the authentication, and before
the prompt, it gives a status message, and requires a key press before the
prompt is given.

-----
ProCurve J4900A Switch 2626
Software revision H.10.38

Copyright (C) 1991-2007 Hewlett-Packard Co.  All Rights Reserved.

                           RESTRICTED RIGHTS LEGEND

 Use, duplication, or disclosure by the Government is subject to restrictions
 as set forth in subdivision (b) (3) (ii) of the Rights in Technical Data and
 Computer Software clause at 52.227-7013.

         HEWLETT-PACKARD COMPANY, 3000 Hanover St., Palo Alto, CA 94303











Press any key to continue
---

After a couple more tests, I don't think this is related to the problem
(although I could be wrong). If I manually log into the switch and issue a
'sh ip ssh' it lists the current connections however at no stage does it
show a connection coming from the machine I'm running this python code on.
If I issue a SSH command manually and leave it on the 'press any key'
message, 'sh ip ssh' does list a connection so it doesn't look like
paramiko is getting stuck at this bit (unless it instantly closes the
connection when it doesn't receive a prompt?).

Does anyone have any ideas? Happy to provide more debugs or information.

---

### Post by riteshsarraf on 2009-11-23
I am having somewhat similar problems.

I do a read of stdout (stdout.read() ) and it reads good. But at the end, after I guess EOF, it returns me a None.

I have raised a Debian bug for this but not had any responses.

---

### Post by phoenix__ on 2009-11-23
Your problem doesn't seem that similar to mine, as you are able to issue a command and read a response. As soon as I try and issue a command I get an exception.

---

