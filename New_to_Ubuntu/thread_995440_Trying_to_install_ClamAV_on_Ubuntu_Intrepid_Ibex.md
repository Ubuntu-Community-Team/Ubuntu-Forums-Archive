---
title: "Trying to install ClamAV on Ubuntu Intrepid Ibex"
date: 2008-11-27
forum: New to Ubuntu
---

### Post by hifly1231 on 2008-11-27
I've installed ClamAV from Synaptec, but it's telling me that it's out of date.  How do I update it?  If possible, could someone tell me step by step?  I'm new to Linux...coming from Windows XP.  Thanks!!!

---

### Post by Keen101 on 2008-11-27
umm... i don't have it currently installed on my system, but willtry to help.

does it install and just give you the error of the database not being updated, or it won't even install?

are you using it from the command line, or one of the couple GUI interfaces for it. If it's from command line, try installing a GUI interface for it.

---

### Post by Paqman on 2008-11-27
You can save yourself the hassle and just not install it. Linux machines dont' normally need antivirus software because we're immune to Windows viruses, and all the viruses that could affect us are taken care of with security patches.

Forget installing antivirus software, just keep up to date with security updates.

---

### Post by Keen101 on 2008-11-27
> **Paqman said:**
> You can save yourself the hassle and just not install it. Linux machines dont' normally need antivirus software because we're immune to Windows viruses, and all the viruses that could affect us are taken care of with security patches.

Forget installing antivirus software, just keep up to date with security updates.

no, but it might be nice to make sure the linux system is not a "virus carrier". Always nice to know that one isn't accidentally passing on windows viruses to ones friends or family.

---

### Post by Paqman on 2008-11-27
> **Keen101 said:**
> no, but it might be nice to make sure the linux system is not a "virus carrier". Always nice to know that one isn't accidentally passing on windows viruses to ones friends or family.

For sure, but they should be perfectly well protected by their own security. I can understand why in a work situation it might be seen as unprofessional to pass malware to a client, but I don't really see the problem for home users.

The bottom line being: installing antivirus software onto Linux machines makes neither Linux nor Windows machines any safer than they would be otherwise.

---

### Post by hifly1231 on 2008-11-27
> **Keen101 said:**
> umm... i don't have it currently installed on my system, but willtry to help.

does it install and just give you the error of the database not being updated, or it won't even install?

are you using it from the command line, or one of the couple GUI interfaces for it. If it's from command line, try installing a GUI interface for it.

I can install it from Synaptic, but when I run it, it says this:

WARNING: Your ClamAV installation is OUTDATED!
DON'T PANIC! Read [http://www.clamav.net/faq](http://www.clamav.net/faq)

I've found the package - clamav-0.94.2.tar.gz, but I have no idea how to install these files yet, and I need to learn.  Can someone help me?  Thanks!!!

---

### Post by nkri on 2008-11-27
Go into a Terminal (Applications>Accessories>Terminal) and type
```
sudo freshclam
```
When it asks for the sudo password, just give it your login password (nothing will show up...just type it in and press enter).

This will update your virus definition files and you should be able to do a regular scan.  Another way to do it is:
```
gksu clamtk
```
and go to Help>Update Signatures.

They both do the same thing, so do with whatever you feel most comfortable.

Good luck!
-nkri

---

### Post by falcon61102 on 2008-11-27
The .tar.gz file that you found needs to be extracted.

The error you are getting just means that there is a newer version out, but the one that you have will still do the trick.  As long as the virus definitions are up to date you're good to go.

---

### Post by hifly1231 on 2008-11-27
> **falcon61102 said:**
> The .tar.gz file that you found needs to be extracted.

The error you are getting just means that there is a newer version out, but the one that you have will still do the trick.  As long as the virus definitions are up to date you're good to go.

OK, I know how to extract a tar.gz file, but then what do I do with it?  I have absolutely no idea how to install these to my computer.

---

### Post by falcon61102 on 2008-11-27
Sorry, without knowing the contents of the file I wouldn't be able to direct you on where to put them.  There may be a readme or instructions on the website.

