---
title: "Is it correct that the server can be accessed by FTP out of the box?"
date: 2011-09-12
forum: New to Ubuntu
---

### Post by gb5256 on 2011-09-12
Hello,
I am using rackspace for testing my websites.
I have now created a fresh server with a fresh ubuntu 10.04 LTS.
I created a new user called user1.
Right after I have done this I seem to have full access via FTP to this server from outside, choosing for FTPS and entering the Username and credentials as mentioned (i use filezilla from a OSX).
Is this correct?
I have not installed any FTP yet (like vsftp etc).
Furthermore I have not changed any iptables, so FTP should not work out of the box from outside i guess...

is this normal behaviour? 

Thanks for helping a newbie...
gb5256

---

### Post by ubudog on 2011-09-12
It seems the Rackspace guys set it up like that, did you choose FTP access when you were setting up the server?

You could uninstall it, for example:
```
sudo apt-get remove vsftpd
```

---

### Post by gb5256 on 2011-09-12
No, i have not setup anything.
This was a fresh machine.
The point for me about this is, that after I install then vsftp, some settings can not be changed by me (for example when I disable that ANY local user can login, the system still allows it do do...

strange...

But thanks for the help. I do know now that this is not supposed to be that way. So I have to check with the rackspace guys.
Thanks for your time.

gb5256

---

### Post by ubudog on 2011-09-12
Tip: If you are ssh'ing in, I recommend setting up key authentication, and then disabling PasswordAuth, if you've not already done so.  Also, you do have root on the box, right?

---

### Post by gb5256 on 2011-09-12
Hello,
Yes I have full root and access the server via ssh.
Thanks for your time.

gfb5256

---

