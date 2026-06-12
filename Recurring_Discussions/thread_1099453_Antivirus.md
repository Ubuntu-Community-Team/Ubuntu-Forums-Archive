---
title: "Antivirus"
date: 2009-03-18
forum: Recurring Discussions
---

### Post by duffaire on 2009-03-18
Is there an anti-virus program for Linux, also is there any spyware avalable. I am new to Linux so any help would be appreciated

---

### Post by Partyboi2 on 2009-03-18
You don't really need a antivirus program for linux. If you are interested in reading up on security, you may find [[COLOR=Blue]this[/COLOR]]("http://ubuntuforums.org/showthread.php?t=510812") useful.

---

### Post by gandaran on 2009-03-18
> **duffaire said:**
> Is there an anti-virus program for Linux, also is there any spyware avalable. I am new to Linux so any help would be appreciated
no, there ain't any and you don't need any, there are antivirus programs you can install in linux, avg, clam, bitdefender (the best), fprot and avast, these are the free ones but they only scan for windows virus so it's no use to have any installed unless you running a linux server and want to protect microsoft windows systems.

---

### Post by 3rdalbum on 2009-03-18
There's no spyware available - that's why you don't need an anti-virus program.

If you live on an island where nobody has polio and nobody who visits has polio, then you don't need a polio vaccination. Linux doesn't run Windows viruses and there are no current Linux-specific viruses.

Same goes for spyware, adware, worms etc.

---

### Post by muteXe on 2009-03-18
Dunno how up to date this is: 

