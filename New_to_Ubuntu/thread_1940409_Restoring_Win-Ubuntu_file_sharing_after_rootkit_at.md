---
title: "Restoring Win-Ubuntu file sharing after rootkit attack"
date: 2012-03-13
forum: New to Ubuntu
---

### Post by poisonborz on 2012-03-13
Hola,
I have several Windows computers in my network, and a 10.4 Ubuntu server for shared folders. All worked well, until Win7 computer got recently attacked by a rootkit (ZeroAccess/Sirefef). After much effort, I was able to clean it off. I got my networking working, and I'm able to see the windows machines - except for the Ubuntu server. 

**I can ping it**, but it does not show up on network discovery, and if I type the address, it shows 'network path not found (53)'. As I said, everything was working before, so the problem must lie within the Windows machine. What setting could be the culprit?

---

### Post by taseedorf on 2012-03-13
What did you do exactly to get rid of it? Did you do anything to the Ubuntu machines in the process? I'd try checking your firewall... also, try uninstall tcp/ip v4 and reinstalling it.

---

### Post by poisonborz on 2012-03-20
I haven't done anything manually - I used anti-rootkit tools like ComboFix and TSSDKiller. The Ubuntu machine was untampered and other machines can see it. I've already tried disabling Windows Firewall, uninstalled Comodo Firewall.

Update: Now i realized that I can access the share via its IP, but not the name... strange, but at least it works.

---

### Post by Paqman on 2012-03-20
TBH, once a machine has had a rootkit, it can't really be trusted to work the way it's supposed to again. Best thing to do is wipe it clean and reinstall the OS from scratch.

---

### Post by JKyleOKC on 2012-03-20
> **poisonborz said:**
> I haven't done anything manually - I used anti-rootkit tools like ComboFix and TSSDKiller. The Ubuntu machine was untampered and other machines can see it. I've already tried disabling Windows Firewall, uninstalled Comodo Firewall.

Update: Now i realized that I can access the share via its IP, but not the name... strange, but at least it works.Look for a file named "hosts" on the Win7 machine; I've not used any Windows version later than XP so I'm not sure which folder it would be in, but that's the file that translates machine names to IP addresses. Microsoft's "hosts" files usually include a set of comments at their start that tell you the required format. Just add a line to the file, with the IP address followed by a tab and then the machine name, save the file, reboot the Windows machine to get the information loaded back into RAM, and you should then be able to access the machine by name.

You may also need to make similar changes to the /etc/hosts file on your Ubuntu machine. In a local network, each machine's hosts file should list all of the other machines to make access by name possible...

The anti-rootkit programs you used probably rewrote the hosts file, since it's often modified by malware.

---

### Post by flurospar on 2012-03-20
[Rootkit Revealer]("http://technet.microsoft.com/en-us/sysinternals/bb897445") is another rootkit detection utility, which is quite good at its job. You could boot in Safe mode (although booting in safe mode may not help much because rootkits go really deep inside the system), run [rkill.com]("http://www.bleepingcomputer.com/download/anti-virus/rkill") and then run Rootkit revealer. Remember to rename the files before you run them.

You might find some more rootkits, and hopefully remove them. Sometimes, just using another detection tool is often helpful in some cases.

---

