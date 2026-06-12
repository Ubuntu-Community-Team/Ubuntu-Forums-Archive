---
title: "bash &amp; ssh"
date: 2010-11-15
forum: Programming Talk
---

### Post by Drenriza on 2010-11-15
Hi all, i'm wondering if it is possible to ssh through a script from one machine to another.
The point in all of this, is that i want to make a script. That can ssh to a machine and execute a series of commands.

But i get stuck. If i go and make a script
```

#!/bin/bash
ssh xxx@ip
##password??
```how do i enter the password in the script? hope it makes sense.

Thanks on advance.
Kind Regards.

EDIT:
I have found this, but what does it do. Exactly? and how does it work.
```
remoteuser=myname
remotecomputer=example.com
ssh -l "$remoteuser" "$remotecomputer" "ls -l; date; "
```
[http://www.unix.com/shell-programming-scripting/44495-bash-script-ssh-login.html](http://www.unix.com/shell-programming-scripting/44495-bash-script-ssh-login.html)

---

### Post by Barrucadu on 2010-11-15
It SSHes into $remotecomputer logging in as the user $remoteuser, and executes the command "ls -l; date".

For passwordless SSH, look into SSH public/private keys.

---

### Post by Drenriza on 2010-11-15
> **Barrucadu said:**
> It SSHes into $remotecomputer logging in as the user $remoteuser, and executes the command "ls -l; date".

For passwordless SSH, look into SSH public/private keys.

what would an example in bash look like when using ssh with a public/private key.

EDIT:
Question #1
If i make my key with 
```
ssh-keygen -t [COLOR=#3300ff]rsa[/COLOR] -b 4096
```and
> Then, paste the content of the local ~/.ssh/id_dsa.pub file into the file ~/.ssh/authorized_keys on the remote host.                      How would i connect to this machine through my script? do i still do
```
ssh xx@ip 
```And then it just wont ask me for a password? Or?

Question #2
The key i make do i need to add that to my script?

---

### Post by saulgoode on 2010-11-15
> **Drenriza said:**
> Question #1
If i make my key with 
```
ssh-keygen -t [COLOR=#3300ff]rsa[/COLOR] -b 4096
```and
How would i connect to this machine through my script? do i still do
```
ssh xx@ip 
```And then it just wont ask me for a password?

That would work but only if the user running the script is 'xx' on both systems (else a password is requested.

---

### Post by Drenriza on 2010-11-15
> **saulgoode said:**
> That would work but only if the user running the script is 'xx' on both systems (else a password is requested.

If it promts me for a password, how can i get the script to supply this password?
So i dont manually need to type the password once the script has started.

---

### Post by Barrucadu on 2010-11-15
Copy the key to the remote server (`ssh-copy-id user@host`), then you can connect without a password (`ssh user@host`)

---

### Post by Drenriza on 2010-11-16
Hi all.

A little update. The method with a public/private key is not possible, since i have realised something. If i do this, and then the local machine gets hacked, then the hackers would have access to my remote machine, without needing to identify themselves. Which of course is a security breach. So what can i do to make this secure in this regard?

---

### Post by Reiger on 2010-11-16
And how would the local machine get hacked? That is a security vulnerability more so than use of public/private keys.

---

### Post by Drenriza on 2010-11-16
> **Reiger said:**
> And how would the local machine get hacked? That is a security vulnerability more so than use of public/private keys.

That is true, but still it is a possibility. But then the keys become "dangerous" since a password is no longer required.

---

### Post by spjackson on 2010-11-16
> **Drenriza said:**
> That is true, but still it is a possibility. But then the keys become "dangerous" since a password is no longer required.
In that case, you cannot do what you want to do.

Any method that can be devised for your script to provide the password for access to the remote machine will be vulnerable if an intruder gets access to your account on the local machine.

Since you have this concern, you will need to live with supplying the password manually every time.

---

### Post by saulgoode on 2010-11-16
> **Drenriza said:**
> If it promts me for a password, how can i get the script to supply this password?
So i dont manually need to type the password once the script has started.

You could accomplish this using 'expect':

```
#!/usr/bin/expect -f
set timeout 5
set ip "ip"
set user "xx"
set password "thepassword"

spawn ssh "$user\@$ip" 

expect "*assword:*" 

send "$password\r"

interact
```

Note, however, that if your concern is with the local machine being compromised then this approach is even worse the shared key authentication. As spjackson has expressed, there is no way to permit automatic logins from local client systems without leaving the remote server vulnerable to compromised clients.

The main reason that the 'expect' approach is worse than shared keys is that the password must exist in plaintext on the local machine (make absolutely certain that the script's permissions only allow it to be read by the owner of password!). Another problem is that your 'expect' script will cease to function if the user's password is ever changed (shared key exchange is unaffected by a password change). 

I highly recommend that you use shared key authentication instead. 'expect' is sometimes useful for accessing FTP and Telnet servers, but with regard to SSH its utility has been made obsolete.

---

### Post by dwhitney67 on 2010-11-16
> **Drenriza said:**
> That is true, but still it is a possibility. But then the keys become "dangerous" since a password is no longer required.

To reduce the chance of being hacked, change your password every 90 days.  Use a 12-character passwords that consists of upper- and lower-case letters, and at least one number and a special symbol.  For example:  Chg*P@ssw0rd

Then use the public/private key for SSH.

---

