---
title: "Ubuntu Vs Windows - Security"
date: 2009-05-16
forum: Recurring Discussions
---

### Post by GeordieJedi on 2009-05-16
Hi all, hope your doing well.


Ive done a bit a research on the forum & google.

My question is this =

How secure is a fully patched Ubuntu Vs a fully patched Windows XP or Vista?
(In Windows im also talking about running a firewall/anti-virus/anti-spyware 
+ whatever bloody else you have to run...).

I'd like to buy stuff online (using https of course). But Ive always previously done that,
using Windows XP/Vista using something like Kaspersky internet suite
and all the usual anti-malware apps.

Am I safe using Ubuntu to buy stuff online?

Any thoughts?


As always, thanks in advance for any help.

---

### Post by lisati on 2009-05-16
Have a look here: [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by whoop on 2009-05-16
I think that a ubuntu box is always a little bit safer. It has no services running by default. And most vulnerabilities target windows specifically. So ubuntu is safe(r), even without antivirus software.

---

### Post by goldblattster on 2009-05-16
I always believe ubuntu and linux and linux in general is safer. A note from me to you is that if you install ubuntu, you can take advantage of Linux's powerful firewall, iptables. To configure iptables, you can use the application firestarter. Install firestarter by typing
```
sudo apt-get install firestarter
```
into a terminal window, and hitting enter. To use firestarter to configure iptables, select firestarter in the System>Administration menu or type
```
sudo firestarter
```
into the terminal.

---

### Post by XCan on 2009-05-16
Since you are interested in purchasing stuff online, I would say Ubuntu is safer. This is due to the reason that there are no worms that might have infected you, installed a trojan and sits around stealing your CC information. You may be running firewall, antivirus and what not under Windows, but remember that there might be exploits for everything you run.

Of course, you could get whacked by a firefox exploit, but since you won't be running it under root/admin, the consequences will be quite light.

---

### Post by GeordieJedi on 2009-05-16
Thanks very much for all the replys.

Its much appreciated! :-D

---

### Post by mojolobo on 2009-05-16
I have been advice to use gufw to configure my firewall , since firestarter in outdated.
My question is it the os or the browser , that is a security threat.

---

### Post by albinootje on 2009-05-16
> **GeordieJedi said:**
>  How secure is a fully patched Ubuntu Vs a fully patched Windows XP or Vista?
(In Windows im also talking about running a firewall/anti-virus/anti-spyware 
+ whatever bloody else you have to run...).


This is a difficult question to answer, since it's a complex issue we're talking about, but let's make a start.

Let's assume that the user behind the keyboard is aware that double-clicking on attachments from unknown senders (or faked senders) is not always the brightest idea to do, especially in MS-Windows. And let's assume that both in Linux and MS-Windows the user will use the latest Firefox web browser, and not MS-IE.

For the rest there's zero day exploits, and since you're talking about MS-Windows XP I recommend you to have a look at this :
[http://secunia.com/advisories/product/22/](http://secunia.com/advisories/product/22/)
> 
Microsoft Windows XP Professional
Unpatched 	13% (30 of 236 Secunia advisories)
Most Critical Unpatched
The most severe unpatched Secunia advisory affecting Microsoft Windows XP Professional, with all vendor patches applied, is rated Moderately critical .

So.. you've decided to work with an OS which still has moderately critical bugs which are not fixed in the OS ..
Compare that with the Secunia advisories for Ubuntu.
E.g. Ubuntu Hardy : [http://secunia.com/advisories/product/18611/](http://secunia.com/advisories/product/18611/)

And I believe that by default a MS-Windows user is more in danger because MS-Windows will run any .exe .bat .scr etc. for you in various applications, while in  Linux (apart from the annoying dot desktop files in KDE en Gnome) a file has to have the executable bit before it can be run (or launched with "sh ./" etc.)

And the amount of malware (viruses,worms,trojans,spyware) for MS-Windows is in the 10 thousands and only increasing, while for Linux there are still no active viruses in the wild, let alone Linux botnets which are sending out spam or attacking websites or try to crack passwords etc.

---

### Post by albinootje on 2009-05-16
And apart from this I'm a happy Firefox addon Noscript user since quite a while. 
I'd like to recommend it, even though it is a bit of a hassle to get used to at first whenever you visit sites which rely on javascript.

---

### Post by rpwdh on 2009-05-16
> **goldblattster said:**
> I always believe ubuntu and linux and linux in general is safer. A note from me to you is that if you install ubuntu, you can take advantage of Linux's powerful firewall, iptables. To configure iptables, you can use the application firestarter. Install firestarter by typing
```
sudo apt-get firestarter
```
into a terminal window, and hitting enter. To use firestarter to configure iptables, select firestarter in the System>Administration menu or type
```
sudo firestarter
```
into the terminal.


What about Gufw?

---

### Post by jakupl on 2009-05-16
> **goldblattster said:**
> you can use the application firestarter. Install firestarter by typing
```
sudo apt-get firestarter
```


that should be
```
sudo apt-get install firestarter
```

---

### Post by goldblattster on 2009-05-16
> **rpwdh said:**
> What about Gufw?


Well, you could use gufw, but then again you could also use guarddog.
I find your avatar offensive.

---

### Post by rpwdh on 2009-05-16
> **goldblattster said:**
> Well, you could use gufw, but then again you could also use guarddog.
I find your avatar offensive.

Actually I was wondering what the difference was between them.

Sorry that you find it offensive, she's actually not nude. It's a bodypaint suit.

---

### Post by The Cog on 2009-05-16
Talking specifically about web browsing, although Ubuntu is probably safer than Windows, you can't assume it is completely safe. Many shopping sites reqire you to enable javascript. As soon as you start downloading and running code you are taking risks. There are a few cross-platform javascript exploits out there. Keep your browser fully patched. The safest approach if you're really paranoid is to do your browsing from a live CD. Next best might be browsing from a VM where you can restore a snapshot after doing your browsing.

---

### Post by lisati on 2009-05-16
> **rpwdh said:**
> Sorry that you find it offensive, she's actually not nude. It's a bodypaint suit.
I see what you mean, but Mrs Lisati might not want me looking too closely, and she's hovering around tending to some housework.

---

### Post by rpwdh on 2009-05-16
> **lisati said:**
> I see what you mean, but Mrs Lisati might not want me looking too closely, and she's hovering around tending to some housework.

It's Linux themed... those are PENGUINS... with "outie" belly buttons.

Edit: Google "Linux Body Paint"

---

### Post by paradigm2 on 2009-05-16
Ubuntu is generally far safer on average.  However, to be sure one must have mastery of their tools, Jedi. ;)  The more you learn, the better off your security.

---

### Post by whoop on 2009-05-16
> **rpwdh said:**
> Actually I was wondering what the difference was between them.

Sorry that you find it offensive, she's actually not nude. It's a bodypaint suit.
I don't find women offensive at all :p Not in general at least...

---

### Post by rpwdh on 2009-05-16
> **whoop said:**
> I don't find women offensive at all :p Not in general at least...

I concur! 8)

---

### Post by albinootje on 2009-05-16
> **whoop said:**
> I don't find women offensive at all :p Not in general at least...

This planet is still (sadly) a men's world, and also homophobia is still widespread 
(Or would a bodypainted nude looking guy as avatar picture not offend you ?).

I have worked with several female computer geek friends in the past, and I remember a sad story told by one of them, about her joining some Linux mailinglist and asking a question, and getting an awful sexist response, which is all about the old fashioned stereotype idea that a woman is a toy, an object, only made for the lust excitement of a man.

Which makes me think that it makes sense, as a woman, to pretend to be a guy on the internet among geeks.

---

### Post by whoop on 2009-05-16
> **albinootje said:**
> 
(Or would a bodypainted nude looking guy as avatar picture not offend you ?).

No it wouldn't
> **albinootje said:**
> 
I have worked with several female computer geek friends in the past, and I remember a sad story told by one of them, about her joining some Linux mailinglist and asking a question, and getting an awful sexist response, which is all about the old fashioned stereotype idea that a woman is a toy, an object, only made for the lust excitement of a man.

That's really sad...
> **albinootje said:**
> 
Which makes me think that it makes sense, as a woman, to pretend to be a guy on the internet among geeks.
I think I wouldn't do that if I where a woman, but I can't be sure of course.

---

### Post by rpwdh on 2009-05-16
> **albinootje said:**
> This planet is still (sadly) a men's world, and also homophobia is still widespread 
(Or would a bodypainted nude looking guy as avatar picture not offend you ?).

I have worked with several female computer geek friends in the past, and I remember a sad story told by one of them, about her joining some Linux mailinglist and asking a question, and getting an awful sexist response, which is all about the old fashioned stereotype idea that a woman is a toy, an object, only made for the lust excitement of a man.

Which makes me think that it makes sense, as a woman, to pretend to be a guy on the internet among geeks.

So what does that say about the Woman that lets herself be painted? What about the Woman that enjoys being dominated? What about the Woman who poses for a nude painting?

Don't lay it all at the feet of men. Women are all for exploiting the fact that they are Women... when it suits them.

I think this is being taken way too seriously.

---

