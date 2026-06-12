---
title: "adifference between a Linux and Microsoft in terms of protection and safety?"
date: 2010-01-02
forum: Recurring Discussions
---

### Post by 0712081 on 2010-01-02
Is there a difference between a Linux and Microsoft in terms of protection and safety???

---

### Post by 0712081 on 2010-01-02
> **0712081 said:**
> [SIZE=5]Is there a difference between a Linux and Microsoft in terms of protection and safety???[/SIZE]
 
 
thank you...

---

### Post by YosefKaro on 2010-01-02
Linux is designed to be secure from the beginning.  It doesn't have all of the security leaks that Windows has.  Ubuntu comes with a strong firewall but even that by default is disabled so it's a safe bet to say that many if not most users are using linux without a firewall and without any AntiVirus.  Linux can still carry a virus and infect your windows using friends so for that reason, I have an anti-virus; I use Bit Defender for linux.  I also have my firewall enabled.

-Yos

---

### Post by Methuselah on 2010-01-02
There are fewer linux viruses and programs cannot generally completely trash your system without being given admin rights.
However, one cannot stop a user who can use 'sudo' from installing malware.

What this means is that you still should not take security for granted.
Prefer to install applications from the software center and trusted repositories.
Be careful (and generally avoid) downloading programs from web pages and running them unless it is from a trusted project.

Safety precuations still apply in the Linux world.

---

### Post by s.fox on 2010-01-02
Hello,

[Here]("http://www.psychocats.net/ubuntu/security") is a very nice article on the subject of security.

-Silver Fox

---

### Post by Kevbert on 2010-01-02
Linux viruses are generally theoretical and security patches for programs appear in advance of any real threat. Catching malware problems, rootkits are still a possibility. Any Windows targeted viruses that appear on a purely Linux machine will not (at present) effect the Linux files.
If you decide to emulate Windows (with Wine or DosBox for example to run Windows programs) you will need antivirus software (e.g. [BitDefender]("https://help.ubuntu.com/community/BitDefender") )
To stop rootkits there is rkhunter.
For general browsing there are programs such as Adblock Plus and NoScript (just go to Tools - Get Add-ons to find these in Firefox).
Firewalls such as [UFW]("https://wiki.ubuntu.com/UncomplicatedFirewall?action=show&redirect=UbuntuFirewall") (installed by default are worth using).
Please also take a look at [this]("https://help.ubuntu.com/community/InstallingSecurityTools").

---

### Post by 3rdalbum on 2010-01-02
> **Kevbert said:**
> 
Firewalls such as [UFW]("https://wiki.ubuntu.com/UncomplicatedFirewall?action=show&redirect=UbuntuFirewall") (installed by default are worth using).

UFW is not a firewall, it's a utility that allows you to configure a firewall.

A personal firewall, at that. You don't need a firewall on Ubuntu unless you have enabled any server services, because Ubuntu (unlike Windows) does not listen to any incoming ports by default.

---

### Post by pfranks on 2010-01-02
At a software and configuration level Linux should be more resistant to malware and users who know enough to be dangerous. Even the relative unfamiliarity of Linux can deter most Windows users from playing where they should not and breaking the security. However, neither system can put up much defense against a skilled user making a deliberate hands-on attack at the keyboard. 

Both have a similar risk level when it comes to social engineering and human stupidity (assume same user). The primary protection in this respect is the relative scarcity of vulnerable Linux systems with dumb users, so the Bad Guys tend to go after the more frequently encountered Windows target.

Finally... the security bugs and patches issue. Linux has a reputation for prompt fixes when a problem is discovered and Windows typically waits rather longer before a patch is released. However, (1) the majority of security failures I encounter on Windows systems result from failure to apply patches (or antivirus updates) which were released months or even years ago. Once again the human factor is the weakest link.

However (2) the scary element for patches and bug fixes is not the known defects, it's the defect the bad guys find and exploit first. The best defence against this is a layered defense so penetrating one layer doesn't open the entire system. Linux is generally considered more capable of this kind of defense, but it could be that users are more security-aware and more likely to make effective security configurations. The majority of Windows users run the default install, add antivirus and then think they are safe :(

Does that make sense? Either system *can* be secure, but it is more likely to find a vulnerable Windows system, and there is a higher probability that a Linux system will be managed by a security-aware user.

---

### Post by tom.swartz07 on 2010-01-02
I like to think of it in termsof how the OS operates. 
In Windows, every program installed on the computer interacts with the OS in some way. Most of the time, it's through the program registry, a database of every program and variable for the system. A malicious program could edit this registry and cause very serious problems, varying from strange desktop backgrounds to filling programs with errors. 
Linux foregoes this registry style and almost completely seperates the OS fromthe programs running. This allows a Linux computer the ability to handle potentially maliciuos programs without it bringing the system down. 

Ina nutshell, Linux just simply handles programs in a safer way than Windows.

---

### Post by tilixibr on 2010-01-02
Linux viruses are very rare since Linux is structured in such a way that is very hard for them to screw up your system, unlike Windows...:?

---

### Post by alakazam on 2010-01-02
Refreshing thread. Utterly gob smacked.

---

### Post by starcannon on 2010-01-02
All operating systems have their glaring flaws; unfortunately for Microsoft, their biggest flaw, in my opinion, is the lack of security. With that said, I do realize that Microsoft has been addressing this issue, and I look forward to seeing if life improves for the millions of Windows7 users who continue to run with admin privileges.

I think really the problem has a few heads on it, Microsoft Windows Users do not understand security(as a generalization). The idea of a separate admin account does not occur to them as a general rule. The other problem, and this affects ALL operating systems, are the users who are completely willing to install software from unknown/untrusted sources; honestly folks(and you know who you are), DON'T DO THAT! Finally, while all operating systems have their inherent security holes, Microsoft has a plethora of them, and they are generally not obscure holes, and they are not generally patched until after the "OMG half the planet is now part of a botnet**™**" problem rears its head.

OSX and Linux seem to be more on top of things regarding security, and they both seem to be a bit more secure right out of the box.

Ultimately, all operating systems have the potential to be locked down to a sane level of security, so really, regardless of what OS you use, YOU must be the one responsible for the security, and knowledge to provide that security to your computers and various assorted connected systems.

GL and Use the right tool for your particular job or jobs.

---

### Post by slooksterpsv on 2010-01-02
Well here's the difference from Windows and Linux on my computer:
--Windows--
Updates - Every day
Antivirus - Updates every day as well.
Firewall - On, but still weak.
Drivers - Updated once every month or so
Programs - Installed and uninstalled make the computer slow down.
Performance Utilities - Use them once a week or every couple of days to keep it performing well.

--Linux--
Installed, updated, enjoying
I don't use Antivirus
I don't use firewall
I don't update drivers
I install and uninstall programs, without system impact.
Performance Utilities - don't use, have tons of HDD space left

[PHP]
shawn@shawn-desktop:~/Downloads$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sdb1            147897080  27751040 112633248  20% /
udev                   1030284       296   1029988   1% /dev
none                   1030284       944   1029340   1% /dev/shm
none                   1030284       200   1030084   1% /var/run
none                   1030284         0   1030284   0% /var/lock
none                   1030284         0   1030284   0% /lib/init/rw
shawn@shawn-desktop:~/Downloads$ 
[/PHP]

Yeah only 20% used of a 160GB HDD, windows on a 250GB, I have about 60gb free.

Linux Rocks!!!

---

