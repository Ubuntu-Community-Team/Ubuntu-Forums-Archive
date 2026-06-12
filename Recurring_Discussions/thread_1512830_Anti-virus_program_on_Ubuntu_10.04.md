---
title: "Anti-virus program on Ubuntu 10.04?"
date: 2010-06-18
forum: Recurring Discussions
---

### Post by paulgreen35 on 2010-06-18
Hi,

I have Ubuntu Desktop 10.04 installed on my laptop.  Could someone tell me if there's antivirus program already installed with the operating system or would I have to download one myself?

Thanks
Paul

---

### Post by Asmodai on 2010-06-18
No to both, as you don't *need* one.

---

### Post by Strongman332 on 2010-06-18
if you have to have one use clamtk.

---

### Post by OtakuWrath on 2010-06-18
Linux is fairly safe as it is, no need to worry too much about viruses.. ;)

---

### Post by bodhi.zazen on 2010-06-18
Moved to recurring discussions.

Linux is not windows and there are no known active linux viruses. Your system was patched to for the old known linux viruses long ago.

See : 			                          			 			[Ubuntu Security]("http://ubuntuforums.org/showthread.php?t=510812")

---

### Post by aysiu on 2010-06-18
There are things you can do to keep your Ubuntu safe, but the default settings are pretty good for basic security. No system is invincible, though. That said, antivirus will not be an effective measure to protect your Ubuntu installation. See bodhi.zazen's link for more details about what you can do to actually harden security in Ubuntu.

---

### Post by paulgreen35 on 2010-06-19
Thank you to those who commented on my post.

---

### Post by Random_Dude on 2010-06-19
I think it would be better for you to think about the firewall first.
There's one already on your Ubuntu installation called UFW (uncomplicated firewall), but it's disabled.

To enable it just type:
```
sudo ufw enable
```

Or you can install GUFW which allows you to configure the firewall without the console (though a GUI).

As for viruses: clamav + clamtk. Never had problems with viruses on Ubuntu, but you can install them anyway.

Cheers :cool:

---

### Post by Chame_Wizard on 2010-06-19
What the heck is an anti-virus software?:lolflag:

---

### Post by Shining Arcanine on 2010-06-20
> **Chame_Wizard said:**
> What the heck is an anti-virus software?:lolflag:

What is a virus? ):P

---

### Post by lisati on 2010-06-20
> **Shining Arcanine said:**
> What is a virus? ):P

What's Malware? Why do I need to run a Windows program to reset my (non-existent) Facebook password? :D

Security begins in the chair in front of the computer. (In other words, be smart with what you allow on your computer and what you look at....)

---

### Post by HotshotGG on 2010-06-20
> **OtakuWrath said:**
> Linux is fairly safe as it is, no need to worry too much about viruses.. ;)

While this is true I would still use ClamAV to add an extra-layer of protection on top your home machine or server! Most trojans roaming around in the wild are Win32 based viruses. The problem with this is say your using Virtualization software for example and it has elevated super-user privileges? Is that a chance you are willing to take? I certainly am not. :neutral:. You also forget about something else commonly known as rootkits. They are both stealthy and can replace any of common processes within Unix they seem like they will more of threat to Linux in the future then malware will be. They hook into the operating system and by the time you know if you have been compromised. Just things to consider if you opt to not run anti-virus software.

---

