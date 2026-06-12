---
title: "setting up openssh in ubuntu server"
date: 2008-10-24
forum: New to Ubuntu
---

### Post by masmithrpg on 2008-10-24
I am trying to setup an openssh server  on ubuntu server.  I have the server setup and can ftp to it, but now i want to change it to use public/private key.  Well partially anyway. 

Here is the scenario.  

Iseries computer- mine inside firewall

Ubuntu server with openssh - mine inside firewall. 

Vendor computer- outside of firewall.  

Ideally, i would like to connect fro Iseries to Ubuntu with only password, but have vendor connect via public key.  

So inside Ubuntu i have an administrator acct and a vendor acct(VDSS)

I receive a file from vendor with their public key.  
i placed this file in folder home/vdss/.ssh
then created a file called authorized_keys in this same folder
then i ran 
cat pubkey.txt >> ~/.ssh/authorized_keys
So now the contents of pubkey.txt exists in my authorized_keys file.  Is this correct????

Then from Administrator logon i ran 
ssh-keygen -t rsa
which created a public/private key pair in home/administrator/.ssh
Is this right?  

I know i need to export the public key to my vendor but how?

anything else i need to do????
Do i need to get this public/private key pair into home/vdss/.ssh/authorized_keys?  How?  

thanks in advance.

---

### Post by __Frank__ on 2008-10-25
Hello masmithrpg,

You don't need to export your public key to the vendor. For the vendor to gain access to your server all that is required is that their public key is added to $HOME/.ssh/authorized_keys. Once you have done that they should be able to access your server without a password.

For a step by step tutorial on this check:
[http://www.csua.berkeley.edu/~ranga/notes/ssh_nopass.html](http://www.csua.berkeley.edu/~ranga/notes/ssh_nopass.html)

Cheers,
Frank

---

