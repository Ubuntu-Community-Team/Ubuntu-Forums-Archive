---
title: "Is my computer safe?"
date: 2011-10-09
forum: New to Ubuntu
---

### Post by sujitrjadhav on 2011-10-09
I recently installed "firestarter" firewall on my Ubuntu 11.04 installation. I was checking active connections and I found some connections even though I am not doing anything actively. Further "program" column sows "tor" even though I dont have tor installed on my laptop. I am worried about security of my laptop as I use it for netbanking/online credit card transactions. attached is screen shot of firestarter.

---

### Post by spiky001 on 2011-10-09
Fire starter is not maintained any more you might be better with ufw (gufw) graphical version

---

### Post by sujitrjadhav on 2011-10-09
Ok I am uninstalling firestarter right now and installing gufw. But my question remains unanswered. why firestarter shows 4 active connections through tor? Are default ubuntu security settings insufficient from security angle?

---

### Post by hakermania on 2011-10-09
> **sujitrjadhav said:**
> Ok I am uninstalling firestarter right now and installing gufw. But my question remains unanswered. why firestarter shows 4 active connections through tor? Are default ubuntu security settings insufficient from security angle?

Ubuntu are quite safe from default right now.
You can use 'Wireshark' to see what's being sent and where.

---

### Post by Dangertux on 2011-10-09
> **sujitrjadhav said:**
> I recently installed "firestarter" firewall on my Ubuntu 11.04 installation. I was checking active connections and I found some connections even though I am not doing anything actively. Further "program" column sows "tor" even though I dont have tor installed on my laptop. I am worried about security of my laptop as I use it for netbanking/online credit card transactions. attached is screen shot of firestarter.

As it was stated earlier Firestarter has not been updated in a long time and even when it was updated it was rather buggy.

I would highly suggest utilizing UFW/GUFW. Other security measures you can take are to make sure you are utilizing SSL on all sites that support it. Make sure you're using browser extensions like NoScript (Firefox) or NotScripts (Chrome/Chromium). Additionally if you want to learn to configure Apparmor it is a good thing to utilize.  

It does appear though that you may be using Tor. If you would like to find out if you're using Tor the following 

```

sudo netstat -anlp | grep tor

```If it shows Tor listening you have it installed to disable tor you may do the following

```

sudo /etc/init.d/tor stop
sudo update-rc.d -f tor remove

```Hope that helps.

---

### Post by haqking on 2011-10-09
> **sujitrjadhav said:**
> Ok I am uninstalling firestarter right now and installing gufw. But my question remains unanswered. why firestarter shows 4 active connections through tor? Are default ubuntu security settings insufficient from security angle?

can you show us the output of

```
ss -aln | grep 9050
```

edit: ninja'd above

yeah looks to me like your running tor

the grape.canonical item is ubuntu one i believe

---

### Post by sujitrjadhav on 2011-10-09
Using Command
sudo /etc/init.d/tor stop
Indeed helped. After executing this command now firestarter dont show any else unexplained connection.  I might have installed tor in the past but never used it. So it appears that my computer was safe. I am new to linux world and dont know much about security. I have installed gufw and wireshark as suggested in replys. What else softwares should I install to protect my laptop? I have read somewhere that linux dosent require any antivirus software so I have not installed any AV software.

---

### Post by haqking on 2011-10-09
> **sujitrjadhav said:**
> Using Command
sudo /etc/init.d/tor stop
Indeed helped. After executing this command now firestarter dont show any else unexplained connection.  I might have installed tor in the past but never used it. So it appears that my computer was safe. I am new to linux world and dont know much about security. I have installed gufw and wireshark as suggested in replys. What else softwares should I install to protect my laptop? I have read somewhere that linux dosent require any antivirus software so I have not installed any AV software.

Installing wireshark does nothing for your system security, it is a packet analyser and if you are a linux newbie it is unlikely to be of any assistance to you (not that you need to know linux to use it), however it requires an in depth understanding of protocols to be able to gleem any information from it, it gathers packets and then you interpret them.

AV is not needed, or at least there is no wild viruses for linux and the only real merit for AV software in Linux is for file sharing with windows users, and most of the Linux AV provides alot of false positives.

read here

[http://en.wikipedia.org/wiki/Linux_malware](http://en.wikipedia.org/wiki/Linux_malware)
[https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus)
[https://help.ubuntu.com/community/Linuxvirus](https://help.ubuntu.com/community/Linuxvirus)
[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)
[http://www.neowin.net/news/a-history-of-viruses-on-linux](http://www.neowin.net/news/a-history-of-viruses-on-linux)

Linux does not suffer from Viruses like other OS, there are no known viruses in the wild currently, the main reason using AV on linux is to scan incase you share files with windows users.  Malware writers have not as yet targeted Linux as they have other OS, they could do so, it is not to say that Linux is inpenetrable from Malware as it is not, however currently there are no known viruses which could effect it, conversely even though viruses have been known about for a very long time certain OS are still susceptible from viruses written 10 years ago.

**No system is 100% secure when on a network or sharing data, security is best in a layered approach and with ongoing vigilence and awareness, the main security flaw in any system is PEBKAP = Problem Exists Between Keyboard And Person**

It can still suffer from trojans, rootkits etc, but that comes down to vigilence and making sure you stick to the security model and not disabling passwords or enabling root etc.

Common sense, dont tell your system you want it to do something unless you are sure etc. Linux assumes you know what you are doing ;-)

In browsers you can still suffer from XSS or CSFR, other script related issues so use things like NoScript plugin for firefox, Ad-block etc.

---

### Post by Dangertux on 2011-10-09
> **sujitrjadhav said:**
> Using Command
sudo /etc/init.d/tor stop
Indeed helped. After executing this command now firestarter dont show any else unexplained connection.  I might have installed tor in the past but never used it. So it appears that my computer was safe. I am new to linux world and dont know much about security. I have installed gufw and wireshark as suggested in replys. What else softwares should I install to protect my laptop? I have read somewhere that linux dosent require any antivirus software so I have not installed any AV software.

Don't take this the wrong way as it is not meant as an insult, but in terms of desktop security the best thing you can install is common sense. 

In this thread alone you have utilized two pieces of software you were previously unaware of on the basis that someone recommended it. I realize that being new to security and Linux can be daunting, however please take the time to research for yourself what others are recommending.

A note on UFW, it will conflict with Firestarter, so you should remove firestarter if you're going to utilize UFW.

Anti-virus on Ubuntu is essentially useless, there is a lack of targeted malware, and if there wasn't I'm unconfident that the present anti-malware solutions would do anything. This is an opinion, draw your own conclusions.

As I stated before addons for Firefox like NoScript, are very helpful especially if you use web based applications to do sensitive things (eg: banking)

Overall just use your best judgement. A friend of mine once said 

"Did you go on the Internet looking to download and install software? No? Then why did you download and install software?"

These are wise words.

---

### Post by sujitrjadhav on 2011-10-09
Thanks very much to all of you for help. I am happy that once again Ubuntu forum has helped me solve problem so quick.

---

