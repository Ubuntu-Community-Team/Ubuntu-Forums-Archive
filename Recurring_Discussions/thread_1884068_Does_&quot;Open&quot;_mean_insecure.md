---
title: "Does &quot;Open&quot; mean insecure?"
date: 2011-11-20
forum: Recurring Discussions
---

### Post by Not unique on 2011-11-20
Does "Open" mean insecure?

I have used Ubuntu since 2005 and love it, also I am always trying to no avail to pursued my friends to try it or at least open source software for Windows as a way forward to recommending Open source and Ubuntu.
**But they ask *Does Open mean insecure?* as any one can get to the code.**
Can any one help me with some good answers?

---

### Post by LinuxFan999 on 2011-11-20
No, Open source software is not insecure, and is usually more secure than proprietary software. A great example is OpenBSD, which has security as it's first priority, and it's open source. Linux is also more secure than Windows, and Browsers like Firefox and Chrome are more secure than Internet Explorer.

---

### Post by Shazaam on 2011-11-20
That's one of the beauties of open source. So many people having access to the source code means there are more "eyes" looking at it. More "eyes" to check and improve code. More "eyes" to detect malicious code. So no, "open source" does not mean it's insecure.

---

### Post by Not unique on 2011-11-20
Yes but if the codes "open" then what's stopping people going in and messing around with it or making virus's/malware/spyware?

---

### Post by An Sanct on 2011-11-20
> **Shazaam said:**
> That's one of the beauties of open source. So many people having access to the source code means there are more "eyes" looking at it. More "eyes" to check and improve code. More "eyes" to detect malicious code. So no, "open source" does not mean it's insecure.

I agree with this, open source means more developers can take a look...

---

### Post by squenson on 2011-11-20
> **Not unique said:**
> Yes but if the codes "open" then what's stopping people going in and messing around with it or making virus's/malware/spyware?
Yes, anyone can change the code and make malicious things, but then what? How would they distribute this code to your machine? The main "distros" are very well controlled from this point of view!

---

### Post by Erik1984 on 2011-11-20
> **Not unique said:**
> Yes but if the codes "open" then what's stopping people going in and messing around with it or making virus's/malware/spyware?

Usually only a few people control access to the actual code in the repository. They can look at the suggested new code to see if it contains any bad stuff. At the same time many other people involved with the project will quickly spot bad code because it's all open.

---

### Post by mamamia88 on 2011-11-20
If anything it would be more secure since you don't have to wait for a massive corporation to release bug fixes.

---

### Post by MG&amp;TL on 2011-11-20
Tell them to go here:

