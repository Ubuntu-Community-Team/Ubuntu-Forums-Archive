---
title: "Logging into Linux box from Mac"
date: 2008-08-18
forum: New to Ubuntu
---

### Post by rgraves on 2008-08-18
I'm having trouble logging into my linux box - Ubuntu 8.04 - from a Mac.

I get the box to enter username and password but keeps giving me message saying username and password are invalid.

I've tried using the IP address for the linux box with same result. OpenSSH is installed on the linux box. I can connect to the Mac from the linux box using SSH and typing in IP address, then username and password, but can't go from Mac to linux box.

I'm sure there is a setting somewhere I haven't set right.

Thanx,
bob

---

### Post by meanburrito920 on 2008-08-18
What is the error it gives you when it fails?

---

### Post by Oldsoldier2003 on 2008-08-18
> **meanburrito920 said:**
> What is the error it gives you when it fails?

using the -v switch with ssh will give even more insight into what is going on.

edit: this is assuming that you are using openssh. you might also want to look at your auth.log on the linux box.

---

### Post by rgraves on 2008-08-19
It's not really an error message. It just says my username and password are invalid.

I'm typing the same username & password I log onto the linux box with. it just won't let me connect.

I'm confused as to what I should be typing in on the Mac.  Username & password, IP address and password or a variation of the two.

Any settings on the linux box or the Mac I should be setting? Seems like it should be a simple setting that I'm missing.

---

### Post by meanburrito920 on 2008-08-19
Have you made sure your public key is on the box to be accessed?

---

### Post by neurostu on 2008-08-19
What I do when I want to SSH into a specific machine is:
```

ssh <UsernameAtRemoteMachine>@<IPofRemote>

```

so lets say I had a login name of foo on a machine with an ip of 127.0.0.1 I would type:
```

ssh foo@127.0.0.1

```
I would then be prompted for the foo's password...

Make sure that: ** openssh-server ** is installed on the machine you're trying to connect to.

ps. I know that 127.0.0.1 is the loopback IP address I couldn't think up a better IP to use in the example...

---

### Post by tgalati4 on 2008-08-19
From your post, it's not clear what you are trying to do.

If you are trying to access a network share, then you use your short mac name and mac user password.  

If you are trying to log in via ssh from the mac to ubuntu then you might need to add your ubuntu machine name in your mac's /etc/hosts file.

Without a /etc/hosts entry then you would need:

ssh -vvv yourubuntuusername@192.168.1.100

This presumes that you have already installed openssh-server on the ubuntu machine.

sudo apt-get install  openssh-server

---

