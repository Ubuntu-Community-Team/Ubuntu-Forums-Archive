---
title: "Antivirus + Rootkit hunter"
date: 2011-11-15
forum: Recurring Discussions
---

### Post by Foobarz on 2011-11-15
Are there any good free antivirus for linux that come with a rootkit hunter or am I asking for too much out of one application?

---

### Post by CharlesA on 2011-11-15
Rkhunter is notorious for false positives and you don't really need anti virus on a *nix box unless you are sharing files with windows machines.

Check out the page here:
[https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)

---

### Post by oldsoundguy on 2011-11-15
> **Foobarz said:**
> Are there any good free antivirus for linux that come with a rootkit hunter or am I asking for too much out of one application?

AV programs are really NOT needed for any Linux unless you are using it for a server and have Windows machines hung onto the network.  Then it is just to protect the Windows machine(s).
You can not install a virus or malware into Linux with just a single click .. it takes steps and it also takes a password.  
HOWEVER .. your BROWSER of choice can get popped now and again if you are not careful.

---

### Post by Foobarz on 2011-11-15
I know that viruses are quite ludicrous since everything needs root permission and everything can be displayed and not hidden. However, What about rootkits? Don't those go around undetected?

---

### Post by 3rdalbum on 2011-11-15
> **Foobarz said:**
> I know that viruses are quite ludicrous since everything needs root permission and everything can be displayed and not hidden. However, What about rootkits? Don't those go around undetected?

Rootkits don't spread themselves - they require human input to put them into your computer, and there must be some avenue into your computer.

In other words, you need to be running some sort of server service on your computer, that has a security flaw that allows a human attacker to run code on your computer. The code must run as root or the attacker must find another security flaw to gain root access. If you are running a vulnerable server service, it also can't be behind a firewall as then the attacker won't be able to connect to it.

The liklihood of all this happening on your home desktop is pretty slim. If you're running a web server that takes credit card details then you need to worry about rootkits. Otherwise it's probably not going to happen.

---

### Post by Kaboom3009 on 2011-11-15
> **3rdalbum said:**
> Rootkits don't spread themselves - they require human input to put them into your computer, and there must be some avenue into your computer.

In other words, you need to be running some sort of server service on your computer, that has a security flaw that allows a human attacker to run code on your computer. The code must run as root or the attacker must find another security flaw to gain root access. If you are running a vulnerable server service, it also can't be behind a firewall as then the attacker won't be able to connect to it.

The liklihood of all this happening on your home desktop is pretty slim. If you're running a web server that takes credit card details then you need to worry about rootkits. Otherwise it's probably not going to happen.

OR if you type your root authorization in when youn didnt do anything that really needs root authorization. OR you downloaded some  software from a site that is NOT very trustworthy and the installer INCLUDES some form of UNWANTED software incorporated within the software you want.

---

### Post by Kaboom3009 on 2011-11-15
> **CharlesA said:**
> Rkhunter is notorious for false positives and you don't really need anti virus on a *nix box unless you are sharing files with windows machines.

Check out the page here:
[https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)


I should have posted my reply to here instead of 3rdalbum BUT it does fit there as well .. Just because it is NOT prevalent doesnt mean they dont exist. The sooner Linux learns to **Cover It's Butt** the safer it will be when it advances in the market share of Operating systems.

 If you go by a generic example .. 6billion windows and Mac users .. 10% infection .. LOTS of people actively trying to clean them ... 600k Linux users 10% infection WORSE - THEY assume they dont got anything.

Just because its Linux doesnt mean it cant happen. It just means it's LESS likely.

---

### Post by CharlesA on 2011-11-15
> **Kaboom3009 said:**
> OR if you type your root authorization in when youn didnt do anything that really needs root authorization. OR you downloaded some  software from a site that is NOT very trustworthy and the installer INCLUDES some form of UNWANTED software incorporated within the software you want.

