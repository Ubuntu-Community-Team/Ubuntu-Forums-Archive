---
title: "G++/GCC programming/compiling"
date: 2013-01-30
forum: New to Ubuntu
---

### Post by tomzie on 2013-01-30
Hi, I am very new at Ubuntu environment. I have created test.cpp to test "Hello, World!". In my directory, I type g++ test.cpp -o test. I get the following message.
 
The program 'g++' can be found in the following packages:
* g++
* pentium-builder
Try: sudo apt-get install <selected package>
 
at $ I typed sudo apt-get install g++.
 
I get gcc-4.6-base is already the newest version.
 
Questions:
1.) Do I need to install g++ or pentium-builder? I have tried installing it, but I get the "..newest version"
2.) If I don't need to install them, how do I use it?
3.) How do I compile my simple cpp or c file?
 
Thanks,
tomzie

---

### Post by kanikilu on 2013-01-30
I don't program, and try to avoid compiling software whenever possible, but I have done it, and I think all I did was install the build-essential package: ```
sudo apt-get install build-essential
```

[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

Maybe the "-base" gcc package doesn't provide everything you need :confused:

---

### Post by tomzie on 2013-01-30
Hi. Thanks for the reply. This is what I get after executing the command.
 
Package build-essential is not available, but is referred to by another package. This may mean that the package is missing, has been obsoleted, or is only available from another source.
 
E: Package 'build-essential' has no installation candidate.
 
Please help. Thanks.

---

### Post by steeldriver on 2013-01-30
what version of ubuntu are you running? can you post the output of the following commands please?

```

$ cat /etc/lsb-release

$ uname -a

```

---

### Post by frank604 on 2013-01-30
install synaptic ```
sudo apt-get install synaptic
```

then try to install build-essential again
```
sudo apt-get install build-essential
```
if it fails to locate again, run > synaptic
in search box search for > build-essential

---

### Post by kanikilu on 2013-01-30
> **tomzie said:**
> Hi. Thanks for the reply. This is what I get after executing the command.
 
Package build-essential is not available, but is referred to by another package. This may mean that the package is missing, has been obsoleted, or is only available from another source.
 
E: Package 'build-essential' has no installation candidate.
 
Please help. Thanks. Have you run an update first? ```
sudo apt-get update
```

---

### Post by tomzie on 2013-01-30
Hi, this is what I get. Thanks.
 
$ cat /etc/lsb-release
 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.1 LTS"
 
$ uname -a
 
Linux ubuntusvr 3.2.0-29-generic-pae #46-Ubuntu SMP Fri Jul 27 17:25:43 UTC 2012 i686 i686 i386 GNU/Linux

---

### Post by tomzie on 2013-01-30
tryied sudo apt-get update
 
I am getting Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/precise](http://ca.archive.ubuntu.com/ubuntu/dists/precise)-........
 
Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by tomzie on 2013-01-30
Hi. Thanks for the reply. This is what I get after executing the command.

Package synaptic is not available, but is referred to by another package. This may mean that the package is missing, has been obsoleted, or is only available from another source.

E: Package 'synaptic' has no installation candidate.

---

### Post by kanikilu on 2013-01-30
> **tomzie said:**
> tryied sudo apt-get update
 
I am getting Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/precise](http://ca.archive.ubuntu.com/ubuntu/dists/precise)-........
 
Some index files failed to download. They have been ignored, or old ones used instead. Sounds like you have an internet connection problem. Either that, or you just need to change your mirror to something else. You can do that in Software Sources.

---

### Post by tomzie on 2013-01-30
Is there a way to test the internet connection inside Ubuntu?

---

### Post by steeldriver on 2013-01-30
can you ping the update server?

```
ping -c4 ca.archive.ubuntu.com
```

---

### Post by GordThompson on 2013-01-30
> **tomzie said:**
> Is there a way to test the internet connection inside Ubuntu?
Did you use that same machine to post your messages here? If so, then your Internet connection is working....

---

### Post by tomzie on 2013-01-30
I can not ping the ca.archive.ubuntu.com. I get 100% loss. How do I fix this issue?

---

### Post by pierceTN on 2013-01-30
> **tomzie said:**
> I can not ping the ca.archive.ubuntu.com. I get 100% loss. How do I fix this issue?

Try pinging google.com:

> ping 8.8.8.8

also, as GordThompson said, if you are on the same machine posting here, then you are connected to the internet


-Pierce

---

### Post by GordThompson on 2013-01-30
> **tomzie said:**
> I can not ping the ca.archive.ubuntu.com. I get 100% loss. How do I fix this issue?
Just FYI, it's generally regarded as good practice to post the *actual results *of commands, like this:
```
gord@ubuntu10vm01:~$ ping -c4 ca.archive.ubuntu.com
PING ca.archive.ubuntu.com (91.189.92.200) 56(84) bytes of data.
64 bytes from obake.canonical.com (91.189.92.200): icmp_seq=1 ttl=51 time=116 ms
64 bytes from obake.canonical.com (91.189.92.200): icmp_seq=2 ttl=51 time=115 ms
64 bytes from obake.canonical.com (91.189.92.200): icmp_seq=3 ttl=51 time=118 ms
64 bytes from obake.canonical.com (91.189.92.200): icmp_seq=4 ttl=51 time=118 ms

--- ca.archive.ubuntu.com ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3006ms
rtt min/avg/max/mdev = 115.773/117.355/118.834/1.285 ms
```The actual error messages are always more helpful than a generic "it doesn't work" comment.

---

### Post by tomzie on 2013-01-30
I have shutdown/restarted the Ubuntu in Virtual Box and I get the following.
 
Waiting for network configuration...
Waiting up to 60 more seconds for network configuration...
Booting system without full network configuration...
 
It looks like kanikilu was correct, I have issue with Internet connection or network configuration inside my Virtual Box. What do I do now? How do I fix this network configuration issue?

---

### Post by frank604 on 2013-01-30
This makes more sense.  Next time it would be easier if you mentioned you are running ubuntu as guest in virtualbox.

Your ubuntu does not have internet access.  In virtualbox, click on (settings). Then on the left hand side click on (Network). 

Change "Attached to:" from (Nat) to (Bridged)
Under "Name" select the device your host computer is connected to (wireless card or ethernet card).
If you are unsure, test both.

Once you get internet access on your guest ubuntu in virtualbox, please go ahead and try to install build-essential package again.

---

### Post by tomzie on 2013-02-08
Hi All, Thanks for all your help. It looks like the issue is the download permission I have at work. Here at home, I am able to install Ubuntu in VirtualBox and able to install the gcc and g++ using the sudo install command.

---

