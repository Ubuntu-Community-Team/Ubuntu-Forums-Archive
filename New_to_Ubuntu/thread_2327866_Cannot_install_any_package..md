---
title: "Cannot install any package."
date: 2016-06-15
forum: New to Ubuntu
---

### Post by unix-lover-2011 on 2016-06-15
Hi Guys,

Just installed Xbuntu on my work laptop. It has Xubuntu 16.04.

When I try to run the very basic command say
```
apt-get update
``` it doesn't do nothing.

Please look at the log below.
```
root@jim-master:~# cat 1|head -20
Ign:1 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial InRelease
Ign:2 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security InRelease
Ign:3 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial-updates InRelease
Ign:4 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security Release
Ign:5 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial-backports InRelease
Ign:6 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main amd64 Packages.diff/Index
Ign:7 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial Release
Ign:8 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main i386 Packages
Ign:9 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial-updates Release
Ign:10 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main all Packages
Ign:11 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main Translation-en_AU
Ign:12 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial-backports Release
Ign:13 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main Translation-en.diff/Index
Ign:14 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial/universe amd64 Packages.diff/Index
Ign:15 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main amd64 DEP-11 Metadata
Ign:16 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial/universe i386 Packages.diff/Index
Ign:17 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main DEP-11 64x64 Icons
Ign:18 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial/universe all Packages
Ign:19 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/restricted amd64 Packages.diff/Index
Ign:20 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial/universe Translation-en_AU.diff/Index
root@jim-master:~# 
```


```
root@jim-master:~# cat 1|tail -30
Ign:116 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial-updates/universe amd64 DEP-11 Metadata
Ign:117 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial-updates/universe DEP-11 64x64 Icons
Err:118 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial-updates/multiverse amd64 Packages
  404  Not Found
Err:119 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial-updates/multiverse i386 Packages
  404  Not Found
Ign:120 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial-updates/multiverse Translation-en
Ign:121 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial-updates/multiverse amd64 DEP-11 Metadata
Err:122 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial-backports/main amd64 Packages
  404  Not Found
Err:123 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial-backports/main i386 Packages
  404  Not Found
Ign:124 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial-backports/main Translation-en
Ign:125 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial-backports/main amd64 DEP-11 Metadata
Err:126 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial-backports/restricted amd64 Packages
  404  Not Found
Err:127 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial-backports/restricted i386 Packages
  404  Not Found
Ign:128 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial-backports/restricted Translation-en
Ign:129 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial-backports/restricted amd64 DEP-11 Metadata
Err:130 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial-backports/universe amd64 Packages
  404  Not Found
Err:131 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial-backports/universe i386 Packages
  404  Not Found
Ign:132 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial-backports/universe Translation-en
Err:138 [ftp://au.archive.ubuntu.com/ubuntu](ftp://au.archive.ubuntu.com/ubuntu) xenial InRelease
  Cannot initiate the connection to au.archive.ubuntu.com:21 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) [IP: 2001:388:30bc:cafe::beef 21]
Err:139 [ftp://au.archive.ubuntu.com/ubuntu](ftp://au.archive.ubuntu.com/ubuntu) xenial-updates InRelease
  Cannot initiate the connection to au.archive.ubuntu.com:21 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) [IP: 2001:388:30bc:cafe::beef 21]
Reading package lists...
root@jim-master:~# 
```


Need help asap as I am unable to do anything without get out to internet.

I can connected to web browser and browse internet, no luck via command line though...

Jim

---

### Post by ajgreeny on 2016-06-15
Can you try ```
ping -c 5 au.archive.ubuntu.com
``` to see if there is a specific connection problem for you; I just tried and all was well.

Try the ```
sudo apt-get update
``` again, and if that still does not work try using another download server rather than the Australian archive; maybe that one is down at the moment, even though I can ping it.

---

### Post by unix-lover-2011 on 2016-06-15
No luck there

```

root@jim-master:~# ping -c 5 au.archive.ubuntu.com
PING mirror.aarnet.edu.au (202.158.214.106) 56(84) bytes of data.


--- mirror.aarnet.edu.au ping statistics ---
5 packets transmitted, 0 received, 100% packet loss, time 3999ms


root@jim-master:~# 




```

I can definitely browse internet on VM with proxy and I did export http_proxy to proxy url on command line

---

### Post by ajgreeny on 2016-06-15
Can you try ```
ping google.com
``` then ```
ping 216.58.210.46
```
They should both work and are both to the same site, but I wonder if just the numbered version will do so.  That will suggest you maybe have a DNS problem of some sort.

---

### Post by unix-lover-2011 on 2016-06-15
I am keen to investigate further what sort of the DNS problem it might be. Here is the output from the command you suggested.

