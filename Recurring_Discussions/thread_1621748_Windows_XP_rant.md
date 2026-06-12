---
title: "Windows XP rant"
date: 2010-11-14
forum: Recurring Discussions
---

### Post by Mr Bean on 2010-11-14
I guess this will just be a rant unless anyone can help me but I have to vent. 

I have two machines running XP Pro SP3, A client and a server. Basically just a bog standard windows share on one that I access from the other. Recently though, it became inaccessible on the client. It gives the error "Local Device Name Is Already In Use"or simply crashes explorer. Or both. This problem started seemingly without any hardware of software changes. And it seems to persist somehow even though I have:

a. installed an entirely new and separate instance of windows on the client.
b. booted into an alternate instance of windows on the server (i have one for troubleshooting) 
c. changed the computer name on the client
d. changed the share name on the server
e. deleted and recreated the clients account on the server
f. changed the IP address of the client (they can both ping each other fine but hey I'm clutching at straws)
g. cleaned heatsinks and reset BIOS on both machines. 

The only things I haven't tried yet are prayer and voodoo. 

Both machines can access the internet okay, but I can only logically conclude that they have recently fallen out and now they hate eachother at the hardware level. It does not seem to matter what installation of Windows or what accounts I use... I just cant get them to share files anymore.

Curiously though, an Ubuntu live session on the client can access the files on the server, as can every other PC on the network. And the server can certainly access its own files okay

This problem doesn't make sense. How can the hardware be fine, but two entirely separate installations of Windows (from different installation media) on that hardware BOTH exhibit an identical problem. Ditto the server. 

The onset of this problem was combined with the onset of another problem: the server will randomly hang about once a day. Only responds to a hard reset. Again, there is no logical reason for this problem either. 

I should also add that my Ubuntu machine can VNC the server but when I  VNC the server from the dodgy client all I get is a black screen. So that's a completely different protocol that is also selectively broken on one client. Didn't change any firewall settings recently or anything. It makes noooooo sense. 

It's driving me completely nuts.

---

### Post by arvevans on 2010-11-14
Others may have a better idea of what your problem is, but here are some things to think about and possibly look at:
[LIST]
[*]Do you have the server firewalled, and is it blocking a specific hardware address?
[*]Does the server have "allow" and/or "deny" limitations that may be blocking specific  connections?
[*]Net-Bios networking might be using the MAC address for filtering or for connections.
[*]Does you client have "allow" or "deny" settings that might be blocking access to the server?
[*]Is there a port-mapper number problem with which port is being watched or used by which machine for specific applications?
[*]Maybe...once the server has tasted a Linux system it has decided to not talk to a plain old Windows box?     :) .
[/LIST]

OK...I have made my guesses.
Good Luck.

---

### Post by Mr Bean on 2010-11-15
Thank you for the suggestions. I thought you were onto something with netBIOS but sadly not. New developments:

a. the ethernet port (built into the mobo) became inaccessible to Windows. Wasn't in the hardware list. Wasn't lighting up on the back or causing the gigabit switch to light up the port it was connected to. It seemed dead. I booted into Ubuntu live and got the same thing. Dead. Then, a few reboots later, it was working again. (or at least, it was showing up as a hardware device and connecting to the network) 

b. I have tried a few more times to use VNC to connect to the server from the client. It still doesnt work in Windows or Ubuntu live. And, it still doesn't work if I disconnect the wired network and use a wireless adaptor instead. So it can't be a problem with the onboard ethernet, or the wireless adaptor would have worked. 

So we have:

A vague hardware problem effecting all NICs. But leaving the rest of the system relatively stable. 

My only thoughts now are to replace the mobo. If I can get the manufacturer (Asus) to swap it. 

I will run memtest in the meantime. Maybe it is a memory error, though I don't think that would interfere with networking specifically.

It really does make no sense.

---

### Post by Hakunka-Matata on 2010-11-15
Please excuse this *simple* suggestion/question.  Could it be a ethernet cable hardware problem, switch ethernet connector problem?  If it's a hardware problem, then as the saying goes "it's usually something simple"... unless it isn't???

Good Luck

---

### Post by Mr Bean on 2010-11-15
I wish. I have tried the following configurations now.

"Original" cable to gigabit switch, then to different port on gigabit switch, then to router. 
Potentially dodgy cable to switch 
definitely working spare cable to router. 

In every case they show as connected but wont access the server.

And the switch is working fine as I am connected to it and I can access the server which is also connected to it. (I can access both VNC and the windows shares). 

Some other curiosities I have discovered:

I went into the advanced configs for the ethernet cards and changed "checksum offload" to disabled on both systems. Now the client can VNC to the server but the server just sends back a black screen. Before it was saying "timed out" or similar. i.e. it couldn't connect at all.

I know I already mentioned the black screen problem. But I evidently changed a few settings since then that made things marginally worse. 


But anyway, I think I can safely say the cables work. There is hope that it's a configuration issue... but I didn't change anything to cause the problem. I have been changing almost everything since the problem started and nothing helps.

---

### Post by Mr Bean on 2010-11-15
And anyway, I said that I tried wireless. 

And I am absolutely 100% sure that the server is configured to allow ALL LAN clients through. And have tried the client on two IP addresses. (probably 3 taking wireless into consideration)

PS. memtest came back clean. 

At this point I'm thinking that I will just replace the server with a NAS box and hope that the client gets on with that a little better.

I have just verified that the client can connect to and use a share hosted by a WinXP virtual machine on my computer. so it can connect to shares. Dont want to waste time and money setting up a NAS if it wont connect to that either. Since I was planning to migrate to a NAS in the near future anyway, I guess I might as well do it now and see if it helps.

---

