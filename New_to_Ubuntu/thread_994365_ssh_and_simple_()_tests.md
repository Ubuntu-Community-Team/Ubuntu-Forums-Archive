---
title: "ssh and simple (?) tests"
date: 2008-11-26
forum: New to Ubuntu
---

### Post by candtalan on 2008-11-26
Using Ubuntu 8.04
I am starting out trying to understand and use ssh with the aim of supporting a relative with ubuntu. So far I have used basic ssh inside my home LAN, and I can connect from my laptop to a desktop. The aim, soon, is to relocate the desktop with my relative, and I will hopefully be able to log in and administer from my laptop at home with me, or maybe, anywhere.

Inside my LAN I can use ssh to connect with no problem now. The desktop has a fixed ip of an easy remember number 192.168.1.192
I generated a key pair on the laptop and copied the public key to the desktop yesterday ok, and now a command from the laptop:
ssh user1@192.168.1.192
connects the laptop to the desktop, and in the laptop terminal I can see a desktop related prompt
user1@810L:~$

I have taken the laptop to an external internet location and tried the next stage of the tests, and also with some router port forwarding - various, to try to connect to my home IP:
ssh user1@[homeIP]

but I see no login activity at all.
I could ping the home IP ok. I could also connect to and administer the home router (passworded), so I was certainly getting through to the router.

One thing also I found I could do (in desperation :-) ) was connect a telnet session, It said it was connected and I was asked for a password, although I did not proceed further. So it seemed that something was working at least. 

However, I could not get anything useful with ssh, no prompt, just a flashing cursor. To abort I used crtl-c

I am guessing that something is amiss with my router settings and I would appreciate some comments about this because I had believed I was using the router settings ok to forward (UDP) (incoming from internet to router) port 22 to 192.168.1.192 then onwards to port 22 
(the desktop in its test location at home)

My adsl router is a DrayTek Vigor2600 annex A and seems fairly sophisticated. Presumably it is working ok.

The router facilty I am using is 
NAT Setup>Configure Port Redirection Table:
Protocol (UDP), public port (22), private IP (192.168.1.192), private port (22), active (yes)

(protocol has a choice of TCP or UDP)

My first question is - should this have worked?

Second question - how can I try an experiment to appear to attempt to make an incoming connection from the external internet, whilst only initiating this from my laptop inside my LAN? The reason is that it is pretty inconvenient to travel out to an external internet location only to find my tests and cunning plan again fails..... :-(

tia


Later Edit:
1) The internet side of things worked when I chose the TCP protocol, not UDP.
2) A connection from my laptop inside my LAN to the full internet IP of the desktop also worked ok, once I chose TCP in the router redirection settings

---

