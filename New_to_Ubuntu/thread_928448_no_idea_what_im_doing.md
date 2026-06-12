---
title: "no idea what im doing?"
date: 2008-09-24
forum: New to Ubuntu
---

### Post by darknettie on 2008-09-24
so a friend of mine convinced me to use ubuntu instead of vista, he done everything so now its a dual boot with ubuntu and vista.
no i know very little about any computer.
here are my problems:
lately everything has been playing up, alot of the programs on my computer wont start and i have to force quit and reboot even then someimes they dont start. 
or ill be using firefox leave the laptop for a second and when i come back its gone...completely gone

when things freeze up ive been told to press ctrl+alt+backspace.
most of the time this doesnt do anything it just freezes it at the login screen.
and last every time i restart my computer or turn it off i have to re do the manual network config. it wont save the settings.
:confused:

---

### Post by Pro-reason on 2008-09-24
It almost sounds like you're booting from the live CD instead of your Ubuntu installation.

---

### Post by Korijn on 2008-09-24
In other words: take out the disc if it's still in your computer.

---

### Post by lisati on 2008-09-24
> **darknettie said:**
> so a friend of mine convinced me to use ubuntu instead of vista, he done everything so now its a dual boot with ubuntu and vista.
no i know very little about any computer.
here are my problems:
lately everything has been playing up, alot of the programs on my computer wont start and i have to force quit and reboot even then someimes they dont start. 
or ill be using firefox leave the laptop for a second and when i come back its gone...completely gone

when things freeze up ive been told to press ctrl+alt+backspace.
most of the time this doesnt do anything it just freezes it at the login screen.
and last every time i restart my computer or turn it off i have to re do the manual network config. it wont save the settings.
:confused:

> **Pro-reason said:**
> It almost sounds like you're booting from the live CD instead of your Ubuntu installation.

> **Korijn said:**
> In other words: take out the disc if it's still in your computer.

+1 for making sure that you have removed the installation CD. Are you getting an opportunity to choose between Vista and Ubuntu when you turn your computer on?

---

### Post by darknettie on 2008-09-24
there is no cd in there

when i restart i get the option to use vista or ubuntu.
it was going fine for a few wekks but then it just started playing up

---

### Post by Pro-reason on 2008-09-24
Have you installed any updates?

---

### Post by Primefalcon on 2008-09-24
if you haven't go to system => Administration => Update Manager

click check and install updates

---

### Post by darknettie on 2008-09-24
ive installed all the updates. 
sometimes even that doesnt work:(

---

### Post by Pro-reason on 2008-09-24
It wasn't a rhetorical question, to urge you to update.

Did you install any updates?  If so, a bug in an update could have affected something.  I am trying to ascertain what might have gone wrong.

---

### Post by Sef on 2008-09-24
1) What are your system specs?

2) How do you connect to the internet?

---

### Post by darknettie on 2008-09-25
i have a wifi connection, it saves all the details except the password. i have to re enter it each time. 

its been playing up for a while. but it started doing it more after i tried to install updates and it wouldnt.

sorry if im not much help:???:

---

### Post by theDaveTheRave on 2008-09-25
Dude,

you are obviously trying to hook into the net with a wireless card?

have you tried running the laptop with a hardwired connection into the back of the wireless router? it should find the network straight off the bat this way, and the download of the updates will be quicker!

what version of ubuntu are you using?? open a terminal and type

<uname -a> and drop the output message into the board.

What desktop are you using?? kde or Gnome?

What happened to your mate that loaded Ubuntu for you? have they buggered off and left you hanging?

Dave

---

### Post by darknettie on 2008-09-25
thats what came up...

Linux 2.6.24-19-generic #1 SMP  i686 GNU/Linux

my desk top is gnome..

my friend went to melb for work, and pretty much left me on my own.

---

### Post by theDaveTheRave on 2008-10-08
Darknettie,

sorry for the slow reply, I'm moving around a lot at the moment, and my connection isn't always good.... at least I can get a short Ubuntu fix for the next few minutes.

From your last post you seem to be running an up to date kernel, so there should be no reason for the network to not be working!

I hate to ask the same question twice, but am I correct in assuming you are using a wireless card?

Have you tried a hard wired connection?

Ok these commands should help us to solve your problem.

> 
ifconfig 

 this will return details for all your network ports, and give a status for them.
If, like I suspect, you are running a wireless card, you can also try
> 
iwlist scan

this will tell you if your wireless port, if you have one, supports scanning, if it doesn't then you'll never see the wireless network!

I'm going to be a bit of a record as I am assuming your issue is with your wireless card.

The functioning of the wireless is a bit strange, essentially you have the card (often reported as ath0 in the return of the <ifconfig> command) and then this needs to be "wrapped" in a bit of controling software that creates a "pseudo netword interface" called wifi0 (or something similar)

so I hope that this info may help explain why there is often a problem getting networking to function in Linux, but once you are there the feeling of success is great  :guitar:.... untill you get some stupid error and the whole thing breaks  :lolflag:

Anyhow, run these commands, and post the output here. with luck it will give us some insight to your problem... if you are serious about fighting your way into the linux / ubuntu world you will find the experience both rewarding and, at times, extremely infuriating.

if you want an idea of what I mean try using vi as your text editor, rather than gedit!](*,)

good luck

Dave

---

### Post by Sycron on 2008-10-08
Also try ```
sudo iwlist scan
```.

---

