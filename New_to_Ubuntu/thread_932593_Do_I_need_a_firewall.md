---
title: "Do I need a firewall?"
date: 2008-09-28
forum: New to Ubuntu
---

### Post by LeeHamo on 2008-09-28
Hi,

Ive googled this and looked around but all posts about it seem to be about 2 years old so I feel I need to ask the question again.

Do I need a firewall for ubuntu?

I want to use firefox to browse my internet banking, make card purchases etc,.

I have the firestarter but when I click lock internet the whole thing locks up, so I just dont touch it now and leave it running, but do I really need it?

Cheers.

Lee.

---

### Post by oilchangeguy on 2008-09-28
> **LeeHamo said:**
> Hi,

Ive googled this and looked around but all posts about it seem to be about 2 years old so I feel I need to ask the question again.

Do I need a firewall for ubuntu?

I want to use firefox to browse my internet banking, make card purchases etc,.

I have the firestarter but when I click lock internet the whole thing locks up, so I just dont touch it now and leave it running, but do I really need it?

Cheers.

Lee.

you don't need firestarter. it's simply a user interface for iptables. most users don't need to play with iptables settings.

---

### Post by Nettoyer on 2008-09-28
Here's my opinion:

I think it comes down to personal preference, if you feel safer using a firewall, then by all means do it! For the use of Firestarter, you just run it and let it go.  Clicking the Lock button stops the in/out of your internet via your machine.  

You could try this website if you're worried about your ports being open:
[https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2)
It's known as "Shields Up", it can give you a better idea of what ports you have open on your machine.

---

### Post by LeeHamo on 2008-09-28
So if I remove it am I safe, on windows I had zonealarm I always feel safe knowing theres something protecting me.

I havent a clue about iptables, do they work without any help from the user?

Am I fully safe to do the things i want without worrying about having my bank details etc stolen?

---

### Post by oilchangeguy on 2008-09-28
> **LeeHamo said:**
> So if I remove it am I safe, on windows I had zonealarm I always feel safe knowing theres something protecting me.

I havent a clue about iptables, do they work without any help from the user?

Am I fully safe to do the things i want without worrying about having my bank details etc stolen?

remember, this is NOT windows. 

iptables works fine for most users without any intervention.

there's no 100% safe. but with linux, you are much more secure than you are with windows. and that's not really windows fault. it's people with too much time on their hands trying to pick thru the worlds most installed operating system. linux in general due to it's low install base makes it less likely of a target.

---

### Post by The Cog on 2008-09-28
You probably don't need a firewall. The defult Ubuntu install isn't listening for connections on any ports. And if you install any services yourself, then you probably want them to be available from the internet anyway so a firewall still won't help.

A firewall would be useful if you installed a service and knew you only wanted it to be reachable from a few known IP addresses (e.g. SSH at home only reachable from work).

---

### Post by oldsoundguy on 2008-09-28
IMO, it won't hinder and it won't hurt.  Remember a firewall just prevents outsiders from accessing or attempting to access your computer.  It also prevents your computer from being used as a Denial Of Service attack bot.  Don't think that can happen with Linux YET, but you can trust that the script kiddies ARE trying to be able to do that.

My computers live behind a router.  It has a built in hardware firewall.

Having said that, using individual firewall on networked computers can limit access to those computers from OTHER computers on that network.  If you are running a small office and want to keep people out of certain computers yet still have full network access FOR those computers, a firewall becomes a valuable tool.

---

### Post by LeeHamo on 2008-09-28
Thanks a lot for the replies, that shields up site really convinved me I was safe, all the tests I ran said I was in stealth mode, not visible to the internet.

which is nice lol.

So I am gonna remove firestarter, this is ok isnt it?

One last thing without me making another thread, do I need a virus scanner or spyware scanners, any scanners in general for that matter or is linux just so safe.

Lee.

---

### Post by oilchangeguy on 2008-09-28
> **LeeHamo said:**
> Thanks a lot for the replies, that shields up site really convinved me I was safe, all the tests I ran said I was in stealth mode, not visible to the internet.

which is nice lol.

So I am gonna remove firestarter, this is ok isnt it?

One last thing without me making another thread, do I need a virus scanner or spyware scanners, any scanners in general for that matter or is linux just so safe.

Lee.

yes, remove firestarter. 
no to virus and spyware scanners. they scan for .exe files, which won't run in linux.

---

### Post by LeeHamo on 2008-09-28
by the way, after reading the last post I thought id mention my Pc lives behing a router also, its wired to a wireless G+ belkin with wep128 enabled.

I use the wireless for the ps3 and Ds and wii but the Pc is cabled up to the router.

Lee.

---

### Post by oldsoundguy on 2008-09-28
no need for virus or spybot scanners or protection unless you have Windows in WINE or in a VM .. those should be installed WITH protection FOR the Windows stuff if you intend to take it on line.

---

### Post by LeeHamo on 2008-09-28
Well I have windows on another drive, just incase I ever want to go back to windows, it has firewall, virus scanner etc and i cant delete it yet cause that drive holds a lot of pictures and personal stuff that I havent transferred to ubuntu yet(dont have the knowledge to do it yet), I also access some of the files in it from ubuntu, music etc.