### Post by cozmicharlie on 2008-11-26
You need to set up DNS.  Most routers use dynamic addresses and you need a static address.  You can get it set up free - go here [http://www.dyndns.com/](http://www.dyndns.com/).

As per testing I know their are ways to do it but I am not sure how.  Someone will post an answer.

---

### Post by aeiah on 2008-11-26
whilst the above poster is correct in that you will probably need dynamic dns once the desktop is located with your relative, you say you could ping your router and get a response over telnet so it isnt an issue for now.

telnet isnt all that secure by the way and you should probably turn it off when you're not using it for testing. you should probably see if you can actually log in via telnet with your next test over the internet though to see if it works properly so you know where the ssh problem lies.

have you made sure the desktop firewall isnt blocking the ssh port? ssh default is port 22 but i always use a different port for it. you should also of course make sure your router is forwarding the port properly. im pretty sure ssh uses TCP (and perhaps also UDP). i noticed you only forwarded UDP.  thats all i can really suggest right now

---

### Post by candtalan on 2008-11-27
> **aeiah said:**
> have you made sure the desktop firewall isnt blocking the ssh port? ssh default is port 22 but i always use a different port for it. you should also of course make sure your router is forwarding the port properly. im pretty sure ssh uses TCP (and perhaps also UDP). i noticed you only forwarded UDP.  thats all i can really suggest right now

I have created a standard ubuntu 8.04 (updated) offering, so the usual settings of iptables (?) are still probably in place. I have not installed firestarter to change anything, nor knowingly changed any desktop ports controls. But what about things working ok over the local LAN though? The desktop ports, 22 for example, are apparently not causing the internal LAN tests to fail are they? The connection within the internal LAN work. So is it ok to conclude that the desktop firewall settings are ok and that they should in principle also work when an outside connection is attempted? On condition that the port redirection is working that is.

I have had a lot of trouble trying to get my head around ports stuff and particularly redirection and or forwarding. I notice that there are no comments about my router port redirection indications - can I take it that in principle they appear to be appropriate?

ssh and UDP
I think I redirected either udp or tcp  but maybe not both, maybe I should try that?

Later edit:
The problem was the lack of TCP! I had done many experiments (not just ssh port 22) and I obviously had not tried just ssh with TCP. It seems to work with only TCP, no UDP fwiw.

This works (also) with the laptop location still inside my LAN, but with the target IP address being the full external internet IP address (using  one of the 'what is my IP address just now' facilities which exist out there)

for reference, I used the following command from the laptop:
ssh -vv user1@[IP address]

---

### Post by hyper_ch on 2008-11-27
you need to portforward tcp 22 from the router to the machine behind the router.

---

### Post by candtalan on 2008-11-27
> **cozmicharlie said:**
> You need to set up DNS.  Most routers use dynamic addresses and you need a static address.  You can get it set up free - go here [http://www.dyndns.com/](http://www.dyndns.com/).

As per testing I know their are ways to do it but I am not sure how.  Someone will post an answer.

Thank you, yes. However, just now my head is spinning with a lot of new concepts and details and stuff, and it is simpler for me to use the browser to use one of the 'tell me what my IP is' services that exist out there. Even when the relative takes possession of the desktop PC I can ask them on the phone to click the (desktop link) to the service and read to me what it says!

---

### Post by hyper_ch on 2008-11-27
most routers do support now automatic update of dyn ip accounts... either dyndns.org or no-ip.com... you just have to make an account, enter teh credentials in the router and all is well :)

---

### Post by porchrat on 2008-11-27
As hyper_ch said try forwarding TCP as well on port 22 to your machines IP address.  Also ensure that your firewall is setup to allow incoming connections on port 22.  I would recommend you use something like Firestarter or preferably UFW to open the appropriate port.

One more thing is that if you are using PKI then you need to ensure that the public key on the host is stored in the /home/user/.ssh/authorized_keys file where "user" is the username you are attempting to login as.  Make sure that the authorized_keys file and the /home/user/.ssh directory are accessible only by the user logging in.

I would assume that this has all already been done though as you were able to connect within the LAN.  Remember that if you have 2 routers (one for ADSL and one for the LAN) then the ADSL router needs to port forward port 22 to the LAN router.

---

### Post by cozmicharlie on 2008-11-27
This should help you with port forwarding.  
[http://portforward.com/](http://portforward.com/)

---

### Post by Xiong Chiamiov on 2008-11-27
> **candtalan said:**
> 
Second question - how can I try an experiment to appear to attempt to make an incoming connection from the external internet, whilst only initiating this from my laptop inside my LAN?

Use your WAN IP (the one reported by various IP-reporting sites instead of the local IP.  Also, I'd personally have a different port be accessed from the outside, and just redirect it to port 22.

---

### Post by candtalan on 2008-11-27
> **Xiong Chiamiov said:**
> Also, I'd personally have a different port be accessed from the outside, and just redirect it to port 22.

Please say more about the reasons for this?

---

### Post by porchrat on 2008-11-28
> Also, I'd personally have a different port be accessed from the outside, and just redirect it to port 22.

I also do this, however I also setup the ssh server to listen on a port other than 22 as well.

You can do this by editing the /etc/ssh/sshd_config file
Where it says "Port 22" change it to "Port #" Where '#' is the port number you want the host to listen to.

> **candtalan said:**
> Please say more about the reasons for this?

The reason for changing the default port number is that a lot of less sophisticated brute force or dictionary attack bots only look for servers on port 22.  Obviously this isn't going to protect you from the bots that scan ports first then attack the open ones, but it does help.

Here are the Wikipedia articles on [brute force]("http://en.wikipedia.org/wiki/Brute_force_attack") and [dictionary]("http://en.wikipedia.org/wiki/Dictionary_attack") attacks if you're interested.

EDIT: Keep in mind that changing the port number is not going to make the SSH host secure, it is however going to cut down on the stream of connection attempts.

---

### Post by hyper_ch on 2008-11-28
> **porchrat said:**
> The reason for changing the default port number is that a lot of less sophisticated brute force or dictionary attack bots only look for servers on port 22.  Obviously this isn't going to protect you from the bots that scan ports first then attack the open ones, but it does help.

actually, sophisticated brute force or dictionary attacks is a contrydiction IMHO ;) either it's brute force/dictionary.. but those are not sophisticated attacks. Having a secure password is enough. Changing port numbers will not help at all preventing sophisticated attacks.

---

### Post by porchrat on 2008-11-28
> **hyper_ch said:**
> actually, sophisticated brute force or dictionary attacks is a contrydiction IMHO ;) either it's brute force/dictionary.. but those are not sophisticated attacks. Having a secure password is enough. Changing port numbers will not help at all preventing sophisticated attacks.

I must agree with you there.  Changing ports is NOT a security advantage, however it is going to trim down the logs a bit (if you look at those sort of things) with fewer teenagers' bots slamming away at port 22 all the time.

---

### Post by hyper_ch on 2008-11-28
each one does it 3 time on me and not anymore - auto-banning :)

