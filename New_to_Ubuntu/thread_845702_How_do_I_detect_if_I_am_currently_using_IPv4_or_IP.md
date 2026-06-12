---
title: "How do I detect if I am currently using IPv4 or IPv6?"
date: 2008-06-30
forum: New to Ubuntu
---

### Post by durundal on 2008-06-30
Is there a terminal command I can run that would show me this information?

---

### Post by LuisGMarine on 2008-06-30
Open up a terminal and type this command into it:

```
lsmod | grep ipv6
```

Output should be something like:

```
ipv6                  411425  18
```

Obiviously if you type that in , and you got an output that means you are running IPV6, if you got nothing back try substituting the ipv6 for ipv4 and if that spits something out you know you have IPV4.

I'm not sure but if you have 8.04 it might be defaulted to IPV6, I don't know what it is or how it works so I really don't know further than what I just gave you.

---

### Post by durundal on 2008-06-30
Hmm, neither of them seem to output anything.

Edit: I'm pretty sure I disabled IPv6 since ifconfig no longer gives my ethernet card an inet6 address.

---

### Post by LuisGMarine on 2008-06-30
Try each command, that's not right if none of them are showing up.  You are telling me that you ran both of these commands and none of them output anything?
```

lsmod | grep ipv6
```

and

```
lsmod | grep ipv4
```

it makes no sense. I thought computers needed to have either or to be able to access the internet.

---

### Post by durundal on 2008-06-30
Nope, neither of them output anything.  

Maybe I shouldn't have put "all variants" in the title since I am using Xubuntu, if that makes any difference at all.

---

### Post by drs305 on 2008-06-30
I don't get a response from either command in ubuntu as well (64-bit hardy, ipv6 disabled).

---

### Post by bab1 on 2008-06-30
IPV4 does not show up in the command lsmod.  That's normal.  I jsut checked mine.  if you do not run IPv6 the the lsmod | grep IPv6 will reveal nothing, and be correct.

The ifconfig command is the best command to tell what your NIC is running.

Try ping "yourhostname" and you will see the IP address you are using.

---

### Post by durundal on 2008-06-30
So basically if ifconfig gives me an inet6 address I am using IPv6 and if it doesn't then I am using IPv4?

Maybe I should make another thread about this but the reason I want to disable IPv6 is because of privacy concerns.

Some DJ on the radio was talking about how the switch from IPv4 to IPv6 would stop all the "evil hackers".  Now if IPv6 can identify the most evilest of hackers then it can't be too good for my privacy, right?

Anyways, upon googling I found an apparent bug in ubuntu involving this privacy issue:

[https://bugs.launchpad.net/ubuntu/+source/procps/+bug/176125](https://bugs.launchpad.net/ubuntu/+source/procps/+bug/176125)

Unfortunately the fixes didn't work for me.  Is this something I should even concern myself with?

---

### Post by Nexusx6 on 2008-06-30
> 
Some DJ on the radio was talking about how the switch from IPv4 to IPv6 would stop all the "evil hackers". Now if IPv6 can identify the most evilest of hackers then it can't be too good for my privacy, right?

Its just ignorant jabber - you can safely ignore it. This is probably one of those situations of a game of Operator gone really bad: "I heard from a friend, of a friend, who's brothers' cousin's aunt on his mothers' side that..."

The IPv6 protocols are for 3 major purposes; Address space, simplifying addresses, and simplifying renumbering. There's nothing about them that inherently gives them black magic powers to stop hackers dead in their tracks - its merely a way more efficient way to assign IP's we've all be using. I've heard that there are some protocols that can assist in authentication which can make internet related things safer, but again, its no more an privacy issue than your current IP address.

---

### Post by LuisGMarine on 2008-06-30
Hackers?  That's what me and you are.  I thought ...

Hackers = people who hack files, like change programming code.  Sort of what all Linux users do to some extend

Crackers = the bad people, ones who do malicious things with a keyboard.  Like beat old ladies at a 7-11

---

### Post by nowshining on 2008-07-01
lsmod | grep ipv6 - gives me nothing - then again I run my own custom kernel from kernel.org with it disabled.

however lsmod | grep ipv4 -

```
 
nf_conntrack_ipv4       6700  19 iptable_nat
nf_conntrack           27981  6 iptable_nat,nf_nat,xt_state,xt_conntrack,nf_conntrack_ftp,nf_conntrack_ipv4

```

i'm running GutsyGibbon7.10+ by the way w/2.6.24.7_kernel

---

### Post by fadman_12 on 2011-02-01
If you run "ifconfig" on a linux system, it will give you both an IPv4 and IPv6 address because it will automatically have an IPv6 address configured even if not in use. It is automatically created by your MAC address of your NIC. So you will be pulling an IPv6 address even if you aren't using it and using IPv4

---

### Post by sydbat on 2011-02-01
> **fadman_12 said:**
> If you run "ifconfig" on a linux system, it will give you both an IPv4 and IPv6 address because it will automatically have an IPv6 address configured even if not in use. It is automatically created by your MAC address of your NIC. So you will be pulling an IPv6 address even if you aren't using it and using IPv4WOW!! Reviving a 2 1/2 year old thread. How threadcromantic of you...

---

### Post by Elfy on 2011-02-01
Closed - back to sleep.

---

### Post by frodon on 2011-02-01
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=182255&stc=1&d=1296333044[/IMG]

---

### Post by Guilden_NL on 2011-02-01
I think this is relevant given the media reports about IPv6.  A lot of new users will be interested.

---

### Post by SoFl W on 2011-02-01
If anybody wants to know...

[http://test-ipv6.com/](http://test-ipv6.com/)

---

### Post by Guilden_NL on 2011-02-01
Thanks for that SoFI W!   I deal with IPv6 all day in my Architect job, but never knew of this site.  It's a nice place to send non-networking gurus for a quick check.

---

### Post by bodhi.zazen on 2011-02-01
And with that this thread is closed.

---

