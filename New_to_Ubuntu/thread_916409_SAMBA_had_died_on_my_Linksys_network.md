---
title: "SAMBA had died on my Linksys network"
date: 2008-09-10
forum: New to Ubuntu
---

### Post by pi.boy.travis on 2008-09-10
Hi.  A problem that I previously thought to be a printer problem (other thread) is in fact a SAMBA problem.  My laptop can't see my desktop's shared files.  In fact, If I select "Network" from the places menu on the desktop, it can't even see it's own shared files!  I can connect to the offending computer using Remote Desktop, and even Rythmbox. SAMBA shares are the only ones malfunctioning.  I have reset my Linksys router several times, and I don't suspect this to be the problem.  Any ideas?  If you need any stats, just say so.

Thanks in advance!

---

### Post by Zzl1xndd on 2008-09-10
By chance are you using Firestarter on the laptop? I have the same issue if I don't stop the firewall.

---

### Post by pi.boy.travis on 2008-09-10
> **tweakedenigma said:**
> By chance are you using Firestarter on the laptop? I have the same issue if I don't stop the firewall.

Thanks for your reply.  No, my local network is behind a hardware firewall, and I use ufw only if I'm on a public network.

---

### Post by Zzl1xndd on 2008-09-10
Ah, I havn't used UFW, but my understanding is it works like Firestarter in that it alters IPtables. Not sure if its the same but even if Firestater isn't running IPtables is still using the Firestarter settings unless it is told to stop. 


and are you able to ping the machine on ports 137-139 as those are the ports Samba uses.

---

### Post by pi.boy.travis on 2008-09-11
OK, I have never used the ping command before, and here is what I got:

```
travis@travis-laptop:~$ ping
Usage: ping [-LRUbdfnqrvVaA] [-c count] [-i interval] [-w deadline]
            [-p pattern] [-s packetsize] [-t ttl] [-I interface or address]
            [-M mtu discovery hint] [-S sndbuf]
            [ -T timestamp option ] [ -Q tos ] [hop1 ...] destination
travis@travis-laptop:~$ ping 137
connect: Invalid argument
travis@travis-laptop:~$ ping -I 192.168.1.104 137
PING 137 (0.0.0.137) from 192.168.1.104 : 56(84) bytes of data.
ping: sendmsg: Invalid argument
ping: sendmsg: Invalid argument
ping: sendmsg: Invalid argument
ping: sendmsg: Invalid argument
ping: sendmsg: Invalid argument
ping: sendmsg: Invalid argument
ping: sendmsg: Invalid argument
ping: sendmsg: Invalid argument
ping: sendmsg: Invalid argument
ping: sendmsg: Invalid argument
ping: sendmsg: Invalid argument
ping: sendmsg: Invalid argument
ping: sendmsg: Invalid argument
ping: sendmsg: Invalid argument
ping: sendmsg: Invalid argument
ping: sendmsg: Invalid argument

```

What am I doing wrong?

None of my computers are running a firewall right now, so I would assume that if shares exist, the port would be open, correct?

Thanks!

---

### Post by Zzl1xndd on 2008-09-11
sorry I was having a stupid moment last night, what I should have said is can you ping the machine and if so go to your network tools and do a port scan.

---

### Post by pi.boy.travis on 2008-09-11
OK, the ports you specified didn't show up.  I know the shares are active.  What can I do?

Thanks!

---

### Post by Zzl1xndd on 2008-09-11
I suspect something is still blocking that port can you use 

```
sudo ufw status
```

and post the out put.

---

### Post by halitech on 2008-09-11
can you open Nautilus, change it so you can type in an address and type in the address to the share? 
```
smb://192.168.1.104/sharename
```

---

### Post by pi.boy.travis on 2008-09-11
Duh. . . I must have forgot to turn the firewall off when I had to connect my laptop directly to my modem.  Thanks for helping me realize my stupid mistake!

"The computer is always right.  It is the user that has made the error"

---

### Post by EarloftheWest on 2008-09-11
pi.boy.travis.
My network exhibits the same behavior.

I can access my windows computers using the ip address assigned by my router, but I can't see the windows shares when I use Network in Nautalis.

I expect it to act like windows would when I access a shared computer but it doesn't. 

I looked for a solution several months ago but couldn't find one. Please post if you find anything.

---

### Post by Zzl1xndd on 2008-09-11
No Problem pi.boy, It took me a while to figure out why my laptop wouldn't display them either.

---

### Post by pi.boy.travis on 2008-09-12
> **EarloftheWest said:**
> pi.boy.travis.
My network exhibits the same behavior.

I can access my windows computers using the ip address assigned by my router, but I can't see the windows shares when I use Network in Nautalis.

I expect it to act like windows would when I access a shared computer but it doesn't. 

I looked for a solution several months ago but couldn't find one. Please post if you find anything.

I usually look to the hardware first when I have a network issue.  Try this:

-Shut down all computers involved

-Unplug all network equipment

-Assuming you only have one router, plug it in, and reset it to factory settings.  There should be a button somewhere.  Check your manual.

-After the router has initialized, hook your modem up to the router first, then plug that back in.

-The internet light on your router should now be on

-Power up your computers, and configure your router if you absolutely need to.  When trouble shooting, preferably you would use factory settings.

If all is still not well, go to software.

-Go to Places-Network (or the windows equivalent) on the computer that has the shared files.  Can you see them there?  If so, the problem probably isn't with this machine (but knowing windows, it could be)

-Next, you will need to disable any and all software firewalls.  If your router has a built in hardware firewall, great.  You don't need a software firewall anyway.  If not, you should unplug the modem from the router to protect your network.  If you are using ufw, run: 

```
sudo ufw disable
```

-If it still isn't working, post with more info about your network, and we can help you fix the problem.

Hope this helps!

---

