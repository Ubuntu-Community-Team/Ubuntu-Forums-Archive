---
title: "Do Linux supercomputers need an antivirus?"
date: 2011-03-22
forum: Recurring Discussions
---

### Post by brawnypandora0 on 2011-03-22
I know the average desktop user with Linux doesn't need an antivirus, as the people on this forum keep saying, but what about the government with supercomputers with sensitive information on them? 

I heard that last year's Stuxnet attack on Iran's nuclear program affected mostly some lower end computers using Windows but some Linux computers were affected too.

---

### Post by 3Miro on 2011-03-22
No, Linux computers don't need AV. Only windows computers need AV.

You have to understand how flawed the idea of AV is. Windows has a known problem and you have to install some third party program to keep you safe. On the other hand, if Linux has a known problem, the problem is fixed and all users get a security update.

AV software does provide a few extra protections (depending on the software), however, under Linux, those are covered by AppArmor or SELinux. Ubuntu comes with AppArmor installed by default, other distributions come with either that or SELinux.

---

### Post by sudosuperuser on 2011-03-22
I beg to differ. Linux computers *may* need AV software, as they very often interact with Windows machines (albeit in a server or peer capacity), and although immune to Win virii themselves, they can still be a conduit for transmitting aforementioned Win virri to Win boxes.

Kapish? :)

---

### Post by NCLI on 2011-03-22
> **brawnypandora0 said:**
> I know the average desktop user with Linux doesn't need an antivirus, as the people on this forum keep saying, but what about the government with supercomputers with sensitive information on them? 

I heard that last year's Stuxnet attack on Iran's nuclear program affected mostly some lower end computers using Windows but some Linux computers were affected too.

[STUXNET did not attack any Linux installation, nor could it.]("http://en.wikipedia.org/wiki/Stuxnet") It was designed specifically to bring down a custom-written Windows application used by Siemens for its control hardware.

---

### Post by cariboo on 2011-03-22
> **sudosuperuser said:**
> I beg to differ. Linux computers *may* need AV software, as they very often interact with Windows machines (albeit in a server or peer capacity), and although immune to Win virii themselves, they can still be a conduit for transmitting aforementioned Win virri to Win boxes.

Kapish? :)

Isn't that why Windows users run av software for?

I fell that we as Ubuntu users have no need to babysit windows users.

---

### Post by dmn_clown on 2011-03-22
> **3Miro said:**
> No, Linux computers don't need AV. Only windows computers need AV.

This attitude is contributing to the explosion of malware written for Android.  If you are connected to a network, you can be vulnerable no matter what operating system you are using.  

Both Red Hat and Fedora have had fairly serious security breaches in the last few years.

---

### Post by wojox on 2011-03-22
> **brawnypandora0 said:**
> but what about the government with supercomputers with sensitive information on them? 
[QUOTE=3Miro;10589738]SELinux[/QUOTE]

NSA, DoD

---

### Post by 3Miro on 2011-03-22
> **dmn_clown said:**
> This attitude is contributing to the explosion of malware written for Android.  If you are connected to a network, you can be vulnerable no matter what operating system you are using.  

Both Red Hat and Fedora have had fairly serious security breaches in the last few years.

We are not talking about the ability to breach a system, but what it needs for security. If your system has an issue, then you should fix it as opposed to patch it with third party software.

Android and Fedora should fix their problems and not wait for someone else to make a program that "patches" the issues. The problem is not whether or not security vulnerabilities exit, but how you fix them. There is no Linux AV software for Linux "viruses".

Also, it is a good idea to put AV software on Linux interacting with Windows only because of Windows. In a pure Linux environment, you don't need AV.

---

### Post by wojox on 2011-03-22
Nevermind

---

### Post by Spice Weasel on 2011-03-22
I can't remember where I read it, but I'm fairly sure that the U.S Department of Defence are Red Hat's biggest customer. So yeah, SELinux.

---

### Post by jennybrew on 2011-03-22
> **3Miro said:**
> No, Linux computers don't need AV. Only windows computers need AV.


I believe there currently are no Linix virus in the wild. Please remember though that not all malware or malicious code is virus.
Linux is most definitely not immune to malware per se. Our favourite Operating System has proved to be particularly vulnerable to worms and Apache, for example, has suffered considerably from Open SSL buffer overflow exploits when running on Open Suse, Mandrake, Slackware and Debian (yes Debian)
However, its true to say that, so far, Linux has proved more secure than Windows. This often attributed to its architecture and system of permissions ... i.e the malware finds it difficult to gain root access.
I have also seen an Ubuntu system pumping out spam e-mail, as a result of infection, like there is no tomorrow. So we dont really have grounds to be smug about security.
The best way to be safe is to act sensibly when using your computer.
Take a look at this neat Wiki [http://en.wikipedia.org/wiki/Linux_malware](http://en.wikipedia.org/wiki/Linux_malware)

---

### Post by cloyd on 2011-03-22
I have had my web browser hijacked using Ubuntu. I had to reboot w/o an internet connection to get control of my machine. But,  to my knowledge never a virus.

---

### Post by Dustin2128 on 2011-03-22
> **sudosuperuser said:**
> I beg to differ. Linux computers *may* need AV software, as they very often interact with Windows machines (albeit in a server or peer capacity), and although immune to Win virii themselves, they can still be a conduit for transmitting aforementioned Win virri to Win boxes.

Kapish? :)
Augh! VIRUSES is proper, not virii. Sorry, just a minor annoyance.

