---
title: "How do I protect my PC..?"
date: 2009-08-25
forum: Recurring Discussions
---

### Post by bigtel on 2009-08-25
I am reletivly new to this operating system and I have just installed Xubuntu onto my laptop, but I want to be sure the information on my laptop is safe while I am connected to the internet.

Can you give me any general (and easy to understand) tips / guidelines on how to keep my information safe?

Am I at risk of the usual viruses and spyware?

Thanks.

---

### Post by MeumFidet on 2009-08-25
> **bigtel said:**
> 
 
Can you give me any general (and easy to understand) tips / guidelines on how to keep my information safe?
 
Am I at risk of the usual viruses and spyware?
 
 
Hi Bigtel,
 
I'm quite new to linux too, but as far as I can tell there are virtually no 'in the wild' virus's (virii?) that can harm your system...yet.   Mostly this is because virus writers target Windows systems that use the FAT disk system, whereas linux uses ext2/3/4 - meaning that a windows virus just cannot run on a linux system. So as long as your partitions use ext and not FAT, you are 99% safe immediately.
 
However, I am sure this will change as linux gains popularity. Also it doesn't stop someone from accessing your system from the net.  Ensuring your system is constantly up-to-date with the latest security patches, is the single best way to keep safe.  This thread: [http://ubuntuforums.org/showthread.php?t=1008906](http://ubuntuforums.org/showthread.php?t=1008906) shows you how to set up AppArmour on Ubuntu.
 
Hope this helps...
 
MF

---

### Post by denver on 2009-08-25
short answer: not really.

long answer:

There are many factors to take in consideration when talking about computer security, but on an average desktop PC running ubuntu (or most other linux distros), the most likely way i can think of that you might be at risk is if you install a service that allows remote user login (such as SSH) and you have a weak password (such as 123456).

Currently there are verry few viruses for linux out there, even fewer that actualy do some damage, and those have to be run as root or as a user with elevated privilages to do system wide damage.

Also, most linux desktops are multi user systems. That means that every user on the system has his/her own home directory which only they (and the root user) have access to. If...say Bob were to get infected, Jack would not be affected by any viri that might have gotten on his system, as the virus can only access files the infected user has access to.

If you get really really paranoid and you are afraid of potential malicious websites, you can run firefox in a chroot (its a sandbox, isolated from the rest of your system). You can search the forum on how to do so.

By default ubuntu does not listen for incoming connections on any external interface. So just idling connected to the internet does not present any risk. You really have to work at it to get infected or to compromise your data.

---

### Post by bigtel on 2009-08-25
I posted this question becasue I have always used a windows based system, but recently I had passwords stolen (I don't know how) and a number of virus infections which i can not seem to disinfect. I am moving over to Linux really becasue of these issues.

---

### Post by HermanAB on 2009-08-25
Howdy,

Ubuntu is secure out of the box.  If you did a default installation, then you can relax and enjoy your nice new system.  

You only need to raise your level of concern once you start to install servers like FTP, SSH, Samba, Apache, Postfix or whatever.  With the default install, don't worry about it.

---

### Post by scorp123 on 2009-08-25
> **MeumFidet said:**
>  meaning that a windows virus just cannot run on a linux system.  So far so good and so true ... BUT:

> **MeumFidet said:**
>  So as long as your partitions use ext and not FAT, you are 99% safe immediately. This is nonsense, I am sorry to say so. Whether or not a Windows virus can run or not has nothing to do with the file system that you use. It's the simple fact that viruses, just like any other program, are written for a specific target OS in mind. So if we're talking about a Windows virus then this thing basically is a Windows program. It was programmed for Windows and thus Windows is the only OS platform it can run on, regardless of the filesystem you use or don't use.

Windows viruses work perfectly well on Linux under WINE (some sort of API emulation layer that makes program think they're running inside a Windows installation) or any virtual machine (VirtualBox, VMware) ... it's only that they can't get out of that sandbox and do any real harm.

> **MeumFidet said:**
>  However, I am sure this will change as linux gains popularity.  This is nonsense too, sorry to say so. Linux *IS _already_* _**highly**_ popular: in the server rooms. It would definitely pay off to create spyware and go after all those fine servers insurances and banks have in their basement ... Except: Linux just like all UNIX-like OS'es has a different design than Windows when it comes to security (strict separation between what a user and his processes can do and not do!) making the life of  any wannabe virus extremely hard if not impossible. 

Human hackers are a real threat though, something you have to be aware of if you run servers.

But viruses? Forget it.


> **MeumFidet said:**
>  Ensuring your system is constantly up-to-date with the latest security patches, is the single best way to keep safe. That .... and knowing what you're doing. It does not help if you keep your system up-to-date but are daft enough e.g. to install programs such as the "Apache Webserver" in highly unsafe ways or if you leave your network shares wide open .... Always know what you do and why you do it.

Knowledge will keep you safe ... having up-to-date packages is just a welcome bonus. :D

---

### Post by rookcifer on 2009-08-25
^^^ What Scorp said.

OP, here are the basic steps a desktop user should take:

1) Never install software (.debs) from outside the official repositories.

2) Whenever the little update icon flashes in your taskbar, click it and let it update.

