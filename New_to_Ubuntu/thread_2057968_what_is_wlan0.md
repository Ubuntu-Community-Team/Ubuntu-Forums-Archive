---
title: "what is wlan0?"
date: 2012-09-14
forum: New to Ubuntu
---

### Post by erfan mehraban on 2012-09-14
hi!
what is wlan0 and mon0!
because i sea it in fern-wifi-cracker (:lolflag:)that is say : wlan0 is not injection or proximity is low?
i saerch it and the answer was
Two things could cause this situation:
1. Distance from the Access point
2. Driver for the card does not support injection.
[link]("http://code.google.com/p/fern-wifi-cracker/issues/detail?id=17")
but i cant find another card!
what can i do?
thanx ):P

---

### Post by dodo3773 on 2012-09-14
wlan0 is your wifi card. wlan is wireless lan and 0 is the number of your card. The count starts from 0 and goes up (0,1,2,3,etc..). So if you had 2 wifi cards plugged in they would be represented by wlan0 and wlan1. There are some other naming schemes for wireless lan but that should explain it a little. mon0 is the same card (wlan0) in monitor mode. Once you put wlan0 in monitor mode it will be read as mon0 and wlan0. Both device names will exist. Learn to use aircrack first and these things will probably make more sense to you.

---

### Post by critin on 2012-09-14
> fern-wifi-cracker Isn't this a password breaker to siphon off other peoples bandwidth?
What else is it used for?

Just curious if the uses are ethical?

---

### Post by dodo3773 on 2012-09-14
> **critin said:**
> Isn't this a password breaker to siphon off other peoples bandwidth?
What else is it used for?

Just curious if the uses are ethical?

It is a penetration tool for wireless networks more or less. At a glance it looks like a huge front end for aircrack. Whether it is being used for ethical or non-ethical purposes is entirely on the individual. To assume that it is being used only to "syphon off of other peoples bandwidth" is a gross assumption.

---

### Post by critin on 2012-09-14
> **dodo3773 said:**
> It is a penetration tool for wireless networks more or less. At a glance it looks like a huge front end for aircrack. Whether it is being used for ethical or non-ethical purposes is entirely on the individual. To assume that it is being used only to "syphon off of other peoples bandwidth" is a gross assumption.

Thanks.  I'm not assuming anything, nor am I judging.  I'm asking.  It is a password breaker, isn't it?  It penetrates wireless networks by those who can't use the internet because they're locked out?  more or less.  

What else is it used for?   

The forums aren't used to get help with non-ethical purposes, on the individual or not.     If a person needs to break a password or penetrate a network, it should be** his** password and **his **network.  There are easier ways to get to those--isn't there?

---

### Post by dodo3773 on 2012-09-14
> **critin said:**
> Thanks.  I'm not assuming anything, nor am I judging.  I'm asking.  It is a password breaker, isn't it?  It penetrates wireless networks by those who can't use the internet because they're locked out?  more or less.  

What else is it used for?   

The forums aren't used to get help to use unethical tools.   If a person needs to break a password or penetrate a network, it should be** his** password and **his **network.  There are easier ways to get to those--isn't there?

It is to simulate an attack on your own network (hopefully). Your attacker will not have those credentials or direct physical access to your network. I understand your concern though (since I have almost never used this tool to do anything ethical ever).

---

### Post by critin on 2012-09-14
> **dodo3773 said:**
> It is to simulate an attack on your own network (hopefully). Your attacker will not have those credentials or direct physical access to your network. I understand your concern though (since I have almost never used this tool to do anything ethical ever).

Thanks, dodo.  
I get what you're saying, but I still don't understand its purpose.  'simulate an attack?  To add credentials to better protect yourself--maybe?  Never mind, I'm not tech-minded.  You explained it fine. 

 I hope you didn't mean this though--a typo?  Guilt complex?  Truth?

> (since I have almost never used this tool to do anything ethical ever)And if you did mean it, that's what I'm concerned about.  Let them learn how to do this somewhere else.

---

### Post by erfan mehraban on 2012-09-15
thank! foe every one!

---

### Post by dodo3773 on 2012-09-15
> **erfan mehraban said:**
> thank! foe every one!

Your welcome. I hope the explanation made sense and now you understand what wlan0 is. Please be sure to mark this thread as solved if you feel it has been. If you are not sure how see this:

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

Take care. 

 

@critin

The original question was something very simple regardless of the tool being used. I don't think we will have to continue this thread any further. To answer your questions directly though - yes, maybe, no, no, yes. That being said I am sure it is a valuable tool in a professional environment.

---