---

### Post by deconstrained on 2011-03-22
There are no viruses on Linux. There may be rootkits and security exploits but no malware; to work it'd have to be tailored to the system.

At [NAS](http://www.nas.nasa.gov/) the computers are kept within an inaccessible enclave that can only be accessed through a secure front-end that requires 2-factor authentication. Additionally, the systems are regularly monitored for tampering or attempts to crack passwords, install rootkits, etc. In short, they take security very seriously.

---

### Post by Shining Arcanine on 2011-03-23
> **brawnypandora0 said:**
> I know the average desktop user with Linux doesn't need an antivirus, as the people on this forum keep saying, but what about the government with supercomputers with sensitive information on them? 

I heard that last year's Stuxnet attack on Iran's nuclear program affected mostly some lower end computers using Windows but some Linux computers were affected too.

Linux systems by definition were unaffected by Stuxnet.

---

### Post by Shining Arcanine on 2011-03-23
> **deconstrained said:**
> There are no viruses on Linux. There may be rootkits and security exploits but no malware; to work it'd have to be tailored to the system.

At [NAS](http://www.nas.nasa.gov/) the computers are kept within an inaccessible enclave that can only be accessed through a secure front-end that requires 2-factor authentication. Additionally, the systems are regularly monitored for tampering or attempts to crack passwords, install rootkits, etc. In short, they take security very seriously.

[http://en.wikipedia.org/wiki/Linux_malware#Viruses](http://en.wikipedia.org/wiki/Linux_malware#Viruses)

And they are called virii, not viruses.

---

### Post by jennybrew on 2011-03-23
> **Shining Arcanine said:**
> [http://en.wikipedia.org/wiki/Linux_malware#Viruses](http://en.wikipedia.org/wiki/Linux_malware#Viruses)
 
And they are called virii, not viruses.
 
[http://en.wikipedia.org/wiki/Plural_form_of_words_ending_in_-us](http://en.wikipedia.org/wiki/Plural_form_of_words_ending_in_-us)
 
For your information :)

---

### Post by wizard10000 on 2011-03-23
> **cariboo907 said:**
> Isn't that why Windows users run av software for?

I fell that we as Ubuntu users have no need to babysit windows users.

If *you* forward malware to a Windows user how is it babysitting them?  A lot of malware authors *use* virus scanners to help create their malware - it's not done until it either disables or bypass a virus scanner.

I run clamav on all my machines.  The freshclam daemon takes up about half a megabyte of memory and if someone can't spare that maybe they need a hardware upgrade  ;)

---

### Post by 3Miro on 2011-03-23
> **jennybrew said:**
> I believe there currently are no Linix virus in the wild. Please remember though that not all malware or malicious code is virus.
Linux is most definitely not immune to malware per se. Our favourite Operating System has proved to be particularly vulnerable to worms and Apache, for example, has suffered considerably from Open SSL buffer overflow exploits when running on Open Suse, Mandrake, Slackware and Debian (yes Debian)
However, its true to say that, so far, Linux has proved more secure than Windows. This often attributed to its architecture and system of permissions ... i.e the malware finds it difficult to gain root access.
I have also seen an Ubuntu system pumping out spam e-mail, as a result of infection, like there is no tomorrow. So we dont really have grounds to be smug about security.
The best way to be safe is to act sensibly when using your computer.
Take a look at this neat Wiki [http://en.wikipedia.org/wiki/Linux_malware](http://en.wikipedia.org/wiki/Linux_malware)

The OP question and the entire point that I was making is that: Linux distributions do not need AV! Furthermore, Linux distribution will never need AV!

Security under Linux is handled in a completely different way. While it is not perfect, it is superior to Windows.

---

### Post by sydbat on 2011-03-23
> **wizard10000 said:**
> If *you* forward malware to a Windows user how is it babysitting them?It is not my responsibility (or yours, or anyone else) to perform security for someone else. Unless they ask me set it up on their computer (and pay me for it), it is **their** responsibility to have a secure computer. That is what is meant by 'babysitting'.

---

### Post by wizard10000 on 2011-03-23
> **sydbat said:**
> It is not my responsibility (or yours, or anyone else) to perform security for someone else. Unless they ask me set it up on their computer (and pay me for it), it is **their** responsibility to have a secure computer. That is what is meant by 'babysitting'.

Now this is getting interesting  ;)

Is it your responsibility to insure you don't send malware to someone else?

---

### Post by 3Miro on 2011-03-23
> **wizard10000 said:**
> 
Is it your responsibility to insure you don't send malware to someone else?

1. I don't send malware on purpose.
2. My machine is secure.
3. If your machine requires extra/different protection, it is not my problem.  When I am not using Windows at all, I don't have to know/understand or even care about Windows security. Furthermore, good protection on your end should be enough to defend against anything I can send you in an e-mail.

---

### Post by deconstrained on 2011-03-23
> **Shining Arcanine said:**
> [http://en.wikipedia.org/wiki/Linux_malware#Viruses](http://en.wikipedia.org/wiki/Linux_malware#Viruses)

And they are called virii, not viruses.
From the very same page, just before:
[quote=en.wikipedia.org]The following is a partial list of known Linux malware; however, few if any are in the wild, and most have been made obsolete by updates. [/quote]

---

