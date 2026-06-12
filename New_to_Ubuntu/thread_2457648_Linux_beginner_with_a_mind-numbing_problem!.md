---
title: "Linux beginner with a mind-numbing problem!"
date: 2021-02-06
forum: New to Ubuntu
---

### Post by 42pjcqyy on 2021-02-06
Hi, For a long time I have been looking for a forum which welcomes beginners to Linux and only just found this one, which looks like a great place to read and learn. 

I rented a VPS to learn linux. Installed Ubuntu 20.04. I followed some guides for securing the VPS (ssh only, root off, passwordauthentication off, changed ssh port), and then installed mullvad VPN on it (CLI). That's where my nightmare began! I have learned a lot while trying to fix the problem but no solution found yet and I have searched for 3 DAYS for solutions! 

I want the VPN to tunnel/encrypt the outbound traffic from the VPS to the outside world, NOT for a VPN for myself to use from other devices (as most research seems to come up with that, my use case seems rare) but this produces a problem.

When logged into terminal via ssh, the second I connect to the VPN (on VPS) I lose my terminal session and can't log in again via ssh user@nativeIP because it’s IP has changed and I have no idea what the new one is. If anyone has any ideas to get around this I would be extremely grateful! 

PS, I found a help page from another VPS company which appeared to understand the problem and gave a solution, three commands:

[I]iptables -A OUTPUT -t mangle -p tcp -m tcp --sport 22 -j MARK --set-xmark 3
ip rule add fwmark 3 table 3
ip r a default via 169.254.0.1 dev eth0 table 3[/I]
I tried this and no change sadly. I also tried using the VPN provider's CLI commands to split-tunnel a specific process (sshd in my case) to try not to get kicked out when i connect the VPN. But even that won't work because i still get kicked out, and when I restart ssh, it's on a new process ID of course! I am really stumped!

---

### Post by The Cog on 2021-02-06
Welcome to the forum.
```
iptables -A OUTPUT -t mangle -p tcp -m tcp --sport 22 -j MARK --set-xmark 3
ip rule add fwmark 3 table 3
ip r a default via 169.254.0.1 dev eth0 table 3
```
What the above is doing is this: 
1: Adding a firewall rule that marks outgoing packets from the ssh service (port 22) wtih a firewall mark (number 3, this is an arbitrary number)
2: Adding a rule that says packets so marked should use routing table number 3 instead of the default routing table
3: Adding a default route to routing table 3, forwarding to 169.254.0.1. You must the normal default route gateway address here.
The idea is that this prevents the ssh server from suddenly going over the VPN when it is brought up.
This command will tell you what the default route (without the VPN) is, giving you the address to use in table 3:
```
ip route list default
```
But you say you have changed the ssh port. If so, you need to change that first line to mark whichever port your ssh is now using. I am guessing that this is your problem. 
If you still have problems, I think we need to see the output from these commands (while the VPN is up), and also to know what port your ssh server is really on:
```
ip route
ip rule
iptables-save  # this prints the rules, not save them
```

Another possibility is that you are using IPv6 not IPv4, which would need similar rules in ip6tables (this post only mentions IPv4). Let us know if this is the case.

---

### Post by 42pjcqyy on 2021-02-06
What a fantastic reply, thank you. 
Thanks for explaining what the code was doing, I didn't have a clue! 

The port number isn't the problem. That's the only thing I am sure of at this point, actually no, also it's not an ipv6 issue I don't think. I set the VPN to use OVPN, not Wireguard which was producing IPV6 address issues before. I changed the port number and understand that part, I also set up a port forward with the VPN provider, so I thought that would be enough but obviously not. I have reinstalled fresh Ubuntu 20.04 so I am back to scratch with root, ssh on default port 22 etc, will do all the securing stuff later once I know no more reinstalls are needed!

I also finally managed to find a thread online which addresses it, on StackOverflow. Everyone seems to have good experience with this solution:

