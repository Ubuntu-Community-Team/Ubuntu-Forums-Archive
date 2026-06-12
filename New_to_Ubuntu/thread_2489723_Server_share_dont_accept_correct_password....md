---
title: "Server share dont accept correct password..."
date: 2023-08-08
forum: New to Ubuntu
---

### Post by avsilva on 2023-08-08
Hi all. 
   	So I mounted an Unraid share using cifs, providing my user and password which are accepted. 
   	Then I try to transfer a file with rsync to it from my Ubuntu machine  and the Unraid server do not accept the same already proven  password  (because it mounted the share with that password..) 
   	Can't figure it out! 
   	PS "senha" means password in portuguese,,, 
   	  
   	Thanks, André 
   	  
   	avallejo@andre-xps:~/Documents$ sudo rsync -rv  testeCopia avs@192.168.0.150:/mnt/BackUPWin
	[sudo] senha para avallejo:  
	The authenticity of host '192.168.0.150 (192.168.0.150)' can't be established.
	ED25519 key fingerprint is SHA256:nZs+LYgnsE4MYqqGU1yMVMj622etdpgwBkcNligzdyE.
	This key is not known by any other names
	Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
	Warning: Permanently added '192.168.0.150' (ED25519) to the list of known hosts.
	(avs@192.168.0.150) Password:  
	(avs@192.168.0.150) Password:  
	(avs@192.168.0.150) Password:  
	avs@192.168.0.150's password:  
	Permission denied, please try again.
	avs@192.168.0.150's password: 
   	Connection closed by 192.168.0.150 port 22
	rsync: connection unexpectedly closed (0 bytes received so far) [sender]
	rsync error: unexplained error (code 255) at io.c(231) [sender=3.2.7]
	avallejo@andre-xps:~/Documents$

---

### Post by MAFoElffen on 2023-08-09
I rsync, back and forth between my servers, workstation and laptop. From my understanding...rsync remote transfers first use shh to establish the connection, then once connected, it invokes the remote host&#8217;s rsync, and then the two programs (remote and local) will determine what parts of the local-file need to be copied so that the remote file matches the local one.

So if you first debug that initial "connection" with showing the output of 
```

ssh -v avs@192.168.0.150

```
Then we will go from there...

Personally, I use encrypted ssh keys copied between my machines, so that rsync uses those keys to take care of the logins between my machines.

---

### Post by ActionParsnip on 2023-08-09
If this will be a common task then I suggest you setup SSH keys rather than using a password

---

### Post by avsilva on 2023-08-09
Thanks guys, I’ll look into this keys/tokens thing, I was anaware of them…

---