nobody can get in through another hard disk with windows on it if i booted up using ubuntu though can they?

---

### Post by oldsoundguy on 2008-09-28
only if you take that Windows drive on line can issues occur if your protection for same is outdated. (not saying they WILL occur, that all depends on WHERE you go.  IF peer to peer .. cross your fingers and toes.

Windows is a great system for playing games just as long as you don't go ON LINE with it!! LOL

I have Windows on separate COMPUTERS.  They go on line to BOINC in Berkeley and to get protection updates from known sites .. virtually no surfing. And especially no other downloading or uploading (except to MY website!).

---

### Post by LeeHamo on 2008-09-28
So when I boot on startup into ubuntu on the F drive and I view files on the C drive which is basically my full XP install, from within ubuntu, is this safe?

---

### Post by wolfen69 on 2008-09-28
yes, you are safe unless you download a file (with a virus) then transfer it to the windows drive, boot into windows, then execute it. but if you are in windows, just scan it first.

---

### Post by PocketDog on 2008-09-28
Hehe you really are thinking like a Windows user :p Not a criticism, you just have to relax. Any programs, even 'viruses', have to be installed and run, by you, after after entering your userpass. Too much trouble, and too much security for malware to proliferate. As long as you get your software from the repos (apt-get, Synaptic) or other trusted sources (Softpedia for instance) then you won't have any security issues. Because Ubuntu is open-source, there are literally thousands upon thousands of eyes watching. You're safe now

---

### Post by wolfen69 on 2008-09-28
but don't worry too much about viruses and spyware while in linux. sure, you could get struck by lightning, but the chances are *real* small. if you dont do anything fancy, i also would not worry about a firewall. linux works differently in that regard.

on a side note, could you imagine going online in windows with no firewall and no anti-virus? funny. (i've always wanted to unplug all my drives and pop in a test drive, install windows with NO protection, and see how long it takes to get fubar'ed. might try it soon. :-) )

---

### Post by AndyCooll on 2008-09-28
> **LeeHamo said:**
> ...can't delete it yet cause that drive holds a lot of pictures and personal stuff that I havent transferred to ubuntu yet(dont have the knowledge to do it yet), I also access some of the files in it from ubuntu, music etc.
To do that you could either simply copy all that stuff to your /home folder, or better still create a new partition calling it something like /share, mount it and finally copy all the stuff to that.

:cool:

---

### Post by Michaelg14 on 2008-09-28
I don't know very much about firewalls but after reading this thread I installed Firestarter and found out that my firewall was not starting.  I had a problem with an unused wifi connection.  I now have it working with the Firewstarter icon in the task pane and it will occasionally turn red indicating something trying to get in.  I'm sure with Linux I wouldn't have a problem but it is interesting to see what is showing up on my doorstep.

---

### Post by shifty_powers on 2008-09-28
i remember an article about a competition, where they took three computers, one with windows xp, one with osx, one with ubuntu. there were several teams of hackers, and they had to compromise and take control of the different pc's. the windows one was compromised fairly quickly, osx lasted about 24 hours, and ubuntu was still standing when the competition ended nearly 6 days later :D

---

### Post by Sef on 2008-09-28
> no need for virus or spybot scanners or protection unless you have Windows in WINE or in a VM .

If you use a client email, then you need an anti-virus.  Viruses will not infect you, but you could send and infect your Windows friends.

---

### Post by jerome1232 on 2008-09-28
Whenever you are behind a router you are essentially firewalled, they use NAT (network address translation) to let multiple computers share a single internet connection. All traffic from the internet is actually addressed to the router, not the individual computers on your network.

Any **incoming** traffic is dropped by your router unless you configured it to forward the traffic to a specific computer.

---

### Post by oldsoundguy on 2008-09-28
> **wolfen69 said:**
> 
on a side note, could you imagine going online in windows with no firewall and no anti-virus? funny. (i've always wanted to unplug all my drives and pop in a test drive, install windows with NO protection, and see how long it takes to get fubar'ed. might try it soon. :-) )
  
Latest figures I have seen from several of the "watch dog" Windows sites is that you will get SOMETHING planted on your Windows computer in NO MORE THAN 20 minutes unprotected surfing on line.  SCARY

<rant>I do on line consulting and service for Windows users at times (as a service).  The truly frightening thing is that most Windows users haven't a CLUE as to the need for protection.  They ASSUME that all will go well with that install they got at the local big box store and that all they have to do is turn the computer on and all will be peachy! Six months later they pay the price when the trial for Norton and the other protection services runs out and they don't want to PAY for anything as they think that the stuff will still work and does not need updating.
Giving the devil his due .. Vista, bloated and slow running as it is and with the need for a navigational map to find anything, HAS, at least, made an effort to ease the problem.
But the new Windows "protection" program (Windows One Care) is full of holes, and they soon are going to CHARGE for the program .. now just how bogus is that?  Build a swiss cheese system, sell it for a lot of money and then CHARGE the customer to protect that self same system?  Think not only is that not fair, it MORALLY REPREHENSIBLE!</rant>

---

