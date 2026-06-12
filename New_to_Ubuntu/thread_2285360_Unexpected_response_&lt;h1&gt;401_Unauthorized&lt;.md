---
title: "Unexpected response: &lt;h1&gt;401: Unauthorized&lt;/h1&gt;Unauthor"
date: 2015-07-05
forum: New to Ubuntu
---

### Post by Xpdin on 2015-07-05
Hi,


I am a very beginner Linux user.


I use Lubuntu-core (Minimal Install) maybe this could cause some of the beyond issues. 


I have just installed Transmission like that:


```
sudo add-apt-repository ppa:transmissionbt/ppa
```


The above command wasn't accepted from the beginning, I had to install phyton software(something like that)...


```
sudo apt-get update
sudo apt-get install transmission-cli transmission-common transmission-daemon
```


Change user with my username:


```
cd /home/user/Downloads
mkdir transmission
cd transmission
mkdir completed incomplete torrents
```


```
sudo usermod -a -G debian-transmission user
```


```
sudo chgrp -R debian-transmission /home/user/Downloads/transmission
```


```
sudo chmod -R 775 /home/user/Downloads/transmission
```


When I use :


```
transmission-remote --add the link to the torrent
```  it appears:


```
Unexpected response: <h1>401: Unauthorized</h1>Unauthorized Usern
```


If it could help you these:


```
 ps aux | grep transmission
debian-+   550  0.0  0.1  31280  2956 ?        Ssl  13:35   0:00 /usr/bin/transmission-daemon -f --config-dir /var/lib/transmission-daemon/info
root      1960  0.0  0.0   4676   828 pts/0    S+   13:46   0:00 grep --color=auto transmission

```


```
ps aux | grep transmission
debian-+   550  0.0  0.1  31280  2956 ?        Ssl  13:35   0:00 /usr/bin/transmission-daemon -f --config-dir /var/lib/transmission-daemon/info
root      1966  0.0  0.0   4676   824 pts/0    S+   13:49   0:00 grep --color=auto transmission

```


It seems that my problem could be in here:
If someone could explain how to


> ```
--config-dir /var/lib/transmission-daemon/info
```


