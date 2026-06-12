---
title: "Automatically setting up SSH keys for many users"
date: 2014-10-17
forum: Programming Talk
---

### Post by Paul_Jewell on 2014-10-17
Hello and greetings. 

I manage an ubuntu server with many users who will ssh from this server to another server to perform tasks. The second server is temporary and hosted on AWS. 
I am the one who manages setting up access to the second server as well and is changes often which makes things somewhat tedious with authentication. 

Basically what I am looking for is a way to add rsa keys for the users programatically so that they may just log in and type "ssh user@server" and it will just work for them. The main hurdle here is that I have the keyfile for one user 'ubuntu' but not for any others without going through some kind of strange password juggling. For example, supposing I knew the password for a user, I could run these commands to set them up:

$ sudo su username
$ ssh-keygen
$ ssh-copy-id user@server
$ <password>
$ yes / ok / whatever 

And they are set up. I need something similar but without having to know every user's password, and instead use my administrate .pem file, which allows root access on the second remote server,  to allow the users to authenticate. 
If there is not an easy way I could just generate random passwords and use those, but that is a last resort. 

Let me know if any of you have an idea.

---

### Post by TheFu on 2014-10-17
a) Use sudo su - username (this will set up HOME properly), then use ssh-keygen.
b) After all the ~/.ssh/id_rsa.pub files are generated for every userid, I'd rename them to beauthorized_keys.$logname and push them all to the AWS server, then manually shove them into the ~/.ssh/authorized_keys file for each matching userid. Make certain the ~/.ssh/ directory is 700 and the ~/.ssh/authorized_keys file is 600 and both are owned by the userid.

When you know the password, ssh-copy-id is easier, but when you don't .... shoving the public key into the auth...keys file works fine - no password needed - well - at least not for these users.  Plus the users won't need to know their own passwords on the AWS instance either.

For 10 people, I'd do this manually. For 11+, I'd write a script ... or just use ansible.

---

