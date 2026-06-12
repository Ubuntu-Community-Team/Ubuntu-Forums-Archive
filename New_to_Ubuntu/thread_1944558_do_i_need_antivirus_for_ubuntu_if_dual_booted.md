---
title: "do i need antivirus for ubuntu if dual booted"
date: 2012-03-21
forum: New to Ubuntu
---

### Post by chestycuogth on 2012-03-21
hello, this is my first post in the forum.
i would like to know if i should install antivirus software on Ubuntu as well as the second OS on my pc, windows vista.
thanks

---

### Post by Paddy Landau on 2012-03-21
This question has been asked many times before.

No, you don't need antivirus on your Ubuntu, unless you frequently forward attachments on untrusted emails to Windows users.

---

### Post by HiImTye on 2012-03-21
it's good to run ClamAV on any files you share with your windows PCs or dual-boots. avoid using it on the 'entire system' as some people report issues with that. you would initiate a scan like so, from my clamscan script:
```
#!/bin/bash
clamscan -r -l scan.log /storage/Videos /storage/Music /storage/Pictures /storage/Windows
exit $?
```if you don't have folders that you share with both or windows-based PCs (or wine programs) then it's not really required

---

### Post by Dreamer Fithp Apprentice on 2012-03-21
My answer would be : Maybe, depending, and it can't hurt. For instance, if you use a VM with windows or a DOS on it and you download stuff to run on the VM with Ubuntu, it would be a real good idea. Of course you can always delete the VM and restore it from a snapshot or backup copy, but maybe you have stuff on the virtual drive that hasn't been backed up yet, like maybe something you did with a Windows ap that you put days of work into and hadn't backed it up yet.

And while malware a 'nix is less of a problem than in Windows it has clearly been demonstrated to be possible. Certainly part of the reason for it's being a pretty small problem in 'nixes is technical but some of it is simply that malware writers target Windows a lot more. The main reason they do so, of course, is simply that there are a lot MORE Windows systems to attack. The second reason is probably that it is easier to write malware to attack Windows systems. Thirdly, tell the truth and shame the devil, Windows users are more likely to actually BELIEVE that they are the one millionth visitor to the website or that the deposed Prince of Zodanga needs their help in gaining access to his millions of Euros.  Somewhere, I believe it is here in the forum, someone said something like "you might be a geek if you ran Windows for years with no antivirus and had no problem." Most infections start with doing something dumb and there are more dumb windows users, even as a percentage, and way more in absolute terms. But some of these things may be changing as the number of 'nix users increases and the malware writers might begin to target us more. Paddy that wrote above is a sharp dude, and he may wish to refute part or all of what I'm writing, but for what it is worth, I use bit defender, which worked a lot better for me that clam. I made an entry in my menu to update it and when I want to use it I update it and scan the files I'm interested in.

---

### Post by yetiman64 on 2012-03-21
> **Paddy Landau said:**
> This question has been asked many times before.

No, you don't need antivirus on your Ubuntu, unless you frequently forward attachments on untrusted emails to Windows users.
This OP, not for Ubuntu and even if you run A/v you're only checking for code that affects Windows (and you should have A/v running in Windows anyhow). No viruses are known to exist "in the wild" for Linux.

---

### Post by QIII on 2012-03-21
Yet.

This is asked all the time, so I will say this:

The term "virus" as it is commonly applied is foreign to Linux.  The possibility that something similar, let's call it a "flea", exists is not.

Many Linux users foolishly believe that they are "secure".  They are not.  The idea that Linux is "more secure than Windows" is a persistent myth.  So is the "Windows is a bigger target" myth.

Linux users need to be every bit as vigilent as Windows users and practice the very same security habits as anyone else.

"Antivirus" is a good idea to detect Windows viruses in Windows documents you may pass to your Windows friends.

Safe practices still apply to Linux.

---

