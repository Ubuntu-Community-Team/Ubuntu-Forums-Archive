---
title: "OpenSSH server problems"
date: 2012-03-28
forum: New to Ubuntu
---

### Post by wolf421 on 2012-03-28
I've just done a complete re-install of my os yesterday (3 times) due to keyboard not being recognized twice. 
Got that problem solved.

Problem is OpenSSH server doesn't want to allow a connection from any pc on my home network.

 Even after configuring the sshd_config file for my ports and allowed users. 

What I've done so far.
1. set server on dynamic ip range
2. set listen address to correct ip range and port
3. set allowed users 
4. made security keys for users
5. restarted server

I keep getting the error "no authentication methods are available" "connection refused public key" from the server when I try to use ssh client from any of my other systems.

The only thing I have been able to come up with is that I can't get the security keys from the server to the other computers in the home. I've tried to copy them to a flash drive and the os won't let me even when using sudo su to be root. 

At this point I'm almost ready to give up and forget networking my home systems. Ubuntu server connected to 4 windows systems over private network. 

Any help please...

---

### Post by papibe on 2012-03-28
Hi wolf421. Welcome to the forums!

Could you post the errors you are getting?

Try for example using extra verbose options:
```
ssh -vvv yourserver
```
Regards.

---

### Post by bodhi.zazen on 2012-03-29
You need to specify a key to use

```
ssh -i ~/.ssh/Your_key server
```

---

### Post by wolf421 on 2012-03-29
> **papibe said:**
> Hi wolf421. Welcome to the forums!

Could you post the errors you are getting?

Try for example using extra verbose options:
```
ssh -vvv yourserver
```
Regards.

Well here´s the output of that command

OpenSSH_5.8p1 Debian-7ubuntu1, OpenSSL 1.0.0e 6 Sep 2011
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug3: cipher ok: aes128-ctr [aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc]
debug3: cipher ok: aes192-ctr [aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc]
debug3: cipher ok: aes256-ctr [aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc]
debug3: cipher ok: arcfour256 [aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc]
debug3: cipher ok: arcfour128 [aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc]
debug3: cipher ok: aes128-cbc [aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc]
debug3: cipher ok: 3des-cbc [aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc]
debug3: ciphers ok: [aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc]
debug2: mac_setup: found hmac-md5
debug3: mac ok: hmac-md5 [hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160]
debug2: mac_setup: found hmac-sha1
debug3: mac ok: hmac-sha1 [hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160]
debug2: mac_setup: found [email]umac-64@openssh.com[/email]
debug3: mac ok: [email]umac-64@openssh.com[/email] [hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160]
debug2: mac_setup: found hmac-ripemd160
debug3: mac ok: hmac-ripemd160 [hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160]
debug3: macs ok: [hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160]
debug2: ssh_connect: needpriv 0
debug1: Connecting to 192.168.1.68 [192.168.1.68] port 13030.
debug1: connect to address 192.168.1.68 port 13030: Connection refused
ssh: connect to host 192.168.1.68 port 13030: Connection refused

And that is after I purged it from the system last night before I went to bed. I was so tired after fighting with it all day that I just locked the window and left the terminal up and running all night.

---

### Post by wolf421 on 2012-03-29
> **bodhi.zazen said:**
> You need to specify a key to use

```
ssh -i ~./ssh/Your_key server
```

What file? It comes up giving me the list of various codes to use with ssh.

---

### Post by bodhi.zazen on 2012-03-29
> **wolf421 said:**
> What file? It comes up giving me the list of various codes to use with ssh.

your key file. You indicated in your origional post you set up ssh keys:

> 4. made security keys for users

So if you set them up, you need to use them.

See [http://bodhizazen.net/Tutorials/SSH_keys](http://bodhizazen.net/Tutorials/SSH_keys)

The output of your command also shows "connection refused" . firewall ? Is the ssh server running ?

---

### Post by wolf421 on 2012-03-29
Ok here´s what I did this morning.

Using the gui file manager I uninstalled openssh and anything relating to it. 
Then I went in and manually deleted the files and folders.
Next I re-installed openssh.
Next changed the port and listen address in /.ssh/sshd_config
Made new keys and copied them to authorized keys
Restarted ssh.
Disabled ufw (I think this was the reason I could not connect) it was blocking the ports. That I had opened for ssh.
Went to laptop and logged in no problem.

Thanks to the both of you for helping this (recent convert ¨windows 7 user¨) over to ubuntu!
30 years running dos and windows systems and I´m finding that I like ubuntu better in less than a week of using it.
Mark this issue as SOLVED!

---

### Post by bodhi.zazen on 2012-03-29
Great, once the keys are working, disable passwords.

FWIW, although controversial, changing the port does little to improve security. Use keys, disable password authentication, and use AllowUsers in sshd_config.

---

