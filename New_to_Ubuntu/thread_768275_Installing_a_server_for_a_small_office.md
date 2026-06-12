---
title: "Installing a server for a small office"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by meGaNoob on 2008-04-26
Ello everyone,

I've just started work at a company where the entire IT department (well 1 person) has recently been fired.

Now I am not the IT guy, but I'm the only one around that my Boss seems to think might be able to handle the following issue (I have doubts):

We need to install a server since there doesn't seem to be one.We have a hp pro curve  switch and an 3M thinggy ontop of it where all the ethernet plugs are plugged in. 

I suggested Ubuntu since I hear so many good things. So ok fine, ubuntu it is then. Here comes the bit where i say again 'i am not the IT' guy: I AM NOT THE IT GUY.

My Question is How do i set up this server? I realise I need a computer to put it on but how/in what way do i hook it up to the switch board?

The main task the server should perform is monitoring traffic and  blocking web pages initially and then email etc as we get someone in or I gain the experience (which I hope will happen).

The office all runs on XP but no doubt this isnt a problem. We just need an interface/server between the switcher and the internet. 

Hope the community lives up to the reputation!

Regards

---

### Post by gsmanners on 2008-04-26
If you have trouble setting up your switcher/router, you really should look around for documentation on that particular device till you're confident you can configure it properly.

Setting up the applications shouldn't be too much trouble once you have the hardware set up properly.

[https://help.ubuntu.com/community/Servers](https://help.ubuntu.com/community/Servers)

---

### Post by scorp123 on 2008-04-26
Why do you think you need a "server"? What for exactly?

Or did you mean: **Firewall.** I suppose this is what you want? Are you absolutely sure you need that?

I wonder how you were able to get that job (I mean no offence!) but please be aware that as "IT administrator" you can be held responsible if anything goes wrong. So please: **Know [B]_what_** you do and _**why**_ you do it.[/B]

Never ever install something "just because". That will only get you into trouble. Be aware what the goal is, be aware how to achieve that goal, and then and only then you start thinking of installing stuff.

Also, guessing from your username "MegaNoob" (again: I don't mean it as an offence!) I suppose your level of Linux knowledge isn't high at the moment. You therefore might want to take a look at other distributions too. In my personal opinion Novell's **OpenSUSE** is better suited for total beginners than Ubuntu. Also, it features a very nice setup and administration program (similar to the "Control Panel" in Windows) which would let you configure most things from a "point and click" menu. You should give it a try in my humble opinion:
[http://www.opensuse.org/](http://www.opensuse.org/)

I am not saying Ubuntu is "bad" or anything ... But if you're really a total beginner and thrown right into IT administration of a company then in my opinion SUSE does a better job at "hand-holding" than Ubuntu does at the moment. On the other hand Ubuntu's forums are absolutely top ... so ultimately it will depend on which distro suits you better and which is easier for you to use.

---

### Post by RudolfMDLT on 2008-04-26
I'm with scorp123 on this one:
> but please be aware that as "IT administrator" you can be held responsible if anything goes wrong.

No offense meant, but it really sounds like you don't really know what you want, never mind how to get there.

What I suggest is that you make a list of things that your company requires from it's IT infrastructure - and specifically this "server". For example:
1)Filter internet to block access to YouTube
2)Store backup files
3)Make Coffee

The forum members can help you either set it up or at least point you in some general direction. But please note that if you are new to linux I really recommend that you actually get some one that know what they are talking about to help you set things up.

Cheers,

Rudolf

---

### Post by meGaNoob on 2008-04-26
Thanks for the replies.

I hear what you're all saying and it isnt that it's something I want, I basically asked the same question of 'for what and why' - after all if the boss wants some sites blocked a simple hosts file installed when everyone's not looking does the trick [at least until someone wisens up].

We need a way of blocking sites and monitoring what some of the office muppets are doing. If my lack of knowledge is horrible imagine how bad the rest of the office is! Basically we are in the middle of nowhere and getting people is not easy - doing my actual job and now this IT business is not my idea of a good time, considering I just got hired for OTHER work.

Anyways thanks for the input, i feel suitably put in the corner of the room :)!

I guess I'll go do some reading.:lolflag:

---

### Post by scorp123 on 2008-04-26
> **meGaNoob said:**
>  We need a way of blocking sites  So you need a proxy server and a web content filter. Please read here:
[http://ubuntuforums.org/showthread.php?t=320733](http://ubuntuforums.org/showthread.php?t=320733)

That description is for an older release of Ubuntu (6.x releases from 2006) but all in all it is still valid and the things described there should still work for the current releases (7.04, 7.10, and the new 8.04).

> **meGaNoob said:**
>  and monitoring what some of the office muppets are doing.  Please be aware that there are legal limits of what you may do or not do. What exactly the limits are is different from country to country, so it may be a good idea to check that. For example here in Switzerland it would be totally illegal for your boss and for you as admin to intercept and read the e-mails of the other employees or inspect their web activities; however it is not illegal to simply block certain web sites (e.g. youtube.com) and certain e-mail addresses (e.g. so that nobody could send e-mails to *.hotmail.com recipients). As I said ... this is different from country to country and you should know what is legal and what isn't. Don't rely on your boss to do your homework for you. You are the IT admin, you have to know, you have the responsibility. So make sure whatever monitoring and other measures you take that might intrude on the privacy of your users is perfectly legal in your jurisdiction.

Also, always keep your e-mails somewhere "safe". If ever anything goes wrong you still have your e-mail archives which can help a great deal if things don't work out the way you expected. Having all the e-mails can help a great deal to prove what was said and what wasn't .... just in case. Better have it and never need it than the other way around! ;)

> **meGaNoob said:**
>  I guess I'll go do some reading. :lolflag:  Basically that's all you really need. Honestly. The first thing you really should master and become a guru of is ... **GOOGLE.** 
I mean it. **Google will solve about 75% of all your problems.** The real art is to feed it correctly with search arguments so you'd get useful results out of it. And whenever you encounter useful postings or whenever Google spits out something useful: **Bookmark it.** Having bookmarks organised by topic and keeping them tidy is the key to solving the other 25% of problems you might ever encounter. That's the whole magic there is to it. The rest is experience (good + bad) which will come with the years ;)

---

### Post by noswal on 2008-04-26
I'm reasonably new to linux but setup a home network, if you can follow this
[http://ubuntuforums.org/showthread.php?t=766343](http://ubuntuforums.org/showthread.php?t=766343) then you can network the whole office and then ask how to use squid to do the other things you need.

---

### Post by meGaNoob on 2008-04-28
Thanks you two...definetly pointed me in the right direction...as for 'policies' on emails - in this country there are none! Not that I want to read their emails anyway. 

Regards

---

