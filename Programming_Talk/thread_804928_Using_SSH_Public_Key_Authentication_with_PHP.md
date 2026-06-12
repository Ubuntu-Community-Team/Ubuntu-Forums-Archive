---
title: "Using SSH Public Key Authentication with PHP"
date: 2008-05-23
forum: Programming Talk
---

### Post by steve_c on 2008-05-23
I'm developing a website with PHP where I want the web server to pass information via SSH to a separate jobs server to process.

Now I'm pretty sure what I want here is to use public keys so that the servers can talk without needing to password authenticate every time.

What I'm having a hard time figuring out is how to generate the SSH keys initially. The PHP pages are executed by a non-login user, wwwrun, which also obviously doesn't have a .ssh directory to store the key in.

What is the best way for me to do this? Do I need to use a bunch of exec() statements to create the key and pass it a blank passphrase when it asks for one? Where can I store it?

The web server does not have the PECL SSH2 extension installed, if that makes a difference.

Thanks for any help.

---

### Post by dwhitney67 on 2008-05-23
Is it SSH you want to use, or do you mean SSL (now, TLS)?  Read this wiki:  [Transport Layer Security]("http://en.wikipedia.org/wiki/Secure_Sockets_Layer")

---

### Post by steve_c on 2008-05-23
The web site basically contains forms that allow users to generate configuration files for some scripts. The way that seems easiest to me is to go ahead and generate those configuration files on the web server and use SSH to copy the configuration files to the job server and launch the scripts that will process the configuration files. 

If you think there's a better way to do this, I'm open to suggestions. I like to do things the best way possible. At the same time, this is the way that I'm most familiar with so that's why I was going that route.

---

### Post by slavik on 2008-05-23
so the web users don't need their own SSH stuff, you just need to build trust between your web server and the job server to allow rpc (remote procedure call) through ssh/rsh.

If the above is correct, then it's a one time set up between the web server and the job server.

---

### Post by steve_c on 2008-05-26
Yes slavik, that's correct.

---

### Post by slavik on 2008-05-26
look up on moving keys around ...

then you can just do: ssh web_server@job_server 'command'

---

### Post by steve_c on 2008-06-17
Just for future reference for anyone else with this issue, here's what I wound up doing:

First of all, I created the key for the user wwwrun by editing /etc/passwd and changing the default shell for the user from /bin/false to /bin/bash. That allowed me to use 'su wwwrun' to log in as the wwwrun user. Using 'cd ; pwd' I found that wwwrun actually does have a home directory inside the filesystem, so that's where I used ssh-keygen to create the key pair and copied the public key to the remote server.

I made sure to edit /etc/passwd to change wwwrun's shell back to /bin/false, and now no-login scp is working just fine.

Thank you guys for your help.

---

