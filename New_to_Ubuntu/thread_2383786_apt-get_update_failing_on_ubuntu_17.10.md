---
title: "apt-get update failing on ubuntu 17.10"
date: 2018-01-29
forum: New to Ubuntu
---

### Post by kris.armstrong on 2018-01-29
I installed ubuntu 17.10.1 today and tried to issue an apt-get update and it fails.  I verified internet connectivity so there should be no reason for it nowt to be able to update???

```
Err:1 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) artful-security InRelease
  503  Service Unavailable [IP: 91.189.91.26 80]
Err:2 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) artful InRelease
  503  Service Unavailable [IP: 91.189.91.26 80]
Get:3 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) artful-updates InRelease [78.6 kB]
Get:4 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) artful-backports InRelease [72.2 kB]
Get:5 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) artful-updates/main amd64 DEP-11 Metadata [73.3 kB]
Get:6 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) artful-updates/main DEP-11 64x64 Icons [49.2 kB]
Get:7 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) artful-updates/universe amd64 DEP-11 Metadata [48.5 kB]
Get:8 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) artful-updates/universe DEP-11 64x64 Icons [52.8 kB]
Get:9 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) artful-backports/universe amd64 DEP-11 Metadata [4,712 B]
Fetched 379 kB in 5s (72.0 kB/s)            
Reading package lists... Done
E: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/artful/InRelease](http://us.archive.ubuntu.com/ubuntu/dists/artful/InRelease)  503  Service Unavailable [IP: 91.189.91.26 80]
E: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/artful-security/InRelease](http://security.ubuntu.com/ubuntu/dists/artful-security/InRelease)  503  Service Unavailable [IP: 91.189.91.26 80]
E: Some index files failed to download. They have been ignored, or old ones used instead.
krisarmstrong@ubuntu:~$ sudo apt-get update
Err:1 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) artful-security InRelease
  503  Service Unavailable [IP: 91.189.88.152 80]
Err:2 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) artful InRelease
  503  Service Unavailable [IP: 91.189.91.23 80]
Hit:3 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) artful-updates InRelease
Hit:4 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) artful-backports InRelease
Reading package lists... Done                      
E: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/artful/InRelease](http://us.archive.ubuntu.com/ubuntu/dists/artful/InRelease)  503  Service Unavailable [IP: 91.189.91.23 80]
E: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/artful-security/InRelease](http://security.ubuntu.com/ubuntu/dists/artful-security/InRelease)  503  Service Unavailable [IP: 91.189.88.152 80]
E: Some index files failed to download. They have been ignored, or old ones used instead.
```

---

### Post by cruzer001 on 2018-01-29
Hello

Please post the following outputs:
```
cat /etc/apt/sources.list
```
and
```
cat /etc/apt/sources.list.save
```
Using code tags

