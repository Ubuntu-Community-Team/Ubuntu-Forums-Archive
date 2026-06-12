---
title: "UBUNTU to UBUNTU file sharing (HELP!)"
date: 2013-07-31
forum: New to Ubuntu
---

### Post by jimbob80 on 2013-07-31
Hello all,
I am a new Ubuntu user whom has take the leap and left Windows behind! Loving it so far. :)

I am having major issues getting my laptops to talk to each other. Both have identical installs of Ubuntu 13.04 but I cannot for the life of me figure out how to access folders on each machine.
For example, I have my Music folder in my home drive on one machine and I would like to move new music across to the music folder on my other laptop.

How is this done (easily)? I have attempted to follow SMB and SSH instructions via Google but to no avail.

Your assistance would be greatly appreciated.

:D

---

### Post by 3eLtehF on 2013-07-31
as far as i know the computers need to be in same network.

folders should be shared and then you can follow SMB instructions.

i would look for the answer as even i would like to see the solutions coming for this one.

---

### Post by MG&amp;TL on 2013-07-31
There is (perhaps unfortunately) a lot of ways to do this on unix-like operating systems (of which Ubuntu is one).

I'll talk you through the SSH method, this works for me quite nicely.

First, on all of your machines, install the *openssh-server* software package by searching in the ubuntu software centre, or by using this command:

```
sudo apt-get install openssh-server
```

Then, say you have a machine with a hostname of "foo" (this is the 'network name' you set in the installer) that you wish to connect to from another machine, say "bar". On "bar", open the file manager, and press Ctrl + L. In the box that appears at the top, type:

```
sftp://foo
```

You should get a dialog box asking for a username and password, which you should fill in with the username and password for the "foo" machine. You should then be able to browse files on "foo".

I can expand on any of the steps if you would like. :)

---

### Post by jimbob80 on 2013-07-31
You are an absolute legend! I bow to thee! :D
Thank you!

---

### Post by Morbius1 on 2013-07-31
One of the great ironies in Linuxdom is that Samba in an all Linux or a Linux/OSX network works much better than in one containing Windows:

Open Nautilus > Right click your Music folder > select Sharing Options > mark all the boxes. If you don't have samba installed it installs it for you.

On the client:
```
nautilus smb://foo.local
```
[COLOR=#0000cd]*Don't forget the .local*[/COLOR]

Ba Da Bing

As long as you haven't done irreparable damage to your smb.conf file by following some guy with a bad HowTo or gone out of your way to disable avahi on either system you should be good to go.

Nothing wrong with SSH - I use it myself - but as described here the client user has at a minimum read access to everything on the server. Samba restricts you to the Music folder or whatever specific folders you have shared.

---

