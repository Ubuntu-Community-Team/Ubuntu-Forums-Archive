---
title: "Unable to use apt: I wasn't able to locate file for the ... package."
date: 2008-05-26
forum: New to Ubuntu
---

### Post by ohaleck on 2008-05-26
Hello,
Recently, I tried to install vmware-server from a deb package converted from rpm alien. The installation did not succeed and it broke the package managers' internal data so that any attempt to use the Update Manager, Synaptic, Aptitute or apt-get ends in the same message:

```
Writing extended state information... Error!
E: I wasn't able to locate file for the vmware-server package. This might mean you need to manually fix this package.
```

I tried to unmark the package from being removed using Synaptic and aptitude. The former just does not do, nor report anything; the latter gives the same "I wasn't able..." message.
I tried various ways of unlocking, cleaning, autoremoving, purging etc. I even removed the vmware-server entry from the /var/lib/aptitute/pkgstates and it did not help.

Now, I need to make my Ubuntu simply forget about the package as I managed to get the VMware Server running in a different way, and I need my apt-get working again, but how can I do it?

Thanks,
OHaleck

---

### Post by Kulgan on 2008-05-26
Have you tried refreshing the sources and updating? 

If that doesn't work, try 
```
apt-get -f install
```

---

### Post by Xiong Chiamiov on 2008-05-26
Using alien is generally a bad idea, as it does screwy things a lot.  There's a nice guide over [here]("http://ubuntuforums.org/showthread.php?t=788169&highlight=howto+vmware") for what you're wanting to do.

---

### Post by shifty_powers on 2008-05-26
heh, that's exaclty why i won't touch alien with a barge pole.

good luck sorting it out ;)

---

### Post by ohaleck on 2008-05-26
Thanks guys for your quick replies.
Indeed, that was the last time I used alien :)

I managed to install vmware using this tutorial:
[http://blog.creonfx.com/linux/how-to-install-vmware-player-workstation-on-2624-kernel](http://blog.creonfx.com/linux/how-to-install-vmware-player-workstation-on-2624-kernel)
Anyway, what I need now is to fix apt.

@Kulgan: I tried it and here is what I got:
```
$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be REMOVED:
  vmware-server
0 upgraded, 0 newly installed, 1 to remove and 18 not upgraded.
1 not fully installed or removed.
After this operation, 704MB disk space will be freed.
Do you want to continue [Y/n]?
(Reading database ... 106762 files and directories currently installed.)
Removing vmware-server ...
[: 62: Illegal number: remove
shift: 62: can't shift that many

dpkg: error processing vmware-server (--remove):
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 vmware-server
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by Kulgan on 2008-05-31
Looking around, I've found something that may help. At least, it makes sense...

One is:
> 
doing this usually helps

```
cd /var/cache/apt/archives
sudo rm -rf *
sudo mkdir partial

sudo apt-get update (perhaps 2x)
sudo apt-get upgrade
```

(I really don't get why people don't use sudo -s instead of sticking sudo everywhere... )

And the other:
> I had a similar problem and what i found that worked for me was going into /var/lib/dpkg/info and deleting everything that had that name and you may also have to go into /var/cache/apt/archives and do the same thing. I'm fairly new to linux so if this breaks anything i am sorry. i haven't run into any problems yet that this has caused.
Make sure you update and upgrade after that, though - assuming it works..

---

### Post by ohaleck on 2008-06-02
Thanks Kulgan,

I finally made it by deleting /var/lib/dpkg/info/vmware-server.postrm and cleaning the contents of vmware-server.list (to make sure my vmware, which I had installed using the tgz package doesn't get deleted).

I must confess I did not know that all these apt* tools are just wrappers of dpkg and I should look for the package infos in dpkg's directories.

---

### Post by Xiong Chiamiov on 2008-06-02
Apt-get, aptitude, synaptic, adept, etc. are all frontends to apt, the advanced packaging tool (or something like that).  Dpkg is an essential part of that, as it deals with the actual package management.

> **Kulgan said:**
> (I really don't get why people don't use sudo -s instead of sticking sudo everywhere... )

Because you can easily do something you didn't want to do if you're operating in a root shell.  It's a nice thing to do sometimes, but it's best not to recommend it to people, incase they forget to "exit".

---

### Post by Kulgan on 2008-06-02
> Because you can easily do something you didn't want to do if you're operating in a root shell. It's a nice thing to do sometimes, but it's best not to recommend it to people, incase they forget to "exit".
Ok :D
Bad habits from the pre-ubuntu "real root" times...

@ohaleck:
Glad it worked. Not having apt is a real pain.

---

### Post by haylocki on 2009-09-18
Hi, old thread I know, but I wanted to keep all the solutions to this problem in one place.

I recently trashed my Jaunty 64 bit installation using alien on the vmware-server version 2.0.1 rpm, and installing the deb package using dpkg.

After following the advice in this thread my problem still remained.

The solution on my system was to :

```
sudo gedit /var/lib/dpkg/status
```

Then used the find option to find "vmware".

I then deleted the whole section relating to the vmware-server.

After a 

```
sudo apt-get update
sudo apt-get upgrade
```

My system was working again.

Cheers, Ian

---

