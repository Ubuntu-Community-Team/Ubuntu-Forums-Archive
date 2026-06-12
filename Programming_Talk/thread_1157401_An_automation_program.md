---
title: "An automation program?"
date: 2009-05-12
forum: Programming Talk
---

### Post by wlraider70 on 2009-05-12
I hope this is the right place.

I am thinking about writing a program that will automate a few things. I need to ...

1) open a terminal
2) ssh to a given box
3) establish a VNC connection, through the ssh.

I have all these things set up, is there a way I could program a single program to open all these task and execute a predetermined command(S).


I'm pretty amateur with programing, so if this is a hugh task it might be beyond me.

Thanks.

---

### Post by gtr32 on 2009-05-12
Are you thinking of getting a SSH connection from computer X to A and from there making a VNC connection to computer B.

Something like this:
X -> internet SSH -> A -> VNC LAN -> B

If so, then...

1) OPTIONAL (to skip password query): make SSH key pairing between X and A, f.e. [http://sial.org/howto/openssh/publickey-auth/](http://sial.org/howto/openssh/publickey-auth/)

2) create a launcher or script with this command: ssh -X address.of.A vncviewer address.of.B:DISPLAY_NUMBER

Replace address.of.A with the real address of course, same with B, and DISPLAY_NUMBER, for example:

ssh -X 192.168.0.2 vncviewer 192.168.0.3:1

If running from command line w/ script, add '&' in the end.

---

### Post by wlraider70 on 2009-05-12
The ssh is from A to B through the internet
and then the VNC is tunneled through the SSH for security.

So for that reason, ssh has to be established before VNC can, further adding to the possibility for confusion.

---

### Post by gtr32 on 2009-05-12
Are both Linux machines or is B a Windows machine?

Either run the X program straight without VNC:

ssh -X remotehost'program'

or script it (first is ssh with port forward):

ssh -L 5900:127.0.0.1:5900 remotehost
vncviewer 127.0.0.1:0

---

### Post by Dill on 2009-05-12
*expect* is also nice for things like this: [http://bash.cyberciti.biz/security/expect-ssh-login-script/](http://bash.cyberciti.biz/security/expect-ssh-login-script/)

Cheers,
Dill

---

### Post by wlraider70 on 2009-05-14
So i have the script set to start the ssh session.

then the the terminal asks for the passphrase. 
What 

type of code would i put into to make it enter the pass.
"command" didn't work?

---

### Post by gtr32 on 2009-05-14
I'm assuming it is asking for SSH password. Here's how you create a key pairing (with empty password).

Create keys in computer A:

```
comp_a$ mkdir ~/.ssh
comp_a$ chmod 700 ~/.ssh
comp_a$ ssh-keygen -q -f ~/.ssh/id_rsa -t rsa
Enter passphrase (empty for no passphrase): <enter>
Enter same passphrase again: <enter>
```

Copy the public key to computer B:

```
comp_a$ scp ~/.ssh/id_rsa.pub address.of.comp_b:/home/user_name/

```

Set the key in computer B:

```
comp_b$ mkdir ~/.ssh
comp_b$ chmod 700 ~/.ssh
comp_b$ cat ~/id_rsa.pub >> ~/.ssh/authorized_keys
comp_b$ chmod 600 ~/.ssh/authorized_keys
comp_b$ rm ~/id_rsa.pub
```

Now try the script.

---

### Post by wlraider70 on 2009-05-14
it going to take me a day or two to do that.
is there no simple command to ether the password for me?


the next question i will have is how do i get it to enter a password into my VNC server.

will that be possible since it is a GUI. 
im using tight vnc.

---

### Post by gtr32 on 2009-05-14
If you already have access to both machine, it should take you about 5 minutes to do that. 

As for VNC, I don't know as I don't really use it. I guess you could just put the password in the script (-passwd option) and secure the script so others can't read it.

---

### Post by UbuKunubi on 2009-05-14
I don't know if the OP will find this usefull, but have a look for xdotool. 

Personal there are some tasks that I do which would too long to code up 'properly' so I direct the mouse, mouse clicks, and keyboard input to an application.

I know its not a 'professional' solution, but ideal for personal tasks.

---

### Post by wlraider70 on 2009-05-14
...error... sorry

---

