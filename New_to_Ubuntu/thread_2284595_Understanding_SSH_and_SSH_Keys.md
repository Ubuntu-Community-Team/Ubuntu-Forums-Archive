---
title: "Understanding SSH and SSH Keys"
date: 2015-06-30
forum: New to Ubuntu
---

### Post by Raner on 2015-06-30
I am working through building my first server in a vm. I am fairly new to linux in general. I am mostly adapting this guide: [https://help.ubuntu.com/14.04/serverguide/openssh-server.html](https://help.ubuntu.com/14.04/serverguide/openssh-server.html)

My questions concern the making and storing of ssh keys. (Warning: This will be a deluge of questions from a newbie.)

The setup I am considering consists of 3 machines: 1 is a server, the other 2 are clients to log into the server remotely.

The first thing I do is

```
sudo apt-get install openssh-server 
```

on each machine.

Here is where I encounter problems. As a regular non-root user on a non-server machine, I run

```
ssh-keygen -t rsa

```

Then it asks me for the location to store the keys. The default location, if I put nothing in, is:

/home/USER/.ssh/id_rsa. Another file named id_rsa.pub is created in the same directory.

But if I type in a name (“test”), the resulting file are not placed in /home/USER/.ssh/ , but instead just /home/USER. So if I name my file test, it will appear in as /home/USER/test (and test.pub).

I am not sure how significant the .ssh folder is. Should all keys be placed in that folder (either because it is required or because it is most practical)? And if so, does it matter if a key is in a sub folder?
(In other words, should I preface all of my keys with ".ssh/(NAME OF KEY)"?

Is it typical to leave an extension off of the one of the files? I just have id_rsa and id_rsa.pub – should the file named “id_rsa” have an extension? Most lunix files seem to not have an extension, so I am guessing this is normal, but one file does and one doesn't, so I want to be clear.

Moving on…

I don’t know which key belongs on which machine. The clients need to log into the server, but not vice versa. So do I need to copy the id_rsa or the id_rsa.pub file from a client to server, or do I need the server to copy either the id_rsa or id_rsa.pub file to the clients? And for two clients, do I need to create new, separate keys on each client machine and copy both of the keys to the server, or can I just copy the key made on one client machine to all client machines?

If I wanted to log into the server via SSH on the go, which files would I take with me from a client or server machine and where would I put them?

Here is what I currently do, but I do not know how it works and it may be overkill:

On a client machine, I run:

```
ssh-copy-id non-root-server-username@xxx.xxx.xxx.xxx
```

and I am prompted to enter the password for the account of non-root-server-username to install the keys

then I test it by running

```
ssh non-root-server-username@xxx.xxx.xxx.xxx
```

And I am no longer asked for a password (which seems like a success).

I see that there is now a "known_hosts" file on my client machine in /home/USER/.ssh/, and an “authorized_keys” file on my host machine in /home/USER/.ssh

Did I get this backwards? Is my server supposed to copy the keys to the client instead?

Is there a way to do this that avoids entering the user’s password (for example, manually copying keys)?

Moving on…

The next problem is logging in as the root on the server. (I can log in a normal user and elevate, but not as root directly).

I run 

```
ssh root@xxx.xxx.xxx.xxx 
```

from a client to the server and I am prompted for a password, but it is always rejected (verified several times it is typed correctly). What is causing this rejection? And can I setup the root account to use ssh keys, too?


Thanks for any clarification and pointers anyone might offer!

---

### Post by Lars Noodén on 2015-06-30
The package openssh-server is only needed on machines you intend to log into.  The machines you will log in from do no need it, and so it can be removed from those. 

The directory /home/USER/.ssh/ is as good a place as any for the keys.  You want them somewhere which has no access from anyone else.  If you put them there or in a subfolder in there, just make sure that only you have access.  You can always move the keys after you've created them but if you want to create them in place use [the -f option with ssh-keygen](http://manpages.ubuntu.com/manpages/trusty/en/man1/ssh-keygen.1.html) and specify a relative path or absolute path to where you want the key.  It might be a good idea to add a comment, too, with the -C option so it can help you keep track of which key is which.  

It's usual that the private part of the key pair has no filename extension, but that the public part of the key pair ends with .pub.  The private key stays on the client and the public key (and only the public key) gets moved to the server.  Each client should have its own key pair unique from the other clients.  The public key from the client goes into the user account on the server inside ~/.ssh/authorized_keys.  It is important that the key is all on one line and not broken up, which can happen if you copy and pastes sometimes.  But using ssh-copy-id as you have done should be the surest way as a beginning.  

It is a good idea to have passphrases for the keys but if you don't want to always type them in, load the key into the agent that Ubuntu has running in its desktop session using [ssh-add](http://manpages.ubuntu.com/manpages/trusty/en/man1/ssh-add.1.html)

Your client should have a known_hosts file with the server's public key and either the hostname, ip number or a hash thereof, in /home/USER/.ssh/ .
Your server should have an authorized_keys file with the client's public key(s) in /home/USER/.ssh/ .  

Setting up the keys requires logging in to the server with the user's password.  After the keys are set up, and you have verified that the keys work, you can turn off password authentication.

In Ubuntu, the root account is always disabled.  Even if you were to enable it, the best practice is to avoid logging in remotely as root.  And even in the edge cases where it is done, the server is set to allow only keys or even only keys containing forced commands.  So before going further down the path of remote root access, it is necessary to ask, why?  What are you trying to do?  There is probably a way around it.

---

### Post by papibe on 2015-06-30
> **Raner said:**
> I am not sure how significant the .ssh folder is. Should all keys be placed in that folder (either because it is required or because it is most practical)? And if so, does it matter if a key is in a sub folder?
(In other words, should I preface all of my keys with ".ssh/(NAME OF KEY)"?
It is a mixed of common practices, and defaults for ssh.

If you put in your ~/.ssh folder it would mean it is under a directory that by common practice does not allow other users to see what is inside. Also, when connecting to server, you would not need to specify the key, as by default ssh would look for it in that folder.

On the other hand, if you let it in your home, it is subject to the default home permissions. Also you would have to pass the location of the key every time you login remotely:
```
ssh -i ./test ....
```
> **Raner said:**
> Is it typical to leave an extension off of the one of the files? I just have id_rsa and id_rsa.pub – should the file named “id_rsa” have an extension? Most lunix files seem to not have an extension, so I am guessing this is normal, but one file does and one doesn't, so I want to be clear.
One is the private key, and one the public key.

As before, if you change the name, or location, you would have to explicitly say which file to use every time you want to login. If you leave them as they are, and put it on the ~/.ssh folder, ssh would consider them every time you ssh remotely. 
> **Raner said:**
> I don’t know which key belongs on which machine. The clients need to log into the server, but not vice versa.
The common procedure is to create the key pair on the client, and then transfer the public key to the server. This way, the private key does not travel. 

This would allow you to connect from that client to the server.
> **Raner said:**
> And for two clients, do I need to create new, separate keys on each client machine and copy both of the keys to the server, or can I just copy the key made on one client machine to all client machines?
Strictly you don't "have" to. You can reuse your key. However...

This is a matter of security administration. For instance, if you reuse your key, and then, say, your laptop is stolen. You would have to disable the key and then all clients would be locked out. 

A company would use different keys for different people, or even machines, but for personal use the decision is more of a compromise on convenience. 
> **Raner said:**
> I see that there is now a "known_hosts" file on my client machine in /home/USER/.ssh/, and an “authorized_keys” file on my host machine in /home/USER/.ssh
The command 'ssh-copy-id' takes the public key on the client and add it to the authorized_keys file on the server.

The file 'known_hosts' is a log of ssh connections.
> **Raner said:**
> And can I setup the root account to use ssh keys, too?
Yes you can. However, please don't.

Right now is not working for root because you did the procedure for the 'non-root-server-username'.

In order for this to work for root, you would have to take additional steps to lax security, which are **not** recommend, and then repeat the previous steps for the root user.

Does that help? Let us know if you have more questions.
Regards.

---

### Post by Raner on 2015-06-30
This was all very helpful! I am going to run through it all again right now.

The reason I wanted remote root access is because (probably due to my limited knowledge) I am not sure how to automate elevating a regular user to a root user. The reason I want to do this is to be able to backup and copy the entire contents of a server ( / ) and I am guessing I will need root access for that. I currently don't know how to respond to a prompt automatically in bash, and there is also the concern of storing my server's root account password in the bash script in plaintext. (I don't know how I will copy the server yet, but I was planning on testing with rsync). So if I write a bash script to be executed at regular intervals on a client machine (or the server to a specified backup client), it seems that I will need root access. Is there a way around this?

---

### Post by Raner on 2015-06-30
I successfully got most things working and I think I understand everything much better now.

To be clear on some things, if I wanted to log into the server via SSH from some new machine but did not want to to create a new ssh key for this this machine, I would copy the id_rsa from the client machine and place it in the new machine/new user's /home/USER/.ssh and things would work as expected? (I could login from the new machine to the remote server.)

I did run into a new difficulty:

I am having trouble letting my root user on my client machine log in using keys on the remote server. I ran all commands prefixed as sudo. (I'm not trying to login as the root, just let me root account ush ssh keys to login to the remote server as a regular user)

```
sudo ssh-keygen -t rsa
sudo ssh-copy-id non-root-server-username@xxx.xxx.xxx.xxx
```
But after this command I am told that:

"/usr/bin/ssh-copy-id: INFO: attempting to log in with the new key(s), to filter out any that are already installed

/usr/bin/ssh-copy-id: WARNING: All keys were skipped because they already exist on the remote system."

But if I try
```

sudo ssh non-root-server-username@xxx.xxx.xxx.xxx
```

I must provide the remote server's password. And I must continue to provide the passwrod each time I try to log in using this command.

---

### Post by Lars Noodén on 2015-06-30
Yes, you could just copy id_rsa, or whatever you've named the private key, to another account even on another machine and it would work as with the first account.  But again, it is a often a good idea to have separate keys for separate users. 

ssh-copy-id should complain if the key already exists in the account on the other server, so that is a good sign.  Regardless of which account, root or a normal user, is launching the ssh client, you'd need to point to the key.  The best way is to use the agent, however running [sudo](http://manpages.ubuntu.com/manpages/trusty/en/man8/sudo.8.html) complicates things. Since you are running ssh locally with sudo, the client side is functionally root and there is no agent normally running for root.  So to find the keys, ssh has to be pointed at them explicitly (there in the root account) using [the -i option in ssh](http://manpages.ubuntu.com/manpages/trusty/en/man1/ssh.1.html). 

```

sudo ssh **-i ~/.ssh/id_rsa** non-root-server-username@xxx.xxx.xxx.xxx
```

That should ask you for root's key's pass phrase instead of non-root-server-username's password on the other machine.  Eventually when you have your backup system figured out, it would be very good to lock down the keys over on the server's authorized_keys file using  **command="*command*"** and **from="*pattern-list*"** as described in [AuthorizedKeysFile section of the manual page for sshd](http://manpages.ubuntu.com/manpages/trusty/en/man8/sshd.8.html)

---

### Post by cariboo on 2015-07-01
Once you have logged into a remote system, you can use sudo to elevate privileges to administer your server, have a look at [this]("https://help.ubuntu.com/community/RootSudo") document. I'd hate to see a new user have their server compromised due to a lack of knowledge.

---

### Post by mastablasta on 2015-07-01
> **Raner said:**
> The reason I want to do this is to be able to backup and copy the entire contents of a server ( / ) and I am guessing I will need root access for that.

hmm are you sure?

anyway you can add scripts or users to sudoers file. : [https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)

temporary elevate yourself to root using sudo

or to run multiple commands i thin it is sudo -i

---

### Post by Raner on 2015-07-16
Another SSH question:

The /etc/ssh/sshd_config has the option to disable password authentication.
 
```
# Change to no to disable tunnelled clear text passwords
#PasswordAuthentication yes
 
```
If I disable this, and my public key is not on the server yet, will I be able to log in to the server and add it via ssh (it would ask me for the server’s password) or would I have to copy my key to the server in some other way? (Like a thumb drive or logging into the server while actually at the server.)
 
I am just concerned that if I use this option on a remotely hosted server I would be effectively locked out if I do not FIRST place my ssh public key on the server.

---

### Post by papibe on 2015-07-16
Your concern is grounded.

If you change it to:
```
PasswordAuthentication no
```
You'll be lock out if the keys are not set up and working.

Regards.

---

### Post by mastablasta on 2015-07-17
keys first, make sure they work, THEN disable password

---

