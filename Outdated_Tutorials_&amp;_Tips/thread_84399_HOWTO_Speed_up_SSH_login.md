---
title: "HOWTO: Speed up SSH login"
date: 2005-10-31
forum: Outdated Tutorials &amp; Tips
---

### Post by Jacky_J on 2005-10-31
If you execute the command:

```
ssh *username*@*hostname*
```

and it takes a good 10-15 seconds to prompt you with a login/password, and you don't want it to take 10-15 seconds, then you've come to the right place.

You can blame IPv6 for this.  Execute: 

```
ssh -4 *username*@*hostname*
```

Note the -4 argument.  This forces ssh to use only IPv4.  If this doesn't speed it up, then you're probably out of luck.

Now, if you don't want to type -4 all the time (or are using CVS with ssh), edit your ssh_config file like so:

```
sudo gedit /etc/ssh/ssh_config
```

add the line
```
AddressFamily inet
```

Now you're set.

---

### Post by Jeconais on 2005-10-31
Works as advertised, thanks, very useful tip :)

---

### Post by DarthMandeep on 2005-10-31
Such a simple thing, yet it makes ssh so much nicer.

Thanks!

---

### Post by majikstreet on 2005-10-31
Thanks! Much faster... If only I could figure out a way for SSH to remember my passphrase for my ssh key............. 

-m

---

### Post by riggsd on 2005-11-01
[QUOTE=majikstreet]Thanks! Much faster... If only I could figure out a way for SSH to remember my passphrase for my ssh key............. [/QUOTE]


```
riggs@ubuntu:~ $ [COLOR="Red"]apt-cache show keychain[/COLOR]
Package: keychain
Priority: optional
Section: universe/net
Installed-Size: 136
Maintainer: Cesar Mendoza <mendoza@debian.org>
Architecture: all
Version: 2.5.5-3ubuntu2
Depends: debconf (>= 1.2.0), openssh-client | ssh-client, grep (>= 2.4.2-1)
Filename: pool/universe/k/keychain/keychain_2.5.5-3ubuntu2_all.deb
Size: 33100
MD5sum: 37e60562c707fe032028fd3280bff756
Description: key manager for OpenSSH
 Keychain is an OpenSSH key manager, typically run from ~/.bash_profile. When
 keychain is run, it checks for a running ssh-agent, otherwise it starts one.
 It saves the ssh-agent environment variables to ~/.keychain/\-sh,
 so that subsequent logins and non-interactive shells such as cron jobs can
 source the file and make passwordless ssh connections.  In addition, when
 keychain runs, it verifies that the key files specified on the command-line
 are known to ssh-agent, otherwise it loads them, prompting you for a password
 if necessary.
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu
```

---

### Post by majikstreet on 2005-11-01
and I use it how?

---

### Post by Jacky_J on 2005-11-01
This is how I did it:

Basically, you need these files on your remote host:
   ~/.ssh/id_rsa
   ~/.ssh/id_rsa.pub
   ~/.ssh/authorized_keys

Then, on your local, you should have a copy of id_rsa
   ~/.ssh/id_rsa

If you don't know how to make those files, ssh to your remote host and execute

   ```
ssh-keygen -t rsa
```

enter in your passphrase, then do

```
cp .ssh/id_rsa.pub .ssh/authorized_keys
```

Then you need to copy id_rsa into your local .ssh directory (use scp or sftp)

after you have all the necessary files, execute

```
ssh-add
```

ssh-add should detect that you have a id_rsa file and asks for your passphrase.  After you do this, you should be able to ssh without a password.
However, you need to do this everytime you boot your computer.

Ubuntu is nice because it has an ssh-agent ID ready to go, so you don't need to mess around with keychain.

---

### Post by majikstreet on 2005-11-03
ahh.. is there any way to put the password in the command?

---

### Post by jdong on 2005-11-03
It's gonna be more secure for you to just leave the passphrase blank. Typing in a password as a part of a command is typically a bad idea. Not only is it displayed to any user doing a 'ps aux', but it also tends to get logged in ~/.bash_history, which by default is world-readable (I change that on all my workstations).

The downside is that if anyone manages to steal your ~/.ssh directory (usually requires physical access), they have full password-free access to any systems you use non-passphrased authentication to, until you realize what happened and remove the key's entry from authorized_keys on the server's end.

---

### Post by majikstreet on 2005-11-03
That sucks..... I guess I'll just type in the password :)

---

### Post by jdong on 2005-11-03
Don't get me wrong -- passwordless keys aren't necessarily bad... I personally use them to log into a few of my boxes (primarily my router)... It's just that when using it, you should understand the consequences. Convenience never comes free :)

