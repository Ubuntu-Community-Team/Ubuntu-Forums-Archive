---
title: "[SOLVED] no new software installs even after reintalling"
date: 2008-05-25
forum: New to Ubuntu
---

### Post by rockerphil on 2008-05-25
ok, this is really getting annoying. i've had this same problem for about 3 days now and not even a clean install fixes it. i recently installed a minimalist OS on my only computer using the Ubuntu Gutsy Gibson minimalist CD to install just a CLI and then adding the x windows server, iceWM and Firefox. well software installs fine for a while but then nothing will instal. i'll post the terminal output when trying to install Synaptic now:

phil@phil:~$ sudo apt-get install synaptic
[sudo] password for phil:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libvte-common libvte9
Suggested packages:
  dwww
Recommended packages:
  deborphan libgnome2-perl
The following NEW packages will be installed:
  libvte-common libvte9 synaptic
0 upgraded, 3 newly installed, 0 to remove and 7 not upgraded.
Need to get 2056kB of archives.
After unpacking 8626kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main libvte-common 1:0.16.9-0ubuntu3
  Connection failed
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main libvte9 1:0.16.9-0ubuntu3
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main synaptic 0.60ubuntu5
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/v/vte/libvte-common_0.16.9-0ubuntu3_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/v/vte/libvte-common_0.16.9-0ubuntu3_all.deb)  Connection failed
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/v/vte/libvte9_0.16.9-0ubuntu3_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/v/vte/libvte9_0.16.9-0ubuntu3_i386.deb)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/s/synaptic/synaptic_0.60ubuntu5_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/s/synaptic/synaptic_0.60ubuntu5_i386.deb)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
phil@phil:~$ 

i have run both "sudo apt-get update" and have run the code with "--fix-missing". i got the problem solved the other day by editing my /etc/hosts file but the problem came back. i'll post the contents of my /etc/hosts file now:

127.0.0.1       localhost
127.0.1.1       phil

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts


and now the contents of my /etc/apt/sources.list file:

 deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
 deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
 deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) gutsy-security main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.


i'm a bit agrivated now. and here's the thing, i don't have any CD burning software installed, so don't say "just burn a new install disk" cus that entails reinstalling and then hurrying to install k3b, and i really don't want to test my 10 year old hard drve. so can anyone help?

---

### Post by shifty_powers on 2008-05-25
is this a laptop?

---

### Post by rockerphil on 2008-05-25
no, it's an old Dell Dimension desktop running a 500 MHz Intel Pentium processor and 128 MB of SD RAM

---

### Post by RiceMonster on 2008-05-25
Looks like the server you're trying to install from is down. It shouldn't be too long before they fix it. I've had that problem a couple of times and it was the server. Open up System > Administration > Software Sources and switch to a different server that's close to you.

---

### Post by shifty_powers on 2008-05-25
[http://us.archive.ubuntu.com/ubuntu/pool/main/v/vte/libvte9_0.16.9-0ubuntu3_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/v/vte/libvte9_0.16.9-0ubuntu3_i386.deb)

is the link of one of the debs apt is trying to download. what happens when you click on it?

---

### Post by shifty_powers on 2008-05-25
> **RiceMonster said:**
> Looks like the server you're trying to install from is down. It shouldn't be too long before they fix it. I've had that problem a couple of times and it was the server. Open up System > Administration > Software Sources and switch to a different server that's close to you.

no they're not as i cal click on the link that is being refused and donwload the deb...

---

### Post by Maestro23 on 2008-05-25
> **shifty_powers said:**
> no they're not as i cal click on the link that is being refused and donwload the deb...

Same here. No probs with the link.

---

### Post by rockerphil on 2008-05-25
no, the server isn't down, i can ping the repo just fine. so that's not the problem. like i said, i once fixed the problem momentarily by editing my /etc/hosts file, but now i can't seem to figure it out

---

### Post by shifty_powers on 2008-05-25
but can you access the debs through firefox?

---

### Post by rockerphil on 2008-05-25
yea, i can download the deb fine. but i can't install with apt-get OR aptitude, and this same problem has reoccured after a clean install

---

### Post by forestpixie on 2008-05-25
Don't know if this is of any help, the error you get appears to show that apt is trying to connect locally - I don't understand myself but...

the only references I can seem to find to > Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused) are to anon-proxy and tor

You say it was installing ok and then stopped - what was the last thing you installed? Are you behind a proxy?

There is an old debian forum thread about this 

[http://forums.debian.net/viewtopic.php?t=310&sid=7a47906174ac51bec1eecb918e49b741](http://forums.debian.net/viewtopic.php?t=310&sid=7a47906174ac51bec1eecb918e49b741)

---

### Post by shifty_powers on 2008-05-25
have you thought of using something like puppy linux?

[http://www.puppylinux.org/](http://www.puppylinux.org/)

i can't help but feeling that ubuntu is just not going to work on your laptop. maybe thats being defeatist but stil...

---

### Post by shifty_powers on 2008-05-25
[https://answers.launchpad.net/ubuntu/+question/6719](https://answers.launchpad.net/ubuntu/+question/6719)

are you using a proxy server by any chance?

[http://ubuntuforums.org/archive/index.php/t-234704.html](http://ubuntuforums.org/archive/index.php/t-234704.html)

---

### Post by forestpixie on 2008-05-25
Yea - they were two I looked at - certainly seems to be something to do with proxies, although I don't profess to understand the ins and outs of it - there was, I think, a command one was talking about ```
echo $http_proxy
``` which returned something - but not on mine.
Might be worth trying it

---

### Post by rockerphil on 2008-05-25
anybody?

---

### Post by shifty_powers on 2008-05-25
when you installed ubuntu, do you remember the name you gave to the computer?

i.e. my username is shifty and the computers name is shifty-desktop....

---

### Post by shifty_powers on 2008-05-25
go system>preferences>network proxy>proxy configuraiton

what is selected?

---

### Post by rockerphil on 2008-05-25
i feel like an idiot. i remove my proxy programs and reboot, it's working fine now, but hey, thanx, i never would have thought about removing anon-proxy

---

### Post by forestpixie on 2008-05-25
Hope I helped a bit then, can you mark thread as solved :) It's good to come across tthings you've never thought of before - there's learnin in them thar hills

---

### Post by shifty_powers on 2008-05-25
heh yep, thought it would be the proxy ;)

and dude, we've all done things like that.

but it must be a reliuef to finally get ti sorted :D

---