Edit your settings.json file as needed. 
[https://trac.transmissionbt.com/wiki/EditConfigFiles](https://trac.transmissionbt.com/wiki/EditConfigFiles) 
[https://trac.transmissionbt.com/wiki/UnixServer/Debian](https://trac.transmissionbt.com/wiki/UnixServer/Debian)


Thank you for your help.

---

### Post by sandyd on 2015-07-05
Try
```

transmission-remote --auth username:password -l

```

---

### Post by Xpdin on 2015-07-07
Thanks sandyd,

I have just tried your command, for both the normal and the root username, and on both ways, after "sudo -i" and befor it, and for all 4 ways, after I press enter it only appear the sign > at the beginning of the new line.

When the new line with " > " appears there I insert 

```
transmission-remote --add the link to the torrent
``` and nothing happens.

If would be someone in here how could help me to "Edit your settings.json file as needed."

I opened the same topic in [here]("https://forum.transmissionbt.com/viewtopic.php?f=9&t=17156&e=1&view=unread#unread") too, if someone has any ideas for my last replay...

Kind regards.

---

### Post by Bucky Ball on 2015-07-07
Transmission is in the repositories. Why not install it from there??? You don't need to install a third-party repo unless there is some specific reason. In fact, better not to.

Perhaps remove Transmission then the PPA, then:

```
sudo apt-get autoremove
sudo apt-get update
sudo apt-get upgrade
```

Open Synaptic package manager (also available in the repos) and install Transmission.

---

### Post by Xpdin on 2015-07-07
Thank you Bucky Ball...

Excuse me, Lubuntu-core (Minimal Installation) doesn't have Synaptic package manager, and AT LEAST FOR THE MOMENT, I would like not to install it, if will not be so big chances to install the needed software without Synaptic package manager, I will install it but, still I will do my best to keep Lubuntu as core as possible... if this will be possible for a Linux beginner user...

As, for why I am trying to use Transmission from the terminal, (not GUI) is because of my little/big obsesion [http://ubuntuforums.org/showthread.php?t=2285225&page=2&p=13315544#post13315544](http://ubuntuforums.org/showthread.php?t=2285225&page=2&p=13315544#post13315544)

Sorry, I am repeating, if I will not manage to keep the system and the applications as core as possible, with my beginner knowledges, I will try to leave step by step(as less as possible) from their cores. 

Many appreciations...

---

### Post by Rob Sayer on 2015-07-07
> **Xpdin said:**
> Thank you Bucky Ball...

Excuse me, Lubuntu-core (Minimal Installation) doesn't have Synaptic package manager, and AT LEAST FOR THE MOMENT, I would like not to install it, if will not be so big chances to install the needed software without Synaptic package manager, I will install it but, still I will do my best to keep Lubuntu as core as possible... if this will be possible for a Linux beginner user...

As, for why I am trying to use Transmission from the terminal, (not GUI) is because of my little/big obsesion [http://ubuntuforums.org/showthread.php?t=2285225&page=2&p=13315544#post13315544](http://ubuntuforums.org/showthread.php?t=2285225&page=2&p=13315544#post13315544)

Sorry, I am repeating, if I will not manage to keep the system and the applications as core as possible, with my beginner knowledges, I will try to leave step by step(as less as possible) from their cores. 

Many appreciations...

Unfortunately you have missed the point of  		Bucky Ball's post.

The relevant issue is not Synaptic.  It's the fact that you are trying to install something that is in the beta tested repos from a ppa.  That means you're installing a version that is *not tested for your release of ubuntu*.  Linux in pretty stable but you can destabilize it, and that's an excellent way to do it.  Figuring out which packages you'll need in a minimal install is complicated enough for a newbie without you making it worse like that.

I have 2 linux boxes, no windows anymore, and neither of them has a single ppa in their sources lists.  And unless I need to use one because the app will do something I can't do without and there is absolutely nothing in the repos that'll do it.

And installing Synaptic is not going to compromise the lightness or coreness ... whatever the frak that means ... of the OS.

---

### Post by Bucky Ball on 2015-07-08
You can install transmission with:

```
sudo apt-get install transmission
```

That's it. :)

If you intend installing everything through the terminal, all good. If not, you are either going to need Synaptics or Software Centre. Good luck.

PS: 

```
 And installing Synaptic is not going to compromise the lightness or coreness ... whatever the frak that means ... of the OS. 
```

Exactly. Synaptic is what's used in regular Lubuntu, and, as I say, if you are happy to install everything via the terminal, all well and good. If not ...

If you want to go really minimal, install the mini.iso then lxde and take it from there. Depending on what you add you may end up with something lighter than Lubuntu-core, maybe not. :)

---

### Post by Xpdin on 2015-07-08
Ups.. :)


My apologize for missing the most important part of  Bucky Ball's post, and because I didn't try to understand better what repos/repository means... now I think that I understand and I hope I get his point well, and I agree with you 100%..


Hopefully you did't get my massage as a rude one or even as a high "tone"/"intonation" or as a reproach to your advises...


I thought that Transmission which I was trying to use with the commands from the first topic is a stable version and I download it from a sure(secure) source. It seems that for the moment is not any Transmission version to use from the terminal, and meet those two conditions, is it true?


> **Bucky Ball said:**
> Transmission is in the repositories. Why not install it from there??? You don't need to install a third-party repo unless there is some specific reason. In fact, better not to.


Perhaps remove Transmission then the PPA, then:


```
sudo apt-get autoremove
sudo apt-get update
sudo apt-get upgrade
```


Open Synaptic package manager (also available in the repos) and install Transmission.


> **Bucky Ball said:**
> You can install transmission with:


```
sudo apt-get install transmission
```


That's it. 


If you intend installing everything through the terminal, all good. If not, you are either going to need Synaptics or Software Centre. Good luck.


 


Of course I will follow your recommendations...


Tell me please is it ok to start with 


```
sudo apt-get remove transmission-gtk
sudo add-apt-repository --remove ppa:transmissionbt/ppa
```


And after that the 3 commands you where saying about...


```
sudo apt-get autoremove
sudo apt-get update
sudo apt-get upgrade
```


Should I use the beyond 2 commands too?


```
sudo apt-get autoclean or 
          sudo apt-get clean

```


Regards.

---

### Post by Bucky Ball on 2015-07-08
Yes, you can use them. As I mentioned, remove the transmission you have installed and the ppa. Then:

```
sudo apt-get autoclean
sudo apt-get clean
sudo apt-get autoremove
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
sudo apt-get install transmission
```	

... should do it.

---

### Post by sandyd on 2015-07-08
Side note:
Transmisison-remote + transmission-daemon does work when installed from the repos without PPA.
```

transmission-remote --auth transmission:transmission -l
ID     Done       Have  ETA           Up    Down  Ratio  Status       Name
Sum:              None               0.0     0.0

```

Additional notes:
To change username/password, run
```

sudo nano /var/lib/transmission-daemon/info/settings.json
```
To change the username, change the rpc-username value
To change the password, change the rpc-password value (value will be re-encoded the next time transmission is restarted)

In order to access transmission using transmission-remote from a computer other than the one you are running on, edit rpc-whitelist with your wanted values.

Ex. to allow 10.0.0.0/8, and 127.0.0.1, use
```

"rpc-whitelist": "127.0.0.1,10.*.*"
```

---

### Post by Xpdin on 2015-07-11
I installed transmission with 

```
sudo apt-get install transmission
```

but I can't see it in my programs list as I can see in 

Accessories 
- File Manager PCManFM
                   - Leafpad

Internet 
       - Google Chrome
etc...

or when I run a downloaded .torrent file it doesn't happen nothing...

I think I have it installed because...

 ```
sudo apt-get install transmission
Reading package lists... Done
Building dependency tree       
Reading state information... Done
transmission is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

Thank you.

---

