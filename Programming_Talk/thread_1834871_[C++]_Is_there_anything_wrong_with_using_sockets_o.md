---
title: "[C++] Is there anything wrong with using sockets on port 80?"
date: 2011-08-28
forum: Programming Talk
---

### Post by ki4jgt on 2011-08-28
I've read everywhere all over the web that different ports have been reserved for different connection types. Is there anything wrong with using a different protocol than http for port 80? Yes, the protocol does connect and disconnect it doesn't stay solid. Will the firewall block it? Thanks for all your answers guys. :-)

---

### Post by Bachstelze on 2011-08-28
There's nothing inherently wrong about using another service on port 80, at worst you will confuse some users. Also whether a firewall will block it depends on its configuration.

---

### Post by karlson on 2011-08-28
> **ki4jgt said:**
> I've read everywhere all over the web that different ports have been reserved for different connection types. Is there anything wrong with using a different protocol than http for port 80? Yes, the protocol does connect and disconnect it doesn't stay solid. Will the firewall block it? Thanks for all your answers guys. :-)

There is nothing wrong with using port 80 as a listener I just have to wonder why is it that you want to do this if it is not http protocol?

---

### Post by ki4jgt on 2011-08-29
> **karlson said:**
> There is nothing wrong with using port 80 as a listener I just have to wonder why is it that you want to do this if it is not http protocol?

I would assume that most computers are more open on port 80 than other ports. Just checking if it would cause any probs with browsing the internet, like congestion or something.

---

### Post by nvteighen on 2011-08-29
> **ki4jgt said:**
> I would assume that most computers are more open on port 80 than other ports.

That's exactly the reason why you shouldn't: if I were a sysadmin and find out that something is connecting to a server's port 80 but isn't http, I'd immediately take precautionary actions. Think about this from the client's perspective: what if that server on port 80 is harmful, exactly because firewalls are usually permissive about that port? Also think about the ISP: what if they detect that non-http data going to some port 80? If I were in charge, I'd cut off the connection.

IMO, it's much more senseful to place a new port dedicated for that. Ok, the user will have to reconfigure his firewall... but isn't the firewall there exactly for that: prevent your computer to engage in unknown transactions with an untrusted server (or become a server for untrusted clients)?

In summary, technically, there's no issue in using port 80 (save that root privileges are needed to bind a socket to that port). But I would avoid that for "social" reasons.

---

### Post by ki4jgt on 2011-08-29
> **nvteighen said:**
> That's exactly the reason why you shouldn't: if I were a sysadmin and find out that something is connecting to a server's port 80 but isn't http, I'd immediately take precautionary actions. Think about this from the client's perspective: what if that server on port 80 is harmful, exactly because firewalls are usually permissive about that port? Also think about the ISP: what if they detect that non-http data going to some port 80? If I were in charge, I'd cut off the connection.

IMO, it's much more senseful to place a new port dedicated for that. Ok, the user will have to reconfigure his firewall... but isn't the firewall there exactly for that: prevent your computer to engage in unknown transactions with an untrusted server (or become a server for untrusted clients)?

In summary, technically, there's no issue in using port 80 (save that root privileges are needed to bind a socket to that port). But I would avoid that for "social" reasons.

The problem with this is the program I'm building actually MUST bypass firewalls :-( That was the only thing I could think of which would do it.

---

### Post by nvteighen on 2011-08-29
> **ki4jgt said:**
> The problem with this is the program I'm building actually MUST bypass firewalls :-( That was the only thing I could think of which would do it.

!?

---

### Post by ki4jgt on 2011-08-29
> **nvteighen said:**
> !?

