---
title: "help please"
date: 2008-07-10
forum: New to Ubuntu
---

### Post by fishhuntercraig on 2008-07-10
hope i'm doing this right - i cannot seem to get connected - and it is further insult to injury that i'm having to use my partners vista machine to post this plea :-)

i've been using the ubuntu linux for non geeks book - seems good to this point - where it became a tad thin for the wireless connecting

the non geek is the key phrase here - i don't seem to understand what i'm suppose to enter where in the network admin boxes - i can see by the network information on this vista machine that the connection is auto detect and assign - but i'm getting nowhere

other than frustrated :-)

thanks

---

### Post by DGortze380 on 2008-07-10
what type of computer is Ubuntu installed on? What model wireless card do you have? You more than likely need to download and install a driver for it, then you can set up DHCP and you should be up and running.  Post that information here and we can try and help with any questions.

---

### Post by tjwoosta on 2008-07-10
yea, like DGortze380 said, we definatly need more information 


also please post the output of theese two commands 

```
lspci
```
```
lsusb
```

---

### Post by fishhuntercraig on 2008-07-10
> **DGortze380 said:**
> what type of computer is Ubuntu installed on? What model wireless card do you have? You more than likely need to download and install a driver for it, then you can set up DHCP and you should be up and running.  Post that information here and we can try and help with any questions.


thanks a bunch in advance - what i have is a hp pavillion dv4000 laptop - intel wireless 2200bg rev 5 and realteck rtl-8139/8139c/8139c+ rev 10

in regards to the lspci command - i 'm not sure how to get that information from my computer to this computer without typing it all - which i can do if it will help - or you can tell me what i'm lookng for and i can type that portion

for the lsusb command it was the same for each of the 1-5 Bus  Device 001: ID 0000:0000

again thanks
craig

---

### Post by tjwoosta on 2008-07-10
well..

i guess you dont really need to post the commands if you know exactly what hardware you have

for wireless look here
[http://ubuntuforums.org/showthread.php?t=448388]("http://ubuntuforums.org/showthread.php?t=448388")

---

### Post by fishhuntercraig on 2008-07-11
thanks for the info - not working yet - but here is more info as it is

from the link posted - 

step 1. result

lo no wireless extensions
eth0 no wireless extensions
eth1 radio off ESSID:""
Mode:Managed Channel:0 Access Point: Not-Associated
Bit Rate 0 kb/s Tx-Power=off Sensitivity=8/0
Retry Limit:7 RTS thr:off
Power Management:off
Link Quality:0 Signal level:0 Noise level:0
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

step 2. result

eth1 No scan results

so at this point it seems to tell me it is a router issue or some such thing - which in my case is telling me nothing

do i need to enter in dns values and domain name stuff on the Network Settings menu or someplce else

again thanks for your patience and assistance

craig

---

### Post by fishhuntercraig on 2008-07-12
since the laptop is a couple years old would i be better off getting a new pcmcia wireless card

and if so what would be the choice to be the most happy in this environment

again thanks

craig

---

### Post by hyper_ch on 2008-07-12
it is adviced to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

a generic topic title like "noob here" or "need help" does not help at all. As you may have notices, just about everyone posting in here has some kind of a problem or issue or question ;) 

and it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

---