### Post by Paddy Landau on 2012-03-22
> **Dreamer Fithp Apprentice said:**
> Paddy that wrote above is a sharp dude, and he may wish to refute part or all of what I'm writing...
Thanks for the nice words! (I'm not really that sharp.) But I will take your invitation for just one point:

> **Dreamer Fithp Apprentice said:**
> And while malware a 'nix is less of a problem than in Windows it has clearly been demonstrated to be possible.
True; but the anti-malware products catch Windows malware, not Linus malware. (As there are no known Linux viruses in the wild, there is no Linux virus for an anti-virus to trap.)

The various comments about being vigilant are as true for Linux as they are for Windows. It is possible to get malware on Linux, but you'd have to be both careless and unlucky. I'm told it's also possible to be caught out with cross-scripting malware in your web browser, but that is something I do not (yet) understand and so cannot comment on.

---

### Post by haqking on 2012-03-22
> **Paddy Landau said:**
> Thanks for the nice words! (I'm not really that sharp.) But I will take your invitation for just one point:


True; but the anti-malware products catch Windows malware, not Linus malware. (As there are no known Linux viruses in the wild, there is no Linux virus for an anti-virus to trap.)

The various comments about being vigilant are as true for Linux as they are for Windows. It is possible to get malware on Linux, but you'd have to be both careless and unlucky. **I'm told it's also possible to be caught out with cross-scripting malware in your web browser, but that is something I do not (yet) understand and so cannot comment on**.

XSS or cross site scripting is when scripts are injected into a web application exploiting the users trust in a site, what makes XSS unique in terms of web based attack vector is that it targets the client and not the server. 

What XSS does can be many things, it can range from entering script directly into a input box where there is bad or no input sanitization/validation such as the following:

input form on webpage

```
<script>alert(XSS hack") </script>
```

of course this wont do much other than pop up a alert box, however this tells us there is a XSS vulnerability as far as input validation is concerned and we could proceed to do more which i probably would receive an infraction for if i posted more ;-)

but basically XSS is when malicious script gets embedded on a web server and is then executed client side to perform a given action.

Cheers

---

### Post by otherethe on 2012-03-22
> **yetiman64 said:**
> This OP, not for Ubuntu and even if you run A/v you're only checking for code that affects Windows (and you should have A/v running in Windows anyhow). No viruses are known to exist "in the wild" for Linux.

This is untrue there are virus for Linux you should do a little more study before you lead people down the wrong road, It's just virus for a Unix based system due to how it's file system is laid out but don't get that confused with no virus at all

---

### Post by Paddy Landau on 2012-03-22
> **otherethe said:**
> This is untrue there are virus for Linux you should do a little more study before you lead people down the wrong road, It's just virus for a Unix based system due to how it's file system is laid out but don't get that confused with no virus at all
I have studied it and found nothing, so I'd really appreciate a couple of links to find out more, please.

---

### Post by otherethe on 2012-03-22
> **Paddy Landau said:**
> I have studied it and found nothing, so I'd really appreciate a couple of links to find out more, please.

[http://en.wikipedia.org/wiki/Linux_malware](http://en.wikipedia.org/wiki/Linux_malware)
[https://www.linux.com/learn/tutorials/284124-myth-busting-is-linux-immune-to-viruses](https://www.linux.com/learn/tutorials/284124-myth-busting-is-linux-immune-to-viruses)

Just a fast search to get you started, it's a myth, Don't listen to all the none sense you hear other people say Linux is no were near what people think it is, but it is very protected hints why so many think it's god like when in fact it's not as godly as everyone is lead to believe I've been using a unix based system for well over 10 years

---

### Post by haqking on 2012-03-22
> **otherethe said:**
> This is untrue there are virus for Linux you should do a little more study before you lead people down the wrong road, It's just virus for a Unix based system due to how it's file system is laid out but don't get that confused with no virus at all

his point was there are no known viruses in the "wild" which is correct as of this time. And also stated in the links you yourself posted

and if there was there is no current AV software for linux which would combat it and so the AV software on Linux point is still moot.

Is linux immune to viruses ? NO, are there any currently in the wild reported ? NO. Could there be ? Yes.  Would current AV software for linux combat it ? NO

Use AV on linux to scan for infection for shared files with windows.

Malware in general however is different

---

### Post by Userspace on 2012-03-22
As far linux security goes I would just recommend enabling the built in firewall there is a graphical user interface tool for this just go into ubuntu software center and search for firewall configuration and download/install it then unlock it so it has root access and set basic block inbound and allow outbound rules and you are good to go

[https://help.ubuntu.com/8.04/serverguide/C/firewall.html](https://help.ubuntu.com/8.04/serverguide/C/firewall.html)

If you really do desire anti virus as well which is optional for linux but can help to stop you from accidentally sending your windows friends a virus their is nod32 for linux it is also especially good if you are using wine since some viruses can actually work in wine

[http://www.eset.com/home/products/](http://www.eset.com/home/products/)

---

### Post by haqking on 2012-03-22
> **Userspace said:**
> As far linux security goes I would just recommend enabling the built in firewall there is a graphical user interface tool for this just go into ubuntu software center and search for firewall configuration and download/install it then unlock it so it has root access and set basic block inbound and allow outbound rules and you are good to go

[https://help.ubuntu.com/8.04/serverguide/C/firewall.html](https://help.ubuntu.com/8.04/serverguide/C/firewall.html)

If you really do desire anti virus as well which is optional for linux but can help to stop you from accidentally sending your windows friends a virus their is nod32 for linux it is also especially good if you are using wine since some viruses can actually work in wine

[http://www.eset.com/home/products/](http://www.eset.com/home/products/)

Setting the basic block and outbound is no different to running no firewall at all really.

To benefit from the firewall features then you should enforce controlled inbound and outbound rules.

You shouldnt just allow outbound, only what is needed to prevent reverse connections and arbitrary port binding from exploited applications.

And a firewall is one of many features required in the security process for any OS.

Read the Ubuntu security wiki link in my sig for more information for security overall and various links to help you configure the firewall, noscript and apparmor amongst others.

Cheers

---

### Post by Paddy Landau on 2012-03-22
@otherethe: Thank you. I have been reading and discovering!

> **haqking said:**
> Setting the basic block and outbound is no different to running no firewall at all really.
I disagree. Run your system with and without the firewall set on [GRC's Shield's Up test]("https://www.grc.com/x/ne.dll?bh0bkyd2"). (Remember to bypass your router or use its DMZ facility  during the tests, otherwise you are testing your router.)

---

### Post by haqking on 2012-03-22
> **Paddy Landau said:**
> @otherethe: Thank you. I have been reading and discovering!


I disagree. Run your system with and without the firewall set on [GRC's Shield's Up test]("https://www.grc.com/x/ne.dll?bh0bkyd2"). (Remember to bypass your router or use its DMZ facility  during the tests, otherwise you are testing your router.)

LOL

no comment on GRC ;-)

and im not saying you dont need a firewall, IMO you do, my point is the basic options are not sufficient, you should configure strict inbound and outbound rules

---

### Post by jerome1232 on 2012-03-22
> **haqking said:**
> LOL

no comment on GRC ;-)

+1, actually +2 for a previous post too.

---

### Post by Ms. Daisy on 2012-03-22
> **haqking said:**
> no comment on GRC ;-)
Good call ;)

---

### Post by haqking on 2012-03-22
for entertainment

[http://attrition.org/errata/charlatan/steve_gibson/](http://attrition.org/errata/charlatan/steve_gibson/)
[http://web.archive.org/web/20070622061544/http://www.grcsucks.com/](http://web.archive.org/web/20070622061544/http://www.grcsucks.com/)

---

### Post by Paddy Landau on 2012-03-22
> **haqking said:**
> ... my point is the basic options are not sufficient, you should configure strict inbound and outbound rules
Point taken. What we need is something *simple* for people to use. I use gufw, but my lack of understanding has led to a basic, not-at-all-strict couple of rules.

[ZoneAlarm]("http://www.zonealarm.com/") makes a Windows firewall that prompts the user each time an application attempts to access the Internet, either incoming or outgoing. It allows the user to accept or reject each connection, and to remember the preference. (As I recall, it comes with a list of pre-approved applications.)

Over time, ZoneAlarm builds up a record of which applications are allowed to do what on the Internet. After the first couple of days, the user is prompted hardly ever, leading to a sensible approach.

Something like that for Linux would be great.

---

### Post by Paddy Landau on 2012-03-22
> **haqking said:**
> for entertainment

[http://attrition.org/errata/charlatan/steve_gibson/](http://attrition.org/errata/charlatan/steve_gibson/)
[http://web.archive.org/web/20070622061544/http://www.grcsucks.com/](http://web.archive.org/web/20070622061544/http://www.grcsucks.com/)
Thank you.

---

### Post by haqking on 2012-03-22
> **Paddy Landau said:**
> Point taken. What we need is something *simple* for people to use. I use gufw, but my lack of understanding has led to a basic, not-at-all-strict couple of rules.

[ZoneAlarm]("http://www.zonealarm.com/") makes a Windows firewall that prompts the user each time an application attempts to access the Internet, either incoming or outgoing. It allows the user to accept or reject each connection, and to remember the preference. (As I recall, it comes with a list of pre-approved applications.)

Over time, ZoneAlarm builds up a record of which applications are allowed to do what on the Internet. After the first couple of days, the user is prompted hardly ever, leading to a sensible approach.

Something like that for Linux would be great.

zonealarm = steve gibson

the trouble with zonealarm and the feature you mention is that it requires the user to understand web traffic and what applications are trusted or not or they just click allow.

If the user understands then it is easy to control anyways ;-)

---

### Post by jerome1232 on 2012-03-22
You mean something like this?

[http://linux-firewall.org/](http://linux-firewall.org/)
and this?
[http://tuxguardian.sourceforge.net/](http://tuxguardian.sourceforge.net/)

note: This is just from a very quick google search, I spent zero time whatsoever figuring out if these application based firewalls are actually good or not.

---

### Post by Paddy Landau on 2012-03-22
> **haqking said:**
> zonealarm = steve gibson
LOL. Oh well, let me see if I can install Microsoft Security Essentials on Wine...

---

### Post by haqking on 2012-03-22
MSE is for malware.

and regardeless of what firewall application you use,you still need to know what is allowed out and in to control it effectively.

Clicking allow cause you "think" an application is trusted is not the same as controlling the flow of trusted traffic ;-)

oh and to clarify i didnt mean steve gibson created zonealarm before anyone chimes in on that

---

### Post by zombifier25 on 2012-03-22
> **Paddy Landau said:**
> LOL. Oh well, let me see if I can install Microsoft Security Essentials on Wine...
It will only able to scan the C: drive, and mapping / to Z: is not a really recommended practice.

---

### Post by Paddy Landau on 2012-03-22
> **zombifier25 said:**
> It will only able to scan the C: drive, and mapping / to Z: is not a really recommended practice.
Sorry, that was meant to be a joke. I wasn't being serious.

---

### Post by haqking on 2012-03-22
> **Paddy Landau said:**
> Sorry, that was meant to be a joke. I wasn't being serious.

you missed the </sarcasm> tag at the end of your post ;-)

---

### Post by Ms. Daisy on 2012-03-22
> **Paddy Landau said:**
> Sorry, that was meant to be a joke. I wasn't being serious.
Well I thought it was funny!

I get what you're saying about needing an easy-to-configure firewall, Paddy. I'm 14 hours into a 24-hour TCP/IP class and I'm just now starting to really understand how to set one up.  I never found an easier way to grasp it (and when we collectively switch to IPv6 I'll be back to square one LOL). I followed some guides before I really understood it but I couldn't troubleshoot the broken stuff- in Windows or Linux.  I don't know what the solution is.

---

### Post by Paddy Landau on 2012-03-22
> **Ms. Daisy said:**
> ... I'm 14 hours into a 24-hour TCP/IP class and I'm just now starting to really understand how to set one up.
That's the problem with computers. A car is easy to use -- you just take it to a mechanic for its annual service or when it breaks down. A computer needs to be the same, but it is still a very primitive device needing frequent attention. Unlike a car, it cannot wait a full year between "services".

---

### Post by Dreamer Fithp Apprentice on 2012-03-22
Very interesting thread. Who would have thought OP's question would generate so much discussion?  I'm too lazy to go back through it to properly quote the remarks I'm responding to but:

on the point that, in practice, simple prudence will keep your 'nix installation, malware free without anti-malware software:
Of course, but that is really true of Windows as well, though perhaps to a slightly lesser degree. I ran DOS and windows for decades without any anti-malware software and the only thing I ever "caught" was the form virus, which apparently came to me on a collection of utilities commercially sold on a 360 k 5.25" floppy, as all software was distributed back in the neolithic. It was an entertaining and clever little bugger that did nothing but reproduce itself through copying itself in a hidden way on any floppy you formatted and at moderately long intervals (1st of every month? something like that) it would, for a day, occasionally at random times toggle the state of your capslock key. If you tracked it down you could find some ASCII from the outer cylinder that wasn't listed as a file in any directory but could still be read with a low level editor if you knew how that said something like "Greetings from the Form virus! Do not panic. I destroy no data. I do no harm. Now that you've found me you should be able to figure out how to delete me."

As to the idea that if Apache under linux could be infected it would have been done and it would be REAL BIG DEAL:
I pretty sure this has been done many times, but it has never been a big deal because because the exploits were found and fixed before the knowledge of them became widely spread. So the only websites affected were small amateur sites where the admin hadn't updated Apache.

Also, if I'm not mistaken, I remember reading that one of the earliest examples of malware, maybe THE earliest example, affected Unix systems, and in some computer lab somewhere, an infected big machine was taken off the WAN (I forget what WAN, maybe not the internet, this may have been before there was an internet) in order to prevent it from spreading the infection, but ironically, this proved to do more harm than good, at least locally, because it delayed the admin's awareness of how to kill the malware, knowledge that was spread via the same WAN.

Caveat: Both of the last two paragraphs are from memory off the top of my head, originating in things I read casually.  I might misremember them and the sources may have been wrong anyway. Take it for what it is worth.

---

### Post by Paddy Landau on 2012-03-23
> **Dreamer Fithp Apprentice said:**
> ... in practice, simple prudence ... that is really true of Windows as well
I don't know about the recent releases of Windows, but that was not true of previous releases. Windows had wide-open holes that would allow Internet-based viruses to contact your machine (uninvited) and install themselves. A firewall was the absolute minimum requirement.

---

