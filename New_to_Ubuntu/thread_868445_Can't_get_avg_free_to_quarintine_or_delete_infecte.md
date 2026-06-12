---
title: "Can't get avg free to quarintine or delete infected files"
date: 2008-07-23
forum: New to Ubuntu
---

### Post by iansane on 2008-07-23
Hi, I just installed avg free for Linux and scanned a mounted windows drive.
It found the usual trojan downloaders and stuff that people get from websites and P2P. It showed me the path but did nothing to them.

After reading some in the manual, I edited the avg.conf file and set the quarantine path and set the onVirusAction = 1 which tells it to move the infected file to quarantine.

Nothing changed. I'm running as sudo and I edited and saved the conf file as sudo, so I can't figure out why it isn't working.

I see there is a command line quarintine config tool but I don't understand any of the options like what is a regular expression? I've had problems with that one before cause I don't know what the expression is.

Anyone use avg and can tell me how to set up quarantine?

Thanks

---

### Post by Dark_Stang on 2008-07-23
AVG is not a good antivirus. If you see the paths to the files, just delete them yourself. However I recommend getting a better antivirus for windows rather than scanning through Linux. Kaspersky, Trend Micro, or Nod32 would do very well. These are not freebies, however there is not a good free antivirus.

---

### Post by iansane on 2008-07-23
well I have to disagree. I use avg because it has gotten rid of viruses in windows many times for me when kapersky and Norton paid versions did not.

Another reason I am scanning from linux is that (tested and proven in my opinion). I get better results scanning a drive that is not booted up. This way keeps viruses from rewriting as fast as the AV software deletes them.

I have scanned systems only to see the harddrive running crazy cause certain system processes are infected and causing the virus to rewrite. When I unplugged it and scanned as an external drive it fixed the problem.

Anyway, I found the avgscan -clean command which supposedly creates a folder $vault$.avg in my home directory and moves them there if it can't heal them. Now I can't find a $vault$.avg folder and I don't know what those $$ mean.

---

### Post by iansane on 2008-07-23
well it worked like it said. All the viruses are gone. I just can't find that $vault$.avg folder it said they are in so I can delete them from my linux system. They are supposed to be encoded avg files so they can't harm anything but I don't like them being there at all

---

### Post by Dark_Stang on 2008-07-23
I understand how virus scanning works. That is why my employer has created their own set of tools for virus removal. All our scans run in our own special environment so reinfection doesn't happen. My grudge against AVG (and Avast) is fairly simple. I use to swear by these programs. However, since last August I've seen about 3 machines every week with AVG or Avast on them reportedly being clean, but actually being highly infected (blatently obvious trojans, Antivirus2008 variants, etc).

I'm sure you've heard this before but, the only way to be completely safe is... not to use windows. You may want to recheck AVG with some other software though. You may be surprised.

Edit: Oh, but you should know. No Antivirus or Antispyware software cleans everything.

---

### Post by iansane on 2008-07-24
Good point and thanks Dark_Stang for the response. I've heard other people say the same thing about different AV programs. I guess it depends on what virus/trojan your infected with and whether your AV company has updated the definitions for something new at the time you need it to be. I really don't understand much about virus removal. I was just saying what I had tried and why I think it seems to have worked in the past. You are right that I should check it with another AV to make sure now.

I agree with not using windows but unfortunately I am trying to get MSCE certified and I'm in college. This is the second college where most of the classes and the online ecourse site they use supports the evil empire of Microsoft forcing me to keep my windows machine. Also, I can't get many people to switch to Linux of any distro because they hold on to there windows like a baby with a pacifier, scared to try something new. So when they need me to help them with something like viruses, I try different ways to clean them without having to format and reinstall. Heh, I was there not to long ago, scared of Linux.

---

### Post by anjilslaire on 2008-07-24
Let's also note that antivirus software is really only useful to quarantine the malware *before* it gets into the system (usually in a subdirectory of \%windir%\.