---

### Post by majikstreet on 2005-11-04
The passworded key is my key on my main computer.. I don't remember if I put a password in the key on my server....errr... wait, maybe I'm wrong?

---

### Post by calt129 on 2005-11-14
You could use ssh-agent & ssh-add. Then you have to type your password only once in a session. Add to this startup scripts or, if you fancy, gstm (Gnome SSH tunnel manager) then you have a pretty secure setup without sacrificing convenience.

---

### Post by matthias_k on 2006-07-17
> **Jacky_J said:**
> This is how I did it:

Basically, you need these files on your remote host:
   ~/.ssh/id_rsa
   ~/.ssh/id_rsa.pub
   ~/.ssh/authorized_keys

Then, on your local, you should have a copy of id_rsa
   ~/.ssh/id_rsa

If you don't know how to make those files, ssh to your remote host and execute

   ```
ssh-keygen -t rsa
```
[...]

Sorry, no offense, but there is so much wrong with this post, I've got to point it out:
You do **not** store your private key on the remote host. Your private key is only (and ONLY!) stored in ~/ssh **on your local machine**. Especially, you don't "ssh to the remote machine and execute ssh-keygen", you do that on your **local** machine to generate the keypair. Please read up on SSH and public key cryptography to understand how it works.

The idea is that in order for a remote machine to be able to authorize you, it encrypts some value with your public key (which may be freely distributed), sends the encrypted value back to your local machine, where ssh-agent decrypts it with your private key and sends the decrypted result back to the remote host. If the values match, you are authenticated. This procedure is also called a "challenge".

I've seen a nice analogy somewhere on the web or in the ssh man pages, which outlines the idea behind public key authorization something like this:
Person A wants to send Person B a secured package. To do this, Person B sends Person A an open lock (the public key) which Person A uses to lock the package. Person A cannot unlock the package once it has been locked with B's lock, as only B has the key to unlock it. Person A then sends the locked package to Person B, who can unlock the package using his special key (the private key), to which only he has access.

As you described it, both persons would have the key to the lock. This would completely undermine the idea behind the algorithm. :-/

---

### Post by Jacky_J on 2006-08-16
> **matthias_k said:**
> Sorry, no offense, but there is so much wrong with this post, I've got to point it out:
You do **not** store your private key on the remote host. Your private key is only (and ONLY!) stored in ~/ssh **on your local machine**. Especially, you don't "ssh to the remote machine and execute ssh-keygen", you do that on your **local** machine to generate the keypair. Please read up on SSH and public key cryptography to understand how it works.

The idea is that in order for a remote machine to be able to authorize you, it encrypts some value with your public key (which may be freely distributed), sends the encrypted value back to your local machine, where ssh-agent decrypts it with your private key and sends the decrypted result back to the remote host. If the values match, you are authenticated. This procedure is also called a "challenge".

I've seen a nice analogy somewhere on the web or in the ssh man pages, which outlines the idea behind public key authorization something like this:
Person A wants to send Person B a secured package. To do this, Person B sends Person A an open lock (the public key) which Person A uses to lock the package. Person A cannot unlock the package once it has been locked with B's lock, as only B has the key to unlock it. Person A then sends the locked package to Person B, who can unlock the package using his special key (the private key), to which only he has access.

As you described it, both persons would have the key to the lock. This would completely undermine the idea behind the algorithm. :-/

You're right.  However, I think we're talking about two different scenarios.  I use this trick to quickly set up passwordless ssh.    I use a lot of different computers, and I don't want to have to call "ssh-keygen -t rsa" on every one I want to ssh from.  I have one id_rsa file that i just sftp over and i'm done.  Since i'm the only one that has access to id_rsa on the remote side, it doesn't matter.

---

### Post by ahmatti on 2007-03-30
> **Jacky_J said:**
> 
it takes a good 10-15 seconds to prompt you with a login/password, and you don't want it to take 10-15 seconds, then you've come to the right place.

You can blame IPv6 for this.  Execute: 

```
ssh -4 *username*@*hostname*
```

Note the -4 argument.  This forces ssh to use only IPv4.  If this doesn't speed it up, then you're probably out of luck.


Many thanks, this works for me! That delay has been driving me crazy :)

I use shellscripts to connect to the servers that I use frequently, the script only says, and named something short after the host
```

#!/bin/sh
ssh -4 -X -C user@host
```

I know this is pretty lazy, but it saves from trouble of typing the same thing over and over again since I use ssh daily to access a few servers...

---

