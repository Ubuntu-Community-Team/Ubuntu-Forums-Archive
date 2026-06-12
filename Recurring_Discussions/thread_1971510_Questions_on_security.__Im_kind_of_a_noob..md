---
title: "Questions on security.  Im kind of a noob."
date: 2012-05-02
forum: Recurring Discussions
---

### Post by livewire94 on 2012-05-02
I installed Ubuntu 12.04 LTS as my main OS because I am interested in learning Linux.  Its pretty snappy and seems to work smoothly so far.  Only had a problem with a printer but solved it.

Is Ubuntu safe and secure as Windows 7 or more secure? 
Is Ubuntu easily hacked vs Windows?  
Is the firewall enabled after installation?  
How do I scan for viruses even if they are Windows viruses?

I pay bills and buy things online sometimes and just want to make sure its safe to do so.

Thank you for any replies.

---

### Post by Hungry Man on 2012-05-02
There isn't really any objective measure of security. You're going to a forum with Ubuntu users so understand there'll likely be a lot of bias.

> Is Ubuntu safe and secure as Windows 7 or more secure? 

**In my opinion** Ubuntu is safer than Windows 7. This is due to quite a few reasons, most notably package management and access control.

> Is Ubuntu easily hacked vs Windows? 

This is one of the questions that really can't be answered. It depends. I mean... if the attacker knows how to get in they know how to get in. I think it is probably more difficult to get into Ubuntu than Windows, and at the very least Ubuntu can be configured in such a way that it is more difficult.

> Is the firewall enabled after installation? 

No but there aren't any open ports. There's a sticky in the securty section about this.

> How do I scan for viruses even if they are Windows viruses?

I think ClamAV is one of the free antiviruses for Linux.

---

### Post by rookcifer on 2012-05-02
> **livewire94 said:**
> Is Ubuntu safe and secure as Windows 7 or more secure? 

I would say more secure out of the box.  Just remember to only install software from the Ubuntu Software Center and you'll be fine.

> Is Ubuntu easily hacked vs Windows?  

One must phrase the question correctly.  A better question to ask is "Will I be picking up viruses left and right as I surf the web?"  The answer to that question is no.  There are zero known viruses in the wild for Ubuntu/Linux right now.  Could that change?  Maybe, but it would likely not be widespread if it does.  I could elaborate, but I won't.


> Is the firewall enabled after installation?  

If you have a router with a firewall enabled, then you're good to go.  If you don't have a router, then you can turn on UFW with the following command:

```
sudo ufw enable
```

Since you're new to Linux, you may not want to use the command line.  That's understandable.  In that case, you can install GUFW, which is the GUI to UFW like so:

```
sudo apt-get install gufw
```

Or you can open the Ubuntu Software Center and search for GUFW.

> How do I scan for viruses even if they are Windows viruses?

Unless you will be sharing files with your Windows machine, I do not recommend installing or using an AV scanner.

> I pay bills and buy things online sometimes and just want to make sure its safe to do so.

Thank you for any replies.

You will be about as safe as you can be short of being really paranoid and using a locked down account with no permissions or running a virtual machine, etc..

---

### Post by livewire94 on 2012-05-02
Thanks for the information.  Wasn't sure about security because of the opensource.  I didn't know if anyone could take the source code and create a security flaw.  If its more secure than Windows that would be cool.  I get asked about security of Linux from Windows users and I had to ask about it.  Guess thats normal.

I will look for the sticky about the firewall.  I will try to use ClamAv to scan for viruses just to keep them off of my backups and other Windows computers.

rookcifer, just read your reply.  Thanks for the info.  I do have a router with firewall using DDWRT firmware.  I will be sharing files with windows users now and then, so I may need to scan some sometimes.

---

### Post by kc1di on 2012-05-02
> **livewire94 said:**
> I installed Ubuntu 12.04 LTS as my main OS because I am interested in learning Linux.  Its pretty snappy and seems to work smoothly so far.  Only had a problem with a printer but solved it.

Is Ubuntu safe and secure as Windows 7 or more secure? 
Is Ubuntu easily hacked vs Windows?  
Is the firewall enabled after installation?  
How do I scan for viruses even if they are Windows viruses?

I pay bills and buy things online sometimes and just want to make sure its safe to do so.

Thank you for any replies.
hi and welcome to Ubuntu

