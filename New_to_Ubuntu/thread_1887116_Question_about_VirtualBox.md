---
title: "Question about VirtualBox"
date: 2011-11-26
forum: New to Ubuntu
---

### Post by WinzenFlyer on 2011-11-26
I was just pointed to VirtualBox as a possible way to run Windows on ubuntu. Do I need to care for the Windows as it was a normal installation (i.e. install all service packs, virus scanner and so on)?

I was also told, that if anything bad would happen, that this couldn't exit the box and do harm to ubuntu. Is that also right?

---

### Post by howefield on 2011-11-26
> **WinzenFlyer said:**
> I was just pointed to VirtualBox as a possible way to run Windows on ubuntu. Do I need to care for the Windows as it was a normal installation (i.e. install all service packs, virus scanner and so on)?

Yes, for the most part your Windows VM would need to be treated as you would a "normal" windows installation.

> I was also told, that if anything bad would happen, that this couldn't exit the box and do harm to ubuntu. Is that also right?

Pretty much correct, although if your VM is part of a network,  however unlikely it is possible for something to cross over.

It might be a good idea to make a backup of your VM, export the appliance or take snapshots. Anything that will get you back to your virgin install. :-)

---

### Post by LinuxFan999 on 2011-11-26
It is always a good Idea to apply updates to any operating system, even one which is running in a virtual machine.
 
The answer to your second question is yes, whatever hapens in the Virtual machine will not harm Ubuntu.
 
EDIT: Someone posted while I was posting. I take too long apparently.

---

### Post by haqking on 2011-11-26
applying service packs and updates are dependent on why or how you use the OS in the VM, for the most part then yes you apply them as you normally would. 

> The answer to your second question is yes, whatever hapens in the Virtual machine will not harm Ubuntu.

This is a little misleading, providing a security blanket to do as you like in a VM without fear or worry.

Bad things can happen, the likelihood is minimum but yes they can, things like shared folders and bridged networking gives the VM access to your network and local machine (host) and so yes there is potential for bad things to happen.

So as always whatever you are using, dont run things you dont understand, dont install from untrusted sources, dont carry out tasks without understanding the potential consequences, run malware solutions in the Windows environment, be aware of what access you give or share etc.

However under normal circumstances (whatever they are ;p) you should be ok with common sense applied.

Peace

---

### Post by Andrew Jeyaraj on 2011-11-26
Yea.If your'e planning to use your Windows VM for productive work then i'd suggest you take care of it as you would a normal windows installation.I used my WindowsVM on Ubuntu just for fun.

You wont have to worry about anything happening to Ubuntu though.:)

---

### Post by haqking on 2011-11-26
> **Andrew Jeyaraj said:**
> 

**You wont have to worry about anything happening to Ubuntu though**.:)

another blanket statement about Linux security which i am afraid is incorrect as i explained above.

Using a VM does not mean you are 100% protected from malicious software propogation and or malicious code execution.

Chances are low admittedly, however there is still a need to be aware of potential so that you can protect yourself as much as possible, if you network or share resources via the host or network then you are networked.  In a networked world nothing is 100% secure.

---

### Post by WinzenFlyer on 2011-11-26
Thanks for all your answers! 

Is it possible to bring Files from ubuntu into the Windows VM? I want to run the Arduino Software on Windows and if I could bring it into there, I wouldn't even need internet access for Windows.

---

### Post by haqking on 2011-11-26
> **WinzenFlyer said:**
> Thanks for all your answers! 

Is it possible to bring Files from ubuntu into the Windows VM? I want to run the Arduino Software on Windows and if I could bring it into there, I wouldn't even need internet access for Windows.

yes through shared folders.

make sure you have the guest additions installed.