```

root@jim-master:~# ping google.com
PING google.com (216.58.220.142) 56(84) bytes of data.
^C
--- google.com ping statistics ---
12 packets transmitted, 0 received, 100% packet loss, time 11089ms


root@jim-master:~# ping 216.58.210.46
PING 216.58.210.46 (216.58.210.46) 56(84) bytes of data.
^C
--- 216.58.210.46 ping statistics ---
6 packets transmitted, 0 received, 100% packet loss, time 5039ms


root@jim-master:~# ping google.com
PING google.com (216.58.220.142) 56(84) bytes of data.
^C
--- google.com ping statistics ---
2 packets transmitted, 0 received, 100% packet loss, time 1008ms


root@jim-master:~# ping google.com
PING google.com (216.58.220.142) 56(84) bytes of data.
^C
--- google.com ping statistics ---
5 packets transmitted, 0 received, 100% packet loss, time 4031ms


root@jim-master:~# ping 216.58.220.142
PING 216.58.220.142 (216.58.220.142) 56(84) bytes of data.
^C
--- 216.58.220.142 ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 2000ms


root@jim-master:~# 

```

My /etc/resolv.conf file is as follows:

```

root@jim-master:~# cat /etc/resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.1.1
search company.com.au
root@jim-master:~# 

```


I really want this to be working  and I'm going to be persistent until issue is resolved. :)

Jim

---

### Post by unix-lover-2011 on 2016-06-16
Addition. I have problem similar to this:
[http://askubuntu.com/questions/104950/how-do-i-configure-apt-get-to-use-a-pac-file-for-a-proxy](http://askubuntu.com/questions/104950/how-do-i-configure-apt-get-to-use-a-pac-file-for-a-proxy)


they say about the file **proxy **located at /etc/apt/apt.conf.d.

However I don't have that file.
root@jim-master:~# ls /etc/apt/apt.conf.d
00aptitude    01autoremove          01-vendor-ubuntu  15update-stamp  20auto-upgrades  50appstream            70debconf
00trustcdrom  01autoremove-kernels  10periodic        20archive       20dbus           50unattended-upgrades  99update-notifier
root@jim-master:~#

I have the files above. However I see a better picture now
I did export http_proxy=http://server.conpany.com.au:8080

```

root@jim-master:~# apt-get update
Hit:1 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial InRelease
Get:2 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial-updates InRelease [94.5 kB] 
Hit:3 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial-backports InRelease 
Hit:4 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security InRelease 
Err:5 [ftp://au.archive.ubuntu.com/ubuntu](ftp://au.archive.ubuntu.com/ubuntu) xenial InRelease 
Cannot initiate the connection to au.archive.ubuntu.com:21 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) [IP: 2001:388:30bc:cafe::beef 21]
Err:6 [ftp://au.archive.ubuntu.com/ubuntu](ftp://au.archive.ubuntu.com/ubuntu) xenial-updates InRelease
Cannot initiate the connection to au.archive.ubuntu.com:21 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) [IP: 2001:388:30bc:cafe::beef 21]
Fetched 94.5 kB in 2min 0s (785 B/s)
Reading package lists... Done
W: Failed to fetch [ftp://au.archive.ubuntu.com/ubuntu/dists/xenial/InRelease](ftp://au.archive.ubuntu.com/ubuntu/dists/xenial/InRelease) Cannot initiate the connection to au.archive.ubuntu.com:21 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) [IP: 2001:388:30bc:cafe::beef 21]
W: Failed to fetch [ftp://au.archive.ubuntu.com/ubuntu/dists/xenial-updates/InRelease](ftp://au.archive.ubuntu.com/ubuntu/dists/xenial-updates/InRelease) Cannot initiate the connection to au.archive.ubuntu.com:21 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) [IP: 2001:388:30bc:cafe::beef 21]
W: Some index files failed to download. They have been ignored, or old ones used instead.
W: Duplicate sources.list entry [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial Release
W: Duplicate sources.list entry [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial-updates Release
root@jim-master:~# 

```

Better than before but still far away.
Could it be related to some security certificates ?


Any help would be greatly appreciated.

---

### Post by ajgreeny on 2016-06-16
Well. those pings that I asked you to run did not seem to work at all, which is very odd and I'm afraid is now turning into a problem that is rather beyond me, though it might be worth trying again to see if it works now and is might be worth pinging your router if you can.

However, as you now seem to be getting a somewhat better output to the update command there must be some hope, so now let's see the output of ```
cat /etc/apt/sources.list
``` to see if there are any problems we can solve.

I note there are some ftp URLs in your sources.list according to the output you show in your last post; where did those come from?  I don't think I have ever seen that before.

---

### Post by unix-lover-2011 on 2016-06-19
Thanks for your help. very much appreciated. While I am unable to contact the outside world my primary aim to install packages is resolved. resolution was export http_proxy'http://proxyserver.company.:port'. All good now, although I am keen to resolve the issue , Unable to ping google.com' from VM but that is something later.

Thanks again !

---

### Post by unix-lover-2011 on 2016-06-19
Yes you are right, I did changed from http to ftp but that comes as a tip from google. I reverted back to http and did the export of http_proxy variable too.

---

### Post by vasa1 on 2016-06-19
> **unix-lover-2011 said:**
> Hi Guys,

Just installed Xbuntu on my work laptop. It has Xubuntu 16.04.

When I try to run the very basic command say
apt-get update it doesn't do nothing.

Please look at the log below.
root@jim-master:~# cat 1|head -20
...
root@jim-master:~# 


root@jim-master:~# cat 1|tail -30
...
root@jim-master:~# 
...
Jim
Why are you running as **root** and not as a standard user using **sudo** whenever you need elevated privileges?

Also, please use code tags when posting content you copy from the terminal. Thanks!

---

