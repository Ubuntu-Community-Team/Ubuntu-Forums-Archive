---
title: "A Good antivirus for Ubuntu?"
date: 2015-05-25
forum: Recurring Discussions
---

### Post by Francesco_Verlato on 2015-05-25
Good morning, i'm new in the Ubuntu world and I need a good antivirus for my pc, can anyone help me? Thanks in advance

---

### Post by monkeybrain20122 on 2015-05-25
You don't need antivirus in Linux, including Ubuntu. Some people install AV as a way to protect Windows users but I totally disagree with that. Windows users should install AV on their ends, it is not my job to babysit them.

---

### Post by Francesco_Verlato on 2015-05-25
Ok thanks a lot, but there are viruses or malware on Ubuntu?Because I often use the computer to make payments and I would not have a problem ...

---

### Post by iamjiwjr on 2015-05-25
In 13 years of using Linux on my desktop and reading bazilions of articles and forum entries and blogs, I've never heard of a desktop user having to deal with a virus. I know it's counter intuitive, but Windows and it's wide open border is the biggest part of the problem, not computing itself. Linux is a small slice of the desktop pie for one thing. And two, it's very difficult to construct a Linux-effective virus, much less one that can spread on any kind of scale. Email is likely the biggest vulnerability we all have. Don't open any email you don't recognize. It just takes one. But even then it's likely designed for the easy pickings of Windows. Payment information out on the internet is fair game, at least once it leaves your computer, but not so much on your end with a desktop Linux system.

Of course the rule of thumb with the press is - it's never as bad as they say it is nor as good as they say it is.

---

### Post by uRock on 2015-05-25
I haven't used any anti-virus softwares in Ubuntu for quite some time, so I can't recommend one. 

The most import thing I can think of, as it applies to browsing security, is to keep the system up to date. Google and Mozilla are always finding and fixing browser security issues.

---

### Post by etescartz on 2015-05-25
If you really want to tackle the antivirus security software , I recommend using ClamAV and LMD - Linux Malware Detect(both of which you will have to configure yourself or look for best practice configuration options). Otherwise , for using a brand name antivirus , Bitdefender, Kaspersky,  Comodo , Eset -NOD32 and even Avast and AVG have linux versions. 

Some of these are useful as 3rd party  LivceCD scanners which you can boot your computer of of and do a scan of desired disks without booting into your installed operating system.That way you can make sure there is no malicious software running in the background or still hidden in your OS's memory.

I recommend installing or running these inside virtual machines to get a feel of how they act / look  without messing up you host computer installment.

Remember though it's all about perception. The more you learn about Linux best security practices, you'll find that there might not be a need for these products in your daily computing needs.

---

### Post by HermanAB on 2015-05-25
Howdy,

The Linux ecosystem has a different mindset than the Windows ecosystem.  On Linux, if a piece of malware is identified, the exploit is fixed within minutes, thus rendering the malware ineffective.  On Windows, when malware is detected, effort is expended by commercial 3rd parties in blocking the malware, not on fixing the actual problem and MS may publish a fix 20 or so years later, if they can ever be rsed to.

So, if you are worried, keep auto-update turned on.  That is effectively the Linux anti-virus system.

---

### Post by monkeybrain20122 on 2015-05-25
Also in linux you tend not to download random software from the internet. In Windows it is a sport.

---

### Post by Francesco_Verlato on 2015-05-26
Thanks everyone, I'll be careful, but be aware that many malware not work reassures me, thank you very much to all):P

---

### Post by Habitual on 2015-05-26
If you can afford it, buy a router.
Install, configure and use NoScript and AdBlock* (firefox addons).
Stick to the repositories.
Update often.

---

### Post by portalhavoc on 2015-05-26
I don't think an anti-virus is necessary on Ubuntu. 

Because Linux is designed to be "**Virus Free**".

---

### Post by iulian X on 2015-09-10
> **Francesco_Verlato said:**
> Ok thanks a lot, but there are viruses or malware on Ubuntu?Because **I often use the computer to make payments** and I would not have a problem ...

This is the safest solution for online payments and internet banking.

[http://ubuntuforums.org/showthread.php?t=2286465&p=13328992#post13328992](http://ubuntuforums.org/showthread.php?t=2286465&p=13328992#post13328992)

---

### Post by ventrical on 2015-09-10
> **Francesco_Verlato said:**
> Good morning, i'm new in the Ubuntu world and I need a good antivirus for my pc, can anyone help me? Thanks in advance

Here I find is the best with real time on access scanning (guard) but notice it says  ubuntu 12.04 so I am not sure it will work with trusty. edit: Yes .... works with trusty fine.

 [URL="https://www.comodo.com/home/internet-security/antivirus-for-linux.php?track=2738&key5sk0=2738&key5sk1=0c434604543cf17c980e1ac91624c44f1946b642"]https://www.comodo.com/home/internet-security/antivirus-for-linux.php?track=2738&key5sk0=2738&key5sk1=0c434604543cf17c980e1ac91624c44f1946b642


[/URL]

---

### Post by finmekingz on 2015-09-10
The only things u need in Linux is only a good firewall iptables setting that all.

---

### Post by robboguy on 2015-11-12
Rarely seen but there are malware for Linux in the wild: [http://arstechnica.com/security/2015/11/new-encryption-ransomware-targets-linux-systems/](http://arstechnica.com/security/2015/11/new-encryption-ransomware-targets-linux-systems/)

---

### Post by Writh on 2016-03-26
A bit of necromancy, but topic is appropriate:
[https://www.av-test.org/en/news/news-single-view/linux-16-security-packages-against-windows-and-linux-malware-put-to-the-test/](https://www.av-test.org/en/news/news-single-view/linux-16-security-packages-against-windows-and-linux-malware-put-to-the-test/)

---

### Post by bashiergui on 2016-03-28
> **HermanAB said:**
> The Linux ecosystem has a different mindset than the Windows ecosystem.  On Linux, if a piece of malware is identified, the exploit is fixed within minutes, thus rendering the malware ineffective.  On Windows, when malware is detected, effort is expended by commercial 3rd parties in blocking the malware, not on fixing the actual problem and MS may publish a fix 20 or so years later, if they can ever be rsed to.<Timewarp rant>This was completely wrong a year ago, still wrong today. Malware exploits vulnerabilities. As vulnerabilities are discovered, software developers release patches. When they find vulnerabilities being exploited by malware, they publish critical security patches. If you update your software often (Windows or linux), then the malware will fail. The entire process is similar for Windows and Linux. To say Microsoft isn't publishing fixes for 20 years is ludicrous and totally incorrect.</Timewarp rant>

[quote=HermanAB]So, if you are worried, keep auto-update turned on.  That is effectively the Linux anti-virus system.[/QUOTE]This is actually good advice. If you remove vulnerabilities (by updating) so malware can't exploit them, then you are much more secure. True for Windows and linux.

---

### Post by cariboo on 2016-03-28
Moved to recurring.

---

### Post by sammiev on 2016-03-28
Programs like Firefox can get malware and key-loggers.

I like [Sophos]("https://www.sophos.com/en-us/products/free-tools/sophos-antivirus-for-linux.aspx") for Linux and it's free.

You need to run everything from the command line but it's very easy to use.

---

