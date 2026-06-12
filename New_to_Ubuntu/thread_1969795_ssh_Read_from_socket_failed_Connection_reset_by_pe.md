---
title: "ssh Read from socket failed: Connection reset by peer"
date: 2012-04-30
forum: New to Ubuntu
---

### Post by jackyu on 2012-04-30
I am having trouble using ssh to connect to a server at university.  The message given by ssh is: "Read from socket failed: Connection reset by peer".

The sys admin has asked me to use ssh protocol version 2.  I am not entirely sure what this means, but have tried ssh  with the option '-2' with the same results. 

I should perhpas mention that I am able to use ssh to connect to several other clusters at university, and that, for this problematic one, I can connect by using PuTTy in Windows.

Any help with this would be much appreciated.  thanks

I am using Ubuntu 11.10 (Oneiric).

The output from  "ssh -v" is:
--------------------------------------------------------------------------
OpenSSH_5.8p1 Debian-7ubuntu1, OpenSSL 1.0.0e 6 Sep 2011
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to gateway2 [67.207.31.243] port 22.
debug1: Connection established.
debug1: identity file /home/jack/.ssh/id_rsa type -1
debug1: identity file /home/jack/.ssh/id_rsa-cert type -1
debug1: identity file /home/jack/.ssh/id_dsa type -1
debug1: identity file /home/jack/.ssh/id_dsa-cert type -1
debug1: identity file /home/jack/.ssh/id_ecdsa type -1
debug1: identity file /home/jack/.ssh/id_ecdsa-cert type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_4.3
debug1: match: OpenSSH_4.3 pat OpenSSH_4*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.8p1 Debian-7ubuntu1
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-ctr hmac-md5 none
debug1: kex: client->server aes128-ctr hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Server host key: RSA 25:6f:f1:37:19:fa:76:7e:61:93:b6:b3:90:86:cc:9c
debug1: Host 'gateway2' is known and matches the RSA host key.
debug1: Found key in /home/jack/.ssh/known_hosts:1
debug1: ssh_rsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: Roaming not allowed by server
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey,gssapi-with-mic,password
debug1: Next authentication method: gssapi-with-mic
debug1: Unspecified GSS failure.  Minor code may provide more information
Credentials cache file '/tmp/krb5cc_1000' not found

debug1: Unspecified GSS failure.  Minor code may provide more information
Credentials cache file '/tmp/krb5cc_1000' not found

debug1: Unspecified GSS failure.  Minor code may provide more information


debug1: Unspecified GSS failure.  Minor code may provide more information


debug1: Next authentication method: publickey
debug1: Trying private key: /home/jack/.ssh/id_rsa
debug1: Trying private key: /home/jack/.ssh/id_dsa
debug1: Trying private key: /home/jack/.ssh/id_ecdsa
debug1: Next authentication method: password
JC0311443@gateway2's password: 
Read from socket failed: Connection reset by peer
---------------------------------------------------------------------------

---

