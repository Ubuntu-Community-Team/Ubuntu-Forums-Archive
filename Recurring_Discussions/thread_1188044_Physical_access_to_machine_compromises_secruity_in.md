---
title: "Physical access to machine compromises secruity in Linux?"
date: 2009-06-15
forum: Recurring Discussions
---

### Post by AICollector on 2009-06-15
On a Windows machine, it's quite possible for me to browse, change and delete files, including passwords, before Windows itself boots up. 

I am aware that Linux is more or less invulnerable to attacks over the net, BUT, is it vulrenble like mentioned above, and would encrypting my home directory seal that breech?

---

### Post by dmizer on 2009-06-15
Unless encrypted with strong passwords, physical access to any machine is as good as breached.

---

### Post by AICollector on 2009-06-15
So home encryption + good password = physical access hole covered?

---

### Post by Chemical Imbalance on 2009-06-15
A good BIOS password and full disk encryption helps, though BIOS passwords can be hacked easily.

Full disk encryption is your best bet.

---

### Post by Bachstelze on 2009-06-15
> **AICollector said:**
> So home encryption + good password = physical access hole covered?

No. There is no way to completely eliminate the physical access risk.

---

### Post by Chemical Imbalance on 2009-06-15
> **HymnToLife said:**
> No. There is no way to completely eliminate the physical access risk.

There is no such thing as 100% secure either.  Physical access or not.

But physical access always means ):P

---

### Post by cdenley on 2009-06-15
With physical access, they can still overwrite the disk, or sabotage your hardware in a number of ways. There is no realistic way to alter, add, or delete files within the encrypted filesystem without a password except for rebooting to a livecd/usb while the filesystem is decrypted (or pulling the memory quickly), and retrieving the encryption key from memory.

---

### Post by anaconda on 2009-06-15
And what if you leave your machine on when you are not home?

Disk encryption wont help in that case.


I prefer encrypted files, which contain the "personal stuff" And those fileas are NOT mounted normally.

---

### Post by tubbygweilo on 2009-06-15
> **anaconda said:**
> ..
I prefer encrypted files, which contain the "personal stuff" And those fileas are NOT mounted normally.

Encrypted personal files stored on external device that is securely held some place close at hand and can be mounted when required **but** don't forget your passphrase!

---

### Post by AICollector on 2009-06-15
Hmmm....*starts wondering if anyone more experienced then himself has attempted to institute a method to which physical access risk is severely reduced, without hampering the user for multiple passwords*

---

### Post by Bachstelze on 2009-06-15
> **AICollector said:**
> Hmmm....*starts wondering if anyone more experienced then himself has attempted to institute a method to which physical access risk is severely reduced, without hampering the user for multiple passwords*

"severly reduced" and "totally covered" are different. ;)

---

### Post by hggdh on 2009-06-15
> **anaconda said:**
> And what if you leave your machine on when you are not home?

Disk encryption wont help in that case.


Indeed. See [Lest we Remember]("http://citp.princeton.edu/memory/") for a recently-published attack on memory...

---

### Post by jflaker on 2009-06-15
TrueCrypt - Allows for plausible deniability by being able to create encrypted volumes, containers,....containers inside of volumes...volumes inside of containers.....etc.

---

### Post by grotesk on 2009-06-15
There are very few universal answers in the security field. Strongly consider the threat scenario you are trying to defend against. For instance:

Is this a server system located in a datacenter?
* Full-disk encryption provides minimal help; your filesystem will be mounted permanently and decryption will be transparent.
* Physical access may not be much of a worry if your datacenter is sufficiently secure.

Is this a laptop system that you might lose or have stolen?
* A BIOS password will deter a very unskilled or un-resourced attacker but anyone can simply remove your hard-disk and boot it in another system, or copy your data from it.
* Full-disk encryption is a good way to guard against data theft in this scenario
* File-by-file encryption is a good way to secure data which you know you you don't want to lose, but you may expose credentials stored on-disk in plaintext or configuration data

Is this a desktop system in your home or office?
* Ask yourself if a physical attacker is a reasonable threat scenario and whether the additional encryption is worth the processing overhead. If it is, consider the options for laptop encryption above, bearing in mind that BIOS passwords and/or GRUB passwords provide little to no security improvement.

---

### Post by doas777 on 2009-06-15
> **AICollector said:**
> On a Windows machine, it's quite possible for me to browse, change and delete files, including passwords, before Windows itself boots up. 

I am aware that Linux is more or less invulnerable to attacks over the net, BUT, is it vulrenble like mentioned above, and would encrypting my home directory seal that breech?

physical access = root access. period. 

full disk encryption can be vulnerable to a number of attacks. in some cases ram can be access to obtain keys, or enterprise products' manageability features can be compromised. Encryption is either managable and recoverable (making it weak against comprimise: ie safeboot) or it is rigid, inflexible, and unforgiving (meaning you are one forgotten password or lost keyfile away from your data...forever; ie truecrypt/PGP/GPG). 

if you need to focus on physical security, an armed gaurd, a CCTV camera, and a door with a strong lock are your best bets.  

if you are at DefCon, handcuff your laptop to your person at all times (lol). otherwise, don't take it anywhere you don;t feel safe taking out your wallet.

---

### Post by rookcifer on 2009-06-15
Bottom line: Whole disk encryption will make your data safe, whether an adversary has physical access or not.  However, encryption will NOT stop an adversary from simply deleting or destroying your encrypted partitions.  All they need is a liveCD and it's goodbye encrypted data.

---

### Post by hggdh on 2009-06-15
> **rookcifer said:**
> Bottom line: Whole disk encryption will make your data safe, whether an adversary has physical access or not.

No, it will not. It makes the attack more complex, at least until the attack is scripted. Again, please see the link I provided above ([Lest we Remeber, or 'Cold Boot Attacks']("http://citp.princeton.edu/memory/). All that is needed is a running machine (or hibernating one, for that matter). And, of course, physical access.

The same attack would also work on coredumps, up to a point (it depends on what programme coredumped, and it depends on what memory segments has been dumped). But I successfully proved it on some scenarios.

---

### Post by AICollector on 2009-06-15
Nothing as serious. I just dislike people gaining access to my machine, which my nephew does on a regular basis.

---

### Post by rookcifer on 2009-06-16
> **hggdh said:**
> No, it will not. It makes the attack more complex, at least until the attack is scripted. Again, please see the link I provided above ([Lest we Remeber, or 'Cold Boot Attacks']("http://citp.princeton.edu/memory/). All that is needed is a running machine (or hibernating one, for that matter). And, of course, physical access.

The same attack would also work on coredumps, up to a point (it depends on what programme coredumped, and it depends on what memory segments has been dumped). But I successfully proved it on some scenarios.

I read that paper months ago. The problem is, the machine has to be gotten to within a minute or two of it being powered off.  Even then the adversary will need to spray the RAM with canned air and have another machine on hand to quickly plug the RAM into.  Not very practical to say the least.  I don't know about you, but I don't have people sitting outside my home with canned air and a laptop ready to strike when I shut my PC off.  

I suppose it all boils down to a matter of perspective and risk analysis.  If the OP has a machine in an environment where a lot of tech savvy people will have quick access to his machine shortly after it is powered off, then perhaps he should worry.  If he is worried that his desktop machine in his home can be compromised this way, I find it highly unlikely short of an armed home invasion.  As for laptops, this attack is a reminder to A) Never let it out of your site and B) If you have to for some reason, then power the thing completely off.

Bottom line: as long as no one has physical access to the machine within a few minutes after it being powered-off, it's safe.

---

