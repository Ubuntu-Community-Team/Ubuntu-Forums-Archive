---
title: "Adding NIC on VirtualBox"
date: 2012-10-07
forum: New to Ubuntu
---

### Post by termvrl on 2012-10-07
Hi All, 
Good Day!
i just want to ask,anybody here familiar with virtualbox.

i trying to add another eth on my ubuntu 12.04 machine. i install vbox on windows7.
i already have two nic eth0 and eth1 connect using bridged adapter.
when  i try to add another new nic using NAT adapter, i cannot connect to  internet.(i add this eth2 while the machine running). when i do ifconfig, the eth2 get the ip address release by dhcp server.

i have another ubuntu machine running using NAT(have 1 nic only) and can go to internet. 

p/s: sorry if this not the right place to ask.
Thanks.

---

### Post by DuckHook on 2012-10-07
You can also try posting your problem to the *Virtualization* forum.

Before doing so, however, please clarify. I don't quite understand your posting and am assuming the following:

1. You are running Ubuntu in a VM on Windows.
2. You have defined two nics, eth0 and eth1 as bridged adapter.
3. *Why do you need so many nics, and in particular, why do you need a third nic?*
4. You say: > i add this eth2 while the machine running
Do you mean while the VM is running? If so, you must not do this. Nics must be attached in the settings menu prior to VM startup. If they are added into the OS as it is running, there will be conflicts with your predefined nics, eth0 and eth1.
5. If, however, you did add the third nic properly (by setting it up prior to starting the VM) then why do you want to bridge two nics and NAT one nic? You should either NAT all three or bridge all three, but not mix and match. This may be what is confusing Ubuntu.

I cannot understand the need for multiple nics unless you are running the VM as a multi-homed router/firewall of some kind. But it does not make sense to do this inside a VM on top of Windows. Such critical functions should be on a base install running directly on hardware without the intervening layer of a VM (and the resource waste of Windows).

Hope this helps.

---

### Post by TheFu on 2012-10-07
I agree with DuckHook completely.

I wasn't certain what your question was after rereading the post 3 times. Sometimes it helps to **clearly explain** what you are trying to accomplish.  That means specifics.  device names, subnet parameters, routing tables, and a clear understanding of which connections are intra-machine and extra-machine. 

Sometimes we can provide a better method to a solution.

---

### Post by termvrl on 2012-10-07
> 1. You are running Ubuntu in a VM on Windows.Yes.

> 2. You have defined two nics, eth0 and eth1 as bridged adapter.Yes. i have two eth0 and eth1 as bridged adapter.

> 3. *Why do you need so many nics, and in particular, why do you need a third nic?*Act i setup this Ubuntu machine as a IDS,eth0 to connect to 192 network. eth1 as a promisc mode, so that it can listen to all traffic. 
i dont know why i cannot go to internet with my 192 network. 
i need third nic as NAT so i can go to internet. 
(i have another vm, i use NAT and it can ping google)

> 4. Do you mean while the VM is running?Yes. I add the third nic while the vm still running.

hope you can understand. 
Thanks.

---

### Post by pqwoerituytrueiwoq on 2012-10-07
if the guest is a linux os you could just create a virtual net adapter
[FONT=Courier New]sudo ifconfig eth0:1 [My IPv4 Address] netmask 255.255.0.0[/FONT]
setting is lost after reboot

---

### Post by TheFu on 2012-10-07
I think you have a routing priority issue and possibly more than 1 default route.  You'll need to resolve that before you'll get an acceptable solution.

Adding a 3rd NIC should work, but not while the VM is running.  You are basically asking for Ubuntu to support hot-swap NICs. Perhaps that is possible ... perhaps not.

If you want more help, we need specific outputs from 
* ifconfig -a
* route
* sudo iptables -L

---

### Post by DuckHook on 2012-10-07
Also,

```
lspci
```

---

### Post by DuckHook on 2012-10-07
With the greatest of respect, I'm afraid that it is still difficult to figure out your configuration and what you are trying to do. I am beginning to suspect the following:

