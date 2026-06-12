---
title: "A new Linux security model (good or bad?)"
date: 2007-05-04
forum: Other OS Talk
---

### Post by floke on 2007-05-04
Hey all,

I've been using Pardus all week and want to ask the community's opinion about its security model. There's not a lot of English documentation on it (the distro's made by the Turkish Institute of Science and Cryptology) so any thoughts would be welcome.

As far as I understand it, Pardus lets the administrator (i.e. me) log in and then run as root in the GUI - i.e. I can add/remove programs in the GUI, change firewall settings etc. without having to enter my password (the assumption being that malware can't click and point). In the CLI, however, the user is not root and must enter their password when trying to add/remove software or change system files.

This makes it easier in the GUI and as far as I can think of, does not represent any security threat (if I left my PC unguarded for 10 mins then someone could come along and remove stuff - but then I could just lock my screen). In the terminal, though, its Linux-security-business as usual.

Any thoughts?

---

### Post by goumples on 2007-05-04
Sounds reasonable enough.. If it saves time and doesn't compromise anything, then why not.

---

### Post by floke on 2007-05-04
That's what I think, but it takes a bit of getting used to after getting used to the traditional Linux way. But really, if I open synaptic to add or remove then do I really have to enter my password? The only drawback I can see is leaving your PC unguarded, but then that's a security issue anyway isn;t it?

<still not 100% sure, but convincing myself - I just can't see what might be wrong with it>

---

### Post by goumples on 2007-05-04
> **Steve.K said:**
> That's what I think, but it takes a bit of getting used to after getting used to the traditional Linux way. But really, if I open synaptic to add or remove then do I really have to enter my password? The only drawback I can see is leaving your PC unguarded, but then that's a security issue anyway isn;t it?

<still not 100% sure, but convincing myself - I just can't see what might be wrong with it>

Yea leaving the computer is always a risk unless you trust everyone that COULD get on it implicitly.  If you dont lock down the machine and leave it, then any jackass could pop in a dos bootdisk, restart and fdisk your whole harddrive clean.  :lolflag: 

 Thing is, they could do this regardless of whether or not there are passwords to access the package manager.

---

### Post by juxtaposed on 2007-05-04
I think it's quite a good idea in terms of practicality, but it might go against the 'spirit' of linux security...

---

### Post by pelle.k on 2007-05-05
I have recently tried pardus 2007.1 out, and i must say it's a really nice distro. I like their clear goals, and organized structure.

The funny thing is, I myself have been thinking the same thing. I would like the system to bug me less, and let me, as a power user, work more seamlessly with GUI apps using root privilegies. **That doesn't mean i would like this to be the default behavior though. I would like have this behavior available with minimum fuss.**
I can always su, or edit sudoers to achieve something similar, but this isn't really optimal. If i could have the system somehow let me run _only_ GUI apps as root without a password prompt, but blocked any attempts to use a terminal/bash in the same way that would be great.

I'm not 100% clear on how/what pardus does, but i'm giong to investigate further. Until then i found an article that discusses this "feature". It's not in pardus favor though.
[article link...]("http://www.beranger.org/index.php?article=2677&page=3k")
 I myself have not decided what to think yet. As i said, i would like to have something like this available, but not by default.

Maybe a better way would be if i could add applications, with valid .desktop files (from kde/gnome menu etc..) to a list of applications that could be run with NOPASSWD. This could be a little bit problematuc though, as some applications will only ask you for root privileges _when_ you are performing a certain actions in them. So i don't know how this would be achieved, but you would then have to let an application run as user, but still gain root privilegies for certain actions. That last part would be a little harder to achive with my example with .desktop applications.

Rant over. This is an interesting discussion. Please continue! :)

---

### Post by 3rdalbum on 2007-05-05
It sounds a bit worrying to me. If the desktop is running as root, that will mean that some network-facing parts of the desktop (if there are any) are also running as root.

---

### Post by pelle.k on 2007-05-05
The desktop, itself, isn't running as root. Just _some_  administration oriented GUI tools.

---

### Post by floke on 2007-05-05
The more I think about it the more I think I like it.
Am currently in Ubuntu: I open synaptic and get asked for my password - now either (a) I'm really me and I meant to open synaptic - in which case I'm bound to enter my passwd anyway; or (b) I'm someone else who has physical access to the machine - in which case software additions/removals are the last thing I should worry about.

It doesn't feel 'quite right' - but I can't rationally think of anything wrong with it...

---

### Post by fkdev on 2007-05-05
> **pelle.k said:**
> The desktop, itself, isn't running as root. Just _some_  administration oriented GUI tools.
So it just suids these tools?
(check the output of stat on a binary to see, or check it with nautilus/other filemanager and look at it's properties)

---

### Post by rai4shu2 on 2007-05-06
> **Steve.K said:**
> As far as I understand it, Pardus lets the administrator (i.e. me) log in and then run as root in the GUI - i.e. I can add/remove programs in the GUI, change firewall settings etc. without having to enter my password (the assumption being that malware can't click and point).

If the malware in question is some kind of buffer overflow that allows it to run whatever arbitrary code is injected into some particular memory, you may assume that code could very well click and point (or whatever else a user is able to do).

This would basically mean that malware would then be able to add/remove packages, start/stop services and change your firewall settings (i.e. more than enough to set up a spam bot on your computer).

If the user never installs anything beyond a properly authenticated repo or disc, then it shouldn't be a problem. The real danger would be if the user downloaded some unknown program.

---

### Post by floke on 2007-05-07
But isn't that always a danger - in ubuntu I go to install an unauthenticated deb package, or compile from source, and must enter my password - so the security model makes no difference in this case. Installing unauthenticated software carries intrinsic risks by its very nature.

---

### Post by rai4shu2 on 2007-05-07
Well, to be honest I have no idea whether Pardus GUI configs can be spoofed. I'm pretty sure you can't spoof gksudo, so maybe that's not the real danger after all.

---

### Post by Extreme Coder on 2007-05-07
There wouldn't be any REAL use for it, unless Ubuntu has some real GUI adminstration tools, like the Mandriva/PCLOS control center. Untill then, the admin can use the CLI.

Extreme Coder

---

### Post by floke on 2007-05-07
No REAL use for what? I don't understand. The Pardus model, or passwords in the GUI?

---

