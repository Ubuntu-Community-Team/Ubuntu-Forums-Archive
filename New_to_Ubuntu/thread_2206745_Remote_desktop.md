---
title: "Remote desktop"
date: 2014-02-20
forum: New to Ubuntu
---

### Post by jmriverofernandez-4 on 2014-02-20
Hi,

I have Ubuntu 13.10 installed in my laptop. I also installed Ubuntu 13.10 in the desktop I use at work. 
I usually run numerical calculations (using COMSOL) that last for days. 
I want to be able to access the desktop computer from my laptop at home. 
How can I do it?
I'm a beginner so please, explain it step by step (for dummies). 

Best regards,

Juan Manuel

---

### Post by TheFu on 2014-02-20
Contact your IT department for help using their existing VPN. Every company has a little different VPN, so we cannot really help for any other information.

Chances are that if YOU setup access to a work desktop from home is a violation of the corporate security policies and will get you fired.

---

### Post by jmriverofernandez-4 on 2014-02-20
I am a student of a master in Mechanical Engineering. It's not officially "work", the computer I use (wich is at my school) is for calculating simulations for my thesis project. There is no violation at all of corporate security if I access the computer in a remote way.

---

### Post by plucky on 2014-02-20
[Teamviewer 9](http://www.teamviewer.com/en/index.aspx?pid=google.r.uk.s.desk.vnc&gclid=CJDU9oTa27wCFYYBwwod3j8AAA) works for me.

Download and install on both computers and then set a password on the computer you wish to login remotely.

This works for me on 12.04.4 to control a remote Windows 7 system.

Good Luck

---

### Post by TheFu on 2014-02-20
> **jmriverofernandez-4 said:**
> I am a student of a master in Mechanical Engineering. It's not officially "work", the computer I use (wich is at my school) is for calculating simulations for my thesis project. There is no violation at all of corporate security if I access the computer in a remote way.

Then just run an ssh server and use any ssh client to remote in. Best to setup key-based authentication, NOT PASSWORDS.
ssh is the normal remote access method for UNIX/Linux systems.

If you need a remote GUI and it is not on the same network, then I like FreeNX as the server and any NX-client software on the other one. NX uses ssh, so the connection is secure, unlike many other options. There is an Ubuntu FreeNX howto.

Plus you don't have to give access to some 3rd party just to access your machines - like any of those go-to-my-pc offerings.

---

### Post by jmriverofernandez-4 on 2014-02-20
Thanks for your reply.
As I said before, I'm a beginner and I have very little notion of how to do this.
TheFu could you be more specific with the steps I have to follow to run an ssh server and use an ssh client?

---

### Post by Bill Tetzeli on 2014-02-21
I would say the easiest way would be to use Team Viewer and make absolutely sure on the school computer to use the whitelist option so that only your home computer is allowed to log in.  Otherwise, I'd go with using Remmina to make a VNC connection via SSH tunnel.  You'd need to download and install x11vnc and openssh-server on the school computer and your own, plus you'd need Remmina on your home computer as well.  You would need to:

- Set up x11vnc to run from boot on your school computer, as well as set up a login password.  Follow Steps 1, 2a and 3 from [this tutorial]("http://seb.so/vnc-from-boot-without-logging-in-ubuntu-lubuntu-xubuntu-and-mint-lmde/").  You should also add the flag **-localhost** when creating the startup script in /etc/init/x11vnc.conf (described in step 2a).  This will ensure that you can only connect via an encrypted SSH tunnel.

- [Set up a public/private key pair]("http://www.ece.uci.edu/~chou/ssh-key.html") to protect your connection to the school computer from hackers.  Two very important things: first, Prof. Chou doesn't say anything about adding a passphrase to the key pair.  You should.  You'll be prompted to.  Second, use the "RSA instead of DSA" method described in step 2 - much stronger encryption by several orders of magnitude.

- On the school computer, ensure you can only SSH into the system using a public/private key pair by typing in terminal

**sudo gedit /etc/ssh/sshd_config**

and change the defaults (if necessary) to the following:

PermitRootLogin no
PubkeyAuthentication yes
PasswordAuthentication no
X11Forwarding no

then save.  Leave everything else as is.


Reboot for the changes to take effect.


On your home computer you need to do the following:

-You may or may not need to set up x11vnc on your home computer just like on the school computer - I connect to and from all my home computers, so I've never not done it on any of them.
- You definitely do need to set up Remmina.

Open up Remmina.
Select Connection > New from the menu
In the top field type a name for the profile if you want to save it for future connections.
From the Protocol field select "VNC - Virtual Network Computing"
Below in the Basic tab input the IP address followed by the port, e.g. 123.456.7.8:5900 (5900 is the default VNC port); change Color Depth to something higher than 256 or you might get kicked off the instant you connect; Quality as you see fit - the higher the quality, the longer the lag.
Click the SSH tab and check the following buttons: Enable SSH Tunnel, Tunnel Via Loopback Address and Identity File (browse to and select /home/*user name*/.ssh/id_rsa (NOT id_rsa.pub)).
Click Connect.  If you've given your profile a name it will be saved automatically, and you can connect next time just by double-clicking on it.

You'll then be presented with two prompts.  The first will be for you SSH public/private key passphrase.  The second will be for the VNC password.  After that you'll be logged into your school's computer.

**NOTE:** Make sure your school computer's firewall is set to allow incoming SSH connections.
[B]
FINAL NOTE: [/B]If for any reason your computer is stolen, you should immediately notify the school's sysadmin to remove the reference to your public key from the /home/*user name*/.ssh/authorized_keys file on the school computer.  It's the equivalent of changing the locks once a key's been stolen.

---

### Post by TheFu on 2014-02-21
Of course all of this only works if the computer at school has a public IP. If it is private, then you'll need to run the ssh-server at home too, open ports on the router and run a reverse ssh connection from the school to your home ... authssh is a good way to do that.

I am terrible at instructions, so I must leave the details for you to discover through google.  Just put "ubuntu" with any google query to find the Ubuntu-specific instructions. Follow instructions from domains with "ubuntu" in the name and be extremely cautious about following steps that have source package compiling involved or require a signin account to anywhere besides the 2 PCs involved.  This stuff really isn't that hard, but there are many details that must be handled correctly, with an understand of what each command means.

---

