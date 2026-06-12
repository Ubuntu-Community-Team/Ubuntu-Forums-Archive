---
title: "dhcp3-server fails to update"
date: 2012-02-03
forum: New to Ubuntu
---

### Post by AlCarmon on 2012-02-03
On my last software update (in Ubuntu 10.04) dhcp3-server didn't update, but its dependents did.  I tried to update dhcp3-server 3.1.3-2ubuntu3 to dhcp3-server 3.1.3-2ubuntu3.3 with the following result:

**An error occurred**
**The following details are provided**:
E: /var/cache/apt/archives/dhcp3-server_3.1.3-2ubuntu3.3_amd64.deb: subprocess new pre-removal script returned error exit status 2

Any ideas? Thanks.

---

### Post by dzponce11 on 2012-04-19
It's probably happening because you are using an old release of Ubuntu. Try upgrading.

~~~~dzponce11

---

### Post by dzponce11 on 2012-04-19
Note: i can probably tell you whats wrong, but i need to know what ubuntu you are using.

~~~~dzponce11

---

### Post by AlCarmon on 2012-04-23
Thanks for the reply.  I have since clean slate upgraded(?) to 11.10.  Still having problems with installing programs.  Get a lot of  all did not install  due to dependency problems with various programs.  Checked all the programs mentioned, and all dependencies and suggested are there.
I am using the default repositories, so I shouldn't be getting wrong file versions.  Also getting a lot of system and Chrome crashes.
Thanks again,
Al

---

### Post by imachavel on 2012-04-23
well trying to trouble shoot your issue, I went through a list of network commands to see what my own dhcpd or dhcp3 conf would look like. I wanted to get some good logs, so thought I'd invoke a few good commands, dhclient -r, dhclient, sudo etc/network restart or whatever it is. And got a lack of ip configuration. Restarting the computer solved the problem for me, but for your sake, I would try, FIRST, find any good logs and compress them then upload them so we can all see. Then, try these commands in terminal (ctrl + alt + t) and then copy and paste the return syntax:

FIRST, ifconfig to see if you have an ipv4 address, without one dhcp updates will stop and i.p. addressing will stop, if you DON'T have an ipv4 address, you can try THIS:

sudo dhclient eth0 assuming that eth0 is your correctly configured interface, then if THAT doesn't work, try THIS out:

sudo gedit /etc/network/interfaces and I would edit it about so:

auto eth0
iface eth0 inet static
           address 192.168.0.4
           netmask 255.255.255.0
           network 192.168.0.0
           broadcast 192.168.0.255
           gateway 192.168.0.1

tell me if that does anything for you. 

[B]ifconfig -a | grep eth

[/B][B]sudo lshw -class network


wouldn't hurt to help diagnose anything either
[/B]

---

### Post by imachavel on 2012-04-23
> **AlCarmon said:**
> Thanks for the reply.  I have since clean slate upgraded(?) to 11.10.  Still having problems with installing programs.  Get a lot of  all did not install  due to dependency problems with various programs.  Checked all the programs mentioned, and all dependencies and suggested are there.
I am using the default repositories, so I shouldn't be getting wrong file versions.  Also getting a lot of system and Chrome crashes.
Thanks again,
Al

as for the fact that chrome keeps crashing try this:

sudo apt-get purge chromium-browser sudo apt-get install chromium-browser
if it's truly a more back end issue with the file system and not necessarily pertaining to chrome, then please list this as well:

lspci

and list all the installed drivers and not installed drivers. 

also before we check logs for what is crashing and not crashing ubuntu, please enter:

top

in the terminal, I'd like to see what is eating up the processor. Often times broken packages will keep trying to execute none the less creating an almost endless loop of actual execution tries(but not actual loops), and it might come up as a process hogging up a lot of processing space. This isn't guaranteed to solve the problem I'm just trying to figure out what logs to look for and where the logs are, so want to get down to a few more details first. My processor is an intel pentium 4 core 2 duo and does pretty healthy with ubuntu, right now firefox is taking up 22% of the cpu, which is not so bad. Xorg is taking up 9%

etc. etc.

We can rule out any hardware failures or OS loading failures with other dependencies failing since you can get into the OS and diagnose that dhcpd isn't working. Just for the hell of it though, what is your network interface adapter, onboard or installed in an expansion slot?

Please open 3 terminals, and in each one type each command, and list each syntax output:

$ lspci
 $ lspci | less
 $ lspci | grep -i eth

---

