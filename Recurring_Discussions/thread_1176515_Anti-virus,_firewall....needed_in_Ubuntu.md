---
title: "Anti-virus, firewall....needed in Ubuntu?"
date: 2009-06-02
forum: Recurring Discussions
---

### Post by scarmpls on 2009-06-02
I am currently running version 8.02 desktop Hardy Heron.  I just got connected to the internet, I am new to forums, Ubuntu and Linux.  I hoped that my internet experience would be smoother (less interruptions for "upgrades", new releases, _[COLOR=Red]security threats[/COLOR]_, etc) than my experience with XP. 

I am downloading version 9.04 desktop right now.

My concern about anti-virus software, firewall, anti-spyware software is simply that it may slow system performance down to below my personal tolerance.  My internet connection is a 7Mb/s fiber optic DSL connection that's directly connected via ethernet, and seems to be moving quite nicely.

I figure someone will reply to this post with a simple, "Yes.  All the stuff you bought for your XP OS is still necessary, but you can get it for free, or cheaper.  Here's where to get  it..."  Which would be fine.  

Any suggestions, comments are welcomed.  Thanks.

---

### Post by Mirge on 2009-06-02
IMO, for a desktop system you don't really need any of the 3. Though you actually already have a "firewall" installed -- iptables. It's used to specify routing/traffic rules.

---

### Post by scarmpls on 2009-06-02
Thanks for your reply.  What does IMO mean?

---

### Post by Psycho.mario on 2009-06-02
IMO=**I**n **M**y **O**pinion

---

### Post by scarmpls on 2009-06-02
I got it, "In my opinion".  Or one could type, "IMHO" for, "in my humble opinion" too if one was so inclined.

---

### Post by Irishe on 2009-06-02
IMO = in My Opinion....:)
 
opps, i'm too Slow...lol

---

### Post by cariboo on 2009-06-02
Have a look at this [thread=510812]thread[/thread], if you are concerned about security.

---

### Post by Soul-Sing on 2009-06-02
iptables is installed, not active though.

```
sudo iptables -L
```

you need a frontend/gui to manage iptables, or use the terminal.
i'am using g(ufw) as frontend/gui.

ubuntu uses a "zero open port policy".

---

### Post by Graham1 on 2009-06-02
Sorry to hijack this thread but my question is kind of related :). 

I always thought that there was no firewall included with Ubuntu (well, installed but not enabled). Is that incorrect? 

I'm referring to UFW or is that just a frontend to IP Tables? Then you've got GUFW. I'm confused :confused:.

:)

---

### Post by Graham1 on 2009-06-02
> **leoquant said:**
> ```
sudo iptables -L
```

Hi leoquant

Is that the same as sudo ufw enable?

:)

---

### Post by Soul-Sing on 2009-06-02
> **Graham1 said:**
> Hi leoquant

Is that the same as sudo ufw enable?

:)

No. It shows you that by default iptables = not active.(empty/no rules)

---

### Post by scarmpls on 2009-06-02
Thanks for the link to the thread to the spool of the kernel of the agenda about security, cariboo907!

It really is a quite extensive, but not too technical overview and how-to on the topic of security.

Good stuff.  Thanks again.

---

### Post by Wiebelhaus on 2009-06-02
Better be safe than sorry , Plus we have the best offering for free with registration , you can scan your /home once a week just to make sure nothing nasty is hanging around , check my sig.

---

### Post by Mirge on 2009-06-02
[http://www.pcworld.com/article/126240/free_agent_linux_firewalls_and_antivirusneeded_or_not.html](http://www.pcworld.com/article/126240/free_agent_linux_firewalls_and_antivirusneeded_or_not.html)

Interesting read... though it is aging.

---

### Post by Viva on 2009-06-03
None of the existing antivirus software check for the so called security threats in linux. They only check for windows viruses, so install it if you want to scan the windows drives for viruses installed while running windows. You don't really beed an antivirus for ubuntu.

---