While antivirus apps are capable of removing the infected files once th system is compromised, that doesn't mitigate the fact that the system is just that: Compromised. Cleaning a system after th fact doesn't help this, and its anyone's guess what other malware has been introduced to the system. 

Once the compromise occurs, the only fool-proof method to ensure the system is secure is to format & reinstall Windows, and then restore your backups (if they are not also infected).

---

### Post by TBOL3 on 2008-07-25
I rarely use windows.  But I find AVG to be a good tool for the one boot up a month I have to do (for applications that requires windows).  But if I were permanently one windows, I'd get something better.

Also, I think firewalls are much more important then AV.  But do any of you know of any good ones in linux?

---

### Post by anjilslaire on 2008-07-25
Ubuntu has a built-in firewall by default known as iptables, but you can install a nice gui to manage it. Try firestarter in the repositories.

Note also that there are no extra ports open by default.

Also, its much easier to have a dedicated hardware firewall (usually within a router)

---

### Post by TBOL3 on 2008-07-25
> **anjilslaire said:**
> Ubuntu has a built-in firewall by default known as iptables, but you can install a nice gui to manage it. Try firestarter in the repositories.

Note also that there are no extra ports open by default.

Also, its much easier to have a dedicated hardware firewall (usually within a router)

Yup, I have a hardware one.  That's why I'm not too concerned about it right now.  But there are a few times I access the web without it.  But thanks.

---

### Post by duckfeet on 2008-07-25
I like Avira myself, which is free for anti-virus, and "pay" for the malware scan and such--(I have the premium on my spare XP HD)...today a friend says he has all these viruses and installed antivirus software, and it got worse, and what should he do?

I'm a bodysurfer, And I'm watching the nice waves we got here lately, but I go take a look hoping it *wasn't* the way it sounded, and as soon he turned on his Dell, all the typical pop-ups started popping up trying to sell him even more crap: this was first time I had ever seen 'antivirus2008' actually infect a computer, and he even showed me the bill he had printed up, as his girlfriend had sent this online ripoff not only 40 bucks, but another fifty bucks for "premium technical support."

And it was totally bogus, and I did what I could, but I have to get my Revo uninstaller and HiJackthis, and some other gear to try to get it all off: I also have Ubuntu 8.04 on my little keychain USB, and tried to talk him into that, but he didn't want anything so radical...

I went from Windows to Mac to now Linux...From lotsa daily hassles to very few...I use Opera browser, and Firestarter as firewall, and still have a wired router, so I feel way safe...

Windows.

---

### Post by Dark_Stang on 2008-07-26
> **duckfeet said:**
> I like Avira myself, which is free for anti-virus, and "pay" for the malware scan and such--(I have the premium on my spare XP HD)...today a friend says he has all these viruses and installed antivirus software, and it got worse, and what should he do?

I'm a bodysurfer, And I'm watching the nice waves we got here lately, but I go take a look hoping it *wasn't* the way it sounded, and as soon he turned on his Dell, all the typical pop-ups started popping up trying to sell him even more crap: this was first time I had ever seen 'antivirus2008' actually infect a computer, and he even showed me the bill he had printed up, as his girlfriend had sent this online ripoff not only 40 bucks, but another fifty bucks for "premium technical support."

And it was totally bogus, and I did what I could, but I have to get my Revo uninstaller and HiJackthis, and some other gear to try to get it all off: I also have Ubuntu 8.04 on my little keychain USB, and tried to talk him into that, but he didn't want anything so radical...

I went from Windows to Mac to now Linux...From lotsa daily hassles to very few...I use Opera browser, and Firestarter as firewall, and still have a wired router, so I feel way safe...

Windows.
If this is true I've got a 3 step solution for you.
Step 1: Smack friend for being dumb.
Step 2: Have friend take his computer into a repair shop. If it's that infected running 1 scan isn't going to clean it. And yes, I understand $100-$200 seems like a lot to have viruses removed, but if you bought all of the software most repair shops use you'd be spending over $600.
Step 3: Have friend cancel credit card and that payment to Antivirus2008.

---

