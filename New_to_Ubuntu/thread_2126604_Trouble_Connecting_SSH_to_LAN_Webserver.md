---
title: "Trouble Connecting SSH to LAN Webserver"
date: 2013-03-17
forum: New to Ubuntu
---

### Post by BEEDO on 2013-03-17
I want to use SSH to connect to a Ubuntu Server that I just set up on my LAN. Originally I just wanted to play around with Moodle to see how I liked it. To use Moodle, a LAMP stack will work well, so I set up Ubuntu Server with LAMP on an old laptop, installing SSH later, as an afterthought. I have Ubuntu Studio on my regular laptop and desktop all connected via wireless router. I want to use the regular laptop to generate files for the server and transfer them using SSH and its utilities and then access the server as a regular user. I've never used SSH and have very little experience with LAMP, MySQL or PHP so my progress has been less than lightning fast, with lots of reading, mostly man pages. What I know is that when I type 10.0.0.2 into my browser on my regular laptop or desktop, I get the "It Works! message so I know my server is alive and well there. After reading about SSH, I decided to try telnet first so if it didn't work, it would be easier to figure out why. I've tried several ideas but the most useful to present here might be:
```

~$ telnet 10.0.0.2
Trying 10.0.0.2...
telnet: Unable to connect to remote host: Connection refused
```

At this moment I am stumped and could use some help.

:popcorn:

---

### Post by Cheesemill on 2013-03-17
That command you are using will fail because there isn't anything listening for connections on port 23 on your server (the standard telnet port).
You can specify a port number with telnet to use it to check for other services that may be running, for example...
```
 telnet 10.0.0.2 80
```
will try and connect to port 80 (the standard http port) or
```
 telnet 10.0.0.2 22
```
will try and connect to port 22 (the standard ssh port).

The easiest method to check a ssh server is running is to simply try and connect to it...
```
ssh user@10.0.0.2
```
```
rob@raring:~$ ssh mysql
Welcome to Ubuntu 12.04.2 LTS (GNU/Linux 3.5.0-25-generic x86_64)

 * Documentation:  https://help.ubuntu.com/
Last login: Fri Mar 15 22:20:18 2013 from raring.home
rob@mysql:~$ logout
Connection to mysql closed.
rob@raring:~$
```

