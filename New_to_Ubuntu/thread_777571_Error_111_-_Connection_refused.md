---
title: "Error 111 - Connection refused"
date: 2008-05-01
forum: New to Ubuntu
---

### Post by Yum_Salad on 2008-05-01
Does anyone know what might be causing this error? I get it in two different instances that i know of. The first when i'm trying to perform an update, the second when trying to use bittorrent..

i'm stumped.. I don't believe my router is blocking any ports.

Thanks for any help!


[SOLVED] - re-enabling automatic updates fixed the problem

---

### Post by Yum_Salad on 2008-05-02
anyone? I need to DL smartmontools and I can't! :(

---

### Post by Yum_Salad on 2008-05-04
bump :confused:

---

### Post by Yum_Salad on 2008-05-08
someone.anyone. :popcorn:

---

### Post by Monicker on 2008-05-08
This only occurs with 2 applications?  Are you talking about the Ubuntu update manager?  And which bittorrent client?

Could I possible see the results of this terminal command:

```
sudo iptables -n -L
```

If it is also the ubuntu update manager giving that error, please show the contents of the file /etc/apt/sources.list.

---

### Post by Yum_Salad on 2008-05-08
Hey Monicker, Thanks for taking a minute of your time..

[HTML]user@user:~$ sudo iptables -n -L
Password:
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
user@user:~$[/HTML]

---

### Post by Yum_Salad on 2008-05-08
It has only been happening with synaptic, and bittorrent. Though that's all i've tried. I'm thinking it's a port issue. But my router shows no blocked ports.

could it be because this install was done in the US and i'm in the UK?

.. just throwing that out there!

Thanks again.

---

### Post by Yum_Salad on 2008-05-08
Moniker, sorry about not including sources.list. I got so exited someone was helping me I didn't read too thoroughly.

sources.list

[HTML]
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ dapper universe main restricted multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
deb http://security.ubuntu.com/ubuntu dapper-security universe
deb-src http://security.ubuntu.com/ubuntu dapper-security universe
[/HTML]

---

### Post by Monicker on 2008-05-08
> **Yum_Salad said:**
> It has only been happening with synaptic, and bittorrent. Though that's all i've tried. I'm thinking it's a port issue. But my router shows no blocked ports.

could it be because this install was done in the US and i'm in the UK?

.. just throwing that out there!

Thanks again.

Hrmm. So, you have not tried connecting to a web site from the computer giving that error?  I would at least do that.

Also, give the results of the following commands

```
ping -c 4 91.189.88.31
ping -c 4 us.archive.ubuntu.com
```

---

### Post by Yum_Salad on 2008-05-08
I'm on the same computer as we speak. Which is why I don't understand why this is happening.

[HTML]user@user:~$ ping -c 4 91.189.88.31
PING 91.189.88.31 (91.189.88.31) 56(84) bytes of data.
64 bytes from 91.189.88.31: icmp_seq=1 ttl=55 time=10.7 ms
64 bytes from 91.189.88.31: icmp_seq=2 ttl=55 time=14.2 ms
64 bytes from 91.189.88.31: icmp_seq=3 ttl=55 time=11.8 ms
64 bytes from 91.189.88.31: icmp_seq=4 ttl=55 time=18.7 ms

--- 91.189.88.31 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3014ms
rtt min/avg/max/mdev = 10.780/13.911/18.742/3.065 ms
user@user:~$
[/HTML]


[HTML]user@user:~$ ping -c 4 us.archive.ubuntu.com
PING us.archive.ubuntu.com (91.189.88.46) 56(84) bytes of data.
64 bytes from lithium.canonical.com (91.189.88.46): icmp_seq=1 ttl=55 time=17.0 ms
64 bytes from lithium.canonical.com (91.189.88.46): icmp_seq=2 ttl=55 time=15.9 ms
64 bytes from lithium.canonical.com (91.189.88.46): icmp_seq=3 ttl=55 time=13.6 ms
64 bytes from lithium.canonical.com (91.189.88.46): icmp_seq=4 ttl=55 time=17.3 ms

--- us.archive.ubuntu.com ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 15180ms
rtt min/avg/max/mdev = 13.654/15.975/17.339/1.449 ms
user@user:~$
[/HTML]

---

### Post by Monicker on 2008-05-08
Ok.  You can ping by name and ip, which is good.  Is there a chance that you configured a proxy server for Synaptic and bittorrent?  I know that Synaptic has that option.

Open Synaptic and go to Settings -> Preferences -> Network

Is it set for a direction connection to the internet, or to use a proxy server?

---

