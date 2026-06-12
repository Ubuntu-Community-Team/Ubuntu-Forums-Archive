---
title: "Virus Alert"
date: 2008-04-12
forum: Recurring Discussions
---

### Post by icontrol on 2008-04-12
Is there a way that Windows virus can penetrate my Ubuntu System?

---------------
[New Age Technology](http://icontrol.blogsome.com)
[The Journey Continues](http://mastermind.blogsome.com)
[Everything Matters](http://serial.blogsome.com)

---

### Post by hyper_ch on 2008-04-12
define: "penetrate my Ubuntu System"

---

### Post by netlogic on 2008-04-12
> **icontrol said:**
> Is there a way that Windows virus can penetrate my Ubuntu System?

no. only your wine folder in your home directory.

---

### Post by mrsteveman1 on 2008-04-13
Depends on what you mean.

Windows viruses typically are specific to windows, they exploit a specific known flaw in some service in windows, which then allows easy escalation to control the entire system because of the faulty way services run in windows. Windows specific exploits will have no effect on an ubuntu system.

If however you mean can your ubuntu system end up CARRYING a windows virus and then spreading it to other windows systems, yes it can. For instance, a windows virus can sit on any shared server or drive and then exploit a windows system that is accessing that drive at the moment.

---

### Post by netlogic on 2008-04-13
> **mrsteveman1 said:**
> Depends on what you mean.

Windows viruses typically are specific to windows, they exploit a specific known flaw in some service in windows, which then allows easy escalation to control the entire system because of the faulty way services run in windows. Windows specific exploits will have no effect on an ubuntu system.

If however you mean can your ubuntu system end up CARRYING a windows virus and then spreading it to other windows systems, yes it can. For instance, a windows virus can sit on any shared server or drive and then exploit a windows system that is accessing that drive at the moment.

Wine can't carry a virus. It can only affect itself. exe and com cannot launch wineserver. Launching of wine can cause other dll in the .wine folder to be affected.  Linux can't be a windows virus carrier.

---

### Post by icontrol on 2008-04-14
What I mean in penetrate is that: "AFFECT the system".

Anyways, are there any reported cases that has been classified as VIRUS for Ubuntu Systems? As we all know that Microsoft Windows started with "Virus-Free" Platform yet, as years go on, there came viruses?

Are there any possibilities that it would happen?

Thanks.

---------------
[New Age Technology](http://icontrol.blogsome.com)
[The Journey Continues](http://mastermind.blogsome.com)
[Everything Matters](http://serial.blogsome.com)

---

### Post by mikewhatever on 2008-04-14
> **icontrol said:**
> What I mean in penetrate is that: "AFFECT the system".

Anyways, are there any reported cases that has been classified as VIRUS for Ubuntu Systems? As we all know that Microsoft Windows started with "Virus-Free" Platform yet, as years go on, there came viruses?

Are there any possibilities that it would happen?

Yes there are. No OS is bullet proof.

---

### Post by lancest on 2008-04-14
I doubt you could find anyone on these forums who has a Linux system that was ever hurt badly by a virus.  That does not mean it couldn't happen someday though. This probably has alot more to do with superior Linux system design than the fact that there are considerably fewer Linux desktop users.

---

### Post by hyper_ch on 2008-04-14
In order for a linux virus to be effective it

(1) needs to chmodded to be executable
(2) requires root privileges in order to damage something

While users may be social engineered to fall into this trap (by getting software from dubious sources.... getting tricked into (real) running attachments sent by strangers), a virus normally will have no impact on linux (this far)

---

### Post by mrsteveman1 on 2008-04-14
I've personally seen Linux systems get compromised, there is in fact malware written to exploit Linux and the services which run on it.

This is however a different attack vector than a random worm or a screensaver with a classical virus inside it. The malware targeting Linux is written with the goal of attacking valuable servers.

Linux exploits get neutralized pretty quick though.

WINE itself isn't likely to enable a windows virus to gain control of anything, but I wasn't talking about wine. A linux system can carry a virus targeted at windows on its drive, or on a flash drive, or on a file server. When a Windows system accesses these things, it may in fact execute the code and compromise the windows system. This is why many Linux mail and fileservers run antivirus services, to protect Windows systems accessing their files and messages.

---

### Post by popch on 2008-04-14
This thread has not yet mentioned that we all routinely execute code fetched from the internet in our browsers. Scripts and plugins run without asking for (individual) permissions. How's that for a vector?

---

### Post by mrsteveman1 on 2008-04-14
Browser exploits tend to be browser specific, though there are some cross platform JS exploits that have come up recently, they seem to mostly stay within the browser and control it remotely.

---

