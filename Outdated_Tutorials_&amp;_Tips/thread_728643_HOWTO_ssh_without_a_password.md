---
title: "HOWTO: ssh without a password"
date: 2008-03-19
forum: Outdated Tutorials &amp; Tips
---

### Post by Jose Catre-Vandis on 2008-03-19
**#UPDATE#**

The initial howto seems to have stopped working on me for some reason, having upgraded both client and server to 9.04. so here is a new effort that works:

############################################################################################################

On your client machine:
```
ssh-keygen -t rsa -b 2048 -f /home/user/.ssh/id_rsa
```
Press Enter twice to avoid a password
```
ssh-copy-id -i /home/user/.ssh/id_rsa.pub server
```
Assuming you have a previous login to the server, enter password as usual
Then logout, and try logging in again, you should go straight in.

Read below for prerequisites, file permissions etc. Replace **user** with your username, and **server** with your servername.

Thanks to [ashton88]("http://ubuntuforums.org/showthread.php?t=1145869") for this update

############################################################################################################

Couldn't find a full explanation of this on the forum so am posting here:

SSH Without a Password

The following steps can be used to ssh from one system to another without specifying a password.
Notes:

    * The system from which the ssh session is started via the ssh command is the client.
    * The system that the ssh session connects to is the server.
    * These steps work on systems running OpenSSH.
    * The steps assume that a DSA key is being used. To use a RSA key substitute 'rsa' for 'dsa'.
    
Steps:

   1. Open a terminal on the client and run the following commands:

      ```
$ mkdir -p $HOME/.ssh            #if not already there
$ chmod 0700 $HOME/.ssh               #if not already OK

$ ssh-keygen -t dsa -f $HOME/.ssh/id_dsa -P ''
```

      This should result in two files, $HOME/.ssh/id_dsa (private key) and $HOME/.ssh/id_dsa.pub (public key). The "-P ' ' " part of the last command helps create a key without a password, this is important.

   2. Copy $HOME/.ssh/id_dsa.pub to the server.
   3.Login to your server via ssh in the normal way. On the server run the following commands:

      ```
$ mkdir $HOME/.ssh                 # if not already there
$ cat id_dsa.pub >> $HOME/.ssh/authorized_keys
$ chmod 0600 $HOME/.ssh/authorized_keys
```

   4.Delete the public key file

   5. Logout of the server

   6. Try logging back in, you should go straight in without having to type a password

Notes: 

this will only work from the client machine you set it up on, you will need to do this for each client machine you wish to use.

When you set up another client machine, follow the first part as before, but this time open up the id-dsa.pub file on your client machine and copy the public key. Then log in to your server, open up the authorized_keys file in nano/pico and paste the new key on the next line. Check the key is all on one line, to match the previous one. Save the file. Logout of the server and test.

Info sourced from and credits to ```
http://www.csua.berkeley.edu
```

---

### Post by Koybe on 2008-03-19
Hello,

This is nice, but I would say  'SSH using registred certificates' instead of 'SSH without a password' ;)

Because like you said, it sounds less secure, but it's not.

---

### Post by waylandbill on 2008-03-19
Giving the world read access to the authorized_keys is not necessary. You could give 600 or even 400 permissions and everything will work as no other user needs to view it and you don't really need to write to it later. If you did, you'd just chmod in write permissions.

---

### Post by ashayh on 2008-03-19
Hi

The command: ssh-copy-id is provided with most modern openssh versions.

After generating your keys, run:
ssh-copy-id joe@servername

And you should be set. 
Running: 
ssh -l joe servername
Should get you in automatically.

I don't think password less keys are a good idea. 
It is better to use the ssh-agent to store your passphrase. (and lock your screen)

---

### Post by Jose Catre-Vandis on 2008-03-19
> **Koybe said:**
> Hello,

This is nice, but I would say  'SSH using registred certificates' instead of 'SSH without a password' ;)

Because like you said, it sounds less secure, but it's not.

I know what you mean, but what newbie who wants to achieve this is going to search on " SSH using registered certificates" ?  :)

@ waylandbill

Have adjusted to 600 from 644 (644 was recommended in some quarters when using 600 failed to provide access for some reason, so I tried to give the most workable solution) I have the world excluded from my LAN :)

@ashayh

See above :) but would also not recommend nil password access for a PC open to the interweb

---

### Post by bornfree on 2008-03-21
i would like to know how do i install ssh and how to enable the putty to be able to access it..
it will only be for internal LAN's access and no external connections are allowed.. 
will telnet be sufficient? or ssh is a better choice?
thanks.

---

### Post by Jose Catre-Vandis on 2008-03-21
> **bornfree said:**
> i would like to know how do i install ssh and how to enable the putty to be able to access it..
it will only be for internal LAN's access and no external connections are allowed.. 
will telnet be sufficient? or ssh is a better choice?
thanks.

To install ssh on your Ubuntu:
```
sudo apt-get install openssh-client openssh-server
```
(remove either the client or server from your command depending on what you want)

With openssh-server installed you should then be able to use putty on a windows machine to ssh into your ubuntu box. If you want to ssh -X then you will have to install cygwin on your windows machine in order to run an X server.

---

### Post by bornfree on 2008-03-24
> **Jose Catre-Vandis said:**
> To install ssh on your Ubuntu:
```
sudo apt-get install openssh-client openssh-server
```
(remove either the client or server from your command depending on what you want)

With openssh-server installed you should then be able to use putty on a windows machine to ssh into your ubuntu box. If you want to ssh -X then you will have to install cygwin on your windows machine in order to run an X server.


thank you.. but i got another noob question.. i am still very new in linux 
i am not able to install as the required files are not available on the machine. i have downloaded the file (openssh-4.7p1.tar.gz) from openssh.org. However, where do i place it in order to install it?

---

### Post by Jose Catre-Vandis on 2008-03-24
> **bornfree said:**
> thank you.. but i got another noob question.. i am still very new in linux 
i am not able to install as the required files are not available on the machine. i have downloaded the file (openssh-4.7p1.tar.gz) from openssh.org. However, where do i place it in order to install it?

Just use synaptic or the command line I posted, don't worry at the stage about downloading and compiling :)


```
sudo apt-get install openssh-client openssh-server
```

If this doesn't work, come back and we'll see what's next ;)

---

### Post by bornfree on 2008-03-24
> **Jose Catre-Vandis said:**
> Just use synaptic or the command line I posted, don't worry at the stage about downloading and compiling :)


```
sudo apt-get install openssh-client openssh-server
```

If this doesn't work, come back and we'll see what's next ;)

my bad.. a lesson learnt.. there is a difference between
```

sudo apt-get install openssh server
sudo apt-get install openssh-server

```

sorry bad syntax on my end. it is working now.. :D 
Thank you Jose.

---

### Post by Jose Catre-Vandis on 2008-03-25
> **bornfree said:**
> my bad.. a lesson learnt.. there is a difference between
```

sudo apt-get install openssh server
sudo apt-get install openssh-server

```

sorry bad syntax on my end. it is working now.. :D 
Thank you Jose.


Oh, we have all been there, most probably still are :)
Pleased you got things sorted :)

---

