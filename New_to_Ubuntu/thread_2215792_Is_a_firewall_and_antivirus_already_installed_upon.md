---
title: "Is a firewall and antivirus already installed upon initial installation?"
date: 2014-04-08
forum: New to Ubuntu
---

### Post by Sherman_Willden on 2014-04-08
[http://www.ubuntu.com/desktop/business](http://www.ubuntu.com/desktop/business) states "The default settings prioritise security, and Ubuntu comes with a  firewall, antivirus software and file and disk encryption tools." Are these tools firestarter and clamav that I have to install myself? Or are some kind of tools installed within Ubuntu 12.10? Do I have to install firestarter and clamav or am I already protected?

Thank you;

---

### Post by mcduck on 2014-04-08
In the default setup you won't need a firewall for anything, the default setup has no services listening for incoming connections. So the only reason you might eed a firewall is if you instal some additional server applciation which doesn't have enough built-in support for limiting outside access to fit your needs. Quite unlikely situation for any individual user, actually. And in case you'd need that anyway, the firewall itself is built in to Linux kernel, all you need is a tool to configure it (UFW is a command-line tool for the purpose, and comes included by default, for a graphical one GUFW is a good choice. Firestarter is not recommended as it's been unmaintained for a while now)

Antivirus isn't really a requirement (or even much use) for home use either, there really aren't enough Linux viruses around so they are only useful for scanning for Windows viruses. Which can make sense if the Linux machine is used as a gateway or server for a larger network of Windows computers, but unlikely situation in any normal home use.

Disc encryption tools are included by default, and you are offered the option to encrypt user home directories during the install.

So the short answer is that a firewall is included but not enabled by default, antivirus software is available for install if needed, and disc encryption is included by default and can be enabled during install.

---

### Post by Sherman_Willden on 2014-04-08
Thank you, mcduck. This helps

---

### Post by anaconda on 2014-04-08
> **mcduck said:**
> 
Antivirus isn't really a requirement (or even much use) for home use either, there really aren't enough Linux viruses around so they are only useful for scanning for Windows viruses. Which can make sense if the Linux machine is used as a gateway or server for a larger network of Windows computers, but unlikely situation in any normal home use..

I disagree.
For your own safety you should have an antivirus program installed.

I recommend installing clamtk (antivirus which uses clamav)
In Ubuntu you dont really need it, but and it is a big BUT. Nowdays many banks etc.. have rules, that say, if something goes wrong with your internet-bank you are responsible for your own losses **unless** you have an updated antivirus-program on your machine 

So for your own safety if you use a netbank or similar you indeed should have antivirus installed. (they don't understand the differences of windows and linux)

And one day, there will be active viruses for ubuntu too. and then you will be better protected if you already have a system, which can detect them.

Iptables -firewall is already installed on your system. But I have installed firewalld and firewall-applet on my system for easier control.
same thing with a firewall and some bank-rules. you have to have one Technically iptables IS a fiirewall, but to be sure I installed also the firewalld...

Oh. and one other thing where you do need the antivirus is, if you run windows programs in wine. I just found a windows virus on a game, that I run in wine.

---

### Post by mcduck on 2014-04-08
Well, having a Linux antivirus software won't protect you until there actually is a Linux virus that could be added to it's database so that it could protect you from it. So the virus must become a real thing before the antivirus even has a chance of protecting you from it. Which means you can just as well install the antivirus software at that point instead of now. (Even more so since we've been waiting for the Linux virus to appear for quite many years now, wastng resources all that time because one day the virus might appear doesn't make much sense.)

If your bank or some other external instance has strange rules requiring you to have antivirus and firewall installed, and you don't believe you'd be able to work around that, then by all means have one (you might not need to actually run it), but in that case it's of course not to protect you from computer viruses but from your bank's lawyers :D (I'd stay away any bank that incapable of dealing with technology, but of course it might not be an option depending on your situation).

What comes to firewalld, it's just one more tool using the iptables, so you won't get even theoretical benefit from that. You already have UFW by default which does the same thing. And once again in most cases even enabling the firewall won't actually do anything security-wise if there's nothing for the firewall to block it's just a waste of resources (unless once again you need one for some other reason than actual security).

---

### Post by buzzingrobot on 2014-04-08
How would a bank *know* if a customer had AV software running on a machine at the time an attack occurred?

---

### Post by maglin2 on 2014-04-08
> **buzzingrobot said:**
> How would a bank *know* if a customer had AV software running on a machine at the time an attack occurred?

Good question. They seem to know that I don't have their Trusteer Rapport antimalware tool - but I guess that is set up to report back to the banks who fund it. Maybe some AVs are too?

---

### Post by Mk32 on 2014-04-08
I wish they had outgoing packet protection like LittleSnitch. I know you can do it with some esoteric configuration of iptables but that's an Advanced User exercise. 

As for viruses and malware, I would suppose it falls in to the similar category of the Apple Defense: I'm a Mac user and there's real no threat. 

I would argue that yes that we are in the minority, but that's not the same thing as immunity, either. 

If your bank wants AV, simply get some out-of-the-way laptop like an older ThinkPad to run Windows 7 or something, and use that for banking. All your regular habits can thus be done on your Linux box.

---

### Post by Berry Greene on 2014-04-08
It seems that Linx / Ubuntu system is pretty safe from virus attack. Are other security issues dealt with?
I suppose Windows viruses can be passed via UBUNTU to Windows if database files are shared.

---

### Post by kurt18947 on 2014-04-08
> **Mk32 said:**
> I wish they had outgoing packet protection like LittleSnitch. I know you can do it with some esoteric configuration of iptables but that's an Advanced User exercise. 

As for viruses and malware, I would suppose it falls in to the similar category of the Apple Defense: I'm a Mac user and there's real no threat. 

I would argue that yes that we are in the minority, but that's not the same thing as immunity, either. 

If your bank wants AV, simply get some out-of-the-way laptop like an older ThinkPad to run Windows 7 or something, and use that for banking. All your regular habits can thus be done on your Linux box.

Or run Windows in a VM.  That sort of nullifies one of the big advantages of using Linux, though.  Perhaps if you had a Windows install in a VM and used that only for banking, malware exposure MIGHT be minimized.  I have a small Linux partition used that way. Basic install, no java no flash.  It only sees financial related sites.  I know there's no guarantee but the odds of picking up a Linux virus from a (presumably) professionally maintained security conscious site -because they're juicy targets - seems pretty small.

---

### Post by sotiris2 on 2014-04-08
One would need to consider that ClamAV does not provide the sort of **real-time** protection windows av do. It just scans files whenever you initiate (or have scheduled via cron etc.) a scan. So I don't see how it would help in online banking or how they could really know if you have it (since it probably won't be running)

---

### Post by buzzingrobot on 2014-04-08
> **maglin2 said:**
> Good question. They seem to know that I don't have their Trusteer Rapport antimalware tool - but I guess that is set up to report back to the banks who fund it. Maybe some AVs are too?

If my bank told me I had to use their AV software, I'd change banks.

I can't imagine anyone buying a commercial AV product once it became known it was secretly sending data to banks.

Customers have more reason to be concerned about bank security than the other way around.

---

