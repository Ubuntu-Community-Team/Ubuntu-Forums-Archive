---
title: "[SOLVED] Share files between 2 ubuntu pc's"
date: 2008-06-08
forum: New to Ubuntu
---

### Post by billgoldberg on 2008-06-08
So I went into gksudo nautilus and shared two folders (prompted to install samba).

I see my pc on my laptop, but can't seem to access the folders (they don't appear).

What step am I missing?

*ps: I did the same on my laptop to install the service.*

---

### Post by billgoldberg on 2008-06-08
Isn't samba ment to share files between windows and ubuntu, wouldn't ssh (openssh) be better?

How would I install openssh and get it working (ubuntu doc's not helping much).

---

### Post by frankos44 on 2008-06-08
I agree, openssh is secure and easier to set up. On each machine:

$ sudo apt-get install openssh-server openssh-client

Then to connect to the other pc click Places->Connect to Server, example attached.

---

### Post by billgoldberg on 2008-06-08
> **frankos44 said:**
> I agree, openssh is secure and easier to set up. On each machine:

$ sudo apt-get install openssh-server openssh-client

Then to connect to the other pc click Places->Connect to Server, example attached.

I'll test that one out, i'll report back in a few minutes to tell if it's working or not.

---

### Post by billgoldberg on 2008-06-08
Well that was easy.

[SOLVED]

---

### Post by frankos44 on 2008-06-08
> **billgoldberg said:**
> Well that was easy.

[SOLVED]

Great, please of helped. 

Also you can securely send files from one pc to another using the terminal as follows:

Example 1
$ scp *.doc tina@192.168.0.5:/home/tina

Example 2
$ scp [email]tina@192.168.0.5:/home/tina/abc.jpg[/email] ./

Example 3
$ sftp tina@192.168.0.5
sftp> help (give list of commands)

---

### Post by Rytron on 2009-06-09
> **frankos44 said:**
> I agree, openssh is secure and easier to set up. On each machine:

$ sudo apt-get install openssh-server openssh-client

Then to connect to the other pc click Places->Connect to Server, example attached.

Thank you frankos44 for this tip. I was having trouble with Samba. This works fine.
):P

---

### Post by clive littlewood on 2009-06-09
Hi

Another interesting file share between "Ubuntu's" is GIVER.

It is in the repos and see my Blog in signature for details.

Have fun

Clive

---

### Post by QKC on 2009-12-02
Hi,
I have configured SSH for both of my ubuntu system.I can log in from my(DELL) pc to (OEM) pc but then I can't log into to my OEM pc to the (DELL) pc.Is there any problem? I have both the pc install SSH.Can someone tell me what is wrong? By the way,since both pc is using SSH, can i log in from another pc from outside using another browser?

Thanks
GJQ

---