Port 80 being all permissive and all. I thought that maybe if I used it, it would allow my users to bypass the security placed on other ports. My program MUST be able to bypass the security setting imposed by most/if not ALL firewalls. :-( I'm reading Tor documentation and how they do it currently. I'm also reading a lot of I2P documentation to see about their network connections. I initially wanted to put all communications through port 80. Then I wanted to listen on port 80 and connect on other ports (since most outbound connections aren't blocked) but now, I'm not so sure what to do. :-(

---

### Post by ofnuts on 2011-08-29
> **ki4jgt said:**
> The problem with this is the program I'm building actually MUST bypass firewalls :-( That was the only thing I could think of which would do it.Don't assume that, on the average PC, you can bypass the firewall by using port 80. If the firewall config is halfway decent, the inbound connections to port 80 are likely forbidden... unless the PC is know to have a HTTP server which case port 80 would already be taken. Outbound filtering of random port numbers is much less likely. If you want to interconnect two computer despite firewalls or HTTP proxies, use a VPN.

---

### Post by Longinus00 on 2011-08-29
> **ki4jgt said:**
> Port 80 being all permissive and all. I thought that maybe if I used it, it would allow my users to bypass the security placed on other ports. My program MUST be able to bypass the security setting imposed by most/if not ALL firewalls. :-( I'm reading Tor documentation and how they do it currently. I'm also reading a lot of I2P documentation to see about their network connections. I initially wanted to put all communications through port 80. Then I wanted to listen on port 80 and connect on other ports (since most outbound connections aren't blocked) but now, I'm not so sure what to do. :-(

Considering most people are behind a NAT or firewall, listening on port 80 is going to be just as useless as listening on any other port. Outbound connections on ports other than 80 aren't usually blocked, try seeing what ports your browser opens when connecting to other sites. You might want to do a bit more studying before you go down this road.

---

### Post by karlson on 2011-08-29
> **ki4jgt said:**
> Port 80 being all permissive and all. I thought that maybe if I used it, it would allow my users to bypass the security placed on other ports. My program MUST be able to bypass the security setting imposed by most/if not ALL firewalls. :-( I'm reading Tor documentation and how they do it currently. I'm also reading a lot of I2P documentation to see about their network connections. I initially wanted to put all communications through port 80. Then I wanted to listen on port 80 and connect on other ports (since most outbound connections aren't blocked) but now, I'm not so sure what to do. :-(

Based on this post allow me to describe what a decent system administrator would do when you attempt to do this in a corporate environment.

1.  Come and yell at you for being an .....
2.  Go to you manager and yell at him for hiring an .....
3.  Take away all your writes to deploy anything on the system.
4.  Set up a keystroke log for your account.

a good system administrator might simply get you fired add legal actions of your favorite choice to the mix on top of making it a requirement for all people that all externally facing servers are now sitting in the DMZ.

If you want to bypass all security put the machine outside the firewall and be done with it.

---

### Post by nvteighen on 2011-08-29
If you were part of a resistance movement against some dictatorship that has violated basic human rights in your country and you were developing some software that might help your movement to succeed in restoring justice and peace by breaking state-censorship measures, I'd endorse this.

But in the Western world, if you want to break a firewall, it's either because you want to get into a network or out from one without being noticed. Unless the only firewall involved is yours, this is going to put you in trouble... and even it's your own firewall, your ISP might not like to see you using port 80 at all (even for a HTTP server... most ISPs prohibit home users to set up a HTTP server, for bandwidth reasons).

Also, be aware that breaking a correctly configured netfilter/iptables is quite hard, because it's deeply buried in the lower levels of Linux. And simple tools like UFW or Firestarter make configuring netfilter/iptables quite easy for everyone.

---

### Post by ki4jgt on 2011-08-29
> **nvteighen said:**
> If you were part of a resistance movement against some dictatorship that has violated basic human rights in your country and you were developing some software that might help your movement to succeed in restoring justice and peace by breaking state-censorship measures, I'd endorse this.

But in the Western world, if you want to break a firewall, it's either because you want to get into a network or out from one without being noticed. Unless the only firewall involved is yours, this is going to put you in trouble... and even it's your own firewall, your ISP might not like to see you using port 80 at all (even for a HTTP server... most ISPs prohibit home users to set up a HTTP server, for bandwidth reasons).

Also, be aware that breaking a correctly configured netfilter/iptables is quite hard, because it's deeply buried in the lower levels of Linux. And simple tools like UFW or Firestarter make configuring netfilter/iptables quite easy for everyone.

Here's my thing:
I'm creating a relatively LOW bandwidth VOIP program. It's goals are to be unblockable, untraceable, uninterceptable, undecipherable. Each user get's their own 10 character (of their own choosing) alphanumeric phone number/username. That's why I'm looking into Tor, Freenet, I2P, and several others. I am combining several of their protocol methods. I already have a good 90% of the protocol worked out and have started to learn C++ for it's speed. I am going to license the software to commercial businesses for $10 USD so that if there's ever a security issue that I can't take care of, I can hire a third party developer. All in all the license wouldn't and couldn't be forced to be mandatory (except where law in concerned) it would just be a trust thing, as implementing such a system would pose a security risk in and of itself.

This is what's been up with the rash of programming questions I have posed here lately. Basically it's a fully secured telephony and even though I have protocol written. Writing and programming are two different animals. :-( But yes, the service is low bandwidth and even if your communications were ever deciphered, the user who managed to do it would have so little of your conversation, that they could not even begin to put it together.

---

### Post by karlson on 2011-08-29
> **ki4jgt said:**
> 
Basically it's a fully secured telephony and even though I have protocol written. 


There is no such thing.  The fact that you don't know how to break it doesn't mean it's fully secured.

> Writing and programming are two different animals. :-( But yes, the service is low bandwidth and even if your communications were ever deciphered, the user who managed to do it would have so little of your conversation, that they could not even begin to put it together.

If you want to decode it in real time may be.  But one can simply sniff the packets on the network and recreate the conversation from the recorded data.

One thing that I still fail to see is what does it have to do with port 80?  You just don't want to go through hoops to open another port on someone else's firewall while you develop your product?

---

### Post by ki4jgt on 2011-08-29
> **karlson said:**
> There is no such thing.  The fact that you don't know how to break it doesn't mean it's fully secured.



If you want to decode it in real time may be.  But one can simply sniff the packets on the network and recreate the conversation from the recorded data.

One thing that I still fail to see is what does it have to do with port 80?  You just don't want to go through hoops to open another port on someone else's firewall while you develop your product?

I do know how to break it down. That's why I've written the protocol. Recreating the conversation isn't that easy. There are safety features put in place to avoid that. Next, it's not absolutely secure. I mean if someone owns a major network share then YES, they can trace you, but they can't intercept your conversations or decipher them (unless they pull all those computer's resources together, safety features put in place prevent it.)

It has nothing to do with port 80 per se. It could be any port. I just assumed port 80 would be more open. Basically, I'm looking for the best way to bypass the firewall so the software may gain access to the network (Like Tor) There are a few online (someone else phrased it as chicken or egg scenarios) but they all end up failing at one place or another that I try them. I was wondering how Tor is able to pull it off. I can't really find any documentation on it as much as I2P and Freenet and others.

---

### Post by Bachstelze on 2011-08-29
You seem very confident about your "safety features". How cute. :)

Neither your protocol nor your code is secure. If you had even half the knowledge it takes to build secure software, you wouldn't be asking questions here.

---

### Post by karlson on 2011-08-29
> **ki4jgt said:**
> I do know how to break it down. That's why I've written the protocol.

I meant your own protocol.

> Recreating the conversation isn't that easy. There are safety features put in place to avoid that. Next, it's not absolutely secure. I mean if someone owns a major network share then YES, they can trace you, but they can't intercept your conversations or decipher them (unless they pull all those computer's resources together, safety features put in place prevent it.)


Like parents for kids?  I mean what's your target market?

> 
It has nothing to do with port 80 per se. It could be any port. I just assumed port 80 would be more open. Basically, I'm looking for the best way to bypass the firewall so the software may gain access to the network (Like Tor) There are a few online (someone else phrased it as chicken or egg scenarios) but they all end up failing at one place or another that I try them. I was wondering how Tor is able to pull it off. I can't really find any documentation on it as much as I2P and Freenet and others.

If you need to have a port open set up your own rather then using a well known port that people that use web servers leave open.  As I said before decent SA's and security people periodically run sweeps of well known open ports and if you are running in such network you will be found.

If you want to learn about Tor I suggest you download the code and read it.

---

### Post by ki4jgt on 2011-08-29
> **Bachstelze said:**
> You seem very confident about your "safety features". How cute. :)

Neither your protocol nor your code is secure. If you had even half the knowledge it takes to build secure software, you wouldn't be asking questions here.

And that is why I was reluctant to tell my idea. Too many people on the Internet are psychic. If you'll notice, I just posed a question. Then was told that I could not get help because they didn't know what I was using the question for. I in turn told why I wanted to use this information. Now you've psychically divined that I'm going to fail before I've even started. (have the protocol written not the code) Thanks for your input.

> Neither your protocol nor your code is secure. If you had even half the knowledge it takes to build secure software, you wouldn't be asking questions here.

Perhaps I'm asking questions here b/c I need a starting place. Perhaps I didn't know what people around here were into. So, instead of standing over my shoulder and telling me I'm going to fail before I even get started, why not do what you would have done to you and either help me or stop trying to put me down. It's a project, nothing more. So what if I make something as secure as I've stated. It's no skin off your back. So what if I don't. It's no skin off your back.
I'm not throwing a fit either, for some reason people read too much into what I say and end up telling me I said this and I said that. All I'm simply saying is, I don't stand over your shoulder and tell you you're going to fail at your projects do I? Please be supportive of mine. and Yes, I am pretty confident in my security measures. Without confidence, life would be worthless. Computer programs are simply a representation of real world objects. It doesn't take years of computer training to manipulate the real world. It just takes years to learn how to program that manipulation into the computer. My program isn't flawless, but it's not a failure. You're also correct, I don't know much about security. That's why I'm asking around. What I used to know, was human thinking. Somewhere along the line people kept telling me to just give up and I no longer cared. I'm actually starting to learn about society and the way people work again. If I can manipulate people, then machines shouldn't be that hard to figure out. Thanks for your suggestion to look elsewhere though. It's duly noted.

---

### Post by PaulM1985 on 2011-08-29
Is the software you are using designed to be client or server side?  I mean, what is your user going to run, client or server, or both?

I recently spent a bit of time looking into this area to make a sort of GoToMyPc type program.

I found that if you are going to have the users running the servers, they are likely to be behind routers, in which case they are going to have to set up port forwarding, so your choice of port would be better to be something that isn't used by other stuff.  Otherwise, if they are running the client and connecting to your server, most ports seemed to work ok for my software (but maybe I was lucky).

I would try to steer clear from using 80 since that in my eyes is for http.  Good luck.

Paul

---

### Post by karlson on 2011-08-29
> **ki4jgt said:**
> and Yes, I am pretty confident in my security measures. Without confidence, life would be worthless.


Forgive my saying so but from your posts you are confident that you can do no wrong rather then you are confident that you can do what you have intended to do.

> Computer programs are simply a representation of real world objects. It doesn't take years of computer training to manipulate the real world. It just takes years to learn how to program that manipulation into the computer. My program isn't flawless, but it's not a failure. You're also correct, I don't know much about security.

Then how can you claim that your protocol is "fully secure"?

> That's why I'm asking around. What I used to know, was human thinking. Somewhere along the line people kept telling me to just give up and I no longer cared.


Noone is telling you to give up.  People here are telling you don't make marketing claims of "fully secure" in the technical forums.

If you have found a way to write fully correct software that implements your protocol without any security problems I think you should publish a paper on that because so far noone to my knowledge have been able to solve that problem.

If you think that your protocol is more secure than anything else out there and you think that there is a market for it then by all means go forth.

---

### Post by ofnuts on 2011-08-29
> **ki4jgt said:**
> Here's my thing:
I'm creating a relatively LOW bandwidth VOIP program. It's goals are to be unblockable, untraceable, uninterceptable, undecipherable. Each user get's their own 10 character (of their own choosing) alphanumeric phone number/username. That's why I'm looking into Tor, Freenet, I2P, and several others. I am combining several of their protocol methods. I already have a good 90% of the protocol worked out and have started to learn C++ for it's speed.

It remains that normally, you can't connect to any port of the average end-user PC on the Internet. Either the PC is behind a corporate firewall, or it is behind a home (or small business) router. There shouldn't be that many end-users PCs still connected directly to the intenet, and those that are are either buttoned up with a military-grade firewall or laden with malware and blacklisted on every router on the planet. So your connection isn't going to happen without explicitly relaxing some rules, and you can't really count on the corporate admins to do so.

---