---

### Post by candtalan on 2008-11-29
> **porchrat said:**
> I also do this, however I also setup the ssh server to listen on a port other than 22 as well.

You can do this by editing the /etc/ssh/sshd_config file
Where it says "Port 22" change it to "Port #" Where '#' is the port number you want the host to listen to

Thanks. Is it necessary to change the 
/etc/ssh/sshd_config file
on both the target machine (the one with the ssh server being used) and also the (ssh client?) machine which is initiating the connection and trying to log into the server machine.

I think I understand that the router managing the server machine will need to have its port redirection changed so that something arriving at the 'non-standard-ssh-port-No' will still go to (say) port 22 of the actual target machine. 
Hey, I think this would mean that the server machine stays using port 22, because the router redirection takes care of the 'non-standard-ssh-port-No'. 

So am I correct in thinking that it is only the client  (initiating) machine that needs its /etc/ssh/sshd_config file   changed to set the 'non-standard-ssh-port-No' ? And the Router at the server end?

tia

Edit: Further information:
I have now tried it and yes I was correct in thinking that..... :-)

---

### Post by porchrat on 2008-12-01
> **candtalan said:**
> Thanks. Is it necessary to change the 
/etc/ssh/sshd_config file
on both the target machine (the one with the ssh server being used) and also the (ssh client?) machine which is initiating the connection and trying to log into the server machine.

I think I understand that the router managing the server machine will need to have its port redirection changed so that something arriving at the 'non-standard-ssh-port-No' will still go to (say) port 22 of the actual target machine. 
Hey, I think this would mean that the server machine stays using port 22, because the router redirection takes care of the 'non-standard-ssh-port-No'. 

So am I correct in thinking that it is only the client  (initiating) machine that needs its /etc/ssh/sshd_config file   changed to set the 'non-standard-ssh-port-No' ? And the Router at the server end?

tia

Edit: Further information:
I have now tried it and yes I was correct in thinking that..... :-)

Sorry I have taken so long to respond my internet has been down.

To answer your question the sshd_config file is the configuration file for running a SSH server.  The client machine doesn't need to change this file.  In fact the client machine's setup file (the setup file for the SSH client program) is the /etc/ssh/ssh_config file.  If you wish to change the port that your client uses you can add it in this file, you can also specify which user to use when attempting to connect to the server so that you don't have to type it out when you attempt to connect.

Another thing I would do if I were you is to specify that only your username may connect via SSH.  You do this by adding "Allow Users <username>" to the sshd_config file on the server machine.  Please remember to create a copy of the sshd_config file before attempting this just to be sure you have something to fall back on.

Hope this helps

---