12.04 is very secure. Safer in MHO than windows.  
Not easily hacked 
you have to setup the firewalls you want 
There are several antivirus programs that will scan Ubuntu and other linux distros. and it's a good Idea if you send files to windows users but not really needed at this point for Ubuntu as there are very few virus' in the wild that can do damage to a Linux machine.

Clamtk  is one such antivirus scanner and it is in the software center.

Here is a page that will tell you how to set up firewalls if you want. 
[https://wiki.ubuntu.com/UncomplicatedFirewall]("https://wiki.ubuntu.com/UncomplicatedFirewall")

---

### Post by Hungry Man on 2012-05-02
Open Source is very arguably more secure than Closed Source. While it may seem like common sense that if an attacker can see the code they can exploit better, that's really not the case. Hiding code from the attacker is not an effective way to protect a system - this is Kerschoff's principle and it's very old, a foundation to security as we know it, and constantly proven.

What open source does provide is the ability for every capable user to audit and review the code, to validate that the code does what it is meant to do.

---

### Post by rookcifer on 2012-05-02
> **Hungry Man said:**
> Open Source is very arguably more secure than Closed Source. While it may seem like common sense that if an attacker can see the code they can exploit better, that's really not the case. Hiding code from the attacker is not an effective way to protect a system - this is Kerschoff's principle and it's very old, a foundation to security as we know it, and constantly proven.

What open source does provide is the ability for every capable user to audit and review the code, to validate that the code does what it is meant to do.

Yeah.  Windows is closed source and it certainly has not stopped people from finding flaws in the code.  There are tools for "fuzzing" that can do just that without needing to see the source code itself.  Sure, having the source code makes finding such flaws faster and easier, but it also makes it easier to audit and fix as well.

---

### Post by livewire94 on 2012-05-02
Great replies, thanks for answering all my questions.  Have fun.

---

### Post by Irihapeti on 2012-05-02
Be aware that the most critical part of security is user behaviour.

The two biggest exploits, as seen on these forums, are via ssh and vnc (remote desktop). Both of these are available from the repositories (so are official packages) and vnc is even installed (though not enabled) by default.

Reading bodhi.zazen's security thread (among the stickies) is a good place to start.

---

### Post by jerome1232 on 2012-05-02
I wanted to add, since no one has touched on it. That the biggest window of attack is your browser and it's plugins. If you must use java/flash which are both huge attack vectors, then do what you can to limit them, take a look at the apparmor sticky, and the other security stickies for ways to do that.

---

### Post by CharlesA on 2012-05-02
> **jerome1232 said:**
> I wanted to add, since no one has touched on it. That the biggest window of attack is your browser and it's plugins. If you must use java/flash which are both huge attack vectors, then do what you can to limit them, take a look at the apparmor sticky, and the other security stickies for ways to do that.

This too.

Check out the security page in my sig.

No matter what OS you use, the user is always the weakest link.

---

### Post by jintegral on 2012-05-03
When answering questions regarding an OS' total "hackability" there are an abundance of overly complex ways to respond. Simply put imo any OS is as secure as its user. Minus the OS' that I would consider bootable facebook systems (Jolly Cloud, Chrome OS etc.). In my opinion Ubuntu is easier to break than Windows due to the constant and nearly required access to the command line which provides less specific regulatory restrictions than most GUI based preference setters, and what have you, do. Whereas Windows in my opinion is easier to infect due to the abundance of malware available for it. In short, the "8th layer" is the most vulnerable one. Minimizing "user-ignorance" in regards to the user in question's OS of choice should be the goal of **all** users.

---

### Post by Ms. Daisy on 2012-05-03
> **Hungry Man said:**
> I think it is probably more difficult to get into Ubuntu than Windows, and at the very least Ubuntu can be configured in such a way that it is more difficult.
OK, I like you so I'm going to pick on you :P

Hmm. I'd encourage you to see this
[http://ubuntuforums.org/showpost.php?p=11006711&postcount=3](http://ubuntuforums.org/showpost.php?p=11006711&postcount=3)

[http://ubuntuforums.org/showpost.php?p=11474688&postcount=20](http://ubuntuforums.org/showpost.php?p=11474688&postcount=20)

and really most of the security threads in the recurring discussions section.  I'm annoyed because I can't find the source on this, but it's actually a smidge easier to crack linux over windows (can't remember why, blast it).  So it is not more difficult to get into Ubuntu than Windows. I'll search some more because I'm a nerd like that.

---

### Post by jerome1232 on 2012-05-03
> **Ms. Daisy said:**
> OK, I like you so I'm going to pick on you :P

Hmm. I'd encourage you to see this
[http://ubuntuforums.org/showpost.php?p=11006711&postcount=3](http://ubuntuforums.org/showpost.php?p=11006711&postcount=3)

[http://ubuntuforums.org/showpost.php?p=11474688&postcount=20](http://ubuntuforums.org/showpost.php?p=11474688&postcount=20)

and really most of the security threads in the recurring discussions section.  I'm annoyed because I can't find the source on this, but it's actually a smidge easier to crack linux over windows (can't remember why, blast it).  So it is not more difficult to get into Ubuntu than Windows. I'll search some more because I'm a nerd like that.

Your reading those posts wrong imo. Dangertux is not saying "Ubuntu is easier to crack than Windows" in those posts.

Post #1 states in summary that Windows 7 is finally starting to look pretty good (as opposed to laughable in XP)on out of the box security.

Post #2 is arguing that Open Source software is not inherently more secure than Proprietary software, and is more theory than anything else.

 While I generally respect Dangertux's opinions when it comes to security, I'm inclined to look at the track record of Apache Web Server vs IIS for an example of popular Open Source Software's security track record vs Proprietary softwares security track record.

In the case above you can't use the bigger target argument, as Apache, for most of it's history, has been the bigger target, not IIS. I would also take at look at Open Source Firefox vs Proprietary IE, although one may employ the bigger target argument to a point on that one.

---

### Post by Irihapeti on 2012-05-03
When I first came to Ubuntu, I wasn't quite sure what to believe - or should that be who?

I heard all sorts of claims about what you did and didn't need, and what knowledge did I have to assess them?

Eventually, I decided to be guided by what actually happens in practice. That was when I began to notice that the top "hacks" were vnc and ssh with password authentication. Then there were those who ran webservers and such like, and had a bit of iffy php code which got busted. I also noticed that heaps of people got freaked out by rkhunter/chrootkit false positives, but I can't recall anyone who found out via those programs that their security had been breached.

I don't go to dodgy websites, so, other than running NoScript, I don't worry too much about that.

To the very best of my knowledge, I've kept out of trouble over the last five years.

I think that this is not an unreasonable approach for the ordinary user. Having said that, I don't run any internet-facing servers; I would certainly want to read up about securing them before unleashing them on the world.

---

### Post by Hungry Man on 2012-05-03
> **Ms. Daisy said:**
> OK, I like you so I'm going to pick on you :P

Hmm. I'd encourage you to see this
[http://ubuntuforums.org/showpost.php?p=11006711&postcount=3](http://ubuntuforums.org/showpost.php?p=11006711&postcount=3)

[http://ubuntuforums.org/showpost.php?p=11474688&postcount=20](http://ubuntuforums.org/showpost.php?p=11474688&postcount=20)

and really most of the security threads in the recurring discussions section.  I'm annoyed because I can't find the source on this, but it's actually a smidge easier to crack linux over windows (can't remember why, blast it).  So it is not more difficult to get into Ubuntu than Windows. I'll search some more because I'm a nerd like that.
My opinions on this are fairly solid I think but I'll give those a read - I'll always take Dangertux's opinion seriously. Thanks Ms Daisy.

EDIT: I agree with his first post that Windows has caught up a lot.  I disagree with 99% of his second post =P but as he says, he's playing a very strong Devil's Advocate. 

The reality of it is that Open Source vs Closed Source is a lot more complicated than "Which on let's me find exploits faster." He glosses over the first bit about MS "privacy" issues, attributing the ability to validate code usage as a purely privacy feature. This isn't actually the case, though it certainly can be a factor. 

The method he uses (strcopy) is an unsafe way to handle strings. I can easily audit code (and I'm not a great programmer) and see a ton of strcopy's and say "Damn, this code was not written with security in mind." I don't have to say "Oh, 10 exploits" I know flat out that security wasn't though of. **I can not verify anything on Windows.** Verification and Validation - that's something that's just far far easier to do on an Open Source project.

There are a thousand other reasons but I don't want to turn this into another open vs closed battle.

I will say that the attacker always knows the system better than the user. I don't care if it's closed or open - this is a fundamental principal of security that has held true since the foundation of cryptography.

---

### Post by Ms. Daisy on 2012-05-03
> **jerome1232 said:**
> Your reading those posts wrong imo. Dangertux is not saying "Ubuntu is easier to crack than Windows" in those posts.

Post #1 states in summary that Windows 7 is finally starting to look pretty good (as opposed to laughable in XP)on out of the box security.

Post #2 is arguing that Open Source software is not inherently more secure than Proprietary software, and is more theory than anything else.

 While I generally respect Dangertux's opinions when it comes to security, I'm inclined to look at the track record of Apache Web Server vs IIS for an example of popular Open Source Software's security track record vs Proprietary softwares security track record.

In the case above you can't use the bigger target argument, as Apache, for most of it's history, has been the bigger target, not IIS. I would also take at look at Open Source Firefox vs Proprietary IE, although one may employ the bigger target argument to a point on that one.
I worded my response terribly. (stop posting after bedtime ms. daisy...)  I was talking about writing and delivering an exploit in Linux vs. Windows, there are a few more obstacles for it to work in Windows.  It's kind of pedantic of me to harp on it because the obstacles can be overcome quickly. There are just a few more steps in the process on the windows side.

---

### Post by nothingspecial on 2012-05-03
*Thread moved to **Recurring Discussions**.*

---

### Post by Ms. Daisy on 2012-05-03
> **Irihapeti said:**
> When I first came to Ubuntu, I wasn't quite sure what to believe - or should that be who?

I heard all sorts of claims about what you did and didn't need, and what knowledge did I have to assess them?

Eventually, I decided to be guided by what actually happens in practice. That was when I began to notice that the top "hacks" were vnc and ssh with password authentication. Then there were those who ran webservers and such like, and had a bit of iffy php code which got busted. I also noticed that heaps of people got freaked out by rkhunter/chrootkit false positives, but I can't recall anyone who found out via those programs that their security had been breached.

I don't go to dodgy websites, so, other than running NoScript, I don't worry too much about that.

To the very best of my knowledge, I've kept out of trouble over the last five years.

I think that this is not an unreasonable approach for the ordinary user. Having said that, I don't run any internet-facing servers; I would certainly want to read up about securing them before unleashing them on the world.
That is a very pragmatic approach. IMO common sense/ smart surfing habits might be the most important piece of security.

---

### Post by Hungry Man on 2012-05-03
> I worded my response terribly. (stop posting after bedtime ms. daisy...) I was talking about writing and delivering an exploit in Linux vs. Windows, there are a few more obstacles for it to work in Windows. It's kind of pedantic of me to harp on it because the obstacles can be overcome quickly. There are just a few more steps in the process on the windows side.
Not really. If we throw away all questions of open source vs closed source and say that each kernel has an equal number of exploits we're left with fairly similar security models - Discretionary Access Control with some MAC implementations. The difference is mostly with the implementation of these two access control systems and with the implementations of ASLR and DEP. Getting into ASLR and DEP isn't worth it - they work on both systems even though the Windows ASLR is arguably better (and ASLR is applied differently on a per-distro basis.) The DAC is pretty much the same with Ubuntu/ Windows. The MAC is very different, and Linux is far better at it.

Windows MAC is the Integrity system. It's decent, but it's not great. Apparmor/SELinux are pretty much superior in every way. They're more customizable and far far far more finely grained and they can be applied to any program/ process on the entire system, regardless of that processes needs. You can't get this on Windows, you just can't. I can't stop my printer service from accessing my XYZ folder on Windows but I can on Linux and that makes a huge amount of difference.

Taking open source into consideration is a more fun/ interesting conversation but also a lot longer and time consuming. It's fairly clear to see that Open Source provides huge potential for security. That doesn't mean OSS = Secure. The same way that ASLR != Secure. I can randomize a few areas of address space but as long as I leave a few significant areas static it won't matter. As with all things it is a matter of implementation.

edit: And I'll take a strong apparmor profile over good sense any day.

---

### Post by zombifier25 on 2012-05-05
> **Hungry Man said:**
> edit: And I'll take a strong apparmor profile over good sense any day.

You let a completely newbie user in front of your computer, then he/she let a random so-called "customer support" dude enter. Let's see AppArmor protect you with THAT!
If you're not smart (e.g. visit dodgy sites, download everything that looks cool on the Internet, trust anyone) then no amount of security tools can help you.
[img]http://imgs.xkcd.com/comics/security.png[/img]

---