[http://www.itsecurity.com/features/ubuntu-secure-install-resource/](http://www.itsecurity.com/features/ubuntu-secure-install-resource/)

Interesting read though.

---

### Post by presence1960 on 2009-03-18
> **Partyboi2 said:**
> You don't really need a antivirus program for linux. If you are interested in reading up on security, you may find [[COLOR=Blue]this[/COLOR]]("http://ubuntuforums.org/showthread.php?t=510812") useful.

+1

I try not to comment too much about anti-virus and firewall. I just link them to that article so they can read it for themselves. BTW that is a great article on security.

---

### Post by Botbob89 on 2009-03-18
At the end of the day, if you really are conscious of getting viruses and spyware (though guys have already talked about there being no need for it), but if you really want to, there are plenty you can install like regular packages through terminal/ synaptic.

But like these guys have said, there's no real need

---

### Post by duffaire on 2009-03-18
Thank you for all your replies and advice

---

### Post by scottuss on 2009-03-18
Welcome! A quick tip for future posts on here, at the top right of the page there is a box labelled "search" If you type something (in this case antivirus) into there you will get all posts (and for antivirus there will be LOTS) related to what you have searched for.

This issue is discussed time and again, please do a search before posting next time.


P.S I don't mean to sound rude! :) Again, welcome to Ubuntu :)

---

### Post by 123456789123456789123456 on 2009-03-18
clam is the only antivirus available for Ubuntu and linux.  It can be found through the add new programs through ubuntu.  Search for virus.
it want be listed as clam, but a scanner for clam.
clam installs, it was listed that you don't need antivirus, that is true and false.  Though there are very few viruses for linux out there, there are some.  and you could be effected by one, though by all means that is rare.  As far as I can tell, there are currently no spyware/mileware for linux, so you don't need protection from them.

---

### Post by scottuss on 2009-03-18
> **123456789123456789123456 said:**
> clam is the only antivirus available for Ubuntu and linux.  It can be found through the add new programs through ubuntu.  Search for virus.
it want be listed as clam, but a scanner for clam.
clam installs, it was listed that you don't need antivirus, that is true and false.  Though there are very few viruses for linux out there, there are some.  and you could be effected by one, though by all means that is rare.  As far as I can tell, there are currently no spyware/mileware for linux, so you don't need protection from them.

Not entirely accurate. The most likely infection on a Linux box would be a Rootkit [http://en.wikipedia.org/wiki/Rootkit]("http://en.wikipedia.org/wiki/Rootkit") A rootkit is not a Virus (some are Trojans) Again, there are a few other bits (mostly trojans and worms) but actually getting infected by one of these is very unlikely, even less so if the user is careful (nothing to do with any software antivirus protection)

---

### Post by cptrohn on 2009-03-18
Don't you need to have Clam or something similar if you are using wine for Windows apps though?

---

### Post by Botbob89 on 2009-03-18
If you are planning on dual booting with Windows and using Windows a lot, then it is advisable that you have some sort of anti - virus in place, simply because if your machine is affected, your Ubuntu will be, whether the Ubuntu actually has the virus or not

---

### Post by LowSky on 2009-03-18
> **cptrohn said:**
> Don't you need to have Clam or something similar if you are using wine for Windows apps though?

No, what?

Viruses only run on the systems they're designed for. Windows Viruses/Malware wont work on a Linux machine. So if you download the bug on your ubuntu machine the file will just sit there, it cant run. and because Windows cannot see EXT3 file systems natively the file cannot even be seen, which means it cant do anything. The only way the file can spread if it is downloaded to a windows partition, and somehow run by the user. 

People please. ... there are known WILD viruses/malware/rootkits that can infect Linux computers at this time. being said the only way to infect a Linux computer is to have Root access which most people here are never running Firefox or Bittorrent on anyway.

So in conclusion your safe running Linux at all times. You can only infect your windows partition if you place the viruses on the Windows partition.

---

### Post by Botbob89 on 2009-03-18
> **LowSky said:**
> No, what?

Viruses only run on the systems they're designed for. Windows Viruses/Malware wont work on a Linux machine. So if you download the bug on your ubuntu machine the file will just sit there, it cant run. and because Windows cannot see EXT3 file systems natively the file cannot even be seen, which means it cant do anything. The only way the file can spread if it is downloaded to a windows partition, and somehow run by the user. 

People please. ... there are known WILD viruses/malware/rootkits that can infect Linux computers at this time. being said the only way to infect a Linux computer is to have Root access which most people here are never running Firefox or Bittorrent on anyway.

So in conclusion your safe running Linux at all times. You can only infect your windows partition if you place the viruses on the Windows partition.
What I meant to say: having your Windows partition infected will affect your linux partition by having your machine a component affected...your actualy linux would be OK

---

### Post by sydbat on 2009-03-18
> **LowSky said:**
> <snip>

People please. ... there are **NO** known WILD viruses/malware/rootkits that can infect Linux computers at this time.Fixed that for you.

> **Botbob89 said:**
> What I meant to say: having your Windows partition infected will affect your linux partition by having your machine a component affected...your actualy linux would be OKWhat? No. Not unless you have installed using WUBI.

---

### Post by Botbob89 on 2009-03-18
> **sydbat said:**
> Fixed that for you.

What? No. Not unless you have installed using WUBI.
Argh I am not articulate enough to say what I mean....I know what I mean, so I guess that's what counts :P

---

### Post by tarps87 on 2009-03-18
> **Botbob89 said:**
> Argh I am not articulate enough to say what I mean....I know what I mean, so I guess that's what counts :P

Yes the computer it's self will be infected, although unless you have install a program to read/write to ext formatted drives on the windows install it won't effect your drive, however if you mount you windows drive it will in essence be on your GNU/Linux system even though there is more chance of  [the International Space Station’s Node 3 being called Ubuntu]("http://www.nasa.gov/externalflash/name_ISS/index.html") ;) than there is of the virus running/ being run.

I think I get what you are trying to say, if that is that you can use the virus scanner in Ubuntu to remove viruses from the windows partition

---

### Post by Botbob89 on 2009-03-18
> **tarps87 said:**
> Yes the computer it's self will be infected, although unless you have install a program to read/write to ext formatted drives on the windows install it won't effect your drive, however if you mount you windows drive it will in essence be on your GNU/Linux system even though there is more chance of  [the International Space Station’s Node 3 being called Ubuntu]("http://www.nasa.gov/externalflash/name_ISS/index.html") ;) than there is of the virus running/ being run.

I think I get what you are trying to say, if that is that you can use the virus scanner in Ubuntu to remove viruses from the windows partition
Yes lol, that!!

I shall have to have a good think next time I try to explain something :P

---

### Post by presence1960 on 2009-03-18
> **123456789123456789123456 said:**
> clam is the only antivirus available for Ubuntu and linux.  It can be found through the add new programs through ubuntu.  Search for virus.
it want be listed as clam, but a scanner for clam.
clam installs, it was listed that you don't need antivirus, that is true and false.  Though there are very few viruses for linux out there, there are some.  and you could be effected by one, though by all means that is rare.  As far as I can tell, there are currently no spyware/mileware for linux, so you don't need protection from them.

Clam AV is not the only one available for Ubuntu & Linux. And all of them scan only for Windows based virus. Please read this : [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

I think it would be more prudent to install chkrootkit and rkhunter from the repositories.

---

### Post by bapoumba on 2009-03-18
Moved to Recurring Discussions.

---