[http://www.virtualbox.org/manual/ch04.html#sharedfolders](http://www.virtualbox.org/manual/ch04.html#sharedfolders)

---

### Post by howefield on 2011-11-26
Yes, there are a number of options, I'd have a look at Shared Folders.

[https://www.virtualbox.org/manual/ch03.html#idp11221088](https://www.virtualbox.org/manual/ch03.html#idp11221088)

There are some short videos on the virtualbox website you might find useful, including one on setting up shared folders.

[https://www.virtualbox.org/wiki/VirtualBoxTV](https://www.virtualbox.org/wiki/VirtualBoxTV)

---

### Post by Dangertux on 2011-11-26
As stated already, if for normal use you should patch it , and maintain it like a normal OS. I also disagree with those that say NOTHING can happen to Ubuntu from Windows in a VM. 

If you doubt that, google hypervisor escalation. Bottom line it's not a completely independent OS, it relies on making calls to the Ubuntu host for system resources. This is a system that can be abused, potentially to the detriment of the Host system. Again it's rare, and extremely targeted but it's not impossible.

Hope this helps.

---

### Post by 3rdalbum on 2011-11-26
> **haqking said:**
> another blanket statement about Linux security which i am afraid is incorrect as i explained above.

Using a VM does not mean you are 100% protected from malicious software propogation and or malicious code execution.

Chances are low admittedly

IMHO, they're so low that you don't need to worry about them. If you spend time and resources fighting every single little 0.1% chance, you'll spend 50% of your computing time doing nothing productive.

As far as I know, there's only been one crossover from a guest OS to its host OS, and that was experimental code that never actually reached the wild. If this kind of exploit starts making the rounds and causing damage, I'm sure we'll hear about it and be able to take precautions. For now though, it's so remote, and there's so little thought about how to prevent such a thing, that it doesn't bear worrying about in your everyday computing practice.

---

### Post by haqking on 2011-11-26
> **3rdalbum said:**
> IMHO, they're so low that you don't need to worry about them. If you spend time and resources fighting every single little 0.1% chance, you'll spend 50% of your computing time doing nothing productive.

As far as I know, there's only been one crossover from a guest OS to its host OS, and that was experimental code that never actually reached the wild. If this kind of exploit starts making the rounds and causing damage, I'm sure we'll hear about it and be able to take precautions. For now though, it's so remote, and there's so little thought about how to prevent such a thing, that it doesn't bear worrying about in your everyday computing practice.

Well i did say it was low, however i never told the OP to worry about it.  I was making them aware of potential, which is reality.

I prefer to spread reality instead of issuing statements about things being secure which is an incorrect.

If a chance is there no matter how low there is potential, in answer to the OP question about it, yes bad things can happen, chances are minimum but the answer of NO bad things cannot happen would be an incorrect answer.

I would say a secure system (end user everyday use) is not something you cannot exploit or is not vulnerable but to be realistic it is something we can use securely within the confines of usability and where we armed with the knowledge can accept or mitigate the risks associated with it.

it is the blanket statements or ignorance about security which allow so many exploits and vulnerabilities to exist, security is about education and not about not worrying about things that dont seem important.

Cheers

---

### Post by SeijiSensei on 2011-11-26
> **haqking said:**
> If a chance is there no matter how low there is potential, in answer to the OP question about it, yes bad things can happen, chances are minimum but the answer of NO bad things cannot happen would be an incorrect answer.

While you're certainly right theoretically, I'm concerned that most ordinary Ubuntu users don't have the experience or knowledge to know whether they should be concerned with a "minimal" security risk or not.  People coming from Windows will probably view any "minimal" risk as a serious threat.

It would be nice to know how often systems in the real world suffer from hypervisor threats.  My guess is we're talking probabilities in the 1/1,000,000 range.  Do you have evidence about how common a threat like this might be?

Propagation via network shares is a much more common threat.

---

### Post by haqking on 2011-11-26
> **SeijiSensei said:**
> While you're certainly right theoretically, I'm concerned that most ordinary Ubuntu users don't have the experience or knowledge to know whether they should be concerned with a "minimal" security risk or not.  People coming from Windows will probably view any "minimal" risk as a serious threat.

It would be nice to know how often systems in the real world suffer from hypervisor threats.  My guess is we're talking probabilities in the 1/1,000,000 range.  Do you have evidence about how common a threat like this might be?

Propagation via network shares is a much more common threat.

Well the answer is simple, forgetting the hypervisor threats.

For the simple end user who knows nothing about security, if you are using a VM, then if you are connected to the host via shared folders and or bridged networking then it is the same as any othe network device in that malicious files may propogate.  Whether or not it infects the Linux host is different, the security factor though is about minimising potential for threat, which spreading malicious code and files comes under.

MYTH: you can do what you like in a VM with what you like and not worry as you are secure and so is your network and host.

FACT: pay the same attention to security in the VM and if you choose to network it then it just another node on the network with potential for attack.

Also i think it is very important infact even more important to let inexperienced users be aware of potential threats, informing a new user something is fine without education progogates the whole Linux is secure statement which is not correct.

Linux and Windows share a roughly equal security certification, given the opportunity no matter the level of experience i will always take steps to educate a person.

> Give me six hours to chop down a tree and I will spend the first four sharpening the axe."  (Abraham Lincoln, 1809-65

---

### Post by WinzenFlyer on 2011-11-26
Thank you for all your answers!

So it also is not so secure if you run Windows only without network connection (i.e. for playing a game or using the Arduino that I mentioned)?

PS: Sorry for potentially dumb questions.

---

### Post by haqking on 2011-11-26
> **WinzenFlyer said:**
> Thank you for all your answers!

So it also is not so secure if you run Windows only without network connection (i.e. for playing a game or using the Arduino that I mentioned)?

PS: Sorry for potentially dumb questions.

running a VM without network connection is more secure yes and the potential for threat is at its minimum.

I was never saying you need to worry about using a VM, purely be aware that using a VM is not 100% secure that is all, the chances are extremely low. I prefer to be realistic rather than wrap people up in a concrete bunker of being secure ;-)

On the contrary i run VM's all the time and some of them solely for the purpose of running malicious files in them.

I am merely making you aware of potential.

When it comes to security i prefer a pragmatic approach rather than a optimistic one.

relax and enjoy your games

---

### Post by WinzenFlyer on 2011-11-26
Thank you for taking the time to explain everything :)! I really like your approach to inform and educate people (and the Abraham Lincoln citation too :))!