If the server is running and you still can't connect you can use up to 3 verbose switches with ssh to give you a more detailed output...
```
ssh -vvv user@10.0.0.2
```
```
rob@raring:~$ ssh -vvv mysql
OpenSSH_6.1p1 Debian-3, OpenSSL 1.0.1c 10 May 2012
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: /etc/ssh/ssh_config line 19: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to mysql [192.168.1.128] port 22.
debug1: Connection established.
debug3: Incorrect RSA1 identifier
debug3: Could not load "/home/rob/.ssh/id_rsa" as a RSA1 public key
debug1: identity file /home/rob/.ssh/id_rsa type 1
debug1: Checking blacklist file /usr/share/ssh/blacklist.RSA-2048
debug1: Checking blacklist file /etc/ssh/blacklist.RSA-2048
debug1: identity file /home/rob/.ssh/id_rsa-cert type -1
debug1: identity file /home/rob/.ssh/id_dsa type -1
debug1: identity file /home/rob/.ssh/id_dsa-cert type -1
debug1: identity file /home/rob/.ssh/id_ecdsa type -1
debug1: identity file /home/rob/.ssh/id_ecdsa-cert type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.9p1 Debian-5ubuntu1
debug1: match: OpenSSH_5.9p1 Debian-5ubuntu1 pat OpenSSH_5*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_6.1p1 Debian-3
debug2: fd 3 setting O_NONBLOCK
debug3: load_hostkeys: loading entries for host "mysql" from file "/home/rob/.ssh/known_hosts"
debug3: load_hostkeys: found key type ECDSA in file /home/rob/.ssh/known_hosts:3
debug3: load_hostkeys: loaded 1 keys
debug3: order_hostkeyalgs: prefer hostkeyalgs: ecdsa-sha2-nistp256-cert-v01@openssh.com,ecdsa-sha2-nistp384-cert-v01@openssh.com,ecdsa-sha2-nistp521-cert-v01@openssh.com,ecdsa-sha2-nistp256,ecdsa-sha2-nistp384,ecdsa-sha2-nistp521
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug2: kex_parse_kexinit: ecdh-sha2-nistp256,ecdh-sha2-nistp384,ecdh-sha2-nistp521,diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: ecdsa-sha2-nistp256-cert-v01@openssh.com,ecdsa-sha2-nistp384-cert-v01@openssh.com,ecdsa-sha2-nistp521-cert-v01@openssh.com,ecdsa-sha2-nistp256,ecdsa-sha2-nistp384,ecdsa-sha2-nistp521,ssh-rsa-cert-v01@openssh.com,ssh-dss-cert-v01@openssh.com,ssh-rsa-cert-v00@openssh.com,ssh-dss-cert-v00@openssh.com,ssh-rsa,ssh-dss
debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se
debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-sha2-256,hmac-sha2-512,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-sha2-256,hmac-sha2-512,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: none,zlib@openssh.com,zlib
debug2: kex_parse_kexinit: none,zlib@openssh.com,zlib
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: first_kex_follows 0 
debug2: kex_parse_kexinit: reserved 0 
debug2: kex_parse_kexinit: ecdh-sha2-nistp256,ecdh-sha2-nistp384,ecdh-sha2-nistp521,diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: ssh-rsa,ssh-dss,ecdsa-sha2-nistp256
debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se
debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-sha2-256,hmac-sha2-256-96,hmac-sha2-512,hmac-sha2-512-96,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-sha2-256,hmac-sha2-256-96,hmac-sha2-512,hmac-sha2-512-96,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: none,zlib@openssh.com
debug2: kex_parse_kexinit: none,zlib@openssh.com
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: first_kex_follows 0 
debug2: kex_parse_kexinit: reserved 0 
debug2: mac_setup: found hmac-md5
debug1: kex: server->client aes128-ctr hmac-md5 none
debug2: mac_setup: found hmac-md5
debug1: kex: client->server aes128-ctr hmac-md5 none
debug1: sending SSH2_MSG_KEX_ECDH_INIT
debug1: expecting SSH2_MSG_KEX_ECDH_REPLY
debug1: Server host key: ECDSA 81:8a:65:0b:d9:90:6a:25:9e:bc:f9:5f:dd:4e:25:cd
debug3: load_hostkeys: loading entries for host "mysql" from file "/home/rob/.ssh/known_hosts"
debug3: load_hostkeys: found key type ECDSA in file /home/rob/.ssh/known_hosts:3
debug3: load_hostkeys: loaded 1 keys
debug3: load_hostkeys: loading entries for host "192.168.1.128" from file "/home/rob/.ssh/known_hosts"
debug3: load_hostkeys: found key type ECDSA in file /home/rob/.ssh/known_hosts:4
debug3: load_hostkeys: loaded 1 keys
debug1: Host 'mysql' is known and matches the ECDSA host key.
debug1: Found key in /home/rob/.ssh/known_hosts:3
debug1: ssh_ecdsa_verify: signature correct
debug2: kex_derive_keys
debug2: set_newkeys: mode 1
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug2: set_newkeys: mode 0
debug1: SSH2_MSG_NEWKEYS received
debug1: Roaming not allowed by server
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug2: service_accept: ssh-userauth
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug2: key: /home/rob/.ssh/id_rsa (0x7f80e15464a0)
debug2: key: /home/rob/.ssh/id_dsa ((nil))
debug2: key: /home/rob/.ssh/id_ecdsa ((nil))
debug1: Authentications that can continue: publickey,password
debug3: start over, passed a different list publickey,password
debug3: preferred gssapi-keyex,gssapi-with-mic,publickey,keyboard-interactive,password
debug3: authmethod_lookup publickey
debug3: remaining preferred: keyboard-interactive,password
debug3: authmethod_is_enabled publickey
debug1: Next authentication method: publickey
debug1: Offering RSA public key: /home/rob/.ssh/id_rsa
debug3: send_pubkey_test
debug2: we sent a publickey packet, wait for reply
debug1: Server accepts key: pkalg ssh-rsa blen 279
debug2: input_userauth_pk_ok: fp 75:50:a6:a9:5a:79:34:8e:ca:0e:69:b7:75:ce:fb:9f
debug3: sign_and_send_pubkey: RSA 75:50:a6:a9:5a:79:34:8e:ca:0e:69:b7:75:ce:fb:9f
debug1: Authentication succeeded (publickey).
Authenticated to mysql ([192.168.1.128]:22).
debug1: channel 0: new [client-session]
debug3: ssh_session2_open: channel_new: 0
debug2: channel 0: send open
debug1: Requesting no-more-sessions@openssh.com
debug1: Entering interactive session.
debug2: callback start
debug2: fd 3 setting TCP_NODELAY
debug3: packet_set_tos: set IP_TOS 0x10
debug2: client_session2_setup: id 0
debug2: channel 0: request pty-req confirm 1
debug1: Sending environment.
debug3: Ignored env SSH_AGENT_PID
debug3: Ignored env GPG_AGENT_INFO
debug3: Ignored env TERM
debug3: Ignored env SHELL
debug3: Ignored env XDG_SESSION_COOKIE
debug3: Ignored env GJS_DEBUG_OUTPUT
debug3: Ignored env WINDOWID
debug3: Ignored env GNOME_KEYRING_CONTROL
debug3: Ignored env GJS_DEBUG_TOPICS
debug3: Ignored env GTK_MODULES
debug3: Ignored env USER
debug3: Ignored env LS_COLORS
debug3: Ignored env XDG_SESSION_PATH
debug3: Ignored env XDG_SEAT_PATH
debug3: Ignored env SSH_AUTH_SOCK
debug3: Ignored env SESSION_MANAGER
debug3: Ignored env DEFAULTS_PATH
debug3: Ignored env XDG_CONFIG_DIRS
debug3: Ignored env PATH
debug3: Ignored env DESKTOP_SESSION
debug3: Ignored env PWD
debug3: Ignored env EDITOR
debug3: Ignored env GNOME_KEYRING_PID
debug1: Sending env LANG = en_GB.UTF-8
debug2: channel 0: request env confirm 0
debug3: Ignored env MANDATORY_PATH
debug3: Ignored env UBUNTU_MENUPROXY
debug3: Ignored env GDMSESSION
debug3: Ignored env SHLVL
debug3: Ignored env HOME
debug3: Ignored env LANGUAGE
debug3: Ignored env GNOME_DESKTOP_SESSION_ID
debug3: Ignored env LOGNAME
debug3: Ignored env XDG_DATA_DIRS
debug3: Ignored env DBUS_SESSION_BUS_ADDRESS
debug3: Ignored env LESSOPEN
debug3: Ignored env TEXTDOMAIN
debug3: Ignored env XDG_RUNTIME_DIR
debug3: Ignored env DISPLAY
debug3: Ignored env XDG_CURRENT_DESKTOP
debug3: Ignored env LESSCLOSE
debug3: Ignored env TEXTDOMAINDIR
debug3: Ignored env COLORTERM
debug3: Ignored env XAUTHORITY
debug3: Ignored env _
debug2: channel 0: request shell confirm 1
debug2: callback done
debug2: channel 0: open confirm rwindow 0 rmax 32768
debug2: channel_input_status_confirm: type 99 id 0
debug2: PTY allocation request accepted on channel 0
debug2: channel 0: rcvd adjust 2097152
debug2: channel_input_status_confirm: type 99 id 0
debug2: shell request accepted on channel 0
Welcome to Ubuntu 12.04.2 LTS (GNU/Linux 3.5.0-25-generic x86_64)

 * Documentation:  https://help.ubuntu.com/
Last login: Sun Mar 17 18:28:36 2013 from raring.home
rob@mysql:~$ 
```