Check out the section on Ubuntu:
[http://www.clamav.net/download/packages/packages-linux](http://www.clamav.net/download/packages/packages-linux)

---

### Post by egalvan on 2008-11-27
> **Paqman said:**
> For sure, but they should be perfectly well protected by their own security.

If this were true, then there would be no virus, malware, trojan or root-kit infestations in the wild. 

All machines would be either protected (Windows) or immune (*nix), so nothing would ever spread.

Right?

>  I can understand why in a work situation it might be seen as unprofessional to pass malware to a client, but I don't really see the problem for home users.

"Bad things" exist only in the workplace?

> The bottom line being: *installing antivirus software onto Linux machines makes neither Linux nor Windows machines any safer* than they would be otherwise.

Watching out for your neighbor helps everyone.
 No one is breaking into my house, short of using rather noisy power tools, but that doesn't mean I won't keep a look-out for any suspicious activity around my neighbor's house.

And remember, Linux machines (which by your definition "should not have anti-virus installed") run a very large portion of the Internet and email servers.


In short, I respectfully disagree with this "no anti-virus software for Linux" view-point;
I think that Linux users should be "good neighbors" and help stamp out junk software.

But I AM in agreement that ALL users should be taught effective techniques for avoiding all types of mal-ware.

ErnestG

---

### Post by Paqman on 2008-11-27
> **egalvan said:**
> If this were true, then there would be no virus, malware, trojan or root-kit infestations in the wild. 

All machines would be either protected (Windows) or immune (*nix), so nothing would ever spread.

Right?


No, of course not. But users are responsible for the security of their own machines. While being neighbourly is good, taking personal responsibility for the security of others' machines is nice in theory, but not practical. 

> 
"Bad things" exist only in the workplace?


No, I never said that at all. I merely pointed out that it would be prudent to avoid even the suggestion of lax security when dealing with someone you had a financial relationship with.

> 
And remember, Linux machines (which by your definition "should not have anti-virus installed") run a very large portion of the Internet and email servers.


Absolutely, and it's for exactly these machines for which we have antivirus apps in our repos. ClamAV is a command line tool, and thus clearly intended for servers.

I think you took my statement about "Linux machines" a little out of context, the OP is clearly setting up a desktop, not a server. Anything designed primarily to serve to Windows machines should have it installed. However, i'm of the opinion that most Linux antivirus suites are of poor quality, and am highly sceptical of their usefulness. ClamAV in particular does [very badly]("http://blogs.pcmag.com/securitywatch/Results-2008q1.htm") in tests.

> 
But I AM in agreement that ALL users should be taught effective techniques for avoiding all types of mal-ware.


As am I. I just don't consider installing Windows antivirus suites onto Linux desktops as being a particularly effective thing to do. It does no harm, sure, but it's important to educate new users that their old Windows habits need to change on Linux. 

To my mind installing antivirus goes in the same category as defragging. Sure, your Linux system could *theoretically* suffer from a fragmented drive, but in practice it isn't worth worrying about unless you're running certain kinds of server. Likewise antivirus.

---

### Post by falcon61102 on 2008-11-28
Most everyone has brought up some valid points on whether or not it's worth installing an anti-virus on Linux but here's my question: 
How does that help the original poster fix his problem?

It's great that everyone has an opinion and is willing to share information regarding that and maybe you can start a thread all about whether or not to install anti-virus.

---

### Post by michwill on 2009-04-02
...any progress on this issue?  If nothing else, where are the "edge" repositories for clamav?

---

### Post by MrWES on 2009-04-02
> **falcon61102 said:**
> Most everyone has brought up some valid points on whether or not it's worth installing an anti-virus on Linux but here's my question: 
How does that help the original poster fix his problem?

It's great that everyone has an opinion and is willing to share information regarding that and maybe you can start a thread all about whether or not to install anti-virus.

I run clamav on my server; I have several windows computers accessing the samba shares. However, I believe it's just the engine that's outdated, the program runs perfectly fine -- so ignore that error. You can run a scan from a cron if you like, and freshclam runs from a daemon and defaults to updating 24 times a day; once an hour.

Bill

---

