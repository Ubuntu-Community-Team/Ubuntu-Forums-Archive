---
title: "hackers from China"
date: 2008-08-20
forum: New to Ubuntu
---

### Post by nynoah on 2008-08-20
Not sure where to post this or to whome.

But I just installed Mobloquer and I am getting TONS of hits from China.  Anyone else get tons of intrusions from China.  How can I stop them?  What if anything can I do about it?  Is there any possibility that somehow any of our Linux programs have been compromised to send out information?  I don't mean to sound paranoid, but stuff like this does happen.

---

### Post by sdennie on 2008-08-20
It's not uncommon.  It's not that someone is out to hack your box, it's that people have machines that are constantly scanning looking for boxes to take over.  If you are worried or just interested, see this thread: [http://ubuntuforums.org/showthread.php?t=765421](http://ubuntuforums.org/showthread.php?t=765421)

---

### Post by nynoah on 2008-08-20
Thanks for the link.  Is there any info or tool that will help me figure out who is trying to get in.  I know people can scramble or use other computers to mask.  How do I figure out stuff like that?

---

### Post by iaculallad on 2008-08-20
Additional:

You could configure your moblock to block the IP specific number range of China.

---

### Post by sdennie on 2008-08-20
Honestly, if you have open ports (especially on the default port numbers), you will get that kind of spam in your logs constantly.  It doesn't matter what you do.  The easiest defense is to just have good passwords on your accounts.

---

### Post by nynoah on 2008-08-20
Still are there any tutorials that you know of that might help me out.  I am trying to figure out how to trace these people.  Being in the Ubuntu world has taught me a lot so far.  I am kinda itchin for more knowledge.

---

### Post by Nepherte on 2008-08-21
I don't really see the point of tracing them. They're most likely not even aware their computer is scanning others since they're most likely zombie bots.

---

### Post by nynoah on 2008-08-21
Yes they could be, but how do I trace them?

---

### Post by iaculallad on 2008-08-21
> **nynoah said:**
> Yes they could be, but how do I trace them?

Try visiting this [site]("http://www.ip-adress.com/ipaddresstolocation/") and input the public IP address you want to trace.

---

### Post by DGortze380 on 2008-08-21
> **nynoah said:**
> Yes they could be, but how do I trace them?

There's no simple answer to that question. There are people that spend years tracking things like this for security companies and gov'ts. If you're interested in learning about it, start learning about anythign and everything to do with networking, then you'll be able to start to understand why no one can just say, "Trace them with this program."

---

### Post by jre on 2008-08-21
Don't worry about any IP shown by MoBlock. Why? Because MoBlock already blocked it! Even better it DROPped it so the other doesn't get noticed that there was an actice block.
What you might worry about are possible attacks/scans/... by IPs which are not blocked by MoBlock. But then (as already others said) I would suggest to put efforts in hardening your system security. Tracing these IPs might be interesting and funny but not of any real use.

EDIT: Please also note that in most cases MoBlock will check traffic before the rest of your software firewall does so. (It is suggested to have the MoBlock iptables rules at the head of the iptables chains.) So a packet blocked by MoBlock *might* have been blocked by your firewall, too.

Greets
jre

---

### Post by jfbays on 2008-08-21
Would turning on the Firewall help prevent this sort of thing?  I have gotten the idea, from other posts, that using a Firewall on a Linux box is not really important.

---

### Post by jerome1232 on 2008-08-21
I don't know if it does anything but every once in awhile I go through my denyhosts log (it auto blocks ips that fail 3 times logging into ssh) then grep my logs for their ip, do a whois on their ip which gives me an abuse report email. 

Then I send an email containing my log of the attacks. Maybe it does something maybe it doesn't I don't know. Gives me something to do in the dull hours.


edit: As for a firewall the only reason I use one is becuase I want certain services open only to my lan, the firewall blocks access to those ports from every ip but ones on my lan.

---

### Post by Nepherte on 2008-08-21
> **jfbays said:**
> Would turning on the Firewall help prevent this sort of thing?  I have gotten the idea, from other posts, that using a Firewall on a Linux box is not really important.
There already runs a firewall, called iptables, by default. The default policy is to accept, but as long as you don't have any services, such as a ssh daemon, running, there's no reason to worry.

---

### Post by jre on 2008-08-22
> **Nepherte said:**
> There already runs a firewall, called iptables, by default.
and MoBlock is part of this firewall.

---

### Post by Nepherte on 2008-08-22
> **jre said:**
> and MoBlock is part of this firewall.
Aye, I wasn't really referring to moblock but rather to the sentence I quoted.

---

