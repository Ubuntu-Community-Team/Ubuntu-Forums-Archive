---
title: "custom login shell script"
date: 2010-08-03
forum: Programming Talk
---

### Post by pytheas22 on 2010-08-03
I have an Ubuntu 10.04 server joined to a Windows Active Directory domain via Likewise Open 6.  All works well and users can log in using their AD credentials without a problem.

Since our AD environment is very large and I only want certain AD users to be able to log in to this machine, I changed Likewise's configuration so that the default login shell points to a simple wrapper script.  The script decides whether a user should be granted a real shell based on whether his AD username is on a whitelist at /etc/domain-users.  The script looks like this:

```

#!/bin/bash

USERNAME=`whoami`

if grep ^$USERNAME$ /etc/domain-users > /dev/null
then
  echo "User authorized"
  /bin/bash
  else echo -e "You are not authorized to log into this server\n\n"
fi
```

This approach works fine for ssh sessions, but it doesn't allow domain users to scp and I can't figure out why.  Running scp with the verbose flag for a domain user outputs:
```

$ scp -v file domain-userserver:/home/domain-user
Executing: program /usr/bin/ssh host server, user domain-user, command scp -v -t /home/domain-user
OpenSSH_5.3p1 Debian-3ubuntu4, OpenSSL 0.9.8k 25 Mar 2009
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to server [128.220.16.23] port 22.
debug1: Connection established.
debug1: identity file /home/user/.ssh/identity type -1
debug1: identity file /home/user/.ssh/id_rsa type -1
debug1: identity file /home/user/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.3p1 Debian-3ubuntu4
debug1: match: OpenSSH_5.3p1 Debian-3ubuntu4 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.3p1 Debian-3ubuntu4
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-ctr hmac-md5 none
debug1: kex: client->server aes128-ctr hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Host 'server' is known and matches the RSA host key.
debug1: Found key in /home/user/.ssh/known_hosts:1
debug1: ssh_rsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey,gssapi-keyex,gssapi-with-mic,password,keyboard-interactive
debug1: Next authentication method: gssapi-keyex
debug1: No valid Key exchange context
debug1: Next authentication method: gssapi-with-mic
debug1: Unspecified GSS failure.  Minor code may provide more information
Credentials cache file '/tmp/krb5cc_1000' not found

debug1: Unspecified GSS failure.  Minor code may provide more information
Credentials cache file '/tmp/krb5cc_1000' not found

debug1: Unspecified GSS failure.  Minor code may provide more information


debug1: Next authentication method: publickey
debug1: Trying private key: /home/user/.ssh/identity
debug1: Trying private key: /home/user/.ssh/id_rsa
debug1: Trying private key: /home/user/.ssh/id_dsa
debug1: Next authentication method: keyboard-interactive
Password: 
debug1: Authentication succeeded (keyboard-interactive).
debug1: channel 0: new [client-session]
debug1: Requesting no-more-sessions@openssh.com
debug1: Entering interactive session.
debug1: Sending environment.
debug1: Sending env LANG = en_US.utf8
debug1: Sending command: scp -v -t /home/domain-user
User authorized
user@user-ubuntu-netbook:~$ debug1: client_input_channel_req: channel 0 rtype exit-status reply 0
debug1: channel 0: free: client-session, nchannels 1
debug1: fd 0 clearing O_NONBLOCK
debug1: fd 1 clearing O_NONBLOCK
Transferred: sent 1552, received 2088 bytes, in 0.2 seconds
Bytes per second: sent 9287.5, received 12495.0
debug1: Exit status 0
```

I think the trick to solving this problem is to figure out a way for my wrapper script to accept a command as an argument and execute it; currently, it looks like scp tries to send the script a command, but it just ignores it.  Any advice on how to solve this would be much appreciated.

EDIT: I figured it out.  I needed to tell my script that it should also execute $2 if it exists, so I changed the wrapper script to:

```
#!/bin/bash

USERNAME=`whoami`

if ! grep ^$USERNAME$ /etc/domain-users > /dev/null; then
   echo -e "You are not authorized to log into this server\n\n"
elif test -z "$2"; then
   echo -e "User authorized"
   /bin/bash
else #in case users are trying to send a command via ssh or use scp
   $2
fi
```

---

### Post by 1971hemicuda on 2011-02-16
I've read through this and think its a great concept!  I have a similar situation where I work

I've run through the basics, created the file list of users

Created your login script

but i don't know where to change the likewise information.  Can you point me in a better direction?

This is a great concept, FYI

---

### Post by pytheas22 on 2011-02-17
Glad you've found this useful.  I can't take credit for the concept, as I'd read about it elsewhere, but I think the implementation is original.  (On that note, I'm not really a professional and I'm sure there are better/more secure ways to do this, but this approach worked for my needs.)

I don't have access to my AD environment right now, but my notes say that to get the wrapper script to work, you need to edit the file /etc/samba/smb.conf and change the value for "template shell" from /bin/bash to the path to your wrapper script.

Hopefully that does the trick; if not let me know and I can look more closely at my notes.

---