Stick to the repos. If you need to install something that isn't in the repos, be sure to check it out before installing it.

> **Kaboom3009 said:**
> I should have posted my reply to here instead of 3rdalbum BUT it does fit there as well .. Just because it is NOT prevalent doesnt mean they dont exist. The sooner Linux learns to **Cover It's Butt** the safer it will be when it advances in the market share of Operating systems.

 If you go by a generic example .. 6billion windows and Mac users .. 10% infection .. LOTS of people actively trying to clean them ... 600k Linux users 10% infection WORSE - THEY assume they dont got anything.

Just because its Linux doesnt mean it cant happen. It just means it's LESS likely.

Right. There are *nix "viruses" out there (proof of concept mostly), but none in the wild. Apparmor/SElinux on Firefox and any other internet aware app would limit the damage if you got something. Keyloggers don't get installed automagically.

EDIT: Check the link I posted, or the monster thread [here]("http://ubuntuforums.org/showthread.php?t=1873643").

---

### Post by Dangertux on 2011-11-16
Little known (read acknowledged) fact : rootkits are more devestating on Linux than Windows. (Incoming hatemail I'm sure).

Due to the nature of how the Linux kernel and operating system work, a rootkit is much more difficult to detect, even for complex anti-malware solutions on Linux than Windows. The silver lining? Rootkits are a much more targeted attack on Linux than Windows.

Weigh your risks, make your decisions and security policies accordingly.

---

### Post by cariboo on 2011-11-16
Asked and answered to many times to count. Moved to recurring.

---

### Post by nerdopolis on 2011-11-16
> **Kaboom3009 said:**
> I should have posted my reply to here instead of 3rdalbum BUT it does fit there as well .. Just because it is NOT prevalent doesnt mean they dont exist. The sooner Linux learns to **Cover It's Butt** the safer it will be when it advances in the market share of Operating systems.

 If you go by a generic example .. 6billion windows and Mac users .. 10% infection .. LOTS of people actively trying to clean them ... 600k Linux users 10% infection WORSE - THEY assume they dont got anything.

Just because its Linux doesnt mean it cant happen. It just means it's LESS likely.

I think in order for a Linux antivirus to work, there HAS to be viruses out there in the wild for it to actually detect.

---

### Post by Dangertux on 2011-11-16
> **nerdopolis said:**
> I think in order for a Linux antivirus to work, there HAS to be viruses out there in the wild for it to actually detect.

Yes and no, in order to detect a threat as what it is, often times the threat must be signatured, therefor their must be some version of it in the wild. However, through the use of heuristics anti-malware solutions can detect activities that are malicious in nature. So there would be a purpose, though anti-malware is not an all encompassing solution, it is definitely a useful layer if implemented and maintained properly.

---

### Post by eveg on 2011-11-22
> **3rdalbum said:**
> Rootkits don't spread themselves - they require human input to put them into your computer, and there must be some avenue into your computer.
 
In other words, you need to be running some sort of server service on your computer, that has a security flaw that allows a human attacker to run code on your computer. The code must run as root or the attacker must find another security flaw to gain root access. If you are running a vulnerable server service, it also can't be behind a firewall as then the attacker won't be able to connect to it.
 
The liklihood of all this happening on your home desktop is pretty slim. If you're running a web server that takes credit card details then you need to worry about rootkits. Otherwise it's probably not going to happen.
 
i disagree. i made the error of clicking on a link from this website or something convincingly impersonating, and the result was a rootkit in a portable drive which is now useless, and in a machine which does not go online, because i prefer not to be accountable for others' criminal activity online. if anyone would like to pretend linux is invulnerable to criminal hackers, please stop insulting everyone's intelligence. while i apollogize if the site feels insulted, i would appreciate it not pretending it could not be criminally impersonated.
 
'another security flaw', yes, well, again, i don't mean to be rude, but *being online* qualifies as 'another security flaw', if we're being realistic and honest.

---

### Post by Dangertux on 2011-11-22
> **eveg said:**
> i disagree. i made the error of clicking on a link from this website or something convincingly impersonating, and the result was a rootkit in a portable drive which is now useless, and in a machine which does not go online, because i prefer not to be accountable for others' criminal activity online. if anyone would like to pretend linux is invulnerable to criminal hackers, please stop insulting everyone's intelligence. while i apollogize if the site feels insulted, i would appreciate it not pretending it could not be criminally impersonated.
 
'another security flaw', yes, well, again, i don't mean to be rude, but *being online* qualifies as 'another security flaw', if we're being realistic and honest.


While I completely agree that Linux is not invulnerable to attack (everyone knows I'm constantly pointing out it is). 

I think it would be very unlikely that you "clicked a link" and your system was root kitted. Yes, something bad may have happened, however root kits are usually somewhat complicated, need configuration for their host system and usually have to be compiled against the kernel they are kitting. Malicious links, and browser code parsing are not very conducive to doing any of that. Of course you could have clicked a link been shelled, and then root kitted, but that's a very targeted attack.

Besides, you can't root kit storage, you root kit a kernel, library or system function in an operating system, so unless you were running a persistent install off of the drive it didn't happen. 

Hope this helps.

---

### Post by 3rdalbum on 2011-11-23
> **eveg said:**
> i disagree. i made the error of clicking on a link from this website or something convincingly impersonating, and the result was a rootkit in a portable drive which is now useless

That's not possible. There's no computer inside your hard drive. It's like saying that your speakers or your fridge got a rootkit. Your drive must have failed for some other reason.

> and in a machine which does not go online, because i prefer not to be accountable for others' criminal activity online.

Very laudable. A lot of people continue to go online even when they know that their computer is infected, and they get angry when you tell them why they should stay offline until it's fixed.

> if anyone would like to pretend linux is invulnerable to criminal hackers, please stop insulting everyone's intelligence.

I hope you're not referring to me. Linux is not invulnerable to attackers. However, it's highly unlikely that a desktop Ubuntu box hidden behind an entirely-closed firewall and used with common sense, will be successfully attacked. Not impossible, but so unlikely that it's barely worth thinking about.
 
> 'another security flaw', yes, well, again, i don't mean to be rude, but *being online* qualifies as 'another security flaw', if we're being realistic and honest.

You misunderstand. I talked about an entry-point; the way for an attacker to enter your system; and then I mentioned another security flaw to obtain root.

Let's say that the entry-point was a poorly-configured web server that runs as root. The attacker gains the ability to run code in the web server's process. They can probably install a rootkit now, because the web server process has root permission. (assuming the absence of AppArmour or SELinux or anything similar).

Now, let's say the entry-point is your web browser. You've been convinced to navigate to a maliciously-crafted web page that can execute code within your web browser's process.

However, the attacker (in theory) cannot install a rootkit. They only have the same permissions as the web browser's process, which is the regular user account. In order to gain root, they need to find a second security hole that allows them to get root.

Do you understand now?

Incidentally, I'm aware of some of the security oversights in a typical Linux desktop distro. Allowing the web browser to write to ~/.config/autostart or ~/.config/menus or ~/.local/share/applications/ makes it possible for a malicious-code attack on your web browser to obtain the 'sudo' password by creating a false menu item with a false gksudo prompt (for instance, a fake Synaptic menu item).

Known, but there doesn't seem to be any guard against it except "Patch holes in the web browser so fewer people know how to attack it".

Still, the likelihood of being attacked in so elaborate a way is quite low. When Linux gets more popular the likelihood will get higher, at which point there will be exploit code in the wild and distro-makers will rush to implement a proper guard against it.

Generally Linux is secure. One or two areas need work, but if you keep your common sense about you it's unlikely that you'll get attacked. Not impossible, as you'd know, but unlikely.

---

