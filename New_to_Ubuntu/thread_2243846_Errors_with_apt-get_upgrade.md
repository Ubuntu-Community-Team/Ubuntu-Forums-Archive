---
title: "Errors with apt-get upgrade"
date: 2014-09-11
forum: New to Ubuntu
---

### Post by ric_Poirier on 2014-09-11
Hi,

I have been updating a remote computer via ssh (Ubuntu 14.04 is installed on that computer). Up to now, everything worked perfectly. A couple days ago, I tried to upgrade it again, but the folowing errors showed up:

```
Err http://ca.archive.ubuntu.com trusty InRelease                              
  
Err http://ca.archive.ubuntu.com trusty-updates InRelease                      
  
Err http://ca.archive.ubuntu.com trusty-backports InRelease                    
  
Err http://security.ubuntu.com trusty-security InRelease                       
  
Err http://extras.ubuntu.com trusty InRelease                                  
  
Err http://ca.archive.ubuntu.com trusty Release.gpg                            
  Could not resolve 'ca.archive.ubuntu.com'
Err http://ca.archive.ubuntu.com trusty-updates Release.gpg
  Could not resolve 'ca.archive.ubuntu.com'
Err http://security.ubuntu.com trusty-security Release.gpg
  Could not resolve 'security.ubuntu.com'
Err http://extras.ubuntu.com trusty Release.gpg
  Could not resolve 'extras.ubuntu.com'
Err http://ca.archive.ubuntu.com trusty-backports Release.gpg
  Could not resolve 'ca.archive.ubuntu.com'
Reading package lists... Done
W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/trusty/InRelease  

W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/trusty-updates/InRelease  

W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/trusty-backports/InRelease  

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/trusty-security/InRelease  

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/trusty/InRelease  

W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/trusty/Release.gpg  Could not resolve 'ca.archive.ubuntu.com'

W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/trusty-updates/Release.gpg  Could not resolve 'ca.archive.ubuntu.com'

W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/trusty-backports/Release.gpg  Could not resolve 'ca.archive.ubuntu.com'

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/trusty-security/Release.gpg  Could not resolve 'security.ubuntu.com'

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/trusty/Release.gpg  Could not resolve 'extras.ubuntu.com'

W: Some index files failed to download. They have been ignored, or old ones used instead.
```

Do you have any suggestions as to what could have caused these errors, and how to fix them?

Thank you very much!

---

### Post by Bashing-om on 2014-09-11
ric_Poirier; Hello.

