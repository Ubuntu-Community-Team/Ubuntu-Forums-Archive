---
title: "NoMachine NX help needed"
date: 2008-10-05
forum: New to Ubuntu
---

### Post by Konstabel on 2008-10-05
I am trying to get a remote desktop running. I have installed all necessary software and can manage to get through NX's authentication. A big white and red IM appears and then a message that states :

*unable to connect to host: Connection refused (111)*

Anybody that can help me please in solving this?

---

### Post by wd5gnr on 2008-10-05
NX uses ssh. So the first thing to do is see if you can ssh to the machine. Sounds like you can't. 
From the client machine try:

ssh -l myuserid my_remote_host

Making the appropriate substitutions for myuserid and my_remote_host. If you are using a Windows client (ugh) install Cygwin or Putty to get ssh.

If you can't login -- make sure sshd is installed and running.

If you can, then did you change the NX security certificate? NX authenticates to itself using it. So if you change it on the server, you will need to get the public key installed on the client.

On Hardy I have had NX work (well) but the remote sound is not set up to be very useful unless you have everything already set to use ESD.

---

### Post by Konstabel on 2008-10-05
SSH is working fine, that is at the moment how I do everything that I have to do on the remote machine.

Can you please explain the certificates thing?

---

### Post by wd5gnr on 2008-10-05
If you didn't change anything you should be ok. The NX server has a certificate that it uses to authenticate the clients. By default this is a "standard" cert and the clients all have this. 

However, if you have changed it (or even if you aren't sure) you can go get the certificate using scp from the server to the client. Then in the configuration for the connection, look at the General tab in the Server box and press the Key button. You need to put the Private key in that box (or use Import).

Read section 4 of [http://www.nomachine.com/documents/admin-guide.php](http://www.nomachine.com/documents/admin-guide.php)

Also note that you MUST have a password on your account for things to work.

---

### Post by Konstabel on 2008-10-06
I have done what you said, even reinstalled the NX software completely. Added new keys ....

But still I cannot manage to connect to my remote desktop. I keep getting a 111 error : Connection refused.

You mention that I must have a password on my account, which account would that be? On my normal login account (for the computer) there is a password.

---

### Post by Konstabel on 2008-10-06
Anybody out there that might be able to help. Anything will be appreciated

---

### Post by handydan918 on 2008-10-06
Two things:
1) Is ssh-server installed (and running!) on the remote machine?

2)Is there a firewall on the remote machine that may be blocking port 22?

---

### Post by Konstabel on 2008-10-06
SSH is running and working. I can log into the remote machine with putty. 

Concerning the firewall: If Hardy has one by default then yes. I did not install one.

---

### Post by fldav76 on 2008-10-30
I just went through this process of setting up NX. here is my version of a guide
[http://ubuntuforums.org/showthread.php?t=901760](http://ubuntuforums.org/showthread.php?t=901760)

i started with a blank hardy install. so that's what my guide assumes. if you have other stuff (samba, etc) it may be interfering.

good luck

---

