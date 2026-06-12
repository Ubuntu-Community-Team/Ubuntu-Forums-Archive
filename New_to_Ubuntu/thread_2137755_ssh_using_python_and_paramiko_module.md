---
title: "ssh using python and paramiko module"
date: 2013-04-21
forum: New to Ubuntu
---

### Post by Shahid09 on 2013-04-21
Hi All,

This is my first post and I am very new in python and paramiko. My requirement is to:

- ssh server1.com
- ssh from server1 to server2.com
- ssh from server2 to server3.com 
- run multiple UNIX commands on server3.com like declog, decrypt, scp, grep etc.... and finally create .tgz file
- Move .tgz file from server3 to server2 to server1 to local

I did Google and found that python script with paramiko module can do this job. I was able to ssh to server1 but don't know how to ssh server2 and server3.

I will also appreciate, if you can give me guidelines or different approach to achieve this task.

```

        ssh = paramiko.SSHClient()
        ssh.set_missing_host_key_policy(paramiko.AutoAddPolicy())
        ssh.load_host_keys("/cygwin/home/skhome/.ssh/known_hosts")
        privkey = paramiko.RSAKey.from_private_key_file ("/cygwin/home/skhome/.ssh/id_rsa")
        ssh.connect('server1.com', username='sk000g',pkey=privkey )
        # Not sure how to connect sever2, server3 and execute UNIX commands

```

Thanks,
Shah

---