### Post by Yum_Salad on 2008-05-08
direct connection to the internet.

This is the error I get in synaptic, no matter what I try to download:

[HTML]W: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/universe/4/44bsd-rdist/44bsd-rdist_20001111-6_i386.deb
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

[/HTML]

---

### Post by Monicker on 2008-05-08
> **Yum_Salad said:**
> direct connection to the internet.

This is the error I get in synaptic, no matter what I try to download:

[HTML]W: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/universe/4/44bsd-rdist/44bsd-rdist_20001111-6_i386.deb
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

[/HTML]

I have seen this before in other posts, though I don't recall seeing the cause of it

```
Could not connect to localhost:4001 (127.0.0.1)
```

Its trying to connect to a port on the local machine, which would have to be proxied in order to work.

---

### Post by Monicker on 2008-05-09
What is the output of the following command?

```

sudo grep -r 4001 /etc
```

That 4001 port setting has to be specified somewhere, but right now I not sure exactly where that might be.

---

### Post by Yum_Salad on 2008-05-09
Moniker, I think you may have got it. You'r awesome!

I was trying to install jap(anon proxy server if you don't know) a few weeks ago.. and I wasn't sure if I got to work or not. Either way, I gave up and forgot about it. But it looks like it's showing up here..

[HTML]user@user:~$ sudo grep -r 4001 /etc
Password:
grep: /etc/alternatives/irssi: No such file or directory
grep: /etc/alternatives/irssi.1.gz: No such file or directory
/etc/default/anon-proxy:PORT="4001"
/etc/init.d/anon-proxy:[ -z "$PORT" ] && PORT="4001"
/etc/rc0.d/K20anon-proxy:[ -z "$PORT" ] && PORT="4001"
/etc/rc1.d/K20anon-proxy:[ -z "$PORT" ] && PORT="4001"
grep: /etc/rc2.d/K77ntp-server: No such file or directory
/etc/rc2.d/S20anon-proxy:[ -z "$PORT" ] && PORT="4001"
grep: /etc/rc3.d/K77ntp-server: No such file or directory
/etc/rc3.d/S20anon-proxy:[ -z "$PORT" ] && PORT="4001"
/etc/rc4.d/S20anon-proxy:[ -z "$PORT" ] && PORT="4001"
/etc/rc5.d/S20anon-proxy:[ -z "$PORT" ] && PORT="4001"
/etc/rc6.d/K20anon-proxy:[ -z "$PORT" ] && PORT="4001"
/etc/udev/rules.d/45-libsane.rules:SYSFS{idVendor}=="05d8", SYSFS{idProduct}=="4001", MODE="664", GROUP="scanner"
/etc/environment:HTTP_PROXY=http://localhost:4001 # +ANON_MARK+
/etc/environment:http_proxy=http://localhost:4001 # +ANON_MARK+
user@user:~$
[/HTML]

---

### Post by Monicker on 2008-05-09
Yup.  I would say that is what is causing it.  I have never used it myself, so I have no idea how it is supposed to be configured.  If you do not need it, I would suggest removing it.
```

sudo apt-get --purge remove anon-proxy
```

Afterwards, rerun the grep command to see if any traces of it are still left.

---

### Post by Yum_Salad on 2008-05-10
EDIT: UPDATE: Bittorrent now works :) But synaptic still doesn't..

I uninstalled it and it doesn't show up in the grep output:

```
user@user:~$ sudo grep -r 4001 /etc
grep: /etc/alternatives/irssi: No such file or directory
grep: /etc/alternatives/irssi.1.gz: No such file or directory
grep: /etc/rc2.d/K77ntp-server: No such file or directory
grep: /etc/rc3.d/K77ntp-server: No such file or directory
/etc/udev/rules.d/45-libsane.rules:SYSFS{idVendor}=="05d8", SYSFS{idProduct}=="4001", MODE="664", GROUP="scanner"
user@user:~$

```

The bottom most line in the output makes a reference to port 4001. Do you have such a line?

---

### Post by Monicker on 2008-05-10
That last line is not relevant.  Its just a product id for some type of scanning device.  Is Synaptic still giving the same error messages as before, or have they changed?

---

### Post by Yum_Salad on 2008-05-10
Yes the same error.. But I solved the problem.

I had disabled automatic updates because i was concerned about unneccessary disk usage(my disk is making those "I'm about to die sounds"). And that's what it was. I don't understand why I wouldn't be able to go into synaptic and install programs with auto updates disabled though. Doesn't make sense to me.

Maybe this is a bug?

Either way, Thanks for all your help Moniker!!

---

