---
title: "New to Ubuntu, grub rescue error"
date: 2014-06-09
forum: New to Ubuntu
---

### Post by Middo on 2014-06-09
Hi All,

i am am totally new to Ubuntu, and yesterday made myself a USB to try it out.  I liked what I saw, so I did the install version that allows my windows to stay usable as well.  I had to partition the hard drive, but it has not worked.  I get an error message:

error: no such device: a253514d- etc
Entering rescue mode...
grub rescue>

And that is where I am stuck.  I have read heaps, and cannot get my mind around the problem.  I can't get into windows, and I can only run Ubuntu using the USB and doing an F12 to select it as the boot device.  Where to from here?  Help me please.  I thought Ubuntu would be a good choice, but it looks like I now have no working computer...

---

### Post by kc1di on 2014-06-09
I would download Boot-Repair form [here. ]("https://help.ubuntu.com/community/Boot-Repair")

follow the instruction on the web page.  It finds many boot problems and fixes them. 
Good luck.
and Welcome to Ubuntu.

---

### Post by Impavidus on 2014-06-09
Something went wrong during partitioning your drive. We need more details to be able to tell you what to do and whether you can still save Windows. Try running [Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair") from the live disk and post the link to the summary it provides here.

---

### Post by stalkingwolf on 2014-06-09
ditto

---

### Post by Navneet_Kumar on 2014-06-09
Hope..boot repair works,otherwise try re-installing ubuntu safely..........:D.

---

### Post by Middo on 2014-06-09
Thanks for the replies but...

I tried to do the boot repair option, using terminal from a live USB, and I get this error before I could even get to the end:



ubuntu@ubuntu:~$ sudo add-apt-repository ppa:yannubuntu/boot-repair
 Simple tool to repair frequent boot problems.

Website: [https://launchpad.net/boot-repair](https://launchpad.net/boot-repair)
 More info: [https://launchpad.net/~yannubuntu/+archive/boot-repair](https://launchpad.net/~yannubuntu/+archive/boot-repair)
Press [ENTER] to continue or ctrl-c to cancel adding it

gpg: keyring `/tmp/tmpmtbzr07c/secring.gpg' created
gpg: keyring `/tmp/tmpmtbzr07c/pubring.gpg' created
gpg: requesting key 60D8DA0B from hkp server keyserver.ubuntu.com
gpg: /tmp/tmpmtbzr07c/trustdb.gpg: trustdb created
gpg: key 60D8DA0B: public key "Launchpad PPA for YannUbuntu" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
OK
ubuntu@ubuntu:~$ sudo sed 's/trusty/saucy/g' -i /etc/apt/sources.list.d/yannubuntu-boot-repair-trusty.list
ubuntu@ubuntu:~$ apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13: Permission denied)
E: Unable to lock directory /var/lib/apt/lists/
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
ubuntu@ubuntu:~$


Something has obviously gone wrong, but can anyone help me?

---

### Post by HatoExB on 2014-06-09
> **Middo said:**
> 
ubuntu@ubuntu:~$ apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13: Permission denied)
E: Unable to lock directory /var/lib/apt/lists/
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

It seems you forgot to type sudo. Which is why it's saying "permission denied, are you root". Type

```
sudo apt-get update
```

and try again.

---

### Post by Middo on 2014-06-09
Doh!  Thanks.  Will try again tonight.

---

### Post by Middo on 2014-06-10
All fixed now.  The problem was that Ubuntu had installed itself onto the external hard drive.  I unplugged it and reinstalled, and it works.  Thanks for your suggestions everyone.

---

