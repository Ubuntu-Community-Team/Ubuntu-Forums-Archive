---
title: "[SOLVED] Setting a WEP key on Ubuntu"
date: 2008-08-18
forum: New to Ubuntu
---

### Post by Spades_Neil on 2008-08-18
Problem solved, but the thread remains here for anyone else who may need it unless a mod decides to delete it.

-------------------------------------

Very simple question, how do I make a WEP key for a wireless router through Ubuntu?

I have a wireless router sitting next to me right now, and used to have one hooked up all the time. Only recently have I been forced to plug it back in.

I want to know how to lock people out of it who do not have the password. SOMEBODY on my street has been hacking my old Linksys network. -.-; Files popping out of no where hit my old computer and messed it up with a virus apparently because they were in the same network and I was receiving these files. I'm not even sure this person realized what was happening anyways.

Still, moving on, having an open router also kills off my bandwidth. I wanna be able to play Xbox! D:

So, anyways, how do I set up a WEP key on my router? Is it different for different routers? Mine is a Belkin router.

(Also, please explain to me this as if you're writing the book, "Linux WEP Key, *For Dummies!*" :P I'm not very good at tech talk, but I somehow know my way around computers well.)

By the way, if there's also a post already put up about this, I'm afraid I couldn't find it. T_T I'm a noob at these forums. >_<

---

### Post by tuxxy on 2008-08-18
Load into the routers manager, here you should be able to enable WEP encryption, although if you say your network has already been breached then WEP may only delay them from breaking in again.  

Attackers can gain access to WEP keys quite easily all they need is the correct toolkit, I use WPA/WPA2 and would advise this over WEP.

---

### Post by nicedude on 2008-08-18
WEP is better than nothing but can not protect you against a skiled cracker ( or even a script kiddie ). I can crack a 128bit WEP key in less than 5 minutes and then be on your network etc. Now all that said the best way if you want to have WEP is to also use MAC address filtering in your routers setup and only program in the mac for your wifi PC or XBOX, that will make it to where the router won't comunicate with any device except the ones on that list. Problem 2 -> I can just spoof my MAC and become your XBOX as far as your router is concerned and then hack its WEP in 5 minutes once again, only downfall is I have to see your devices communication in operation to know its MAC in order to spoof it. Now your little neighborhood hacker wannabe might not be able to spoof his MAC if he is not bright and using windows etc. but I don't know how good he is or what software & equipment he uses. If he was just using your open Wifi before then that is not even a hacker that is someone using your open door :-) 

Also make sure you set your routers password ( the one to log into the router ) to something very secure as at least that will keep anyone from changing your router settings and having full control. Using Ubuntu he will not be able to hack your machine if he gets connected to your network nor give you any Viruses as they don't work. In fact it would be much easier to set him up with a nice un passworded share directory with a Zero day Windows virus infected file in it that sounds like a awesome warez file :-) but nonetheless he will be powerless against Ubuntu and I don't think he will hack into your XBOX either so you should be safe anyway.

WPA with a very strong passphrase is the only way I know of to secure your wifi VS a skilled attacker, but it doesn't work with all devices etc.


Try getting a directional antennae for your laptop and walking around the neighborhood and seeing exactly who it is, then just knock on his door and say you are logging his attacks and you have called the FBI and local police and see if he has the balls to keep it up.

Goodluck with your problem, I hope this info helps.

nicedude

---

### Post by Spades_Neil on 2008-08-18
> **tuxxy said:**
> Load into the routers manager, here you should be able to enable WEP encryption

Not sure how to get into the router manager. Mind explaining? *already clicking buttons*

> **tuxxy said:**
> although if you say your network has already been breached then WEP may only delay them from breaking in again.

Attackers can gain access to WEP keys quite easily all they need is the correct toolkit, I use WPA/WPA2 and would advise this over WEP.

Not that worried about 'attackers' since no one around here is really good at computers. I'm like the computer tech guy for my entire street. I really think the 'invasion' was my next door neighbor on his laptop, goofed up because he doesn't know what he's doing, and already has a virus clusterborked computer running Windows 2000. Windows computers like to search for open networks when their normal one doesn't work for some reason.

---

### Post by tuxxy on 2008-08-18
lol I see, ok to load your router manager you need to know its IP address, then type the address into your browsers address bar.