3) **Disable ssh** if you do not use it (I don't believe it listens by default anyway).

4) **Do not** install any servers like http, FTP, VNC etc. unless you have a good reason to.  And if you do, learn how to secure them.

5) Although only necessary if you have services listening to the Internet at large, you can use ufw/gufw (Ubuntu's firewall) if you just have to have a firewall.  Again, a firewall on the typical desktop box isn't a necessity.  There are no services listening to the Internet at large on a default Ubuntu install (that is unless you have installed servers of some sort).

6) If you really want to go to the next level, utilize AppArmor and make a profile for Firefox.  There is a sticky at the top of this forum detailing how.

7) ```
sudo apt-get install rcconf
``` and then type "sudo rcconf".  Go through the list of services and turn off what you don't need (I usually turn off things like Bluetooth, braile, etc.).  This isn't a necessity as none of the services listen to the Internet at large, but I like to know that no unnecessary services are running on my box (I guess I am a bit OCD).

8] Do not worry about malware or viruses.  They are not a threat and this talk of viruses and AV software only distracts new users from focusing on points 1-7.

Steps 1-4 are the most important and what one should focus on (especially steps 1-2).  Steps 4-8 are good practice but not of the utmost importance.

---

### Post by tubbygweilo on 2009-08-26
In addition to the advice outlined above It would also help if you have a system to backup your data but remember to test that you backup system functions as expected **before** you need to use it for real.

---

### Post by running_rabbit07 on 2009-08-26
Linux may be immune to Windows viruses, but we are carriers. If you share files with a Windows system, then you will want to run a virus scanner.

---

### Post by bigtel on 2009-08-26
Is there a virus scanner for Ubuntu?

---

### Post by denver on 2009-08-26
clamav is in the repos. There are more out there but clam is by far the most popular. There is also BitDefender, AVG and a few others. All linux ativirus programs have on-demand scanning. That means that you have to tell it which folder to scan whenever you wish to do so.

As the users above already said...you only need an antivirus if you are sharing files with windows PC's. Linux antivirus programs scan for windows virii (and the verry few impotent linux virii out there).

---

### Post by running_rabbit07 on 2009-08-26
> **bigtel said:**
> Is there a virus scanner for Ubuntu?

Go to System>Administration>Synaptic Package Manager and search ClamAV. Once you find it, check to install, click the install button at the top ans you'll be good to go. 

Make sure to update the program before each scan.

For more security info see the link in my signature.

---

### Post by MeumFidet on 2009-08-26
> **scorp123 said:**
> So far so good and so true ... BUT:
 
This is nonsense, I am sorry to say so. Whether or not a Windows virus can run or not has nothing to do with the file system that you use. 
 
I stand corrected...... BUT:
 
> **scorp123 said:**
> 
This is nonsense too, sorry to say so. Linux *IS _already_* _**highly**_ popular: in the server rooms.  
 
...agreed.  But I thought we were talking desktops here... and 99% (or whatever the statistic actually is) of desktops run windows - no matter what we, personally think of it.  *That* is where the majority of viruses occur, simply because it has a larger target audience.  I reckon when linux has a great enough audience, viruses will emerge that will present a problem to the average linux desktop user. 'Hope I'm wrong.
 
 > **scorp123 said:**
> 
That .... and knowing what you're doing. It does not help if you keep your system up-to-date but are daft enough e.g. to install programs such as the "Apache Webserver" in highly unsafe ways or if you leave your network shares wide open .... Always know what you do and why you do it.
 
 
I bow to your wisdom. :-)
 
Cheers,  MF

---

### Post by scorp123 on 2009-08-26
> **MeumFidet said:**
>  But I thought we were talking desktops here...  OK, true.


> **MeumFidet said:**
>  and 99% (or whatever the statistic actually is) of desktops run windows Personally I think that *this* number is vastly overblown regardless if you look at the home sector or at the business sector.