[https://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](https://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

Ignore the outdated pics in that post.

---

### Post by kris.armstrong on 2018-01-29
Here you go.
```

krisarmstrong@ubuntu:~$ cat /etc/apt/sources.list
#deb cdrom:[Ubuntu 17.10 _Artful Aardvark_ - Release amd64 (20180105.1)]/ artful main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ artful main restricted
# deb-src http://us.archive.ubuntu.com/ubuntu/ artful main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ artful-updates main restricted
# deb-src http://us.archive.ubuntu.com/ubuntu/ artful-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ artful universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ artful universe
deb http://us.archive.ubuntu.com/ubuntu/ artful-updates universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ artful-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ artful multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ artful multiverse
deb http://us.archive.ubuntu.com/ubuntu/ artful-updates multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ artful-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ artful-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ artful-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu artful partner
# deb-src http://archive.canonical.com/ubuntu artful partner

deb http://security.ubuntu.com/ubuntu artful-security main restricted
# deb-src http://security.ubuntu.com/ubuntu artful-security main restricted
deb http://security.ubuntu.com/ubuntu artful-security universe
# deb-src http://security.ubuntu.com/ubuntu artful-security universe
deb http://security.ubuntu.com/ubuntu artful-security multiverse
# deb-src http://security.ubuntu.com/ubuntu artful-security multiverse
krisarmstrong@ubuntu:~$ cat /etc/apt/sources.list.save
cat: /etc/apt/sources.list.save: No such file or directory


```

---

### Post by cruzer001 on 2018-01-29
I expected to see maybe a typo, but all looks good.

Try a different download mirror (under software & updates).

---

### Post by kris.armstrong on 2018-01-29
so under software and updates it says my system is up to date.  

What I really need to do is install iperf3 and build-essentials. BUt those are failing to

```

krisarmstrong@ubuntu:/etc/apt$ sudo apt-get install  build-essentials
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package build-essentials

```

---

### Post by westie457 on 2018-01-29
Remove the last 's' because the package is build-essential

---

### Post by kris.armstrong on 2018-01-29
oops good catch on the typo but still a no go.  This is just odd. I have done this a hundred times over on other machiensand never had and issue until today. so weird.

```

krisarmstrong@ubuntu:/etc/apt$ sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package build-essential
krisarmstrong@ubuntu:/etc/apt$ ping ubuntu.com
PING ubuntu.com (91.189.94.40) 56(84) bytes of data.
64 bytes from ovinnik.canonical.com (91.189.94.40): icmp_seq=1 ttl=49 time=140 ms
64 bytes from ovinnik.canonical.com (91.189.94.40): icmp_seq=2 ttl=49 time=143 ms
64 bytes from ovinnik.canonical.com (91.189.94.40): icmp_seq=3 ttl=49 time=135 ms
^C
--- ubuntu.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 135.152/139.709/143.945/3.622 ms
krisarmstrong@ubuntu:/etc/apt$ 

```

---

### Post by cruzer001 on 2018-01-29
Heres a (dated) picture of the download source (software & updates).

[https://askubuntu.com/questions/104695/how-do-i-change-mirrors-in-ubuntu-server-from-regional-to-main](https://askubuntu.com/questions/104695/how-do-i-change-mirrors-in-ubuntu-server-from-regional-to-main)

And a list of mirrors if you need it.

[https://launchpad.net/ubuntu/+archivemirrors](https://launchpad.net/ubuntu/+archivemirrors)

---

### Post by tps-mail on 2018-01-29
Sometimes services go off line. Try switching to another mirror, and you should be good.

---

### Post by kris.armstrong on 2018-01-31
Still haveing issues see below

```


:/$ sudo apt-get update -y
Err:1 http://us.archive.ubuntu.com/ubuntu artful InRelease
  503  Service Unavailable [IP: 91.189.91.26 80]
Err:2 http://security.ubuntu.com/ubuntu artful-security InRelease
  503  Service Unavailable [IP: 91.189.88.149 80]
Get:3 http://us.archive.ubuntu.com/ubuntu artful-updates InRelease [78.6 kB]
Get:4 http://us.archive.ubuntu.com/ubuntu artful-backports InRelease [72.2 kB]
Get:5 http://us.archive.ubuntu.com/ubuntu artful-updates/main amd64 DEP-11 Metadata [73.4 kB]
Get:6 http://us.archive.ubuntu.com/ubuntu artful-updates/main DEP-11 64x64 Icons [49.2 kB]
Get:7 http://us.archive.ubuntu.com/ubuntu artful-updates/universe amd64 DEP-11 Metadata [48.5 kB]
Get:8 http://us.archive.ubuntu.com/ubuntu artful-updates/universe DEP-11 64x64 Icons [52.8 kB]
Get:9 http://us.archive.ubuntu.com/ubuntu artful-backports/universe amd64 DEP-11 Metadata [4,712 B]
Fetched 379 kB in 5s (69.2 kB/s)       
Reading package lists... Done
E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/artful/InRelease  503  Service Unavailable [IP: 91.189.91.26 80]
E: Failed to fetch http://security.ubuntu.com/ubuntu/dists/artful-security/InRelease  503  Service Unavailable [IP: 91.189.88.149 80]
E: Some index files failed to download. They have been ignored, or old ones used instead.
krisarmstrong@ubuntu:/$ nslookup
> security.ubuntu.com
Server:		127.0.0.53
Address:	127.0.0.53#53


Non-authoritative answer:
Name:	security.ubuntu.com
Address: 91.189.88.152
Name:	security.ubuntu.com
Address: 91.189.88.162
Name:	security.ubuntu.com
Address: 91.189.91.23
Name:	security.ubuntu.com
Address: 91.189.88.161
Name:	security.ubuntu.com
Address: 91.189.88.149
Name:	security.ubuntu.com
Address: 91.189.91.26
> us.archive.ubunt.com
Server:		127.0.0.53
Address:	127.0.0.53#53


Non-authoritative answer:
Name:	us.archive.ubunt.com
Address: 176.74.176.187

```

---

### Post by cruzer001 on 2018-02-01
I rechecked your sources.list trying to find something I missed, like a extra space or?  Can't find anything wrong.

Code 503 usually means server side, could be busy/maintenance.

But when I try the URLs and they work for me.
[http://us.archive.ubuntu.com/ubuntu/dists/artful](http://us.archive.ubuntu.com/ubuntu/dists/artful)  (main, multi, and on)
[http://security.ubuntu.com/ubuntu/dists/artful-security](http://security.ubuntu.com/ubuntu/dists/artful-security)  (main, multi, and on)

Still think you should try another source, just to cover all avenues.  Easy to do in terminal.

Make a backup
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.bak
```

Switch to the main server
```
sudo sed -i 's/http:\/\/us./http:\/\//g' /etc/apt/sources.list
```

And update

I really don't have any other ideas :(

---

### Post by jl2414 on 2018-02-01
I'm not a long-time user...

I have Ubuntu 16.04.
I recently started to use Terminal to update and I receive the about the same message.
I use also the Software Updater program to further update. You can also use Ubuntu Software navigate to Updates and update.

More I cannot tell you.

I hope a more longtime user can give some more information...

---

### Post by kris.armstrong on 2018-02-01
This is just weird :-) !!!!  no change

I even for the heck of it tried changing dns servers.  
Google DNS (8.8.8.8, 8.8.4.4)
OpenDNS (208.67.222.222, 208.67.220.220) 

neither made a differnce.  

```

krisarmstrong@ubuntu:/$ sudo cp /etc/apt/sources.list /etc/apt/sources.list.bak[sudo] password for krisarmstrong: 
krisarmstrong@ubuntu:/$ sudo sed -i 's/http:\/\/us./http:\/\//g' /etc/apt/sources.list
krisarmstrong@ubuntu:/$ sudo apt-get update
Err:1 http://security.ubuntu.com/ubuntu artful-security InRelease
  503  Service Unavailable [IP: 91.189.91.26 80]
Err:2 http://archive.ubuntu.com/ubuntu artful InRelease
  503  Service Unavailable [IP: 91.189.88.161 80]
Err:3 http://archive.ubuntu.com/ubuntu artful-updates InRelease
  503  Service Unavailable [IP: 91.189.88.161 80]
Get:4 http://archive.ubuntu.com/ubuntu artful-backports InRelease [72.2 kB]
Get:5 http://archive.ubuntu.com/ubuntu artful-backports/main i386 Packages [1,504 B]
Get:6 http://archive.ubuntu.com/ubuntu artful-backports/main amd64 Packages [1,508 B]
Get:7 http://archive.ubuntu.com/ubuntu artful-backports/main Translation-en [668 B]
Get:8 http://archive.ubuntu.com/ubuntu artful-backports/universe i386 Packages [3,380 B]
Get:9 http://archive.ubuntu.com/ubuntu artful-backports/universe amd64 Packages [3,392 B]
Get:10 http://archive.ubuntu.com/ubuntu artful-backports/universe Translation-en [1,880 B]
Get:11 http://archive.ubuntu.com/ubuntu artful-backports/universe amd64 DEP-11 Metadata [4,712 B]
Get:12 http://archive.ubuntu.com/ubuntu artful-backports/universe DEP-11 64x64 Icons [2,717 B]
Fetched 92.0 kB in 11s (8,254 B/s)      
Reading package lists... Done
E: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/artful/InRelease  503  Service Unavailable [IP: 91.189.88.161 80]
E: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/artful-updates/InRelease  503  Service Unavailable [IP: 91.189.88.161 80]
E: Failed to fetch http://security.ubuntu.com/ubuntu/dists/artful-security/InRelease  503  Service Unavailable [IP: 91.189.91.26 80]
E: Some index files failed to download. They have been ignored, or old ones used instead.
krisarmstrong@ubuntu:/$ 

```

---

### Post by tps-mail on 2018-02-01
So, service unavailable usually means you can't connect to the 'service' being requested. Not 'host not found' or anything DNS related. You are obviously resolving the IP from the FQDN, so ignore DNS. It's working. From a command prompt, try running 
```

telnet archive.ubuntu.com 80

```

I don't remember if telnet is installed by default. You may have to install it. If you get the server banner, you are good. I'll assume you get the server banner. Are you behind any kind of firewall or HTTP Proxy setup?

---

