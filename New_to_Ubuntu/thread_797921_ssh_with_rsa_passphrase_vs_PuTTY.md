---
title: "ssh with rsa passphrase vs PuTTY"
date: 2008-05-17
forum: New to Ubuntu
---

### Post by edmicman on 2008-05-17
I just moved from WinXP to Ubuntu 8.04 full time.  I'm trying to access a remote server via SSH.

On Windows, I used putty; I'd put in the remote server address, it would connect, ask if I wanted to save/accept the key or something, I'd hit OK, and then be able to log in to the remote server.

On ubuntu, I opened a terminal, typed "ssh myremoteserver", it connected, asked if I wanted to accept the key, and then it prompts for a password.  I assume this is something key related due to the forums I search, plus it's before I get to any sort of login screen on the remote server.

After some searching I came across the command "ssh-keygen -t rsa" which it sounded like I could set the passphrase it was asking me, or set it to nothing.  I did that, but it's still asking for some password using the terminal.  I did install putty on Ubuntu and it works just like on Windows, and I was able to do what I wanted.

My question is, how should I be doing this, or what am I doing wrong?  What is putty doing for ssh that the terminal is/isn't?  I'm OK with entering a passphrase or whatever to do ssh stuff if I need to, though it does seem kind of annoying at first.  Why can't I just type "ssh myserver" and have it work?  Thanks for any info!

---

### Post by bodhi.zazen on 2008-05-17
A few thoughts.

first, putty is available on Linux.

second, it sounds like you are using a key to connect w/ putty (a passwordless key tisk tisk). fire up putty on Windows and load the server you are connecting to.

Click the + in the panel on the left under ssh and go to the Auth tab. There do you see anything under the window tot eh immediate left of the "Browse" button ?

If so, that is your key.

You can copy it to Linux and use it w/ putty.

However if you want to use the key from linux on the command line you need to convert it. Putty uses it's own format while ssh is different.

Keys Convert : [http://www.linux-sxs.org/networking/openssh.putty.html](http://www.linux-sxs.org/networking/openssh.putty.html)

linux : 
                [http://linux.die.net/man/1/puttygen](http://linux.die.net/man/1/puttygen)

                puttygen mykey.ppk -O private-openssh -o my-openssh-key


Or you can generate a new key. You will need access to the server however ...

Can you post the output you are getting from the ssh connection ? You can copy - paste from the terminal.

[http://alblue.blogspot.com/2005/08/howto-ssh-logins-using-keys.html](http://alblue.blogspot.com/2005/08/howto-ssh-logins-using-keys.html)

---

### Post by Oldsoldier2003 on 2008-05-17
Putty is nice but stripping your passkey of its passphrase is bad juju. I prefer using the openssh client that ships with Ubuntu.

---

### Post by edmicman on 2008-05-17
Interesting, thanks for the replies!  I've always used putty on Windows for any SSH connections, and didn't realize it was doing weird or less-than-secure methods.  So is the "correct" way to do things to generate a key on the remote server, copy that key to your local machine, and then everything's kosher?  Or the other way around?  Is there like a newbie's guide to SSH somewhere since I apparently missed out on how it's supposed to work?  :-)

---

### Post by bodhi.zazen on 2008-05-17
Look here :

[uwiki]SSHHowto[/uwiki]

[uwiki]AdvancedOpenSSH[/uwiki]

and the link I gave you.

It does not matter where you generate the keys or what you name them.

I use :

```
ssh-keygen -t dsa -f <key_name>
```

where "<key_name> is a name I give to the key, say foo

This will generate a key pair foo and foo.pub

The names are confusing.

Put foo on the client in ~/.ssh. chmod it to 400 (read only) and owned by your user.

Put foo.pub on the server in ~/.ssh and rename it to ~/.ssh/authorized_keys2

chmod it to 400 (read only).

now, from the client, 

ssh user@server -i ~/.ssh/foo

---

