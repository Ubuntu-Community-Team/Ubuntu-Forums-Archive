---
title: "Firewall for Ubuntu?"
date: 2008-07-19
forum: New to Ubuntu
---

### Post by phantomjoker on 2008-07-19
Im a little paranoid seeming I switched to Linux after my Windows system took on an awful virus

- so I was wondering about firewalls for Ubuntu and any sort of anti-virus software that I could use?

I have heard a lot about IPTable firewalls and admit I lack any knowledge on them so if that is the recommendation then a small explanation may also be helpful.

I also should point out I have Avast! (anti-virus) on my PC but I worry it doesn't work so your help is *crucial*.

Thanks a lot

---

### Post by pikabuntu on 2008-07-19
> **phantomjoker said:**
> Im a little paranoid seeming I switched to Linux after my Windows system took on an awful virus

- so I was wondering about firewalls for Ubuntu and any sort of anti-virus software that I could use?

I have heard a lot about IPTable firewalls and admit I lack any knowledge on them so if that is the recommendation then a small explanation may also be helpful.

I also should point out I have Avast! (anti-virus) on my PC but I worry it doesn't work so your help is *crucial*.

Thanks a lot
you don't really need it...
linux is pretty secure

---

### Post by iaculallad on 2008-07-19
> **phantomjoker said:**
> Im a little paranoid seeming I switched to Linux after my Windows system took on an awful virus

- so I was wondering about firewalls for Ubuntu and any sort of anti-virus software that I could use?

I have heard a lot about IPTable firewalls and admit I lack any knowledge on them so if that is the recommendation then a small explanation may also be helpful.

I also should point out I have Avast! (anti-virus) on my PC but I worry it doesn't work so your help is *crucial*.

Thanks a lot

For the Firewall, I'd say [Firestarter]("https://help.ubuntu.com/community/Firestarter").
For the AntiVirus, I'd say [Clamav]("https://help.ubuntu.com/community/ClamAV").

But for me: I'd say, I don't need both of them. I'm secure when I'm logged using Ubuntu.

---

### Post by cpetercarter on 2008-07-19
You can download firestarter using Synaptic to configure the Ubuntu firewall. The default settings are very conservative and you are unlikely to need to change them. You do not need to install anti-virus software on Ubuntu.

---

### Post by Sef on 2008-07-19
Ubuntu comes with a command line firewall called IP Tables.  

> For the Firewall, I'd say Firestarter.

Firestarter is simply a front-end gui for IP Tables.

As for an anti-virus, one isn't needed unless you have a mail client.  The viruses won't affect Ubuntu, but can ride on top of it and can infect your friends who have windows.

---

### Post by phantomjoker on 2008-07-19
When you say

> I'm secure when I'm logged using Ubuntu.

What do you mean?

I know linux isn't prone to virus' but there are some out there - so is that what you mean or am I missing something?

---

