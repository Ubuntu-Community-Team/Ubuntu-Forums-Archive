---
title: "Another &quot;Naive&quot; Antivirus thread"
date: 2009-12-14
forum: Recurring Discussions
---

### Post by el Tedward on 2009-12-14
Howdy, I'm just looking for some opinions on what the best antivirus software for linux is(or even just unix systems in general). I did a search for this topic and most of the posts were not very helpful. I'm an Information Assurance major and I'm perfectly aware of the current state of malware and linux, so please don't just tell me that it is not necessary or turn this into a silly debate. I do a lot of "filesharing" and I'm almost always networked with windows clients (which I may or may not be sharing files with), so I do have a use for this. I'm probably gana be spending more time messing with firewalls and such(which is what I'll probably have a bunch of people tell me I should focus on in this thread..) once I get done with finals, and especially in my classes next semester. 

These are the things I'm looking for:
-Virus detection rate. If you can tell me from experience which AV software is going to catch the most viruses from all the um, 'stuff' I'm downloading, that would be extremely helpful. 
-Functionality and options. The ability to centrally manage things on a network would be pretty cool, though it's not necessary as I'll probably only be actually using this on one or two machines. I ran into [**_panda_**]("http://www.pandasoftware.com/download/linux/linux.asp"), which sounds like it could have some decent central management functions. 
-If you know of anything at all that actually searches for linux/unix targeting viruses, I'll give you a really big hug. While there might not really be anything out there in the wild (my paranoia disagrees), it'd be kind of like really freaking awesome to hear about something that scans for whatever linux viruses that have been documented so far. 
-Free is preferred, but if you know of a really good product that isn't free, I'll probably be interested in looking at it. 


I installed Bitdefender today, and it seems like a decent product. The documentation that comes along with it seems pretty good. Does anyone have any experience they can share about bitdefender? I'm probably going to install one or two AV suites regardless (I know I'm being paranoid, but I'm getting rather frustrated that I haven't found any viruses on the stuff I've been downloading & scanning with avg [on my desktop], and avast [on my laptop before I upgraded to karmic]).

I'm really just looking for opinions from people who have some good AV experience with linux. Any sort of advice I can get in that regard would be greatly appreciated ;)

---

### Post by sliketymo on 2009-12-14
" I haven't found any viruses on the stuff'.

Perhaps there is nothing to find ? There are many good posts concerning ant-virus in the forums. Also a quick google search on anti-virus in Linux will yield a wealth of information on the subject.

---

### Post by HermanAB on 2009-12-15
ClamAV works well enough.  I use it on all my mail servers and never have virus problems.

---

### Post by cariboo on 2009-12-15
As far as I recall clamav is the only av scanner that claims it scans for Linux viruses, the rest of them only scan for Windows viruses. 

So far the only way malware will work is through social engineering, and a virus scanner won't be able to prevent any thing like that from happening.

Instead of relying on software to protect you from malware, educate yourself so that you know when something is not right and prevent an attack in the first place.

Virus scanners, when they do work usually only work after the system has been infected and the damage is already done.

---

### Post by DouglasAWh on 2009-12-15
> **cariboo907 said:**
> 
Instead of relying on software to protect you from malware, educate yourself so that you know when something is not right and prevent an attack in the first place.

Virus scanners, when they do work usually only work after the system has been infected and the damage is already done.

As someone that works in a mixed environment, I'd echo this. Most Windows AV programs are worthless piles of crap.  Certain institutions pay a lot of money for their worthless piles of crap though.

---

### Post by noway2 on 2009-12-15
I too would vote for Clam AV.  As you mentioned, you intend to do file share with windows machines.  The concern isn't so much that your linux system will get an infection, but you have a responsibility not to "spread the love".  I've been using it on my email server for the better part of the past year and it has caught every test I threw at it and hasn't caused any performance issues.

---

### Post by aysiu on 2009-12-15
> **DouglasAWh said:**
> As someone that works in a mixed environment, I'd echo this. Most Windows AV programs are worthless piles of crap.  Certain institutions pay a lot of money for their worthless piles of crap though.
I vote for this as well.

I know it's not what you (el Tedward) want to hear, but it's the truth. Antivirus isn't security. If you want the Windows users you share files with to be secure, tell them to get some real security and not rely on you scanning files for them. A limited user account, Firefox with NoScript, turned-off autorun, common sense, no-longer-hidden file extensions, and regular Windows updates will make them far more secure than antivirus.

Antivirus does **nothing** to protect you.

More importantly, it's not your job to protect them. If they aren't protected, then they will get infected by others (not you). And if they are protected, then it won't matter what you send them. How about just stop sharing files that you don't trust or you don't create yourself?

> **el Tedward said:**
> so please don't just tell me that it is not necessary or turn this into a silly debate. It won't be a silly debate if you just concede that antivirus offers you no added security (or any security, really).

---

### Post by el Tedward on 2009-12-16
Probably should have just put this in the OP, but I'm really just looking for AV mostly as something to just play with rather than something I feel like I really need.. I understand that AV, like anything else, is not going to provide complete security by itself or necessarily be a preventative measure, but there's a lot of things I plan on doing security wise that aren't entirely necessary. 

Anyways, thanks for the replies (the helpful ones :p).

---

### Post by MasterNetra on 2009-12-16
> **el Tedward said:**
> Probably should have just put this in the OP, but I'm really just looking for AV mostly as something to just play with rather than something I feel like I really need.. I understand that AV, like anything else, is not going to provide complete security by itself or necessarily be a preventative measure, but there's a lot of things I plan on doing security wise that aren't entirely necessary. 

Anyways, thanks for the replies (the helpful ones :p).

Hope you also know that AV is useless to Linux itself, its only remotely good for scanning files that are heading out to windows machines, other then that it really doesn't do anything but waste ram and space. But if your just playing with it I suppose both ClamAV and Avast are good ones.

---

### Post by doas777 on 2009-12-16
> **aysiu said:**
> 
Antivirus does **nothing** to protect you.


thats probably going too far. My personal experience (and thousands of others as well) has proven otherwise. I understand why you say it, but as categorical statements go, this one is hard to support. it's not as useful as we would like, but saying it is completely useless is beyond the pale.

Op, in your usecase, it is probably best to have a good active AV system on your windows boxes and let them take care of the problem. this is of course only for home use. if you are talking about running a corporate mail server for instance, make sure you have somthing installed, even if it is doing nothing worthwhile. I would be fired from my job if I deployed a server without AV/firewall, since our minimal security specifications require it.

---

### Post by aysiu on 2009-12-16
I don't think it's hard to support at all. In fact, not only does antivirus do *nothing* to protect you, it sometimes can harm you through complacency. Instead of taking real security measures, you may end up relying on antivirus to catch bad stuff for you. Or antivirus can also make you paranoid about benign files (just do a Google search for *remove tracking cookies* to see what I'm talking about).

Are there situations in which antivirus may be useful? Sure. If you run a mail server.

---

### Post by doas777 on 2009-12-16
> **aysiu said:**
> I don't think it's hard to support at all. In fact, not only does antivirus do *nothing* to protect you, it sometimes can harm you through complacency. Instead of taking real security measures, you may end up relying on antivirus to catch bad stuff for you. Or antivirus can also make you paranoid about benign files (just do a Google search for *remove tracking cookies* to see what I'm talking about).

Are there situations in which antivirus may be useful? Sure. If you run a mail server.

I find tools useful when removing scareware and other drive-by downloads from my users workstations. we had one guy get caught by a clipboard-jacking exploit (cross platform btw) last year, and the link he pasted into a dept wide email, was not the link he copied. after that i had to remove "antivirus 2009" from 20 PCs. the symantec scanner missed them, but malwarebytes saved me about 2 weeks of rebuilding terminals.

so, how is it that it does Nothing to protect/assist me? 
your tracking cookie example is a red herring. just because you don't know how to intrepret the output of a tool does not mean that it is wrong, only that you are.

---

### Post by The Real Dave on 2009-12-16
Without opinion on the whole antivirus or no thing, I recommend both ClamAV and Avast! for Linux Workstation. Clam is in the Repos, though check their site for the newest versions, and Avast! can be downloaded for free from their site, though requires a licence. This can be obtained by registering, which is free, but lasts only a year. Both great pieces of software, with good effectiveness. High recommended.

---

### Post by aysiu on 2009-12-16
> **doas777 said:**
> I find tools useful when removing scareware and other drive-by downloads from my users workstations. we had one guy get caught by a clipboard-jacking exploit (cross platform btw) last year, and the link he pasted into a dept wide email, was not the link he copied. after that i had to remove "antivirus 2009" from 20 PCs. the symantec scanner missed them, but malwarebytes saved me about 2 weeks of rebuilding terminals. Once a computer is compromised, the only surefire way to know the malware is gone is to back up important personal data and then reinstall the OS from scratch. I don't trust that antivirus scans or even malwarebytes totally remove malware infections.

As I said before, prevention is the best method. Harden the installation with limited user accounts, Firefox with NoScript, regular Windows updates, etc. and you won't have malware to remove.

> so, how is it that it does Nothing to protect/assist me? 
your tracking cookie example is a red herring. just because you don't know how to intrepret the output of a tool does not mean that it is wrong, only that you are. I don't have any problem interpreting things. I know what a tracking cookie is. And I know what is safe and what is not. I don't need "antivirus" placebos telling me what is safe and what is dangerous. And if I did, it wouldn't tell me the right things anyway (that was my point--false positives).

---

### Post by doas777 on 2009-12-16
> **aysiu said:**
> 
 I don't have any problem interpreting things. I know what a tracking cookie is. And I know what is safe and what is not. I don't need "antivirus" placebos telling me what is safe and what is dangerous. And if I did, it wouldn't tell me the right things anyway (that was my point--false positives).

sorry if that came off the wrong way, I didn't mean you personally, I meant the generic you. obviously you know what they are, and it was clear to me that you were talking about false positives.

part of my argument is a converse to your own. just as having AV may hurt you by making you complacent, so too would thinking you know how to be safe, when in fact you are not prepared for every kind of new attack.

we've (you , me, bodi, and many others) have been having this recurring argument for some time now, so I just wanted to say, it's nothing personal. we all just like to argue :)

---

### Post by aysiu on 2009-12-16
> **doas777 said:**
> sorry if that came off the wrong way, I didn't mean you personally, I meant the generic you. obviously you know what they are, and it was clear to me that you were talking about false positives. That's cool. I may have been reading in a tone that you didn't intend. Thanks for clarifying.

> part of my argument is a converse to your own. just as having AV may hurt you by making you complacent, so too would thinking you know how to be safe, when in fact you are not prepared for every kind of new attack. If you think just by having Linux installed that you're invincible, then you can be just as complacent as those who rely on antivirus. The key is to look to actual security measures and not just say "I have _____, so I don't have to worry about anything." Unfortunately, too many people put "antivirus" into that blank space.

> we've (you , me, bodi, and many others) have been having this recurring argument for some time now, so I just wanted to say, it's nothing personal. we all just like to argue :) I certainly do when it comes to antivirus!

---

### Post by almufadado on 2009-12-16
Also

Most Antivirus databases updates get the latest threat  3 days to 1 week for the first occurrence, so even the best av is ineffective ! 

Virus and trojans comes from email, p2p infected apps, and so on.. 
  -- check you emails before open them (don't use outlook express ! that opens and execute them by default without any type of care !!) 
 -- in p2p check for fake files and wmp movies and wma sound

Malware, in general (virus, trojans, scripts, code injection, open tcp/up doors, bad windows services exploits (remote registry, netbios over tcp helper, rdp, accept remote assistance, etc etc) and worst of all activex (as it has direct access to your harddisk from remote) have a big gap between starting messing with systems and you getting a "miraculous cure" or a patch so the only solution is to secure your system.
 
New Scripts and web-based malware infections that you get from a web site can only be preventing by you, by being aware of what is happening,  

(A biiiiig long time ago, I had to reinstall my windows because i mistyped an URL (was a mistype of google, i think !) and went into a site that used the integrated windows media player to deliver a file that some how screwed the registry beyond recovery )  

All of this can only be avoid by prevention !

Sex : people go to sites offering "free <something> ... for those you believe ... start unbelieving in "free lunches" . There are so many ways to get real free sex stuff it hurts ! 
"Good " sex sites offer a preview and will eventually ask you for you card number !
"Bad" sex sites offer you free stuff to click ... most exploiting the wmp non existent security.

IM : MSN messenger is the worst thing i ever seen !  beside from opening up your computer to whom ever is preying on you it doesn't even obey to windows file system rules creating a mess in your harddrive (non-deletable files, files exceeding name length, 

Windows OS : everything is a potential executable !!! even a temp file disregarding extensions, contents can be executed without notice.
Security is also lame because for the system to run smoothly, the temp and temporary internet files dirs must have "everybody" access , has there will be always some app that do not go with the SO rules (protected games, HASP's, "old" apps,  


Solution :
Both for windows and linux

- close all unneeded open doors ... if you are expecting  some comm open it in that moment ! 

- Use IP blockers to prevent comms from lame sites (adware, spyware, malware... and in worst cases level1.

- Open windows update by yourself  ... bet yet choose from the IT site  what to download ... choose the critical and if in doubt disregard the rest (choose only office updates that precede the newest version ... all updates after that are intended (too strong a word ? :) )  
to mess your office system !!!

- Get a firewall where all comm are logged and where you can stop them ... which is a thing missing in linux, I mean a practical (graphic !) stopper to use  !

- Always make a image of you installation so you can both restore and compare !
  
- Have all data and system backups in a preferably in a second harddrive (if you value time !) or at least in a second partition (if you value money!) (check windows registry for "profilelist" and change the location from c:\documents and settings to for example d:\ preferably when installing )  
This works for linux by moving your home directory to another partition

- Always create more than one user (2 administrators and 1 user or poweruser) and login all at least two times 
 in linux works too because some apps are run from the user config 

- In linux have a full copy of your "/etc" directory 
- in windows have a full copy of your \windows\system32  

- have always at hand a bootable cd with disk and/or system access (hirens, winpe, sysinternal recovery cd) of a linux live cd with full ntfs access/compatibilty

Otherwise-

don't worry ...be happy ... and pay the system recovery bill !

---