for example, [http://192.168.0.1](http://192.168.0.1)

---

### Post by Spades_Neil on 2008-08-18
> **nicedude said:**
> WEP is better than nothing but can not protect you against a skiled cracker ( or even a script kiddie ). I can crack a 128bit WEP key in less than 5 minutes and then be on your network etc. Now all that said the best way if you want to have WEP is to also use MAC address filtering in your routers setup and only program in the mac for your wifi PC or XBOX, that will make it to where the router won't comunicate with any device except the ones on that list. Problem 2 -> I can just spoof my MAC and become your XBOX as far as your router is concerned and then hack its WEP in 5 minutes once again, only downfall is I have to see your devices communication in operation to know its MAC in order to spoof it. Now your little neighborhood hacker wannabe might not be able to spoof his MAC if he is not bright and using windows etc. but I don't know how good he is or what software & equipment he uses. If he was just using your open Wifi before then that is not even a hacker that is someone using your open door :-) 

Also make sure you set your routers password ( the one to log into the router ) to something very secure as at least that will keep anyone from changing your router settings and having full control. Using Ubuntu he will not be able to hack your machine if he gets connected to your network nor give you any Viruses as they don't work. In fact it would be much easier to set him up with a nice un passworded share directory with a Zero day Windows virus infected file in it that sounds like a awesome warez file :-) but nonetheless he will be powerless against Ubuntu and I don't think he will hack into your XBOX either so you should be safe anyway.

WPA with a very strong passphrase is the only way I know of to secure your wifi VS a skilled attacker, but it doesn't work with all devices etc.


Try getting a directional antennae for your laptop and walking around the neighborhood and seeing exactly who it is, then just knock on his door and say you are logging his attacks and you have called the FBI and local police and see if he has the balls to keep it up.

Goodluck with your problem, I hope this info helps.

nicedude

Not too worried about the hardcore stuff. :P I know enough about computers to know that WEP is not the best out there, I just want something to keep annoying laptops and stuff from auto-connecting to my computer because they can't get internet elsewhere. I'm not worried about viruses anymore anyways.

Plus, the whole reason I even GOT Ubuntu was so my sister would stop breaking computers with her limewire viruses and junk. :P

---

### Post by Spades_Neil on 2008-08-18
> **tuxxy said:**
> lol I see, ok to load your router manager you need to know its IP address, then type the address into your browsers address bar.

for example, [http://192.168.1.1](http://192.168.1.1)

That I can try. I think I already know how to find my IP.

System -> Admin -> Network -> Hosts -> DNS

Correct?

---

### Post by tuxxy on 2008-08-18
> **Spades_Neil said:**
> That I can try. I think I already know how to find my IP.

System -> Admin -> Network -> Hosts -> localhost

Correct?

No not your IP, you want the **routers IP**, open a terminal and type this command

```
nslookup localhost
```

The address you want will be the first one dispalyed named as the **server** address, now type this address in your browser like  [http://192.168.0.1](http://192.168.0.1)

---

### Post by Spades_Neil on 2008-08-18
> **tuxxy said:**
> No not your IP, you want the **routers IP**, open a terminal and type this command

```
nslookup localhost
```

The address you want will be the first one dispalyed named as the **server** address, now type this address in your browser like  [http://192.168.0.1](http://192.168.0.1)

Ironically, I seem to have found the router IP anyways by mistake. ^^;

It brought me to my Belkin page though. I edited what I needed to, and now I have a simple password set into my router to block annoyances. Plus, if say my friends with a PDA or PSP perhaps comes over, they can log in with ease. If I ever have an issue... I'll just jump up the security from a simple word password to a cluster of random letters and numbers. XD

Thanks for the help. ^_^

---

### Post by nicedude on 2008-08-18
Hey tuxxy heres a simple tip, if you want to get to your router setup right away you can always just open a terminal and do the following

firefox-2 192.168.0.1 

and hit enter

I use Firefox 2 still so yours would prob be 3 or whatever. I just like using that as it just loads up the auth window right away and without having to enter it into browser bar & if instructing others I don't have to make sure they don't search for 192.168.0.1 in GOOGLE by mistake :-)

---

### Post by tuxxy on 2008-08-18
No problem neil, nicedude yes I understand thats why i showed him an example to make sure he has http:// at the start also I thought it would be more simple to use the browser than terminal, good tip :)

---

### Post by Spades_Neil on 2008-08-18
> **tuxxy said:**
> No problem neil, nicedude yes I understand thats why i showed him an example to make sure he has http:// at the start also I thought it would be more simple to use the browser than terminal, good tip :)

Yea, I've tried using the terminal before. Not too good with it. ^^;

But yea, the http:// method I was much more familiar with since I watched the Comcast guy do it for the modem more recently. Although, I also found out that day I'm not supposed to use two modems, so he made that one turn off. XD

Hence the reason I'm now using the router.

---

### Post by tuxxy on 2008-08-20
Good job, you can mark your thread as solved now then :)

---