### Post by hyper_ch on 2008-07-19
neither a firewall nor antivirus is normaly required.... besides, you already have a firewall installed (which actually doesn't filter anything).

Have a read [http://ubuntuforums.org/showthread.php?t=765421](http://ubuntuforums.org/showthread.php?t=765421) and [http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)

Don't install av or twinker with iptables before you don't actually thought about it whether you really need it.

---

### Post by phantomjoker on 2008-07-19
A little more detail please Sef?

sorry - im not sure what a > front-end gui for IP Tables. is?

thank you

---

### Post by Kevbert on 2008-07-19
There's a guide for IPTables [[COLOR="Red"]here[/COLOR]]("http://ubuntuforums.org/showthread.php?t=159661").

---

### Post by the_hardy_kid on 2008-07-19
You really don't need a firewall or antivirus protection.
But if you want, the above seem fine.

Sincerely,
Tyler

---

### Post by john.nicholls on 2008-07-19
The firewall I use is Shorewall. It sets up an IPtables based firewall in a relatively straightforward manner and has example configurations for most common configurations. If you decide to try it, you should also download the comprehensive documentation package that accompanies it.

---

### Post by phantomjoker on 2008-07-19
Hyper_Ch

how could I make my (currently installed) firewall active?

---

### Post by Locutus_of_Borg on 2008-07-19
an anti-virus utility is unnecessary, but if you want one anyway, i would suggest clamav as it is available in the ubuntu repositories, but it is really only useful if you share files with windows

as for a firewall, iptables is THE firewall.

there are various frontends to iptables (guarddog and firestarter for instance) that give you a GUI to help with setting up iptables, but it is really not difficult once you read a little to do iptables manually

a really good place to start is here: [https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

basically what you do is set up rules for traffic based on their ports

it is wise to have a default setting of drop for everything, and then open up only the traffic you want, i can help you out if you like

attached is my firewall.rules to give you an idea of what it entailed

---

### Post by Kevbert on 2008-07-19
> **phantomjoker said:**
> A little more detail please Sef?

sorry - im not sure what a  is?

thank you

GUI = Graphical User Interface - what you would see in Gnome or Windows with display boxes and buttons to press.

---

### Post by zipperback on 2008-07-19
firestarter for firewall management.
clamav for antivirus.

---

### Post by iaculallad on 2008-07-19
> **phantomjoker said:**
> When you say



What do you mean?

I know linux isn't prone to virus' but there are some out there - so is that what you mean or am I missing something?

What I mean is: I don't have to worry on virii's, worms, malware's, etc .. (too name a few of windoze BEST's).

If you're that paranoid, you can install Clamav for your antiviral thing application. There maybe *some* Linux viruses, but surely, there just there in the wild getting dormant and eventually dies..
Don't worry, you have both your root and user account that can be use to protect you.

EDIT: Inserted conjunction "to"

---

### Post by hyper_ch on 2008-07-19
> **phantomjoker said:**
> Hyper_Ch

how could I make my (currently installed) firewall active?

You add rules to it by either using a frontend like firestarter or the new UFW tool or adding manually rules....

But ask yourself first why you think you require a firewall? Generally I'd say you don't need to think about it at all.

---

### Post by Sef on 2008-07-19
> front-end gui for IP Tables. 

It's where you can point and click with a mouse.

---

### Post by phantomjoker on 2008-07-19
fair point iaculallad

the reason for my concern is mainly through having to move work and files between a Linux and Windows computer - I asume if I get a virus that doesn't affect Linux but does affect Windows - and move the file containing the virus to the Windows computer - it will get infected? 

is that right?

---

### Post by hyper_ch on 2008-07-19
yes, windows viruses won't affect your linux install but you can pass it on to windows... so that could be one reason to install anti-virus on linux... although I think it's not Linux's job to filter out malware for Windows... Windows should be able to protect itself.

---

### Post by phantomjoker on 2008-07-19
ha - thats a nice twist - I would personally agree with you - but I pass documents and files onto computers I have no control over and don't know whether they are protected - thus I feel the need and obligation to protect

---

### Post by Canis familiaris on 2008-07-19
> **phantomjoker said:**
> fair point iaculallad

the reason for my concern is mainly through having to move work and files between a Linux and Windows computer - I asume if I get a virus that doesn't affect Linux but does affect Windows - and move the file containing the virus to the Windows computer - it will get infected? 

is that right?
It is possible. But you could easily manually delete the virus as you do to a file. You can easy recognise their names, wierd strange names.

Also you can install ClamAV. - Antivirus.
Go to Applications->Add/Remove.
Search for ClamAV and install it.

There is also Avast for Linux, you could download and install it.

---

### Post by iaculallad on 2008-07-19
> **phantomjoker said:**
> fair point iaculallad

the reason for my concern is mainly through having to move work and files between a Linux and Windows computer - I asume if I get a virus that doesn't affect Linux but does affect Windows - and move the file containing the virus to the Windows computer - it will get infected? 

is that right?

That could be right. Because, if you have installed the ClamavAV, it's database signatures are different from that of other windoze AV softwares. ClamAV will only detect virus signatures made for Ubuntu (Linux) (correct me if I'm wrong with this part. Maybe, it could still detect some of windoze virus too).

My Only suggestion is to install AV softwares to your windoze machines and updates it's signature daily. On your Ubuntu machine, just leave it be.

---

### Post by Canis familiaris on 2008-07-19
> **iaculallad said:**
> That could be right. Because, if you have installed the ClamavAV, it's database signatures are different from that of other windoze AV softwares. ClamAV will only detect virus signatures made for Ubuntu (Linux) (correct me if I'm wrong with this part. Maybe, it could still detect some of windoze virus too).

My Only suggestion is to install AV softwares to your windoze machines and updates it's signature daily. On your Ubuntu machine, just leave it be.

You are mistaken. ClamAV detects Windows viruses too.

---

### Post by Sef on 2008-07-19
> the reason for my concern is mainly through having to move work and files between a Linux and Windows computer - I asume if I get a virus that doesn't affect Linux but does affect Windows - and move the file containing the virus to the Windows computer - it will get infected?

is that right?

That can happen.  If you are moving files between GNU/Linux and Windows, then an anti-virus is needed for GNU/Linux.

---

### Post by iaculallad on 2008-07-19
> **Anurag_panda said:**
> You are mistaken. ClamAV detects Windows viruses too.

That's why I opt to include the phrase "**correct me if I'm wrong with this part**" to my post. I did not experience it first hand (ClamavAV detecting my infected files in Windoze) so I played it in safe side w/o actually saying "It will not detect windoze virii's". Anyway, thanks for the info though.

---

### Post by phantomjoker on 2008-07-19
yes this is my theory.

I have downloaded ClamAV which seems to throw up an error about signatures? - but also seems to scan ok - so I think I'll leave it for the time being

and as for a firewall - i think i'll leave it - since I need only scan files I move


(as for Anurag_panda comment - not all viruses are in there own files - i've had much experiance with that.) 

thanks guys - i think this one is SOLVED

but keep posting if you want - i will...

---

### Post by Canis familiaris on 2008-07-19
Source: :)
[https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus)
[https://help.ubuntu.com/community/ClamAV](https://help.ubuntu.com/community/ClamAV)

---

### Post by hyper_ch on 2008-07-19
> **iaculallad said:**
> That could be right. Because, if you have installed the ClamavAV, it's database signatures are different from that of other windoze AV softwares. ClamAV will only detect virus signatures made for Ubuntu (Linux) (correct me if I'm wrong with this part. Maybe, it could still detect some of windoze virus too).

Well ClamAV detects almost only windows viruses as there is no need to detect linux viruses ;)

---

### Post by iaculallad on 2008-07-19
For other security options for your Ubuntu machine, you could try reading this Ubuntu Community's Security Tools [page]("https://help.ubuntu.com/community/InstallingSecurityTools").

HTH

---

