---
title: "virus protection"
date: 2008-09-24
forum: Recurring Discussions
---

### Post by sdybruce on 2008-09-24
I am new to using ubuntu and just installed it. Do i need to install a firewall and virus protection.
Thanks

---

### Post by pvella on 2008-09-24
My understanding is that it is not really necessary since the operating system is not as susceptible to viruses as windows.  If you connect to the internet via a router, then you already have a firewall.  Linux has an inbuilt firewall program called ipchains, and you can get software like firestarter to run it in a GUI, but I don't think it is really necessary.

Correct me if I am wrong here....

---

### Post by brnetonboy on 2008-09-24
You wont need virus protection in Linux--it is inherently more secure and it is also targeted much less than Windows. I have never heard of any Linux virus... 

What you should worry about instead is messing up the system yourself. If you are looking for help on the internet and someone tells you to type something into your shell, there is a chance that it could be a command to delete your hard drive or something like that. So be aware of what you type in--get an idea of what sort of commands might do damage and be careful what you type in--if you don't have a good idea of what it does and you don't trust the person it came from, be careful!

---

### Post by lisati on 2008-09-24
There isn't the same need for antivirus protection with Ubuntu as there is with Windows. Have a look [here]("http://ubuntuforums.org/showthread.php?t=510812").

If you choose to install the free version of AVG antivirus (yes, there is an Ubuntu-friendly version), you will need to add your admin account to the avg user group to be able to do the online updates easily. (This is described in the AVG documentation)

BTW, I think Ubuntu uses iptables, not ipchains.

EDIT: having anti-virus or similar is usually more of a courtesy to Windows users you might be in contact with: you don't want to accidentally send something nasty off to other people

---

### Post by tuxxy on 2008-09-24
Yes and I would use ufw not firestarter, would only need anti-virus software if your regularly sharing files with or accessing a windows drive, this would be prevention of spreading virii really.

---

### Post by Ptero-4 on 2008-09-24
The firewall comes installed by default, just that you don´t have a GUI for it installed but you can install it (firestarter for ubuntu and xubuntu, kguarddog for kubuntu). Antimalware isn´t needed as of now, unless you use your computer to relay files/mail to windows computers, in that case installing clamav would be handy to keep from unknowingly "tunneling" malware to the windows computers.
BTW: Ubuntu uses ufw as it´s firewall (firestarter is only a GUI, it work´s with whichever firewall daemon (ufw, iptables, etc) is installed).
BTW2: most distros use iptables, ipchains was deprecated around kernel 2.0

---

### Post by bodhi.zazen on 2008-09-24
Security id very different in Linux then Windows.

See : 

[Ubuntu Security - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=510812") 

[[all variants] Intrusion Detection - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=919472")

---

### Post by sdybruce on 2008-09-24
Thank you all
I understand now. 
It is  a lot smarter approach to safety with this operating system

---

### Post by martin_h on 2008-11-01
> **lisati said:**
> 
If you choose to install the free version of AVG antivirus (yes, there is an Ubuntu-friendly version), you will need to add your admin account to the avg user group to be able to do the online updates easily. (This is described in the AVG documentation)


EDIT: having anti-virus or similar is usually more of a courtesy to Windows users you might be in contact with: you don't want to accidentally send something nasty off to other people

I am traveling a lot so I needed to find a way to have my wife installing avg free on her laptop. I decided to write it up as it may be useful for newbies. Perhaps not strictly the way to do it, but it worked for us. 


The Easy installation of AVG antivirus free on your Ubuntu can be done as follows if you are not happy using terminal:

go to < system < administration < synaptic package manager , search for < dazuko >. This will find a package called < klamav>, which contains dazuko, an application that is also required by AVG.  Install klamav and its dependencies. 

Open up your browser and go to [http://free.avg.com/download?prd=afl]("http://free.avg.com/download?prd=afl")  and download AVG free for linux / ubuntu. Default this is downloaded to the desktop. When the download finishes,go to the desktop and double click on the file to open it with Gdebi package installer.  Install the file and reboot the system.

Now there should be under  >applications>Accessories  a new entry called AVG Linux for workstation. If its there installation worked. 

To set the permission for the programme go to: > System > administration > users and groups. Press unlock and type the password.  Got to ¨ manage groups ¨ and find the entry ¨avg¨, which is usually the last in the list.  Click on it and then press ¨ properties¨, mark all users as group member, press OK and close the dialogue box.  Reboot your computer and set up AVG as you want it to work.

---

