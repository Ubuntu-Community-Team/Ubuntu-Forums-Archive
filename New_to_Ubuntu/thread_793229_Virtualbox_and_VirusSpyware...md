---
title: "Virtualbox and Virus/Spyware.."
date: 2008-05-13
forum: New to Ubuntu
---

### Post by flutti-tutti on 2008-05-13
Hi
I am absolutely new to Linux/Ubuntu. Since I need to run Mathcad 13/14 with Windows XP or Vista, I plan to use VirtualBox, and the Mathcad 13/14 needs to be connected to Internet.  I have a few questions regarding firewall and virus protection for Windows in VirtualBox. 

1. Do I have to install Windows firewall software inside VirtualBox?
   (Firestarter has been installed to Ubuntu)  
2. How about protection software for Windows virus or other malicious programs?  
3. Although they are not very likely to do any harm to Ubuntu, will my virtual Windows directory be contaminated, when it is attacked?

I would rather avoid to use Windows firewall or anti-virus programs, and am really tired of them.  (they are ineffective.)

Could you share your experiences?
Thanks for your help and suggestion in advance.
tutti :?

---

### Post by Monicker on 2008-05-13
See my comment in this thread:

[http://ubuntuforums.org/showthread.php?t=793007]("http://ubuntuforums.org/showthread.php?t=793007")

Yes, your windows vm is still capable of getting any windows viruses and malware.  They won't have a lot of impact on your linux host, though they can still consume bandwidth and be used to cause problems for others.

---

### Post by SunnyRabbiera on 2008-05-13
well I do think it should be able to use Ubuntu's firewall, but yes its possible to get virtualbox windows infected, but it will probably not harm your ubuntu system as its virtual...
you may want to get a antivirus for windows within Virtualbox.

---

### Post by mister_pink on 2008-05-14
I'd say you could get away without either. Windows might be prone to viruses but its not as bad as people here might like you to think - basically I think you'd have to be trying pretty hard to get a virus whilst using Mathcad. As long as you don't browse the internet inside the guest then you won't get anything. 

You can also just set the machine up how you want it, and then make a copy of the virtual disk. If anything goes wrong just delete the disk and use the copy. Make sure you don't save any of your work inside the virtual drive if you plan to do this!

---

### Post by billgoldberg on 2008-05-14
Right, if you only use that one program, and don't begin surfing the internet, you should be fine.

But yes, you can get viruses in Virtualbox, and No, it won't do any harm to the files on Ubuntu.

---

### Post by mister_pink on 2008-05-14
Should probably add - it could potentially do harm to ubuntu files if you mounted them using the virtual network tool with read/write access. Still, really quite unlikely and it would only be able to do things to the files you had shared. Even if you did get a virus on it or whatever, noone really writes viruses to just blitz your computer these days, they're usually to do things to make money for someone!

---

### Post by aquavitae on 2008-05-14
> **mister_pink said:**
> Should probably add - it could potentially do harm to ubuntu files if you mounted them using the virtual network tool with read/write access. Still, really quite unlikely and it would only be able to do things to the files you had shared. Even if you did get a virus on it or whatever, noone really writes viruses to just blitz your computer these days, they're usually to do things to **make money for someone**!e.g. Norton, McAfee, Trend, etc...

---

### Post by Cadmus on 2008-05-14
Is it still advisable to keep as up to date as possible with patches? I would assume a vbox is still vulnerable to remote exploits if it can be reached somehow.

---

### Post by lazyart on 2008-05-14
I would treat a virtual machine just like a physical machine-- If it is online it is just as vulernable, especially if you use a bridged connection where the machine gets an address on the same network as the host.

If you configure it as NAT then the host should effectively act as a firewall and you might not be as exposed.

---

### Post by mister_pink on 2008-05-14
As is said above, with NAT (which I think I'm right in saying is the default for virtualbox) you'll be protected firewall-wise, but if you browse with IE on anything dodgy the virtual machine would still be vulnerable to say for example a javascript exploit, which could allow remote code execution resulting in the machine getting a virus/ trojan/ spyware/whatever. This is all really unlikely though. To answer the original question in short - I really wouldn't worry about it. 
> **aquavitae said:**
> e.g. Norton, McAfee, Trend, etc...
Not quite what I was thinking, but well thats one theory ;) Personally I blame those crazy russian hackers, probably the same people that keep kindly informing me that I need to enter my bank details into some random website or I could be a victim of fraud...

---

### Post by aquavitae on 2008-05-15
Maybe I'm just cynical, but it would make good business sense!

Regarding the original question, I'll add my voice to those saying its probably not worth worrying about. If you are worried, why not use ClamAV in linux. Its FOSS.

---

### Post by flutti-tutti on 2008-05-15
Thanks for your suggestions!!
I would not be worried about VirtualBox infection.

Upon your suggestions my strategy includes:
1. NAT setting in VirtualBox
2. Limited internet connection only for Windows and application updates 
3. Backup the virtual disk and shared directories
4. Ran antivirus on the virtual disk and shared directories (clamscan)
5. No firewall nor anti-virus/spyware inside VirtualBox

(If you have further suggestion, would appreciate it.)
Thanks again
tutti
[http://ubuntuforums.org/images/smilies/new_popcornsmiley.gif](http://ubuntuforums.org/images/smilies/new_popcornsmiley.gif)

---

