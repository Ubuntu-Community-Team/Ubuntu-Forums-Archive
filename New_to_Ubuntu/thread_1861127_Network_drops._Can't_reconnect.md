---
title: "Network drops. Can't reconnect"
date: 2011-10-15
forum: New to Ubuntu
---

### Post by vasa1 on 2011-10-15
After upgrading to 11.10, I'm finding that my DSL net connection drops after about 10-15 min and I have to reboot to start it again.

Just logging out and logging in doesn't seem to help.

Please help me fix this!

---

### Post by Lisiano on 2011-10-15
Could you please be a bit more specific as to how you connect? Do you use a modem attached to your computer or use a router? Did it start recently? Did you install anything new recently?

---

### Post by vasa1 on 2011-10-15
> **Lisiano said:**
> Could you please be a bit more specific as to how you connect? Do you use a modem attached to your computer or use a router? Did it start recently? Did you install anything new recently?

I have a cable internet connection. It's a DSL connection. I just have to provide my laptop's MAC, ISP username and password. No router or modem at my end.

It started after I upgraded to 11.10 from 11.04 which worked without problems.

I have not tweaked/installed any software after the upgrade. As I said, after it drops, I have to reboot to get it to work. I don't do anything other than reboot.

---

### Post by vasa1 on 2011-10-15
I hope this picture helps:

Edit: removed pic as per suggestion below

---

### Post by Lisiano on 2011-10-15
(No experience with DSL on Ubuntu)
Go to Network Manager -> Edit Connections -> DSL -> Your DSL connection name -> Edit -> Make sure everything is correct in there. Try ticking Connect Automatically and Available to All Users.
When you disconnect, try pressing the Network Manager icon and pressing your DSL connection name.


EDIT: Saw your new post, please remove the attachment as someone with malicious intent might try attacking your IP.
As another way, try telling Ubuntu to turn off your network interface then turn it on
Open a terminal (Ctrl+Alt+T) and type these commands
```
sudo ifconfig eth0 down
sudo ifconfig eth0 up
```
It will ask for your password, type it, note: it won't be visible, even asterisks.

---

### Post by vasa1 on 2011-10-15
> **Lisiano said:**
> (No experience with DSL on Ubuntu)
Go to Network Manager -> Edit Connections -> DSL -> Your DSL connection name -> Edit -> Make sure everything is correct in there. Try ticking Connect Automatically and Available to All Users.
When you disconnect, try pressing the Network Manager icon and pressing your DSL connection name.

Yes, that's how I set it up. Connect automatically and Available to all users.

I can't get a screenshot of the dropdown otherwise I'd post that here but when the net is connected I see:
DSL Connection 3
My other DSL Connections and auto eth0
Disconnect
Enable Networking (ticked)
Connection information
Edit connections

Then (from memory) when the net drops in this new way (on 11.10), none of my connections are listed in the dropdown although they're available in "edit connections".

---

### Post by vasa1 on 2011-10-15
> **Lisiano said:**
> ...
As another way, try telling Ubuntu to turn off your network interface then turn it on
Open a terminal (Ctrl+Alt+T) and type these commands
```
sudo ifconfig eth0 down
sudo ifconfig eth0 up
```...

