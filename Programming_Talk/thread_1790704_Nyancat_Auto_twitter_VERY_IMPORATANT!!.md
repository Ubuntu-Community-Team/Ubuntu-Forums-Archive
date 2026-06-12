---
title: "Nyancat Auto twitter VERY IMPORATANT!!"
date: 2011-06-25
forum: Programming Talk
---

### Post by conradin on 2011-06-25
Lol, Ok, maybe not very important. 
I "wrote" an Imacro script which I can have loop up to 10000 times, which tweets my nyan-cat runtime every hour (or what ever).
```

VERSION BUILD=7220523 RECORDER=FX
TAB T=1
TAG POS=1 TYPE=DIV ATTR=TXT:Tweet<SP>Your<SP>Score
TAB T=2
FRAME F=0
TAG POS=1 TYPE=INPUT:SUBMIT FORM=ID:update-form ATTR=VALUE:Tweet
TAB T=2
TAB CLOSE
WAIT SECONDS=3600
TAB T=1

``` 

So, that works fine when the nyan-cat page has been loaded. What I want to do is have it loop every hour to infinity. What I tried to do in a bash script, was to load the nyan cat page and the macro. but when I do the macro only comes up as text. ```

#!/bin/bash
firefox 'http://nyan.cat/' '/home/user/iMacros/Macros/NyanCAT!.iim'
read

```
when I include a bit to have the macro pre-load the web-page, the page refreshes, and kills my high score. 

Anyone have some ideas how I can indefinitely run / tweet my nyan-cat scores?

---

### Post by Zugzwang on 2011-06-28
Look [here]("http://wiki.imacros.net/iMacros_for_Firefox"), Section "Command Line Support" - appearently you will need to start firefox first, wait a bit and then direct firefox to your macro. Then your bash script might work.

---

### Post by SoFl W on 2011-06-28
You gave me an idea, for which I have no use for at this time but it would be fun to see if I could get it to work.  
I could make a twitter account, set it to private, and then have my computer tweet my IP address every so often.  If I ever needed to do a remote connection, I would have the IP address.

(I have several variations of this idea as it is, but just to do it for fun)

---

### Post by scu-ba-de-buntu on 2011-06-28
...

---

### Post by StartedTheFire on 2011-06-28
This has to be the most ridiculous subject line I've ever seen.

---

### Post by Barrucadu on 2011-06-28
> **SoFl W said:**
> You gave me an idea, for which I have no use for at this time but it would be fun to see if I could get it to work.  
I could make a twitter account, set it to private, and then have my computer tweet my IP address every so often.  If I ever needed to do a remote connection, I would have the IP address.

(I have several variations of this idea as it is, but just to do it for fun)

The normal solution is to use a dynamic DNS service.

---

### Post by Pierrick584 on 2011-06-28
But, we are on the programming talk forum of a linux distribution, who here is actualy normal?

---

### Post by conradin on 2011-07-01
> **Zugzwang said:**
> Look [here]("http://wiki.imacros.net/iMacros_for_Firefox"), Section "Command Line Support" - appearently you will need to start firefox first, wait a bit and then direct firefox to your macro. Then your bash script might work.

I Think thats how I'm going to do it. Just exhausted right now. 

I'm glad when ever my non-sense can produce usefulness. Who would have thought anything useful would ever come out of Twitter?

---

### Post by scu-ba-de-buntu on 2011-07-06
> **conradin said:**
> I'm glad when ever my non-sense can produce usefulness. Who would have thought anything useful would ever come out of Twitter?

The good is from Nyancat, the breakfast snack cat, she who leaves rainbows in her wake and nyans amongst the interwebz' stars. Twitter's just there by association.

---

### Post by pafoo on 2011-07-07
> **SoFl W said:**
> You gave me an idea, for which I have no use for at this time but it would be fun to see if I could get it to work.  
I could make a twitter account, set it to private, and then have my computer tweet my IP address every so often.  If I ever needed to do a remote connection, I would have the IP address.

(I have several variations of this idea as it is, but just to do it for fun)

Why in the world would you keep tweeting the same ip address over and over. Why not just save the ip to your VNC/RDP client or in a text file... I'm lost.

---

### Post by scu-ba-de-buntu on 2011-07-07
> **pafoo said:**
> Why in the world would you keep tweeting the same ip address over and over. Why not just save the ip to your VNC/RDP client or in a text file... I'm lost.

This is off topic, pafoo, but I want to clairify this for you.

As stated earlier, there are (some would consider better) alternatives to logging IP changes, but the reason for wanting a system would be dynamic IP assignment. Some ISPs dynamically allocate IPs, This is very common with dial-up users and some internal organizations which act as ISPs {some colleges}. If you had a server on such a networked system, you would need to keep all references to the server current. Usually this is done by running a program of some sort which reports changes to another server - usually some dynamic dns service. Then the references (website, nameserver info etc) are set to point to the dns server which then points to (the current location of) your server.

---