```
ip rule add from $(ip route get 1 | grep -Po '(?<=src )(\S+)') table 128

ip route add table 128 to $(ip route get 1 | grep -Po '(?<=src )(\S+)')/32 dev $(ip -4 route ls | grep default | grep -Po '(?<=dev )(\S+)')

ip route add table 128 default via $(ip -4 route ls | grep default | grep -Po '(?<=via )(\S+)')
```

Sadly it made no difference for me, I just installed VPN, connected, and kicked out as before. Back to your post:

I ran the command you suggested (ip route list default) which gave this response:

default via 169.254.0.1 dev ens3 proto static 

So am I right in thinking that I have all the info I need in that line above, combined with your commands, to fix this issue? 
Also am I right in thinking my default network interface/adapter is ens3 rather than the usual eth0?

thank you again, I feel finally like I might win!

---

### Post by 42pjcqyy on 2021-02-06
Just had a thought. 
I am using port 21786 for ssh purely because, when I first started investigating this a week ago nearly, mullvad support told me to forward my ssh port so I could get in via the external IP. It wasn't bad advice either, their support is great, but that was when I was looking for a 'hack'/trick to work out the external IP via the VPN to connect back into. Now I think I ruled out that being easily achievable for me, so I am now looking to use a proper rule on the server to forward traffic out of the native IP of the VPS and actually stop it going down the VPN tunnel. Just been thinking about this and it occurred to me, I probably want to get rid of that forwarded port don't I?!

---

### Post by 42pjcqyy on 2021-02-06
Nope that didn't help. Really stumped. I ran the three commands in the top post changing the info as needed, to no avail.

---

### Post by SeijiSensei on 2021-02-06
>  I am now looking to use a proper rule on the server to forward traffic out of the native IP of the VPS and actually stop it going down the VPN tunnel. 
You can do this with routing rules. First let's suppose the VPN tunnel has addresses 10.0.0.1 on the server end and 10.0.0.2 on the client end. Also let's suppose you have a local network with addresses in the range 192.168.0.0-255. Typically that's represented as 192.168.0.0/24, the "24" meaning that the first 24 bits of the address define the subnet you're using.  Then on the server you would add this route:
```

sudo ip route add 192.168.0.0/24 via 10.0.0.2

```
(Presumably the VPN software would set up the addresses on either end of the tunnel.)

Now the server will send traffic intended for the local network over the VPN, but send all other traffic out the main public address.

---

### Post by 42pjcqyy on 2021-02-06
Really sorry, I just don't understand much of your message. That's my failing not yours of course.

I was told my subnet should end /32 (i dont know what this means, just had that said to me by someone who tried to help but didn't know much more than me so couldn't really help in the end)

I have no idea what the IP of the VPN would be, the minute i connect I get booted out.

---

### Post by 42pjcqyy on 2021-02-06
After login i see this info
[[IMG]https://i.ibb.co/XWvb8sB/Screenshot-2021-02-06-at-19-15-07.png[/IMG]]("https://imgbb.com/")
Why are there 2 diffeent IP4 addesses? They are identical except for the first bits (89 and 10)

---

### Post by 42pjcqyy on 2021-02-06
And this is output from route command

[[img]https://i.ibb.co/6gNw4x0/Screenshot-2021-02-06-at-19-20-40.png[/img]](https://imgbb.com/)

---

### Post by SeijiSensei on 2021-02-06
I'm puzzled. Do you have a VPN that links the remote server with a local machine?  If not, what is the VPN supposed to do?

---

### Post by 42pjcqyy on 2021-02-07
Yes many get puzzled by that. 

I want to use VPS as a virtual machine for research. I want all OUTBOUND traffic from that VPS (just like i do with my home computer) to be routed and encrypted via use of a third party VPN service, just like millions do with their phone/computer. I install the VPN app on the ubuntu VPS box, but once connected, I can't ssh into it again as its public IP obviously changes. I need to either prevent my ssh connection going over the VPN, or find a trick to find out the external IP address of a VPS I can no longer log into! (so that I can!)

---

