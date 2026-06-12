---
title: "How secure is Ubuntu?"
date: 2010-02-05
forum: Recurring Discussions
---

### Post by john.kreelman on 2010-02-05
Is it secure? Obviously less of a target than Windows but can you realistically run Ubuntu behind a secure Nat router without machine based security?

I ask this as I read the sticky note about setting up NID & HID and it seemed horrendously involved!

Are there other less labour intensive apps to install for security?

I'm very new the Linux and am not used to command line stuff at all.

---

### Post by Bachstelze on 2010-02-05
As a regular desktop user, you won't need any kind of security software on Ubuntu, even moreso if you're behind a NAT. If you want to be paranoid, a few antiviruses exist for Linux, and soem graphical tools to configure the iptables firewall, but as I said, this will really not be necessary.

---

### Post by sxmaxchine on 2010-02-05
i always recomend an antivirus even for ubuntu that has a much lower chance of getting a virus. basicaly just because you run linux that doesnt make you invincible. also i think avast has a linux.

check this for more information about avast [http://www.debianadmin.com/avast-antivirus-for-ubuntu-desktop.html]("http://www.debianadmin.com/avast-antivirus-for-ubuntu-desktop.html")

---

### Post by lykwydchykyn on 2010-02-05
rkhunter and chkrootkit are decent, if you're concerned about rootkits.

Most of the threats you need to worry about with Linux are attacks against network services exposed to the internet, for instance if you're running ssh and forwarding it through your router.

If you're not doing that, pretty much everything else is social engineering (phishing, scams, etc).

---

### Post by bodhi.zazen on 2010-02-05
> **lykwydchykyn said:**
> rkhunter and chkrootkit are decent, if you're concerned about rootkits.

Most of the threats you need to worry about with Linux are attacks against network services exposed to the internet, for instance if you're running ssh and forwarding it through your router.

If you're not doing that, pretty much everything else is social engineering (phishing, scams, etc).

+1

For the vast majority of desktop users you need 

1. A router (provides a firewall).

2. strong passwords.

3. Default installation of Ubuntu is fine for the vast majority of users. 

4. I know old habits die hard, but there are no known active viruses for Linux and Linux security, unlike Windows security, is not dependent of antivirus or spyware scanners. Likewise a default installation of Ubuntu has no signifigant open ports so no need for a firewall.

5. If you are interested in additional technical details, read the security sticky :

[Ubuntu Security - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=510812")

6. By far the biggest thread is "social engineering", just take care with installing applications from untrusted sources.

---

### Post by john.kreelman on 2010-02-05
Thanks, there seems to be alot of stuff to digest and I very much appreciate you writing the information down for the likes of myself who come from windows mindset. I must admit that to imagine not having a firewall running and no av would feel like trotting through Brixton high street naked with bags of cash open for all to see. You wouldn't last five seconds!!!

I can see what you are indicating though. I'll take time to read the articles. Many thanks. Cheers to the other respondees too, I'll be looking at the suggestions.

---

### Post by tubbygweilo on 2010-02-05
I live in Brixton and use Ubuntu - no problems at all;)

---

### Post by Roasted on 2010-02-05
I utilize an anti virus on my Ubuntu desktop, and I swear by it. But my Windows machines back up to my Ubuntu desktop every night at 4 am, so when I do scans and find viruses on the backups, I know I have to be a little more active with the automatic virus scanners on the Windows boxes themselves.

Even though the viruses don't effect Linux, a virus is still a file, and files can still reside on a Linux computer. Dormant/dead file to Linux or not, it's still a virus, and something that I like to actively take care of.

---

### Post by mamamia88 on 2010-02-05
i don't use an antivirus because i'm not paranoid.  and besides virues are more of social engineering concern than security concern.  if you are stupid enough to grant root permissions to something you have no idea where it came from i'm sorry but you deserve to get infected.

---

### Post by lykwydchykyn on 2010-02-05
> **john.kreelman said:**
> Thanks, there seems to be alot of stuff to digest and I very much appreciate you writing the information down for the likes of myself who come from windows mindset. I must admit that to imagine not having a firewall running and no av would feel like trotting through Brixton high street naked with bags of cash open for all to see. You wouldn't last five seconds!!!

I can see what you are indicating though. I'll take time to read the articles. Many thanks. Cheers to the other respondees too, I'll be looking at the suggestions.

If you're behind a router and aren't forwarding any ports, you effectively have a firewall.  Adding one to the workstation is just redundant.

If it's a laptop you intend to connect to public networks, if you're forwarding ports, if you think your router might get hacked, or if you suspect someone might connect to your network and try malicious things, then a firewall on the workstation is sensible.  Fortunately there's one built into the linux kernel, and lots of options for working with it.

Here's a good option: [http://www.ubuntugeek.com/gufw-simple-gui-for-ufw-uncomplicated-firewall.html](http://www.ubuntugeek.com/gufw-simple-gui-for-ufw-uncomplicated-firewall.html)

---