[http://uptime.netcraft.com/up/graph]("http://uptime.netcraft.com/up/graph") And search for their favourite sites. Then see how many of them are running Linux/Apache compared to Windows/whatever the windows webserver is called.

---

### Post by haqking on 2011-11-20
Open has nothing to do with security and does not effect security.

Linux and Windows are equally secure and certified such, the way the user runs things will effect security.

Linux is as easily attacked as Windows, however Linux does not suffer from Virus code but only due to the lack of distribution and the malicious code writers not as yet targeting Linux, but AV is a very small security issue and small percentage of attack vectors.

there is no more secure in the Linux and Windows world as an end user OS.

You can tighten the security in windows as you can and need to in Linux.

Things like running with admin permission, allowing scripts to run in your browser etc etc

Read here for a wiki we have been working on for the Ubuntu noob to security [https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)

which was born from this thread [http://ubuntuforums.org/showthread.php?t=1873643](http://ubuntuforums.org/showthread.php?t=1873643)

Security is user/admin controlled with common sense.

Open however means the code is open source and so more eyes to look at to modify and develop, so things get patched quicker generally than in the proprietary world but that is debatable.

to summarise there is no MORE SECURE in either windows or Linux they are certified roughly the same.

---

### Post by sffvba[e0rt on 2011-11-20
*Thread moved to **Recurring Discussions**.*


404

---

### Post by F.G. on 2011-11-20
yeah, i don't think that the 'open' aspect effects the security. there are plenty of know exploits for windows systems, i don't think that the 'security by obscurity' method works at all well.  security in linux is basically built into the logic of the system.

ubuntu, fedora, gentoo and redhat can all be 'hardened' to make them super secure. also there is a distro called SELinux (security enabled linux) the focus of which is on security.

being 'open-source' is akin to being able to view the blueprint. if i can see the blueprint of a prison, if it is a well designed prison i still wont be able to break in (or rather out). the idea that you can get real security from keeping these things a secret doesn't really work (particularly as if you open the source code you basically make the development team much bigger, so you wind up with a better designed and coded project).

i think until recently the NSA recommended SELinux for it's people to use.

---

### Post by haqking on 2011-11-20
> **F.G. said:**
> yeah, i don't think that the 'open' aspect effects the security. there are plenty of know exploits for windows systems, i don't think that the 'security by obscurity' method works at all well.  security in linux is basically built into the logic of the system.

ubuntu, fedora, gentoo and redhat can all be 'hardened' to make them super secure. also there is a distro called SELinux (security enabled linux) the focus of which is on security.

being 'open-source' is akin to being able to view the blueprint. if i can see the blueprint of a prison, if it is a well designed prison i still wont be able to break in (or rather out). the idea that you can get real security from keeping these things a secret doesn't really work (particularly as if you open the source code you basically make the development team much bigger, so you wind up with a better designed and coded project).

i think until recently the NSA recommended SELinux for it's people to use.


SELinux is not a distro it is feature in the kernel from 2.6

Edit: i should clarify actually on that, it is there as an enhancement allowing you to enforce Mandatory access controls if you so desire

---

### Post by CharlesA on 2011-11-20
> **MG&TL said:**
> Then see how many of them are running Linux/Apache compared to Windows/whatever the windows webserver is called.

Microsoft's web server is called IIS. ;)

> **haqking said:**
> 
Open however means the code is open source and so more eyes to look at to modify and develop, so things get patched quicker generally than in the proprietary world but that is debatable.


Bingo. I'd quote the whole rest of the post but I think that summed it up pretty well.

---

### Post by Not unique on 2011-11-20
What i meant to say was as the code is "Open" can they get in to mess up stuff when it is on **your** machine?

P.S. Would it help encoding everything?

---

### Post by haqking on 2011-11-20
> **not unique said:**
> what i meant to say was as the code is "open" can they get in to mess up stuff when it is on **your** machine?

no, open does not mean the source code of your running operating system is open for the world to see remotely. Open means the source of the linux kernal is available for view if you want to see it, work on it, edit it, develop for it etc

---

### Post by del_diablo on 2011-11-20
> **Not unique said:**
> What i meant to say was as the code is "Open" can they get in to mess up stuff when it is on **your** machine?

P.S. Would it help encoding everything?

"Open" just means that if you leave a backdoor in the code, everybody will see it, and then exploit it, so you can't make that backdoor.
It also means that there might come somebody along, and see a obvious code flaw, and submit a patch or explaination on why its broken.

With "Closed" code, there may or may not be a backdoor, and you are at the mercy of the comapny to keep on providing you with properly patched code.
In both cases you are still at the mercy of whoever is providing the patches, but in the Open one, a small firm can at the least get their own software patched even if the provider refuses to do so.

---

### Post by Not unique on 2011-11-20
Thanks F.G. that was by far the best answer for my question although I still aren't sure that having the "blueprints" doesn't mean it's easier to get in and cause havoc.

---

### Post by haqking on 2011-11-20
> **Not unique said:**
> Thanks F.G. that was by far the best answer for my question although I still aren't sure that having the "blueprints" doesn't mean it's easier to get in and cause havoc.

just want to point out to FG (no disresepct)that his information on SELinux is incorrect and also that neither windows or linux is any more or less secure than each other as  i posted above.

Cheers

---

### Post by Dangertux on 2011-11-20
I'm going to play the devil's advocate here and serve up a nice hot FUD sundae real quick.  It is important to note that I am in agreement with haqking and whoever else said that Open Source does not make something inherently more secure than something else that is proprietary. Unless of course you're one of those "Microsoft is spying on me, WGA is evil." folks, in which case I'm just going to say security is not the same as privacy.

So now on to open source and the implications of Open Source software in terms of security. Many will argue that more developers will see the code, thus security flaws will be found quicker and patched sooner. Unfortunately that logic is terribly flawed. The opposite side of that coin is that security researchers and exploit developers (if there is a difference) also get to see the code more readily, and can find vulnerabilities faster than proprietary software. I will give an example here.

For instance, if one is attempting to find a memory corruption (buffer overflow) vulnerability in proprietary Windows software for which the source code is not available. They would do something like this. They would start up the software, and hook it with a debugger, they would than have to examine the functions available in the debugger. They are looking for a function that does not validate user input, which can be manipulated to allow code injection into the EIP register. If you've never done this I assure you it is a PAINFUL PAINFUL task. It could take days, and even if you find the right code, there is no guarantee it will yield code execution or anything other than a denial of service. So you may end up repeating the process all over again.

Now let's look at the same concept with Open Source software. Say we want to look for a simple overflow. We could download the source code, we could examine it looking for vulnerable functions.

So say we see something like

```

strcopy(password, argv[1]);

```We know that the secure version of this function is strcopy_s , so we know the above function is not performing bounds checking.

If we look to where password is defined we will see how much buffer we have to overflow. We can then test POC against it to ensure we have code execution, if not we can move to the next function much more easily.

So theoretically, the speed with which you can develop exploit code for Linux is increased proportially to the speed by which vulnerabilities are patched, and in the end neither method is inherently more secure.

Hope that makes sense.

EDIT: Also something to think about, precompiled proprietary software is more likely to have been compiled with compile/link time sanitization than software compiled by a user who does not have a QA/QC process and may be prone to human error like accidentally adding -fno-stack-protector (if you need proof of that check out ProFTP 1.3.2 in the Lucid repos)

---

### Post by Not unique on 2011-11-20
Dangertux that was a fantastic answer but not every one can code.
But how about this: would it be true to say that if a hacker or virus/malware happens to be attacking your machine then there is more chance of him/it being a success on a Windows machine for example? also attacking is more likely to ocur on a Windows machine?

---

### Post by haqking on 2011-11-20
> **Not unique said:**
> Dangertux that was a fantastic answer but not every one can code.
But how about this: would it be true to say that if a hacker or virus/malware happens to be attacking your machine then there is more chance of him/it being a success on a Windows machine for example? also attacking is more likely to ocur on a Windows machine?

read the posts above.

Neither is more secure than each other.

Viruses as yet do not exist as prolifically for Linux as they do for Windows, viruses are a small section of Malware in general however, both OS are attacked in multiple ways.

---

### Post by F.G. on 2011-11-20
> **haqking said:**
> just want to point out to FG (no disresepct)that  his information on SELinux is incorrect and also that neither windows  or linux is any more or less secure than each other as  i posted above.

Cheers
Haqking, as ever, thanks for correcting me. i've never really used a  security enabled system, so don't know much about it.  i did read  somewhere (possibly on this forum) that the NSA have now started using  Windows 7 and were involved in it's development, so my guess is that it must be fairly  secure.

Not unique, i don't know if this is helpful for you (if your worried about someone meddling with the source code of a program or OS that you are actually using then this may help):

Linux (like most OSs) is written in C, which is a  compiled language rather than a scripting or interpreted language or a markup language. the  significance of this is that the code cannot be changed once it has been  compiled. ie someone can't edit out or chuck a snippet of code into the  operating system source code (as you could if it was python, ruby or  html code) once it has been compiled (which usually happens before you get it, unless you opt to compile from source). Either way once it's running the source code cannot be altered.  so with regard to messing with the code that *your* system is actually using, that is not really possible.

---

### Post by haqking on 2011-11-20
> **F.G. said:**
> Haqking, as ever, thanks for correcting me. i've never really used a  security enabled system, so don't know much about it.  i did read  somewhere (possibly on this forum) that the NSA have now started using  Windows 7 and were involved in it's development, so my guess is that it must be fairly  secure.

Not unique, i don't know if this is helpful for you (if your worried about someone meddling with the source code of a program or OS that you are actually using then this may help):

Linux (like most OSs) is written in C, which is a  compiled language rather than a scripting or interpreted language or a markup language. the  significance of this is that the code cannot be changed once it has been  compiled. ie someone can't edit out or chuck a snippet of code into the  operating system source code (as you could if it was python, ruby or  html code) once it has been compiled (which usually happens before you get it, unless you opt to compile from source). Either way once it's running the source code cannot be altered.  so with regard to messing with the code that *your* system is actually using, that is not really possible.


Lots of Govt and other use Windows based OS, the fact that the NSA may use Windows (x) as its client OS in certain areas says nothing about security but more about functionality and ease of use for the end user.

It is not like they use Windows 7 for cryptanalysis.

Windows 7/Vista/XP or any other flavour, and Linux all have the same rough security certification from an architecture point of view.  You can harden and should harden your OS whatever it is, out of the box they are all pretty standard security wise and are geared for ease of use and functionality (if they hardened them anymore it would increase the security certification level) but that is not the intended market for the OS.

Whatever you use it needs to be hardened for your needs based on your apps and services and general use.

---

### Post by Dangertux on 2011-11-20
> **Not unique said:**
> Dangertux that was a fantastic answer but not every one can code.
But how about this: would it be true to say that if a hacker or virus/malware happens to be attacking your machine then there is more chance of him/it being a success on a Windows machine for example? also attacking is more likely to ocur on a Windows machine?


Well now you're talking about something different. The original question was is one more secure or insecure than another, to which I answered already. Now you're talking about the odds that someone is targeting your system (not yours specifically, yours as in the OS you use).

An exploit targeted at a Windows machine will most likely not work against the same application on a Linux system. It is in theory possible that if the payload and exploit were coded properly it COULD happen if the stars aligned properly and the attacker was the luckiest person on earth. But let's face it that's not a realistic situation. So no.

However that is only ONE aspect. We're talking simply about exploiting a piece of software there -- firefox, apache whatever... There is an entire spectrum of other really bad things that can happen to your internet connected Ubuntu/Linux open source powerhouse that people often times don't take into account. 

Here are some things that the Ubuntu/Linux community are LIKELY to run into that can easily compromise their systems. Usually due to a lack of understanding of how their operating system and others work. For instance, how many times have you seen "I don't need NoScript." Okay, it takes 2 seconds to download and about 10 minutes to configure. Everyone (windows linux mac whoever) has a browser, and they all speak javascript. If you're not putting time in here, you're exposing yourself to very common threats like XSS, CSRF, click jacking, clear clicking blah blah blah. In reality you're far more likely to run into something like that, then you are a targeted attack against your browser or a service running on your system. Those types of attacks are targeting things like your credentials for another site, or to carry out an action with your permission (even though you don't know you're giving it). That stuff is all over the place. It makes sense to spend time worrying about that.

Another common thing Ubuntu/Linux users love to do. Administer their system from elsewhere, using SSH or VNC, and for some reason often they think @g00dP455W0rd! is in fact a good password. It's not, it's easy to crack, and those services are cracked all the time. Open source / Closed Source, neither will protect your from weak passwords. 

Or how many times have you seen an "Anti Virus" advertisement that tells you, you have malware, and displays your C: drive. I know all of us Linux folks chuckle, and say "HAH I HAVE LINUX CAN'T GET ME." So be honest, how many clicked it just to revel in the fact that it can't hurt them anymore? It's okay we all do it... So for those same people who did that, did you consider this? What if the attacker made a pop-up that looked like windows, but when you click it actually has a simple javascript or php script that reads your browser header and redirects you to the proper exploit code for your operating system. Linux won't save you from that. Use common sense (and NoScript).

The bottom line is security is in the simple things. There are many exploitable vulnerabilities in Windows and Ubuntu alike, don't make yourself a victim to them by skipping the small stuff, and making assumptions about how Ubuntu protects you.

---

### Post by Not unique on 2011-11-20
Thanks every one that's a lot to be going on with so I will mark the thread closed.
Thankyou all.

---

