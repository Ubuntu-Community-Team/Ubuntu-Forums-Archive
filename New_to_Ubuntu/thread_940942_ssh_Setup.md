---
title: "ssh Setup"
date: 2008-10-07
forum: New to Ubuntu
---

### Post by Konstabel on 2008-10-07
Hi, 

How do I setup a ssh server. I have it working already, what I mean is, how do I set the fine details and settings: ie generate new security keys, etc.

---

### Post by wolfen69 on 2008-10-07
[Here]("https://help.ubuntu.com/community/SSHHowto") you go.

---

### Post by bodhi.zazen on 2008-10-07
[https://help.ubuntu.com/community/AdvancedOpenSSH](https://help.ubuntu.com/community/AdvancedOpenSSH)

[https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)

---

### Post by Konstabel on 2008-10-08
Thanks Bodi,

I read the ssh and advanced ssh articles, but one thing did I not find. How do I get the ssh key generated on my Ubuntu server to my Windows putty client?

---

### Post by bodhi.zazen on 2008-10-08
> **Konstabel said:**
> Thanks Bodi,

I read the ssh and advanced ssh articles, but one thing did I not find. How do I get the ssh key generated on my Ubuntu server to my Windows putty client?

You have to convert the key. 

You generated an openssh key , now you need to convert it to a format Putty understands.

You do this with putty's key generator (puttygen.exe)

Import the key, you will be asked for your password.

Then save the key Use the same name as the original key (important). 

[http://linux-sxs.org/networking/openssh.putty.html](http://linux-sxs.org/networking/openssh.putty.html)

Scroll down to the "Converting the OpenSSH private key to Putty format" section.

_Note_: I updated the SSH wiki page adding a short section and the above link.

---

### Post by Nxion on 2008-10-08
> **bodhi.zazen said:**
> You have to convert the key. 

You generated an openssh key , now you need to convert it to a format Putty understands.

You do this with putty's key generator (puttygen.exe)

Import the key, you will be asked for your password.

Then save the key Use the same name as the original key (important). 

[http://linux-sxs.org/networking/openssh.putty.html](http://linux-sxs.org/networking/openssh.putty.html)

Scroll down to the "Converting the OpenSSH private key to Putty format" section.

Your quick bodhi.zazen! I was going to suggest ex actually what you put. I started typing and say that you already replied :)

---

### Post by Konstabel on 2008-10-08
Thanks for the help, it is really appreciated.

Now I am stuck with the actual import step. When I try to do File->Load Private key, I get an error message stating "Cannot open file" (the id_rsa file).

I saved the file in a shared folder, accessible by my windows machine. Everything else in the same folder I can access.

---

### Post by Konstabel on 2008-10-08
I forgot to ask. Why is it that when ssh-keygen generates a key it is called a public key

*Your public key has been saved in ...*

But when you import it into keygen, it asks for a private key?

---

### Post by bodhi.zazen on 2008-10-08
ssh-keygen generates two keys, a public and private key.

The default is "id_rsa"

You can change the name ...

At any rate you get 2 files, id_rsa and id_rsa.pub

The terminology is confusing.

The .pub is the public key, you put that on the ssh server, under ~/.ssh/authorized_keys

The private key you keep.

You want to import the private key (to putty-gen) and then save is as "id_rsa.ppk".

I found this helpful :

[http://alblue.blogspot.com/2005/08/howto-ssh-logins-using-keys.html](http://alblue.blogspot.com/2005/08/howto-ssh-logins-using-keys.html)


[http://docs.ocf.berkeley.edu/wiki/SSH_key_management](http://docs.ocf.berkeley.edu/wiki/SSH_key_management)

---

