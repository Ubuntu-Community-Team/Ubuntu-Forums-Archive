---
title: "How Do you protect Your Ubuntu System?"
date: 2013-02-16
forum: New to Ubuntu
---

### Post by gregoryshock on 2013-02-16
As a windows user I feel naked using Ubuntu.  How does one protect Himself from Viruses and Malware on the internet?  What are the things that exploit Ubuntu?

---

### Post by offgridguy on 2013-02-16
> **gregoryshock said:**
> As a windows user I feel naked using Ubuntu.  How does one protect Himself from Viruses and Malware on the internet?  What are the things that exploit Ubuntu?
Lots of reading here.

[[COLOR=Red]https://wiki.ubuntu.com/BasicSecurity[/COLOR]]("https://wiki.ubuntu.com/BasicSecurity")

---

### Post by DuckHook on 2013-02-16
I know the feeling well. I came to Linux after decades of Windows. At first, it's hard to believe that you don't need antivirus. Well, you don't. There's nothing complicated about it, so a simple answer suffices. You just don't.

Please see these threads. Very helpful to new users and explain in great detail about Linux security.

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)
[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)
[https://sites.google.com/site/easylinuxtipsproject/security](https://sites.google.com/site/easylinuxtipsproject/security)

This next will sound snarkey, but such is not my intent:

The single biggest security threat in Linux are new users themselves. This is especially true of Windows migrants who bring their Windows mindsets with them. They insist on installing antivirus, which is pointless worthless bloatware, yet, often in the same breath, insist on disabling passwords, which is at the heart of Linux security and the reason why they don't need antivirus. They also want to disable sudo, activate their root account, do everything as the root user... in short, they want to drag along the worst and most destructive habits of Windows. Candidly, if you insist on treating Linux like Windows, then it will become just as insecure and full of holes as Windows. No surprise there.

You feel naked, as I did at first, because Windows has conditioned you to think of the abnormal as normal. Welcome to Linux. Welcome to sanity.

---

### Post by gregoryshock on 2013-02-16
> **DuckHook said:**
> I know the feeling well. I came to Linux after decades of Windows. At first, it's hard to believe that you don't need antivirus. Well, you don't. There's nothing complicated about it, so a simple answer suffices. You just don't.

Please see these threads. Very helpful to new users and explain in great detail about Linux security.

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)
[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)
[https://sites.google.com/site/easylinuxtipsproject/security](https://sites.google.com/site/easylinuxtipsproject/security)

This next will sound snarkey, but such is not my intent:

The single biggest security threat in Linux are new users themselves. This is especially true of Windows migrants who bring their Windows mindsets with them. They insist on installing antivirus, which is pointless worthless bloatware, yet, often in the same breath, insist on disabling passwords, which is at the heart of Linux security and the reason why they don't need antivirus. They also want to disable sudo, activate their root account, do everything as the root user... in short, they want to drag along the worst and most destructive habits of Windows. Candidly, if you insist on treating Linux like Windows, then it will become just as insecure and full of holes as Windows. No surprise there.

You feel naked, as I did at first, because Windows has conditioned you to think of the abnormal as normal. Welcome to Linux. Welcome to sanity.

Guys thank you for the articles.  I am currently printing them.

I don't plan on disabling any password protection.  However I don't feel that I need the boot up password for logging in, because my computers are always at home, and there is no body here that wants to get on it and use it.

---

### Post by DuckHook on 2013-02-16
> **gregoryshock said:**
> ...However I don't feel that I need the boot up password for logging in, because my computers are always at home, and there is no body here that wants to get on it and use it.

Bad habits, my friend. One of the biggest problems with Windows was that it indulged bad habits. Ubuntu, in its default configuration, does not. Sign in passwords is a good example.

Again, I'm not picking on you. After all, you are thinking like the vast majority of Windows migrants. But consider:
1. You think of the three extra seconds needed for password login as highly inconvenient.
2. You consider the ten minutes of virus downloads and viral engine updates, followed by twenty minutes of viral scanning, HDD frenzy and halved system performance to be perfectly acceptable.

If someone were to offer me the choice, I'd pick system password login in a heartbeat.

It should be noted that login passwords are not just for fending off physical security risks. If your computer can be booted remotely, it is conceivable that a bad guy could install a Trojan that boots it up in the middle of the night, does what he wants it to do, and shuts down before you awaken in the morning. A login password places one more obstacle in the bad guy's path.

I'm probably coming across as a strident preacher, so I'll say one more thing and forever hold my peace:

A forum friend is fond of repeating the wisdom that security is not a program, but a process. It's a layering process wherein every security layer we add makes it that much tougher for bad guys to penetrate our systems. Every good habit of mind we learn makes it that much harder for bad guys to dupe us. Every good practice we implement makes it that much harder for bad practice to gain a toehold. The big software vendors and the antivirus cartel have duped the vast majority of people into believing that they've got a program that will take care of all of their problems for them. All you have to do is pay them an annual fee and they'll look after all of it for you. This has resulted in people thinking that if they've got antivirus loaded, they can act like fools. The Linux philosophy is the opposite. It operates on the premise that good judgment, good practices and good processes are the best sort of defence. So far, I think the facts bear out which approach is superior.

So, it's your call, as most things are in Linux. But I encourage you to start out the right way and enforce login security.

<edit>
Was cudgelling my aging brain trying think of a practical application for login password and finally remembered--without a login password you forego the ability to encrypt your home directory. In fact if you wish to encrypt *any* data directory, it requires a password to unlock. In such cases, it is actually easier to use login password, because the act of logging in unlocks all encrypted directories.
</edit>

---

