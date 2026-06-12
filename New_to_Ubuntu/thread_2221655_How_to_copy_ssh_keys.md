---
title: "How to copy ssh keys?"
date: 2014-05-03
forum: New to Ubuntu
---

### Post by jim50 on 2014-05-03
Good morning!

with some help, I have been able to set up ssh on a wlan and public network. Now I want to switch it over to key authentication. 

I've generated both rsa and dsa keys.

I'm not really understanding how tocopy these keys. I've seen some really complicated things, calling the key with cat, piplelining to ssh-copy and forwarding to another computer. Why can you not just copy the .pub file? 

I've been trying to set this up from a tablet using apps that have 5 star reviews, but cannot figure out how to copy the keys. I've tried copy'ing and pasting the text in the key and it always fails? 

Jim

---

### Post by Lars Noodén on 2014-05-03
I would leave the DSA keys and use only RSA or Ed25519.  

But about copying, all you have to do for key based authentication is copy and paste the *public* key into the remote server's ~/.ssh/authorized_keys file.  You can do this by any method you want.  The only thing that matters  (if all the other defaults are left alone) is that the public key ends up in the right file on one single line with no breaks.  

Others prefer using the [ssh-copy-id](http://manpages.ubuntu.com/manpages/trusty/en/man1/ssh-copy-id.1.html) script.  

```

ssh-copy-id  -i ~/.ssh/some_key_rsa.pub  user@someserver.org

```

---

### Post by jim50 on 2014-05-03
Thanks lars!

I tried copy and pasting the text in to both apps and got a no go. I looked online and it said to file transfer the .pub key in itunes, I did this and both apps still say the keys are invalid.

I've read that I need to convert my rsa pub key to a ppk putty key. I downloaded putty tools, but I cannot for the life of me work this out?

Jim

---

### Post by TheFu on 2014-05-03
For system to system key transfers (everything was created in the default way, default location), I use just
```
ssh-copy-id userid@server
```
In the old days, we would select/paste the contents of the .pub key between 2-xterms - 1 local and 1 on the remote machine into the authorized_keys file it would go, then manually remove any newline characters, check the directory and file permissions (ssh is picky), then try the connection.

Other non-Linux key-creation tools may not create a compatible key. I don't know.

For years, I didn't know about ssh-copy-id - handling the keys was a hassle.  Since learning about, I'm completely sold and setup key-based authentication to every server, every time. It is too easy now.

---

### Post by Lars Noodén on 2014-05-03
If you are connecting from Ubuntu as a client to Ubuntu as a server, then you do not need to modify the keys after they are created.  If you did not use ssh-copy-id, then you can paste them.  First, open the local copy of the public key, highlight it and copy.

```

nano -w ~/.ssh/some_key_rsa.pub

```

Then log into the server as normal and open the authorized keys file for editing and paste in the public key.

```

nano -w ~/.ssh/authorized_keys

```

The -w is necessary to prevent the long lines from wrapping.  Maybe that's what was forgotten?

After that, you should be able to connect to the server:

```

ssh -i ~/.ssh/some_key_rsa  user@server.example.org

```

Why is iTunes mentioned?  Do you have a mac?

---

### Post by jim50 on 2014-05-03
Thank you so much for the hep.

i have made a little progress. Where i was going wrong was i thought i had to copy my public key. Apparently my ssh client doesnt support this. Instead it generates a private key and a public key of its own and i have to add these to the ~/.ssh/authorized_keys folder.

I get the principle, but i am now stuck. I tried using putty to create the keys and i tried letting this client generate the keys. Every time it tries to connect, then says invalid key/passcode.

I don't really know how to fix this?

I have extracted the text from the putty header and footer as instructions dictate so that only the letters and numbers of the key sit on one line in the authorized_keys file?

---

### Post by jim50 on 2014-05-03
Update!

I'm in! Just after i posted that message, I realised i only copied the key to the folder. I didn't add the preceding ssh-rsa comment! \\:D/ 

Thank you so much for all your help and quick responses - i can see why they say linux is about community!

finally do you have any good security practices? So far i have
-changed the port
-blocked root log in
-allowed only one user log in, blocked all other users
-changed my passkey to 2048 from 1024 rsa2, setting passphrase to 18 char
-renamed my keys directory and file names
-changed permissions to my new ssh directory recursively to 700
-disabled x11 forwarding


oh and i read it's good to disable port forwarding in sshd_config too? I'm ssh'ing to a virtualbox guest, so i have to port forward virtualbox's network adapter to connect. Does this option mean port forwarding to connect, like I'm using, or stoppig the ssh user from additional port forwarding??

Thanks again 

Jim


PS how do you all put the code in the boxes??

---

### Post by Lars Noodén on 2014-05-03
It looks like you have found the main steps.  There are some steps you can take with iptables to limit brute-force attacks, but those are a lot less common now and if you've disabled password login then it's not an issue anyway.  Congrats.  

About the boxes, [****code][/code] does the job and put what you want in the box in between the two tags.

---

### Post by jim50 on 2014-05-03
```
 hello world 
```

---

### Post by jim50 on 2014-05-03
Ah, got it! Cheers Lars and the fu (that would be a good indie band name) so much for all your help!

I think I'm almost ready to begin installing ubuntu server on my actual hardware now! 

Have a fantastic weekend

Jim

---

### Post by Lars Noodén on 2014-05-03
If you are sure the keys work then password authentication can be disabled with the following in sshd_config:

```

PasswordAuthentication no

```

Then reload the configuration.

```

sudo service ssh restart

```

That will make you immune to the password-guessing attacks that occur on publicly facing servers.

---

### Post by TheFu on 2014-05-03
NEVER push the private key anywhere!  Only the public key. This applies to all PKI methods. Private means "PRIVATE" - not to be shared.

[http://blog.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures](http://blog.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures) for security and ssh.  I don't bother changing the port or the directories on the servers. I let the router do port translations.

If you use vbox with bridged adapters, no need to forward anything. The guestOS is a full member of the subnet.  I almost NEVER use NAT virtual machine networking.

Congrats on getting this working.   Now ... learn about the ~/.ssh/config file. It will save you tons and tons of time. I wish I'd known about it 10 yrs earlier than I did. ;)

---

### Post by jim50 on 2014-05-03
Hi 
Thanks so much for the tip!

I (finally) got bridged mode working and signed the port on the network. I also looked up how to create a config file! 

I've created something like this for each user:
```

Host ubuntu
 Hostname 198.254.1.20
 User jim
 Port 3333
 ServerAliveInterval 200

Host suse
 Hostname 198.254.1.21
 User jim
 Port 3334
 ServerAliveInterval 200

Host fedora
 Hostname 198.254.1.22
 User jim
 Port 3355
 ServerAliveInterval 200
```

As you can see I've tried seting up a couple of VM's to get the hang of it! It's all working great! Thank you so much!

Jim

---

### Post by TheFu on 2014-05-03
As you have more servers, different userids, different ports around the world, I find having all that documented (and used) inside the ~/.ssh/config file totally great.  Even with DNS names for servers, sometimes my alias is much more descriptive.

Plus, never having to remember is that is a -P or -p option to set the port for any command that uses ssh under the covers is completely worth it.  I never have to lookup, specify the port again! They all use the config file too!  Oh - and for userids ... sometimes Ansible doesn't like my ~/.ssh/config settings, so I have to comment those out for a few servers.

---

### Post by Lars Noodén on 2014-05-03
I'm also quite happy about the shortcuts made possible by ssh_config.  Since we're on the topic of keys, you can also specify which key which server will use.

```

  ...
  IdentitiesOnly yes
  IdentityFile ~/.ssh/server1_rsa

```

If you have to pass through a gateway host or want to add a tunnel that can be defined, too.

---

### Post by jim50 on 2014-05-03
Thanks again guys! 

I've found out how to set the defaults too:

```

Host *
 User jim
 ServerAliveInterval 200
 Protocol 2

Host ubuntu
 Hostname 198.254.1.20
 Port 3333
 IdentityFile ~/.ssh/rsa_ubuntu


Host suse
 Hostname 198.254.1.21
 Port 3334
 IdentityFile ~/.ssh/rsa_suse


Host fedora
 Hostname 198.254.1.22
 Port 3355
 IdentityFile ~/.ssh/rsa_fedora
 
```

I've learned so much today!  :D

---

