---
title: "Wipe free space on encrypted drive"
date: 2016-02-14
forum: New to Ubuntu
---

### Post by carla4 on 2016-02-14
Hi,
So I have an encrypted hard drive on my laptop, and I deleted some files using bleachbit, but did so without making sure I had it set up to securely delete them, which was what I wanted. So, now, I see my best option (using bleachbit) is to wipe free space, to securely delete the already deleted files. Is this safe to do, with an encrypted drive/OS? 
Apologies if it is a stupid question, and thank you!

-Carla

---

### Post by ian-weisser on 2016-02-14
It's not a stupid question, but it is a bit confusing.

Perhaps you are mixing two concepts?
I see little benefit using secure delete on an encrypted filesystem.
The data is already irrecoverably scrambled and worthless without your key.

---

### Post by carla4 on 2016-02-14
Well, maybe just humor me a little? :)
I guess I wanted to get my head around how I could keep my data entirely secure. I know it's unlikely, but in theory, if I didn't secure delete the data couldn't a hacker retrieve the data from me if they broke into my computer? Put another way, if I ended up with a virus on my system, couldn't the hacker access any data I hadn't securely deleted, because my system would already be unencrypted as it will be in use?
So with that in mind, because I deleted some files that in hindsight I would rather have deleted securely, I thought it best to use bleachbit to wipe the free space, although like I said, I wasn't sure if that might mess anything up.

---

### Post by ian-weisser on 2016-02-14
Good security is a set of practices, not just one. But I'm sure you know that already.

Okay, if Badperson gains access to your system AND the breach is not contained by AppArmor or permissions AND Badperson knows your key, then they can decrypt anything they wish anytime they wish and your life is an open book to them.
If Badperson gains access to your system WHILE you are logged in, and the breach isn't contained by AppArmor or permissions, then they can see everything decrypted. The moment you logout, it become gibberish.
If Badperson plants a sniffer or keylogger on your system, and the breach isn't contained by AppArmor or permissions, then the malware can see everything decrypted only while you are logged in.

But, honestly, this is the earthquake-during-a-hurricane (worst of the worst) scenario. Any system with data THAT sensitive should have an air-gap, and not be accessible to the public internet anyway.

For the rest of us, security practices focus on prevening Badperson from gaining access to your system in the first place, preventing privelege escalation, preventing the implantation of malware, and preventing random file-browsing. A whole host of security practices go into those, like having no open ports in the default install of Ubuntu, like using software from the Ubuntu repositories, like subscribing to Ubuntu's security updates, etc.

---

### Post by carla4 on 2016-02-14
Thanks Ian, for the detailed explanation/response! It's helped a lot with me understanding different threat levels and the realities of how that might all play out.
So, in the first example you have, where Badperson gets access to the system and the breach is not contained and they know my key, they basically have free run of my computer. So, going with that idea, they'd obviously be able to retrieve files that I didn't delete securely.

Basically, I had my bank details written down and saved on my computer, and though I deleted the file, I didn't securely delete it, so I know enough to understand that file could be floating around somewhere still. So, even though I have my computer encrypted, and so on, I'd like to now make sure that deleted file is unretrievable in case someone gets malicous access to the computer (despite my good practices / precautions).

So, I was planning on using bleachbit to wipe the free space, understanding that would clean up and securely remove my previously deleted file. Is that safe to do on an encrypted drive? Is there a chance it messes things up, or is it just the same as running it on a regular hard drive?

---

### Post by ian-weisser on 2016-02-14
> **carla4 said:**
> Badperson gets access to the system and the breach is not contained and they know my key, they basically have free run of my computer. So, going with that idea, they'd obviously be able to retrieve files that I didn't delete securely.

Sure, you can use bleachbit.
But it's a false feeling of security - it won't actually help in a meaningful way.

A hypothetical wide-open breach that completely exposed your account and encrypted data may expose you to far worse than mere bank fraud (which your bank and  law enforcement would try to recover for you). Your e-mail, browser  passwords, social media accounts, personal photos, business contacts, and  much more would be theirs. They could trash your business and personal reputation using your  own accounts, while locking you out of them. They could re-encrypt your  data and ransom it (or abandon it, effectively securely deleted). They could install a keylogger so they get your bank data  anyway. They could get you into serious legal trouble by downloading ...inappropriate... files.

Bleachbit won't help you with any of that...but good security habits will.

---

