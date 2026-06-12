---
title: "add-apt-repository doesn't work because of keyservers"
date: 2018-01-22
forum: New to Ubuntu
---

### Post by fxdave on 2018-01-22
Hi, 
my PC is behind a proxy by university and I am sure it allows 80,443,22 ports. 
So i wanted to setup hkp://keyserver.ubuntu.com:80 .

I have just misconfigured something. 
Trying to reset keyservers, but i haven't found any solutions. 
I found a command but i cant understand why is it needed : ```
sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys 2EA8F35793D8809A
```
I have few questions:
What recv-keys are? 
What kind of protocol hkp is. 
How to set proxy behind it? 
Is it really solution for my problem?

Example:
```

$ sudo add-apt-repository ppa:webupd8team/atom
 PPA for Atom text editor: https://atom.io

Now available for both 32bit and 64bit!

More info, report packaging bugs, feedback, etc.: http://www.webupd8.org/2014/05/install-atom-text-editor-in-ubuntu-via-ppa.html

Report non-packaging Atom bugs here: https://github.com/atom/atom/issues
 More info: https://launchpad.net/~webupd8team/+archive/ubuntu/atom
Press [ENTER] to continue or Ctrl-c to cancel adding it.

gpg: keybox '/tmp/tmpk20a8tc5/pubring.gpg' created
gpg: keyserver receive failed: No keyserver available
Failed to add key.

```

How can I fix this?

---

### Post by QIII on 2018-01-22
Hello.

Have you spoken with the University's network administrators?

---

### Post by fxdave on 2018-01-22
Once I tried for port 21 to be able to connect via ftp. He didn't change anything.
There must be another solution.
I have got vpn but I dont want to use every time when I want to download a package.
But it is eneugh to me if i could reset de keyservers to the default. Can you help me with that? I don't want to reinstall my OS.

---

### Post by QIII on 2018-01-22
What did the Uni's network admins say?

---

### Post by fxdave on 2018-01-22
They said I am allowed to connet via ftp. Oh and he was right, but only via plain FTP, and the most common ftp clients use TLS. So port 21 is also open.
But why is it important?

---

### Post by QIII on 2018-01-22
Because we don't know what the network setup may be.

My guess is that hkp is a typo and it should be http to retrieve the key.

---

### Post by fxdave on 2018-01-22
I have tried before.
```

$ sudo apt-key adv --keyserver http://keyserver.ubuntu.com:80 --recv-keys 2EA8F35793D8809A
[sudo] password for dbiro: 
Executing: /tmp/apt-key-gpghome.nsVqQ6tguM/gpg.1.sh --keyserver http://keyserver.ubuntu.com:80 --recv-keys 2EA8F35793D8809A
gpg: keyserver receive failed: No keyserver available

```

---

### Post by QIII on 2018-01-22
What is the script to which you are passing that?

I think your command may be malformed anyway.  I'm not at home on my Linux machine, but hopefully someone will be by to help shortly.

---

### Post by fxdave on 2018-01-22
As I understand, developers have to sign their application, and the signification is the key, and the keyserver stores the keys. Am I right?

In my case, ` gpg: keyserver receive failed: No keyserver available Failed to add key.`, so it can't access the keyserver. But I can ping the keyserver.ubuntu.com.
So add-apt-repository doesn't work with proxy?

In addition, I use budgie-ubuntu, so I don't have "Apply system wide" button in proxy settings, that plain ubuntu has.
I think I will go back to plain ubuntu. With budgie I have got a lot of problem.

---

### Post by fxdave on 2018-01-23
With VPN I could get the missing keys. Thanks for your help.

---