### Post by ActionParsnip on 2023-08-09
also why "sudo rsync" ? does your user not have read access to the [COLOR=#E8E6E3]testeCopia file?[/COLOR]

---

### Post by MAFoElffen on 2023-08-09
> **ActionParsnip said:**
> also why "**[COLOR=#ff0000]sudo rsync[/COLOR]**" ? does your user not have read access to the [COLOR=#E8E6E3]testeCopia file?[/COLOR]
@ActionParsnip -- Thank you for pointing that out ^^^. (I missed that part.) 'That' is why it failed.

If you use sudo with rsync, then it tries to use sudo with the ssh part of that, so ends up being the "root" user logging in remotely using 'root' on your side, and user 'avs' on the remote node, ...which will fail.

If you did
```

sudo ssh -v avs@192.168.0.150

```
It would then show what is going on with that...

sshd.conf is setup by default with the root user prevented from using shh.

If you need to do rsync as root because of permissions issues, then setup encrypted keys for the root user, edit the config files to allow encrypted key ssh logins for root...

---

### Post by avsilva on 2023-08-09
Learning with you about all of this…I really want to learn Linux, but it’s a long learning curve…thanks!

---

### Post by MAFoElffen on 2023-08-09
> **avsilva said:**
> Learning with you about all of this…I really want to learn Linux, but it’s a long learning curve…thanks!
The learning curve Is a very worthwhile journey. I enjoy tinkering around and making thing "mine" with little customization's here and there. Mostly things are static and stable... I like to learn how things should work together underneath it all. I challenge myself to keep learning new things.

With Linux, that is easy and inexpensive. Most things are free and "available" to learn.

Welcome to your journey. This is a great community to learn and share with others.

---

### Post by avsilva on 2023-08-09
> **MAFoElffen said:**
> 
Welcome to your journey. This is a great community to learn and share with others.

Thanks! I’m enjoying the ride too. As a photographer, I confess that I miss some of the tools available to my Mac system, but using the Linux apps also stimulate me to try new things, which are never bad to creativity…time will tell…

---

### Post by avsilva on 2023-08-10
There I go again... so I created ssh keys and successfully installed on the Unraid server (named Calango). I can log in allright:

[FONT=monospace][COLOR=#54ff54]**avallejo@andre-xps**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ ssh 'root@192.168.0.150' [/COLOR]
Last login: Thu Aug 10 07:06:46 2023 from 192.168.0.102 
Linux 6.1.36-Unraid. 
[COLOR=#54ff54]**root@Calango**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]# sudo su [/COLOR]
[COLOR=#54ff54]**root@Calango**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]# exit[/COLOR]


Now, if I try to login as an user, not root...
[/FONT][FONT=monospace][COLOR=#54ff54]**avallejo@andre-xps**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ ssh 'avs@192.168.0.150' [/COLOR]
(avs@192.168.0.150) Password:  
(avs@192.168.0.150) Password:  
(avs@192.168.0.150) Password:  
avs@192.168.0.150's password:  
Permission denied, please try again. 
avs@192.168.0.150's password:  
Received disconnect from 192.168.0.150 port 22:2: Too many authentication failures 
Disconnected from 192.168.0.150 port 22

My user password is not accepted...lost again! I&#7743; probably missing some point here...
[/FONT]

---

### Post by ActionParsnip on 2023-08-10
If you are sshing as root, why did you run "sudo su"...?
You need to copy the public key to the authoized keys file of the avs user if you want to use the same private key for the avs user. You can't log in directly as any user on the system just because it is in root's authoized keys. That's not how keys work.

---

### Post by TheFu on 2023-08-10
Let's clarify some things.

Any passwords and account that use CIFS/Samba have very little to do with local Linux/Unix accounts.  Using the same name means nothing.  Samba has its own password DB with users and passwords. This is not related to Unix/Linux in any way.

As for ssh, every process runs with an effective userid.  With the default prompt, your userid will be displayed.  If we assume the local username is avsilva, then when you use ssh-keygen to create new keys, those keys will be created for that specific user and place into ~avsilva/.ssh/ as a public and private key-pair.

If you use sudo ssh-keygen AND the OS on the system is 22.04 or later, then the ssh keys will be created for the 'root' user and place into ~root/.ssh/ as a public and private key-pair.
These are vastly different.

It is possible to have avsilva on the local system connect to root on a different system using ssh keys, but in the debian world, this is considered _bad form_ and should mostly be avoided. There are exceptions and well used techniques to address root -to- root logins, but these are really only used for lazy needs.  My backups run in a way that effectively does root -to- root transfers, but I use a non-root account on both sides. It is a little trick that's possible because the passwd file doesn't demand uid values be unique.  Also, with ssh, it is possible to specify that only 1 command is allowed to be run based on the ssh-key used, which can be used to drastically improve security.  This is how websites like github work.

I'm not a fan of **sudo su**.  I'd rather see **sudo -i** or **sudo -s** depending on which environment you want carried into the new terminal session.  For a few commands, using **sudo cmd** is better so everything run gets logged.

As for copying around the ssh public keys to where they need to be, there's a tool, **ssh-copy-id** designed just for that. It works well and prevents dumb mistakes.  I make enough dumb mistakes that when a tool is there to prevent them and does the job easily, I want to use it.

---

### Post by avsilva on 2023-08-10
Ok&#8230;so now my brain is officially boiling&#8230;guess I have to give a step back and study more before trying again. I only used sudo su at the prompt because I read that it was a way to check if  I had permissions issues, apparently not&#8230; About the keys, what I did was to generate the keys, which are now stored in root/.ssh. Then I used ssh-copy-id to the root of the server. So that&#8217;s why I can connect to it, root to root, fine. Now that I want to access a share on the server from what I understand you both saying, I have to copy it to my avs user on the server, so I did:

[FONT=monospace][COLOR=#54ff54]**avallejo@andre-xps**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ ssh-copy-id avs@192.168.0.150[/COLOR]
/usr/bin/ssh-copy-id: INFO: Source of key(s) to be installed: "/home/avallejo/.ssh/i
d_rsa.pub" 
/usr/bin/ssh-copy-id: INFO: attempting to log in with the new key(s), to filter out 
any that are already installed 
/usr/bin/ssh-copy-id: INFO: 1 key(s) remain to be installed -- if you are prompted n
ow it is to install the new keys 
(avs@192.168.0.150) Password:  
(avs@192.168.0.150) Password:  
(avs@192.168.0.150) Password:  
avs@192.168.0.150's password:  
Permission denied, please try again. 
avs@192.168.0.150's password:  
Received disconnect from 192.168.0.150 port 22:2: Too many authentication failures 
Disconnected from 192.168.0.150 port 22 
[COLOR=#54ff54]**avallejo@andre-xps**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$  [/COLOR]

As you can see, my password keeps being rejected.

Of interest, while searching about the problem, I stumbled upon the following advice:
[/FONT]In the client's configuration file (/etc/ssh/ssh_config), uncomment lines 42 and 43.
Those were:
#   VisualHostKey no
#   ProxyCommand ssh -q -W %h:%p gateway.example.com

So I did and the share mounted...but the system immediately hanged and soon after the share unmounted by itself and the system came back to life...could be a clue...

I guess the gateway.example.com should be something else...like what? The gateway is the IP of the router?

---

### Post by TheFu on 2023-08-10
Does the username, avs, exist on the device ... and I don't mean for samba. I mean for Unix logins.  Each userid has a different password, hope that is clear too.

Also, while the /etc/ssh/ssh_config is a client config, each userid can also have one in ~/.ssh/config which accepts the same client-side settings.  It is best practice to leave the central config files alone and only modify the per-userid configs.

If it was me, I'd not use root/sudo for this without very good reason.  I'd use
```
$ ssh -vvv avs@192.168.0.150
```
for troubleshooting.  This assumes avs is a username on the remote system and 192.168.0.150 is the correct IP address of that remote system.

If it were me, I'd setup NFS between Unix systems. That is the native way to have shared storage in Unix and it provides native POSIX permissions. The only time I'd use CIFS is when MS-Windows is involved. CIFS is sorta the bottom-of-the-barrel option for network file access.  Of course, you'll need ssh access to setup NFS on the remote system, open the needed firewall ports, etc.  NFS allows about 99.9% of all programs native access to remote storage. Only a very few don't work with NFS and when it doesn't, that is a bug.

---

### Post by MAFoElffen on 2023-08-10
> **TheFu said:**
> ```
$ ssh -vvv avs@192.168.0.150
```
for troubleshooting.  This assumes avs is a username on the remote system and 192.168.0.150 is the correct IP address of that remote system.

+1 - The OP has been asked for ssh debug output in Posts #'s  2, 6, & 14 so far with no response with those... yet.

---

### Post by avsilva on 2023-08-10
> **MAFoElffen said:**
> +1 - The OP has been asked for ssh debug output in Posts #'s  2, 6, & 14 so far with no response with those... yet.

Oh, just learned how to do that...:o..I guess this is it...


[FONT=monospace][COLOR=#54ff54]**avallejo@andre-xps**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$  ssh -vvv avs@192.168.0.150 [/COLOR]
OpenSSH_9.0p1 Ubuntu-1ubuntu8.4, OpenSSL 3.0.8 7 Feb 2023 
debug1: Reading configuration data /etc/ssh/ssh_config 
debug1: /etc/ssh/ssh_config line 19: include /etc/ssh/ssh_config.d/*.conf matched no
 files 
debug1: /etc/ssh/ssh_config line 21: Applying options for * 
debug2: resolve_canonicalize: hostname 192.168.0.150 is address 
debug3: expanded UserKnownHostsFile '~/.ssh/known_hosts' -> '/home/avallejo/.ssh/kno
wn_hosts' 
debug3: expanded UserKnownHostsFile '~/.ssh/known_hosts2' -> '/home/avallejo/.ssh/kn
own_hosts2' 
debug3: ssh_connect_direct: entering 
debug1: Connecting to 192.168.0.150 [192.168.0.150] port 22. 
debug3: set_sock_tos: set socket 3 IP_TOS 0x10 
debug1: Connection established. 
debug1: identity file /home/avallejo/.ssh/id_rsa type 0 
debug1: identity file /home/avallejo/.ssh/id_rsa-cert type -1 
debug1: identity file /home/avallejo/.ssh/id_ecdsa type -1 
debug1: identity file /home/avallejo/.ssh/id_ecdsa-cert type -1 
debug1: identity file /home/avallejo/.ssh/id_ecdsa_sk type -1 
debug1: identity file /home/avallejo/.ssh/id_ecdsa_sk-cert type -1 
debug1: identity file /home/avallejo/.ssh/id_ed25519 type -1 
debug1: identity file /home/avallejo/.ssh/id_ed25519-cert type -1 
debug1: identity file /home/avallejo/.ssh/id_ed25519_sk type -1 
debug1: identity file /home/avallejo/.ssh/id_ed25519_sk-cert type -1 
debug1: identity file /home/avallejo/.ssh/id_xmss type -1 
debug1: identity file /home/avallejo/.ssh/id_xmss-cert type -1 
debug1: identity file /home/avallejo/.ssh/id_dsa type -1 
debug1: identity file /home/avallejo/.ssh/id_dsa-cert type -1 
debug1: Local version string SSH-2.0-OpenSSH_9.0p1 Ubuntu-1ubuntu8.4 
debug1: Remote protocol version 2.0, remote software version OpenSSH_9.3 
debug1: compat_banner: match: OpenSSH_9.3 pat OpenSSH* compat 0x04000000 
debug2: fd 3 setting O_NONBLOCK 
debug1: Authenticating to 192.168.0.150:22 as 'avs' 
debug3: record_hostkey: found key type ED25519 in file /home/avallejo/.ssh/known_hos
ts:1 
debug3: load_hostkeys_file: loaded 1 keys from 192.168.0.150 
debug1: load_hostkeys: fopen /home/avallejo/.ssh/known_hosts2: No such file or direc
tory 
debug1: load_hostkeys: fopen /etc/ssh/ssh_known_hosts: No such file or directory 
debug1: load_hostkeys: fopen /etc/ssh/ssh_known_hosts2: No such file or directory 
debug3: order_hostkeyalgs: have matching best-preference key type ssh-ed25519-cert-v
[EMAIL="01@openssh.com"]01@openssh.com[/EMAIL], using HostkeyAlgorithms verbatim 
debug3: send packet: type 20 
debug1: SSH2_MSG_KEXINIT sent 
debug3: receive packet: type 20 
debug1: SSH2_MSG_KEXINIT received 
debug2: local client KEXINIT proposal 
debug2: KEX algorithms: [EMAIL="sntrup761x25519-sha512@openssh.com"]sntrup761x25519-sha512@openssh.com[/EMAIL],curve25519-sha256,curve25
[EMAIL="519-sha256@libssh.org"]519-sha256@libssh.org[/EMAIL],ecdh-sha2-nistp256,ecdh-sha2-nistp384,ecdh-sha2-nistp521,diffi
e-hellman-group-exchange-sha256,diffie-hellman-group16-sha512,diffie-hellman-group18
-sha512,diffie-hellman-group14-sha256,ext-info-c 
debug2: host key algorithms: [EMAIL="ssh-ed25519-cert-v01@openssh.com"]ssh-ed25519-cert-v01@openssh.com[/EMAIL],ecdsa-sha2-nistp256-ce
[email]rt-v01@openssh.com,ecdsa-sha2-nistp384-cert-v01@openssh.com[/email],ecdsa-sha2-nistp521-cert
[email]-v01@openssh.com,sk-ssh-ed25519-cert-v01@openssh.com[/email],sk-ecdsa-sha2-nistp256-cert-v01
@openssh.com,rsa-sha2-512-cert-v01@openssh.com,rsa-sha2-256-cert-v01@openssh.com,ssh
-ed25519,ecdsa-sha2-nistp256,ecdsa-sha2-nistp384,ecdsa-sha2-nistp521,sk-ssh-ed25519@
openssh.com,sk-ecdsa-sha2-nistp256@openssh.com,rsa-sha2-512,rsa-sha2-256 
debug2: ciphers ctos: [EMAIL="chacha20-poly1305@openssh.com"]chacha20-poly1305@openssh.com[/EMAIL],aes128-ctr,aes192-ctr,aes256-ctr
,aes128-gcm@openssh.com,aes256-gcm@openssh.com 
debug2: ciphers stoc: [EMAIL="chacha20-poly1305@openssh.com"]chacha20-poly1305@openssh.com[/EMAIL],aes128-ctr,aes192-ctr,aes256-ctr
,aes128-gcm@openssh.com,aes256-gcm@openssh.com 
debug2: MACs ctos: [email]umac-64-etm@openssh.com,umac-128-etm@openssh.com[/email],hmac-sha2-256-et
[email]m@openssh.com,hmac-sha2-512-etm@openssh.com,hmac-sha1-etm@openssh.com[/email],umac-64@openss
h.com,umac-128@openssh.com,hmac-sha2-256,hmac-sha2-512,hmac-sha1 
debug2: MACs stoc: [email]umac-64-etm@openssh.com,umac-128-etm@openssh.com[/email],hmac-sha2-256-et
[email]m@openssh.com,hmac-sha2-512-etm@openssh.com,hmac-sha1-etm@openssh.com[/email],umac-64@openss
h.com,umac-128@openssh.com,hmac-sha2-256,hmac-sha2-512,hmac-sha1 
debug2: compression ctos: none,zlib@openssh.com,zlib 
debug2: compression stoc: none,zlib@openssh.com,zlib 
debug2: languages ctos:  
debug2: languages stoc:  
debug2: first_kex_follows 0  
debug2: reserved 0  
debug2: peer server KEXINIT proposal 
debug2: KEX algorithms: [EMAIL="sntrup761x25519-sha512@openssh.com"]sntrup761x25519-sha512@openssh.com[/EMAIL],curve25519-sha256,curve25
[EMAIL="519-sha256@libssh.org"]519-sha256@libssh.org[/EMAIL],ecdh-sha2-nistp256,ecdh-sha2-nistp384,ecdh-sha2-nistp521,diffi
e-hellman-group-exchange-sha256,diffie-hellman-group16-sha512,diffie-hellman-group18
-sha512,diffie-hellman-group14-sha256 
debug2: host key algorithms: rsa-sha2-512,rsa-sha2-256,ecdsa-sha2-nistp256,ssh-ed255
19 
debug2: ciphers ctos: [EMAIL="chacha20-poly1305@openssh.com"]chacha20-poly1305@openssh.com[/EMAIL],aes128-ctr,aes192-ctr,aes256-ctr
,aes128-gcm@openssh.com,aes256-gcm@openssh.com 
debug2: ciphers stoc: [EMAIL="chacha20-poly1305@openssh.com"]chacha20-poly1305@openssh.com[/EMAIL],aes128-ctr,aes192-ctr,aes256-ctr
,aes128-gcm@openssh.com,aes256-gcm@openssh.com 
debug2: MACs ctos: [email]umac-64-etm@openssh.com,umac-128-etm@openssh.com[/email],hmac-sha2-256-et
[email]m@openssh.com,hmac-sha2-512-etm@openssh.com,hmac-sha1-etm@openssh.com[/email],umac-64@openss
h.com,umac-128@openssh.com,hmac-sha2-256,hmac-sha2-512,hmac-sha1 
debug2: MACs stoc: [email]umac-64-etm@openssh.com,umac-128-etm@openssh.com[/email],hmac-sha2-256-et
[email]m@openssh.com,hmac-sha2-512-etm@openssh.com,hmac-sha1-etm@openssh.com[/email],umac-64@openss
h.com,umac-128@openssh.com,hmac-sha2-256,hmac-sha2-512,hmac-sha1 
debug2: compression ctos: none,zlib@openssh.com 
debug2: compression stoc: none,zlib@openssh.com 
debug2: languages ctos:  
debug2: languages stoc:  
debug2: first_kex_follows 0  
debug2: reserved 0  
debug1: kex: algorithm: [EMAIL="sntrup761x25519-sha512@openssh.com"]sntrup761x25519-sha512@openssh.com[/EMAIL] 
debug1: kex: host key algorithm: ssh-ed25519 
debug1: kex: server->client cipher: [EMAIL="chacha20-poly1305@openssh.com"]chacha20-poly1305@openssh.com[/EMAIL] MAC: <implicit> co
mpression: none 
debug1: kex: client->server cipher: [EMAIL="chacha20-poly1305@openssh.com"]chacha20-poly1305@openssh.com[/EMAIL] MAC: <implicit> co
mpression: none 
debug3: send packet: type 30 
debug1: expecting SSH2_MSG_KEX_ECDH_REPLY 
debug3: receive packet: type 31 
debug1: SSH2_MSG_KEX_ECDH_REPLY received 
debug1: Server host key: ssh-ed25519 SHA256:nZs+LYgnsE4MYqqGU1yMVMj622etdpgwBkcNligz
dyE 
debug3: record_hostkey: found key type ED25519 in file /home/avallejo/.ssh/known_hos
ts:1 
debug3: load_hostkeys_file: loaded 1 keys from 192.168.0.150 
debug1: load_hostkeys: fopen /home/avallejo/.ssh/known_hosts2: No such file or direc
tory 
debug1: load_hostkeys: fopen /etc/ssh/ssh_known_hosts: No such file or directory 
debug1: load_hostkeys: fopen /etc/ssh/ssh_known_hosts2: No such file or directory 
debug1: Host '192.168.0.150' is known and matches the ED25519 host key. 
debug1: Found key in /home/avallejo/.ssh/known_hosts:1 
debug3: send packet: type 21 
debug2: ssh_set_newkeys: mode 1 
debug1: rekey out after 134217728 blocks 
debug1: SSH2_MSG_NEWKEYS sent 
debug1: expecting SSH2_MSG_NEWKEYS 
debug3: receive packet: type 21 
debug1: SSH2_MSG_NEWKEYS received 
debug2: ssh_set_newkeys: mode 0 
debug1: rekey in after 134217728 blocks 
debug1: get_agent_identities: bound agent to hostkey 
debug1: get_agent_identities: ssh_fetch_identitylist: agent contains no identities 
debug1: Will attempt key: /home/avallejo/.ssh/id_rsa RSA SHA256:rmkc3VqG4V3fZkd0+MLb
m10SdcEG5eVFtcM0h17psQA 
debug1: Will attempt key: /home/avallejo/.ssh/id_ecdsa  
debug1: Will attempt key: /home/avallejo/.ssh/id_ecdsa_sk  
debug1: Will attempt key: /home/avallejo/.ssh/id_ed25519  
debug1: Will attempt key: /home/avallejo/.ssh/id_ed25519_sk  
debug1: Will attempt key: /home/avallejo/.ssh/id_xmss  
debug1: Will attempt key: /home/avallejo/.ssh/id_dsa  
debug2: pubkey_prepare: done 
debug3: send packet: type 5 
debug3: receive packet: type 7 
debug1: SSH2_MSG_EXT_INFO received 
debug1: kex_input_ext_info: server-sig-algs=<ssh-ed25519,sk-ssh-ed25519@openssh.com,
ecdsa-sha2-nistp256,ecdsa-sha2-nistp384,ecdsa-sha2-nistp521,sk-ecdsa-sha2-nistp256@o
penssh.com,webauthn-sk-ecdsa-sha2-nistp256@openssh.com,ssh-dss,ssh-rsa,rsa-sha2-256,
rsa-sha2-512> 
debug1: kex_input_ext_info: [EMAIL="publickey-hostbound@openssh.com"]publickey-hostbound@openssh.com[/EMAIL]=<0> 
debug3: receive packet: type 6 
debug2: service_accept: ssh-userauth 
debug1: SSH2_MSG_SERVICE_ACCEPT received 
debug3: send packet: type 50 
debug3: receive packet: type 51 
debug1: Authentications that can continue: publickey,password,keyboard-interactive 
debug3: start over, passed a different list publickey,password,keyboard-interactive 
debug3: preferred gssapi-with-mic,publickey,keyboard-interactive,password 
debug3: authmethod_lookup publickey 
debug3: remaining preferred: keyboard-interactive,password 
debug3: authmethod_is_enabled publickey 
debug1: Next authentication method: publickey 
debug1: Offering public key: /home/avallejo/.ssh/id_rsa RSA SHA256:rmkc3VqG4V3fZkd0+
MLbm10SdcEG5eVFtcM0h17psQA 
debug3: send packet: type 50 
debug2: we sent a publickey packet, wait for reply 
debug3: receive packet: type 51 
debug1: Authentications that can continue: publickey,password,keyboard-interactive 
debug1: Trying private key: /home/avallejo/.ssh/id_ecdsa 
debug3: no such identity: /home/avallejo/.ssh/id_ecdsa: No such file or directory 
debug1: Trying private key: /home/avallejo/.ssh/id_ecdsa_sk 
debug3: no such identity: /home/avallejo/.ssh/id_ecdsa_sk: No such file or directory 
debug1: Trying private key: /home/avallejo/.ssh/id_ed25519 
debug3: no such identity: /home/avallejo/.ssh/id_ed25519: No such file or directory 
debug1: Trying private key: /home/avallejo/.ssh/id_ed25519_sk 
debug3: no such identity: /home/avallejo/.ssh/id_ed25519_sk: No such file or directo
ry 
debug1: Trying private key: /home/avallejo/.ssh/id_xmss 
debug3: no such identity: /home/avallejo/.ssh/id_xmss: No such file or directory 
debug1: Trying private key: /home/avallejo/.ssh/id_dsa 
debug3: no such identity: /home/avallejo/.ssh/id_dsa: No such file or directory 
debug2: we did not send a packet, disable method 
debug3: authmethod_lookup keyboard-interactive 
debug3: remaining preferred: password 
debug3: authmethod_is_enabled keyboard-interactive 
debug1: Next authentication method: keyboard-interactive 
debug2: userauth_kbdint 
debug3: send packet: type 50 
debug2: we sent a keyboard-interactive packet, wait for reply 
debug3: receive packet: type 60 
debug2: input_userauth_info_req: entering 
debug2: input_userauth_info_req: num_prompts 1 
(avs@192.168.0.150) Password:  
debug3: send packet: type 61 
debug3: receive packet: type 51 
debug1: Authentications that can continue: publickey,password,keyboard-interactive 
debug2: userauth_kbdint 
debug3: send packet: type 50 
debug2: we sent a keyboard-interactive packet, wait for reply 
debug3: receive packet: type 60 
debug2: input_userauth_info_req: entering 
debug2: input_userauth_info_req: num_prompts 1 
(avs@192.168.0.150) Password: 

When I enter the password, it's not accepted...

[/FONT]

---

### Post by avsilva on 2023-08-10
And then when I do the same as root...(I'm in my home network, no security fears). It&#347; a home backup server.

[FONT=monospace][COLOR=#54ff54]**avallejo@andre-xps**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$  ssh -vvv root@192.168.0.150 [/COLOR]
OpenSSH_9.0p1 Ubuntu-1ubuntu8.4, OpenSSL 3.0.8 7 Feb 2023 
debug1: Reading configuration data /etc/ssh/ssh_config 
debug1: /etc/ssh/ssh_config line 19: include /etc/ssh/ssh_config.d/*.conf matched no
 files 
debug1: /etc/ssh/ssh_config line 21: Applying options for * 
debug2: resolve_canonicalize: hostname 192.168.0.150 is address 
debug3: expanded UserKnownHostsFile '~/.ssh/known_hosts' -> '/home/avallejo/.ssh/kno
wn_hosts' 
debug3: expanded UserKnownHostsFile '~/.ssh/known_hosts2' -> '/home/avallejo/.ssh/kn
own_hosts2' 
debug3: ssh_connect_direct: entering 
debug1: Connecting to 192.168.0.150 [192.168.0.150] port 22. 
debug3: set_sock_tos: set socket 3 IP_TOS 0x10 
debug1: Connection established. 
debug1: identity file /home/avallejo/.ssh/id_rsa type 0 
debug1: identity file /home/avallejo/.ssh/id_rsa-cert type -1 
debug1: identity file /home/avallejo/.ssh/id_ecdsa type -1 
debug1: identity file /home/avallejo/.ssh/id_ecdsa-cert type -1 
debug1: identity file /home/avallejo/.ssh/id_ecdsa_sk type -1 
debug1: identity file /home/avallejo/.ssh/id_ecdsa_sk-cert type -1 
debug1: identity file /home/avallejo/.ssh/id_ed25519 type -1 
debug1: identity file /home/avallejo/.ssh/id_ed25519-cert type -1 
debug1: identity file /home/avallejo/.ssh/id_ed25519_sk type -1 
debug1: identity file /home/avallejo/.ssh/id_ed25519_sk-cert type -1 
debug1: identity file /home/avallejo/.ssh/id_xmss type -1 
debug1: identity file /home/avallejo/.ssh/id_xmss-cert type -1 
debug1: identity file /home/avallejo/.ssh/id_dsa type -1 
debug1: identity file /home/avallejo/.ssh/id_dsa-cert type -1 
debug1: Local version string SSH-2.0-OpenSSH_9.0p1 Ubuntu-1ubuntu8.4 
debug1: Remote protocol version 2.0, remote software version OpenSSH_9.3 
debug1: compat_banner: match: OpenSSH_9.3 pat OpenSSH* compat 0x04000000 
debug2: fd 3 setting O_NONBLOCK 
debug1: Authenticating to 192.168.0.150:22 as 'root' 
debug3: record_hostkey: found key type ED25519 in file /home/avallejo/.ssh/known_hos
ts:1 
debug3: load_hostkeys_file: loaded 1 keys from 192.168.0.150 
debug1: load_hostkeys: fopen /home/avallejo/.ssh/known_hosts2: No such file or direc
tory 
debug1: load_hostkeys: fopen /etc/ssh/ssh_known_hosts: No such file or directory 
debug1: load_hostkeys: fopen /etc/ssh/ssh_known_hosts2: No such file or directory 
debug3: order_hostkeyalgs: have matching best-preference key type ssh-ed25519-cert-v
[email]01@openssh.com[/email], using HostkeyAlgorithms verbatim 
debug3: send packet: type 20 
debug1: SSH2_MSG_KEXINIT sent 
debug3: receive packet: type 20 
debug1: SSH2_MSG_KEXINIT received 
debug2: local client KEXINIT proposal 
debug2: KEX algorithms: [email]sntrup761x25519-sha512@openssh.com[/email],curve25519-sha256,curve25
[email]519-sha256@libssh.org[/email],ecdh-sha2-nistp256,ecdh-sha2-nistp384,ecdh-sha2-nistp521,diffi
e-hellman-group-exchange-sha256,diffie-hellman-group16-sha512,diffie-hellman-group18
-sha512,diffie-hellman-group14-sha256,ext-info-c 
debug2: host key algorithms: [email]ssh-ed25519-cert-v01@openssh.com[/email],ecdsa-sha2-nistp256-ce
[email]rt-v01@openssh.com,ecdsa-sha2-nistp384-cert-v01@openssh.com[/email],ecdsa-sha2-nistp521-cert
[email]-v01@openssh.com,sk-ssh-ed25519-cert-v01@openssh.com[/email],sk-ecdsa-sha2-nistp256-cert-v01
@openssh.com,rsa-sha2-512-cert-v01@openssh.com,rsa-sha2-256-cert-v01@openssh.com,ssh
-ed25519,ecdsa-sha2-nistp256,ecdsa-sha2-nistp384,ecdsa-sha2-nistp521,sk-ssh-ed25519@
openssh.com,sk-ecdsa-sha2-nistp256@openssh.com,rsa-sha2-512,rsa-sha2-256 
debug2: ciphers ctos: [email]chacha20-poly1305@openssh.com[/email],aes128-ctr,aes192-ctr,aes256-ctr
,aes128-gcm@openssh.com,aes256-gcm@openssh.com 
debug2: ciphers stoc: [email]chacha20-poly1305@openssh.com[/email],aes128-ctr,aes192-ctr,aes256-ctr
,aes128-gcm@openssh.com,aes256-gcm@openssh.com 
debug2: MACs ctos: [email]umac-64-etm@openssh.com,umac-128-etm@openssh.com[/email],hmac-sha2-256-et
[email]m@openssh.com,hmac-sha2-512-etm@openssh.com,hmac-sha1-etm@openssh.com[/email],umac-64@openss
h.com,umac-128@openssh.com,hmac-sha2-256,hmac-sha2-512,hmac-sha1 
debug2: MACs stoc: [email]umac-64-etm@openssh.com,umac-128-etm@openssh.com[/email],hmac-sha2-256-et
[email]m@openssh.com,hmac-sha2-512-etm@openssh.com,hmac-sha1-etm@openssh.com[/email],umac-64@openss
h.com,umac-128@openssh.com,hmac-sha2-256,hmac-sha2-512,hmac-sha1 
debug2: compression ctos: none,zlib@openssh.com,zlib 
debug2: compression stoc: none,zlib@openssh.com,zlib 
debug2: languages ctos:  
debug2: languages stoc:  
debug2: first_kex_follows 0  
debug2: reserved 0  
debug2: peer server KEXINIT proposal 
debug2: KEX algorithms: [email]sntrup761x25519-sha512@openssh.com[/email],curve25519-sha256,curve25
[email]519-sha256@libssh.org[/email],ecdh-sha2-nistp256,ecdh-sha2-nistp384,ecdh-sha2-nistp521,diffi
e-hellman-group-exchange-sha256,diffie-hellman-group16-sha512,diffie-hellman-group18
-sha512,diffie-hellman-group14-sha256 
debug2: host key algorithms: rsa-sha2-512,rsa-sha2-256,ecdsa-sha2-nistp256,ssh-ed255
19 
debug2: ciphers ctos: [email]chacha20-poly1305@openssh.com[/email],aes128-ctr,aes192-ctr,aes256-ctr
,aes128-gcm@openssh.com,aes256-gcm@openssh.com 
debug2: ciphers stoc: [email]chacha20-poly1305@openssh.com[/email],aes128-ctr,aes192-ctr,aes256-ctr
,aes128-gcm@openssh.com,aes256-gcm@openssh.com 
debug2: MACs ctos: [email]umac-64-etm@openssh.com,umac-128-etm@openssh.com[/email],hmac-sha2-256-et
[email]m@openssh.com,hmac-sha2-512-etm@openssh.com,hmac-sha1-etm@openssh.com[/email],umac-64@openss
h.com,umac-128@openssh.com,hmac-sha2-256,hmac-sha2-512,hmac-sha1 
debug2: MACs stoc: [email]umac-64-etm@openssh.com,umac-128-etm@openssh.com[/email],hmac-sha2-256-et
[email]m@openssh.com,hmac-sha2-512-etm@openssh.com,hmac-sha1-etm@openssh.com[/email],umac-64@openss
h.com,umac-128@openssh.com,hmac-sha2-256,hmac-sha2-512,hmac-sha1 
debug2: compression ctos: none,zlib@openssh.com 
debug2: compression stoc: none,zlib@openssh.com 
debug2: languages ctos:  
debug2: languages stoc:  
debug2: first_kex_follows 0  
debug2: reserved 0  
debug1: kex: algorithm: [email]sntrup761x25519-sha512@openssh.com[/email] 
debug1: kex: host key algorithm: ssh-ed25519 
debug1: kex: server->client cipher: [email]chacha20-poly1305@openssh.com[/email] MAC: <implicit> co
mpression: none 
debug1: kex: client->server cipher: [email]chacha20-poly1305@openssh.com[/email] MAC: <implicit> co
mpression: none 
debug3: send packet: type 30 
debug1: expecting SSH2_MSG_KEX_ECDH_REPLY 
debug3: receive packet: type 31 
debug1: SSH2_MSG_KEX_ECDH_REPLY received 
debug1: Server host key: ssh-ed25519 SHA256:nZs+LYgnsE4MYqqGU1yMVMj622etdpgwBkcNligz
dyE 
debug3: record_hostkey: found key type ED25519 in file /home/avallejo/.ssh/known_hos
ts:1 
debug3: load_hostkeys_file: loaded 1 keys from 192.168.0.150 
debug1: load_hostkeys: fopen /home/avallejo/.ssh/known_hosts2: No such file or direc
tory 
debug1: load_hostkeys: fopen /etc/ssh/ssh_known_hosts: No such file or directory 
debug1: load_hostkeys: fopen /etc/ssh/ssh_known_hosts2: No such file or directory 
debug1: Host '192.168.0.150' is known and matches the ED25519 host key. 
debug1: Found key in /home/avallejo/.ssh/known_hosts:1 
debug3: send packet: type 21 
debug2: ssh_set_newkeys: mode 1 
debug1: rekey out after 134217728 blocks 
debug1: SSH2_MSG_NEWKEYS sent 
debug1: expecting SSH2_MSG_NEWKEYS 
debug3: receive packet: type 21 
debug1: SSH2_MSG_NEWKEYS received 
debug2: ssh_set_newkeys: mode 0 
debug1: rekey in after 134217728 blocks 
debug1: get_agent_identities: bound agent to hostkey 
debug1: get_agent_identities: ssh_fetch_identitylist: agent contains no identities 
debug1: Will attempt key: /home/avallejo/.ssh/id_rsa RSA SHA256:rmkc3VqG4V3fZkd0+MLb
m10SdcEG5eVFtcM0h17psQA 
debug1: Will attempt key: /home/avallejo/.ssh/id_ecdsa  
debug1: Will attempt key: /home/avallejo/.ssh/id_ecdsa_sk  
debug1: Will attempt key: /home/avallejo/.ssh/id_ed25519  
debug1: Will attempt key: /home/avallejo/.ssh/id_ed25519_sk  
debug1: Will attempt key: /home/avallejo/.ssh/id_xmss  
debug1: Will attempt key: /home/avallejo/.ssh/id_dsa  
debug2: pubkey_prepare: done 
debug3: send packet: type 5 
debug3: receive packet: type 7 
debug1: SSH2_MSG_EXT_INFO received 
debug1: kex_input_ext_info: server-sig-algs=<ssh-ed25519,sk-ssh-ed25519@openssh.com,
ecdsa-sha2-nistp256,ecdsa-sha2-nistp384,ecdsa-sha2-nistp521,sk-ecdsa-sha2-nistp256@o
penssh.com,webauthn-sk-ecdsa-sha2-nistp256@openssh.com,ssh-dss,ssh-rsa,rsa-sha2-256,
rsa-sha2-512> 
debug1: kex_input_ext_info: [email]publickey-hostbound@openssh.com[/email]=<0> 
debug3: receive packet: type 6 
debug2: service_accept: ssh-userauth 
debug1: SSH2_MSG_SERVICE_ACCEPT received 
debug3: send packet: type 50 
debug3: receive packet: type 51 
debug1: Authentications that can continue: publickey,password,keyboard-interactive 
debug3: start over, passed a different list publickey,password,keyboard-interactive 
debug3: preferred gssapi-with-mic,publickey,keyboard-interactive,password 
debug3: authmethod_lookup publickey 
debug3: remaining preferred: keyboard-interactive,password 
debug3: authmethod_is_enabled publickey 
debug1: Next authentication method: publickey 
debug1: Offering public key: /home/avallejo/.ssh/id_rsa RSA SHA256:rmkc3VqG4V3fZkd0+
MLbm10SdcEG5eVFtcM0h17psQA 
debug3: send packet: type 50 
debug2: we sent a publickey packet, wait for reply 
debug3: receive packet: type 60 
debug1: Server accepts key: /home/avallejo/.ssh/id_rsa RSA SHA256:rmkc3VqG4V3fZkd0+M
Lbm10SdcEG5eVFtcM0h17psQA 
debug3: sign_and_send_pubkey: using [email]publickey-hostbound-v00@openssh.com[/email] with RSA SHA
256:rmkc3VqG4V3fZkd0+MLbm10SdcEG5eVFtcM0h17psQA 
debug3: sign_and_send_pubkey: signing using rsa-sha2-512 SHA256:rmkc3VqG4V3fZkd0+MLb
m10SdcEG5eVFtcM0h17psQA 
debug3: send packet: type 50 
debug3: receive packet: type 52 
Authenticated to 192.168.0.150 ([192.168.0.150]:22) using "publickey". 
debug1: channel 0: new [client-session] 
debug3: ssh_session2_open: channel_new: 0 
debug2: channel 0: send open 
debug3: send packet: type 90 
debug1: Requesting [email]no-more-sessions@openssh.com[/email] 
debug3: send packet: type 80 
debug1: Entering interactive session. 
debug1: pledge: filesystem 
debug3: receive packet: type 80 
debug1: client_input_global_request: rtype [email]hostkeys-00@openssh.com[/email] want_reply 0 
debug3: client_input_hostkeys: received RSA key SHA256:9Ub7VXAvf11S3mXMmwBIKRckepTPC
EV9VQ/0Qzm0J5o 
debug3: client_input_hostkeys: received ECDSA key SHA256:bjeAzoiCORfXsbgyiLLgaAL8A0P
DjjRC8ui+0DClC7o 
debug3: client_input_hostkeys: received ED25519 key SHA256:nZs+LYgnsE4MYqqGU1yMVMj62
2etdpgwBkcNligzdyE 
debug1: client_input_hostkeys: searching /home/avallejo/.ssh/known_hosts for 192.168
.0.150 / (none) 
debug3: hostkeys_foreach: reading file "/home/avallejo/.ssh/known_hosts" 
debug3: hostkeys_find: found ssh-ed25519 key at /home/avallejo/.ssh/known_hosts:1 
debug3: hostkeys_find: found ssh-ed25519 key under different name/addr at /home/aval
lejo/.ssh/known_hosts:2 
debug1: client_input_hostkeys: searching /home/avallejo/.ssh/known_hosts2 for 192.16
8.0.150 / (none) 
debug1: client_input_hostkeys: hostkeys file /home/avallejo/.ssh/known_hosts2 does n
ot exist 
debug3: client_input_hostkeys: 3 server keys: 2 new, 18446744073709551615 retained, 
2 incomplete match. 0 to remove 
debug1: client_input_hostkeys: host key found matching a different name/address, ski
pping UserKnownHostsFile update 
debug3: receive packet: type 4 
debug1: Remote: /root/.ssh/authorized_keys:1: key options: agent-forwarding port-for
warding pty user-rc x11-forwarding 
debug3: receive packet: type 4 
debug1: Remote: /root/.ssh/authorized_keys:1: key options: agent-forwarding port-for
warding pty user-rc x11-forwarding 
debug3: receive packet: type 91 
debug2: channel_input_open_confirmation: channel 0: callback start 
debug2: fd 3 setting TCP_NODELAY 
debug3: set_sock_tos: set socket 3 IP_TOS 0x10 
debug2: client_session2_setup: id 0 
debug2: channel 0: request pty-req confirm 1 
debug3: send packet: type 98 
debug1: Sending environment. 
debug3: Ignored env SHELL 
debug3: Ignored env WINDOWID 
debug3: Ignored env QT_ACCESSIBILITY 
debug3: Ignored env COLORTERM 
debug3: Ignored env XDG_CONFIG_DIRS 
debug3: Ignored env XDG_SESSION_PATH 
debug3: Ignored env GTK_IM_MODULE 
debug3: Ignored env LANGUAGE 
debug3: Ignored env MANDATORY_PATH 
debug1: channel 0: setting env LC_ADDRESS = "pt_BR.UTF-8" 
debug2: channel 0: request env confirm 0 
debug3: send packet: type 98 
debug1: channel 0: setting env LC_NAME = "pt_BR.UTF-8" 
debug2: channel 0: request env confirm 0 
debug3: send packet: type 98 
debug3: Ignored env SSH_AUTH_SOCK 
debug3: Ignored env SHELL_SESSION_ID 
debug3: Ignored env XMODIFIERS 
debug3: Ignored env DESKTOP_SESSION 
debug1: channel 0: setting env LC_MONETARY = "pt_BR.UTF-8" 
debug2: channel 0: request env confirm 0 
debug3: send packet: type 98 
debug3: Ignored env SSH_AGENT_PID 
debug3: Ignored env GTK_RC_FILES 
debug3: Ignored env XCURSOR_SIZE 
debug3: Ignored env XDG_SEAT 
debug3: Ignored env PWD 
debug3: Ignored env XDG_SESSION_DESKTOP 
debug3: Ignored env LOGNAME 
debug3: Ignored env XDG_SESSION_TYPE 
debug3: Ignored env GPG_AGENT_INFO 
debug3: Ignored env SYSTEMD_EXEC_PID 
debug3: Ignored env XAUTHORITY 
debug3: Ignored env GTK2_RC_FILES 
debug3: Ignored env HOME 
debug3: Ignored env IM_CONFIG_PHASE 
debug1: channel 0: setting env LC_PAPER = "pt_BR.UTF-8" 
debug2: channel 0: request env confirm 0 
debug3: send packet: type 98 
debug1: channel 0: setting env LANG = "pt_BR.UTF-8" 
debug2: channel 0: request env confirm 0 
debug3: send packet: type 98 
debug3: Ignored env LS_COLORS 
debug3: Ignored env XDG_CURRENT_DESKTOP 
debug3: Ignored env KONSOLE_DBUS_SERVICE 
debug3: Ignored env KONSOLE_DBUS_SESSION 
debug3: Ignored env PROFILEHOME 
debug3: Ignored env XDG_SEAT_PATH 
debug3: Ignored env QTWEBENGINE_DICTIONARIES_PATH 
debug3: Ignored env INVOCATION_ID 
debug3: Ignored env KONSOLE_VERSION 
debug3: Ignored env MANAGERPID 
debug3: Ignored env CLUTTER_IM_MODULE 
debug3: Ignored env KDE_SESSION_UID 
debug3: Ignored env SDL_IM_MODULE 
debug3: Ignored env PIPEWIRE_QUANTUM 
debug3: Ignored env LESSCLOSE 
debug3: Ignored env XDG_SESSION_CLASS 
debug3: Ignored env TERM 
debug1: channel 0: setting env LC_IDENTIFICATION = "pt_BR.UTF-8" 
debug2: channel 0: request env confirm 0 
debug3: send packet: type 98 
debug3: Ignored env DEFAULTS_PATH 
debug3: Ignored env LESSOPEN 
debug3: Ignored env USER 
debug3: Ignored env COLORFGBG 
debug3: Ignored env KDE_SESSION_VERSION 
debug3: Ignored env PAM_KWALLET5_LOGIN 
debug3: Ignored env DISPLAY 
debug3: Ignored env SHLVL 
debug1: channel 0: setting env LC_TELEPHONE = "pt_BR.UTF-8" 
debug2: channel 0: request env confirm 0 
debug3: send packet: type 98 
debug3: Ignored env QT_IM_MODULE 
debug1: channel 0: setting env LC_MEASUREMENT = "pt_BR.UTF-8" 
debug2: channel 0: request env confirm 0 
debug3: send packet: type 98 
debug3: Ignored env XDG_VTNR 
debug3: Ignored env XDG_SESSION_ID 
debug3: Ignored env PAPERSIZE 
debug1: channel 0: setting env LC_CTYPE = "pt_BR.UTF-8" 
debug2: channel 0: request env confirm 0 
debug3: send packet: type 98 
debug3: Ignored env XDG_RUNTIME_DIR 
debug3: Ignored env DEBUGINFOD_URLS 
debug1: channel 0: setting env LC_TIME = "pt_BR.UTF-8" 
debug2: channel 0: request env confirm 0 
debug3: send packet: type 98 
debug3: Ignored env QT_AUTO_SCREEN_SCALE_FACTOR 
debug3: Ignored env JOURNAL_STREAM 
debug3: Ignored env XCURSOR_THEME 
debug3: Ignored env XDG_DATA_DIRS 
debug3: Ignored env KDE_FULL_SESSION 
debug3: Ignored env PATH 
debug3: Ignored env DBUS_SESSION_BUS_ADDRESS 
debug3: Ignored env KDE_APPLICATIONS_AS_SCOPE 
debug1: channel 0: setting env LC_NUMERIC = "pt_BR.UTF-8" 
debug2: channel 0: request env confirm 0 
debug3: send packet: type 98 
debug3: Ignored env KONSOLE_DBUS_WINDOW 
debug3: Ignored env _ 
debug2: channel 0: request shell confirm 1 
debug3: send packet: type 98 
debug2: channel_input_open_confirmation: channel 0: callback done 
debug2: channel 0: open confirm rwindow 0 rmax 32768 
debug3: receive packet: type 99 
debug2: channel_input_status_confirm: type 99 id 0 
debug2: PTY allocation request accepted on channel 0 
debug2: channel 0: rcvd adjust 2097152 
debug3: receive packet: type 99 
debug2: channel_input_status_confirm: type 99 id 0 
debug2: shell request accepted on channel 0 
Last login: Thu Aug 10 07:09:26 2023 from 192.168.0.102 
Linux 6.1.36-Unraid. 
[COLOR=#54ff54]**root@Calango**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]# [/COLOR]


[/FONT]

---

### Post by TheFu on 2023-08-10
Looks to me like you are presenting an RSA key when the public key on the other side is ed25519. 
Forget about using sudo or root. That isn't helping and seems to just confuse you.

So, start over.
On the remote system, delete ~/.ssh
On the local system, delete ~/.ssh

On the local system, create a new ed25519 key.  
```
   $ ssh-keygen -t ed25519
```
then push that key to the remote system.
```
   $ ssh-copy-id -i ~/.ssh/id_ed25519.pub     username@remote
```

ssh is picky about owners, groups, permissions. DON'T SCREW WITH THEM.  Those 2 command is all you need, assuming the "ssh" metapackage was installed on both the client and remote server.

Test the connection, 
```
   $ ssh  username@remote
```

You'll get in.  If not, then we need to delve into things you've changed in the system files or how old the OS might be.  For at least the last 5 yrs, ed25519 keys have been well supported.  If you need to use RSA keys for some reason, be certain they are 4K in size.

If this doesn't work, probably the easiest answer is to remove all ssh programs and settings (that means use (apt purge ssh) from both systems, then do a fresh install on both system:
```
$ sudo apt install ssh fail2ban
```

I'll assume you have console access to both systems.

---

### Post by avsilva on 2023-08-10
> **TheFu said:**
> Looks to me like you are presenting an RSA key when the public key on the other side is ed25519. 
Forget about using sudo or root. That isn't helping and seems to just confuse you.

So, start over.
On the remote system, delete ~/.ssh
On the local system, delete ~/.ssh
I'll assume you have console access to both systems.

Thanks a lot for taking the time to look into it...I&#314;l be away from my machines for the next days, so I'll work on your directions early next week and get back with results here. 
André

---

