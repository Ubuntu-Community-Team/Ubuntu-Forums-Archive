---
title: "Antivirus on Linux"
date: 2009-03-15
forum: Recurring Discussions
---

### Post by quarkhirad on 2009-03-15
> **hyper_ch said:**
> why do you run antivirus on linux anyway?

You need to run an antivirus because when you have a dual boot with windows then you are in trouble. As the virus can be sitting and doing no harm in linux and as soon as you log into windows your in trouble. Also it isnt polite to give your pen drive with 50 virus's and 3 files to a windows user. 

Anyway where and how so i install kaspersky for linux. Any help???? Aas in can i download it??

---

### Post by lisati on 2009-03-15
Ignore those who say you don't need antivirus with *nix - the malware might not have the same potential to hurt *nix systems, but it is good manners (and required by some email providers) to avoid sending nasty stuff by email. And some of us interact with Windows machines too.....

Passing on malware could even be seen as illegal as well: depending on how it's sent, it could be considered an unsolicited email. Some relevant legislation can be found at [http://www.legislation.govt.nz/act/public/2007/0007/latest/DLM405134.html](http://www.legislation.govt.nz/act/public/2007/0007/latest/DLM405134.html)

---

### Post by hyper_ch on 2009-03-15
> **quarkhirad said:**
> You need to run an antivirus because when you have a dual boot with windows then you are in trouble.
So, you run antivirus on linux but not antivirus on Windows?

> **quarkhirad said:**
> Also it isnt polite to give your pen drive with 50 virus's and 3 files to a windows user.
Well, if someone runs a certain OS isn't it his/her obligation to make sure no malware can enter? If they have appropriate antivirus then you can't pass those viruses to them.
If they don't have such a thing, don't you think it's much more likely they will get infected by someone else and not by you?
 
> **lisati said:**
> Ignore those who say you don't need antivirus with *nix - the malware might not have the same potential to hurt *nix systems, but it is good manners (and required by some email providers) to avoid sending nasty stuff by email. And some of us interact with Windows machines too.....
Are you an email provider? Don't you think each one should be responsible for securing their own machine?

> **lisati said:**
> Passing on malware could even be seen as illegal as well: depending on how it's sent, it could be considered an unsolicited email. Some relevant legislation can be found at [http://www.legislation.govt.nz/act/public/2007/0007/latest/DLM405134.html](http://www.legislation.govt.nz/act/public/2007/0007/latest/DLM405134.html)
That's New Zealand... little interest to me.

---

### Post by bodhi.zazen on 2009-03-15
> **quarkhirad said:**
> You need to run an antivirus because when you have a dual boot with windows then you are in trouble. As the virus can be sitting and doing no harm in linux and as soon as you log into windows your in trouble.

FYI this is just wrong. If you have a Windows virus on your Linux partition and boot windows nothing will happen.

Please do not spread misinformation on these forums, especially about security.

If you are running Windows without antivirus, then this is the problem.

> Also it isnt polite to give your pen drive with 50 virus's and 3 files to a windows user.

Can you support this claim with a single referance to a virus that is detected by Linux antivirus but not windows antivirus ?

May I also ask, what application do you run in Windows to scan for Linux malware ? OSX malware ? FreeBSD malware ?

I agree with what others have said, if you run an OS you need to secure it. If you run Windows you need to run antivirus. If you do so, windows antivirus will protect you from viruses as much as is possible and, unless you can cite a referance, there is no need or additional benefit from running antivirus on Linux as you suggest.

No antivirus, however, will protect you from zero day exploits.

---

### Post by cardinals_fan on 2009-03-16
[http://www.happyassassin.net/2009/01/20/on-linux-security/](http://www.happyassassin.net/2009/01/20/on-linux-security/)

---

### Post by hyper_ch on 2009-03-17
> **cardinals_fan said:**
> [http://www.happyassassin.net/2009/01/20/on-linux-security/](http://www.happyassassin.net/2009/01/20/on-linux-security/)

Actually there is some magic that prevents you getting malware - you just don't install software from any third party site on linux as you do on windows. Most stuff is in the official repos.

---

### Post by lisati on 2009-03-17
> **hyper_ch said:**
> 
That's New Zealand... little interest to me.

It was just an example. I'm sure that there's probably some relevant legislation in Switzerland as well.

---

### Post by hyper_ch on 2009-03-17
> **lisati said:**
> I'm sure that there's probably some relevant legislation in Switzerland as well.
You're free to point it out to me.

---

### Post by lisati on 2009-03-17
> **hyper_ch said:**
> You're free to point it out to me.

I haven't bothered looking (I don't live in Switzerland), but did notice in Yahoo's [terms and conditions]("http://info.yahoo.com/legal/us/yahoo/utos/") that there's a clause about not sending out malware. I quote:
> 
You agree to not use the Yahoo! Services to:

  <snip>
   8.

      upload, post, email, transmit or otherwise make available any material that contains software viruses or any other computer code, files or programs designed to interrupt, destroy or limit the functionality of any computer software or hardware or telecommunications equipment;


---

### Post by hyper_ch on 2009-03-17
> **lisati said:**
> I haven't bothered looking (I don't live in Switzerland), but did notice in Yahoo's [terms and conditions]("http://info.yahoo.com/legal/us/yahoo/utos/") that there's a clause about not sending out malware. I quote:

And you've heard of anyone being closed down by yahoo for accidentally sending malware?

---

### Post by fatality_uk on 2009-03-17
If you use a Linux PC in a mixed OS environment, such as an office, then a decent AV would be advised.

---

### Post by bodhi.zazen on 2009-03-17
> **fatality_uk said:**
> If you use a Linux PC in a mixed OS environment, such as an office, then a decent AV would be advised.

... On your windows boxes ;)

---

### Post by snl2587 on 2009-03-17
Well, this is always a fun discussion.

Frankly, I see both sides of the issue. While I am all for computer security and am one of those self-described paranoid Linux (and Windows) users who scoffs at those who fail to keep themselves protected, there's a point where ideology meets practice. I keep ClamAV around on my Linux box whenever I'm giving any kind of downloaded file to my friends, mostly because many of them flat-out refuse to run any kind of anti-virus, and sometimes refuse to run even a basic firewall. Do I do that when I pass files to my own Windows box? No, because I keep that machine well-protected and rarely run anything I have the slightest suspicion about (save those for the VMs, right?).

Do we need anti-virus/anti-malware for Linux itself? Not if you're like me, and besides that I'm not even sure if there is a program like that. And should you feel in any way obligated to run Windows AV in Linux? Absolutely not, but I do suggest trying to help those who are less computer-savvy if you're so inclined.

---

### Post by hyper_ch on 2009-03-17
> **snl2587 said:**
> I keep ClamAV around on my Linux box whenever I'm giving any kind of downloaded file to my friends, mostly because many of them flat-out refuse to run any kind of anti-virus, and sometimes refuse to run even a basic firewall.
So you think chances are higher that they get infected by you and not by someone else they know or other malicious way?

> **snl2587 said:**
> Absolutely not, but I do suggest trying to help those who are less computer-savvy if you're so inclined.
Then educate them instead...

---

### Post by snl2587 on 2009-03-17
> **hyper_ch said:**
> So you think chances are higher that they get infected by you and not by someone else they know or other malicious way?
No. But I refuse to be the source.

> Then educate them instead...
What do you want me to do...alienate everyone I know by preaching at them at every turn until they break down? Tie them to a chair and force a flash drive with an anti-virus installer down their throats? Of course I've suggested that they use good security practices, and I keep an anti-virus installer on my local fileshare, automatically install protective software whenever I fix their computers, etc. But what else can I really do? Most people could care less about computer security.

---

### Post by linuxisevolution on 2009-03-17
> **quarkhirad said:**
> You need to run an antivirus because when you have a dual boot with windows then you are in trouble. As the virus can be sitting and doing no harm in linux and as soon as you log into windows your in trouble. Also it isnt polite to give your pen drive with 50 virus's and 3 files to a windows user. 

Anyway where and how so i install kaspersky for linux. Any help???? Aas in can i download it??

The main thing you should be worried about is rootkits. Viruses are pretty nonexistant for Linux.

So, if I don't have windows at all I don't need it? LOL. Linux antivirus doesn't exist for what I know, but there are several programs for Linux that will scan for *Windows* viruses... You should be running Windows with a restrictive account like you do in Linux, I mean, you do that, right? :D

---

### Post by cardinals_fan on 2009-03-17
> **hyper_ch said:**
> Actually there is some magic that prevents you getting malware - you just don't install software from any third party site on linux as you do on windows. Most stuff is in the official repos.
Sure.  But the point is that a scary number of people don't follow this sage advice.  The 15-minute sudo timeout doesn't help either...

Anyway, I am still waiting to hear a single good reason to run an antivirus application on any operating system.  There are some decent heuristics-based scanners, but they aren't nearly as useful as education and responsibility.  Signatures-based scanners are worse than useless.

---

### Post by hyper_ch on 2009-03-18
it helps as stuff outside the repos in a lot of cases need to be compiled ;)

---