The first command killed my connection just the way it has been doing in post 1.
The second command didn't help in restoring the connection. I'm back after a reboot :(

---

### Post by Lisiano on 2011-10-15
Sorry, I have no more ideas as to why this is happening.
The only thing that might help would be trying this
```
sudo service networking stop
sudo service networking start
```
As previous method, it will also turn off your connection so try it when your connection drops again.

---

### Post by vasa1 on 2011-10-15
> **Lisiano said:**
> Sorry, I have no more ideas as to why this is happening.
The only thing that might help would be trying this
```
sudo service networking stop
sudo service networking start
```
As previous method, it will also turn off your connection so try it when your connection drops again.

Not to worry and appreciate the help!

I suspect it's not something serious like drivers or whatever ... just some config issue.

I must mention that towards the end of the upgrade process, there was "an offer" to retain some old setting relating to the network manager but I went with the option to have the all new whatever it was. I can't be more specific since I was really stressed by that time even though everything was going error-free.

Perhaps, the problem may just go away by itself! It's 35 min since I restarted the computer and logged in.

---

### Post by Lisiano on 2011-10-15
The file Oneiric tried to install is
/etc/NetworkManager/NetworkManager.conf
The old Natty file is
/etc/NetworkManager/NetworkManager.conf.dpkg-old

Take a look inside them, they might contain some sensitive stuff like MACs and IPs so if you wish to post those, please substitute/censor the MACs and IPs.

---

### Post by vasa1 on 2011-10-15
> **Lisiano said:**
> The file Oneiric tried to install is
/etc/NetworkManager/NetworkManager.conf
The old Natty file is
/etc/NetworkManager/NetworkManager.conf.dpkg-old

Take a look inside them, they might contain some sensitive stuff like MACs and IPs so if you wish to post those, please substitute/censor the MACs and IPs.

That's pretty sharp!
```
**New**:
[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=false

**Old**:
# This file is installed into /etc/NetworkManager, and is loaded by 
# NetworkManager by default.  To override, specify: '--config file' 
# during NM startup.  This can be done by appending to DAEMON_OPTS in 
# the file:
#
# /etc/default/NetworkManager
#

[main]
plugins=ifupdown,keyfile

no-auto-default=00:32:ea:d2:24:31,

[ifupdown]
managed=false

```

I hope you can make sense of that. I did fudge the MAC address. Re. IP addresses, they're dynamic, AFAIK but they don't figure here in any case.

---

### Post by Lisiano on 2011-10-15
The only thing that changed is that this line ```
no-auto-default=00:32:ea:d2:24:31,
``` Is not present in the new file. Yet it does not explain why you lose the network list.

Offtopic: If you have multiple computers, a laptop or guests that sometimes come with their laptops and want to browse the web, you should get a router to handle the DSL connection. If you get a router with WiFi you could then walk around your home with your laptop and still be on the net, meaning you don't always have to stay in one spot.

Ontopic: Have you tried using a LiveCD of 11.10? Sometimes upgrades can break stuff in weird ways that are hard to find.

---

### Post by vasa1 on 2011-10-15
> **Lisiano said:**
> The only thing that changed is that this line ```
no-auto-default=00:32:ea:d2:24:31,
``` Is not present in the new file. Yet it does not explain why you lose the network list.


Well, it's been ~75 min without dropping. Maybe the gremlin took off for elsewhere?

Either way, if I get a drop again, I'll first try the second line you suggested above:
```
sudo service networking start
```
I could also try to add the missing part into the new config file?

> 
Offtopic: If you have multiple computers, a laptop or guests that sometimes come with their laptops and want to browse the web, you should get a router to handle the DSL connection. If you get a router with WiFi you could then walk around your home with your laptop and still be on the net, meaning you don't always have to stay in one spot.

I'm the only user and I don't encourage others. This connection is MAC-bound unless I give the ISP details of another PC.

> 
Ontopic: Have you tried using a LiveCD of 11.10? Sometimes upgrades can break stuff in weird ways that are hard to find.
Yes, I still have the 11.10 LiveUSB. I had used to it check that 11.10 would be fine and that I could log on, and do stuff I wanted to. Then, I went and did the upgrade over the net via Update Manager since Canonical feels it's the way to go.

---

### Post by Lisiano on 2011-10-15
Offtopic: When you use a router, the ISP ONLY sees the routers MAC, thus anything connected to the router, be it wireless or by wire, is able to use the internet but the ISP still sees it as 1 machine. Some routers also provide tools to Spoof it's own MAC so you don't have to call the ISP to tell them the new MAC. For example, the IP my PC thinks it has is 192.168.1.68 but if I go to any website that tells me my IP, I will get my real one 84.xxx.xxx.xxx. Now if there was a website that could tell a IPs MAC it would be the routers MAC instead of anyone on the network. Currently I have around 5 systems connected to my router, 2 desktops, 1 android phone, 1 development board, 1 IPTV box. From the web, they all are the same.

Ontopic: Just incase, you should first try running the stop one, then the start one.

[quote=vasa1]Maybe the gremlin took off for elsewhere?[/quote]
Now that I think about it, maybe it was something on the ISPs end? Did you give them a call? Remember to tell you are using Linux only if they try to give you instructions on how to do something, since if you tell them early, they might think you are a Linux Guru and tell you that they can't help people with Linux and hang up (Even if you are just asking information). My ISP is great, if anything, I call them (Toll-free) and if they ever want to get some information out of me, they switch me over to a specialist that then tells me what to do.

---

### Post by vasa1 on 2011-10-15
> **Lisiano said:**
> Offtopic: When you use a router, the ISP ONLY sees the routers MAC, thus anything connected to the router, be it wireless or by wire, is able to use the internet but the ISP still sees it as 1 machine. ...
That's a whole science by itself and a bit like rocket science to me.
> 
Ontopic: Just incase, you should first try running the stop one, then the start one.

Will do. Since there's no harm in running the first one if the connection isn't there.

> 
Now that I think about it, maybe it was something on the ISPs end? ...
I doubt it. Not that the ISP's anywhere near perfect, but it would be a coincidence that a reboot and the net reconnecting happened at the same time three times.

And my ISP's workers are usually temps who are taught the minimal trouble-shooting skills and Linux is not one of those skills. As a matter of fact I don't know anyone else at a personal level who is using Linux.

Anyway, as you suggested, it's possible that it was an ISP issue. It's now ~2h without dropping. On other days, it would have dropped (and reconnected by itself) at least twice or thrice by now!

So, once again, thanks for the help! Who knows, the first code you gave could have caused the gremlin to flee?

---

### Post by Lisiano on 2011-10-15
The ifconfig command just turned off and on your ethernet port, nothing else.

It's possible that it is not a coincidence since sometimes they might reset your connection, Ubuntu will log it as a unplugged cable/etc and won't reconnect. Rebooting helps then since it notices that the cable is plugged in and everything is okay.
Next time it happens, try calling your ISP and demand to talk to a specialist if the temps can't do anything.

---

### Post by vasa1 on 2011-10-16
The gremlin returned. But, in the meantime, I did a little more reading.

I came across this post by garvinrick4:
[http://ubuntuforums.org/showpost.php?p=11345797&postcount=10](http://ubuntuforums.org/showpost.php?p=11345797&postcount=10)

It suggested
```
sudo /etc/init.d/network-manager restart
```

And this is the terminal "output" that I got on running it when my net connection dropped like I described previously:
```

mycomp:~$ sudo /etc/init.d/network-manager restart
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service network-manager restart

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the stop(8) and then start(8) utilities,
e.g. stop network-manager ; start network-manager. The restart(8) utility is also available.
network-manager stop/waiting
network-manager start/running, process 4070
mycomp:~$ 
```

The result was that I now saw all my connections and was able to attempt a reconnection.

I also agree that the break in connectivity was from my ISP's end but it appears that Ubuntu's  (11.10, not 11.04) response was that the network-manager went into stop/waiting mode. Running ```
sudo /etc/init.d/network-manager restart
``` seems to have reactivated it which was something I otherwise had to achieve by restarting the computer.

Now my question is: what do I do about this surprisingly verbose advice that resulted on running the code provided by garvinrick4:
> Since the script you are attempting to invoke has been converted to an
**Upstart** job, you may also use the stop(8) and then start(8) utilities,
e.g. stop network-manager ; start network-manager. The restart(8) utility is also available.
What is an **Upstart job** and what does **(8)** refer to? I did do man Upstart but I'm not much the wiser after reading that. It's a bit advanced!

But I feel progress is being made ...

---

### Post by Lisiano on 2011-10-16
It's generally asking you to use service instead of /etc/init.d, while init.d is still usable (I prefer it btw but gradually moving to services)
To be more precise```
sudo service network-manager restart
```

EDIT: The 8 refers to the manual page you can read more about it on.
```
man 8 stop
``` OR just simply
```
man stop
```

---

### Post by vasa1 on 2011-10-16
[QUOTE=Lisiano;11354761]It's generally asking you to use service instead of /etc/init.d, while init.d is still usable (I prefer it btw but gradually moving to services)
To be more precise```
sudo service network-manager restart
```

Okay, thanks for clearing that up. I'll wait for a couple of days to see how things play out and then mark the thread as Solved.

---

### Post by vasa1 on 2011-10-17
Actually, I forgot about
```
sudo service network-manager restart
```

If that works, that should be easy to alias and I won't have to chain two commands the first involving sudo!




One more question and a very basic one!

Can I chain two commands that involve **sudo**?

Can I do:
```
sudo stop network-manager && start network-manager
```

My bright idea is to have a line in **.bash_aliases** like:
```
alias qqq='sudo stop network-manager && start network-manager'
```

I guess it will fail because the first one will require my password.

Is there a magical solution?

---

### Post by Lisiano on 2011-10-17
It will still work but use this instead```
sudo service network-manager restart
```

---

### Post by vasa1 on 2011-10-17
> **Lisiano said:**
> It will still work but use this instead```
sudo service network-manager restart
```

Okay. That's what I did:
```
alias qqq='sudo service network-manager restart'
```

This is a million times better than having to reboot which is what I was doing.

(I'm still wondering if it's possible to fix things as they were in 11.04 in which network manager would "stop" but I'm marking this as "Solved". Thanks once again for your help!)

---

### Post by rimibchatterjee on 2011-11-01
I'm having exactly the same problem since I installed 11.10 on my Lenovo laptop yesterday. Connection shuts down if idle or without warning, then the link disappears from the NM menu although it is visible when editing, it cannot be activated. Only solution that works is reboot. Vasa1, have you been able to fix the problem? It's happened twice already.
Previously I had Ubuntu 10.04 on my desktop (which is no more) can 't seem to be able to change my distro in my profile :(

Edit: am I correct in believing that this command line restores the network (instead of rebooting), but doesn't actually solve the problem?

---

### Post by vasa1 on 2011-11-01
> **rimibchatterjee said:**
> ...
Edit: am I correct in believing that this command line restores the network (instead of rebooting), but doesn't actually solve the problem?

That's the way it looks. No need for re-login or reboot but it's not the solution IMHO. We shouldn't have to do that :(

---

