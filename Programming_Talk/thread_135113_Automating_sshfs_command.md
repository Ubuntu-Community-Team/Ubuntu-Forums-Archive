---
title: "Automating sshfs command"
date: 2006-02-23
forum: Programming Talk
---

### Post by thheggel on 2006-02-23
I've been trying write an automation script for sshfs using expect and also pexpect. I can't seem to get it right. Does anybody know how to get the sshfs automation working?

This is what i want to do:
Given a username and a password, i want the script to mount the home directory for the username given, at a location on the local machine. 

ex: sshfs me@192.168.0.10: /home/thisuser/mountpoint

I don't want a solution using certificates, and automaticly logon to ssh. I wan't to get this working using only scripting.

Anyone?

---

### Post by gmclachl on 2006-09-08
Sorry about bringing this post back from the dead so to speak, but I was having the same problem myself. 

 Anyway once I downloaded pexpect I wrote a quick and dirty python script to connect. 

 [PHP]
 #!/usr/bin/python
import pexpect
import time

command = "sshfs username@server:/path/to/home/folder /mount/point/"

def start_sshfs():
    try:
        sshfs = pexpect.spawn(command)
        sshfs.expect("Password: ")
        time.sleep (0.1)
        sshfs.sendline ("YourPassword")
        time.sleep (10) 
        sshfs.expect (pexpect.EOF)

    except Exception, e:
        print str(e)

def main ():
    start_sshfs()

if __name__ == '__main__':
    main ()

[/PHP]

Hope this helps someone.

Of course this has some security issues as you are storing a password in plain text. So remember to guard against that. 
George

---

### Post by HakanS on 2006-09-21
How do I use this script?

---

### Post by fde on 2007-09-02
up!

---

### Post by cwaldbieser on 2007-09-02
> **HakanS said:**
> How do I use this script?

You have to change the line starting with "command =" to have the correct command to mount the sshfs filesystem (e.g. replace the username, server, path to remote folder, and local mount point).  You also need to replace "YourPassword" with the actual password used to log on.  This is why the original poster cautions that you would have to have your password in plain-text in the script.

---

### Post by artheus on 2010-02-24
I've made an update of this script.. So it will work in Karmic. And with the newest update of sshfs.

[PHP]#!/usr/bin/python
import pexpect
import time

username = "username"
password = "password"
host = "adress.for.the.host"
hostdirectory = "/path/on/host"
mountpoint = "/path/to/mountpoint"

command = "sshfs " + username + "@" + host + ":" + hostdirectory + " " + mountpoint

def start_sshfs():
    try:
        sshfs = pexpect.spawn(command)
        sshfs.expect(username + "@" + host + "'s password: ")
        time.sleep (0.1)
        sshfs.sendline (password)
        time.sleep (10) 
        sshfs.expect (pexpect.EOF)

    except Exception, e:
        print str(e)

def main ():
    start_sshfs()

if __name__ == '__main__':
    main () [/PHP]

Hope that this will soon be a native feature of the Ubuntu distro. Just a little checkbox when you mount a network/ssh path. "Automount this on startup"

Cheers,
Artheus

---

### Post by coelho on 2010-11-20
Great solution from [http://darklaunch.com/2009/06/05/how-to-remote-mount-with-password-using-sshfs-and-stdin-ubuntu-sshfs-remote-mounting-mosso](http://darklaunch.com/2009/06/05/how-to-remote-mount-with-password-using-sshfs-and-stdin-ubuntu-sshfs-remote-mounting-mosso)

```
echo mypassword | sshfs myuser@ftp.mysite.com:/ ~/mounts/mysite -o workaround=rename -o password_stdin
```

---

### Post by aaronLund on 2011-12-06
> **coelho said:**
> Great solution from [http://darklaunch.com/2009/06/05/how-to-remote-mount-with-password-using-sshfs-and-stdin-ubuntu-sshfs-remote-mounting-mosso](http://darklaunch.com/2009/06/05/how-to-remote-mount-with-password-using-sshfs-and-stdin-ubuntu-sshfs-remote-mounting-mosso)

```
echo mypassword | sshfs myuser@ftp.mysite.com:/ ~/mounts/mysite -o workaround=rename -o password_stdin
```

I'm wondering why this doesn't work when you plug it into "Startup Applications"?

Works just fine in a terminal.

---