Think of it: How did they measure those 99%? By counting how many PC's got bought with Windows preinstalled vs. those with no OS or with Linux preinstalled? You and me know that measuring *that* would be silly from start. My PC too had Vista 64-bit on it when I bought it. It was simply too complicated and too much of a hassle to try and buy a system without any OS on it. So I went ahead and paid the stupid M$ tax which isn't much anyway (and plus: I already had received a 35% rebate on the price so I really didn't care anymore paying the M$ tax or not ...). But I assure you: Vista definitely isn't there anymore :D  .... I even removed the recovery partition. So my PC is guaranteed never ever to boot Windows Vista again. I assume that many 100'000 other people did the same: Yes, they sure bought a PC with a Windows OS on it. Yeah, right. But that does not mean that they keep the OS.

In my opinion the true percentage of Linux users is not really measurable. Even if we count all the users of all the Linux forums (Debian, Ubuntu, Fedora, OpenSUSE, Arch, Gentoo, ...) and all the accounts in the Linux-related IRC channels and USENET newsgroups and even if we manage to exclude double accounts and what not ... I'd be sure we'd still not really manage to get the real number.

Example: I am a Linux user since 1996 ... but until 2006 when I joined this forum I never ever engaged in on-line discussions. I was a happy lurker, AltaVista, Yahoo and now Google provided me with everything I ever wanted to know. 

How many Linux users are out there who never ever register anywhere, who lurk in the dark without ever entering into any kind of communication with the rest of us ...? My assumption is: LOTS!!

So really ... how in the world did Microsoft, Gartner, or any of those other consultant companies measure those 99%?

Look at this article:
[http://times.debian.net/1224](http://times.debian.net/1224)

That's the area in Switzerland where I live. And that's just one example, I see more and more similar examples every day on my job. Those 99% simply can't be true no matter how you turn those figures around.

And these guys here moved to OpenSolaris a few months ago:
[http://www.osor.eu/case_studies/open-source-on-the-desktops-of-the-swiss-federal-court-and-federal-administrative-court-organisational-challenges](http://www.osor.eu/case_studies/open-source-on-the-desktops-of-the-swiss-federal-court-and-federal-administrative-court-organisational-challenges)

OK, this is not Linux but still an OpenSource OS.

That's what I see day in and day out on my job: People and companies abandoning Microsoft in large numbers.

99%??? Don't believe in statistics you didn't fake yourself! :D

> **MeumFidet said:**
>   I reckon when linux has a great enough audience, viruses will emerge I keep hearing this since 1996. That's the year I switched to Linux. I am still waiting for something to happen. And I will still be waiting in another 13 years. Read my lips: It can't happen.

Unix-like systems had their share of virus waves ... ages ago. Like in the late 70's and early 80's. The reaction to that? All Unix-makers changed the design of their operating systems so radically that since then no virus has ever again made it anywhere. Linux and other modern Unix-like OS such as the various BSD variations profit from that directly and were designed in such ways that reflects those OS design changes too.

Compare that to Microsoft's typical reactions: Some security guru proves publicly that a network protocol that Windows uses is totally unsafe and extremely exploitable ... Microsoft's first reaction: They threaten the guy with a lawsuit. He won't shut up and goes public with his exploit. So now the script kiddies have it too. Microsoft's second reaction: They come up with various "firewall" tools and what not and they started producing this "Malware removal tool" that you get each month ... Did they remove the stupid unsafe protocol in question? NOPE. It's still all there in Windows. Windows is full with such crap.

See the different mind-sets?

> **MeumFidet said:**
>   that will present a problem to the average linux desktop user. The average Linux desktop user won't even notice. ***Even if ***(and that's a f****ing big "*if*" !!!) Linux were ever susceptible to any kind of virus ... Linus Torvalds will simply do what the other Unix makers did in the late 70's: He will change the OS in such a way so that the virus can't do anything anymore. Taddaaaaa ... Linux is immune. Again. And the "average Linux desktop" user will simply install the update that shows up in the update manager on the next morning and voila ... nothing to worry about. Again.

That's how it works right here, right now. And why stories that "Linux will get more viruses once it's popular" are just that: stories. Or wishfull thinking of certain Microsoft executives. But nothing more.

Sorry for this long posting. :D

---

### Post by rookcifer on 2009-08-26
Just to touch on the Windows market share -- M$ holds about 88% of the market on *desktops* (not 99%).  Apple products comprise over 10% of all Internet devices (iPhone included), and Linux is over 1% on the desktop right now.  

With Apple's almost 10% share on desktops/laptops, one has to wonder why there are virtually no viruses in the wild for that platform.  10% is not insignificant.  The same goes for Linux/BSD (which I think is more secure than OS X since Linux/BSD have package managers).  If only 1 out of a 1000 malware authors wrote for Linux, we should still see a good bit of malware out in the wild, **but we don't**.

---

### Post by aljoriz on 2009-08-27
For the truly, pardon the language, "paranoid" using an anti-virus for linux might have some of these drawbacks to consider:
a.  It might decrease boot time
b.  Most of them require knowledge of command line parameters.  

If you want a GUI based virus scanner than try AVAST for LINUX

---

### Post by wojox on 2009-08-27
I'm pretty sure clamav has a gui. ClamTk

---

### Post by aljoriz on 2009-08-27
that I better check.  does it run all time when you boot? I hate it when anti-viruses slows down a boot time

---

### Post by scorp123 on 2009-08-27
Those anti-virus solutions are scanning for Windows viruses anyway.

---

