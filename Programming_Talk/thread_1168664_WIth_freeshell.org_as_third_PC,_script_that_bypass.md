---
title: "WIth freeshell.org as third PC, script that bypass all firewalls (ingoing) for SSH ?"
date: 2009-05-24
forum: Programming Talk
---

### Post by frenchn00b on 2009-05-24
Hello, 

I am looking for home purpose a way to connect to a relative of mine.

He runs (remote):
./ssh_3bypass_server.sh

I run (master that has the control of console on remote):
./ssh_3bypass_client.sh
 
and I can install him his Linux box. Man, that's so unlucky that I cannot finish installing a one +1 Linux machine for spreading Linux :( 

Happy Tux

---

### Post by soltanis on 2009-05-24
I think you're looking for an SSH tunnel (can be done in a single command, script not required), specifically a reverse SSH tunnel, whereby your computer listens for an inbound connection, and his computer initiates an SSH connection to your computer.

Then, you can connect to a local port on your computer, and ssh automagically routes that session back to your relative's computer (through the firewall) over a secure connection.

But for the life of me I have never been able to figure out how the command goes (the man page is really confusing).

EDIT.

Okay, so this requires editing configuration files.
In your relative's computer (the one behind the firewall):
```

# In file ~/.ssh/config
Host host-name
    Hostname [YOUR computer's IP address]
    RemoteForward [port number]:localhost:22
    User [YOUR username]

```

Now, have your relative run
```

ssh host-name
[YOUR username]'s password: [enter the password for YOUR username]

```

Once the connection is established, on your computer run:

```

ssh -p [port number] [relative's username]@localhost
[relative's username]'s password: [enter your relative's username's password]

```

And then you should have a remote shell into his machine.

EDIT 2.

Without editing configuration files, this is also possible (using the same [names]). Run this command, instead of doing steps 1 and 2, on your relative's machine (have him run it).

```

ssh -R [port number]:localhost:22 [YOUR username]@[YOUR address]
[YOUR username]'s password: [enter YOUR username's password]

```

I hope you can understand all this, it confuses the heck out of me (I mix up all the addresses and ports).

---

### Post by frenchn00b on 2009-05-24
**side ssh server: There is at least two - three firewalling / routeur with only limiting to port 80, at least. Forget any ideas of port forwarding, anythign, but stupid ssh outgoing to port 22 and whatever port works in SSH**

seems maybe a soluation
thank you for filling hte scripts, that's making life easier

---

### Post by frenchn00b on 2009-05-24
> **soltanis said:**
> Now, have your relative run
Code:

ssh host-name
[YOUR username]'s password: [enter the password for YOUR username]
.

something that I dont understand.
my relative starts SSH ok, but it will be private to him, no?
I cannot use his SSH connection with is activate, to write in his SSH back?

---

### Post by soltanis on 2009-05-25
The connection is set up in the config file to run a reverse tunnel. He's not actually logging in to start a session; he's actually telling the ssh server on your side to start listening on the [port number] you specified for a local connection.

To use that, on your side you do
```

ssh -p [port number] [username]@localhost

```

That will connect to the forwarded port. This notifies your relative's computer that someone is connected to the forwarded port; that computer then starts a login shell, and all traffic thereafter is forwarded over the first SSH connection your relative made to your computer.

Get it?

---

### Post by frenchn00b on 2009-05-25
> **soltanis said:**
> The connection is set up in the config file to run a reverse tunnel. He's not actually logging in to start a session; he's actually telling the ssh server on your side to start listening on the [port number] you specified for a local connection.

To use that, on your side you do
```

ssh -p [port number] [username]@localhost

```

That will connect to the forwarded port. This notifies your relative's computer that someone is connected to the forwarded port; that computer then starts a login shell, and all traffic thereafter is forwarded over the first SSH connection your relative made to your computer.

Get it?
 
 
ahh
so if my friend run this script, then 
```

Without editing configuration files, this is also possible (using the same [names]). Run this command, instead of doing steps 1 and 2, on your relative's machine (have him run it).

Code:

ssh -R [port number]:localhost:22 [YOUR username]@[YOUR address]
[YOUR username]'s password: [enter YOUR username's password]


```

I can ssh.

so:

./ssh-traversal-server.sh
```
#!/bin/sh
echo "type pass1"
read $passwt1
echo "type pass2"
read $passwt2
ssh -R [port number]:localhost:22 [YOUR username]@[YOUR address]
$passwt2: $passwt2
```

Thanks I am slow with the undsersstandning of this thing

---

### Post by frenchn00b on 2009-05-25
[B][COLOR="Red"][http://souptonuts.sourceforge.net/sshtips.htm](http://souptonuts.sourceforge.net/sshtips.htm)
man, by my relative all is blocked ingoing

he can just do RELATIVE => firewall => port 22 outgoing to freeshell.org or whatever hold ssh server port 22[/COLOR][/B]

---

### Post by frenchn00b on 2009-05-25
this page is of no use: [http://souptonuts.sourceforge.net/sshtips.htm](http://souptonuts.sourceforge.net/sshtips.htm)

for my tunnelling :(


[http://img33.imageshack.us/my.php?image=sshfrenchloopback.jpg](http://img33.imageshack.us/my.php?image=sshfrenchloopback.jpg)

---

### Post by soltanis on 2009-05-25
That shell script won't properly input the passwords for you.

You need to make sure you have an SSH server running on your machine, and you need to give your relative access to your account (or otherwise create an account for him that he has the password to). He needs this to log in to your machine and set up the tunnel.

I would suggest that you use the single-command ssh option instead of editing your configuration lines; if you're talking to your relative over IM or the telephone, its a little harder to tell him what to type, but the end result will be easier than messing with configs.

As soon as your relative tells you that the command completed (i.e., no prompt is showing up on the terminal anymore, and it didn't say something like access denied) then you should be able to use the tunnel by sshing into the port on your machine.

If you have any more problems, please detail them so I can better help you.

---

### Post by frenchn00b on 2009-05-25
I may have it partially:

cat sshserver.sh
```
#!/bin/sh
# user@ip
# $2 shall be -p
# $3 is the port on the target
ssh -R 5637:localhost:`cat /etc/ssh/sshd_config  | grep Port | cut -d' ' -f 2`  $1 -p $3
```

cat sshclient.sh
```
#!/bin/sh
# $1 is the user
# $2 shall be -p
# $3 is the port on the target
# ssh -R 5637:localhost:`cat /etc/ssh/sshd_config  | grep Port | cut -d' ' -f 2`  $1 -p $3
ssh $1@localhost -p 5637
```

---

### Post by soltanis on 2009-05-25
The -R only needs to go on the computer that is initiating the reverse tunnel. When the tunnel is set up, to use it, all you need to do is run

```

ssh -p [port] [user]@localhost

```

No -R.

---

