---
title: "ubuntu related help needed asap"
date: 2011-11-07
forum: New to Ubuntu
---

### Post by cherryw on 2011-11-07
hello guys,
I am a kind of newbie to ubuntu( in some aspects like  networking). And  what I wanna ask is about NOAUTH. I read on "ubuntu  help" that while  configuring a PPPOE connection we need to enable  NOAUTH. I just couldnt  figure out what it is? I mean I wanna know  exactly about it(meaning  and a lil bit of explanation). So guys pls help  me out. I even wanna  know about DEFAULTROUTE , NODETACH, PEER DNS,   LIMITED MSS PROBLEM. I  am really sorry if I am expecting too much from u  guys. But I would  definitely do something for u in return.
I posted this already but im posting this again because I didnt get even a single reply and Im feeling helpless. Any helpful guys out there please please please help me.

---

### Post by wildmanne39 on 2011-11-07
Hi, I do not have all the answers to your questions, but to make it simple most of the time network manager sets up your connection just fine and you should not make any manual adjustments unless you are running a server without a GUI.

So is this a ehternet connection? and is it working and what is your goal?

I am getting off for tonight it is late here and it has been a long day, I will check back tomorrow.
Thank you

---

### Post by cbowman57 on 2011-11-07
Nothing comes to mind but networking isn't my strong suit.

---

### Post by anewguy on 2011-11-07
You would be better off keeping a few things in mind:

(1) There is a networking forum within the ubuntu forums.  You might be better off posting there.

(2) An internet search engine is your best friend:  try a search using

ubuntu pppoe noauth

in the search string and do a lot of reading.

(3) Give your thread a meaningful title.  Saying you need related help doesn't mean squat in a forum already dedicated to ubuntu.  Saying you need it asap, then posting these types of questions instead of indeed an extremely urgent problem, will turn people off from giving you any answers.

(4) Read the ubuntu documentation.

---

### Post by papibe on 2011-11-07
Could you tell us a little bit more about your network?

Do you have a modem or a router? (both?)

Why do you need to setup a pppoe connection?

Regards.

---

### Post by cherryw on 2011-11-07
hi anewguy,
Yeah i posted it there but didnt get even a single reply and i really tried the 3 things u told me and finally i got here where i am right now and I really hope that someone would help me out.

---

### Post by cherryw on 2011-11-07
hi papibe,
I have a modem with broadband adsl and i need to setup a pppoe connection in order to make it work. I read this in the ubuntu community documentation.

---

### Post by wojox on 2011-11-07
You can open a terminal and 
```
man pppd
```

Or use this web page [Point-to-Point Protocol Daemon ]("http://linux.die.net/man/8/pppd")

---

### Post by cherryw on 2011-11-07
> **wojox said:**
> You can open a terminal and 
```
man pppd
```

Or use this web page [Point-to-Point Protocol Daemon ]("http://linux.die.net/man/8/pppd")
hi wojox,
I know how to set up a pppoe connection. I really wanna know what the terms mean exactly bcoz how can i enable something without knowing what it is? Hope u got it.

---

### Post by wojox on 2011-11-07
> **cherrywarrior said:**
> hi wojox,
I know how to set up a pppoe connection. I really wanna know what the terms mean exactly bcoz how can i enable something without knowing what it is? Hope u got it.

Go to the web pages and search for all your terms. They are in there. :p

---

### Post by cherryw on 2011-11-07
> **wojox said:**
> Go to the web pages and search for all your terms. They are in there. :p
what webpage do you mean? I already searched the whole ubuntu official website but was unable to find them.

---

### Post by wojox on 2011-11-07
> **cherrywarrior said:**
> what webpage do you mean? I already searched the whole ubuntu official website but was unable to find them.

[Point-to-Point Protocol Daemon ]("http://linux.die.net/man/8/pppd")

---

### Post by cherryw on 2011-11-07
Hey wojox,
I have trouble accessing that website and if you dont mind can you please copy and paste the definitions here. Ill be really grateful to you.

If you dont wanna copy and paste them atleast explain those terms in one line, Imma pretty fast learner. Thanks in advance.

---

### Post by dannyboy79 on 2011-11-07
> **cherrywarrior said:**
> hello guys,
I am a kind of newbie to ubuntu( in some aspects like  networking). And  what I wanna ask is about NOAUTH. I read on "ubuntu  help" that while  configuring a PPPOE connection we need to enable  NOAUTH. I just couldnt  figure out what it is? I mean I wanna know  exactly about it(meaning  and a lil bit of explanation). So guys pls help  me out. I even wanna  know about DEFAULTROUTE , NODETACH, PEER DNS,   LIMITED MSS PROBLEM. I  am really sorry if I am expecting too much from u  guys. But I would  definitely do something for u in return.
I posted this already but im posting this again because I didnt get even a single reply and Im feeling helpless. Any helpful guys out there please please please help me.
you can learn about all those terms if you view the man page for pppd, which is what the previous poster linked you to.

