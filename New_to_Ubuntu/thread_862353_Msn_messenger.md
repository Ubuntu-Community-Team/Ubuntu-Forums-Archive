---
title: "Msn messenger?"
date: 2008-07-17
forum: New to Ubuntu
---

### Post by xsabrewulf on 2008-07-17
I have Pidgin, but I only really use the MSN Messenger portion

I was wondering, is there any other app that specializes in MSN and that will handle MSN messenger better?

---

### Post by almaddin on 2008-07-17
> **xsabrewulf said:**
> I have Pidgin, but I only really use the MSN Messenger portion

I was wondering, is there any other app that specializes in MSN and that will handle MSN messenger better?

Try AMSN for instance, there are a lot more. Really can't remember them all.

---

### Post by Morpheun on 2008-07-17
> **xsabrewulf said:**
> I have Pidgin, but I only really use the MSN Messenger portion

I was wondering, is there any other app that specializes in MSN and that will handle MSN messenger better?


Look here:
[http://en.wikipedia.org/wiki/Comparison_of_instant_messaging_clients](http://en.wikipedia.org/wiki/Comparison_of_instant_messaging_clients)

It's really a personal preference based on what you like.

---

### Post by phantomjoker on 2008-07-17
what do you find an issue with pidgen? I use it for the same thing and find it alright. what features do you specifically need?

---

### Post by Dutch70 on 2008-07-17
also you can try emesene. its made to work with MSN.
I just installed it last night. :)

just go to synaptic and search for it. mark and install...you're done!

Dutch

---

### Post by bobbocanfly on 2008-07-17
```
sudo apt-get install amsn
```
```
sudo apt-get install emesene
```

Either of those will fix your problem

---

### Post by space.duck on 2008-07-17
what do you find annoying with pidgin. I only use the MSN protocol of pidgin but i think it's fantastic, much better than any windows live messenger.

---

### Post by Dutch70 on 2008-07-17
> **space.duck said:**
> what do you find annoying with pidgin. I only use the MSN protocol of pidgin but i think it's fantastic, much better than any windows live messenger.

I'll take a shot at this one, since the op hasn't returned!

EDIT: Wasn't trying to be rude, just thought that he as well as myself would like to see other opinions.

Did you ever go to online help and try and add or change anything(like smileys)...looks like you need to redesign it with source codes or somehting, or they just tell you to forget it, cause its never gonna change.
 Dont get me wrong, I like pidgin better than WLM too, but when I communicate with my daughter, she doesn't even get the smileys I send her. yeah, yeah, laugh it up...lol j/k, of course thats only important when I talk to her. And I don't know that any others would be any different.

Now what is so fantastic about pidgin? 

OH CRAP! emesene is msn messenger for the most part...lol
I'm sticking with pidgin!

---

### Post by xsabrewulf on 2008-07-17
The issue I have with Pidgin is when I go to my windows machine and I change my msn name

I load up pidgin and it has my user name from like months ago.


The username is never the same.

---

### Post by Joeb454 on 2008-07-17
That's because of an option in Windows Live Messenger, which allows you to use the same username across any WLM client (WLM is the new name for MSN in case you didn't know).

All Linux clients will do exactly the same as pidgin is doing (I'd know, I've used both the suggested clients ;))

---

### Post by xsabrewulf on 2008-07-17
Yea i know its Windows Live Messenger. just still call it MSN MESSENGER


That really sucks.

So nothing will fix that eh

---

### Post by whitethorn on 2008-07-17
You could also try using Galaxium, right now it only works for msn with yahoo contacts but it's being developed.  

here's the homepage

[http://code.google.com/p/galaxium/](http://code.google.com/p/galaxium/)

they have a couple screenshots up.

---

### Post by Raistlin82 on 2008-07-17
Galaxium looks sweet, thinking I may have to try that one out :)

---

### Post by burty89 on 2008-07-18
> **Joeb454 said:**
> All Linux clients will do exactly the same as pidgin is doing (I'd know, I've used both the suggested clients ;))

Incorrect :) Galaxium will make use of the roaming profile to share data across machines & with WLM.

---

### Post by new2gutsy on 2008-07-21
Looks like a sweet app,however this is what I get when I try to install it 

joey@joey-Ubuntu:~$ sudo apt-get install galaxium
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package galaxium


I also tried Emesene but just got a white screen no contacts

---

### Post by whitethorn on 2008-07-21
> **new2gutsy said:**
> Looks like a sweet app,however this is what I get when I try to install it 

joey@joey-Ubuntu:~$ sudo apt-get install galaxium
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package galaxium


I also tried Emesene but just got a white screen no contacts

Hi to be able to install galaxium you need to 


Add the following line to /etc/apt/sources.list: 

gksudo gedit /etc/apt/sources.list

go to the bottom of the file and add the two lines

deb [http://ppa.launchpad.net/galaxium/ubuntu](http://ppa.launchpad.net/galaxium/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/galaxium/ubuntu](http://ppa.launchpad.net/galaxium/ubuntu) hardy main

Type the following commands in a terminal: 
apt-get update
apt-get install galaxium

It's not in the official repositories, but you can add this repository to your list and you will get updates to the program.

---

### Post by Joeb454 on 2008-07-21
> **burty89 said:**
> Incorrect :) Galaxium will make use of the roaming profile to share data across machines & with WLM.

I never knew it existed, so I stand (sit?) corrected

---