---

### Post by BEEDO on 2013-03-17
Cheesemill,

I tried your suggestions and ...

[HTML]
~$ ssh -vvv me@10.0.0.2
OpenSSH_5.9p1 Debian-5ubuntu1, OpenSSL 1.0.1 14 Mar 2012
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: /etc/ssh/ssh_config line 19: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to 10.0.0.2 [10.0.0.2] port 22.
debug1: connect to address 10.0.0.2 port 22: Connection timed out
ssh: connect to host 10.0.0.2 port 22: Connection timed out

[/HTML]

I am as lost as before, I am sorry to say.  :confused:

---

### Post by Cheesemill on 2013-03-17
Do you actually have the ssh server installed on your laptop?
```
sudo apt-get install openssh-server
```

---

### Post by BEEDO on 2013-03-17
Cheesemill, Yes, I did not originally install it but did use that very command almost immediately after I installed the server.

---

### Post by BEEDO on 2013-03-17
Hey! I have connected with ssh on the server after inputting this at the server's physical console: 
```

 ~$ sudo ufw allow ssh
```

Thanks Cheesemill!

---

### Post by ivancarrascoq on 2013-04-17
Hi, probably this can help you.
You should scan all port on your computer target:
[INDENT][B]root@TR069:/home/ivanx# apt-get install nmap
[/B]
then...
(to scan all ports)
[B]
root@TR069:/home/ivanx# nmap 10.0.0.2[/B]
or 
(to scan an especific port, ie. telnet)[/INDENT]
[INDENT][B]
root@TR069:/home/ivanx# nmap 10.4.126.144 -p 23[/B][/INDENT]
[INDENT]
[/INDENT]
[INDENT]Starting Nmap 5.21 ( [http://nmap.org](http://nmap.org) ) at 2013-04-17 18:38 CDT[/INDENT]
[INDENT]Nmap scan report for 10.4.126.144[/INDENT]
[INDENT]Host is up (0.00022s latency).[/INDENT]
[INDENT]PORT   STATE SERVICE[/INDENT]
[INDENT]23/tcp open  telnet[/INDENT]
[INDENT]MAC Address: 00:0C:42:EA:65:6A (Routerboard.com)[/INDENT]
[INDENT]
[/INDENT]
[INDENT]Nmap done: 1 IP address (1 host up) scanned in 14.83 seconds[/INDENT]
[INDENT]**root@TR069:/home/ivanx#**[/INDENT]


Ivan Carrasco Q.
:-)

---

