---
title: "Security Concerns with Live CDs"
date: 2007-09-18
forum: Other OS Talk
---

### Post by TheThinker on 2007-09-18
According to the makers of NimbleX, the Live CD can be used to recover files from a hard-drive, even without needing a password. I'm wondering if this software can be used for malicious purposes, such as stealing passwords from local computers in a network...or worse. Is this fear of mine justified, or are the security measures in linux distros more rigorous than what they make them out to be?

I know other LiveCD distros advertise this capability; I'm just wondering if they double as hacking tools.

---

### Post by epimer on 2007-09-18
As I understand it, it's long been true that security measures will more or less be compromised if somebody has physical access to your system. I don't know how this affects passwords (they're not stored as plain text, but they could be otherwise accessible?), but it's certainly true that a LiveCD is an easy way to gain root access to a filesystem.

So put a password on your BIOS and GRUB!

---

### Post by mips on 2007-09-18
Might help to use an encrypted filesystem.

---

### Post by LaRoza on 2007-09-18
Any live disk can do that, assuming it can be booted and the FS is not encrypted.

That is nothing new. 

Even a BIOS password is easy to break (remove the battery, or use the jumpers), security of information comes from encryption and restricted access.

---

### Post by tgalati4 on 2007-09-18
This is also why Dell's and other business computers do not enable "boot from CDROM" by default.  It requires going into the BIOS and turning on "boot from CDROM".

So, to improve security:  remove CDROM from list of boot devices and put a password on BIOS as previously suggested.  Of course this will cause other problems--like IT folks forgetting the password.

---

### Post by LaRoza on 2007-09-18
> **tgalati4 said:**
> 
So, to improve security:  remove CDROM from list of boot devices and put a password on BIOS as previously suggested.  Of course this will cause other problems--like IT folks forgetting the password.

BIOS passwords are easy to break, so don't rely on them. Clear the CMOS settings, and the password is gone.

---

### Post by TheThinker on 2007-09-18
Thanks for the suggestions everyone. I guess file-encryption is the best option, apart from setting up a password for my BIOS settings? That I don't mind, since I already have around five passwords to remember for different accounts (e-mail, etc). 

Is it possible to tailor a unique Rescue CD for your own system, assuming it's been encrypted, so that it's the only boot-disk that can have root access? Just wondering.

---

### Post by LaRoza on 2007-09-18
> **TheThinker said:**
> ...apart from setting up a password for my BIOS settings? 

Open the case, look at the motherboard, there is a little battery (circle, flatish). If that battery were removed for a few seconds, any password you had in the BIOS would be gone.

---

### Post by igknighted on 2007-09-18
Why would you give someone that you don't trust physical access to your computer?

EDIT: Or if you had to, why would you leave important/confidential files on that computer?  Even file system encryption isn't perfect, all the person would need to do is walk up with a Norton Ghost disk and image your file system, then they'd have forever to de-crypt it.

---

### Post by TheThinker on 2007-09-19
> **igknighted said:**
> Why would you give someone that you don't trust physical access to your computer?

EDIT: Or if you had to, why would you leave important/confidential files on that computer?  Even file system encryption isn't perfect, all the person would need to do is walk up with a Norton Ghost disk and image your file system, then they'd have forever to de-crypt it.

It's not that I WANT someone to have physical access to my computer, it's that I want that computer to be more difficult for anyone without my permission to access.  I'm not being paranoid here. Forget personal files; some jerk might as well just screw up my system settings if he/she wanted to.

And no, I don't have files, like my social, on that computer...but I will. Who here doesn't have important files to protect, or will never have files to protect?

Also, consider this. Last week I gave a copy of NimbleX to my parents and I had a tough time convincing them to keep it. Their concern is like my own, except it's more about the siblings living at home that may abuse the rescue-disk.  I said that they should hide the disk if they're so concerned, which they soon did. Ironic, isn't it, that a "Rescue-CD" should be hidden?

I already know that practically any software can be abused. I'm just wondering if there are less abusable alternatives, such as what I had asked in my previous post.

For now I'm going for encryption. Thanks LaRoza for that explanation.

---

### Post by karellen on 2007-09-19
you're a little paranoid. if someone has physical access to your computer, it can do anything with your data, given enough time. but if someone has physical access, that should mean is a person trusted by you. in my case, it's just my sister.

---

### Post by smoker on 2007-09-19
if you want to be safe fit a removable hard drive caddy, then you can take your hard drive with you, or store it away from your computer. some examples here: [http://www.circotech.com/removable-hd-kits-ide.html](http://www.circotech.com/removable-hd-kits-ide.html)

---

### Post by K.Mandla on 2007-09-20
> **smoker said:**
> if you want to be safe fit a removable hard drive caddy, then you can take your hard drive with you, or store it away from your computer. 
Really, that is the only solution I would trust. It's like taking the radio out of your car if you don't want it stolen. 

And as I was told, many moons ago, if someone has physical access to your machine, all security bets are off.

---

### Post by TheThinker on 2007-09-20
Thanks Smoker! That's a cool idea. Kind of reminds me of Mr.Been taking out his steering wheel from his car to prevent any theft, and it's an old mini-cooper of all things. LOL! 

Well, that's about it for me. Thanks to everyone for contributing your two-cents. I quite enjoyed reading your suggestions :KS Cheers to you all!

---

### Post by jinx099 on 2007-09-20
> **karellen said:**
> you're a little paranoid. if someone has physical access to your computer, it can do anything with your data, given enough time. but if someone has physical access, that should mean is a person trusted by you. in my case, it's just my sister.

Its a good idea, but then you have to worry about wear and tear on the drive.  For example, if you leave the drive in your car for too long, if could get cooked in the heat.

So can you afford data loss?  If you need data integrity, then you need RAID-1 or higher, which mean you'd need to take 2 or more drives with you all the time.

---