With some small amount of hesitation I offer that "inrelease" is not valid for the field .
I get:
> 
[http://ca.archive.ubuntu.com/ubuntu/dists/trusty/InRelease](http://ca.archive.ubuntu.com/ubuntu/dists/trusty/InRelease) ::->
Not Found

The requested URL /ubuntu/dists/trusty/InRelease was not found on this server.

Apache/2.2.22 (Ubuntu) Server at ca.archive.ubuntu.com Port 80

Whereas up to 'trusty' all is accepted:
> 
[http://ca.archive.ubuntu.com/ubuntu/dists/trusty/](http://ca.archive.ubuntu.com/ubuntu/dists/trusty/) ::->
Index of /ubuntu/dists/trusty


That leads me to believe that you should check and adjust your source list(s).

[INDENT][INDENT]just my thought
[/INDENT][/INDENT]

---

### Post by ian-weisser on 2014-09-11
Do other name-resolution activities work properly?

For example, can that machine ping out to a named server instead of an IP address?

---

### Post by ric_Poirier on 2014-09-11
> **Bashing-om said:**
> 
That leads me to believe that you should check and adjust your source list(s).
[INDENT][INDENT]just my thought
[/INDENT]
[/INDENT]


Thank you for your answer. I went to take a look at my **source.list**, but I'm not exactly sure of what I should change. Also, what I find weird is that the computer I use to connect to my remote computer also has Ubuntu 14.04 installed and I have never had this problem...

Here is what I found in my **source.list** file:

```

#deb cdrom:[Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release amd64 (20140722.2)]/ trusty main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://ca.archive.ubuntu.com/ubuntu/ trusty main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu/ trusty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ca.archive.ubuntu.com/ubuntu/ trusty-updates main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu/ trusty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://ca.archive.ubuntu.com/ubuntu/ trusty universe
deb-src http://ca.archive.ubuntu.com/ubuntu/ trusty universe
deb http://ca.archive.ubuntu.com/ubuntu/ trusty-updates universe
deb-src http://ca.archive.ubuntu.com/ubuntu/ trusty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ca.archive.ubuntu.com/ubuntu/ trusty multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu/ trusty multiverse
deb http://ca.archive.ubuntu.com/ubuntu/ trusty-updates multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu/ trusty-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://ca.archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu trusty-security main restricted
deb-src http://security.ubuntu.com/ubuntu trusty-security main restricted
deb http://security.ubuntu.com/ubuntu trusty-security universe
deb-src http://security.ubuntu.com/ubuntu trusty-security universe
deb http://security.ubuntu.com/ubuntu trusty-security multiverse
deb-src http://security.ubuntu.com/ubuntu trusty-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu trusty partner
# deb-src http://archive.canonical.com/ubuntu trusty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu trusty main
deb-src http://extras.ubuntu.com/ubuntu trusty main

```

Are you suggesting I change my update server, and if yes, how (command line)? Thank you!

---

### Post by ric_Poirier on 2014-09-11
Hi, thanks for your answer. I'm not sure exactly of what you want me to verify... Up to now, I connected to this machine only using its IP address.

---

### Post by ian-weisser on 2014-09-11
Those failures seem rather like name resolution failures: Converting foo.com to an IP address.

If so, _all_ your outbound name-based activity should fail to resolve. Pings to foo.com, e-mail to mailserver.net, time updates from pool.ubuntu.com, and package activity (which uses http) to all those named mirrors.

---

### Post by Bashing-om on 2014-09-11
ric_Poirie; Humm ??

I too see nothing wrong in the " .etc/apt/sources.list " file. I really had expected to.

As Ian advises, there should be no need to resort to "sed" to change the mirror as we are now looking at DNS .

ain't nothing but a thing

---

### Post by ric_Poirier on 2014-09-13
> **ian-weisser said:**
> Those failures seem rather like name resolution failures: Converting foo.com to an IP address.

If so, _all_ your outbound name-based activity should fail to resolve. Pings to foo.com, e-mail to mailserver.net, time updates from pool.ubuntu.com, and package activity (which uses http) to all those named mirrors.

Hi Ian,

I have tried the following (on the remote machine): ```
ping -a ca.archive.ubuntu.com
``` and here is the output: ```
ping: unknown host ca.archive.ubuntu.com
```

If I understand well what you are telling me, the problem is that this machine is unable to make the link between *ca.archive.ubuntu.com* and its IP adress? How can I fix that?

---

### Post by Bashing-om on 2014-09-13
ric_Poirier; Hey hey ;

That do seem to indicate networking problems:

Can you ping your router ?
what returns from:
```

ping -c3 127.0.0.1
ping -c3 8.8.8.8
ip link ls
sudo lshw -C network
ifconfig eth0 ##(or whichever the network is,eth1)##
cat /etc/network/interfaces

```
which will give an indication of where the problem may lie, and where to to from here.

[INDENT][INDENT]ain't no step for a stepper
[/INDENT][/INDENT]

---

### Post by ric_Poirier on 2014-09-14
Thanks for your answers Bashing-om and ian_weisser,

I decided to let the server go for now. It was only an experiment I made for a class, and I realise I have not yet enough knowledge of networks to make it work properly. I'll read some more about it, and come back to it later.

Thanks again.

---

### Post by Bashing-om on 2014-09-14
ric_Poirier; Hey !

I hope you are not feeling intimidated or overwhelmed .
If you are willing and want to learn we can work through this - at your pace.
A lack of knowledge is fixable here in 'buntu land.

[INDENT][INDENT]here there are no secrets.
[/INDENT][/INDENT]

---

