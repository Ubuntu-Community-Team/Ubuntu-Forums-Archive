---
title: "changing user access to sftp from ftp"
date: 2008-05-08
forum: New to Ubuntu
---

### Post by ceabaird on 2008-05-08
OK, I'm trying to change a user from ftp to ssh access, to plug a security hole.

I can ftp in fine, but when I try to ssh in, I get prompted for the user's password, and after entering it, the connection is automatically closed.

I've been looking thru the forums here and on google, but I'm not finding what I'm looking for. A point in the right direction, please?

Thanks

---

### Post by ceabaird on 2008-05-08
OK, when I ssh -v in, I get this output:

xxxxx:~ xxxxx$ ssh -v [email]xxxxx@xxx.xxx.xxx.xxx[/email]
OpenSSH_4.7p1, OpenSSL 0.9.7l 28 Sep 2006
debug1: Reading configuration data /etc/ssh_config
debug1: Connecting to xxx.xxx.xxx.xxx [xxx.xxx.xxx.xxx] port 22.
debug1: Connection established.
debug1: identity file /Users/xxx/.ssh/identity type -1
debug1: identity file /Users/xxx/.ssh/id_rsa type -1
debug1: identity file /Users/xxx/.ssh/id_dsa type 2
debug1: Remote protocol version 2.0, remote software version OpenSSH_4.3p2 Debian-8ubuntu1.2
debug1: match: OpenSSH_4.3p2 Debian-8ubuntu1.2 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_4.7
debug1: Miscellaneous failure
No credentials cache found

debug1: Miscellaneous failure
No credentials cache found

debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-cbc hmac-md5 none
debug1: kex: client->server aes128-cbc hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Host 'xxx.xxx.xxx.xxx' is known and matches the RSA host key.
debug1: Found key in /Users/xxx/.ssh/known_hosts:1
debug1: ssh_rsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey,password
debug1: Next authentication method: publickey
debug1: Trying private key: /Users/xxx/.ssh/identity
debug1: Trying private key: /Users/xxx/.ssh/id_rsa
debug1: Offering public key: /Users/xxx/.ssh/id_dsa
debug1: Authentications that can continue: publickey,password
debug1: Next authentication method: password
[email]xxx@xxx.xxx.xxx.xxx[/email]'s password: 
debug1: Authentication succeeded (password).
debug1: channel 0: new [client-session]
debug1: Entering interactive session.
Linux xxx.xxxxx.com 2.6.20-15-server #2 SMP Sun Apr 15 07:41:34 UTC 2007 i686

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.
Last login: Thu May  8 15:38:46 2008 from ex104.xxx.xx.xx
debug1: client_input_channel_req: channel 0 rtype exit-status reply 0
debug1: channel 0: free: client-session, nchannels 1
Connection to xxx.xxx.xxx.xxx closed.
debug1: Transferred: stdin 0, stdout 0, stderr 39 bytes in 0.0 seconds
debug1: Bytes per second: stdin 0.0, stdout 0.0, stderr 1229.8
debug1: Exit status 1

I assume that it's looking for a key to go with the user account that I'm trying to log (ssh) in with, and it's not finding it?

---