1. You only have one actual physical nic (_N_etwork _I_nterface _C_ard), which is an actual piece of hardware, installed in your computer.
2. You have created two separate bridges to this one card within the settings of your first VM (let's call this VM Alpha). The first bridge is eth0 and the second is eth1.
3. This setup does not allow you to access the network (Internet).
4. You then created another completely separate VM (let's call this VM Beta) with only NAT as your network interface and this allowed you to access the network (Internet).
5. You thought that by creating a third virtual network interface in VM Alpha, you could then access the Internet because this seems work for you in VM Beta.

Is my description an accurate description of your setup and your thought processes?

If so, then please understand the following:

You cannot make two bridges to one network card within the same VM without creating major problems for the operating system. Just ask yourself: when my browser tries to reach out to the Internet, which bridge (virtual network card) is it supposed to use? You are confusing your operating system by having two bridged connections. If you now add a third, you are only making things worse.

Conclusion: you are trying to make things way too complicated. While such a setup is theoretically possible, it is way beyond the scope of a beginner forum to thrash out such a configuration, and it requires very high-level network knowledge to even attempt such a thing. You would have to play with subnet masks and routing tables, and even then, the whole thing would be fragile as all get go.

Strong suggestion: Eliminate all but one network connection. It doesn't matter if you choose NAT or bridged. I prefer bridged, but this is not a big deal either way. The important thing is to stick to one connection and leave it at that. If you must run your card in promiscuous mode (I assume for gaming, though I can't think of any Linux games that require this), then turn on this mode only for times when you must have it. Otherwise, run it safely and securely.

---

### Post by termvrl on 2012-10-07
HI All,
Thanks for your help.

What DuckHook said is correct, this is what i do 
> 1. You only have one actual physical nic (_N_etwork _I_nterface _C_ard), which is an actual piece of hardware, installed in your computer.
2. You have created two separate bridges to this one card within the  settings of your first VM (let's call this VM Alpha). The first bridge  is eth0 and the second is eth1.
3. This setup does not allow you to access the network (Internet).
4. You then created another completely separate VM (let's call this VM  Beta) with only NAT as your network interface and this allowed you to  access the network (Internet).
5. You thought that by creating a third virtual network interface in VM  Alpha, you could then access the Internet because this seems work for  you in VM Beta.Attached together is the network diagram of what i try to do. 
If you can suggest me the best way how i can achieve this.

And this is my ifconfig -a
```
This is my ifconfig -a

root@ubuntu:~# ifconfig -a
eth0      Link encap:Ethernet  HWaddr 08:00:27:a9:9f:f0
          inet addr:192.168.1.20  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::a00:27ff:fea9:9ff0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:814 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1345 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:60256 (60.2 KB)  TX bytes:151159 (151.1 KB)

eth1      Link encap:Ethernet  HWaddr 08:00:27:13:6f:e9
          inet6 addr: fe80::a00:27ff:fe13:6fe9/64 Scope:Link
          UP BROADCAST RUNNING PROMISC MULTICAST  MTU:1500  Metric:1
          RX packets:43061 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:35326942 (35.3 MB)  TX bytes:468 (468.0 B)

eth2      Link encap:Ethernet  HWaddr 08:00:27:de:7e:2e
          inet addr:10.0.4.15  Bcast:10.0.4.255  Mask:255.255.255.0
          inet6 addr: fe80::a00:27ff:fede:7e2e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1180 (1.1 KB)  TX bytes:1152 (1.1 KB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:444 (444.0 B)  TX bytes:444 (444.0 B)
```

Thanks again.

---

### Post by DuckHook on 2012-10-08
Okay. I believe that we are finally getting to an understanding of what you are trying to do. Might I suggest that, in the future, you should give this much information from the beginning if you want help, rather than forcing us to guess at your configuration and what it is that you are trying to do?

If I can summarize:

1. You want to run *Snort* to detect intrusion attempts.
2. You are running Snort in Ubuntu on a VM on top of Windows.
3. You have only one physical NIC installed in 192.168.1.1

I will start by saying that your concept of your network topology is all wrong. If your router is a standard commercial type router, then it acts as both your router and your firewall all at once. You do not have a separate firewall that is independent of the router. Once again, I must make assumptions. If I am wrong and your physical topology is actually as per your illustration, then your firewall is useless and cannot protect you from malicious traffic. However, I am betting that the three pieces of equipment in your illustration are actually only one piece of equipment--a single router that acts as firewall, switch and router. If I am wrong, then please clarify.

1. If you want to use *Snort*, then you should not run it inside a virtual machine. It should be running on the OS that is running on the base equipment. In other words, either run the Windows version of *Snort* if you want Windows as your base OS, or nuke Windows and install Ubuntu as your base OS if you want to run the Linux version of *Snort*.

2. Right now, you are running into problems because you are asking your one NIC to do two contradictory things at the same time. You have set it in promiscuous mode for *Snort*, and you have set it in nonpromiscuous mode for Internet browsing. This is what happens when you bind the same physical NIC to two virtual NICs in a virtual machine. This is not possible and just cannot work.

3. Run your NIC either in promiscuous mode or in nonpromiscuous mode but never both. But be warned: setting your NIC in promiscuous mode eats up CPU cycles and slows down your computer.

By simplifying your setup, you should now be able to browse and run *Snort* at the same time. Remember, do *not* assign multiple virtual NICs to one physical NIC within the same VM. This only leads to problems. There should be only a eth0 on your VM and nothing else.

---

### Post by termvrl on 2012-10-08
Hi
First of all,Sorry for insufficient information.
i thing i get your point. but, because of i have limited resources(only one pc).
i will try to add another physical nic in my pc, so one physical nic for promisc mode and another one for nonpromisc. And i will look over my network topo again and make it simple. If still dont work, i have no choice to get a dedicated machine for my ids.T_T

Thanks for your advice!Really appreciate it.
i will update later.

---

### Post by DuckHook on 2012-10-08
Sorry. Now I'm the one being unclear.

You do not need another physical NIC. You just need to make sure that you delete all virtual NICs except one. In other words, you should only have eth0. Your problems are caused by creating eth1 and eth2. That is what I mean by simplifying your system. In your case, buying another physical NIC may actually make your system too complicated again.

Good Luck!

---

### Post by termvrl on 2012-10-08
Hi All
i doing some simple testing to understanding the virtualbox networking.
And Yes, it just like what DuckHook said, 
> Right now, you are running into problems because you are asking your one  NIC to do two contradictory things at the same time. You have set it in  promiscuous mode for *Snort*, and you have set it in  nonpromiscuous mode for Internet browsing. This is what happens when you  bind the same physical NIC to two virtual NICs in a virtual machine.  This is not possible and just cannot work.i found that:
1. we cannot set two bridged virtual nic assigned to single physical nic within the same Virtual Machine
2. we cannot set bridged and NAT to single physical nic within the same machine.
3. we cannot set promisc mode and non if we use single physical nic.

So,if we want to have two nic in the virtual machine, we need two physical nic in the hosting machine. 

Thanks again for your help.

---

