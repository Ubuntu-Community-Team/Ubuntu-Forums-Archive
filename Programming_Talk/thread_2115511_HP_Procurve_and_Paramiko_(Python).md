---
title: "HP Procurve and Paramiko (Python)"
date: 2013-02-13
forum: Programming Talk
---

### Post by ronni on 2013-02-13
Hi,

I'm working on a script that should connect to switches of different vendors and execute some commands.

I've tried the different paramiko examples that I can find on the internet, but all of them fail on the HP Procurve switches, but works well on Cisco.

-- script that works on Cisco, fails on HP --
#!/usr/bin/python

import paramiko

cmd = "show version"
host = '10.10.10.1'
user = 'test'
passwd = 'test'

ssh = paramiko.SSHClient()

ssh.set_missing_host_key_policy(paramiko.AutoAddPolicy())
ssh.connect(host, username=user, password=passwd)
stdin, stdout, stderr = ssh.exec_command(cmd)
stdin.flush()
print stdout.readlines()
ssh.close()
-----
-- Error --
user@ubuntu:~/PythonScript$ ./gett.py
Traceback (most recent call last):
  File "./gett.py", line 20, in <module>
    stdin, stdout, stderr = ssh.exec_command(cmd)
  File "/usr/local/lib/python2.7/dist-packages/paramiko/client.py", line 364, in exec_command
    chan.exec_command(command)
  File "/usr/local/lib/python2.7/dist-packages/paramiko/channel.py", line 213, in exec_command
    self._wait_for_event()
  File "/usr/local/lib/python2.7/dist-packages/paramiko/channel.py", line 1084, in _wait_for_event
    raise e
paramiko.SSHException: Channel closed.
-----

I found this thread with the same problem:
[http://ubuntuforums.org/showthread.php?t=1332379](http://ubuntuforums.org/showthread.php?t=1332379)

Does anyone know why this don't work for this exact switch vendor and have a solution / hint on how to solve it?

---

