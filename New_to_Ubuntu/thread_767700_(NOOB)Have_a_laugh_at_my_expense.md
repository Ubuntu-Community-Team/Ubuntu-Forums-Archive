---
title: "(NOOB)Have a laugh at my expense"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by gav-the-lad on 2008-04-25
Having just switched from windows xp, and being the security continuous person i am, and having to rely on a firewall, anti spyware and anti virus software. Do i need to do the same with Ubuntu?

---

### Post by Jimmy9pints on 2008-04-25
I am not an expert but as far as I understand Ubuntu doesn't need any antivirus. I am not sure about the firewall... I'd like to know myself.

---

### Post by kelvin273 on 2008-04-25
None of these things are as necessary for Ubuntu as they are for Windows. However, there is a Linux-compatible firewall called Firestarter, which you can get under Applications --> Add/Remove (just search for it, check the box next to it in the search results, and click Apply Changes). There are anti-virus programs for Linux, but I think they're more targeted toward servers than individual desktops. I don't know of any anti-spyware programs for Linux.

---

### Post by spiderbatdad on 2008-04-25
Here's a thread that might be of interest. [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by stalkier on 2008-04-25
> **gav-the-lad said:**
> Having just switched from windows xp, and being the security continuous person i am, and having to rely on a firewall, anti spyware and anti virus software. Do i need to do the same with Ubuntu?

Not that I know of. I know Ubuntu has a built in firewall. You will need to install the GUI for it. it is in the repos. There are also AV etc in the repos if you must have it.

---

### Post by Joeb454 on 2008-04-25
You can use a firewall, there is one installed by default (iptables) though you would be better off installing a GUI Front-End for this.

And no you won't need any anti-virus when running Ubuntu :D Unless you want to scan Windows files that is :p

Personally I don't run a firewall, and I haven't for around 2 years, because my router - like most routers nowadays - has a built in firewall. I believe routers themselves are hardware firewalls because they have 1 IP for several PC's it's harder to get through a router :)

---

### Post by stalkier on 2008-04-25
> **kelvin273 said:**
> None of these things are as necessary for Ubuntu as they are for Windows. However, there is a Linux-compatible firewall called Firestarter, which you can get under Applications --> Add/Remove (just search for it, check the box next to it in the search results, and click Apply Changes). There are anti-virus programs for Linux, but I think they're more targeted toward servers than individual desktops. I don't know of any anti-spyware programs for Linux.

Avast has one version for linux. It is a free download. I have installed it but could not get it running. I am sure I just don't know what I am doing. :D

---

### Post by crjackson on 2008-04-25
> **gav-the-lad said:**
> Having just switched from windows xp, and being the security continuous person i am, and having to rely on a firewall, anti spyware and anti virus software. Do i need to do the same with Ubuntu?

Are you hosting windows files or windows email users.  If not, then no, you don't really need anything.

---

### Post by Harpoon on 2008-04-25
Perhaps a bit of personal experience will help you judge:

I've had at least one active linux installation running for the past ten years (in addition to all those MS releases).  On the linux side I have never encountered a virus/worm/trojan.  Linux is secure enough that you don't really **need** to worry about the firewall issue, unless you have some specific IPs that you really do want to blacklist (block).  If that's the case, install Firestarter -- easy to use gui.

For that extra bit of security paranoia, go to synaptic and search for "rootkit."  There are two programs there that will thoroughly check to make sure you have not been secretly invaded.

I have spent countless hours on curing windows virus problems, and a few minutes periodically checking for rootkits.

But, that's only ten years experience.  Time will tell.....

---

### Post by axor1337 on 2008-04-25
there are some anti-virus tools for Linux My personal favorite is avast  I use on windows machines at work and it has a port for Linux.  This is great to have if you transfer files from Ubuntu to Windows  Plus their are a few Linux virus's out there. As far as a firewall, if you are running behind a router chances are that you are already behind a firewall built in to the router if not it may be a good idea but I don't use one.

---

### Post by BaffledMollusc on 2008-04-25
Well, if you're into anecdotal evidence:

I've been running Windows XP and various Linux distros on about a 50/50 basis over the past five years or so. I'm pretty security conscious under Windows, but even so, I've had to remove a few viruses / rootkits / spy and adware over the years. Under Linux, I've never even tried to be security conscious and had zero problems, even without using any virus-checkers or firewall.

---

### Post by BIGtrouble77 on 2008-04-25
Virus', spyware and firewalls are really not needed on a Linux desktop.  At least not for the reasons they are needed for a windows desktop.  So don't worry about them.  

What you do need to worry about is following instructions and howto's on these (and other) forums and potentially executing malicious commands.  Whenever you run commands that require root authentication double check that you are not doing something that can harm your system.  New users have a tendency to cut and paste like the wind, but have no idea what they are doing.  It's always good to read through the entire thread before you start executing commands.

---

### Post by friendofpugs on 2008-04-25
Thanks Big- that's sound advice for all us newbies. Look before you leap.

---

### Post by Crope on 2008-04-25
I've heard of something called ClanAV that's an antivirus for Linux; haven't really looked into it though. Try googling it.

---

### Post by Paqman on 2008-04-25
> **kelvin273 said:**
> However, there is a Linux-compatible firewall called Firestarter

Just to clarify this: Firestarter is not a firewall in the sense of a Windows firewall. You don't need to leave it running all the time.

Firestarter is just a tool for configuring the built-in Linux firewall system called iptables. You only need to run Firestarter when you want to make changes to your firewall, which you normally never need to do.

---

### Post by gav-the-lad on 2008-04-26
Thanks for your views guys:) This is one of the main reasons i switched from xp to ubuntu, i was just sick and tired of scanning for viruses etc. Now i don't have to worry about it. Its great:guitar:

---

