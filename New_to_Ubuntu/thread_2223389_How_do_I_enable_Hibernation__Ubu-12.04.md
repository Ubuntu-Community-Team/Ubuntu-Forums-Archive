---
title: "How do I enable Hibernation?  Ubu-12.04"
date: 2014-05-10
forum: New to Ubuntu
---

### Post by nivek2 on 2014-05-10
I cannot enable hibernation on my desktop, It works fine on my laptop.
I tried a CLI commands I googled, but nothing seems to work.
Is there a way, maybe an easier way?  And why isn't this option in the System settings? weird...

Well thanks for any help, or advise anyone can give.

-NiVeK

---

### Post by Frogs Hair on 2014-05-10
If the installation was done via the Windows Installer aka Wubi suspend is possible but not hibernation because there is no swap partition . If you installed a traditional dual boot please wait for suggestions because I never use hibernation .

---

### Post by Vladlenin5000 on 2014-05-10
Hibernation requires a swap partition with space equal or higher than the system's RAM. That's the first thing to check for... Tell us what you have and we'll see from there.

---

### Post by nivek2 on 2014-05-10
I've stopped using Win, so this is just Ubuntu (actually Mint13 on Desktop)  Just a fresh instal.

Thanks [**[COLOR=#C61919][B]Frogs Hair**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=1024576") for answering.

---

### Post by nivek2 on 2014-05-10
Thanks! [ 						 							[IMG]http://ubuntuforums.org/customavatars/avatar1468732_3.gif[/IMG] 						 					]("http://ubuntuforums.org/member.php?u=1468732") 				 				 					 						 	[**[COLOR=#000000]Vladlenin5000[/COLOR]**]("http://ubuntuforums.org/member.php?u=1468732"), I'll check that out, but currently my desktop is not loading, I'll give you my post about that... ;)
You seem smart, maybe you'll know that post, lol

[http://ubuntuforums.org/showthread.php?t=2223386](http://ubuntuforums.org/showthread.php?t=2223386)

---

### Post by sam_baker2 on 2014-05-10
Do you need to hibernate or will suspend do? I have a desktop with 12.04 on it and I use the terminal command rtcwake .  I Have it in a script with a desktop icon to activate it. You can set it to suspend to memory or disk.

---

### Post by nivek2 on 2014-05-11
> **sam_baker2 said:**
> Do you need to hibernate or will suspend do? I have a desktop with 12.04 on it and I use the terminal command rtcwake .  I Have it in a script with a desktop icon to activate it. You can set it to suspend to memory or disk.

I would like hibernate, I made a desktop link to hibernate, but would rather also have it in my shutdown options (plus I like to learn new things).  I have it in the shut-down options on my Laptop (same distro). Just not sure why it isn't available here. I'm not sure if I configured the laptop, or it was already available...

---