NOAUTH basically means that the peer will NOT be required to authenticate itself before allowing network packets to be sent or received

NODETACH is Don't detach from the controlling terminal.

All this is in the page he linked you to: [http://linux.die.net/man/8/pppd](http://linux.die.net/man/8/pppd)

EDIT: i see now you are saying you can't access that page, I have no idea why but you can also view each of these definitions by issuing > man pppd within a terminal window.

so unless you have a specific question I can't really help you anymore. Did you get your connection established and are able to surf the web?

---

### Post by cherryw on 2011-11-07
> **dannyboy79 said:**
> you can learn about all those terms if you view the man page for pppd, which is what the previous poster linked you to.

NOAUTH basically means that the peer will NOT be required to authenticate itself before allowing network packets to be sent or received

NODETACH is Don't detach from the controlling terminal.

All this is in the page he linked you to: [http://linux.die.net/man/8/pppd](http://linux.die.net/man/8/pppd)

EDIT: i see now you are saying you can't access that page, I have no idea why but you can also view each of these definitions by issuing  within a terminal window.

so unless you have a specific question I can't really help you anymore. Did you get your connection established and are able to surf the web?
Ok thanks but what do you mean by a peer in ur answer exactly and generally do all computers have NOAUTH enabled or is it unsafe?

---

### Post by dannyboy79 on 2011-11-07
> **cherrywarrior said:**
> Ok thanks but what do you mean by a peer in ur answer exactly and generally do all computers have NOAUTH enabled or is it unsafe?
the peer means the computer which you're trying to connect to (your ISP) so that you can have an internet connection. (i think, lol)

Here's a great link to some common ppp issues. [http://ppp.samba.org/FAQ.html](http://ppp.samba.org/FAQ.html)

I took this snipit in case you can't access that webpage.

> You can add the `noauth' option to the /etc/ppp/options file. Pppd will then not ask the peer to authenticate itself. If you do this, I *strongly* recommend that you remove the set-uid bit from the permissions on the pppd executable, with a command like this:

	chmod u-s /usr/sbin/pppd

Then, an intruder could only use pppd maliciously if they had already become root, in which case they couldn't do any more damage using pppd than they could anyway. 

---

### Post by cherryw on 2011-11-07
> **dannyboy79 said:**
> the peer means the computer which you're trying to connect to (your ISP) so that you can have an internet connection. (i think, lol)

Here's a great link to some common ppp issues. [http://ppp.samba.org/FAQ.html](http://ppp.samba.org/FAQ.html)

I took this snipit in case you can't access that webpage.
and one more question i mentioned above is do all computers generally enable NOAUTH and is it fine(safe) ?
and i couldnt understand the intruder thing. do you mean that intruders can easily use my comp and connection easily if I have NOAUTH enabled or what?

---

### Post by bluexrider on 2011-11-07
> **cherrywarrior said:**
> hello guys,
I am a kind of newbie to ubuntu( in some aspects like  networking). And  what I wanna ask is about NOAUTH. I read on "ubuntu  help" that while  configuring a PPPOE connection we need to enable  NOAUTH. I just couldnt  figure out what it is? I mean I wanna know  exactly about it(meaning  and a lil bit of explanation). So guys pls help  me out. I even wanna  know about DEFAULTROUTE , NODETACH, PEER DNS,   LIMITED MSS PROBLEM. I  am really sorry if I am expecting too much from u  guys. But I would  definitely do something for u in return.
I posted this already but im posting this again because I didnt get even a single reply and Im feeling helpless. Any helpful guys out there please please please help me.

NOAUTH [http://manpages.ubuntu.com/manpages/hardy/man5/NoAuth.5.html](http://manpages.ubuntu.com/manpages/hardy/man5/NoAuth.5.html)

User Guide 
[https://help.ubuntu.com/](https://help.ubuntu.com/)

Use the search in the upper right for your questions

hope this helps

---

### Post by dannyboy79 on 2011-11-07
> **cherrywarrior said:**
> and one more question i mentioned above is do all computers generally enable NOAUTH and is it fine(safe) ?
and i couldnt understand the intruder thing. do you mean that intruders can easily use my comp and connection easily if I have NOAUTH enabled or what?

i don't know, I would have to google it to learn myself. PPP is pretty much dead with broadband availability now days.

 I am done helping you. Please don't PM me anymore either.

---

### Post by dannyboy79 on 2011-11-07
> **bluexrider said:**
> NOAUTH [http://manpages.ubuntu.com/manpages/hardy/man5/NoAuth.5.html](http://manpages.ubuntu.com/manpages/hardy/man5/NoAuth.5.html)

User Guide 
[https://help.ubuntu.com/](https://help.ubuntu.com/)

Use the search in the upper right for your questions

hope this helps
OMG really? She's not asking about AFS server config options. You're going to confuse her even more.

---

### Post by lisati on 2011-11-07
> **cherrywarrior said:**
> hi anewguy,
Yeah i posted it there but didnt get even a single reply and i really tried the 3 things u told me and finally i got here where i am right now and I really hope that someone would help me out.

Please don't start multiple threads on the same problem, it dilutes the community's ability to help. I've closed your other threads.

---

### Post by cherryw on 2011-11-07
hey danny,
what do you mean by "PPP is dead" ? Isnt there a need to configure my connection thru PPPOE if im using broadband?
Im really confused.

---

### Post by dannyboy79 on 2011-11-07
> **cherrywarrior said:**
> hey danny,
what do you mean by "PPP is dead" ? Isnt there a need to configure my connection thru PPPOE if im using broadband?
Im really confused.
My reluctance to help you is overpowered by the memory I have when I first started using Ubuntu BUT you have to more patient. Sending me PM's saying that I am ignoring you and basically demanding people help you ASAP will NOT get you help from most IMO.

I will attempt to help some more but you need to really just post your specific question instead of asking for definitions of terms that are within the man pages. (man = manual)

I said PPP is pretty much dead because it's mostly used for dial-up connections to the best of my knowledge and I am not aware of really anyone still using dial-up BUT I am sure there are people who do. I had to help a family friend who wanted to test out Ubuntu with a dial-up modem to see if he would use the internet enough to justify getting a broadband service. It was a lot of resesarch and googling and setup but I did get it work.

You're actually confusing me. Please answer the following questions BEFORE posting anything else, PLEASE.

1. What type of internet service do you have at the location your ubuntu computer is being used at? (example: dial-up, dsl, broadband, aircard)

2. If it is dsl, do you know the username and password in order to connect to your ISP? (ISP=internet service provider)

3. Are you connected with an ethernet cord directly to the modem OR do you have a router in between?

Answer those and I will attempt to provide help. If your questions are merely about certain settings, what they mean, is it safe, etc etc, UNFORTUNATELY I can't help you as I am unsure myself.

---

### Post by anewguy on 2011-11-07
You need to also keep this in mind:  sometimes, especially when just starting out, you are going to have to be a little more concerned about getting it working than hounding people for definitions you can find yourself.  What you will find is that people are ignoring you and won't answer because people have given you your answer already:  search the WEB (not just the forum, as well as the ubuntu documents website) for each of those terms, then search the web (or the Ubuntu documents website) for documents on ppd (the daemon you need running) and how it all works.  All the technical details are there - every little step.  BUT *YOU* need to do the footwork.  We can't really hold your hand that much, and replying to every definition request would be horrendous.

Follow some advice to get your connection working - that's what dannyboy79 is offering to you if you will:

(1) quit hounding him
(2) answer the questions he has asked
(3) don't ask more questions.  Do it step by step with him.

Once your connection is working, search and read - and it will take a lot of time.  It's the only way you're going to learn what all the things are you are asking.

And let's face it - if you were in Windows chances are your ISP would have given you a disk to get it all working and you'd never know there are the proverbial "zillion" things you can set for the internals there as well - you'd just accept it and let it run.

For now try doing the same with the help being offered.

And for EVERYONE out there - unless specifically requested by the user, do not PM people who have replied to your posts.  Post a request in the thread asking them to PM you - if they do, be polite and don't start hounding them.

---

### Post by wildmanne39 on 2011-11-07
Hi, as I said in my first post most of the time all of it gets setup for you in network manager.

I asked questions that last night that you did not answer.

If your connection is not working state that and tell us if it is wired or wireless then we maybe able to help.
Thank you

---

### Post by anewguy on 2011-11-07
> **wildmanne39 said:**
> Hi, as I said in my first post most of the time all of it gets setup for you in network manager.

I asked questions that last night that you did not answer.

If your connection is not working state that and tell us if it is wired or wireless then we maybe able to help.
Thank you
Thanks for offering to help the OP again.  You can probably tell my patience, as well as that of others, is running extremely thin as they are so concerned about what all of the options mean instead of just getting it running.  In fact, from everything they've replied so far, I can't tell if they have working connection already or not.  It seems so stupid to me that people let a Windows driver set up, ISP set up, program install, etc., do whatever it wants but you throw in open-source Linux and how a lot of the options are more up-front and visual all of a sudden it's like nothing can be done anymore.

At any rate, you have more patience than me at this point.  Hope things are going great for you!

Dave ;)

---

