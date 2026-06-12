---
title: "Unattended Upgrades"
date: 2023-02-06
forum: New to Ubuntu
---

### Post by jonfisher on 2023-02-06
I've used Ubuntu for many years and never seen "Unattended Upgrades" upon shut down.
Is this something new, etc...?
Someone educate me...

---

### Post by Dennis N on 2023-02-06
If you try to power off or restart while the Unattended Upgrade process is active (either downloading or installing) you would get a message about waiting until the upgrades are completed. Similarly, if you try to use Software Updater while the U.U. is working, you will have to wait until U.A. exits before Software Updater can work.

Unattended Upgrades are not new.

---

### Post by vmpx on 2023-02-07
You can disable it in:
```
/etc/apt/apt.conf.d/10periodic
/etc/apt/apt.conf.d/20auto-upgrades
```
with:
```
APT::Periodic::Unattended-Upgrade "0";
```

---

### Post by ian-weisser on 2023-02-07
For most users, disabling Unattended Upgrades is unwise. Very unwise...tending toward foolish.

There are enterprise and expert use cases for which Unattended Upgrades hinders more than it helps. But if you have one of those, you also likely have years of experience in this and are unlikely to be asking this question.

For users curious about what Unattended Upgrades is: Just let it do it's job.

If not, then YOU must do it's job. Every day.

---

### Post by ajgreeny on 2023-02-08
I am in agreement with Ian above, though having said that I always remove the unattended-upgrades package from my systems, preferring to run update/upgrade commands very regularly.

It takes very little time and with an alias command just three keyboard keys to do the job. I never use a GUI application to run this as it is not fast enough and generally much less informative about what is happening.

It's your choice but if you don't use that system do ensure that you do the job manually very often!

---

### Post by Impavidus on 2023-02-08
I've completely removed the unattended-upgrades package, but I kept the GUI update-manager, which automatically checks for updates daily and shows a pop-up if any are available for installation. It doesn't automatically download and install the updates. That works good enough on a desktop/laptop system.

---

### Post by DuckHook on 2023-02-08
With all due respect, there are guys like me who don't like anything being done to my computers that I didn't actively start or that I don't consciously control. I find unattended upgrades freaky and scary. I want to know what is being added, changed or removed on every one of my systems at all times. I want to be given the choice of saying "Yes" or "No" and I don't want the computer bypassing me to install stuff without my knowledge or my express permission. Ever. It may seem counter&#8209;intuitive, but that's a security concern.

So, the first thing that I do on all of my own installs is to disable unattended upgrades.

Truth be told, I was reluctant to post this.

I get what Ian is saying and, in support of his sentiments, I do leave this feature enabled on almost all the systems that I install for nontechnical friends and family. In their case, the choice is between something that automatically monkeys with their system versus forgetting (or neglecting) to patch at all. The lesser of the two evils is the former. One might even characterize unattended upgrades as a necessary evil. But it remains an evil and, for responsible power users who patch their systems diligently, the unattended upgrades function is a pain in the neck that is a legitimate target to nerf.

---

### Post by ajgreeny on 2023-02-08
I'm 100% with DuckHook on this; I do not want things running on my machines that I am unable to control, though like DuckHook I don't disable or remove it on my wife's computer as she is most definitely not a computer literate user and I fear updates would possibly happen very irregularly if it was left to her.

Just be grateful that we are able to make such decisions ourselves, unlike in some other OSs!

---

### Post by ian-weisser on 2023-02-08
> **ajgreeny said:**
> Just be grateful that we are able to make such decisions ourselves, unlike in some other OSs!

I'm hoisting a drink to that sentiment.

---

### Post by ActionParsnip on 2023-02-10
> **ajgreeny said:**
> I'm 100% with DuckHook on this; I do not want things running on my machines that I am unable to control, though like DuckHook I don't disable or remove it on my wife's computer as she is most definitely not a computer literate user and I fear updates would possibly happen very irregularly if it was left to her.

Just be grateful that we are able to make such decisions ourselves, unlike in some other OSs!

WSUS gives you the control. You then manage your own updates and so on.

---

### Post by ajgreeny on 2023-02-10
Thanks for that ActionParsnip, though I had to search out what WSUS is, never having heard of it.

For others like me who wish to know:-
> Windows Server Update Services (WSUS) is a Windows server role that can plan, manage and deploy updates, patches and hotfixes for Windows servers, client operating systems (OSes) and other Microsoft software.
I have no idea how it's used or exactly what it offers and have no Windows on which to try it.

---

### Post by ActionParsnip on 2023-02-10
> **ajgreeny said:**
> Thanks for that ActionParsnip, though I had to search out what WSUS is, never having heard of it.

For others like me who wish to know:-

I have no idea how it's used or exactly what it offers and have no Windows on which to try it.

It's how you deploy Windows updates in a managed way in a Windows environment. You can create groups and push updates to them as required. You tell clients to get updates from the WSUS server rather than packages.microsoft.com and you can get all or even no updates as you need. You can also run reports to make sure a critical update is on all servers. If one doesn't have it then it can be pushed out as you wish

---

### Post by DuckHook on 2023-02-10
> **ActionParsnip said:**
> It's how you deploy Windows updates in a managed way in a Windows environment. You can create groups and push updates to them as required. You tell clients to get updates from the WSUS server rather than packages.microsoft.com and you can get all or even no updates as you need. You can also run reports to make sure a critical update is on all servers. If one doesn't have it then it can be pushed out as you wish
I was aware that such a tool existed, though unaware of its exact name, but (there's always a "but" with MS), from Wikipedia:> Licensing

WSUS is a feature of the Windows Server product and therefore requires a valid Windows Server license for the machine hosting the service. The fact that user workstations authenticate themselves on the WSUS service to retrieve their updates makes it necessary to acquire a fileserver client access license (CAL) for each workstation connecting to the WSUS service.[6] Fileserver CAL for WSUS is the same CAL as the one required for connecting to a Microsoft Active Directory, fileserver and printserver, and has to be acquired once for a device or a user.

WSUS is often considered as a free product because fileserver CAL are already paid for in an enterprise network that has a Microsoft Active Directory and thus do not need to be acquired again.[6]

In a network using Samba Active Directory, it is not necessary to purchase CALs to connect to the domain controller or connect to a Samba file server. However, the use of a WSUS server will still require the purchase of client access licenses for all Windows workstations that will connect to the WSUS server.[7] 
So, as I understand it:

[LIST=1]
[*]You need to run a WSUS server (= $)
[*]and, if not enterprise clients, you need to purchase further client access licenses (= more $)
[/LIST]
This is enough of a barrier for a user like me to consider this a typical MS non&#8209;solution.

It's still really hard (if not impossible for the average user) to just reach into the guts of Windows and nerf its autoupdate feature.

---