Best Wishes,
WF

---

### Post by haqking on 2011-11-26
> **WinzenFlyer said:**
> Thank you for taking the time to explain everything :)! I really like your approach to inform and educate people (and the Abraham Lincoln citation too :))!

Best Wishes,
WF

You are welcome.

As for Abe, well yes Proper planning and preparation prevents poor performance.

Only with the knowledge of a risk can you accept or mitigate it.

Peace and enjoy

---

### Post by WinzenFlyer on 2011-11-27
Well, I am back with another question. Yesterday I finished installing Win 7 and it's Service Pack and then downloaded all the Updates as well as MSE and Firefox into the VM.

To access the internet, I only could use my WLAN stick when setting VB to "Bridged Networking".

Now I was just told that I should have run it in NAT mode. And haqking, you said:
> For the simple end user who knows nothing about security, if you are  using a VM, then if you are connected to the host via shared folders and  or bridged networking then it is the same as any othe network device in  that malicious files may propogate.  Whether or not it infects the  Linux host is different, the security factor though is about minimising  potential for threat, which spreading malicious code and files comes  under.


What does that mean exactly? Could I even have compromised my ubuntu now?

---

### Post by Dangertux on 2011-11-27
> **WinzenFlyer said:**
> Well, I am back with another question. Yesterday I finished installing Win 7 and it's Service Pack and then downloaded all the Updates as well as MSE and Firefox into the VM.

To access the internet, I only could use my WLAN stick when setting VB to "Bridged Networking".

Now I was just told that I should have run it in NAT mode. And haqking, you said:


What does that mean exactly? Could I even have compromised my ubuntu now?

It's not likely that Ubuntu was compromised even if the Windows 7 guest was compromised. However it is possible. We can't tell you if it happened or not because we don't have access to the systems in question.

The best answer I can give is that it is not very likely to have happened.

Also you mentioned NAT and Bridged networking a while back, if you are using a USB Dongle for Internet access on the VM why not consider changing the network settings to host only in VirtualBox, this will keep the Guest inaccessible from outside machines. Of course if you download something malicious directly into the guest, it can still become compromised.

Hope this helps.

---

### Post by haqking on 2011-11-27
> **WinzenFlyer said:**
> Well, I am back with another question. Yesterday I finished installing Win 7 and it's Service Pack and then downloaded all the Updates as well as MSE and Firefox into the VM.

To access the internet, I only could use my WLAN stick when setting VB to "Bridged Networking".

Now I was just told that I should have run it in NAT mode. And haqking, you said:


What does that mean exactly? Could I even have compromised my ubuntu now?

Well you are bridging to your existing host WLAN connection then ? which means your VM is on your LAN.

As DT mentions above set it to host only.  However i am not sure if i am reading it right (i have a headache) anyways do you menan a USB dongle as in its own internet connection ? or a USB wifi dongle which connects to your router ? if it conencts to your router then it is still on your LAN.

---

### Post by WinzenFlyer on 2011-11-27
There is a USB WLAN receiver by TP-LINK that I use to go online with ubuntu. And when I set "bridged networking", I got internet in Windows (and Windows showed a wired connection inside the VM).

---

### Post by SeijiSensei on 2011-11-28
If you don't need to let other systems access the VM, then you should use NAT mode.  The VM will be able to access the Internet, but it will be "hidden" behind the host, just the same way machines behind a router are hidden.

It sounds like NAT is the best choice for you.  Bridging is a solution if you want the VM to act as a server.

---

### Post by Paqman on 2011-11-28
> **WinzenFlyer said:**
> I want to run the Arduino Software on Windows

Just in case you weren't aware: the Arduino IDE is in the Ubuntu repos, you can install it from Software Centre.

---

### Post by WinzenFlyer on 2011-12-01
I tried this one but I always got problems which I described here: [http://ubuntuforums.org/showthread.php?p=11490885](http://ubuntuforums.org/showthread.php?p=11490885)

---

