---
title: "laptop (kubunt) to old netbook ubuntu server (headless no gui) to sign in and startup"
date: 2014-12-31
forum: New to Ubuntu
---

### Post by gregory10 on 2014-12-31
My problem is I don't know the commands to use but also if I need a crossover cable
I have been doing research but not able to find anything to suite this.
I'm just a learner the whole idea of doing this is to get hands on experience so I can run a server later.

I am running Kubuntu on my laptop
ubuntu server on the netbook: the netbook an old Asus Eeepc has no monitor because am converting that to use with a raspberry pi voip phone system

At present it's about finding ways to do all this together: the voip phone system with a work-group-server simulating a small office setup.
Right now its about setting up the work-group server small office scenerio. So trying going headless using the Asus Netbook
it works ok with a monitor and can sign in and it starts fine all working.

Now I need to do this remotely via a network cable pare to pare. I think I need a crossover cable but this question if for the commands to use remotely via Konsole.
I need to know what commands to use so I can sign into the server from the laptop connected straight through using a network cable

I need confirmation that I do need the crossover cable because was told these days these systems detect the cable you are using and do it auto
Also need to know what commands I use via the terminal on the laptop and what to expect when I go to connect.

thanks for your help to anyone who can help with some advice on the commands I need to use to login the the server remotely
(the cable thing is a side issue)
G

---

### Post by raja.genupula on 2015-01-01
All I understood , You are trying to access monitor less Ubuntu Server from a machine remotely. You can access a Linux machine remotely in many ways like telnet(not recommended),SSH,VNC etc. 

As you said you want to learn command-line way of usage you better use through SSH. All you need to make sure is having installed SSH Server at Server machine and SSH Client at client machine i.e your Kubuntu. [https://www.digitalocean.com/community/tutorials/how-to-use-ssh-to-connect-to-a-remote-server-in-ubuntu](https://www.digitalocean.com/community/tutorials/how-to-use-ssh-to-connect-to-a-remote-server-in-ubuntu) & [https://charlesauer.net/tutorials/ubuntu/openssh-server-ubuntu.php](https://charlesauer.net/tutorials/ubuntu/openssh-server-ubuntu.php)  will help you.

Just go through them.

---

### Post by gregory10 on 2015-01-01
Thanks for the quick reply @raja.genupula
Just had a quick look through those links 
appreaciate what you had to say.

still need confirmation to know if I actually need a crossover cable
the ones I have a normal are all straight through standard cables. should I expect a connection with the standard cable?
I did try to connect and the network manager looked to be working hard to establish a connection but was not completing.
I just don't know what to think of that and my thoughts are that it is the cable giving a problem when the system tries an auto connect.
If not it is that I need to set up an ssh connection in the network manager. Just need confirmation that is right and it is not the type of cable I am using.

I basically don't want to have to buy a cable unless I have  to. I would know if I tried the crossover cable. so in the meantime it's a bit confusing.
I don't know if the connections problem was the cable or the wired connection I tried to set up using ssh I could have put some of the details in wrong.
So I am hoping someone can tell me if the crossover cable is a must have in this situation going pair to pair.
I was told I don't need the crossover cable but am now confused. hate to think it was the problem and not my setting up of the ssh details in network manager on kubuntu.

---

### Post by ajgreeny on 2015-01-01
If both machines are using wifi you will not need any cable at all; if one or both are using cable connections you still do not need to use a crossover cable to connect the two machines using SSH, as the connection between machines is carried through the router.

Attached is a txt file I wrote as a quick reminder of how to use SSH to connect home computers on the same LAN.
Don'r assume everything is still exactly the same in terms of GUI you might see as this was written a long time ago, but the basics should still be fine.
I hope it helps you out, as a starter at least.

---

### Post by gregory10 on 2015-01-01
@ajgreeny
thanks indeed for this advice and the text file got it downloaded

will try it soon as possible 
I guess a lot of it is confidence. Can only get that through trying these things but have had a few things resolved now since starting this endevour.
all the best for the New Year
G

---

### Post by Holger_Gehrke on 2015-01-01
If the interfaces on both machines are set up correctly, an 'ifconfig eth0' in the shell should (among a lot of other stuff) tell you the IP-address associated with that network interface. Now try 'ping -c 10 <IP-adress of the other machiche>' in the shell of each PC. If cabling, interface settings etc are good, you should get 10 Lines of '64 bytes from <other machines adress>: icmp_req=<counter> ttl=64 time=x.xx ms' and a few lines of statistics.

If avahi (an open source mDNS, similar to ZeroConf and Bonjour) is running (which it should be, it's part of the standard installation) you should also be able to use the name of the other machines as given by 'hostname' in the ping command.

---

### Post by SeijiSensei on 2015-01-01
Are you trying to connect the machines to each other over an Ethernet cable, or are they connected to a router or hub?  If the latter, you don't need a crossover cable.  If you are trying to wire the machines directly together, whether that works depends on whether the network adapters have "auto-sensing" that will determine the correct wire pairs to use. 

Here's a quick method to set things up:
1)  Attach the cable to the network ports on the two machines.

2)  On one machine issue the command:
```
sudo ifconfig 10.10.10.10 netmask 255.255.255.0 broadcast 10.10.10.255
```

3) On the other machine enter
```
sudo ifconfig 10.10.10.11 netmask 255.255.255.0 broadcast 10.10.10.255
```

4) Now on this same machine try 
```
ping 10.10.10.10
```

If you get replies, the adapters have used auto-sensing and you should be good to go.  If the pings time out, you'll need a crossover cable, or better yet a small router or network switch.

---

